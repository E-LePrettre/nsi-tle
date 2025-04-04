---
author: ELP
title: 01e Fiche méthode - Recherche d'une valeur dans un tableau
---




## **<H2 STYLE="COLOR:BLUE;">Rechercher une valeur dans un tableau (version 1)</H2>**

???+ question "Activité n° 1 : Énoncé"

    Rechercher une valeur dans un tableau de dimension `n`. Retourner vrai si la note est présente, faux dans le cas contraire. Par exemple à partir d’une liste de `n` notes de la classe, rechercher la présence de la note 12/20.

    - Liste de notes n°1 : 5 14 18 11 10 12 10 9 16 : oui la note est présente

    - Liste de notes n°2 : 5 14 18 11 10 11 10 9 16 : non la note n’est pas présente

    Pré-condition : Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.
    
    Post-condition : Un booléen vrai est retourné si la note est présente dans le tableau.



    ```python
    def rechercheNote(Liste, note):
    for i in range(len(Liste)):
        if Liste[i] == note:
            return True
    return False
    
    print(rechercheNote([5, 14, 18, 11, 10, 12, 10, 9, 16], 12))
    print(rechercheNote([5, 14, 18, 11, 10, 11, 10, 9, 16], 12))
    ```
    Observez le résultat dans la console.

    ??? success "Python"
        {{ IDE() }}        




**Complexité de l’algorithme** : O(n) car il faut parcourir le tableau de dimension n.


## **<H2 STYLE="COLOR:BLUE;">Rechercher une valeur dans un tableau (version 2)</H2>**

???+ question "Activité n° 2 : Énoncé"

    Rechercher une valeur dans un tableau de dimension `n`. Retourner vrai si la note est présente, faux dans le cas contraire. Par exemple à partir d’une liste de `n` notes de la classe, rechercher la présence de la note 12/20.

    - Liste de notes n°1 : 5 14 18 11 10 12 10 9 16 : oui la note est présente

    - Liste de notes n°2 : 5 14 18 11 10 11 10 9 16 : non la note n’est pas présente

    Pré-condition : Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.
    
    Post-condition : Un booléen vrai est retourné si la note est présente dans le tableau.



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
    print(rechercheNote([5, 14, 18, 11, 10, 11, 10, 9, 16], 12))
    ```
    Observez le résultat dans la console.

    ??? success "Python"
        {{ IDE() }}        



**Complexité de l’algorithme** : O(n) car il faut parcourir le tableau de dimension n.



Intérêt de la boucle « while » par rapport à la boucle « for » : Le parcours du tableau pour trouver la valeur peut se terminer plus rapidement en fonction de la position de la valeur dans le tableau.



## **<H2 STYLE="COLOR:BLUE;">Rechercher une valeur maximale dans un tableau</H2>**

???+ question "Activité n° 3 : Énoncé"

    Rechercher la valeur maximale dans un tableau de dimension `n` puis retourner cette valeur. Par exemple à partir d’une liste de `n` notes de la classe, rechercher la note maximale.

    - Liste de notes : 5 14 18 11 10 12 10 9 16 : note max : 18


    Pré-condition : Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.
    
    Post-condition : Une valeur (entière ou décimale) maximale du tableau est retournée.



    ```python
    def maxNote(Liste):
    maxi = Liste[0]
    for i in range(1, len(Liste)):
        if Liste[i] > maxi:
            maxi = Liste[i]
    return maxi
    
    
    print(maxNote([5, 14, 18, 12, 10, 10, 9, 16]))
    ```
    Observez le résultat dans la console.

    ??? success "Python"
        {{ IDE() }} 


**Complexité de l’algorithme** : O(n) car il faut parcourir le tableau de dimension n.



## **<H2 STYLE="COLOR:BLUE;">Rechercher une valeur minimale dans un tableau</H2>**

???+ question "Activité n° 4 : Énoncé"

    Rechercher la valeur minimale dans un tableau de dimension `n` puis retourner cette valeur. Par exemple à partir d’une liste de `n` notes de la classe, rechercher la note minimale.

    - Liste de notes : 5 14 18 11 10 12 10 9 16 : note max : 5


    Pré-condition : Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.
    
    Post-condition : Une valeur (entière ou décimale) minimale du tableau est retournée.



    ```python
    def minNote(Liste):
    mini = Liste[0]
    for i in range(1, len(Liste)):
        if Liste[i] < mini:
            mini = Liste[i]
    return mini
    
    print(minNote([14, 18, 12, 10, 5, 10, 9, 16]))
    ```
    Observez le résultat dans la console.

    ??? success "Python"
        {{ IDE() }} 


**Complexité de l’algorithme** : O(n) car il faut parcourir le tableau de dimension n.



## **<H2 STYLE="COLOR:BLUE;">Calculer la valeur moyenne d’un tableau</H2>**

???+ question "Activité n°5 : Énoncé"

    Par exemple à partir d’une liste de `n` notes de la classe, calculer la moyenne des notes.

    - Liste de notes : 14 18 11 10 5 10 9 16 : moyenne : 


    Pré-condition : Le tableau de valeurs est compris entre 0 et 20 inclus. Le tableau possède au moins 2 valeurs.
    
    Post-condition : La moyenne (décimale) des notes du tableau est retournée.



    ```python
    def moyenneNote(Liste):
    somme = 0
    for elmt in Liste:
        somme += elmt
    return somme / len(Liste)
    
    print(moyenneNote([14, 18, 12, 10, 5, 10, 9, 16]))
    ```
    Observez le résultat dans la console.

    ??? success "Python"
        {{ IDE() }} 

**Complexité de l’algorithme** : O(n) car il faut parcourir le tableau de dimension n.




