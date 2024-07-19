---
author: ELP
title: 06a Introduction à l’algorithmique
---

**Table des matières** 

1. [Un peu d’histoire](#_page0_x40.00_y471.92)
2. [Efficacité d’un algorithme](#_page1_x40.00_y36.92)
3. [Création d’un algorithme](#_page1_x40.00_y488.92)
4. [Complexité](#_page3_x40.00_y361.92)
5. [Exercices](#_page7_x40.00_y36.92)

On désigne par algorithmique l'ensemble des activités logiques qui relèvent des algorithmes ; en particulier, en informatique, cette discipline désigne l'ensemble des règles et des techniques qui sont impliquées dans la définition et la conception des algorithmes. 

*Sources : Stéphane Grandcolas, Didier Müller, wikipedia* 

<H2 STYLE="COLOR:BLUE;">## 1. Un<a name="_page0_x40.00_y471.92"></a> peu d’histoire</H2> 

![](Aspose.Words.a85c3482-3dff-4bb5-bcc8-000ab623943b.001.png)

Le mot « algorithme » vient du nom du mathématicien perse Al Khwarizmi (780 – 850), qui, au  9ème siècle écrivit le premier ouvrage systématique sur la solution des équations linéaires et  quadratiques. La notion d'algorithme est donc historiquement liée aux manipulations numériques,  mais elle s'est progressivement développée pour porter sur des objets de plus en plus complexes :  des textes, des images, des formules logiques, des objets physiques, etc.  

**Un algorithme est un énoncé d'une suite d'opérations permettant de donner la réponse à un  problème en un temps fini. **

![](Aspose.Words.a85c3482-3dff-4bb5-bcc8-000ab623943b.003.png)

<H2 STYLE="COLOR:BLUE;">## 2. Efficacité<a name="_page1_x40.00_y36.92"></a> d’un algorithme</H2> 

Un algorithme doit être **efficace**. Imaginez par exemple qu'après avoir cherché quelque chose sur un moteur de recherche, il faille attendre plusieurs heures pour avoir le résultat ! Il faut donc être attentif à ce qu'un programme soit assez rapide. Il faut trouver l'idée, l'algorithme qui soit le plus efficace pour résoudre le problème qu'il nous est posé.  

Regardons quelques situations pour lesquelles plusieurs algorithmes existent :  

Pour calculer le nombre de pages d'un livre on peut :  

- Compter les pages une par une (la première, la deuxième,...) jusqu'à arriver à la fin du livre. 
- Regarder directement le numéro de la dernière page du livre. 

De même, quand on va faire ses achats avec sa liste de courses, on peut :  

- Passer dans chaque rayon l'un après l'autre en prenant les produits s'ils sont sur la liste.  
- Aller chercher dans le bon rayon chacun des produits de la liste, l'un après l'autre, dans l'ordre dans lequel ils sont écrits.  

Dans les deux situations ci-dessus, chacune des techniques proposées (des algorithmes utilisés) est correcte car elle donnera le bon résultat. Cependant, certaines sont **beaucoup plus lentes que d'autres** et on ne les utiliserait jamais en pratique. Il nous faut donc un moyen pour pouvoir comparer deux algorithmes, afin de savoir lequel sera le plus rapide.  

Comme le temps d’exécution d’un programme dépend de nombreux paramètres (langage utilisé, processeur, type de mémoire,  talent  du  programmeur,  autre  programmes  en  tache  de  fond,…),  on  ne  pourra  pas  comparer  deux algorithmes en les implémentant. 

Reprenons le premier exemple de l'introduction et essayons de compter le nombre d'actions nécessaires pour mettre en œuvre les deux techniques proposées. On suppose que le livre contient 1000 pages.  

- Technique 1 : on doit regarder chacune des pages, donc on va devoir en regarder 1000 au total. 
- Technique 2 : on ne doit regarder que la dernière page, donc on ne regarde que 1 page au total. 

La deuxième technique est donc 1000 fois plus rapide que la première sur cet exemple de livre.  

Afin d'avoir un résultat généralisable, on va supposer que le livre contient *N* pages. La technique 1 va alors regarder *N* pages au total et elle est donc *N* fois plus lente que la seconde.  

Ainsi pour évaluer l'efficacité d'un algorithme **nous allons compter le nombre d'opérations qu'il effectue**. Il sera alors bien plus facile de le comparer à un autre algorithme résolvant le même problème.  

<H2 STYLE="COLOR:BLUE;">## 3. Création<a name="_page1_x40.00_y488.92"></a> d’un algorithme</H2> 
<H3 STYLE="COLOR:GREEN;">### 3.1. Le<a name="_page1_x40.00_y516.92"></a> pseudo-code</H3> 

Le pseudo-code permet de décrire facilement un algorithme avec un vocabulaire simple et sans connaissance à priori du langage de programmation utilisé pour son implémentation machine. Ce travail d’algorithmique peut se faire sans  ordinateur,  sur  une  simple  **feuille  de  papier.**  En  ayant  comme  connaissances  quelques  principes  de programmation, comme les structures de boucles et les instructions, on peut ainsi échanger en pseudo-code avec une autre personne qui utilise un langage de programmation qu’on ne maitrise pas. 

<H3 STYLE="COLOR:GREEN;">### 3.2. Règles<a name="_page1_x40.00_y618.92"></a> d’écriture d’un algorithme</H3> 

Il existe différentes manières de réaliser une trace de programme et/ou d'algorithmes. Une trace : 

- permet de suivre pas à pas l'algorithme; 
- permet de détecter des erreurs; 
- permet de contrôler que l'algorithme fait bien ce que l'on avant prévu; 
- permet de déterminer ce que fait un algorithme. 

Dans la mesure du possible, on peut organiser une trace d'exécution d'un algorithme en **constituant un tableau avec toutes les variables de l'algorithme**.  

Voici un exemple : 

![](Aimg.png)


Il faut numéroter toutes les lignes de l'algorithme. 

![](Aimg2.png)
 

Voici une trace de l'algorithme avec n=5. Quelle est la valeur de la variable r ? 

|#ligne |n |r |Commentaires |
| - | - | - | - |
|1 |5 |0 |Initialisation |
|2 |5 |0 |0\*0<=5 , on entre dans la ligne 3 |
|3 |5 |1 |r←1 |
|2 |5 |1 |1\*1<=5 , on entre dans la ligne 3 |
|3 |5 |2 |r←2 |
|2 |5 |2 |2\*2<=5 , on entre dans la ligne 3 |
|3 |5 |3 |r←3 |
|2 |5 |3 |3\*3>5 , on sort de la boucle |
|4 |5 |2 |r←2 |

La variable r a pour valeur 2 

En mathématiques, vous auriez une version minimaliste de ce tableau, qui correspondrait à l'état des variables : 

|n |5 |5 |5 |5 |5 |5 |
| - | - | - | - | - | - | - |
|r |0 |0 |1 |2 |3 |2 |

<H3 STYLE="COLOR:GREEN;">### 3.3. Recherche<a name="_page2_x40.00_y447.92"></a> du processus itératif</H3> 

La construction d’un algorithme qui met en jeu un processus itératif s’effectue en 4 étapes : 

1. rechercher l’itération qui s’applique au processus 
2. déterminer si le nombre d’itérations est connu 
3. initialiser les entrées et conditions de boucles 
4. vérifier les sorties de boucle 

Exemple : en septembre 2004, un iceberg de 25 tonnes dérive depuis l’Islande et perd 10 % de sa masse chaque jour. Déterminer à partir de quel jour il reste moins d’une tonne de glace. 

Solution : 

1. le processus itératif est masse restante = masse iceberg – 10 % masse iceberg, appliqué à chaque jour. On incrémente le nombre de jours à chaque fois. 
2. il n’est pas possible de connaître à l’avance le nombre de jours, on utilisera une boucle tantque. 
3. on entre dans la boucle si masse restante est initialisée et masse restante > 1 tonne. Au départ le nombre de jour est 1. 
4. l’opération masse restante = masse iceberg – 10 % masse iceberg converge vers 0 < 1 tonne, on termine forcément. 

```
nombre de jours := 1
masse restante :=

 masse iceberg
tantque masse restante > 1 tonne faire
    masse restante := masse restante – 10 % masse restante
    nombre de jours := nombre de jours + 1
```

<H3 STYLE="COLOR:GREEN;">### 3.4. Correction<a name="_page3_x40.00_y125.92"></a></H3>

Pour s'assurer qu'un algorithme est correct, il faut démontrer deux choses :

1. que l'algorithme se termine (**terminaison**), autrement dit qu'il **ne boucle pas** ou ne diverge pas, produisant au moins un résultat. 
2. que  le  résultat  de  l'algorithme  **satisfait  la  spécification  du  résultat**  comme  énoncé  dans  la description de l'algorithme (**correction partielle**). 

La conjonction de la **correction partielle et de la terminaison** s'appelle la **correction totale.** 

**Remarque pour aller plus loin** : **Correction d’un algorithme itératif :**  L'argument principal de la démonstration de la correction partielle d'un algorithme itératif est la recherche d'un **invariant de boucle**.  

Un invariant est un **prédicat** portant sur les variables du programme qui doit être stable lors de l'exécution de la boucle :  **l'invariant est satisfait avant, pendant et après l'exécution du corps de la boucle**. 

<H2 STYLE="COLOR:BLUE;">## 4. Complexité<a name="_page3_x40.00_y361.92"></a></H2> 

Un algorithme est implémenté dans un langage spécifique (Java, C, Python,...) et va s'exécuter sur une machine. 

La durée d'exécution du programme va dépendre du nombre d'instructions élémentaires mobilisées lors de son exécution. On parle alors de **complexité temporelle.** 

Le programme va également mobiliser un certain nombre de ressources machines, en particulier la mémoire. On parle alors de complexité spatiale.  

Être capable d'évaluer la complexité d'un algorithme est importante, tout particulièrement, dans le cadre du traitement de données importantes (big data). Cela va permettre de sélectionner l'algorithme le plus performant en fonction des données à traiter. 

On va donc effectuer des calculs sur l’algorithme en lui-même, dans sa version "papier". Les résultats de ces calculs fourniront une **estimation du temps d’exécution de l’algorithme lors de son fonctionnement.** 

<H3 STYLE="COLOR:GREEN;">### 4.1. Complexité<a name="_page3_x40.00_y529.92"></a> temporelle</H3> 
<H4 STYLE="COLOR:MAGENTA;">#### 4.1.1. Règles<a name="_page3_x40.00_y549.92"></a> de calcul</H4> 

Pour calculer la complexité, il faut examiner chaque ligne de code et l'y attribuer un **coût en temps.** 

Le coût ainsi obtenu n'aura pas d'unité, il s'agit d'un nombre d'opérations dont chacune aurait le même temps d’exécution : 1. Les opérations qui vont devoir être comptabilisées sont : 

- Les affectations comptent pour 1 unité de temps: a←2 

- Les comparaisons comptent pour 1 unité de temps: 2<3  

- L'accès aux mémoires  comptent pour une 1 unité de temps et afficher pour 2 unités de temps: Lire a  Afficher a 
- Chaque opération élémentaire compte pour une 1 unité de temps : 3+2  

Déterminons le coût de la ligne de code suivante : 

a←a+1 

T(n) = 1(affectation) + 1(accès à la mémoire) + 1(addition) = 3 

On ne comptera **pas la définition des fonctions**. 

<H4 STYLE="COLOR:MAGENTA;">#### 4.1.2. Algorithmes<a name="_page4_x40.00_y124.92"></a> sans structure de contrôle</H4> 

<H3 STYLE="COLOR:red;">**Activité n°1.:** Le coût T(n) de cet algorithme écrit en python.</H3>

![](Aimg3.png)


T(n) = 1(//) + 1(affectation) + 1 (mémoire) + 1(\*) + 1(-) + 1(//) + 1(affectation) + 2 (mémoire) + 1(%) + 1 affectation + 1 (mémoire) + 3(accès mémoire) = 15 

![](Aspose.Words.a85c3482-3dff-4bb5-bcc8-000ab623943b.018.png)

Le coût C est constant et ne dépend pas de n, on le note alors O(1) en notation de Landau.  

O caractérise le comportement asymptotique quand n → +∞.  

<H4 STYLE="COLOR:MAGENTA;">#### 4.1.3. Algorithmes sans structure conditionnelle</H4> 

<H3 STYLE="COLOR:red;">**Activité n°2.:** On s’intéresse à la fonction (−1)<sup>n</sup>.  Le coût T(n) de cet algorithme écrit en python.</H3>

![](Aimg4.png)

T(n) = 1(comparaison) + 1(%) + 1 (mémoire) + 1(affectation) + 1(accès mémoire) = 5 

<H4 STYLE="COLOR:MAGENTA;">#### 4.1.4. Algorithmes<a name="_page4_x40.00_y507.92"></a> avec structure itérative</H4> 

<H3 STYLE="COLOR:red;">**Activité n°3.:** On s’intéresse à la fonction qui utilise une structure for pour calculer la somme des n premiers entiers.** Le coût T(n) de cet algorithme écrit en python.</H3>

![](Aimg5.png)

T(n)   = 1(affectation) + (n + 1) \*[1(+) +1(affectation) +1(mémoire) +1(affectation)] + 1(accès mémoire)  

= 1 + (n + 1) \* 4 + 1  
= 2 + 4n + 4
= 4n + 6

La complexité de cet algorithme est dite **linéaire.**  

Ce sera le cas de tous les algorithmes avec un coût du type : **T(n)=an + b** où a et b sont des réels. 

Ici, le coût dépend linéairement du nombre d’éléments à traiter. On le note O(n).

<H4 STYLE="COLOR:MAGENTA;">#### 4.1.5. Algorithmes<a name="_page5_x40.00_y36.92"></a> avec deux structures itératives imbriquées</H4> 

<H3 STYLE="COLOR:red;">**Activité n°4.:** On considère que la taille des listes mots et fichiers\_test sont de n.**  La complexité T(n) de cet algorithme écrit en python.</H3>

![](Aimg6.png)

T(n)  = 1(affectation)+n\*[n \*[1(comparaison)+1(affectation+1(mémoire))]+1(mémoire)  

= 1 + n \* (n \* 3) + 1  
= 2 + 3 n²  

La complexité de cet algorithme est dite **quadratique**.  

Ce sera le cas de tous les algorithmes avec un coût du type : **T(n)=an² + bn + c** où a, b et c sont des réels. 

Le coût est fonction du carré du nombre d’éléments à traiter. On le note O(n²).

<H3 STYLE="COLOR:GREEN;">### 4.2. Complexité<a name="_page5_x40.00_y322.92"></a> en espace</H3> 

La complexité en espace est une mesure de l'espace utilisé par un algorithme, exprimé comme fonction de la taille de l'entrée. L'espace compte le nombre maximum de cases mémoire utilisées simultanément pendant un calcul. 

<H3 STYLE="COLOR:GREEN;">### 4.3. Echelle<a name="_page5_x40.00_y386.92"></a> de comparaisons</H3> 

L'étude des différents algorithmes proposés dans la suite des activités (Tris, Recherche, Knn,...) permettra de mettre en évidence les différents ordres de grandeur suivants.  

|**Ordre de complexité**|**Exemples** |**Type de complexité** |
| - | - | - |
|O(1) |Ici la complexité ne dépend pas des données. Accès à une cellule d'un tableau. |constante |
|O(log(n)) |Algorithme divisant le problème par une constante k. O(log(n)) pour la recherche dichotomique  |Logarithmique |
|O(n) |Parcours de liste. |linéaire |
|O(n.log(n)) |Algorithme  divisant  le  problème 

 en  nombre  de  sous-problèmes constants, dont les résultats sont réutilisés par recombinaison (Ex Tri fusion). |quasi-linéaire |
|O(n²) |Algorithme  traitant  généralement  de  couples  de  données  (boucles imbriquées). Parcours d'une matrice de pixels. |quadratique |

![](Aspose.Words.a85c3482-3dff-4bb5-bcc8-000ab623943b.032.jpeg)

Comparaison des temps d’exécution d’algorithmes de différentes complexités 

![](Aspose.Words.a85c3482-3dff-4bb5-bcc8-000ab623943b.033.jpeg)

Si on double la taille d’un tableau : 

- Pour un algorithme de complexité n, le temps d’exécution est doublé 
- Pour un algorithme de complexité n², le temps d’exécution est quadruplé 
- Pour un algorithme de complexité log2(n), le temps d’exécution prend une unité. 

RESSOURCES : 

- Vidéo (définition de la complexité) :[ https://www.youtube.com/watch?v=exaHKrP6RsA ](https://www.youtube.com/watch?v=exaHKrP6RsA)
- Vidéo (calcul de complexités) :[ https://www.youtube.com/watch?v=clZ4q5zPBlE ](https://www.youtube.com/watch?v=clZ4q5zPBlE)![](Aspose.Words.a85c3482-3dff-4bb5-bcc8-000ab623943b.002.png)

<H2 STYLE="COLOR:BLUE;">## 5. Exercices<a name="_page7_x40.00_y36.92"></a></H2>

<H3 STYLE="COLOR:red;">**Exercice 1** : Calculer le coût de cet algorithme</H3>

```
largeur <- LireEntier() 
longueur <- LireEntier() 
aire <- largeur \* longueur 
perimetre <- (largeur + longueur) \* 2 
Afficher aire 
Afficher perimetre 
```

<H3 STYLE="COLOR:red;">**Exercice 2** : Calculer le coût de cet algorithme</H3>

```
nbLivres <- LireEntier() 
Si nbLivres < 10 
    prix <- nbLivres \* 10 
Sinon 
    prix <- nbLivres \* 9 
Afficher prix 
```

<H3 STYLE="COLOR:red;">**Exercice 3** : Calculer le coût de cet algorithme</H3>

```
X <- 1 
Tant que X <= 100 
    Afficher "Bonjour !"    
    X <- X + 1 
```

<H3 STYLE="COLOR:red;">**Exercice 4** : Calculer le coût de cet algorithme</H3>

```
total <- 0 
i <- 1 
Tant que i <= 100 
    total <- total + i    
    i <- i + 1 
Afficher total 
```

<H3 STYLE="COLOR:red;">**Exercice 5** : Calculer le coût de cet algorithme</H3>

```
iMax <- LireEntier() 
total <- 0 
i <- 1 
Tant que i <= iMax 
    total <- total + i    
    i <- i + 1 
Afficher total 
```

<H3 STYLE="COLOR:red;">**Exercice 6** : Calculer le coût de cet algorithme</H3>

```
iMax <- LireEntier() 
total <- 0 
Tant que iMax > 0 
    total <- total + iMax    
    iMax <- iMax - 1 
Afficher total 
```

<H3 STYLE="COLOR:red;">**Exercice 7** : Calculer le coût de cet algorithme</H3>

```
taille <- LireEntier()			1
X <- 0						    2
Tant que X < taille				3
   Y <- 0					    4
   Tant que Y < taille			5
      Si X = Y					6
         Afficher "X"			7
      Sinon					    8
         Afficher "."			9		
      Y <- Y + 1				10
   Retour à la ligne			11
   X <- X + 1		            12
```
