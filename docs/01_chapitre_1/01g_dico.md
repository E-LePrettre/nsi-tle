---
author: ELP
title: 01g Fiche méthode - Les dictionnaires
---

## <H2 style="color:blue;">📘 1. Définition</H2>

Un **dictionnaire** en Python est une structure de données qui associe des **clés** (`keys`) à des **valeurs** (`values`).  
Il est défini entre accolades `{}`.

✅ Caractéristiques :

- Chaque **clé est unique**
- Les **valeurs** peuvent être de n'importe quel type : `int`, `str`, `list`, etc.

---

## <H2 style="color:blue;">🛠️ 2. Création d’un dictionnaire</H2>

???+ question "🎯Activité n°1 : Créer un dictionnaire" 

    Crée un dictionnaire représentant un étudiant avec les informations suivantes :

    - nom : "Dupont"

    - âge : 17

    - classe : "Terminale"

    ??? success "Python"
        ```python
        etudiant = {"nom": "Dupont", "age": 17, "classe": "Terminale"}
        print(etudiant)
        ```

    ??? success "Explication"
        Le dictionnaire est créé avec trois paires **clé-valeur**.  
        Les clés sont des chaînes (`str`) : `"nom"`, `"age"`, `"classe"`.


🧠 Chaque paire clé-valeur est notée sous la forme `"clé": valeur`.

---

## <H2 style="color:blue;">🔍 3. Accéder aux éléments</H2>

???+ question "🎯 Activité n°2 : Accès aux données"

    À partir du dictionnaire `etudiant`, affiche :

    - le nom de l’étudiant

    - l’âge via la méthode `.get()`

    - une clé inexistante avec une valeur par défaut

    ??? success "Python"
        ```python
        print(etudiant["nom"])
        print(etudiant.get("age"))
        print(etudiant.get("adresse", "Clé non trouvée"))
        ```

    ??? success "Résultat"
        ```
        Dupont
        17
        Clé non trouvée
        ```

🧠 `.get()` permet d’éviter une erreur si la clé n’existe pas.

---

## <H2 style="color:blue;">✏️ 4. Modifier un élément</H2>

???+ question "🎯 Activité n°3 : Modifier une valeur"

    Modifie l'âge de l'étudiant en le passant à 18.

    ??? success "Python"
        ```python
        etudiant["age"] = 18
        print(etudiant)
        ```

➡️ On remplace simplement la valeur associée à la clé `"age"`.

---

## <H2 style="color:blue;">➕ 5. Ajouter un élément</H2>

???+ question "🎯 Activité n°4 : Ajouter une adresse"

    Ajoute une nouvelle clé `"adresse"` avec la valeur `"Paris"`.

    ??? success "Python"
        ```python
        etudiant["adresse"] = "Paris"
        print(etudiant)
        ```

➡️ Si la clé n'existe pas, elle est ajoutée automatiquement.

---

## <H2 style="color:blue;">🗑️ 6. Supprimer un élément</H2>

???+ question "Activité n°5 : Suppression"

    Supprime la clé `"classe"` avec `del` et la clé `"age"` avec `.pop()`.

    ??? success "Python"
        ```python
        del etudiant["classe"]
        age = etudiant.pop("age")
        print(etudiant)
        print("Âge supprimé :", age)
        ```

🧠 `del` supprime sans retour ; `.pop()` supprime et renvoie la valeur.

---

## <H2 style="color:blue;">🔁 7. Parcourir un dictionnaire</H2>

???+ question "Activité n°6 : Parcourir le dictionnaire"

    Affiche :

    - les clés

    - les valeurs
    
    - les couples clé-valeur

    ??? success "Python"
        ```python
        for cle in etudiant:
            print("Clé :", cle)

        for valeur in etudiant.values():
            print("Valeur :", valeur)

        for cle, valeur in etudiant.items():
            print(f"{cle}: {valeur}")
        ```


🧠 Utilise `.values()` ou `.items()` selon ce que tu veux parcourir.

---

## <H2 style="color:blue;">🧰 8. Méthodes utiles</H2>

| Méthode              | Description                       | Exemple                               |
| -------------------- | --------------------------------- | ------------------------------------- |
| `len(dico)`          | Nombre de paires clé-valeur       | `len(etudiant)`                       |
| `dico.keys()`        | Liste des clés                    | `etudiant.keys()`                     |
| `dico.values()`      | Liste des valeurs                 | `etudiant.values()`                   |
| `dico.items()`       | Liste des couples `(clé, valeur)` | `etudiant.items()`                    |
| `dico.clear()`       | Vide le dictionnaire              | `etudiant.clear()`                    |
| `dico.update({...})` | Met à jour ou ajoute des paires   | `etudiant.update({"ville": "Paris"})` |

---

## <H2 style="color:blue;">🧱 9. Dictionnaires imbriqués</H2>

???+ question "Activité n°7 : Dictionnaires imbriqués"

    Crée un dictionnaire représentant une classe contenant deux élèves avec nom et âge.

    ??? success "Python"
        ```python
        classe = {
            "eleve1": {"nom": "Dupont", "age": 17},
            "eleve2": {"nom": "Martin", "age": 18}
        }

        print(classe["eleve1"]["nom"])  # Affiche "Dupont"
        ```

🧠 Les dictionnaires peuvent contenir **d'autres dictionnaires**. On accède alors aux valeurs avec plusieurs crochets `[ ]`.

---







