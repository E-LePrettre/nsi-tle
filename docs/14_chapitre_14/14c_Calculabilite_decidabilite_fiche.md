---
author: Elisabeth Le Prettre (LePrettre)
title: 14 📜 Fiche Méthode - Calculabilité – Décidabilité
---

# Calculabilité et décidabilité

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur la calculabilité et la décidabilité :
    programme comme donnée, **problème de l'arrêt** et sa preuve, notions de
    décidabilité / calculabilité. La partie **P / NP** est un **approfondissement
    hors programme**.

---

## 1. Programme comme donnée

| Terme | Définition |
|---|---|
| **Programme** | Suite d'**instructions** réalisant une tâche. |
| **Entrée** | Données **fournies** au programme. |
| **Sortie** | Résultat **produit** par le programme. |
| **Code source** | **Texte** du programme. |
| **Exécution** | **Lancement** du programme sur une entrée. |
| **Programme passé en paramètre** | Un programme reçu comme **donnée** par un autre programme. |

!!! note "Un programme peut manipuler du code"
    Un programme peut prendre **le code d'un autre programme** — voire **son propre
    code** — comme donnée d'entrée. C'est cette idée qui rend possible le
    raisonnement sur le problème de l'arrêt.

!!! tip "Quine"
    Un **quine** est un programme qui **affiche son propre code source**, sans le lire
    depuis un fichier : illustration concrète d'un programme qui se manipule lui-même.

---

## 2. Terminaison

```python
def countdown(n):
    while n != 0:
        n = n - 1
    return 0
```

- **programme qui termine** : pour `n ≥ 0`, `n` atteint `0` ;
- **boucle infinie** : pour `n < 0`, `n` ne vaut **jamais** `0` ;
- **analyse d'un cas particulier** : ici, on **peut** raisonner facilement ;
- **décision universelle** : décider pour **tout** programme et **toute** entrée est
  une **tout autre** question.

!!! warning "Attention"
    Le fait qu'un programme **tourne longtemps** ne permet **pas** de conclure avec
    **certitude** qu'il **ne terminera jamais** (il pourrait s'arrêter plus tard).

---

## 3. Programme hypothétique `halt`

On **imagine** un programme :

```
halt(prog, x)
```

- renverrait **`True`** si `prog(x)` **termine** ;
- renverrait **`False`** sinon.

!!! danger "Programme supposé"
    Ce programme **n'existe pas**. On le **suppose** uniquement pour mener une
    **preuve par l'absurde**.

---

## 4. Preuve du problème de l'arrêt

On construit un programme `sym` à partir de `halt` :

```python
def sym(prog):
    if halt(prog, prog):   # si halt annonce que prog(prog) termine…
        while True:        # …sym BOUCLE
            pass
    else:
        return 1           # sinon, sym RENVOIE 1 (termine)
```

On exécute alors `sym(sym)` :

| Réponse de `halt` | Conséquence réelle | Contradiction |
|---|---|---|
| `True` | `sym(sym)` **boucle** | il était annoncé qu'il **terminerait** |
| `False` | `sym(sym)` **renvoie `1`** | il était annoncé qu'il **ne terminerait pas** |

!!! success "Conclusion"
    Dans les deux cas, on aboutit à une **contradiction** : le programme **`halt`
    ne peut pas exister**. Le **problème de l'arrêt** est **indécidable**.

---

## 5. Définitions essentielles

| Terme | Définition |
|---|---|
| **Problème de décision** | Problème dont la réponse est **oui / non**. |
| **Problème décidable** | Il existe un **algorithme** qui répond **toujours** correctement. |
| **Problème indécidable** | **Aucun** algorithme ne peut répondre dans **tous** les cas. |
| **Fonction calculable** | Il existe un algorithme qui la calcule. |
| **Fonction non calculable** | Aucun algorithme ne peut la calculer. |
| **Raisonnement par l'absurde** | Supposer le contraire pour aboutir à une contradiction. |
| **Problème de l'arrêt** | Décider si un programme termine sur une entrée donnée. |

!!! quote "Énoncé à retenir"
    « Aucun algorithme universel ne peut déterminer, pour **tout** programme `P` et
    **toute** entrée `E`, si `P(E)` terminera. »

---

## 6. Turing, Church et Rice

- **Alan Turing**, **1936** : formalise le calcul et démontre l'indécidabilité de l'arrêt ;
- **machine de Turing** : modèle théorique du calcul ;
- **Alonzo Church** : **lambda-calcul**, autre formalisation équivalente du calcul ;
- **David Hilbert** : projet de **décision universelle** (résoudre tout problème par un algorithme) — montré **impossible** ;
- **théorème de Rice** : **toute propriété sémantique non triviale** d'un programme
  est **indécidable**.

!!! note "Questions indécidables universellement"
    - le programme **termine-t-il** ?
    - **renvoie-t-il** une valeur donnée ?
    - **provoque-t-il** une erreur ?

---

## 7. Machine de Turing

- **modèle théorique** d'un algorithme ;
- **outil** pour étudier ce qui est **calculable** ;
- une **machine universelle** reçoit une machine `M` et une entrée `e`…
- …et **simule l'exécution** de `M(e)` ;
- c'est l'ancêtre conceptuel de l'**ordinateur programmable** (un même appareil
  exécute n'importe quel programme).

---

## 8. Calculabilité et complexité

| Question | Domaine |
|---|---|
| Existe-t-il un algorithme ? | **calculabilité** |
| Cet algorithme est-il efficace ? | **complexité** |
| Aucun algorithme ne convient | **indécidable / non calculable** |
| Algorithme existant mais très coûteux | **calculable mais difficile** |

!!! warning "Distinction essentielle"
    **Indécidable** ne signifie **pas** seulement « lent ». Un problème indécidable
    n'a **aucun** algorithme, même infiniment lent ; un problème seulement
    **difficile** a un algorithme, mais **coûteux**.

---

## 9. Approfondissement : P, NP et NP-complet

!!! info "Hors programme du bac"
    Cette partie est un **approfondissement** : elle n'est **pas** un attendu du bac.

- **P** : problèmes résolus en **temps polynomial** ;
- **NP** : problèmes de décision dont une **solution se vérifie** en temps polynomial ;
- **`P ⊆ NP`** : tout problème de P est dans NP ;
- **question ouverte** : **`P = NP ?`** (non résolue).

!!! note "Exemples (versions décisionnelles)"
    **Sudoku**, **factorisation**, **sac à dos**, **voyageur de commerce**.

!!! abstract "Problème NP-complet"
    Un problème **NP-complet** est parmi **les plus difficiles** de NP : un algorithme
    **polynomial** pour **un seul** d'entre eux fournirait un algorithme polynomial
    pour **tous** les problèmes de NP (et donc `P = NP`).

!!! quote "Prix du millénaire"
    La question **`P = NP ?`** fait partie des **problèmes du prix du millénaire**
    (récompensés s'ils sont résolus).

---

## 10. Méthodes bac

!!! tip "Procédures à appliquer"
    - **expliquer pourquoi un programme est une donnée** (il peut être passé en paramètre) ;
    - **présenter l'hypothèse `halt`** (programme supposé qui décide la terminaison) ;
    - **analyser `sym`** (boucle si `halt` annonce l'arrêt, renvoie `1` sinon) ;
    - **étudier les deux cas** de `sym(sym)` ;
    - **repérer chaque contradiction** ;
    - **formuler la conclusion** d'indécidabilité ;
    - **distinguer calculabilité** (existe-t-il un algorithme ?) et **efficacité** (est-il rapide ?) ;
    - **distinguer P et NP** (résoudre vs vérifier).

---

## 11. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - détecter **certaines** boucles ≠ résoudre **universellement** l'arrêt ;
    - programme **lent** ≠ programme **non calculable** ;
    - **exponentiel** ≠ **indécidable** ;
    - oublier que **`halt` est hypothétique** (il n'existe pas) ;
    - croire qu'une **simulation** dit toujours si le programme **terminera plus tard** ;
    - croire que **NP** signifie « **non polynomial** » (faux : c'est « vérifiable en
      temps polynomial ») ;
    - affirmer que **`P ≠ NP`** est démontré (c'est **ouvert**) ;
    - confondre **vérifier** une solution et **la trouver**.

---

## 12. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Pourquoi dit-on qu'un programme peut être une donnée ?"
    Parce qu'il peut être **passé en paramètre** à un autre programme (voire à
    lui-même), sous forme de **code source**.

??? question "2. `countdown(n)` termine-t-il pour tout `n` entier ?"
    Non : il termine pour `n ≥ 0`, mais **boucle indéfiniment** pour `n < 0`
    (`n` n'atteint jamais `0`).

??? question "3. Pourquoi une longue exécution ne prouve-t-elle pas la non-terminaison ?"
    Le programme pourrait **s'arrêter plus tard** : observer qu'il tourne longtemps
    ne permet **pas** de conclure.

??? question "4. Que renverrait `halt(prog, x)` s'il existait ?"
    `True` si `prog(x)` **termine**, `False` sinon.

??? question "5. Que fait `sym(prog)` selon la réponse de `halt` ?"
    Si `halt(prog, prog)` annonce un arrêt, `sym` **boucle** ; sinon, `sym`
    **renvoie `1`**.

??? question "6. Quelle contradiction apparaît si `halt(sym, sym) = True` ?"
    `halt` annonce que `sym(sym)` **termine**, mais `sym(sym)` **boucle** → contradiction.

??? question "7. Quelle est la conclusion de la preuve ?"
    Le programme **`halt` ne peut pas exister** : le problème de l'arrêt est **indécidable**.

??? question "8. Qu'est-ce qu'un problème décidable ?"
    Un problème pour lequel **il existe un algorithme** qui répond **toujours**
    correctement (oui / non).

??? question "9. À quoi sert la machine de Turing ?"
    C'est un **modèle théorique** du calcul, servant à étudier ce qui est **calculable**.

??? question "10. Qu'affirme le théorème de Rice ?"
    Toute **propriété sémantique non triviale** d'un programme est **indécidable**.

??? question "11. « Indécidable » signifie-t-il « très lent » ?"
    Non : un problème **indécidable** n'a **aucun** algorithme ; un problème **lent**
    en a un, mais coûteux.

??? question "12. Que signifie réellement « NP » ?"
    Une **solution se vérifie** en temps **polynomial** — et **non** « non polynomial ».

---

## À retenir absolument

!!! success "Problème de l'arrêt"
    « Aucun algorithme universel ne peut déterminer, pour **tout** programme `P` et
    **toute** entrée `E`, si `P(E)` terminera. » → **indécidable**.

!!! abstract "Étapes de la preuve par contradiction"
    1. **supposer** que `halt` existe ;
    2. construire **`sym`** (boucle si arrêt annoncé, renvoie `1` sinon) ;
    3. exécuter **`sym(sym)`** ;
    4. les **deux cas** mènent à une **contradiction** ;
    5. conclure que **`halt` n'existe pas**.

!!! note "Distinctions clés"
    - **décidable** : un algorithme répond toujours ; **indécidable** : aucun ne le peut ;
    - **calculable** : un algorithme calcule la fonction ; **non calculable** : impossible ;
    - **calculabilité** (existe-t-il ?) ≠ **complexité** (est-il efficace ?).

!!! quote "Machine de Turing & P/NP"
    - **Machine de Turing** : modèle théorique du calcul ; une machine **universelle**
      simule `M(e)`.
    - **(Hors programme)** `P ⊆ NP`, et la question **`P = NP ?`** reste **ouverte**.