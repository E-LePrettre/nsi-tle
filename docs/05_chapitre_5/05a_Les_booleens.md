---
author: ELP
title: 05a Les booléens
---

**Table des matières** 

1. [L’algèbre de Boole ](#_page0_x40.00_y375.04)
2. [Les fonctions logiques et tables de vérité](#_page1_x40.00_y213.04)
3. [Quelques propriétés](#_page3_x40.00_y448.04)
4. [Exercices](#_page4_x40.00_y43.04)


## **<H2 STYLE="COLOR:BLUE;">1. L’algèbre<a name="_page0_x40.00_y375.04"></a> de Boole</h2>** 

L'algèbre de Boole, ou calcul booléen, est la partie des mathématiques qui s'intéresse aux opérations et aux fonctions sur les variables logiques. Elle fut inventée par le mathématicien britannique George Boole. Aujourd'hui, l'algèbre de Boole trouve de nombreuses applications en informatique et dans la conception des circuits électroniques. 

On appelle B l'ensemble constitué de deux éléments appelés valeurs de vérité {FAUX, VRAI}. Cet ensemble est aussi noté B = {0, 1}, notation que l'on utilisera désormais. Sur cet ensemble on peut définir les lois ET et OU et une transformation appelée « complémentaire » (parfois « inversion » ou « contraire »). 

### **<H3 STYLE="COLOR:GREEN;">1.1. ET<a name="_page0_x40.00_y473.04"></a></h3>** 

Elle est définie de la manière suivante : **a ET b est VRAI si et seulement si a est VRAI et b est VRAI.**

Cette loi est aussi notée : 

- a · b 
- a/\b (dans quelques notations algébriques, ou en APL[^1]) 
- a&b ou a&&b (Perl, C, PHP, ...) 
- a AND b (Ada, Pascal, Python, ...)

### **<H3 STYLE="COLOR:GREEN;">1.2. OU<a name="_page0_x40.00_y591.04"></a></h3>** 

Elle est définie de la manière suivante : **a OU b est VRAI si et seulement si a est VRAI ou b est VRAI, ou si a et b sont vrais.**

Cette loi est aussi notée : 

- a+b 
- a\/b (dans quelques notations algébriques ou en APL) 
- ab ou ab (Perl, C, PHP, ...) 
- a OR b (Ada, Pascal, Python, ...) 

### **<H3 STYLE="COLOR:GREEN;">1.3. NON<a name="_page1_x40.00_y43.04"></a></h3>** 

Le contraire de « a » est VRAI si et seulement si a est FAUX

Le contraire de a est noté : 

- a 
- ¬a 
- ~a (dans quelques notations algébriques ou en APL) 
- !a (C, C++...) 
- NOT a (ASM, Pascal, ...) 

## **<H2 STYLE="COLOR:BLUE;">2. Les<a name="_page1_x40.00_y213.04"></a> fonctions logiques et tables de vérité</h2>** 

A la base de la plupart des composants d’un ordinateur, on retrouve le **transistor**. Il a été inventé fin 1947 par les Américains  John  Bardeen,  William  Shockley  et  Walter  Brattain.  Les  premiers  ordinateurs  datent  de  1943  et fonctionnaient grâce à des tubes électroniques moins performant que les transistors. 

Les transistors sont regroupés dans des circuits intégrés : ils sont gravés sur des plaques de silicium ainsi que les connexions. Un transistor se comportent comme un interrupteur : le courant passe ou le courant ne passe pas. On parle d’un **état « haut »** symbolisé par **un 1** et d’un **état « bas »** symbolisé par **un 0.** 

Un transistor est l’élément de base des circuits logiques. Un circuit logique permet de réaliser une  **opération booléenne**. Ces opérations booléennes sont directement liées à l’algèbre de Boole (1815-1864). Un circuit logique prend en entrée un ou des signaux électriques (1 ou 0) et donne en sortie un ou des signaux électriques. Il existe deux catégories de circuit logique : 

- Les **circuits combinatoires** : les états en sortie dépendent uniquement des états en entrée 
- Les **circuits séquentiels** : les états en sortie dépendent des états en entrée ainsi que du temps et des états antérieurs 

### **<H3 STYLE="COLOR:GREEN;">2.1. La<a name="_page1_x40.00_y426.04"></a> porte NON (NOT)</h3>** 

La porte NON inverse l’état en entrée. Si l’entrée de la porte est dans un état « bas » on obtiendra en sortie un état « haut » et vice versa. On aura la **table de vérité** suivante : 



|E (Entrée) |S (Sortie)| 
| - | - | 
|1 |0 |
|0 |1 |

La porte NON est symbolisée par le schéma suivant : 

|Symbole |Autre symbole |Opération |
| - | - | - |
|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.010.png)|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.011.png)|![](Aimg0.png)|

### **<H3 STYLE="COLOR:GREEN;">2.2. La<a name="_page1_x40.00_y623.04"></a> porte OU (OR)</h3>** 

La porte OU a deux entrée E1 et E2 et une sortie S 



|E1 (Entrée) |E2 (Entrée) |S (Sortie) |
| - | - | - |
|0 |0 |0 |
|0 |1 |1 |
|1 |0 |1 |
|1 |1 |1 |

La porte OU est symbolisée par le schéma suivant : 

|Symbole |Autre symbole |Opération |
| - | - | - |
|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.012.png)|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.013.png)|E1 + E2 |

### **<H3 STYLE="COLOR:GREEN;">2.3. La<a name="_page2_x40.00_y162.04"></a> porte ET (AND)</h3>** 

La porte ET a deux entrée E1 et E2 et une sortie S 



|E1 (Entrée) |E2 (Entrée) |S (Sortie) |
| - | - | - |
|0 |0 |0 |
|0 |1 |0 |
|1 |0 |0 |
|1 |1 |1 |

La porte ET est symbolisée par le schéma suivant : 



|Symbole |Autre symbole |Opération |
| - | - | - |
|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.014.png)|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.015.png)|E1 . E2 |

### **<H3 STYLE="COLOR:GREEN;">2.4. La<a name="_page2_x40.00_y432.04"></a> porte OU EXCLUSIF (XOR)</h3>** 

La porte XOR a deux entrée E1 et E2 et une sortie S 

|E1 (Entrée) |E2 (Entrée) |S (Sortie) |
| - | - | - |
|0 |0 |0 |
|0 |1 |1 |
|1 |0 |1 |
|1 |1 |0 |

La porte XOR est symbolisée par le schéma suivant : 

|Symbole |Autre symbole |Opération |
| - | - | - |
|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.016.png)|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.017.png)|![](Aimg02.png) |

### **<H3 STYLE="COLOR:GREEN;">2.5. La<a name="_page2_x40.00_y649.04"></a> porte NON ET (NAND)</h3>** 

|Symbole |Table de vérité |Opération |
| - | - | - |
|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.018.png)|![](Aimg04.png)|![](Aimg03.png) |



### **<H3 STYLE="COLOR:GREEN;">2.6. La porte NON OU (NOR)</h3>** 

|Symbole |Table de vérité |Opération |
| - | - | - |
|![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.019.png)|![](Aimg05.png)|![](Aimg06.png) |




**<H3 STYLE="COLOR:red;">Activité n°1.:</H3>** Écrivez les tables de vérité des expressions suivantes : 

- ![](Aimg07.png)
- ![](Aimg08.png)
- ![](Aimg09.png)

**<H3 STYLE="COLOR:red;">Activité n°2.:</H3>** Voici un exemple de fonction booléenne : La fonction multiplexeur, notée mux.  
 
mux(x,y,z)=(not(x) and y)or (x and z) 
1.  Compléter le tableau 
x y z not(x) not(x) and y x and z mux(x,y,z) 
![](Aimg010.png)

2. Montrer que (x and y) = not (not(x) or not(y))  
3. Montrer que (x or y) = not (not(x) and not(y))  
4. Trouver l’expression  de  la  fonction  ssi(x,y)  à  l’aide  des  opérateurs booléens   

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.020.png)

## **<H2 STYLE="COLOR:BLUE;">3. Quelques<a name="_page3_x40.00_y448.04"></a> propriétés</h2>** 
### **<H3 STYLE="COLOR:GREEN;">3.1. Associativité</h3>**
Comme avec les opérations habituelles, certaines parenthèses sont inutiles :

(a + b) + c = a + (b + c) = a + b + c 

(a·b)·c = a·(b·c) = a·b·c 

### **<H3 STYLE="COLOR:GREEN;">3.2. Commutativité<a name="_page3_x40.00_y528.04"></a></H3>** 
L'ordre est sans importance : 

a + b = b + a 

a·b = b·a 

### **<H3 STYLE="COLOR:GREEN;">3.3. Distributivité<a name="_page3_x40.00_y585.04"></a></h3>** 

Comme avec les opérations mathématiques habituelles, il est possible de distribuer : 

a·(b + c) = a·b + a·c 

Attention : comportement différent par rapport aux opérateurs + et · habituels  

### **<H3 STYLE="COLOR:GREEN;">3.4. Lois<a name="_page3_x40.00_y649.04"></a> de Morgan</h3>**[^2] 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.021.png)

Le  complément  d’une  somme  logique  (non  arithmétique)  est  égal  au  produit  logique  (non  arithmétique) des termes complémentés. Loi de Morgan  

![](Aimg011.png)  

Le  complément  d’un  produit  logique  (non  arithmétique)  est  égal  à  la  somme  logique  (non  arithmétique) des termes complémentés.  

![](Aimg012.png)

## **<H2 STYLE="COLOR:BLUE;">4. Exercices<a name="_page4_x40.00_y43.04"></a></h2>** 

=> **CAPYTALE Le code vous sera donné par votre enseignant**


**<H3 STYLE="COLOR:red;">Exercice n°1</H3>** ★ **:** On considère le circuit logique suivant. 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.022.png)

1. Réaliser le circuit à l’aide du logiciel Logisim. 
2. Donner l’expression booléenne de S en fonction des variables A et B. 
3. Compléter la table de vérité ci-dessous. 

![](Aimg013.png)

4 Par quel circuit comprenant seulement deux portes peut-on remplacer le circuit étudié ? 

**<H3 STYLE="COLOR:red;">Exercice n°2</H3>** ★ :  On considère le circuit logique ci-dessous 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.024.png)

1 Donner l’expression booléenne de S en fonction des variables A, B et C. 

2 Compléter la table de vérité ci-dessous 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.025.jpeg)

3 En déduire une formule pour S qui ne dépend que des variables A et B. 

**<H3 STYLE="COLOR:red;">Exercice n°3</H3>** ★ : On considère les circuits logiques ci-dessous 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.026.png)![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.027.png)![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.027.png)



1 Donner les expressions booléennes de U et V en fonction des variables A, B et C. 

2 Compléter les tables de vérité ci-dessous. 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.028.jpeg)

3 Les expressions booléennes U et V sont-elles équivalentes ? 

**<H3 STYLE="COLOR:red;">Exercice n°4</H3>** ★– (circuit MUX-2) : On considère le circuit logique suivant.



![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.029.png)

1. Donner l’expression de Out en fonction  de E1 et E2. 
2. Compléter le tableau de vérité de ce circuit. 

Le circuit étudié est appelé multiplexeur à 2 entrées. Selon la valeur de la commande (C), il permet de  reproduire en sortie (Out) : 

- le signal E1 si C est à 0. 
- le signal E2 si C est à 1. 

![](Aimg014.png) 



**<H3 STYLE="COLOR:red;">Exercice  n°5</H3>**  (circuit MUX-4)  

On  considère  un  multiplexeur  à  4  entrées, dont le circuit  est  représenté  ci- dessous.  
![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.035.jpeg)

1. Par analyse du circuit, déterminer l’expression booléenne de Out en fonction des entrées E1,  E2, E3, E4 et des commandes C0 et C1. 

2. Quelles sont les valeurs des commandes C0 et C1 qui permettent de sélectionner en sortie (Out) : 

- l’entrée E1 ? 
- l’entrée E2 ? 
- l’entrée E3 ? 
- l’entrée E4 ? 

**<H3 STYLE="COLOR:red;">Exercice n °6</H3>** ★★– (Half adder) Le circuit étudié, appelé  demi-additionneur, permet d’additionner deux bits A et B.  Il  comporte  deux  sorties  C  et  S  qui  représentent  deux  expressions booléennes.  
![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.037.png)

1 Donner les expressions booléennes de C et S  en  fonction de A et B.  
2 Compléter la table de vérité de C et S. 

![](Aimg015.png) 

3 Quel est le rôle des sorties C et S dans la fonction  du circuit ? 


Le choix de la lettre C vient du fait qu’en anglais,  « retenue»se dit«carry».  

**<H3 STYLE="COLOR:red;">Exercice  n°7</H3>**  ★★–  *(Full adder)* Le circuit étudié dans cet  exercice  permet  d’additionner  deux bits en tenant compte d’une  retenue Cin. 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.053.jpeg)

Réaliser ce circuit à l’aide du logiciel Logisim et compléter la table de vérité ci-dessous. 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.054.jpeg)



**<H3 STYLE="COLOR:red;">Exercice n°8</H3>** ★★**:** Soit le circuit ci-dessous : 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.055.png)

1. Écrivez l'équation de ce circuit. 
2. Établissez la table de vérité de ce circuit. 

**<H3 STYLE="COLOR:red;">Exercice n°9 ★★★ :</H3>** 

Un pont peut supporter 10 tonnes au maximum. La route menant au pont est strictement interdite aux véhicules de plus de 10 tonnes. À chaque extrémité du pont se trouve une barrière et une bascule pour mesurer le poids (a ou b) des véhicules. 

![](Aspose.Words.097e3465-a1f8-4dd1-8604-dd29d3a73091.056.jpeg)

Si un seul véhicule attend devant le pont, la barrière devant lui (A ou B) s'ouvre (étape initiale). Sinon : 

- Si a + b ≤ 10 tonnes, les barrières A et B s'ouvrent. 
- Si a + b > 10 tonnes, seule la barrière correspondant au véhicule le plus léger s'ouvre. 

L'autre véhicule attend que le premier ait franchi le pont, puis le protocole d'ouverture des barrières recommence à l'étape initiale. 

- Si a = b, la barrière A s'ouvre en priorité. 

Indication : a et b n'étant pas des variables binaires, il convient de créer deux variables binaires x et y et de reformuler l'énoncé du problème. 

Aide : on posera x= a + b <= 10  et  y = a > b 

1. Écrivez la table de vérité pour l'ouverture des barrières A et B. 
2. Donnez les équations logiques pour l'ouverture des barrières A puis pour l’ouverture de la barrière B. 
3. Dessinez le circuit logique déterminant l'ouverture des barrières. 


[^1]: ` `*A Programming Language* : langage adapté aux calculs statistiques 
[^2]: Augustus De Morgan (1806-1871) : Logicien et Mathématicien Anglais 