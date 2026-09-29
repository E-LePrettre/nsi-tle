---
author: Elisabeth Le Prettre (LePrettre)
title: 12 📜 Fiche Méthode - Algorithme de Boyer - Moore
---

# Recherche textuelle et algorithme de Boyer-Moore

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur la recherche d'un motif dans un texte :
    méthodes Python, **recherche naïve**, et algorithme de **Boyer-Moore** (comparaison
    depuis la fin + table de décalages).

---

## 1. Vocabulaire

| Terme | Définition |
|---|---|
| **Texte** | Chaîne dans laquelle on **cherche**. |
| **Motif / clé** | Chaîne **recherchée**. |
| **Occurrence** | Une **apparition** du motif dans le texte. |
| **Indice** | **Position** d'un caractère dans le texte. |
| **Fenêtre** | Portion du texte **alignée** avec le motif. |
| **Comparaison** | Test caractère par caractère. |
| **Discordance** | Deux caractères **différents** (échec de comparaison). |
| **Décalage** | **Déplacement** de la fenêtre dans le texte. |
| **Prétraitement** | Calcul **préalable** (ici, la table de décalages). |

!!! note "Repère essentiel"
    ```
    texte[i:i+len(motif)] == motif
    ```
    signifie que le **motif apparaît à l'indice `i`**.

---

## 2. Méthodes Python

| Méthode | Si trouvé | Si absent |
|---|---|---|
| `index()` | premier indice | **`ValueError`** |
| `find()` | premier indice | **`-1`** |

!!! note "Précisions"
    - **`try / except ValueError`** : permet de renvoyer `None` au lieu de planter ;
    - **`find(motif, debut)`** : reprend la recherche **à partir** d'une position ;
    - bien distinguer **`None`** (absence neutre), **`-1`** (code de `find`) et une
      **exception** (`index`).

```python
def chercher(texte, motif):
    try:
        return texte.index(motif)
    except ValueError:
        return None
```

---

## 3. Compter les occurrences

```python
def compter(texte, motif):
    n = 0
    pos = texte.find(motif)
    while pos != -1:
        n += 1
        pos = texte.find(motif, pos + 1)   # reprendre après la position
    return n
```

1. `pos = texte.find(motif)` ;
2. **tant que** `pos != -1` ;
3. **incrémenter** le compteur ;
4. rechercher **à partir de `pos + 1`**.

!!! tip "Points clés"
    La **boucle est indispensable** pour trouver **toutes** les occurrences, et
    reprendre à **`pos + 1`** (et non `pos + len(motif)`) autorise les
    **chevauchements**.

---

## 4. Recherche naïve

- tester **toutes les positions** possibles ;
- comparer **de gauche à droite** ;
- **décaler de 1** après un échec ;
- renvoyer le **premier indice** trouvé, ou **`-1`**.

```python
def recherche_naive(texte, motif):
    N = len(texte)
    n = len(motif)
    for i in range(N - n + 1):              # positions possibles
        j = 0
        while j < n and texte[i+j] == motif[j]:
            j += 1
        if j == n:                          # tout le motif a correspondu
            return i
    return -1
```

!!! note "Les variables"
    - **`i`** : début de la **fenêtre** dans le texte ;
    - **`j`** : position dans le **motif** ;
    - **`i + j`** : caractère **comparé dans le texte**.

!!! note "Complexité"
    `N − n + 1` positions, au plus `n` comparaisons chacune → coût `(N − n + 1) × n`.
    **Ordre de grandeur retenu dans le cours : `O(n²)`.**

---

## 5. Boyer-Moore

!!! abstract "Principe"
    - **comparer depuis la fin** du motif ;
    - **exploiter une discordance** pour sauter plusieurs positions ;
    - effectuer un **saut** au lieu d'avancer systématiquement de 1.

| Situation à la discordance | Saut |
|---|---|
| Caractère **absent** du motif | saut **maximal** : `len(motif)` |
| Caractère **présent** | saut donné par la **table de décalages** |
| Plusieurs caractères déjà **égaux** | **poursuivre** la comparaison vers la **gauche** |

---

## 6. Table de décalages

```python
def pre_traitement(mot):
    n = len(mot)
    table = {}
    for i in range(n - 1):          # tous les caractères SAUF le dernier
        table[mot[i]] = n - 1 - i   # décalage
    return table
```

- dictionnaire **`caractère → décalage`** ;
- on parcourt les caractères **sauf le dernier** ;
- décalage **`n − 1 − i`** ;
- si une lettre **apparaît plusieurs fois**, la **dernière valeur écrite** est conservée ;
- un caractère **absent** du dictionnaire → saut de **`n`**.

!!! example "Résultats du cours"
    - `"dab"` → `{'d': 2, 'a': 1}` ;
    - `"maman"` → `{'m': 2, 'a': 1}` (les répétitions écrasent : `m` puis `a` gardent
      la **dernière** valeur).

??? question "Exercice : construire la table de `\"coco\"`"
    `n = 4`. `i=0 : 'c' → 3` ; `i=1 : 'o' → 2` ; `i=2 : 'c' → 1` (écrase) ; le dernier
    `'o'` est ignoré.
    **Table : `{'c': 1, 'o': 2}`.**

---

## 7. Algorithme du cours

```python
def recherche_boyer(texte, motif):
    N = len(texte)
    n = len(motif)
    table = pre_traitement(motif)          # 1. N, n et la table
    i = n - 1                              # 2. i sous la fin du motif
    while i < N:
        c = texte[i]                       # 3. caractère sous la fin
        if c == motif[n-1]:                # 4. correspond au dernier caractère
            if texte[i-n+1:i+1] == motif:  #    vérifier la fenêtre complète
                return True
            i += 1                         #    sinon, avancer de 1
        elif c in table:                   # 5. caractère dans la table
            i += table[c]                  #    appliquer son décalage
        else:                              # 6. sinon
            i += n                         #    avancer de n
    return False                           # 7. motif absent
```

!!! info "Version simplifiée"
    Il s'agit d'une **version simplifiée** de Boyer-Moore : elle renvoie un **booléen**
    (présence) et ne gère pas toutes les optimisations de l'algorithme complet.

!!! example "Déroulé : motif `\"dab\"` dans `\"abcdab\"`"
    Table de `"dab"` = `{'d': 2, 'a': 1}`, dernier caractère `'b'`. `N = 6`, `n = 3`.

    | `i` | `texte[i]` | Analyse | Action |
    |---|---|---|---|
    | 2 | `c` | ≠ `'b'`, absent de la table | `i += 3` → `i = 5` |
    | 5 | `b` | = `'b'` → fenêtre `texte[3:6] = "dab"` ✔ | **trouvé** (indice 3) |

---

## 8. Comparaison

| Critère | Naïf | Boyer-Moore |
|---|---|---|
| Sens de comparaison | gauche → droite | **depuis la fin** |
| Décalage après échec | toujours 1 | **variable** |
| Prétraitement | non | **oui** (table) |
| Résultat (code du cours) | indice ou `-1` | **booléen** |
| Texte long | lent | généralement plus rapide |

!!! note "Mesurer le temps"
    On peut comparer les durées avec **`timeit`**. Les valeurs mesurées **dépendent
    de la machine et des données** : elles illustrent une tendance, sans être absolues.

---

## 9. Méthodes bac

!!! tip "Procédures à appliquer"
    - **analyser** `index()` et `find()` (valeurs / exception) ;
    - **compter** toutes les occurrences (boucle + `pos + 1`) ;
    - **suivre** une recherche naïve (valeurs de `i` et `j`) ;
    - **calculer** les positions possibles (`N − n + 1`) ;
    - **compléter** les boucles et conditions ;
    - **construire** une table de sauts (`n − 1 − i`, dernier exclu) ;
    - **représenter** les fenêtres successives de Boyer-Moore ;
    - **déterminer** le saut effectué (présent / absent) ;
    - **comparer** deux temps d'exécution ;
    - **expliquer** pourquoi Boyer-Moore évite des comparaisons.

---

## 10. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **`index()`** (exception) et **`find()`** (`-1`) ;
    - confondre **exception**, **`None`** et **`-1`** ;
    - confondre **motif** et **caractère unique** ;
    - confondre **`i`**, **`j`** et **`i + j`** ;
    - se tromper sur le **nombre de fenêtres** = `N − n + 1` ;
    - oublier de **reprendre à `pos + 1`** lors du comptage ;
    - placer la **dernière lettre** dans la table (elle est **exclue**) ;
    - mal gérer les **lettres répétées** (garder la **dernière** valeur) ;
    - comparer Boyer-Moore **dans le mauvais sens** (il part de la **fin**) ;
    - oublier le **saut maximal** (`n`) pour une lettre **absente** ;
    - oublier que le naïf renvoie un **indice** alors que Boyer-Moore (cours) renvoie un **booléen**.

---

## 11. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Que signifie `texte[i:i+len(motif)] == motif` ?"
    Le **motif apparaît** dans le texte à l'**indice `i`**.

??? question "2. Quelle est la différence entre `index()` et `find()` si le motif est absent ?"
    `index()` lève une **`ValueError`** ; `find()` renvoie **`-1`**.

??? question "3. Comment renvoyer `None` quand le motif est absent ?"
    Avec un **`try / except ValueError`** autour de `index()`.

??? question "4. Pourquoi reprendre à `pos + 1` pour compter les occurrences ?"
    Pour trouver **toutes** les occurrences, y compris celles qui se **chevauchent**.

??? question "5. Dans la recherche naïve, que représentent `i`, `j` et `i + j` ?"
    `i` = début de fenêtre ; `j` = position dans le motif ; `i + j` = caractère
    comparé dans le **texte**.

??? question "6. Combien de positions teste la recherche naïve ?"
    `N − n + 1` (avec `N = len(texte)`, `n = len(motif)`).

??? question "7. Quel est l'ordre de grandeur de la complexité naïve retenu dans le cours ?"
    `O(n²)`.

??? question "8. Construire la table de décalages de `\"dab\"`."
    `{'d': 2, 'a': 1}` (le dernier caractère `'b'` est exclu).

??? question "9. Pour `\"maman\"`, pourquoi obtient-on `{'m': 2, 'a': 1}` ?"
    Les lettres répétées conservent la **dernière** valeur écrite : `m` → 2, `a` → 1.

??? question "10. Dans Boyer-Moore, que fait-on si le caractère est absent du motif ?"
    On effectue le **saut maximal** : `len(motif)` (soit `n`).

??? question "11. Que renvoie `recherche_boyer` du cours ?"
    Un **booléen** (présence ou absence du motif).

??? question "12. Pourquoi Boyer-Moore est-il souvent plus rapide sur un texte long ?"
    Il **compare depuis la fin** et effectue des **sauts** : il évite de nombreuses
    comparaisons inutiles.

---

## À retenir absolument

!!! success "`index()` vs `find()`"
    | | trouvé | absent |
    |---|---|---|
    | **`index()`** | indice | `ValueError` |
    | **`find()`** | indice | `-1` |

!!! abstract "Recherche naïve"
    Tester chaque position de **gauche à droite**, décaler de **1** après un échec ;
    **nombre de fenêtres = `N − n + 1`** ; complexité du cours **`O(n²)`**.

!!! note "Boyer-Moore"
    - **table** : `pre_traitement` → `caractère → n − 1 − i` (dernier exclu, dernière
      valeur conservée pour les répétitions) ;
    - **comparaison depuis la droite** ;
    - **décalage** : lettre **présente** → valeur de la table ; lettre **absente** →
      saut de **`n`** ; plusieurs caractères égaux → poursuivre vers la gauche.

!!! quote "Formulations utiles au bac"
    - « Le motif apparaît à l'indice `i` car `texte[i:i+n] == motif`. »
    - « La recherche naïve teste `N − n + 1` fenêtres, d'où une complexité en `O(n²)`. »
    - « Boyer-Moore compare depuis la **fin** et saute grâce à la **table**, ce qui
      lui évite de nombreuses comparaisons. »