---
author: ELP
title: 01c A la découverte de Python
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
- Compléter votre script resume\_ch02.py avec les nouvelles commandes apprises : c’est l’équivalent d’une fiche de cours, il faut donc en prendre soin 
- Pour chaque série d’exercice (à la fin des cours) : réaliser chaque exercice dans un fichier nommé : exo\_ch02\_01.py, exo\_ch02\_02.py, exo\_ch02\_03.py,…… 

### **4.4. Premiers<a name="_page3_x40.00_y36.92"></a> pas avec l’interpréteur de commandes Python** 

**Activité n°1.:Les calculs de bases :** Tester les calculs suivant dans la console

\>>> 7 + 3 * 4 
\>>> (7 + 3 ) * 4 
\>>> 10 / 3

???+ question "Lancer la console et tester"

    {{ IDE('scripts/activite') }}

 
 Les espaces sont optionnels. 
 Les règles de priorité en maths sont-elles respectées ? …………………….
 
**Activité n°2.:** **Addition de float :** Tester les calculs suivant dans la console

\>>> 3.11 + 2.08  

???+ question "Lancer la console et tester"

    {{ IDE('scripts/activite') }}
    
Que remarquez-vous ?............. 

**Activité n°3.:** **La division entière et le modulo :** Tester les calculs suivant dans la console

\>>> 10 // 5  
\>>> 10 // 4 
\>>> 10 % 4 
\>>> 10 % 3 

???+ question "Lancer la console et tester"

    {{ IDE('scripts/activite') }}
    
La division entière permet de déterminer la valeur tronquée de la division et le modulo permet de déterminer la valeur du reste. 

On souhaite effectuer la division de 3395  par 99.  

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.019.jpeg)

On s’est arrêté car 29 est plus petit que 99 et qu’on ne souhaitait pas aller plus loin et se retrouver avec un nombre à virgule. On a effectué une division dite division entière. On en déduit donc que 3395 = 99 \* 34 + 29

**Activité n°4.:** **L’exponentiation :** Tester les scripts suivant dans l’interpréteur et compléter la colonne de gauche ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.020.png)

\>>> 3 \*\* 2  >>> 2 \*\* 3 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.021.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.022.png)

5. **Variables,<a name="_page4_x40.00_y133.92"></a> types** 

Une variable est un espace mémoire dans lequel il est possible de stocker une valeur (une donnée). On va affecter des valeurs à des variables.  ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.023.png)

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.024.png)**Attention le symbole de l’affectation est =** 

1. Noms<a name="_page4_x40.00_y194.92"></a> de variables 

Le nom d’une variable s'écrit avec des lettres (**non accentuées**), des chiffres ou bien l’underscore \_ Le nom d’une variable ne doit pas commencer par un chiffre. 

Exemple : age, mon\_age, temperature1  A éviter : Age, AGE, monAge, Temperature1 

2. Le<a name="_page4_x40.00_y249.92"></a> type int (integer) 



|**Activité n°5.:** |
| - |
|>>> age = 17 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.025.png)|
||
|La fonction print affiche la valeur de la variable : |
|>>> print(age) 17 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.026.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.027.png)|
||
|La fonction type() retourne le type de la variable : |
|>>> print(type(age)) ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.028.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.029.png)<class 'int'> |
||
|int est le type des nombres entiers.|



|**Activité n°6.:** L’incrémentation ou la décrémentation : |
| - |
|<p>>>> # ceci est un commentaire ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.030.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.031.png)</p><p>>>> a = 10 </p><p>>>> a = a + 1 # on incrémente la valeur de a. On peut l’écrire aussi a +=1 >>> print(a) </p><p>11 </p><p>>>> a = a – 3 # on décrémente la valeur de a. On peut l’écrire aussi a -=3  >>> print(a) </p>|
||
3. Le<a name="_page4_x40.00_y602.92"></a> type float (nombres en virgule flottante) **Activité n°7.: ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.032.png)**

\>>> b = 17.0  # le séparateur décimal est un point (et non une virgule) >>> print(b) ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.033.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.034.png)

17\.0 

\>>> print(type(b)) 

<class 'float'> 

\>>> c = 14.0 / 3.0 >>> print(c) 4.66666666667 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.035.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.036.png)

\>>> c = 14.0 // 3.0  # division entière >>> print(c) ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.037.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.038.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.039.png)

4\.0 

![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.040.png)Attention : avec des nombres entiers, l’opérateur / renvoie généralement un flottant : 

\>>> c = 14 / 3 >>> print(c) 4.666666666666667 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.041.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.039.png)

4. Le<a name="_page5_x40.00_y196.92"></a> type str (string : chaîne de caractères) ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.042.png)



|**Activité n°8.:**  |
| - |
|<p>>>> nom = 'Dupont'    # entre apostrophes ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.043.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.044.png)</p><p>>>> print(nom) </p><p>Dupont </p><p>>>> print(type(nom)) </p><p><class 'str'> </p><p>>>> prenom = "Pierre"   # on peut aussi utiliser les guillemets >>> print(prenom) </p><p>Pierre </p><p>>>> print(nom, prenom)   # ne pas oublier la virgule </p><p>Dupont Pierre </p>|
||


|**Activité n°9.:** La concaténation désigne la mise bout à bout de plusieurs chaînes de caractères (de type string). La |
| - |
|concaténation utilise l’opérateur + |
|<p>>>> nom = 'Dupont' >>> prenom = "Pierre"![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.045.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.046.png)</p><p>>>> chaine = nom + prenom  # concaténation de deux chaînes de caractères >>> print(chaine) </p><p>DupontPierre </p>|
||


|**Activité n°10.:** La fonction len() retourne la longueur (length) de la chaîne de caractères : |
| - |
|>>> len("abc") 3 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.047.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.048.png)|
||
En Python, **un slice** permet le découpage de structures de données séquentielles (chaînes de caractères ou les listes). Les slices sont des expressions du langage Python qui permettent en une ligne de code d'extraire des éléments d'une liste ou d'une chaîne selon leurs indices **[début:fin:pas].** 

NB : si pas < 0, la liste est parcourue dans le sens inverse. 

0  1  2  3  4  ...  21  22  23  24  25 



|A |B |C |D |E |... |V |W |X |Y |Z |
| - | - | - | - | - | - | - | - | - | - | - |

-26  -25  -24  -23  -22  -5  -4  -3  -2  -1 



|**Activité n°11.:** |
| - |
|<p>>>>>>> string = "ABCDEFGHIJKLMNOPQRSTUVWXYZ" ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.049.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.050.png)</p><p>>>> string[0]  # Renvoie l’élément à l’indice 0 </p><p>'A' </p><p>>>> string[2]  # Renvoie l’élément à l’indice 2 </p><p>'C' </p><p>>>> string[:3]   # Renvoie les trois premiers termes </p><p>'ABC' </p><p>>>> string[:13:2]  # Renvoie les 13 premiers termes, mais 1 sur 2 'ACEGIKM' </p><p>>>> string[::-1]  # Renvoie le renversement la chaine de caractère 'ZYXWVUTSRQPONMLKJIHGFEDCBA' </p><p>>>> string[13::-2]  # Renvoie du 13e à la fin, mais 1 sur 2 et à l’envers 'NLJHFDB' </p><p>>>> string[:13:-2]  # Renvoie du début au 13e, mais 1 sur 2 et à l’envers 'ZXVTRP' </p><p>>>> string[-1::]  # Renvoie du -1 à la fin donc le -1 </p><p>'Z' </p><p>>>> string[-4:-2:]  # Renvoie du -4 au -2 </p><p>'WX' </p>|
||


|**Activité n°12.:** ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.051.png)Attention aux apostrophes et guillemets dans les chaînes de caractères ! |
| - |
|<p>>>> chaine = 'Aujourd'hui' ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.052.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.053.png)</p><p>SyntaxError: invalid syntax </p><p>>>> chaine  = 'Aujourd\'hui'   # séquence d'échappement \' >>> print(chaine) </p><p>Aujourd'hui </p><p>>>> chaine  = "Aujourd'hui" </p><p>>>> print(chaine) </p><p>Aujourd'hui </p>|
||
**Activité n°13.:** La séquence d'échappement \n représente un saut ligne : ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.054.png)

\>>> chaine = 'Premiere ligne\nDeuxieme ligne' >>> print(chaine) ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.055.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.056.png)

Premiere ligne 

Deuxieme ligne 



|**Activité n°14.:** On ne peut pas mélanger les serviettes et les torchons (ici type str et type int) : |
| - |
|<p>>>> chaine = 'a' ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.057.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.058.png)</p><p>>>> chaine = chaine + 2 </p><p>TypeError: cannot concatenate 'str' and 'int' objects </p>|
||
5. Le<a name="_page6_x40.00_y680.92"></a> type list (liste) 

Une liste est une structure de données. Le premier élément d’une liste possède l’indice (l’index) 0. Dans une liste, on peut avoir des éléments de plusieurs types. 



|**Activité n°15.:**  |
| - |
|<p>>>> liste = [5,7,8]   # Crée la liste [5,7,8] ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.059.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.060.png)</p><p>>>> liste   # Affiche le contenu de liste </p><p>[ 5 , 7 , 8 ] </p><p>>>> liste[0]    # Affiche l'élément numéro 0  </p><p>5 </p><p>>>> infoperso = ['Pierre', 'Dupont', 17, 1.75, 72.5] </p><p>>>> print('Prénom : ', infoperso[0])   # premier élément (indice 0) Prénom :  Pierre </p><p>>>> print('Age : ', infoperso[2])    # le troisième élément a l'indice 2 Age :  17 </p>|
||
**Activité n°16.:** Quelques fonctions utiles len() ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.061.png)

\>>> liste = [5,7,8]   # Crée la liste [5,7,8] ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.062.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.063.png)

\>>> len(liste)   # Affiche le nombre d'éléments dans liste 3 



|**Activité n°17.:** Quelques méthodes utiles : append() , pop()|
| - |
|<p>>>> liste = [5, 8, 11] ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.064.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.065.png)</p><p>>>> liste.append(3)     #Ajoute l'élément 3 en fin de liste >>> liste </p><p>[5, 8, 11, 3] </p><p>>>> liste.pop (1)       #Retire l’élément à l’indice 1 </p><p>8 </p><p>>>> liste </p><p>[5, 11, 3] </p>|
||


|**Activité n°18.:** La méthode lower()retourne la chaîne de caractères en casse minuscule (upper() fait l’inverse): |
| - |
|<p>>>> chaine = "BONJOUR"  # ou bien : chaine = str("BONJOUR") ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.066.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.067.png)</p><p>>>> chaine2 = chaine.lower()   # on applique la méthode lower() à l'objet chaine >>> print(chaine2) </p><p>bonjour </p><p>>>> print(chaine) </p><p>BONJOUR </p>|
||


|**Activité n°19.:** Les opérations sur les listes |
| - |
|<p>>>> x = [ 1 , 2 , 3 , 4] ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.068.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.069.png)</p><p>>>> y = [ 5 , 6 , 7 , 8] </p><p>>>> x + y </p><p>[ 1 , 2 , 3 , 4 , 5 , 6 , 7 , 8] </p><p>>>> x = [ 0 , 1] </p><p>>>> [ 0 ]\*10 </p><p>[ 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 ] </p>|
||


|**Activité n°20.:** La fonction split() permet de créer une liste en indiquant le séparateur (par exemple l’espace pour obtenir |
| - |
|une liste de mot) : |
|<p>>>> texte = "Il est important de construire" >>> a = texte.split(' ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.070.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.071.png)') </p><p>>>> a </p><p>['Il', 'est', 'important', 'de', 'construire'] </p>|
||
|Cette méthode est communément appelée tuple unpacking |



|**Activité n°21.:** La fonction ' '.join(a) fait l’inverse, elle prend une liste et renvoie un teste, entre guillemets |
| - |
|on indique le séparateur si on ne met rien, tout sera attaché. |
|<p>>>> liste1 = ' '.join(a) ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.072.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.073.png)</p><p>>>> liste1 </p><p>'Il est important de construire' >>> liste2 = '.'.join(a) </p><p>>>> liste2 'Il.est.important.de.construire' </p>|
||
|C’est la méthode inverse du tuple unpacking |

6. Le<a name="_page8_x40.00_y323.92"></a> type bool (booléen) 



|**Activité n°22.:** Deux valeurs sont possibles : True et False |
| - |
|<p>>>> choix = True ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.074.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.075.png)</p><p>>>> print(type(choix)) <class 'bool'> </p>|
||
Les opérateurs de comparaison : 

Opérateur   Signification    Remarques < ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.076.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.077.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.078.png) strictement inférieur <=  inférieur ou égal >  strictement supérieur  >=  supérieur ou égal 

==  égal  Attention : deux signes  ==  !=  différent 



|**Activité n°23.:**  |
| - |
|<p>>>> b = 10 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.079.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.080.png)</p><p>>>> print(b > 8) </p><p>True </p><p>>>> print(b == 5) False </p><p>>>> print(b != 10) False </p><p>>>> print(0 <= b <= 20) True </p>|
||
**Activité n°24.:** Les opérateurs logiques : and, or, not![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.081.png)

\>>> note = 13.0 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.082.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.083.png)

\>>> print(note >= 12.0 and note < 14.0 ) True 



|**Activité n°25.:** L’opérateur in s’utilise avec des chaînes (type str) ou des listes (type list) : |
| - |
|<p>>>> chaine = 'Bonsoir' ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.084.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.071.png)</p><p>>>> print('soir' in chaine) True </p>|
||
|>>> maliste = [4, 8, 15] ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.085.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.075.png)>>> print(9 in maliste) False |
||
5. **Exercices<a name="_page10_x40.00_y36.92"></a>** 

**Exercice n°1**  ☆ Afficher la taille en octets et en bits d’un fichier de 536 ko. On donne : 1 ko (1 kilooctet) = 1000 octets !!! 1 octet = 1 byte = 8 bits 

**Exercice n°2**  ★ Le numéro de sécurité sociale est constitué de 13 chiffres auquel s’ajoute la clé de contrôle (2 chiffres). Exemple : 1 89 11 26 108 268 91 

La clé de contrôle située à la fin du numéro est calculée par la formule : 97 - (numéro de sécurité sociale modulo 97) Retrouver la clé de contrôle de votre numéro de sécurité sociale. Quel est l’intérêt de la clé de contrôle ? 

**Exercice n°3**  ★ Afficher la valeur numérique de √(4,63 - 15/16) Comparer avec votre calculette. 

**Exercice n°4**  ★ A partir des deux variables prenom et nom, afficher les initiales (par exemple LM pour Léa Martin). 

**Exercice n°5** ★** Quels résultats donnent les instructions suivantes ?  

len("C'est facile de compter") 

len('123' \* 20) 

**Exercice n°6** ☆ Supposons que je veuille imprimer les quatre lignes suivantes :  

Hello World Aujourd'hui 

C'est "Dommage!" Hum \Oh/ 

Quel code est valide ?  

- # code 1 

print('Hello World') print('Aujourd'hui') print('C'est "Dommage!"') print('Hum \Oh/') 

- # code 2 

print("Hello World") print("Aujourd'hui") print("C'est "Dommage!"") print("Hum \Oh/") 

- # code 3 

print("Hello World") print("Aujourd'hui") print("C'est \"Dommage!\"") 

print("Hum \Oh/") 

- # code 4 

print("Hello World") print("Aujourd'hui") print("C'est \"Dommage!\"") print("Hum \\Oh\/") 

**Exercice n°7**  ★☆ **PRÉPAREZ UNE MOUSSE AU CHOCOLAT !**  

La recette de la mousse au chocolat sur le site marmiton.org est la suivante : Ingrédients (pour 4 personnes) : 

3 oeufs 

100 g chocolat (noir ou au lait) 

1 sachet de sucre vanillé 

QUIZ SUR LA MOUSSE AU CHOCOLAT 

Pouvez-pour me dire, à une unité près, la quantité de chaque ingrédient que je dois avoir pour faire ma recette pour 7 personnes, en arrondissant les valeurs calculées à l’unité près (par exemple 3.4 est arrondi à 3 et 3.5 à 4) ? 

*Note :  La fonction prédéfinie round() peut vous aider. Pour comprendre comment, tapez dans une console help(round) (Et si l’anglais n’est pas votre fort, n’oubliez pas que google traduction ou un autre traducteur automatique est votre ami).* 

Première NSI   Chap 12 : A la découverte de Python  Page 12/13 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.086.png)

Pour faire de la mousse pour 7 personnes, combien d’oeufs vous faut-il (arrondis à l’unité) ? Combien de grammes de chocolat vous faut-il (arrondis à l’unité) ? Combien de sachets de sucres vanillés vous faut-il (arrondis à l’unité) ? Exemple : 

Recette de mousse au chocolat pour 7 personnes ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.087.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.088.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.089.png)

Le nombre d'oeufs pour 7 personnes est : … 

La quantité de chocolat pour 7 personnes est : … 

Le nombre de sachet de vanille pour 7 personnes est :… 

Généraliser la recette pour un nombre déterminer par l’utilisateur. Par exemple : 

\>>> Quel est le nombre de personne ?>? (l’utilisateur entre la valeur 10) Recette de mousse ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.090.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.091.png)![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.092.png)au chocolat pour  10  personnes 

Le nombre d'oeufs pour  10  personnes est : 13 

La quantité de chocolat pour  10  personnes est : 438  g 

Le nombre de sachet de vanille pour  10  personnes est : 4 

**Exercice n°8**  ★☆ L’identifiant d’accès au réseau du lycée est construit de la manière suivante : initiale du prénom puis les 8 premiers caractères du nom (le tout en minuscule). 

Alexandre Lecouturier → alecoutur A partir des deux variables prenom et nom, construire l’identifiant. 

QCM :[ http://fabrice.sincere.free.fr/qcm/qcm.php?nom=qcm_python3x_1 ](http://fabrice.sincere.free.fr/qcm/qcm.php?nom=qcm_python3x_1)
Première NSI   Chap 1 : A la découverte de Python  Page 13/13 ![](Aspose.Words.7488426a-f593-4c9d-89c4-e8b91637fe20.086.png)
