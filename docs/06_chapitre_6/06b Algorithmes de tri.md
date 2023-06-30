---
author: ELP
title: Chapitre 6 - Algorithmes de tri
---


**Table des matières** 

1. [Créer une liste de données aléatoire](#_page0_x40.00_y438.92)
2. [Le tri par sélection](#_page1_x40.00_y54.92)
3. [Tri par insertion](#_page4_x40.00_y702.92)
4. [Autres algorithmes de tris : le tri à bulles (Bubble sort) ](#_page8_x40.00_y36.92)
4. [Exercices ](#_page9_x40.00_y511.92)

Introduction : Qu’est-ce que trier ? Pourquoi trier ? 

1. **Créer<a name="_page0_x40.00_y438.92"></a> une liste de données aléatoire** 

**Ce premier script sera nécessaire dans tous les algorithmes de tri.** 

**Activité n°1.:** Commencer par créer des données de façon aléatoire grâce au module random afin de pouvoir les classer. 

import random ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.001.png)

def genere\_liste\_aleatoire(N, n): 

`    `"""Génére une liste aléatoire de N éléments compris entre 0 et n"""     ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.002.png)return [random.randrange(n) for i in range(N)] 

- Création d'une liste de 50 valeurs comprises entre 0 et 100 liste\_aleatoire = genere\_liste\_aleatoire(50, 100) print(liste\_aleatoire) 

\>>>  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.003.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.004.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.005.png)

[1, 76, 61, 88, 38, 34, 89, 91, 78, 30, 19, 37, 16, 56, 90, 95, 67, 17, 29, 61, 60, 37, 4, 62, 79, 18, 13, 58, 10, 18, 53, 71, 44, 25, 95, 83, 48, 79, 32, 72, 83, 85, 11, 73, 21, 82, 50, 0, 31, 62] ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)

2. **Le<a name="_page1_x40.00_y54.92"></a> tri par sélection :** 
1. **Le<a name="_page1_x40.00_y76.92"></a> principe** 

Sur un tableau de N éléments (numérotés de 0 à N), le principe du tri par sélection est le suivant : ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.007.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.008.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.009.png)

- **Rechercher le plus petit élément** du tableau, et l'échanger avec l'élément d'indice 0 ; 
- **Rechercher le second plus petit élément** du tableau, et l'échanger avec l'élément d'indice 1 ; 
- Continuer de cette façon jusqu'à ce que le tableau soit entièrement trié.
2. **Illustration<a name="_page1_x40.00_y201.92"></a> graphique** 

Exemple : Soit la suite de nombres suivante : 6, 1, 9, 3. Trions cette suite avec l’algorithme du tri par  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.010.png)sélection dans l’ordre croissant :  

*1er tour* : 6, **1**, 9, 3 -> le plus petit élément du tableau est 1, on le place donc sur la première case (en  l'échangeant avec le 6).  

*2ème tour* : 1, 6, 9, **3** -> le deuxième plus petit élément est 3, on le place sur la deuxième case et on  l’échange avec le 6.  

*3ème tour* : 1, 3, 9, **6** -> le troisième plus petit élément est 6, on l’échange avec 9 pour le placer sur la  troisième case.  

*4ème tour* : 1, 3, 6, **9** -> le quatrième plus petit élément du tableau est 9, il est déjà en quatrième  position on ne fait rien.  

Ce tri se décompose réellement en deux étapes distinctes : À chaque tour, on cherche le minimum dans  l'espace non trié du tableau (le minimum est représenté en bleu, et la partie non triée en blanc), ensuite on déplace cet élément à sa place définitive (représentée en vert). En faisant cela pour chaque élément du tableau, ce dernier se retrouve trié au bout de N tours maximum (N étant la taille du tableau). 

3. **Illustration<a name="_page1_x40.00_y434.92"></a> en vidéo** 

Vidéo :[ https://www.youtube.com/watch?v=Ns4TPTC8whw ](https://www.youtube.com/watch?v=Ns4TPTC8whw)Attention : les danseurs s’échangent (si nécessaire) à chaque fois alors que le vrai algorithme ne procède à l’échange qu’à la fin de chaque tour  

4. **Pseudo-code<a name="_page1_x40.00_y485.92"></a>** 

ALGORITHME tri\_selection ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.011.png)

DEBUT 

`    `PROCEDURE echange (T, i, j)      # on échange la valeur de T[i] avec celle de T[j]         tmp <- T[i]                 # variable temporaire pour stocker 

`        `T[i] <- T[j] 

`        `T[j] <- tmp 

`    `PROCEDURE tri\_sélection (T) 

`        `POUR i ALLANT DE 1 A N [SAUT DE 1] FAIRE    # parcours  

`            `mini <- i                                # on stocke l'indice du premier terme

`            `POUR j ALLANT DE i+1 A N [SAUT DE 1]    # parcours 

`                `SI T[j] < T[mini] ALORS           # si la valeur stockée n'est pas la plus petite                     mini <- j                        

`                `FIN SI 

`                `j <- j + 1 

`            `FIN POUR 

`            `SI mini =! i ALORS           # donc la condition SI a été vérifié 

`                `echange(T, i, mini)              # on :appelle la procédure d'échange             FIN SI 

`            `i <- i + 1 

`        `FIN POUR     

FIN ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)

Première NSI   Chap 2 : Algorithmes de tri  Page 2/16 
5. **Complexité<a name="_page2_x40.00_y36.92"></a>** 

Le tri par sélection a une complexité en O(N²) : Calculons le nombre d’itérations 

`                        `DEBUT ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.012.png)

`                            `PROCEDURE echange (T, i, j) 

1                               tmp <- T[i]                                  1                               T[i] <- T[j]  

1                               T[j] <- tmp 

`                            `PROCEDURE tri\_sélection (T) 

N fois                          POUR i ALLANT DE 1 A N [SAUT DE 1] FAIRE   

`    `1                               mini <- i                                 

`    `N-1 fois                        POUR j ALLANT DE i+1 A N [SAUT DE 1]                                  1                               SI T[j] < T[mini] ALORS               

`        `1 (pire cas)                        mini <- j      

`                                        `FIN SI 

`        `1+1 pour le calcul              j <- j + 1 

`                                    `FIN POUR 

`    `N-1 (pire cas)                  SI mini =! i FAIRE                        

`                                        `echange(T, i, mini)            

`                                    `FIN SI 

`    `1+1 pour le calcul              i <- i + 1  

`                                `FIN POUR     

`                        `FIN 

Procédure d’échange 3 opérations pour chaque échange 

Procédure tri\_sélection : 

- Boucle « POUR j ALLANT DE i+1 A N» : (N-1) x 4 
- Si min =! i FAIRE echange (T, T[i], T[min]) : (N-1) x 3       
- Boucle « POUR i ALLANT DE 1 A N» : N x (1 + (N-1) x 4 + (N-1) x 3 +2)  

Donc le nombre d’itérations dans le pire des cas : N x (3+4N-4+3N-3) = N x (7N – 4) = 7 N² -4 N 

*Pour aller plus loin : De la même manière en ne s’intéressant qu’aux boucle, dans le pire des cas, chaque élément est inséré au début de la partie trié. Dans ce cas, tous les éléments de la partie triée doivent être déplacés à chaque itération. La ième itération génère (i-1) comparaisons et échanges de valeurs :* 

( − 1)

- − 1 =

2

=1

**Conclusion** : Le **tri par sélection** est donc un algorithme assez simple, mais peu efficace à cause de sa complexité en ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.013.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.014.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.015.png)**O(N²) dans le meilleur des cas ou dans le pire des cas.**  

On parle aussi de **complexité quadratique.** 

Le tri par sélection sert de base à d'autres algorithmes plus efficaces que nous étudierons plus tard. C’est un tri instable et en place (travail sur la structure et non sur une copie).

6. **Stabilité<a name="_page2_x40.00_y632.92"></a> d’un algorithme** 

On dit qu'un algorithme de tri est ***stable*** s'il ne modifie pas l'ordre initial des clés identiques. 

Par exemple, imaginez que vous vouliez trier la collection de bouteilles ci-dessous par ordre de volume (le volume est indiqué sous la bouteille) : ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.016.png)

Première NSI   Chap 4 : Algorithmes de tri  Page 4/16 

Si vous obtenez ceci, alors votre tri n'était **pas stable** : 

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.017.png)

En effet, la bouteille noire de volume *1* se trouve maintenant avant la bouteille bleue de même volume alors qu'elle devrait être après. Il en est de même pour les deux bouteilles de volume *4* qui sont inversées par rapport à l'ordre initial. 

Avec un **tri stable**, on aurait obtenu : 

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.018.png)

L'intérêt d'un tri stable est **qu'on peut appliquer ce tri successivement, avec des critères différents.**  

7. **Preuve<a name="_page3_x40.00_y297.92"></a> de correction** 

**Recherche de l’invariant de boucle** : Deux éléments ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.019.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.020.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.021.png)

- Au début de la ième étape, les i-1 premiers éléments du tableau sont triés par ordre croissant. 
- Au début de la ième étape, les éléments de rang supérieurs ou égal à i sont tous supérieurs au i-1ème élément 

D’où la correction de cet algorithme 

On a deux boucles for qui sont imbriquées  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.022.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.023.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.024.png)

- À chaque tour de la boucle extérieure, la liste restante diminue. 
- À chaque tour de la boucle intérieure, j augmente. Elle s’arrête bien. 

**La terminaison est assurée** 

8. **Implémentation<a name="_page3_x40.00_y497.92"></a> en Python** 

**Activité n°2.:** Création de la liste aléatoire **avec l’activité 1** ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.025.png)

- Création d'une liste de 5 valeurs comprises entre 0 et 20 à trier data = genere\_liste\_aleatoire(5, 20) 

print("Liste initiale: ", data) 

**Activité n°3.: implémentation classique** : ajouter à l’activité 2 les deux fonctions suivantes : ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.026.png)

def swap(T : list, i : int, j : int) -> list: 

`    `""" fonction permutation (à garder elle sert beaucoup!!)  """     T[i] , T[j] = T[j] , T[i]  

`    `return T 

def selection\_sort(T : list) -> list: 

`    `""" fonction tri par sélection recherche de la valeur minimum dans une liste     puis permutation avec indice précédent """ ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.027.png)

`    `for i in range(len(T)): 

`        `mini = i                        # au départ mini = i = 0 ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.028.png)

`        `for j in range(i+1, len(T)):    # au départ j = 1 

`            `if T[j] < T[mini]:          # on compare chaque T[j] à T[mini] ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.029.png)

`                `mini = j 

`        `if mini != i : 

`            `swap(T, i, mini ) 

`    `return T 

print("Liste triée   : ", selection\_sort(data)) ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)

Première NSI   Chap 6 : Algorithmes de tri  Page 6/16 

\>>>  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.030.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.031.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.032.png)

Liste initiale:  [9, 16, 14, 12, 7] Liste triée   :  [7, 9, 12, 14, 16] 

**Activité n°4.: Tri par sélection et temps d’exécution** : ajouter ce script aux fonctions de l’activité précédente en mettant en commentaire les deux print précédent : 

import time ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.033.png)

- on fait une moyenne sur plusieurs tris de tableau de même longueur somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(1\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `selection\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 1\_000: %s secondes ---" % (moyenne)) 

somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(2\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `selection\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 2\_000: %s secondes ---" % (moyenne)) 

somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(10\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `selection\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 10\_000: %s secondes ---" % (moyenne)) 

\>>>  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.034.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.035.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.005.png)

Temps d execution pour 1\_000: 0.048070335388183595 secondes --- Temps d execution pour 2\_000: 0.16699233055114746 secondes --- Temps d execution pour 10\_000: 4.141367197036743 secondes --- 

On voit bien que multiplier par 10 le nombre d’éléments du tableau à trier revient à multiplier le temps par 10². **Animation :[** http://lwh.free.fr/pages/algo/tri/tri_selection.html ](http://lwh.free.fr/pages/algo/tri/tri_selection.html)**

3. **Tri<a name="_page4_x40.00_y702.92"></a> par insertion** 
1. **Le<a name="_page4_x40.00_y724.92"></a> principe** 

Le tri par insertion est un algorithme de **tri stable** et le plus rapide en pratique sur une entrée de petite taille. ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)

**Principe de l’algorithme :** Le principe du tri par insertion est de trier les éléments du tableau comme avec des cartes:** 

- On prend nos cartes mélangées dans notre main. 
- On crée deux ensembles de carte, l’un correspond à l’ensemble de carte triée, l’autre contient l’ensemble des cartes restantes (non triées). 
- On prend au fur et à mesure, une carte dans l’ensemble non trié et on l’insère à sa bonne place dans l’ensemble de carte triée. 
- On répète cette opération tant qu’il y a des cartes dans l’ensemble non trié. 

Dans l'algorithme, on parcourt le tableau à trier du début à la fin. Au moment où on considère le i-ème élément, les éléments qui le précèdent sont déjà triés.  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.036.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.037.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.038.png)

L'objectif d'une étape est donc d'insérer le i-ème élément à sa place parmi ceux qui précèdent. Il faut pour cela : 

- **trouver où l'élément** doit être inséré en le comparant aux autres,  
- puis **décaler les éléments** afin de pouvoir effectuer l'insertion.  

En pratique, ces deux actions sont fréquemment effectuées en une passe, qui consiste à faire « remonter » l'élément au fur et à mesure jusqu'à rencontrer un élément plus petit. 

2. **Illustration<a name="_page5_x40.00_y290.92"></a> graphique  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.039.png)**

Exemple : 9, 2, 7, 1 à trier en ordre croissant avec l’algorithme du tri par insertion :  

*1er tour* : 9 | **2**, 7, 1 -> à gauche la partie triée du tableau (le premier élément est considéré comme trié  puisqu'il est seul dans cette partie), à droite la partie non triée. On prend le premier élément de la partie  non triée, 2, et on l'insère à sa place dans la partie triée, c'est-à-dire à gauche de 9.  

*2ème tour* : 2, 9 | **7**, 1 -> on prend 7, et on le place entre 2 et 9 dans la partie triée.  

*3ème tour* : 2, 7, 9 | **1** -> on continue avec 1 que l’on place au début de la première partie.  

Pour insérer un élément dans la partie triée, on parcourt de droite à gauche tant que l'élément est plus  grand que celui que l'on souhaite insérer. Pour résumer l'idée de l'algorithme : La partie verte du tableau  est la partie triée, l'élément en bleu est le prochain élément non trié à placer et la partie blanche est la  partie non triée. 

3. **Illustration<a name="_page5_x40.00_y491.92"></a> vidéo** 

Vidéo :[ https://www.youtube.com/watch?v=ROalU379l3U ](https://www.youtube.com/watch?v=ROalU379l3U)

4. **Pseudo-code<a name="_page5_x40.00_y542.92"></a>** 

ALGORITHME tri\_insertion ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.040.png)

DEBUT 

`    `PROCEDURE insere(T, i)            # insère tmp dans le tableau[0...i[ trié 

`        `tmp = T[i]             # valeur à inserer 

`        `j <- i-1  # indice en cours                                                            TANT QUE j >= 0 et T[j] > tmp ALORS         

`            `T[j+1] <- T [j]          

- l'élément qui précède on le décale vers la droite jusqu'à laisser la place libre à tmp            

`            `j <- j - 1                # on décale l'indice 

`        `FIN TANT QUE 

`        `T[j+1] <- tmp     # on insère tmp 

`    `PROCEDURE tri\_insertion(T)      

`        `POUR i ALLANT DE 1 A n [SAUT DE 1] FAIRE                      insere (T, i)              

`            `i <- i + 1                                              FIN POUR 

FIN ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)

Première NSI   Chap 8 : Algorithmes de tri  Page 8/16 
5. **Complexité<a name="_page6_x40.00_y36.92"></a>**  

L’algorithme du tri par insertion a une complexité de O(N2). Calculons le nombre d’instructions : 

`                    `DEBUT ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.041.png)

`                        `PROCEDURE insere(T, i, tmp)                      

`                            `i, j, tmp ENTIERS 

1                           j <- i                                                           N-1 fois                    TANT QUE j > 0 et T[j-1] > tmp ALORS         

`    `1                           T[j] <- T [j-1]                          

`    `1                           j <- j - 1                               

`                            `FIN TANT QUE 

1                           T[j] <- tmp                                    

`                        `PROCEDURE tri\_insertion(T)      

`                            `i, ENTIERS                                                      N fois                      POUR i ALLANT DE 1 A n [SAUT DE 1] FAIRE          

`    `insere                      insere (T, i, T[i])              

`    `1                           i <- i + 1                                      

`                            `FIN POUR 

`                    `FIN 

- Procédure insere : 1 + (N – 1) x 2 + 1 = 2 + (N – 1) x 2 = 2 N 
- Procédure tri\_insertion : N x (2N +1) = 2 N² + N 

Pour simplifier les calculs de complexité, on s’intéresse seulement aux nombres de itérations des boucles, puisque c’est elles qui vont donner le comportement asymptotique (quand N très grand). 

*Pour aller plus loin : Exemple t = [ 4, 3, 2, 1]* 

*Le 2ème élément : le « 3 » est décalé d’un cran vers la gauche [ 3, 4, 2, 1]* 

*Le 3ème élément : le « 2 » est décalé de deux crans vers la gauche [ 2, 3, 4, 1]* 

*Le 4ème élément : le « 1 » est décalé de trois crans vers la gauche [ 1, 2, 3, 4]* 

*Pour trouver le plus petit élément, (n-1) itérations sont nécessaires, pour le 2ème plus petit élément, (n-2) itérations sont effectuées, .… Pour trouver le dernier plus petit élément, 0 itération sont effectuées.* 

*Le nombre de itérations des deux boucles est 1 + 2 + 3 = 6 c’est-à-dire* ∑3

=1

*Donc le pire des cas, le tableau est trié à l’envers, pour chaque valeur i on compte N - 1 passages dans la boucle for :* 

−1

( − 1)

- =

2

=1

**Conclusion** : le **tri par insertion** a une complexité en temps de **O(N²) dans le pire des cas O(N) dans le ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.042.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.043.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.044.png)meilleur des cas (tableau déjà trié).**  

Cependant des améliorations et des variantes permettent de le rendre plus rapide comme le tri shell. C’est un algorithme stable et en place (travail sur la structure et non sur la copie).

6. **Preuve<a name="_page6_x40.00_y637.92"></a> de correction** 

Recherche de **l’invariant de boucle** : Deux éléments ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.045.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.046.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.047.png)

- Boucle for : A la ième étape, les i premiers éléments du tableau sont triés par ordre croissant. 
- Boucle while : A la fin de la jème étape, la valeur que l’on cherche à insérer est plus petite que toutes les valeurs de l’indice j+1 à l’indice i 

D’où la correction de cet algorithme 

La boucle for se termine forcément. Pour la boucle while, on part de j qui vaut n jusqu’à 0. **La terminaison est assurée.** ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)

Première NSI   Chap 10 : Algorithmes de tri  Page 10/16 

7. **Implémentation<a name="_page7_x40.00_y36.92"></a> en Python** 

**Activité n°5.:** Création de la liste aléatoire **avec l’activité 1** : reprendre l’activité 1 ou 2 

**Activité n°6.: implémentation classique** : ajouter à l’activité précédente les deux fonctions suivantes : ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.048.png)

def insert(T, i): 

`    `""" fonction qui insère la valeur T[i] à la bonne place dans le tableau"""     ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.049.png)tmp = T[i] 

`    `j = i - 1 

`    `while j >= 0 and T[j] > tmp: 

`        `T[j+1] = T[j] 

`        `j = j - 1 

`    `T[j+1] = tmp 

def insertion\_sort(T): 

""" fonction tri par insertion parcours du vecteur avec décalage ascendant des éléments """ ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.050.png)    for i in range(1,len(T)): 

`        `insert(T, i) 

`    `return T 

print("Liste triée   : ", insertion\_sort(data)) 

**Remarque : on aurait pu également faire une seule fonction**  

**Activité n°7.: Tri par insertion et temps d’exécution** : ajouter ce script aux fonctions de l’activité précédente en mettant en commentaire les deux print précédent : 

import time ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.051.png)

- on fait une moyenne sur plusieurs tris de tableau de même longueur somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(1\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `insertion\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 1\_000: %s secondes ---" % (moyenne)) 

somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(2\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `insertion\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 2\_000: %s secondes ---" % (moyenne)) 

somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(10\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `insertion\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 10\_000: %s secondes ---" % (moyenne)) 

\>>>  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.052.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.053.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.054.png)

Temps d execution pour 1\_000: 0.06062502861022949 secondes --- Temps d execution pour 2\_000: 0.23924431800842286 secondes --- Temps d execution pour 10\_000: 6.42768611907959 secondes --- 

**Animation :[ http://lwh.free.fr/pages/algo/tri/tri_insertion.html ](http://lwh.free.fr/pages/algo/tri/tri_insertion.html)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)**

Première NSI   Chap 12 : Algorithmes de tri  Page 12/16 

4. **Autres<a name="_page8_x40.00_y36.92"></a> algorithmes de tris : le tri à bulles (Bubble sort)** 

Le tri à bulles est un algorithme de tri qui consiste à faire  **remonter  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.055.png)progressivement les plus petits éléments d'une liste**, comme les bulles  d'air remontent à la surface d'un liquide.  

L'algorithme  parcourt  la  liste,  et  **compare  les  couples  d'éléments  successifs**.   

Lorsque deux éléments successifs ne sont pas dans l'ordre croissant, **ils  sont échangés**.   

Après chaque parcours complet de la liste, l'algorithme **recommence l'opération**. Lorsque aucun échange n'a lieu pendant un parcours, cela signifie que la liste est triée : l'algorithme peut s'arrêter. 

On optimise l’algorithme en se basant sur la propriété que le dernier élément permuté se trouve nécessairement bien trié. Il n’est alors pas besoin de parcourir la liste jusqu’à la fin : combsort (tri à peignes) 

**Conclusion** : Le tri à bulles présente une complexité en **O(N²)** dans le pire des cas (où N est la longueur de la liste), et en O(N) dans le cas où le tableau est déjà ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.056.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.057.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.058.png)trié, ce qui le classe parmi les mauvais algorithmes de tri. Il n'est donc quasiment pas utilisé en pratique. 

Comme le tri par insertion, le tri à bulle est un tri stable. Illustration vidéo :[ https://www.youtube.com/watch?v=lyZQPjUT5B4 ](https://www.youtube.com/watch?v=lyZQPjUT5B4) 

**Activité n°8.:** Création de la liste aléatoire **avec l’activité 1** : reprendre l’activité 1 ou 2 

**Activité n°9.: implémentation classique Avec la fonction echange et la fonction bubble\_sort** 

def swap(T : list, i : int, j : int) -> list: ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.059.png)

`    `""" fonction permutation (à garder elle sert beaucoup!!)  """     T[i] , T[j] = T[j] , T[i] 

`    `return T 

def bubble\_sort(T : list) -> list: 

`    `""" fonction tri a bulle permutation des éléments 2 à 2 en faisant remonter     la plus grande valeur en fin de la liste  """ ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.060.png)

`    `for i in range(len(T) - 1): # ou for i in range(len(T)) mais tour pour rien ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.061.png)        for j in range(len(T) - 1): 

`            `if T[j] > T[j + 1]: 

`                `swap(T, j, j + 1) 

`    `return T 

\>>> ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.030.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.062.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.032.png)

Liste initiale:  [1, 14, 6, 17, 11] Liste triée   :  [1, 6, 11, 14, 17] 

**Remarque : il existe d’autres versions du tri bulle** 

**Activité n°10.: Tri bulle et temps d’exécution** : ajouter ce script aux fonctions de l’activité précédente en mettant en commentaire les deux print précédent : ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)

Première NSI   Chap 14 : Algorithmes de tri  Page 14/16 

import time ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.063.png)

- on fait une moyenne sur plusieurs tris de tableau de même longueur somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(1\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `bubble\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 1\_000: %s secondes ---" % (moyenne)) 

somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(2\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `bubble\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 2\_000: %s secondes ---" % (moyenne)) 

somme\_des\_durees = 0 

for i in range(5): 

`    `liste = genere\_liste\_aleatoire(10\_000, 1\_000\_000) 

`    `start\_time=time.time() 

`    `bubble\_sort(liste) 

`    `somme\_des\_durees = somme\_des\_durees + time.time() - start\_time moyenne = somme\_des\_durees/5 

print("Temps d execution pour 10\_000: %s secondes ---" % (moyenne)) 

\>>>  ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.064.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.065.png)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.066.png)

Mesure de la durée de plusieurs tris 

Temps d execution pour 100: 0.002393150329589844 secondes --- Temps d execution pour 1\_000: 0.22002701759338378 secondes --- 

Animation :[ http://lwh.free.fr/pages/algo/tri/tri_bulle.html ](http://lwh.free.fr/pages/algo/tri/tri_bulle.html)

5. **Exercices<a name="_page9_x40.00_y511.92"></a>** 

**Exercice n°1** : Créer une fonction selection\_sort\_desc() qui permet trier avec l’algorithme de tri par sélection une liste aléatoire par valeurs décroissantes. 

**Exercice n°2** : Créer une fonction selection\_sort\_asc\_partir\_fin() qui permet trier avec l’algorithme de tri par sélection une liste aléatoire par valeurs croissantes de manière à compléter l’algorithme suivant :  

def selection\_sort\_asc\_partir\_fin(*T*): *![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.067.png)*    for i in range(…, 0, …): 

`        `maxi = … 

`        `for j in range(…): 

`            `if *T*[j]> *T*[…]: 

`                `maxi = j 

`        `if maxi !=i: 

`            `… 

`    `return *T* 

**Exercice n°3** : Créer une fonction selection\_sort\_desc\_partir\_fin() qui permet trier avec l’algorithme de tri par sélection et l’algorithme de l’exercice 2, une liste aléatoire par valeurs décroissantes. 

**Exercice n°4** : Créer une fonction bubble\_sort\_desc() qui permet trier avec l’algorithme de tri à bulles une liste aléatoire par valeurs décroissantes. ![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)
Première NSI   Chap 7 : Algorithmes de tri  Page 16/16 
