
C++FRUG #17 is No C++17
=======================
<sup>&emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; (No = Not only)</sup>

> **Jeudi 18 mai**  
> &emsp; 19:00 &nbsp; Accueil  
> &emsp; 19:15 &nbsp; Présentation de notre sponsor  
> &emsp; 19:30 &nbsp; **Actualités sur le C++**  
> &emsp; 20:00 &nbsp; **La puissance de son Raspberry Pi 3 avec le C++** &nbsp; Ludo  
> &emsp; 20:30 &nbsp; Pizza  
> &emsp; 21:00 &nbsp; **Nouvelle approche de Mocking en C++** &nbsp; Philippe  
> &emsp; 21:30 &nbsp; **C++17 en images** &nbsp; Oliver  
> &emsp; 22:00 &nbsp; Rangement de la salle

[meetup.com](https://www.meetup.com/fr-FR/User-Group-Cpp-Francophone/events/239663039/) &emsp; [**cppfrug.org**](http://cppfrug.org/paris/events/2017-01-19_n14/) &emsp; [github.com](https://github.com/cpp-frug/paris/blob/master/events/2017-01-19_n14/README.md) [![le logo C++FRUG est consitué du drapeau de la francophonie avec C++ au centre](http://cpp-frug.github.io/images/Cpp-Francophonie.svg "Logo C++FRUG")](https://github.com/cpp-frug/cpp-frug.github.io/blob/master/images/Cpp-Francophonie.svg) **Communauté C++ francophone**


Actualités C++
==============


C++Now
======

15–20 mai 2017  
Aspen  
Colorado  
USA


![Aspen en mois de juin](https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/Aspen_CO_downton.jpg/1024px-Aspen_CO_downton.jpg)


C++17
=====

21 mars 2017  
Le comité a achevé son travail sur le C++17.  
L'institution ISO est en train de finaliser la mise en page.

Brouillon : [http://**wg21.link/n4659**](http://wg21.link/n4659)


C++20
=====

10 Juillet 2017  
Toronto (Canada)  
Le comité reprend un nouveau cycle pour travailler sur C++20.


GCC
===

2 mai 2017  
**GCC 7.1**

Prend en charge C++17 sauf le  
*Elementary string conversions* [P0067](http://wg21.link/p0067)

[gcc.gnu.org/gcc-7/](https://gcc.gnu.org/gcc-7/)  
[cppreference.com/w/cpp/compiler_support](http://en.cppreference.com/w/cpp/compiler_support)

Clang
=====

13 mars 2017  
**Clang 4.0.0**

Prend en charge C++17 sauf le  
*Elementary string conversions* [P0067](http://wg21.link/p0067)  
el le *Splicing Maps and Sets* [P0083](http://wg21.link/p0083)

[releases.llvm.org/4.0.0/tools/clang/docs](http://releases.llvm.org/4.0.0/tools/clang/docs/)  
[releases.llvm.org/4.0.0/tools/clang/tools/extra/docs](http://releases.llvm.org/4.0.0/tools/clang/tools/extra/docs/) (`clang-tidy`, `clang-include-fixer`...)


Clang new compilation flag
==========================

 `-fsave-optimization-record`
 -----------------------------

> `-fsave-optimization-record`
> 
> Generate a YAML optimization record file
>
> `-foptimization-record-file=<value>`
>
> Specify the file name of any generated YAML optimization record


Test `-fsave-optimization-record`
--------------------------------

[gcc.godbolt.org](http://gcc.godbolt.org)

```cpp
int square (int num) {
    return num * num;
}
```


La multiplication est une suite de sommes
-----------------------------------------

```cpp
int square (int num) {
    int result = 0;
    for (int i = 0; i < num; ++i)
        result += num;
    return result;
}
```

Fonction `sum()` dans la boucle `for`
-------------------------------------

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
    
* [gcc.godbolt.org](http://gcc.godbolt.org/#compilers:!((source:%27struct+MaClasse%0A{%0A++++template%3Cclass+T%3E%0A++++void+fait()+{+}%0A}%3B%0A%0Atemplate%3Cclass+T%3E%0Avoid+mafonction(T%26+t)%0A{%0A++++t.fait%3Cint%3E()%3B+//error:+expected+primary-expression+before+!%27int!%27%0A}%0A%0Aint+main()%0A{%0A++++MaClasse+maclasse%3B%0A++++mafonction(maclasse)%3B%0A}%27)),filterAsm:(commentOnly:!t,directives:!t,labels:!t),version:3) de [Matt Godbolt](https://github.com/mattgodbolt) propulsé par [GCC Explorer](https://github.com/mattgodbolt/gcc-explorer) sous licence [BSD-2-Clause](https://github.com/mattgodbolt/gcc-explorer/blob/master/LICENSE) ;
* [coliru.stacked-crooked.com](http://coliru.stacked-crooked.com/a/71c3371692723de1) (astuce : remplacer `g++` par `clang++`) ;
* [cpp.sh](http://www.cpp.sh/22av) ;
* [codepad.org](http://codepad.org/XYy3ZoXw) ;
* [ideone.com](http://ideone.com/cDnejN) ;
* [rextester.com](http://rextester.com/XYSX22503) ;
* [tutorialspoint.com/compile_cpp11_online.php](https://goo.gl/9rqwoy) ;
* [repl.it](https://repl.it/DfuG/1) ;
* [webcompiler.cloudapp.net](http://webcompiler.cloudapp.net/).


Évolutions cppfrug.org
======================

* Actuellement le site utilise partiellement [Jekhyll](https://github.com/jekyll/jekyll/blob/master/README.markdown)
* Peut-être un passage à [Hugo](https://github.com/spf13/hugo)... Tests en cours par Aurelien Regat-Barrel.
* Toujours avec [GitHub Pages](https://pages.github.com/) (site web statique)
* Quel chat en ligne ? [jb3](https://github.com/devnewton/jb3), [Slack](https://isocpp.org/blog/2016/08/cpp-slack-group), [Mattermost](https://github.com/mattermost/platform/blob/master/README.md), [Rocket.Chat](https://github.com/RocketChat/Rocket.Chat/blob/develop/README.md)...
* Enrichissement de [ZesteDeSavoir.com](https://zestedesavoir.com/) (créé par des anciens du SiteDuZéro)


Vidéo des Meetups C++
=====================

Merci à Nicolas Hessling, professionnel de la captation audio-visuelle (spéctacles, conférences...) et montage vidéo multicam. Nicolas est également spécialiste de la numérisation des vielles cassettes VHS, SECAM, Hi-8... N'hésitez pas à lui commander des travaux ;-)

C'est Guss, un jeune développeur fou C++, fanatique des template, qui va s'occuper des chaînes YouTube, DailyMotion... Guss est actuellement en convalescance et attend impatiemment les vidéo d'aujourd'hui. Souhaitons lui un bon rétablissement ;-)
