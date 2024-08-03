---
author: ELP
title: 04 La P.O.O.
---



**Table des matières**

[1.	Introduction](#_toc88030949)

[2.	Définitions](#_toc88030950)

[3.	Les trois fondamentaux](#_toc88030960)

[4.	Décorateurs (pour aller plus loin)](#_toc88030972)

[5.	Exercices](#_toc88030973)

[6.	Projet (démarche d’investigation)](#_toc88030974)

**Compétences évaluables :**

- Ecrire la définition d’une classe
- Accéder aux attributs et méthodes d’une classe


## <H2 STYLE="COLOR:BLUE;"> <a name="_toc88030949"></a>**1. Introduction**</H2>
La programmation orientée objet repose, comme son nom l'indique, sur le concept **d'objet**.

Chaque objet se décrit par un ensemble **d’attributs** (caractéristiques de l’objet) et un ensemble de **méthodes** portant sur des attributs (fonctionnalité de l’objet).

L’un des objectifs principaux de la notion d’objet est d’organiser des programmes complexes grâce aux notions :

- **l'encapsulation** des attributs empêche toute modification externe accidentelle (l’utilisateur va utiliser l’objet sans savoir ce qu’il contient. Par exemple, un conducteur de voiture). Le principe de l’encapsulation est **de regrouper dans le même objet**, les **données (attributs**) et les **traitements (méthodes**) qui lui sont spécifiques. Ainsi un objet est défini par ses attributs et ses méthodes.
- **l’abstraction** : L’intérêt de la POO est qu’elle permet de créer des objets possédant un certain degré d’abstraction. Ce processus d’abstraction consiste à identifier des caractéristiques et des mécanismes communs pour un ensemble d’éléments.

  **Attributs** : Ce sont les données de l’objets, ses caractéristiques.

  **Méthodes** : Ce sont les comportements de l’objet.

- **l'héritage** qui permet la ré utilisabilité du code, une classe Fille hérite d’une classe Mère (ex : classe Mère : animal, classe Fille : Panda)

  La **super-classe** (classe mère) déclare des méthodes et des attributs communs.

La **sous-classe** hérite des attributs, des méthodes et du type de la super-classe et peut les redéfinir (cf. polymorphisme).

- **le polymorphisme** : c’est la faculté pour une méthode portant le **même nom** mais appartenant à des classes distinctes héritées d’effectuer un **travail différent.** Cette propriété est acquise par la technique de la surcharge.

En terminal seules les deux premières notions sont au programme de NSI

## <H2 STYLE="COLOR:BLUE;"> <a name="_toc88030950"></a>**2. Définitions**</H2>
### <H3 STYLE="COLOR:GREEN;"> <a name="_toc88030951"></a>**2.1. Classe**</H3> 
Exemple :
```python
class Personne:

   """

   Classe des personnes

   """

   pass
```
- Un nom de classe commence toujours (c’est une convention) par une **lettre capitale** ;
- pass est l’instruction Python qui indique de ne rien faire.

Quelles actions a déclenché le code précédent ?
- Création d’un objet Classe Personne ;
- Création d’une variable Personne dans l’espace de nom global. Cette variable référence l’objet Classe Personne

La classe est une espèce de moule, à partir de ce moule nous allons créer des **objets** (plus exactement nous parlerons **d'instances**).

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc88030952"></a>**2.2. Objet ou instance**</H3>
Exemple :
```python
Julien = Personne() # c'est la personne numéro 1

Mathilde = Personne() # c'est la personne numéro 2
```

Quelles actions a déclenché le code précédent ?
- Création d’un **objet (ou instance)** de la classe Personne ;
- Création d’une variable Julien ou Mathilde dans l’espace de nom global. Chaque variable référence l’objet.

Julien et Mathilde sont des objets (des instances) de la classe Personne.

Afin d’en découvrir davantage sur Julien, taper et exécuter l’instruction suivante :
```python
print(Julien)
```
On obtient
```txt
<__main__.Personne object at 0x0000021C7CE97A10>
```
Julien appartient à l’espace de nom global et référence un objet de type Personne situé à l’adresse 0x0000021C7CE97A10.

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc88030953"></a>**2.3. Les méthodes**</H3>
#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030954"></a>**2.3.1. Définition**</H4>

Une méthode est une « **fonction** » définie dans une classe. Elle est **locale** à la classe. Elle correspond à une **action** agissant sur l'objet.

Par exemple : manger, marcher, parler, dormir sont des méthodes de la classe Personne. Tous les objets d’une même classe partagent les mêmes méthodes.

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030955"></a>**2.3.2. Les constructeurs ou initialiseur**</H4>
Parmi les différents types de méthode, il existe un type particulier : les **constructeurs** ou **initialiseur**.

Les constructeurs sont des **méthodes** qui construisent l'objet désigné par la classe au moment **d’instanciation** de la classe, c’est-à-dire ils permettent d’initialiser l’objet : ses attributs sont automatiquement créés, des valeurs par défaut peuvent même leur être affectées. Un constructeur porte le nom ```__init__```.

**<H3 STYLE="COLOR:red;">Activité n° 1 : Classe et constructeur**</H3>
```python
class Personne:
   """Classe définissant une personne caractérisée par :
   - son nom
   - son prénom
   - son âge"""

   def __init__(self, nom : str, prenom : str):   # le constructeur
      """ Pour l'instant, on ne va définir que 3 attributs """
      # Dans le constructeur, on crée des variables self.nom, self.prenom et self.age que 
      l’on initialise avec les paramètres passés au constructeur lors de l’instanciation.
      self.nom   = nom
      self.prenom    = prenom
      self.age   = 33

gollum = Personne('Dupont', 'Jean')
print("Je suis {0} {1}, j'ai {2} ans." . format(gollum.prenom, gollum.nom, gollum.age))
```

```txt
Je suis Jean Dupont, j'ai 33 ans.
```

Lors de la création de l’instance gollum, Python va automatiquement remplacer self par gollum et ainsi créer trois attributs :

- gollum.nom qui aura pour valeur le nom passé en paramètre (Dupont), 
- gollum.prenom qui aura pour valeur le prénom passé en paramètre (Jean),
- gollum.age qui aura pour valeur de départ la valeur donnée à self.age.

La définition du constructeur consiste en une définition « classique » d'une fonction. Elle a pour nom ```__init__```. En Python, **tous les constructeurs s'appellent ainsi**. Les noms de méthodes entourés de part et d'autre de deux signes soulignés (```__nommethode__```) sont des **méthodes spéciales**. Dans la définition de méthode, on passe un premier paramètre nommé self**.

self (c’est une convention) correspond simplement à l’objet sur lequel on applique la méthode (il représente l’objet en train de se créer).

Un **attribut** est une variable de classe propre à l’objet et sert à le caractériser.

Exemple : nom, prénom, age.

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030956"></a>**2.3.3. Les destructeurs**</H4>

Le **destructeur** d'une classe est une méthode spéciale lancée lors de la destruction d'un objet afin de récupérer les ressources (principalement la mémoire vive) réservée dynamiquement lors de l'instanciation de l'objet. Un constructeur porte le nom ```__del__```.

Le destructeur est appelé implicitement à la sortie du programme, ou explicitement à travers l’instruction del.

**<H3 STYLE="COLOR:red;">Activité n° 2 : Classe et destructeur**</H3>
```python
class Personne:
   """Classe définissant une personne caractérisée par :
   - son nom
   - son prénom
   - son âge"""

   def __init__(self, nom : str, prenom : str):   # le constructeur
      self.nom   = nom
      self.prenom    = prenom
      self.age   = 33
      print("Voici {0} {1}" . format(self.prenom, self.nom))

   def __del__(self): # le destructeur
      print("décédé(e) à {0} ans". format(self.age))

moi = Personne('Dupont', 'Jean')
del moi
```

```txt
Voici Jean Dupont
décédé(e) à 33 ans
```

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030957"></a>**2.3.4. Les autres méthodes**</H4>

Créer une **méthode d'instance**, revient à **créer une fonction** ayant comme premier paramètre le mot clef self.

**<H3 STYLE="COLOR:red;">Activité n° 3 : Classe et méthode**</H

3>
```python
class Personne:
   """Classe définissant une personne caractérisée par :
   - son nom
   - son prénom
   - son âge
   - son lieu de résidence"""
   def __init__(self, nom : str, prenom : str):   # le constructeur
      """ on ajoute un attribut lieu de résidence... """
      self.nom      = nom
      self.prenom       = prenom
      self.age      = 33
      self.residence = "Paris"

   def ma_residence(self):
      """ ...et la méthode associée au lieu de résidence """
      return "J'habite {0}." . format(self.residence)

qui = Personne('Dupont', 'Jean')
print("Je suis {0} {1}, j'ai {2} ans." . format(qui.prenom, qui.nom, qui.age))
print(qui.ma_residence())
```

```txt
Je suis Jean Dupont, j'ai 33 ans.
J'habite Paris.
```

Pour appeler une méthode de l’instance Personne, il suffit donc d’écrire instance.méthode().

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030958"></a>**2.3.5. Les méthodes pour représenter un objet**</H4>

**<H3 STYLE="COLOR:red;">Activité n° 4 : Surcharge de méthode :**</H3> 
La méthode spéciale ```__repr__``` retourne la chaine de caractère qu’il faut afficher lorsque l’on tape directement le nom de l’objet
```python
class Personne:
    """Classe représentant une personne"""
    def __init__(self, nom : str, prenom : str):
        self.__nom    = nom
        self.__prenom = prenom

    def __repr__(self):
        return self.__nom + " " + self.__prenom
```
```txt
Je suis Jean Dupont, j'ai 33 ans.
J'habite Paris.
```
**<H3 STYLE="COLOR:red;">Activité n° 5 : Surcharge de méthode :**</H3> 
La méthode spéciale ```__str__``` retourne la chaine de caractère qu’il faut afficher lorsque l’on appelle la fonction print sur l’objet
```python
class Personne:
    """Classe représentant une personne"""
    def __init__(self, nom : str, prenom : str):
        self.__nom    = nom
        self.__prenom = prenom

    def __str__(self):
        return self.__prenom + " " + self.__nom
toi = Personne('Durant', 'Jean')
print(toi)
```
```txt
Jean Durant
```

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc88030959"></a>**2.4. Attributs de classe**</H3>
Jusqu’à présent, les attributs sont contenus dans l’objet. Ils sont propres à l’objet : si on crée plusieurs objets, les attributs nom, prénom,… de chacun ne seront pas forcément identiques d’un objet à l’autre. Mais on peut aussi définir des **attributs dans la classe**.

**<H3 STYLE="COLOR:red;">Activité n° 6 : Classe et attributs de classe**</H3>
```python
class Personne:
   """Classe définissant une personne caractérisée par :
   - son nom
   - son prénom"""
   population = 0

   def __init__(self, nom : str, prenom : str):
      self.nom   = nom
      self.prenom    = prenom
      Personne.population += 1

moi = Personne('Dupont', 'Jean')
toi = Personne('Durant', 'Jean')
print(Personne.population)
```
```txt
2
```

On définit l’attribut de classe directement dans le corps de la classe **avant** la définition du constructeur. Lorsqu’on veut l’appeler dans le constructeur, on **préfixe le nom de l’attribut de classe** par le **nom de la classe :** Personne.population.

Et on y accède également en dehors de la classe.

A chaque fois que l’on crée un objet de type Personne, l’attribut de classe population s’incrémente de 1. Cela peut être utile d’avoir des attributs de classe, quand tous nos objets doivent avoir **certaines données identiques.**

## <H2 STYLE="COLOR:BLUE;"> <a name="_toc88030960"></a>**3. Les trois fondamentaux**</H2>

La POO est dirigée par trois fondamentaux qu'il convient de toujours garder à l'esprit : **encapsulation**, **héritage** et **polymorphisme**. Les deux derniers sont hors programmes.

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc88030961"></a>**3.1. Encapsulation**</H3>
L’encapsulation introduit une nouvelle manière de gérer les données. On cherche aussi à **masquer** aux yeux d’un programmeur extérieur tous les rouages d’un objet et donc l’ensemble des procédures et fonctions destinées à la **gestion interne de l’objet**, auxquelles le programmeur final n’aura pas à avoir accès.

L’encapsulation permet donc de **masquer un certain nombre d’attributs et méthodes** tout en laissant visibles d’autres attributs et méthodes.

On va définir des méthodes appelées des **accesseurs** et **mutateurs** (ou getter et setter en anglais). Les accesseurs donnent accès à l’attribut. Les mutateurs permettent de le modifier.

- Pour accéder à un attribut, au lieu d’écrire ```mon_objet.mon_attribut```, il faut écrire ```mon_objet.get_mon_attribut()```. 
- Pour modifier l’attribut ce sera ```mon_objet.set_mon_attribut(valeur)``` et non pas ```mon_objet.mon_attribut = valeur```.

![](Aspose.Words.427b5c12-e7cd-426a-b87c-f85884ba8965.003.png){: .center }

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030962"></a>**3.1.1. Attributs et méthode publics**</H4>
Comme leur nom l'indique, les attributs et méthodes dits publics sont **accessibles** depuis tous les descendants et dans tous les modules. On peut considérer que les éléments publics n'ont pas de restriction particulière.

**<H3 STYLE="COLOR:red;">Activité n° 7 : attributs publics**</H3>
```python
class Personne:
   """Classe définissant une personne caractérisée par :
   - son nom
   - son prénom
   - son âge"""

   def __init__(self, nom : str, prenom : str, age=33):
      self.nom   = nom
      self.prenom    = prenom
      self.age   = age

### Programme principal ###
qui = Personne('Dupont', 'Jean')

print(qui.nom)       # donne le nom
qui.nom = 'Durant'    # modifie l'attribut => INTERDIT
print(qui.nom)          # donne le nouveau nom
```

```txt
Dupont
Durant
```

Un **attribut** ne devrait être **public** que si sa modification n'entraîne **pas de changement dans le comportement de l'objet.** Dans le cas contraire, il faut **passer par une méthode**.

Modifier un attribut "manuellement" et ensuite appeler une méthode pour informer de cette modification est une **violation du principe d'encapsulation.**

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030963"></a>**3.1.2. Attributs et méthodes privés**</H4>

Python permet (plus ou moins) de protéger les attributs en leur donnant un nom qui commence par le double souligné **```__```** C’est une convention !!

Lorsqu’on crée un attribut (ou une méthode) dont le nom commence par ```__``` il n’est plus accessible directement. L’utilisateur ne pourra pas lire ni modifier directement les variables internes : il doit utiliser une méthode créée par les codeurs !! Ce sont les getter (accesseur) et setter (mutateur) .

Très souvent, les **accesseurs** en **lecture** verront leur nom commencer par get quand leurs homologues, les **mutateurs**, en **écriture** verront le leur commencer par set. Ainsi si on veut créer une méthode qui renvoie le nom, on pourrait la nommer ```get_name```.

**<H3 STYLE="COLOR:red;">Activité n° 8 : attributs privés et accesseur**</H3>
```python
class Personne:
    """Classe définissant une personne caractérisée par :
    - son nom
    - son prénom
    - son âge"""

    def __init__(self, nom : str, prenom : str, age=33):
        self.__nom   = nom        #attribut privé
        self.prenom    = prenom
        self.age   = age
    def get_name(self):
        return self.__nom

### Programme principal ###
qui = Personne('Dupont', 'Jean')

print(qui.get_name())     # donne le nom
print(qui.__nom)         # lève l’exception AttibuteError car l’attribut n’est plus accessible !!
qui.__nom = 'Durant'      # ne modifie pas l’attribut
print(qui.get_name())
```
On met en commentaire la ligne levant l’exception
```python
class Personne:
    """Classe définissant une personne caractérisée par :
    - son nom
    - son prénom
    - son âge"""

    def __init__(self, nom : str, prenom : str, age=33):
        self.__nom   = nom        #attribut privé
        self.prenom    = prenom
        self.age   = age
    def get_name(self):
        return self.__nom

### Programme principal ###
qui = Personne('Dupont', 'Jean')

print(qui.get_name())     # donne le nom
# print(qui.__nom)       # lève l’exception AttibuteError
qui.__nom = 'Durant'      # ne modifie pas l’attribut
print(qui.get_name())
```
```txt
Dupont
Dupont
```

**<H3 STYLE="COLOR:red;">Activité n° 9 : attributs privés et mutateur**</H3>
```python
class Personne:
    """Classe définissant une personne caractérisée par :
    - son nom
    - son prénom
    - son âge"""

    def __init__(self, nom : str, prenom : str, age=33):
        self.__nom   = nom        #attribut privé
        self.prenom    = prenom
        self.age   = age

    def get_name(self):
        return self.__nom

    def set_name(self, nom : str):
        nom = str(nom)        # il faut que le nom fourni soit un string
        self.__nom = nom

### Programme principal ###
qui = Personne('Dupont', 'Jean')

print(qui.get_name())
qui.set_name('Durant')     # modifie le nom
print(qui.get_name())
```

```txt
Dupont
Durant
```

Le mutateur récupère l’argument fournit dans le paramètre (nom) et place la chaine dans ```self.__nom```.

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030964"></a>**3.1.3. (Hors programme) Propriétés**</H4>

Les propriétés sont un moyen transparent de **manipuler des attributs d’objet**. Elles permettent de dire à Python : « Quand un utilisateur souhaite modifier cet attribut, fais cela ». De cette façon, on peut rendre certains attributs tout à fait **inaccessibles depuis l’extérieur de la classe**, ou dire qu’un attribut ne **sera visible qu’en lecture et non modifiable**. Ou encore, on peut faire en sorte que, si on modifie un attribut, Python recalcule la valeur d’un autre attribut de l’objet.

Pour l’utilisateur, c’est absolument transparent : il croit avoir, dans tous les cas, un accès direct à l’attribut. C’est **dans la définition de la classe** que l’on précise que tel ou tel attribut doit être accessible ou modifiable grâce à certaines propriétés.

Un constructeur porte le nom property. Elle attend quatre paramètres, tous optionnels :

- La méthode donnant accès à l’attribut ;
- La méthode modifiant l’attribut ;
- La méthode appelée quand on souhaite supprimer l’attribut ;
- La méthode appelée quand on demande de l’aide sur l’attribut.

En pratique, on utilise surtout les deux premiers paramètres : ceux définissant les méthodes d’accès et de modification, autrement dit les **accesseur** et **mutateur** d’objet.

**<H3 STYLE="COLOR:red;">(Hors programme) Activité n° 10 : Encapsulation de l’attribut**</H3>
```python
class Personne:
    """Classe définissant une personne caractérisée par :
    - son nom
    - son prénom
    - son âge"""

    def __init__(self, nom : str, prenom : str, age=33):
        self.__nom   = nom        #attribut privé
        self.prenom    = prenom
        self.age   = age

    def __get_name(self): # méthode donnant accès à l'attribut ne pas oublier les underscores devant
        return self.__nom

    def __set_name(self, nom : str): # méthode modifiant l'attribut
        self.__nom = nom

    nom = property(__get_name, __set_name) # l'attribut nom est accessible et modifiable

### Programme principal ###
qui = Personne('Dupont', 'Jean')

# pour l'utilisateur l'attribut nom parait public
print(qui.nom)    # donne le nom
qui.nom = 'Durant'
print(qui.nom)
```

```txt
Dupont
Durant
```

**<H3 STYLE="COLOR:red;">(Hors programme) Activité n° 11 : Encapsulation de l’attribut**</H3>
contrôle de l’accès à l’attribut
```python
class Personne:
    """ Classe représentant une personne """
    def __init__(self, nom : str, prenom : str, age=33):
        self.nom    = nom
        self.prenom = prenom
        self.__age    = age

    def __get_age(self):
        return self.__age

    def __set_age(self, age : int):
        if age > 18:
            self.__age = age

    age = property(__get_age, __set_age)

### Programme principal ###
qui = Personne('Dupont', 'Jean')
print(qui.age)
qui.age = 10      # ne modifie pas l’attribut
print(qui.age)
```

```txt
33
33
```

La **méthode spéciale** ```__getattr__``` permet de définir une méthode d’accès aux attributs plus large que celle que Python propose par défaut. En fait, cette méthode est appelée quand on tape objet.attribut (non pas pour modifier l’attribut mais simplement pour y accéder). Python recherche l’attribut et, s’il ne le trouve pas dans l’objet et si une méthode ```__getattr__``` existe, il va l’appeler en lui passant en paramètre le nom de l’attribut recherché, sous la forme d’une **chaine de caractères**.

```__getattr__``` est utilisé uniquement si l'attribut auquel on tente d'avoir accès n'existe pas dans l'objet.

**<H3 STYLE="COLOR:red;">(Hors programme)Activité n° 12 : méthode spéciale ```__getattr__```**</H3>
```python
class Personne:
    """ Classe représentant une personne """
    def __init__(self, nom : str, prenom : str, age=33):
        self.__nom    = nom
        self.__prenom = prenom
        self.__age    = age
    def __get_age(self):
        return self.__age
    def __set_age(self, age : int):
        if age > 17:
            self.__age = age

    age = property(__get_age, __set_age)

### Programme principal ###
qui = Personne('Dupont', 'Jean')
print(qui.age)
qui.age = 10      # ne modifie pas l’attribut car < 17
print(qui.age)
print(qui.nom)   # lever d’exception car nom est un attribut privé (n’existe pas)
```

Lever d'exception

```python
class Personne:
    """ Classe représentant une personne """
    def __init__(self, nom : str, prenom : str, age=33):
        self.__nom    = nom
        self.__prenom = prenom
        self.__age    = age
    def __getattr__(self, name : str):
        return 'Attribut introuvable'
    def __get_age(self):
        return self.__age
    def __set_age(self, age : int):
        if age > 17:
            self.__age = age

    age = property(__get_age, __set_age)

### Programme principal ###
qui = Personne('Dupont', 'Jean')
print(qui.age)
qui.age = 10      # ne modifie pas l’attribut car < 17
print(qui.age)
print(qui.nom)
print(qui.tartempion)
```

```txt
33
33
Attribut introuvable
Attribut introuvable
```

**<H3 STYLE="COLOR:red;">(Hors programme)Activité n° 13 : Ce qu’il ne faut pas faire !!**</H3>
```python
class Personne:
    """ Classe représentant une personne """
    def __init__(self, nom : str, prenom : str, age=33):
        self.__nom    = nom
        self.__prenom = prenom
        self.__age    = age
    def __get_age(self):
        return self.__age
    def __set_age(self, age : int):
        if age > 17:
            self.__age = age

    age = property(__get_age, __set_age)

### Programme principal ###
qui = Personne('Dupont', 'Jean')
print(qui.age)
qui.__name, qui.__age = 'Albert', 18      # à proscrire !! c'est INTERDIT en terminale il faut utiliser une méthode pour cela !!
print(qui.__name, qui.__age)
print(qui.age)    # résultat très étonnant...
```

```txt
33
Albert 18
33
```

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc88030965"></a>**3.2. (Hors programme) Héritage**</H3>

L’héritage est l’un des fondements de la programmation objet qui permet une **réutilisation** d’éléments déjà programmés dans un cadre général. L’héritage est une fonctionnalité objet qui permet de déclarer que telle classe sera elle-même modelée sur une autre classe, qu’on appelle la classe parente, ou la classe **mère**. 

Si une classe B hérite de la classe A, les objets créés sur le modèle de la classe B auront accès aux méthodes et attributs de la classe A. On dit que la classe B est la **fille** de la classe A qui est le **parent** (ou la superclasse).

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030966"></a>**3.2.1. (Hors programme) Héritage simple**</H4>

**<H3 STYLE="COLOR:red;">(Hors programme) Activité n° 14  Héritage simple:**</H3> 
On définit une première classe Personne et une seconde classe AgentSpecial qui hérite de Personne.
```python
class Personne:
    """Classe représentant une personne"""
    def __init__(self, nom : str, prenom : str):
        self.__nom    = nom
        self.__prenom = prenom
    def get_identity(self):
        return self.__prenom + " " + self.__nom

class AgentSpecial(Personne):
    """Classe définissant un agent spécial.
    Elle hérite de la classe Personne"""
    def __init__(self, nom : str, prenom : str, matricule : str):
        """Un agent se définit par son nom et son matricule"""
        Personne.__init__(self, nom, prenom)   # appel explicite au constructeur
        self.__matricule = matricule
    def get_matricule(self):
        return self.__matricule

### Programme principal ###
qui = AgentSpecial('Dupont', 'Jean', '007')
print("{0} : {1}".format(qui.get_identity(), qui.get_matricule()))
```

```txt 
Jean Dupont : 007
```

On n’a pas besoin de redéfinir les attribut nom et prenom de la classe AgentSpecial puisqu’elle hérite de Personne.

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030967"></a>**3.2.2. (Hors programme) Héritage multiple**</H4>

Python inclut un mécanisme permettant l’héritage multiple. L’idée est en substance très simple : au lieu d’hériter d’une seule classe, on peut hériter de plusieurs. Assez souvent, on utilisera l’héritage multiple pour des classes qui ont besoin de certaines fonctionnalités définies dans une classe mère.

On précise plusieurs classes mères séparée par des virgules :
```txt
class SuperHero(Personne, Pouvoirs):
```

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030968"></a>**3.2.3. (Hors programme) Ordre de recherche de méthodes**</H4>

La recherche des méthodes se fait dans l’ordre de la définition de la classe. Dans l’exemple ci-dessus, si on appelle une méthode d’un objet issu de SuperHero, on va d’abord chercher dans la classe SuperHero. Si la méthode n’est pas trouvée, on cherche dans toutes les classes mère de la classe Personne. Si on ne trouve pas la méthode, on la recherche dans Pouvoirs et ses classes mères successivement.

L’ordre de définition des classes mères est important.

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc88030969"></a>**3.3. (Hors programme) Polymorphisme**</H3>

Un objet va hériter des attributs et méthodes de ces ancêtres. Mais un objet garde toujours la capacité de pouvoir redéfinir une méthode afin de la réécrire ou de la compléter.

Le polymorphisme permet à un objet de modifier son comportement propre et celui de ses descendants.

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030970"></a>**3.3.1. (Hors programme) Polymorphisme statique : surcharge de méthodes**</H4>

Lorsqu’on surcharge une méthode, le but n’est pas d’écraser l’ancienne, mais de la compléter de façon à apporter de nouvelles fonctionnalités.

De fait, il n’est pas nécessaire pour un objet de réécrire une méthode ou un constructeur si ceux de son ancêtre suffisent.

**<H3 STYLE="COLOR:red;">(Hors programme) Activité n° 15 surcharge de méthodes :**</H3> 
On ajoute ```get_identity``` aux deux classes.
```python
class Personne:
    """Classe représentant une personne"""
    def __init__(self, nom : str, prenom : str):
        self.__nom    = nom
        self.__prenom = prenom

    def get_identity(self):
        return self.__prenom + " " + self.__nom

class AgentSpecial(Personne):
    """Classe définissant un agent spécial.
    Elle hérite de la classe Personne"""
    def __init__(self, nom : str, prenom : str, matricule : str):
        """Un agent se définit par son nom et son matricule"""
        Personne.__init__(self, nom, prenom)   # appel explicite au constructeur pour nom et prénom
        self.__matricule = matricule            # on ajoute l'attribut matricule

    def get_identity(self):                     # pour accéder au matricule
        return self.__matricule

### Programme principal ###
moi = AgentSpecial('Dupont', 'Jean', '007')
print("identité : {0}".format(moi.get_identity()))

toi = Personne('Durant', 'Jean')
print("identité : {0}".format(toi.get_identity()))
```

```txt
identité : 007
identité : Jean Durant
```

#### <H4 STYLE="COLOR:MAGENTA;"> <a name="_toc88030971"></a>**3.3.2. (Hors programme) Polymorphisme statique : surcharge d’opérateurs**</H4>

La surcharge d’opérateur permet d’avoir une signification spécifique quand ils sont appliqués à des types spécifiques. Surcharger les opérateurs standards permet de tirer parti de l’intuition des utilisateurs de la classe.

Pour surcharger l’addition, la méthode spéciale à redéfinir est \_\_add\_\_. Elle prend en paramètre l’objet que l’on souhaite ajouter. Il existe d’autres méthodes :

- \_\_sub\_\_ : surcharge de l'opérateur –
- \_\_mul\_\_ : surcharge de l'opérateur \*
- \_\_truediv\_\_ : surcharge de l'opérateur /
- \_\_floordiv\_\_ : surcharge de l'opérateur // (division entière)
- \_\_mod\_\_ : surcharge de l'opérateur % (modulo)
- \_\_pow\_\_ : surcharge de l'opérateur \*\* (puissance)

à consulter sur [le site web de Python](https://www.python.org/).

Méthode de comparaison qui prend en paramètre l’objet à comparer à self et renvoie un booléen.

- \_\_eq\_\_ : surcharge l’opérateur ==
- \_\_ne\_\_ : surcharge l’opérateur !=
- \_\_gt\_\_ : surcharge l’opérateur >
- \_\_ge\_\_ : surcharge l’opérateur =>=
- \_\_lt\_\_ : surcharge l’opérateur <
- \_\_le\_\_ : surcharge l’opérateur <=

Exemple de comparaison de durée :
```python
class Duree:
    """Classe contenant des durées sous la forme d'un nombre de minutes
    et de secondes"""
    def __init__(self, duree = 0.0):
        min, sec = str(duree).split('.')
        self.__min, self.__sec = int(min), int(sec)

    def __str__(self):
        return "{0:02}:{1:02}".format(self.__min, self.__sec)

    def __add__(self, duree : float):
        """L'objet à ajouter est un entier, le nombre de secondes"""
        nouvelle_duree = Duree()
        min, sec = str(duree).split('.')
        nouvelle_duree.__min  = self.__min + int(min)
        nouvelle_duree.__sec  = self.__sec + int(sec)
        if nouvelle_duree.__sec >= 60:
            nouvelle_duree.__min += nouvelle_duree.__sec // 60
            nouvelle_duree.__sec  = nouvelle_duree.__sec % 60
        return nouvelle_duree

    def __eq__(self, autre_duree):
        """Test si self et autre_duree sont égales"""
        return self.__sec == autre_duree.__sec and self.__min == autre_duree.__min

    def __gt__(self, autre_duree):
        """Test si self > autre_duree"""
        nb_sec1 = self.__sec + self.__min * 60
        nb_sec2 = autre_duree.__sec + autre_duree.__min * 60
        return nb_sec1 > nb_sec2

d1 = Duree(12.8)
print(d1)
d2 = d1 + .54  # ajoute 54 secondes
print(d2)
print(d1 == d2)
print(d2 > d1)
```

## <H2 STYLE="COLOR:BLUE;"> <a name="_toc88030972"></a>**4. (Hors programme) Décorateurs**</H2>
Les décorateurs sont des fonctions de Python dont le rôle est de **modifier le comportement** par défaut d’autres fonctions ou classes. Une fonction modifiée par un décorateur ne s’exécutera pas elle-même mais appellera le décorateur. C’est au décorateur de décider s’il veut exécuter la fonction et dans quelles conditions.

La syntaxe et la suivante :
```txt
@nom_du_decorateur

def ma_fonction(...)
```
Le décorateur s’exécute

 au moment de la définition et non lors de l’appel. Il prend en paramètre une fonction (celle qu’il modifie) et renvoie une fonction (qui peut être la même).
```txt
def fonction():
   pass
```

Le code précédent a le même comportement que le code suivant:
```txt
def fonction():
   pass

fonction = decorateur(fonction)
```

**<H3 STYLE="COLOR:red;">(Hors programme) Activité n° 16 décorateur debug avec les fonctions :**</H3> 
```python 
def debug(fonction : callable):
    print("appel de la fonction {0}".format(fonction))
    return fonction

@debug
def factoriel(n : int) -> int:
    """ calcul de n! """
    if n < 2:
        return 1
    return n * factoriel(n-1)

print(factoriel(4))
```

```txt
appel de la fonction <function factoriel at 0x000001CF559CD040>
24
```

On peut ainsi poursuivre le débogage et tracer les appels récursifs de la fonction factoriel()

**<H3 STYLE="COLOR:red;">(Hors programme) Activité n° 17 décorateur debug avec les fonctions :**</H3> 
plus en détail
```python
def debug(fonction : callable):
    print("appel de la fonction {0}".format(fonction))

    def pile_appels(n : int):
        print("appel de la fonction", n)
        return fonction(n)
    return pile_appels

@debug
def factoriel(n : int) -> int:
    """ calcul de n! """
    if n < 2:
        return 1
    return n * factoriel(n-1)

print(factoriel(4))
```

```txt
appel de la fonction <function factoriel at 0x00000268913B14C0>
appel de la fonction 4
appel de la fonction 3
appel de la fonction 2
appel de la fonction 1
24
```

Il est important de noter que les décorateurs peuvent s’utiliser avec des méthodes de classes.

**<H3 STYLE="COLOR:red;">(Hors programme) Activité n° 18 décorateur debug avec la POO :**</H3>
Il faut obligatoirement définir la méthode \_\_call\_\_() pour pouvoir rendre cette instance callable.
```python
class Debug:
    def __init__(self, fonction):
        self.call = 0
        self.fonction = fonction
    def __call__(self, *args, **kwargs):
        self.call +=1
        print("appel de la fonction {0}".format(self.call))
        return self.fonction(*args, **kwargs)

@Debug
def factoriel(n : int) -> int:
    """ calcul de n! """
    if n < 2:
        return 1
    return n * factoriel(n-1)

print(factoriel(4))
```

```txt
appel de la fonction 1
appel de la fonction 2
appel de la fonction 3
appel de la fonction 4
24
```





## <H2 STYLE="COLOR:BLUE;"> <a name="_toc88030973"></a>**5. Exercices**</H2>
**<H3 STYLE="COLOR:red;">Exercice n°1 :**</H3> On considère une classe **Personnage** représentant un personnage de Jeu. Le plateau de jeu est représenté par un repère **orthonormé à trois axes**. La position du joueur dans le plateau est repérée par **ses attributs x, y, z**.

1. Écrire un constructeur initialisant les mesures.

2. Écrire les méthodes **avance, droite** et **saute** permettant respectivement de faire avancer, aller à droite et sauter le personnage, c’est-à-dire d’augmenter de 1 respectivement x, y et z.

3. Implémenter une autre méthode **coord** renvoyant les coordonnées sous forme d’un triplet.

4. Essayer avec : Laura = Personnage(0, 0, 0)

**<H3 STYLE="COLOR:red;">Exercice n°2 :**</H3> Voici un programme en Python :
```python
import random 
class Piece : 
    def alea(self) : 
        return random.randint(0,1) 
    def moyenne(self, n): 
        tirage = [] 
        for i in range(n): 
            tirage.append(self.alea()) 
        return sum(tirage) / n 
p = Piece() 
print(p.moyenne(100)) 
```

Expliquer en détail ce qu’il permet d’afficher.

**<H3 STYLE="COLOR:red;">Exercice n°3 :**</H3> On considère une classe **Carre** admettant la mesure des côtés d’un carré en attribut.

1. Écrire un constructeur initialisant les mesures.

2. Écrire les méthodes :
   - **perimetre**, permettant de retourner le périmètre du carré.
   - **aire** permettant de retourner son aire.

3. Créer des exemples.

**<H3 STYLE="COLOR:red;">Exercice n°4 :**</H3> Définir une classe **Fraction** pour représenter un nombre rationnel.

Cette classe possède deux **attributs num** et **denom**, qui sont des entiers et désignent respectivement le numérateur et le dénominateur.

De plus, on demande que le dénominateur soit particulièrement un entier strictement positif.

4 Écrire un constructeur de cette classe.

   Le constructeur doit lever une **ValueError** si le dénominateur fourni n’est pas strictement positif.

   Pour cela, on utilise : raise : <https://www.w3schools.com/python/ref_keyword_raise.asp#:~:text=The%20raise%20keyword%20is%20used,to%20print%20to%20the%20user>.

![](Aspose.Words.427b5c12-e7cd-426a-b87c-f85884ba8965.014.png){: .center }

5 Ajouter une méthode **\_\_str\_\_** qui renvoie une chaîne de caractère de la forme "12 / 13", ou simplement de la forme "12" lorsque le dénominateur vaut 1. ( \_\_str\_\_(self) est une méthode de Python : renvoie une chaîne de caractères)

6 Ajouter des méthodes **\_\_eq\_\_** et **\_\_lt\_\_** qui reçoivent une deuxième fraction en argument et renvoient True si la première fraction représente respectivement un nombre égal ou un nombre strictement inférieur à la fraction. 

   ( \_\_lt\_\_(self, other) est une méthode de Python : Pour self = t, elle renvoie True si t est strictement plus petit que other ) ( \_\_eq\_\_(self, other) est une méthode de Python : Pour self = t, elle renvoie True si t est égal à other )

7 Ajouter des méthodes **\_\_add\_\_** et **\_\_mul\_\_** qui reçoivent une deuxième fraction en argument et renvoient une nouvelle fraction représentant respectivement la somme et le produit des deux fractions.

8 Tester ces opérations.

9 **Question bonus** : S’assurer que les fractions sont toujours sous forme réduite.

**<H3 STYLE="COLOR:red;">Exercice n°5 : La classe « Complexe »**</H3>

En mathématiques, dans un plan rapporté à un repère orthonormé ( O;u,v), tout point M de coordonnées (x; y) peut être représenté par ce que l'on nomme un nombre complexe, qui peut s'écrire sous la forme:

*z=x+iy*.

On dit que x est la partie réelle de z et y, sa partie imaginaire.

En posant z = x + iy et z' = x' + iy, on définit alors les opérations suivantes :

- z + z' = (x + x') + i(y + y')
- z - z' = (x - x') + i(y - y')
- z × z' = (xx' - yy') + i(xy' + x'y)

De plus, on dit que z = z' si x = x' et y = y'. Écrire en Python une classe complexe :

- qui définit un nombre complexe (le constructeur devra initialiser un tuple de deux nombres : la partie réelle et la partie imaginaire);
- ayant une méthode permettant d'afficher le nombre complexe sous forme d'un tuple de deux éléments;
- permettant d'ajouter, soustraire, multiplier et comparer (en termes d'égalité) deux nombres complexes;
- permettant de donner la distance de l'origine du repère au point représenté par le nombre complexe (on appelle cette distance le module, qui est égal à $\sqrt{x^2+y^2}$).

**Aide :** Les méthodes à mettre sont des méthodes spéciales qui existent déjà (dans l'ordre de l'exercice) :

- \_\_add\_\_
- \_\_sub\_\_
- \_\_mul\_\_
- \_\_eq\_\_

De ce fait on aura :
```python
def __add__(self, other):
    return Complexe(self.x + other.x, self.y + other.y)
```

où other représente l’autre objet.

Tester cette classe avec les nombres : *z=3 + 5i* et *z’=7 + i*.

Ce qui donne si on appelle afficher\_tuple() la méthode permettant d’afficher le tuple :
```txt
>>> z = Complexe(-3,5)
>>> zprime = Complexe(7,1)
>>> z.afficher_tuple()
Out[3]: (-3, 5)
>>> (z+zprime).afficher_tuple()
Out[4]: (4, 6)
```
Etc…

**<H3 STYLE="COLOR:red;">Exercice n°6 : La classe « Temps »**</H3>

En Python, écrire une classe Temps qui permet de définir un horaire au format hh : mm : ss et qui admet les méthodes suivantes :

- affiche, qui affiche l'horaire au format « 12 h 37 min 45 s »;
- \_\_add\_\_ , qui ajoute deux horaires de la classe Temps;
- \_\_sub\_\_ , qui calcule la différence entre deux horaires de la classe Temps.

**<H3 STYLE="COLOR:red;">Exercice n°7 : La classe « Mot» et « Phrase »**</H3>

On considère la classe Mot définie ainsi :
```python
from random import shuffle

class Mot:
    def __init__(self, m):
        self.m = m
    def doReverse(self):
        self.m = self.m[::-1]    
    def doShuffle(self):
        L = list(self.m)
        shuffle(L)
        self.m = ''.join(L)   
    def value(self):
        return self.m
```

1 Indiquer ce que fait la fonction fctA() définie par :
```python
def fctA():
    m=Mot("Socrate")
    m.doReverse()
    print(m.value())
```

2 Indiquer ce que fait la fonction fctB() définie par :
```python
def fctB():
    m=Mot("Socrate")
    m.doShuffle()
    print(m.value())
```

On souhaite écrire une classe Phrase. Toutes les questions suivantes porteront sur cette classe.

3 Écrire un constructeur qui définit une liste self.mots remplie de tous les mots de la phrase passée en paramètre, chacun des mots devant être de classe Mot.

4 Écrire deux méthodes doReverse et value telles que la fonction fctC() suivante :
```python
def fctC():
    p = Phrase("Tous les hommes sont mortels")
    p.doReverse()
    print(p.value())
```

Affiche : « mortels sont hommes les Tous ».

5 Écrire une méthode doShuffle afin que la fonction suivante :
```python
def fctD():
    p = Phrase('Tous les hommes sont mortels')
    p.doShuffle()
    print(p.value())
```

Affiche les mots de la phrase « Tous les hommes sont mortels » dans un ordre aléatoire.

6 On définit la méthode motAt de la manière suivante:
```python
def motAt(self, pos):
    return self.mots[pos]
```

Que fait la fonction fctE() suivante?
```python
def f

ctE():
    p = Phrase('Tous les hommes sont mortels')
    m = p.motAt(3)
    m.doReverse()
    print(p.value())
```

7 On définit la méthode insert de la manière suivante :
```python
def insert(self, pos, chaine):
    self.mots.insert(pos, Mot(chaine))
```
Que fait la fonction fctF() suivante?
```python
def fctF():
    p = Phrase('Tous les hommes sont mortels')
    p.insert(3,"ne")
    p.insert(5, "pas")
    print(p.value())
```

8 On définit la méthode remove de la manière suivante :
```python
def remove(self, pos):
    self.mots.pop(pos)
```

Que fait la fonction fctG() suivante?
```python
def fctG():
    p = Phrase('Tous les hommes sont mortels')
    m = p.motAt(4)
    m.doShuffle()
    p.remove(2)
    p.insert(2, m.value())
    print(p.value())
```

**<H3 STYLE="COLOR:red;">Exercice n°8 : La classe Intervalle**</H3>

Définir une classe Intervalle représentant des intervalles de nombres. Cette classe possède deux attributs a et b représentant respectivement l’extrémité inférieure et l'extrémité supérieure de l’intervalle.

Les deux extrémités sont considérées comme incluses dans l'intervalle.

Tout intervalle avec b < a représente l'intervalle vide.

- Écrire le constructeur de la classe Intervalle et une méthode est\_vide renvoyant True si l’objet représente l’intervalle vide et False sinon.
- Ajouter des méthodes \_\_len\_\_ renvoyant la longueur de l'intervalle (l'intervalle vide à une longueur 0) et \_\_contains\_\_ testant l’appartenance à l'intervalle.
- Ajouter une méthode \_\_eq\_\_ permettant de tester l'égalité de deux intervalles avec == et une méthode \_\_le\_\_  permettant de tester l'inclusion d’un intervalle dans un autre avec <=.

Attention : toutes les représentations de l'intervalle vide doivent être considérées égales, et incluses dans tout intervalle.

- Ajouter des méthodes intersection et union calculant respectivement l'intersection de deux intervalles et le plus petit intervalle contenant l’union de deux intervalles (l'intersection est bien toujours un intervalle, alors que l’union ne l’est pas forcément). Ces deux fonctions doivent renvoyer un nouvel intervalle sans modifier leurs paramètres.

**<H3 STYLE="COLOR:red;">Exercice n°9 : La classe Date**</H3>

Définir une classe Date pour représenter une date, avec trois attributs jour, mois et annee.

Écrire son constructeur.

- Ajouter une méthode \_\_str\_\_ qui renvoie une chaîne de caractères de la forme "8 mai 1945". On pourra se servir d’un attribut de classe qui est un tableau donnant les noms des douze mois de l’année.

Tester en construisant des objets de la classe Date puis en les affichant avec print.

- Ajouter une méthode \_\_lt\_\_ qui permet de déterminer si une date d1 est antérieure à une date d2 en écrivant d1 < d2. La tester.

**<H3 STYLE="COLOR:red;">Exercice n°10 : La classe Tableau**</H3>

Dans certains langages de programmation, comme Pascal ou Ada, les tableaux ne sont pas nécessairement indexés à partir de 0. C’est le programmeur qui choisit sa plage d’indices.

Par exemple, on peut déclarer un tableau dont les indices vont de -10 à 9 si on le souhaite.

Dans cet exercice, on se propose de construire une classe Tableau pour réaliser de tels tableaux.

Un objet de cette classe aura deux attributs, un attribut premier qui est la valeur de premier indice et un attribut contenu qui est un tableau Python contenant les éléments. Ce dernier est un vrai tableau Python, indexé à partir de 0.

- Écrire un constructeur \_\_init\_\_(self, tmin, tmax, v) où tmin est le premier indice, tmax le dernier indice et v la valeur utilisée pour initialiser toutes les cases du tableau.

Ainsi, on peut écrire   t = Tableau(-10, 9, 42) 

Pour construire un tableau de vingt cases, indexées de -10 à 9 et toutes initialisées avec la valeur 42.

- Écrire une méthode \_\_len\_\_(self) qui renvoie la taille du tableau.
- Écrire une méthode \_\_getitem\_\_(self, i) qui renvoie l'élément du tableau self d'indice i. De même, écrire une méthode \_\_setitem\_\_(self, i, v) qui modifie l’élément du tableau self d'indice i pour lui donner la valeur v.

Ces deux méthodes doivent vérifier que l’indice i est bien valide et, dans le cas contraire, lever l'exception IndexError avec la valeur de i en argument (c’est-à-dire raise IndexError(i)).

- Enfin, écrire une méthode \_\_str\_\_(self) qui renvoie une chaîne de caractères décrivant le contenu du tableau.

