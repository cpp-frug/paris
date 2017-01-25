Articles C++17 sur LinuxFr.org
==============================

Copyright &emsp; Oliver H &emsp; 2017

[**CC BY-SA 4.0**](https://creativecommons.org/licenses/by-sa/4.0/deed.fr)

[![le logo C++FRUG est consitué du drapeau de la francophonie avec C++ au centre](http://cpp-frug.github.io/images/Cpp-Francophonie.svg "Logo C++FRUG")](https://github.com/cpp-frug/cpp-frug.github.io/blob/master/images/Cpp-Francophonie.svg)

[cppfrug.org / paris / events / 2017-01-19_n14 / LinuxFr.org](http://cpp-frug.github.io/paris/events/2017-01-19_n14/LinuxFr.org/)

[github.com / cpp-frug / paris / events / 2017-01-19_n14 / LinuxFr.org](https://github.com/cpp-frug/paris/blob/master/events/2017-01-19_n14/LinuxFr.org/README.md)


[LinuxFr.org](http://linuxfr.org/tags/c++17/public)
=============

* Rédaction collaborative en Markdown
* Licence libre ([CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr))
* Modérateurs sympas, pro et réactifs
* Grande audience francophone
* ~~Lecteurs C++~~ &nbsp; ~~Trolls~~ &nbsp; ~~Franglais~~

![Deux collègues content d'une nouvelle version C++17 mais qui ne sont pas au courant des dépêches C++17 sur LinuxFr.org qui leur permettrait de cerner les nouvelles fonctionnalités.](http://cpp-frug.github.io/materials/images/cpp-complexe-path.svg)


Succès des publications
=======================

* 25 juin 2016 &emsp; Le comité C++ clôture l'ajout des fonctionnalités au C++17
* 20 août 2016 &emsp; [**Les coulisses du standard C++**](http://linuxfr.org/news/les-coulisses-du-standard-cpp)
* 2 octobre 2016 &nbsp; [**C++17, Genèse d’une version mineure**](http://linuxfr.org/news/cpp17-genese-d-une-version-mineure)

[![Évolution du langage C++](https://cpp-frug.github.io/materials/images/cpp-evolution-path.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/cpp-evolution-original.svg)


Calendrier de l'Avent
=====================

> 01/12 &nbsp; [**C++17 fixe l’ordre d’évaluation des expressions**](http://linuxfr.org/news/cpp17-fixe-l-ordre-d-evaluation-des-expressions)  
> 02/12 &nbsp; [**C++17 indique la disponibilité des headers**](http://linuxfr.org/news/cpp17-indique-la-disponibilite-des-en-tetes-header)  
> 05/12 &nbsp; [**C++17 branche à la compilation**](http://linuxfr.org/news/cpp17-branche-a-la-compilation-if-constexpr)  
> 07/12 &nbsp; [**C++17 exprime la virgule flottante en hexadécimal**](http://linuxfr.org/news/cpp17-exprime-la-virgule-flottante-en-hexadecimal-et-offre-des-cadeaux-aux-lecteurs-de-linuxfr-org)  
> 11/12 &nbsp; [**C++ se court-circuite le constructeur de copie**](http://linuxfr.org/news/cpp-se-court-circuite-le-constructeur-de-copie)  
> 13/12 &nbsp; [**C++17 garantit le court-circuit de copie**](http://linuxfr.org/news/cpp17-garantit-le-court-circuit-de-copie-suite-de-la-precedente-depeche)


Bonnes résolutions 2017
=======================

Être plus nombreux, mieux répartir l'effort.

[![Une personne affolé prévient son collègue que LinuxFr.org s'est fait piraté. Son collègue vient constater l’attaque avec un site inondé de dépêches C++ et avoue que les dév. C++ sont trop balaises](https://cpp-frug.github.io/materials/images/linuxfr-ne-parle-que-de-cpp_copyright-OliverH-2016_CC-BY-SA-3.png)](https://github.com/cpp-frug/materials/blob/gh-pages/images/linuxfr-ne-parle-que-de-cpp_copyright-OliverH-2016_CC-BY-SA-3.png)


`github.com` / `cpp-frug`
-------------------------
    
* Les dépêches restent figées sur LinuxFr.org
* L'amélioration s'effectue sur le Git C++FRUG
* Idéal pour héberger les illustrations
* Montpellier, Paris (Aix, Marseille, Toulouse...)

![Logo GitHub social coding](http://securityaffairs.co/wordpress/wp-content/uploads/2015/03/github-social-coding.jpg)



C++17/20/23 dès aujourd'hui
---------------------------

Les [***feature testing macros***](http://en.cppreference.com/w/User:D41D8CD98F/feature_testing_macros) permettent d'écrire du code  
qui s'adapte aux fonctionnalités prises en charge   
par le compilateur et sa bibliotèque standard `std::`

```cpp
#ifdef __cpp_lib_experimental_filesystem
#include <filesystem>
void backup()
{
  std::filesystem::copy("file.txt","file.bak");
}
#else
void backup()
{
  /* ... */
}
#endif
```

* `__cpp_concept` (déjà pris en charge par GCC)
* `__cpp_lib_filesystem` (`_lib_` identifie une fonctionnalité de la `std::`)
* Correspond à la [date comme `2015'01`](en.cppreference.com/w/cpp/experimental/feature_test#Language_Features) selon la publication de la TS


Alternatives aux *feature testing macros*
----------------------------------------

* Macro `__cplusplus`  
  Valeurs `201103`, `201402` et bientôt `2017xx`  
  Ou bien `2011'03`, `2014'02` et `2017'00`  
  Juste bien pour détecter le flag `-std=c++14`  
  
* Macros [**Boost.Config**](http://www.boost.org/doc/libs/1_61_0/libs/config/doc/html/boost_config/boost_macro_reference.html)  

* [**`CMAKE_CXX_KNOWN_FEATURES`**](https://cmake.org/cmake/help/latest/prop_gbl/CMAKE_CXX_KNOWN_FEATURES.html)  
  CMake connait les fonctionnalités C++ du compilateur
        
    ```cmake
    target_compile_features(MyLib PRIVATE cxx_constexpr)
    ```
* Macro `__has_include`  


`__has_include`
---------------

> [**P0061**](https://wg21.link/p0061) ajoute la macro [**`__has_include()`**](http://en.cppreference.com/w/cpp/preprocessor/include)  
> pour vérifier la présence d'un *header* à la compilation.

```cpp
#ifdef __has_include
# if   __has_include(<filesystem>)
#            include <filesystem>
# elif __has_include(<experimental/filesystem>)
#            include <experimental/filesystem>
# elif __has_include(<boost/filesystem.hpp>)
#            include <boost/filesystem.hpp>
# else
#  error  Cannot find any 'filesystem' header
#else
# include <boost/filesystem.hpp>
#endif
```


Virgule flottante en hexadécimal
--------------------------------
    
[**P0245**](http://wg21.link/p0245) officialise les ***hexadecimal floating literals*** (C99, Java 5 2004)
    
```cpp
float  v = 0x'Baffe.bobo'p1f;
double w = 0x'C0DE'2017'1.cafe'p1;
``` 
    
[![Les Nerdettes s’entraînent pour le concours des littéraux hexadécimaux sur LinuxFr.org](https://cpp-frug.github.io/materials/images/nerdettes_litteral_hexa.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/nerdettes_litteral_hexa.svg)


Concours de jeux de mots
------------------------

[Attention, le concours se termine fin janvier !](http://linuxfr.org/news/attention-le-concours-de-jeux-de-mots-se-termine-fin-janvier-2017)

[![Les deux filles nerds discutent sur la manipulation des bits au grand bonheur des jeux de mots](https://cpp-frug.github.io/materials/images/nerd_jeux-de-mots.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/nerd_jeux-de-mots.svg)



`if constexpr`
-------------

> [**P0292**](https://wg21.link/p0292) simplifie la métaprogrammation  
> avec `static_if` ... `constexpr_if` ... `constexpr if` ...
  
```cpp
template <class T, class... R>
void fonction (const T& t, const R&... r)
{
  std::cout << t;    // Gère un argument
  if constexpr (sizeof...(r))
    fonction(r...);  // Gère le reste
  else
    std::cout << std::endl;
}
```


Variable `inline` ([P0386](http://wg21.link/p0386))
----------------------------------------------------

* Après les variables `template` (C++14), voici les variables `inline`
* Fin du [***One Definition Rule***](https://en.wikipedia.org/wiki/One_Definition_Rule) ?

[![Les deux filles nerds résolvent une erreur de link d'une variable membre static non définie en rajoutant inline](https://cpp-frug.github.io/materials/images/nerd_cpp17_variable_inline.svg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/nerd_cpp17_variable_inline.svg)


Structured bindings
-------------------

[P0217](https://wg21.link/p0217) apporte la **décomposition du retour de fonction**,  
mais limitée aux `std::tuple`, aux tableaux (comme `std::array`)  
et aux structures plates (comme `std::pair`).
    
```cpp
struct A
{
  int  a;
  bool b;
  char c;
};

A foo()
{
  return A{42, true, 'c'};
}

auto [ x, y, ignored ] = foo();
``` 
    
* Mieux que `std::tie` cantonné aux `std::tuple` et à `std::pair`
* Pas de `std::ignore`


`if(init;condition)` et `switch(init;condition)`
------------------------------------------------

Le TS [P0305](wg21.link/p0305) ajoute les *instructions de sélection avec initialiseur*  
comme pour `for( initialisation; condition; incrémentation )`.

```cpp
if (auto [it, inserted] = mySet.insert(value); inserted)
{
  foo(it);
}

switch (bool loop=true; loop)
{
  /* ... */
  loop = false;
  /* ... */
}
```


`auto x{42};` déduit comme `int x{42};`
-------------------------------------

[N3922](https://wg21.link/n3922) comble un trou sur les règles de déduction pour `auto` à partir des `{`listes d'initialisation`}`.
    
```cpp
auto a   {1};     //ok => int a{1};
auto b = {1};     //ok => std::initializer_list<int> b = {1};
    
auto c   {1, 2};  //KO car plus d'un élément
auto d = {1, 2};  //ok => std::initializer_list<int> d = {1, 2};
    
auto e   {1, 2.0}; //KO car plus d'un élément
auto f = {1, 2.0}; //KO car pas le même type (int et double)
``` 
    
[![Une écolière écrit une boucle for en C++17 pour régler sa punition d'écrire 100 fois "Je ne dois pas envoyer d'avion en papier"](http://cpp-frug.github.io/materials/images/cpp-ecole-primaire_copyright-Ziyue-OliverH-2016_CC-BY-SA-3_auto.jpg)](https://github.com/cpp-frug/materials/blob/gh-pages/images/README.md#c17-sauve-une-%C3%A9coli%C3%A8re)


`typename` pour les paramètres `template template`
-------------------------------------------------

[N4051](https://wg21.link/n4051) autorise enfin `typename` pour les paramètres `template template`

```cpp
template<template<typename> class    T> class Cpp98;
template<template<typename> typename T> class Cpp17;
```


C++ without `class`
-------------------

Le nom originel du C++ était ***C with `class`***.  
Avec [N4051](https://wg21.link/n4051), le C++17 devient le ***C++ without `class`***.

```cpp
template <class T, template<class> C>
class AvecClass : C<T>
{
    int v;
};
    
template <typename T, template<typename> C>
struct SansClass : private C<T>
{
private:
    int v;
};
```



Suppression des trigraphes
--------------------------

C++11 aurait pu rendre les trigraphes obsolètes.  
Mais quelques membres du comité C++ s'y étaient opposés (IBM, Bloomberg).  
Pour C++17, les membres ont finalement voté [N4086](https://wg21.link/n4086)  
qui les supprime directement sans passer par l'étape *deprecated*.

```cpp
/??/
/??/ Avec trigraphes
??=include <iostream>
int main (int argc, char *argv??(??)) ??< 
  const char txt??(??) = "J'aime le C++17??/0";
  std::cout << txt << std::endl;
??>
``` 
    
```cpp
/\
/\ Sans trigraphe
#include <iostream>
int main (int argc, char *argv[]) {
  const char txt[] = "J'aime le C++17";
  std::cout << txt << std::endl;
}
```


Apple ][ (1977-1988)
--------------------

Aucune touche ne dispose du symbole *accolade* ou *crochet*.

[![Image du clavier de l'Apple II qui n'a pas de touche avec accolade ou crochet](https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Apple_II-IMG_7073.jpg/1024px-Apple_II-IMG_7073.jpg)](https://commons.wikimedia.org/wiki/File:Apple_II-IMG_7073.jpg)


BBC Master (1986-1994)
----------------------

Le clavier intégré du micro-ordinateur 8 bits BBC Master de Acorn indique les *crochets* mais pas les *accolades*.

[![Clavier intégré du micro-ordinateur BBC Master de Acorn](https://upload.wikimedia.org/wikipedia/commons/6/60/Acorn_BBC_Master_Series.jpg "Micro-ordinateur BBC Master de Acorn (8-bit avec clavier intégré) fabriqué entre 1986 et 1994")](https://en.wikipedia.org/wiki/BBC_Master)



Suppression du mot-clé `register`
--------------------------------

> Historiquement, le mot-clé [`register`](http://en.cppreference.com/w/c/keyword/register) aidait le compilateur à identifier la variable à conserver dans un registre du processeur (les compilateurs n'étaient pas très futés...)
>
> **C++11** : `register` est déprécié, mais conservé pour la compatibilité avec le C, en particulier avec les arguments des fonctions. Pourtant, son usage n’est pas pertinent en C++ :  redondant avec d’autres fonctionnalités et ses restrictions ne peuvent être facilement transcrites en C++.
>
> **C++17** : Plutôt que d’essayer de résoudre les différences avec le C, le standard fait de `register` un **mot-clé réservé non utilisé**.


Booléen non incrémentable
-------------------------

`bool` avait été conçu pour ne pas trop casser le vieux code C/C++

```c
#define bool int
```

* décrémentation interdite
* incrémentation autorisée

```cpp
bool b = foo();
--b; // Erreur depuis C++98
++b; // Erreur depuis C++17
```
