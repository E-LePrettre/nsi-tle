---
author: ELP
title: 05b Liste - Pile - File - Dictionnaire
---

📚 **Table des matières**

[1.	🧱 Principaux types abstraits fournis avec le langage Python](#_toc151667915)  
[2.	🧩 Les tableaux](#_toc151667919)  
[3.	🔗 Les listes (chainées)](#_toc151667920)  
[4.	🥞 Les piles](#_toc151667926)  
[5.	🛒 Les files](#_toc151667931)  
[6.	🛠️ Les dictionnaires](#_toc151667938)  
[7.	💡 Exercices](#_toc151667945)  
[8.	🔍 Projets](#_toc151667946)  

🎯 **Compétences évaluables :**

- ✅ Distinguer des structures par le jeu des méthodes qui les caractérisent.

- ✅ Choisir une structure de données adaptée à la situation à modéliser.

- ✅ Distinguer la recherche d’une valeur dans une liste et dans un dictionnaire.

---

## <H2 STYLE="COLOR:BLUE;">🧱 <a name="_toc151667915"></a>**1. Principaux types abstraits fournis avec le langage Python**</H2>

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667916"></a>🧱 **1.1. Liste (`list`)**</H3>

Le type **`list`** de Python repose sur une implémentation par **tableaux dynamiques**.

> ⚠️ **Attention** : Les *listes en Python* ne sont pas des *listes chaînées*, mais bien des **tableaux dynamiques** (équivalents à `array` dans d'autres langages).

Les **listes**, **piles** (`stack`) et **files** (`queue`) sont des **structures de données abstraites** fondamentales.  
Elles diffèrent principalement par **les règles d’ajout et d’accès aux éléments** qu’elles imposent.

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667917"></a>🧩 **1.2. Tableau associatif (`dict`)**</H3>

Le type **`dict`** est l'implémentation Python du type abstrait **tableau associatif**.

- Il repose sur une **table de hachage**.
- Chaque **clé** est transformée par une **fonction de hachage** en un **indice** du tableau, utilisé pour stocker ou retrouver la valeur.

> ✅ L’accès à une valeur par clé se fait en **temps constant** (_O(1)_), **indépendamment du nombre de valeurs stockées**.

Ainsi :

- 🔍 Rechercher une valeur associée à une **clé** est très rapide ;

- ❓ Savoir si une **clé** est présente est également en **temps constant** ;

- 🔁 Contrairement aux listes, où la recherche est proportionnelle à la taille (O(n)).

📌 L’étude détaillée des dictionnaires est abordée plus loin dans ce chapitre.

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667918"></a>🧮 **1.3. Ensemble (`set`)**</H3>

Un **`set`** Python est similaire à un **dictionnaire** ne contenant que des **clés**.

- 📌 Tous les éléments sont **uniques** ;
- 🧰 Les opérations classiques sur les ensembles (union, intersection, différence, etc.) sont **nativement disponibles** et **optimisées**.

Exemple :
```python
myset = {"apple", "banana", "cherry"}
```

---

## <H2 STYLE="COLOR:BLUE;">🧩 <a name="_toc151667919"></a>**2. Les tableaux**</H2>

Un **tableau** est une **structure de données** dont :

* tous les éléments sont du **même type** ;
* les éléments sont stockés à des **adresses contiguës** en mémoire ;
* la **taille est fixée à la création**.

📊 **Résumé des opérations sur un tableau abstrait :**

| **Type Python** | **Type abstrait** |       **Opération**       |     **Exemple**     | **Complexité** |
| :-------------: | :---------------: | :-----------------------: | :-----------------: | :------------: |
|   N’existe pas  |      Tableau      |     Accès à un élément    |       `tab[i]`      |      O(1)      |
|                 |                   | Modification d’un élément |     `tab[i] = x`    |      O(1)      |
|                 |                   |  Effacement d’un élément  |   `retire(tab, i)`  |      O(n)      |
|                 |                   |   Insertion d’un élément  | `insere(tab, x, i)` |      O(n)      |
|                 |                   |   Recherche d’un élément  |  `est_dans(tab, x)` |      O(n)      |

🔎 **Pourquoi l’insertion est-elle en O(n) ?**

Prenons un tableau initial :

|  1  |  1  |  2  |  3  |  4  |  5  | vide | vide | vide |
| :-: | :-: | :-: | :-: | :-: | :-: | :--: | :--: | :--: |

Si l'on insère la valeur **7 en position 1**, il faut **décaler tous les éléments** vers la droite :

|  7  |  1  |  1  |  2  |  3  |  4  |  5  | vide | vide |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :--: | :--: |

Ainsi, plus le tableau est rempli, plus **l'opération devient coûteuse**.

---

## <H2 STYLE="COLOR:BLUE;">🔗 <a name="_toc151667920"></a>**3. Les listes (chaînées)**</H2>

Les **listes chaînées** sont une **structure de données** :

* 🔁 **à longueur variable** ;
* ⚡ **plus efficaces que les tableaux** pour l'ajout ou la suppression d’éléments ;
* 🧱 Utiles pour construire d'autres structures complexes.

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667921"></a>🔗 **3.1. Obtenir une définition**</H3>

Lorsque les éléments sont reliés **les uns aux autres**, on parle de **liste chaînée**.

![](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.004.png){width=60%; : .center }

Chaque élément, ou **cellule**, contient :

* 📦 la **valeur** stockée ;
* 📍 l’**adresse** de l’élément suivant.

Une liste chaînée est :

* soit **vide** (`None`) ;
* soit constituée d’une **cellule** (élément) suivie du **reste de la liste**, ce qui en fait une **structure récursive**.

---




### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667922"></a>**3.2. Primitives sur les listes**</H3>

Voici les **opérations minimales** (appelées aussi **primitives**) qui permettent de définir la structure et de lui donner les méthodes attendues :

* Le **constructeur :** produit soit une liste vide ou une liste **à partir d’un couple tête (élément) et reste (liste)**
* Les **sélecteurs** qui permettent d’accéder à la tête de la liste ou au reste. Par exemple, ajouter un élément en tête de liste.
* Le **prédicat** qui teste la vacuité d’une liste (le fait qu’elle soit vide). Il renvoie un booléen.

| 🧱 Opération                                                                     | 💡 Instruction      |
| -------------------------------------------------------------------------------- | ------------------- |
| Créer une liste L vide                                                           | `L = vide()`        |
| Tester si une liste L est vide                                                   | `estVide(L)`        |
| Ajouter un élément *x* en tête de la liste L                                     | `ajouteEnTete(x,L)` |
| Supprimer la tête *x* d’une liste L et renvoyer cette tête *x*                   | `supprEnTete(L)`    |
| Créer une nouvelle liste L1 à partir d’un élément *x* et d’une liste existante L | `L1 = cons(x, L)`   |

🛠️ **Le constructeur**, historiquement appelé `cons`, permet d’obtenir une nouvelle liste à partir d’une liste et d’un élément (`L1 = cons(x, L)`).

Il est possible « d’enchaîner » les `cons` et d’obtenir ce genre de structure :

```python
cons(x, cons(y, cons(z, L)))
```

---

📌 **Exemple :** Voici une série d'instructions (les instructions ci-dessous s'enchaînent) :

* `L=vide()` ⇒ on a créé une liste vide
* `estVide(L)` ⇒ renvoie `vrai`
* `ajoutEnTete(3,L)` ⇒ La liste L contient maintenant l'élément `3`
* `estVide(L)` ⇒ renvoie `faux`
* `ajoutEnTete(5,L)` ⇒ la tête de L = `5`, la queue contient `3`
* `ajoutEnTete(8,L)` ⇒ la tête de L = `8`, la queue contient `5` et `3`
* `t = supprEnTete(L)` ⇒ `t = 8`, L devient \[5, 3]
* `L1 = vide()`
* `L2 = cons(8, cons(5, cons(3, L1)))` ⇒ L2 = \[8, 5, 3]

---

!!! info "🧠 Capytale : Structure liste (chaînée) avec des tuples (activite_liste_tuples )"


???+ question "📝 **Activité n°1 :**"
    Voici une série d'instructions (les instructions ci-dessous s'enchaînent), expliquez ce qui se passe à chacune des étapes :

    ```
    L = vide() 
    ajoutEnTete(10, L) 
    ajoutEnTete(9, L) 
    ajoutEnTete(7, L) 
    L1 = vide() 
    L2 = cons(5, cons(4, cons(3, cons(2, cons(1, cons(0, L1))))))
    ```

    ??? success "📤 Solution :"

        1. on crée un liste vide L 
        2. (10, vide())
        3. (9, (10, vide()))
        4. (7, (9, (10, vide())))
        5. on crée un liste vide L1
        5. L2 est une liste constituée de (5, (4, (3, (2, (1, (0, vide()))))))



---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667923"></a>**3.3. ❤️1<sup>ère</sup> implémentation de la structure liste (chaînée) avec des tuples❤️**</H3>

Les **tuples** sont déclarés en utilisant **les parenthèses**.
Ils peuvent être parcourus via des **boucles `for`**.

⚠️ Les tuples sont **non-mutables** : on **ne peut pas modifier leur contenu après leur création**.

---

#### <H4 STYLE="COLOR:MAGENTA;"> **3.3.1. Implémentation simple avec les tuples**</H4>

📊 Schéma : principe de l'interface entre l'utilisateur et les données
![Principe interface utilisateur/données](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.010.png){width=50%; : .center }

📌 Structure avec tuples – représentation mémoire :
![](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.011.png){width=60%; : .center }

---

???+ question "🧪 **Activité n°2 : structure liste avec des tuples – fonctions `nouvelleListe()` et `estVide()`**"

    Voici une première implémentation de la structure liste avec des tuples :

    ```python
    '''Implémentation de type abstrait Liste en utilisant des tuples (tête, queue)'''

    def nouvelleListe():
        '''Renvoie une liste vide'''
        pass

    # prédicat
    def estVide(L):
        '''Renvoie True si la liste est vide'''
        pass
    ```

    Vérifie leur bon fonctionnement avec les instructions suivantes :

    ```python
    >>> a = ()
    >>> estVide(a)
    ???

    >>> b = None
    >>> estVide(b)
    ???

    >>> c = "C"
    >>> estVide(c)
    ???

    >>> d = nouvelleListe()
    >>> estVide(d)
    ???
    ```

    ??? success "📤 Solution :"

        Rappel du contrat : la fonction `nouvelleListe()` doit renvoyer une **liste vide** compatible avec le prédicat `estVide()`.

        Voici les tests :

        ```python
        a = ()
        print(estVide(a))
        # ✅ True  # Le tuple vide est interprété comme une liste vide ici


        b = None
        print(estVide(b))
        # ❌ False  # `None` n’est pas compatible avec l’implémentation par tuple

        c = "C"
        print(estVide(c))
        # ❌ False  # une chaîne de caractères n’est pas une liste chaînée

        d = nouvelleListe()
        print(estVide(d))
        # ✅ True  # nouvelleListe doit renvoyer un tuple vide (), donc résultat True
        ```

    ❓ **Question finale :**

    Quelle est **la seule proposition** qui respecte **l’interface imposée par le créateur** de cette implémentation ?

    ??? success "📤 Solution :"

        📌 La **seule structure** respectant **l’interface imposée** est :

        ```python
        d = nouvelleListe()
        ```

        💡 Il faut que `nouvelleListe()` retourne le tuple vide `()` pour que `estVide()` fonctionne correctement.

---




???+ question "🧪 Activité n° 3 : `insererTete`"

    📌 **Objectif** : Créer la fonction d'interface suivante :

    ```
    insererTete(x:Elt, L:Liste) → Liste
    ```

    🔧 Elle **renvoie** une nouvelle liste dont la **tête** est l’élément `x`, et la **queue** est la liste précédente `L`.

    💬 **Astuce** : Il suffit de créer un **nouveau tuple** dont la tête est `x`, et la queue est `L`.

    🎯 **Exemple d'utilisation** :

    ```python
    # constructeur
    def insererTete(x,L) :
        '''Renvoie une nouvelle liste où x est la tête et liste la queue'''
        pass
    ```

    ```
    >>> a = nouvelleListe()
    >>> a = insererTete(5, a)
    >>> a
    (5, ())

    >>> a = insererTete(2, a)
    >>> a
    (2, (5, ()))
    ```

    ??? success "📤 Solution :"

        ```python
        def insererTete(x, L):
            '''Renvoie une nouvelle liste dont la tête est x et la queue est L'''
            return (x, L)
        ```

---

???+ question "🧪 Activité n° 4 : `supprimerTete`"

    📌 **Objectif** : Créer une fonction d’interface pour **supprimer la tête** d’une liste.

    ```
    supprimerTete(L:Liste) → Liste
    ```

    📎 Elle **renvoie** une nouvelle liste dont la tête est l’élément **suivant** (celui de la queue précédente).

    🧠 Cela revient à "récupérer la queue". On aurait d'ailleurs pu l'appeler `recupererQueue`.

    ⚠️ **Précondition** : `L` est une liste bien formée (vide `()` ou `(tête, queue)`).

    🧪 Exemple visuel :

    ```
    Liste initiale : 5 → 8 → 2 → 3
    Résultat      : 8 → 2 → 3
    ```

    💬 **Astuce** :

    * La **tête** est en `L[0]`
    * La **queue** est en `L[1]`

    👀 Pense à gérer deux cas :

    * 🔸 **Liste vide** → on renvoie `()`
    * 🔹 **Liste non vide** → on renvoie `L[1]`

    🎯 **Exemples d’utilisation** :

    ```python
    def supprimerTete(L):
        '''Renvoie une nouvelle liste où on a supprimé la tête de l'ancienne '''
        pass
    ```

    ```
    >>> a = nouvelleListe()
    >>> b = supprimerTete(a)
    >>> b
    ()

    >>> a = insererTete(5, nouvelleListe())
    >>> b = supprimerTete(a)
    >>> b
    ()

    >>> a = (20, (15, (5, ())))
    >>> b = supprimerTete(a)
    >>> b
    (15, (5, ()))

    >>> c = supprimerTete(b)
    >>> c
    (5, ())
    ```

    ??? success "📤 Solution :"

        ```python
        def supprimerTete(L):
            '''Renvoie la queue de la liste (supprime la tête)'''
            if estVide(L):
                return nouvelleListe()
            else:
                return L[1]
        ```

---

???+ question "🧪 Activité n° 5 : `lireTete`"

    📌 **Objectif** : Créer la fonction permettant de **lire la tête** d’une liste sans la modifier.

    ```
    lireTete(L:Liste) → Elt
    ```

    ⚠️ **Précondition** : `L` est bien une liste (vide ou `(tête, queue)`).

    📎 **Attention** :

    * On **ne modifie pas** la structure.
    * Il faut vérifier que la liste **n’est pas vide** avant d’accéder à `L[0]`.

    🎯 **Exemple d'utilisation** :

    ```python
    def lireTete(L):
        '''Renvoie la tête de la liste, sans toucher à la liste elle-même'''
        pass
    ```

    ```
    >>> a = insererTete(5, nouvelleListe())
    >>> a = insererTete(15, a)
    >>> lireTete(a)
    15

    >>> b = nouvelleListe()
    >>> lireTete(b)
    None
    ```

    ??? success "📤 Solution :"


        ```python
        def lireTete(L):
            '''Renvoie l’élément en tête de la liste (sans modification)'''
            if estVide(L):
                return None  # ou lever une exception si on préfère
            else:
                return L[0]
        ```

---




???+ question "🎯 Activité n° 6 : `afficherListe`"

    Il nous manque encore une fonctionnalité pratique (mais non obligatoire dans l’interface) : **une représentation lisible** de notre liste sans en montrer l’implémentation réelle.

    Nous aimerions obtenir une représentation comme :
    👉 **`(20, 15, 5)`**
    plutôt que :
    👉 **`(20, (15, (5, ())))`**

    🧪 **Principe** : lire la tête, la supprimer, ajouter la valeur lue à une liste temporaire, puis transformer cette liste en `tuple` pour l'affichage. On renverra un `string`.

    ```python
    def afficherListe(L):
        '''Renvoie une représentation de la Liste sous forme d'une séquence commençant par la tête'''
        reponse = []
        # à compléter
        return str(tuple(reponse))
    ```

    📌 **Instructions d'utilisation** :

    ```python
    >>> a = insererTete(20, (15, (5, nouvelleListe())))
    >>> afficherListe(a)
    '(20, 15, 5)'
    ```

    ❓**Question** : Un utilisateur peut-il déduire l’implémentation interne de la liste en utilisant seulement les fonctions d’interface ?

    ??? success "📤 Solution :"

        ```python
        def afficherListe(L):
            '''Renvoie une représentation de la Liste sous forme d'une séquence commençant par la tête'''
            reponse = []
            while not estVide(L):
                reponse.append(lireTete(L))
                L = supprimerTete(L)
            return str(tuple(reponse))
        ```

        📌 **Réponse à la question** :
        Non. Grâce à notre interface, l’utilisateur manipule la structure abstraite sans jamais avoir à connaître sa représentation interne (des tuples emboîtés).

---

###  <H4 STYLE="COLOR:MAGENTA;">🧱 3.3.2. Implémentation plus souple avec les tuples</H4>

Nous aimerions maintenant accéder à **n'importe quelle valeur** de la liste, et non plus seulement la tête.

![Interface de lecture par position](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.012.png){width=50%; : .center }

✅ **Avantage** : cette implémentation suit fidèlement la logique (tête, queue)
⚠️ **Inconvénient** : certaines opérations deviennent plus coûteuses.

---

???+ question "🧪 Activité n° 7 : fonction `lireElement`"

    Créer la fonction `lireElement` en **réutilisant les fonctions précédentes**.
    On devra **supprimer la tête autant de fois que nécessaire** jusqu'à atteindre la position visée, puis la lire.

    📌 Syntaxe attendue :

    ```python
    lireElement(L:Liste, position:int) -> Elt
    ```

    ```python
    listeA = (12, 15, 18, 4)
    reponse = lireElement(listeA, 1)
    ```

    ✅ `reponse` vaut 15.

    ```python
    def lireElement(L, position):
        '''Renvoie l'élément en position `position` dans la Liste'''
        pass
    ```

    Exemples :

    ```python
    >>> a = insererTete(20, (15, (5, nouvelleListe())))
    >>> lireElement(a, 1)
    15
    >>> lireElement(a, 0)
    20
    >>> lireElement(a, 2)
    5
    ```

    ❓**Question** : quel est le **coût** de cette opération ?

    A : logarithmique

    B : linéaire

    C : quadratique

    D : exponentielle

    ??? success "📤 Solution :"

        ```python
        def lireElement(L, position):
            '''Renvoie l'élément à la position donnée dans la Liste'''
            for _ in range(position):
                L = supprimerTete(L)
            return lireTete(L)
        ```

        ✅ Réponse à la question : **B : linéaire**, car on parcourt la liste séquentiellement jusqu’à l’élément recherché. Il va falloir supprimer autant de tête que l'index voulu et ensuite on pourra lire la valeur.

    ---

???+ question "🧪 Activité n° 8 : fonction `insererElement`"

    Créer la fonction suivante :

    ```python
    insererElement(x:Elt, L:Liste, position:int) -> Liste
    ```

    🎯 Objectif : renvoyer une nouvelle liste dans laquelle l'élément `x` est inséré **à la position spécifiée**, en suivant un index débutant à 0.

    ```python
    listeA = (12, 15, 18, 4)
    listeB = insererElement(5, listeA, 2)
    ```

    ✅ `listeB` = (12, 15, **5**, 18, 4)

    ```python
    def insererElement(x, L, position):
        '''Renvoie une nouvelle liste avec x inséré à la position donnée'''
        pass
    ```

    Exemples :

    ```python
    >>> a = insererTete(20, (15, (5, nouvelleListe())))
    >>> afficherListe(a)
    '(20, 15, 5)'

    >>> a = insererElement(12, a, 1)
    >>> afficherListe(a)
    '(20, 12, 15, 5)'

    >>> a = insererElement(20, a, 2)
    >>> afficherListe(a)
    '(20, 12, 20, 15, 5)'
    ```

    ❓**Question** : Quel est le **coût** dans le pire des cas (insertion en fin de liste) ?

    A : logarithmique

    B : linéaire

    C : quadratique

    D : exponentielle

    ??? success "📤 Solution :"

        ```python
        # version itérative
        def insererElement(x, L, position):
        '''Renvoie une représentation de la Liste sous forme d'une séquence commençant par la tête '''
        L1= nouvelleListe()
        for i in range(position):
            a = lireTete(L)
            L = supprimerTete(L) 
            L1 = insererTete(a,L1)
        L = insererTete(x,L)
        while not estVide(L1):
            a = lireTete(L1)
            L1 = supprimerTete(L1)
            L = insererTete(a,L)
        return L 

        # version récursive
        def insererElement(x, L, position):
            '''Insère l’élément x à la position donnée dans la Liste'''
            if position == 0:
                return insererTete(x, L)
            else:
                return insererTete(lireTete(L), insererElement(x, supprimerTete(L), position - 1))
        ```

        ✅ Réponse à la question : **B : linéaire**. Si notre liste possède n éléments, on voudra le placer à l'index n-1.
        On remarque qu'on a n-1 opérations de suppressions de têtes puis n-1 opérations d'insertion de têtes.
        On a donc 2 * (n-1) opérations linéaires à effectuer.
        On a donc 2 n - 2 opérations.
        On voit donc que l'insertion possède un coût en O(n) : il s'agit d'une évolution linéaire.

📌 **Résumé des coûts** :

| Opération   | Coût (Θ) |
| ----------- | -------- |
| Lecture     | Θ(n)     |
| Insertion   | Θ(n)     |
| Suppression | Θ(n)     |

---



!!! info "Capytale : Structure liste (chainée) avec les lists de Python (activite_liste_list)"



### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667924"></a>**3.4. ❤️2<sup>ème</sup> implémentation de la structure liste (chaînée) avec les `lists` de Python❤️**</H3>

🧠 Si le type natif `list` se nomme ainsi, c'est bien qu'il permet l'**implémentation de Liste**.
⚙️ En interne, il s'agit d’un **tableau dynamique** qui possède plus de fonctions d'interface que le type abstrait **TABLEAU DYNAMIQUE**.
🔁 La structure de données `list` est donc un **savoureux mélange de fonctionnalités** issues des **tableaux** et des **listes**.

---

???+ question "🧪 Activité n° 9 : structure liste avec des `lists` – fonctions `nouvelleListe`, `estVide`, `lireElement`"

    Ces fonctions restent les mêmes, même si on utilise les `lists` de Python plutôt que des tableaux :

    ```python
    '''Implémentation 3 de type abstrait Liste en utilisant le type natif liste de Python

    Liste désigne la structure de données que nous utilisons pour gérer les listes.
    Elt désigne la structure de données pouvant être un élément de nos listes.

    Description rapide de l'interface :
    -----------------------------------

    1 ::: nouvelleListe() -> Liste
    2 ::: estVide(liste:Liste) -> bool
    3 ::: lireElement(liste:Liste, index:int) -> Elt 
    4 ::: insererElement(x:Elt, liste:Liste, position:int) -> Liste
    5 ::: supprimerPosition(liste:Liste, position:int)  -> Liste
    6 ::: afficherListe(liste:Liste) -> str
    '''

    def nouvelleListe():
        '''Renvoie une liste vide '''
        pass

    def estVide(L):
        '''Renvoie True si la liste est vide '''
        pass

    def lireElement(L, index=-1):
        '''Renvoie la valeur stockée à l'index voulu '''
        pass
    ```

    ??? success "📘 Solution :"

        ```python
        def nouvelleListe():
            return []

        def estVide(L):
            return L == []

        def lireElement(L, index=-1):
            return L[index]
        ```

---

???+ question "🧪 Activité n° 10 : structure liste avec des `lists` – fonction `insererElement`"

    On connaît déjà la méthode `append`, mais ici **on l’évite**, car elle **modifie la liste en place**.
    La fonction devra toujours **renvoyer une copie modifiée**.

    💡 Astuce : s'aider des fonctions `supprimerTete(L)` et `ajouterTete(x,L)`.

    ```python
    def insererElement(x, L, position):
        '''Renvoie une Liste en insérant x à la position position. '''
        pass

    L = nouvelleListe()
    L = ajouterTete(2, L)
    L = ajouterTete(3, L)
    L = ajouterTete(1, L)
    print(L)
    L = insererElement(25, L, 1)
    print(L)
    ```


    ??? success "📘 Solution :"

        ```python
        def supprimerTete(L):
            return L[1:]

        def ajouterTete(x,L):
            return [x]+L

        def insererElement(x, L, position):
            '''Renvoie une Liste en insérant x à la position position. '''
            L1 = nouvelleListe()
            for i in range(position):
                a = lireElement(L,0)
                L = supprimerTete(L)
                L1 = ajouterTete(a,L1)
            L = ajouterTete(x, L)
            while not estVide(L1):
                a = lireElement(L1,0)
                L1 = supprimerTete(L1)
                L = ajouterTete(a,L)
            return L
        
        L = nouvelleListe()
        L = ajouterTete(2, L)
        L = ajouterTete(3, L)
        L = ajouterTete(1, L)
        print(L)
        L = insererElement(25, L, 1)
        print(L)
        ```

**Remarque** il existe également une méthode nommée insert qui permet de faire la même chose en choisissant la position de l'insertion.

**Erreur courante :** Ne faites donc jamais ceci : ❌ `insert()` est une **fonction-procédure** : elle retourne `None` !.
```python
reponse = [element for element in L]
return reponse.insert(position, x)
```
---


???+ question "🧪 Activité n° 11 : structure liste avec des `lists` – fonction `supprimerPosition`"

    Comme pour `append`, la méthode `pop()` modifie la liste en place. On s'en sert uniquement pour ses effets de bord.

    ```python
    def supprimerPosition(L, position):
        '''Renvoie une nouvelle liste où on a supprimé l'élément situé à la position fournie'''
        pass

    L = supprimerPosition(L, 2)
    print(L)
    ```

    

    ??? success "📘 Solution :"

        ```python
        def supprimerPosition(L, position):
            '''Renvoie une nouvelle liste où on a supprimé l'élément situé à la position fournie'''
            L1 = nouvelleListe()
            for i in range(position):
                a = lireElement(L,0)
                L = supprimerTete(L)
                L1 = ajouterTete(a,L1)
            L = supprimerTete(L)
            while not estVide(L1):
                a = lireElement(L1,0)
                L1 = supprimerTete(L1)
                L = ajouterTete(a,L)
            return L

        L = supprimerPosition(L, 2)
        print(L)
        ```
⚠️ **À ne pas faire :**

    ```python
    reponse = [element for element in L]
    return reponse.pop(position)
    ```

    ❌ Cela retourne l'élément supprimé, **pas la nouvelle liste**.
---

???+ question "🧪 Activité n° 12 : structure liste avec des `lists` – fonction `afficherListe`"

    On ajoute ici une fonction **d’affichage globale** pour respecter l’interface du type abstrait Liste :

    ```python
    def afficherListe(L):
        '''Renvoie une représentation de la Liste sous forme d'une séquence commençant par la tête'''
        return str(tuple(L))

    print(afficherListe(L))
    ```

    📎 On affiche la structure comme une **séquence immuable**, ce qui est plus lisible que la syntaxe brute d’une `list`.



---


!!! info "Capytale : Structure liste (chainée) avec POO (activite_liste_POO)"


### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667925"></a>**3.5. ❤️ 3<sup>ème</sup> implémentation de la structure liste (chaînée) avec POO ❤️**</H3>

🧠 Une **liste chaînée** est une structure composée de **cellules** ou **maillons**, comme une chaîne métallique.
Chaque cellule contient deux éléments essentiels :

* 📦 Le **contenu** de la cellule
* 🔗 **L’adresse** ou **référence** vers la cellule suivante

👉 Et **rien d’autre** !

---

🔍 **Représentation visuelle**

Voici la représentation typique d’une liste chaînée :

![Liste chaînée – représentation](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.014.png){width=50%; : .center }

🧩 Les cellules sont alignées logiquement, mais pas forcément physiquement en mémoire. Ce sont les **références** qui relient les cellules entre elles.

---

➕ **Insertion d’un nouvel élément**

Insérer un élément consiste simplement à :

1. Créer un lien de l’élément précédent vers le **nouvel élément**
2. Lier ce **nouvel élément** à l’ancien suivant

![Insertion dans une liste chaînée](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.015.png){width=50%; : .center }

✅ Cela ne nécessite **que 2 opérations**, peu importe la taille de la liste. On parle donc d’un **coût d’insertion constant**.

---

🏗️ **Cas d'une grosse liste**

Même dans une grande liste, l’insertion reste rapide :

![Grosse insertion](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.016.png){width=50%; : .center }

---

🔄 **Changement de tête**

Remplacer la tête dans une liste chaînée est également très efficace :

![Changement de tête](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.017.png){width=50%; : .center }

⛔ En comparaison, un **tableau** impose de **décaler** tous les éléments pour insérer en tête.

---

❌ **Inconvénient : la lecture**

📉 Lire un élément en milieu de liste est plus coûteux :
Il faut suivre les références une à une jusqu’à la cellule voulue.

✔️ En revanche, avec un **tableau**, l’accès à l’élément à l’indice `i` est **direct**, donc plus rapide.

---

⚙️ **Structure d’une cellule (ou maillon)**

Chaque cellule (Node) de la liste chaînée est représentée par une **classe `Node`**, constituée de deux attributs :

* `v` : la **valeur** (tête)
* `n` : la **référence** (next) vers la **cellule suivante** (queue)

---

#### <H4 STYLE="COLOR:MAGENTA;"> **3.5.1. Création de la cellule `Node`**</H4>

???+ question "📝 **Activité 13 : Création de la classe Cellule (`Node`)**"

    Chaque cellule est constituée d’une **tête** et d’un **pointeur**.
    Crée une classe `Node` avec un constructeur qui accepte deux paramètres (`value`, `next`) et les stocke dans les attributs `v` et `n`.

    ```python
    class Node:
        '''Classe permettant de créer des cellules-maillons basiques'''
        def __init__(self, value, next=None):
            pass
    ```

    Teste ensuite les créations suivantes :

    ```python
    >>> c1 = Node(5, None)
    >>> c2 = Node(15, c1)
    >>> c3 = Node(25, c2)
    >>> c4 = Node(35, c3)
    ```

    ??? success "📤 Solution :"

        ```python
        class Node:
            '''Classe permettant de créer des cellules-maillons basiques'''
            def __init__(self, value, next=None):
                self.v = value
                self.n = next
        ```

        🧪 Avec ces instructions :

        ```python
        >>> c1 = Node(5, None)
        >>> c2 = Node(15, c1)
        >>> c3 = Node(25, c2)
        >>> c4 = Node(35, c3)
        ```

---






???+ question "📝 **Activité n°14 : Représentation de la structure chaînée**"

    Représenter sur **feuille** la **structure séquentielle linéaire** (schéma des cellules) créée par les instructions précédentes.

    ??? success "📤 Solution :"
        ```
        [35 | ●] → [25 | ●] → [15 | ●] → [5 | ∅]
  c4          c3         c2        c1
        ```

---

???+ question "📝 **Activité n°14bis : Programmation défensive**"

    Notre cellule possède encore un léger problème :
    On pourrait lui transmettre **n’importe quoi** dans `next`, pas obligatoirement un objet `Node` ou `None`.

    ➡️ On va donc **protéger** notre code en imposant que `next` soit bien une instance de `Node` ou `None`.

    🧩 Compléter ce constructeur avec une assertion :

    ```python
    class Node:
        '''Classe permettant de créer des cellules-maillons basiques'''
        def __init__(self, value, next=None):
            assert isinstance(next, ...) or next == ...
            # ce que vous avez écrit précédemment 
    ```

    ??? success "📤 Solution :"

        ```python
        class Node:
            '''Classe permettant de créer des cellules-maillons basiques'''
            def __init__(self, value, next=None):
                assert isinstance(next, Node) or next == None
                self.v = value
                self.n = next
        ```

---

???+ question "🧪 **Activité n°15 : Tester les contraintes**"

    Tester les instructions suivantes :

    ```python
    >>> a = Node('Marie-Antoinette', None)
    >>> b = Node('Louis XVI', a)
    >>> c = Node('Louis XV', 'Louis XVI')
    ```

    **Question : Quel est le problème ?**

    ??? success "📤 Solution :"

        💥 La documentation n'a rien à voir dans cette histoire. Erreur sur la dernière ligne :

        `'Louis XVI'` est une **chaîne de caractères**, pas une **instance de Node**.

        Grâce à l’assertion, le constructeur **refuse** cette valeur inappropriée, ce qui évite des comportements imprévisibles.

---

📌 **Attention terminologique :**

L’attribut `n` n’est **pas** la queue complète !
C’est **le premier maillon** de la queue. Toute la suite est encore à parcourir.

---

🔁 **Lecture de la liste avec une méthode récursive**

On va créer une méthode `returnFinalValue` qui :

1. Affiche les valeurs des cellules une par une
2. Renvoie la valeur de la **dernière cellule** (celle qui n’a pas de `next`)

![Lecture récursive](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.018.png){width=50%; : .center }

Si on part ici de la tête qui contient le string "Lundi", on devrait lire la séquence des jours et renvoyer la référence de la dernière cellule, celle qui contient "Dimanche".

---

???+ question "🧠 **Activité n°16 : Création de la méthode `returnFinalValue`**"

    **Prototype :**

    ```python
    returnFinalValue(self) -> valeur
    ```

    C’est une méthode **récursive**.
    Elle suit le principe suivant :

    * Si `self.n` est `None`, c’est la dernière cellule → on retourne `self.v`
    * Sinon, on appelle `returnFinalValue()` sur la cellule suivante

    **Questions associées :**

    1. Quelle est la condition d’arrêt ?
    2. Quel est le cas de base ?
    3. Comment la fonction progresse-t-elle dans la liste ?

    ??? success "📤 Solution :"
        1. if self.n == None:
        2. self # self.v est possible mais ce n’est pas demandé
        3. self.n.fonction

    Voici le squelette à compléter :

    ```python
    class Node:
        '''Classe permettant de créer des cellules-maillons basiques'''
        def __init__(self, value, next=None):
            # ce qui a été fait précédemment

        def returnFinalValue(self):
            pass


    di = Node("Dimanche")
    sa = Node("Samedi", di)
    ve = Node("Vendredi", sa)
    je = Node("Jeudi", ve)
    me = Node("Mercredi", je)
    ma = Node("Mardi", me)
    lu = Node("Lundi", ma)
    ```

    Tester la méthode returnFinalValue avec 

    - lu

    puis

    - je

    ??? success "📤 Solution :"

        ```python
        class Node:
            def __init__(self, value, next=None):
                assert isinstance(next, Node) or next == None
                self.v = value
                self.n = next

            def returnFinalValue(self):
                if self.n is None:
                    return self.v
                else:
                    return self.n.returnFinalValue()
        ```

🖨️ **Affichage de la liste entière**

???+ question "📺 **Activité n°17 : méthode `__str__` pour l’affichage**"

    Tester l'affichage de 
    - lu

    puis

    - je

    Qu'est ce que vous remarquez ?

    ??? success "📤 Solution :"
        ```python
        print(lu)
        print(je)
        ```
        **Observation :**
        On voit des objets `Node` comme `<__main__.Node object at ...>`. Ce sont les adresses en mémoire de chaque Node qui sont évidement différentes.
        C’est peu lisible.

    ➡️ On va donc écrire une méthode `__str__` qui affiche toutes les valeurs liées.

    Format attendu :

    ```
    >>> print(lu)
    Lundi-Mardi-Mercredi-Jeudi-Vendredi-Samedi-Dimanche
    >>> print(je)
    Jeudi-Vendredi-Samedi-Dimanche
    ```

    💡 Remarque : il **ne faut pas afficher `None` à la fin**.

    Compléter ce squelette :

    ```python
    class Node:
        def __init__(self, value, next=None):
            # ce qui a été fait précédemment

        def returnFinalValue(self):
            # ce qui a été fait précédemment

        def __str__(self):
            pass


    di = Node("Dimanche")
    sa = Node("Samedi", di)
    ve = Node("Vendredi", sa)
    je = Node("Jeudi", ve)
    me = Node("Mercredi", je)
    ma = Node("Mardi", me)
    lu = Node("Lundi", ma)

    print(lu)
    print(je)
    ```

    ??? success "📤 Solution :"

        ```python
        def __str__(self):
            if self.n :
                return str(self.v) + '-' + str(self.n)
            else :
                return str(self.v)
        ```

        ✅ On obtient une chaîne lisible représentant **toute la séquence** de maillons depuis le nœud initial.

---




#### <H4 STYLE="COLOR:MAGENTA;">🧱 **3.5.2. Création de la Liste Chaînée `Liste`**</H4>

???+ question "🔧 **Activité n°18 : Création de la classe Liste**"

    Créer une **classe Liste** qui représentera la liste chaînée complète. Elle contient :

    * Un seul attribut `head` représentant la **tête de la liste** (un objet `Node`)
    * Ce `head` est `None` si la liste est vide

    💬 Initialement, la liste est vide, donc `head = None`. Ensuite, chaque cellule pointe vers la suivante jusqu’à la dernière dont le `next` est `None`.

    ```python
    class Node:
        '''Classe permettant de créer des cellules-maillons basiques'''
        def __init__(self, value, next=None):
            # ce qui a été fait précédemment

        def returnFinalValue(self):
            # ce qui a été fait précédemment

        def __str__(self): 
            # ce qui a été fait précédemment

    class Liste:
        '''Classe implémenter une Liste sous forme Liste chaînée '''
        def __init__(self, head = None):
            assert type(head) == ... or head == ...
            pass
    
    # Programme principal
    di = Node("Dimanche")
    sa = Node("Samedi", di)
    ve = Node("Vendredi", sa)
    je = Node("Jeudi", ve)
    me = Node("Mercredi", je)
    ma = Node("Mardi", me)
    lu = Node("Lundi", ma)
    list1 = Liste(lu)
    ```
    

    ??? success "❇️ Solution :"

        ```python
        class Liste:
            '''Classe pour implémenter une Liste sous forme de liste chaînée'''
            def __init__(self, head=None):
                assert type(head) == Node or head is None
                self.head = head
        ```

    🔍 **Questions de compréhension** :

    1. Comment obtenir dans la console le contenu de la tête en utilisant `list1` ?
    

    2. Comment obtenir le contenu de l’élément suivant ?
    

    3. Et encore derrière ?
   
    ??? success "❇️ Solution :"

        → `list1.head.v`

        → `list1.head.n.v`

        → `list1.head.n.n.v`

🧠 Le constructeur utilise `type()` au lieu de `isinstance()` pour montrer qu’il existe deux façons de vérifier le type d’un objet.

---

#### <H4 STYLE="COLOR:MAGENTA;">🔁 **3.5.3. Création d'une interface mutable**</H4>

![Illustration interface liste chaînée](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.019.png){width=50%; : .center }

Voici les **méthodes prévues** dans notre interface :


1. ```nouvelleList()``` correspond au constructeur `__init__() -> Liste` : on crée une nouvelle liste vide. 

1. ```isEmpty(L:Liste) -> bool``` : renvoie un booléen qui vaut True si la liste L transmise est une liste vide.
```
listeA = Liste()
isEmpty(listeA) va donc renvoyer l'équivalent de True.
```
3 ```insertPosition(x:Elt, L:Liste, position:int) -> None``` : on **modifie sur place** la liste : l'élément fourni x est maintenant l'élément de la liste situé en position position. On prendra ici un système de position lié à un index commençant à 0.
```
listeA peut être représentée par (12, 15, 18, 4)

insertPosition(5, listeA, 2)
listeA peut alors être représentée par (12, 15, 5, 18, 4).
```
4 ```delPosition(L:Liste, position:int) -> None``` : on **modifie sur place** la liste : l'élément en position position est supprimé, rendant la liste moins longue.
```
listeA peut être représentée par (12, 15, 18, 4)

delPosition(listeA, 1)
listeA peut alors être représentée par (12, 18, 4).
```
5 ```readPosition(L:Liste, position:int) -> Elt``` : on **renvoie** l'élément stocké en position position
```
listeA peut être représentée par (12, 15, 18, 4)

reponse = readPosition(listeA, 1)
reponse peut alors être représentée par 15.
```

---

???+ question "📥 **Activité n°19 : Méthode `isEmpty`**"

    Créer une méthode d’interface `isEmpty()` qui retourne `True` si la liste est vide, `False` sinon.


    🧪 À tester :

    ```python
    >>> list1.isEmpty()
    False
    >>> list2 = Liste()
    >>> list2.isEmpty()
    True
    ```

    ??? success "❇️ Solution :"

        ```python
        class Liste:
            def __init__(self, head=None):
                assert type(head) == Node or head is None
                self.head = head

            def isEmpty(self):
                return self.head is None
        ```

---




???+ question "📥 Activité n° 20 :structure liste avec de la POO, Création de la structure méthode `insertHead` :"

    🧠 Créer une méthode d’interface `insertHead`. La solution est :

    * de mémoriser l’ancienne entête dans une variable temporaire `temporary`,
    * de créer une instance de `Node` dont la valeur stockée est `newData` et qui pointe en sortie vers l’ancienne tête,
    * de modifier l’attribut `head` de la Liste pour qu’il corresponde bien à la nouvelle instance de `Node`.



    📎 Ajouter la méthode à la classe `Liste` :

    ```python
    def insertHead(self, newData): 
        pass
    ```


    🧪 Tester :

    ```python
    >>> list1.insertHead('sunday')
    >>> list1.insertHead('saturday')
    >>> list1.head.v
    'saturday'
    >>> list1.head.n.v
    'sunday'
    >>> list1.head.n.n.v
    'Lundi'
    >>> list1.head.n.n.n.v
    'Mardi'
    ```

    ??? success "❇️ Solution :"

        ```python
        def insertHead(self, newData):
            temporary = self.head
            self.head = Node(newData, temporary)
        
        # plus simplement
        def insertHead(self, newData): 
            self.head = Node(newData, self.head)
        ```

---

📘 **Pour réaliser la méthode `insertPosition`** :

Par exemple, pour insérer une Cellule en position 2, il faudra :

* Mémoriser l'adresse nommée **predecesseur** de l'élément en position 1 (celle de contenu B ici),
* Mémoriser l'adresse nommée **successeur** de l'élément en position 2 actuellement (celle de contenu C ici),
* Créer une nouvelle cellule **nouvelle** (celle de contenu Z ici) et la faire pointer vers **successeur**,
* Faire pointer **predecesseur** sur notre **nouvelle** cellule.

Avant d'insérer la nouvelle Cellule en position 2, il faut mémoriser les identifiants des cellules contenant B (**predecesseur**, "index" 1) et C (**successeur**, "index" 2).

📷 **Illustration avant modification :**

![Avant insertion](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.020.png){width=50%; : .center }

📷 **Illustration après modification :**

![Après insertion](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.021.png){width=50%; : .center }

---

📌 **Quelques précisions :**

* Pour insérer en position 1 : **predecesseur** est l'élément en position 0, soit... la tête de la liste.
* Pour insérer en position 2 : **predecesseur** sera l'élément en position 1. Il faut donc faire un bond en avant depuis la tête.
* Pour insérer en position 3 : **predecesseur** sera l'élément en position 2. Il faut donc faire un bond en avant depuis la tête.
* Si je veux insérer en position **position** : **predecesseur** sera la Cellule en position **position - 1**. Il faut donc faire un bond en avant depuis la tête.

---

???+ question "📥 Activité 21 :structure liste avec de la POO, Création de la structure méthode `insertPosition` :"

    Voici une méthode d'interface `insertPosition` :

    ```python
    insertPosition(self, newData:Elt, position:int) -> None
    ```

    ➡️ Elle modifie sur place la liste : l'élément fourni `newData` est maintenant l'élément de la liste situé en position `position`.

    On prendra ici un système de position lié à un **index commençant à 0**.



    🧠 Lorsqu'on veut insérer ailleurs qu'à la tête, cette méthode va :

    1. partir de la tête, effectuer `position - 1` sauts vers la cellule suivante, et mémoriser l'identifiant de cette cellule dans **predecesseur** ;
    2. mémoriser dans **successeur** la référence de la cellule actuellement à la suite de **predecesseur** ;
    3. créer la **nouvelle Cellule**, et la faire pointer vers **successeur** ;
    4. modifier **predecesseur** pour qu'elle pointe vers **nouvelle**.

    📷 Illustration :

    ![Insertion position](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.022.png){width=60%; : .center }



    📎 Ajouter la méthode suivante à la classe `Liste` :

    ```python
    def insertPosition(self, newData, position):
        pass
    ```


    ❓ **Question** :
    Analyser le code pour parvenir à identifier les lignes où sont effectuées précisément les actions **1 à 4** précédentes.



    🧪 Tester :

    ```python
    >>> list1.insertPosition('Tuesday', 1)
    >>> list1.head.v
    'Lundi'
    >>> list1.head.n.v
    'Tuesday'
    >>> list1.head.n.n.v
    'Mardi'
    ```

    ??? success "❇️ Solution :"

        ```python
        def insertPosition(self, newData, position):
            if position == 0:  # On retrouve la fonction insertHead en réalité
                self.insertHead(newData)
            else :
                previousNode = self.head
                for i in range(position-1): #On avance jusqu'à position-1 pour trouver previousNode
                    previousNode = previousNode.n
                previousNode.n = Node(newData, previousNode.n)
        ```

        ligne 5 on part de la tête
        ligne 6 effectuer position-1 saut vers la cellule suivante
        ligne 7 mémoriser l'identifiant de cette cellule dans predecesseur
        ligne 8 predecesseur sera la Cellule en position position - 1

---




???+ question "🧩 Activité n° 22 :Structure liste avec de la POO, Analyse du coût d'insertion"

    💡 L'insertion pure ne concerne que les lignes suivantes :

    ```python
    # nextNode = previousNode.n  # on mémorise la cellule qu'il faudra "déplacer"
    # newNode = Node(newData, nextNode)
    # previousNode.n = newNode
    # qui se résume par
    self.head = Node(newData, self.head)
    ```

    📌 Ici le coût est bien **constant**.

    Mais que peut-on dire du coût de la **recherche** de la Cellule `predecesseur` dans le pire des cas ?

    ??? success "❇️ Solution :"
        Cependant, pour insérer un élément à une position donnée (autre que le début de la liste), il faut d'abord identifier son prédécesseur dans la liste. La recherche du prédécesseur nécessite un parcours séquentiel des nœuds à partir de la tête jusqu'à atteindre la position voulue.

        Dans le pire des cas, cette recherche implique de traverser toute la liste, c'est-à-dire n−1 nœuds pour une liste de taille 
        n. Le coût est donc linéaire, soit O(n).

    ```python
    previousNode = self.head
    for etape in range(1, position):  # On avance jusqu’à (position - 1) pour trouver previous
        previousNode = previousNode.n
    ```

    ❓ **Au total**, que peut-on alors dire du coût de l'insertion ?

    ??? success "❇️ Solution :"

        Si l’on insère en tête de liste, on n’a pas besoin de chercher le prédécesseur, donc le coût est constant : O(1).

        En revanche, pour une insertion à une position quelconque, il faut souvent trouver le prédécesseur, ce qui coûte O(n) dans le pire des cas.

        ➡️ Donc, le coût total de l’insertion dans une liste chaînée est en général O(n), à cause de la recherche du prédécesseur.


    
---

⛅ C’est un peu **décevant** du coup...

🔁 On retrouve une **insertion à coût constant**, **mais uniquement si on connaît la cellule précédente**.

En réalité, la grande force des listes ne vient pas de l’insertion d’une cellule individuelle (souvent on ne connaît pas sa référence), mais de **l’insertion d’une liste à la suite d’une autre**.

On parle alors de **concaténation de listes**, comme avec les chaînes de caractères.

---

🧠 Imaginons deux listes contenant 20 000 éléments chacune.

➡️ Si on souhaite insérer la deuxième liste **à la suite** de la première, cela devient **très coûteux** avec des tableaux :

1. Réserver une nouvelle mémoire de 40 000 cases :

   ![Création d'un nouveau tableau](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.022.png){width=60%; : .center }

2. Copier les 20 000 éléments du premier tableau :

   ![Déplacement des éléments de A](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.023.png){width=60%; : .center }

3. Copier ensuite les 20 000 éléments du deuxième tableau :

   ![Déplacement des éléments de B](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.024.png){width=60%; : .center }

---

🔗 Avec une **liste chaînée**, il suffit de connaître la **dernière cellule de la première liste** (20 000 lectures au pire) et de la faire pointer vers la **tête** de la deuxième liste.

> On pourra donc écrire quelque chose comme `lst1 + lst2`, ce qui signifie : faire pointer la cellule de fin de la première liste vers la tête de la deuxième.

📌 Illustration du lien entre les deux :

![Changement de référence](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.025.png){width=60%; : .center }

---

📚 En conclusion, le **type abstrait LISTE** peut s’implémenter de plusieurs manières différentes :

* **Structure de données tableau** : accès rapide à un index (lecture à coût constant)
* **Liste chaînée** : insertion rapide (coût constant parfois), idéale pour concaténer ou insérer sans tout déplacer

👉 En fonction des **besoins de l’algorithme**, on choisira l’implémentation la plus adaptée.

---

???+ question "🧪 Activité n° 23 :Créer une structure fonction `afficherListe` et `recupererValeur`"

    🔍 En utilisant l’interface, l’utilisateur peut-il se douter que les données sont stockées sous forme de **liste chaînée** composée d’objets ?

    🛠️ Ajouter les **2 fonctions** :

    ```python
    def afficherListe(L):
        tableau = recupererValeur(L.head)
        return str(tuple(tableau))

    def recupererValeur(cellule):
        if cellule.n == None:
            return [cellule.v]
        else:
            return [cellule.v] + recupererValeur(cellule.n)

    # Programme principal
    di = Node("Dimanche")
    sa = Node("Samedi", di)
    ve = Node("Vendredi", sa)
    je = Node("Jeudi", ve)
    me = Node("Mercredi", je)
    ma = Node("Mardi", me)
    lu = Node("Lundi", ma)
    list1 = Liste(lu)
    print(afficherListe(list1))
    ```

    ??? success "❇️ Solution :"

        Ces deux fonctions permettent de reconstruire **un affichage lisible** depuis une structure de type liste chaînée.

        * `recupererValeur` utilise une **fonction récursive** pour parcourir les cellules,

        * `afficherListe` transforme le résultat en tuple pour un affichage plus clair.

---

???+ question "🧹 Activité n° 24 : Créer la méthode `delPosition` pour supprimer un élément"

    🛠️ Compléter la méthode :

    ```python
    def delPosition(self, position):
        pass
    ```

    🧪 Tester :

    ```python
    >>> afficherListe(list1)
    "('Lundi', 'Mardi', 'Mercredi', 'Jeudi', 'Vendredi', 'Samedi', 'Dimanche')"
    >>> list1.delPosition(3)
    >>> afficherListe(list1)
    "('Lundi', 'Mardi', 'Mercredi', 'Vendredi', 'Samedi', 'Dimanche')" 
    ```

    ??? success "❇️ Solution :"

        ```python
        def delPosition(self, position):
            if not self.isEmpty():
                if position==0:
                    self.head = self.head.n
                else:
                    newNode = self.head
                    for i in range(position-1):
                        newNode = newNode.n
                    newNode.n = newNode.n.n
        ```

🧠 Cette méthode :

* Gère d’abord le **cas particulier** où l’on supprime la tête (`position == 0`),
* Puis, pour toute autre position, elle repère la cellule à supprimer (via le **prédécesseur**) et **reconnecte** les cellules entre elles en **sautant** celle à supprimer.

---


???+ question "🧠 Activité n° 25 : structure liste avec de la POO, Création de la structure autres méthodes"

    🧩 Réaliser maintenant la méthode d'interface de lecture des valeurs. Voici le prototype :

    ```python
    readPosition(self:Liste, position:int) -> Elt
    ```

    🔎 On renvoie l'élément stocké en position `position`.

    ```python
    def readPosition(self, position):
        pass
    ```

    🧪 Tester :

    ```python
    >>> list1.readPosition(2)
    'Mercredi'
    ```

    ??? success "✅❇️ Solution :"

        ```python
        def readPosition(self, position):
            if not self.isEmpty():
                newNode = self.head
                for i in range(position):
                    newNode = newNode.n
                return newNode.v
        ```

---

!!! info "🧪 Capytale : Structure pile avec les listes de Python (activite_pile_list)"

## <H2 STYLE="COLOR:BLUE;">🥞 <a name="_toc151667926"></a>**4. Les piles**</H2>

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667927"></a>**4.1. Généralités 📚**</H3>

💻 En informatique, une **pile** (en anglais **stack**) est une structure de données fondée sur le principe **« dernier arrivé, premier sorti »** (**LIFO** pour *Last In, First Out*), ce qui veut dire que les derniers éléments ajoutés à la pile seront les premiers à être récupérés.

🍽️ Le fonctionnement est donc celui d’une pile d’assiettes : on ajoute des assiettes sur la pile, et on les récupère dans l’ordre inverse, en commençant par la dernière ajoutée.

📌 Voici quelques exemples d’usage courant d’une pile :

* 🌐 Dans un navigateur web, une pile sert à mémoriser les **pages Web visitées**.
* 🧮 L’évaluation des **expressions mathématiques** en notation post-fixée (ou polonaise inverse).
* ✏️ La fonction « Annuler la frappe » (*Undo*) dans un traitement de texte.

---

🧰 Pour implémenter une pile, on utilise quatre **fonctions primitives** :

* 🔹 **pileVide()** : renvoie une pile vide
* 🔹 **estVide(pile)** : renvoie un booléen indiquant si la pile est vide
* 🔹 **empiler(pile, element)** : ajoute un élément à la pile (**push**)
* 🔹 **depiler(pile)** : retire un élément de la pile et le renvoie (**pop**)

---

📖 **Exemple d’utilisation :**

Soit une pile P composée des éléments suivants :
`12, 14, 8, 7, 19, 22` (le sommet est 22)
🔁 Pour chaque exemple, on repart de la pile d’origine :

* **pop(P)** → renvoie 22 → sommet devient 19
* **push(P,42)** → pile devient `... 19, 22, 42`
* **sommet(P)** → renvoie 22
* **pop(P)** x6 → pile vide → **pile\_vide(P)** = True
* **pop(P)** x1 → reste 5 éléments → **taille(P)** = 5

📝 **Remarque** : pour lire le sommet **sans modifier** la pile, il faut le dépiler puis le rempiler.

---



### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667928"></a>**4.2. ❤️1<sup>ère</sup> implémentation de la structure pile avec les listes de Python❤️**</H3>

📌 Nous utiliserons une simple liste pour représenter la pile.
🔧 Les méthodes `append()` et `pop()` jouent déjà les rôles de `empiler()` (`push()`) et `depiler()` (`pop()`).

---

???+ question "🔧 Activité n° 26 : Structure pile avec les listes"

    ✍️ Compléter la **structure de base** suivante :

    💬 **Remarque** : La fonction `empiler` ne renvoie rien.

    ⚠️ **Attention aux effets de bord** :

    **pile += [element] (opérateur d'addition avec affectation):**

    - C'est une opération sur place pour les objets mutables comme les listes.

    - Cela modifie directement la liste originale référencée par pile.

    - L'objet reste le même en mémoire.

    **pile = pile + [element] (concaténation suivie d'affectation):**

    - C'est une opération de création d'un nouvel objet.

    - L'expression pile + [element] crée une nouvelle liste en concaténant pile et [element].

    - L'affectation pile = ... fait alors pointer le nom pile vers ce nouvel objet. Mais si la variable pile est passée à la fonction par référence (comme c'est souvent le cas avec les objets mutables en Python), cela coupe le lien avec l'objet original.

    ```python
    '''Implémentation de type abstrait Pile en utilisant les listes de Python'''

    def pileVide() :
        pass

    def estVide(pile) :
        pass

    def empiler(pile, element) :
        # 1ère façon 
        #pile.append(element) 
        # 2ème façon
        pass

    def depiler(pile) :
        if not estVide(pile):
            # 1ère façon 
            # return pile.pop()
            # 2ème façon
            pass
        pass

    # Programme principal
    if __name__ == '__main__':
        ma_pile = pileVide()
        assert estVide(ma_pile) == True
        empiler(ma_pile, 'Lundi')
        empiler(ma_pile, 'Mardi')
        empiler(ma_pile, 'Mercredi')
        assert estVide(ma_pile) == False
        assert depiler(ma_pile) == 'Mercredi'
        assert depiler(ma_pile) == 'Mardi'
        assert depiler(ma_pile) == 'Lundi'
        assert depiler(ma_pile) == 'Pile vide'
    ```

    ??? success "🎯✅ Solution :"

        ```python
        '''Implémentation de type abstrait Pile en utilisant les listes de Python'''

        def pileVide():
            return []

        def estVide(pile):
            return pile == []

        def empiler(pile, element):
            pile.append(element)  # méthode en place
            # pile += [element]   # aussi en place, mais attention aux effets de bord

        def depiler(pile):
            if not estVide(pile):
                # 1ère façon 
                # return pile.pop()
                
                # 2ème façon
                val = pile[-1]  
                pile[:] = pile[:-1]   # ou del pile[-1] qui est plus performant
                return val
            return 'Pile vide'

        # Programme principal
        if __name__ == '__main__':
            ma_pile = pileVide()
            assert estVide(ma_pile) == True
            empiler(ma_pile, 'Lundi')
            empiler(ma_pile, 'Mardi')
            empiler(ma_pile, 'Mercredi')
            assert estVide(ma_pile) == False
            assert depiler(ma_pile) == 'Mercredi'
            assert depiler(ma_pile) == 'Mardi'
            assert depiler(ma_pile) == 'Lundi'
            assert depiler(ma_pile) == 'Pile vide'
        ```

---




???+ question "🧱 Activité n° 27 : Structure pile avec les listes"

    🎯 On va rajouter à la structure de base précédente deux fonctions : `taille` et `sommet`
    📌 Elles permettent respectivement de :

    * retourner la **taille de la pile** (**sans utiliser `len`** ❌)
    * retourner le **sommet de la pile** (**sans utiliser les indices** ❌)

    💡 On n'utilisera que les fonctions primitives précédentes (`empiler`, `depiler`, etc.)
    📦 On pourra s’aider d’une **pile auxiliaire** pour restaurer l’état initial.

    ```python
    def taille(pile):
        pass

    def sommet(pile):
        pass

    # Programme principal
    if __name__ == '__main__':
        ma_pile = pileVide()
        empiler(ma_pile, 'Lundi')
        empiler(ma_pile, 'Mardi')
        empiler(ma_pile, 'Mercredi')
        assert taille(ma_pile) == 3
        assert sommet(ma_pile) == 'Mercredi'
    ```

    ??? success "✅❇️ Solution :"

        ```python
        def taille(pile):
            compteur = 0
            pile_temp = pileVide()
            while not estVide(pile):
                empiler(pile_temp, depiler(pile))
                compteur += 1
            while not estVide(pile_temp):
                empiler(pile, depiler(pile_temp))
            return compteur

        def sommet(pile):
            assert pile, "La pile est vide" 
            temporary = depiler(pile)
            empiler(pile, temporary)
            return temporary
        ```

---

!!! info "💡 Capytale : Structure pile avec la POO et les lists de Python (activite_pile_POO_list)"

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667929"></a>**4.3. ❤️2<sup>ème</sup> implémentation de la structure pile avec la POO et les lists de Python❤️**</H3>

---

???+ question "🏗️ Activité n° 28 : Structure pile avec la POO et les lists de Python"

    Créer une classe `Pile` qui construit une liste vide, puis compléter les autres méthodes de la classe :

    ```python
    '''Implémentation 3 de type abstrait Liste en utilisant la POO et les listes de Python'''

    class Pile:
        '''Classe permettant de créer des piles'''
        def __init__(self):
            pass

        def estVide(self) :
            pass

        def empiler(self, element) :
            # 1ère version
            # self.pile.append(element)
            # 2ème version
            pass

        def depiler(self):
            # 1ère version
            # return self.pile.pop() # ou self.pile.pop(-1)
            # 2ème version
            pass

    if __name__ == '__main__':
        p = Pile()
        for i in range(4):
            p.empiler(2 * i)
    ```

    🧪 Tester :

    ```python
    >>> p.estVide() 
    >>> p.depiler()
    >>> p.depiler()
    >>> p.depiler()
    >>> p.depiler()
    >>> p.depiler()
    ```

    ??? success "✅ Solution :"

        ```python
        class Pile:
            '''Classe permettant de créer des piles'''
            def __init__(self):
                self.pile = []

            def estVide(self):
                return self.pile == []

            def empiler(self, element):
                self.pile.append(element)
                # ou : self.pile += [element]

            def depiler(self):
                assert not self.estVide(),"Pile vide"
                # 1ère version
                # return self.pile.pop() # ou self.pile.pop(-1)
                
                # 2ème version
                val = self.pile[-1]
                self.pile = self.pile[:-1]
                return val

        if __name__ == '__main__':
            p = Pile()
            for i in range(4):
                p.empiler(2 * i)
        ```

---

???+ question "📐 Activité n° 29 : Méthodes `taille` et `sommet` en POO"

    On va rajouter à la structure de base précédente deux méthodes de la classe `Pile` :

    * `taille` : retourne la **taille de la pile** (**sans utiliser `len`** ❌)
    * `sommet` : retourne le **sommet de la pile** (**sans utiliser les indices** ❌)

    📦 On pourra s’aider d’une **pile auxiliaire**.
    📌 On doit récupérer la pile dans son état initial.

    ```python
    def taille(self):
        pass

    def sommet(self):
        pass 

    if __name__ == '__main__':
        p = Pile()
        for i in range(4):
            p.empiler(2 * i)
    ```

    Tester :

    ```python
    >>> p.taille()
    >>> p.sommet()
    ```



    ??? success "✅❇️ Solution :"

        ```python
        def taille(self):
            q = Pile()
            compteur = 0
            while not self.estVide():
                q.empiler(self.depiler())
                compteur += 1
            while not q.estVide():
                self.empiler(q.depiler())
            return compteur

        def sommet(self):
            assert not self.estVide(), "Pile vide"
            temporary = self.depiler()
            self.empiler(temporary)
            return temporary

        ```

🧠 Ici, **tous les coûts d’exécution sont unitaires.**
---

???+ question "🖨️ Activité n° 30 : Affichage d’une pile (POO + liste)"

    On va rajouter à la structure une méthode de la classe `Pile` :
    🔎 `afficher` → permet d’**afficher (retourner) la pile** sous forme de **liste**

    ```python
    def afficher(self):
        pass
    ```

    🧪 Tester :

    ```python
    >>> p.afficher()
    [0, 2, 4, 6, 8]
    ```

    ??? success "✅ Solution :"

        ```python
        def afficher(self):
            return self.pile
        ```

---




!!! info "Capytale : Structure pile avec la POO et les listes chainée (activite_pile_POO)"





### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667930"></a>**4.4. ❤️3<sup>ème</sup> implémentation de la structure pile avec la POO et les listes chainée❤️**</H3>

La version à une classe est plus simple, elle peut être suffisante, mais les puristes préfèrent la version à deux classes qui colle davantage au modèle théorique proche des listes dans lequel une pile est soit une cellule, soit une pile vide.

---

???+ question "📘 Activité n° 31 : Structure pile avec la POO et les listes chainée version 1 classe"

    Créer une classe `Pile` qui peut recevoir deux paramètres lors de l'appel du constructeur : un paramètre `value` et un paramètre `next`.

    Les deux valeurs transmises devront être stockées dans deux attributs nommés `v` et `n`.



    🎯 Compléter la structure suivante :

    ```python
    '''Implémentation 3 de type abstrait Liste en utilisant la POO et les listes chainées version 1 classe'''

    class Pile:
        def __init__(self, value=None, next=None):
            pass

        def estVide(self):
            pass

        def empiler(self, element):
            pass

        def depiler(self):
            pass
    ```

    ??? success "✅ Solution :"

        ```python
        class Pile:
            def __init__(self, value=None, next=None):
                self.v = value
                self.n = next

            def estVide(self):
                return self.v is None and self.n is None

            def empiler(self, element):
                if self.estVide():
                    self.v = element
                else:
                    self.n = Pile(self.v, self.n)
                    self.v = element

            def depiler(self):
                if self.estVide():
                    return "Pile vide"
                elif self.n is None:
                    val = self.v
                    self.v = None
                    return val
                else:
                    val = self.v
                    self.v = self.n.v
                    self.n = self.n.n
                    return val
        ```

    🖥️ Que faut-il écrire dans la console pour :

    1. Créer une pile `p` ?
    2. Tester si `p` est vide ?
    3. Empiler dans `p` : Lundi, Mardi, Mercredi
    4. Tester si `p` est vide ?
    5. Dépiler toute la pile `p`

    ??? success "✅ Solution :"
        ```
        p = Pile()
        p.estVide()

        P.empiler('Lundi')
        p.empiler('Mardi')
        p.empiler('Mercredi')

        p.estVide()

        p.depiler()
        p.depiler()
        p.depiler()
        ```

    📝 **Remarque** : on pourra afficher les piles construites en ajoutant la méthode `__str__`

    ```python
    def __str__(self):  # on peut mettre __repr__ à la place pour éviter de taper print
        pass
    ```

    📌 Ajouter les deux méthodes `taille` et `sommet` :

    ```python
    def taille(self):
        pass

    def sommet(self):
        pass

    if __name__ == '__main__':
        p = Pile()
        p.empiler('Lundi')
        p.empiler('Mardi')
        p.empiler('Mercredi')
        print(p.taille())
        print(p.sommet())
    ```

    ??? success "✅ Solution :"

        ```python
        class Pile:
            def __init__(self, value=None, next=None):
                self.v = value
                self.n = next

            def estVide(self):
                return self.v is None and self.n is None

            def empiler(self, element):
                if self.estVide():
                    self.v = element
                else:
                    self.n = Pile(self.v, self.n)
                    self.v = element

            def depiler(self):
                if self.estVide():
                    return "Pile vide"
                elif self.n is None:
                    val = self.v
                    self.v = None
                    return val
                else:
                    val = self.v
                    self.v = self.n.v
                    self.n = self.n.n
                    return val

            def __str__(self): # on peut mettre __repr__ à la place pour éviter de taper print
                return str(self.v) + "-" + str(self.n)

            def taille(self):
                q = Pile()
                compteur = 0
                while not self.estVide():
                    q.empiler(self.depiler())
                    compteur += 1
                while not q.estVide():
                    self.empiler(q.depiler())
                return compteur

            def sommet(self):
                return self.v
        ```

---

???+ question "🧱 Activité n° 32 : Structure pile avec la POO et les listes chainée version 2 classes"

    Créer une classe `Node` qui peut recevoir deux paramètres lors de l'appel du constructeur :

    * un paramètre `value`
    * un paramètre `next`

    Les deux valeurs transmises devront être stockées dans deux attributs nommés `v` et `n`.

    🎯 Compléter la structure suivante :

    ```python
    '''Implémentation 3 de type abstrait Liste en utilisant la POO et les listes chainées version 2 classes'''

    class Node:
        def __init__(self, value=None, next=None):
            pass

    class Pile:
        def __init__(self, c=None):
            pass

        def estVide(self):
            pass

        def empiler(self, element):
            pass

        def depiler(self):
            pass
    ```

        ??? success "✅❇️ Solution :"

        ```python
        class Node:
            def __init__(self, value=None, next=None):
                self.v = value
                self.n = next

        class Pile:
            def __init__(self, c=None):
                self.cellule = c

            def estVide(self):
                return self.cellule is None

            def empiler(self, element):
                self.cellule = Node(element, self.cellule)

            def depiler(self):
                if self.estVide():
                    return "Pile vide"
                else:
                    val = self.cellule.v
                    self.cellule = self.cellule.n
                    return vaL
        ```

    🖥️ Que faut-il écrire dans la console pour :

    1. Créer une pile `p` ?
    2. Tester si `p` est vide ?
    3. Empiler dans `p` : Lundi, Mardi, Mercredi
    4. Tester si `p` est vide ?
    5. Dépiler toute la pile `p`

    ??? success "✅❇️ Solution :"
        ```
        p = Pile()
        p.estVide()

        p.empiler('Lundi')
        p.empiler('Mardi')
        p.empiler('Mercredi')

        p.estVide()

        p.depiler()
        p.depiler()
        p.depiler()
        ```

    📝 **Remarque** : On pourra afficher les piles construites avec les fonctions `afficherListe` et `recupererValeur` des Listes chaînées :

    ```python
    def afficherListe(L):
        tableau = recupererValeur(L.cellule)
        return str(tuple(tableau))

    def recupererValeur(cellule):
        if cellule.n == None:
            return [cellule.v]
        else:
            return [cellule.v] + recupererValeur(cellule.n)
    ```

    ??? success "✅❇️ Solution :"

        ```python
        def afficherListe(L):
            tableau = recupererValeur(L.cellule)
            return str(tuple(tableau))

        def recupererValeur(cellule):
            if cellule is None:
                return []
            if cellule.n == None:
                return [cellule.v]
            else:
                return [cellule.v] + recupererValeur(cellule.n)
        p = Pile()
        p.empiler('Lundi')
        p.empiler('Mardi')
        p.empiler('Mercredi')
        afficherListe(p)
        ```

---




???+ question "📘 Activité n° 33 : Structure pile avec la POO et les listes chaînées version 2 classes – méthodes `taille` et `sommet`"

    🧩 Rajouter aux structures précédentes deux méthodes :

    * `taille` qui retourne la taille de la pile
    * `sommet` qui retourne le sommet de la pile

    ```python
    def taille(self):
        pass

    def sommet(self):
        pass

    if __name__ == '__main__':
        p = Pile()
        p.empiler('Lundi')
        p.empiler('Mardi')
        p.empiler('Mercredi')
        print(p.taille())
        print(p.sommet())
    ```

    ??? success "✅ Solution :"

        ```python
        def taille(self):
            q = Pile()
            compteur = 0
            while not self.estVide():
                q.empiler(self.depiler())
                compteur += 1
            while not q.estVide():
                self.empiler(q.depiler())
            return compteur

        def sommet(self):
            if self.cellule is None:
                return "Pile vide"
            return self.cellule.v

        p = Pile()
        p.empiler('Lundi')
        p.empiler('Mardi')
        p.empiler('Mercredi')
        print(p.taille())
        print(p.sommet())
        ```

---

???+ question "📘 Activité : Structure pile avec la POO et les listes chaînées version 2 classes – fonctions `taille2` et `sommet2`"

    🧪 Rajouter aux structures précédentes deux **fonctions externes** :

    * `taille2` : retourne la taille de la pile
    * `sommet2` : retourne le sommet de la pile



    ??? success "✅ Solution :"

        ```python
        def taille2(pile):
            q = Pile()
            compteur = 0
            while not pile.estVide():
                q.empiler(pile.depiler())
                compteur += 1
            while not q.estVide():
                pile.empiler(q.depiler())
            return compteur

        def sommet2(pile):
            if pile.cellule is None:
                return "Pile vide"
            return pile.cellule.v
        ```

📺 **[Vidéo – Le crêpier psychorigide](https://ladigitale.dev/digiview/#/v/66b7280a8b3b5)**

---

!!! info "Capytale : Structure file avec les listes de Python (activite_file_list)"

## <H2 STYLE="COLOR:BLUE;">🛒 <a name="_toc151667931"></a>**5. Les files**</H2>

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667932"></a>**5.1. Généralités**</H3>

En informatique, une **file** (*queue* en anglais) est une structure de données basée sur le principe :
➡️ **Premier entré, premier sorti** (**FIFO : First In, First Out**)

![](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.033.png){width=30%; : .center }

📌 **Exemples d’usage** :

* 📊 Transactions temporaires en attente
* 🖨️ Requêtes d’un **serveur d’impression**
* ⚙️ Tâches en **multitâche** dans un OS
* 🛒 Gestion de file d’attente de clients, stocks…

---

🛠️ **Primitives courantes** :

* `fileVide()` : créer une file vide
* `enfiler(file, x)` : ajoute un élément à la **queue** (**enqueue**)
* `defiler(file)` : retire et renvoie l’élément en **tête** (**dequeue**)
* `estVide(file)` : teste si la file est vide

![](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.035.png){width=60%; : .center }

---

🎯 **Exemple** :

Soit une file `F` composée de `12, 14, 8, 7, 19, 22`
(➡️ Premier élément : **22** ; Dernier élément : **12**)

* `enfiler(F,42)` → devient : `42, 12, 14, 8, 7, 19, 22`
* `defiler(F)` → devient : `12, 14, 8, 7, 19`
* `defiler(F)` x6 → `estVide(F)` renvoie **True**

---



### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667933"></a>**5.2. ❤️1<sup>ère</sup> implémentation de la structure file avec les listes de Python❤️**</H3>

On peut utiliser une implémentation similaire à celle des piles,
mais :

* `defiler()` retire l’élément **en tête**
* `enfiler()` ajoute un élément **en queue**
  → donc en **temps linéaire** (il faut parcourir toute la file)

---

???+ question "📘 Activité n° 34 : Structure file avec les listes"

    🧩 Compléter la **structure de base** suivante :

    💬 **Remarque** : la fonction `enfiler` ne renvoie rien.

    ⚠️ **Attention aux effets de bord :**

    **file += [element] (opérateur d'addition avec affectation):**

    - C'est une opération sur place pour les objets mutables comme les listes.

    - Cela modifie directement la liste originale référencée par file.

    - L'objet reste le même en mémoire.

    **file = file + [element] (concaténation suivie d'affectation):**

    - C'est une opération de création d'un nouvel objet.

    - L'expression file + [element] crée une nouvelle liste en concaténant file et [element].

    - L'affectation file = ... fait alors pointer le nom pile vers ce nouvel objet. Mais si la variable pile est passée à la fonction par référence (comme c'est souvent le cas avec les objets mutables en Python), cela coupe le lien avec l'objet original.

    De la même manière

    **file = file[1:]** crée une nouvelle liste et réaffecte la variable file localement dans la fonction. Cela ne modifie pas l'objet d'origine si vous utilisez la liste en dehors de la fonction (par exemple, une liste passée en argument). Pour corriger cela, vous devez modifier la liste en place.

    ```python
    '''Implémentation de type abstrait File en utilisant les listes de Python'''

    def fileVide():
        pass

    def estVide(file):
        pass

    def enfiler(file, element):
        # 1ère façon 
        # file.append(element)
        # 2ème façon
        pass

    def defiler(file):
        if not estVide(file):
            # 1ère façon 
            # return file.pop(0)
            # 2ème façon
            pass
        return "File vide"

    # Programme principal
    if __name__ == '__main__':
        ma_file = fileVide()
        assert estVide(ma_file) == True
        enfiler(ma_file, 'Lundi')
        enfiler(ma_file, 'Mardi')
        enfiler(ma_file, 'Mercredi')
        assert estVide(ma_file) == False
        assert defiler(ma_file) == 'Lundi'
        assert defiler(ma_file) == 'Mardi'
        assert defiler(ma_file) == 'Mercredi'
        assert defiler(ma_file) == 'File vide'
    ```

    ??? success "✅ Solution :"

        ```python
        def fileVide():
            return []

        def estVide(file):
            return file == []

        def enfiler(file, element):
            # 1ère façon 
            #file.append(element) 
            
            # 2ème façon
            file += [element]

        def defiler(file):
            if not estVide(file):
                # 1ère façon 
                # return file.pop(0)
                
                # 2ème façon      
                valeur = file[0]
                file[:] = file[1:] # ou del file[0] qui est plus performant
                return valeur
            else:
                return 'File vide'

        # Programme principal
        if __name__ == '__main__':
            ma_file = fileVide()
            assert estVide(ma_file) == True
            enfiler(ma_file, 'Lundi')
            enfiler(ma_file, 'Mardi')
            enfiler(ma_file, 'Mercredi')
            assert estVide(ma_file) == False
            assert defiler(ma_file) == 'Lundi'
            assert defiler(ma_file) == 'Mardi'
            assert defiler(ma_file) == 'Mercredi'
            assert defiler(ma_file) == 'File vide'
        ```

---

???+ question "📘 Activité n° 35 : Fonctions `taille` et `sommet` pour les files"

    🎯 Rajouter deux fonctions à la structure précédente :

    * `taille(file)` : retourne la **taille** de la file (**sans utiliser `len`**)
    * `sommet(file)` : retourne le **sommet** (1er élément inséré) **sans utiliser les indices**

    On ne pourra utiliser **que les primitives précédentes**, et la file **doit être restaurée**.

    ```python
    def taille(file):
        pass

    def sommet(file):
        pass

    # Programme principal
    if __name__ == '__main__':
        ma_file = fileVide()
        enfiler(ma_file, 'Lundi')
        enfiler(ma_file, 'Mardi')
        enfiler(ma_file, 'Mercredi')
        assert taille(ma_file) == 3
        assert sommet(ma_file) == 'Lundi'
    ```

    ??? success "✅ Solution :"

        ```python
        def taille(file):
            compteur = 0
            file_temp = fileVide()
            while not estVide(file):
                enfiler(file_temp, defiler(file))
                compteur += 1
            while not estVide(file_temp):
                enfiler(file, defiler(file_temp))
            return compteur

        def sommet(file):
            assert not estVide(file), "File vide"
            temporary = defiler(file)
            q = fileVide()
            enfiler(q, temporary)
            while not estVide(file):
                enfiler(q, defiler(file))
            while not estVide(q):
                enfiler(file, defiler(q))
            return temporary
        ```

---


!!! info "Capytale : Structure file avec la POO et les lists de Python(activite_file_POO_list)"



### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667934"></a>**5.3. ❤️2<sup>ème</sup> implémentation de la structure file avec la POO et les listes de Python❤️**</H3>



???+ question "📘 Activité n° 36 : Structure file avec la POO et les listes de Python"

    Créer une classe `File` qui construit une **liste vide**, puis compléter les autres méthodes :

    💬 **Remarque** : La fonction `enfiler` ne renvoie rien.

    ⚠️ **Attention** :

    **file += [element] (opérateur d'addition avec affectation):**

    - C'est une opération sur place pour les objets mutables comme les listes.

    - Cela modifie directement la liste originale référencée par file.

    - L'objet reste le même en mémoire.

    **file = file + [element] (concaténation suivie d'affectation):**

    - C'est une opération de création d'un nouvel objet.

    - L'expression file + [element] crée une nouvelle liste en concaténant file et [element].

    - L'affectation file = ... fait alors pointer le nom pile vers ce nouvel objet. Mais si la variable pile est passée à la fonction par référence (comme c'est souvent le cas avec les objets mutables en Python), cela coupe le lien avec l'objet original.

    De la même manière

    **file = file[1:]** crée une nouvelle liste et réaffecte la variable file localement dans la fonction. Cela ne modifie pas l'objet d'origine si vous utilisez la liste en dehors de la fonction (par exemple, une liste passée en argument). Pour corriger cela, vous devez modifier la liste en place.

    ```python
    '''Implémentation 3 de type abstrait Liste en utilisant la POO et les listes de Python'''

    class File:
        '''Classe permettant de créer des files'''
        def __init__(self):
            pass

        def estVide(self):
            pass

        def enfiler(self, element):
            # 1ère façon
            # self.file.append(element)
            # 2ème façon
            pass

        def defiler(self):
            if not self.estVide():
                # 1ère façon 
                # return self.file.pop(0)
                # 2ème façon 
                pass
            return "File vide"
    
    # Programme principal
    if __name__ == '__main__':
        ma_file = File()
        assert ma_file.estVide() == True
        ma_file.enfiler('Lundi')
        ma_file.enfiler('Mardi')
        ma_file.enfiler('Mercredi')
        assert ma_file.estVide() == False
        assert ma_file.defiler() == 'Lundi'
        assert ma_file.defiler() == 'Mardi'
        assert ma_file.defiler() == 'Mercredi'
        assert ma_file.defiler() == 'File vide'
    ```

    ??? success "✅❇️ Solution :"

        ```python
        class File:
            def __init__(self):
                self.file = []

            def estVide(self):
                return self.file == []

            def enfiler(self, element):
                self.file += [element]

            def defiler(self):
                if not self.estVide():
                    # 1ère façon 
                    # return self. file.pop(0)
                
                    # 2ème façon
                    valeur = self.file[0]
                    self.file[:] = self.file[1:] # ou del self.file[0] qui est plus performant
                    return valeur
        else:
            return 'File vide'

        # Programme principal
        if __name__ == '__main__':
            ma_file = File()
            assert ma_file.estVide() == True
            ma_file.enfiler('Lundi')
            ma_file.enfiler('Mardi')
            ma_file.enfiler('Mercredi')
            assert ma_file.estVide() == False
            assert ma_file.defiler() == 'Lundi'
            assert ma_file.defiler() == 'Mardi'
            assert ma_file.defiler() == 'Mercredi'
            assert ma_file.defiler() == 'File vide'
        ```

---

???+ question "📘 Activité n° 37 : Méthodes `taille` et `sommet` (POO – file avec listes)"

    On rajoute à la classe `File` deux méthodes :

    * `taille` ➜ retourne la taille (**sans `len`**)
    * `sommet` ➜ retourne le premier élément (**sans indices**)

    📌 On pourra s’aider d’une **file auxiliaire**, et la file **doit être restaurée**.

    ```python
    def taille(self):
        pass

    def sommet(self):
        pass

    # Programme principal
    if __name__ == '__main__':
        ma_file = File()
        ma_file.enfiler('Lundi')
        ma_file.enfiler('Mardi')
        ma_file.enfiler('Mercredi')
        assert ma_file.taille() == 3
        assert ma_file.sommet() == 'Lundi'
    ```



    ??? success "✅ Solution :"

        ```python
        def taille(self):
            g = File()
            compteur = 0
            while not self.estVide():
                g.enfiler(self.defiler())
                compteur += 1
            while not g.estVide():
                self.enfiler(g.defiler())
            return compteur

        def sommet(self):
            assert not self.estVide(), "File vide"
            temporary = self.defiler()
            g = File()
            g.enfiler(temporary)
            while not self.estVide():
                g.enfiler(self.defiler())
            while not g.estVide():
                self.enfiler(g.defiler())
            return temporary
        
        # Programme principal
        if __name__ == '__main__':
            ma_file = File()
            ma_file.enfiler('Lundi')
            ma_file.enfiler('Mardi')
            ma_file.enfiler('Mercredi')
            assert ma_file.taille() == 3
            assert ma_file.sommet() == 'Lundi'
        ```

📎 Tous les **coûts d’exécution sont unitaires.**

---

???+ question "📘 Activité n° 38 : Méthode `afficher` de la file (POO + liste)"

    🎯 Ajouter une méthode `afficher` dans la classe `File`, qui retourne la file sous forme de **liste Python**.

    ```python
    def afficher(self):
        pass
    ```

    🔧 Dans le programme principal :

    ```python
    assert ma_file.afficher() == ['Mardi', 'Mercredi', 'Lundi']
    ```

    💡 Cette implémentation est **peu efficace**, mais fonctionnelle.

    ??? success "✅❇️ Solution :"

        ```python
        def afficher(self):
            return self.file
        ```

Cette implémentation est très peu efficace

---

???+ question "📘 Activité : Fonctions `taille2` et `sommet2` (version fonctionnelle)"

    🎯 Ajouter deux **fonctions** externes à la classe `File` :

    * `taille2(file)` ➜ retourne la taille
    * `sommet2(file)` ➜ retourne le sommet (1er élément)

    📌 Toujours **sans `len`, ni indices**, avec restauration complète de la file.
    On peut s’aider d’une **file auxiliaire**.

    ??? success "✅ Solution :"

        ```python
        def taille2(file):
            compteur = 0
            file_temp = File()
            while not file.estVide():
                file_temp.enfiler(file.defiler())
                compteur += 1
            while not file_temp.estVide():
                file.enfiler(file_temp.defiler())
            return compteur

        def sommet2(file):
            assert not file.estVide(), "File vide"
            premier = file.defiler()
            file.enfiler(premier)
            return premier
        ```

---


!!! info "Capytale : structure file avec la POO et une liste chainée (activite_file_POO)"

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667935"></a>**5.4. ❤️3<sup>ème</sup> implémentation de la structure file avec la POO et une liste chainée❤️**</H3>





???+ question "📘 Activité n° 39 : Structure pile avec la POO et les listes chainées"

    ```python
    '''Implémentation de type abstrait File avec la POO et les listes chainées et deux classes'''

    class Node:
        def __init__(self, value = None, next = None):
            pass
    ```

    Compléter le constructeur de la classe `File`

    💡 **Attention** : pour améliorer l’implémentation, il nous faudra un attribut `queue`.

    ```python
    class Node:
        def __init__(self, value = None, next = None):
            pass

    class File:
        def __init__(self, c=None):
            pass
            self.head = ...
    ```

    ??? success "✅ Solution :"
        ```python
        class Node:
            def __init__(self, value = None, next = None):
                self.v = value
                self.n = next

        class File:
            def __init__(self, c=None):
                self.head = c
        ```

    🧪 Tester :

    ```python
    f = File()
    ```

    Compléter les 3 méthodes :

    * `estVide()`
    * `enfiler()` et `defiler()` → version : enfiler par la tête et défiler par la queue (**plus compliquée**)
    * `enfiler2()` et `defiler2()` → version : enfiler par la queue et défiler par la tête (**plus simple**)

    ??? success "✅ Solution :"
        ```python
        class Node:
            def __init__(self, value = None, next = None):
                self.v = value
                self.n = next

        class File:
            def __init__(self, c=None):
                self.head = c

            def estVide(self):
                return self.head is None
            
            
            def enfiler(self, element):
                ### version enfiler par la tête et défiler par la queue
                self.head = Node(element, self.head)

            def defiler(self):
                ### version enfiler par la tête et défiler par la queue
                if not self.estVide():
                    newNode = self.head
                    if newNode.n == None: # cas d'une seule valeur
                        val = newNode.v 
                        self.head = None
                        return val
                        
                    while not newNode.n.n == None: # on s'arrête à l'avant dernier
                        newNode = newNode.n
                    val = newNode.n.v
                    newNode.n = None
                    return val
                else:
                    return 'File vide'
            
            def enfiler2(self, element):
                ### version enfiler par la queue et défiler par la tete
                if self.estVide():
                    self.head = Node(element)
                else:
                    tmp = self.head
                    while tmp.n != None :
                        tmp = tmp.n
                    tmp.n = Node(element)
            
            def defiler2(self):
                ### version enfiler par la queue et défiler par la tete
                if not self.estVide():
                    val = self.head.v
                    self.head = self.head.n
                    return val
                else:
                    return 'File vide'
        ```

    🧪 Tester :

    ```python
    f = File()
    assert f.estVide() == True
    f.enfiler('Lundi')
    f.enfiler('Mardi')
    f.enfiler('Mercredi')
    assert f.estVide() == False
    assert f.defiler() == 'Lundi'
    assert f.defiler() == 'Mardi'
    assert f.defiler() == 'Mercredi'
    assert f.defiler() == 'File vide'
    f.enfiler2('Lundi')
    f.enfiler2('Mardi')
    f.enfiler2('Mercredi')
    assert f.defiler2() == 'Lundi'
    assert f.defiler2() == 'Mardi'
    assert f.defiler2() == 'Mercredi'
    assert f.defiler2() == 'File vide'
    ```

    🎯 Compléter la méthode `__str__`.
    On peut utiliser une liste pour enregistrer les valeurs lues sur la file afin de les présenter dans l’ordre :

    * Sommet (à gauche)
    * Queue (à droite)


    ```python
    class Node:
        def __init__(self, value = None, next = None):
            pass

    class File:
        def __init__(self, c=None):
            pass
            self.head = ...

        def estVide(self):
            pass

        def enfiler(self, element):
            ### version enfiler par la tête et défiler par la queue
            pass

        def defiler(self):
            ### version enfiler par la tête et défiler par la queue
            pass
        
        def enfiler2(self, element):
            ### version enfiler par la queue et défiler par la tête
            pass

        def defiler2(self):
            ### version enfiler par la queue et défiler par la tête
            pass
        
        def __str__(self):
            ### version enfiler par la queue et défiler par la tête
            pass

    f = File()
    assert f.estVide() == True
    f.enfiler2('Lundi')
    f.enfiler2('Mardi')
    f.enfiler2('Mercredi')
    ```

    ??? success "✅ Solution :"
        ```python
        #"""
        def __str__(self):
            ### version enfiler par la queue et défiler par la tete
            if self.head is None:
                return "[]"
            result=[]
            currentNode = self.head
            while not currentNode == None:
                result.append(str(currentNode.v))
                currentNode = currentNode.n
            return str(result)
            
            
            """
            def __str__(self):  # on peut mettre __repr__ à la place pour éviter de taper print
                if self.head is None:
                    raise IndexError("File vide")
                else:
                    result = str(self.head.v)
                    next_node = self.head.n
                    while next_node is not None:
                        result =  str(next_node.v)+" - "  +result
                        next_node = next_node.n
                    return result
            """
        ```

    🎯 Compléter les deux méthodes suivantes : `taille()` et `sommet()`
    (On utilisera `enfiler2()` et `defiler2()` → version plus simple)

    ```python
    class Node:
        def __init__(self, value = None, next = None):
            pass

    class File:
        def __init__(self, c=None):
            pass
            self.head = ...

        def estVide(self):
            pass

        def enfiler(self, element):
            pass

        def defiler(self):
            pass
        
        def enfiler2(self, element):
            pass

        def defiler2(self):
            pass
        
        def __str__(self):
            pass

        def taille(self):
            pass
        
        def sommet(self):
            pass

    f = File()
    assert f.estVide() == True
    f.enfiler2('Lundi')
    f.enfiler2('Mardi')
    f.enfiler2('Mercredi')
    ```

    ??? success "✅ Solution :"
        ```python
        def taille(self):
            compteur = 0
            currentNode = self.head
            while currentNode is not None:
                compteur += 1
                currentNode = currentNode.n
            return compteur
        
        def sommet(self):
            if self.estVide():
                return 'File vide'
            return self.head.v
        ```

    🧪 Tester



    🎯 Ajouter deux fonctions hors classe : `taille(file)` et `sommet(file)`
    (utiliser également `enfiler2()` et `defiler2()`)

    ??? success "✅ Solution :"
        ```python
        def taille2(file):
            count = 0
            tmp = file.head
            while tmp is not None:
                count += 1
                tmp = tmp.n
            return count

        def sommet2(file):
            if file.estVide():
                return "File vide"
            return file.head.v
        ```
    🧪 Tester



    🎯 Ajouter une fonction `afficherFile(file)`

    🧪 Tester



    ??? success "✅ Solution :"

        ```python
        #version avec une list
        def afficherFile(file):
            result=[]
            if file.head is None:
                return "File vide"
            else:
                result.append(file.head.v)
                next_node = file.head.n
                while next_node is not None:
                    result.append(next_node.v)
                    next_node = next_node.n
                return result

        """
        def afficherFile(file):
            if file.head is None:
                return "File vide"
            else:
                result = str(file.head.v)
                next_node = file.head.n
                while next_node is not None:
                    result += " - " + str(next_node.v)
                    next_node = next_node.n
                return result
        """
        ```





La file implémentée de la sorte n'est **pas très efficace** car il faut entièrement la la parcourir pour enfiler un élément!!
    
On va améliorer l'efficacité avec **2 pointeurs** : l'un vers la **tête** et l'autre vers la **queue**!

 
---

???+ question "📘 Activité n° 39bis : Optimisation de la file avec 2 pointeurs (tête et queue)"

    🧠 La file implémentée précédemment n’est **pas très efficace** car il faut la parcourir entièrement pour enfiler un élément.

    🚀 On va **améliorer l’efficacité** avec **2 pointeurs** :

    * Un vers la **tête** (début de la file),
    * Un vers la **queue** (fin de la file).

    Compléter la structure suivante :

    ```python
    class Node:
        def __init__(self, value=None, next=None):
            # Initialisation d'un nœud avec une valeur et un pointeur vers le nœud suivant
            pass


    class File:
        def __init__(self, c=None):
            # Initialisation de la file avec une tête et une queue
            self.head = c...    # Pointeur vers le premier élément de la file
            self.queue = ...    # Pointeur vers le dernier élément de la file

        def estVide(self):
            # Vérifie si la file est vide
            pass

        def enfiler(self, element):
            """Ajoute un élément au début de la file."""
            ...

        def defiler(self):
            """Retire un élément à la fin de la file."""
            ...

        def enfiler2(self, element):
            """Ajoute un élément à la fin de la file."""
            ...

        def defiler2(self):
            """Retire un élément au début de la file."""
            ...

        def __str__(self):
            """Affiche les éléments de la file sous forme d'une chaîne."""
            ...
    ```

    🧪 **Tester le comportement de la file :**

    ```python
    f = File()
    assert f.estVide() == True
    f.enfiler('Lundi')
    f.enfiler('Mardi')
    f.enfiler('Mercredi')
    assert f.estVide() == False
    assert f.defiler() == 'Lundi'
    assert f.defiler() == 'Mardi'
    assert f.defiler() == 'Mercredi'
    assert f.defiler() == 'File vide'
    f.enfiler2('Lundi')
    f.enfiler2('Mardi')
    f.enfiler2('Mercredi')
    print(f)
    assert f.defiler2() == 'Lundi'
    assert f.defiler2() == 'Mardi'
    assert f.defiler2() == 'Mercredi'
    ```


    ??? success "✅ Solution :"

        ```python
        class Node:
            def __init__(self, value=None, next=None):
                self.v = value
                self.n = next


        class File:
            def __init__(self, c=None):
                self.head = c
                self.queue = c

            def estVide(self):
                return self.head is None

            def enfiler(self, element):
                ### version enfiler par la tête et défiler par la queue
                newNode = Node(element)
                if self.estVide():
                    self.head = self.queue = newNode
                else:
                    newNode.n = self.head
                    self.head = newNode

            def defiler(self):
                ### version enfiler par la tête et défiler par la queue
                if self.estVide():
                    return 'File vide'
                
                if self.head == self.queue: # Si la file n'a qu'un seul élément
                    val = self.head.v
                    self.head = None
                    self.queue = None
                    return val
                # Sinon, on doit parcourir la liste pour trouver l'avant-dernier nœud
                currentNode = self.head
                while currentNode.n != self.queue:
                    currentNode = currentNode.n
                val = self.queue.v
                currentNode.n = None
                self.queue = currentNode
                return val

            def enfiler2(self, element):
                nouveau = Node(element)
                if self.estVide():
                    self.head = nouveau
                    self.queue = nouveau
                else:
                    self.queue.n = nouveau
                    self.queue = nouveau

            def enfiler2(self, element):
                ### version enfiler par la queue et défiler par la tete
                newNode = Node(element) 
                if self.estVide():
                    self.head = self.queue = newNode
                else:
                    self.queue.n = newNode  # L'ancien dernier nœud pointe vers le nouveau nœud
                    self.queue = newNode    # La queue est mise à jour pour pointer vers le nouveau nœud

            def defiler2(self):
                ### version enfiler par la queue et défiler par la tete
                if not self.estVide():
                    val = self.head.v
                    self.head = self.head.n
                    if self.head is None:  # Si la tête devient vide, la file est vide
                        self.queue = None
                    return val
                else:
                    raise IndexError("File vide")

            #"""
            def __str__(self):
                ### version enfiler par la queue et défiler par la tete
                if self.head is None:
                    return "[]"
                result=[]
                currentNode = self.head
                while not currentNode == None:
                    result.append(str(currentNode.v))
                    currentNode = currentNode.n
                return str(result)
    
       
    
            """        
            def __str__(self):  # on peut mettre __repr__ à la place pour éviter de taper print
                if self.head is None:
                    raise IndexError("File vide")
                else:
                    result = str(self.head.v)
                    next_node = self.head.n
                    while next_node is not None:
                        result += " - " + str(next_node.v)
                        next_node = next_node.n
                    return result
            """
        
        ```

---





!!! info "Capytale : Utilisation de deque (activite_deque)"

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667936"></a>**5.5. Autre implémentation des files avec les bibliothèques de Python**</H3>




???+ question "📦 Activité n°40 : Utilisation de `deque` pour implémenter une **Pile**"

    🔁 Opérations fondamentales :

    * `empiler` → `.append()`
    * `depiler` → `.pop()`

    ```python
    from collections import deque

    # Création de la pile
    pile = deque()

    ##########################################################
    # Vérifier si la pile est vide


    print("La pile est vide ?", est_vide(pile))

    ##########################################################
    # Empiler des éléments 10, 20 puis 30 
    #à compléter



    print("Pile après empilage:", pile)

    ##########################################################
    # Dépiler un élément
    # à compléter



    print("Élément dépilé:", element)

    #########################################################
    # Regarder l'élément au sommet sans le dépiler
    # à compléter


    print("Élément au sommet:", sommet)

    #########################################################
    # Déterminer la taille de la pile 
    # à compléter


    print("La taille de la pile:", taille)
    ```


    ??? success "✅❇️ Solution :"

        ```python
        from collections import deque

        # Création de la pile
        pile = deque()

        # Vérifier si la pile est vide
        def est_vide(pile):
            return len(pile) == 0

        print("La pile est vide ?", est_vide(pile))

        # Empiler des éléments
        pile.append(10)
        pile.append(20)
        pile.append(30)

        print("Pile après empilage:", pile)

        # Dépiler un élément
        element = pile.pop()
        print("Élément dépilé:", element)

        # Regarder le sommet
        sommet = pile[-1]
        print("Élément au sommet:", sommet)

        # Taille de la pile
        taille = len(pile)
        print("La taille de la pile:", taille)
        ```

---

???+ question "🚉 Activité n°41 : Utilisation de `deque` pour implémenter une **File**"

    🔁 Opérations fondamentales :

    * `enfiler()` → `.append()`
    * `défiler()` → `.popleft()`

    ```python
    from collections import deque

    # Création de la file
    file = deque()

    ##########################################################
    # Vérifier si la file est vide


    print("La file est vide ?", est_vide(file))

    ##########################################################
    # Enfiler des éléments 10, 20 puis 30 
    #à compléter



    print("file après enfilage:", file)

    ##########################################################
    # Défiler un élément
    # à compléter



    print("Élément défilé:", element)

    #########################################################
    # Regarder l'élément au sommet sans le défiler
    # à compléter


    print("Élément au sommet:", sommet)

    #########################################################
    # Déterminer la taille de la file 
    # à compléter


    print("La taille de la file:", taille)
    ```



    ??? success "✅ Solution :"

        ```python
        from collections import deque

        # Création de la file
        file = deque()

        # Vérifier si la file est vide
        def est_vide(file):
            return len(file) == 0

        print("La file est vide ?", est_vide(file))

        # Enfiler des éléments
        file.append(10)
        file.append(20)
        file.append(30)

        print("file après enfilage:", file)

        # Défiler un élément
        element = file.popleft()
        print("Élément défilé:", element)

        # Regarder l’élément au sommet
        sommet = file[0]
        print("Élément au sommet:", sommet)

        # Taille de la file
        taille = len(file)
        print("La taille de la file:", taille)
        ```

---

🧠 **Rappel** :
Les **piles** et **files** sont des structures fondamentales.
✅ L’utilisation de `deque` est **préférée** pour les performances, notamment en file (accès efficace en **tête** et **queue**).

---






### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667937"></a>**5.6. 🔁 Piles vs Files :**</H3>

|                                         🧱 **Pile**                                         |                                       🚦 **File**                                       |
| :-----------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------: |
|               📍 Les objets sont insérés et supprimés à **1 seule extrémité**               |                🔄 Les objets sont insérés et retirés aux **2 extrémités**               |
| 📌 Dans les piles, un **seul pointeur** est utilisé. Il pointe vers le **haut** de la pile. | 📌 Dans les files, **deux pointeurs** sont utilisés : vers la **tête** et la **queue**. |
|                 📦 Le **dernier objet inséré** est le **premier à sortir**.                 |               🚪 Le **premier objet inséré** est le **premier à sortir**.               |
|                          🔃 Ordre : **LIFO** (*Last In First Out*)                          |                        🔁 Ordre : **FIFO** (*First In First Out*)                       |
|                         🛠️ Opérations : « Empiler » et « Dépiler »                         |                       🛠️ Opérations : « Enfiler » et « Défiler »                       |
|                         🧊 Visualisation : **collection verticale**                         |                      📏 Visualisation : **collection horizontale**                      |

---

## <H2 STYLE="COLOR:BLUE;">🛠️ <a name="_toc151667938"></a>**6. Les dictionnaires**</H2>

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc60173193"></a><a name="_toc151667939"></a>**6.1. 📚 Définition**</H3>

🧠 Les dictionnaires ont déjà été étudiés en classe de première.
Pour rappel, ce type de données, aussi appelé **tableau associatif**, permet de stocker des **valeurs** accessibles via une **clé**, contrairement au tableau où on accède par indice.

**📖 Exemple** : un dictionnaire de langues
🔑 Toutes les **clés sont distinctes**. On s’intéresse donc ici principalement **aux clés** et à leur gestion.

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc60173194"></a><a name="_toc151667940"></a>**6.2. 🛠️ Opérations de base dans un dictionnaire**</H3>

Les opérations classiques à connaître :

* ➕ **Ajouter** une entrée : `dico["clé"] = valeur`
* ✏️ **Modifier** une entrée : `dico["clé"] = nouvelle_valeur`
* ❌ **Supprimer** une entrée : `dico.pop("clé")`
* 🔍 **Rechercher** une clé : `"clé" in dico`

⚠️ **Attention** :
Le dictionnaire Python est une **version spécifique** d'une structure plus générale.
Ce qui nous intéresse ici, c’est **l’efficacité des interrogations et modifications.**

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc60173197"></a><a name="_toc151667941"></a>**6.3. 🧩 Les clés**</H3>

Une **clé** peut être un type :

* ✅ non mutable (str, int, tuple, etc.)
* ❌ **pas** mutable (liste, dictionnaire…)

Exemple d’erreur avec une liste :

```
>>> dico[[2,1]] = "..."
TypeError: unhashable type: 'list'
```

🧠 La raison : le type `list` **n’est pas hashable**. Cela signifie qu’il **ne peut pas être utilisé comme clé**.

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667942"></a>**6.4. 🔐 Hachage**</H3>

📌 Le **hachage** est au cœur du fonctionnement des dictionnaires.
C’est une opération qui transforme une **clé** en **indice unique** dans une table.

---

#### <H4 STYLE="COLOR:MAGENTA;">🔧 6.4.1. Définition d’une fonction de hachage</H4>

🔑 Une fonction de hachage produit une **empreinte unique** pour une clé donnée.
Elle doit respecter plusieurs propriétés :

1. 📏 **Longueur constante**
   → L’empreinte doit toujours avoir la même taille, peu importe l’entrée.

2. 🔒 **Irréversibilité**
   → On ne doit **pas pouvoir retrouver la clé d’origine** à partir de l’empreinte.

3. 🧬 **Unicité (maximale)**
   → Deux clés différentes doivent générer **des empreintes différentes**.
   ✅ Des **collisions** sont possibles mais rares.

4. ♻️ **Déterminisme**
   → La **même entrée** doit toujours produire **la même sortie**.

⚠️ **Remarque** :

La fonction `hash()` de Python **ne garantit pas** une empreinte identique entre deux exécutions.

➡️ Pour un **hachage stable**, on utilisera plutôt le module `hashlib`.




#### <H4 STYLE="COLOR:MAGENTA;"> **6.4.2. Quelques utilisations du hachage**</H4>
⚓︎  

**Stockage sécurisé des mots de passe**  

Lorsqu'un utilisateur crée un compte, son mot de passe ne doit jamais être stocké en clair pour des raisons de sécurité. Le mot de passe est transformé en empreinte (par exemple, via une fonction comme SHA-256) avant d'être enregistré. Si la base de données est compromise, il est presque impossible de retrouver le mot de passe original.  

Exemple Python avec `hashlib` pour une empreinte SHA-256 :  

```python
import hashlib

password = "monMotDePasse"
hash_object = hashlib.sha256(password.encode())
hashed_password = hash_object.hexdigest()
print(hashed_password)  # Empreinte unique
```

???+ question "Tester ce qui est proposé"

    {{ IDE() }}



**Détection des modifications dans un fichier**  

En calculant l'empreinte d'un fichier à un moment donné, on peut détecter si ce fichier a été modifié ultérieurement. C'est une méthode utilisée par les systèmes de contrôle de versions ou les logiciels de vérification d'intégrité (ex : `md5sum`, `sha256sum`).  

Exemple d'utilisation avec Python :  
```python
import hashlib

def hash_file(filename):
    hasher = hashlib.sha256()
    with open(filename, 'rb') as f:
        while chunk := f.read(8192):  # Lecture par blocs
            hasher.update(chunk)
    return hasher.hexdigest()

print(hash_file("monFichier.txt"))
```



**Autres usages courants** :  

- **Indexation et recherche rapide** (dans les bases de données ou dictionnaires).  
- **Cryptographie** : Les fonctions de hachage jouent un rôle clé dans les signatures numériques et la blockchain.  
- **Vérification des téléchargements** : Les empreintes permettent de s'assurer qu'un fichier n'a pas été altéré pendant son transfert.  

---

#### <H4 STYLE="COLOR:MAGENTA;"> **6.4.3. Table de hachage** </H4>
⚓︎  

Une table de hachage est une structure de données clé-valeur qui permet un accès rapide aux éléments.  

**Principe** :

Chaque clé est transformée en un indice via une fonction de hachage, permettant d'accéder directement à la valeur correspondante.  

**Exemple simplifié de fonctionnement en Python** : 

```python
dictionnaire = {"nom": "Alice", "âge": 30}
print(dictionnaire["nom"])  # Recherche rapide grâce à une table de hachage
```
???+ question "Tester ce qui est proposé"

    {{ IDE() }}


**Caractéristiques** :  

1. **Complexité en temps constant** :  
   L'accès à un élément dans une table de hachage est en moyenne constant, \( O(1) \), indépendamment de la taille de la table.  

2. **Gestion des collisions** :  
   Lorsque deux clés différentes produisent le même indice (collision), des techniques comme le chaînage ou l'adressage ouvert sont utilisées pour résoudre le conflit.  

**Comparaison avec d'autres structures** :  

- Dans un tableau ou une liste chaînée, la recherche est proportionnelle au nombre d'éléments (\( O(n) \)).  
- Une table de hachage est donc beaucoup plus rapide pour la recherche sur des clés.  

Regardez la vidéo ci-dessous sur les tables de hachage.

Tables de hash : <https://ladigitale.dev/digiview/#/v/66bcbaf4e545d>

**Les limites des fonctions de hachage :**  

   - Elles ne garantissent pas l'absence totale de collisions.  
   - Leur efficacité dépend de la qualité de la fonction de hachage choisie.  


**Exemples de fonctions de hachage populaires :**  

- MD5 (désormais considéré comme obsolète en cryptographie). 

- SHA-1 (déprécié pour des raisons de sécurité).  

**Longueur de l'empreinte** : SHA-1 produit une empreinte de 160 bits (40 caractères hexadécimaux).  

**Pourquoi elle est dépréciée ?**  
  SHA-1 n'est plus considéré comme sécurisé, car des chercheurs ont trouvé des moyens de générer des **collisions** (deux données différentes produisant la même empreinte) en un temps raisonnable avec des ressources informatiques modernes. Cela rend SHA-1 inadapté pour des usages sensibles comme la cryptographie ou la vérification d'intégrité.  

**Exemple** :  
```python
import hashlib

data = "Message important"
hash_object = hashlib.sha1(data.encode())
sha1_hash = hash_object.hexdigest()
print(sha1_hash)  # Exemple d'empreinte : a5e64f98b819a40e05d15ec2cbd7d25544f6f435
```
???+ question "Tester ce qui est proposé"

    {{ IDE() }}


- SHA-256 (très courant et plus sécurisé)

**Longueur de l'empreinte** : SHA-256 produit une empreinte de 256 bits (64 caractères hexadécimaux).  

**Pourquoi est-il utilisé ?**  
  SHA-256 est beaucoup plus robuste que SHA-1, car il est conçu pour éviter les collisions et les attaques par force brute. Il est largement utilisé dans des domaines sensibles comme la sécurité informatique, la blockchain, et les signatures numériques.  

**Exemple** :  
```python
import hashlib

data = "Message important"
hash_object = hashlib.sha256(data.encode())
sha256_hash = hash_object.hexdigest()
print(sha256_hash)  # Exemple d'empreinte : 9e31b9c8c694b1616dfd28481f54741a421d2481a18c62e531b34a79b36520b4
```

???+ question "Tester ce qui est proposé"

    {{ IDE() }}


**Applications simples :**

1 **Vérification d'intégrité des fichiers :**

   - Avant de télécharger un fichier (par exemple un logiciel), on vous fournit une empreinte (souvent en SHA-256). 

   - Après le téléchargement, vous calculez l'empreinte de votre fichier et vérifiez qu'elle correspond à celle fournie. 

   - **But** : S'assurer que le fichier n'a pas été modifié ou corrompu pendant le transfert.

   **Exemple pratique :**  

   Vous téléchargez un fichier "important.iso" et l'empreinte fournie par le site est :  
   `d2a6c7b04f09d856a0e6b7a4c5d4c8c9d9e8f7e2e67f6c98d8c7e4b5c4d3b2a1`  
   Vous calculez ensuite :  
   ```python
   hash_file = hashlib.sha256(open("important.iso", "rb").read()).hexdigest()
   print(hash_file)
   ```  
   Si les deux empreintes sont identiques, le fichier est fiable.

---

2 **Stockage sécurisé des mots de passe :**

   - Quand un utilisateur crée un compte, son mot de passe n'est jamais stocké directement. Au lieu de cela, une empreinte est générée avec SHA-256 (ou une version améliorée comme PBKDF2).  

   - Quand l'utilisateur se connecte, son mot de passe saisi est haché et comparé à l'empreinte stockée. Si elles correspondent, l'accès est accordé.  

   **Pourquoi ne pas stocker les mots de passe en clair ?**  
   
   Si une base de données est piratée, les mots de passe sont protégés, car il est pratiquement impossible de retrouver l'original à partir de l'empreinte.  

   **Exemple simple :**  
   ```python
   def store_password(password):
       hash_object = hashlib.sha256(password.encode())
       return hash_object.hexdigest()

   stored_hash = store_password("motDePasse123")
   print(stored_hash)
   # Empreinte stockée : d2d2d2c7e9d3f4d4c8e7c7e5a6d3e4b8d7c9f6a4b6e4c8e2
   ```

???+ question "Tester ce qui est proposé"

    {{ IDE() }}

!!! info "Capytale : Utilisation des dictionnaires (activite_dico)"



### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667943"></a>**6.5. 🧪 Rappel : Utilisation des dictionnaires en Python**</H3>

📘 Dans un dictionnaire, les clés sont stockées dans une **table de hachage**, ce qui explique pourquoi cette structure est **optimisée pour la recherche sur les clés**.

🎥 Pour vous remémorer les bases, vous pouvez consulter la vidéo suivante :
🔗 [Les dictionnaires](https://ladigitale.dev/digiview/#/v/66bcbd45219a3)

---

???+ question "🔎 Activité n° 42 : Itérer sur les éléments d’un dictionnaire"

    🦁 Au zoo de Beauval, on recense différents animaux :

    ```python
    if __name__ == "__main__":
        zoo_Beauval = {
            'éléphant': ('Asie', 5),
            'écureuil': ('Asie', 17),
            'panda': ('Asie', 2),
            'hippopotame': ('Afrique', 7),
            'girafe': ('Afrique', 4),
            'lion': ('Afrique', 17)
        }
    ```

    🦓 Et au zoo de La Flèche :

    ```python
    zoo_LaFleche = {
        'ours': ('Europe', 4),
        'tigre': ('Asie', 7),
        'girafe': ('Afrique', 11),
        'hippopotame': ('Afrique', 3)
    }
    ```

    On veut créer une fonction `plus_grand_nombre()` qui retourne l’animal **le plus représenté** dans un zoo donné.

    ```python
    assert plus_grand_nombre(zoo_LaFleche) == 'girafe'
    assert plus_grand_nombre(zoo_Beauval) == 'écureuil'
    ```

    1️⃣ Quel type de boucle peut-on envisager pour le code de cette fonction ?

    ```python
    for cle in dico.keys()
    for valeur in dico.values()
    for (cle, valeur) in dico.items()
    Aucune boucle.
    ```
    ??? success "❇️ Solution :"
        ```
        ✅ for (cle, valeur) in dico.items()
        ```

    2️⃣ ✏️ Écriture de la fonction :

    ??? success "❇️ Solution :"

        ```python
        def plus_grand_nombre(zoo):
                max_nombre = 0
                animal_max = None
                for animal, tple in zoo.items():
                    if tple[1] > max_nombre:
                        max_nombre = tple[1]
                        animal_max = animal
                return animal_max
        ```



    🐘 Maintenant, on veut une fonction `nombre_total()` qui prend en paramètre un zoo et un **continent**, et renvoie le **nombre total d'animaux** originaires de ce continent :

    ```python
    assert nombre_total(zoo_LaFleche, 'Afrique') == 14
    assert nombre_total(zoo_Beauval, 'Asie') == 24
    ```

    3️⃣ Quel type de boucle peut-on envisager pour le code de cette fonction ?

    ```python
    for cle in dico.keys()
    for valeur in dico.values()
    for (cle, valeur) in dico.items()
    Aucune boucle.
    ```

    ??? success "❇️ Solution :"
        ```✅ for (cle, valeur) in dico.items()```

    4️⃣ ✏️ Écriture de la fonction :

    ??? success "❇️ Solution :"

        ```python
        def nombre_total(zoo, continent):
            total = 0
            for (animal, (cont, nb)) in zoo.items():
                if cont == continent:
                    total += nb
            return total
        ```



    🐼 Enfin, une fonction `nombre()` qui retourne le **nombre d’un animal donné** dans un zoo :

    ```python
    assert nombre(zoo_LaFleche, 'panda') == 0
    assert nombre(zoo_Beauval, 'panda') == 2
    ```

    5️⃣ Quel type de boucle peut-on envisager pour le code de cette fonction ?

    ```python
    for cle in dico.keys()
    for valeur in dico.values()
    for (cle, valeur) in dico.items()
    Aucune boucle.
    ```

    ??? success "❇️ Solution :"
        ```✅ Aucune boucle```

    6️⃣ ✏️ Écriture de la fonction :

    ??? success "❇️ Solution :"

        ```python
        def nombre(zoo, animal):
            return zoo[animal][1] if animal in zoo else 0
        ```

🕒 **Le temps de recherche** dans un dictionnaire est **indépendant du nombre d’entrées**, contrairement à une liste.
💡 C’est donc une **structure très efficace** pour accéder à des données par clé.

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc151667944"></a>**6.6. 📊 La complexité**</H3>

![](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.039.png){width=50%; : .center }

🔁 Les structures précédentes (tableaux, dictionnaires simples…) **ne permettent pas toujours une efficacité maximale**.

🎯 On vise une **complexité logarithmique** pour des opérations comme :

* la recherche 🔍
* l’insertion ➕
* la suppression ❌

🌳 C’est possible grâce à des structures plus évoluées comme les **arbres binaires de recherche (ABR)**.




## <H2 STYLE="COLOR:BLUE;">💡 <a name="_toc151667945"></a>**7. Exercices**</H2>

**=> CAPYTALE Le code vous sera donné par votre enseignant**

!!! abstract "**Exercice n°1 : Implémentation d’une file avec deux piles avec les listes chainées**"

    Comment créer une file avec 2 piles ?

    L'idée est la suivante : on crée une pile d'entrée et une pile de sortie.

    - quand on veut enfiler, on empile sur la pile d'entrée.
    - quand on veut défiler, on dépile sur la pile de sortie.
    - si celle-ci est vide, on dépile entièrement la pile d'entrée dans la pile de sortie.

    ![](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.040.png){width=50%; : .center }

    ```python
    # il est impératif de comprendre qu'on peut choisir l'implémentation
    # de la classe Pile qu'on préfère parmi les deux traitées plus haut.
    # Comme elles ont la MÊME INTERFACE et qu'on ne va se servir que
    # de cette interface, leur mécanisme interne n'a aucune influence
    # sur le code de la classe File que nous ferons ensuite.

    # Par exemple, on choisit celle avec la liste chaînée :

    class Cellule :
        def __init__(self, contenu, suivante):
            pass

    class Pile:
        def __init__(self):
            pass

        def est_vide(self):
            pass

        def empile(self, x):
            pass

        def depile(self):
            pass

        def __str__(self):
            s = ""
            c = self.data
            while c is not None:
                s += str(c.contenu)  # Ajouter la valeur de la cellule
                if c.suivante is not None:  # Ajouter un séparateur si ce n'est pas le dernier élément
                    s += " -> "
                c = c.suivante
            return s if s else ""  # Retourner un message "" si la pile est vide

    p = Pile()
    print( p.est_vide())  # True

    # Empiler des éléments
    p.empile(10)
    p.empile(20)
    p.empile(30)

    print(p)  # |30|20|10|
    print(p.est_vide())  # False

    # Dépiler des éléments
    print(p.depile())  # 30
    print(p)  # |20|10|
    print(p.depile())  # 20
    print(p)  # |10|

    # Tester défilement jusqu'à vide
    print(p.depile())  # 10
    print(p.est_vide())  # True

    # -------------------------------------------------------    
    # Implémentation d'une file à l'aide de deux piles 

    class File:
        def __init__(self):
            self.entree = Pile()
            self.sortie = Pile()

        def est_vide(self):
            pass

        def enfile(self,x):
            pass

        def defile(self):
            pass
        
        def __str__(self):
            return str(self.entree) + " " + str(self.sortie)
        

    f = File()
    print(f.est_vide())  # True

    # Ajouter des éléments dans la file
    f.enfile("Lundi")
    f.enfile("Mardi")
    f.enfile("Mercredi")
    print(f)

    # Défilage d'éléments
    print(f.defile())  # Lundi
    print(f)

    print(f.defile())  # Mardi
    print(f)

    # Ajouter un nouvel élément
    f.enfile("Jeudi")
    print(f)

    # Défilage jusqu'à vide
    print(f.defile())  # Mercredi
    print(f.defile())  # Jeudi
    print(f.est_vide())  # True
    ```

!!! abstract "**Exercice n°2 : Structure de données**"

    Quelle structure de données choisir pour chacune de ces tâches ? 

    1. Représenter un répertoire téléphonique.
    1. Stocker l'historique des actions effectuées dans un logiciel et disposer d'une commande Annuler (ou Undo).
    1. Envoyer des fichiers au serveur d'impression

!!! abstract "**Exercice n°3 : La calculatrice HP**"

    La Notation Polonaise Inversée (NPI) permet d'écrire des opérations arithmétiques, sans utiliser de parenthèses. Ici, nous nous limiterons à des nombres entiers naturels et aux opérations+, -, \* et/ sur eux. Dans cette notation, les opérateurs sont écrits après les opérandes (nombres entiers naturels). Par exemple l'expression classique : 

    13\*(3+2)

    Donne en NPI 

    3 2 +13 \*

    On écrit et on exécute les opérations dans le sens des priorités vues en cours de mathématiques. Dans cette notation, on réalise

    - L'addition entre 3 et 2 ( 3 2 + )
    - La multiplication entre le précédent résultat et 13 ( 13 \*)
    - On a ainsi le résultat.

    1 Donner la File correspondante à la saisie NPI de l'exemple. Faire de même avec la Pile.
    2 Quelle est la structure adaptée à la résolution de l'expression ?

    Note : On remarquera qu'on doit toujours avoir 2 opérandes pour un opér

    ateur. li faut stocker le résultat intermédiaire dans la structure pour effectuer la suite des calculs.

    3 En utilisant les opérations du type abstrait Pile, proposer une fonction permettant d'afficher le résultat d'une expression en NPI.

    Note : On supposera également que la syntaxe en NPI est correcte.

    ```python
    def evaluer_npi(pile):
        # Pile pour stocker les opérandes
        p = []

        pass


        return p.pop()


    pile = [3, 2, "+", 13, "*"]
    assert evaluer_npi(pile) == 65

    pile = [4, 5, "+", 2, "*"]
    assert evaluer_npi(pile) == 18

    pile = [10, 2, "/"]
    assert evaluer_npi(pile) == 5

    pile = [15, 7, "-", 1, "+"]
    assert evaluer_npi(pile) == 9

    pile = [15, 7, 1, 1, "+", "-", "/", 3, "*", 2, 1, 1, "+", "+", "-"]
    assert evaluer_npi(pile) == 5

    pile = [10, 0, "/"]
    try:
        evaluer_npi(pile)
    except AssertionError as e:
        assert str(e) == "Division par zéro impossible."

    ```

!!! abstract "**Exercice n°4 : Types abstraits**"

    1\. Quelle opération ne fait pas partie de l'interface d'une pile ?

    1. ajouter un élément à la pile 
    1. retirer l'élément le plus récent de la pile 
    1. retirer l'élément le plus ancien de la pile 

    2\. Quelle opération ne fait pas partie de l'interface d'une file?

    1. ajouter un élément à la file 
    1. retirer l'élément le plus récent de la file 
    1. retirer l'élément le plus ancien de la file 

    3\. L'opération dequeue d'une file s'exécute en un temps qui est proportionnel au nombre de valeurs stockées dans la file.

    1. Faux 
    1. Vrai

    4\. Un tableau associatif permet de créer une association clé -> valeur.

    Pour stocker des numéros de téléphone à l'aide d'un tableau associatif, quelle solution semble préférable, dans la mesure où il peut y avoir des homonymes?

    1. La clé est le numéro de téléphone, et la valeur est le nom correspondant 
    1. La clé est le nom et la valeur est le numéro de téléphone correspondant 
    1. La clé est le nom et la valeur la collection des numéros de téléphone correspondants 
    1. La clé est un simple numéro unique et la valeur le couple nom/téléphone

!!! abstract "**Exercice n°5 : Type list en Python**"

    1\. Le type list utilisé dans Python correspond le mieux :

    1. au type abstrait liste chaînée 
    1. au type abstrait file 
    1. au type abstrait tableau 

    2\. La récupération d'un élément d'un objet Python de type list, connaissant son indice :

    1. nécessite un temps proportionnel au nombre d'éléments de la liste 
    1. s'effectue en temps constant 
    1. est impossible 

    3\. Sur un objet de type list Python, quelles opérations sont faites en un temps indépendant de la longueur de la liste?

    1. supprimer le premier élément 
    1. supprimer le dernier élément
    1. ajouter un élément au début (en position 0)
    1. ajouter un élément à la fin

!!! abstract "**Exercice n°6 : Structures de donnés Python**"

    1\. Pour implémenter une pile avec Python, on peut se servir d'un type de données disponible dans le langage :

    1. le type list 
    1. le type dict 
    1. le type set 
    1. le type tuple 

    2\. Accéder à une valeur dans un dictionnaire à partir de la clé à laquelle la valeur est associée est réalisé :

    1. en un temps proportionnel à la taille du dictionnaire 
    1. en un temps constant 

!!! abstract "**Exercice n°7 : Pile classique**"

    Nous allons réaliser une classe Pile en utilisant une liste Python. Voici le contructeur de la classe

    ```python
    class Pile:
        """Structure  de  pile"""
        def init (self): 
            self.contenu = []
            
        # à compléter   
            
        def __str__(self):
            return " -> ".join(map(str, reversed(self.contenu)))

    # Création d'une instance de la pile
    p = Pile()

    # Vérifier si la pile est vide
    print(p.est_vide())  # True

    # Empiler des éléments
    p.empiler(10)
    p.empiler(20)
    p.empiler(30)
    print(p)  # 30 -> 20 -> 10

    # Dépiler des éléments
    print(p.depiler())  # 30
    print(p)  # 20 -> 10

    # Empiler un nouvel élément
    p.empiler(40)
    print(p)  # 40 -> 20 -> 10

    # Dépiler jusqu'à vider la pile
    print(p.depiler())  # 40
    print(p.depiler())  # 20
    print(p.depiler())  # 10
    print(p.est_vide())  # True

    # Tentative de dépiler une pile vide
    try:
        p.depiler()
    except IndexError as e:
        print("Erreur :", e)  # La pile est vide
                    
        
    ```

    1 Implémentez la méthode est\_vide(self) qui retourne True si la Pile est vide et False sinon.

    2 Implémentez la méthode empiler(self,v) qui ajoute la valeur v au sommet de la pile (et donc en fin de la liste)

    3 Implémentez la méthode depiler(self) qui :

    1. lève une exception *IndexError* si la liste est vide ;
    1. sinon, retire l’élément au sommet de la pile et le retourne.

    4 **Bonus :** Vous pouvez implémenter la méthode spéciale str (self)

    !!! info
        ```python
            def __str__(self):
                return "Pile : " + " -> ".join(map(str, reversed(self.contenu)))
        ```  

        **1. reversed(self.contenu) :**

        reversed() est une fonction Python qui retourne un itérateur avec les éléments de la liste dans l'ordre inverse.

        Cela est nécessaire car dans une pile (LIFO), le dernier élément ajouté est en haut, donc on souhaite afficher les éléments du sommet vers la base.

        **2. map(str, reversed(self.contenu)) :**

        map est une fonction Python qui applique une fonction à chaque élément d'une collection (liste, itérateur, etc.).
        Ici, map(str, ...) convertit chaque élément retourné par reversed(self.contenu) en chaîne de caractères (str).

        Pourquoi utiliser map ? Cela évite de devoir écrire une boucle pour convertir chaque élément en chaîne de caractères.

        **3. " -> ".join(...) :**

        join est une méthode des chaînes de caractères en Python.

        Elle prend une liste de chaînes en entrée et concatène tous les éléments en insérant la chaîne spécifiée (ici " -> ") entre eux.
    !!!

!!! abstract "**Exercice n°8 :** annulé"



!!! abstract "**Exercice n°9 : pile ou file et parenthèse**"

    On dit qu’une chaîne de caractères comprenant, entre autre choses, des parenthèses ( et ) est bien parenthésée lorsque chaque parenthèse ouvrante est associée à une unique parenthèse fermante, et réciproquement.

    Ecrire une fonction prenant en paramètres :

    - une chaîne de caractères bien parenthésée ;
    - l’indice d’une parenthèse fermante.

    et qui retourne l’indice de la parenthèse ouvrante associée.

    ```python
    def trouver_parenthese_ouvrante(chaine, indice_fermante):
        pile = ...  # Pile pour stocker les indices des parenthèses ouvrantes
        pass

    assert trouver_parenthese_ouvrante("(a + b)", 6) == 0  
    assert trouver_parenthese_ouvrante("((a + b) * c)", 7) == 1  
    assert trouver_parenthese_ouvrante("a + (b + (c + d))", 15) == 9 
    assert trouver_parenthese_ouvrante("(a + (b + (c)))", 13) == 5 
    ```

!!! abstract "**Exercice n°10 : file et copie**"

    Vous allez améliorer la classe file en lui ajoutant quelques fonctionnalités. Vous pouvez utiliser, comme base de travail, l’implémentation des files avec les doubles piles ou celle avec les listes chaînées  

    1. Ajouter la méthode spéciale \_\_len\_\_ (self) qui renvoie la longueur d’une file.

    ```python
    class Cellule :
        def __init__(self, contenu, suivante):
            pass

    class Pile:
        def __init__(self):
            pass

        def est_vide(self):
            pass

        def empile(self, x):
            pass

        def depile(self):
            pass

        def __str__(self):
            s = ""
            c = self.data
            while c is not None:
                s += str(c.contenu)  # Ajouter la valeur de la cellule
                if c.suivante is not None:  # Ajouter un séparateur si ce n'est pas le dernier élément
                    s += " -> "
                c = c.suivante
            return s if s else ""  # Retourner un message "" si la pile est vide

    class File:
        def __init__(self):
            self.entree = Pile()
            self.sortie = Pile()

        def est_vide(self):
            pass

        def enfile(self,x):
            pass

        def defile(self):
            pass
        
        def __str__(self):
            return str(self.entree) + " " + str(self.sortie)

            
        def __len__(self):
            pass
        

    f = File()
    f.enfile("Lundi")
    f.enfile("Mardi")
    f.enfile("Mercredi")
    f.enfile("Jeudi")
    print(len(f))
    f.defile()
    len(f)
    ```
    2 Ecrire une fonction copie\_file(f) recevant une file (f) comme argument et renvoyant une copie f2 de f. Attention, la file f doit (bien sûr) être conservée !

    Tester avec avec f
    et la copie_file de f

!!! abstract "**Exercice n°11 : Le problème de Josephus**"

    Josephus Flavius était un célèbre historien du premier siècle. Durant une guerre il fut pris au piège dans une cave avec son groupe de 40 soldats, entouré par les troupes ennemies. La légende raconte que le groupe encerclé préféra se suicider plutôt que d'être capturé. Ainsi Josephus et ses soldats formèrent un cercle et décidèrent de se tuer mutuellement et successivement, de manière à ce qu'une personne tue la troisième personne sur sa gauche, que la personne à droite du mort tue à son tour la troisième personne sur sa gauche, ainsi de suite jusqu'à ce qu'il ne reste qu'un seul survivant. Restant seul, ce dernier est censé se suicider lui-même. Josephus, qui ne souhaitait pas mourir, trouva rapidement la place sûre, c'est-à-dire la place de la dernière personne debout, sans que quiconque ne reste pour le tuer. Ainsi il resta en vie et put par la suite raconter cette légende. Trouver cette place sûre est maintenant appelé le problème de Josephus.

    Durant cet exercice nous implémenterons un programme qui simulera une version généralisée du problème de Josephus de la manière suivante : étant donnés n soldats, placés en cercle aux positions [0 ; n-1] avec 0 comme position de départ, il faut retirer chaque m-ième soldat jusqu'à ce que tous les soldats (même Josephus pour simplifier les choses) soient retirés.

    Dans l'exemple ci-dessous, nous commençons avec 8 soldats, et nous tuons à chaque tour le troisième soldat sur la gauche (remarquez que lorsqu'il reste au plus trois personnes vivantes, le soldat tuant se compte lui-même dans cette distance de trois soldats):

    ![](Aspose.Words.3ce2697d-9906-42ed-81f7-b7f514336a4d.043.png){width=80%; : .center }

    Le programme que vous devez développer devra prendre comme entrées les nombres n et m, respectivement le nombre de soldats et la distance (dans l'exemple nous avons n=8 et m=3), et produire comme sortie l'ordre dans lequel les soldats seront tués, le dernier "tué" étant finalement le survivant :

    4 7 2 6 3 1 5 8 The surviving soldier is 8

    c'est-à-dire que le soldat à la position 4 est le premier à être tué, et 8 est la place sûre recherchée par Josephus.

    La fonction josephus qui fait appel à la TAD file est donnée ci-dessous

    !!! info
    Le TAD signifie Type Abstrait de Données (Abstract Data Type en anglais). C'est un concept théorique en informatique qui définit une structure de données uniquement par les opérations qu'elle propose, indépendamment de son implémentation concrète.
    !!!

    Pour le problème de Josephus, nous ajoutons les éléments suivants :

    1. Initialisation :

    Les personnes sont placées dans la file dans l'ordre initial.

    2 Rotation circulaire :

    On utilise les opérations defile et enfile pour faire circuler les personnes dans le cercle.

    3 Élimination :

    Après avoir déplacé les m−1 premières personnes en fin de file, on utilise defile pour éliminer la m-ième personne.

    4 Répétition :

    On continue le processus jusqu'à ce qu'il reste un seul élément dans la file.


    Implémenter la file avec une liste chainée pour que la fonction josephus([1, 2, 3, 4, 5, 6, 7, 8], 3) 


    Pour simplifier on peut d’abord sortir : 4 7 2 6 3 1 5 8 the last one is 8

    ```python
    class Node:
        def __init__(self, value = None, next = None):
            self.v = ...
            self.n = ...

    class File:
        def __init__(self, c=None):
            self.head = ...

        def estVide(self):
            pass
        
        def enfile(self, element):
            ### version enfiler par la queue et défiler par la tete
            if self.estVide():
                self.head = Node(element)
            else:
                ...
        
        def defile(self):
            ### version enfiler par la queue et défiler par la tete
            if not self.estVide():
                ...
            else:
                raise IndexError("File vide")

        
        def __str__(self):  # on peut mettre __repr__ à la place pour éviter de taper print
            if self.head is None:
                raise IndexError("File vide")
            else:
                result = str(self.head.v)
                next_node = self.head.n
                while next_node is not None:
                    result += " - " + str(next_node.v)
                    next_node = next_node.n
                return result
        
                
        def __len__(self):
            pass
    ```
    Implémenter la fonction josephus(liste, m)

    ```python
    def josephus(liste, m):
        f = File()

        # Initialisation : enfiler toutes les personnes
        ...
        
        # on part du numéro 1 qu'en va renfiler 

        # Élimination des personnes
        while len(f) > 1:
            # Faire circuler les m-1 premières personnes
            ...    
                # On défiler et renfile 
                ...
            # Éliminer la m-ième personne
            elimine = ...
            print(f"Personne éliminée : {elimine}")

        # Retourner le dernier survivant
        survivant = ...
        print(f"Le survivant est : {survivant}")
        return survivant

    # Exemple : 8 personnes et élimination toutes les 3 positions
    liste_personnes = [1, 2, 3, 4, 5, 6, 7, 8]
    m = 3

    # Appel de la fonction josephus
    dernier_survivant = josephus(liste_personnes, m)
    print(dernier_survivant)

    ```

!!! abstract "**Exercice n°12 : Le jeu de cartes : bataille**"

    Compléter le programme ci-dessous du jeu de la bataille. Sur **Thonny** : On l’appelera bataille.py

    Vous aurez à  gérer d'une part la valeur des cartes et d'autre part les cas d'égalités.

    **Indice** : il faut créer une file égalité.

    Le programme partiel du jeu de bataille :

    **Créer et importer une File**

    ```python
    class Node:
        def __init__(self, value = None, next = None):
            self.v = ...
            self.n = ...

    class File:
        def __init__(self, c=None):
            self.head = ...

        def estVide(self):
            pass
        
        def enfiler(self, element):
            ### version enfiler par la queue et défiler par la tete
            if self.estVide():
                self.head = Node(element)
            else:
                ...
        
        def defiler(self):
            ### version enfiler par la queue et défiler par la tete
            if not self.estVide():
                ...
            else:
                raise IndexError("File vide")

        
        def __str__(self):  # on peut mettre __repr__ à la place pour éviter de taper print
            if self.head is None:
                raise IndexError("File vide")
            else:
                result = str(self.head.v)
                next_node = self.head.n
                while next_node is not None:
                    result += " - " + str(next_node.v)
                    next_node = next_node.n
                return result
        
                
        def __len__(self):
            pass
    ```

    ```python
    import random

    paquet_alice = File()
    paquet_basile = File()
    ...  # Initialisation de la file pour les égalités

    # crée le jeu de 52 cartes
    cartes = [i for i in range(0, 52)]
    # melange les cartes
    random.shuffle(cartes)
    # distribue les cartes aux 2 joueurs
    for i in range(len(cartes) // 2):
        paquet_alice.enfiler(cartes.pop())
        paquet_basile.enfiler(cartes.pop())


    # Gestion d'un tour de jeu
    def tour():
        global en_cours
        if paquet_alice.estVide():
            print("Alice perd")
            en_cours = False
        elif paquet_basile.estVide():
            print("Basile perd")
            en_cours = False
        else:
            tirer()


    # Si la partie n'est pas terminée, tirage d'une carte
    def tirer():
        a = paquet_alice.defiler()
        b = paquet_basile.defiler()

        valeura = a % 13
        valeurb = b % 13
        print("Alice", valeura, valeurb, "Basile")
        # le programme ne gere pas l'égalité
        if valeura > valeurb:
            paquet_alice.enfiler(a)
            paquet_alice.enfiler(b)
        elif valeura < valeurb:
            paquet_basile.enfiler(b)
            paquet_basile.enfiler(a)
        else: 
            ...


    # démarrage du jeu
    en_cours = True
    nb_tours = 0
    while en_cours:  # not paquet_alice.est_vide() and not paquet_basile.est_vide()  :
        tour()
        nb_tours += 1
    print("Partie en ", nb_tours, " tours")
    ```




    Une fois terminé les modifications, vous transformerez le programme bataille en classe Bataille avec toutes les fonctions encapsulées dans celle-ci.

    ```python
    import random


    class Bataille:
        def __init__(self, paquet_alice, paquet_basile):
            self.paquet_alice = paquet_alice
            self.paquet_basile = paquet_basile
            self.egalite = File()
            self.en_cours = True
        
        def tour(self):
            pass
        
        def tirer(self):
            pass
            
    # Initialisation des paquets
    paquet_alice = File()
    paquet_basile = File()

    # Création et mélange du jeu de 52 cartes
    cartes = [i for i in range(0, 52)]
    random.shuffle(cartes)

    # Distribution des cartes aux 2 joueurs
    for i in range(len(cartes) // 2):
        paquet_alice.enfiler(cartes.pop())
        paquet_basile.enfiler(cartes.pop())

    # Démarrage du jeu
    en_cours = True
    nb_tours = 0
    jeu = Bataille(paquet_alice, paquet_basile)

    while jeu.en_cours:
        jeu.tour()
        nb_tours += 1

    print(f"Partie terminée en {nb_tours} tours.")
    ```

## <H2 STYLE="COLOR:BLUE;">🔍 <a name="_toc151667946"></a>**8. Projets**</H2>

!!! abstract "**Projet n°01 : Pile et contrôle du parenthésage d’une expression**

    **=> CAPYTALE Le code vous sera donné par votre enseignant**

    Il s’agit d’écrire une fonction qui contrôle si une expression mathématique, donnée sous forme d’une chaine de caractères, est bien parenthésée, c’est-à-dire s’il y a autant de parenthèses ouvrantes que de fermantes, et qu’elles sont bien placées. Par exemple :

    - (()) est bien parenthésée
    - ())( ne l’est pas

    L’algorithme :

    On crée une pile

    On parcourt l’expression de gauche à droite

    A chaque fois que l’on rencontre une parenthèse ouvrante "( " on l’empile.

    Si on rencontre une parenthèse fermante " ) " et que la pile n’est pas vide on dépile (sinon on retourne faux). 

    A la fin la pile doit être vide…

    Ecrire une fonction verification(expression) qui prend en paramètre une chaine de caractère qui retourne OK si l’expression est bien parenthésée et NON sinon.

    assert verification("(())") == "OK"
    assert verification("())(") == "NON"

!!! abstract "**Projet n°02 : implémentation d’une liste chainée**"

    **=> CAPYTALE Le code vous sera donné par votre enseignant**

    A partir de ce qui a été vu sur les listes chaînées, implémenter :

    1. La méthode lenListe(self) qui retourne la longueur de la liste
    1. La méthode insert\_next(self, i, x) qui ajoute une cellule contenant la valeur x après la cellule d’indice i. Déterminer sa complexité
    1. La méthode get\_node\_index(self, i) qui permet de retourner la cellule d’indice i. Déterminer son ordre de complexité
    1. La méthode delete\_head(self) qui supprime la première cellule de la liste et la renvoie. Déterminer sa complexité
    1. la méthode delete\_next(self, x) qui supprime la cellule située après la cellule de valeur x et le renvoie

    ```python


    lst = Liste()
    assert lst.isEmpty() == True
    assert lst.lenListe() == 0

    lst.insert_next(0, 10)  # liste : [10]
    assert lst.lenListe() == 1

    lst.insert_next(1, 20)  # liste : [10, 20]
    assert lst.lenListe() == 2

    lst.insert_next(2, 30)  # liste : [10, 20, 30]
    assert lst.lenListe() == 3
    
    assert lst.get_node_index(0).v == 10
    assert lst.get_node_index(1).v == 20
    assert lst.get_node_index(2).v == 30

    lst.insert_next(1, 25)  # liste : [10, 20, 25, 30]
    assert lst.lenListe() == 4

    assert lst.get_node_index(2).v == 25

    val = lst.delete_head() 
    # liste : [20, 25, 30]
    assert val == 10
    assert lst.lenListe() == 3
    assert lst.get_node_index(0).v == 20


    # liste actuelle : [20, 25, 30]
    val_del = lst.delete_next(20)

    # liste : [20, 30]
    assert val_del == 25
    assert lst.lenListe() == 2
    assert lst.get_node_index(1).v == 30
    ```

!!! abstract "**Projet n°03 : Pile et palindromes**"

    **=> CAPYTALE Le code vous sera donné par votre enseignant**

    Un palindrome est un mot qui se lit de la même façon de gauche à droite et de droite à gauche. Par exemple, abababa et un palindrome, ainsi que kayak et coloc.

    Les piles sont des structures très utiles pour détecter les palindromes : on peut lire le mot jusqu’à sa moitié, et empiler les lettres qu’on lit, puis arrivé à la moitié on lit les lettres tout en dépilant et en regardant si le résultat du dépilage correspond à la lettre lue. Si ce n’est pas le cas, le mot en entrée n’est pas un palindrome.

    S’il y a toujours égalité, c’est un palindrome.

    Il faut faire attention à distinguer les mots de longueur paire et impaire. Si le mot est pair, de longueur 2n, on lit n lettres en empilant, puis n lettres en dépilant. Si le mot est impair, de longueur 2n+1, on lit n lettres en empilant, on lit la lettre du milieu sans rien faire, puis on lit n lettres en dépilant.

    1 sur **Thonny** : Créer un fichier python pile.py

    2 Créer une classe Pile avec Un constructeur \_\_init\_\_() initialisant l’attribut **privé** que l’on appellera container à [] (liste vide Python)

    3 Implémenter la méthode publique get\_container dont le prototype est : get\_container(self) -> list et qui renvoie le contenu de la pile.

    4 Implémenter la méthode publique size() dont le prototypage est le suivant : size(self) -> int et qui renvoie la taille de la liste

    5 Implémenter la méthode publique is\_empty() qui renvoie True si la pile stockée dans le container est vide et False sinon. Le prototype est : is\_empty(self) -> bool

    6 Implémenter la méthode publique push(item) qui ajoute à la fin de la liste. On empile !!

    7 Implémenter la méthode publique pop() qui :

    - Retourne None si la pile est vide.
    - Retourne et enlève l’élément au sommet de la pile, si la pile n’est pas vide.

    8 Valider les tests unitaires (avec des assert) suivants à partir d’une pile p qui contient les éléments respectivement empilés 1 et 2 :

    - p.is\_empty() == False
    - p.get\_container() == [1,2]
    - p.pop() == 2

    9 Sur **Thonny** : Créer un fichier python palindrome.py

    10 Implémenter à l’aide d’une pile une fonction palindrome() qui prend en entrée un mot et renvoie True si c’est un palindrome et False sinon. On donne le prototype de la fonction palindrome(word : str) -> bool.

    11 Tester votre programme avec les tests suivants :

    - palindrome("kayak")
    - palindrome("trust")

!!! abstract "**Projet n°04 : File et ordonnancement**"

    **=> CAPYTALE Le code vous sera donné par votre enseignant**

    L’ordonnancement consiste, pour le système d’exploitation, à optimiser l’utilisation du processeur en lui affectant tour à tour différentes tâches à exécuter. On appelle processus un programme en cours d’exécution. Il peut y en avoir des centaines à la fois sur une machine, alors qu’il n’y a que quelques processeurs (souvent 4).

    L’ordonnanceur va répartir le temps de calcul entre les programmes, afin que tous puissent avancer dans leur exécution de manière satisfaisante, et que les programmes qui n’ont pas besoin de temps processeur à un certain moment (par exemple parce qu’ils attendent une réponse de l’utilisateur avant de continuer) ne gaspillent pas de temps de calcul.

    La plupart des ordonnanceurs modernes utilisent des files pour garder en mémoire de façon optimale les programmes à exécuter. En effet, tout comme la pile était une structure naturelle pour gérer les palindromes à l’exercice précédent, la file est parfaitement adaptée à l’ordonnancement : les programmes qui demandent du temps de calcul sont insérés en bout de file, et ceux qui seront défilés pour obtenir effectivement du temps processeur sont ceux qui attendent depuis le plus longtemps.

    1 Sur **Thonny** : Créer un fichier python file.py

    2 Créer une classe File avec Un constructeur \_\_init\_\_() initialisant l’attribut **privé** que l’on appellera container à [] (liste vide Python)

    3 Implémenter la méthode publique get\_container dont le prototype est : get\_container(self) -> list et qui renvoie le contenu de la file.

    4 Implémenter la méthode publique size() dont le prototypage est le suivant : size(self) -> int et qui ren

    voie la taille de la liste

    5 Implémenter la méthode publique is\_empty() qui renvoie True si la file stockée dans le container est vide et False sinon. Le prototype est : is\_empty(self) -> bool

    6 Implémenter la méthode publique queue(item) qui ajoute à la fin de la liste. On enfile !!

    7 Implémenter la méthode publique enqueue() qui :

    - Retourne None si la file est vide.
    - Retourne et enlève l’élément au début de la file, si la file n’est pas vide.

    8 Valider les tests unitaires (avec des assert) suivants à partir d’une file f qui contient les éléments respectivement enfilés 1 et 2 :

    - f.is\_empty() == False
    - f.get\_container() == [1, 2]
    - f.enqueue() == 1

    9 Sur **Thonny** : Créer un fichier python scheduler.py

    10 Créer une classe Activite pour modéliser des activités avec Un constructeur \_\_init\_\_() initialisant ayant trois attributs privés : name, time et priority. Le prototype est le suivant : \_\_init\_\_(self, name : str, time : int, priority : int)

    11 Un accesseur (getter) get\_time() qui renvoie la valeur de l’attribut time.

    12 Un accesseur (getter) get\_priority() qui renvoie la valeur de l’attribut priority.

    13 Une méthode publique execute() qui décrémente l’attribut time d’une valeur passée en paramètre appelée time à la méthode et qui renvoie un booléen indiquant si time est nul (True) ou non (False).

    **Aide** : time ne peut en aucun cas être < 0.

    14 Une méthode spéciale \_\_repr\_\_(self) renvoyant une chaîne représentant l’activité selon le format : ```<nom activité>: <temps>s [<priorité>]```. 

    **Aide** : on utilisera la méthode format() <https://python.sdv.univ-paris-diderot.fr/03_affichage/>

    15 Créer une classe Ordonnanceur sur le patron suivant :
    ```python
    import file as fl

    class Ordonnanceur:
        def __init__(self, quota=0):
            self.__file  = fl.File()
            self.__quota = int(quota)

        def set_quota(self, quota : int) -> int:
            # à compléter

        def add_activity(self, activity : object):
            # à compléter

        def step(self):
            # à compléter

        def run(self):
            # à compléter
    ```

    16 Compléter la méthode add\_activity() qui ajoute une activité passée en paramètre à la file de processus de l’ordonnanceur.

    17 Compléter le mutateur (setter) set\_quota()

    18 **★★** Modifier la méthode step() qui effectue un “tour” d’ordonnancement comme suit :

    - si la file est vide, on ne fait rien : on attend.
    - s’il y a au moins une activité dans la file, on exécute l’activité en affichant son nom et sa durée. Puis, on décrémente son temps d’une unité et si son quota arrive à 0, on enfile l’activité.

    19 **★★** Modifier la méthode run() qui itère step jusqu’à obtenir une file de processus vides.

    20 **★★** Créer une liste de 10 activités de durée et de priorité aléatoires (durée entre 1 et 10 et priorité entre 0 et 2).

    21 **★★** A l’aide d’une boucle, mettre toutes les activités dans la file de l’ordonnanceur puis exécuter l’ordonnanceur.

!!! abstract "**Projet n°05 : Implémentation du type abstrait tableau dynamique en Python**"

    **=> CAPYTALE Le code vous sera donné par votre enseignant**

    **Interface du type abstrait Tableau\_dynamique**

    L’interface de la classe est la suivante :
    ```python
    Help on class TableauDynamique in module __main__:

    class TableauDynamique(builtins.object)
    |  TableauDynamique() -> 'None'
    |  
    |  Classe implémentant le type « tableau dynamqie »,
    |  version très simplifiée du type « liste » de Python.
    |  
    |  Methods defined here:
    |  
    |  __getitem__(self: 'TableauDynamique', i: 'int') -> 'object'
    |      Retourne l'élément d'indice i.
    |  
    |  __init__(self: 'TableauDynamique') -> 'None'
    |      Création d'un tableau vide à l'initialisation.
    |  
    |  __len__(self: 'TableauDynamique') -> 'int'
    |      Retourne le nombre d'éléments dans le tableau.
    |  
    |  append(self: 'TableauDynamique', obj: 'object') -> 'None'
    |      Ajoute l'élément obj en dernière position dans le tableau.
    ```

    **Implémentation**

    1 Créer la classe **TableauDynamique**.

    2 Dans la méthode **\_\_init\_\_**, initialiser trois attributs privés **\_nbre**, **\_capacite** et **\_tab** tels que **\_nbre** donne le nombre d’éléments dans le tableau (initialement égal à 0), **\_capacite** donne le nombre maximal possible d’éléments dans le tableau (initialement égal à 1) et **\_tab** référence un tableau créé à l’aide de la fonction **py\_object** du module **ctypes**.

    **Remarque :** le code de création du tableau est le suivant :
    ```python
    def _construit_tableau(self: TableauDynamique, capacite: int):
        """
        Construction d'un tableau de capacité donnée.
        """
        return (capacite * ctypes.py_object)()
    ```

    3 Définir la méthode **\_\_len\_\_** dont la spécification est :
    ```python
    def __len__(self: TableauDynamique) -> int:
        """
        Retourne le nombre d'éléments dans le tableau.
        """
    ```

    4 Définir la méthode **\_\_getitem\_\_** dont la spécification est :
    ```python
    def __getitem__(self: TableauDynamique, i: int) -> object:
        """
        Retourne l'élément d'indice i.

        Une exception est levée si l'indice n'appartient
        pas au bon intervalle.
        """
    ```

    5 Définir la méthode privée **\_augmente\_taille** dont la spécification est :
    ```python
    def _augmente_taille(self: TableauDynamique, capacite: int) -> None:
        """
        Crée un nouveau tableau de dimension capacite puis copie tous les
        éléments de l'ancien tableau dans ce dernier.
        Fait en sorte que le nouveau tableau soit le tableau désormais
        utilisé.
        Met à jour l'attribut capacite.
        """
    ```

    6 Définir la méthode **append** dont la spécification est :
    ```python
    def append(self: TableauDynamique, obj: object) -> None:
        """
        Ajoute l'élément obj en dernière position dans le tableau.
        """
    ```

    **Remarque :** La méthode **append** doit appeler la méthode **\_augmente\_taille**.

    7 Définir la méthode **\_\_repr\_\_** dont la spécification est :
    ```python
    def __repr__(self: TableauDynamique) -> str:
        """
        Retourne la chaîne de caractères représentant le tableau.
        """
    ```

    8 Tester le bon fonctionnement de la classe.
