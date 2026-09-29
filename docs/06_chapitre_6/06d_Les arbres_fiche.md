---
author: Elisabeth Le Prettre (LePrettre)
title: 06a 📜 Fiche Méthode - Les arbres
---

# Les arbres binaires

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur les arbres binaires : vocabulaire,
    mesures, formules, représentations, TAD, parcours (profondeur / largeur) et
    arbres d'expression (RPN).

!!! warning "Conventions"
    Plusieurs conventions coexistent (profondeur de la racine = 0 ou = 1). **Lis
    toujours celle donnée dans l'énoncé** et précise celle que tu utilises.

---

## 1. Vocabulaire

| Terme | Définition |
|---|---|
| **Arbre** | Structure hiérarchique de nœuds reliés sans cycle. |
| **Racine** | Nœud du sommet, sans père. |
| **Nœud** | Élément de l'arbre. |
| **Étiquette** | Valeur portée par un nœud. |
| **Père** | Nœud situé juste au-dessus d'un autre. |
| **Fils** | Nœud situé juste en dessous d'un autre. |
| **Feuille** | Nœud **sans fils**. |
| **Nœud interne** | Nœud ayant **au moins un fils**. |
| **Arête** | Lien entre un père et un fils. |
| **Ancêtre** | Nœud situé sur le chemin vers la racine. |
| **Descendant** | Nœud situé sous un nœud donné. |
| **Sous-arbre gauche / droit** | Arbre formé par le fils gauche / droit et sa descendance. |
| **Arbre vide** | Arbre sans aucun nœud. |

---

## 2. Mesures

| Mesure | Définition |
|---|---|
| **Taille** | Nombre de **nœuds**. |
| **Profondeur d'un nœud** | Distance à la racine. |
| **Hauteur** | Profondeur **maximale** (la plus grande profondeur d'une feuille). |
| **Nombre d'arêtes** | `taille − 1` (pour un arbre non vide). |
| **Nombre de feuilles** | Nombre de nœuds sans fils. |

!!! note "Les deux conventions de profondeur de la racine"
    - **Convention A** : la racine est à la profondeur **0** (on compte les **arêtes**).
    - **Convention B** : la racine est à la profondeur **1** (on compte les **niveaux**).

    Les formules changent selon la convention : **toujours vérifier celle de l'énoncé**.

---

## 3. Arbres binaires

**Définition récursive :** un arbre binaire est soit **vide**, soit constitué
d'une **racine** et de deux sous-arbres binaires (**gauche** et **droite**).

- chaque nœud a **0, 1 ou 2 fils** ;
- **fils ≠ sous-arbre** : le fils est un nœud, le sous-arbre est tout l'arbre qui
  en découle (et peut être **vide**).

| Type d'arbre | Description |
|---|---|
| **Complet (parfait)** | Tous les niveaux sont **entièrement remplis**. |
| **Filiforme** | Chaque nœud a **au plus un fils** (forme de « chaîne »). |
| **Déséquilibré** | Les sous-arbres ont des hauteurs très différentes. |

---

## 4. Formules (arbre complet)

!!! note "Taille d'un arbre complet de hauteur `h`"
    - **Convention A** (racine à hauteur 0) : `n = 2^(h+1) − 1` ;
      inverse : `h = log₂(n + 1) − 1`.
    - **Convention B** (racine à hauteur 1) : `n = 2^h − 1` ;
      inverse : `h = log₂(n + 1)`.

!!! note "Encadrement de la hauteur d'un arbre de taille `n`"
    En **convention A** (racine à hauteur 0) :
    ```
    ⌊log₂(n)⌋  ≤  hauteur  ≤  n − 1
    ```
    - **minimum** atteint par un arbre **complet / équilibré** (`⌊log₂(n)⌋`) ;
    - **maximum** atteint par un arbre **filiforme** (`n − 1`).

---

## 5. Représentation par tableau (méthode d'Eytzinger)

On range les nœuds **niveau par niveau**, de gauche à droite.

| Indexation | Fils gauche de `i` | Fils droit de `i` | Père de `i` |
|---|---|---|---|
| **à partir de 0** | `2i + 1` | `2i + 2` | `(i − 1) // 2` |
| **à partir de 1** | `2i` | `2i + 1` | `i // 2` |

!!! tip "Dessiner un arbre à partir d'un tableau"
    1. Placer la **racine** : indice `0` (indexation 0) ou `1` (indexation 1).
    2. Pour chaque nœud d'indice `i`, calculer ses fils avec la formule ci-dessus.
    3. Descendre **niveau par niveau** jusqu'à épuiser le tableau.

---

## 6. TAD arbre binaire

| Primitive | Rôle |
|---|---|
| `creer_noeud(v, g, d)` | Créer un nœud de valeur `v`, de sous-arbres `g` et `d`. |
| `arbre_vide()` | Renvoyer un arbre vide. |
| `construire(v, g, d)` | Construire un arbre à partir d'une valeur et de deux sous-arbres. |
| `est_vide(a)` | Tester si l'arbre est vide. |
| `racine(a)` | Renvoyer la valeur de la racine. |
| `gauche(a)` | Renvoyer le **sous-arbre gauche**. |
| `droite(a)` | Renvoyer le **sous-arbre droit**. |

!!! tip "Interface vs implémentation"
    Le **client** manipule l'arbre **uniquement** via ces primitives (l'interface),
    sans connaître la **représentation** interne (tuples, classes, dictionnaire…).

---

## 7. Implémentations

| Implémentation | Valeur | Sous-arbre gauche | Sous-arbre droit |
|---|---|---|---|
| **Tableau / liste** (Eytzinger) | `T[i]` | indice `2i+1` | indice `2i+2` |
| **Tuples** | `a[0]` | `a[1]` | `a[2]` |
| **Classe unique `Noeud`** | `a.valeur` | `a.gauche` | `a.droite` |
| **Classes `Noeud` + `Arbre`** | `arbre.racine.valeur` | `arbre.racine.gauche` | `arbre.racine.droite` |
| **Dictionnaire** | `d['valeur']` | `d['gauche']` | `d['droite']` |

```python
class Noeud:
    def __init__(self, valeur, gauche=None, droite=None):
        self.valeur = valeur
        self.gauche = gauche
        self.droite = droite
```

---

## 8. Taille et hauteur récursives

```
taille(a):
    si est_vide(a):
        renvoyer 0                       # cas de base
    sinon:
        renvoyer 1 + taille(gauche(a)) + taille(droite(a))

hauteur(a):                              # convention : arbre vide → -1
    si est_vide(a):
        renvoyer -1                      # cas de base
    sinon:
        renvoyer 1 + max(hauteur(gauche(a)), hauteur(droite(a)))
```

- **cas de base** : arbre vide (taille `0`, hauteur `−1`, donc une feuille a hauteur `0`) ;
- **cas récursif** : on combine les résultats des deux sous-arbres ;
- **dérouler les appels** : descendre jusqu'aux sous-arbres vides, puis **remonter**
  en additionnant (taille) ou en prenant le `max` (hauteur).

!!! note "Fonction vs méthode"
    - **Fonction** : `taille(a)` (l'arbre est passé en **paramètre**) ;
    - **Méthode** : `a.taille()` (appelée **sur** l'objet, qui utilise `self`).

---

## 9. Parcours en profondeur

| Parcours | Ordre | Sur un arbre d'expression |
|---|---|---|
| **Préfixe** | **N → G → D** (racine d'abord) | notation **préfixée** |
| **Infixe** | **G → N → D** (racine au milieu) | notation **infixée** usuelle |
| **Suffixe** | **G → D → N** (racine en dernier) | notation **postfixée (RPN)** |

!!! example "Exemple"
    ```
            1
           / \
          2   3
         / \   \
        4   5   6
    ```
    - **Préfixe** : `1 2 4 5 3 6`
    - **Infixe**  : `4 2 5 1 3 6`
    - **Suffixe** : `4 5 2 6 3 1`

Modèles récursifs condensés :

```
prefixe(a):  si non vide:  afficher(racine(a)); prefixe(gauche(a)); prefixe(droite(a))
infixe(a):   si non vide:  infixe(gauche(a));  afficher(racine(a)); infixe(droite(a))
suffixe(a):  si non vide:  suffixe(gauche(a)); suffixe(droite(a)); afficher(racine(a))
```

*Variante :* au lieu d'**afficher**, on peut **renvoyer une liste** en
concaténant `gauche + [racine] + droite` (ici pour l'infixe).

---

## 10. Parcours en largeur

On visite les nœuds **niveau par niveau**, à l'aide d'une **file** (`deque`).

```python
from collections import deque

def largeur(a):
    if est_vide(a):
        return
    f = deque()
    f.append(a)                       # enfiler la racine
    while f:
        n = f.popleft()               # défiler (tête)
        print(racine(n))
        if not est_vide(gauche(n)):
            f.append(gauche(n))       # enfiler le fils gauche
        if not est_vide(droite(n)):
            f.append(droite(n))       # enfiler le fils droit
```

*Sur l'arbre de l'exemple :* `1 2 3 4 5 6`.

!!! tip "Profondeur vs largeur"
    - **Profondeur** : on descend au plus loin → **pile** (ou récursivité).
    - **Largeur** : on explore niveau par niveau → **file** (`deque`).

---

## 11. Arbre d'expression et RPN

- les **nœuds internes** sont des **opérateurs** ;
- les **feuilles** sont des **nombres** ;
- le **parcours suffixe** donne la **notation polonaise inverse (RPN)**.

!!! example "Exemple"
    ```
            +
           / \
          *   2
         / \
        3   4
    ```
    Suffixe (RPN) : `3 4 * 2 +`

**Évaluation par pile :**

1. parcourir l'expression RPN de gauche à droite ;
2. **empiler** chaque nombre ;
3. à chaque **opérateur**, **dépiler deux** opérandes, calculer, **empiler** le résultat.

!!! warning "Ordre des opérandes"
    Le **premier dépilé** est l'opérande de **droite**, le **second** est celui de
    **gauche** : `b = dépiler()`, `a = dépiler()`, résultat `a opérateur b`.
    Crucial pour `−` et `/` (non commutatifs).

    *Exemple `3 4 * 2 +` :* empiler 3, empiler 4 ; `*` → `3*4 = 12` ; empiler 2 ;
    `+` → `12 + 2 = 14`.

---

## 12. Méthodes bac

!!! tip "Procédures à appliquer"
    - **lire / dessiner** un arbre (depuis un schéma ou un tableau d'Eytzinger) ;
    - **calculer** taille, hauteur, nombre de feuilles, d'arêtes ;
    - **appliquer la convention** donnée (racine à 0 ou à 1) ;
    - **retrouver un parcours** (préfixe, infixe, suffixe, largeur) ;
    - **compléter** un pseudo-code de taille / hauteur / parcours ;
    - **suivre l'état d'une file** lors d'un parcours en largeur ;
    - **interpréter un arbre d'expression** et l'évaluer (RPN + pile).

---

## 13. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **taille**, **hauteur** et **profondeur** ;
    - oublier la **convention** (racine à 0 ou à 1) → formules fausses ;
    - confondre **fils** et **sous-arbre** ;
    - oublier le cas de l'**arbre vide** (cas de base) ;
    - se tromper dans les **indices d'Eytzinger** (`2i+1` / `2i+2` vs `2i` / `2i+1`) ;
    - confondre l'**ordre des parcours** (N-G-D, G-N-D, G-D-N) ;
    - confondre **file** (largeur) et **pile** (profondeur) ;
    - inverser l'**ordre de dépilement** des opérandes en RPN.

---

## 14. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Différence entre une feuille et un nœud interne ?"
    Une **feuille** n'a **aucun fils** ; un **nœud interne** a **au moins un fils**.

??? question "2. Quelle est la taille et le nombre d'arêtes d'un arbre de 7 nœuds ?"
    Taille = `7` ; nombre d'arêtes = `7 − 1 = 6`.

??? question "3. Combien de nœuds dans un arbre complet de hauteur 3 (racine à hauteur 0) ?"
    `n = 2^(3+1) − 1 = 15`.

??? question "4. Encadrer la hauteur d'un arbre de 8 nœuds (racine à hauteur 0)."
    `⌊log₂(8)⌋ ≤ h ≤ 8 − 1`, soit `3 ≤ h ≤ 7`.

??? question "5. Tableau d'Eytzinger (indexation 0) : quels sont les fils de l'indice 2 ?"
    Fils gauche : `2×2 + 1 = 5` ; fils droit : `2×2 + 2 = 6`.

??? question "6. Donner le parcours préfixe de l'arbre exemple (§9)."
    `1 2 4 5 3 6`.

??? question "7. Donner le parcours infixe du même arbre."
    `4 2 5 1 3 6`.

??? question "8. Donner le parcours suffixe du même arbre."
    `4 5 2 6 3 1`.

??? question "9. Compléter le cas de base de `hauteur(a)` (arbre vide)."
    `si est_vide(a): renvoyer -1` (ainsi une feuille a une hauteur de `0`).

??? question "10. Quel parcours visite l'arbre niveau par niveau et avec quelle structure ?"
    Le **parcours en largeur**, à l'aide d'une **file** (`deque`).

??? question "11. Écrire la RPN de l'arbre d'expression du §11 et donner sa valeur."
    RPN : `3 4 * 2 +` ; valeur : `14`.

??? question "12. En RPN, pour l'opérateur `−`, quel opérande est dépilé en premier ?"
    L'opérande de **droite** : `b = dépiler()`, `a = dépiler()`, résultat `a − b`.

---

## À retenir absolument

!!! success "Les quatre parcours"
    | Parcours | Ordre | Structure utilisée |
    |---|---|---|
    | **Préfixe** | N → G → D | pile / récursivité |
    | **Infixe** | G → N → D | pile / récursivité |
    | **Suffixe** | G → D → N | pile / récursivité (→ RPN) |
    | **Largeur** | niveau par niveau | **file** (`deque`) |

!!! abstract "Formules essentielles (arbre complet)"
    - **Convention A** (racine à 0) : `n = 2^(h+1) − 1` ↔ `h = log₂(n+1) − 1` ;
    - **Convention B** (racine à 1) : `n = 2^h − 1` ↔ `h = log₂(n+1)` ;
    - **arêtes** = `taille − 1` ;
    - **encadrement** (racine à 0) : `⌊log₂(n)⌋ ≤ h ≤ n − 1`.

!!! note "Algorithmes de taille et hauteur"
    ```
    taille(a)  = 0   si vide ; sinon 1 + taille(G) + taille(D)
    hauteur(a) = -1  si vide ; sinon 1 + max(hauteur(G), hauteur(D))
    ```

!!! quote "Formulations utiles au bac"
    - « Un arbre binaire est **vide**, ou possède une **racine** et deux
      **sous-arbres** gauche et droit. »
    - « La hauteur est `1 + max` des hauteurs des sous-arbres ; l'arbre vide a une
      hauteur de `−1`. »
    - « Le parcours **suffixe** d'un arbre d'expression donne sa forme **RPN**. »
    - « Le parcours en **largeur** utilise une **file** ; le parcours en
      **profondeur** une **pile**. »