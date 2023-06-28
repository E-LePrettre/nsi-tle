**Chap 04 : codage de l’information** 

<a name="_hlk38577387"></a>**Table des matières**

[1.	Vocabulaire	1](#_toc89276877)

[2.	Les bases courantes	2](#_toc89276878)

[2.1.	La base 10 ou base décimale	2](#_toc89276879)

[2.2.	La base 2 ou base binaire	2](#_toc89276880)

[2.2.1.	Le binaire	2](#_toc89276881)

[2.2.2.	Le binaire en Python	3](#_toc89276882)

[2.2.3.	Passage du système décimal au binaire	3](#_toc89276883)

[2.2.4.	Passage du système binaire au décimal	3](#_toc89276884)

[2.2.5.	Addition de deux nombres binaires	4](#_toc89276885)

[2.2.6.	Multiplication de deux nombres binaires	4](#_toc89276886)

[2.3.	La base 16 ou base hexadécimal	5](#_toc89276887)

[2.3.1.	L’hexadécimal	5](#_toc89276888)

[2.3.2.	Passage du système binaire au système hexadécimal et réciproquement	5](#_toc89276889)

[2.3.3.	Passage du système décimal au système hexadécimal	5](#_toc89276890)

[2.3.4.	Passage du système hexadécimal au décimal	5](#_toc89276891)

[2.3.5.	Addition de deux nombres en base 16	6](#_toc89276892)

[2.4.	Une base quelconque	6](#_toc89276893)

[3.	Le codage des nombres entiers signés en binaire	6](#_toc89276894)

[3.1.	Représentation avec la valeur absolue	7](#_toc89276895)

[3.2.	Principe du complément à 2<sup>n</sup> :	8](#_toc89276896)

[3.2.1.	De décimal vers binaire : Pour un entier positif	8](#_toc89276897)

[3.2.2.	De décimal vers binaire : Pour les entiers négatifs	8](#_toc89276898)

[3.2.3.	Addition de deux nombres binaires	8](#_toc89276899)

[3.2.4.	De binaire vers décimal : Pour les entiers négatifs	8](#_toc89276900)

[3.3.	Table de valeurs	9](#_toc89276901)

[4.	Exercices	10](#_toc89276902)

[5.	Représentation des nombres réels	13](#_toc89276903)

[5.1.	Conversion de binaire en décimal	13](#_toc89276904)

[5.2.	Conversion de décimal en binaire	13](#_toc89276905)

[5.3.	Représentation des flottants dans un ordinateur	14](#_toc89276906)

[6.	Exercices	16](#_toc89276907)

[7.	Codage des caractères	17](#_toc89276908)

[7.1.	Le code ASCII	17](#_toc89276909)

[7.2.	Les encodages ISO-latin	17](#_toc89276910)

[7.3.	Unicode	18](#_toc89276911)

[8.	Représentation des images	18](#_toc89276912)

[9.	Exercices	19](#_toc89276913)



1. <a name="_toc89276877"></a>**Vocabulaire**

La mémoire des ordinateurs est constituée d’une multitude de petits circuits électroniques qui ne peuvent être, chacun, que dans **deux états conventionnellement appelés 0 et 1**, (1, y'a du courant, 0, y'en a pas), mais on aurait pu tout aussi bien les appeler faux et vrai. 

0, ou 1 s’appelle : 

- un booléen, 
- ou un chiffre binaire 
- ou encore un bit (binary digit). 

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.001.png)

Un tel circuit à deux états s’appelle un **circuit mémoire un bit.** 

Toute l’information traitée par un ordinateur est en binaire. 

Le **bit** (b minuscule dans les notations) est la plus petite unité d'information manipulable par une machine numérique.

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.002.png)

Il est possible de représenter physiquement cette information binaire par un signal électrique ou magnétique, qui, au-delà d'un certain seuil, correspond à la valeur 1. 

L'**octet** (en anglais **byte** ou B majuscule dans les notations) est une unité d'information composée de **8 bits**. Il permet par exemple de stocker un caractère comme une lettre ou un chiffre.

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.003.png)

Une unité d'information composée de 16 bits est généralement appelée **mot** (en anglais word). Une unité d'information de 32 bits de longueur est appelée mot double (en anglais double word, d'où l'appellation dword).

Beaucoup d'informaticiens ont appris que 1 kilooctet valait 1024 octets. Or, depuis décembre1998, l'organisme international IEC a statué sur la question[^1].

Voici les unités standardisées :

- Un kilooctet (ko)	= 10<sup>3</sup> octets
- Un mégaoctet (Mo)	= 10<sup>6</sup> octets
- Un gigaoctet (Go)	= 10<sup>9</sup> octets
- Un téraoctet (To)	= 10<sup>12</sup> octets
- Un pétaoctet (Po)	= 10<sup>15</sup> octets
- Un exaoctet (Eo)	= 10<sup>18</sup> octets
- Un zettaoctet (Zo)	= 10<sup>21</sup> octets
- Un 1yottaoctet (Yo)	= 10<sup>24</sup> octets

Un mégaoctet devrait en principe valoir 1000 x 1000 octets, c'est-à- dire 1.000.000 d'octets, mais il vaut 1024 x 1024 octets en informatique, c'est-à-dire 1.048.576 octets... ce qui correspond à une différence de 4,63% !

1. <a name="_toc89276878"></a>**Les bases courantes**
   1. <a name="_toc89276879"></a>**La base 10 ou base décimale**

Elle s’appuie sur **10 « symboles »** : 0, 1, 2, 3, 4, 5, 6, 7, 8, 9. On peut ainsi compter jusqu'à 9. Et si l'on veut aller au-delà de 9, il faut changer de rang. Cela signifie que si le rang des unités est plein, il faut passer à celui des dizaines, puis des centaines, milliers…

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.004.png)

185=1×102+8×101+5×100

**La position des chiffres définit la valeur associée à ce chiffre.**

1. <a name="_toc89276880"></a>**La base 2 ou base binaire**
   1. <a name="_toc89276881"></a>Le binaire

**Remarque** : Il faut toujours indiquer la base dans laquelle un nombre est exprimé (sauf, par usage et commodité, en base 10) : 1010<sub>2</sub> ou %1010. La base par défaut du code Python est la base 10.

Par exemple : 

|**Décimal**|0|1|2|3|4|5|6|7|8|9|10|
| - | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|Binaire|0000|0001|0010|0011|0100|0101|0110|0111|1000|1001|1010|

1. <a name="_toc14218091"></a><a name="_toc89276882"></a>Le binaire en Python

|<p>**Activité n°  AUTONUM  \* Arabic**** : La fonction bin de Python donne une chaîne de caractères représentant l’écriture binaire de l’entier passé en paramètre.</p><p>
\>>> bin(47)</p><p>
'0b101111'</p><p>
\>>> 0b101</p><p>
5</p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.005.png)</p>|
| - |

En Python on peut écrire les nombres entiers directement en binaire. Il suffit pour cela de faire précéder cette écriture par 0b***.*** 

1. ![10 types of people](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.006.png)<a name="_toc89276883"></a><a name="_toc14218092"></a>Passage du système décimal au binaire 

**Méthode de Horner :** 

*Sens de lecture*

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.007.png)Exemple : Convertir 145 en binaire

- 145=72×2+1
- 72=36×2+0
- 36=18×2+0
- 18=9×2+0
- 9=4×2+1
- ![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.008.png)4=2×2+0
- 2=1×2+0
- 1=0×2+1

La conversion de 145 en binaire est donc : 10010001<sub>2</sub>

**Méthode des puissances de 2** :
|**Exposant** n|**0**|**1**|**2**|**3**|**4**|**5**|**6**|**7**|**8**|**9**|**10**|**11**|**12**|**13**|**14**|
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|2<sup>n</sup>|1|2|4|8|16|32|64|128|256|512|1024|2048|4096|8192|16384|


![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.009.png) 

Écrire 57 en base 2 (=donner sa représentation binaire).

- 32 < 57 < 64. Donc on fait 57 = 32+25 = 2<sup>5</sup>+25. On a un chiffre 1 à la position 6.
- 16 < 25 < 32. Donc on fait 25 = 16+9 = 2<sup>4</sup>+9. On a un chiffre 1 à la position 5.
- 8 < 9 < 16. Donc on fait 9=8+1=2<sup>3</sup>+1. On a un chiffre 1 à la position 4.
- 1=2<sup>0</sup>. On peut s’arrêter (dès qu’on atteint une puissance de 2). On a un chiffre 1 à la position 1.

![divisions successives](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.010.png)57 = 0b111001


**L’algorithme des divisions successives**

- On divise par 2 jusqu'à ce que le quotient soit 0
- On lit les bits en montant de droite à gauche : 167 = 0b10100111



1. <a name="_toc89276884"></a>Passage du système binaire au décimal

Les nombres écrits en binaire suivent le même principe que ceux écrits en décimal mais avec les** puissances de deux.

Le mot de 8 bits %01101110 =  1.2<sup>6</sup> +  1.2<sup>5</sup> +  1.2<sup>3</sup> +  1.2<sup>2</sup> +  1.2<sup>1</sup> en décimale.

|**Puissances**|2<sup>7</sup>|2<sup>6</sup>|2<sup>5</sup>|2<sup>4</sup>|2<sup>3</sup>|2<sup>2</sup>|2<sup>1</sup>|2<sup>0</sup>|
| - | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|**Valeurs en décimale**|128|64|32|16|8|4|2|1|
|**exemple**|0|1|1|0|1|1|1|0|
|**Valeur en décimale correspondante**|64 + 32 + 8 + 4 + 2 = 110||||||||

Donc, quand on a un nombre binaire, **il suffit de multiplier chaque nombre qui le compose par la puissance de 2 correspondante au rang de son bit et d’additionner tous les résultats.**

|<p>**Activité n°  AUTONUM  \* Arabic**** : La fonction int de Python donne une chaîne de caractères représentant l’écriture décimal d’un entier passé en paramètre.</p><p>
\>>> int('01101110', 2)</p><p>
110</p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.011.png)</p><p>On retrouve bien la valeur 110 précédente.</p>|
| - |

1. <a name="_toc89276885"></a>Addition de deux nombres binaires

On procède comme avec les nombre écrit en décimal, sauf que 1 + 1 = 10.

Exemple : 

|Retenues||1||||1|1||
| - | - | - | - | - | - | - | - | - |
|a||1|1|0|1|0|1|1|
|b|+||1|1|0|0|1|1|
|a + b =|1|0|0|1|1|1|1|0|

On remarque que la somme de deux nombres binaires sur m bits et n bits donne un nombre binaire sur le plus grand nombre de bits **(m ou n) + 1 au maximum**.

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.012.png)

1. <a name="_toc89276886"></a>Multiplication de deux nombres binaires

Exemple : 

||||||||||
| - | - | - | - | - | - | - | - | - |
|a||1|1|0|1|0|1|1|
|b|\*||||||1|1|
|Retenues|1|1|1|1|1|1|||
|||1|1|0|1|0|1|1|
|   |1|1|0|1|0|1|1||
|a \* b =   1|0|1|0|0|0|0|0|1|

On remarque que le produit de deux nombres binaires sur m bits et n bits donne un nombre binaire sur **m + n bits au maximum.**
![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.013.png)

1. <a name="_toc14218094"></a><a name="_toc89276887"></a>**La base 16 ou base hexadécimal**
   1. <a name="_toc14218095"></a><a name="_toc89276888"></a>L’hexadécimal

En informatique, tout est basé sur le binaire, et étant une base d'indice 2, c'est plus aisé d'encoder les informations sur un nombre multiple de 2. On utilise donc souvent la base 16, appelé **système hexadécimal** 

|**Hexa**|**0**|**1**|**2**|**3**|**4**|**5**|**6**|**7**|**8**|**9**|**A**|**B**|**C**|**D**|**E**|**F**|
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|Décimal|0|1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|

**Remarque** : Il faut toujours indiquer la base dans laquelle un nombre est exprimé (sauf, par usage et commodité, en base 10) : A9<sub>16</sub> ou $A9 ou #A9. La base par défaut du code Python est la base 10.

1. <a name="_toc14218096"></a><a name="_toc89276889"></a>Passage du système binaire au système hexadécimal et réciproquement

<a name="_hlk13783787"></a>Pour convertir un nombre binaire en base 16, **on regroupe les bits 4 à 4**, chaque groupe donnant un chiffre hexadécimal. À l'inverse, passer d'un nombre hexadécimal à sa représentation binaire se fait en remplaçant chaque chiffre pour son équivalent sur 4 bits. 

Si le nombre binaire de départ n'a pas un nombre de bits multiple de 4, **il faut ajouter des zéros en tête** (ce qui ne change pas sa valeur) afin de pouvoir les regrouper 4 par 4. 

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.014.png)

110110012=1101 10012=D916, 

7F16=0111 11112=011111112. 

À noter que la chaîne de caractères, avec Python, débute par*** 0x, le x mettant en évidence qu’il s’agit de l’écriture décimal d’un entier.

1. <a name="_toc14218097"></a><a name="_toc89276890"></a>Passage du système décimal au système hexadécimal 

**Méthode de Horner** : Pour convertir un nombre binaire en base 16, on regroupe les bits 4 à 4, chaque groupe donnant un chiffre hexadécimal. 

*Sens de lecture*

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.015.png)Exemple : Convertir 185 en hexadécimal

- 185=11×16+9
- 11=0×16+11

La conversion de 185 en hexadécimal est donc : B9.

**L’algorithme des divisions successives :** comme pour le binaire

|<p>**Activité n°  AUTONUM  \* Arabic**** : La fonction hex de Python donne une chaîne de caractères représentant l’écriture binaire de l’entier passé en paramètre.</p><p>
\>>> hex(185)</p><p>
'0xb9'</p><p>
\>>> 0x7F</p><p>
127</p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.016.png)</p>|
| - |

1. <a name="_toc89276891"></a>Passage du système hexadécimal au décimal

Il faut remplacer les lettres par les nombres correspondants :

- un A, on le remplace par un 10
- un C, on le remplace par un 12
- un D, on le remplace par un 13
- un E, on le remplace par un 14
- un F, on le remplace par un 15

Le principe est le même que pour la conversation "binaire en décimal" 

Par exemple :

12B716=1×163+2×162+11×161+7×160=1×4096+2×256+11×16+7=4791.

|<p>**Activité n°  AUTONUM  \* Arabic**** : La fonction int de Python donne une chaîne de caractères représentant l’écriture décimal d’un entier passé en paramètre.</p><p>
\>>> int('12B7', 16)</p><p>
4791</p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.017.png)</p>|
| - |

1. <a name="_toc89276892"></a><a name="_toc14218098"></a>Addition de deux nombres en base 16

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.018.png)

8<sub>16</sub> + 9<sub>16</sub> = une seizaine et un

C’est-à-dire on pose 1 et on retient le 1 de la seizaine

















Ce nombre 151 en hexadécimal se lirait donc "une seizaine-carré cinq seizaines et un".

D'ou le calcul en base 10 : 1x16x16 + 5x16 + 1 = 256 + 80 + 1 soit  337 en base 10

Ainsi le nombre 151 exprimé en hexadécimal est le même nombre que 337 en base 10

On pouvait aussi convertir les deux nombres en binaire et faire leur addition.

Ce nombre 151 en hexadécimal se lirait donc "une seizaine-carré cinq seizaines et un".

D'ou le calcul en base 10 : 1x16x16 + 5x16 + 1 = 256 + 80 + 1 soit  337 en base 10

Ainsi le nombre 151 exprimé en hexadécimal est le même nombre que 337 en base 10.

1. <a name="_toc89276893"></a>**Une base quelconque**

Par exemple la représentation de base cinq de 58

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.019.png)

Donc, 58 objets se regroupent en 11 paquets et 3 unités, puis les 11 paquets se regroupent en 2 paquets de paquets et 1 paquet.

58 = 2 × 5² + 1× 5<sup>1</sup> +3 × 5<sup>0</sup>. Donc 58 = 213<sub>5.</sub>

1. <a name="_toc14218099"></a><a name="_toc89276894"></a>**Le codage des nombres entiers signés en binaire**

Un entier naturel est appelé **entiers non signés.** En Python, on ne manipule que des **entiers relatifs.**

**Entiers naturels** : entiers positifs ou nuls (0, 1, 2 etc.)

**Entiers relatifs** : entiers de n’importe quel signe (…, -2, -1, 0, 1,…)

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.020.png)

1. <a name="_toc14218103"></a><a name="_toc14218104"></a><a name="_toc89276895"></a>**Représentation avec la valeur absolue**

ATTENTION 

MAUVAISE 

METHODE

Un entier relatif comporte **un signe** et **une valeur absolue (VA).** Par convention : **le bit de plus fort poids (le plus à gauche) représente le signe :**

- **0 = signe +**
- **1 = signe –**

Le bit de plus fort poids est aussi appelé **le MSB (Most Significant Bit)**

Les autres bits représentent **la valeur absolue** du nombre 

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.021.png)![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.022.png)

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.023.png)

Sur 8 bits, on a 2<sup>8</sup> - 1 nombres de l’intervalle : [-(2<sup>7</sup> - 1),  2<sup>7</sup>-1] soit  [-127, +127]

Sur n bits, on a 2<sup>n</sup> - 1 nombres de l’intervalle : [-(2<sup>n-1</sup> – 1), 2<sup>n-1</sup>-1] 

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.024.png)

**Contrainte immédiate** : il faut que la machine sache quelle est la taille du nombre !! on encodera dans tout le chapitre **sur 8 bits**

**Premier inconvénient de ce codage** : le zéro est codé de deux écritures : le zéro positif 00000000 et le zéro négatif 10000000

Testons avec 27 :

27 = 0b11011

On complète sur 8 bits :

27 = 0b 0001 1011

27 > 0 on garde le premier bit à 0

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.025.png)

Testons avec -9 :

La valeur absolue de -9 est 9.

9 = 0b1001

On complète sur 8 bits :

9 = 0b 0000 1001

-9 < 0 on remplace le premier bit par -1 :

-9 = 0b 1000 1001

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.026.png)

Testons avec 27 + (-9) = 18

0b 0001 1011

\+ 0b 1000 1001

\--------------

= 0b 1010 0100

… mais 0b 1010 0100 = 164

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.027.png)

Échec total ! **Le binaire signé ne permet pas de réaliser les additions habituelles**

1. <a name="_toc14218105"></a><a name="_toc89276896"></a>**Principe du complément à 2<sup>n</sup> :**
   1. <a name="_toc89276897"></a>De décimal vers binaire : Pour un entier positif
- coder l’entier en binaire comme d’habitude,
- compléter l’octet avec des 0 devant.

Exemple : pour 27 

- coder l'entier en binaire comme d'habitude : 27 = 0b11011
- compléter l'octet avec des 0 devant : 27 = 0b 0001 1011

Le complément à 2 sur un octet de 27 est 0b 0001 1011

1. <a name="_toc89276898"></a>De décimal vers binaire : Pour les entiers négatifs
- Coder la valeur absolue du nombre en base 2,
- compléter l’octet avec des 0 devant,
- échanger tous les bits (1↔0),
- ajouter 1.

Exemple pour -9 :

- coder la valeur absolue du nombre : 9 = 0b1001
- compléter l'octet : 	0b 0000 1001
- échanger tous les bits : 	0b 1111 0110
- ajouter 1 : 		0b 1111 0111

Le complément à 2 sur un octet de −9 est 0b 1111 0111

1. <a name="_toc89276899"></a>Addition de deux nombres binaires

Vérifions : 27+(−9)=18

`  `0001 1011

\+ 1111 0111

\-----------

= 0001 0010

On vérifie immédiatement que 18 = 0b10010

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.028.png)

**Remarque** la dernière retenue (tout à gauche) disparait.

1. <a name="_toc89276900"></a>De binaire vers décimal : Pour les entiers négatifs

Si l’entier est négatif (si premier bit est 1)

- On échange tous les bits 0↔1,
- On ajoute 1,
- On converti en binaire comme d’habitude,
- On change le signe.

Exemple : 0b 1111 0111

- On échange tous les bits,

0b 0000 1000

- On ajoute 1,

0b 0000 1001

- On convertit en binaire comme d'habitude,

0b 1001 = 1 \* 1 + 1 \* 8 = 9

- On change le signe.

0b 1111 0111 = -9

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.029.png)

1. <a name="_toc89276901"></a>**Table de valeurs**

bit

` `de

signe

`    `0 1 1 1 1 1 1 1 =  127 (à connaitre)

`    `0      ...      =  ...

`    `0 0 0 0 0 0 1 0 =    2

`    `0 0 0 0 0 0 0 1 =    1

`    `0 0 0 0 0 0 0 0 =    0

`    `1 1 1 1 1 1 1 1 =   -1

`    `1 1 1 1 1 1 1 0 =   -2

`    `1      ...      =  ...

`    `1 0 0 0 0 0 0 1 = -127

`    `1 0 0 0 0 0 0 0 = -128 (à connaitre)

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.030.png)

Le 4 juin 1996, une fusée Ariane 5 a explosé 40 secondes après l'allumage. La fusée et son chargement avaient coûté 500 millions de dollars. La commission d'enquête a rendu son rapport au bout de deux semaines. Il s'agissait d'une erreur de programmation dans le système inertiel de référence. À un moment donné, un nombre codé en virgule flottante sur 64 bits (qui représentait la vitesse horizontale de la fusée par rapport à la plate-forme de tir) était converti en un entier sur 16 bits. Malheureusement, le nombre en question était plus grand que 32768 (le plus grand entier que l'on peut coder sur 16 bits) et la conversion a été incorrecte.


![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.031.png)



1. <a name="_toc89276902"></a>**Exercices**

**Exercice 1 : ★** On suppose toujours nos entiers encodés sur un octet.

- Donner la représentation binaire 12, 100 et 88
- Réaliser l’addition binaire bit à bit de ces 3 nombres.

**Exercice 2 : ★** On suppose toujours nos entiers encodés sur un octet. Donner les compléments à 2 de -12, -100 et -88.

**Exercice 3 : ★**

- Réaliser l’addition binaire des compléments à 2 des nombres 12 et -100.
- Vérifier qu’on retrouve bien le résultat précédent pour -88.

**Exercice 4 : ★** Donner les notations décimales des binaires signés sur un octet suivant :

- 0b1111 1111
- 0b1000 0000
- 0b0111 1111
- 0b1010 0011

**Exercice 5 :<a name="__refheading___toc111327_1918782305"></a>** Conversion décimal – binaire

1. **★** Écrire un programme qui convertisse un nombre décimal en binaire. Utiliser une fonction dec2bin

On donne l’algorithme suivant :

Algorithme dec2bin

{ conversion décimal → binaire pour des entiers ≥ 0 }

variables

`	`nombre : entier

`	`binaire : tableau de [1..N] entiers

`	`mot	: chaine de caractère

début

`	`lire(nombre)

`	`fonction(nombre)

`		`binaire.ajout(nombre modulo 2)	{ ajout en fin de tableau }

`		`tantque nombre ≥ 2 faire

`			`nombre := nombre / 2

`			`binaire.ajout(nombre modulo 2)

`		`tantque longueur(binaire)<7

`			`binaire.ajout(0)

`		`binaire.renversée

`		`mot := chaine de caractère correspondant à binaire

`	`afficher(mot)

fin

**Aide :** 

- la méthode renversée avec reverse() <https://www.geeksforgeeks.org/python-list-reverse/> ou avec slicing inverse : binaire[::-1]
- pour transformer la liste en chaine de caractère : mot=''.join(str(element) for element in binaire)

Tout au début du programme, ne pas oublier cette ligne : # coding: utf-8

1. Indiquer l’utilité de cette ligne.
1. Donner la conversion de 1843 en binaire[^2].
1. Convertir -2 et conclure.
1. **★★★** Modifier le programme pour coder un nombre négatif selon la méthode du complément à 2.

**Aide :**

- Le complément à 2 peut être calculer par une autre méthode : Sur 8 bits, -88 en complément à 2 correspond au nombre binaire suivant :
  - 2<sup>7</sup> – 88 = 40
  - 40 en binaire => 010 1000

Le bit de signe donne donc 1010 1000

- Faire une deuxième fonction dec2bin\_negatif qui teste si le nombre entré est positif ou négatif et qui fait appel à la première fonction codée
1. Convertir -1 pour un codage sur un mot et conclure.
1. Convertir -1.1 et conclure.

Pour éviter que le programme « crash » sur une erreur de valeur d’entrée (ValueError), une façon de gérer cette erreur est d’intercepter le message d’erreur et de le traiter correctement à l’aide des instructions try et except.

La syntaxe est la suivante :

try:

`	`# bloc d’instructions à exécuter

except ValueError:

`	`# afficher « erreur de valeur »

1. **★★** Modifier le programme précédent en conséquence.
1. **★★**Faire une boucle infinie pour que le programme demande un autre nombre tant que la valeur n’est pas un entier relatif
1. Vérifier la cohérence et la stabilité du programme avec quelques tests : 1, -1, 0, 1.1, -1.0, a

**Exercice 6 :<a name="__refheading___toc111329_1918782305"></a>** Conversion hexadécimal – binaire

1. **★★★** Écrire un programme hex2dec qui convertisse un nombre hexadécimal en décimal non signé.

**Aide :** 

- On utilisera une chaîne : chaine = "0123456789ABCDEF".
- Et on pourra utiliser la méthode index() <https://www.geeksforgeeks.org/python-list-index/>
1. Donner les conversions de 1, A, a et A5 en décimal.
1. Donner la conversion de AZ et conclure.
1. Modifier votre programme comme précédemment pour gérer des erreurs éventuelles (bugs).

NB : on affichera « valeur héxadécimale incorrecte »

On souhaite réutiliser le code de programme dec2bin pour écrire un programme hex2bin qui convertisse un nombre hexadécimal en binaire. Pour cela, il « suffit » de récupérer la valeur obtenue par hex2dec et la passer à dec2bin.

**On prototype** une fonction en indiquant son nom, le type des éventuels paramètres et de la valeur renvoyée le cas échéant.

Exemple pour une fonction qui calcule le carré d’un nombre et renvoie la valeur trouvée :

def carre(nombre : int) -> int:

`	`return nombre \*\* 2
![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.032.png)

1. Dans le programme hex2bin, faire un copier/coller du code du programme dec2bin.
1. **★★** Remodeler (refactor) le code pour le transformer en fonction dont le prototype sera le suivant :

dec2bin(nombre : int, nbits : int) -> list

- nombre est le nombre décimal à convertir
- nbits est le nombre de bits
- la fonction renvoie la conversion sous forme d’une liste binaire (au lieu de l’afficher)
1. Tester la fonction en l’appelant depuis le corps principal (main) du programme.

**Aide** : 

- Juste après la fonction : print(dec2bin(501, 10)) 
- vérifier que l’on obtient [0, 1, 1, 1, 1, 1, 0, 1, 0, 1]
1. A la suite de cette fonction, faire un copier/coller du code du programme hex2dec.
1. **★★** Remodeler (refactor) le code pour le transformer en fonction dont le prototype sera le suivant :

hex2dec(hexa : str) -> int

•	hexa est le nombre hexadécimal à convertir

•	la fonction renvoie la conversion sous forme d’un nombre décimal

1. Tester la fonction en l’appelant dans le corps principal (main) du programme.

**Aide** : 

- Juste après la fonction : print(hex2dec('AF'))
- vérifier que l’on obtient 175
1. **★★** Enchaîner les appels successifs pour afficher la valeur binaire sur 8 bits des nombres suivants : 1, A et A5.
1. Donner la conversion de AZ et conclure.

Traiter l’erreur en local a ses limites : il faut faire remonter l’erreur vers les couches supérieures. La dernière couche traitera en dernier l’erreur selon des spécifications bien précises.

1. **★★** Modifier les fonctions hex2dec et dec2bin pour qu’elles renvoient « None » au lieu d’afficher une erreur. 

Syntaxe :

try:

`	`# bloc d’instructions à exécuter

except :

`	`return None

NB : L'objet Python None, exprime l'absence de valeur. Cet objet n'a aucune méthode.

1. **★★** Modifier le corps principal du programme pour tester la valeur de retour sur chaque fonction appelée. En cas d’erreur (valeur None), afficher le message d’erreur .
1. Créer un docstring pour chacune des fonctions du programme hex2bin.

Syntaxe, par exemple :

def fonction (x : int, y : int) -> tuple:

`    `"""

`    `fonction qui …

`    `:param x: int

`    `:param y: int

`    `:return: tuple

`    `"""



Convertisseur en ligne : <https://www.exploringbinary.com/twos-complement-converter/>

QCM : <http://www.scientillula.net/MPI/fex6_conversions/fex6_conversions.html>

QCM 2 : <http://fabrice.sincere.free.fr/qcm/qcm.php?nom=qcm_numerique>



1. <a name="_toc89276903"></a>**Représentation des nombres réels**

En base 10, l’expression 652,375 est une manière abrégée d’écrire :

6\.102+5.101+2.100+3.10-1+7.10-2+5.10-3

Il en va de même pour la base 2. L’expression 110,101 signifie :

1\.22+1.21+0.20+1.2-1+0.2-2+1.2-3

1. <a name="_toc89276904"></a>**Conversion de binaire en décimal**

On peut ainsi facilement convertir un nombre réel de la base 2 vers la base 10. Par exemple :

110,101=1.22+1.21+0.20+1.2-1+0.2-2+1.2-3=4+2+0,5+0,125=6,625

1. <a name="_toc89276905"></a>**Conversion de décimal en binaire**

Le passage de base 10 en base 2 est plus subtil. Par exemple : convertissons 1234,347 en base 2.

1. La partie entière se transforme comme précédemment : 1234<sub>10</sub> = 10011010010<sub>2</sub>
1. On transforme la partie décimale selon le schéma suivant :

0,347 x 2 = 0,694		0,347 =>0,0...

0,694 x 2 = 1,388		0,347 => 0,01...

0,388 x 2 = 0,766		0,347 => 0,010...

0,766 x 2 = 1,552		0,347 => 0,0101...

0,552 x 2 = 1,104		0.347 => 0,01011...

0,104 x 2 = 0,208		0,347 => 0,010110...

0,208 x 2 = 0,416		0,347 => 0,0101100...

0,416 x 2 = 0,832		0,347 => 0,01011000...

0,832 x 2 = 1,664		0,347 => 0,010110001...

0,664 x 2 = 1,328		0,347 => 0,0101100011...

On continue ainsi jusqu'à la précision désirée..

Attention ! Un nombre à développement décimal fini en base 10 ne l'est pas forcément en base 2. Cela peut engendrer de mauvaises surprises.

Le 25 février 1991, pendant la Guerre du Golfe, une batterie américaine de missiles Patriot, à Dharan (Arabie Saoudite), a échoué dans l'interception d'un missile Scud irakien. Le Scud a frappé un baraquement de l'armée américaine et a tué 28 soldats. La commission d'enquête a conclu à un calcul incorrect du temps de parcours, dû à un problème d'arrondi. Les nombres étaient représentés en virgule fixe sur 24 bits. Le temps était compté par l'horloge interne du système en dixième de seconde. Malheureusement, 1/10 n'a pas d'écriture finie dans le système binaire : 1/10 = 0,1 (dans le système décimal) = 0,0001100110011001100110011... (dans le système binaire). L'ordinateur de bord arrondissait 1/10 à 24 chiffres, d'où une petite erreur dans le décompte du temps pour chaque 1/10 de seconde. Au moment de l'attaque, la batterie de missile Patriot était allumée depuis environ 100 heures, ce qui a entraîné une accumulation des erreurs d'arrondi de 0,34 s. Pendant ce temps, un missile Scud parcourt environ 500 m, ce qui explique que le Patriot soit passé à côté de sa cible.

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.033.png)

1. <a name="_toc89276906"></a>**Représentation des flottants dans un ordinateur**

Il est parfois nécessaire d’approximer la valeur à représenter.

Règles de base :

- Il ne faut jamais tester une égalité entre deux nombres flottants mais utiliser une marge d’erreur relative. 
- Il ne faut pas se fier à l’affichage de Python qui n’affiche pas toutes les décimales stockées du nombre flottant.

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.034.png)



|<p>**Activité n°  AUTONUM  \* Arabic**** : </p><p>
\>>> 0.1</p><p>
0\.1</p><p>
\>>> 0.2</p><p>
0\.2</p><p>
\>>> 0.1 + 0.2</p><p>
0\.30000000000000004</p><p>
\>>> 0.1 + 0.2 == 0.3</p><p>
False</p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.035.png)</p>|
| - |

La norme IEEE[^3] 754 est la norme la plus employée pour la représentation des nombres à virgule flottante dans le domaine informatique. Il existe deux formats de codage : 

- le format dit "simple précision" et le format dit "double précision". 
- Le format "simple précision" utilise 32 bits pour écrire un nombre flottant alors que le format "double précision" utilise 64 bits. 

Sur 32 bits (ou 64), on utilise :

- 1bit pour le signe, 
- 8 (ou 11) pour l’exposant 
- 23 bits (ou 52 bits) pour la mantisse.
![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.036.png)

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.037.png)

Conditions à respecter :

- l'exposant 00000000 est interdit.
- l'exposant 11111111 est interdit. On s'en sert toutefois pour signaler des erreurs, on appelle alors cette configuration du nombre NaN, ce qui signifie « Not a number ».
- il faut commencer par écrire le nombre sous la forme : 1,XXXXX.2<sup>exposant</sup>. La partie « XXXXX » constitue la mantisse. 
- Pour le format simple précision, 8 bits sont consacrés à l’exposant, il est donc possible de représenter 256 valeurs : soit les exposants compris entre (-126)<sub>10</sub> et (+127)<sub>10</sub> c’est-à-dire 126 valeurs négatives + le zéro + 127 valeurs positives (-127 et +128 sont des valeurs réservées).
- Pour avoir des valeurs uniquement positives, il va falloir procéder à un décalage : ajouter systématiquement 127 à la valeur de l’exposant. 

Exemple : -10,125 au format simple précision

1<sup>ère</sup> étape : conversion en binaire du nombre relatif

- 10<sub>10</sub> = 1010<sub>2</sub>
- 0,125<sub>10</sub> 
  - 0,125 x 2 = 0,250
  - 0,250 x 2 = 0,50
  - 0,50 x 2 = 1 + 0 (arrêt)

0,125<sub>10</sub> =  0,001<sub>2</sub> 

10,125<sub>10</sub> = 1010,001<sub>2</sub>

2<sup>ème</sup> étape : utilisation de la norme IEEE 754

- Le bit de signe est 1 (nombre négatif)
- On décale la virgule de trois rangs vers la gauche 1010,001 = 1,010001.2<sup>3</sup>
- On ajoute 127 à la valeur de l’exposant 1,010001.2<sup>130</sup> 
- L’exposant est 130<sub>10</sub> = 10000010<sub>2</sub>
- La mantisse 010001 doit comporter 23 bits => on rajoute des zéros pour arriver à 23

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.038.png)

En convertissant en hexadécimal :

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.039.png)

<https://www.h-schmidt.net/FloatConverter/IEEE754.html> 

1. <a name="_toc89276907"></a>**Exercices**

|<p>**Exercice 7** convertir en base 10</p><p>1. 0,0101010101<sub>2</sub></p><p>&emsp;2. 11100,10001<sub>2</sub></p>|<p>**Exercice 8 :** Convertir en binaire puis en norme IEEE-754</p><p>1. 5,1875</p><p>&emsp;2. 4,3125</p><p>&emsp;3. 0,3125</p>|
| - | - |

**Exercice 9** : **conversion des flottants**

On souhaite transformer un nombre binaire décimal en base 10. Pour simplifier, on va déjà écrire un programme qui transforme la partie décimale en binaire, puis dans un deuxième temps on transformera la partie entière.

**PARTIE I**

1. **★** Écrire un programme bin2float.py qui convertisse la partie décimale d’un nombre binaire en flottant.

**Aide** : on pourra utiliser la méthode split() de l’objet str pour récupérer la partie décimale. On utilisera le séparateur ','. Attention ce n’est pas une méthode en place donc il faut la réaffecter : <https://www.w3schools.com/python/ref_string_split.asp>

1. **★** Transformer 0,0101010101 <sub>2</sub> et 11100,10001 <sub>2</sub> en base 10.

**Aide** : print(bin2float(nombre))

1. **★** Modifier le programme précédent pour créer une fonction avec le prototype suivant :

decimale(nom\_variable\_a\_changer : str) -> float

- binaire : chaine binaire de la partie décimale
- la fonction doit renvoyer le nombre flottant correspondant
1. **★** Ajouter une fonction qui convertisse en base 10 la partie entière du binaire. Le prototype est le suivant :

entiere(nom\_variable\_a\_changer : str) -> int

1. **★** Enchaîner les appels successifs pour transformer un nombre binaire décimal en base 10. On utilisera une fonction avec le prototype suivant :

bin2float(nombre : str) -> float

**PARTIE II**

On souhaite maintenant réaliser l’opération inverse et transformer un flottant en binaire. Pour cela, on va encore séparer le problème en deux sous problèmes : d’abord transformer la partie décimale, puis terminer avec la partie entière.

1. **★** Écrire un programme float2bin qui convertisse la partie décimale d’un nombre flottant en binaire. On donne l’algorithme :

algorithme float2bin

{ converti un nombre décimal < 1 en binaire }

variables

precision : entier := 16

decimal : réel := 0.347

binaire : chaine[16] := ""

i : entier := 0

début

tantque decimal <> 0 ET i < precision faire

`      `decimal := decimal \* 2

`      `si decimal < 1 alors

`            `binaire := binaire + "0"

`      `sinon

`            `binaire := binaire + "1"

`             `decimal := decimal modulo 1

`             `i := i + 1

fin

decimal <> 0 signifie différent de 0

1. Donner la signification de l’instruction : decimal := decimal modulo 1
1. Tester le programme. Résultat attendu : 0101100011010100.
1. **★** Modifier le programme précédent pour créer une fonction avec le prototype suivant :

bin\_decimal(decimal : float, precision : int) -> str

- décimal : partie décimale du nombre flottant
- precision : précision souhaité dans le calcul
- la fonction doit renvoyer la chaîne binaire correspondante
1. Transformer 0,5625 et 0,15 en base 2.
1. **★★**Ajouter une fonction qui convertisse en base 2 la partie entière du nombre flottant. Le prototype est le suivant : bin\_entiere(entier :int) -> str

**Aide** : on pourra utiliser la fonction float(),  int() et le modulo 1

1. **★★** Enchaîner les appels successifs pour transformer un nombre binaire décimal en base 10. On utilisera une fonction avec le prototype suivant :

float2bin(nombre : str) -> str

1. Transformer 12,9 en base 2.
1. **★** Créer un docstring pour chacune des fonctions du programme float2bin.
1. <a name="_toc89276908"></a>**Codage des caractères**
   1. <a name="_toc89276909"></a>**Le code ASCII[^4]**

La norme ASCII[^5] (on prononce généralement « aski ») établit une correspondance entre une représentation binaire des caractères de l'alphabet latin et les symboles, les signes, qui constituent cet alphabet. 

Par exemple, le caractère a est associé à 1100001 (97) et A à 1000001 (65). 

La norme ASCII permet ainsi à toutes sortes de machines de stocker, analyser et communiquer de l'information textuelle. En particulier, la quasi-totalité des ordinateurs personnels et des stations de travail utilisent l'encodage ASCII. Le code ASCII de base représentait les caractères sur 7 bits (c'est- à-dire 128 caractères possibles, de 0 à 127).

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.040.png)

1. L’œuvre complète de Shakespeare tient sur 5 615 776 caractères (lettres et signes de ponctuation et d’espacement). À raison d’un octet pour représenter un caractère, cela fait donc environ 5,6 mégaoctets (5,6 Mo) de texte brut.
1. Une photo de résolution moyenne (4:3 8 mégapixel, 3264x2448) prise par un smartphone fait 19,5 kilo-octets (19,5 ko) une fois compressée.
1. La Joconde en haute définition (HD) sur une image de 7 479 × 11 146 pixels pour une taille de fichier de 89,94 mégaoctets (89,94 Mo).
1. Une minute de vidéo sur YouTube de qualité web pour smartphone, fait 3,1 méga-octets (3 Mo)


|<p>**Activité n°  AUTONUM  \* Arabic**** : **Python et la table ascii** Les fonctions chr et ord permettent d’accéder à la table</p><p>
\>>> chr(65) # caractère 65 (décimal)</p><p>
'A'</p><p>
\>>> ord('A') # numéro décimal du caractère</p><p>
65</p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.041.png)</p>|
| - |

1. <a name="_toc89276910"></a>**Les encodages ISO-latin**

Dans les années 1990, pour satisfaire les besoins des pays européens, ont été définis plusieurs encodages alternatifs, connus sous le nom de ISO-latin, ou encore ISO-8859. 

Idéalement, on aurait pu et certainement dû définir un seul encodage pour représenter tous les nouveaux caractères; mais entre toutes les langues européennes, le nombre de caractères à ajouter était substantiel, et cet encodage unifié aurait largement dépassé 256 caractères différents, il n'aurait donc pas été possible de tout faire tenir sur un octet.

Mais on a préféré préserver la "bonne propriété" du modèle un **caractère = un octet**, ceci afin de préserver le code existant qui aurait sinon dû être retouché ou récrit.

Dès lors il n'y avait pas d'autre choix que de définir plusieurs encodages distincts; par exemple pour le **français** on a utilisé à l'époque **ISO-latin-1**; pour le russe ISO-latin-5.

1. <a name="_toc89276911"></a>**Unicode**

Il existe d'autres normes que l'ASCII, comme l'Unicode par exemple, qui présentent l'avantage de proposer une version unifiée des différents encodages de caractères complétant l'ASCII mais aussi de permettre l'encodage de caractères autres que ceux de l'alphabet latin. Unicode définit des dizaines de milliers de codes, mais les 128 premiers restent compatibles avec ASCII.

![martine](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.042.jpeg)

Dans le codage UTF-8, chaque point de code est codé sur une suite d'un à quatre octets. Il a été conçu pour être compatible avec certains logiciels originellement prévus pour traiter des caractères d'un seul octet.

Toutes ces normes différentes et leurs incompatibilités partielles sont la cause des problèmes que l'on rencontre parfois avec les caractères accentués. C'est pour cette raison qu'il vaut mieux, quand on écrit des courriels à l'étranger, n'utiliser que des caractères non accentués.

**Martine écrit en UTF-8** : 

- La lettre é a été encodée en **UTF-8** (parce que 2 caractères sont affichés)
- En mémoire elle occupe 2 octets (elle n’est pas dans la table ascii)
- Ces deux octets ont été décodés en iso-latin1 (1 octet par caractère).



1. ![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.043.png)<a name="_toc89276912"></a>**Représentation des images**

Une image peut être vue comme un quadrillage rempli d'une multitude de petits cases appelées pixels.

Chaque pixel est un carré d'une couleur définie. Cette couleur se code à l'aide d'une combinaison de trois couleurs de base : rouge, vert et bleu (Red, Green, Blue en anglais - souvent abrégé en RGB). Chacune des trois couleurs étant codée sur 8 bits, soit entre 0 et 255.

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.044.png)

Ainsi, le pixel grisé désigné sur la photo est codé comme la combinaison de 174 de rouge (Red), 181 de vert (Green) et 190 de bleu (Blue). Chacun de ces trois nombres étant codé sur 8 bits, il faut 3x8=24 bits au total pour coder un pixel. En codant ainsi chaque pixel de l'image originale, on peut ainsi traduire une image en série de bit. Et inversement, on peut reconstituer une image à partir d'une série de bits donnée.

1. <a name="_toc89276913"></a>**Exercices**

**Exercice 10 :** Image matricielle

L’objectif de cet exercice est de dessiner une image matricielle dans le quadrillage 8x8 en page 1, ci-dessous, grâce à vos réponses aux différentes questions de conversions entre les bases numériques.

Chaque case de l’image correspond à un bit. Une ligne de l’image fait 8 cases, soit 8 bits, soit 1 octet. Pour remplir les cases de l’image, vous devrez donc passer par la valeur binaire de la conversion afin de pouvoir appliquer cette règle de coloriage, même si la réponse n’aboutit pas à du binaire. Lorsque le bit est à 1 alors la case est noire, lorsque le bit est à 0 alors la case est blanche.

Exemple :

|Ligne|Valeur binaire correspondante|Valeur décimale correspondante|Valeur hexadécimale correspondante|
| :-: | :-: | :-: | :-: |
|||||

|||||||||
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |

||0b10010101|149|0x95|
| :-: | :-: | :-: | :-: |

Quadrillage pour l’image matricielle de 8x8 :

||||||<p></p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.045.png)</p>|||Pour la question 1|
| - | - | - | - | - | - | - | - | - |
|<p></p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.045.png)</p>|*00*|*000*|<p></p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.045.png)</p>||111|000||Réponse à la question 2|
|||00|00|<p></p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.045.png)00</p>|00|||Réponse à la question 3|
|||||||||Pour la question 4|
||||<p></p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.045.png)000</p>|00||||Réponse à la question 5|
|||<p></p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.045.png)0</p>|000|<p></p><p>![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.045.png)00</p>|00|||Réponse à la question 6|
|||||||||Réponse à la question 7|
|||||||||Réponse à la question 8|

**Traduire** la première ligne de l’image en valeur en binaire.

1. **Convertir** la valeur binaire de la première ligne en décimal :
1. **Convertir** la valeur hexadécimale 0x66 en binaire :
1. **Convertir** la valeur hexadécimale 0x3C en décimal :
1. **Convertir** la valeur binaire de la ligne N°4 en hexadécimal :
1. **Convertir** la valeur décimale 24 en binaire :
1. **Convertir** la valeur décimale 60 en hexadécimal :
1. ` `**Colorier** la ligne N°7 de l’image avec la valeur binaire suivante :  **0b01100110**
1. **Convertir** la valeur binaire 0b11111111 en hexadécimal :

RAPPELS : 	Un nombre binaire s’écrit ainsi : <b>1011<sub>(2)</sub></b> ou <b>0b1011</b> ou <b>%1011</b> ou <b>1011b</b>

Un nombre hexadécimal s’écrit ainsi : <b>9A<sub>(16)</sub></b> ou <b>0x9A</b> ou <b>$9A</b> ou <b>9Ah</b>

![Montre binaire The One](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.046.jpeg)**Exercice 11** L’heure en binaire ????

Cette montre affiche l’heure en binaire :

• une ligne affiche les minutes,

• une autre ligne affiche les heures.

1. Quelle est la valeur maximale en décimal que peut afficher la ligne du haut ? en binaire ? en hexadécimal ?
1. Quelle est la valeur maximale en décimal que peut afficher la ligne du bas ? en binaire ? en hexadécimal ?
1. En déduire quelle ligne indique les minutes et quelle ligne indique les heures ?
1. Dans quel format les heures sont-elles données au 12H (am/pm) ou 24H ?
1. Quelle valeur maximale en décimal sera réellement affichée sur la ligne des heures ? en binaire ? en hexadécimal ?
1. Quelle valeur maximale en décimal sera réellement affichée sur la ligne des minutes ? en binaire ? en hexadécimal ?
1. Quelle est l’heure donnée par les montre ci-dessous ?

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.047.png)

1					2					3

1. Complétez les cadrans suivants dans le cas où la montre indique :

![](Aspose.Words.954fe12f-58fd-4d51-83f3-9316ddb0bfe8.048.png)

1				2				3			4

1. Quelle modification faudrait-il faire pour que les heures soient affichées sur un format 24h ?
1. Quelle modification faudrait-il faire pour afficher également les secondes ?
Première NSI 	Chap 04 : Codage de l’information	Page 20/20

[^1]: <https://physics.nist.gov/cuu/Units/binary.html>
[^2]: 1843 est l’année de création du 1<sup>er</sup> programme informatique par Augusta Ada King, comtesse de Lovelace
[^3]: IEEE, que l'on peut prononcer « i3e » : Institute of Electrical and Electronics Engineers
[^4]: American Standard Code for Information Interchange
[^5]: inventé par Robert William Bemer en 1960