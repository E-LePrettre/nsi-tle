**Chap 07 : Le HTML**

<a name="_hlk38577387"></a>**Table des matières**

[1.	Historique	1](#_toc100764808)

[2.	Le fonctionnement des sites web	2](#_toc100764809)

[2.1.	Les navigateurs utilisés	2](#_toc100764810)

[2.2.	Les langages	2](#_toc100764811)

[2.3.	Les éditeurs et les logiciels conseillés	2](#_toc100764812)

[3.	Le langage HTML5	3](#_toc100764813)

[3.1.	Page web en HTML	3](#_toc100764814)

[3.2.	Les balises	3](#_toc100764815)

[3.2.1.	Les balises en paires	3](#_toc100764816)

[3.2.2.	Les balises orphelines	3](#_toc100764817)

[3.3.	Les attributs	3](#_toc100764818)

[3.4.	Structure de base d’une page HTML5	3](#_toc100764819)

[4.	L’organisation d’une page HTML5	4](#_toc100764820)

[4.1.	Les paragraphes	4](#_toc100764821)

[4.2.	La balise retour à la ligne	4](#_toc100764822)

[4.3.	Les titres	4](#_toc100764823)

[4.4.	Mettre en valeur	6](#_toc100764824)

[4.5.	Les listes	8](#_toc100764825)

[4.6.	Les liens hypertexte	8](#_toc100764826)

[4.6.1.	Les liens absolus	8](#_toc100764827)

[4.6.2.	Lien relatif vers une page d’un même dossier	9](#_toc100764828)

[4.6.3.	Lien relatif vers une page située dans un dossier fils	9](#_toc100764829)

[4.6.4.	Lien relatif vers une page située dans un dossier parent	9](#_toc100764830)

[4.6.5.	Lien vers une ancre sur une même page	9](#_toc100764831)

[4.6.6.	Lien vers une ancre sur une autre page	10](#_toc100764832)

[4.6.7.	Lien affichant une infobulle	10](#_toc100764833)

[4.6.8.	Lien qui ouvre une nouvelle fenêtre	10](#_toc100764834)

[4.6.9.	Un lien pour envoyer un e-mail	10](#_toc100764835)

[4.6.10.	Un lien pour télécharger un fichier	10](#_toc100764836)

[5.	Insérer une image	10](#_toc100764837)

[5.1.	Les différents formats d’images	10](#_toc100764838)

[5.1.1.	Le JPEG	10](#_toc100764839)

[5.1.2.	Le PNG	10](#_toc100764840)

[5.1.3.	Le GIF	11](#_toc100764841)

[5.1.4.	Le BITMAP	11](#_toc100764842)

[5.2.	Insérer une image	11](#_toc100764843)



1. <a name="_toc100764808"></a>**Historique**

**Video** : historique

Le "World Wide Web", plus communément appelé "Web" a été développé au CERN (Conseil Européen pour la Recherche Nucléaire) par le Britannique **Sir Timothy John Berners-Lee** et le Belge **Robert Cailliau** en 1991. À cette époque les principaux centres de recherche mondiaux étaient déjà connectés les uns aux autres, mais pour faciliter les échanges d'information Tim Berners-Lee met au point le système hypertexte. Le système hypertexte permet, à partir d'un document, de consulter d'autres documents en cliquant sur des mots clés. Ces mots "cliquables" sont appelés **hyperliens** et sont souvent soulignés et en bleu. 

La première page web est toujours consultable à l'adresse suivante : 

- <http://info.cern.ch/hypertext/WWW/TheProject.html>


Tim Berners-Lee développe le premier navigateur web (logiciel permettant de lire des pages contenant des hypertextes), il l'appelle simplement "**WorldWideWeb**". Tim Berners-Lee a créé le World Wide Web Consortium (W3C) qui définit les nouvelles versions des langages liés au Web.

Une chose très importante à bien avoir à l'esprit : beaucoup de personnes confondent "web" et "internet. L’ "**internet**" est un "**réseau de réseau**" alors que, comme nous venons de le voir, le web est la combinaison de trois technologies : HTTP, URL et HTML. D'ailleurs on trouve autre chose que le "web" sur internet, par exemple, les emails avec le protocole SMTP (Simple Mail Transfert Protocol) et les transferts de fichiers avec le protocole FTP (File Transfert Protocol).

Tim Berners-Lee n'est donc pas l'inventeur d'Internet, c'est « seulement » l'inventeur du Web.

1. <a name="_toc27249512"></a><a name="_toc100764809"></a>**Le fonctionnement des sites web**
   1. <a name="_toc27249513"></a><a name="_toc100764810"></a>**Les navigateurs utilisés**

Pour consulter un site web, on doit lancer un programme appelé **navigateur web** :

1. <a name="_toc27249514"></a><a name="_toc100764811"></a>**Les langages**

Pour créer des sites web, on utilise des langages particuliers : le CSS,  le HTML. 

Ces deux langages ont des rôles différents :

- HTML (HyperText Markup Language) : Son rôle est de gérer et organiser le contenu. C’est donc en HTML que l’on écrit ce qui doit être affiché sur la page : le texte, les liens, les images….
- CSS (Cascading Style Sheets) : le role du CSS est de gérer l’apparence de la page Web (agencement, positionnement, …). Il est apparu en 1996. Il a besoin d’une page HTML pour fonctionner

|<p>HTML</p><p></p>|<p>HTML + CSS</p><p></p>|
| :-: | :-: |
|||
- Le HTML définit le contenu.
- Le CSS permet de définir la présentation : couleurs, image de fond, marges, taille du texte…

1. <a name="_toc27249515"></a><a name="_toc100764812"></a>**Les éditeurs et les logiciels conseillés**

**Notepad ++, Visual Studio code**, Visual Studio Community, Sublime Text (qui fonctionne sous différents OS). 

**Il est vivement conseillé d’installer** **Notepad ++, Visual Studio code**

De plus, il est conseillé d’installer plusieurs navigateurs sur son ordinateur pour s’assurer que son site fonctionne correctement sur chacun d’eux : **Microsoft Edge et Firefox** au minimum. 

Le site <https://caniuse.com/> tient à jour une liste des fonctionnalités prises en charge par les différentes versions de chaque navigateur. 

1. <a name="_toc27249516"></a><a name="_toc100764813"></a>**Le langage HTML5**
   1. <a name="_toc27249517"></a><a name="_toc100764814"></a>**Page web en HTML**

**Activité n° AUTONUM  \* Arabic  :** 

Ouvrir un éditeur (Notepad++, Visual Studio code ou Notepad)

Faire menu Fichier>Enregistrer (ou File >Save en anglais) 

Enregistrer dans un **dossier <a name="_hlk40012128"></a>**Documents\site**.**

Donner au fichier le nom, en terminant par.html **:** index.html.

1. <a name="_toc27249518"></a><a name="_toc100764815"></a>**Les balises**

Pour donner les instructions en HTML il faut utiliser des **balises**. Celles-ci sont invisibles à l’écran mais elles permettent à l’ordinateur de comprendre ce qu’il doit afficher. Les balises se repèrent facilement. Elles sont entourées de « chevrons », c’est-à-dire des symboles < balise>. 

1. <a name="_toc27249519"></a><a name="_toc100764816"></a>Les balises en paires

Elles fonctionnent en nombre paire : <balise1> des indications </balise1>. On distingue une balise ouvrante et une balise fermante

1. <a name="_toc27249520"></a><a name="_toc100764817"></a>Les balises orphelines

Elles servent en un point précis <balise/>.

1. <a name="_toc27249521"></a><a name="_toc100764818"></a>**Les attributs**

Ce sont les options des balises : appelées attributs. Ils donnent les options des balises. Ils se placent après le nom de la balise ouvrante.

**<balise attribut="valeur">**

1. <a name="_toc27249522"></a><a name="_toc100764819"></a>**Structure de base d’une page HTML5**

**Activité n° AUTONUM  \* Arabic  :** 

<!DOCTYPE html>

<html>

`    `<head>

`        `<meta charset="utf-8" />

`        `<title>Logique sur les passoires</title>

`    `</head>

`    `<body>

`        `Bonjour tout le monde

`    `</body>

</html>

Par souci de lisibilité du code on met des indentations (non obligatoires en HTML5)

Enregistrer, ouvrer le fichier dans Firefox et observer…

- La première ligne s’appelle le **doctype**, elle indique qu’il s’agit bien d’une page web HTML. 
- Les deux balises html englobe tout le contenu de la page
- L’en-tête head donne le titre, l’encodage. Le titre s’affichera dans l’onglet du navigateur et dans les résultats de recherche de Google par exemple. Les informations que contient l'en-tête ne sont pas affichées sur la page, ce sont simplement des informations générales à destination de l'ordinateur.
  - <meta charset="utf-8" /> : Cette balise indique l'encodage utilisé dans le fichier .html qui détermine comment les caractères spéciaux vont s'afficher (accents, idéogrammes chinois et japonais, caractères arabes, etc.) . Il y a plusieurs techniques d'encodage mais aujourd'hui autant que possible on utilise UTF-8. 
  - <title> : C'est le titre de votre page, probablement l'élément le plus important ! Toute page doit avoir un titre qui décrit ce qu'elle contient

Il faut savoir que le titre apparaît aussi dans les résultats de recherche, comme sur Google.

- Le corps body : tout ce qui est écrit ici sera affiché.

**Les commentaires** : (pour pouvoir se relire ou pour expliquer le code)

<!-- je fais un commentaire-->

1. <a name="_toc27249523"></a><a name="_toc100764820"></a>**L’organisation d’une page HTML5**
   1. <a name="_toc27249524"></a><a name="_toc100764821"></a>**Les paragraphes**

La plupart du temps, on écrit du texte à l’intérieur d’un paragraphe. Le langage HTML propose justement la balise <p> pour délimiter les paragraphes. Il faut évidemment mettre ses paragraphes entre les balises body.

**Activité n° AUTONUM  \* Arabic :** 

`    `<body>

`        `<p>Bonjour et bienvenue sur ma page</p>

`    `</body>

**Activité n° AUTONUM  \* Arabic  :** Je voudrais écrire le texte suivant exactement avec la même mise en page ci-dessous à la place de « Bonjour et bienvenue sur ma page ». **A vous de jouer !!**

<body>

`    `<p>

`        `On appelle passoire tout instrument sur lequel on peut définir trois sous-ensembles : l’intérieur, l’extérieur, et les trous.

`        `L’intérieur est généralement placé au-dessus de l’extérieur et se compose le plus souvent de nouilles et d’eau.

`        `Les trous ne sont pas importants. En effet, une expérience simple permet de se rendre compte que l’on ne change pas notablement les qualités de l’instrument en réduisant de moitié le nombre des trous, puis en réduisant cette moitié de moitié… etc… etc… et à la limite jusqu’à ce qu’il n’y ait plus de trous du tout. D’où le théorème :

`        `La notion de passoires est indépendante de la notion de trous et réciproquement.

`    `</p>

</body>

**Attention à mettre des indentations pour que le code soit lisible !!**

1. <a name="_toc27249525"></a><a name="_toc100764822"></a>**La balise retour à la ligne**

Il existe une balise orpheline <br /> qui permet un retour à la ligne.

**Activité n° AUTONUM  \* Arabic :** Modifier l’application n° 4 pour ne mettre qu’un seul paragraphe et garder la mise en page.

1. <a name="_toc27249526"></a><a name="_toc100764823"></a>**Les titres**

Il a y six niveaux de titres différents :

- Entre les balises <h1></h1> : titre de niveau 1.
- Entre les balises <h2></h2> : titre de niveau 2.
- ….
- Entre les balises <h6></h6> : titre de niveau 6.

**Activité n° AUTONUM  \* Arabic :** Ajouter un titre à l’application n°4 : Les passoires

Puis un sous-titre : Le théorème des passoires, 

Ainsi, on aura :

**Activité n° AUTONUM  \* Arabic :** Ajouter un autre paragraphe à la suite dont voici le texte :

Les différents ordres de passoires

On appelle passoires du premier ordre les passoires quine laissent passer ni les nouilles ni l'eau. 

On appelle passoires du second ordre les passoires qui laissent passer et les nouilles et l'eau.

On appelle passoires du troisième ordre, ou passoires complexes, les passoires qui laissent passer quelquefois l'un ou l'autre et quelquefois pas.   

Ajouter les bonnes balises pour observer cela sur le navigateur

**Attention à mettre des indentations pour que le code soit lisible !!**

**Activité n° AUTONUM  \* Arabic :** Ajouter des titres d’ordre inférieures et des paragraphe correspondants, dont voici le texte :

Les différents types de passoires du troisième ordre

Pour qu'une passoire complexe laisse passer l'eau et pas les nouilles, il faut et il suffit que le diamètre des trous soit notablement inférieur au diamètre des nouilles.

Pour qu'une passoire complexe laisse passer les nouilles et pas l'eau, il faut et il suffit que le diamètre des trous soit notablement inférieur au diamètre de l'eau.

Les différents types de passoire du premier ordre

Quant aux passoires du premier ordre qui ne laissent passer ni les nouilles ni l'eau, il y en a de deux sortes : 

Les passoires qui ne laissent passer ni les nouilles ni l'eau ni dans un sens ni dans l'autre et celle qui ne laissent passer ni les nouilles ni l'eau que dans un sens unique. 

Ces passoires là on les appelle des casseroles.

Ajouter les bonnes balises pour observer cela sur le navigateur


**Activité n° AUTONUM  \* Arabic :** Ajouter des titres d’ordre inférieures et des paragraphe correspondants, dont voici le texte :

Les différents types de casseroles

Il y a trois sortes de casseroles. Les casseroles avec la queue à droite, les casseroles avec la queue à gauche, et les casseroles avec pas de queues du tout. Mais celles-là on les appelle des autobus.

Les différents types d'autobus

Il y a trois sortes d'autobus : les autobus qui marchent à droite ; les autobus qui marchent à gauche et les autobus qui ne marchent ni d'un côté ni de l'autre. Mais ceux-là, on les appelle des casseroles.


1. <a name="_toc27249527"></a><a name="_toc100764824"></a>**Mettre en valeur**

Il y a différentes façons de mettre en valeur :

- Pour mettre un peu en valeur le texte on utilise la balise <em></em>.

<a name="_hlk26720452"></a>**Activité n° AUTONUM  \* Arabic  :** utiliser les balises précédentes pour le mot passoire et théorème du premier paragraphe.

- Pour mettre en valeur le texte on utilise la balise <strong></strong>. 

**Activité n° AUTONUM  \* Arabic****  : utiliser les balises précédentes pour les mots ci-dessous du deuxième paragraphe

- Les balises<mark> </mark> permet de faire ressortir visuellement une portion de texte.  L’extrait n’est pas forcément considéré comme important mais on veut qu’il se distingue bien du reste du texte. 

**Activité n° AUTONUM  \* Arabic**** : utiliser les balises précédentes pour les mots ci-dessous du troisième paragraphe

**Attention** :  HTML pour le fond, CSS pour la forme

Le rôle des balises est d'indiquer le sens du texte. Ainsi, <strong> indique à l'ordinateur « Ce texte est important ». C'est tout.

Et pour montrer que le texte est **important**, l'ordinateur décide de le mettre en gras (mais il pourrait aussi bien l'écrire en rouge !). La plupart des navigateurs affichent les textes importants en gras, mais rien ne les y oblige. 

Pourquoi c’est important de différencier par les balises adéquat le texte ?

De nombreux programmes analysent le code source des pages web, à commencer par les robots de moteurs de recherche. Ces robots parcourent le Web en lisant le code HTML de tous les sites. C'est le cas des robots de Google et de Bing, par exemple. Les mots-clés « **importants** » ont tendance à avoir plus de valeur à leurs yeux, donc si quelqu'un fait une recherche sur ces mots, il a plus de chances de tomber sur votre site.

1. <a name="_toc27249528"></a><a name="_toc100764825"></a>**Les listes**

Il y a deux types de listes :

- Les listes non ordonnées ou listes à puces

Pour créer une liste d’éléments sans notion d’ordre, il suffit d’utiliser les balise <ul></ul> . Puis pour chacun des éléments on utilise les balises <li></li>.

Par exemple : 

<ul>

`    `<li>Fraises</li>

`    `<li>Framboises</li>

`    `<li>Cerises</li>

</ul>

**Activité n° AUTONUM  \* Arabic****  : utiliser les balises précédentes pour les mots ci-dessous du cinquième paragraphe

- Les listes ordonnée ou listes numérotées ou énumérations

Il suffit de remplacer les balises <ul> par <ol> et on utilise aussi les balise <li></li>.

Par exemple :

<ol>

`    `<li>Fraises</li>

`    `<li>Framboises</li>

`    `<li>Cerises</li>

</ol>

**Activité n° AUTONUM  \* Arabic****  : utiliser les balises précédentes pour les mots ci-dessous du dernier paragraphe

1. <a name="_toc27249529"></a><a name="_toc100764826"></a>**Les liens hypertexte**
   1. <a name="_toc27249530"></a><a name="_toc100764827"></a>Les liens absolus

Pour faire un lien vers un autre site, il faut utiliser les balises <a></a> et un attribut href qui indiquera la page.

Par exemple : 

<a href="https://fr.wikipedia.org/wiki/Passoire">Passoire</a>

**Activité n° AUTONUM  \* Arabic****  : utiliser les balises précédentes pour mettre un lien vers casserole sur wikipedia comme ci-dessous.

**Remarque** : Si vous faites un lien vers un site qui comporte une adresse un peu bizarre avec des &, comme : http://www.site.com/?data=15&name=mateo21, vous devrez remplacer tous les « & » par « &amp; » dans votre lien comme ceci :http://www.site.com/?data=15&amp;name=mateo21.

1. <a name="_toc27249531"></a><a name="_toc100764828"></a>Lien relatif vers une page d’un même dossier

Pour faire un lien vers une page située dans un même dossier, on crée un lien relatif. Il suffit d’utiliser les balises <a> avec l’attribut href. 

**Activité n° AUTONUM  \* Arabic****  : Créer un nouvelle page html page2.html dans le dossier Documents\site** (Titre : Page 2). Après avoir rempli, la **structure minimale de la nouvelle page html** :

<p>

`    `Pour consulter la <a href="index.html">logique sur les passoires</a>

</p>

Observer la page2.html dans Firefox.

1. <a name="_toc27249532"></a><a name="_toc100764829"></a>Lien relatif vers une page située dans un dossier fils

Pour faire un lien vers une page située dans un sous dossier, on utilise le chemin relatif :

**Activité n° AUTONUM  \* Arabic****  : Créer un dossier **contenu** dans le dossier Documents\site**.** Créer un nouvelle page html page3.html** avec la **structure minimale** dans le dossier contenu (Titre : Page3). Sur la page2.html, rajouter :

<p>

`    `Pour consulter la <a href="contenu/page3.html">page 3 </a> du site

</p>

Observer la page2.html dans Firefox.

1. <a name="_toc27249533"></a><a name="_toc100764830"></a>Lien relatif vers une page située dans un dossier parent

Pour faire un lien vers une page dans un dossier parent, on utilise toujours la même chose

**Activité n° AUTONUM  \* Arabic****  : Sur la page3.html, rajouter :

<p>

`    `Pour consulter la <a href="../page2.html">page 2 </a> du site

</p>

1. <a name="_toc27249534"></a><a name="_toc100764831"></a>Lien vers une ancre sur une même page

Une **ancre** est une sorte de point de repère que l’on peut mettre dans les pages html lorsqu’elles sont très longues. Il peut alors être utile de faire un lien amenant plus bas dans la même page pour que le visiteur puisse sauter directement à la partie qui l'intéresse. Pour créer une ancre, il suffit de rajouter l'attribut id à une balise qui va alors servir de repère. Ce peut être n'importe quelle balise.

**Activité n° AUTONUM  \* Arabic****  : Sur la index.html, on va faire une ancre sur le titre en haut de page

`        `<h1 id = "haut"> Les passoires</h1>

On crée un lien en bas de la page pour remonter vers le haut. Rajouter tout en bas (mais dans le body) la référence avec #

`        `<p>

`            `<a href = "#haut">Aller en haut</a>

`        `</p>

Enregistrer et observer dans Firefox. S’il ne se passe rien augmenter le zoom dans Firefox afin de faire apparaitre les barres de défilement sur le côté.

1. <a name="_toc27249535"></a><a name="_toc100764832"></a>Lien vers une ancre sur une autre page

Pour faire un lien vers **une ancre située dans une autre page,** on précise l’adresse de la page et le nom de l’ancre précédée de #.

**Activité n° AUTONUM  \* Arabic****  : Sur la page2.html, on va faire un lien vers l’ancre de la index.html. 

`        `<h1 id = "haut"> Les passoires</h1>

On crée un lien en bas de la page pour remonter vers le haut. Rajouter tout en bas (mais dans le body) la référence avec #

`  `<p>

`      `<a href = "index.html#haut">Aller en haut de la page logique sur les passoires</a>

`  `</p>

Enregistrer et observer dans Firefox.

1. <a name="_toc27249536"></a><a name="_toc100764833"></a>Lien affichant une infobulle

Avec l’**attribut** title 

**Activité n° AUTONUM  \* Arabic****  : Sur la page2.html, on va faire une infobulle

<p>

`    `<a href = "index.html#haut" title = "Vous ne le regretterez pas !">Aller en haut de la page logique sur les passoires</a>

</p>

Enregistrer et observer dans Firefox.

1. <a name="_toc27249537"></a><a name="_toc100764834"></a>Lien qui ouvre une nouvelle fenêtre

Pour forcer l’ouverture d’un lien dans une nouvelle fenêtre, on rajoutera target="\_blank" à la balise <a>

**Activité n° AUTONUM  \* Arabic****  : Sur la page2.html, on va faire une infobulle

<p>

`   `<a href = "index.html#haut" title = "Vous ne le regretterez pas !" target = "\_blank">Aller en haut de la page logique sur les passoires</a>

</p>

Enregistrer et observer dans Firefox.

1. <a name="_toc27249538"></a><a name="_toc100764835"></a>Un lien pour envoyer un e-mail

Avec un lien de type mailto, en cas de click, un nouveau message vide s’ouvre.

**Activité n° AUTONUM  \* Arabic****  : Sur la index.html, on va faire un lien vers un mail

<p>

`   `<a href="mailto:votrenom@bidule.com">Envoyez-moi un e-mail !</a>

</p>

Enregistrer et observer dans Firefox.

1. <a name="_toc27249539"></a><a name="_toc100764836"></a>Un lien pour télécharger un fichier

Il s’agit d’un même type de lien mais vers le dossier à télécharger.

Par exemple :

<p><a href="monfichier.zip">Télécharger le fichier</a></p>

1. <a name="_toc27249540"></a><a name="_toc100764837"></a>**Insérer une image**
   1. <a name="_toc27249541"></a><a name="_toc100764838"></a>**Les différents formats d’images**

Le format de l’image influence le poids mais également la qualité de l’image. Toutes les images diffusées sur internet ont un point commun : elles sont **compressées.**

1. <a name="_toc27249542"></a><a name="_toc100764839"></a>Le JPEG

Les images au format JPEG (Joint Photographic Expert Group) sont très répandues sur le Web. Ce format est conçu pour réduire le poids des photos qui peuvent comporter plus de 16 millions de couleurs différentes. Les images JPEG sont enregistrées avec l’extension .jpg ou .jpeg. Ce format permet de réduire le poids des photos mais les images sont de moindre qualité.

1. <a name="_toc27249543"></a><a name="_toc100764840"></a>Le PNG

Le format PNG (Portable Network Graphics) est le plus récent de tous. Le PNG a deux gros avantage : il peut être rendu transparent et il n’altère pas la qualité de l’image.

Le PNG existe en deux versions :

- PNG 8 bits : 256 couleurs
- PNG 24 bits : 16 millions de couleurs

Une photo au format PNG a un poids plus important qu’au format JPEG.

1. <a name="_toc27249544"></a><a name="_toc100764841"></a>Le GIF

Le format GIF est limité à 256 couleurs. Par contre il peut être animé.

1. <a name="_toc27249545"></a><a name="_toc100764842"></a>Le BITMAP

C’est un format non compressé donc très (trop) gros.

1. <a name="_toc27249546"></a><a name="_toc100764843"></a>**Insérer une image**

Pour insérer une image, il faut utiliser la balise orpheline <img />. La balise doit être accompagnée de deux attributs obligatoires :

- src : il permet d’avoir le chemin de la source

Par exemple : 

<img src="http://monsite.fr/fleur.jpg" />

<img src="images/fleur.jpg" />

- alt : cela signifie « texte alternatif ». Il faut toujours indiquer un texte alternatif à l’image qui permet de décrire l’image si elle ne s’affiche pas dans le navigateur de l’utilisateur. De plus, elle sera d’une aide précieuse pour les personnes mal voyantes. Cela aide aussi les robots des moteurs de recherche pour les recherches d'images. Pour la fleur, on mettrait par exemple :  alt="Une fleur".
- title : permet d’insérer une info bulle (attribut facultatif)

On aura ainsi finalement : 

<p>

`    `Voici une photo d'une fleur de mon jardin <br />

`    `<img src="images/fleur.jpg" alt="Photo d'une fleur" title="C'est beau les fleurs quand même !" />

</p>

**Attention** : a ne pas mettre d’espace dans le nom !!

**Activité n° AUTONUM  \* Arabic****  : Chercher trois images sur le web d’une passoire, d’une casserole et d’un autobus. Les enregistrer dans un dossier** images dans le dossier Documents\site. Ouvrir la index.html et insérer ces trois images de telle sorte à obtenir la page ci-dessous. Mettre des infobulles du type « Ceci est une passoire ! »



Enregistrer et observer dans Firefox.

On peut proposer une miniature cliquable pour des images très grosse :

Il faut les placer toutes les deux dans un dossier img. On affiche la version mini sur la page et on fait un lien vers la plus grosse image pour que l’image agrandie s’affiche lorsqu’on clique sur la miniature.

<p>

`    `Voici une photo d'une fleur de mon jardin. Cliquez dessus !<br />

`    `<a href="img/fleur.jpg">

`        `<img src="images/fleur\_mini.jpg" alt="Photo d'une fleur" title="C'est beau les fleurs quand même !" />

`    `</a>

</p>




|<p><h2>Vérification de la syntaxe de votre page.</h2></p><p>Pour vérifier que votre page Web est conforme aux spécifications HTML5, rendez-vous sur le site du W3C (World Wide Web Consortium) : [http://validator.w3.org](http://validator.w3.org/)</p><p>Pour une page Web locale (pas encore publiée sur le Web) :</p><p>Validate by File Upload → Check</p><p>S'il y a des erreurs, elles vous seront indiquées, avec des explications.</p>|
| :- |

































Première NSI 	Chap 07 : Le HTML	Page 13/13
