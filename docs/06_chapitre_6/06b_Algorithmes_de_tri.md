---
author: ELP
title: 06b Algorithmes de tri
---


**Table des matières** 

1. [Créer une liste de données aléatoire](#_page0_x40.00_y438.92)
2. [Le tri par sélection](#_page1_x40.00_y54.92)
3. [Tri par insertion](#_page4_x40.00_y702.92)
4. [Autres algorithmes de tris : le tri à bulles (Bubble sort) ](#_page8_x40.00_y36.92)
4. [Exercices ](#_page9_x40.00_y511.92)

Introduction : Qu’est-ce que trier ? Pourquoi trier ? 

## **1. Créer<a name="_page0_x40.00_y438.92"></a> une liste de données aléatoire** 

**Ce premier script sera nécessaire dans tous les algorithmes de tri.** 

**Activité n°1.:** Commencer par créer des données de façon aléatoire grâce au module random afin de pouvoir les classer. 

```python
import random
def genere_liste_aleatoire(N, n):
    """Génére une liste aléatoire de N éléments compris entre 0 et n"""
    return [random.randrange(n) for i in range(N)]

# Création d'une liste de 50 valeurs comprises entre 0 et 100
liste_aleatoire = genere_liste_aleatoire(50, 100)
print(liste_aleatoire)
```
???+ question "Faire ce qui est proposé"

    {{ IDE() }}

## **2. Le<a name="_page1_x40.00_y54.92"></a> tri par sélection :** 
### **2.1. Le<a name="_page1_x40.00_y76.92"></a> principe** 

Sur un tableau de N éléments (numérotés de 0 à N), le principe du tri par sélection est le suivant : 

- **Rechercher le plus petit élément** du tableau, et l'échanger avec l'élément d'indice 0 ; 
- **Rechercher le second plus petit élément** du tableau, et l'échanger avec l'élément d'indice 1 ; 
- Continuer de cette façon jusqu'à ce que le tableau soit entièrement trié.

### **2.2. Illustration<a name="_page1_x40.00_y201.92"></a> graphique** 

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.010.png)

Exemple : Soit la suite de nombres suivante : 6, 1, 9, 3. Trions cette suite avec l’algorithme du tri par  sélection dans l’ordre croissant :  

*1er tour* : 6, **1**, 9, 3 -> le plus petit élément du tableau est 1, on le place donc sur la première case (en  l'échangeant avec le 6).  

*2ème tour* : 1, 6, 9, **3** -> le deuxième plus petit élément est 3, on le place sur la deuxième case et on  l’échange avec le 6.  

*3ème tour* : 1, 3, 9, **6** -> le troisième plus petit élément est 6, on l’échange avec 9 pour le placer sur la  troisième case.  

*4ème tour* : 1, 3, 6, **9** -> le quatrième plus petit élément du tableau est 9, il est déjà en quatrième  position on ne fait rien.  

Ce tri se décompose réellement en deux étapes distinctes : À chaque tour, on cherche le minimum dans  l'espace non trié du tableau (le minimum est représenté en bleu, et la partie non triée en blanc), ensuite on déplace cet élément à sa place définitive (représentée en vert). En faisant cela pour chaque élément du tableau, ce dernier se retrouve trié au bout de N tours maximum (N étant la taille du tableau). 

### **2.3. Illustration<a name="_page1_x40.00_y434.92"></a> en vidéo** 

Vidéo :[ https://www.youtube.com/watch?v=Ns4TPTC8whw ](https://www.youtube.com/watch?v=Ns4TPTC8whw)Attention : les danseurs s’échangent (si nécessaire) à chaque fois alors que le vrai algorithme ne procède à l’échange qu’à la fin de chaque tour  

### **2.4. Pseudo-code<a name="_page1_x40.00_y485.92"></a>** 

```
ALGORITHME tri_selection
    PROCEDURE echange (T, i, j)      # on échange la valeur de T[i] avec celle de T[j]
        tmp <- T[i]                 # variable temporaire pour stocker
        T[i] <- T[j]
        T[j] <- tmp

    PROCEDURE tri_sélection (T)
        POUR i ALLANT DE 1 A N [SAUT DE 1] FAIRE    # parcours 
            mini <- i                                # on stocke l'indice du premier terme
            POUR j ALLANT DE i+1 A N [SAUT DE 1]    # parcours
                SI T[j] < T[mini] ALORS         	# si la valeur stockée n'est pas la plus petite
                    mini <- j                       
                FIN SI
                j <- j + 1
            FIN POUR
            SI mini =! i ALORS        		  	# condition non nécessaire!
                echange(T, i, mini)            	# on :appelle la procédure d'échange
            FIN SI
            i <- i + 1
        FIN POUR    
```

### **2.5. Complexité<a name="_page2_x40.00_y36.92"></a>** 

Le tri par sélection a une complexité en O(N²) : Calculons le nombre d’itérations 

```
                            PROCEDURE echange (T, i, j)
1                               tmp <- T[i]                                 	
1                               T[i] <- T[j]				
1                               T[j] <- tmp	
			
                            PROCEDURE tri_sélection (T)
N fois                          POUR i ALLANT DE 1 A N [SAUT DE 1] FAIRE  
    1                               mini <- i                                		
    N-1 fois                        POUR j ALLANT DE i+1 A N [SAUT DE 1]                         
        1                               SI T[j] < T[mini] ALORS              			
        1 (pire cas)                        mini <- j     					               
                                        FIN SI
        1+1 pour le calcul              j <- j + 1				
                                    FIN POUR
    N-1 (pire cas)                  SI mini =! i FAIRE                       		
                                        echange(T, i, mini)           
                                    FIN SI
    1+1 pour le calcul              i <- i + 1					
                                FIN POUR    
```

Procédure d’échange 3 opérations pour chaque échange 

Procédure tri\_sélection : 

- Boucle « POUR j ALLANT DE i+1 A N» : (N-1) x 4 
- Si min =! i FAIRE echange (T, T[i], T[min]) : (N-1) x 3       
- Boucle « POUR i ALLANT DE 1 A N» : N x (1 + (N-1) x 4 + (N-1) x 3 +2)  

Donc le nombre d’itérations dans le pire des cas : N x (3+4N-4+3N-3) = N x (7N – 4) = 7 N² -4 N 

*Pour aller plus loin : De la même manière en ne s’intéressant qu’aux boucle, dans le pire des cas, chaque élément est inséré au début de la partie trié. Dans ce cas, tous les éléments de la partie triée doivent être déplacés à chaque itération. La ième itération génère (i-1) comparaisons et échanges de valeurs :* 

![](Aimg7.png)

**Conclusion** : Le **tri par sélection** est donc un algorithme assez simple, mais peu efficace à cause de sa complexité en **O(N²) dans le meilleur des cas ou dans le pire des cas.**  

On parle aussi de **complexité quadratique.** 

Le tri par sélection sert de base à d'autres algorithmes plus efficaces que nous étudierons plus tard. C’est un tri instable et en place (travail sur la structure et non sur une copie).

### **2.6. Stabilité<a name="_page2_x40.00_y632.92"></a> d’un algorithme** 

On dit qu'un algorithme de tri est ***stable*** s'il ne modifie pas l'ordre initial des clés identiques. 

Par exemple, imaginez que vous vouliez trier la collection de bouteilles ci-dessous par ordre de volume (le volume est indiqué sous la bouteille) : 

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.016.png)


Si vous obtenez ceci, alors votre tri n'était **pas stable** : 

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.017.png)

En effet, la bouteille noire de volume *1* se trouve maintenant avant la bouteille bleue de même volume alors qu'elle devrait être après. Il en est de même pour les deux bouteilles de volume *4* qui sont inversées par rapport à l'ordre initial. 

Avec un **tri stable**, on aurait obtenu : 

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.018.png)

L'intérêt d'un tri stable est **qu'on peut appliquer ce tri successivement, avec des critères différents.**  

### **2.7. Preuve<a name="_page3_x40.00_y297.92"></a> de correction** 

#### **2.7.1.	Correction** 
Pour prouver la correction de cet algorithme, nous définissons un **invariant de boucle** qui doit être vrai avant et après chaque itération de la boucle externe for. L’invariant est le suivant :

Invariant de boucle : À chaque début de l’itération de l’indice i de la boucle externe, les éléments T[0] à T[i-1] sont triés et sont les i plus petits éléments du tableau original.

1 **Initialisation** : Avant la première itération de la boucle externe (i = 0), il n’y a pas d’éléments dans la partie triée, donc l’invariant est trivialement vrai.

2 **Maintien** : Supposons que l’invariant est vrai au début de l’itération pour un certain i. Nous devons montrer qu’il reste vrai après la fin de cette itération.

- Pendant l’itération, l’algorithme trouve l’index du plus petit élément dans la sous-liste T[i] à T[n-1] et le place en T[i] par un échange, avec n = len(T)

- Après cet échange, T[i] est le i-ème plus petit élément du tableau original, et les éléments T[0] à T[i] sont triés et sont les i+1 plus petits éléments du tableau original.

- Ainsi, à la fin de l’itération, les éléments T[0] à T[i] sont triés et sont les i+1 plus petits éléments du tableau original, ce qui montre que l’invariant est maintenu.

3 **Terminaison** : La boucle se termine lorsque i atteint n. À ce moment-là, i = n, donc tous les éléments T[0] à T[n-1] sont triés. L’invariant garantit que ces éléments sont les plus petits éléments du tableau original et qu’ils sont triés.

En utilisant cet invariant de boucle, nous avons prouvé que l’algorithme de tri par sélection est **correct**. L’invariant de boucle nous permet de démontrer que l’algorithme maintient la partie triée du tableau correctement à chaque itération et qu’il termine avec l’ensemble du tableau trié.

#### **2.7.2.	Terminaison**
Pour prouver la terminaison de l'algorithme de tri par sélection, nous devons utiliser un **variant de boucle** pour montrer que la boucle externe et la boucle interne de l'algorithme se terminent après un nombre fini d'itérations.

- Variant de Boucle pour la Boucle Externe : Pour la boucle externe for de l'algorithme de tri par sélection, le variant de boucle est simplement l'indice i qui va de 0 à n-1. La boucle externe se termine lorsque i atteint n. À ce moment-là, n - i = 0, donc la boucle externe se termine.

- Variant de Boucle pour la Boucle Interne : Pour la boucle interne for de l'algorithme de tri par sélection, le variant de boucle est l'indice j qui va de i + 1 à n-1. La boucle interne se termine lorsque j atteint n. À ce moment-là, n - j = 0, donc la boucle interne se termine.

Puisque les deux boucles terminent après un nombre fini d'itérations, nous avons prouvé que l'algorithme de tri par sélection **termine toujours**.


### **2.8. Implémentation<a name="_page3_x40.00_y497.92"></a> en Python** 

=> CAPYTALE Le code vous sera donné par votre enseignant

**Activité n°2.:** Création de la liste aléatoire **avec l’activité 1** 

```python
import random
def genere_liste_aleatoire(N, n):
    """Génére une liste aléatoire de N éléments compris entre 0 et n"""
    return [random.randrange(n) for i in range(N)]

# Création d'une liste de 5 valeurs comprises entre 0 et 20 à trier
data = genere_liste_aleatoire(5, 20)
print("Liste initiale: ", data)
```


**Activité n°3.: implémentation classique** : AJOUTER à l’activité 2 les deux fonctions suivantes à compléter avec l'algorithme précédent : 

```python
def swap(T : list, i : int, j : int) -> list:
    """ fonction permutation (à garder elle sert beaucoup!!)  """
    # à compléter

def selection_sort(T : list) -> list:
    """ fonction tri par sélection recherche de la valeur minimum dans une liste
    puis permutation avec indice précédent """
    # à compléter

print("Liste triée   : ", selection_sort(data))
```



**Activité n°4.: Tri par sélection et temps d’exécution** : AJOUTER ce script aux fonctions de l’activité précédente en mettant en commentaire les deux print précédent : 

```python
import time

# on fait une moyenne sur plusieurs tris de tableau de même longueur
somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(1_000, 1_000_000)
    start_time=time.time()
    selection_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 1_000: %s secondes ---" % (moyenne))


somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(2_000, 1_000_000)
    start_time=time.time()
    selection_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 2_000: %s secondes ---" % (moyenne))


somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(10_000, 1_000_000)
    start_time=time.time()
    selection_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 10_000: %s secondes ---" % (moyenne))
```
On mesure la durée moyenne (sur 5 tableaux) d’exécution du tri sur des tableaux dont le nombre d’éléments est de plus en plus grand.


On voit bien que multiplier par 10 le nombre d’éléments du tableau à trier revient à multiplier le temps par 10². 

**Animation :[** http://lwh.free.fr/pages/algo/tri/tri_selection.html ](http://lwh.free.fr/pages/algo/tri/tri_selection.html)**

## **3. Tri<a name="_page4_x40.00_y702.92"></a> par insertion** 
### **3.1. Le<a name="_page4_x40.00_y724.92"></a> principe** 

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

### **3.2. Illustration<a name="_page5_x40.00_y290.92"></a> graphique  **

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.039.png)

Exemple : 9, 2, 7, 1 à trier en ordre croissant avec l’algorithme du tri par insertion :  

*1er tour* : 9 | **2**, 7, 1 -> à gauche la partie triée du tableau (le premier élément est considéré comme trié  puisqu'il est seul dans cette partie), à droite la partie non triée. On prend le premier élément de la partie  non triée, 2, et on l'insère à sa place dans la partie triée, c'est-à-dire à gauche de 9.  

*2ème tour* : 2, 9 | **7**, 1 -> on prend 7, et on le place entre 2 et 9 dans la partie triée.  

*3ème tour* : 2, 7, 9 | **1** -> on continue avec 1 que l’on place au début de la première partie.  

Pour insérer un élément dans la partie triée, on parcourt de droite à gauche tant que l'élément est plus  grand que celui que l'on souhaite insérer. Pour résumer l'idée de l'algorithme : La partie verte du tableau  est la partie triée, l'élément en bleu est le prochain élément non trié à placer et la partie blanche est la  partie non triée. 

### **3.3. Illustration<a name="_page5_x40.00_y491.92"></a> vidéo** 

Vidéo :[ https://www.youtube.com/watch?v=ROalU379l3U ](https://www.youtube.com/watch?v=ROalU379l3U)

### **3.4. Pseudo-code<a name="_page5_x40.00_y542.92"></a>** 

```
ALGORITHME tri_insertion
    PROCEDURE insere(T, i)            # insère tmp dans le tableau[0...i[ trié
        tmp = T[i]          			# valeur à inserer
        j <- i-1		    		# indice en cours                                                        
        TANT QUE j >= 0 et T[j] > tmp ALORS        
            T[j+1] <- T [j]         
	     # l'élément qui précède on le décale vers la droite jusqu'à laisser la place libre à tmp           
            j <- j - 1              	# on décale l'indice
        FIN TANT QUE
        T[j+1] <- tmp   			# on insère tmp

    PROCEDURE tri_insertion(T)     
        POUR i ALLANT DE 1 A n [SAUT DE 1] FAIRE         
            insere (T, i)             
            i <- i + 1                                     
        FIN POUR
```


### **3.5. Complexité<a name="_page6_x40.00_y36.92"></a>**  

L’algorithme du tri par insertion a une complexité de O(N²). Calculons le nombre d’instructions : 

```
                        PROCEDURE insere(T, i)                     
1                           tmp = T[i]
1                           j <- i                                                          
N-1 fois                    TANT QUE j >= 0 et T[j] > tmp ALORS        
    1                           T[j+1] <- T [j]                         
    1                           j <- j - 1                              
                            FIN TANT QUE
1                           T[j+1] <- tmp                                   
                        PROCEDURE tri_insertion(T)                                                         
N fois                      POUR i ALLANT DE 1 A n [SAUT DE 1] FAIRE         
    insere                      insere (T, i)             
    1                           i <- i + 1                                     
                            FIN POUR
```


- Procédure insere : 2 + (N – 1) x 2 + 1 = 3 + (N – 1) x 2 = 2 N + 2
- Procédure tri\_insertion : N x (2N + 2) = 2 N² + 2 N 

Pour simplifier les calculs de complexité, on s’intéresse seulement aux nombres de itérations des boucles, puisque c’est elles qui vont donner le comportement asymptotique (quand N très grand). 

*Pour aller plus loin : Exemple t = [ 4, 3, 2, 1]* 

*Le 2ème élément : le « 3 » est décalé d’un cran vers la gauche [ 3, 4, 2, 1]* 

*Le 3ème élément : le « 2 » est décalé de deux crans vers la gauche [ 2, 3, 4, 1]* 

*Le 4ème élément : le « 1 » est décalé de trois crans vers la gauche [ 1, 2, 3, 4]* 

*Pour trouver le plus petit élément, (n-1) itérations sont nécessaires, pour le 2ème plus petit élément, (n-2) itérations sont effectuées, .… Pour trouver le dernier plus petit élément, 0 itération sont effectuées.* 

*Le nombre de itérations des deux boucles est 1 + 2 + 3 = 6 c’est-à-dire* ![](Aimg8.png)

*Donc le pire des cas, le tableau est trié à l’envers, pour chaque valeur i on compte N - 1 passages dans la boucle for :* 

![](Aimg7.png)

**Conclusion** : le **tri par insertion** a une complexité en temps de **O(N²) dans le pire des cas O(N) dans le meilleur des cas (tableau déjà trié).**  

Cependant des améliorations et des variantes permettent de le rendre plus rapide comme le tri shell. C’est un algorithme stable et en place (travail sur la structure et non sur la copie).

### **3.6. Preuve<a name="_page6_x40.00_y637.92"></a> de correction** 


#### **3.6.1.	Correction**

Pour prouver la correction de cet algorithme, nous définissons un **invariant de boucle** qui doit être vrai avant et après chaque itération de la boucle externe for. L’invariant est le suivant :

Invariant de boucle : À chaque début de l’itération de l’indice i de la boucle externe, les éléments T[0] à T[i-1] sont triés.

1 **Initialisation** : Avant la première itération de la boucle externe (i = 1), il n’y a qu’un seul élément dans la partie considérée du tableau (T[0]), qui est trivialement trié. Donc l’invariant est vrai.

2 **Maintien** : Supposons que l’invariant est vrai au début de l’itération pour un certain i. Nous devons montrer qu’il reste vrai après la fin de cette itération.

- Pendant l’itération, l’algorithme sélectionne tmp = T[i] et cherche sa place correcte dans la sous-liste triée T[0] à T[i-1].

- La boucle while déplace les éléments plus grands que tmp d’une position vers la droite pour faire de la place pour tmp.

- Après avoir trouvé la place correcte pour tmp, l’algorithme insère tmp à cette position.

- À la fin de cette itération, les éléments T[0] à T[i] sont triés.
Ainsi, l’invariant est maintenu, car après chaque itération, les éléments T[0] à T[i] sont triés.

3 **Terminaison** : La boucle se termine lorsque i atteint n. À ce moment-là, i = n, donc tous les éléments T[0] à T[n-1] sont triés. L’invariant garantit que ces éléments sont triés.

En utilisant cet invariant de boucle, nous avons prouvé que l’algorithme de tri par insertion est **correct**. L’invariant de boucle nous permet de démontrer que l’algorithme maintient la partie triée du tableau correctement à chaque itération et qu’il termine avec l’ensemble du tableau trié.

#### **3.6.2.	Terminaison**

Pour prouver la terminaison de l'algorithme de tri par insertion, nous devons utiliser un **variant de boucle**. Un variant de boucle est une fonction numérique qui décroît à chaque itération de la boucle et qui est bornée inférieurement.

- Variant de Boucle pour la Boucle Externe : Pour la boucle externe for de l'algorithme de tri par insertion, le variant de boucle est simplement l'indice i qui va de 1 à n-1. La boucle externe se termine lorsque i atteint n. À ce moment-là, n - i = 0, donc la boucle externe se termine.

- Variant de Boucle pour la Boucle Interne : Pour la boucle interne while de l'algorithme de tri par insertion, le variant de boucle est l'indice j qui est initialisé à i - 1 et qui décroît jusqu'à ce que la condition j >= 0 ou T[j] > tmp ne soit plus satisfaite. La boucle interne se termine lorsque j devient négatif ou lorsque T[j] <= tmp. Dans les deux cas, la condition de la boucle while n'est plus satisfaite et la boucle se termine.

Puisque les deux boucles terminent après un nombre fini d'itérations, nous avons prouvé que l'algorithme de tri par sélection **termine toujours**.




### **3.7. Implémentation<a name="_page7_x40.00_y36.92"></a> en Python** 

=> CAPYTALE Le code vous sera donné par votre enseignant

**Activité n°5.:** Création de la liste aléatoire **avec l’activité 1** : reprendre l’activité 1 et 2 

**Activité n°6.: implémentation classique** : ajouter à l’activité précédente les deux fonctions suivantes : 

```python
def insert(T, i):
    """ fonction qui insère la valeur T[i] à la bonne place dans le tableau"""
    # à compléter

def insertion_sort(T):
    """ fonction tri par insertion parcours du vecteur avec décalage ascendant des éléments """
    # à compléter

print("Liste triée   : ", insertion_sort(data))
```



**Remarque : on aurait pu également faire une seule fonction**  

**Activité n°7.: Tri par insertion et temps d’exécution** : ajouter ce script aux fonctions de l’activité précédente en mettant en commentaire les deux print précédent : 

```python
import time

# on fait une moyenne sur plusieurs tris de tableau de même longueur
somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(1_000, 1_000_000)
    start_time=time.time()
    insertion_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 1_000: %s secondes ---" % (moyenne))

somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(2_000, 1_000_000)
    start_time=time.time()
    insertion_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 2_000: %s secondes ---" % (moyenne))

somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(10_000, 1_000_000)
    start_time=time.time()
    insertion_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 10_000: %s secondes ---" % (moyenne))
```
On mesure la durée moyenne (sur 5 tableaux) d’exécution du tri sur des tableaux dont le nombre d’éléments est de plus en plus grand.



**Animation :[ http://lwh.free.fr/pages/algo/tri/tri_insertion.html ](http://lwh.free.fr/pages/algo/tri/tri_insertion.html)![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.006.png)**



## **4. Autres<a name="_page8_x40.00_y36.92"></a> algorithmes de tris : le tri à bulles (Bubble sort)** 

Le tri à bulles est un algorithme de tri qui consiste à faire  **remonter  progressivement les plus petits éléments d'une liste**, comme les bulles  d'air remontent à la surface d'un liquide. 

![](Aspose.Words.44e8a127-fa79-459d-b056-b00fa0212d54.055.png)

L'algorithme  parcourt  la  liste,  et  **compare  les  couples  d'éléments  successifs**.   

Lorsque deux éléments successifs ne sont pas dans l'ordre croissant, **ils  sont échangés**.   

Après chaque parcours complet de la liste, l'algorithme **recommence l'opération**. Lorsque aucun échange n'a lieu pendant un parcours, cela signifie que la liste est triée : l'algorithme peut s'arrêter. 

On optimise l’algorithme en se basant sur la propriété que le dernier élément permuté se trouve nécessairement bien trié. Il n’est alors pas besoin de parcourir la liste jusqu’à la fin : combsort (tri à peignes) 

**Conclusion** : Le tri à bulles présente une complexité en **O(N²)** dans le pire des cas (où N est la longueur de la liste), et en O(N) dans le cas où le tableau est déjà trié, ce qui le classe parmi les mauvais algorithmes de tri. Il n'est donc quasiment pas utilisé en pratique. 

Comme le tri par insertion, le tri à bulle est un tri stable. Illustration vidéo :[ https://www.youtube.com/watch?v=lyZQPjUT5B4 ](https://www.youtube.com/watch?v=lyZQPjUT5B4) 

=> CAPYTALE Le code vous sera donné par votre enseignant

**Activité n°8.:** Création de la liste aléatoire **avec l’activité 1** : reprendre l’activité 1 et 2 

**Activité n°9.: implémentation classique Avec la fonction echange et la fonction bubble\_sort** 

```python
def swap(T : list, i : int, j : int) -> list:
    """ fonction permutation (à garder elle sert beaucoup!!)  """
    # à compléter

def bubble_sort(T : list) -> list:
    """ fonction tri a bulle permutation des éléments 2 à 2 en faisant remonter
    la plus grande valeur en fin de la liste  """
    # à compléter
```


**Remarque : il existe d’autres versions du tri bulle** 

**Activité n°10.: Tri bulle et temps d’exécution** : ajouter ce script aux fonctions de l’activité précédente en mettant en commentaire les deux print précédent : 

```python
import time

# on fait une moyenne sur plusieurs tris de tableau de même longueur
somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(1_000, 1_000_000)
    start_time=time.time()
    bubble_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 1_000: %s secondes ---" % (moyenne))

somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(2_000, 1_000_000)
    start_time=time.time()
    bubble_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 2_000: %s secondes ---" % (moyenne))

somme_des_durees = 0
for i in range(5):
    liste = genere_liste_aleatoire(10_000, 1_000_000)
    start_time=time.time()
    bubble_sort(liste)
    somme_des_durees = somme_des_durees + time.time() - start_time
moyenne = somme_des_durees/5
print("Temps d execution pour 10_000: %s secondes ---" % (moyenne))
```



Animation :[ http://lwh.free.fr/pages/algo/tri/tri_bulle.html ](http://lwh.free.fr/pages/algo/tri/tri_bulle.html)

## **5. Exercices<a name="_page9_x40.00_y511.92"></a>** 

=> CAPYTALE Le code vous sera donné par votre enseignant

**Exercice n°1** : Créer une fonction selection\_sort\_desc() qui permet trier avec l’algorithme de tri par sélection une liste aléatoire par valeurs décroissantes. 

**Exercice n°2** : Créer une fonction selection\_sort\_asc\_partir\_fin() qui permet trier avec l’algorithme de tri par sélection une liste aléatoire par valeurs croissantes de manière à compléter l’algorithme suivant :  

```python
def selection_sort_asc_partir_fin(T):
    for i in range(…, 0, …):
        maxi = …
        for j in range(…):
            if T[j]> T[…]:
                maxi = j
        if maxi !=i:
            …
    return T
```


**Exercice n°3** : Créer une fonction selection\_sort\_desc\_partir\_fin() qui permet trier avec l’algorithme de tri par sélection et l’algorithme de l’exercice 2, une liste aléatoire par valeurs décroissantes. 

**Exercice n°4** : Créer une fonction bubble\_sort\_desc() qui permet trier avec l’algorithme de tri à bulles une liste aléatoire par valeurs décroissantes. 

