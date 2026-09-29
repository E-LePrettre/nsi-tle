---
author: Elisabeth Le Prettre (LePrettre)
title: 05b 📜 Fiche Méthode - Liste - Pile - File - Dictionnaire
---

# Listes chaînées, piles, files et dictionnaires

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur les principales structures de
    données : `list`, **liste chaînée**, **pile** (LIFO), **file** (FIFO),
    **dictionnaire** et `set`, leurs interfaces, leurs implémentations et leurs
    **complexités**.

---

## 1. Tableau comparatif initial

| Structure | Principe | Accès | Ajout / Retrait | Usage typique | Complexités essentielles |
|---|---|---|---|---|---|
| **`list` Python** | Séquence indexée, taille dynamique | Direct par indice | En **fin** facile, en tête/milieu coûteux | Usage général | Accès `O(1)` ; ajout fin `O(1)` amorti ; insertion/suppression milieu `O(n)` |
| **Liste chaînée** | Cellules reliées par des références | **Séquentiel** | En **tête** facile | Nombreuses insertions/suppressions en tête | Accès position `O(n)` ; insertion tête `O(1)` |
| **Pile** | **LIFO** | Sommet seulement | Au **sommet** | Parenthésage, calculatrice, annulation | `empiler` / `depiler` `O(1)` |
| **File** | **FIFO** | Tête et queue | Enfiler en **queue**, défiler en **tête** | File d'attente, parcours en largeur | `enfiler` / `defiler` `O(1)` (bonne implémentation) |
| **Dictionnaire** | Association **clé → valeur** | Par **clé** | Par clé | Recherche rapide, associations | Recherche/ajout/suppression `O(1)` **moyen** |
| **`set`** | Ensemble de valeurs **uniques** | Par valeur | Par valeur | Appartenance, unicité | Appartenance/ajout/retrait `O(1)` **moyen** |

---

## 2. Tableaux

- **taille fixe**, **mémoire contiguë** ;
- **accès** et **modification** d'une case : `O(1)` (par l'indice) ;
- **recherche** d'une valeur : `O(n)` ;
- **insertion** / **suppression** : `O(n)` (il faut décaler les éléments).

---

## 3. Listes chaînées

### Définitions

| Terme | Définition |
|---|---|
| **Cellule / `Node`** | Maillon contenant une **valeur** et une **référence** vers le suivant. |
| **Valeur** | Donnée stockée dans la cellule. |
| **Référence suivante** | Lien vers la cellule suivante (`None` à la fin). |
| **Tête** | Première cellule de la liste. |
| **Queue** | Dernière cellule de la liste. |
| **Vide** | Liste sans aucune cellule. |
| **Structure récursive** | Une liste est **vide**, ou bien une **cellule suivie d'une liste**. |

### Primitives

créer · tester le vide · `cons` / ajouter en tête · lire / supprimer la tête ·
lire / insérer / supprimer à une **position** · afficher.

### Trois implémentations

| Implémentation | Principe | Caractéristique |
|---|---|---|
| **Tuples imbriqués** | `(v1, (v2, (v3, None)))` | **Non mutable**, approche **fonctionnelle** |
| **`list` Python** | tête = `L[0]`, reste = `L[1:]` | Utilise **copies / slices** |
| **POO** | classes `Node` et `Liste`, attribut `head` | Interface **mutable** |

```python
class Node:
    def __init__(self, valeur, suivant=None):
        self.valeur = valeur
        self.suivant = suivant

class Liste:
    def __init__(self):
        self.head = None
    def isEmpty(self):
        return self.head is None
    def insertHead(self, v):           # ajout en tête : O(1)
        self.head = Node(v, self.head)
```

### Méthodes du cours

- `isEmpty` : la liste est-elle vide ? (`head is None`) ;
- `insertHead` : ajouter une valeur en **tête** ;
- `insertPosition` : insérer à une **position** (parcourir jusqu'au prédécesseur, puis relier) ;
- `delPosition` : supprimer à une **position** (relier le prédécesseur au successeur) ;
- `readPosition` : lire la valeur à une **position** (parcours séquentiel) ;
- **affichage** et **récupération récursive** (parcourir la structure récursive).

### Coûts

| Opération | Coût | Pourquoi |
|---|---|---|
| Accès à une position | `O(n)` | parcours séquentiel depuis la tête |
| Insertion en **tête** | `O(1)` | une seule liaison à modifier (vraie liste chaînée) |
| Recherche du **prédécesseur** | `O(n)` | parcours nécessaire avant d'insérer/supprimer |
| **Liaison** seule | `O(1)` | changer une référence est immédiat |

!!! tip "Intérêt de la concaténation (approche fonctionnelle)"
    Avec `cons`, ajouter un élément en tête (`O(1)`) **partage** le reste de la
    liste sans la recopier : on construit une nouvelle liste tout en réutilisant
    l'ancienne.

!!! note "Trois styles à distinguer"
    - **fonctionnel** : structures **non mutables**, on **crée** de nouvelles listes ;
    - **mutation** : on **modifie** la liste en place (POO) ;
    - **programmation défensive** : vérifier les préconditions et **copier** pour
      éviter les effets de bord involontaires.

---

## 4. Piles

**LIFO** — dernier entré, premier sorti. Usages : **parenthésage**,
**calculatrice** (expression postfixée), annulation, gestion des appels récursifs.

**Primitives :** `pileVide`, `estVide`, `empiler`, `depiler`, `taille`, `sommet`.

| Implémentation | Idée |
|---|---|
| **`list`** | `append` pour empiler, `pop` pour dépiler |
| **POO avec `list`** | une classe encapsulant une liste |
| **Liste chaînée (1 ou 2 classes)** | empiler = ajouter en tête |
| **`deque`** | `from collections import deque` (efficace aux deux bouts) |

!!! warning "Effets de bord à connaître"
    - `append(x)` : **modifie** la liste, renvoie `None` ;
    - `pop()` : **modifie** la liste **et renvoie** l'élément retiré ;
    - `+=` : **modifie** la liste en place ;
    - **concaténation** `+` : crée une **nouvelle** liste ;
    - **slice** `L[a:b]` : crée une **copie** (nouvelle liste).

!!! example "Calculer taille / sommet sans modifier l'état (pile auxiliaire)"
    ```
    fonction taille(p):
        aux ← pileVide()
        n ← 0
        tant que non estVide(p):
            empiler(aux, depiler(p)) ; n ← n + 1
        tant que non estVide(aux):
            empiler(p, depiler(aux))     # on restaure p
        renvoyer n
    ```

---

## 5. Files

**FIFO** — premier entré, premier sorti. Usages : **file d'attente**, parcours en
largeur, jeux (**bataille**).

**Primitives :** `fileVide`, `estVide`, `enfiler`, `defiler`, `taille`, **tête**.

| Implémentation | Coût aux extrémités |
|---|---|
| **`list`** | ajout en fin `O(1)` amorti, retrait en tête `O(n)` (décalage) |
| **POO** | encapsule une `list` |
| **Liste chaînée** | tête/queue gérées par références |
| **Deux pointeurs `head` / `queue`** | enfiler et défiler en `O(1)` |
| **`deque`** | `O(1)` aux deux extrémités |
| **Deux piles** | défiler `O(1)` **amorti** (voir ci-dessous) |

!!! note "File avec deux piles"
    ```python
    class File2Piles:
        def __init__(self):
            self.entree = []   # pile d'entrée
            self.sortie = []   # pile de sortie
        def enfiler(self, x):
            self.entree.append(x)
        def defiler(self):
            if not self.sortie:                # transfert si sortie vide
                while self.entree:
                    self.sortie.append(self.entree.pop())
            return self.sortie.pop()
    ```
    Le transfert **inverse** l'ordre, ce qui rétablit le comportement FIFO.

!!! example "Restaurer la file après calcul de taille / tête"
    ```
    fonction taille(f):
        aux ← fileVide() ; n ← 0
        tant que non estVide(f):
            enfiler(aux, defiler(f)) ; n ← n + 1
        tant que non estVide(aux):
            enfiler(f, defiler(aux))     # restauration (l'ordre est conservé)
        renvoyer n
    ```

---

## 6. Dictionnaires et hachage

### Le dictionnaire

- **tableau associatif** : ensemble de paires **clé → valeur** ;
- les **clés** sont **distinctes** et **hashables** (donc **non mutables**) ;
- opérations : **ajout** `d[k] = v`, **modification** `d[k] = v2`, **suppression**
  `del d[k]`, **appartenance** `k in d` ;
- parcours : `keys()` (clés), `values()` (valeurs), `items()` (paires).

### La fonction de hachage

| Notion | Définition |
|---|---|
| **Fonction de hachage** | Transforme une clé en un entier (son **empreinte**). |
| **Empreinte** | Entier calculé à partir de la clé, servant d'indice. |
| **Déterminisme** | Une même clé donne **toujours** la même empreinte. |
| **Répartition** | Une bonne fonction répartit les empreintes **uniformément**. |
| **Collision** | Deux clés différentes donnent la **même** empreinte. |

### La table de hachage

- **table de hachage** : tableau indexé par l'empreinte des clés ;
- gestion des collisions :
    - **chaînage** : chaque case contient une **liste** des paires en collision ;
    - **adressage ouvert** : on cherche une **autre case libre** ;
- **redimensionnement** : la table s'agrandit quand elle devient trop pleine.

### Complexités

| Opération | Moyenne | Pire cas |
|---|---|---|
| Recherche | `O(1)` | `O(n)` |
| Insertion | `O(1)` | `O(n)` |
| Suppression | `O(1)` | `O(n)` |

!!! tip "Comparaison liste vs dictionnaire"
    Rechercher une valeur dans une **liste** coûte `O(n)` (parcours), alors que la
    recherche par **clé** dans un **dictionnaire** coûte `O(1)` en moyenne.

!!! warning "Deux usages très différents du hachage"
    - **`hash()`** et les **tables de hachage** servent à organiser des données
      (dictionnaires, `set`) ;
    - le **hachage cryptographique** (`hashlib`) sert à la **sécurité**.
    Pour stocker des **mots de passe**, on utilise un **sel** (donnée aléatoire
    ajoutée) et des **fonctions lentes** spécialement conçues, et **non** la
    fonction `hash()` des structures de données.

---

## 7. Méthode de choix d'une structure

| Besoin | Structure conseillée |
|---|---|
| Accès direct par **indice**, ordre fixe | **Tableau** / `list` |
| Beaucoup d'**insertions / suppressions en tête** | **Liste chaînée** |
| Dernier arrivé traité en premier (**LIFO**) | **Pile** |
| Premier arrivé traité en premier (**FIFO**) | **File** |
| **Associer** une information à une **clé**, recherche rapide | **Dictionnaire** |
| Vérifier l'**unicité** / l'appartenance | `set` |

!!! tip "Critères de décision"
    Se poser quatre questions : l'**ordre** compte-t-il ? quel **mode d'accès**
    (indice, clé, extrémités) ? où ont lieu les **ajouts/retraits** ? quel **coût**
    attendu pour l'opération la plus fréquente ?

---

## 8. Méthodes bac

!!! tip "Procédures à appliquer"
    - **reconnaître** une structure à partir de son **interface** (primitives) ;
    - **suivre l'état** d'une pile / file / liste après une suite d'opérations ;
    - **compléter** une classe ou une fonction (cas vide, mise à jour des liens) ;
    - **préserver la structure** (restaurer après usage d'une auxiliaire) ;
    - **justifier une complexité** (`O(1)`, `O(n)`, `O(1)` amorti / moyen) ;
    - **comparer deux implémentations** (coûts, effets de bord) ;
    - **repérer les effets de bord** (`append`, `pop`, `+=`, slices…).

---

## 9. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **`list` Python** et **liste chaînée** ;
    - confondre **LIFO** (pile) et **FIFO** (file) ;
    - confondre **tête**, **sommet** et **queue** ;
    - confondre **valeur retournée** et **structure modifiée** ;
    - croire que `pop` renvoie une **nouvelle liste** (il **modifie** la liste) ;
    - utiliser une **clé mutable** dans un dictionnaire (interdit) ;
    - confondre `O(1)` **moyen** et `O(1)` **garanti** (dictionnaire : pire cas `O(n)`) ;
    - confondre **hachage de table** (structures) et **hachage cryptographique** (sécurité).

---

## 10. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Pile vide : empiler(2), empiler(5), depiler(), empiler(9). État final ?"
    La pile contient `[2, 9]` (sommet = `9`). `depiler` avait renvoyé `5`.

??? question "2. File vide : enfiler(1), enfiler(2), defiler(), enfiler(3). État final ?"
    `defiler` retire l'élément de tête, c'est-à-dire `1`. Il reste alors la file
    `[2, 3]`, avec `2` en tête et `3` en queue.

??? question "3. Parenthésage : quelle structure et quel principe ?"
    Une **pile** : on **empile** chaque parenthèse ouvrante et on **dépile** à
    chaque fermante. L'expression est correcte si la pile est **vide** à la fin et
    n'a jamais été dépilée à vide.

??? question "4. Calculatrice (expression postfixée) : quelle structure ?"
    Une **pile** : on empile les nombres, et à chaque opérateur on dépile deux
    valeurs, on calcule, puis on empile le résultat.

??? question "5. Problème de Josephus : quelle structure convient ?"
    Une **file** (FIFO) : on défile/réenfile les participants pour simuler le tour
    de table, en éliminant un participant à intervalle régulier.

??? question "6. Jeu de bataille : comment modéliser les mains des joueurs ?"
    Par deux **files** : chaque joueur pioche en **tête** et place les cartes
    gagnées en **queue** (comportement FIFO).

??? question "7. File avec deux piles : que se passe-t-il au premier `defiler` ?"
    Si la pile de **sortie** est vide, on **transfère** toute la pile d'entrée
    dedans (ce qui inverse l'ordre), puis on dépile la sortie : on récupère bien le
    **premier** entré.

??? question "8. Coût de l'insertion en tête d'une vraie liste chaînée ?"
    `O(1)` : on crée une cellule et on modifie une seule référence.

??? question "9. Pourquoi la recherche dans un dictionnaire est-elle plus rapide que dans une liste ?"
    Le dictionnaire utilise le **hachage** : la clé donne directement l'indice, d'où
    `O(1)` en moyenne, contre `O(n)` pour parcourir une liste.

??? question "10. Qu'est-ce qu'une collision et comment la gérer ?"
    Deux clés différentes ont la **même empreinte**. On gère cela par **chaînage**
    (liste dans la case) ou par **adressage ouvert** (autre case libre).

??? question "11. Corriger : `empiler` écrite comme `def empiler(p, x): p.pop(x)`"
    `pop` **retire** un élément ; il faut `append` pour empiler :
    ```python
    def empiler(p, x):
        p.append(x)
    ```

??? question "12. `O(1)` moyen et `O(1)` garanti, est-ce pareil pour un dictionnaire ?"
    Non : les opérations sont `O(1)` **en moyenne**, mais `O(n)` **au pire** (si
    toutes les clés entrent en collision). Le `O(1)` n'est donc pas **garanti**.

---

## À retenir absolument

| Structure | Principe | Accès | Force | Coût clé |
|---|---|---|---|---|
| **Tableau / `list`** | Cases indexées | Direct (indice) | Accès immédiat | Accès `O(1)`, insertion milieu `O(n)` |
| **Liste chaînée** | Cellules reliées | Séquentiel | Insertion **en tête** | Tête `O(1)`, accès position `O(n)` |
| **Pile** | **LIFO** | Sommet | Simplicité | `empiler`/`depiler` `O(1)` |
| **File** | **FIFO** | Tête / queue | File d'attente | `enfiler`/`defiler` `O(1)` (bonne implémentation) |
| **Dictionnaire** | Clé → valeur (hachage) | Par clé | Recherche rapide | `O(1)` moyen, `O(n)` pire |
| **`set`** | Valeurs uniques | Par valeur | Appartenance / unicité | `O(1)` moyen |

!!! quote "Formulations utiles au bac"
    - « Une **liste chaînée** permet l'insertion en tête en `O(1)`, là où un tableau
      impose un décalage en `O(n)`. »
    - « `depiler` a un **effet de bord** : il modifie la pile **et** renvoie une valeur. »
    - « La recherche par clé dans un dictionnaire est `O(1)` **en moyenne** grâce au
      **hachage**, mais `O(n)` au pire cas. »
    - « On choisit une **file** car le premier élément arrivé doit être traité en premier. »