---

author: ELP
title: 09 Algorithme glouton

---

**Table des matières** 

1. [ALGORITHMES GLOUTONS](#_page0_x51.00_y229.00)
2. [EXERCICES](#_page7_x51.00_y32.00)
3. [PROBLEME : TSP - LE VOYAGEUR DE COMMERCE](#_page9_x51.00_y32.00)

## <H2 STYLE="COLOR:BLUE;"> **1. Algorithmes<a name="_page0_x51.00_y229.00"></a> gloutons**</H2> 

En informatique, un algorithme glouton (greedy algorithm) est une **technique** permettant de résoudre un problème. Un algorithme glouton va aborder la résolution d'un problème en plusieurs étapes :

- À chaque étape, l’algorithme va adopter un choix qui lui **semble le meilleur,** et ce, **dans l'espoir** qu'à la fin de la résolution, le résultat obtenu soit lui-même **optimal**. 
- Mais un algorithme glouton **ne repart jamais en arrière** afin de modifier ses choix (le choix qui semble le meilleur à un instant t est définitif) donc il se peut que le résultat final ne soit pas. 

Les algorithmes gloutons servent principalement à résoudre des **problèmes d'optimisation**. Il existe de multiples exemples. 

### <H3 STYLE="COLOR:GREEN;"> **1.1. Le<a name="_page0_x51.00_y404.00"></a> problème de rendu de monnaie**</H3> 

Un des grands classiques est le problème du rendu de monnaie où l'on souhaite rendre une somme en utilisant le moins de pièces (ou de billets) possibles. Le principe de l'algorithme consiste à répéter **le choix de la pièce de plus grande valeur** qui ne dépasse pas la somme restante. 

**Remarque** : On dit qu'il s'agit d'un algorithme glouton, car il choisit la pièce la plus grosse à chaque étape sans réfléchir à la suite. 

Exemple avec le système de pièces européen : Rendre la somme de 8€ 

![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.004.png)
<table xmlns="http://www.w3.org/1999/html">
<tr><td colspan="11">Solution optimale</td><td colspan="11">Solution non optimale </td></tr>

<td colspan="11">1 billet de 5€<br> 1 pièce de 2€ <br>1 pièce de 1€</td><td colspan="11">4 pièces de 2€</td></tr>
</table>


Avec le système de pièces européen, l’algorithme glouton donne toujours un choix optimal. 

Mais que se passe-t-il, si l’on utilise un autre monnayeur avec des pièces différentes ? 

Rendre la somme de 6 €

![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.005.png)
<table>
<tr><td colspan="11">Solution optimale</td><td colspan="11">Solution non optimale </td></tr>
<tr><td colspan="11">2 pièces de 3€</td><td colspan="11">1 pièce de 4€<br>  2 pièces de 1€ <br>Total : 3 pièces (algorithme glouton)</td></tr>
</table>

=> **CAPYTALE Le code vous sera donné par votre enseignant**

**<H3 STYLE="COLOR:RED;">Activité n°1.**</H3> Rendu de monnaie : Traduire l’algorithme suivant, en Python dans capytale

```
Fonction renduMonnaie (somme : entier, pièces : liste des pièces dans l’ordre décroissant) : liste des pièces choisies

	n←longueur de la liste de pièces
	initialiser à zéro la liste "choisies" de dimension n
	Pour i de 1 à n par pas de 1
		Tant que somme>= pieces[i]
			somme←somme-pieces[i]
			choisies[i]← choisies[i]+1
		fin tant que
	fin pour
    retourner choisies
``` 
Aide : 	

- le prototype de la fonction est donc : ```renduMonnaie(somme: int, pieces: list) -> list``` 

- Ne pas oublier de documenter la fonction 

**Test n°1 :**
```python
#pieces en centimes d'euros
pieces=[500,200,100,50,20,10,5,2,1]
somme=780
print('Les pièces choisies sont')
print(renduMonnaie(somme,pieces))
```

Soit 780 centimes, <b>l’algorithme fonctionne et est optimal</b> avec le système de pièces européen  

**Test n°2 :**
```python
print('Test n°2')
#pieces en euros
pieces=[4,3,1]
somme=6
print('Les pièces choisies sont')
print(renduMonnaie(somme,pieces))
```

Soit 6 euros, l’algorithme fonctionne, <b>mais n’est pas optimal</b>, car on aurait pu rendre 2 pièces de 3 € 

**Remarque**:  Il existe d’autres méthodes permettant d’optimiser le rendu de monnaie comme la programmation dynamique (non abordé ici). L’idée est de calculer toutes les possibilités permettant d’obtenir 6 € avec le jeu de pièces tout en choisissant le nombre minimal de pièces.

**Test n°3**
```python
print('Test n°3')
#pieces en euros
pieces=[10,5,2]
somme=31
print('Les pièces choisies sont')
print(renduMonnaie(somme,pieces))
```

Soit 30 euros, l’algorithme ne fonctionne plus, car il manque une pièce de 1 euro. 

### <H3 STYLE="COLOR:GREEN;"> **1.2. Le<a name="_page2_x51.00_y32.00"></a> problème du sac à dos**</H3> 

Le problème du sac à dos (knapsack problem) est aussi un **problème d’optimisation.** Il permet de résoudre le problème du remplissage d’un sac à dos. 

On dispose pour cela de plusieurs objets (chaque objet possède une valeur et un poids). Seulement le sac ne peut pas contenir plus d’un certain poids. Le but des de choisir judicieusement les objets afin de **maximiser la valeur des objets** sans dépasser le poids maximum. 

L’algorithme glouton va choisir **à chaque étape du remplissage l’objet de plus grande valeur**. On répète les étapes du remplissage juste avant que le poids maximal soit atteint. 

Exemple : 

<table><tr><th colspan="1" rowspan="2"><b>Matériel à emmener dans un sac de 4.7KG</b> </th><th colspan="1" rowspan="2">Valeur et poids </th><th colspan="4">Emporté (oui/non) </th></tr>
<tr><td colspan="1">Etape1 </td><td colspan="1">Etape2 </td><td colspan="1">Etape3 </td><td colspan="1">Etape4 </td></tr>
<tr><td colspan="1">gourde</td><td colspan="1">Valeur : 2 </br>Poids : 1 </td><td colspan="1">x </td><td colspan="1">x </td><td colspan="1">Pas possible</td><td colspan="1"><p>Pas possible</p></td></tr>
<tr><td colspan="1">jumelles</td><td colspan="1">Valeur : 5 </br>Poids : 0.5 </td><td colspan="1">Oui </td><td colspan="1">Déjà pris </td><td colspan="1">Déjà pris </td><td colspan="1">Déjà pris </td></tr>
<tr><td colspan="1">carte</td><td colspan="1">Valeur : 1 </br>Poids : 0.2 </td><td colspan="1">x </td><td colspan="1">x </td><td colspan="1">x </td><td colspan="1">Oui </td></tr>
<tr><td colspan="1">tente</td><td colspan="1">Valeur : 3 </br>Poids : 4 </td><td colspan="1">x </td><td colspan="1">oui </td><td colspan="1">Déjà pris </td><td colspan="1">Déjà pris </td></tr>
</table>

**<H3 STYLE="COLOR:RED;">Activité n°2.**: Sac à dos :</H3> affichage des objets choisis selon leur valeur: Traduire l’algorithme suivant, en Python dans capytale : 
```
Fonction remplirSac (objets : liste des objets dans l’ordre décroissant, poidsMax : en décimal) : liste des objets choisis

	p←0


	n←longueur de la liste des objets
	initialiser à zéro la liste objetschoisis de dimension n
	Pour i de 1 à n par pas de 1
		Si p+objets[i][1]<= poidsMax alors
			objetsChoisis[i]←1
			p ← p + objets[i][1]
		fin si
	fin pour
	retourner objetschoisis
```

**Aide :** 

- Ne pas oublier le prototype de la fonction et de la documenter

**Test** 

Attention **: il faudra trier les objets par ordre décroissant de valeur** avant d’appeler la fonction remplirSac(objets,poidsMax)

**Résultat dans la console** 
```python
print('Test')
#liste du matériel
objets=[[2,1],[5,0.5],[1,0.2],[3,4]]
objets=list(reversed(sorted(objets)))
print(objets)
poidsMax=4.7
print('Les objets choisis sont')
print(remplirSac(objets,poidsMax))
```

L’algorithme choisit bien les articles selon notre prévision.

**<H3 STYLE="COLOR:RED;">Activité n°3.**: Sac à dos :</H3> affichage des objets choisis selon leur valeur et du poids total : 

Avant de partir aux Bahamas, on doit remplir sa valise. La compagnie d’aviation n’accepte qu’une valise de dépassant pas 23kg. 

La liste des objets est la suivante :
```python
objets=[[6,5.0,'chaussures'],[5,5.0,'habits'],[4.5,2.0,'trousse de toilette'],[4,2.0,'crêmes'],[3,8.0,'livres'],[2,2.0,'palmes tuba'],[1,0.5,'guide touristique']]
```

exemple :  
```[6,5.0,'chaussures'] → 6 : valeur, 5.0 : poids, 'chaussures' : désignation ```

Utiliser l’algorithme glouton correspondant afin d’indiquer les objets pouvant être mis dans la valise. Coder une fonction ```remplirSacpoids``` qui tiennent compte de la nouvelle situation et qui soit basée sur l'algorithme glouton 

**<H3 STYLE="COLOR:RED;">Activité n°4.**: Sac à dos V2 :</H3> affichage des objets choisis selon leur valeur avec leur nombre: on veut retourner un dictionnaire. Coder une fonction ```remplirSacDico``` qui tiennent compte de la nouvelle situation et qui soit basée sur l'algorithme glouton
Le prototype de la fonction est : 
```remplirSacDico(objets: list,poidsMax: float) -> dict: ```

**Résultat attendu** : 
```{'chaussures': 1, 'habits': 1, 'trousse de toilette': 1, 'crèmes': 1, 'livres': 1, 'palmes tuba': 0, 'guide touristique': 1} ```

**<H3 STYLE="COLOR:RED;">Activité n°5.**: Sac à dos V3 :</H3> affichage des objets choisis selon leur valeur avec leur nombre différent de 0 : 
on veut retourner un dictionnaire qui n’affichera que les objets réellement mis dans la valise (dont le nombre d’objet !=0). Coder une fonction ```remplirSacDico_V2``` qui tiennent compte de la nouvelle situation et qui soit basée sur l'algorithme glouton

**Résultat attendu :** 
```{'chaussures': 1, 'habits': 1, 'trousse de toilette': 1, 'crèmes': 1, 'livres': 1, 'guide touristique': 1} ```

**Remarque** :  
L’algorithme glouton est un algorithme qui ne remet jamais en cause une décision prise auparavant.  

C’est donc une **méthode de résolution approchée.** Pour trouver la solution optimale, et être certain qu’il n’y a pas mieux, il faut utiliser une méthode exacte qui demande un temps de calcul beaucoup plus long. On peut citer la procédure par  séparation  et  évaluation  (PSE)  qui  peut  énumère  toutes  les  solutions  possibles,  mais  seules  les  solutions potentiellement de bonnes qualités sont énumérées. Il faut alors mettre en place un ***arbre de recherche*** qui sera vu en terminale. 

## <H2 STYLE="COLOR:BLUE;"> **2. Exercice<a name="_page7_x51.00_y32.00"></a>**</H2>  

=> **CAPYTALE Le code vous sera donné par votre enseignant**

★ **<H3 STYLE="COLOR:RED;">Rendu de monnaie**</h3> 

Étant donné un système de monnaie (pièces et billets), comment rendre une somme donnée de façon optimale, c'est-à- dire avec le nombre minimal de pièces et billets ? 

Par exemple, la meilleure façon de rendre 7€ est de rendre un billet de cinq et une pièce de deux, même si d'autres façons existent (rendre 7 pièces de 1€, par exemple). 

Ce problème est **NP-complet**[^1] dans le cas général, c'est-à-dire difficile à résoudre. Cependant pour certains systèmes de monnaie, l'algorithme glouton est optimal, c'est-à-dire qu'il suffit de rendre systématiquement la pièce ou le billet de valeur maximale — ce tant qu'il reste quelque chose à rendre. 

Dans la zone euro, le système S en vigueur est, en mettant de côté les centimes d'euros : 

```S = (1, 2, 5, 10, 20, 50, 100, 200, 500)```. 

Il y a par exemple six triplets de pièces (ou billets) de 1, 2 et 5 euros qui permettent de rendre la valeur v = 7€ (les billets de 10 euros ou plus étant inutiles) : (7,0,0), (5,1,0), (3,2,0), (1,3,0), (2,0,1), (0,1,1). 

La solution au problème de rendu de monnaie (S, 7) est alors le triplet (x1, x2, x3) qui minimise le nombre total x1 + x2 + x3 de pièces rendues, soit (0, 1, 1), c'est-à-dire une pièce de 2 euros et une de 5 (un billet). On a donc le nombre minimal de pièces du système $M_{(1,2 5)}$(7) = 2. 

Pour rendre toute somme inférieure à 500€ pièces il faut au plus 3 pièces pour les unités, 3 billets pour les dizaines et jusqu'à 2 billets pour les centaines, soit au plus 8 pièces ou billets. L'optimum au-delà est alors formé de $v/500$ billets de 500€, plus les pièces et billets nécessaires pour le reste v modulo 500€. 

Ainsi, 2019 = 500×4 + 19 = 500×4 + 10×1 + 5×1 + 2×2, soit 4+1+1+2 = 6 billets et 2 pièces. 

1 Écrire **l’algorithme de rendu de monnaie en pseudo-code** pour une valeur** v à rendre avec un système de pièces S, trié par ordre croissant.  

**Aide :** 

- Noter les entrées et le(s) sortie(s).  
- S’inspirer de l’algorithme en pseudo-code de recherche dichotomique 

2 Montrer que l’algorithme termine. 

**Rappels :** 

Pour s'assurer qu'un algorithme est correct, il faut démontrer deux choses : 

- que l'algorithme se termine (**terminaison**), autrement dit qu'il **ne boucle pas** ou ne diverge pas, produisant au moins un résultat. 

- que le résultat de l'algorithme **satisfait la spécification du résultat** comme énoncé dans la description de l'algorithme (**correction partielle**). 

La conjonction de la **correction partielle et de la terminaison** s'appelle la **correction totale.** 

3 Implémenter cet algorithme en langage Python. On donne le prototype de la fonction : 

```rendu(S : list, valeur : int) -> list``` 

- ```S``` -- liste des pièces ordonnées 

- ```valeur``` -- somme à rendre 

- la fonction retourne la liste des pièces à rendre 

4 Documenter la fonction  

5 Tester le programme pour deux systèmes de monnaies : 

- européen : ```S = (1, 2, 5, 10, 20, 50, 100, 200, 500)```

- royaume uni : ```S = (1, 3, 4, 10, 30, 40, 100, 300, 400)```[^2] on prendra 2019 pour somme à rendre 

★★ **<H3 STYLE="COLOR:RED;">le voyageur**</h3>

Une route comporte n+1 stations-service, numérotées dans l'ordre du parcours, de 0 à n. La première est à une distance d[0] du départ, la deuxième est à une distance d[1] de la première, la troisième à une distance d[2] de la deuxième, etc. La fin de la route est à une distance d[n] de la n-ième et dernière station-service. 

Un automobiliste prend le départ de la route avec une voiture dont le réservoir d'essence est plein. Il désire faire le plein le moins souvent possible. Sa voiture possède une autonomie notée autonomie avec un plein. 

1 Écrire l’algorithme qui détermine à quelles stations-service il doit s'arrêter avec la distance parcourue. 

2 Montrer que l’algorithme termine. 

3 Implémenter cet algorithme en langage Python. On donne le prototype de la fonction : 
```voyage(distance : list, autonomie : int) -> list```

- ```distance``` -- liste des distances entre les stations-service 

- ```autonomie``` -- distance maximum que l'on peut parcourir 

- la fonction retourne la liste de tuple (numéro de la station, distance parcourue depuis le début) 

4 Documenter la fonction 

5 Tester le programme : 

- 17 stations-service avec 

```python
distance = [23, 40, 12, 44, 21, 9, 67, 32, 51, 30, 11, 55, 24, 64, 32, 57, 12, 80] 
autonomie = 100 
```

★★★ **<H3 STYLE="COLOR:RED;">le cambrioleur**</h3> 

Un cambrioleur entre par effraction dans une maison. Il n'est capable de porter qu’une masse limitée : il lui faudra donc choisir entre les différents objets de valeur, afin d'amasser le plus gros magot possible. 

1 Écrire un algorithme qui donne un choix optimal pour le voleur. 

**Aide** : 

- Pour amasser le plus gros butin, il suffit de considérer le rapport prix/masse. A chaque fois, on en prend le rapport maximal. 
- il faut rajouter ce critère à la liste [prix, poids] et la trier sur ce critère par ordre décroissant. 

2 Montrer que cet algorithme termine.

3 Programmez une fonction remplir dont le prototype est le suivant : 
```voleur(articles : list, masse : int) -> list```

- ```articles``` -- liste des articles (masse, valeur)  

- ```masse``` -- masse maximale

- la fonction retourne la liste des articles : liste de tuple(masse, valeur)

- Le programme ou la fonction précédente retournera aussi** la masse totale **et** la valeur totale 

4 Documenter la fonction 

On dispose d’une liste d’objets de masses ```m = [9, 10, 12, 14, 11, 5, 7, 5, 6, 2]``` ainsi que de leurs valeurs associées ```v = [10, 8, 7, 7, 5, 4, 3, 2, 2, 1]```.

5 Tester le programme pour une masse maximale de 22 kg. Conclure. 

## <H2 STYLE="COLOR:BLUE;"> **3.  Problème : TSP - Le voyageur de commerce<a name="_page9_x51.00_y32.00"></a>**</H2> 

Le problème du voyageur de commerce - *Traveling Salesman Problem* TSP -, étudié depuis le 19e siècle, est l’un des plus connus dans le domaine de la recherche opérationnelle. William Rowan Hamilton a posé pour la première fois ce problème sous forme de jeu dès 1859.

**Problème**  
![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.028.jpeg)

Le problème du TSP sous sa forme la plus classique est  le suivant : « Un voyageur de commerce doit visiter une  et une seule fois un nombre fini de villes et revenir à son  point d’origine. **Comment trouver l’ordre de visite des  villes qui minimise la distance totale parcourue par le  voyageur. ? »** 

Ce problème d’optimisation combinatoire appartient à la  classe des problèmes NP-Complets. 

Les domaines d’application sont nombreux : problèmes  de logistique, de transport aussi bien de marchandises  que  de  personnes,  et plus largement  toutes  sortes  de  problèmes d’ordonnancement.  Certains  problèmes rencontrés dans l’industrie se modélisent sous la forme  d’un  problème  de  voyageur  de  commerce, comme  l’optimisation  de  trajectoires  de  machines outils  :  comment  percer  plusieurs  points  sur  une carte  électronique le plus vite possible ? 

**<H3 STYLE="COLOR:RED;">Exercice 1 :**</H3> 

1- Pour un ensemble de 4 villes, combien existe t-il de chemins différents possibles ?  

2- Pour un ensemble de 5 villes, combien existe t-il de chemins possibles ?

3- Pour un ensemble de 71 villes, combien existe t-il de chemins différents possibles ?

4- Sachant que mon ordinateur est capable de traiter 10 000 000 de trajets par seconde, en combien de temps aura t-il traité le problème des 71 villes ? 

**L'objectif de ce TP est de réaliser un algorithme glouton pour résoudre le TSP** en considérons les villes nommées succinctement A, B, C, D, E, F et G dont ont connaît les coordonnées géographiques (longitude, latitude) :

**A ( 0 ; 0 )  B ( 7 ; 3 )  C ( 3 ; 1 )  D ( 2 ; 4 )  E ( 4 ; 6 )  F ( 3 ; 2 )  G ( 5 ; 0 )**

**<H3 STYLE="COLOR:RED;">Exercice 2  :**</H3> Sur la première "carte" à votre disposition, **en partant de la ville F (que vous entourerez)**, tracer l'itinéraire (boucle) **qui vous semble optimal pour minimiser la distance à parcourir**.

**<H3 STYLE="COLOR:RED;">Exercice 3 :**</H3> Ecrire en une phrase **la méthode gloutonne** qui détermine le choix (qui vous semble optimale) de votre prochaine étape.

**<H3 STYLE="COLOR:RED;">Exercice 4 :**</H3> sur chacune des autres "cartes" à votre disposition, **en partant d'une autre ville (que vous entourerez)**, tracer l'itinéraire (boucle) déterminée par la méthode gloutonne précédente.![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.009.png)

**<H3 STYLE="COLOR:RED;">Exercice 5 :**</H3>Quels sont les itinéraires qui paraissent bien "longs" et que l’on peut éliminer ?

Visuellement, à l'aide de la carte, vous arrivez assez facilement à distinguer quelle est la ville la plus proche de votre étape, mais un ordinateur n'a pas accès à cette "vision d'ensemble"! Pour chaque étape, il doit calculer la distance qui sépare la position actuelle de chacune des autres villes à partir de leur coordonnées.

**A vous de vous mettre dans "la peau d'un ordinateur" en CACHANT les cartes.**

**<H3 STYLE="COLOR:RED;">Exercice 6 :**</H3>

Compléter le *distancier* ci-dessous en utilisant les coordonnées des villes :

**A ( 0 ; 0 )  B ( 7 ; 3 )  C ( 3 ; 1 )  D ( 2 ; 4 )  E ( 4 ; 6 )  F ( 3 ; 2 )  G ( 5 ; 0 )![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.009.png)**

<table>
<tr><td colspan="1"></td><td colspan="1">A</td><td colspan="1">B</td><td colspan="1">C</td><td colspan="1">D</td><td colspan="1">E</td><td colspan="1">F</td><td colspan="1">G</td></tr>
<tr><td colspan="1">A</td><td colspan="1">0 </td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td></tr>
<tr><td colspan="1">B</td><td colspan="1"></td><td colspan="1">0</td><td colspan="1"></td><td colspan="1">√26</td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td></tr>
<tr><td colspan="1">C</td><td colspan="1"> </td><td colspan="1"></td><td colspan="1">0</td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td></tr>
<tr><td colspan="1">D</td><td colspan="1"> </td><td colspan="1">√26</td><

td colspan="1"></td><td colspan="1">0</td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td></tr>
<tr><td colspan="1">E</td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1">0</td><td colspan="1"></td><td colspan="1"></td></tr>
<tr><td colspan="1">F</td><td colspan="1"> </td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1">0</td><td colspan="1"></td></tr>
<tr><td colspan="1">G</td><td colspan="1"> </td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1"></td><td colspan="1">0</td></tr>
</table>


Exemple : détermination de la distance BD ou DB: B ( 7 ; 3 )	D ( 2 ; 4 )

D'après le théorème de Pythagore : 
```
BD² = (xB-xD)² + (yB – yD)²
    = (7-2)²+(3-4)²
    = 5² + 1² 
    = 25 + 1 
    = 26
```

Avec un petit peu d'organisation, on pourrait se répartir le travail…

**Uniquement en utilisant ce distancier (SANS REGARDER les "cartes"), déterminer :** 

Itinéraire glouton en partant de A : Longueur de l'itinéraire en partant de A :

Itinéraire glouton en partant de B : Longueur de l'itinéraire en partant de B :

Itinéraire glouton en partant de C : Longueur de l'itinéraire en partant de C : 

Itinéraire glouton en partant de D : Longueur de l'itinéraire en partant de D :

Itinéraire glouton en partant de E : Longueur de l'itinéraire en partant de E :

Itinéraire glouton en partant de F : Longueur de l'itinéraire en partant de F :

Itinéraire glouton en partant de G : Longueur de l'itinéraire en partant de G :

**Pour le plus court itinéraire glouton : il faut partir de … **

**Longueur de ce plus court itinéraire :**

 

![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.033.png) ![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.033.png)

![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.033.png) ![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.033.png)

![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.033.png) ![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.033.png)

![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.033.png) ![](Aspose.Words.35e5d16a-adab-4fc0-8fbe-75d584bf8d1c.033.png)

**Maintenant c’est à vous de compléter le fichier sur capytale**  




[^1]: c'est-à-dire un problème complet pour la classe NP (non déterministe polynomial) 
[^2]: avant sa réforme en 1971

