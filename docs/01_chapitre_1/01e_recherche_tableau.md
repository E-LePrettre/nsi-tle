---
author: ELP
title: 01e Fiche méthode - Recherche d'une valeur dans un tableau
---




## **<H2 STYLE="COLOR:BLUE;">Rechercher une valeur dans un tableau (version 1)</H2>**

### **<H3 STYLE="COLOR:GREEN;">Énoncé</H3>**

À partir d’une liste de `n` notes de la classe, rechercher la présence de la note 12/20.

### **<H3 STYLE="COLOR:GREEN;">Exemple</H3>**

- **<H3 STYLE="COLOR:RED;">Liste de notes n°1 :</H3>** 5 14 18 11 10 12 10 9 16 : oui la note est présente
- **<H3 STYLE="COLOR:RED;">Liste de notes n°2 :</H3>** 5 14 18 11 10 11 10 9 16 : non la note n’est pas présente

### **<H3 STYLE="COLOR:GREEN;">Solution</H3>**

Rechercher une valeur dans un tableau de dimension `n`. Retourner vrai si la note est présente, faux dans le cas contraire.

#### **<H4 STYLE="COLOR:MAGENTA;">Entrées</H4>**

Tableau de valeurs et note à rechercher.

#### **<H4 STYLE="COLOR:MAGENTA;">Sortie</H4>**

Valeur booléenne (vrai ou faux) représentant la présence de la valeur à chercher.

#### **<H4 STYLE="COLOR:MAGENTA;">Pré-condition</H4>**

Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.

#### **<H4 STYLE="COLOR:MAGENTA;">Post-condition</H4>**

Un booléen vrai est retourné si la note est présente dans le tableau.

### **<H3 STYLE="COLOR:GREEN;">Algorithme en pseudo-code</H3>**

**Programme en python**

```python
def rechercheNote(Liste, note):
    for i in range(len(Liste)):
        if Liste[i] == note:
            return True
    return False

print(rechercheNote([5, 14, 18, 11, 10, 12, 10, 9, 16], 12))
```

???+ question "Tester ce qui est proposé"

    {{ IDE() }}

**Complexité de l’algorithme** : O(n) car il faut parcourir le tableau de dimension n.

### **<H3 STYLE="COLOR:GREEN;">Résultats du test :</H3>**

???+ question "Test effectué avec la liste : Liste = [5, 18, 10, 12, 10, 14, 18] et la note à rechercher 12."

    **Compléter le tableau suivant**   
    | Étape                        | Note à chercher | Variable i | Liste[i] | Variable trouve |
    |------------------------------|-----------------|-----------------|---------------|-----------------|
    | Avant de rentrer dans la boucle | 12              |                 |               | Faux            |
    | Dans la boucle (1ère itération)  | 12              | 0               | 5             | Faux            |
    | Dans la boucle (2ème itération)  | 12              |                 |               |                 |
    | Dans la boucle (3ème itération)  | 12              |                 |               |                 |
    | Dans la boucle (4ème itération)  | 12              |                 |               |                 |
    | Dans la boucle (5ème itération)  | 12              |                 |               |                 |
    | Dans la boucle (6ème itération)  | 12              |                 |               |                 |
    | Dans la boucle (7ème itération)  | 12              |                 |               |                 |
    | En sortie de boucle              | 12              |                 |               |                 |


    ??? success "Solution"

        La couleur du cheval blanc d'Henri IV est le blanc. En fait  la robe du cheval d'Henri IV était probablement grise.

    **2.** Question 2.   
    Quelle est la proportion de la terre recouverte par les océans ?

    ??? success "Solution"

        Environ 71 %.

        Pour approfondir : [Lien wikipédia sur les océans](https://fr.wikipedia.org/wiki/Oc%C3%A9an){ .md-button target="_blank" rel="noopener" }





Conclusion : L’algorithme se termine en un temps fini et produit la sortie désirée (présence ou non de la valeur recherchée).

## **<H2 STYLE="COLOR:BLUE;">Rechercher une valeur dans un tableau (version 2)</H2>**

### **<H3 STYLE="COLOR:GREEN;">Énoncé</H3>**

À partir d’une liste de `n` notes de la classe, rechercher la présence de la note 12/20.

### **<H3 STYLE="COLOR:GREEN;">Exemple</H3>**

- **<H3 STYLE="COLOR:RED;">Liste de notes n°1 :</H3>** 5 14 18 11 10 12 10 9 16 : oui la note est présente
- **<H3 STYLE="COLOR:RED;">Liste de notes n°2 :</H3>** 5 14 18 11 10 11 10 9 16 : non la note n’est pas présente

### **<H3 STYLE="COLOR:GREEN;">Solution</H3>**

Rechercher une valeur dans un tableau de dimension `n`. Retourner vrai si la note est présente, faux dans le cas contraire.

#### **<H4 STYLE="COLOR:MAGENTA;">Entrées</H4>**

Tableau de valeurs et note à rechercher.

#### **<H4 STYLE="COLOR:MAGENTA;">Sortie</H4>**

Valeur booléenne (vrai ou faux) représentant la présence de la valeur à chercher.

#### **<H4 STYLE="COLOR:MAGENTA;">Pré-condition</H4>**

Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.

#### **<H4 STYLE="COLOR:MAGENTA;">Post-condition</H4>**

Un booléen vrai est retourné si la note est présente dans le tableau.

### **<H3 STYLE="COLOR:GREEN;">Algorithme en pseudo-code</H3>**

**Programme en python**

```python
def rechercheNote(Liste, note):
    trouve = False
    i = 0
    while not trouve and i < len(Liste):
        if Liste[i] == note:
            trouve = True
        i += 1
    return trouve

print(rechercheNote([5, 14, 18, 11, 10, 12, 10, 9, 16], 12))
```

???+ question "Tester ce qui est proposé"

    {{ IDE() }}

**Complexité de l’algorithme** : O(n) car il faut parcourir le tableau de dimension n.

### **<H3 STYLE="COLOR:GREEN;">Résultats du test :</H3>**

Test effectué avec la liste : Liste = [5, 14, 18, 12, 10, 10, 9, 16] et la note à rechercher 12.

| Étape                        | Note à chercher | Variable i | Liste[i] | Variable trouve |
|------------------------------|-----------------|-----------------|---------------|-----------------|
| Avant de rentrer dans la boucle | 12              | 0               |               | Faux            |
| Dans la boucle (1ère itération)  | 12              | 0               | 5             | Faux            |
| Dans la boucle (2ème itération)  | 12              |                 |               |                 |
| Dans la boucle (3ème itération)  | 12              |                 |               |                 |
| Dans la boucle (4ème itération)  | 12              |                 |               |                 |
| En sortie de boucle              | 12              |                 |               |                 |


Intérêt de la boucle « while » par rapport à la boucle « for » : Le parcours du tableau pour trouver la valeur peut se terminer plus rapidement en fonction de la position de la valeur dans le tableau.

Conclusion : On a une affectation supplémentaire et une condition supplémentaire...

## **<H2 STYLE="COLOR:BLUE;">Rechercher une valeur maximale dans un tableau</H2>**

### **<H3 STYLE="COLOR:GREEN;">Énoncé</H3>**

À partir d’une liste de `n` notes de la classe, rechercher la note maximale.

### **<H3 STYLE="COLOR:GREEN;">Exemple</H3>**

- **<H3 STYLE="COLOR:RED;">Liste de notes :</H3>** 5 14 18 11 10 12 10 9 16 : note max : 18

### **<H3 STYLE="COLOR:GREEN;">Solution</H3>**

Rechercher la valeur maximale dans un tableau de dimension `n` puis retourner cette valeur.

#### **<H4 STYLE="COLOR:MAGENTA;">Entrée</H4>**

Tableau de valeurs.

#### **<H4 STYLE="COLOR:MAGENTA;">Sortie</H4>**

Valeur de la note maximale.

#### **<H4 STYLE="COLOR:MAGENTA;">Pré-condition</H4>**

Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.

#### **<H4 STYLE="COLOR:MAGENTA;">Post-condition</H4>**

Une valeur (entière ou décimale) maximale du tableau est retournée.

### **<H3 STYLE="COLOR:GREEN;">Algorithme en pseudo-code</H3>**

**Programme en python**

```python
def maxNote(Liste):
    maxi = Liste[0]
    for i in range(1, len(Liste)):
        if Liste[i] > maxi:
            maxi = Liste[i]
    return maxi

print(maxNote([5, 14, 18, 12, 10, 10, 9, 16]))
```

???+ question "Tester ce qui est proposé"

    {{ IDE() }}

**Complexité de l’algorithme** : O(n) car il faut parcourir le tableau de dimension n.

### **<H3 STYLE="COLOR:GREEN;">Résultats du test :</H3>**

Test effectué avec la liste : Liste = [5, 14, 18, 12, 10, 10, 9, 16]

| Étape                        | Variable i | Liste[i] | Variable maxi |
|------------------------------|-----------------|---------------|-----------------|
| Avant de rentrer dans la boucle |                 | 5             | 5               |
| Dans la boucle (1ère itération)  | 1               | 14            | 14              |
| Dans la boucle (2ème itération)  |                 |               |                 |
| Dans la boucle (3ème itération)  |                 |               |                 |
| Dans la boucle (4ème itération)  |                 |               |                 |
| Dans la boucle (5ème itération)  |                 |               |                 |
| Dans la boucle (6ème itération)  |                 |               |                 |
| Dans la boucle (7ème itération)  |                 |               |                 |
| Dans la boucle (8ème itération)  |                 |               |                 |
| En sortie de boucle              |                 |               |                 |

Conclusion : L’algorithme se termine en un temps fini et produit la sortie désirée (valeur maximale du tableau trouvée).

## **<H2 STYLE="COLOR:BLUE;">Rechercher une valeur minimale dans un tableau</H2>**

### **<H3 STYLE="COLOR:GREEN;">Énoncé</H3>**

À partir d’une liste de `n` notes de la classe, rechercher la note minimale.

### **<H3 STYLE="COLOR:GREEN;">Exemple</H3>**

- **<H3 STYLE="COLOR:RED;">Liste de notes :</H3>** 14 18 11 10 5 10 9 16 : note min : 5

### **<H3 STYLE="COLOR:GREEN;">Solution</H3>**

Rechercher la valeur minimale dans un tableau de dimension `n` puis retourner cette valeur.

#### **<H4 STYLE="COLOR:MAGENTA;">Entrée</H4>**

Tableau de valeurs.

#### **<H4 STYLE="COLOR:MAGENTA;">Sortie</H4>**

Valeur de la note minimale.

#### **<H4 STYLE="COLOR:MAGENTA;">Pré-condition</H4>**

Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.

#### **<H4 STYLE="COLOR:MAGENTA;">Post-condition</H4>**

Une valeur (entière ou décimale) minimale du tableau est retournée.

### **<H3 STYLE="COLOR:GREEN;">Algorithme en pseudo-code</H3>**

**Programme en python**

```python
def minNote(Liste):
    valeur = Liste[0]
    for indice in range(1, len(Liste)):
        if Liste[indice] < valeur:
            valeur = Liste[indice]
    return valeur

print(minNote([14, 18, 12, 10, 5, 10, 9, 16]))
```

Complexité de l’algorithme : O(n) car il faut parcourir le tableau de dimension n.

### **<H3 STYLE="COLOR:GREEN;">Résultats du test :</H3>**

Test effectué avec la liste : Liste = [14, 18, 12, 10, 5, 10, 9, 16]

| Étape                        | Variable indice | Liste[indice] | Variable valeur |
|------------------------------|-----------------|---------------|-----------------|
| Avant de rentrer dans la boucle |                 | 14            | 14              |
| Dans la boucle (1ère itération)  | 1               | 18            | 14              |
| Dans la boucle (2ème itération)  |                 |               |                 |
| Dans la boucle (3ème itération)  |                 |               |                 |
| Dans la boucle (4ème itération)  |                 |               |                 |
| Dans la boucle (5ème itération)  |                 |               |                 |
| Dans la boucle (6ème itération)  |                 |               |                 |
| Dans la boucle (7ème itération)  |                 |               |                 |
| En sortie de boucle              |                 |               |                 |

Conclusion : L’algorithme se termine en un temps fini et produit la sortie désirée (valeur minimale du tableau trouvée).

## **<H2 STYLE="COLOR:BLUE;">Calculer la valeur moyenne d’un tableau</H2>**

### **<H3 STYLE="COLOR:GREEN;">Énoncé</H3>**

À partir d’une liste de `n` notes de la classe, calculer la moyenne des notes.

### **<H3 STYLE="COLOR:GREEN;">Exemple</H3>**

- **<H3 STYLE="COLOR:RED;">Liste de notes :</H3>** 14 18 11 10 5 10 9 16 : moyenne : 

### **<H3 STYLE="COLOR:GREEN;">Solution</H3>**

#### **<H4 STYLE="COLOR:MAGENTA;">Entrée</H4>**

Tableau de valeurs.

#### **<H4 STYLE="COLOR:MAGENTA;">Sortie</H4>**

Valeur de la moyenne des notes.

#### **<H4 STYLE="COLOR:MAGENTA;">Pré-condition</H4>**

Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.

#### **<H4 STYLE="COLOR:MAGENTA;">Post-condition</H4>**

La moyenne (décimale) des notes du tableau est retournée.

### **<H3 STYLE="COLOR:GREEN;">Algorithme en pseudo-code</H3>**

**Programme en python**

```python
def moyenneNote(Liste):
    somme = sum(Liste)
    moyenne = somme / len(Liste)
    return moyenne

print(moyenneNote([14, 18, 12, 10, 5, 10, 9, 16]))
```

Complexité de l’algorithme : O(n) car il faut parcourir le tableau de dimension n.

### **<H3 STYLE="COLOR:GREEN;">Résultats du test :</H3>**

Test effectué avec la liste : Liste = [14, 18, 12, 10, 5, 10, 9, 16]

| Étape                        | Variable indice | Liste[indice] | Variable somme | Variable moyenne |
|------------------------------|-----------------|---------------|----------------|------------------|
| Avant de rentrer dans la boucle |                 |               | 0              | X                |
| Dans la boucle (1ère itération)  | 0               | 14            | 14             | X                |
| Dans la boucle (2ème itération)  |                 |               |                | X                |
| Dans la boucle (3ème itération)  |                 |               |                | X                |
| Dans la boucle (4ème itération)  |                 |               |                | X                |
| Dans la boucle (5ème itération)  |                 |               |                | X                |
| Dans la boucle (6ème itération)  |                 |               |                | X                |
| Dans la boucle (7ème itération)  |                 |               |                | X                |
| Dans la boucle (8ème itération)  |                 |               |                | X                |
| En sortie de boucle              |                 |               |                |                  |

Conclusion : L’algorithme se termine en un temps fini et produit la sortie désirée (calcul de la valeur moyenne).






