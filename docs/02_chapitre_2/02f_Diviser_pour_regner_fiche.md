---
author: Elisabeth Le Prettre (LePrettre)
title: 02b 📜 Fiche Méthode - Diviser pour régner 
---


# La méthode diviser pour régner

!!! abstract "Fiche de révision — Terminale NSI"
    Cette fiche porte principalement sur la méthode **diviser pour régner** :
    principe (diviser / régner / combiner), exponentiation rapide, tri fusion,
    fonction fusion, recherche dichotomique récursive, complexités et exercices
    d'application du cours.

---

## 1. Objectifs du chapitre

À la fin de ce chapitre, les élèves doivent savoir :

- définir la méthode diviser pour régner ;
- expliquer les trois étapes : **diviser, régner, combiner** ;
- reconnaître un algorithme de type diviser pour régner ;
- expliquer le lien avec la récursivité ;
- comprendre l'exponentiation rapide ;
- expliquer le tri fusion ;
- expliquer le rôle de la fonction fusion ;
- comprendre la recherche dichotomique récursive ;
- comparer des complexités simples ;
- justifier pourquoi certains algorithmes sont plus efficaces ;
- répondre à des questions de type bac.

---

## 2. Définitions essentielles

!!! note "Définitions à connaître"
    **Diviser pour régner** : méthode qui consiste à résoudre un problème en le
    découpant en sous-problèmes plus petits de même nature, puis en combinant
    leurs solutions.

    **Diviser** : découper le problème initial en sous-problèmes plus petits.

    **Régner** : résoudre les sous-problèmes (souvent de façon récursive).

    **Combiner** : assembler les résultats des sous-problèmes pour obtenir la
    solution finale.

    **Sous-problème** : problème plus petit, de même nature que le problème de départ.

    **Cas de base** : situation suffisamment simple pour être résolue directement,
    sans nouvel appel récursif. C'est lui qui arrête la récursion.

    **Récursivité** : technique où une fonction s'appelle elle-même sur un problème
    plus petit.

    **Complexité** : estimation du nombre d'opérations effectuées par un algorithme
    en fonction de la taille `n` des données.

    **O(n)** : complexité linéaire — le nombre d'opérations est proportionnel à `n`.

    **O(log n)** : complexité logarithmique — la taille du problème est divisée
    par deux à chaque étape.

    **O(n log n)** : complexité du tri fusion — environ `log₂(n)` niveaux, chacun
    coûtant `O(n)`.

    **O(n²)** : complexité quadratique — typique des tris insertion et sélection.

    **Tri fusion** : tri par diviser pour régner qui coupe la liste en deux, trie
    chaque moitié puis fusionne les deux moitiés triées.

    **Fusion** : opération qui combine **deux listes déjà triées** en une seule
    liste triée.

    **Recherche dichotomique** : recherche d'une valeur dans une **liste triée**
    en divisant l'espace de recherche par deux à chaque étape.

    **Pivot** : élément de référence choisi dans le tri rapide pour séparer les
    éléments plus petits et plus grands.

---

## 3. Principe général de diviser pour régner

La méthode se déroule toujours en **trois étapes**.

**1. Diviser** — Découper le problème initial en sous-problèmes plus petits.

**2. Régner** — Résoudre les sous-problèmes. Le plus souvent, cela se fait **récursivement**.

**3. Combiner** — Assembler les résultats des sous-problèmes pour obtenir la solution finale.

!!! quote "Idée centrale"
    « Un algorithme diviser pour régner résout un problème en le remplaçant par
    des problèmes plus petits de même nature. »

!!! tip "Comment reconnaître un algorithme diviser pour régner ?"
    - le problème est **découpé** ;
    - les sous-problèmes **ressemblent** au problème initial ;
    - un **cas simple** arrête la récursion ;
    - les résultats sont **combinés** ;
    - la **taille** du problème **diminue fortement**.

---

## 4. Différence entre récursion simple et diviser pour régner

- Une **récursion simple** réduit souvent le problème de **1** à chaque appel.
- **Diviser pour régner** coupe souvent le problème **en deux**.
- Cela peut donner une **meilleure complexité**.

| Approche | Réduction du problème | Complexité |
|---|---|---|
| Puissance récursive simple | `n - 1` | O(n) |
| Exponentiation rapide | `n // 2` | O(log n) |

!!! tip "À retenir"
    - enlever **1** à chaque étape donne souvent **O(n)** ;
    - diviser par **2** donne souvent **O(log n)** ;
    - diviser en deux **puis fusionner** à chaque niveau peut donner **O(n log n)**.

---

## 5. Exponentiation rapide

**Problème :** calculer `a^n`.

### 5.1 Version itérative

- on multiplie par `a` dans une boucle ;
- la boucle s'exécute `n` fois ;
- complexité **O(n)**.

### 5.2 Version récursive simple

- cas de base : `n == 0` ;
- appel récursif : `a * exp2(n - 1, a)` ;
- complexité **O(n)**, car on diminue `n` de 1 à chaque appel.

### 5.3 Version rapide

```python
def exp3(n: int, a: float) -> float:
    if n == 0:
        return 1
    else:
        y = exp3(n // 2, a)
        if n % 2 == 0:
            return y * y
        else:
            return a * y * y
```

Explications :

- cas de base : `n == 0` ;
- appel récursif sur `n // 2` ;
- si `n` est **pair** : `a^n = a^(n/2) × a^(n/2)` ;
- si `n` est **impair** : `a^n = a × a^(n//2) × a^(n//2)` ;
- `n` est **divisé par 2** à chaque appel ;
- complexité : **O(log n)**.

!!! example "Exemple guidé : `exp3(5, a)`"
    | Appel | `n` | pair/impair | Retour |
    |---|---|---|---|
    | `exp3(0, a)` | 0 | cas de base | `1` |
    | `exp3(1, a)` | 1 | impair | `a × 1 × 1 = a` |
    | `exp3(2, a)` | 2 | pair | `a × a = a²` |
    | `exp3(5, a)` | 5 | impair | `a × a² × a² = a⁵` ✅ |

    On obtient bien `a⁵` avec seulement quelques appels (et non 5 multiplications successives).

!!! info "Ce qu'il faut savoir faire au bac"
    - expliquer le **cas pair** et le **cas impair** ;
    - justifier la **terminaison** (`n // 2` finit par atteindre `0`) ;
    - justifier la **complexité logarithmique** ;
    - **comparer** avec la version en O(n).

---

## 6. Le tri fusion

Le tri fusion est l'**algorithme central** de la méthode diviser pour régner.

**Objectif :** trier une liste.

**Principe :**

- si la liste a **0 ou 1 élément**, elle est déjà triée ;
- sinon, on la **coupe en deux** ;
- on **trie récursivement** les deux moitiés ;
- on **fusionne** les deux moitiés triées.

```python
def tri_fusion(S):
    n = len(S)
    if n < 2:
        return
    milieu = n // 2
    S1 = S[:milieu]
    S2 = S[milieu:]
    tri_fusion(S1)
    tri_fusion(S2)
    fusion(S1, S2, S)
```

Explication ligne par ligne :

- `n = len(S)` : on récupère la taille de la liste ;
- `if n < 2` : **cas de base**, une liste de 0 ou 1 élément est déjà triée ;
- `milieu = n // 2` : on calcule l'indice de séparation ;
- `S1 = S[:milieu]` : première moitié ;
- `S2 = S[milieu:]` : seconde moitié ;
- `tri_fusion(S1)` : on trie récursivement `S1` ;
- `tri_fusion(S2)` : on trie récursivement `S2` ;
- `fusion(S1, S2, S)` : on fusionne les deux moitiés triées dans `S`.

!!! abstract "Les trois étapes dans le tri fusion"
    - **Diviser** : création de `S1` et `S2` ;
    - **Régner** : appels récursifs `tri_fusion(S1)` et `tri_fusion(S2)` ;
    - **Combiner** : appel à `fusion(S1, S2, S)`.

---

## 7. La fonction fusion

La fonction `fusion` sert à **combiner deux listes déjà triées** en une seule liste triée.

```python
def fusion(S1, S2, S):
    i = 0
    j = 0

    while i < len(S1) and j < len(S2):
        if S1[i] < S2[j]:
            S[i + j] = S1[i]
            i += 1
        else:
            S[i + j] = S2[j]
            j += 1

    while i < len(S1):
        S[i + j] = S1[i]
        i += 1

    while j < len(S2):
        S[i + j] = S2[j]
        j += 1
```

Explications :

- `i` parcourt `S1` ;
- `j` parcourt `S2` ;
- `i + j` indique la position dans `S` ;
- on compare `S1[i]` et `S2[j]` ;
- on place le **plus petit** dans `S` ;
- à la fin, on **recopie les éléments restants** de la liste non vide.

!!! example "Exemple : fusionner `[1, 4, 7]` et `[2, 3, 8]`"
    | Comparaison | Plus petit placé | `S` en construction |
    |---|---|---|
    | 1 < 2 | 1 | `[1]` |
    | 4 ≥ 2 | 2 | `[1, 2]` |
    | 4 ≥ 3 | 3 | `[1, 2, 3]` |
    | 4 < 8 | 4 | `[1, 2, 3, 4]` |
    | 7 < 8 | 7 | `[1, 2, 3, 4, 7]` |
    | reste de `S2` | 8 | `[1, 2, 3, 4, 7, 8]` ✅ |

!!! warning "Pièges fréquents avec fusion"
    - oublier que `S1` et `S2` sont **déjà triées** ;
    - oublier de **recopier la fin** d'une liste ;
    - confondre `i`, `j` et `i + j` ;
    - croire que `fusion` trie **seule** des listes non triées (elle ne le fait pas).

---

## 8. Complexité du tri fusion

- à chaque niveau, la fusion parcourt **tous les éléments** : coût **O(n)** ;
- le nombre de niveaux est environ **log₂(n)** ;
- la complexité totale est donc **O(n log n)**.

| Tri | Complexité |
|---|---|
| Tri insertion | O(n²) |
| Tri sélection | O(n²) |
| **Tri fusion** | **O(n log n)** |

Pour de **grandes listes**, `O(n log n)` est nettement meilleur que `O(n²)` :
le nombre d'opérations croît beaucoup plus lentement.

!!! quote "Phrase utile au bac"
    « Le tri fusion est en O(n log n) car il y a environ log₂(n) niveaux de
    division et, à chaque niveau, la fusion parcourt l'ensemble des éléments. »

---

## 9. Recherche dichotomique récursive

**Objectif :** rechercher une valeur dans une **liste triée**.

!!! warning "Condition indispensable"
    La liste **doit être triée**, sinon la recherche dichotomique ne fonctionne pas.

**Principe :**

- calculer le **milieu** ;
- comparer l'élément du milieu avec la valeur cherchée ;
- si c'est **égal**, on a trouvé ;
- si la valeur cherchée est **plus petite**, chercher dans la **moitié gauche** ;
- si elle est **plus grande**, chercher dans la **moitié droite** ;
- si l'intervalle devient **vide**, la valeur n'est **pas présente**.

!!! abstract "Les trois étapes"
    - **Diviser** : on coupe l'espace de recherche en deux ;
    - **Régner** : on cherche dans une **seule** moitié ;
    - **Combiner** : on renvoie le résultat de l'appel récursif.

**Complexité :**

- on divise le nombre d'éléments par **deux** à chaque étape ;
- complexité : **O(log n)**.

!!! warning "Erreurs fréquentes"
    - oublier que la liste doit être **triée** ;
    - mal calculer le **milieu** ;
    - mal mettre à jour les **bornes** ;
    - oublier le cas où la valeur **n'est pas présente**.

---

## 10. Autres applications du cours

### 10.1 Somme d'un tableau par division

- couper le tableau en deux ;
- calculer la somme de chaque moitié ;
- additionner les résultats.

### 10.2 Recherche du minimum et du maximum

- diviser le tableau ;
- chercher le min et le max dans chaque moitié ;
- combiner les résultats.

!!! note
    La complexité reste **O(n)** car il faut examiner tous les éléments.

### 10.3 Tri rapide

- choix d'un **pivot** ;
- séparation des éléments **inférieurs** et **supérieurs** au pivot ;
- appels récursifs sur les sous-listes ;
- complexité **moyenne O(n log n)** ;
- **pire cas O(n²)**.

### 10.4 Rotation récursive d'image

- l'image est divisée en **quadrants** ;
- les quadrants sont traités **récursivement** ;
- ils sont **recombinés** pour obtenir la rotation.

---

## 11. Méthodes bac à maîtriser

### Méthode 1 — Reconnaître diviser pour régner

1. Repérer la **découpe** du problème.
2. Identifier les **sous-problèmes**.
3. Vérifier qu'ils sont de **même nature** que le problème initial.
4. Identifier le **cas de base**.
5. Identifier l'étape de **combinaison**.

### Méthode 2 — Expliquer un algorithme diviser pour régner

Utiliser la structure :

- **Diviser** : …
- **Régner** : …
- **Combiner** : …

!!! example "Exemple pour le tri fusion"
    - **Diviser** : on coupe la liste en deux ;
    - **Régner** : on trie les deux moitiés ;
    - **Combiner** : on fusionne les deux listes triées.

### Méthode 3 — Justifier une complexité logarithmique

!!! quote "Formulation utile"
    « La complexité est logarithmique car la taille du problème est divisée par
    deux à chaque étape. »

À appliquer à : **exponentiation rapide** et **recherche dichotomique**.

### Méthode 4 — Justifier la complexité du tri fusion

!!! quote "Formulation utile"
    « Le tri fusion est en O(n log n) car il y a environ log₂(n) niveaux de
    division et chaque niveau nécessite une fusion linéaire en O(n). »

### Méthode 5 — Compléter un code de tri fusion

1. repérer le **cas de base** ;
2. calculer le **milieu** ;
3. créer les **deux sous-listes** ;
4. appeler récursivement `tri_fusion` ;
5. appeler `fusion`.

### Méthode 6 — Comprendre la fonction fusion

1. suivre les indices `i` et `j` ;
2. comparer les éléments courants ;
3. placer le **plus petit** ;
4. avancer le **bon indice** ;
5. recopier les éléments restants.

---

## 12. Erreurs fréquentes à éviter

!!! danger "À ne pas faire"
    - confondre **récursion simple** et **diviser pour régner** ;
    - oublier l'étape de **combinaison** ;
    - oublier le **cas de base** ;
    - croire que **toute récursion** est du diviser pour régner ;
    - croire que la recherche dichotomique fonctionne sur une liste **non triée** ;
    - oublier de **recopier les éléments restants** dans `fusion` ;
    - croire que `fusion` **trie** des listes non triées ;
    - confondre **O(log n)** et **O(n log n)** ;
    - confondre **O(n log n)** et **O(n²)** ;
    - mal interpréter le rôle de `n // 2`.

---

## 13. Questions type bac avec réponses

!!! tip "Conseil d'utilisation"
    Lis la question, cherche la réponse de tête, **puis** déplie la correction.

??? question "1. Définir la méthode diviser pour régner."
    C'est une méthode qui résout un problème en le découpant en sous-problèmes
    plus petits **de même nature**, puis en **combinant** leurs solutions pour
    obtenir la solution finale.

??? question "2. Donner les trois étapes de cette méthode."
    **Diviser** (découper le problème), **Régner** (résoudre les sous-problèmes,
    souvent récursivement) et **Combiner** (assembler les résultats).

??? question "3. Pourquoi l'exponentiation rapide est-elle plus efficace que la version récursive simple ?"
    La version simple diminue `n` de 1 à chaque appel (`n - 1`), ce qui donne
    O(n). L'exponentiation rapide divise `n` par 2 à chaque appel (`n // 2`), ce
    qui donne O(log n) : beaucoup moins d'appels.

??? question "4. Donner la complexité de l'exponentiation rapide."
    **O(log n)**, car `n` est divisé par 2 à chaque appel récursif.

??? question "5. Expliquer le principe du tri fusion."
    Si la liste a 0 ou 1 élément, elle est déjà triée. Sinon on la coupe en deux,
    on trie récursivement chaque moitié, puis on fusionne les deux moitiés triées.

??? question "6. Identifier les étapes diviser, régner, combiner dans le tri fusion."
    **Diviser** : création de `S1` et `S2`. **Régner** : `tri_fusion(S1)` et
    `tri_fusion(S2)`. **Combiner** : `fusion(S1, S2, S)`.

??? question "7. Expliquer le rôle de la fonction fusion."
    Elle **combine deux listes déjà triées** en une seule liste triée, en
    comparant les éléments courants et en plaçant à chaque fois le plus petit.

??? question "8. Donner la complexité du tri fusion."
    **O(n log n)** : environ log₂(n) niveaux de division, chacun nécessitant une
    fusion en O(n).

??? question "9. Comparer tri fusion, tri insertion et tri sélection."
    Tri insertion : O(n²). Tri sélection : O(n²). Tri fusion : O(n log n), donc
    plus efficace que les deux autres pour de grandes listes.

??? question "10. Pourquoi la recherche dichotomique est-elle en O(log n) ?"
    Parce qu'on divise le nombre d'éléments à examiner par deux à chaque étape.

??? question "11. Pourquoi la recherche dichotomique nécessite-t-elle une liste triée ?"
    Parce qu'on déduit la moitié à explorer en comparant la valeur cherchée à
    l'élément du milieu : ce raisonnement n'est valable que si la liste est triée.

??? question "12. Repérer une erreur dans une fonction fusion."
    Exemples d'erreurs : oublier de recopier la fin d'une liste après la première
    boucle, confondre `i + j` avec `i` ou `j`, ou supposer que les listes ne sont
    pas triées.

??? question "13. Compléter un code de tri fusion."
    Il faut : le cas de base `if n < 2: return`, `milieu = n // 2`, `S1 = S[:milieu]`,
    `S2 = S[milieu:]`, les appels `tri_fusion(S1)` et `tri_fusion(S2)`, puis
    `fusion(S1, S2, S)`.

??? question "14. Expliquer la différence entre O(n), O(log n), O(n log n) et O(n²)."
    **O(n)** : on parcourt les éléments une fois. **O(log n)** : on divise le
    problème par deux à chaque étape. **O(n log n)** : log₂(n) niveaux coûtant
    chacun O(n). **O(n²)** : croissance quadratique, beaucoup plus lente pour de
    grandes données.

??? question "15. Reconnaître un algorithme diviser pour régner dans un exemple."
    Vérifier que le problème est découpé, que les sous-problèmes sont de même
    nature, qu'il existe un cas de base, que la taille diminue fortement et que
    les résultats sont combinés.

---

## 14. À retenir absolument

!!! success "Mini-fiche finale"
    - **diviser pour régner** = **diviser, régner, combiner** ;
    - la méthode est souvent **récursive** ;
    - elle consiste à résoudre des **sous-problèmes plus petits** ;
    - **exponentiation rapide** : O(log n) ;
    - **recherche dichotomique** : O(log n) ;
    - **tri fusion** : O(n log n) ;
    - **tri insertion** et **tri sélection** : O(n²) ;
    - une liste de **taille 0 ou 1** est déjà triée ;
    - **fusion** combine deux listes **déjà triées** ;
    - la **recherche dichotomique exige une liste triée** ;
    - au bac, savoir identifier : **découpe, sous-problèmes, cas de base, combinaison et complexité**.

!!! quote "Formulations utiles pour rédiger au bac"
    - « L'algorithme suit la méthode diviser pour régner car… »
    - « La phase **diviser** consiste à… »
    - « La phase **régner** consiste à… »
    - « La phase **combiner** consiste à… »
    - « La complexité est logarithmique car… »
    - « Le tri fusion est en O(n log n) car… »
