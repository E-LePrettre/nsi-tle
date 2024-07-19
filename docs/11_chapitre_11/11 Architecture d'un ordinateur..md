---
author: ELP
title: 12 Architecture de l’ordinateur
---


**Table des matières** 

1. [**Historique de l’informatique**](#_page0_x40.00_y403.92)
2. [**Les différents types de mémoires**](#_page3_x40.00_y539.92)
3. [**Architecture de Von Neumann**](#_page4_x40.00_y536.92)
4. [**Langage assembleur**](#_page8_x40.00_y390.92)
5. [**Simulation CPU**](#_page11_x40.00_y36.92)


Video 1 :[ https://www.dailymotion.com/video/xhleks ](https://www.dailymotion.com/video/xhleks)

## **1. Historique<a name="_page0_x40.00_y403.92"></a> de l’informatique** 

Video 2 :[ https://www.youtube.com/watch?v=7TrsMU5DukE ](https://www.youtube.com/watch?v=7TrsMU5DukE)

### **1.1. Les<a name="_page0_x40.00_y459.92"></a> machines à programmes externes** 
- **Machines électromécaniques** 

L’allemand **Konrad ZUSE** achève le **Z1** en 1938, un  ordinateur  mécanique  utilisant  le  système binaire,  puis  le  **Z3**  en  1941,  premier  ordinateur complètement automatique lisant son programme sur une bande perforée. Le Z3 utilisait déjà le calcul en virgule flottante et réalisait 3 à 4 additions par seconde.

**Réplique du Zuse Z3 au Deutsches Museum de Munich.**
![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.002.png)

Peu  après  aux  Etats-Unis,  **Howard  H.  AIKEN** construit l’ordinateur électromécanique **MARK I** (1944). Le MARK I pesait environ 5 tonnes et était composé de plus de 750 000 pièces !   

**L’ordinateur MARK inauguré à Harvard le 7 août 1944 mesurait 16m de long, 2,40m de haut, 0,5 m de profondeur et pesait 4,5 tonnes.**

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.001.png)
Source : espace-turing.fr 

Le **Mark I** lisait ses instructions sur des cartes perforées et exécutait l’instruction courante puis lisait la suivante.

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.003.png)
Source : Wikipédia 

- **Machines électroniques** 

L’apparition des **tubes à vide**, bien plus rapides que les relais des machines électromécaniques, marque le début de l’électronique moderne.  

Entre 1943 et 1945 les Britanniques **Max NEWMAN** et **Tomy FLOWERS** mettent en service les **COLOSSUS** utilisés pour déchiffrer le code de LORENZ employé par les allemands durant la seconde guerre mondiale. 

Le célèbre **ENIAC** des Américains **John MAUCHLY** et **John ECKERT** est achevé en novembre 1945 et effectue des calculs balistiques à l’aide de 18 00 tubes à vide. 

**L'ENIAC** (Electronic Numerical Integrator And Computer) : premier ordinateur entièrement électronique (1945).  

Il peut être reprogrammé pour résoudre, en principe, tous les problèmes calculatoires.  

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.004.png)
Source : Wikipédia 

### **1.2. Les<a name="_page1_x40.00_y480.92"></a> machines à programmes enregistrés** 

- Basés sur les travaux de **MAUCHLY**, **ECKERT** et **VON NEUMANN**, les machines à programmes enregistrés sont les ancêtres directs des ordinateurs actuels.  Dans ce type de machines, les données et les programmes résident en mémoire. Les premières machines de ce type apparaissent dès 1948 avec les ordinateurs britanniques  BABY et EDSAC, suivis par leurs homologues américains **EDVAC** et **UNIVAC**. 
- Le début des années 1950 voient apparaître les premiers ordinateurs commerciaux et les modèles se succèdent avec comme principaux acteurs les constructeurs **IBM** (International Business Machines), **DEC** (Digital Equipment Corporation) et **BULL**. 

### **1.3. Du<a name="_page1_x40.00_y644.92"></a> micro-ordinateur à la micro-informatique** 
- **Miniaturisation et explosion du marché** 

Le **transistor** (1947) devient un produit industriel très fiable qu’on peut fabriquer à faible coût au milieu des années 1950. Son émergence technologique, marque la fin des tubes à vide.  

Le **circuit intégré** qui rassemble de nombreux composants miniaturisés sur une petite surface apparaît en 1958 et ne cessera de se perfectionner au fil du temps.  

Durant plus de 10 ans, **IBM** et **DEC** dominent le marché alors que la science informatique encore naissante, permet de former dans les université des personnes qui se spécialisent dans l’utilisation et la programmation des ordinateurs. L’apparition du **microprocesseur** (INTEL 4004 en 1971) permet à de nouveaux acteurs d’apparaître et d’innover : l’informatique s’ouvre au grand public. 

Une multitude de machines sont commercialisées : **l’ALTAIR 8800** premier ordinateur grand public, sans clavier ni  écran, l’**APLLE II**  (1977), l’**IBM PC** (1981), le  **COMMODORE 64**  (1982), le **APPLE MACINTOSH** (1984). Ce dernier est d’ailleurs le premier ordinateur personnel équipé d’une souris et d’une interface graphique. 

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.005.png) 
ALTAIR 8800

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.007.png)
APLLE II

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.006.png) 
IBM PC 

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.008.png)
COMMODORE 64 
    
![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.009.png)
APPLE MACINTOSH

- **Langages et système d’exploitation **

Après la naissance des premiers compilateurs conçus Grace HOPPER à partir de 1951, **John BACKUS** achève l’élaboration  du langage **FORTRAN** en 1956. Il est suivi par **LISP**, **COBOL** et enfin **BASIC** en 1964. Les grands principes des langages de programmation étant formulés, de nombreux langages voient le jour entre les années 1970 et 2000 : le **C** (1972), **ML** (1973) dont est issu **CAML**, **ADA** (1983) et APPLE  **C++**  en  1986.  Le  langage  **PYTHON**  verra  le  jour  quant  à  lui  en  1991  et JAVASCRIPT en 1995. 

Au milieu des années 1960, chaque constructeur développe son propre système d’exploitation  :  **OS  360**  puis  **MVS**  chez  **IBM**,  le  système  **UNIX**  (1970)  chez AT&T… 

En 1984 **Richard STALLMAN**, chercheur au MIT entame la création du système **GNU** (GNU’s Not Unix) et promeut  le mouvement du logiciel libre. 

Par la suite, c’est finalement **MS-DOS**, écrit par Microsoft pour IBM qui s’imposera sur les micro- ordinateurs grand public, suivi par Windows en 1985.  

A l’heure actuelle on distingue trois grands types d’OS (Operating System) équipant les ordinateurs modernes : **WINDOWS**, **MAC OS** et **GNU LINUX** créé par **Linus TORVALDS** en 1991. 



<table><tr><th colspan="4" valign="top"><b>Activité n°1.:</b> Répondre par Vrai ou faux Remarque : Certaines questions nécessitent une recherche internet.</th></tr>
<tr><td colspan="2" valign="top">Blaise Pascal a mis au point le logiciel Turbo Pascal. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">George Boole était un spécialiste de la logique binaire. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">Alan Turing a travaillé sur l’intelligence artificielle. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">Alan Turing a cassé le code Enigma. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">L’ordinateur ENIAC était aussi petit qu’une boite à chaussure. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">John Von Neumann a conçu l’architecture de base de tous les ordinateurs actuels. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">L’invention du transistor a permis de miniaturiser les ordinateurs. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">Le premier micro-ordinateur est américain. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">Le processeur 8086 possède 1000000 de transistors </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">Gary Kasparov est imbattable aux échecs. </td><td colspan="2"></td></tr>
<tr><td colspan="2" valign="top">La loi de Moore est toujours valide en 2020 </td><td colspan="2"></td></tr>
</table>


<table><tr><th colspan="8" valign="top"><b>Activité n°2.:</b> Cocher la ou les bonnes réponses. Remarque : Certaines questions nécessitent une recherche internet.</th></tr>
<tr><td colspan="8" valign="top">  </td></tr>
<tr><td colspan="2" valign="top"><p>1. Le premier algorithme connu remonte... </p><p>- au XX siècle </p><p>- au XIX siècle </p><p>- au 1er siècle </p><p>- bien avant le 1er siècle </p></td><td colspan="2" valign="top"><p>2. Le mot algorithme vient du nom </p><p>- Al-Khwârizmi </p><p>- Grace Murray Hopper </p><p>- Steve Jobs </p><p>- Augusta Ada King </p></td><td colspan="2" valign="top"><p>3. Le 1er compilateur fut conçu par </p><p>- Al-Khwârizmi </p><p>- Grace Murray Hopper </p><p>- Steve Jobs </p><p>- Augusta Ada King </p></td><td colspan="2"></td><td colspan="3" rowspan="2" valign="top"></td></tr>
<tr><td colspan="2" valign="top"><p>4. Le 1er programme fut  écrit par </p><p>- Al-Khwârizmi </p><p>- Grace Murray Hopper </p><p>- Steve Jobs </p><p>- Augusta Ada King </p></td><td colspan="2" valign="top"><p>5. Le transistor fut inventé dans les années </p><p>- 1850 </p><p>- 1900 </p><p>- 1950 </p><p>- 2000 </p></td><td colspan="2" valign="top"><p>6. Le circuit intégré fut inventé après le transistor. </p><p>- Vrai </p><p>- Faux </p><p>- Les deux ont été inventés en même temps </p><p>- Cette question n'a aucun sens</p></td><td colspan="2"></td><td colspan="3" rowspan="2" valign="top"></td></tr>
<tr><td colspan="2" valign="top"><p>7. La souris a été inventée après le disque dur. </p><p>- Vrai </p><p>- Faux </p><p>- Les deux ont été inventés en même temps </p><p>- Cette question n'a aucun sens </p></td><td colspan="2" valign="top"><p>8.  L’invention  du  premier microprocesseur date des années </p><p>- 1945 </p><p>- 1970 </p><p>- 1990 </p><p>- début des années 2000 </p></td><td colspan="2" valign="top"><p>9. L’internet a été inventé après le web. </p><p>- Vrai </p><p>- Faux </p><p>- Les deux ont été inventés en même temps </p><p>- Cette question n'a aucun sens</p></td><td colspan="2"></td><td colspan="3" rowspan="2" valign="top"></td></tr>
<tr><td colspan="6" valign="top"><p>10. Le moteur de recherche Google a été créé en </td><td colspan="3" rowspan="3" valign="top"></td></tr>
<tr><td colspan="6" valign="top">- 1990 </td></tr>
<tr><td colspan="6" valign="top">- 1998 </td></tr>
<tr><td colspan="6" valign="top">- 2005 </td></tr>
<tr><td colspan="6" valign="top">- 2010 </td></tr>
</table>

## **2. Les<a name="_page3_x40.00_y539.92"></a> différents types de mémoires** 
### **2.1. Organisation<a name="_page3_x40.00_y567.92"></a> de la mémoire** 

Il  existe  de  nombreuses  technologies  de  mémoire  qui  se  distinguent  par  leur  durabilité  (volatile  ou permanente), leur mode d’accès (par adresse ou dans l’ordre de leur rangement) ou leur temps d’accès. En règle générale, plus une mémoire est performante, plus elle est chère.  

- Il existe la **mémoire morte** ( **ROM** = Read Only Memory ) chargée de stocker le programme. C’est une mémoire à lecture seule, en principe. 
- On parle de **mémoire vive** (ou volatile) (**RAM** = Random Access Memory) quand le contenu est perdu lorsque le courant s’arrête : il s’agit des registres, des mémoires cache, de la mémoire centrale. 
- Les disques durs, disquettes, CDROM, etc… sont des périphériques de stockage et sont considérés comme des mémoires secondaires. 

Remarque : la mémoire ROM contient notamment le BIOS (Basic Input Output System) qu’il est possible, sur les machines dotées de carte mère récente, de mettre à jour (flashage du BIOS). 

### **2.2. Les<a name="_page4_x40.00_y47.92"></a> registres** 

Un **registre** est un emplacement **mémoire interne** au processeur. Les registres se situent au sommet de la hiérarchie mémoire : il s'agit de la **mémoire la plus rapide** d'un ordinateur, mais dont le coût de fabrication est le plus élevé, car la place dans un microprocesseur est limitée.  

Il sert à **stocker des opérandes** et **des résultats intermédiaires** lors des opérations effectuées dans l’UAL. Leur capacité, leur nombre et leurs rôles varient selon les processeurs. La grande majorité des processeurs actuels ont des registres de taille 64 bits. Ils sont accessibles via un jeu d’instructions. 

### **2.3. Mémoires<a name="_page4_x40.00_y175.92"></a> centrales et mémoires caches** 

La **mémoire centrale** est une mémoire vive qui contient les programmes en cours et les données qu’ils manipulent. Elle est de taille importante (plusieurs Go). Elle est organisée en **cellules** appelées « **cases mémoires** » qui contiennent chacune une donnée ou une instruction repérée par une **adresse** qui est un **nombre entier**. Le temps d’accès à chaque cellule est le même : on parle de mémoire à accès aléatoire (RAM) bien qu’il soit plus judicieux de parler de mémoire à accès direct.  

Afin de pouvoir adapter la très grande vitesse du processeur à celle plus faible de la mémoire centrale, on place entre les deux une mémoire plus rapide, la **mémoire cache** qui contient les instructions et les données en cours d’utilisation car, la plupart du temps, les données qui viennent d’être utilisées ont une probabilité plus grande d’être réutilisées que d’autres. La **mémoire cache** (de l’ordre de quelques Mo) est souvent constitué  de  mémoire  de  type  statique  SRAM  plus  rapide  mais  plus  chère  que  celle  de  type  **RAM dynamique (SDRAM, DDR** …) utilisée dans la mémoire centrale. Généralement la mémoire cache est intégrée au « socket » du processeur. 

**Activité n°3.:** Quelques interrogations 

Il reste toujours pas mal de questions en suspens. Quatre exemples :  

1. Où sont stockés les programmes là-dedans ? ça doit être forcément dedans puisque le programme fait partie de la machine. Mais où ?  
1. Comment fait la machine pour faire une addition ?  
1. Si on veut récupérer des données externes (clavier ?), on récupère à partir de quelle provenance ?  
1. Si on veut envoyer des informations vers l’extérieur (écran ?), on envoie vers quelle destination ? 

## **3. Architecture<a name="_page4_x40.00_y536.92"></a> de Von Neumann** 

L’architecture dite **architecture de Von Neumann est** un modèle pour un ordinateur qui utilise une structure de stockage unique pour conserver à la fois les instructions et les données demandées ou produites par le calcul. De telles machines sont aussi connues sous le nom d’**ordinateur à programme enregistré**. Le modèle de Von Neumann est conforme à un schéma qui a peu évolué depuis son origine en 1945. 

### **3.1. Organisation<a name="_page4_x40.00_y633.92"></a> générale** 

Les instructions qui composent les programmes sont exécutées par le **CPU** (Central Processing Unit). Il est schématiquement constitué de 3 parties.   

- **L’unité arithmétique et logique** (UAL ou ALU en anglais) est chargée de l’exécution de tous les calculs de base que peut réaliser le microprocesseur.  
- **L’unité de contrôle** est chargée du séquençage des opérations : elle permet d’exécuter les instructions (les programmes). 
- **la mémoire** contient à la fois les données et le programme. Le programme indique à l’unité de contrôle les calculs à faire sur les données. La mémoire est divisée en mémoire volatile (programmes  et  données  en  cours  de  fonctionnement)  et  mémoire  permanente (programmes et données de base de la machine). Un emplacement de mémoire interne à un processeur est appelé un registre. 

Les données doivent circuler entre les différentes parties d’un ordinateur, notamment entre la mémoire vive et le CPU. Le système permettant cette circulation est appelé **bus** : un bus de 64 bits est constitué de 64 «fils électriques » qui permettent de faire transiter 64 bits simultanément.  Il existe, sans entrer dans les détails, 3 grands types de bus :   

- Le **bus d’adresses** permet de faire circuler des adresses (par exemple l’adresse d’une donnée à aller chercher en mémoire). 
- Le **bus de données** permet de faire circuler des données. 
- Le **bus de contrôle** permet de spécifier le type d’action (exemples : écriture d’une donnée en mémoire, lecture d’une donnée en mémoire). 

Les **dispositifs d’entrée-sortie** permettent de communiquer avec le monde extérieur (clavier, écran, imprimante,…) 

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.021.jpeg)

**Architecture simplifiée de Von Neumann** 

Remarques : 

- **L’architecture Havard** se distingue de l’architecture Von Neuman uniquement par le fait que les mémoires  programmes  et  données  **sont  séparées**.  Cette  organisation  permet  de  transférer instructions et des données simultanément, ce qui améliore les performances, mais augmente les coûts. 
- Les ordinateurs **multiprocesseurs** permettent un parallélisme de tâches pour obtenir une plus grande puissance de calcul. Cette technologie a été utilisée pour des supercalculateurs, elle peut aussi l'être pour s'affranchir des limites de la montée en fréquence des processeurs : de nombreux processeurs actuels sont dits **multi-cœur**, et embarquent en fait plusieurs **monoprocesseurs** sur une même puce. 

**Activité n°4.:**  
On part du principe que le système doit pouvoir transporter en une seule opération une adresse via son bus d’adresses. Peux-tu répondre à ces deux questions. 

1. Combien d’adresses-mémoires RAM différentes peut-on avoir dans un ordinateur dont le bus d’adresse est un bus 16 bits ? 

2. Si on considère que chaque case mémoire correspond à un octet, quelle est la mémoire vive maximale disponible sur ce système s’il ne disposant pas d’autres manières d’adresser sa mémoire ?

### **3.2. Le<a name="_page6_x40.00_y297.92"></a>  CPU** 

Le processeur (CPU, pour Central Processing Unit) est le cerveau de l’ordinateur. Il permet de manipuler, des données et des instructions codées sous forme binaires. Le processeur est composé de millions  de  transistors  placés  dans  un  boitier  comportant  des  connecteurs  d’entrée-sortie, surmonté d’un ventilateur. C’est un circuit électronique cadencé au rythme d’une horloge interne qui envoie des impulsions. 

### **3.3. Le<a name="_page6_x40.00_y426.92"></a> role de l’horloge CPU** 

Une **horloge** rythme le travail du CPU: à chaque battement, une action. Plus la fréquence de l'horloge, mesurée en hertz (Hz), est élevée, plus le processeur est rapide. Cadencé à 2 GHz, il abat ainsi deux milliards d'opérations par seconde.  

On caractérise le microprocesseur par : 

- sa fréquence d’horloge : en MHz ou GHz 
- le nombre d’instructions par secondes qu’il est capable d’exécuter 
- la taille des données qu’il est capable de traiter : en bits 

**Activité n°5.:** Sur les photos ci-dessous, identifier le processeur. 

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.026.png)
![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.027.png)
![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.028.png)


### **3.4. Les<a name="_page7_x40.00_y274.92"></a> limites** 

Ce modèle impose un **va-et-vient** constant entre le **CPU et la mémoire**, soit pour charger la prochaine instruction à exécuter, soit pour récupérer les données sur lesquelles l’instruction courante doit opérer. Mais la différence de vitesse entre les microprocesseurs et la mémoire est très grande. De plus, cet accès se fait à travers un bus, mais pour des raisons technologiques, le débit du bus a augmenté moins vite que le débit d’accès à la mémoire et surtout que la vitesse des processeurs. D’où un phénomène d’attente — le **« goulot de von Neumann »** — qui réduit les performances  

### **3.5. Évolution<a name="_page7_x40.00_y423.92"></a> : le multiprocesseur et les mémoires caches** 

Selon la **loi de Moore** (1965), le nombre de transistors, c’est-à-dire l’élément principal qui compose les processeurs des ordinateurs**, double tous les deux ans**. Et parallèlement, double également la puissance des appareils. Moore fixa ensuite le cycle non plus sur 2 ans, mais **dix-huit mois.** Donc selon Moore tous les 18 mois il y a doublement du nombre de transistors, rendant les ordinateurs rapidement obsolètes. Sa loi  s’est  vérifiée  jusqu’à  récemment.  Il  avait  cependant  déclaré  en  1997  que  cette  croissance  des performances des puces se heurterait aux environs de 2017 à une limite physique : celle de la taille des atomes. Et nous y sommes. On voit en effet depuis quelques années le rythme du doublement diminuer en fréquence.  

Mais, l'augmentation de la fréquence devenant techniquement de plus en plus difficile (problème de surchauffe), une nouvelle idée permet de poursuivre la loi de Moore : mettre **plus de processeurs** dans un seul PC. 

De plus, la multiplication des cœurs pose le problème de la synchronisation de la mémoire.  Il existe plusieurs stratégies pour répartir la mémoire cache de chaque processeur.  

Ces évolutions ont pour conséquence de mettre la **mémoire**, plutôt que l’unité centrale, **au centre de l’ordinateur**, et **d’augmenter le degré de parallélisme** dans le traitement et la circulation de l’information 


**Activité n°6.:** Ci-contre, retrouver les interfaces RJ45, VGA, HDMI et USB. 

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.032.jpeg)

## **4. Langage<a name="_page8_x40.00_y390.92"></a> assembleur**  

Le microprocesseur étant incapable d'interpréter la phrase "additionne le nombre 125 et la valeur située dans le registre R2, range le résultat dans le registre R1", il faut coder cette instruction sous forme binaire : 

"additionne le nombre 125 et la valeur située dans le registre R2, range le résultat dans le registre R1" ⇓ 

"11100010100000100001000001111101" 

Afin de faciliter la lecture et l'écriture d'instructions machine par les informaticiens, on remplace les codes binaires par des symboles mnémoniques, en utilisant la syntaxe du langage appelé assembleur. 

"additionne le nombre 125 et la valeur située dans le registre R2, range le résultat dans le registre R1" ⇓  
"ADD R1,R2,#125" ⇓ 

"11100010100000100001000001111101" 

**Exemples d’instruction en assembleur :** 

- LDR R1,78 

Place la valeur stockée à l'adresse mémoire 78 dans le registre R1 (par souci de simplification, nous continuons à utiliser des adresses mémoire codées en base 10) 

- STR R3,125 

Place la valeur stockée dans le registre R3 en mémoire vive à l'adresse 125 

- ADD R1,R0,#128 

Additionne le nombre 128 (une valeur immédiate est identifiée grâce au symbole #) et la valeur stockée dans le registre R0, place le résultat dans le registre R1 

- ADD R0,R1,R2  

Additionne la valeur stockée dans le registre R1 et la valeur stockée dans le registre R2, place le résultat dans le registre R0 

- SUB R1,R0,#128 

Soustrait le nombre 128 de la valeur stockée dans le registre R0, place le résultat dans le registre R1 

- SUB R0,R1,R2  

Soustrait la valeur stockée dans le registre R2 de la valeur stockée dans le registre R1, place le résultat dans le registre R0 

- MOV R1, #23 

Place le nombre 23 dans le registre R1 

- MOV R0, R3 

Place la valeur stockée dans le registre R3 dans le registre R0 

- B 45 

Nous avons une structure de rupture de séquence, la prochaine instruction à exécuter se situe en mémoire vive à l'adresse 45 

- CMP R0, #23 

Compare la valeur stockée dans le registre R0 et le nombre 23. Cette instruction CMP doit précéder une instruction de branchement conditionnel BEQ, BNE, BGT, BLT (voir ci-dessous) 

- CMP R0, R1 

Compare la valeur stockée dans le registre R0 et la valeur stockée dans le registre R1. 

- CMP R0, #23 BEQ 78  

La prochaine instruction à exécuter se situe à l'adresse mémoire 78 si la valeur stockée dans le registre R0 est égale à 23 

- CMP R0, #23 BNE 78  

La prochaine instruction à exécuter se situe à l'adresse mémoire 78 si la valeur stockée dans le registre R0 n'est pas égale à 23 

- CMP R0, #23 BGT 78  

La prochaine instruction à exécuter se situe à l'adresse mémoire 78 si la valeur stockée dans le registre R0 est plus grand que 23 

- CMP R0, #23 BLT 78  

La prochaine instruction à exécuter se situe à l'adresse mémoire 78 si la valeur stockée dans le registre R0 est plus petit que 23 

- HALT !

Arrête l'exécution du programme 



**Activité n°7.:** Expliquer les instructions suivantes 

- ADD R0, R1, #42  
- LDR R5,98 
- CMP R4, #18 
- BGT 77 
- STR R0,15 
- B 100 



**Activité n°8.:** Écrire les instructions en assembleur correspondant aux phrases suivantes :

-  Additionne la valeur stockée dans le registre R0 et la valeur stockée dans le registre R1, le résultat est stocké dans le registre R5 

-  Place la valeur stockée à l'adresse mémoire 878 dans le registre R0 

-  Place le contenu du registre R0 en mémoire vive à l'adresse 124 

-  la prochaine instruction à exécuter se situe en mémoire vive à l'adresse 478 

-  Si la valeur stockée dans le registre R0 est égale 42 alors la prochaine instruction à exécuter se situe à l'adresse mémoire 85 

**Activité n°9.:** Correspondance du langage Python et du langage  assembleur
```python
x = 4
y = 8
if x == 10:
    y = 9
else:
    x = x + 1
z = 6
```

```
   MOV R0, #4
   STR R0,30
   MOV R0, #8
   STR R0,75
   LDR R0,30
   CMP R0, #10
   BNE else
   MOV R0, #9
   STR R0,75
   B endif
else:
   LDR R0,30
   ADD R0, R0, #1
   STR R0,30
endif:
   MOV R0, #6
   STR R0,23
   HALT
```

Après avoir analysé très attentivement le programme en assembleur ci-dessus, vous essaierez d'établir une correspondance entre les lignes du programme en Python et les lignes du programme en assembleur. À quoi sert la ligne "B endif" ? À quoi correspondent les adresses mémoires 23, 75 et 30 ?

## **5. Simulation<a name="_page11_x40.00_y36.92"></a> CPU** 

On utilise un simulateur développé par Peter L Higginson. Ce simulateur est basé sur une architecture de von Neumann. Nous allons trouver dans ce simulateur :  

- une RAM 
- un CPU 

Une version en ligne de ce simulateur est disponible ici :[ http://www.peterhigginson.co.uk/AQA/ ](http://www.peterhigginson.co.uk/AQA/)

![](Aspose.Words.49fb7717-1633-4b59-ac3e-82de7dfc0910.050.jpeg)

Les différentes parties du simulateur : 

- à droite, on trouve la mémoire vive ("main memory") 
- au centre, on trouve le microprocesseur 
- à gauche on trouve la zone d'édition ("Assembly Language"), c'est dans cette zone que nous allons saisir nos programmes en assembleur 

### **5.1. La<a name="_page11_x40.00_y648.92"></a> RAM** 

Par défaut le contenu des différentes cellules de la mémoire est en base 10 (entier signé), mais d'autres options sont possibles : base 10 (entier non-signé, "unsigned"), base 16 ("hex"), base 2 ("binary"). On accède à ces options à l'aide du bouton "OPTIONS" situé en bas dans la partie gauche du simulateur. 



**Activité n°10.:** À l'aide du bouton "OPTIONS", passer à un affichage en binaire. 
Chaque cellule de la mémoire comporte 32 bits (classiquement une cellule de RAM comporte 8 bits). 
Chaque cellule de la mémoire possède une adresse (de 000 à 199), ces adresses sont codées en base 10. 
Repasser à un affichage en base 10 (bouton "OPTION"->"signed") 


### **5.2. Le<a name="_page12_x40.00_y73.92"></a> CPU** 

Dans la partie centrale du simulateur, nous allons trouver en allant du haut vers le bas : 

- le **bloc "registre"** ("Registers") : nous avons 13 registres (R0 à R12) + 1 registre (PC) qui contient l'adresse mémoire de l'instruction en court d'exécution 
- le  **bloc  "unité  de  commande"**  ("Control  Unit")  qui  contient  l'instruction  machine  en  cours d'exécution (au format hexadécimal) 
- le **bloc "unité arithmétique et logique"** ("Arithmetic and Logic Unit") 

### **5.3. programmer<a name="_page12_x40.00_y218.92"></a> en assembleur** 

**Activité n°11.:** Dans la partie "éditeur" ("Assembly Language") saisissez les lignes de codes suivantes : 
```
MOV R0,#42
STR R0,150
HALT
```
Cliquer sur le bouton "submit 

L’assembleur converti les trois lignes du programme en instructions machines :  

- la première instruction est stockée à l’adresse mémoire 000 
- la deuxième à l’adresse 001 
- la troisième à l’adresse 002 

**Activité n°12.:** Exécution pas à pas : 
Il suffit maintenant de cliquer sur le bouton "RUN". Le CPU va "travailler" en direct grâce à de petites animations. Si cela va trop vite (ou trop doucement), on peut régler la vitesse de simulation à l'aide des boutons "<<" et ">>". Un appui sur le bouton "STOP" met en pause la simulation. 
Une fois la simulation terminée, on constate que la cellule mémoire d'adresse 150, contient bien le nombre 42 (en base 10) et que le registre R0 a bien stocké le nombre 42. 
Attention : pour relancer la simulation il faut appuyer sur « RESET » 


**Activité n°13.:** Modifier le programme précédent pour qu'à la fin de l'exécution on trouve le nombre 54 à l'adresse mémoire 50. On utilisera le registre R1 à la place du registre R0. Tester vos modifications en exécutant la simulation. 



**Activité n°14.:** Saisir et tester le programme suivant : 
```
   MOV R0, #4
   STR R0,30
   MOV R0, #8
   STR R0,75
   LDR R0,30
   CMP R0, #10
   BNE else
   MOV R0, #9
   STR R0,75
   B endif
else:
   LDR R0,30
   ADD R0, R0, #1
   STR R0,30
endif:
   MOV R0, #6
   STR R0,23
   HALT
```
