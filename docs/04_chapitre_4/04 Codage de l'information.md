---
author: ELP
title: Chapitre 4 - Codage de l'information
---


**Table des matières** 

1. [Vocabulaire ](#_page0_x40.00_y610.92)
2. [Les bases courantes](#_page1_x40.00_y467.92)
3. [Le codage des nombres entiers signés en binaire](#_page5_x40.00_y574.92)
4. [Exercices](#_page9_x40.00_y36.92)
5. [Représentation des nombres réels](#_page12_x40.00_y36.92)
6. [Exercices](#_page15_x40.00_y36.92)
7. [Codage des caractères](#_page16_x40.00_y36.92)
8. [Représentation des images](#_page17_x40.00_y448.92)
9. [Exercices](#_page18_x40.00_y36.92)


## **1. Vocabulaire<a name="_page0_x40.00_y610.92"></a>** 

La mémoire des ordinateurs est constituée d’une multitude de petits circuits électroniques qui ne peuvent être, chacun, que dans **deux états conventionnellement appelés 0 et 1**, (1, y'a du courant, 0, y'en a pas), mais on aurait pu tout aussi bien les appeler faux et vrai.  

0, ou 1 s’appelle :  
- un booléen,  
- ou un chiffre binaire  
- ou encore un bit (binary digit).  

Un tel circuit à deux états s’appelle un **circuit mémoire un bit.**  

Toute l’information traitée par un ordinateur est en binaire.  

Le **bit** (b minuscule dans les notations) est la plus petite unité d'information manipulable par une machine numérique. 

Il est possible de représenter physiquement cette information binaire par un signal électrique ou magnétique, qui, au- delà d'un certain seuil, correspond à la valeur 1.  

L'**octet** (en anglais **byte** ou B majuscule dans les notations) est une unité d'information composée de **8 bits**. Il permet par exemple de stocker un caractère comme une lettre ou un chiffre. 

Une  unité  d'information  composée  de  16  bits  est  généralement  appelée  **mot**  (en  anglais  word).  Une  unité d'information de 32 bits de longueur est appelée mot double (en anglais double word, d'où l'appellation dword). 

Beaucoup d'informaticiens ont appris que 1 kilooctet valait 1024 octets. Or, depuis décembre1998, l'organisme international IEC a statué sur la question[^1]. 

Voici les unités standardisées : 

- Un kilooctet (ko)  = 103 octets 
- Un mégaoctet (Mo)  = 106 octets 
- Un gigaoctet (Go)  = 109 octets 
- Un téraoctet (To)  = 1012 octets 
- Un pétaoctet (Po)  = 1015 octets 
- Un exaoctet (Eo)  = 1018 octets 
- Un zettaoctet (Zo)  = 1021 octets 
- Un 1yottaoctet (Yo)  = 1024 octets 

Un mégaoctet devrait en principe valoir 1000 x 1000 octets, c'est-à- dire 1.000.000 d'octets, mais il vaut 1024 x 1024 octets en informatique, c'est-à-dire 1.048.576 octets... ce qui correspond à une différence de 4,63% ! 

## **2. Les<a name="_page1_x40.00_y467.92"></a> bases courantes** 
### **2.1. La<a name="_page1_x40.00_y489.92"></a> base 10 ou base décimale** 

Elle s’appuie sur **10 « symboles »** : 0, 1, 2, 3, 4, 5, 6, 7, 8, 9. On peut ainsi compter jusqu'à 9. Et si l'on veut aller au- delà de 9, il faut changer de rang. Cela signifie que si le rang des unités est plein, il faut passer à celui des dizaines, puis des centaines, milliers… 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.008.png)

185 = 1 × 102 + 8 × 101 + 5 × 100 
**La position des chiffres définit la valeur associée à ce chiffre.** 

### **2.2. La<a name="_page1_x40.00_y677.92"></a> base 2 ou base binaire** 
#### **2.2.1. Le<a name="_page1_x40.00_y697.92"></a> binaire**

**Remarque** : Il faut toujours indiquer la base dans laquelle un nombre est exprimé (sauf, par usage et commodité, en base 10) : 1010<sub>2</sub> ou %1010. La base par défaut du code Python est la base 10. 

Par exemple :  

**Décimal**  0  1  2  3  4  5  6  7  8  9  10 
**Binaire**  0000  0001  0010  0011  0100  0101  0110  0111  1000  1001  1010 

#### **2.2.2. Le<a name="_page2_x40.00_y74.92"></a> binaire en Python**

**Activité n° 1.**: La fonction bin de Python donne une chaîne de caractères représentant l’écriture binaire de l’entier passé en paramètre. 
Tester
> bin(47) '

> 0b101 

???+ question "Faire ce qui est proposé"

    {{ terminal() }}

En Python on peut écrire les nombres entiers directement en binaire. Il suffit pour cela de faire précéder cette écriture par 0b***.***  

#### **2.2.3. Passage<a name="_page2_x40.00_y235.92"></a> du système décimal au binaire**

**Méthode de Horner :**   

Exemple : Convertir 145 en binaire  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.013.png)

- 145 = 72 × 2 + 1  
- 72 = 36 × 2 + 0  
- 36 = 18 × 2 + 0  *Sens de lecture  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.014.png)*
- 18 = 9 × 2 + 0  
- 9 = 4 × 2 + 1  
- 4 = 2 × 2 + 0  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.015.png)
- 2 = 1 × 2 + 0  
- 1 = 0 × 2 + 1  

La conversion de 145 en binaire est donc : 100100012 **Méthode des puissances de 2** : 

**Exposant** n  **0  1  2  3  4  5  6  7  8  9  10  11  12  13  14 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.016.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.017.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.018.png)**

2n  1  2  4  8  16  32  64  128  256  512 1024 2048 4096 8192 16384 

Écrire 57 en base 2 (=donner sa représentation binaire). 

- 32 < 57 < 64. Donc on fait 57 = 32+25 = 25+25. On a un chiffre 1 à la position 6. 
- 16 < 25 < 32. Donc on fait 25 = 16+9 = 24+9. On a un chiffre 1 à la position 5. 
- 8 < 9 < 16. Donc on fait 9=8+1=23+1. On a un chiffre 1 à la position 4. 
- 1=20. On peut s’arrêter (dès qu’on atteint une puissance de 2). On a un chiffre 1 à la position 1. 57 = 0b111001  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.019.png)

**L’algorithme des divisions successives**  

- On divise par 2 jusqu'à ce que le quotient soit 0  
- On lit les bits en montant de droite à gauche : 167 = 0b10100111  
#### **2.2.4. Passage<a name="_page2_x40.00_y722.92"></a> du système binaire au décimal**

Les nombres écrits en binaire suivent le même principe que ceux écrits en décimal mais avec les** puissances de deux.** Le mot de 8 bits %01101110 =  1.26 +  1.25 +  1.23 +  1.22 +  1.21 en décimale. 

**Puissances** 27 26 25 24 23 22 21 20 
 -  -  -  -  -  -  -  -  - 
**Valeurs en décimale** 128 64 32 16 8 4 2 1 
**exemple** 0 1 1 0 1 1 1 0 
**Valeur en décimale correspondante** 64 + 32 + 8 + 4 + 2 = 110 

Donc, quand on a un nombre binaire, **il suffit de multiplier chaque nombre qui le compose par la puissance de 2 correspondante au rang de son bit et d’additionner tous les résultats.** 

**Activité n° 2.**: La fonction int de Python donne une chaîne de caractères représentant l’écriture décimal d’un entier passé en paramètre. ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.020.png)

\>>> int('01101110', 2) 110 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.021.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.022.png)

On retrouve bien la valeur 110 précédente. 

#### **2.2.5. Addition<a name="_page3_x40.00_y258.92"></a> de deux nombres binaires** 

On procède comme avec les nombre écrit en décimal, sauf que 1 + 1 = 10. Exemple :  

Retenues   1  1  1 

a  1  1  0  1  0  1  1 

b  +   1  1  0  0  1  1 

a + b =  1  0  0  1  1  1  1  0 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.023.png)

On remarque que la somme de deux nombres binaires sur m bits et n bits donne un nombre binaire sur le plus ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.024.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.025.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.026.png)grand nombre de bits **(m ou n) + 1 au maximum**. 

#### **2.2.6. Multiplication<a name="_page3_x40.00_y462.92"></a> de deux nombres binaires Exemple :**  

a  1  1  0  1  0  1  1 b  \*  1  1 

Retenues  1  1  1  1  1  1 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.027.png)

1  1  0  1  0  1  1 1  1  0  1  0  1  1 

a \* b =   1  0  1  0  0  0  0  0  1 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.028.png)

On remarque que le produit de deux nombres binaires sur m bits et n bits donne un nombre binaire sur **m + n bits au maximum.![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.029.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.030.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.006.png)** 

### **2.3. La<a name="_page3_x40.00_y727.92"></a> base 16 ou base hexadécimal** 
#### **2.3.1. L’hexadécimal<a name="_page3_x40.00_y747.92"></a>** 

En informatique, tout est basé sur le binaire, et étant une base d'indice 2, c'est plus aisé d'encoder les informations sur un nombre multiple de 2. On utilise donc souvent la base 16, appelé **système hexadécimal**  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)

**Hexa  0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.032.png)**Décimal  0  1  2  3  4  5  6  7  8  9  10  11  12  13  14  15 

**Remarque** : Il faut toujours indiquer la base dans laquelle un nombre est exprimé (sauf, par usage et commodité, en base 10) : A916 ou $A9 ou #A9. La base par défaut du code Python est la base 10. 

#### **2.3.2. Passage<a name="_page4_x40.00_y103.92"></a> du système binaire au système hexadécimal et réciproquement**

Pour convertir un nombre binaire en base 16, **on regroupe les bits 4 à 4**, chaque groupe donnant un chiffre hexadécimal. À l'inverse, passer d'un nombre hexadécimal à sa représentation binaire se fait en remplaçant chaque chiffre pour son équivalent sur 4 bits![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.033.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.034.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.035.png).  

Si le nombre binaire de départ n'a pas un nombre de bits multiple de 4, **il faut ajouter des zéros en tête** (ce qui ne change pas sa valeur) afin de pouvoir les regrouper 4 par 4. 

110110012 = 1101 10012 = 916,  7 16 = 0111 11112 = 011111112.  

À noter que la chaîne de caractères, avec Python, débute par*** 0x, le x mettant en évidence qu’il s’agit de l’écriture décimal d’un entier. 

#### **2.3.3. Passage<a name="_page4_x40.00_y309.92"></a> du système décimal au système hexadécimal**  

**Méthode de Horner** : Pour convertir un nombre binaire en base 16, on regroupe les bits 4 à 4, chaque groupe donnant un chiffre hexadécimal.  

Exemple : Convertir 185 en hexadécimal ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.036.png)

- 185 = 11 × 16 + 9  *Sens de lecture ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.037.png)*
- 11 = 0 × 16 + 11 

La conversion de 185 en hexadécimal est donc : B9. **L’algorithme des divisions successives :** comme pour le binaire 

**Activité n° 3.**: La fonction hex de Python donne une chaîne de caractères représentant l’écriture binaire de l’entier passé en paramètre. ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.038.png)

\>>> hex(185) '0xb9' ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.039.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.040.png)

\>>> 0x7F 127 

#### **2.3.4. Passage<a name="_page4_x40.00_y569.92"></a> du système hexadécimal au décimal** 

Il faut remplacer les lettres par les nombres correspondants : 

- un A, on le remplace par un 10 
- un C, on le remplace par un 12 
- un D, on le remplace par un 13 
- un E, on le remplace par un 14 
- un F, on le remplace par un 15 

Le principe est le même que pour la conversation "binaire en décimal"  

Par exemple : 

12 716 = 1 × 163 + 2 × 162 + 11 × 161 + 7 × 160 = 1 × 4096 + 2 × 256 + 11 × 16 + 7 = 4791. 



**Activité n° 4.**: La fonction int de Python donne une chaîne de caractères représentant l’écriture décimal d’un 
 - 
entier passé en paramètre. 



>>> int('12B7', 16) 4791 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.041.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.042.png)
 :- 

#### **2.3.5. Addition<a name="_page5_x40.00_y90.92"></a> de deux nombres en base 16** 

816 + 916 = une seizaine et un ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.043.png)

C’est-à-dire on pose 1 et on retient le 1 de la seizaine 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.044.png)

Ce nombre 151 en hexadécimal se lirait donc "une seizaine-carré cinq seizaines et un". D'ou le calcul en base 10 : 1x16x16 + 5x16 + 1 = 256 + 80 + 1 soit  337 en base 10 Ainsi le nombre 151 exprimé en hexadécimal est le même nombre que 337 en base 10 

On pouvait aussi convertir les deux nombres en binaire et faire leur addition. 

### **2.4. Une<a name="_page5_x40.00_y421.92"></a> base quelconque** 

Par exemple la représentation de base cinq de 58 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.045.png)

Donc, 58 objets se regroupent en 11 paquets et 3 unités, puis les 11 paquets se regroupent en 2 paquets de paquets et 1 paquet. 

58 = 2 × 5² + 1× 51 +3 × 50. Donc 58 = 213

5\. 

## **3. Le<a name="_page5_x40.00_y574.92"></a> codage des nombres entiers signés en binaire** 

Un entier naturel est appelé **entiers non signés.** En Python, on ne manipule que des **entiers relatifs.** 

**Entiers naturels** : entiers positifs ou nuls (0, 1, 2 etc.) ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.046.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.047.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.048.png)

**Entiers relatifs** : entiers de n’importe quel signe (…, -2, -1, 0, 1,…) 

### **3.1. Représentation<a name="_page5_x40.00_y708.92"></a> avec la valeur absolue** 

Un entier relatif comporte **un signe** et **une valeur absolue (VA).** Par convention : **le bit de plus fort poids ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.049.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.050.png)(le plus à gauche) représente le signe :** 

- **0 = signe +** 
- **1 = signe –** 

Le bit de plus fort poids est aussi appelé **le MSB (Most Significant Bit)** Les autres bits représentent **la valeur absolue** du nombre  

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.051.png)

Sur 8 bits, on a 28 - 1 nombres de l’intervalle : [-(27 - 1), 27-1] soit [-127, +127] 

Sur n bits, on a 2n - 1 nombres de l’intervalle : [-(2n-1 – 1), 2n-1-1]  

**Contrainte immédiate** : il faut que la machine sache quelle est la taille du nombre !! on encodera dans tout le chapitre **sur 8 bits** 

**Premier inconvénient de ce codage** : le zéro est codé de deux écritures : le zéro positif 00000000 et le zéro négatif 10000000 

Testons avec 27 : 

27 = 0b11011 

On complète sur 8 bits : 27 = 0b 0001 1011 

27 > 0 on garde le premier bit à 0 

Testons avec -9 : 

La valeur absolue de -9 est 9. 9 = 0b1001 

On complète sur 8 bits : 

9 = 0b 0000 1001 

-9 < 0 on remplace le premier bit par -1 : 

-9 = 0b 1000 1001 

Testons avec 27 + (-9) = 18 

0b 0001 1011 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.052.png)

+ 0b 1000 1001 -------------- 
- 0b 1010 0100 

… mais 0b 1010 0100 = 164 

Échec total ! **Le binaire signé ne permet pas de réaliser les additions habituelles** 

### **3.2. Principe<a name="_page6_x40.00_y773.92"></a> du complément à 2n :

#### **3.2.1. De<a name="_page7_x40.00_y36.92"></a> décimal vers binaire : Pour un entier positif**

- coder l’entier en binaire comme d’habitude, 
- compléter l’octet avec des 0 devant. 

Exemple : pour 27  

- coder l'entier en binaire comme d'habitude : 27 = 0b11011 
- compléter l'octet avec des 0 devant : 27 = 0b 0001 1011 

Le complément à 2 sur un octet de 27 est 0b 0001 1011 

#### **3.2.2. De<a name="_page7_x40.00_y158.92"></a> décimal vers binaire : Pour les entiers négatifs** 
- Coder la valeur absolue du nombre en base 2, 
- compléter l’octet avec des 0 devant, 
- échanger tous les bits (1↔0), 
- ajouter 1. 

Exemple pour -9 : 

- coder la valeur absolue du nombre : 9 = 0b1001 
- compléter l'octet :   0b 0000 1001 
- échanger tous les bits :  0b 1111 0110 
- ajouter 1 :   0b 1111 0111 

Le complément à 2 sur un octet de −9 est 0b 1111 0111 

#### **3.2.3. Addition<a name="_page7_x40.00_y335.92"></a> de deux nombres binaires** 

Vérifions : 27+(−9)=18

`  `0001 1011 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.054.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.055.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.056.png)

+ 1111 0111 

\----------- 

- 0001 0010 

On vérifie immédiatement que 18 = 0b10010 

**Remarque** la dernière retenue (tout à gauche) disparait. 

#### **3.2.4. De<a name="_page7_x40.00_y496.92"></a> binaire vers décimal : Pour les entiers négatifs** 

Si l’entier est négatif (si premier bit est 1) 
- On échange tous les bits 0↔1, 
- On ajoute 1, 
- On converti en binaire comme d’habitude, 
- On change le signe. 

Exemple : 0b 1111 0111 

- On échange tous les bits, ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.057.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.058.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.059.png)

0b 0000 1000 

- On ajoute 1, 

0b 0000 1001 

- On convertit en binaire comme d'habitude, 0b 1001 = 1 \* 1 + 1 \* 8 = 9 
- On change le signe. 

0b 1111 0111 = -9 

### **3.3. Table<a name="_page7_x40.00_y758.92"></a> de valeurs** 

bit ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.060.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.061.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.062.png)

` `de 

signe 

`    `0 1 1 1 1 1 1 1 =  127 (à connaitre)     0      ...      =  ... 

`    `0 0 0 0 0 0 1 0 =    2 

`    `0 0 0 0 0 0 0 1 =    1 

`    `0 0 0 0 0 0 0 0 =    0 

`    `1 1 1 1 1 1 1 1 =   -1 

`    `1 1 1 1 1 1 1 0 =   -2 

`    `1      ...      =  ... 

`    `1 0 0 0 0 0 0 1 = -127 

`    `1 0 0 0 0 0 0 0 = -128 (à connaitre) 

Le 4 juin 1996, une fusée Ariane 5 a explosé 40 secondes après l'allumage. La fusée et son chargement ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.063.png)avaient coûté 500 millions de dollars. La commission d'enquête a rendu son rapport au bout de deux semaines. Il s'agissait d'une erreur de programmation dans le système inertiel de référence. À un moment donné, un nombre codé en virgule flottante sur 64 bits (qui représentait la vitesse horizontale de la fusée par rapport à la plate-forme de tir) était converti en un entier sur 16 bits. Malheureusement, le nombre en question était plus grand que 32768 (le plus grand entier que l'on peut coder sur 16 bits) ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.064.png)et la conversion a été incorrecte. 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.065.png)

## **4. Exercices<a name="_page9_x40.00_y36.92"></a>** 

**Exercice 1 :** ★ On suppose toujours nos entiers encodés sur un octet. 

- Donner la représentation binaire 12, 100 et 88 
- Réaliser l’addition binaire bit à bit de ces 3 nombres. 

**Exercice 2 :** ★ On suppose toujours nos entiers encodés sur un octet. Donner les compléments à 2 de -12, -100 et -88. 

**Exercice 3 :** ★

- Réaliser l’addition binaire des compléments à 2 des nombres 12 et -100. 
- Vérifier qu’on retrouve bien le résultat précédent pour -88. 

**Exercice 4 :** ★ Donner les notations décimales des binaires signés sur un octet suivant :** 

- 0b1111 1111 
- 0b1000 0000 
- 0b0111 1111 
- 0b1010 0011 

**Exercice 5 :** Conversion décimal – binaire** 

1. ★ Écrire un programme qui convertisse un nombre décimal en binaire. Utiliser une fonction dec2bin ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.066.png)On donne l’algorithme suivant : 

Algorithme dec2bin ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.067.png)

{ conversion décimal → binaire pour des entiers ≥ 0 } 

variables 

nombre : entier 

binaire : tableau de [1..N] entiers 

mot  : chaine de caractère 

début 

lire(nombre) 

fonction(nombre) 

binaire.ajout(nombre modulo 2)  { ajout en fin de tableau } tantque nombre ≥ 2 faire 

nombre := nombre / 2 

binaire.ajout(nombre modulo 2) 

tantque longueur(binaire)<7 

binaire.ajout(0) 

binaire.renversée 

mot := chaine de caractère correspondant à binaire 

afficher(mot) 

fin 

**Aide :**  

- la méthode renversée avec reverse()[ https://www.geeksforgeeks.org/python-list-reverse/ ](https://www.geeksforgeeks.org/python-list-reverse/)ou avec slicing inverse : binaire[::-1]
- pour transformer la liste en chaine de caractère : mot=''.join(str(element) for element in binaire) 

Tout au début du programme, ne pas oublier cette ligne : # coding: utf-8

2. Indiquer l’utilité de cette ligne. 
2. Donner la conversion de 1843 en binaire2. 
2. Convertir -2 et conclure. 
2. ★★★ Modifier le programme pour coder un nombre négatif selon la méthode du complément à 2. **Aide :** 
- Le complément à 2 peut être calculer par une autre méthode : Sur 8 bits, -88 en complément à 2 correspond au nombre binaire suivant : 
- 27 – 88 = 40 
- 40 en binaire => 010 1000 

Le bit de signe donne donc 1010 1000 

- Faire une deuxième fonction dec2bin\_negatif qui teste si le nombre entré est positif ou négatif et qui fait appel à la première fonction codée ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.068.png)

2 1843 est l’année de création du 1er programme informatique par Augusta Ada King, comtesse de Lovelace ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)

6. Convertir -1 pour un codage sur un mot et conclure. 
6. Convertir -1.1 et conclure. 

Pour éviter que le programme « crash » sur une erreur de valeur d’entrée (ValueError), une façon de gérer cette erreur est d’intercepter le message d’erreur et de le traiter correctement à l’aide des instructions try et except. 

La syntaxe est la suivante : 

try: ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.069.png)

- bloc d’instructions à exécuter 

except ValueError: 

- afficher « erreur de valeur » 
8. ★★ Modifier le programme précédent en conséquence. 
8. ★★Faire une boucle infinie pour que le programme demande un autre nombre tant que la valeur n’est pas un entier relatif 
8. Vérifier la cohérence et la stabilité du programme avec quelques tests : 1, -1, 0, 1.1, -1.0, a 

**Exercice 6 :** Conversion hexadécimal – binaire

1. ★★★ Écrire un programme hex2dec qui convertisse un nombre hexadécimal en décimal non signé. ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.070.png)**Aide :**  
- On utilisera une chaîne : chaine = "0123456789ABCDEF".![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.071.png)
- Et on pourra utiliser la méthode index()[ https://www.geeksforgeeks.org/python-list-index/ ](https://www.geeksforgeeks.org/python-list-index/)
2. Donner les conversions de 1, A, a et A5 en décimal. 
2. Donner la conversion de AZ et conclure. 
2. Modifier votre programme comme précédemment pour gérer des erreurs éventuelles (bugs). 

NB : on affichera « valeur héxadécimale incorrecte » 

On souhaite réutiliser le code de programme dec2bin pour écrire un programme hex2bin qui convertisse un nombre hexadécimal en binaire. Pour cela, il « suffit » de récupérer la valeur obtenue par hex2dec et la passer à dec2bin. 

**On prototype** une fonction en indiquant son nom, le type des éventuels paramètres et de la valeur renvoyée le cas échéant. ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.072.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.073.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.074.png)

Exemple pour une fonction qui calcule le carré d’un nombre et renvoie la valeur trouvée : 

def carre(nombre : int) -> int: return nombre \*\* 2 

5. Dans le programme hex2bin, faire un copier/coller du code du programme dec2bin. 
5. ★★ Remodeler (refactor) le code pour le transformer en fonction dont le prototype sera le suivant : ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.075.png)



dec2bin(nombre : int, nbits : int) -> list 
 -  -  :-  :- 
<p>- nombre est le nombre décimal à convertir </p><p>- nbits est le nombre de bits </p><p>- la fonction renvoie la conversion sous forme d’</p>une liste binaire (au lieu de l’afficher) 

7. Tester la fonction en l’appelant depuis le corps principal (main) du programme. **Aide** :  
   1. Juste après la fonction : print(dec2bin(501, 10))
   1. vérifier que l’on obtient [0, 1, 1, 1, 1, 1, 0, 1, 0, 1]
7. A la suite de cette fonction, faire un copier/coller du code du programme hex2dec. 
9. ★★ Remodeler (refactor) le code pour le transformer en fonction dont le prototype sera le suivant : 

hex2dec(hexa : str) -> int ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.076.png)

- hexa est le nombre hexadécimal à convertir 
- la fonction renvoie la conversion sous forme d’un nombre décimal 
10. Tester la fonction en l’appelant dans le corps principal (main) du programme. **Aide** :  
    1. Juste après la fonction : print(hex2dec('AF'))![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.077.png)
    1. vérifier que l’on obtient 175![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.078.png)
10. ★★ Enchaîner les appels successifs pour afficher la valeur binaire sur 8 bits des nombres suivants : 1, A et A5. 
10. Donner la conversion de AZ et conclure. 

Traiter l’erreur en local a ses limites : il faut faire remonter l’erreur vers les couches supérieures. La dernière couche traitera en dernier l’erreur selon des spécifications bien précises. 

13. ★★ Modifier les fonctions hex2dec et dec2bin pour qu’elles renvoient « None » au lieu d’afficher une erreur.  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.079.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.080.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.081.png)

Syntaxe : 

try: ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.082.png)

- bloc d’instructions à exécuter 

except : 

return None 

NB : L'objet Python None, exprime l'absence de valeur. Cet objet n'a aucune méthode. 

14. ★★ Modifier le corps principal du programme pour tester la valeur de retour sur chaque fonction appelée. En cas d’erreur (valeur None), afficher le message d’erreur . 
14. Créer un docstring pour chacune des fonctions du programme hex2bin. 

Syntaxe, par exemple : 

def fonction (x : int, y : int) -> tuple:     """ ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.083.png)

`    `fonction qui … 

`    `:param x: int 

`    `:param y: int 

`    `:return: tuple 

`    `""" 

Convertisseur en ligne :[ https://www.exploringbinary.com/twos-complement-converter/ ](https://www.exploringbinary.com/twos-complement-converter/)

QCM :[ http://www.scientillula.net/MPI/fex6_conversions/fex6_conversions.html ](http://www.scientillula.net/MPI/fex6_conversions/fex6_conversions.html)QCM 2 :[ http://fabrice.sincere.free.fr/qcm/qcm.php?nom=qcm_numerique](http://fabrice.sincere.free.fr/qcm/qcm.php?nom=qcm_numerique)

## **5.  Représentation des nombres réels<a name="_page12_x40.00_y36.92"></a>** 

En base 10, l’expression 652,375 est une manière abrégée d’écrire : 

6\.102 + 5.101 + 2.100 + 3.10−1 + 7.10−2 + 5.10−3

Il en va de même pour la base 2. L’expression 110,101 signifie : 

1\.22 + 1.21 + 0.20 + 1.2−1 + 0.2−2 + 1.2−3

### **5.1. Conversion<a name="_page12_x40.00_y115.92"></a> de binaire en décimal** 

On peut ainsi facilement convertir un nombre réel de la base 2 vers la base 10. Par exemple : 

110,101 = 1.22 + 1.21 + 0.20 + 1.2−1 + 0.2−2 + 1.2−3 = 4 + 2 + 0,5 + 0,125 = 6,625 

### **5.2. Conversion<a name="_page12_x40.00_y167.92"></a> de décimal en binaire** 

Le passage de base 10 en base 2 est plus subtil. Par exemple : convertissons 1234,347 en base 2. 

1. La partie entière se transforme comme précédemment : 123410 = 100110100102 
1. On transforme la partie décimale selon le schéma suivant : ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)

Première NSI   Chap 13 : Codage de l’information  Page 13/21 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)

0,347 x 2 = 0,694 0,694 x 2 = 1,388 0,388 x 2 = 0,766 0,766 x 2 = 1,552 0,552 x 2 = 1,104 0,104 x 2 = 0,208 0,208 x 2 = 0,416 0,416 x 2 = 0,832 0,832 x 2 = 1,664 0,664 x 2 = 1,328 

0,347 =>0,0... 

0,347 => 0,01... 

0,347 => 0,010... 

0,347 => 0,0101... 

0\.347 => 0,01011... 0,347 => 0,010110... 0,347 => 0,0101100... 0,347 => 0,01011000... 0,347 => 0,010110001... 0,347 => 0,0101100011... 

Première NSI   Chap 21 : Codage de l’information  Page 21/21 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)

On continue ainsi jusqu'à la précision désirée..

Attention ! Un nombre à développement décimal fini en base 10 ne l'est pas forcément en base 2. Cela peut engendrer de mauvaises surprises. 

Le 25 février 1991, pendant la Guerre du Golfe, une batterie américaine de missiles Patriot, à Dharan ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.084.png)(Arabie  Saoudite),  a  échoué  dans  l'interception  d'un  missile  Scud  irakien.  Le  Scud  a  frappé  un baraquement de l'armée américaine et a tué 28 soldats. La commission d'enquête a conclu à un calcul incorrect du temps de parcours, dû à un problème d'arrondi. Les nombres étaient représentés en virgule fixe sur 24 bits. Le temps était compté par l'horloge interne du système en dixième de seconde. Malheureusement, 1/10 n'a pas d'écriture finie dans le système binaire : 1/10 = 0,1 (dans le système décimal)  =  0,0001100110011001100110011...  (dans  le  système  binaire).  L'ordinateur  de  bord arrondissait 1/10 à 24 chiffres, d'où une petite erreur dans le décompte du temps pour chaque 1/10 de seconde. Au moment de l'attaque, la batterie de missile Patriot était allumée depuis environ 100 heures, ce qui a entraîné une accumulation des erreurs d'arrondi de 0,34 s. Pendant ce temps, un missile Scud parcourt environ 500 m, ce qui explique que le Patriot soit passé à côté de sa cible. 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.085.png)

### **5.3. Représentation<a name="_page13_x40.00_y36.92"></a> des flottants dans un ordinateur** 

Il est parfois nécessaire d’approximer la valeur à représenter. ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.086.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.087.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.088.png)

Règles de base : 

- Il ne faut jamais tester une égalité entre deux nombres flottants mais utiliser une marge d’erreur relative.  
- Il ne faut pas se fier à l’affichage de Python qui n’affiche pas toutes les décimales stockées du nombre flottant. 



**Activité n° 5.**:  
 - 
<p>>>> 0.1 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.089.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.090.png)</p><p>0\.1 </p><p>>>> 0.2 </p><p>0\.2 </p><p>>>> 0.1 + 0.2 0.30000000000000004 >>> 0.1 + 0.2 == 0.3 False </p>

La norme IEEE[^2] 754 est la norme la plus employée pour la représentation des nombres à virgule flottante dans le domaine informatique. Il existe deux formats de codage :  

- le format dit "simple précision" et le format dit "double précision".  
- Le format "simple précision" utilise 32 bits pour écrire un nombre flottant alors que le format "double précision" utilise 64 bits.  

Sur 32 bits (ou 64), on utilise : ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.091.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.092.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.093.png)

- 1bit pour le signe,  
- 8 (ou 11) pour l’exposant  
- 23 bits (ou 52 bits) pour la mantisse. 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.094.jpeg)

Conditions à respecter : 

- l'exposant 00000000 est interdit. 
- l'exposant 11111111 est interdit. On s'en sert toutefois pour signaler des erreurs, on appelle alors cette configuration du nombre NaN, ce qui signifie « Not a number ». 
- il faut commencer par écrire le nombre sous la forme : 1,XXXXX.2exposant. La partie « XXXXX » constitue la mantisse.  
- Pour le format simple précision, 8 bits sont consacrés à l’exposant, il est donc possible de représenter 256 valeurs : soit les exposants compris entre (-126)10 et (+127)10 c’est-à-dire 126 valeurs négatives + le zéro + 127 valeurs positives (-127 et +128 sont des valeurs réservées). 
- Pour avoir des valeurs uniquement positives, il va falloir procéder à un décalage : ajouter systématiquement 127 à la valeur de l’exposant.  

Exemple : -10,125 au format simple précision 

1ère étape : conversion en binaire du nombre relatif 

- 1010 = 10102 
- 0,12510
- 0,125 x 2 = 0,250 
- 0,250 x 2 = 0,50 
- 0,50 x 2 = 1 + 0 (arrêt) 

0,12510 =  0,0012  

10,12510 = 1010,0012 

2ème étape : utilisation de la norme IEEE 754 

- Le bit de signe est 1 (nombre négatif) 
- On décale la virgule de trois rangs vers la gauche 1010,001 = 1,010001.23
- On ajoute 127 à la valeur de l’exposant 1,010001.2130
- L’exposant est 13010 = 100000102 
- La mantisse 010001 doit comporter 23 bits => on rajoute des zéros pour arriver à 23 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.095.jpeg)

En convertissant en hexadécimal : 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.096.jpeg)

[https://www.h-schmidt.net/FloatConverter/IEEE754.html ](https://www.h-schmidt.net/FloatConverter/IEEE754.html) 

## **6.  Exercices<a name="_page15_x40.00_y36.92"></a>** 

**Exercice 7** convertir en base 10  **Exercice 8 :** Convertir en binaire puis en norme IEEE-754 

1. 0,01010101012  1.  5,1875 
1. 11100,100012  2.  4,3125 

   3. 0,3125 

**Exercice 9** : **conversion des flottants** 

On souhaite transformer un nombre binaire décimal en base 10. Pour simplifier, on va déjà écrire un programme qui transforme la partie décimale en binaire, puis dans un deuxième temps on transformera la partie entière. 

**PARTIE I  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.097.png)**

1. ★ Écrire un programme bin2float.py qui convertisse la partie décimale d’un nombre binaire en flottant. 

**Aide** : on pourra utiliser la méthode split() de l’objet str pour récupérer la partie décimale. On utilisera le séparateur ','. Attention ce n’est pas une méthode en place donc il faut la réaffecter :[ https://www.w3schools.com/python/ref_string_split.asp ](https://www.w3schools.com/python/ref_string_split.asp)

2. ★ Transformer 0,0101010101 2 et 11100,10001 2 en base 10. 

**Aide** : print(bin2float(nombre)) 

3. ★ Modifier le programme précédent pour créer une fonction avec le prototype suivant : 

decimale(nom\_variable\_a\_changer : str) -> float
 -  :-  :-  :- 
<p>￿ </p><p>binaire : chaine binaire de la partie décimal</p>e 

- la fonction doit renvoyer le nombre flottant correspondant 
4. ★ Ajouter une fonction qui convertisse en base 10 la partie entière du binaire. Le prototype est le suivant : 

entiere(nom\_variable\_a\_changer : str) -> int
 -  :-  :-  :- 
5\.  ★ Enchaîner les appels successifs pour transformer un nombre binaire décimal en base 10. On utilisera une fonction

avec le prototype suivant : 

bin2float(nombre : str) -> float
 -  :-  :-  :- 
**PARTIE II** 
On souhaite maintenant réaliser l’opération inverse et transformer un flottant en binaire. Pour cela, on va encore séparer le problème en deux sous problèmes : d’abord transformer la partie décimale, puis terminer avec la partie entière. ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.098.png)

6. ★ Écrire un programme float2bin qui convertisse la partie décimale d’un nombre flottant en binaire. On donne 

l’algorithme : ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.099.png)

algorithme float2bin 

{ converti un nombre décimal < 1 en binaire } 

variables 

precision : entier := 16 

decimal : réel := 0.347 

binaire : chaine[16] := "" 

i : entier := 0 

début 

tantque decimal <> 0 ET i < precision faire 

`      `decimal := decimal \* 2 

`      `si decimal < 1 alors 

`            `binaire := binaire + "0" 

`      `sinon 

`            `binaire := binaire + "1" 

`             `decimal := decimal modulo 1 

`             `i := i + 1 

fin 

decimal <> 0 signifie différent de 0 

7. Donner la signification de l’instruction : decimal := decimal modulo 1 
7. Tester le programme. Résultat attendu : 0101100011010100. 
7. ★ Modifier le programme précédent pour créer une fonction avec le prototype suivant : 

bin\_decimal(decimal : float, precision : int) -> str
 -  :-  :-  :- 
<p>- décimal : partie décimale du nombre flottant </p><p>- precision : précision souhaité dans le calcul </p><p>- la fonction doit renvoyer la chaîne binaire corresp</p>ondante 

10. Transformer 0,5625 et 0,15 en base 2. 
10. ★★Ajouter une fonction qui convertisse en base 2 la partie entière du nombre flottant. Le prototype est le suivant : bin\_entiere(entier :int) -> str 

**Aide** : on pourra utiliser la fonction float(),  int() et le modulo 1 

12. ★★ Enchaîner les appels successifs pour transformer un nombre binaire décimal en base 10. On utilisera une fonction avec le prototype suivant : 

float2bin(nombre : str) -> str
 -  :-  :-  :- 
13\. Transformer 12,9 en base 2.
14\. ★ Créer un docstring pour chacune des fonctions du programme float2bin. ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.100.png)

## **7.  Codage des caractères<a name="_page16_x40.00_y36.92"></a>** 

### **7.1. Le<a name="_page16_x40.00_y58.92"></a> code ASCII**[^3]** 

La norme ASCII[^4] (on prononce généralement « aski ») établit une correspondance entre une représentation binaire des caractères de l'alphabet latin et les symboles, les signes, qui constituent cet alphabet.  

Par exemple, le caractère a est associé à 1100001 (97) et A à 1000001 (65).  

La norme ASCII permet ainsi à toutes sortes de machines de stocker, analyser et communiquer de l'information textuelle. En particulier, la quasi-totalité des ordinateurs personnels et des stations de travail utilisent l'encodage ASCII. Le code ASCII de base représentait les caractères sur 7 bits (c'est- à-dire 128 caractères possibles, de 0 à 127). 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.101.jpeg)

1. L’œuvre complète de Shakespeare tient sur 5 615 776 caractères (lettres et signes de ponctuation et ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.102.png)d’espacement). À raison d’un octet pour représenter un caractère, cela fait donc environ 5,6 mégaoctets ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.103.png)(5,6 Mo) de texte brut. 
1. Une photo de résolution moyenne (4:3 8 mégapixel, 3264x2448) prise par un smartphone fait 19,5 kilo- octets (19,5 ko) une fois compressée. 
1. La Joconde en haute définition (HD) sur une image de 7 479 × 11 146 pixels pour une taille de fichier de 89,94 mégaoctets (89,94 Mo). 
1. Une minute de vidéo sur YouTube de qualité web pour smartphone, fait 3,1 méga-octets (3 Mo) 

**Activité n° 6.**: **Python et la table ascii** Les fonctions chr et ord permettent d’accéder à la table ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.104.png)

\>>> chr(65) # caractère 65 (décimal) ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.105.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.040.png)

'A' 

\>>> ord('A') # numéro décimal du caractère 65 

### **7.2. Les<a name="_page16_x40.00_y611.92"></a> encodages ISO-latin** 

Dans les années 1990, pour satisfaire les besoins des pays européens, ont été définis plusieurs encodages alternatifs, connus sous le nom de ISO-latin, ou encore ISO-8859.  

Idéalement, on aurait pu et certainement dû définir un seul encodage pour représenter tous les nouveaux caractères; mais entre toutes les langues européennes, le nombre de caractères à ajouter était substantiel, et cet encodage unifié aurait largement dépassé 256 caractères différents, il n'aurait donc pas été possible de tout faire tenir sur un octet. Mais on a préféré préserver la "bonne propriété" du modèle un **caractère = un octet**, ceci afin de préserver le code existant qui aurait sinon dû être retouché ou récrit. 

Dès lors il n'y avait pas d'autre choix que de définir plusieurs encodages distincts; par exemple pour le **français** on a utilisé à l'époque **ISO-latin-1**; pour le russe ISO-latin-5. 

### **7.3. Unicode<a name="_page17_x40.00_y54.92"></a>** 

Il existe d'autres normes que l'ASCII, comme l'Unicode par exemple, qui présentent l'avantage de proposer une version unifiée des différents encodages de caractères complétant l'ASCII mais aussi de permettre l'encodage de caractères autres que ceux de l'alphabet latin. Unicode définit des dizaines de milliers de codes, mais les 128 premiers restent compatibles avec ASCII. 

Dans le codage UTF-8, chaque point de code est codé sur une suite d'un à quatre octets. Il a été conçu pour être compatible avec certains logiciels originellement prévus pour traiter des caractères d'un seul octet. ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.106.jpeg)

Toutes  ces  normes  différentes  et  leurs  incompatibilités partielles sont la cause des problèmes que l'on rencontre parfois  avec  les  caractères  accentués.  C'est  pour  cette raison  qu'il  vaut  mieux,  quand  on  écrit  des  courriels  à l'étranger, n'utiliser que des caractères non accentués. 

**Martine écrit en UTF-8** :  

- La lettre é a été encodée en **UTF-8** (parce que 2 caractères sont affichés) 
- En mémoire elle occupe 2 octets (elle n’est pas dans la table ascii) 
- Ces deux octets ont été décodés en iso-latin1 (1 octet par caractère). 

## **8. Représentation<a name="_page17_x40.00_y448.92"></a> des images**

Une image peut être vue comme un quadrillage  rempli d'une multitude de petits cases appelées  pixels.  

Chaque pixel est un carré d'une couleur définie.  Cette  couleur  se  code  à  l'aide  d'une  combinaison de trois couleurs de base : rouge,  vert  et  bleu  (Red,  Green,  Blue  en  anglais  -  souvent  abrégé  en  RGB).  Chacune  des  trois  couleurs étant codée sur 8 bits, soit entre 0 et  255.  

Ainsi, le pixel grisé désigné sur la photo est codé comme la  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.108.png)combinaison de 174 de rouge (Red), 181 de vert (Green) et  190 de bleu (Blue). Chacun de ces trois nombres étant codé  sur 8 bits, il faut 3x8=24 bits au total pour coder un pixel.  En codant ainsi chaque pixel de l'image originale, on peut  ainsi traduire une image en série de bit. Et inversement, on  peut  reconstituer  une  image  à  partir  d'une  série  de  bits  donnée.  

## **9. Exercices<a name="_page18_x40.00_y36.92"></a>** 

**Exercice 10 :** Image matricielle 

L’objectif de cet exercice est de dessiner une image matricielle dans le quadrillage 8x8 en page 1, ci-dessous, grâce à vos réponses aux différentes questions de conversions entre les bases numériques. 

Chaque case de l’image correspond à un bit. Une ligne de l’image fait 8 cases, soit 8 bits, soit 1 octet. Pour remplir les cases de l’image, vous devrez donc passer par la valeur binaire de la conversion afin de pouvoir appliquer cette règle de coloriage, même si la réponse n’aboutit pas à du binaire. Lorsque le bit est à 1 alors la case est noire, lorsque le bit est à 0 alors la case est blanche. 

Exemple : 



Ligne Valeur binaire correspondante Valeur décimale correspondante Valeur hexadécimale correspondante 
 -  :-  -  :-:  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :-  :- 
0b10010101 149 0x95 

Quadrillage pour l’image matricielle de 8x8 : 



Pour la question 1 
 :-  :-  :-  :-  :-  :-  :-  :-  - 
* *   Réponse à la question 2 
    Réponse à la question 3 
Pour la question 4 
  Réponse à la question 5 
    Réponse à la question 6 
Réponse à la question 7 
Réponse à la question 8 

**Traduire** la première ligne de l’image en valeur en binaire. 

1. **Convertir** la valeur binaire de la première ligne en décimal : 
1. **Convertir** la valeur hexadécimale 0x66 en binaire : 
1. **Convertir** la valeur hexadécimale 0x3C en décimal : 
1. **Convertir** la valeur binaire de la ligne N°4 en hexadécimal : 
1. **Convertir** la valeur décimale 24 en binaire : 
1. **Convertir** la valeur décimale 60 en hexadécimal : 
1. **Colorier** la ligne N°7 de l’image avec la valeur binaire suivante :  **0b01100110**
1. **Convertir** la valeur binaire 0b11111111 en hexadécimal : 

RAPPELS :   Un nombre binaire s’écrit ainsi : **1011(2)** ou **0b1011** ou **%1011** ou **1011b**

Un nombre hexadécimal s’écrit ainsi : **9A(16)** ou **0x9A** ou **$9A** ou **9Ah ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)**

Première NSI   Chap 20 : Codage de l’information  Page 20/21 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)

**Exercice 11** L’heure en binaire ????  ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.109.png)

Cette montre affiche l’heure en binaire :  

- une ligne affiche les minutes,  
- une autre ligne affiche les heures.  
1. Quelle est la valeur maximale en décimal que peut afficher la ligne  du haut ? en binaire ? en hexadécimal ?  
1. Quelle est la valeur maximale en décimal que peut afficher la ligne  du bas ? en binaire ? en hexadécimal ?  
1. En déduire quelle ligne indique les minutes et quelle ligne indique  les heures ?  
1. Dans quel format les heures sont-elles données au 12H (am/pm) ou  24H ?  
1. Quelle valeur maximale en décimal sera réellement affichée sur la  ligne des heures ? en binaire ? en hexadécimal ?  
1. Quelle valeur maximale en décimal sera réellement affichée sur la  ligne des minutes ? en binaire ? en hexadécimal ?  
1. Quelle est l’heure donnée par les montre ci-dessous ?  

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.110.png)

1  2  3 

8. Complétez les cadrans suivants dans le cas où la montre indique : 

![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.111.png)

1   2  3  4 

9. Quelle modification faudrait-il faire pour que les heures soient affichées sur un format 24h ? 
9. Quelle modification faudrait-il faire pour afficher également les secondes ? 
Première NSI   Chap 4 : Codage de l’information  Page 21/21 ![](Aspose.Words.764b7a7a-9a22-42aa-a7aa-fadf25e6a13d.031.png)

[^1]: [1https://physics.nist.gov/cuu/Units/binary.html ](https://physics.nist.gov/cuu/Units/binary.html)
[^2]: IEEE, que l'on peut prononcer « i3e » : Institute of Electrical and Electronics Engineers 
[^3]: American Standard Code for Information Interchange 
[^4]: inventé par Robert William Bemer en 1960 