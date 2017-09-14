Vous avez dit bizarre ?
-----------------------

Copyright 2017 olibre &emsp; [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr)

[![le logo C++FRUG est consitué du drapeau de la francophonie avec C++ au centre](http://cpp-frug.github.io/images/Cpp-Francophonie.svg "Logo C++FRUG")](https://github.com/cpp-frug/cpp-frug.github.io/blob/master/images/Cpp-Francophonie.svg)

* Reveal [cppfrug.org/paris/events/2017-09-14_n19/bizarre/reveal.html](http://cppfrug.org/paris/events/2017-09-14_n19/bizarre/reveal.html)
* Jekyll [cppfrug.org/paris/events/2017-09-14_n19/bizarre](http://cpp-frug.github.io/paris/events/2017-09-14_n19/bizarre/)
* GitHub [github.com/cpp-frug/paris/events/2017-09-14_n19/bizarre](https://github.com/cpp-frug/paris/blob/master/events/2017-09-14_n19/bizarre/README.md)




Pas besoin d'indiquer `return` pour `main()`

```cpp
int main()
{
  // return 0 by default
}
```

    > g++ main.cpp && ./a.out && echo $?
    0



```cpp
#include <iostream>

int main()
{
  std::cout << 007 << std::endl;
  std::cout << 042 << std::endl;
  std::cout << 123 << std::endl;
}
```


```cpp
#include <iostream>

int main()
{
  std::cout << 007 << std::endl;
  std::cout << 042 << std::endl;
  std::cout << 123 << std::endl;
}
```

    7
    34
    123


```cpp
#include <iostream>

int main()
{
  std::cout << std::oct;  // s'applique partout

  std::cout << 007 << std::endl;
  std::cout << 042 << std::endl;
  std::cout << 123 << std::endl;
}
```

    7
    42
    173


Temps parcouru par la lumière entre le Soleil et Jupiter

```cpp
#include <iostream>
#include <chrono>
using namespace std::chrono_literals;

template <typename T>
auto answer(T t)
{
  // Light takes 43:07 from Sun to Jupiter
  return t ???-- 43:07;
}

int main()
{
  auto day = 24h;
  auto halfhour = 0.5h;
  std::cout <<"one day is "<< day.count() <<" hours\n"
            <<"1/2 hour is "<< halfhour.count() <<" hours\n"
            <<"the answer is "<< answer(day.count()) <<'\n';
}
```

    one day is 24 hours
    1/2 hour is 0.5 hours
    the answer is 42

http://coliru.stacked-crooked.com/a/0f60ac9f5bef835a


Trigraph &emsp; `??-` &emsp; -> &emsp; `~`

```cpp
#include <iostream>
#include <chrono>
using namespace std::chrono_literals;

template <typename T>
auto answer(T t)
{
  // Light takes 43:07 from Sun to Jupiter
  return t ?~- 43:07;
}

int main()
{
  auto day = 24h;
  auto halfhour = 0.5h;
  std::cout <<"one day is "<< day.count() <<" hours\n"
            <<"1/2 hour is "<< halfhour.count() <<" hours\n"
            <<"the answer is "<< answer(day.count()) <<'\n';
}
```

    one day is 24 hours
    1/2 hour is 0.5 hours
    the answer is 42


Opérateur ternaire

```cpp
#include <iostream>
#include <chrono>
using namespace std::chrono_literals;

template <typename T>
auto answer(T t)
{
  // Light takes 43:07 from Sun to Jupiter
  return t ? ~-43 : 07;
}

int main()
{
  auto day = 24h;
  auto halfhour = 0.5h;
  std::cout <<"one day is "<< day.count() <<" hours\n"
            <<"1/2 hour is "<< halfhour.count() <<" hours\n"
            <<"the answer is "<< answer(day.count()) <<'\n';
}
```

    one day is 24 hours
    1/2 hour is 0.5 hours
    the answer is 42


Complément à un *(ones' complement)*
[std::bit_not](http://en.cppreference.com/w/cpp/utility/functional/bit_not)
&emsp; `~1` &emsp; -> &emsp; `-2` &emsp; (si signé)

```cpp
#include <iostream>
#include <chrono>
using namespace std::chrono_literals;

template <typename T>
auto answer(T t)
{
  // Light takes 43:07 from Sun to Jupiter
  return t ? 42 : 07;
}

int main()
{
  auto day = 24h;
  auto halfhour = 0.5h;
  std::cout <<"one day is "<< day.count() <<" hours\n"
            <<"1/2 hour is "<< halfhour.count() <<" hours\n"
            <<"the answer is "<< answer(day.count()) <<'\n';
}
```

    one day is 24 hours
    1/2 hour is 0.5 hours
    the answer is 42



Vous avez dit bizarre ?

```cpp
#include <iostream>

int main()
{
  auto x = ("C++", '2017');
  std::cout << x << std::endl;
}
```

http://coliru.stacked-crooked.com/a/8ff0bbede46cd18f


Vous avez dit bizarre ?

```cpp
#include <iostream>

int main()
{
  auto x = ("C++", '2017');
  std::cout << x << std::endl;
}
```

    842019127


Opérateur virgule *(Comma operator)*
[wikipedia.org](https://en.wikipedia.org/wiki/Comma_operator)
[cppreference.com](http://en.cppreference.com/w/cpp/language/operator_other#Built-in_comma_operator)

```cpp
#include <iostream>

int main()
{
  auto x = ("C++", '2017');
  std::cout << x << std::endl;
}
```

    842019127


Sans l'opérateur virgule

```cpp
#include <iostream>

int main()
{
  auto x = '2017';
  std::cout << x << std::endl;
}
```

    842019127


Multi-character character constant

```cpp
#include <iostream>

int main()
{
  int x = '2017';
  std::cout << x << std::endl;
}
```

    842019127


Multi-character character constant are just characters

```cpp
#include <iostream>

int main()
{
  int x = '2017';
  char* txt = reinterpret_cast<char*>(&x);
  std::cout << txt[3];
  std::cout << txt[2];
  std::cout << txt[1];
  std::cout << txt[0];
}
```

    2017



Non mais !!??

```cpp
#include <iostream>

template <bool B = true>
bool foo (bool b = B) {
  return !!b??!??!!!b;
}

template <bool B = false>
bool bar (bool b = B) {
  std::cout << !b??!??!!b;
}

int main() {
  !foo()??!??!bar();
}
```

    1

http://coliru.stacked-crooked.com/a/3a7d316dd41cb1b3


Trigraphs &emsp; `??!` &emsp; -> &emsp; `|`

```cpp
#include <iostream>

template <bool B = true>
bool foo (bool b = B) {
  return !!b || !!b;     // !!b??!??!!!b
}

template <bool B = false>
bool bar (bool b = B) {
  std::cout << !b || b;  // !b??!??!!b
}

int main() {
  !foo() || bar();      // !foo()??!??!bar();
}
```

    1


Simplifications

```cpp
#include <iostream>

template <bool B = true>
bool foo (bool b = B) {
  return b;  // !!b || !!b
}

template <bool B = false>
bool bar (bool b = B) {
  std::cout << true;  // !b || b
}

int main() {
  if (foo()) bar();  // !foo() || bar();
}
```

    1



```cpp
#include <iostream>

int main()
{
  char a[] = "ciel + v";

  std::cout << 7 + a << 1[a] << 7[a]
     << 2[a] << 6[a] << 3[a] << 2[a]
     << 6[a] <<  *a  << 5[a] << a[5];
}
```


```cpp
#include <iostream>

int main()
{
  char a[] = "ciel + v";

  std::cout << 7 + a << 1[a] << 7[a]
     << 2[a] << 6[a] << 3[a] << 2[a]
     << 6[a] <<  *a  << 5[a] << a[5];
}
```

    vive le c++



Ternary as lvalue

    (a ? b : c) = 42;


```cpp
#include <iostream>

int main()
{
    int a, b, c;
    (a ? b : c) = 42;
    std::cout << a <<' '<< b <<' '<< c;
}
```

    32765 42 0



URL in code

```cpp
#include <iostream>

int main()
{
std::cout << '4';
http://www.cppfrug.org
std::cout << '2';
}
```

http://coliru.stacked-crooked.com/a/230fc215df0fa6d1


URL in code

```cpp
#include <iostream>

int main()
{
std::cout << '4';
http://www.cppfrug.org
std::cout << '2';
}
```

    42


```cpp
#include <iostream>

int main()
{
std::cout << '4';
http://www.cppfrug.org
std::cout << '2';
goto http;
}
```

    42222222222222222222222222222222...



Scope-declared types

```cpp
#include <iostream>

int main()
{
  for (struct { int a; float b; } loop = { 1, 2.3 };
       loop.a < 5 || loop.b < 999;
       loop.a++, loop.b *= loop.a)

         std::cout << loop.a <<' '<< loop.b <<'\n';
}
```

    1 2.3
    2 4.6
    3 13.8
    4 55.2
    5 276



Optionnellement bizarre

```cpp
std::optional<bool> var(false);

if (var && var == false)
    std::cout << "lol";
```


```cpp
#include <iostream>
#include <optional>

int main()
{
  std::optional<bool> var(false);

  if (var && var == false)
    std::cout << "lol";
}
```

    lol



```cpp
template<typename T>
void foo (T& t)
{
    t.bar<int>();
}

struct C
{
    template<typename T>
    void bar() { }
};

int main()
{
    C c;
    foo<C>(c);
}
```

    > g++-7.2 -Wall -Wextra -pedantic main.cpp
    main.cpp: In function 'void foo(T&)':
    main.cpp:4:11: error: expected primary-expression before 'int'
          t.bar<int>();
                ^~~
    main.cpp:4:11: error: expected ';' before 'int'


```cpp
template<typename T>
void foo (T& t)
{
    t.bar<int>();
}

struct C
{
    template<typename T>
    void bar() { }
};

int main()
{
    C c;
    foo<C>(c);
}
```

    > clang++-3.6 -Wall -Wextra -pedantic main.cpp
    main.cpp:4:7: error: use 'template' keyword to treat 'bar' as a dependent template name
        t.bar<int>();
          ^
          template


```cpp
template<typename T>
void foo (T& t)
{
    t.template bar<int>();  // Insérer template
}

struct C
{
    template<typename T>
    void bar() { }
};

int main()
{
    C c;
    foo<C>(c);
}
```



Passer le retour d'une fonction par paramètre

```cpp
class C {};

void foo (C &) {}

C bar() { return C(); }

int main()
{
  foo( bar() );
}
```


GCC ne veut pas

```cpp
class C {};

void foo (C &) {}

C bar() { return C(); }

int main()
{
  foo( bar() );
}
```

    > g++-7.2 -Wall -Wextra main.cpp
    main.cpp: In function 'int main()':
    main.cpp:9:11: error: cannot bind non-const lvalue reference of type 'C&' to an rvalue of type 'C'
       foo( bar() );
            ~~~^~
    main.cpp:3:6: note:   initializing argument 1 of 'void foo(C&)
     void foo (C &) {}
          ^~~


Clang non plus

```cpp
class C {};

void foo (C &) {}

C bar() { return C(); }

int main()
{
  foo( bar() );
}
```

    > clang++-3.8 -Wall -Wextra main.cpp
    main.cpp:9:3: error: no matching function for call to 'foo'
      foo( bar() );
      ^~~
    main.cpp:3:6: note: candidate function not viable: expects an l-value for 1st argument
    void foo (C &) {}
         ^


Transformer une R-Value en L-Value

```cpp
class C {};

void foo (C &) {}

C bar() { return C(); }

int main()
{
  foo( bar() );
}
```

Le standard C++ ne permet pas de transformer une R-Value en L-Value  
(modifier un objet temporaire qui va tout de suite mourir)


```cpp
class C {};

void foo (C &) {}

C bar() { return C(); }

int main()
{
  foo( bar() );
}
```

1. La fonction `foo()` est appelée avec comme paramètre le retour de la fonction `bar()`
   c’est une **unnamed variable** (ou **anonymous variable**).
2. Comme sa durée de vie s’arrête avec la fin de l’appel de `foo()`,
   c’est aussi un **temporary object** (ou **temporary value**).
3. Mais `foo(C&)` attend un objet modifiable.  
   (même s’il n’en fait rien, cet objet doit être modifiable.)
4. Donc il n’y a pas d’intérêt à donner un objet temporaire à une fonction qui va le modifier.


Scott Meyers - More Effective C++

Consider this function:

```cpp
// changes all chars in str to upper case
void uppercasify( std::string& str );
```

In the character-counting example, a char array passed to uppercasify() fails:  
http://coliru.stacked-crooked.com/a/f324de25c709cb0e

```cpp
char title[] = "Effective C++";
uppercasify(             title  );  // error #1
uppercasify( std::string(title) );  // error #2
```

`error #1` No temporary is created to make the call succeed. Why not?

Suppose a temporary were created (`error #2`). Then the temporary would be passed to `uppercasify()`, which would modify the temporary so its characters were in upper case. But the actual argument to the function call — `title` — would not be affected; only the temporary `std::string` object generated from `title` would be changed.

Surely this is not what the programmer intended. That programmer passed title to `uppercasify()`, and that programmer expected `title` to be modified.

Implicit type conversion for references-to-non-const objects, then, would allow temporary objects to be changed when programmers expected non-temporary objects to be modified. That's why the language prohibits the generation of temporaries for non-const reference parameters. Reference-to-const parameters don't suffer from this problem, because such parameters, by virtue of being `const`, can't be changed.


[Contournenement C++03](http://coliru.stacked-crooked.com/a/314016237c79ad25)

```cpp
struct C {};

void foo (const C &) {}  // const

C bar() { return C(); }

int main()
{
  foo( bar() );
}
```


[Un autre contournenement C++03](http://coliru.stacked-crooked.com/a/bff5b2165e2e4994)

```cpp
struct C {};

void foo (C &) {}

C bar() { return C(); }

int main()
{
  C c;  // no temporary object
  foo( c = bar() );
}
```


[Contournement C++11](http://coliru.stacked-crooked.com/a/aebff3189a99eaff)

```cpp
#include <utility>  // std::move

struct C
{
    C &  ok() { return           *this;  }
    C && ko() { return std::move(*this); }
};

void foo (C &) {}

C bar() { return C(); }

int main()
{
    foo( bar().ok() );
    foo( bar().ko() );  // ERROR
}
```


Mais [sans succès](http://coliru.stacked-crooked.com/a/e1fd06609cdb2b43)
avec les
[ref-qualifier `&` et `&&`](http://en.cppreference.com/w/cpp/language/member_functions)


```cpp
#include <utility>  // std::move

struct C
{
    C &  ok() &  { return           *this;  }
    C && ko() && { return std::move(*this); }
};

void foo (C &) {}

C bar() { return C(); }

int main()
{
    foo( bar().ok() );  // ERROR
    foo( bar().ko() );  // ERROR
}
```

[Avec](http://coliru.stacked-crooked.com/a/c6bd0c3a57282d8f)
la rvalue-reference (C++11)

```cpp
struct C {};

void foo (C &&) {}  // non-const rvalue-reference

C bar() { return C(); }

int main()
{
  foo( bar() );
}
```


Que sont `c1` et `c2` ?

```cpp
#include <iostream>

template<class T>
struct C
{
  C()  { std::cout <<"default ctor\n";            }
  C(T) { std::cout <<"ctor: "<< sizeof(T) <<'\n'; }
};

template <class T> C<T> c1;
template <class T> C<T> c2(2);

int main()
{
  auto a1 = c1<short>;
  auto a2 = c2<short>;
  auto a3 = c2<double>;
}
```


Que sont `c1` et `c2` ?

```cpp
#include <iostream>

template<class T>
struct C
{
  C()  { std::cout <<"default ctor\n";            }
  C(T) { std::cout <<"ctor: "<< sizeof(T) <<'\n'; }
};

template <class T> C<T> c1;
template <class T> C<T> c2(2);

int main()
{
  auto a1 = c1<short>;
  auto a2 = c2<short>;
  auto a3 = c2<double>;
}
```

    default ctor
    ctor: 2
    ctor: 8


`c1` et `c2` sont des [variables template](https://en.wikipedia.org/wiki/C%2B%2B14#Variable_templates) (C++14)

```cpp
#include <iostream>

template<class T>
struct C
{
  C()  { std::cout <<"default ctor\n";            }
  C(T) { std::cout <<"ctor: "<< sizeof(T) <<'\n'; }
};

template <class T> C<T> c1;
template <class T> C<T> c2(2);

int main()
{
  auto a1 = c1<short>;
  auto a2 = c2<short>;
  auto a3 = c2<double>;
}
```

    default ctor
    ctor: 2
    ctor: 8


À quoi sert les
[variable templates](http://en.cppreference.com/w/cpp/language/variable_template)
?


Avant, pour avoir des "variables paramétrables" on avait deux contournements :

- Déclarer + Définir des membres `static` aux classes templates (`*.h` + `*.cpp`)
- Définir des fonctions templates `constexpr` retournant la bonne valeur



Quelle ligne ne compile pas ?

```cpp
template <int X>
struct Base
{
    void foo() { }
};

template <int X>
struct Derive : Base<X>
{
    void bar() { foo(); }
};
```

http://coliru.stacked-crooked.com/a/daca4a7b7d8ef906


GCC

```cpp
template <int X>
struct Base
{
    void foo() { }
};

template <int X>
struct Derive : Base<X>
{
    void bar() { foo(); }  // ERROR
};
```

    > g++-7.2 -Wall -Wextra -pedantic main.cpp
    main.cpp: In member function 'void Derive<X>::bar()':
    main.cpp:10:18: error: there are no arguments to 'foo' that depend on a template parameter, so a declaration of 'foo' must be available [-fpermissive]
         void bar() { foo(); }
                      ^~~
    main.cpp:10:18: note: (if you use '-fpermissive', G++ will accept your code, but allowing the use of an undeclared name is deprecated)


Clang

```cpp
template <int X>
struct Base
{
    void foo() { }
};

template <int X>
struct Derive : Base<X>
{
    void bar() { foo(); }
};
```

    > clang++-3.8 -Wall -Wextra -pedantic main.cpp
    main.cpp:10:18: error: use of undeclared identifier 'foo'
        void bar() { foo(); }
                     ^
    main.cpp:11:3: warning: no newline at end of file [-Wnewline-eof]


Explication: `Derive<X>` connaîtra le contenu de `Base<X>`
quand `Base<X>` sera instancié,
donc quand `Derive<X>` sera lui-même instancié
(pas lors du parsing de `Derive<X>`)

```cpp
template <int X>
struct Base {
   void foo() { }
};

template <>
struct Base<42> {    // spécialisation de Base<X>
   void rien() { }   // pas de fonction foo()
};

template <int X>
struct Derive : Base<X> {  // Et si X=42 ?
   void bar() { foo(); }   // D'où vient foo() ?
};
```


Correction en utilisant `this->`

```cpp
template <int X>
struct Base
{
    void foo() { }
};

template <int X>
struct Derive : Base<X>
{
    void bar() { this->foo(); }  // this->
};
```


Correction en utilisant `Base<X>::`

```cpp
template <int X>
struct Base
{
    void foo() { }
};

template <int X>
struct Derive : Base<X>
{
    void bar() { Base<X>::foo(); }  // Base<X>::
};
```


Correction en utilisant `using Base<X>::foo`

```cpp
template <int X>
struct Base
{
    void foo() { }
};

template <int X>
struct Derive : Base<X>
{
    using Base<X>::foo;    // using
    void bar() { foo(); }
};
```





and xor or and_eq bitand compl 
http://en.cppreference.com/w/cpp/language/operator_alternative







http://madebyevan.com/obscure-cpp-features/


https://www.youtube.com/watch?v=_wzc7a3McOs



  
Mini-features (petards mouilles) :
---------------
- template union wt/ ctor/dtor	:

truc marrant avec le return du main :).


- code sapin de Noël
- Bjarn livre bug
- ::std::vector<::std::string>
