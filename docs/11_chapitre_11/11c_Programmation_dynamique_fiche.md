---
author: Elisabeth Le Prettre (LePrettre)
title: 11 📜 Fiche Méthode - Programmation dynamique
---

# La programmation dynamique

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur la programmation dynamique :
    mémoïsation, **top-down / bottom-up**, et applications du cours (Fibonacci, rendu
    de monnaie, sac à dos, découpe, triangle de Pascal).

---

## 1. Paradigmes

| Paradigme | Principe | Sous-problèmes | Optimalité |
|---|---|---|---|
| **Force brute** | tester toutes les possibilités | tous les cas | garantie mais coûteuse |
| **Glouton** | meilleur choix local | pas de retour arrière | non garantie |
| **Diviser pour régner** | diviser puis combiner | **indépendants** | selon l'algorithme |
| **Programmation dynamique** | **mémoriser** les résultats | **se chevauchent** | optimale si la relation est correcte |

!!! note "Définitions"
    - **Programmation dynamique** : résoudre un problème en **mémorisant** les
      résultats de sous-problèmes qui **se chevauchent**.
    - **Mémoïsation** : **stocker** un résultat déjà calculé pour ne pas le recalculer.
    - **Sous-problèmes qui se chevauchent** : les mêmes sous-problèmes **réapparaissent** plusieurs fois.
    - **Principe d'optimalité de Bellman** : une solution optimale est composée de
      solutions **optimales** de ses sous-problèmes.
    - **Top-down** : approche **récursive + cache** (on part du grand problème).
    - **Bottom-up** : approche **itérative** (on part des petits sous-problèmes).
    - **Sentinelle** : valeur marquant un état **non calculé** (`-1`, `+∞`, `-∞`).
    - **Cache** : structure qui **stocke** les résultats déjà obtenus.

---

## 2. Méthode générale

!!! tip "Démarche en 8 étapes"
    1. définir précisément l'**état** du sous-problème ;
    2. identifier les **cas de base** ;
    3. établir la **relation de récurrence** ;
    4. choisir **top-down** ou **bottom-up** ;
    5. **initialiser** la structure de stockage ;
    6. calculer chaque état **une seule fois** ;
    7. **lire** la solution finale ;
    8. mémoriser des **prédécesseurs** si la solution doit être **reconstruite**.

---

## 3. Fibonacci

Définition : `F₀ = 0`, `F₁ = 1`, `Fₙ = Fₙ₋₁ + Fₙ₋₂`.

| Version | Principe | Temps | Mémoire | Limite |
|---|---|---|---|---|
| récursive naïve | deux appels | exponentiel | pile récursive | recalculs |
| itérative | deux variables | `O(n)` | `O(1)` | recalcule à chaque appel |
| top-down liste | récursion + cache | `O(n)` | `O(n)` | récursion |
| top-down dictionnaire | récursion + cache | `O(n)` | `O(n)` | récursion |
| bottom-up tableau | tableau croissant | `O(n)` | `O(n)` | stockage complet |
| pythonesque | deux variables | `O(n)` | `O(1)` | grands entiers |

```python
# top-down avec liste et sentinelle -1
def fib(n, F=None):
    if F is None:
        F = [-1] * (n + 2)        # taille n+2 pour couvrir les indices utilisés
    if n < 2:
        return n
    if F[n] != -1:                # déjà calculé → on lit le cache
        return F[n]
    F[n] = fib(n-1, F) + fib(n-2, F)
    return F[n]

# bottom-up avec tableau
def fib(n):
    F = [0] * (n + 2)
    F[1] = 1
    for i in range(2, n + 1):
        F[i] = F[i-1] + F[i-2]
    return F[n]

# pythonesque (affectation simultanée)
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a
```

!!! note "Points à comprendre"
    - **arbre d'appels** : la version naïve **recalcule** sans cesse les mêmes valeurs ;
    - **sentinelle `-1`** : marque une case **non encore calculée** ;
    - **test `n not in F`** (version dictionnaire) : ne calculer que si absent du cache ;
    - **cache persistant** : un dictionnaire conservé entre les appels évite de tout recalculer ;
    - **argument mutable par défaut** : `def fib(n, cache={})` partage le cache entre
      tous les appels — pratique pour la persistance, mais **piège** classique ;
    - **rôle de `n+2`** : dimensionner le tableau pour les indices utilisés ;
    - **affectation simultanée** : `a, b = b, a + b` met à jour les deux variables d'un coup ;
    - **grands entiers** : les additions deviennent plus **coûteuses** quand les nombres grandissent ;
    - **complexité asymptotique ≠ temps mesuré** : `O(n)` décrit la croissance, pas le
      temps réel (qui dépend de la machine et du coût des additions).

---

## 4. Top-down et bottom-up

| Critère | **Top-down** | **Bottom-up** |
|---|---|---|
| Sens du calcul | du grand vers le petit | du petit vers le grand |
| Récursivité | **oui** | non (itératif) |
| Stockage | cache (liste / dict) | tableau rempli dans l'ordre |
| `RecursionError` | **possible** | non |
| États calculés | seulement ceux **nécessaires** | **tous** les états |
| Cache réutilisable | **oui** (entre appels) | non (recalcul à chaque appel) |

---

## 5. Rendu de monnaie

**Problème :** rendre une **somme** avec le **minimum de pièces**.

| Approche | Comportement |
|---|---|
| Force brute | teste toutes les combinaisons (coûteux) |
| Glouton | prend la plus grosse pièce possible → **pas toujours optimal** |
| Récursif naïf | explore sans mémoriser (recalculs) |
| Programmation dynamique | mémorise → **optimal** |

!!! danger "Contre-exemple glouton : pièces `[1, 3, 4]`, somme `6`"
    Le **glouton** prend `4 + 1 + 1` = **3 pièces** ; l'optimal est `3 + 3` = **2 pièces**.

!!! abstract "Relation de récurrence"
    ```
    nb[0] = 0
    nb[s] = min(1 + nb[s − p])   pour toutes les pièces p ≤ s
    ```

```python
import math
def rendu(pieces, somme):
    nb = [math.inf] * (somme + 1)     # initialisation à +∞
    nb[0] = 0
    for s in range(1, somme + 1):     # sommes croissantes
        for p in pieces:              # tester toutes les pièces
            if p <= s:
                nb[s] = min(nb[s], 1 + nb[s - p])
    return nb[somme] if nb[somme] != math.inf else -1   # -1 si impossible
```

- **temps** `O(n × k)` (`n` = somme, `k` = nombre de pièces) ; **espace** `O(n)`.

!!! example "Remplissage complet pour `[1, 2]`, somme `5`"
    | `s` | 0 | 1 | 2 | 3 | 4 | 5 |
    |---|---|---|---|---|---|---|
    | `nb[s]` | 0 | 1 | 1 | 2 | 2 | **3** |

    *Détail :* `nb[2] = min(1+nb[1], 1+nb[0]) = 1` ; `nb[5] = min(1+nb[4], 1+nb[3]) = 3`.

---

## 6. Reconstruction d'une solution

!!! tip "Approche 1 — tableau `combi`"
    On stocke directement, pour chaque somme, **la liste des pièces** utilisées
    (avec une **sentinelle `0`** / liste vide pour `0`). Simple, mais **coûteux en mémoire**.

!!! tip "Approche 2 — tableau `parent` (recommandée)"
    On mémorise, pour chaque somme, **la dernière pièce choisie**, puis on **remonte**
    depuis la somme finale :
    ```python
    s = somme
    choix = []
    while s > 0:
        p = parent[s]
        choix.append(p)
        s -= p
    ```
    Le tableau `parent` permet une mémoire en **`O(n)`** (un seul entier par somme).

---

## 7. Sac à dos

- objets `(valeur, poids)` ; **capacité maximale `w`** ; objectif : **maximiser la valeur**.

!!! abstract "Relation"
    Pour chaque objet, deux choix :
    - **ne pas le prendre** : on garde la meilleure solution sans lui ;
    - **le prendre** (si le poids rentre) : sa **valeur** + meilleure solution pour la
      **capacité restante**.
    On retient le **maximum** des deux.

- **lignes** = objets, **colonnes** = capacités ;
- **remontée** dans le tableau pour retrouver les **objets choisis** ;
- **temps** et **mémoire** : `O(n × w)`.

---

## 8. Découpe optimale

- déterminer le **meilleur prix** pour une longueur donnée ;
- essayer **toutes les premières découpes** possibles ;
- **réutiliser** les résultats déjà mémorisés (sous-problèmes) ;
- approche **récursive top-down** ;
- **sentinelle `−∞`** pour un prix non encore calculé.

!!! abstract "Relation"
    ```
    prix_opt(L) = max( prix[i] + prix_opt(L − i) )   pour i de 1 à L
    ```

---

## 9. Triangle de Pascal

- les coefficients des **bords** valent `1` (`C(i, 0) = C(i, i) = 1`) ;
- **relation** :
  ```
  C(i, j) = C(i−1, j−1) + C(i−1, j)
  ```
- **formule factorielle** : `C(i, j) = i! / (j! × (i−j)!)` ;
- la version **récursive** recalcule les mêmes coefficients (recalculs) ;
- la **construction dynamique** se fait **ligne par ligne**, en réutilisant la ligne
  précédente ;
- un **tableau** conserve les solutions des sous-problèmes.

---

## 10. Méthodes bac

!!! tip "Procédures à appliquer"
    - **repérer les états** (que représente un sous-problème ?) ;
    - **écrire les cas de base** ;
    - **établir la relation** de récurrence ;
    - **choisir l'ordre** de remplissage (top-down / bottom-up) ;
    - **compléter un tableau** (case par case) ;
    - **expliquer une mémoïsation** (cache + test « déjà calculé ») ;
    - **calculer** temps et espace ;
    - **détecter une somme impossible** (résultat resté à `+∞` → `-1`) ;
    - **retrouver** une combinaison ou des objets par **remontée** ;
    - **comparer** glouton et programmation dynamique.

---

## 11. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - **glouton ≠ toujours optimal** (cf. `[1, 3, 4]` pour `6`) ;
    - **programmation dynamique ≠ diviser pour régner** (ici les sous-problèmes **se chevauchent**) ;
    - **mémoïsation ≠ recalculer puis stocker** (on **lit** le cache si déjà calculé) ;
    - confondre **top-down** et **bottom-up** ;
    - **tableau mal dimensionné** (penser à `somme + 1`, `n + 2`…) ;
    - **cas de base non initialisé** (`nb[0] = 0`) ;
    - utiliser **`0`** à tort comme valeur **inconnue** ;
    - oublier **`float('inf')`** ou **`-math.inf`** comme sentinelle ;
    - **argument mutable par défaut** partagé entre appels (attention au cache) ;
    - **mal interpréter une case impossible** (valeur restée infinie) ;
    - **oublier la reconstruction** (le minimum ne donne pas la combinaison) ;
    - croire que le rendu est en `O(n)` : c'est **`O(n × k)`**.

---

## 12. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Qu'est-ce qui distingue diviser pour régner de la programmation dynamique ?"
    En diviser pour régner les sous-problèmes sont **indépendants** ; en PD ils
    **se chevauchent**, d'où l'intérêt de les **mémoriser**.

??? question "2. Pourquoi Fibonacci récursif naïf est-il exponentiel ?"
    Son **arbre d'appels** recalcule sans cesse les mêmes valeurs (chaque appel en
    génère deux).

??? question "3. Qu'est-ce que la mémoïsation ?"
    Stocker le résultat d'un sous-problème pour le **réutiliser** au lieu de le recalculer.

??? question "4. Quelle est la différence entre top-down et bottom-up ?"
    **Top-down** : récursif + cache, du grand vers le petit ; **bottom-up** :
    itératif, du petit vers le grand.

??? question "5. À quoi sert la sentinelle `-1` dans la version liste de Fibonacci ?"
    À marquer une case **non encore calculée** (pour savoir s'il faut calculer ou lire).

??? question "6. Quelle est la complexité en temps et en mémoire de Fibonacci bottom-up ?"
    Temps `O(n)`, mémoire `O(n)` (le tableau complet).

??? question "7. Donner la relation de récurrence du rendu de monnaie."
    `nb[0] = 0` ; `nb[s] = min(1 + nb[s − p])` pour toute pièce `p ≤ s`.

??? question "8. Pourquoi le glouton échoue-t-il sur `[1, 3, 4]` et somme `6` ?"
    Il prend `4 + 1 + 1` (3 pièces) au lieu de `3 + 3` (2 pièces) : choix local non optimal.

??? question "9. Compléter `nb` pour `[1, 2]` et somme `5`."
    `[0, 1, 1, 2, 2, 3]` → il faut **3** pièces pour rendre `5`.

??? question "10. Comment détecter qu'une somme est impossible à rendre ?"
    Si `nb[somme]` est resté à **`+∞`** : on renvoie `-1`.

??? question "11. Comment reconstruire la combinaison de pièces avec un tableau `parent` ?"
    En remontant depuis la somme finale : `p = parent[s]`, puis `s -= p`, jusqu'à `0`.

??? question "12. Sac à dos : quels sont les deux choix pour chaque objet ?"
    **Ne pas le prendre**, ou **le prendre** (sa valeur + meilleure solution pour la
    capacité restante) ; on garde le **maximum**.

??? question "13. Quelle est la complexité du sac à dos ?"
    Temps et mémoire en **`O(n × w)`**.

??? question "14. Découpe optimale : donner la relation."
    `prix_opt(L) = max( prix[i] + prix_opt(L − i) )` pour `i` de `1` à `L`.

??? question "15. Triangle de Pascal : donner la relation entre coefficients."
    `C(i, j) = C(i−1, j−1) + C(i−1, j)` (bords égaux à `1`).

---

## À retenir absolument

!!! success "Définition"
    La **programmation dynamique** résout un problème en **mémorisant** les résultats
    de sous-problèmes **qui se chevauchent**, pour ne les calculer **qu'une seule fois**.

!!! abstract "Étapes de résolution"
    état → cas de base → **relation de récurrence** → top-down ou bottom-up →
    initialiser le stockage → calculer chaque état une fois → lire la solution →
    (mémoriser les **prédécesseurs** pour reconstruire).

!!! note "Top-down vs bottom-up"
    | | **Top-down** | **Bottom-up** |
    |---|---|---|
    | Style | récursif + cache | itératif |
    | États calculés | nécessaires | tous |
    | Risque | `RecursionError` | aucun |
    | Cache réutilisable | oui | non |

!!! quote "Repères chiffrés"
    - **Rendu de monnaie** : `nb[s] = min(1 + nb[s − p])` ; temps `O(n × k)`, espace `O(n)` ;
    - **Sac à dos** : `O(n × w)` ; **Fibonacci** : `O(n)` (vs exponentiel en naïf) ;
    - **Reconstruction** : tableau **`parent`** (dernière pièce / dernier choix) remonté
      depuis l'état final, en mémoire `O(n)`.