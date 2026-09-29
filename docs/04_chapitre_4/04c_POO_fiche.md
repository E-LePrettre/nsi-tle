---
author: Elisabeth Le Prettre (LePrettre)
title: 04 📜 Fiche Méthode - P.O.O.
---

# La programmation orientée objet (POO) en Python

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur la POO en Python : vocabulaire,
    modèle d'une classe, attributs et méthodes, encapsulation, héritage et
    polymorphisme. Les **approfondissements hors programme** sont signalés par un
    encadré **« Hors programme »**.

---

## 1. Vocabulaire

| Terme | Définition |
|---|---|
| **POO** | Façon de programmer en regroupant des données et des actions dans des **objets**. |
| **Classe** | Modèle (plan) décrivant des objets de même nature. |
| **Objet** | Élément concret construit à partir d'une classe. |
| **Instance** | Synonyme d'objet : un objet est une instance de sa classe. |
| **Référence** | Lien (variable) qui désigne un objet en mémoire. |
| **Instanciation** | Action de créer un objet à partir d'une classe (`Carre(5)`). |
| **Attribut** | Donnée (variable) appartenant à un objet ou à une classe. |
| **Attribut d'instance** | Attribut propre à **chaque** objet (défini avec `self`). |
| **Attribut de classe** | Attribut **partagé** par toutes les instances de la classe. |
| **Méthode** | Fonction définie dans une classe, agissant sur l'objet. |
| **Méthode spéciale** | Méthode au nom encadré de `__` (ex. `__init__`, `__str__`). |
| **Constructeur** | Méthode `__init__`, appelée à la création de l'objet. |
| **Destructeur** | Méthode `__del__`, appelée à la destruction de l'objet. |
| **`self`** | Référence à l'objet courant, premier paramètre des méthodes. |
| **Abstraction** | Ne montrer que l'essentiel, masquer les détails internes. |
| **Encapsulation** | Regrouper données + méthodes et **protéger** l'accès aux données. |
| **Accesseur** | Méthode qui **lit** un attribut (*getter*). |
| **Mutateur** | Méthode qui **modifie** un attribut (*setter*), souvent avec contrôle. |
| **Héritage** | Une classe fille **reprend** les attributs et méthodes d'une classe mère. |
| **Polymorphisme** | Une même méthode peut se comporter différemment selon la classe. |

---

## 2. Modèle minimal d'une classe

```python
class Carre:
    def __init__(self, cote):      # 1. constructeur
        self.cote = cote           # 2. attribut d'instance

    def aire(self):                # 3. méthode qui retourne une valeur
        return self.cote * self.cote

c = Carre(5)        # 4. création d'une instance
print(c.cote)       # 5. lecture d'un attribut   → 5
print(c.aire())     # 6. appel d'une méthode      → 25
```

Explication ligne par ligne :

- `class Carre:` → **déclaration** de la classe ;
- `def __init__(self, cote):` → **constructeur**, exécuté à la création ;
- `self.cote = cote` → crée l'**attribut d'instance** `cote` ;
- `def aire(self):` → **méthode d'instance** ; `self` désigne l'objet ;
- `return self.cote * self.cote` → la méthode **retourne** une valeur ;
- `c = Carre(5)` → **instanciation** : `c` référence un nouvel objet ;
- `c.cote` → **lecture** d'un attribut avec la notation `objet.attribut` ;
- `c.aire()` → **appel** d'une méthode avec `objet.methode()` (parenthèses !).

---

## 3. Méthodes et attributs

| Élément | Rôle |
|---|---|
| `__init__(self, …)` | **Constructeur** : initialise les attributs à la création. |
| `__del__(self)` | **Destructeur** : appelé quand l'objet est détruit. |
| Méthode d'instance | Fonction agissant sur l'objet, premier paramètre `self`. |
| `__str__(self)` | Texte **lisible** affiché par `print(objet)`. |
| `__repr__(self)` | Représentation **technique** (utile au débogage / dans la console). |

!!! note "Attribut d'instance vs attribut de classe"
    ```python
    class Compteur:
        nombre = 0          # attribut de CLASSE (partagé)
        def __init__(self):
            self.valeur = 0 # attribut d'INSTANCE (propre à chaque objet)
    ```
    - `self.valeur` est **différent** pour chaque objet ;
    - `Compteur.nombre` est **commun** à toutes les instances.

!!! tip "Notation d'accès"
    - `objet.attribut` → lecture / écriture d'un attribut ;
    - `objet.methode()` → appel d'une méthode (**ne pas oublier `()`**).

---

## 4. Encapsulation

| Niveau | Écriture | Signification |
|---|---|---|
| **Public** | `self.nom` | Accessible librement depuis l'extérieur. |
| **Protégé (convention)** | `self._nom` | Accès **déconseillé** de l'extérieur (simple convention). |
| **Privé** | `self.__nom` | Accès **interdit** directement (nom « rendu interne » par Python). |

**Getters et setters** permettent de contrôler l'accès aux données :

```python
class Compte:
    def __init__(self, solde):
        self.__solde = solde            # attribut privé

    def get_solde(self):                # accesseur (getter)
        return self.__solde

    def set_solde(self, montant):       # mutateur (setter)
        if montant >= 0:                # contrôle des données
            self.__solde = montant
```

- **lire** une donnée protégée → passer par un **accesseur** ;
- **modifier** une donnée protégée → passer par un **mutateur** qui **valide**
  la nouvelle valeur (ici, refuser un solde négatif).

!!! warning "Affectation directe à `objet.__nom` depuis l'extérieur"
    Écrire `c.__solde = 100` **depuis l'extérieur** ne modifie **pas** l'attribut
    privé : Python crée alors un **nouvel attribut** sans rapport avec l'attribut
    interne. C'est une erreur fréquente : on croit modifier la donnée protégée,
    alors qu'on en a créé une autre.

!!! info "Hors programme — les propriétés"
    Le décorateur `@property` (avec un *setter* associé) permet d'utiliser un
    attribut comme s'il était public tout en gardant le contrôle d'un setter. À
    présenter **uniquement** s'il figure dans le cours ; ce n'est **pas** un
    attendu du bac.

---

## 5. Héritage et polymorphisme

| Notion | Définition |
|---|---|
| **Classe mère** | Classe dont on hérite (la « parente »). |
| **Classe fille** | Classe qui hérite (reçoit les attributs / méthodes). |
| **Héritage simple** | La classe fille a **une seule** classe mère. |
| **Redéfinition** | La fille **réécrit** une méthode héritée. |

```python
class Personne:
    def __init__(self, nom):
        self.nom = nom
    def se_presenter(self):
        return f"Je suis {self.nom}"

class AgentSpecial(Personne):           # héritage simple
    def __init__(self, nom, matricule):
        super().__init__(nom)           # appel du constructeur de la mère
        self.matricule = matricule
    def se_presenter(self):             # redéfinition de la méthode
        return f"Agent {self.matricule}"
```

- `class AgentSpecial(Personne)` → `AgentSpecial` **hérite** de `Personne` ;
- `super().__init__(nom)` → appelle le **constructeur de la classe mère** ;
- `se_presenter` est **redéfinie** dans la fille ;
- **polymorphisme** : appeler `se_presenter()` sur une `Personne` ou un
  `AgentSpecial` donne un comportement **différent** selon la classe réelle.

**Surcharge d'opérateurs** (méthodes spéciales), exemple `Duree` :

```python
class Duree:
    def __init__(self, minutes):
        self.minutes = minutes
    def __add__(self, autre):           # surcharge de +
        return Duree(self.minutes + autre.minutes)
    def __str__(self):
        return f"{self.minutes} min"

d = Duree(30) + Duree(45)   # appelle __add__
print(d)                    # appelle __str__ → 75 min
```

!!! info "Hors programme"
    - **Héritage multiple** (plusieurs classes mères) et **MRO** (*Method
      Resolution Order*, ordre de recherche des méthodes) : **hors programme**,
      à ne traiter qu'en approfondissement.
    - La **surcharge d'opérateurs** et les **comparaisons** (`__add__`, `__eq__`,
      `__lt__`…) ne sont à présenter que si elles figurent explicitement dans le
      cours ; vérifie ce qui est exigible dans ta progression.

---

## 6. Décorateurs

!!! info "Pour aller plus loin (hors programme du bac)"
    Ces notions **ne sont pas des attendus du bac**. À ne lire qu'en approfondissement.

    - **`@decorateur`** : un décorateur « enveloppe » une fonction pour modifier
      son comportement, en l'écrivant au-dessus de sa définition :
      ```python
      @mon_decorateur
      def f():
          ...
      ```
    - **`__call__`** : méthode spéciale qui rend un **objet appelable** comme une
      fonction (`objet()`).
    - **`*args`** : reçoit un **nombre variable** d'arguments positionnels (tuple).
    - **`**kwargs`** : reçoit un **nombre variable** d'arguments nommés (dictionnaire).

---

## 7. Méthodes bac

### Écrire une classe pas à pas

1. **Repérer les attributs** demandés dans l'énoncé.
2. **Écrire le constructeur** `__init__(self, …)`.
3. **Choisir les paramètres** du constructeur (ce qu'on fournit à la création).
4. **Écrire les méthodes** (une action = une méthode).
5. **Distinguer lecture et modification** : accesseur (lit) vs mutateur (modifie).
6. **Choisir une méthode spéciale** si nécessaire (`__str__`, `__add__`, …).
7. **Instancier et tester** : créer un objet et appeler ses méthodes.
8. **Suivre l'évolution des attributs** à chaque appel (état de l'objet).

### Lire un programme objet et prévoir l'affichage

!!! tip "Procédure"
    1. Repérer la (les) **classe(s)** et leurs **attributs**.
    2. Repérer ce que fait le **constructeur** (état initial de l'objet).
    3. Suivre **chaque appel** de méthode et **mettre à jour** les attributs.
    4. Identifier ce qui est **affiché** (`print`) vs **retourné** (`return`).
    5. En déduire **l'affichage** ou **l'état final** de l'objet.

---

## 8. Applications du cours

Compétences travaillées dans les classes étudiées :

| Classe / projet | Compétences principales |
|---|---|
| `Personnage` | Constructeur, attributs d'instance, méthodes d'action. |
| `Piece` | Modélisation simple, état d'un objet. |
| `Carre` | Constructeur, calcul (aire / périmètre). |
| `Fraction` | Calculs, **validation**, surcharge d'opérateurs, `__str__`. |
| `Complexe` | Opérateurs (`+`, `*`), affichage lisible. |
| `Temps` | Calculs sur le temps, normalisation, comparaisons. |
| `Intervalle` | Validation des bornes, comparaisons, appartenance. |
| `Carte` | Modélisation d'un objet du jeu, `__str__`. |
| `JeuDeCartes` | **Collection d'objets** (liste de `Carte`), méthodes de gestion. |
| Projet **filtres d'image** | Manipulation d'objets, méthodes de transformation, tests. |

!!! note "Fil rouge des compétences"
    constructeur · calculs · **validation** des données · **comparaisons** ·
    **surcharge d'opérateurs** · **collections d'objets** · **encapsulation** ·
    **tests** d'une classe.

---

## 9. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - **oublier `self`** (en paramètre ou devant un attribut) ;
    - **confondre classe et instance** (la classe est le modèle, l'objet l'exemplaire) ;
    - **confondre attribut de classe et attribut d'instance** (partagé vs propre) ;
    - **oublier les parenthèses** lors d'un appel : `c.aire` ❌ → `c.aire()` ✅ ;
    - **confondre `return` et `print`** (`print` affiche, `return` renvoie une valeur) ;
    - **modifier directement** un attribut à protéger au lieu de passer par un setter ;
    - **getter ou setter incorrect** (oubli du `return`, contrôle manquant) ;
    - **mauvais appel du constructeur parent** (oublier `super().__init__(…)`) ;
    - **méthode spéciale qui ne retourne pas le bon résultat** (`__str__` doit
      renvoyer une **chaîne**, `__add__` un **objet**) ;
    - **constructeur acceptant une valeur incohérente** (absence de validation) ;
    - **création involontaire d'un nouvel attribut** (faute de frappe sur un nom,
      ou affectation à `objet.__nom` depuis l'extérieur).

---

## 10. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Quelle est la différence entre une classe et un objet ?"
    Une **classe** est un modèle décrivant des objets ; un **objet** (ou instance)
    est un exemplaire concret construit à partir de cette classe.

??? question "2. À quoi sert `self` dans une méthode ?"
    `self` désigne **l'objet courant** : il permet d'accéder à ses attributs et à
    ses autres méthodes (`self.attribut`, `self.methode()`).

??? question "3. Que vaut `c.cote` puis `c.aire()` après `c = Carre(5)` ? (voir §2)"
    `c.cote` vaut `5` (l'attribut), `c.aire()` vaut `25` (la méthode retourne
    `5 * 5`).

??? question "4. Compléter le constructeur d'une classe `Point` à deux coordonnées."
    ```python
    class Point:
        def __init__(self, x, y):
            self.x = x
            self.y = y
    ```

??? question "5. Écrire une méthode `perimetre` pour la classe `Carre`."
    ```python
    def perimetre(self):
        return 4 * self.cote
    ```

??? question "6. Pourquoi écrire un attribut `__solde` plutôt que `solde` ?"
    Pour l'**encapsuler** : empêcher la modification directe depuis l'extérieur et
    forcer le passage par un mutateur qui **valide** la valeur.

??? question "7. Quelle est la différence entre attribut de classe et attribut d'instance ?"
    L'attribut de **classe** est **partagé** par toutes les instances ; l'attribut
    d'**instance** (`self.x`) est **propre à chaque** objet.

??? question "8. Que doit renvoyer la méthode `__str__` et à quoi sert-elle ?"
    Elle doit renvoyer une **chaîne de caractères** ; elle définit le texte affiché
    par `print(objet)`.

??? question "9. Donner la méthode spéciale qui permet d'écrire `a + b` entre deux objets."
    `__add__(self, autre)` : elle est appelée par l'opérateur `+` et doit renvoyer
    le résultat (souvent un nouvel objet).

??? question "10. Corriger : `class A: def aff(): print(self.x)`"
    Il manque `self` en paramètre de la méthode :
    ```python
    class A:
        def aff(self):
            print(self.x)
    ```

---

## À retenir absolument

!!! success "Modèle minimal d'une classe"
    ```python
    class NomClasse:
        def __init__(self, parametres):
            self.attribut = parametres
        def methode(self):
            return ...        # ou une action
    objet = NomClasse(...)    # instanciation
    objet.attribut            # lecture
    objet.methode()           # appel
    ```

!!! abstract "L'essentiel"
    - **classe** = modèle ; **objet** = instance concrète de la classe ;
    - **`self`** désigne l'objet courant (toujours premier paramètre) ;
    - **méthodes spéciales** essentielles : `__init__` (constructeur), `__str__`
      (affichage) ; `__del__` (destructeur) ;
    - **encapsulation** : `public`, `_protégé` (convention), `__privé` ; lire avec
      un **accesseur**, modifier avec un **mutateur** qui **valide** ;
    - `objet.attribut` (donnée) vs `objet.methode()` (action, avec `()`).

!!! info "Approfondissements hors programme (à distinguer)"
    - **propriétés** (`@property`) ;
    - **héritage multiple** et **MRO** ;
    - **décorateurs** (`@decorateur`), **`__call__`**, **`*args` / `**kwargs`** ;
    - la **surcharge d'opérateurs** n'est exigible que si elle figure dans le cours.

!!! quote "Formulations utiles au bac"
    - « `self` permet d'accéder aux attributs de l'objet courant. »
    - « Cet attribut est **privé** pour empêcher sa modification directe depuis
      l'extérieur. »
    - « La méthode `__init__` initialise les attributs lors de l'instanciation. »
    - « La classe fille **redéfinit** la méthode `…` héritée de la classe mère. »