---
author: ELP
title: 01g Fiche méthode - Les dictionnaires
---




## <span style="color:blue;">1. Définition</span>

Un dictionnaire est une structure de données en Python qui associe des clés (**keys**) à des valeurs (**values**).  
Il est défini par des accolades `{}`.

- Chaque **clé est unique**.
- Les **valeurs peuvent être de n’importe quel type** (int, str, list, autre dictionnaire…).


## <span style="color:blue;">2. Création d’un Dictionnaire</span>

???+ question "Activité n°1 : Créer un dictionnaire"

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



## <span style="color:blue;">3. Accéder aux Éléments</span>

???+ question "Activité n°2 : Accès aux données"

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



## <span style="color:blue;">4. Modifier un Élément</span>

???+ question "Activité n°3 : Modifier une valeur"

    Modifie l'âge de l'étudiant en le passant à 18.

    ??? success "Python"
        ```python
        etudiant["age"] = 18
        print(etudiant)
        ```



## <span style="color:blue;">5. Ajouter un Élément</span>

???+ question "Activité n°4 : Ajouter une adresse"

    Ajoute une nouvelle clé `"adresse"` avec la valeur `"Paris"`.

    ??? success "Python"
        ```python
        etudiant["adresse"] = "Paris"
        print(etudiant)
        ```



## <span style="color:blue;">6. Supprimer un Élément</span>

???+ question "Activité n°5 : Suppression"

    Supprime la clé `"classe"` avec `del` et la clé `"age"` avec `.pop()`.

    ??? success "Python"
        ```python
        del etudiant["classe"]
        age = etudiant.pop("age")
        print(etudiant)
        print("Âge supprimé :", age)
        ```



## <span style="color:blue;">7. Parcourir un Dictionnaire</span>

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



## <span style="color:blue;">8. Méthodes Utiles</span>

| Méthode               | Description                                 | Exemple                                   |
|-----------------------|---------------------------------------------|-------------------------------------------|
| `len(dico)`           | Nombre d’éléments dans le dictionnaire      | `len(etudiant)`                          |
| `dico.keys()`         | Retourne une vue des clés                   | `etudiant.keys()`                        |
| `dico.values()`       | Retourne une vue des valeurs                | `etudiant.values()`                      |
| `dico.items()`        | Retourne une vue des couples clé-valeur     | `etudiant.items()`                       |
| `dico.clear()`        | Vide le dictionnaire                       | `etudiant.clear()`                       |
| `dico.update(autre)`  | Ajoute ou met à jour des paires clé-valeur  | `etudiant.update({"age": 19, "ville": "Paris"})` |



## <span style="color:blue;">9. Imbrication des Dictionnaires</span>

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

