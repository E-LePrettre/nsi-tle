---
author: ELP
title: 01g Fiche méthode - Les dictionnaires
---


## **<H2 STYLE="COLOR:BLUE;">1. Définition</H2>**
Un dictionnaire est une structure de données en Python qui associe des clés (**keys**) à des valeurs (**values**).  
Il est défini par des accolades `{}`.  
- Chaque clé est unique.
- Les valeurs peuvent être de n’importe quel type (int, str, list, autre dictionnaire…).

## **<H2 STYLE="COLOR:BLUE;">2. Création d’un Dictionnaire</H2>**
**Syntaxe** :  
```python
# Dictionnaire vide
mon_dictionnaire = {}

# Dictionnaire avec des données
etudiant = {"nom": "Dupont", "age": 17, "classe": "Terminale"}
```

---

## **<H2 STYLE="COLOR:BLUE;">3. Accéder aux Éléments</H2>**
On utilise la clé entre crochets `[]` ou la méthode `.get()`.

**Exemple :**  
```python
etudiant = {"nom": "Dupont", "age": 17, "classe": "Terminale"}

# Par les crochets
print(etudiant["nom"])  # Affiche "Dupont"

# Par la méthode .get()
print(etudiant.get("age"))  # Affiche 17

# Si la clé n'existe pas avec .get()
print(etudiant.get("adresse", "Clé non trouvée"))  # Affiche "Clé non trouvée"
```

---

## **<H2 STYLE="COLOR:BLUE;">4. Modifier un Élément</H2>**
Il suffit d'assigner une nouvelle valeur à une clé existante.

**Exemple :**  
```python
etudiant["age"] = 18  # Change l'âge à 18
print(etudiant)
```

---

## **<H2 STYLE="COLOR:BLUE;">5. Ajouter un Élément</H2>**
Pour ajouter un couple clé-valeur, on utilise une clé nouvelle.

**Exemple :**  
```python
etudiant["adresse"] = "Paris"
print(etudiant)
```

---

## **<H2 STYLE="COLOR:BLUE;">6. Supprimer un Élément</H2>**
**Méthodes principales :**
- `del` pour supprimer une clé.
- `.pop()` pour récupérer et supprimer une valeur.

**Exemple :**  
```python
# Supprimer avec del
del etudiant["classe"]
print(etudiant)

# Supprimer avec .pop()
age = etudiant.pop("age")
print(etudiant)  # La clé "age" est supprimée
print(age)  # Affiche 18
```

---

## **<H2 STYLE="COLOR:BLUE;">7. Parcourir un Dictionnaire</H2>**
**Boucle `for`** pour parcourir clés, valeurs ou les deux.

**Exemples :**  
```python
# Parcourir les clés
for cle in etudiant:
    print(cle)

# Parcourir les valeurs
for valeur in etudiant.values():
    print(valeur)

# Parcourir les deux
for cle, valeur in etudiant.items():
    print(f"{cle}: {valeur}")
```

---

## **<H2 STYLE="COLOR:BLUE;">8. Méthodes Utiles</H2>**
| Méthode               | Description                                 | Exemple                                   |
|-----------------------|---------------------------------------------|-------------------------------------------|
| `len(dico)`           | Nombre d’éléments dans le dictionnaire      | `len(etudiant)`                          |
| `dico.keys()`         | Retourne une vue des clés                   | `etudiant.keys()`                        |
| `dico.values()`       | Retourne une vue des valeurs                | `etudiant.values()`                      |
| `dico.items()`        | Retourne une vue des couples clé-valeur     | `etudiant.items()`                       |
| `dico.clear()`        | Vide le dictionnaire                       | `etudiant.clear()`                       |
| `dico.update(autre)`  | Ajoute ou met à jour des paires clé-valeur  | `etudiant.update({"age": 19, "ville": "Paris"})` |

---

## **<H2 STYLE="COLOR:BLUE;">9. Imbrication des Dictionnaires</H2>**
Les dictionnaires peuvent contenir d'autres dictionnaires.

**Exemple :**  
```python
classe = {
    "eleve1": {"nom": "Dupont", "age": 17},
    "eleve2": {"nom": "Martin", "age": 18}
}

print(classe["eleve1"]["nom"])  # Affiche "Dupont"
```

