---
author: ELP
title: 01e Fiche méthode - Recherche dans un tableau
---

## <H2 style="color:blue;">🔍 Rechercher une valeur (version 1)</H2>

???+ question "Activité n° 1 : Énoncé"

    Rechercher une **note donnée** dans un tableau `Liste` de dimension `n`.  
    Retourner `True` si elle est présente, sinon `False`.

    📌 Exemple :

    - Liste 1 : `5 14 18 11 10 12 10 9 16` → ✅ 12 est présente
    - Liste 2 : `5 14 18 11 10 11 10 9 16` → ❌ 12 n'est pas présente

    🔒 **Pré-condition** : les valeurs sont comprises entre 0 et 20 inclus, et la liste contient au moins 2 éléments.  
    ✅ **Post-condition** : un booléen (`True` ou `False`) est retourné.

    ```python
    def rechercheNote(Liste, note):
        for i in range(len(Liste)):
            if Liste[i] == note:
                return True
        return False

    print(rechercheNote([5, 14, 18, 11, 10, 12, 10, 9, 16], 12))  # True
    print(rechercheNote([5, 14, 18, 11, 10, 11, 10, 9, 16], 12))  # False
    ```
    
    ??? success "Python"
        {{ IDE() }} 

📊 **Complexité** : 𝑶(n) → on parcourt toute la liste dans le pire des cas.

---

## <H2 style="color:blue;">🔁 Rechercher une valeur (version 2)</H2>

???+ question "Activité n° 2 : Énoncé"

    Même objectif que l’activité précédente, mais cette fois avec une **boucle `while`** :

    ```python
    def rechercheNote(Liste, note):
        trouve = False
        i = 0
        while not trouve and i < len(Liste):
            if Liste[i] == note:
                trouve = True
            i += 1
        return trouve

    print(rechercheNote([5, 14, 18, 11, 10, 12, 10, 9, 16], 12))  # True
    print(rechercheNote([5, 14, 18, 11, 10, 11, 10, 9, 16], 12))  # False
    ```

    ??? success "Python"
        {{ IDE() }} 

📌 **Avantage de `while` :**
➡️ le programme peut **s'arrêter plus tôt** si la valeur est trouvée dès le début.

📊 **Complexité** : 𝑶(n) dans le pire des cas.

---

## <H2 style="color:blue;">📈 Rechercher la valeur maximale</H2>

???+ question "Activité n° 3 : Énoncé"

    Objectif : retourner la **plus grande valeur** dans une liste.

    📌 Exemple :
    Liste : `5 14 18 11 10 12 10 9 16` → Max = 18

    ```python
    def maxNote(Liste):
        maxi = Liste[0]
        for i in range(1, len(Liste)):
            if Liste[i] > maxi:
                maxi = Liste[i]
        return maxi

    print(maxNote([5, 14, 18, 12, 10, 10, 9, 16]))  # 18
    ```

    ??? success "Python"
        {{ IDE() }} 

📊 **Complexité** : 𝑶(n)
➡️ Il faut parcourir toute la liste.

---

## <H2 style="color:blue;">📉 Rechercher la valeur minimale</H2>

???+ question "Activité n° 4 : Énoncé"

    📌 Exemple :
    Liste : `5 14 18 11 10 12 10 9 16` → Min = 5

    ```python
    def minNote(Liste):
        mini = Liste[0]
        for i in range(1, len(Liste)):
            if Liste[i] < mini:
                mini = Liste[i]
        return mini

    print(minNote([14, 18, 12, 10, 5, 10, 9, 16]))  # 5
    ```

    ??? success "Python"
        {{ IDE() }} 

📊 **Complexité** : 𝑶(n)

---

## <H2 style="color:blue;">📊 Calculer la moyenne d’un tableau</H2>

???+ question "Activité n°5 : Énoncé"

    📌 Exemple :
    Liste : `14 18 12 10 5 10 9 16` → Moyenne ≈ 11.75

    ```python
    def moyenneNote(Liste):
        somme = 0
        for elmt in Liste:
            somme += elmt
        return somme / len(Liste)

    print(moyenneNote([14, 18, 12, 10, 5, 10, 9, 16]))  # 11.75
    ```

    ??? success "Python"
        {{ IDE() }} 

📊 **Complexité** : 𝑶(n)

---

💡 **À retenir :**

| Tâche                             | Algo utilisé | Complexité |
| --------------------------------- | ------------ | ---------- |
| Rechercher une valeur (for/while) | linéaire     | 𝑶(n)      |
| Trouver le max                    | linéaire     | 𝑶(n)      |
| Trouver le min                    | linéaire     | 𝑶(n)      |
| Calculer la moyenne               | linéaire     | 𝑶(n)      |


Pour s'entrainer par ordre de dificulté croissante : 

- [CODEX : Recadrer les mesures d'un tableau](https://codex.forge.apps.education.fr/exercices/recadrer/)

- [CODEX : indice du minimum](https://codex.forge.apps.education.fr/exercices/ind_min/)

- [CODEX : Maximum](https://codex.forge.apps.education.fr/exercices/maximum_nombres/)

- [CODEX : Valeur et indice du maximum](https://codex.forge.apps.education.fr/exercices/val_ind_max/)

- [CODEC : Indice de la première occurrence](https://codex.forge.apps.education.fr/exercices/ind_prem_occ/)

- [CODEC : Dernière occurrence](https://codex.forge.apps.education.fr/exercices/derniere_occurrence/)

- [CODEC : Nombre de répétitions](https://codex.forge.apps.education.fr/exercices/repetitions/)

- [CODEX : Le plus proche](https://codex.forge.apps.education.fr/exercices/plus_proche/)




