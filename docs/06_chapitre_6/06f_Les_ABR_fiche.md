---
author: Elisabeth Le Prettre (LePrettre)
title: 06b 📜 Fiche Méthode - Arbre binaire de recherche
---

# Les arbres binaires de recherche (ABR)

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur les arbres binaires de recherche :
    propriété d'ordre, reconnaissance, construction, insertion, recherche, parcours
    infixe, minimum / maximum, et lien entre **hauteur** et **performance**.

!!! note "Exemple filé"
    Arbre obtenu en insérant la séquence `8, 3, 10, 1, 6, 14, 4, 7, 13` :
    ```
                8
              /   \
             3     10
            / \      \
           1   6      14
              / \     /
             4   7   13
    ```

---

## 1. Définition

Un **arbre binaire de recherche (ABR)** est un arbre binaire dans lequel chaque
nœud porte une **clé** (et éventuellement une **donnée associée**), tel que :

- toutes les clés du **sous-arbre gauche** sont **inférieures** à la clé du nœud ;
- toutes les clés du **sous-arbre droit** sont **supérieures** à la clé du nœud ;
- cette **propriété est vérifiée récursivement** pour **tous** les nœuds.

| Terme | Définition |
|---|---|
| **Clé** | Valeur servant au **classement** et aux comparaisons. |
| **Donnée associée** | Information rattachée à la clé (l'enregistrement). |

---

## 2. Reconnaître un ABR

!!! tip "Méthode"
    Il ne suffit **pas** de comparer un nœud à ses **enfants directs** : il faut que
    **tout** le sous-arbre gauche soit inférieur et **tout** le sous-arbre droit
    supérieur. On vérifie donc, pour chaque nœud, un **intervalle** de valeurs
    autorisées :

    1. la racine peut prendre n'importe quelle valeur ;
    2. en allant à **gauche**, on impose une **borne supérieure** (la clé du père) ;
    3. en allant à **droite**, on impose une **borne inférieure** (la clé du père) ;
    4. chaque nœud doit respecter l'intervalle hérité de **tous** ses ancêtres.

!!! danger "Contre-exemple classique"
    ```
          8
         / \
        3   10
             \
              7     ← 7 < 8 mais placé dans le sous-arbre DROIT de 8 : INVALIDE
    ```
    `7` respecte son père direct `10` (7 < 10) mais **viole** la contrainte de
    l'ancêtre `8` (tout le sous-arbre droit doit être > 8).

---

## 3. Construire un ABR

!!! tip "Insertion manuelle d'une séquence"
    - la **première** clé devient la **racine** ;
    - chaque nouvelle clé est comparée depuis la racine : **plus petite → gauche**,
      **plus grande → droite**, jusqu'à trouver une place vide ;
    - **l'ordre d'arrivée modifie la forme** de l'arbre.

!!! warning "Même ensemble, arbres différents"
    Insérer `1, 2, 3, 4` (déjà trié) donne un arbre **filiforme** (une « chaîne »),
    alors que `2, 1, 3` donne un arbre **équilibré**. Deux ordres d'insertion ne
    donnent **pas** forcément le même arbre.

---

## 4. Performances

| Forme de l'arbre | Hauteur | Coût des opérations |
|---|---|---|
| **Équilibré** | environ `log₂(n)` | `O(log n)` |
| **Filiforme (dégénéré)** | `n − 1` | `O(n)` |

!!! note "Coût lié à la hauteur"
    Recherche, insertion et min/max suivent **un chemin** de la racine vers le bas :
    leur coût est **proportionnel à la hauteur**. D'où `O(log n)` **en moyenne**
    dans un arbre suffisamment **équilibré**, mais `O(n)` dans le **pire cas**
    (arbre dégénéré en peigne).

---

## 5. Implémentation

```python
class Node:
    def __init__(self, cle, gauche=None, droite=None):
        self.cle = cle           # clé / valeur
        self.gauche = gauche     # fils gauche
        self.droite = droite     # fils droit
    def __str__(self):
        return str(self.cle)
    def est_feuille(self):
        return self.gauche is None and self.droite is None
```

!!! note "Fonction vs méthode"
    - **Fonction** : `inserer(a, c)` — l'arbre est un **paramètre** ;
    - **Méthode** : `a.est_feuille()` — appelée **sur** l'objet, utilise `self`.

---

## 6. Insertion

```
inserer(a, c):
    si a est vide:
        renvoyer Node(c)              # vide → créer
    si c < a.cle:
        a.gauche ← inserer(a.gauche, c)   # plus petit → gauche
    sinon si c > a.cle:
        a.droite ← inserer(a.droite, c)   # plus grand → droite
    renvoyer a                        # on RENVOIE la racine (mise à jour)
```

Étapes clés :

- **vide → créer** un nouveau nœud ;
- **plus petit → gauche**, **plus grand → droite** ;
- **gérer le retour de la racine** : chaque appel renvoie le sous-arbre (mis à
  jour), qu'on **réaffecte** (`a.gauche ← …`) — indispensable en style fonctionnel ;
- **doublons** : à traiter **selon le code du cours** (souvent **ignorés** : si
  `c == a.cle`, on ne fait rien).

!!! info "À adapter à ton cours"
    Si ton cours **autorise** les doublons (par exemple en les plaçant à droite, ou
    en comptant les occurrences), précise-le moi et j'ajuste le pseudo-code.

---

## 7. Recherche

```
rechercher(a, c):
    si a est vide:
        renvoyer Faux                 # vide → absent
    si c == a.cle:
        renvoyer Vrai                 # égal → trouvé
    si c < a.cle:
        renvoyer rechercher(a.gauche, c)   # plus petit → gauche
    sinon:
        renvoyer rechercher(a.droite, c)   # plus grand → droite
```

!!! tip "Tracer le chemin de recherche"
    À chaque nœud visité, **noter / afficher la clé** : on obtient le **chemin**
    suivi de la racine jusqu'à la valeur trouvée (ou jusqu'à un sous-arbre vide).
    *Ex. : rechercher `7` dans l'arbre filé → chemin `8 → 3 → 6 → 7`.*

---

## 8. Parcours infixe

Ordre **G → N → D** (gauche, racine, droite).

!!! tip "Pourquoi l'ordre croissant ?"
    Par la propriété d'ordre, tout ce qui est à **gauche** est plus petit que la
    racine, et tout ce qui est à **droite** est plus grand. Le parcours infixe
    visite donc les clés **dans l'ordre croissant**.

*Sur l'arbre filé :* infixe = `1 3 4 6 7 8 10 13 14` (trié).

!!! note "Trier une collection"
    On peut **trier** un ensemble de valeurs en les **insérant** dans un ABR, puis
    en effectuant un **parcours infixe** : on récupère les clés triées.

---

## 9. Minimum et maximum

- **minimum** = nœud **le plus à gauche** ;
- **maximum** = nœud **le plus à droite**.

```
# Itératif
minimum(a):                      maximum(a):
    n ← a                            n ← a
    tant que n.gauche ≠ vide:        tant que n.droite ≠ vide:
        n ← n.gauche                     n ← n.droite
    renvoyer n.cle                   renvoyer n.cle

# Récursif
minimum(a):  si a.gauche vide → a.cle ; sinon minimum(a.gauche)
maximum(a):  si a.droite vide → a.cle ; sinon maximum(a.droite)
```

*Sur l'arbre filé :* min = `1`, max = `14`.

---

## 10. Autres opérations

**Taille**, **hauteur**, **nombre de feuilles** et **parcours en largeur** se
calculent **exactement comme pour un arbre binaire classique** (la propriété d'ordre
ne change rien à ces opérations).

```
taille(a)  = 0   si vide ; sinon 1 + taille(gauche) + taille(droite)
hauteur(a) = -1  si vide ; sinon 1 + max(hauteur(gauche), hauteur(droite))
```

---

## 11. Clé et données (projet Pokémon)

Dans le projet Pokémon, chaque nœud contient :

- une **clé** (par exemple le **numéro de Pokédex**) qui sert au **classement** et
  aux comparaisons dans l'ABR ;
- des **données** (l'**enregistrement** : nom, type, statistiques…) que l'on
  consulte **une fois la clé trouvée**.

!!! tip "Interface vs accès direct"
    - **fonctions d'interface** (ex. `get_cle(n)`, `get_donnees(n)`) : on passe par
      des opérations dédiées, sans dépendre de la représentation interne ;
    - **accès direct aux attributs** (ex. `n.cle`, `n.donnees`) : plus court, mais
      lie le code à l'implémentation choisie.

---

## 12. Méthodes bac

!!! tip "Procédures à appliquer"
    - **reconnaître ou corriger** un ABR (vérifier les **sous-arbres entiers**) ;
    - **construire** l'arbre à partir d'une **séquence** (1ʳᵉ clé = racine) ;
    - **suivre** une insertion ou une recherche (chemin de comparaisons) ;
    - **compléter** une fonction récursive (cas vide, comparaison, retour de racine) ;
    - **donner l'ordre infixe** (clés croissantes) ;
    - **trouver min / max** (le plus à gauche / à droite) ;
    - **justifier la complexité** à partir de la **hauteur**.

---

## 13. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - vérifier **seulement les enfants directs** au lieu des sous-arbres entiers ;
    - **inverser les comparaisons** (`<` / `>`, gauche / droite) ;
    - **oublier le cas vide** (cas de base) ;
    - **perdre la racine** dans une insertion fonctionnelle (oublier `renvoyer a`
      ou la réaffectation `a.gauche ← …`) ;
    - croire que **deux ordres d'insertion** donnent toujours le **même** arbre ;
    - annoncer **systématiquement `O(log n)`** (faux pour un arbre filiforme : `O(n)`) ;
    - **confondre clé et donnée** ;
    - utiliser un **autre parcours que l'infixe** pour obtenir l'ordre croissant.

---

## 14. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Énoncer la propriété d'un ABR."
    Pour **tout** nœud : toutes les clés du sous-arbre **gauche** sont **inférieures**
    à sa clé, et toutes celles du sous-arbre **droit** sont **supérieures**
    (vérifié **récursivement**).

??? question "2. Pourquoi ne suffit-il pas de comparer un nœud à ses enfants directs ?"
    Parce que la contrainte porte sur **tout** le sous-arbre : un nœud peut respecter
    son père direct mais **violer** la contrainte d'un **ancêtre** plus haut.

??? question "3. Construire l'ABR de la séquence 5, 2, 8, 1, 3."
    ```
          5
         / \
        2   8
       / \
      1   3
    ```

??? question "4. Quel arbre obtient-on en insérant 1, 2, 3, 4 dans cet ordre ?"
    Un arbre **filiforme** (chaîne descendante vers la droite), de hauteur `3`
    (racine à 0).

??? question "5. Rechercher 13 dans l'arbre filé : quel est le chemin suivi ?"
    `8 → 10 → 14 → 13` : trouvé.

??? question "6. Donner le parcours infixe de l'arbre filé."
    `1 3 4 6 7 8 10 13 14` (ordre croissant).

??? question "7. Où se trouvent le minimum et le maximum dans un ABR ?"
    Le **minimum** est le nœud le plus à **gauche** ; le **maximum**, le plus à
    **droite**.

??? question "8. Compléter le cas de base de `rechercher(a, c)`."
    `si a est vide: renvoyer Faux` (la clé est absente).

??? question "9. Quelle est la complexité de la recherche dans un ABR équilibré ? dégénéré ?"
    `O(log n)` dans un arbre **équilibré** ; `O(n)` dans un arbre **filiforme**.

??? question "10. Comment trier une collection à l'aide d'un ABR ?"
    En **insérant** toutes les valeurs dans l'ABR, puis en effectuant un parcours
    **infixe** (qui renvoie les clés triées).

??? question "11. Dans une insertion récursive fonctionnelle, pourquoi écrire `a.gauche ← inserer(a.gauche, c)` ?"
    Pour **récupérer le sous-arbre mis à jour** renvoyé par l'appel récursif et le
    rattacher : sinon la modification (et parfois la racine) serait **perdue**.

??? question "12. Dans le projet Pokémon, à quoi sert la clé et à quoi servent les données ?"
    La **clé** (ex. numéro de Pokédex) sert au **classement** dans l'ABR ; les
    **données** contiennent l'**enregistrement** consulté une fois la clé trouvée.

---

## À retenir absolument

!!! success "Propriété d'ordre"
    Pour tout nœud : **sous-arbre gauche < clé < sous-arbre droit** (récursivement
    sur **tous** les nœuds).

!!! abstract "Schémas d'insertion et de recherche"
    ```
    inserer(a, c)    : vide → créer ; c < clé → gauche ; c > clé → droite ; renvoyer a
    rechercher(a, c) : vide → absent ; égal → trouvé ; c < clé → gauche ; c > clé → droite
    ```

!!! note "Repères essentiels"
    - **parcours infixe** (G-N-D) → clés dans l'**ordre croissant** ;
    - **minimum** = le plus à **gauche** ; **maximum** = le plus à **droite** ;
    - **hauteur ↔ performance** : `O(log n)` si **équilibré**, `O(n)` si **filiforme** ;
    - taille / hauteur / feuilles / largeur : **comme un arbre binaire** classique.

!!! quote "Formulations utiles au bac"
    - « Cet arbre est un ABR car, pour chaque nœud, **tout** le sous-arbre gauche
      est inférieur et **tout** le sous-arbre droit supérieur à sa clé. »
    - « Le coût de la recherche est proportionnel à la **hauteur** : `O(log n)` si
      l'arbre est équilibré, `O(n)` s'il est filiforme. »
    - « Le parcours **infixe** restitue les clés dans l'**ordre croissant**. »