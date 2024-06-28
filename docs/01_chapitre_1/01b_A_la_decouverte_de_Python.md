---
author: ELP
title: 01b A la découverte de Python
---


**Table des matières** 

1. [**Un langage de programmation ? Qu’est ce que c’est ?**](#_page0_x40.00_y432.92)

2. [**Quelques langages de programmation courants**](#_page2_x40.00_y36.92) 

3. [**Pseudo-code**](#_page2_x40.00_y367.92)
4. [**Python**](#_page2_x40.00_y464.92)

5. [**Exercices**](#_page10_x40.00_y36.92)

## **1. Un<a name="_page0_x40.00_y432.92"></a> langage de programmation ? Qu’est ce que c’est ?** 

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.001.png)

Il y a plusieurs sortes de langages de programmation, mais le seul directement  utilisable  par  le  processeur  est  le  langage  machine  constitué  de  0  et  de  1.  Aujourd’hui presque plus personne ne programme en langage machine.  

On peut les classer en :  

- Le **langage machine** : binaire  
- Le **langage assembleur** : le langage machine s'exécute directement par  un ordinateur après conversion en code machine. 
- Le **langage de haut niveau**   
- **Langage compilé** : C, C++, Pascal et OCaml.  
- **Langage interprété :** Java (+ JavaScool), Ruby et Python ;  
### **1.1. Les<a name="_page1_x40.00_y36.92"></a> langages compilés**  
![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.002.jpeg)

Dans ces langages, le code source (celui que vous  écrivez) est tout d'abord **compilé**, par un logiciel le  **compilateur**, en un code binaire qui est très facile à  lire pour un ordinateur.   

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.003.png)

### **1.2. Les<a name="_page1_x40.00_y402.92"></a> langages interprétés**  
![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.004.png)

Dans ces langages, le code source est **interprété**,  par un logiciel l’**interpréteur**.   

### **1.3. Principales<a name="_page1_x40.00_y504.92"></a> différences**  

Dans un langage interprété, **le même code source pourra marcher directement sur tout ordinateur**. Avec un langage compilé, il faudra (en général) **tout recompiler à chaque fois** ce qui pose parfois des soucis. 

Par contre, dans un langage **compilé**, le programme est directement exécuté sur l'ordinateur, donc il sera en général **plus rapide** que le même programme dans un langage interprété. 

### **1.4. Un<a name="_page1_x40.00_y593.92"></a> langage particulier : Python** 

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.005.png)

C’est une t**echnique mixte** : l’interprétation du **bytecode compilé**. C’est un bon compromis entre la facilité de développement et la rapidité d’exécution ; 

Le **bytecode** (forme intermédiaire) est **portable** sur tout ordinateur muni de la machine virtuelle 

Pour exécuter un programme, Python charge le fichier **source .py** en mémoire vive, en fait **l’analyse,** produit le **bytecode** et enfin **l’exécute**. Afin de ne pas refaire inutilement toute la phase d’analyse et de production, Python **sauvegarde le bytecode** produit (dans un fichier .pyo ou .pyc) et recharge simplement le fichier bytecode s’il est plus récent que le fichier source dont il est issu.  

## **2. Quelques<a name="_page2_x40.00_y36.92"></a> langages de programmation courants** 
### **2.1. Historique<a name="_page2_x40.00_y58.92"></a>** 

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.006.jpeg)

### **2.2. «<a name="_page2_x40.00_y316.92"></a> Hello world ! »** 

C'est dans un mémorandum interne de Brian Kernighan, Programming in C : A tutorial, écrit en 1974 dans les laboratoires Bell, que l'on trouve la première version d'un mini-programme affichant à l'écran « Hello World! ».  

## **3. Pseudo-code<a name="_page2_x40.00_y367.92"></a>** 

En programmation, le pseudo-code est une façon de décrire un algorithme en respectant certaines conventions, mais sans référence à un langage de programmation en particulier. L'écriture en pseudo-code permet de développer une démarche structurée. 

Il n'existe **pas de convention universelle** pour le pseudo-code. Afin de bien nous comprendre dans la suite de ce cours, nous adopterons celle décrite ci-dessous. 

## **4. Python<a name="_page2_x40.00_y464.92"></a>** 
### **4.1. Pourquoi<a name="_page2_x40.00_y486.92"></a> apprendre le langage Python ?** 

Python est à la fois simple et puissant, il vous permet d'écrire **des scripts très simples**, mais grâce à ses nombreuses bibliothèques, vous pouvez travailler sur des **projets plus ambitieux.** 



### **4.2. Qu’est-ce<a name="_page2_x40.00_y550.92"></a> que c’est ?** 

En 1989, le hollandais **Guido van Rossum** commence le développement du langage de programmation Python. Python est un langage **multi plateforme**. 

Le langage Python est gratuit, sous **licence libre**. 

### **4.3. Les<a name="_page2_x40.00_y614.92"></a> consignes** 
- Dans la suite du cours, ouvrir l’interpréteur Python  
- Les commandes à faire dans l’interpréteur, aussi appelée console python, seront dans le style de rectangle suivant et commenceront par un prompt >>> 
- Taper chacune des commandes présentées et vérifier son résultat. 
- Ouvrir un **éditeur de Python**  
- Compléter votre script resume\_ch0X.py avec les nouvelles commandes apprises : c’est l’équivalent d’une fiche de cours, il faut donc en prendre soin 
- Pour chaque série d’exercice (à la fin des cours) : réaliser chaque exercice dans un fichier nommé : exo\_ch0X\_01.py, exo\_ch0X\_02.py, exo\_ch0X\_03.py,…… 

### **4.4. Premiers<a name="_page3_x40.00_y36.92"></a> pas avec l’interpréteur de commandes Python** 

**Activité n°1.:Les calculs de bases :** Tester les calculs suivant :
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
7 + 3 * 4
(7 + 3 ) * 4
10 / 3
```

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

 
 Les espaces sont optionnels. 
 Les règles de priorité en maths sont-elles respectées ? …………………….
 
**Activité n°2.:** **Addition de float :** Tester les calculs suivant :

```python
3.11 + 2.08
```

???+ question "Faire ce qui est proposé"

    {{ terminal() }}
    
Que remarquez-vous ?............. 

**Activité n°3.:** **La division entière et le modulo :** Tester les calculs :
**ATTENTION : faire entrer à chaque ligne du scripts suivant**

```python
10 // 5
10 // 4
10 % 4
10 % 3
```

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

La division entière permet de déterminer la valeur tronquée de la division et le modulo permet de déterminer la valeur du reste. 

On souhaite effectuer la division de 3395  par 99.  

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.019.jpeg)

On s’est arrêté car 29 est plus petit que 99 et qu’on ne souhaitait pas aller plus loin et se retrouver avec un nombre à virgule. On a effectué une division dite division entière. On en déduit donc que 3395 = 99 \* 34 + 29

**Activité n°4.:** **L’exponentiation :** Tester les calculs :
**ATTENTION : faire entrer à chaque ligne du scripts suivant**

```python
3 ** 2
2 ** 3
```

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

### **4.5. Variables,<a name="_page4_x40.00_y133.92"></a> types** 

Une variable est un espace mémoire dans lequel il est possible de stocker une valeur (une donnée). On va affecter des valeurs à des variables.  

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.024.png)**Attention le symbole de l’affectation est =** 

#### **4.5.1. Noms<a name="_page4_x40.00_y194.92"></a> de variables**

Le nom d’une variable s'écrit avec des lettres (**non accentuées**), des chiffres ou bien l’underscore \_ Le nom d’une variable ne doit pas commencer par un chiffre. 

Exemple : age, mon\_age, temperature1  A éviter : Age, AGE, monAge, Temperature1 

#### **4.5.2. Le<a name="_page4_x40.00_y249.92"></a> type int (integer)** 



**Activité n°5.:** Tester les calculs : 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
age = 17
```
La fonction print affiche la valeur de la variable :
```python
print(age)
```

La fonction type() retourne le type de la variable : 
```python
print(type(age))
```

???+ question "Faire ce qui est proposé"

    {{ terminal() }}


**Activité n°6.:** L’incrémentation ou la décrémentation : Tester les calculs suivant dans la console
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
# ceci est un commentaire 
a = 10 
a = a + 1 # on incrémente la valeur de a. On peut l’écrire aussi a +=1 
print(a) 
a = a – 3 # on décrémente la valeur de a. On peut l’écrire aussi a -=3  
print(a) 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

#### **4.5.3. Le<a name="_page4_x40.00_y602.92"></a> type float (nombres en virgule flottante)**
**Activité n°7.:** Tester les calculs suivant dans la console
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
b = 17.0  # le séparateur décimal est un point (et non une virgule) 
print(b) 
print(type(b)) 
```


```python
c = 14.0 / 3.0 
print(c) 
```


```python
c = 14.0 // 3.0  # division entière print(c)
```


![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.040.png)Attention : avec des nombres entiers, l’opérateur / renvoie généralement un flottant : 

```python
c = 14 / 3 
print(c)
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

#### **4.5.4. Le<a name="_page5_x40.00_y196.92"></a> type str (string : chaîne de caractères)**


**Activité n°8.:**  Tester les calculs suivant dans la console
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
nom = 'Dupont'    # entre apostrophes 
print(nom) 
print(type(nom)) 
prenom = "Pierre"   # on peut aussi utiliser les guillemets 
print(prenom) 
print(nom, prenom)   # ne pas oublier la virgule 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°9.:** La concaténation désigne la mise bout à bout de plusieurs chaînes de caractères (de type string). La concaténation utilise l’opérateur + 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
nom = 'Dupont' 
prenom = "Pierre"
chaine = nom + prenom  # concaténation de deux chaînes de caractères 
print(chaine) 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°10.:** La fonction len() retourne la longueur (length) de la chaîne de caractères : 

```python
len("abc")  
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

En Python, **un slice** permet le découpage de structures de données séquentielles (chaînes de caractères ou les listes). Les slices sont des expressions du langage Python qui permettent en une ligne de code d'extraire des éléments d'une liste ou d'une chaîne selon leurs indices **[début:fin:pas].** 

NB : si pas < 0, la liste est parcourue dans le sens inverse. 

![](Aimg.png)

**Activité n°11.:** 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
string = "ABCDEFGHIJKLMNOPQRSTUVWXYZ" 
string[0]  # Renvoie l’élément à l’indice 0 
string[2]  # Renvoie l’élément à l’indice 2 
string[:3]   # Renvoie les trois premiers termes 
string[:13:2]  # Renvoie les 13 premiers termes, mais 1 sur 2 'ACEGIKM' 
string[::-1]  # Renvoie le renversement la chaine de caractère 'ZYXWVUTSRQPONMLKJIHGFEDCBA' 
string[13::-2]  # Renvoie du 13e à la fin, mais 1 sur 2 et à l’envers 'NLJHFDB' 
string[:13:-2]  # Renvoie du début au 13e, mais 1 sur 2 et à l’envers 'ZXVTRP' 
string[-1::]  # Renvoie du -1 à la fin donc le -1 
string[-4:-2:]  # Renvoie du -4 au -2 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°12.:** ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.051.png)Attention aux apostrophes et guillemets dans les chaînes de caractères ! 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
chaine = 'Aujourd'hui'
chaine  = 'Aujourd\'hui'   # séquence d'échappement \' 
print(chaine) 
chaine  = "Aujourd'hui"
print(chaine) 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°13.:** La séquence d'échappement \n représente un saut ligne : 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**
```python
chaine = 'Premiere ligne\nDeuxieme ligne' 
print(chaine)
``` 

???+ question "Faire ce qui est proposé"

    {{ terminal() }}


**Activité n°14.:** On ne peut pas mélanger les serviettes et les torchons (ici type str et type int) : 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
chaine = 'a' 
chaine = chaine + 2
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

#### **4.5.5. Le<a name="_page6_x40.00_y680.92"></a> type list (liste)**

Une liste est une structure de données. Le premier élément d’une liste possède l’indice (l’index) 0. Dans une liste, on peut avoir des éléments de plusieurs types. 

**Activité n°15.:**  
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
liste = [5,7,8]   # Crée la liste [5,7,8] 
liste[0]    # Affiche l'élément numéro 0  
infoperso = ['Pierre', 'Dupont', 17, 1.75, 72.5]
print('Prénom : ', infoperso[0])   # premier élément (indice 0) 
print('Age : ', infoperso[2])    # le troisième élément a l'indice 2
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°16.:** Quelques fonctions utiles len() 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
liste = [5,7,8]   # Crée la liste [5,7,8]
len(liste)   # Affiche le nombre d'éléments dans liste 3 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°17.:** Quelques méthodes utiles : append() , pop()
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
liste = [5, 8, 11] 
liste.append(3)     #Ajoute l'élément 3 en fin de liste 
liste 
liste.pop(1)       #Retire l’élément à l’indice 1 
liste 
```

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°18.:** La méthode lower()retourne la chaîne de caractères en casse minuscule (upper() fait l’inverse): 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
chaine = "BONJOUR"  # ou bien : chaine = str("BONJOUR") 
chaine2 = chaine.lower()   # on applique la méthode lower() à l'objet chaine 
print(chaine2) 
print(chaine) 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}


**Activité n°19.:** Les opérations sur les listes 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
x = [ 1 , 2 , 3 , 4] 
y = [ 5 , 6 , 7 , 8] 
x + y 
x = [ 0 , 1] 
[ 0 ]*10 
```

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°20.:** La fonction split() permet de créer une liste en indiquant le séparateur (par exemple l’espace pour obtenir une liste de mot) : 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**
```python
texte = "Il est important de construire" 
a = texte.split(' ') 
a 
```

Cette méthode est communément appelée tuple unpacking 

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°21.:** La fonction ' '.join(a) fait l’inverse, elle prend une liste et renvoie un teste, entre guillemets on indique le séparateur si on ne met rien, tout sera attaché. 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
texte = "Il est important de construire" 
liste1 = ' '.join(a) 
liste1 
liste2 = '.'.join(a) 
liste2
```

C’est la méthode inverse du tuple unpacking 

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

#### **4.5.6. Le<a name="_page8_x40.00_y323.92"></a> type bool (booléen)** 



**Activité n°22.:** Deux valeurs sont possibles : True et False 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
choix = True 
print(type(choix)) 
```

![](Aimg2.png)
 
???+ question "Faire ce qui est proposé"

    {{ terminal() }}


**Activité n°23.:**  
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
b = 10 
print(b > 8) 
print(b == 5) 
print(b != 10) 
print(0 <= b <= 20) 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°24.:** Les opérateurs logiques : and, or, not
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
note = 13.0 
print(note >= 12.0 and note < 14.0 ) 
```

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

**Activité n°25.:** L’opérateur in s’utilise avec des chaînes (type str) ou des listes (type list) : 
**ATTENTION : faire entrer à chaque ligne du scripts suivants**

```python
chaine = 'Bonsoir' 
print('soir' in chaine) 
maliste = [4, 8, 15] 
print(9 in maliste) 
```
???+ question "Faire ce qui est proposé"

    {{ terminal() }}

## **5. Exercices<a name="_page10_x40.00_y36.92"></a>** 

**Exercice n°1**  ☆ Afficher la taille en octets et en bits d’un fichier de 536 ko. On donne : 1 ko (1 kilooctet) = 1000 octets !!! 1 octet = 1 byte = 8 bits 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**Exercice n°2**  ★ Le numéro de sécurité sociale est constitué de 13 chiffres auquel s’ajoute la clé de contrôle (2 chiffres). 
Exemple : le numéro entier de sécurité sociale est : 1 89 11 26 108 268 91; il se compose de 1891126108268 et de 91 qui est la clé de contrôle

La clé de contrôle située à la fin du numéro est calculée par la formule : 97 - (numéro de sécurité sociale modulo 97) Retrouver la clé de contrôle de votre numéro de sécurité sociale. Quel est l’intérêt de la clé de contrôle ? 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**Exercice n°3**  ★ Afficher la valeur numérique de √(4,63 - 15/16) Comparer avec votre calculette. 
Aide : vous aurez besoin de la fonction racine carrée de python. Pour cela il faut l'importer en commandant par la ligne suivante:
```python
from math import sqrt
``` 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**Exercice n°4**  ★ A partir des deux variables prenom et nom, afficher les initiales (par exemple LM pour Léa Martin). 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**Exercice n°5** ★** Quels résultats donnent les instructions suivantes ?  

len("C'est facile de compter") 

len('123' \* 20) 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**Exercice n°6** ☆ Supposons que je veuille imprimer les quatre lignes suivantes :  

```txt
Hello World 
Aujourd'hui 
C'est "Dommage!" 
Hum \Oh/ 
```

Quel code est valide pour afficher le message ci-dessus **sans les tester auparavant** puis vérifier à l’aide d’une console python ? 

- code 1 
```python
print('Hello World') 
print('Aujourd'hui') 
print('C'est "Dommage!"') 
print('Hum \Oh/') 
```
- code 2 
```python
print("Hello World") 
print("Aujourd'hui") 
print("C'est "Dommage!"") 
print("Hum \Oh/") 
```
- code 3 
```python
print("Hello World") 
print("Aujourd'hui") 
print("C'est \"Dommage!\"") 
print("Hum \Oh/") 
```
- code 4 
```python
print("Hello World") 
print("Aujourd'hui") 
print("C'est \"Dommage!\"") 
print("Hum \\Oh\/") 
```
???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**Exercice n°7**  ★☆ **PRÉPAREZ UNE MOUSSE AU CHOCOLAT !**  

La recette de la mousse au chocolat sur le site marmiton.org est la suivante : Ingrédients (pour 4 personnes) : 

3 oeufs 

100 g chocolat (noir ou au lait) 

1 sachet de sucre vanillé 

QUIZ SUR LA MOUSSE AU CHOCOLAT 

Pouvez-pour me dire, à une unité près, la quantité de chaque ingrédient que je dois avoir pour faire ma recette pour 7 personnes, en arrondissant les valeurs calculées à l’unité près (par exemple 3.4 est arrondi à 3 et 3.5 à 4) ? 

*Note :  La fonction prédéfinie round() peut vous aider. Pour comprendre comment, tapez dans une console help(round) (Et si l’anglais n’est pas votre fort, n’oubliez pas que google traduction ou un autre traducteur automatique est votre ami).* 


Pour faire de la mousse pour 7 personnes, combien d’oeufs vous faut-il (arrondis à l’unité) ? Combien de grammes de chocolat vous faut-il (arrondis à l’unité) ? Combien de sachets de sucres vanillés vous faut-il (arrondis à l’unité) ? Exemple : 

```python
Recette de mousse au chocolat pour 7 personnes 
Le nombre d'oeufs pour 7 personnes est : … 
La quantité de chocolat pour 7 personnes est : … 
Le nombre de sachet de vanille pour 7 personnes est :… 
```
???+ question "Faire ce qui est proposé"

    {{ IDE() }}

Généraliser la recette pour un nombre déterminer par l’utilisateur. Par exemple : 

```python
Quel est le nombre de personne ?>? (l’utilisateur entre la valeur 10) 
Recette de mousse au chocolat pour  10  personnes 
Le nombre d'oeufs pour  10  personnes est : 13 
La quantité de chocolat pour  10  personnes est : 438  g 
Le nombre de sachet de vanille pour  10  personnes est : 4 
```
???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**Remarque** : Vous aurez besoin de la fonction input() déjà vu en seconde
```python
a = int(input('quel est votre âge?')) # entrer votre âge
print(a)
```
???+ question "Faire ce qui est proposé"

    {{ IDE() }}

**Exercice n°8**  ★☆ L’identifiant d’accès au réseau du lycée est construit de la manière suivante : initiale du prénom puis les 8 premiers caractères du nom (le tout en minuscule). 

Alexandre Lecouturier → alecoutur A partir des deux variables prenom et nom, construire l’identifiant. 

???+ question "Faire ce qui est proposé"

    {{ IDE() }}
    
QCM :[ http://fabrice.sincere.free.fr/qcm/qcm.php?nom=qcm_python3x_1 ](http://fabrice.sincere.free.fr/qcm/qcm.php?nom=qcm_python3x_1)

