C++FRUG #17 is No C++17
-----------------------

> **Jeudi 18 mai** &emsp; &emsp; &emsp; &emsp; &emsp; <sup><small>(No = Not only)</small></sup>  
> &emsp; 19:15 &nbsp; Présentation de notre sponsor  
> &emsp; 19:30 &nbsp; [**Actualités**](./news)  
> &emsp; 20:00 &nbsp; **Le C++ à la rescousse du Raspberry Pi** - Ludo  
> &emsp; 20:30 &nbsp; Pizza  
> &emsp; 21:00 &nbsp; [**Nouvelle approche de Mocking**](https://axanux.net/mock.html) - Philippe  
> &emsp; 21:30 &nbsp; [**C++17 en images**](./Cpp17-en-images) - Oliver  

[![le logo C++FRUG est consitué du drapeau de la francophonie avec C++ au centre](http://cpp-frug.github.io/images/Cpp-Francophonie.svg "Logo C++FRUG")](https://github.com/cpp-frug/cpp-frug.github.io/blob/master/images/Cpp-Francophonie.svg)  
[reveal](http://cppfrug.org/paris/events/2017-04-26_n17/news/reveal.html) &emsp;  [**cppfrug.org**](http://cppfrug.org/paris/events/2017-04-26_n17/news) &emsp; [github.com](https://github.com/cpp-frug/paris/blob/master/events/2017-04-26_n17/news/README.md) &emsp; [meetup.com](https://www.meetup.com/fr-FR/User-Group-Cpp-Francophone/events/239663039/)  &emsp; **Communauté C++ francophone**


Actualités C++
==============


C++Now
======

15–20 mai 2017

Aspen, Colorado, USA


![Aspen en mois de juin](https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/Aspen_CO_downton.jpg/1024px-Aspen_CO_downton.jpg)


C++17
=====

21 mars 2017

Le comité a achevé son travail sur le C++17.  
ISO en train de finaliser la mise en page...

Brouillon : [wg21.link/n4659](http://wg21.link/n4659)


C++20
=====

10 Juillet 2017

Toronto, Canada

Le comité reprend un nouveau cycle de trois ans.



GCC
===

2 mai 2017  
[**GCC 7.1**](https://gcc.gnu.org/gcc-7/)

[Prend en charge C++17](http://en.cppreference.com/w/cpp/compiler_support) sauf le  
*Elementary string conversions* [P0067](http://wg21.link/p0067)


Clang
=====

13 mars 2017  
**Clang 4.0.0**

[Prend en charge C++17](http://en.cppreference.com/w/cpp/compiler_support) sauf le  
*Elementary string conversions* [P0067](http://wg21.link/p0067)  
et le *Splicing Maps and Sets* [P0083](http://wg21.link/p0083)


Clang
=====

&nbsp;

* [releases.llvm.org/4.0.0/tools/clang/docs](http://releases.llvm.org/4.0.0/tools/clang/docs/)  
  `clang++`, `clang-check`, `clang-format`...

* [releases.llvm.org/4.0.0/tools/clang/tools/extra/docs](http://releases.llvm.org/4.0.0/tools/clang/tools/extra/docs/)  
  `clang-tidy`, `clang-include-fixer`...


Clang new compilation flag
--------------------------

&nbsp;

> **`-fsave-optimization-record`**  
> &emsp; Generate a YAML optimization record file
>
> **`-foptimization-record-file=<value>`**  
> &emsp; Specify the file name of any  
> &emsp; generated YAML optimization record


**`-fsave-optimization-record`**

Test on [gcc.godbolt.org](http://gcc.godbolt.org)

```cpp
int square (int num) {
    return num * num;
}
```


### La multiplication est une suite de sommes

```cpp
int square (int num) {
    int result = 0;
    for (int i = 0; i < num; ++i)
        result += num;
    return result;
}
```


### Fonction `sum()` dans la boucle `for`

```cpp
int sum (int a, int b) {
    return a + b;
}

int square (int num) {
    int result = 0;
    for (int i = 0; i < num; ++i)
        result += sum (result, num);
    return result;
}
```


Les compilateurs C++ en lignes
------------------------------

* [gcc.godbolt.org](http://gcc.godbolt.org/) de [Matt Godbolt](https://github.com/mattgodbolt) basé sur [GCC Explorer](https://github.com/mattgodbolt/gcc-explorer)
* [coliru.stacked-crooked.com](http://coliru.stacked-crooked.com/a/71c3371692723de1)  
  <small>(remplacer `g++` par `clang++`)</small>
* [cpp.sh](http://www.cpp.sh/22av)
* [codepad.org](http://codepad.org/XYy3ZoXw)
* [ideone.com](http://ideone.com/cDnejN)
* [rextester.com](http://rextester.com/XYSX22503)
* [tutorialspoint.com/compile_cpp11_online.php](https://goo.gl/9rqwoy)
* [repl.it](https://repl.it/DfuG/1)
* [webcompiler.cloudapp.net](http://webcompiler.cloudapp.net/)



Elle est libre et open
----------------------

Mars 2016 &emsp; **C++FRUG #11**  
&emsp; &emsp; &emsp; Quentin présente ses coroutines
&emsp; &emsp; &emsp; asynchrones bientôt libérées...

Décembre 2016 &emsp; Docker rachète Infinit...

Février 2017 &emsp; [github.com/infinit/elle](https://github.com/infinit/elle)

[Promesse tenue.](http://blog.infinit.sh/elle-our-c-core-library-is-now-open-source/)  
Merci Julien, Quentin et toute l'équipe &emsp; :-D  
![Logo de Elle](https://raw.githubusercontent.com/infinit/elle/master/docs/static_files/elle_logotype@2x.png)



Évolutions cppfrug.org
----------------------

* Actuellement [Jekhyll](https://github.com/jekyll/jekyll/blob/master/README.markdown)  
  <small>(partiel)</small>  

* Peut-être passage à [Hugo](https://github.com/spf13/hugo)...  
  <small>(tests en cours par Aurelien Regat-Barrel)</small>  

* Toujours avec [GitHub Pages](https://pages.github.com/)  
  <small>(site web statique)</small>


Quel chat en ligne ?
--------------------

* [jb3](https://github.com/devnewton/jb3)  

* [Slack](https://isocpp.org/blog/2016/08/cpp-slack-group)  

* [Mattermost](https://github.com/mattermost/platform/blob/master/README.md)  

* [Rocket.Chat](https://github.com/RocketChat/Rocket.Chat/blob/develop/README.md)  

* ...


Zeste De Savoir
---------------

Rejoindre [ZesteDeSavoir.com](https://zestedesavoir.com/) ?  
<small>(créé par des anciens du SiteDuZéro)</small>


Vidéo des Meetups C++
---------------------

Merci à **Nicolas Hessling** pour son matos,  
sa captation audio-visuelle  
et son montage vidéo multicam.

Nicolas est également spécialiste de la numérisation  
des vieilles cassettes VHS, PAL, SECAM, Hi-8...

N'hésitez pas à lui commander des travaux &nbsp; ;-)


Chaînes YouTube & DailyMotion
-----------------------------

C'est Guss, un jeune développeur fou C++,  
fanatique des template, qui va s'en occuper.

Guss est actuellement en convalescance et  
attend impatiemment les vidéo d'aujourd'hui.  
Souhaitons lui un bon rétablissement ;-)
