# **Presentation** : Guillaume *"Guss"* Dua

---

## **C++** Serialization

---

Problematic overview :
===================

> * Needs of GGE
> * Frances buentempo's article ([see Overload journal, Accu.org](https://accu.org/index.php/journal))
> * Brownian motion reproducibility

![GGE](/events/2017-01-19_n14/Serial/img_rendering/GGE.PNG "Screenshot GGE : Brownian particles test")]

> "How generate a two-way mapping between **types** and constexpr **indexes**,
> with both **static** and **dynamic** accessors ?
>
>  **Write** "type" information in a file
>  and get it back while **reading**
> 
>  Part of https://github.com/GuillaumeDua/GCL_CPP
>  GCL::Serialization

---

Existing solutions :
> Debug infos : GCC Drawf ?

---
### Pre-requis :
* STL
* Templates : template-template-..., variadics
* *(Bonus)* SFINAE using std::void_t

---

Store type infos (1)
==============
* Type/index mapping : *static*
 
![TypePack](/events/2017-01-19_n14/Serial/img_rendering/TypePack.png "TypePack : Static association")

```cpp
template <typename ... Types>
struct TypePack
{
	using _Types = std::tuple<Types...>;

	template <typename T>
	static constexpr inline size_t indexOf(void);			// Type -> ID
	
	template <size_t N>
	using TypeAt = typename std::tuple_element<N, _Types>::type;	// ID -> Type
};
```
```cpp
using _TypePack = TypePack<...>;

using MyType = _TypePack.TypeAt<42>;                // correct
const size_t index = _TypePack.indexOf<MyClass1>(); // correct

size_t myTypeIndex = /* dynamic value */;
using MyType = _TypePack.TypeAt<myTypeIndex>;		// error !
```
----------
Store types infos (2)
==============

Type/index mapping : *dynamic*

	* std::map<T_Key, T_Value>
	* Initializer-list for template viariadics expansion
	* Polymorphism

![TypeIndexer_0](/events/2017-01-19_n14/Serial/img_rendering/TypePack_dynamic_0.png "TypePack : Static association 0")
![TypeIndexer_1](/events/2017-01-19_n14/Serial/img_rendering/TypePack_dynamic_1.png "TypePack : Static association 1")
![TypeIndexer_2](/events/2017-01-19_n14/Serial/img_rendering/TypePack_dynamic_2.png "TypePack : Static association 2")
---

C++ Serialization : Bring all pieces together
==============

```cpp
template <class T_Interface>
struct InterfaceIs
{
	using _InterfaceType = T_Interface;

	template <typename ...Types>
	struct OfTypes
	{
		using _TypesPack = typename GCL::TypeTrait::TypePack<Types...>;
		using _ThisType = typename OfTypes<Types...>;

		template <typename T_IO_POlicy = GCL::IO::Policy::Binary>
		struct Writer;
		template <typename T_IO_POlicy = GCL::IO::Policy::Binary>
		struct Reader;
	}
}	
```
---
C++ Serialization : Writer
==============

![Writer](/events/2017-01-19_n14/Serial/img_rendering/Writer.png "GCL::Serialization::Writer")

```cpp
template <typename T_IO_POlicy = GCL::IO::Policy::Binary>
struct Writer
{
	template <typename T>
	static void	write(std::ostream & os, const T & var)
	{
		static_assert(std::is_base_of<_InterfaceType, T>::value,
		              "GCL::Serialization::InterfaceIs<I>::Writer::write<T> : T is not child of I");
		
		T_IO_POlicy::write(os, _TypesPack::template indexOf<T>());
		os << var;
	}

	template <typename T>
	Writer &	operator<<(const T & element)
	{
		write(_oStream, element);
		return *this;
	}
};
```

---
C++ Serialization : Reader
==============

![Reader](/events/2017-01-19_n14/Serial/img_rendering/Reader.png "GCL::Serialization::Reader")

```cpp
template <typename T_IO_POlicy = GCL::IO::Policy::Binary>
struct Reader
{
	using T_TypeManager = typename TypeTrait::InterfaceIs<_InterfaceType>::template OfTypes<Types...>;

	template <typename T>
	static void				read(std::istream & is, T & var)
	{
		size_t typeIndex;
		is >> typeIndex;
		_GCL_ASSERT(_TypesPack::template indexOf<T>() == typeIndex);
		is >> var;
	}
	static _InterfaceType *	read(std::istream & is)
	{
		size_t typeIndex;

		T_IO_POlicy::read(is, typeIndex);
		if (is.eof()) return 0x0;

		auto & constructor = T_TypeManager::index.at(typeIndex).defaultConstructeurCallerOp; // std::map.at can throw
		_InterfaceType * elem = constructor();
		is >> *elem;
		return elem;
	}
	
	Reader &				operator>>(_InterfaceType *& element);
	Reader &				operator>>(std::queue<_InterfaceType*> & elemQueue);
};
```

---

C++ Serialization : Usage
==============

Interface
------------
```cpp
struct TestInterface
{
	virtual void DoStuff() const = 0;

	virtual std::istream & operator>>(std::istream &) = 0;
	virtual std::ostream & operator<<(std::ostream &) const = 0;
	friend inline std::ostream& operator<<(std::ostream & os, const TestInterface & s);
	friend inline std::istream& operator>>(std::istream & is, TestInterface & s);
};
```
Classes to serialize
---------------------------
Let's be lazy *(sorry)*
```cpp
#define GenTestClass(name, type)\
struct name : TestInterface	{	\																									
	name() = default;			\
	name(type value)			\
	: _value(value){}           \
	type _value;                \
	void	DoStuff(void) const override \
	{ std::cout << ""#name##"" " -> value=[" << _value << ']' << std::endl; }\
	std::ostream & operator<<(std::ostream & os) const  override \
	{ GCL::IO::Policy::Binary::write(os, _value); return os; }	 \
	std::istream & operator>>(std::istream & is) override        \
	{ GCL::IO::Policy::Binary::read (is, _value); return is; }	 \
};
```

```cpp
GenTestClass(Toto, int);
GenTestClass(Titi, std::string);
GenTestClass(Tata, int);
GenTestClass(Tutu, std::string);
```

---

Writer
---------
```cpp
using Writer = Serialization::InterfaceIs<TestInterface>::OfTypes<Toto, Titi, Tata, Tutu>::Writer<>;

std::stringstream ss;
Writer writer(ss);
writer
	<< Toto{ 42 }
	<< Titi{ "Hello, world" }
	<< Tata{ 130390 }
	<< Tutu{ "Morning' coffee" }
;
std::cout << "Serialized : [" << ss.str() << ']' << std::endl;
```
Console output :
```
Serialized : [    *   ☺   ♀   Hello, world☻   V²☺ ♥   ☼   Morning' coffee]
```

---

Reader
----------
```cpp
using Reader = Serialization::InterfaceIs<TestInterface>::OfTypes<Toto, Titi, Tata, Tutu>::Reader<>;
try
{
    Reader			reader(ss);

	std::queue<TestInterface*> elements;
	reader
        >> elements
    ;

	while (not elements.empty())
	{
		elements.front()->DoStuff();	// TestInterface::DoStuff
		delete elements.front();
		elements.pop();
	}
}
catch (const std::exception & ex)
{
	std::cerr << ex.what() << std::endl;
}
```
Console output :
```
Toto -> value=[42]
Titi -> value=[Hello, world]
Tata -> value=[130390]
Tutu -> value=[Morning' coffee]
```

---

Bonus : Go futher
==============

---

Restrictions using "Attributes" (1)
===========================

What about **C#** ?
----------------------------

Few words about  [NonSerialized()] attribute

```Csharp
namespace Sample
{
    public class DataToSerialize
    {
        // ...
        [NonSerialized()] 		// <------- !
        private BigStuff _bigStuff;
    }
}
```

---

Restrictions using "Attributes" (2)
===========================

What about **C++** ?
------------------------------

* SFINAE
*(also introduce by Walter Brown talk's about std::void_t : [see Cppcon14 Youtube video](https://www.youtube.com/watch?v=a0FliKwcwXE))*

	``` std::void_t<typename T:: > ``` 

* Base code, be lazy : 

```cpp
#define GCL_Introspection__GenHasNested(nested)			\
template< class, class = std::void_t<> >				\
struct has_##nested##_nested : std::false_type { };
```

---

Restrictions using "Attributes" (3)
===========================

What about GCL::Serialization ?
--------------------------------------------

```cpp
GCL_Introspection__GenHasNested(NotSerializable)

template <typename T>
struct WriterImpl
{
	static constexpr bool isSerializable = !GCL::Introspection::has_NotSerializable_nested<T>::value;

	template <bool _isSerializable = isSerializable>
	static constexpr void	write_impl(std::ostream & os, const T & var);
	template <>
	static constexpr void	write_impl<true>(std::ostream & os, const T & var)
	{
		T_IO_POlicy::write(os, _TypesPack::template indexOf<T>());
		os << var;
	}
	template <>
	static constexpr void	write_impl<false>(std::ostream & os, const T & var)
	{
	    // Do nothing or ...
		// static_assert(false, "This type has \"NotSerializable\" static-qualifier");
	}
};
```

---

Restrictions using "Attributes" (4)
===========================

Result
---------

```cpp
struct NotSerializableType
{
	enum NotSerializable{};
};
```

```cpp
Writer writer(ss);
writer
	<< Toto{ 42 }
	<< Titi{ "Hello, world" }
	<< Tata{ 130390 }
	<< Tutu{ "Morning' coffee" }
	<< NotSerializableType{}     // Error !
;
```

```cpp
error C2338: This type has "NotSerializable" static-qualifier
```

---

Evolutions ?
==========
* Codec
* Retro-compatibility ?
