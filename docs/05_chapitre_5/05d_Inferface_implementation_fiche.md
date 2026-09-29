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
| `estVide(p)` | Tester si vide | pile `p` | aucun | booléen |
| `empiler(p, x)` | Ajouter au sommet | pile `p`, valeur `x` | `p` modifiée | — |
| `depiler(p)` | Retirer le sommet | pile `p` (non vide) | `p` modifiée | la valeur retirée |

!!! note "Méthodes du cours (n'utilisant que les primitives)"
    **Compter les éléments en restaurant la pile** — on vide `p` dans une pile
    auxiliaire, puis on la reconstitue :
    ```
    fonction compter(p):
        aux ← vide()
        n ← 0
        tant que non estVide(p):
            empiler(aux, depiler(p))   # depiler renvoie ET modifie
            n ← n + 1
        tant que non estVide(aux):     # restauration de p
            empiler(p, depiler(aux))
        renvoyer n
    ```
    *Deux passages dans l'auxiliaire remettent les éléments dans l'ordre initial.*

    **Supprimer le deuxième élément** (juste sous le sommet) :
    ```
    fonction supprimer_deuxieme(p):
        sommet ← depiler(p)   # on met de côté le sommet
        depiler(p)            # on retire (et jette) le 2e élément
        empiler(p, sommet)    # on remet le sommet
    ```

---

## 4. Interface de la file

Principe **FIFO** : on **enfile en queue** et on **défile en tête**. Une file se
décrit par sa **tête** (premier élément), sa **queue** (dernier) et son **reste**.

| Primitive | Rôle | Paramètres | Effet | Résultat |
|---|---|---|---|---|
| `vide()` | Créer une file vide | aucun | — | une file vide |
| `estVide(f)` | Tester si vide | file `f` | aucun | booléen |
| `enfiler(f, x)` | Ajouter en queue | file `f`, valeur `x` | `f` modifiée | — |
| `defiler(f)` | Retirer en tête | file `f` (non vide) | `f` modifiée | la valeur retirée |

!!! note "Méthodes du cours (n'utilisant que les primitives)"
    **Compter les éléments en restaurant la file** :
    ```
    fonction compter(f):
        aux ← vide()
        n ← 0
        tant que non estVide(f):
            enfiler(aux, defiler(f))
            n ← n + 1
        tant que non estVide(aux):     # restauration de f
            enfiler(f, defiler(aux))
        renvoyer n
    ```
    *En FIFO, recopier dans l'auxiliaire puis revenir conserve l'ordre initial.*

    **Supprimer l'élément demandé** (`e` passé en paramètre) :
    ```
    fonction supprimer(f, e):
        aux ← vide()
        tant que non estVide(f):
            x ← defiler(f)
            si x ≠ e:               # on ne réenfile pas l'élément visé
                enfiler(aux, x)
        tant que non estVide(aux):  # restauration de f sans e
            enfiler(f, defiler(aux))
    ```

!!! info "À adapter à ton cours"
    Si la version de ton cours supprime l'élément à une **position** donnée (et non
    par valeur), il suffit de compter les positions avec un compteur `i` et de ne
    pas réenfiler celui d'indice visé. Dis-moi la signature exacte si besoin.

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
    interface**. Le client écrit `empiler(p, x)` de la même manière, quelle que
    soit la représentation interne.

---

## 6. Tableaux

- un tableau a une **taille fixe** ;
- ses cases sont **indexées** (de `0` à `taille - 1`) ;
- **accès** et **modification** se font directement par `T[i]` ;
- `T[i]` permet de **lire** (`x ← T[i]`) ou d'**écrire** (`T[i] ← x`).

---

## 7. Pile implémentée par tableau

**Données :** un tableau `T` + un indice `sommet`.

- convention : `sommet` = indice du dernier élément ; `sommet = -1` si la pile est **vide** ;
- la pile est **pleine** si `sommet = taille - 1`.

```
estVide(p):
    renvoyer sommet == -1

empiler(p, x):           # si pile non pleine
    sommet ← sommet + 1
    T[sommet] ← x

depiler(p):              # si pile non vide
    x ← T[sommet]
    sommet ← sommet - 1
    renvoyer x
```

!!! example "État après une suite d'opérations"
    Après `empiler(2)`, `empiler(5)`, `empiler(8)` puis `depiler()` :
    `sommet` vaut `1` et la pile « logique » est `[2, 5]`.
    La case `T[2]` contient **encore** `8`, mais cette valeur **n'appartient
    plus** à la pile : seules les cases jusqu'à `sommet` en font partie.

---

## 8. File implémentée par tableau circulaire

**Données :** un tableau `T` de taille `N` + deux indices `tete` et `queue`.

- `tete` = indice du **premier** élément ;
- `queue` = indice de la **prochaine case libre** (emplacement d'insertion) ;
- **retour circulaire** : quand un indice dépasse `N-1`, il revient à `0` grâce à
  l'opération **modulo** (`mod N`) ;
- file **vide** : `tete == queue` ;
- file **pleine** : `(queue + 1) mod N == tete` (on laisse une case libre pour
  distinguer le vide du plein).

```
estVide(f):
    renvoyer tete == queue

enfiler(f, x):           # si file non pleine
    T[queue] ← x
    queue ← (queue + 1) mod N

defiler(f):              # si file non vide
    x ← T[tete]
    tete ← (tete + 1) mod N
    renvoyer x
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
    - **oublier le fonctionnement circulaire** de la file (oubli du `mod N`).

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

??? question "3. Spécifier l'opération `depiler(p)`."
    **Paramètre** : une pile `p`. **Précondition** : `p` non vide. **Effet** :
    retire le sommet (modifie `p`). **Résultat** : renvoie la valeur retirée.

??? question "4. Pourquoi le client n'a-t-il pas besoin de l'implémentation ?"
    Parce qu'il utilise la structure **via son interface** : connaître le nom des
    opérations et leur effet suffit, quelle que soit la réalisation interne.

??? question "5. Pile vide, on fait : empiler(3), empiler(7), depiler(). Que renvoie depiler et quel est l'état ?"
    `depiler` renvoie `7`. La pile contient ensuite `[3]` (sommet = `3`).

??? question "6. Dans une pile par tableau, que vaut `sommet` quand la pile est vide ?"
    `sommet == -1`.

??? question "7. File circulaire : à quoi sert l'opération `mod N` dans `enfiler` ?"
    Elle assure le **retour circulaire** : quand `queue` dépasse `N-1`, l'indice
    revient à `0` pour réutiliser les premières cases.

??? question "8. Comment teste-t-on qu'une file circulaire est vide ?"
    Lorsque `tete == queue`.

??? question "9. Corriger ce pseudo-code de `empiler` : `T[sommet] ← x ; sommet ← sommet + 1`"
    L'ordre est inversé : il faut d'abord avancer `sommet`, puis écrire :
    ```
    sommet ← sommet + 1
    T[sommet] ← x
    ```

??? question "10. Une case du tableau contient encore 8 après un depiler. Cette valeur appartient-elle à la pile ? Justifier."
    **Non** : seules les cases jusqu'à `sommet` appartiennent à la pile. La valeur
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
    - dans une file par tableau **circulaire**, ne pas oublier le `mod N`.

!!! quote "Formulations utiles au bac"
    - « Le client utilise la structure via son **interface**, sans connaître son
      **implémentation**. »
    - « `depiler` a un **effet de bord** (la pile est modifiée) **et** renvoie une
      valeur. »
    - « Cette case contient une ancienne valeur, mais elle **n'appartient plus** à
      la structure. »
    - « Une même interface peut être réalisée par **plusieurs implémentations**. »