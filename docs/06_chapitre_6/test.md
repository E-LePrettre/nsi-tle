---
author: ELP
title: 06c La recherche dichotomique
---

**Table des matières**

1. [Introduction](#_page0_x40.00_y275.92)
2. [TP](#_page0_x40.00_y599.92)
3. [Le pseudo-code (version itérative)](#_page4_x40.00_y332.92)
4. [Complexité](#_page4_x40.00_y600.92)
5. [Preuve de correction](#_page5_x40.00_y211.92)
6. [Implémentation en Python](#_page6_x40.00_y408.92)
7. [Exercices](#_page7_x40.00_y407.92)

## <H2 STYLE="COLOR:BLUE;">1. Introduction<a name="_page0_x40.00_y275.92"></a></H2>

La famille des algorithmes « diviser pour régner » fait appel à une technique algorithmique consistant à :

1. **Diviser** : découper un problème initial en sous-problèmes
2. **Régner** : résoudre les sous-problèmes (récursivement ou directement s'ils sont assez petits)
3. **Combiner** : calculer une solution au problème initial à partir des solutions des sous-problèmes

Cette technique fournit des **algorithmes efficaces** pour de nombreux problèmes, comme la recherche d'un élément dans un tableau trié (recherche dichotomique) ou le tri (tri fusion, tri rapide) par exemple.

La **faible complexité** des algorithmes diviser pour régner est l'un de leurs principaux intérêts. Il existe plusieurs théorème facilitant le calcul des complexités des algorithmes de type diviser pour régner (le principal théorème est le [Master theorem](https://fr.wikipedia.org/wiki/Master_theorem)).

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.004.png)

La recherche dichotomique est formalisée dans un article de John Mauchly en 1946, mais l'idée d'utiliser une liste triée pour faciliter la recherche remonte à Babylone en -220. L'algorithme d'Euclide pour calculer le plus grand commun diviseur de deux nombres peut être vu comme un algorithme diviser pour régner (les deux nombres diminuent et on se ramène à un problème plus petit). John von Neumann invente le tri fusion en 1945. Knuth donne une méthode utilisée par les services postaux : les lettres sont triées et séparés en fonction des zones géographiques, puis en sous-zones géographiques, etc.

## <H2 STYLE="COLOR:BLUE;">2. TP<a name="_page0_x40.00_y599.92"></a></H2>

L'idée de base est simple :

- On dispose d'un tableau trié de valeurs, et on cherche à déterminer si une valeur v est présente dans le tableau.
- Pour cela, on procède par *dichotomie* :

### <H3 STYLE="COLOR:GREEN;">2.1. Méthode<a name="_page1_x40.00_y36.92"></a> visuelle : La valeur se trouve dans le tableau</H3>

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.005.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.006.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.007.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.008.jpeg)

### <H3 STYLE="COLOR:GREEN;">2.2. Méthode<a name="_page1_x40.00_y518.92"></a> visuelle : La valeur ne se trouve pas dans le tableau</H3>

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.010.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.011.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.012.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.013.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.014.jpeg)

![](Aspose.Words.811dea78-cc24-44b0-94c9-7acd3bdf0560.015.jpeg)

Animation : [https://www.infoforall.fr/art/algo/animation-de-la-recherche-dichotomique/](https://www.infoforall.fr/art/algo/animation-de-la-recherche-dichotomique/)

### <H3 STYLE="COLOR:GREEN;">2.3. Application<a name="_page2_x40.00_y511.92"></a> de l’algorithme à un exemple</H3>

Voici une bande de papier illustrant un tableau de nombres en mémoire

![](Aimg9.png)

Essayons de rechercher le nombre 35 et de connaitre son emplacement (indice) dans le tableau

Le tableau contient 16 valeurs (indice de 0 à 15)

**Etape 1** : Comment calculer la moitié ?

|**Indice Bas1** |**Indice Haut1** |**Indice milieu1** |
| - | - | - |

**Etape 2** : Dans quelle partie se trouve la valeur 35 ?

| | | | | | | |
| - | - | - | - | - | - | - |

**Etape 3** : Comment calculer la moitié de la nouvelle partie du tableau ?

|**Indice Bas2** |**Indice Haut2** |**Indice milieu2** |
| - | - | - |

**Etape 4** : Dans quelle partie se trouve la valeur 35 ?

| | | |
| - | - | - |

| | | |
| - | - | - |

**Etape 5** : Comment calculer la moitié de la nouvelle partie du tableau ?

|**Indice Bas3** |**Indice Haut3** |**Indice milieu3** |
| - | - | - |

**Etape 6** : Dans quelle partie se trouve la valeur 35 ?

**Etape 7** : Comment calculer la moitié de la nouvelle partie du tableau ?

|**Indice Bas4** |**Indice Haut4** |**Indice milieu4** |
| - | - | - |

**Etape 8** : le nombre 35 est trouvé, il se trouve à l’indice milieu4 = 6

Résumé : Chiffre à trouver 35

![](Aimg10.png)

La valeur 35 se trouve à l’indice 6 (milieu) dans le tableau

**<H3 STYLE="COLOR:red;">Activité n°1.:** Entrainez-vous avec la bande de papier fournie en complétant le tableau ci-dessous :</H3>

![](Aimg11.png)

Chiffre à trouver 72

![](Aimg12.png)

La valeur 72 se trouve à l’indice 13 (milieu) dans le tableau

## <H2 STYLE="COLOR:BLUE;">3. Le<a name="_page4_x40.00_y332.92"></a> pseudo-code (version itérative)</H2>

```
ALGORITHME recherche_dichotomique
    PROCEDURE recherche_dichotomique(x, tableau)
        gauche <- 1
        droite <- taille du tableau
        TANT QUE gauche <= droite FAIRE
            milieu <- (gauche + droite)/2   # on cherche l'élément central
            si T[milieu] < x         # la recherche peut se restreindre à la partie droite du tableau
                gauche = milieu + 1   # on modifie la valeur de gauche en conséquence
            sinon si T[milieu] > x     # la recherche peut se restreindre à la partie gauche du tableau
                droite = milieu-1     # on modifie la valeur de gauche en conséquence
            sinon si T[milieu] = x
                renvoyer milieu   #True     # on a trouvé la valeur
        FIN TANT QUE
        renvoyer None  #False     # gauche <= droite n'est plus vraie. La valeur x n'est pas dans T
```

## <H2 STYLE="COLOR:BLUE;">4. Complexité<a name="_page4_x40.00_y600.92"></a></H2>

Au niveau de la boucle, combien doit-on effectuer d'itérations pour un tableau de taille n dans le cas le plus défavorable (l'entier x n'est pas dans le tableau t) ?

Sachant qu'**à chaque itération de la boucle on divise le tableau en 2**, cela revient donc à se demander combien de fois faut-il diviser le tableau en 2 pour obtenir, à la fin, un tableau comportant un seul entier.

Autrement dit, combien de fois

 faut-il diviser n par 2 pour obtenir 1.

Mathématiquement cela se traduit par l'équation  $\frac {n }{ 2^a}  =1$ avec a le nombre de fois qu'il faut diviser n par 2 pour obtenir 1. Il faut donc trouver a.

A ce stade il est nécessaire d'introduire une nouvelle notion mathématique : le "logarithme base 2" noté log<sub>2</sub>.  Par définition  log<sub>2</sub>(2<sup>x</sup>) = x . Nous avons donc :

$\frac {n }{ 2^a}  =1$

n = 2<sup>a</sup>

log<sub>2</sub>(n) = log<sub>2</sub>(2<sup>a</sup>)

log<sub>2</sub>(n) = a

nous avons donc  a = log<sub>2</sub>(n)

Nous pouvons donc dire que la complexité en temps dans le pire des cas de l'algorithme de recherche dichotomique est **O(log<sub>2</sub>(n))**

L'algorithme de recherche dichotomique est **plus efficace** que l'algorithme de recherche qui consiste à parcourir l'ensemble du tableau.

## <H2 STYLE="COLOR:BLUE;">5. Preuve<a name="_page5_x40.00_y211.92"></a> de correction</H2>

### <H3 STYLE="COLOR:GREEN;">5.1. Correction partielle</H3>

**Invariant de boucle** : À chaque début de la boucle while, si la cible est dans le tableau, alors elle se trouve entre les indices gauche et droite inclus.

1 **Initialisation** : Avant la première itération de la boucle, gauche est initialisé à 0 et droite à len(T) - 1. Donc, l’invariant est vrai car si la cible est dans le tableau, elle doit se trouver quelque part entre ces indices.

2 **Maintien** : Supposons que l’invariant est vrai au début d’une itération. La boucle while calcule milieu comme étant la moyenne de gauche et droite. Il y a trois cas à considérer :

- Cas 1 : Si T[milieu] == x, alors l’algorithme retourne milieu, ce qui est correct et l’invariant reste vrai.
- Cas 2 : Si T[milieu] < x, alors la cible, si elle est présente, doit être à droite de milieu. Nous mettons donc à jour gauche à milieu + 1. L’invariant reste vrai car nous avons réduit l’intervalle de recherche de manière correcte.
- Cas 3 : Si T[milieu] > x, alors la cible, si elle est présente, doit être à gauche de milieu. Nous mettons donc à jour droite à milieu - 1. Encore une fois, l’invariant reste vrai car nous avons correctement réduit l’intervalle de recherche.

3 **Terminaison** : La boucle se termine lorsque gauche > droite. À ce moment-là, si la cible était dans le tableau, elle aurait été trouvée dans une itération précédente, donc nous pouvons conclure que la cible n’est pas présente dans le tableau. Ainsi, l’algorithme retourne -1.

### <H3 STYLE="COLOR:GREEN;">5.2. Correction Totale</H3>

Pour prouver la correction totale, nous devons également prouver que l’algorithme termine toujours. Cela peut être prouvé en utilisant un variant de boucle.

**Variant de Boucle** : Pour l’algorithme de recherche dichotomique, un variant de boucle approprié est la longueur de l’intervalle de recherche, c’est-à-dire droite - gauche.

1 **Définition du Variant** : Au début de chaque itération de la boucle while, le variant est droite - gauche.

2 **Initialisation** :

- Avant la première itération, gauche est initialisé à 0 et droite à len(T) - 1.
- Ainsi, initialement, le variant est len(T) - 1.

3 **Maintien et Diminution du Variant** :

- À chaque itération de la boucle while, la variable milieu est calculée comme la moyenne de gauche et droite.
- Ensuite, il y a trois cas :
  - Cas 1 : Si T[milieu] == x, l’algorithme termine immédiatement.
  - Cas 2 : Si T[milieu] < x, alors gauche est mis à jour à milieu + 1. La nouvelle longueur de l’intervalle de recherche est droite - (milieu + 1), ce qui est strictement inférieur à l’ancienne longueur.
  - Cas 3 : Si T[milieu] > x, alors droite est mis à jour à milieu - 1. La nouvelle longueur de l’intervalle de recherche est (milieu - 1) - gauche, ce qui est strictement inférieur à l’ancienne longueur.
- Dans les cas 2 et 3, la nouvelle valeur de droite - gauche est strictement inférieure à l’ancienne valeur, donc le variant décroît à chaque itération.

4 **Borne Inférieure** :

- Le variant droite - gauche est toujours non négatif.
- La boucle continue tant que gauche <= droite, donc droite - gauche est toujours au moins 0.

5 **Terminaison** : Puisque le variant de boucle commence à une valeur positive et décroît strictement à chaque itération tout en étant borné inférieurement par 0, la boucle doit nécessairement terminer après un nombre fini d’itérations.

## <H2 STYLE="COLOR:BLUE;">6. Implémentation<a name="_page6_x40.00_y408.92"></a> en Python</H2>

=> CAPYTALE Le code vous sera donné par votre enseignant

**<H3 STYLE="COLOR:red;">Activité n°2.:** compléter le script suivant</H3>

```python
def rechercheDichotomique(T , x):
    """
    recherche l'indice d'un élément dans une liste triée
    :param T: tableau d'entier
    :param x: entier
    :return: entier (indice de la valeur)
    """
    # à compléter
```

**Tester avec (ajouter le script suivant à la suite)**

```python
import random
t1 = [random.randint(1,100_000_000) for _ in range(10_000)]
t1.sort()
print(rechercheDichotomique(t1, 0))
```

**<H3 STYLE="COLOR:red;">Activité n°3.: Observation de durées</H3>**

On peut mesurer les durées pour trouver une valeur dans un tableau déjà trié. Comme les temps d’exécution sont très faibles, et que la fonction time est peu précise il faut avoir recours à la fonction magique %timeit de iPython. Voilà un exemple de script pour mesurer les durées sur des tableaux de longueurs différentes :

```python
# construction d'un tableau par compréhension
import random
t1 = [random.randint(1,100_000_000) for _ in range(10_000)]
t1.sort()

t2 = [random.randint(1,100_000_000) for _ in range(100_000)]
t2.sort()

t3 = [random.randint(1,100_000_000) for _ in range(1_000_000)]
t3.sort()

t4 = [random.randint(1,100_000_000) for _ in range(2_000_000)]
t4.sort()

t5 = [random.randint(1,100_000_000) for _ in range(4_000_000)]
t5.sort()
```

Observer et commenter

```
%timeit rechercheDichotomique(t1, 0)
2.69 µs ± 144 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%timeit rechercheDichotomique(t2, 0)
2.9 µs ± 105 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%timeit rechercheDichotomique(t3, 0)
4.02 µs ± 425 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%timeit rechercheDichotomique(t4, 0)
4.37 µs ± 457 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%timeit rechercheDichotomique(t5, 0)
4.64 µs ± 256 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
```

## <H2 STYLE="COLOR:BLUE;">7. Exercices<a name="_page7_x40.00_y407.92"></a></H2>

=> CAPYTALE Le code vous sera donné par votre enseignant

**<H3 STYLE="COLOR:red;">Exercice 1 : Recherche d’un maximum dans une liste de n éléments**</H3> : 

1. Ecrire l’algorithme en pseudo – code
2. Calculer la complexité de cet algorithme
3. L’implémenter en Python
4. Modifier le programme pour créer une fonction ```maximum(T :list) -> int```
5. Tester la fonction avec une liste aléatoire de 20 valeurs

**<H3 STYLE="COLOR:red;">Exercice 2 : Recherche de la moyenne des éléments d’une liste de n éléments**</H3> : 

1. Ecrire l’algorithme en pseudo – code
2. Calculer la complexité de cet algorithme
3. L’implémenter en Python
4. Modifier le programme pour créer une fonction ```moyenne(T :list) -> int```
5. Tester la fonction avec une liste aléatoire de 20 valeurs

**<H3 STYLE="COLOR:red;">Exercice 3 : Recherche en table**</H3>

Si on utilisait une méthode séquentielle pour chercher un nom dans un annuaire, on ouvrirait celui-ci à la première page et on comparerait le nom recherché au premier nom de l’annuaire, puis au deuxième, puis au troisième, etc., jusqu’à trouver le nom recherché, ou arriver au dernier nom de l’annuaire. Un annuaire contenant 30.000 noms et une comparaison prenant 100 ms, il faudrait, dans le pire des cas, 3.000 secondes, soit 50 minutes, pour trouver le nom recherché ou se convaincre qu’il n’appartient pas à l‘annuaire.

Bien entendu, ce n’est pas ainsi que l’on procède : on ouvre l‘annuaire au milieu, on compare le nom recherché au nom médian. Si le nom recherché est avant le nom médian dans l’ordre alphabétique, on élimine la seconde moitié de l’annuaire, sans même la regarder ; s’il est après le nom médian, on élimine la première moitié. En recommençant avec le demi-annuaire restant, on élimine ensuite un demi-demi-annuaire et on continue jusqu’à trouver le nom en question ou obtenir l’ensemble vide.

1. Compléter le tableau ci-dessous pour rechercher un nom dans un annuaire de 30.000 noms :

|**Comparaison** |**Ensemble de recherche (mots)** |
| - | - |
|1 |15\.000 |
|2 |7\.500 |
|... |... |

2. En déduire le temps de recherche dans le pire des cas et conclure.

On appelle logarithme à base 2, log<sub>2</sub>(x) d’un nombre x ≥ 1, le nombre de fois qu’il faut le diviser x par 2 pour obtenir un nombre inférieur ou égal à 1.

Sur la calculatrice, log<sub>2</sub>(x) = $\frac{log(x)}{log(2)}$

3. A partir du logarithme à base 2, retrouver le résultat obtenu à la question 1.
4. Calculer le temps nécessaire pour rechercher un nom dans l’annuaire français pour n = 60 millions d’entrées.