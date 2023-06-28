---
author: Votre nom
title: Le morse
tags:
  - 3-dictionnaires
  - Difficulté **
---

## Le code morse : 

![morse](images/code_Morse.png){ width=40%; : .center }

Crédits : F1jmm, [CC BY-SA 4.0](https:https://creativecommons.org/licenses/by-sa/4.0){:target="_blank" } , Wikimedia Commons


!!! info "Utilisation d'un dictionnaire"

    On représente le code morse à l'aide d'un dictionnaire, on ne s'intéresse qu'aux lettres en majuscules non accentuées.  
    Pour l'espace on utilise le slash (par exemple).
    Vous pourrez recopier dans votre code ce dictionnaire.

    ```python
    morse = {' ': '/', 'E': '°', 'I': '°°', 'S': '°°°', 'H': '°°°°', 'V': '°°°-', 'U': '°°-', 'F': '°°-°',
    'A': '°-', 'R': '°-°', 'L': '°-°°', 'W': '°--', 'P': '°--°', 'J': '°---', 'T': '-', 'N': '-°', 'D': '-°°',
    'B': '-°°°', 'X': '-°°-', 'K': '-°-', 'C': '-°-°', 'Y': '-°--', 'M': '--', 'G': '--°', 'Z': '--°°', 
    'Q': '--°-', 'O': '---'}
    ```

## Travail à faire : 

Ecrire un script qui permet de déchiffrer un message envoyé en morse.

!!! warning "Contraintes"

    * Le script sera bien structuré, avec plusieurs fonctions
    * Vous utiliserez le dictionnaire donné

!!! example "Exemple d'exécution"

    Vous pouvez avoir des noms de fonctions différents. Ceci n'est qu'un exemple.

    ```pycon
    >>> message = 
    '-°°°*°-°*°-*°°°-*---*/°---*°*°°-*-°*°*/°--°*°-*-°°*°-*°--*°-*-°*/°-°°*°-*/-°*°°°*°°*/°*°°°*-*/°-*°°°-*°*-°-°*/-*---*°°*'
    >>> decode_mots(message, morse)
    'BRAVO JEUNE  PADAWAN LA NSI EST AVEC TOI'
    ```
