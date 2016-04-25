URL|     http://linuxfr.org/news/douzieme-rencontre-parisienne-c-mercredi-27-avril-2016
---|------
Title|   Douzième rencontre parisienne C++ mercredi 27 avril 2016
Authors| Oliver H, Benoît Sibaud, ZeroHeure et tankey
Date|    2016-04-21T22:57:19+02:00
License| CC by-sa
Tags|    c++17, c++ et infos_locales
Score|   10


L'association C++FRUG organise la douzième rencontre parisienne **C++ Francophone** avec pour nom de code : `decltype(new event)`.
-----------------

* Mercredi 27 avril 2016 de 19:00 à 21:30&nbsp;;
* [43 Rue Beaubourg, Paris](http://www.openstreetmap.org/?mlat=48.86&amp;mlon=2.354#map=19/48.86/2.354), locaux de Mobiskill Partner&nbsp;;
* **Métros** Rambuteau (ligne 11) et Châtelet - Les Halles (RER A, B, D et ligne 4)  --  **Bus** [29, 38, 47, 75, N12, N13, N14 et N23](http://www.vianavigo.com/fr/itineraire-plan-de-quartier/#id=&proximity=43+rue+Beaubourg%2C+Paris&proximityType=Address&proximityCity=Paris&proximityExternalCode=ADDRESS32611&proximityCityCode=75000&proximityCoordX=&proximityCoordY=&spcar=%C3%A2&hit=1&hat=1&L=0&submitSearchProximity=&ajid=/stif_web_carto/comp/proximity/search.html_)  --  **Station vélib** [n°3010](http://www.velib.paris/Plan/Trouver-une-station/%28id%29/3010).

Horaires | Programme
------|----------
19:00 | Accueil
19:30 | Présentations éclairs *(Lightning talks)*
20:00 | Pause dinatoire, pizzas et bières offertes par Mobiskill Partner
20:30 | Révolution des `<algorithme>` en C++17
21:15 | Informations générales et fin de la rencontre

----

* [Meetup C++ FRUG #12](http://www.meetup.com/User-Group-Cpp-Francophone/events/230392153/)
* [Dépêche C++ FRUG #11](http://linuxfr.org/news/onzieme-rencontre-c-francophone-jeudi-31-mars-2016-a-paris)
* [Dépêche C++ FRUG #10](http://linuxfr.org/news/dixieme-rencontre-c-francophone-jeudi-21-janvier-2016-paris-chatelet-les-halles)
* [Site officiel du Standard C++](https://isocpp.org/)
* [Dépôts Git du Standard C++](https://github.com/cplusplus)
* [Événement dans l'Agenda du Libre](http://www.agendadulibre.org/events/11228)

----

![logo C++ Francophonie, licence CC0](http://cpp-frug.github.io/images/Cpp-Francophonie.svg)


Joël, le joyeux organisateur
----------------------------

[Joël Falcou](https://www.lri.fr/membre.php?mb=1146) organise depuis 2013 les rencontres parisiennes du *Groupe des Utilisateurs C++ Francophone* (abrégé en anglais *C++ FRUG* en clin d'œil à nous les [*Frogs*](https://fr.wiktionary.org/wiki/Frog)).


Dans la vie, [Joël](https://fr.linkedin.com/in/jfalcou) est maître de conférences [LRI](https://fr.wikipedia.org/wiki/Laboratoire_de_recherche_en_informatique) et [Polytech Paris-Sud](https://fr.wikipedia.org/wiki/%C3%89cole_polytechnique_de_l'universit%C3%A9_Paris-Sud). Joël assure bénévolement la [maintenance de projets libres comme des parties de Boost](http://www.boost.org/doc/libs/1_60_0/libs/predef/doc/html/index.html). Joël est également [membre bénévole du comité de standardisation ISO C++](https://isocpp.org/blog/2014/05/n4035).


![Joël anime Questions pour un Champion++](https://upload.wikimedia.org/wikipedia/commons/d/dc/20160121_CppFRUG_Joel_Falcou_CppQuiz_2.jpg)



Présentations éclairs *(Lightning talks)*
-----------------------------------------

Loïc Joly présente deux outils autour du C++, 


- Les [*raw string litterals*](http://en.cppreference.com/w/cpp/language/string_literal) et comment les remanier (*refactoring*)

```c++
const char* ma_chaine_de_caracteres = R"nesaffichepas(
Salut
les "passionnés" du C++
)nesaffichepas";
```

- Un visualiseur interactif d'arbre syntaxique basé sur Clang 

Joël Falcou présente quelques bonnes pratiques en C++ moderne 

- Trucs et astuces
- Détourner les variadiques à son profit


Révolution des `<algorithme>` en C++17
--------------------------------------


Thomas Petit présente les avancées du comité de normalisation C++17 (SG9) a propos des [`<algorithm>`](http://en.cppreference.com/w/cpp/header/algorithm) -- *Ranges TS : `view::transform<algorithm>`*.


Les `<algorithm>` de la STL sont mal aimés : difficilement composables, encombrés d'une syntaxe pénible, ils n'ont jamais réussi à convaincre et vivotent dans l'ombre des conteneurs. Mais récemment le comité de normalisation C++ (SG9) sous l'impulsion d'Eric Niebler a annoncé une série de TS (*Technical Specification*) qui devrait les remettre sur le devant de la scène.

Le premier TS, pas encore publié, mais dont le brouillon (*draft*) est très avancé, va revisiter les algorithmes existant pour en simplifier massivement l'utilisation. En introduisant de nouvelles surcharges acceptant les *ranges* (https://github.com/ericniebler/range-v3/).

Les infâmes `begin()`/`end()` que vomissent les codes utilisant fortement les `<algorithm>` ne seront bientôt plus qu'un lointain souvenir. L'arrivé des [Concepts](http://en.cppreference.com/w/cpp/language/constraints), ainsi que de nouvelles fonctionnalités comme les [Callables](http://en.cppreference.com/w/cpp/concept/Callable) et les Projections, vont eux aussi participer à la cure de simplification qui attend `<algorithm>`.

Le deuxième TS, en préparation, s'annonce encore plus révolutionnaire. En introduisant les *View*, la STL devrait se doter d'une nouvelle classe d'algorithme [paresseux (*lazy*)](https://fr.wikipedia.org/wiki/%C3%89valuation_paresseuse), non-mutable et composable permettant une écriture fonctionnelle merveilleusement concise et malléable.  



Historique des rencontres *C++ francophones*
-------------------------------------------

Profitons de cette dépêche pour faire un point sur les rencontres C++ francophones.


Traditionnellement les développeurs C++ n'étaient pas très motivés pour se réunir en association comme pour d'autres langages de programmation comme Perl, Python, Ada, PHP.
  

Mais en 2011, les développeurs C++ se sont pris une claque. Du moins, ceux qui ont compris la portée des révolutions apportées dans le nouveau standard [C++11](https://fr.wikipedia.org/wiki/C%2B%2B11) qui tranche avec l’encéphalogramme plat auquel nous étions habitués depuis les années 90 !

C'est ainsi que de partout dans le monde les passionnés du C++ se sont mis à avoir de plus en plus envie de se rencontrer pour partager leur enthousiasme et parfois leurs incompréhensions...


La communauté C++ francophone n'a pas échappé à ce phénomène et de nombreuses rencontres C++ se produisent depuis :   



Date      | Lieu      | Sujet
----------|-----------|------
2013-06-05|Paris      |[Qt on mobile](http://www.meetup.com/User-Group-Cpp-Francophone/events/120838202/)
2014-03-11|Lyon       |[C++ et Web: la croisée des chemins](http://humantalks.com/talks/363-c-et-web-la-croisee-des-chemins)
2014-03-13|Lyon       |[Le C++ évolue, et vous ?](http://www.meetup.com/fr-FR/LyonCPP/events/168296962/)
2014-04-22|Lyon       |[Rencontre C++](http://www.meetup.com/fr-FR/LyonCPP/events/175920152/)
2014-05-23|Paris      |[C++ FRUG #3 - En faire ++ avec C++](http://www.meetup.com/User-Group-Cpp-Francophone/events/177106822/)
2014-10-02|Paris      |[C++ FRUG #4 - C++ & Python](http://www.meetup.com/User-Group-Cpp-Francophone/events/181945092/)
2014-10-21|Montpellier|[Rencontre C++](http://www.meetup.com/fr-FR/Montpellier-CPP/events/207878182/)
2014-11-25|Montpellier|[Meetup C++ novembre](http://www.meetup.com/fr-FR/Montpellier-CPP/events/215049692/)
2014-12-16|Montpellier|[Rencontre C++ décembre](http://www.meetup.com/fr-FR/Montpellier-CPP/events/219024139/)
2014-12-18|Paris      |[C++ FRUG #5 - L'asynchronisme en deux talks](http://www.meetup.com/User-Group-Cpp-Francophone/events/218740271/)
2015-03-05|Paris      |[C++ FRUG #6 - La métaprogrammation, non non ca sert en vrai](http://www.meetup.com/User-Group-Cpp-Francophone/events/220602373/)
2015-03-17|Montpellier|[Rencontre C++ mars](http://www.meetup.com/fr-FR/Montpellier-CPP/events/220718755/)
2015-04-28|Paris      |[C++ FRUG #7 - Nuts & Bolt](http://www.meetup.com/User-Group-Cpp-Francophone/events/221811241/)
2015-06-18|Paris      |[C++ FRUG #8 - Nuts & Bolts II - Le retour](http://www.meetup.com/User-Group-Cpp-Francophone/events/223101208/)
2015-11-24|Montpellier|[Rencontre C++](http://www.meetup.com/fr-FR/Montpellier-CPP/events/226573490/)
2015-12-10|Paris      |[C++ FRUG #9 - Not Dead Yet !](http://www.meetup.com/User-Group-Cpp-Francophone/events/226963782/)
2016-01-21|Paris      |[C++ FRUG #10 - `import <new_blood>`](http://www.meetup.com/User-Group-Cpp-Francophone/events/227761739/)
2016-03-18|Marseille  |[Première rencontre: lancement du groupe](http://www.meetup.com/fr-FR/Marseille-Marseille-C-User-Group/events/229405969/)
2016-03-31|Paris      |[C++ FRUG #11 - `std::move(meetup)`](http://www.meetup.com/User-Group-Cpp-Francophone/events/229508095/)
2016-04-19|Montpellier|[Rencontre C++](http://www.meetup.com/fr-FR/Montpellier-CPP/events/230050042/)
2016-04-27|Paris      |[C++ FRUG #12 - `decltype(new event)`](http://www.meetup.com/User-Group-Cpp-Francophone/events/230392153/)

Les [rencontres C++ parisiennes sont classées au sixième rang](http://www.meetup.com/topics/c-programming/) au niveau mondial dans la catégorie *"C++ Programming"* sur le site meetup.com (avec 489 *c++ dev* lors de la rédaction de cette dépêche).

Anciennes présentations disponibles en ligne
--------------------------------------------


Avec un peu de web-spéléo-archéologie, on trouve des traces d'anciennes présentations.


* Supports de présentation&nbsp;:
    * [Montpellier](http://cpp-frug.github.io/montpellier/)&nbsp;;
    * [Paris](http://fr.slideshare.net/cppfrug/)&nbsp;;
    * [Lyon](http://lyon.francecpp.org/).
* Captations audiovisuelles&nbsp;:
    * [Canal C++FRUG sur dailymotion](http://www.dailymotion.com/cppfrug)&nbsp;;
    * [Vidéos par Guillaume Belz](https://www.youtube.com/user/GuillaumeBelz)&nbsp;;
    * [Vidéos par NumScale](https://www.youtube.com/user/NumScale).


Merci de proposer d'autres liens dans les commentaires ;-)

Genèse de l'association C++FRUG
-------------------------------

Ce besoin de partager les nouveautés du C++ a pour conséquence la création d'associations C++ dans plusieurs pays. Et c'est aussi le cas de la communauté francophone dont les plus motivés ont [proposé](https://groups.google.com/forum/#!msg/cpp-frug/A61eq1wPsZ8/lNxR4lMIbFEJ) une association C++FRUG.

L'association se veut trans-mondiale et aider toute rencontre C++ dans la francophonie. Un objectif important est de réduire notre dépendance au bon vouloir des sites non-libres. Un autre objectif est de conserver en accès libre les supports de présentations et les captations audiovisuelles.

Par contre, le site web C++FRUG est encore en cours de rédaction et avance selon les disponibilités des plus motivés... (faut dire que les dévs C++ ne sont pas forcément des flèches en développement web).

Inscription sur meetup.com
--------------------------


L'inscription sur le site meetup.com n'est pas obligatoire, mais cela permet de :


* Commander suffisamment de pizza et de bières sans trop en commander&nbsp;
* Choisir/préparer la salle et installer le nombre de chaises nécessaires&nbsp;
* Suivre dans le temps les statistiques du nombre d'inscrits&nbsp;
* Les inscrits peuvent donner leur impression et indiquer ce qui peut être amélioré&nbsp;
* Retrouver une personne rencontrée pour, par exemple, continuer une discussion…


Ceux qui n'ont pas une adresse de courriel anonyme ou qui ne veulent pas dévoiler leur identité au site meetup.com peuvent venir sans s'y inscrire. Nous espérons que cela représente une petite minorité afin de ne pas avoir de surprise dans l'organisation de l'événement ;-)
