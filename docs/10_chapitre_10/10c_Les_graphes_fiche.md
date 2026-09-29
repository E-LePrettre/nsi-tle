---
author: Elisabeth Le Prettre (LePrettre)
title: 10 📜 Fiche Méthode - Les graphes
---

# Les graphes

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur les graphes : vocabulaire,
    représentations, parcours **BFS / DFS**, détection de cycle, plus courts chemins
    (**BFS, Dijkstra, Bellman-Ford**) et application au **labyrinthe**.

!!! note "Graphe-exemple filé (non orienté)"
    Arêtes : `A-B`, `A-C`, `B-D`, `C-D`, `D-E`.
    ```
    A: [B, C]   B: [A, D]   C: [A, D]   D: [B, C, E]   E: [D]
    ```

---

## 1. Vocabulaire

| Terme | Définition |
|---|---|
| **Graphe** | Ensemble de **sommets** reliés par des **arêtes**. |
| **Sommet / nœud** | Élément du graphe. |
| **Arête** | Lien **non orienté** entre deux sommets. |
| **Arc** | Lien **orienté** (a un sens). |
| **Ordre** | Nombre de **sommets** (`n`). |
| **Voisin / adjacent** | Sommet directement relié à un autre. |
| **Degré** | Nombre d'arêtes incidentes à un sommet. |
| **Chaîne / chemin** | Suite de sommets reliés successivement. |
| **Cycle** | Chemin qui **revient** à son point de départ. |
| **Graphe connexe** | Tout sommet est **atteignable** depuis n'importe quel autre. |
| **Orienté / non orienté / pondéré** | Avec sens / sans sens / avec **poids** sur les liens. |

---

## 2. Représentations

| Représentation | Principe | Mémoire | Adjacence | Voisins |
|---|---|---|---|---|
| **Matrice** | tableau `n × n` | `O(n²)` | `O(1)` | `O(n)` |
| **Liste d'adjacence** | dictionnaire de voisins | `O(n+m)` | linéaire dans les voisins | accès direct |

!!! note "Précisions"
    - matrice **symétrique** si le graphe est **non orienté** ;
    - ligne `i`, colonne `j` = arc `i → j` ;
    - dans un graphe **pondéré**, on met le **poids** à la place du `1` ;
    - graphe **orienté** : on distingue **successeurs** et **prédécesseurs** ;
    - graphe **pondéré** : on stocke des couples `(voisin, poids)`.

---

## 3. Conversions

```python
# matrice → dictionnaire
def matrice_vers_dict(M, sommets):
    d = {}
    for i in range(len(M)):
        d[sommets[i]] = [sommets[j] for j in range(len(M)) if M[i][j] != 0]
    return d

# matrice pondérée → dictionnaire de couples (voisin, poids)
def matrice_ponderee_vers_dict(M, sommets):
    d = {}
    for i in range(len(M)):
        d[sommets[i]] = [(sommets[j], M[i][j]) for j in range(len(M)) if M[i][j] != 0]
    return d

# dictionnaire → matrice
def dict_vers_matrice(d, sommets):
    n = len(sommets)
    idx = {s: k for k, s in enumerate(sommets)}
    M = [[0] * n for _ in range(n)]          # matrice de zéros
    for u in d:
        for v in d[u]:
            M[idx[u]][idx[v]] = 1
    return M
```

!!! tip "Rôle des indices"
    Les **indices de lignes / colonnes** correspondent aux **sommets** (via un
    dictionnaire `sommet → indice`). On **initialise** toujours une matrice de
    **zéros** avant de placer les `1` (ou les poids).

---

## 4. Visualisation et POO

| Outil | Éléments |
|---|---|
| **NetworkX** | `Graph`, `add_node`, `add_edge`, `draw` |
| **Graphviz** | `Graph`, `Digraph`, `node`, `edge` |

Interface de la classe `Graphe` :

```python
class Graphe:
    def __init__(self):
        self.adj = {}
    def ajouter_arete(self, u, v):
        self.adj.setdefault(u, [])
        self.adj.setdefault(v, [])
        if v not in self.adj[u]:        # éviter les doublons
            self.adj[u].append(v)
        if u not in self.adj[v]:        # arête non orientée → dans les DEUX listes
            self.adj[v].append(u)
    def voisins(self, u):
        return self.adj[u]
    def sont_voisins(self, u, v):
        return v in self.adj[u]
    def get_dictionnaire(self):
        return self.adj
```

!!! warning "Arête non orientée"
    Une arête non orientée est ajoutée dans **les deux listes** d'adjacence, en
    veillant à **éviter les doublons**.

---

## 5. BFS (parcours en largeur)

!!! abstract "Fiche synthèse BFS"
    - **structure** : **file FIFO** ;
    - **outils** : `deque`, `append` (enfiler), `popleft` (défiler) ;
    - **exploration par niveaux** (de proche en proche) ;
    - donne le **plus court chemin** dans un graphe **non pondéré** ;
    - **mémorise** les sommets déjà **découverts**.

```python
from collections import deque

def bfs(graphe, depart):
    f = deque([depart])
    decouverts = {depart}
    while f:
        s = f.popleft()
        for v in graphe.voisins(s):
            if v not in decouverts:
                decouverts.add(v)
                f.append(v)
    return decouverts
```

!!! example "Suivi BFS depuis A"
    | Sommet retiré | File après | Découverts |
    |---|---|---|
    | — (init) | [A] | {A} |
    | A | [B, C] | {A, B, C} |
    | B | [C, D] | {A, B, C, D} |
    | C | [D] | {A, B, C, D} |
    | D | [E] | {A, B, C, D, E} |
    | E | [ ] | {A, B, C, D, E} |

    Ordre de visite : **A, B, C, D, E**.

---

## 6. DFS (parcours en profondeur)

!!! abstract "Fiche synthèse DFS"
    - **structure** : **pile LIFO** ou **récursion** ;
    - **outils** : `append` (empiler), `pop` (dépiler) ;
    - **exploration en profondeur** (on s'enfonce avant de revenir) ;
    - **retour en arrière** (*backtracking*) quand on est bloqué ;
    - l'**ordre dépend de l'ordre des voisins**.

```python
# DFS itératif (pile)
def dfs_iter(graphe, depart):
    pile = [depart]
    visites = set()
    while pile:
        s = pile.pop()
        if s not in visites:
            visites.add(s)
            for v in graphe.voisins(s):
                if v not in visites:
                    pile.append(v)
    return visites

# DFS récursif
def dfs(graphe, s, visites=None):
    if visites is None:          # éviter l'argument par défaut MUTABLE
        visites = set()
    visites.add(s)
    for v in graphe.voisins(s):
        if v not in visites:
            dfs(graphe, v, visites)
    return visites
```

!!! warning "Argument par défaut mutable"
    Ne **jamais** écrire `def dfs(..., visites=set())` : le `set` serait **partagé**
    entre tous les appels. On utilise `visites=None` puis on l'initialise dans la fonction.

*DFS récursif depuis A (ordre des voisins respecté)* : **A, B, D, C, E**.

---

## 7. Comparaison BFS / DFS

| Critère | BFS | DFS |
|---|---|---|
| Structure | file | pile / récursion |
| Exploration | par niveaux | en profondeur |
| Plus court non pondéré | **oui** | non garanti |
| Applications | proximité, distance | cycles, exploration |

---

## 8. Détection de cycle (graphe orienté)

On colore chaque sommet selon trois **états** :

| État | Signification |
|---|---|
| **non_visité** | pas encore exploré |
| **en_cours** | en cours d'exploration (sur le chemin courant) |
| **terminé** | entièrement exploré |

```python
def detecte_cycle(graphe, sommets):
    etat = {s: "non_visité" for s in sommets}

    def visiter(u):
        etat[u] = "en_cours"
        for v in graphe.voisins(u):
            if etat[v] == "en_cours":        # voisin en_cours → CYCLE
                return True
            if etat[v] == "non_visité" and visiter(v):
                return True
        etat[u] = "terminé"
        return False

    for s in sommets:                        # lancer depuis CHAQUE sommet non visité
        if etat[s] == "non_visité" and visiter(s):
            return True
    return False
```

- il y a un **cycle** si un voisin rencontré est **`en_cours`** ;
- il faut **lancer le DFS depuis chaque sommet non visité** (graphe non connexe).

!!! info "Hors programme / approfondissement"
    La détection de cycle dans un graphe **non orienté** est un **approfondissement**.

---

## 9. Chemins les plus courts

| Situation | Algorithme | Principe | Complexité (cours) |
|---|---|---|---|
| **Non pondéré** | **BFS** | niveaux | `O(n+m)` |
| **Poids positifs** | **Dijkstra** | sommet le plus proche + relaxation | `O(n²)` |
| **Poids négatifs** | **Bellman-Ford** | toutes les arêtes `n−1` fois | `O(n×m)` |

!!! note "Relaxation"
    ```
    nouvelle distance = distance[u] + poids(u, v)
    ```
    Si elle est **plus petite** que `distance[v]`, on met `distance[v]` à jour (et on
    note `u` comme **parent** de `v`).

!!! tip "Dijkstra (poids positifs)"
    1. distances à **l'infini**, source à **0** ;
    2. choisir le sommet **non visité le plus proche** ;
    3. le **retirer** (distance définitive) ;
    4. **relâcher** ses arêtes.

!!! tip "Bellman-Ford (poids éventuellement négatifs)"
    1. **initialiser** les distances ;
    2. **répéter `n−1` fois** ;
    3. **parcourir toutes les arêtes** ;
    4. **améliorer** les distances (relaxation) ;
    5. un **passage supplémentaire** permet de **détecter un cycle négatif** (si une
       distance peut encore diminuer).

---

## 10. Labyrinthe

| Élément du labyrinthe | Traduction en graphe |
|---|---|
| **Case** | sommet |
| **Passage** | arête |
| **Mur** | absence d'arête |

- un sommet s'écrit sous la forme **`(ligne, colonne)`** ;
- on explore avec **BFS** ou **DFS** ;
- un dictionnaire **`parent`** mémorise d'où l'on vient ;
- on peut faire un **arrêt anticipé** dès qu'on atteint la **sortie** ;
- **DFS ne garantit pas** le plus court chemin (préférer **BFS**).

```python
# reconstruire le chemin grâce au dictionnaire parent
def reconstruire(parent, arrivee):
    chemin = []
    s = arrivee
    while s is not None:
        chemin.append(s)
        s = parent[s]
    chemin.reverse()
    return chemin
```

---

## 11. Méthodes bac

!!! tip "Procédures à appliquer"
    - **calculer** l'ordre (nb de sommets) et les **degrés** ;
    - **reconnaître** le type de graphe (orienté / pondéré / connexe) ;
    - **compléter** une matrice ou une liste d'adjacence ;
    - **convertir** une représentation en une autre ;
    - **suivre** un parcours BFS ou DFS (avec tableau de suivi) ;
    - **compléter** une classe `Graphe` ;
    - **détecter un cycle** (états + DFS) ;
    - **choisir** l'algorithme de chemin (non pondéré / positifs / négatifs) ;
    - **réaliser une relaxation** (`distance[u] + poids`) ;
    - **reconstruire** un chemin via le dictionnaire **parent**.

---

## 12. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **arête** (non orientée) et **arc** (orienté) ;
    - oublier qu'un graphe **non orienté** se représente **dans les deux sens** ;
    - croire qu'une matrice **orientée** est forcément **symétrique** (faux) ;
    - confondre **BFS ⇒ file** et **DFS ⇒ pile** ;
    - confondre **sommets visités** et **seulement les sommets déjà retirés** ;
    - oublier que l'**ordre d'un parcours dépend de l'ordre des voisins** ;
    - utiliser **BFS** sur un graphe **pondéré** (il ignore les poids) ;
    - utiliser **Dijkstra** avec des **poids négatifs** (interdit) ;
    - oublier que **Bellman-Ford** est plus **lent** mais plus **général** ;
    - croire que **DFS** fournit le **plus court chemin** (non garanti).

---

## 13. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Quelle est la différence entre une arête et un arc ?"
    Une **arête** relie deux sommets **sans sens** (graphe non orienté) ; un **arc**
    est **orienté** (a un sens).

??? question "2. Dans le graphe-exemple, quel est l'ordre et le degré de D ?"
    Ordre = `5` (A, B, C, D, E) ; degré de D = `3` (voisins B, C, E).

??? question "3. Quand la matrice d'adjacence est-elle symétrique ?"
    Lorsque le graphe est **non orienté**.

??? question "4. Que représente `M[i][j] = 1` ?"
    L'existence d'un **arc** (ou d'une arête) de `i` vers `j`.

??? question "5. Comment représenter un graphe pondéré dans un dictionnaire ?"
    Avec des couples **`(voisin, poids)`** dans la liste de chaque sommet.

??? question "6. Pourquoi ajoute-t-on une arête non orientée dans les deux listes ?"
    Parce qu'elle relie les deux sommets **dans les deux sens** : chacun est voisin
    de l'autre.

??? question "7. Quelle structure utilise BFS et quelles opérations sur `deque` ?"
    Une **file** : `append` (enfiler) et `popleft` (défiler).

??? question "8. Donner l'ordre de visite du BFS depuis A (graphe-exemple)."
    **A, B, C, D, E**.

??? question "9. Donner l'ordre de visite du DFS récursif depuis A."
    **A, B, D, C, E** (dépend de l'ordre des voisins).

??? question "10. Pourquoi éviter `visites=set()` en argument par défaut ?"
    Car ce `set` serait **partagé** entre tous les appels (argument mutable). On
    utilise `visites=None` puis on l'initialise.

??? question "11. Dans un graphe orienté, quand détecte-t-on un cycle en DFS ?"
    Quand un **voisin** rencontré est dans l'état **`en_cours`**.

??? question "12. Quel algorithme pour le plus court chemin avec des poids positifs ?"
    **Dijkstra** (`O(n²)` dans le cours).

??? question "13. Quel algorithme accepte des poids négatifs et à quel coût ?"
    **Bellman-Ford**, en `O(n×m)` (plus lent mais plus général).

??? question "14. Écrire la formule de relaxation."
    `nouvelle distance = distance[u] + poids(u, v)` ; on met à jour si elle est plus
    petite que `distance[v]`.

??? question "15. Dans un labyrinthe, comment reconstruire le chemin trouvé ?"
    En remontant le dictionnaire **`parent`** de l'arrivée jusqu'au départ, puis en
    **inversant** la liste obtenue.

---

## À retenir absolument

!!! success "Représentations"
    | | **Matrice** | **Liste d'adjacence** |
    |---|---|---|
    | Mémoire | `O(n²)` | `O(n+m)` |
    | Test d'adjacence | `O(1)` | linéaire dans les voisins |
    | Lister les voisins | `O(n)` | accès direct |

!!! abstract "BFS vs DFS"
    - **BFS** : **file**, par **niveaux**, **plus court chemin non pondéré** ;
    - **DFS** : **pile / récursion**, en **profondeur**, **cycles** et exploration.

!!! note "Choisir l'algorithme de plus court chemin"
    | Poids | Algorithme | Complexité |
    |---|---|---|
    | aucun (non pondéré) | **BFS** | `O(n+m)` |
    | positifs | **Dijkstra** | `O(n²)` |
    | négatifs possibles | **Bellman-Ford** | `O(n×m)` |

!!! quote "Cycle & reconstruction de chemin"
    - **Cycle (orienté)** : DFS avec états `non_visité` / `en_cours` / `terminé` ;
      cycle si un voisin est **`en_cours`** ; relancer depuis **chaque** sommet non visité.
    - **Reconstruction** : dictionnaire **`parent`**, remonté de l'arrivée au départ
      puis **inversé**.