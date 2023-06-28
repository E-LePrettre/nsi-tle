---
author: ELP
title: 03 Mise au point des scripts et gestion des exceptions
---


**Table des matières **

1. [Les bonnes pratiques : documenter les fonctions ](#_page0_x40.00_y447.92)
2. [Les tests](#_page1_x40.00_y350.92)
3. [Les préconditions et les postconditions](#_page5_x40.00_y567.92)
4. [Les modules](#_page6_x40.00_y233.92)
5. [Gestion des exceptions](#_page9_x40.00_y401.92)
6. [Exercices](#_page13_x40.00_y375.92)

## **1.  Les bonnes pratiques : <a name="_page0_x40.00_y447.92"></a>documenter les fonctions** 

Chaque fonction doit être **documentée** avec une « chaine de documentation » ou « docstring » c’est-à-dire une chaine de caractère placée immédiatement après l’en-tête de la fonction.

**Activité n° 1.**: Exemple de documentation de fonctions que l’on obtient dans l’aide de la fonction 

```python
def factorielle(n):
   """
   fonction qui retourne la factorielle d'un nombre
   :param n: int
   :return: int
   CU (conditions d'utilisation) : n >= 0
   >>> factorielle(0)
   1
   >>> factorielle(4)
   24
   """
   resultat = 1
   for i in range(2, n+1):
      resultat = resultat * i
   return resultat
```
Tester 
> help(factorielle)
   
Réaliser une telle chaîne de documentation permet 

- **à l’utilisateur** de la fonction de savoir 
  - à quoi peut servir la fonction ; 
  - comment il peut l’utiliser ; 
  - et quelles conditions il doit respecter pour l’utiliser (CU). 
- et **au programmeur** de la fonction de préciser 
   - le nombre et la nature de ses paramètres ; 
   - la relation entre la valeur renvoyée et celle du ou des paramètres ; 
   - ses idées avec quelques exemples. 

## **2. Les<a name="_page1_x40.00_y350.92"></a> tests** 

Pour vérifier si un programme ne produit pas d’erreur au cours de son exécution et s’il effectue réellement la tâche que l’on attend de lui, une première méthode consiste à exécuter plusieurs fois ce programme, en lui fournissant des entrées, ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.006.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.007.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.008.png)**appelées tests**, qui servent à détecter les erreurs éventuelles.  

Pour qu’elles jouent leur rôle, il faut choisir ces entrées de sorte que :  

- L’on sache quelle doit être la sortie correcte du programme avec chacune de ces entrées : 
- Chaque cas distinct d’exécution du programme soit parcouru avec au moins un choix d’entrées 
- Les cas limites soient essayés : nombres nuls ou négatifs, liste vide etc.. 

### **2.1. Les<a name="_page1_x40.00_y523.92"></a> tests simples avec assert![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.009.png)**

L’idée la plus simple à mettre en place est d’utiliser la commande assert pour vérifier que les résultats voulus correspondent à ce que renvoie la fonction désirée.  ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.010.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.011.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.012.png)

En particulier :  

- la division euclidienne de 10 par 2 doit renvoyer un quotient de 5 pour un reste nul ; 
- celles de −10 par 7, de 10 par −7, de 10.3 par 4 ou encore de 11 par 3.5 doivent toutes renvoyer le code −1 « d’erreur »   
- reste le cas particulier du zéro : une division par zéro doit renvoyer −1  

On utilise if \_\_name\_\_ == '\_\_main\_\_': qui permet de n’exécuter les tests que lorsqu’on  travaille sur ce fichier et pas lorsque ce fichier est appelé par un autre fichier du programme.  ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.013.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.014.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.015.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)



 **Activité n° 2.**:    

```python 
 def division\_euclidienne(a,b):   
 if a >=0 and b>0 and type(a)==int and type(b) == int:   
 return a%b, a//b   
 else:   
 return -1   
   
 if \_\_name\_\_ == '\_\_main\_\_':   
 assert division\_euclidienne(10, 2) == (5, 0)   
 assert division\_euclidienne(-10, 7) == -1   
 assert division\_euclidienne(10, -7) == -1   
 assert division\_euclidienne(10.3, 4) == -1   
 assert division\_euclidienne(11, 3.5) == -1   
 assert division\_euclidienne(3, 0) == -1   
```  
   
 L’inconvénient majeur de cette méthode est que l’on doit traiter **une assertion après l’autre** car le programme s’arrête dès   
 le premier test qui échoue. En cas de réussite, il ne se passe simplement **rien.**   
   


 **Activité n° 3.**:    

```python  
 def division\_euclidienne(a,b):   
 if a >=0 and b>0 and type(a)==int and type(b) == int:   
 return a//b, a%b   
 else:   
 return -1   
   
 if \_\_name\_\_ == '\_\_main\_\_':   
 assert division\_euclidienne(10, 2) == (5, 0)   
 assert division\_euclidienne(-10, 7) == -1   
 assert division\_euclidienne(10, -7) == -1   
 assert division\_euclidienne(10.3, 4) == -1   
 assert division\_euclidienne(10, 4.3) == -1   
 assert division\_euclidienne(3, 0) == -1   
```   
   
**CE SONT LES PLUS UTILISÉS** 

### **2.2. Les<a name="_page2_x40.00_y650.92"></a> tests avec doctest** 

Les exemples donnés dans les docstrings (chaine de documentation) peuvent être testés à l’aide du module ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.016.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.017.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.018.png)doctest. ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)



 **Activité n° 4.**:  

```python  
 def factorielle(n):  
 *"""*  
 *fonction qui retourne la factorielle d'un nombre*  
 ***:param** n: int*  
 ***:return**: int*  
 *CU (conditions d'utilisation) : n >= 0*  
 *>>> factorielle(0)*  
 *1*  
 *>>> factorielle(4)*  
 *24*  
 *"""*  
  
 resultat = 1  
 for i in range(2, n+1):  
 resultat = resultat \* i  
 return resultat  

```
 >>> import doctest ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.019.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.020.png)doctest.testmod() TestResults(failed=0, attempted=2)  
  
 La  fonction testmod du module doctest est  allée  chercher  dans  les docstring des  fonctions  du  module  
 actuellement chargé,  tous les exemples (reconnaissables à la présence des triples chevrons >>>  
 ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.021.png) **à mettre un espace après** ), et a vérifié que la fonction documentée satisfait bien ces exemples. Dans le  
 cas présent, une seule fonction dont la documentation contient deux exemples (attempted = 2 ) a été testée, et il  
 n’y a eu aucun échec (failed  = 0 )  



 **Activité n° 5.**:on introduit une erreur dans un des exemples du docstring  

```python  
 def factorielle(n):  
 *"""*  
 *fonction qui retourne la factorielle d'un nombre*  
 ***:param** n: int*  
 ***:return**: int*  
 *CU (conditions d'utilisation) : n >= 0*  
 *>>> factorielle(0)*  
 *12*  
 *>>> factorielle(4)*  
 *24*  
 *"""*  
  
 resultat = 1  
 for i in range(2, n+1):  
 resultat = resultat \* i  
 return resultat  
```

 <p>>>> import doctest ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.022.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.023.png)\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* File … </p><p>Failed example: </p><p>`    `factorielle(0) </p><p>Expected: </p><p>`    `12000 </p><p>Got: </p><p>`    `1 \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* 1 items had failures: </p><p>`   `1 of   2 in \_\_main\_\_.factorielle </p><p>\*\*\*Test Failed\*\*\* 1 failures. </p><p>TestResults(failed=1, attempted=2) </p> 
  
**Activité n° 6.**: on peut rendre automatique les tests : ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.024.png)

```python
def factorielle(n): 

`    `*"""* 

`    `*fonction qui retourne la factorielle d'un nombre     **:param** n: int* 

`    `***:return**: int* 

`    `*CU (conditions d'utilisation) : n >= 0* 

*>>> factorielle(0) 1* 

*>>> factorielle(4) 24* 

*"""* 
\*
`    `resultat = 1 

`    `for i in range(2, n + 1):         resultat = resultat \* i     return resultat 

if \_\_name\_\_ == '\_\_main\_\_':     import doctest 

`    `doctest.testmod() 
```
Ici il n’y a aucune erreur, on n’obtient **rien**, ce qui est parfois déconcertant ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)



 **Activité n° 7.**:  avec une erreur   

```python 
 def factorielle(n):   
 *"""*   
 *fonction qui retourne la factorielle d'un nombre*   
 ***:param** n: int*   
 ***:return**: int*   
 *CU (conditions d'utilisation) : n >= 0*   
   
 *>>> factorielle(0)*   
 *12*   
 *>>> factorielle(4)*   
 *24*   
 *"""*   
   
 resultat = 1   
 for i in range(2, n + 1):   
 resultat = resultat \* i   
 return resultat   
   
 if \_\_name\_\_ == '\_\_main\_\_':   
 import doctest   
 doctest.testmod()   
```  
   


 **Activité n° 8.**:  On rend les doctests bavard même en cas de succès avec le mode verbose   

```python 
 def factorielle(n):   
 *"""*   
 *fonction qui retourne la factorielle d'un nombre*   
 ***:param** n: int*   
 ***:return**: int*   
 *CU (conditions d'utilisation) : n >= 0*   
   
 *>>> factorielle(0)*   
 *1*   
 *>>> factorielle(4)*   
 *24*   
 *"""*   
   
 resultat = 1   
 for i in range(2, n + 1):   
 resultat = resultat \* i   
 return resultat   
   
 if \_\_name\_\_ == '\_\_main\_\_':   
 import doctest   
 doctest.testmod(verbose=True)   
```  
   

## **3. Les<a name="_page5_x40.00_y567.92"></a> préconditions et les postconditions** 

Les assertions sont utilisées pour vérifier un résultat lorsque le test se fait, **test par test**. Donc un seul test à la ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.025.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.026.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.027.png)fois. 

Mais les assertions peuvent aussi être dans le programme **pour vérifier tous les résultats** 



 **Activité n° 9. : Utilisation de l’assertion dans une fonction**   

```python
 from math import sqrt  
  
 def square\_root(x):     # racine carrée ...  
 assert x >= 0     # on veut ici être sur que x est positive ou nul avant tout calc 
 ul  
 racine = sqrt(x)  
 assert racine\*\*2 == x # on vérifie qu'on a bien trouvé la racine carrée  
 return racine  
```


 <p>>>> print(square\_root(25)) ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.028.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.029.png)5.0 </p><p>>>> print(square\_root(-25)) </p><p>Traceback (most recent call last): </p><p>….. </p><p>`    `assert x >= 0     # on veut ici être sur que x est positive ou nul avant tout calcul AssertionError </p> 
  :-  
  
 La ligne assert x >=0 s’appelle une **précondition**, puisqu’elle est appelée au début de la fonction et vérifie les propriétés  
 des arguments passés dans la fonction  
 La ligne assert solution \*\*2 == x s’appelle une **postcondition**, puisqu’elle et appelée juste avant le retour.  
 Les préconditions et les postconditions permettent de trouver très rapidement les bugs.   

Pour plus de précisions :[ https://www.youtube.com/watch?v=DRVoh5XiAZo ](https://www.youtube.com/watch?v=DRVoh5XiAZo)

## **4. Les<a name="_page6_x40.00_y233.92"></a> modules** 
### **4.1. Qu’est<a name="_page6_x40.00_y255.92"></a> ce que c’est ?** 

Un module est un bout de code que l’on a **enfermé dans un fichier**. On emprisonne ainsi des fonctions et des variables ayant toutes un rapport entre elles. Puis si l’on veut travailler avec les fonctionnalités prévues par le module, il n’y a qu’à **importer le module** et utiliser ensuite toutes les fonctions et variables prévues. Par exemple le module math. **Rappels** : 

\>>> import math as mathematiques >>> mathematiques.sqrt(25) ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.030.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.031.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.032.png)

\>>> import random 

\>>> x = random.randint(0,10)  

\>>> from random import randint >>> randint(0,10) 

\>>> from random import \* 

\>>> randint(0,10) 

\>>> randrange(10,20,3) #retourne un entier entre 10 et 19 et un pas =3 

### **4.2. Emprisonner<a name="_page6_x40.00_y498.92"></a> le code dans un fichier** 

Le code doit être enregistrer dans un fichier en .py. (sous windows) 

Sous Linux, comme les extensions ne servent à rien, il faut ajouter dans le fichier une ligne, tout au début, spécifiant le chemin de l’interpréteur Python : ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.033.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.034.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.035.png)

#!/usr/bin/python3.8

Il faut changer le droit d’exécution du fichier avant de l’exécuter comme un script ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.036.png)

ls -l  

sudo chmod a+x *lefichier* 

### **4.3. Derniers<a name="_page6_x40.00_y664.92"></a> ajustements** 

Si le programme contient des accents, il est nécessaire de préciser à Python l’encodage de ces accents. Il faut donc lui indiquer l’encodage. Ligne à placer tout en haut du fichier (juste après le chemin de python sous Linux) ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.037.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.038.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.039.png)

- coding: utf-8 ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)

Il est probable, si vous exécutez votre application d’un double-clic, que votre programme **se referme immédiatement** après avoir exécuté le programme. Il faut donc demander au programme **de se mettre en pause à la fin de son exécution**.  

Ligne à placer dans le fichier (sous windows) ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.040.png)

- **coding: utf-8** 

**import os # On importe le module os qui dispose de variables**  

- **et de fonctions utiles pour dialoguer avec votre**  
- **système d'exploitation** 
- **Programme  blablabla** 
- **On met le programme en pause pour éviter qu'il ne se referme (Windows) ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.041.png)os.system("pause")** 

Sous Linux : on peut simplement exécuter le programme dans la console. Si l’on veut faire une pause on peut utilisez input avant la fin du programme (pas très élégant mais fonctionne) 

### **4.4. Utilisation<a name="_page7_x40.00_y231.92"></a> en module ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)**



 **Activité n° 10. :** On crée un fichier multipli.py qui contiendra la fonction table : table de multiplication  

```python
 **# coding: utf-8**  
  
 **"""module multipli contenant la fonction table"""**  
  
 **def table(nb, max=10):**  
 **"""Fonction affichant la table de multiplication par nb de**  
 **1 \* nb jusqu'à max \* nb"""**  
 **i = 0**  
 **while i < max:**  
 **print(i + 1, "\*", nb, "=", (i + 1) \* nb)**  
 **i += 1**  

```
 Enregistrer votre fichier sous le nom multipli.py dans un dossier c:\langages\  
 Lancer l’invite de commande de windows (cmd)  
 Aller dans le dossier précédent avec la commande cd c:\langages  
 <p>c:\langages>python multipli.py # on lance le fichier ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.042.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.043.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.044.png)</p><p>c:\langages>python # on lance la console Python </p><p>Python 3.8.2 (tags/v3.8.2:7b3ab59, Feb 25 2020, 23:03:10) [MSC v.1916 64 bit (AMD64)] on win32 Type "help", "copyright", "credits" or "license" for more information. </p><p>>>> from multipli import table    # 1ere méthode pour appeler la fonction </p><p>>>> table(5) </p><p>1 \* 5 = 5 </p><p>2 \* 5 = 10 </p><p>3 \* 5 = 15 </p><p>4 \* 5 = 20 </p><p>5 \* 5 = 25 </p><p>6 \* 5 = 30 </p><p>7 \* 5 = 35 </p><p>8 \* 5 = 40 </p><p>9 \* 5 = 45 </p><p>10 \* 5 = 50 </p><p>>>> import multipli  # 2eme methode pour appeler la fonction </p><p>>>> multipli.table(4) </p><p>1 \* 4 = 4 </p><p>2 \* 4 = 8 </p><p>3 \* 4 = 12 </p><p>4 \* 4 = 16 </p><p>5 \* 4 = 20 </p><p>6 \* 4 = 24 </p><p>7 \* 4 = 28 </p><p>8 \* 4 = 32 </p><p>9 \* 4 = 36 </p><p>10 \* 4 = 40 </p> 

### **4.5. Création<a name="_page8_x40.00_y36.92"></a> de son propre module** 



 **Activité n°11. :** On crée deux fichiers :   
  -  
 ￿  le fichier multipli.py créé précédemment  
 ￿  Un fichier test.py qui contiendra le test d’exécution du module. Enregistrer votre fichier sous le nom test.py  
 dans un dossier c:\langages\ 
```python
 # coding: utf-8  
  
 import os  
 from multipli import \*  
  
 # test de la fonction table  
 table(3,11)  
 os.system("pause")  
```  
 Si on est dans python (console précédente) utiliser la fonction exit()  
 <p>>>> exit() ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.045.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.046.png)</p><p>c:\langages>python test.py </p><p>1 \* 3 = 3 </p><p>2 \* 3 = 6 </p><p>3 \* 3 = 9 </p><p>4 \* 3 = 12 </p><p>5 \* 3 = 15 </p><p>6 \* 3 = 18 </p><p>7 \* 3 = 21 </p><p>8 \* 3 = 24 </p><p>9 \* 3 = 27 </p><p>10 \* 3 = 30 </p><p>11 \* 3 = 33 </p><p>Appuyez sur une touche pour continuer... </p> 
  
 On peut noter la ligne os.system("pause") pour que la console ne se faire pas une fois le programme exécuté.  

On a vu comment créer un module, il suffit de le mettre dans un fichier. Ici, on a utilisé un module test mais on aurait pu utiliser toute autre fonction. On peut alors l'importer depuis un autre fichier contenu dans le même répertoire en précisant le nom du fichier (sans l'extension.py). 

Au moment d'importer le module, Python va lire (ou créer s’il n'existe pas) un fichier.pyc. Ce fichier se trouve dans un dossier\_\_pycache\_\_.

Ce fichier est généré par Python et contient le code compilé (ou presque) du module. Il ne s'agit pas réellement de langage machine mais d'un format que Python décode un peu plus vite que le code que vous pouvez écrire. 

### **4.6. Les<a name="_page8_x40.00_y616.92"></a> packages** 

Les modules sont un des moyens de **regrouper plusieurs fonctions**. On peut aller encore au-delà en regroupant des modules dans des packages. Cela permet de ranger plus proprement les modules dans des emplacements séparés.  En pratique, les packages sont des répertoires. ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)



 **Activité n°12. :** Créer un dossier package *dans* le dossier c:\langages\ y placer le fichier multipli.py. Pour importer  
 
 la fonction table dans un nouveau fichier que l’on appelera multipli\_away.py :  
```python
 from package.multipli import table  
 table(7) # 1ere methode appel de la fonction table  
 # OU  
 import package.multipli  
 package.multipli.table(6) # 2eme methode appel de la fonction table  
```


 <p>>>> exit() ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.047.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.048.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.049.png)</p><p>c:\langages>python multipli\_away.py 1 \* 7 = 7 </p><p>2 \* 7 = 14 </p><p>3 \* 7 = 21 </p><p>4 \* 7 = 28 </p><p>5 \* 7 = 35 </p><p>6 \* 7 = 42 </p><p>7 \* 7 = 49 </p><p>8 \* 7 = 56 </p><p>9 \* 7 = 63 10 \* 7 = 70 1 \* 6 = 6 2 \* 6 = 12 3 \* 6 = 18 4 \* 6 = 24 5 \* 6 = 30 6 \* 6 = 36 7 \* 6 = 42 8 \* 6 = 48 9 \* 6 = 54 10 \* 6 = 60 </p> 
  -  
  
## **5. Gestion<a name="_page9_x40.00_y401.92"></a> des exceptions** 

Ce sont les erreurs que peut rencontrer Python en exécutant le programme. Ces erreurs peuvent être **interceptées** très facilement et dans certains cas indispensables. 

### **5.1. Lever<a name="_page9_x40.00_y467.92"></a> d’exception** 

Quand Python rencontre une erreur dans le code, il lève **une exception**.  



 **Application n°13. :** Tester  
  -  
 <p>>>> 1/0 ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.050.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.051.png)</p><p>Traceback (most recent call last): </p><p>`  `File "<stdin>", line 1, in <module> ZeroDivisionError: division by zero </p> 
  
  
 On obtient deux informations :  
 ￿  ZeroDivisionError : le type de l’exception  
 ￿  division by zero : le message qu’envoie Python pour aider à comprendre l’erreur qui vient de se produire.  

A chaque fois qu’il y a une levée d’exception, Python **arrête** l’exécution du programme. Si on teste le programme en faisant un double-clic directement dans l'explorateur, il va se fermer tout de suite (en fait, il affiche bel et bien l'erreur mais se referme aussitôt). 

### **5.2. Gestions<a name="_page9_x40.00_y734.92"></a> des exceptions ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)**

Il  est  possible  de  gérer  les  exceptions  pour  éviter  l’arrêt  brutal  du  programme.  Pour  cela,  on  utilise ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.052.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.053.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.054.png)conjointement les instructions try et except. 

#### **5.2.1. Forme<a name="_page10_x40.00_y106.92"></a> minimale du bloc try**

Syntaxe : 

try:  ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.056.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.057.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.058.png)

- Bloc à essayer  

except:  

- Bloc qui sera exécuté en cas d'erreur 

**TRÈS UTILISÉS AUSSI** 



 **Application n°14. :** On suppose que l’utilisateur entre une année. Ici il peut fournir une valeur impossible à convertir en  
  -  
 entier.  
  
 annee = input()  
 try: # On essaye de convertir l'année en entier  
 annee = int(annee)  
 except:  
 print("Erreur lors de la conversion de l'année.")  
  
 Si l'utilisateur saisit une année impossible à convertir, le système affiche certes **une erreur** mais finit par **planter** (puisque  
 l'année, au final, n'a pas été convertie).   
 Une des solutions envisageables est d'attribuer **une valeur par défaut** à l'année, en cas d'erreur, ou de redemander à  
 l'utilisateur de saisir l'année.  
 <p>>>> 2020-2021 ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.059.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.060.png)</p><p>Erreur lors de la conversion de l'année. </p> 
  
Ensuite et surtout, **cette méthode est assez grossière** : elle essaye une instruction et **intercepte n'importe quelle exception** liée à cette instruction. Ici, c'est acceptable car nous n'avons pas énormément d'erreurs possibles 

sur cette instruction. Mais c'est une **mauvaise habitude. On va voir une méthode plus fine dans la suite.** 

#### **5.2.2. Interception<a name="_page10_x40.00_y547.92"></a> d’exceptions particulières Dans le cas d’une division :** 

resultat = numerateur / denominateur ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.061.png)

Ici plusieurs erreurs sont susceptibles d’intervenir, chacune levant une exception différente. ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.062.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.063.png)

- TypeError : l’une des variables *numerateur* ou *denominateur*  n’a peut diviser ou être divisée (les chaines de caractères ne peuvent être divisées, ni diviser d’autres types) 
- ZeroDivisionError* : si *denominateur* vaut 0. 



 **Application n°15. :** On peut ainsi intercepter ces erreurs possibles à l’exécution du code  
  -  
 numerateur = input('Numérateur ?')  
 denominateur = input('Dénominateur ?')  
  
 try:  



 resultat = int(numerateur) / int(denominateur)   
  -   :-  
 except ValueError:   
 print("La variable numérateur ou dénominateur possède un type incompatible avec la   
 division.")   
 except ZeroDivisionError:    
 print("La valeur entrée au dénominateur est égale à 0.")   
   
   
   
#### **5.2.3. Le<a name="_page11_x40.00_y338.92"></a> bloc try/except et les mots clés else et finally**



 **Application n°16. :** L’instruction else se déroule **s’il n’y a pas d’exceptions** de lever   
  -   :-  
 numerateur = input('Numérateur ?')   
 denominateur = input('Dénominateur ?')   
   
 try:   
 resultat = int(numerateur) / int(denominateur)   
 except ValueError:   
 print("La variable numérateur ou dénominateur possède un type incompatible avec la   
 division.")   
 except ZeroDivisionError as division\_par\_zero : # ici on renomme l’exception   
 print("La valeur entrée au dénominateur est égale à 0.")   
 else:   
 print("Le résultat obtenu est", resultat)   
   
   
Dans les faits, on utilise assez peu else. La plupart des codeurs préfère mettre la ligne contenant le print ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.067.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.068.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.069.png)directement dans le bloc try. ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)



 **Application n°17. :** L’instruction finally permet d'exécuter du code après un bloc try, **quel que soit le résultat** de  
  -  
 l'exécution du bloc.  
 numerateur = input('Numérateur ?')  
 denominateur = input('Dénominateur ?')  
  


 try:   
  -   :-  
 resultat = int(numerateur) / int(denominateur)   
 except ValueError:   
 print("La variable numérateur ou dénominateur possède un type incompatible avec la   
 division.")   
 except ZeroDivisionError as division\_par\_zero : # ici on renomme l’exception   
 print("La valeur entrée au dénominateur est égale à 0.")   
 else:   
 print("Le résultat obtenu est", resultat)   
 finally:   
 print('Ligne qui sera toujours affichée')   
   
   
#### **5.2.4. Avec<a name="_page12_x40.00_y346.92"></a> les assertions**

L’utilisation de* assert* permet de faire des tests Si le test renvoie True*,* l’exécution se poursuit normalement. Sinon, une exception ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.067.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.070.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.069.png)AssertionError* est levée. 

. 



 **Application n°18. :** Dans le programme testant si une année est bissextile, on pourrait vouloir s’assurer que l’utilisateur ne   
  -   :-  
 saisit pas une année inférieure ou égale à 0 par exemple :    
 annee = input("Saisissez une année supérieure à 0 :")   
 try:   
 annee = int(annee) # Conversion de l'année   
 assert annee > 0   
 except ValueError:   
 print("Vous n'avez pas saisi un nombre entier.")   
 except AssertionError:   
 print("L'année saisie est inférieure ou égale à 0.")   
   
   
#### **5.2.5. Déclencher<a name="_page12_x40.00_y748.92"></a> une exception**

L’instruction raise permet au programmeur de déclencher une exception spécifique.. ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.071.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.072.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.073.png)



 **Application n°19. :** Si l’utilisateur entre une année trop grande par exemple supérieure à 3000, on peut estimer qu’il s’agit   
  -   :-  
 d’une erreur   
 annee = input("Saisissez une année supérieure à 0 :")   
 try:   
 annee = int(annee) # Conversion de l'année   
 if annee >=3000 or annee < 0:   
 raise ValueError   
 except ValueError:   
 print("L'année entrée n'est pas dans l'intervalle [0, 2999]")   
 except AssertionError:   
 print("L'année saisie est inférieure ou égale à 0.")   
   
   
N’oubliez pas : un programme bien écrit doit **gérer proprement les exceptions.** ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.074.png)

## **6. Exercices<a name="_page13_x40.00_y375.92"></a>** 

**Exercice 1 :** On considère la fonction multiplier\_par\_deux(x) qui prend en paramètre x et qui renvoie son double. Ecrire un script de cette fonction avec : 

1. Cas des assert :  
   1. Sa documentation dans le docstring comme dans l’activité 1. Ne pas mettre d’exemples 
   1. 4 tests en assert (comme dans l’activité 3) : avec 0, avec -1, avec 3.2 et avec ‘a’ 
1. Cas du doctest en mode verbose : 
- Sa documentation dans le docstring comme dans l’activité 1.  
- 4 tests dans le docstring (comme dans l’activité 10) : avec 0, avec -1,  avec 3.2 et avec ‘a’ 

**Exercice 2** : On considère une fonction somme\_carres(x) qui prend en paramètre x (entier strictement positif) et renvoie la somme des x premiers carrés non nuls.  

Ecrire un script de cette fonction avec : 

1. Cas des assert :  
   1. Sa documentation dans le docstring comme dans l’activité 1. Ne pas mettre d’exemples 
   1. 3 tests en assert (comme dans l’activité 3) : avec 1, avec 2 et avec 3 
1. Cas du doctest en mode verbose : 
- Sa documentation dans le docstring comme dans l’activité 1.  
- 3 tests dans le docstring (comme dans l’activité 10) : avec 1, avec 2 et avec 3 

**Exercice 3** : La fonction précédente à pour condition d’utilisation : x doit être strictement positif. Déclencher une exception et capturer là si le nombre entrée est 0 ou négatif. ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)

Exemple : 

\>>> somme\_carres(5) ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.075.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.076.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.077.png)55 

\>>> somme\_carres(0) 

Le nombre entré est nul ou négatif 

\>>> somme\_carres(-2) 

Le nombre entré est nul ou négatif 

**Exercice 4 :** On part du script suivant qui permet d’inverser un nombre ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.078.png)

try: 

`    `chaine = input('Entrer un nombre : ') # permet de pouvoir gérer l’exception ValueError ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.079.png)    nombre = float(chaine) 

`    `inverse = 1.0/nombre 

except ValueError: 

`    `#ce bloc est exécuté si une exception de type ValueError est levée dans le bloc try ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.080.png)

`    `print(chaine, "n'est pas un nombre !") 

except ZeroDivisionError: 

#ce bloc est exécuté si une exception de type ZeroDivisionError est levée dans le bloc try     ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.081.png)print("Division par zéro !") 

else: 

`    `#on arrive ici si aucune exception n'est levée dans le bloc try ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.082.png)

`    `print("L'inverse de", nombre, "est :", inverse) 

Compléter le script précédent de manière à ressaisir le nombre en cas d’erreur. On pourra englober le script dans une boucle while. Par exemple : 

\>>>  ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.083.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.084.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.085.png)

Entrer un nombre : >? "a" 

"a" n'est pas un nombre ! Entrer un nombre : >? 'salut !' 'salut !' n'est pas un nombre ! Entrer un nombre : >? 0 Division par zéro ! 

Entrer un nombre : >? 'mince' 'mince' n'est pas un nombre ! Entrer un nombre : >? 2 L'inverse de 2.0 est : 0.5 

Aide : penser à une boucle infinie et au mot clé break.  

**Exercice 5 :** Ecrire un script qui calcule la racine carrée d’un nombre, avec gestion des exceptions. Utiliser la fonction sqrt() du module math.  

Par exemple : ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)

Première NSI   Chap 15 : Mise au point des scripts et gestion des exceptions  Page 15/16 

\>>>  ![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.086.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.087.png)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.088.png)

Entrer un nombre : >? go 

go n'est pas un nombre valide ! Entrer un nombre : >? -5.26 

-5.26 n'est pas un nombre valide ! Entrer un nombre : >? 16 

La racine de  16.0 est : 4.0 

Remarquez bien qu’on demande le nombre à l’utilisateur *jusqu'à* ce qu’il convienne. 

[Documentation sur les exceptions ](http://docs.python.org/3/tutorial/errors.html#exceptions)

Source :[ Fabrice Sincère ](http://fsincere.free.fr/isn/python/cours_python_ch5.php)-[ Contenu sous licence CC BY-NC-SA 3.0 ](http://creativecommons.org/licenses/by-nc-sa/3.0/fr/)![](Aspose.Words.e93ca6fc-1f42-415a-966d-a3fd9bc79766.005.png)
Première NSI   Chap 3 : Mise au point des scripts et gestion des exceptions  Page 16/16 
