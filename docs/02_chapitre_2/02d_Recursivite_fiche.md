---
author: Elisabeth Le Prettre (LePrettre)
title: 02a 📜 Fiche Méthode - Récursivité
---

# La récursivité

!!! abstract "Fiche de révision — Terminale NSI"
    Cette fiche porte **uniquement sur la récursivité** : cas de base, cas récursif,
    condition d'arrêt, terminaison, pile d'exécution, déroulé des appels, et
    comparaison itératif / récursif. Les autres usages de la récursivité (diviser
    pour régner, tri fusion, exponentiation rapide, recherche dichotomique) font
    l'objet d'une fiche séparée.

---

## 1. Objectifs du chapitre

À la fin de ce chapitre, les élèves doivent savoir :

- définir une fonction récursive ;
- identifier le **cas de base** ;
- identifier le **cas récursif** ;
- expliquer la **condition d'arrêt** ;
- expliquer pourquoi une fonction récursive **termine** ;
- **dérouler** les appels récursifs à la main ;
- comprendre la **pile d'exécution** ;
- comparer une version **itérative** et une version **récursive** ;
- repérer une **récursion infinie** ;
- expliquer pourquoi une récursion peut être élégante mais parfois inefficace ;
- répondre à des questions de type bac sur la récursivité.

---

## 2. Définitions essentielles

!!! note "Définitions à connaître"
    **Fonction récursive** : fonction qui s'appelle elle-même.
    *Ex. : `factorielle_r` appelle `factorielle_r`.*

    **Appel récursif** : instruction par laquelle la fonction se rappelle
    elle-même, sur un problème plus petit.

    **Cas de base** : cas le plus simple, résolu **directement**, sans nouvel
    appel récursif. *Ex. : `n == 0`.*

    **Condition d'arrêt** : test qui déclenche le cas de base et **stoppe** la
    récursion.

    **Cas récursif** : cas où la fonction se rappelle elle-même avec des
    paramètres plus simples.

    **Pile d'exécution** : structure qui **empile** les appels en attente, puis
    les **dépile** au fur et à mesure des retours.

    **Descente des appels** : phase où les appels récursifs s'enchaînent jusqu'au
    cas de base.

    **Remontée des résultats** : phase où les résultats remontent, du cas de base
    vers l'appel initial.

    **Terminaison** : garantie que la fonction finit par s'arrêter (elle atteint
    le cas de base).

    **Récursion infinie** : fonction qui ne s'arrête jamais, car elle n'atteint
    jamais le cas de base.

    **RecursionError** : erreur levée par Python lorsque le nombre d'appels
    récursifs dépasse la limite autorisée.

    **Version itérative** : version utilisant une **boucle** (`for`, `while`) au
    lieu d'appels récursifs.

    **Version récursive** : version reposant sur des **appels de la fonction à
    elle-même**.

---

## 3. Méthode générale pour écrire une fonction récursive

1. Comprendre **ce que la fonction doit renvoyer**.
2. Trouver **le cas le plus simple**.
3. Écrire **le cas de base**.
4. Trouver **comment réduire le problème**.
5. Écrire **l'appel récursif**.
6. Vérifier que l'appel récursif **rapproche du cas de base**.
7. **Tester** sur un petit exemple.
8. Vérifier la différence entre `return` et `print`.

Modèle général :

```python
def fonction(arguments):
    if condition_arret:
        return valeur_de_base
    else:
        return fonction(arguments_plus_simples)
```

!!! quote "Formulation bac"
    « Le cas de base permet d'arrêter les appels récursifs. Le cas récursif appelle
    la même fonction avec des paramètres plus simples. »

---

## 4. Méthode pour analyser une fonction récursive

1. Lire la **spécification**.
2. Repérer les **paramètres**.
3. Repérer la **condition d'arrêt**.
4. Repérer ce qui est **retourné dans le cas de base**.
5. Repérer **l'appel récursif**.
6. Observer **comment les paramètres changent**.
7. Vérifier qu'on **se rapproche du cas de base**.
8. **Dérouler** les appels à la main.
9. **Remonter** les résultats.

!!! quote "Phrase type"
    « À chaque appel, la valeur de `…` diminue. Elle finit donc par atteindre `…`,
    qui est le cas de base. »

---

## 5. Exemple 1 : le décompte récursif

**Principe :**

- afficher les nombres de `n` à `1` ;
- s'arrêter à `0` ;
- afficher `"fin"` au cas de base.

```python
def decompte_r(n):
    if n == 0:
        print("fin")
        return
    print(n)
    decompte_r(n - 1)
```

Explications :

- **cas de base** : `n == 0` → on affiche `"fin"` et on s'arrête ;
- **appel récursif** : `decompte_r(n - 1)` ;
- la fonction **termine** car `n` diminue de 1 à chaque appel et atteint `0`.

!!! example "Déroulé de `decompte_r(3)`"
    | Appel | Affichage |
    |---|---|
    | `decompte_r(3)` | `3` |
    | `decompte_r(2)` | `2` |
    | `decompte_r(1)` | `1` |
    | `decompte_r(0)` | `fin` |

**Version itérative** équivalente :

```python
def decompte_i(n):
    for i in range(n, 0, -1):
        print(i)
    print("fin")
```

---

## 6. Exemple 2 : la puissance récursive

**Objectif :** calculer `x^n` sans utiliser `**`.

```python
def puissance(x, n):
    if n == 0:
        return 1
    return x * puissance(x, n - 1)
```

Explications :

- **cas de base** : `n == 0` ;
- valeur retournée dans le cas de base : `1` ;
- **cas récursif** : `x * puissance(x, n - 1)` ;
- `n - 1` **rapproche du cas de base** (`n` finit par atteindre `0`).

!!! example "Déroulé de `puissance(2, 4)`"
    **Descente des appels**
    ```
    puissance(2, 4) = 2 * puissance(2, 3)
    puissance(2, 3) = 2 * puissance(2, 2)
    puissance(2, 2) = 2 * puissance(2, 1)
    puissance(2, 1) = 2 * puissance(2, 0)
    puissance(2, 0) = 1          ← cas de base
    ```
    **Remontée des résultats**
    ```
    puissance(2, 1) = 2 * 1 = 2
    puissance(2, 2) = 2 * 2 = 4
    puissance(2, 3) = 2 * 4 = 8
    puissance(2, 4) = 2 * 8 = 16   ✅
    ```

!!! info "Ce qu'il faut savoir faire au bac"
    - identifier le **cas de base** ;
    - **compléter** le code ;
    - expliquer la **terminaison** ;
    - **calculer** un résultat à la main (descente puis remontée).

---

## 7. Exemple 3 : récursion sans cas d'arrêt

```python
def f(n):
    return 1 + f(n + 1)
```

Explications :

- la fonction **n'a pas de cas de base** ;
- elle s'appelle **indéfiniment** ;
- Python finit par produire une erreur **`RecursionError`**.

!!! note "Limite de récursion"
    Python limite le nombre d'appels récursifs empilés. Quand cette limite est
    dépassée, l'exécution s'arrête avec une `RecursionError`. Ici, `n + 1`
    **éloigne** du cas de base au lieu de s'en rapprocher : la pile grossit
    jusqu'à saturation.

!!! danger "Erreurs à éviter"
    - oublier la **condition d'arrêt** ;
    - écrire un appel récursif qui **éloigne** du cas de base ;
    - croire qu'**augmenter la limite de récursion** résout le problème (cela ne
      fait que repousser l'erreur).

---

## 8. Exemple 4 : multiplication du paysan russe

**Objectif :** multiplier deux entiers à l'aide de divisions par 2, de
multiplications par 2 et d'additions.

```python
def multiply_r(x, y):
    if x <= 0:
        return 0
    elif x % 2 == 0:
        return multiply_r(x // 2, y * 2)
    else:
        return multiply_r(x // 2, y * 2) + y
```

Explications :

- **cas de base** : `x <= 0` → on renvoie `0` ;
- **cas pair** (`x % 2 == 0`) : on continue avec `x // 2` et `y * 2` ;
- **cas impair** : on fait de même, mais on **ajoute `y`** ;
- `x // 2` **réduit** `x` à chaque appel (rôle : rapprocher du cas de base) ;
- `y * 2` **double** `y` pour compenser la division de `x` ;
- on **ajoute `y` quand `x` est impair** car la division entière « oublie » alors
  une unité de `x` qu'il faut récupérer.

!!! example "Exemple : `multiply_r(105, 253)`"
    En appliquant la règle (diviser `x` par 2, doubler `y`, ajouter `y` aux étapes
    impaires), on obtient bien **105 × 253 = 26 565**.

!!! warning "Pièges fréquents"
    - oublier le `+ y` dans le **cas impair** ;
    - utiliser `/` au lieu de `//` (la division entière est indispensable) ;
    - ne pas comprendre pourquoi `x` doit **diminuer** pour assurer la terminaison.

---

## 9. Exemple 5 : factorielle

**Définition :**

```
n! = n × (n - 1) × … × 1
0! = 1
```

```python
def factorielle_r(n):
    if n == 1 or n == 0:
        return 1
    return n * factorielle_r(n - 1)
```

Explications :

- **cas de base** : `n == 1` ou `n == 0` → renvoie `1` ;
- **cas récursif** : `n * factorielle_r(n - 1)` ;
- **terminaison** : `n` diminue de 1 à chaque appel et atteint le cas de base.

!!! example "Déroulé de `factorielle_r(4)`"
    **Descente**
    ```
    factorielle_r(4) = 4 * factorielle_r(3)
    factorielle_r(3) = 3 * factorielle_r(2)
    factorielle_r(2) = 2 * factorielle_r(1)
    factorielle_r(1) = 1          ← cas de base
    ```
    **Remontée**
    ```
    factorielle_r(2) = 2 * 1 = 2
    factorielle_r(3) = 3 * 2 = 6
    factorielle_r(4) = 4 * 6 = 24   ✅
    ```

!!! note "Récursif vs itératif"
    - **récursif** : proche de la définition mathématique, très lisible ;
    - **itératif** : souvent plus efficace en Python (pas d'empilement d'appels).

---

## 10. Exemple 6 : les tours de Hanoï

**Problème :** trois tours (piques), des disques à déplacer en respectant les
règles du jeu.

**Raisonnement récursif :**

1. déplacer les `n-1` disques vers la tour **intermédiaire** ;
2. déplacer le **plus grand disque** vers la tour d'**arrivée** ;
3. déplacer les `n-1` disques vers la tour d'**arrivée**.

```python
def hanoi(n, a="A", b="B", c="C"):
    if n == 0:
        return None
    hanoi(n - 1, a, c, b)
    print(f"Déplacer le disque {n} de la pique {a} vers la pique {c}.")
    hanoi(n - 1, b, a, c)
```

Explications :

- **cas de base** : `n == 0` → rien à déplacer, on s'arrête ;
- **deux appels récursifs** : avant et après le déplacement du grand disque ;
- les paramètres `a`, `b`, `c` désignent les tours **départ**, **intermédiaire**
  et **arrivée** ;
- les tours **changent de rôle** d'un appel à l'autre : ce qui est « arrivée » à
  un niveau devient « intermédiaire » au niveau suivant, etc.

---

## 11. Exemple 7 : Fibonacci récursif et itératif

**Définition :**

```
F0 = 0
F1 = 1
Fn = F(n-1) + F(n-2)
```

**Version récursive (naïve) :**

```python
def fib(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fib(n - 1) + fib(n - 2)
```

**Version itérative :**

```python
def fib_iter(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a
```

!!! warning "Pourquoi la version récursive naïve est inefficace"
    - elle **recalcule plusieurs fois** les mêmes valeurs ;
    - elle crée un **arbre d'appels très grand** ;
    - certains résultats sont **recalculés inutilement**.

!!! example "Exemple avec `fib(5)`"
    `fib(5)` appelle `fib(4)` et `fib(3)` ; `fib(4)` appelle `fib(3)` et `fib(2)`…
    `fib(3)` et `fib(2)` sont donc **calculés plusieurs fois**. Résultat :
    `F5 = 5` (suite : 0, 1, 1, 2, 3, 5), mais au prix de nombreux appels redondants.

!!! quote "Conclusion importante"
    « La récursivité peut être élégante, mais elle n'est pas toujours efficace. »

---

## 12. Exercices récursifs classiques du cours

Pour chacun : **objectif**, **idée récursive**, **cas de base**, **cas récursif**,
**piège à éviter**.

??? example "Somme des n premiers entiers"
    - **Objectif** : calculer `1 + 2 + … + n`.
    - **Idée** : `somme(n) = n + somme(n - 1)`.
    - **Cas de base** : `n == 0` → `0`.
    - **Cas récursif** : `n + somme(n - 1)`.
    - **Piège** : oublier le cas de base, ou faire augmenter `n`.

??? example "Palindrome"
    - **Objectif** : vérifier qu'une chaîne se lit pareil dans les deux sens.
    - **Idée** : comparer le **premier** et le **dernier** caractère, puis recommencer
      sur l'intérieur.
    - **Cas de base** : chaîne **vide** ou de **taille 1** → palindrome.
    - **Cas récursif** : premier == dernier **et** l'intérieur est un palindrome.
    - **Piège** : oublier le cas de la chaîne vide ou de taille 1.

??? example "Nombre d'adhérents"
    - **Objectif** : compter des éléments dans une structure traitée récursivement.
    - **Idée** : compter l'élément courant, puis ajouter le décompte du reste.
    - **Cas de base** : structure vide → `0`.
    - **Cas récursif** : `1 + compter(reste)`.
    - **Piège** : ne pas réduire la structure à chaque appel.

??? example "Suite de Syracuse"
    - **Objectif** : calculer/afficher les termes jusqu'à atteindre `1`.
    - **Idée** : si pair → `n // 2`, si impair → `3 * n + 1`, puis recommencer.
    - **Cas de base** : `n == 1`.
    - **Cas récursif** : appel sur le terme suivant.
    - **Piège** : utiliser `/` au lieu de `//` pour le cas pair.

??? example "PGCD"
    - **Objectif** : calculer le plus grand commun diviseur.
    - **Idée** : `pgcd(a, b) = pgcd(b, a % b)`.
    - **Cas de base** : `b == 0` → `a`.
    - **Cas récursif** : `pgcd(b, a % b)`.
    - **Piège** : inverser les arguments, ou oublier le cas `b == 0`.

??? example "Nombre de chiffres"
    - **Objectif** : compter les chiffres d'un entier.
    - **Idée** : un chiffre de moins à chaque division entière par 10.
    - **Cas de base** : `n < 10` → `1`.
    - **Cas récursif** : `1 + nb_chiffres(n // 10)`.
    - **Piège** : oublier le cas des nombres à un seul chiffre.

??? example "Recherche dans une chaîne"
    - **Objectif** : déterminer si un caractère/motif est présent.
    - **Idée** : tester le premier caractère, puis chercher dans le reste.
    - **Cas de base** : chaîne vide → absent.
    - **Cas récursif** : trouvé en tête **ou** présent dans le reste.
    - **Piège** : ne pas réduire la chaîne à chaque appel.

??? example "Recherche du plus petit élément d'une liste"
    - **Objectif** : trouver le minimum d'une liste.
    - **Idée** : comparer le premier élément au minimum du reste.
    - **Cas de base** : liste à **un** élément → cet élément.
    - **Cas récursif** : `min(premier, mini(reste))`.
    - **Piège** : oublier le cas de la liste à un seul élément.

??? example "Somme de listes imbriquées"
    - **Objectif** : additionner tous les nombres, même dans des sous-listes.
    - **Idée** : si l'élément est une liste, sommer récursivement ; sinon l'ajouter.
    - **Cas de base** : élément qui n'est pas une liste → l'élément lui-même.
    - **Cas récursif** : somme des sommes des sous-éléments.
    - **Piège** : ne pas distinguer un nombre d'une sous-liste.

??? example "Duplication d'un élément"
    - **Objectif** : produire un élément répété plusieurs fois.
    - **Idée** : ajouter une occurrence, puis dupliquer le reste.
    - **Cas de base** : `n == 0` → rien (liste/chaîne vide).
    - **Cas récursif** : élément + duplication `n - 1` fois.
    - **Piège** : oublier de décrémenter le compteur.

??? example "Extraction des n premiers éléments"
    - **Objectif** : renvoyer les `n` premiers éléments d'une liste.
    - **Idée** : prendre le premier, puis extraire `n - 1` éléments du reste.
    - **Cas de base** : `n == 0` → liste vide.
    - **Cas récursif** : `[premier] + extraire(reste, n - 1)`.
    - **Piège** : oublier le cas `n == 0`.

??? example "Renversement d'une liste"
    - **Objectif** : inverser l'ordre des éléments.
    - **Idée** : renverser le reste, puis placer le premier élément à la fin.
    - **Cas de base** : liste vide → liste vide.
    - **Cas récursif** : `renverser(reste) + [premier]`.
    - **Piège** : placer le premier élément au mauvais endroit.

---

## 13. Méthodes bac à maîtriser

### Méthode 1 — Identifier le cas de base

- chercher le **cas le plus simple** ;
- vérifier qu'il **ne nécessite plus d'appel récursif** ;
- écrire le `return` correspondant.

Exemples : `n == 0` pour `puissance` ; `n == 0` ou `n == 1` pour `factorielle` ;
chaîne vide ou de taille 1 pour un palindrome.

### Méthode 2 — Identifier le cas récursif

- comprendre **comment réduire** le problème ;
- appeler la **même fonction** sur un problème plus petit ;
- **combiner** le résultat si nécessaire.

### Méthode 3 — Dérouler les appels

- écrire les **appels successifs** (descente) ;
- aller jusqu'au **cas de base** ;
- **remonter** les résultats.

*À pratiquer avec `puissance(2, 4)` ou `factorielle_r(4)` (voir §6 et §9).*

### Méthode 4 — Justifier la terminaison

!!! quote "Phrase modèle"
    « La fonction termine car, à chaque appel récursif, la valeur de `…` diminue
    strictement et finit par atteindre le cas de base `…`. »

### Méthode 5 — Prévoir un affichage

- si `print` est **avant** l'appel récursif → l'affichage a lieu **à la descente** ;
- si `print` est **après** l'appel récursif → l'affichage a lieu **à la remontée**.

### Méthode 6 — Compléter un code à trous

- lire la **consigne** ;
- chercher le **cas de base** ;
- chercher **ce qui diminue** ;
- écrire **l'appel récursif** ;
- vérifier le **type retourné**.

---

## 14. Erreurs fréquentes à éviter

!!! danger "À ne pas faire"
    - oublier le **cas de base** ;
    - écrire une **condition d'arrêt impossible** ;
    - faire **augmenter** le paramètre au lieu de le diminuer ;
    - confondre `return` et `print` ;
    - croire qu'une fonction récursive est **toujours plus rapide** ;
    - ne pas comprendre la **remontée** des appels ;
    - oublier qu'un appel récursif **attend un résultat** ;
    - écrire une fonction qui ne fonctionne que pour **certains cas** ;
    - ne pas **tester** sur un petit exemple.

---

## 15. Questions type bac avec réponses

!!! tip "Conseil d'utilisation"
    Lis la question, cherche la réponse de tête, **puis** déplie la correction.

??? question "1. Qu'est-ce qu'une fonction récursive ?"
    Une fonction qui s'appelle elle-même, sur un problème plus petit, jusqu'à
    atteindre un cas de base.

??? question "2. Quels sont les deux éléments indispensables d'une fonction récursive ?"
    Un **cas de base** (qui arrête la récursion) et un **cas récursif** (qui
    rappelle la fonction sur un problème plus petit).

??? question "3. Quel est le cas de base de `puissance(x, n)` ?"
    `n == 0`, qui renvoie `1`.

??? question "4. Dérouler `puissance(2, 3)`."
    `puissance(2,3) = 2 * puissance(2,2) = 2 * (2 * puissance(2,1)) =
    2 * 2 * (2 * puissance(2,0)) = 2 * 2 * 2 * 1 = 8`.

??? question "5. Dérouler `factorielle_r(4)`."
    `4 * factorielle_r(3) = 4 * 3 * factorielle_r(2) = 4 * 3 * 2 * factorielle_r(1)
    = 4 * 3 * 2 * 1 = 24`.

??? question "6. Pourquoi une fonction sans cas de base provoque-t-elle une erreur ?"
    Sans cas de base, les appels récursifs ne s'arrêtent jamais : la pile
    d'exécution se remplit jusqu'à dépasser la limite, ce qui provoque une
    `RecursionError`.

??? question "7. Quelle est la différence entre `return` et `print` dans une fonction récursive ?"
    `return` **renvoie** une valeur à l'appelant (qui peut la réutiliser), tandis
    que `print` ne fait qu'**afficher** : il ne transmet aucune valeur à la
    remontée des appels.

??? question "8. Pourquoi Fibonacci récursif naïf est-il inefficace ?"
    Parce qu'il recalcule plusieurs fois les mêmes valeurs, ce qui engendre un
    arbre d'appels très grand avec de nombreux calculs redondants.

??? question "9. Comment justifier la terminaison d'une fonction récursive ?"
    En montrant qu'à chaque appel un paramètre diminue strictement et finit par
    atteindre le cas de base. *Ex. : « `n` diminue de 1 à chaque appel et atteint
    `0` ». *

??? question "10. Repérer l'erreur dans une fonction récursive mal écrite."
    Vérifier d'abord la présence d'un cas de base, puis que l'appel récursif
    **rapproche** du cas de base (paramètre qui diminue), et enfin qu'on utilise
    bien `return` quand une valeur doit remonter.

---

## 16. À retenir absolument

!!! success "Mini-fiche finale"
    - une fonction récursive **s'appelle elle-même** ;
    - elle doit avoir un **cas de base** ;
    - elle doit avoir un **cas récursif** ;
    - l'appel récursif doit **rapprocher du cas de base** ;
    - la **pile d'exécution** empile les appels puis les dépile ;
    - savoir distinguer **descente** et **remontée** ;
    - récursif **ne veut pas dire** plus efficace ;
    - **Fibonacci récursif naïf** est coûteux ;
    - au bac, toujours identifier : **entrées, sortie, cas de base, cas récursif,
      paramètres modifiés, terminaison et résultat**.

!!! quote "Formulations utiles pour rédiger au bac"
    - « Le cas de base est atteint lorsque… »
    - « À chaque appel, la valeur de `…` diminue… »
    - « La fonction termine car… »
    - « L'appel récursif permet de traiter un problème plus petit… »
    - « La récursivité est élégante mais peut être coûteuse si elle provoque des
      appels redondants. »
