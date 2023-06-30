---
author: ELP
title: Chapitre 6 - La recherche dichotomique
---

**Table des matières** 

1. [Introduction](#_page0_x40.00_y275.92)
2. [TP](#_page0_x40.00_y599.92)
3. [Le pseudo-code (version itérative)](#_page4_x40.00_y332.92)
4. [Complexité](#_page4_x40.00_y600.92)
5. [Preuve de correction](#_page5_x40.00_y211.92)
6. [Implémentation en Python](#_page6_x40.00_y408.92)
7. [Exercices](#_page7_x40.00_y407.92)


## **1.  Introduction<a name="_page0_x40.00_y275.92"></a>** 

La famille des algorithmes « diviser pour régner »1 fait appel à une technique algorithmique consistant à : 

1. **Diviser** : découper un problème initial en sous-problèmes 
2. **Régner** : résoudre les sous-problèmes (récursivement ou directement s'ils sont assez petits) 
3. **Combiner** : calculer une solution au problème initial à partir des solutions des sous-problèmes 

Cette technique fournit des **algorithmes efficaces** pour de nombreux problèmes, comme la recherche d'un élément dans un tableau trié (recherche dichotomique) ou le tri (tri fusion, tri rapide) par exemple. 

La **faible complexité** des algorithmes diviser pour régner est l'un de leurs principaux intérêts. Il existe plusieurs théorème facilitant le calcul des complexités des algorithmes de type diviser pour régner (le principal théorème est le[ Master theorem)](https://fr.wikipedia.org/wiki/Master_theorem). 

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.004.png)

La recherche dichotomique est formalisée dans un article de John Mauchly en 1946, mais l'idée d'utiliser une liste triée pour faciliter la recherche remonte à Babylone en -220. L'algorithme  d'Euclide pour calculer le plus grand commun diviseur de deux nombres peut être vu comme un  algorithme diviser pour régner (les deux nombres diminuent et on se ramène à un problème plus  petit). John von Neumann invente le tri fusion en 1945. Knuth donne une méthode utilisée par les  services postaux : les lettres sont triées et séparés en fonction des zones géographiques, puis en  sous-zones géographies, etc.  

## **2. TP<a name="_page0_x40.00_y599.92"></a>** 

L'idée de base est simple : 

- On dispose d'un tableau [^2] trié de valeurs, et on cherche à déterminer si une valeur v est présente dans le tableau. 
- Pour cela, on procède par *dichotomie* : 

### **2.1. Méthode<a name="_page1_x40.00_y36.92"></a> visuelle : La valeur se trouve dans le tableau** 

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.005.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.006.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.007.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.008.jpeg)

### **2.2. Méthode<a name="_page1_x40.00_y518.92"></a> visuelle : La valeur ne se trouve pas dans le tableau**

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.010.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.011.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.012.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.013.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.014.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.015.jpeg)

Animation :[ https://www.infoforall.fr/art/algo/animation-de-la-recherche-dichotomique/ ](https://www.infoforall.fr/art/algo/animation-de-la-recherche-dichotomique/)

### **2.3. Application<a name="_page2_x40.00_y511.92"></a> de l’algorithme à un exemple** 

Voici une bande de papier illustrant un tableau de nombre en mémoire

![](Aimg9.png)

Essayons de rechercher le nombre 35 et de connaitre son emplacement (indice) dans le tableau

Le tableau contient 16 valeurs (indice de 0 à 15) 

**Etape 1** : Comment calculer la moitié ?

|**Indice Bas1** |**Indice Haut1** |**Indice milieu1** |
| - | - | - |


**Etape 2** : Dans quelle partie se trouve la valeur 35 ? ………………………………………………………………………………………………………………………. 


|. |. |. |. |. |. |. |
| - | - | - | - | - | - | - | 

**Etape 3** : Comment calculer la moitié de la nouvelle partie du tableau ? 

|**Indice Bas2** |**Indice Haut2** |**Indice milieu2** |
| - | - | - |


**Etape 4** : Dans quelle partie se trouve la valeur 35 ? ……………………………………………………………………………………………………………………….. 

|. |. |. |
| - | - | - | 

|. |. |. |
| - | - | - | 

**Etape 5** : Comment calculer la moitié de la nouvelle partie du tableau ? 


|**Indice Bas3** |**Indice Haut3** |**Indice milieu3** |
| - | - | - |

**Etape 6** : Dans quelle partie se trouve la valeur 35 ?

………………………………………………………………………………………………………………………………………………….. 


**Etape 7** : Comment calculer la moitié de la nouvelle partie du tableau ? 



|**Indice Bas4** |**Indice Haut3** |**Indice milieu4** |
| - | - | - |


**Etape 8** : le nombre 35 est trouvé, il se trouve à l’indice milieu4 = 6

Résumé : Chiffre à trouver 35 


![](Aimg10.png)

La valeur 35 se trouve à l’indice 6 (milieu) dans le tableau 

**Activité n°1.:** Entrainez-vous avec la bande de papier fournie en complétant le tableau ci-dessous : 

![](Aimg11.png)



Chiffre à trouver 72 


![](Aimg12.png)

La valeur 72 se trouve à l’indice 13 (milieu) dans le tableau 

## **3. Le<a name="_page4_x40.00_y332.92"></a> pseudo-code (version itérative)** 

```
ALGORITHME recherche_dichotomique
    PROCEDURE recherche_dichotomique(elmt, tableau)
        gauche <- 1
        droite <- taille du tableau
        TANT QUE gauche <= droite FAIRE     
            milieu <- (gauche + droite)/2   # on cherche l'élément centrale 
            si T[milieu] < x         # la recherche peut se restreindre à la partie droite du tableau
                gauche = milieu + 1   # on modifie la valeur de gauche en conséquence
            sinon si T[milieu] > x     # la recherche peut se restreindre à la partie gauche du tableau
                droite = milieu-1     # on modifie la valeur de gauche en conséquence
            sinon 
                renvoyer milieu             # on a trouvé la valeur 
        FIN TANT QUE
        renvoyer None                # gauche <= droite n'est plus vraie. La valeur x n'est pas dans T     
```


## **4. Complexité<a name="_page4_x40.00_y600.92"></a>** 

Au niveau de la boucle, combien doit-on effectuer d'itérations pour un tableau de taille n dans le cas le plus défavorable (l'entier x n'est pas dans le tableau t) ? 

Sachant qu'**à chaque itération de la boucle on divise le tableau en 2,** cela revient donc à se demander combien de fois faut-il diviser le tableau en 2 pour obtenir, à la fin, un tableau comportant un seul entier.  

Autrement dit, combien de fois faut-il diviser n par 2 pour obtenir 1. 

Mathématiquement cela se traduit par l'équation  $ {n \over 2^a}  =1$ avec a le nombre de fois qu'il faut diviser n par 2 pour obtenir 1. Il faut donc trouver a.  

A ce stade il est nécessaire d'introduire une nouvelle notion mathématique : le "logarithme base 2" noté log2.  Par définition  2(2 ) = . Nous avons donc :  ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.009.png)

- 1 ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.018.png)

2

- 2 

2( ) = 2(2 ) 2( ) = 

nous avons donc  = 2( ) 

Nous pouvons donc dire que la complexité en temps dans le pire des cas de l'algorithme de recherche dichotomique est ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.019.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.020.png)**O(log2(n))** 

L'algorithme de recherche dichotomique est **plus efficace** que l'algorithme de recherche qui consiste à parcourir l'ensemble du tableau. 

## **5. Preuve<a name="_page5_x40.00_y211.92"></a> de correction :** 

TERMINAISON : La fonction recherche\_dichotomique contient une boucle non bornée, une boucle while, et pour être sûr de toujours obtenir un résultat, il faut s’assurer que le programme termine, **que l’on ne reste pas bloqué infiniment dans la boucle**. Pour prouver que c’est bien le cas, nous allons utiliser **un variant de boucle**. 

**Variant de boucle** : Il s’agit d’une quantité entière qui :  ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.021.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.022.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.023.png)

- doit être positive ou nulle pour rester dans la boucle ;  
- doit décroître à chaque itération.  

Si l’on arrive trouver une telle quantité, il est évident que l’on va nécessairement sortir de la boucle au bout d’un nombre fini d’itérations, puisqu’**un entier positif ne peut décroître infiniment.**  

Preuve de la terminaison : Pour le cas qui nous occupe, un variant est très facile à trouver : il s’agit de la largeur de la quantité droite - gauche.  

La condition de boucle étant gauche <= droite, cela correspond exactement à ce que notre variant soit positif ou nul. Montrons maintenant que le variant décroit strictement lors de l’exécution du corps de la boucle. On commence par définir milieu = (gauche + droite) / 2. En particulier, on a alors gauche <= milieu <= droite.

Ensuite, trois cas sont possibles.  

- si T[milieu] = x, on sort directement de la boucle à l’aide d’un return. La **terminaison est assurée.****  
- si T[milieu] > x, on modifie la valeur de gauche. En appelant gauche' cette nouvelle valeur, on a :**  



|droite - gauche' < droite - milieu <= droite - gauche||||
| - | :- | :- | :- |
|Ainsi, le variant a **strictement décru.** sinon, on modifie droite et on a de même :**  ||||
￿ 



|droite' - gauche < milieu - gauche <= droite - gauche||||
| - | :- | :- | :- |
|De même, le variant a **strictement décru.**  ||||
On a trouvé un variant pour notre boucle, nous avons prouvé qu’**elle termine bien**. Bien sûr, l’utilisation très basique de ce variant ne permet pas, telle qu’elle, de justifier la complexité de la recherche dichotomique.  

*POUR ALLER PLUS LOIN : CORRECTION : Pour prouver que si le programme renvoie None, alors c’est bien que la valeur recherchée n’est pas présente dans le tableau, nous allons utiliser l’invariant de boucle suivant :*  

**Invariant** *: Si* x *est présente dans* T*, c’est nécessairement à un indice compris entre* gauche *et* droite *(inclus).  Prouvons qu’il s’agit bien d’un invariant de la boucle de la fonction* recherche\_dichotomique*. Pour cela, il faut* 

*s’intéresser à une exécution qui va jusqu’à la fin du corps de la boucle.* 

*On suppose donc qu’en entrée de boucle, l’***Invariant** *est vérifié. Après avoir défini milieu, trois cas sont examinés :  ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.009.png)*

- *si* T[milieu] = x, *on sort de la boucle prématurément à l’aide de l’instruction retourner milieu, donc ce cas ne nous intéresse pas dans le cadre de la preuve d’invariant de boucle.  **![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.024.png)***
- *si* T [milieu] > x*, et si* x *est présente dans le tableau, alors comme celui-ci est ordonné de façon croissante, cela implique que* x *ne peut être présent à l’indice milieu, ni avant. On en déduit d’après l’***Invariant** *que si* x *se trouve dans* T *c’est nécessairement à un indice compris entre* milieu + 1 *et* droite*. Ainsi, après l’affectation* gauche =  milieu + 1*, l’***Invariant** *est encore vérifié.   **![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.025.png)***
- *sinon, on a* T[milieu] < x *et, de même, cela implique que l’on ne peut trouver* x *dans le tableau à un indice inférieur ou égal à* milieu*. Ainsi, en supposant* **Invariant** *vrai au départ et en effectuant l’affectation* droite 
- milieu - 1, *l’***invariant** *reste vérifié.***  

*Ainsi, dans tous les cas d’une exécution menant à la fin du corps de la boucle, si l’***Invariant** *est vérifié au début du corps, il l’est encore à la fin. C’est donc un invariant de la boucle de la fonction* recherche\_dichotomique*.*  

*Voyons maintenant comme cela nous permet de prouver la correction de cette fonction lorsque le résultat est* None*. Avant d’entrer dans la boucle, on a* gauche = 1 *et* droite = milieu - 1*, et donc si* x *est présente dans* T*, c’est nécessairement à un indice compris entre* gauche *et* droite*. Ainsi, l’***Invariant** *est vérifié en entrant dans la boucle.  Puisqu’il s’agit d’un invariant de cette boucle, il est encore vérifié en sortant de la boucle. Mais à ce moment, on sait que :*  

- **Invariant** *: si* x *est présente dans* T *sa position sera comprise entre* gauche *et* droite*.  **![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.026.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.027.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.028.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.029.png)***
- *Sortie de boucle : la condition de boucle* gauche <= droite *n’est plus vérifiée, on a donc* droite < gauche*.***  

*En combinant les deux, si* x *est présente dans* T *à une position comprise entre* gauche *et* droite*, ce qui implique que* gauche <= droite*, qui est incompatible avec* droite < gauche*.*  

*Ainsi, en sortie de boucle,* x *ne peut être présente dans le tableau (car aucun indice n’est possible) et le résultat renvoyé* None *est donc correct.*  

*En conclusion, la fonction* recherche\_dichotomique *a deux comportements possibles : si le résultat renvoyé est un entier positif, on a montré qu’il correspond à un indice où se trouve la valeur recherchée dans le tableau ; sinon, le résultat renvoyé est* None  *et on a montré que dans ce cas, la valeur recherchée n’apparaît pas dans le tableau.* 

## **6. Implémentation<a name="_page6_x40.00_y408.92"></a> en Python** 

**Activité n°2.:** 

def rechercheDichotomique(T \*, x): ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.030.png)

`    `*"""* 

`    `*recherche l'indice d'un élément dans une liste triée* 

`    `***:param** T: tableau d'entier* 

`    `***:param** x: entier* 

`    `***:return**: entier (indice de la valeur)* 

`    `*"""* 
\*
`    `gauche = 0 

`    `droite = len(T)-1 #attention il s'agit ici des indices !! 

`    `while gauche <= droite : 

`        `milieu = (gauche + droite)//2 # ATTENTION c'est un indice donc un entier         ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.031.png)if T[milieu] < x: 

`            `gauche = milieu + 1 

`        `elif T[milieu] > x: 

`            `droite = milieu - 1 

`        `else : 

`            `return milieu 

`    `return None 

\# construction d'un tableau par compréhension ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.032.png)import random 

t1 = [random.randint(1,100\_000\_000) for \_ in range(10\_000)] t1.sort() 

t2 = [random.randint(1,100\_000\_000) for \_ in range(100\_000)] t2.sort() 

t3 = [random.randint(1,100\_000\_000) for \_ in range(1\_000\_000)] ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.009.png)

t3.sort() ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.033.png)

t4 = [random.randint(1,100\_000\_000) for \_ in range(2\_000\_000)] t4.sort() 

t5 = [random.randint(1,100\_000\_000) for \_ in range(4\_000\_000)] t5.sort() 

Comme les temps d’exécution sont très faibles, et que la fonction time est peu précise il faut avoir recourt à la fonction magique ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.034.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.035.png)%timeit de **iPython.** (Le prompt est remplacé par ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.036.png)) 

%timeit rechercheDichotomique(t1, 0) ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.037.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.038.png)![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.039.png)

2\.69 µs ± 144 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each) %timeit rechercheDichotomique(t2, 0) 

2\.9 µs ± 105 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each) %timeit rechercheDichotomique(t3, 0) 

4\.02 µs ± 425 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each) %timeit rechercheDichotomique(t4, 0) 

4\.37 µs ± 457 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each) %timeit rechercheDichotomique(t5, 0) 

4\.64 µs ± 256 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each) 

## **7. Exercices<a name="_page7_x40.00_y407.92"></a>** 

**Exercice 1** : Recherche d’un maximum dans une liste de n éléments 

1. Ecrire l’algorithme en pseudo – code 
1. Calculer la complexité de cet algorithme  
1. L’implémenter en Python 
1. Modifier le programme pour créer une fonction maximum(T :list) -> int
1. Tester la fonction avec une liste aléatoire de 20 valeurs 

**Exercice 2** : Recherche de la moyenne des éléments d’une liste de n éléments 

1. Ecrire l’algorithme en pseudo – code 
1. Calculer la complexité de cet algorithme  
1. L’implémenter en Python 
1. Modifier le programme pour créer une fonction moyenne(T :list) -> int
1. Tester la fonction avec une liste aléatoire de 20 valeurs ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.009.png)

**Exercice 3 : Recherche en table** 

Si on utilisait une méthode séquentielle pour chercher un nom dans un annuaire, on ouvrirait celui-ci à la première page et on comparerait le nom recherché au premier nom de l’annuaire, puis au deuxième, puis au troisième, etc., jusqu’à trouver le nom recherché, ou arriver au dernier nom de l’annuaire. Un annuaire contenant 30.000 noms et une comparaison prenant 100 ms, il faudrait, dans le pire des cas, 3.000 secondes, soit 50 minutes, pour trouver le nom recherché ou se convaincre qu’il n’appartient pas à l‘annuaire. 

Bien entendu, ce n’est pas ainsi que l’on procède : on ouvre l‘annuaire au milieu, on compare le nom recherché au nom médian. Si le nom recherché est avant le nom médian dans l’ordre alphabétique, on élimine la seconde moitié de l’annuaire, sans même la regarder ; s’il est après le nom médian, on élimine la première moitié. En recommençant avec le demi-annuaire restant, on élimine ensuite un demi-demi-annuaire et on continue jusqu’à trouver le nom en question ou obtenir l’ensemble vide. 

1. Compléter le tableau ci-dessous pour rechercher un nom dans un annuaire de 30.000 noms : 



|**comparaison** |**ensemble de recherche (mots)** |
| - | - |
|1 |15\.000 |
|2 |7\.500 |
|... |... |

2. En déduire le temps de recherche dans le pire des cas et conclure. 

On appelle logarithme à base 2, log2(x) d’un nombre x ≥ 1, le nombre de fois qu’il faut le diviser x par 2 pour obtenir un nombre inférieur ou égal à 1. 

Sur la calculatrice, log2( ) = log( ) log(2)

3. A partir du logarithme à base 2, retrouver le résultat obtenu à la question 1. 
3. Calculer le temps nécessaire pour rechercher un nom dans l’annuaire français pour n = 60 millions d’entrées. ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.009.png)

**Exercice 4** : Algorithme de recherche dichotomique 

1\.  Faire la preuve (correction totale) de l’algorithme ci-dessous. 

Pour montrer qu’un algorithme est correcte, il faut montrer que l’algorithme : 

1. se termine : problème de la terminaison. 
1. calcule bien ce qu'il est supposé calculer : problème la correction partielle. 

La correction totale est la terminaison et la correction partielle. 

fonction **dichotomie**(liste : tableau d’entiers, valeur : entier) -> booléen : { recherche d'une valeur dans une liste par dichotomie } ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.040.png)

{ renvoie vrai si la valeur est trouvée, faux sinon } 

variables 

gauche : entier := 0 

droite : entier := taille(liste) - 1 

trouvé : booléen := faux 

milieu : entier 

début 

tantque gauche <= droite et non trouvé faire 

milieu = (gauche + droite) / 2 

si liste[milieu] = valeur alors 

trouvé := vrai 

sinon 

si liste[milieu] < valeur alors 

gauche := milieu + 1 sinon 

droite := milieu – 1 

retourne trouve 

fin 

2. Tracer la courbe temps = f(log(taille)) sur Tableur. 

Un test de performances en temps de cet algorithme, effectué sur une machine équipée d’un processeur AMD A9 dual core à 3.5 GHZ et implémenté avec Python 3.4 sous MS Windows 10, donne le tableau de mesures ci-dessous : 



|Taille  |500 |1000 |2000 |10000 |30000 |100000 |300000 |
| - | - | - | - | - | - | - | - |
|Temps (ns) |8,49 |10,61 |15,92 |24,00 |32,48 |35,00 |45,48 |



3. Déterminer l’équation de la droite et prouver que cet algorithme est bien logarithmique 
3. Créer un fichier dichotomie.py et implémenter l’algorithme ci-dessus. 
3. Valider les tests unitaires suivants : 

dichotomie([], 0) == False ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.041.png)

dichotomie([1], 0) == False 

dichotomie([1], 1) == True 

dichotomie([1, 2, 3], 2) == True 

dichotomie([1, 2, 3, 4], 2) == True 

dichotomie([1, 2, 3, 4], 0.1 \* 20) == True dichotomie([1, 2, 3, 4], 2.5) == False dichotomie("string", 's') == False 

dichotomie(['g', 'i', 'n', 'r', 's', 't'], 's') == True 

6. On souhaite améliorer l’algorithme ci-dessus pour obtenir également la position de la valeur cherchée si elle apparaît dans la liste de recherche, sinon la position à laquelle il faudrait l’insérer.  ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.009.png)

Première NSI   Chap 12 : La recherche dichotomique  Page 12/13 

Pour cela, on enlève la variable trouve et on modifie les conditions. 

La condition de continuation n’est plus « gauche ≤ droite et non trouvé » mais  

« gauche <= droite  ». 

Puis on déplace par dichotomie les bornes pour se rapprocher de la valeur cherchée. La borne droite donne, dans chaque cas possible, la position de l’élément s’il est trouvé ou la position à laquelle il faudrait l’insérer. 

Ecrire l’algorithme correspondant 

**Aide :** 

dichotomie\_extend(liste: list, valeur: int) -> tuple ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.042.png)

La fonction retournera (True, position) si valeur trouvée, (False, position à insérer) sinon  

7. Valider les tests unitaires suivants : 

dichotomie\_extend([0], 1) == (False, 1) dichotomie\_extend([0], -1) == (False, 0) dichotomie\_extend([1, 2, 3], 2) == (True, 1) ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.043.png)

8. S’assurer que les fonctions sont correctement documentées (docstring). ![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.009.png)
Première NSI   Chap 6 : La recherche dichotomique  Page 13/13 

[^1]: - On regarde **l'élément du milieu du tableau** et on **le compare à** v. 
- 
    S'ils sont égaux, on a gagné, sinon, on poursuit la recherche dans la première ou la seconde moitié du 
[^2]: ableau.  ￿  Si à la fin, on a réduit la portion du tableau au point qu'il ne contient plus aucun élément, la recherche s'arrête sur un echec : v n'est pas présent dans t. 