---
author: Elisabeth Le Prettre (LePrettre)
title: 05a 📜 Fiche Méthode - Interface et implémentation
---

# Interface et implémentation des structures de données

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur les structures de données abstraites :
    distinction **interface / implémentation**, **pile** (LIFO) et **file** (FIFO),
    leurs primitives, et leurs réalisations par **tableau** et **tableau circulaire**.

---

## 1. Définitions

| Terme | Définition |
|---|---|
| **Module** | Regroupement de code (types, fonctions) réutilisable par d'autres programmes. |
| **Implémentation** | **Comment** une structure est réalisée concrètement (le code interne). |
| **Interface / API** | **Ce qu'on peut faire** avec la structure : liste des opérations utilisables. |
| **Client** | Programme (ou personne) qui **utilise** la structure via son interface. |
| **Spécification** | Description précise d'une opération : nom, paramètres, type retourné, effet. |
| **Structure de données abstraite** | Structure définie par son **comportement** (son interface), indépendamment de sa réalisation. |
| **Opérateur** | Opération de base (primitive) fournie par l'interface. |
| **Tableau** | Suite de cases **indexées** de taille **fixe**, accès direct par indice. |
| **Pile** | Structure **LIFO** : dernier entré, premier sorti. |
| **File** | Structure **FIFO** : premier entré, premier sorti. |
| **LIFO** | *Last In, First Out* — on retire en priorité le **dernier** ajouté. |
| **FIFO** | *First In, First Out* — on retire en priorité le **premier** ajouté. |
| **Fonction** | Sous-programme qui **renvoie** une valeur (`return`). |
| **Procédure** | Sous-programme qui **agit** (modifie un état) sans forcément renvoyer de valeur. |
| **Effet de bord** | Modification d'un état (ex. : la structure est modifiée) en plus, ou à la place, d'un résultat. |

---

## 2. Spécification

Une fonction est entièrement décrite par :

- son **nom** ;
- ses **paramètres** et leurs **types** ;
- le **type retourné** ;
- sa **documentation** (rôle, préconditions, effet, résultat).

!!! tip "Principe fondamental"
    Le **client** utilise une structure **uniquement via son interface**. Il n'a
    **pas besoin de consulter l'implémentation** : il lui suffit de connaître le
    nom des opérations, leurs paramètres et ce qu'elles font.

---

## 3. Interface de la pile

Une pile peut se décrire **récursivement** : une pile est soit **vide**, soit
constituée d'une **tête** (le sommet) et d'un **reste** (le dessous de la pile).

| Primitive | Rôle | Paramètres | Effet | Résultat |
|---|---|---|---|---|
| `vide()` | Créer une pile vide | aucun | — | une pile vide |
| `estVide(P)` | Tester si vide | pile `P` | aucun | booléen |
| `empiler(a, P)` | Ajouter au sommet | valeur `a`, pile `P` | `P` modifiée | — |
| `depiler(P)` | Retirer le sommet | pile `P` (non vide) | `P` modifiée | la valeur retirée |

!!! note "Méthodes du cours (n'utilisant que les primitives)"
    **Compter les éléments en restaurant la pile** (activité 4) — on vide `P` dans
    une pile temporaire, puis on la reconstitue :
    ```
    fonction compter_elements(P):
        temp = vide()
        compteur = 0
        tant que non estVide(P):
            elt = depiler(P)           # depiler renvoie ET modifie
            empiler(elt, temp)
            compteur = compteur + 1
        tant que non estVide(temp):    # restauration de P
            elt = depiler(temp)
            empiler(elt, P)
        retourner compteur
    ```
    *Deux passages dans l'auxiliaire remettent les éléments dans l'ordre initial.*

    **Supprimer le deuxième élément** (activité 5, juste sous le sommet) :
    ```
    fonction supprimer_deuxieme(P):
        si estVide(P):
            retourner
        elt1 = depiler(P)       # on met de côté le sommet
        si estVide(P):          # un seul élément : rien à supprimer
            empiler(elt1, P)
            retourner
        depiler(P)              # 2e élément : on ne le remet pas
        empiler(elt1, P)        # on remet le sommet
    ```

---

## 4. Interface de la file

Principe **FIFO** : on **enfile en queue** et on **défile en tête**. Une file est
soit **vide**, soit constituée de trois champs : une **tête**, une **queue** et un
**troisième champ** contenant une file.

| Primitive | Rôle | Paramètres | Effet | Résultat |
|---|---|---|---|---|
| `vide()` | Créer une file vide | aucun | — | une file vide |
| `estVide(F)` | Tester si vide | file `F` | aucun | booléen |
| `enfiler(a, F)` | Ajouter en queue | valeur `a`, file `F` | `F` modifiée | — |
| `defiler(F)` | Retirer en tête | file `F` (non vide) | `F` modifiée | la valeur retirée |

!!! note "Méthodes du cours (n'utilisant que les primitives)"
    **Compter les éléments en restaurant la file** (activité 6) :
    ```
    fonction compter_elements(F):
        temp = vide()
        compteur = 0
        tant que non estVide(F):
            elt = defiler(F)
            enfiler(elt, temp)
            compteur = compteur + 1
        tant que non estVide(temp):    # restauration de F
            elt = defiler(temp)
            enfiler(elt, F)
        retourner compteur
    ```
    *En FIFO, recopier dans l'auxiliaire puis revenir conserve l'ordre initial.*

    **Supprimer le premier élément du troisième champ** (activité 7) : c'est le
    **deuxième** élément de la file, celui qui suit la tête.
    ```
    fonction supprimer_premier_du_troisieme(F):
        si estVide(F):
            retourner
        temp = vide()
        enfiler(defiler(F), temp)    # on garde la tête
        si non estVide(F):
            defiler(F)               # 2e élément : supprimé
        tant que non estVide(F):
            enfiler(defiler(F), temp)
        tant que non estVide(temp):  # restauration de F
            enfiler(defiler(temp), F)
    ```

---

## 5. Interface contre implémentation

| | **Interface** | **Implémentation** |
|---|---|---|
| Question | *Que peut-on faire ?* | *Comment est-ce réalisé ?* |
| Contenu | Noms, paramètres, effets des opérations | Structures internes + code |
| Vue par | Le **client** | Le **concepteur** de la structure |
| Stabilité | Doit rester **stable** | Peut **changer** sans gêner le client |

!!! tip "Une même interface, plusieurs implémentations"
    Une pile (ou une file) peut être réalisée de **plusieurs façons** — par exemple
    avec une **liste chaînée** ou avec un **tableau** — **sans changer son
    interface**. Le client écrit `empiler(a, P)` de la même manière, quelle que
    soit la représentation interne.

---

## 6. Tableaux

- un tableau a une **taille fixe** ;
- ses cases sont **indexées** (dans le cours, de `1` à `n`) ;
- **accès** et **modification** se font directement par `T[i]` ;
- `T[i]` permet de **lire** (`x ← T[i]`) ou d'**écrire** (`T[i] ← x`).

---

## 7. Pile implémentée par tableau

**Données :** un tableau `T` de `n` cases (indices `1` à `n`) + l'attribut `sommet(P)`.

- `sommet(P)` = indice de l'élément **le plus récemment empilé** : la pile va de
  `T[1]` (base) à `T[sommet(P)]` (sommet) ;
- la pile est **vide** si `sommet(P) == 0`, **pleine** si `sommet(P) == n`.

```
estVide(P):
    si sommet(P) == 0:
        retourner VRAI
    sinon:
        retourner FAUX

empiler(a, P):
    si sommet(P) == n:            # le tableau est plein
        afficher "espace insuffisant"
    sinon:
        sommet(P) := sommet(P) + 1
        T[sommet(P)] := a

depiler(P):
    si sommet(P) == 0:
        afficher "pile vide"
    sinon:
        sommet(P) := sommet(P) - 1
        retourner T[sommet(P) + 1]
```

!!! example "État après une suite d'opérations"
    Pile vide, puis `empiler(2, P)`, `empiler(5, P)`, `empiler(8, P)` et `depiler(P)` :
    `depiler` renvoie `8`, `sommet(P)` vaut `2` et la pile est `(5, (2, vide()))`.
    La case `T[3]` contient **encore** `8`, mais cette valeur **n'appartient
    plus** à la pile : seules les cases `T[1]` à `T[sommet(P)]` en font partie.

---

## 8. File implémentée par tableau circulaire

**Données :** un tableau `T` de `n` cases (indices `1` à `n`) + deux attributs `tete(F)` et `queue(F)`.

- `tete(F)` = indice de l'élément en **tête** de la file ;
- `queue(F)` = indice de l'**emplacement où insérer** le prochain élément (case vide
  au sens de la file) : la file va de `T[tete(F)]` à `T[queue(F) - 1]` ;
- **tableau circulaire** : après la case `n`, on revient à la case `1` ;
- file **vide** : `tete(F) == queue(F)` ;
- file **pleine** : `tete(F) == queue(F) + 1` (ou `tete(F) == 1` et `queue(F) == n`).

```
estVide(F):
    si queue(F) == tete(F):
        retourner VRAI
    sinon:
        retourner FAUX

enfiler(a, F):
    T[queue(F)] := a
    si queue(F) == n:
        queue(F) := 1
    sinon:
        queue(F) += 1

defiler(F):
    x := T[tete(F)]
    si tete(F) == n:
        tete(F) := 1
    sinon:
        tete(F) += 1
    retourner x
```

!!! warning "Case conservée en mémoire"
    Après un `defiler`, l'ancienne case de `tete` **contient encore** sa valeur,
    mais celle-ci **n'appartient plus** à la file. Seules les cases comprises
    entre `tete` et `queue` (en tenant compte du **fonctionnement circulaire**)
    font partie de la file.

---

## 9. Méthodes bac

!!! tip "Procédures à appliquer"
    - **Extraire l'interface d'un énoncé** : repérer les opérations demandées et
      leur rôle, sans se soucier du code interne.
    - **Spécifier une opération** : préciser ses **paramètres**, ses
      **préconditions** (ex. : pile non vide), son **effet** (structure modifiée)
      et son **résultat** (valeur renvoyée).
    - **Représenter une pile / file après opérations** : appliquer les opérations
      une à une et noter l'état (contenu logique + indices).
    - **Compléter un pseudo-code** : identifier le cas de base (vide / plein) et la
      mise à jour des indices.
    - **Vérifier les cas vide et plein** : tester `estVide` avant `depiler` /
      `defiler`, et le cas « plein » avant `empiler` / `enfiler`.
    - **Restaurer une structure** après usage d'une structure **auxiliaire**
      (revider l'auxiliaire dans la structure d'origine).
    - **Distinguer index, valeur et position logique** : l'indice d'une case, la
      valeur qu'elle contient et la place de l'élément dans la structure sont trois
      choses différentes.

---

## 10. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **interface** et **implémentation** ;
    - confondre **LIFO** (pile) et **FIFO** (file) ;
    - confondre **sommet** (pile) avec **tête** / **queue** (file) ;
    - confondre **fonction** (renvoie) et **procédure** (agit) ;
    - **oublier un retour** : `depiler` / `defiler` doivent **renvoyer** la valeur ;
    - confondre **valeur présente dans le tableau** et **valeur appartenant
      encore à la structure** (une case « oubliée » n'en fait plus partie) ;
    - **oublier le fonctionnement circulaire** de la file (après la case `n`, on revient à la case `1`) ;
    - inverser l'ordre des paramètres : c'est `empiler(a, P)` et `enfiler(a, F)` (la valeur d'abord).

---

## 11. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Quelle est la différence entre interface et implémentation ?"
    L'**interface** décrit les opérations utilisables (le « quoi ») ;
    l'**implémentation** est la réalisation concrète interne (le « comment »).

??? question "2. Que signifient LIFO et FIFO ?"
    **LIFO** (pile) : le dernier élément ajouté est le premier retiré.
    **FIFO** (file) : le premier élément ajouté est le premier retiré.

??? question "3. Spécifier l'opération `depiler(P)`."
    **Paramètre** : une pile `P`. **Précondition** : `P` non vide. **Effet** :
    retire le sommet (modifie `P`). **Résultat** : renvoie la valeur retirée.

??? question "4. Pourquoi le client n'a-t-il pas besoin de l'implémentation ?"
    Parce qu'il utilise la structure **via son interface** : connaître le nom des
    opérations et leur effet suffit, quelle que soit la réalisation interne.

??? question "5. Pile vide, on fait : empiler(3, P), empiler(7, P), depiler(P). Que renvoie depiler et quel est l'état ?"
    `depiler` renvoie `7`. La pile est ensuite `(3, vide())`.

??? question "6. Dans une pile par tableau, que vaut `sommet(P)` quand la pile est vide ?"
    `sommet(P) == 0` (les cases utilisées vont de `T[1]` à `T[sommet(P)]`).

??? question "7. File circulaire : pourquoi `enfiler` teste-t-il `queue(F) == n` ?"
    Pour le **retour circulaire** : après la dernière case `n`, `queue(F)` revient
    à `1` pour réutiliser les premières cases.

??? question "8. Comment teste-t-on qu'une file circulaire est vide ?"
    Lorsque `tete(F) == queue(F)`.

??? question "9. Corriger ce pseudo-code de `empiler` : `T[sommet(P)] := a` puis `sommet(P) := sommet(P) + 1`"
    L'ordre est inversé : `sommet(P)` indexe le **dernier élément empilé**, il faut
    donc d'abord avancer `sommet(P)`, puis écrire :
    ```
    sommet(P) := sommet(P) + 1
    T[sommet(P)] := a
    ```

??? question "10. Une case du tableau contient encore 8 après un depiler. Cette valeur appartient-elle à la pile ? Justifier."
    **Non** : seules les cases `T[1]` à `T[sommet(P)]` appartiennent à la pile. La valeur
    `8` est une **ancienne valeur** restée en mémoire mais hors de la structure.

---

## À retenir absolument

!!! success "L'essentiel"
    - le **client dépend de l'interface, pas de la représentation** interne ;
    - **pile = LIFO** ; **file = FIFO** ;
    - `depiler` et `defiler` **modifient** la structure **et renvoient** la valeur retirée ;
    - **plusieurs implémentations** (tableau, liste chaînée…) peuvent respecter
      **le même cahier des charges** (la même interface) ;
    - une valeur **présente dans le tableau** n'appartient pas forcément **encore**
      à la structure ;
    - dans une file par tableau **circulaire**, après la case `n` on revient à la case `1`.

!!! quote "Formulations utiles au bac"
    - « Le client utilise la structure via son **interface**, sans connaître son
      **implémentation**. »
    - « `depiler` a un **effet de bord** (la pile est modifiée) **et** renvoie une
      valeur. »
    - « Cette case contient une ancienne valeur, mais elle **n'appartient plus** à
      la structure. »
    - « Une même interface peut être réalisée par **plusieurs implémentations**. »