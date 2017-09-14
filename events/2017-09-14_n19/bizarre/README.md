Vous avez dit bizarre ?
-----------------------

Copyright 2017 olibre &emsp; [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr)

[![le logo C++FRUG est consitué du drapeau de la francophonie avec C++ au centre](http://cpp-frug.github.io/images/Cpp-Francophonie.svg "Logo C++FRUG")](https://github.com/cpp-frug/cpp-frug.github.io/blob/master/images/Cpp-Francophonie.svg)

* Reveal [cppfrug.org/paris/events/2017-09-14_n19/bizarre/reveal.html](http://cppfrug.org/paris/events/2017-09-14_n19/bizarre/reveal.html)
* Jekyll [cppfrug.org/paris/events/2017-09-14_n19/bizarre](http://cpp-frug.github.io/paris/events/2017-09-14_n19/bizarre/)
* Source [github.com/cpp-frug/paris/events/2017-09-14_n19/bizarre](https://github.com/cpp-frug/paris/blob/master/events/2017-09-14_n19/bizarre/README.md)




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



http://coliru.stacked-crooked.com/a/0f60ac9f5bef835a


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
  std::cout << "one day is "<< day.count() <<" hours\n"
            << "1/2 hour is "<< halfhour.count() <<" hours\n"
            << "the answer is "<< answer(day.count()) <<'\n';
}
```



Trigraph `??-` -> `~`


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
  std::cout << "one day is "<< day.count() <<" hours\n"
            << "1/2 hour is "<< halfhour.count() <<" hours\n"
            << "the answer is "<< answer(day.count()) <<'\n';
}
```



Espacement


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
  std::cout << "one day is "<< day.count() <<" hours\n"
            << "1/2 hour is "<< halfhour.count() <<" hours\n"
            << "the answer is "<< answer(day.count()) <<'\n';
}
```



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
  std::cout << "one day is "<< day.count() <<" hours\n"
            << "1/2 hour is "<< halfhour.count() <<" hours\n"
            << "the answer is "<< answer(day.count()) <<'\n';
}
```


Complément à un *(ones' complement)*  `~1` -> `-2` (if signed)


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
  std::cout << "one day is "<< day.count() <<" hours\n"
            << "1/2 hour is "<< halfhour.count() <<" hours\n"
            << "the answer is "<< answer(day.count()) <<'\n';
}
```





```cpp
#include <iostream>

int main()
{
  auto x = ("C++", '2017');
  std::cout << x << std::endl;
}
```



La composition

              évaluation
              |
    auto x = ("C++", '2017');
                   | |
             virgule valeur

Pratique quand pour décomposer un variadic sans recursion :

```cpp
int _/*anonymous*/[] = (/*evaluation*/, 0)...;

template <typename ...T> void print_vars()
{
  int _/*anonymous*/[] = ((std::cout << T::var), 0)...; (void)_;
}
```





http://coliru.stacked-crooked.com/a/3a7d316dd41cb1b3

```cpp
#include <iostream>

template <bool B = true>
bool foo(bool b = B)
{
  return !!b??!??!!!b;
}

template <bool B = false>
bool bar(bool b = B)
{
  std::cout << !b??!??!!b;
}

int main()
{
  !foo()??!??!bar();
}
```


Trigraphs `??!` -> `|`



  
  
  
http://madebyevan.com/obscure-cpp-features/


https://www.youtube.com/watch?v=_wzc7a3McOs



  
Mini-features (petards mouilles) :
---------------
- Array / ptr arythmetic		: a[1] -> 1[a]							+ operator[] overload
- Ternary as lvalue				: (a == 0 ? a : b) = 1;
- URL in code					: label + comment
- scope-declared types 			: for(struct { int a; float b; } loop = { 1, 2 }; ...; ...) {
- template union wt/ ctor/dtor	:
- main return 0 by default		:

C'est plutot incomplet, par exemple je me rappel plus le truc marrant avec le return du main :).



std::optionnal<bool> var(false);

if (var && var == false)
   std::cout << "Lolz\n";
   
   
   
Il faut corriger le code ci-dessous pour satisfaire les compilos C++.

Pas besoin de fonctionnalités C++11 / C++14, c’est du bon vieux C++03.

 

 

template<typename T>

void myfunction( T& t )

{

    t.process<int>();

}

 

struct Myclass

{

    template<typename T>

    void process() { }

};

 

int main()

{

   Myclass myclass;

    myfunction<Myclass>(myclass);

}

 

 

 

Erreur GCC 5.1

 

 

> g++ -std=c++11 -Wall -Wextra -pedantic main.cpp

 

main.cpp: In function 'void myfunction(T&)':

main.cpp:11:15: error: expected primary-expression before 'int'

     t.process<int>();

               ^

main.cpp:11:15: error: expected ';' before 'int'

 

 

Erreur Clang 3.6

 

 

> clang++ -std=c++11 -Wall -Wextra -pedantic main.cpp

 

main.cpp:11:7: error: use 'template' keyword to treat 'process' as a dependent template name

    t.process<int>();

      ^

      template

1 error generated.










Cette nouvelle énigme tient en 5 lignes de code :

 

 

class Myclass {};

 

void foo (Myclass &) {}

 

Myclass bar() { return Myclass(); }

 

int main()             

{

  foo( bar() );

}

 

 

Et comme d’habitude, les compilos se plaignent L

 

GCC-5.1

 

> g++ -std=c++11 -Wall -Wextra -pedantic main.cpp

main.cpp: In function 'int main()':

main.cpp:9:11: error: invalid initialization of non-const reference of type 'Myclass&' from an rvalue of type 'Myclass'

   foo( bar() );

           ^

main.cpp:3:6: note:   initializing argument 1 of 'void foo(Myclass&)'

void foo (Myclass &) {}

      ^

 

 

Clang-3.6

 

> clang++ -std=c++11 -Wall -Wextra -pedantic main.cpp

main.cpp:9:3: error: no matching function for call to 'foo'

  foo( bar() );

  ^~~

main.cpp:3:6: note: candidate function not viable: expects an l-value for 1st argument

void foo (Myclass &) {}

     ^

1 error generated.

 

 

La question: Qu’est-ce que le C++ nous interdit de faire ici ?

 

Vous pouvez aussi essayer de trouver une correction.

(je connais trois solutions possibles, il y en a peut-être d’autres…)

 

Faites vos essais en utilisant gcc.godbolt.org (compilo en ligne).





L’erreur est d’essayer de transformer une R-Value en L-Value.

 

Le compilateur peut être trompé par l’utilisation d’un « setter chaîné » comme ceci :

  Myclass &setTheMember(int  val) { member = val; return *this; }

 

Il faut donc éviter ça si le compilateur le permet (compiler de préférence avec C++11), et utiliser l’écriture & et && en qualificateur de fonction.

 

#include <utility>

class Myclass {

public:

  Myclass &setTheMember(int val) { member = val; return *this; }

 

  Myclass &setTheMemberSafe(int val) & { member = val; return *this; }

  Myclass &&setTheMemberSafe(int val) && { member = val; return std::move(*this); }

 

  int member;

};

 

void foo (Myclass & c) {}

 

Myclass bar() { return Myclass(); }

 

int main()             

{

  Myclass obj {};

  obj.setTheMember(2);

 

  foo( bar().setTheMember(1) );

  foo( bar().setTheMemberSafe(1) ); // ERREUR (COOL !)

}




Bravo à Sikirou et Armel pour avoir trouvé des réponses à la question.

Merci à Docteur Bakic et Frank pour leurs solutions.

 

Rappel du problème :

 

struct Myclass {};

 

void foo(Myclass &) {}

 

Myclass bar() { return Myclass(); }

 

int main()             

{             //compiler errors:

  foo(bar()); //CLANG: no matching function for call to 'foo'

}             //GCC: invalid initialization of non-const reference of type 'Myclass&' from an rvalue of type 'Myclass'

 

 

Rappel de la question :

Qu’est-ce que le C++ nous interdit de faire ici ?

 

Réponse rapide :

Le standard nous empêche de faire des bêtises :
Eviter de modifier une objet temporaire qui va tout de suite mourir.

 

Explications :

1.       La fonction foo() est appelée avec comme paramètre le retour de la fonction bar()
c’est une unnamed variable (ou anonymous variable).

2.       Comme sa durée de vie s’arrête avec la fin de l’appel de foo(),
c’est aussi un temporary object (certains préfèrent dire une temporary value).

3.       Mais foo(Myclass&) attend un objet modifiable.
(même s’il n’en fait rien, cet objet doit être modifiable.)

4.       Donc il n’y a pas d’intérêt à donner un objet temporaire à une fonction qui va le modifier.

 

Sikirou nous rappelle la parole de Scott Meyers dans le verset 19 de la sourate More Effective C++ 
(je me suis permis de blasphémer simplifier un peu)

Consider this function:

// changes all chars in str to upper case

void uppercasify( std::string& str );

In the character-counting example, a char array passed to uppercasify() fails: 

char title[] = "Effective C++";

uppercasify(             title  );    // error #1
uppercasify( std::string(title) );    // error #2

 

error #1: No temporary is created to make the call succeed. Why not?

Suppose a temporary were created (the error #2). Then the temporary would be passed to uppercasify(), which would modify the temporary so its characters were in upper case. But the actual argument to the function call — title — would not be affected; only the temporary std::string object generated from title would be changed.

Surely this is not what the programmer intended. That programmer passed title to uppercasify(), and that programmer expected title to be modified.

Implicit type conversion for references-to-non-const objects, then, would allow temporary objects to be changed when programmers expected non-temporary objects to be modified. That's why the language prohibits the generation of temporaries for non-const reference parameters. Reference-to-const parameters don't suffer from this problem, because such parameters, by virtue of being const, can't be changed.

Compiler le code sur Coliru => http://coliru.stacked-crooked.com/a/f324de25c709cb0e

 

Bon, cela n’empêche pas de tricher si on repère une fonction retournant une référence :

 

#include <utility>     // std::move

 

struct Myclass

{

   Myclass &  truc() { return           *this;  }

   Myclass && toto() { return std::move(*this); }

};

 

void foo(Myclass &) {}

 

Myclass bar() { return Myclass(); }

 

int main()             

{

  foo( bar().truc() );   // OK ??

//foo( bar().toto() );   // error

}

 

Lien coliru => http://coliru.stacked-crooked.com/a/aebff3189a99eaff

 

Heureusement, notre apôtre Armel se rappelle encore de l’enseignement de Saint Joel Falcou :

 

Avec C++11, protégez vos brebis égarées avec les ref-qualifier & et &&

http://en.cppreference.com/w/cpp/language/member_functions

 

#include <utility>     // std::move

 

struct Myclass

{

   Myclass &  truc() &  { return           *this;  } // non-const rvalue-references to temporary objects

   Myclass && toto() && { return std::move(*this); }

};

 

void foo(Myclass &) {}

 

Myclass bar() { return Myclass(); }

 

int main()             

{

  foo( bar().truc() );   // error

//foo( bar().toto() );   // error

}

 

Lien coliru => http://coliru.stacked-crooked.com/a/e1fd06609cdb2b43

 

Un fix C++03 

 

struct Myclass {};

 

void foo( const Myclass & ) {}

 

Myclass bar() { return Myclass(); }

 

int main()             

{

  foo( bar() );

}

 

http://coliru.stacked-crooked.com/a/314016237c79ad25

 

Un autre contournement en C++03 

 

struct Myclass {};

 

void foo( Myclass & ) {}

 

Myclass bar() { return Myclass(); }

 

int main()             

{

  Myclass mc;        // no temporary object

  foo( mc = bar() );   // OK C++03

}

 

http://coliru.stacked-crooked.com/a/bff5b2165e2e4994

 

Et la fameuse rvalue-reference (en C++11)

 

struct Myclass {};

 

void foo( Myclass && ) {}       // non-const rvalue-reference

 

Myclass bar() { return Myclass(); }

 

int main()             

{

  foo( bar() );                 // OK C++11

}

 

http://coliru.stacked-crooked.com/a/c6bd0c3a57282d8f

 

 

Vous pouvez constater que c’est plus plus facile quand même, non ?

 

Allez, je vous préparerai une troisième Enigme pour la semaine prochaine ;-)

Oliver










Que sont ‘pap_’ et ‘pape’ dans le code source ?

 

 

Code source

 

 

#include <iostream>

 

template<class T>

struct     Pap

{

  Pap()  { std::cout << "default ctor"         << std::endl; }

  Pap(T) { std::cout << "ctor : " << sizeof(T) << std::endl; }

};

 

template <typename T>

Pap<T>         pap_;

 

template <typename T>

Pap<T>         pape(0);

 

int main()

{

  auto t0 = pap_<short>;

  auto t2 = pape<short>;

  auto t1 = pape<double>;

  return 0;

}

 

 

Compilation

 

 

g++ -std=c++14 main.cpp

 

 

Sortie lors de l’exécution

 

 

default ctor

ctor : 2

ctor : 8




Code source

 

 

template<class T>

struct     Pap { };

 

template <typename T>

Pap<T>         pape;

 

 

Réponse

 

 

pape is a variable template    # C++14

 

 

Félicitations

 

 

Bravo à Pape et Docteur Bakic pour avoir trouvé rapidement.

Encore bravo à Pape, mais aussi à Alex pour le lancement d’AtomX  (et accessoirement à Gildas).

Bravo à tous ceux qui se sont grattés la tête pour comprendre cette nouvelle notation.

 

 

Références

 

 

·         wikipedia / C++14 Variable templates

·         cppreference / variable template

 

 

Mais à quoi ça sert ?

 

 

Avant, pour avoir des "variables paramétrables" on avait deux contournements :

·         Déclarer + Définir des membres static aux classes templates (*.hpp + *.cpp)

·         Définir des fonctions templates constexpr retournant la bonne valeur

 

 

Oui, mais à quoi ça sert d’avoir des "variables paramétrables" ?

 

 

à manger des brownies

 

 

C’est l’heure du gouter

 

 

Des brownies sont disponibles sur mon armoire

 

 

-- Oliver

01 70 48 27 79

06 31 82 83 84

 

 

Plus de lecture :

stackoverflow.com / C++14 Variable Templates: What is their purpose? Any usage example?






Code source     http://coliru.stacked-crooked.com/a/daca4a7b7d8ef906

 

 

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

 

int main()

{

}

 

 

Erreurs g++ 5.2.0

 

 

main.cpp: In member function 'void Derive<X>::bar()':

main.cpp:10:22: error: there are no arguments to 'foo' that depend on a template parameter, so a declaration of 'foo' must be available [-fpermissive]

     void bar() { foo(); }

                      ^

main.cpp:10:22: note: (if you use '-fpermissive', G++ will accept your code, but allowing the use of an undeclared name is deprecated)

 

 

Erreurs clang++ 3.6.0

 

 

main.cpp:10:18: error: use of undeclared identifier 'foo'

    void bar() { foo(); }

                 ^

1 error generated.

 

 

Question

 

 

Pourquoi le standard C++ empêche une classe template d’utiliser une fonction de sa classe mère template ?

 

 

Récompense










omme Siki l’indique, Derive<X> ne connaîtra le contenu de Base<X> que quand ce dernier sera instancié, donc quand Derive<X> sera lui-même instancié.

 

                http://coliru.stacked-crooked.com/a/25ffa8aa92fb8962

 

template <int X>

struct Base

{

   void foo() { }

};

 

template <>                    // spécialisation de Base<X>

struct Base<42>

{

   void foobar() { }           // la function foo() n’existe plus !

};

 

template <int X>

struct Derive : Base<X>

{

   void bar() { this->foo(); } // Derive<X> pourrait être spécialisé avec X=42

};                             // mais Base<42> ne contient pas de fonction foo()

 

int main()

{

   Derive<41> d41;

   d41.bar();                  // correct

 

   Derive<42> d42;

   d42.bar();                  // erreur

}

 

 

g++ 5.2.0

 

main.cpp: In instantiation of 'void Derive<X>::bar() [with int X = 42]':

main.cpp:25:12:   required from here

main.cpp:16:17: error: 'struct Derive<42>' has no member named 'foo'

    void bar() { this->foo(); } // Derive<X> pourrait être spécialisé avec X=42

                 ^

 

 

clang++ 3.6.0

 

main.cpp:16:23: error: no member named 'foo' in 'Derive<42>'

   void bar() { this->foo(); } // Derive<X> pourrait être spécialisé avec X=42

                ~~~~  ^

main.cpp:25:8: note: in instantiation of member function 'Derive<42>::bar' requested here

   d42.bar();                  // erreur

       ^

1 error generated.

 

 

Les  différentes solutions

 

 

template <int X>

struct Derive : Base<X>

{

    void bar() { this->foo(); }

};

 

 

 

template <int X>

struct Derive : Base<X>

{

    void bar() { Base<X>::foo(); }

};

 

 

 

template <int X>

struct Derive : Base<X>

{

    using Base<X>::foo;

    void bar() { foo(); }

};




and xor or and_eq bitand compl 
http://en.cppreference.com/w/cpp/language/operator_alternative







