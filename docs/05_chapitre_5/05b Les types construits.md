---
author: ELP
title: Chapitre 5 - Types construits
---


**Table des matières** 

1. [Les séquences en Python](#_page0_x40.00_y242.92)
2. [Les dictionnaires](#_page6_x40.00_y36.92)
3. [Exercices](#_page9_x40.00_y273.92)

1. **Les<a name="_page0_x40.00_y242.92"></a> séquences en Python** 

Il est possible de "stocker" plusieurs grandeurs dans une même structure, ce type de structure est appelé **une ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.001.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.002.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.003.png)séquence.** De façon plus précise, nous définirons une séquence comme un ensemble fini et ordonné d'éléments indicés de 0 à n-1 (si cette séquence comporte n éléments). 

Nous allons étudier plus particulièrement 2 types de séquences **: les tuples et les listes** (il en existe d'autres que nous n'évoquerons pas ici). 

1. **Les<a name="_page0_x40.00_y378.92"></a> tuples en Python** 

Les **tuples** sont des séquences (ou p-uplet), assez semblables aux listes, sauf qu'on ne peut **PAS MODIFIER ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.001.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.004.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.003.png)**un tuple après qu'il ait été créé :  ils sont **non mutables.** Cela signifie qu'on définit le contenu d'un tuple (les objets qu'il doit contenir) lors de sa création, mais qu'on ne peut en ajouter ou en retirer par la suite. 



|**Activité n°1.: Les parentaises sont facultatives**  |
| - |
|tuple = 'a', 123 , True |
|print(tuple) |
|autre\_tuple = 'hello',    # <-- notez la virgule |
|print(autre\_tuple) |
|<p>>>>  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.005.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.006.png)</p><p>('a', 123, True) ('hello',) </p>|
||
**Activité n°2.: Création de tuples à partir d’une liste :** avec la fonction tuple() : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.007.png)

\>>> liste = [7, 5, 6, 8, 3] >>> a = tuple(liste) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.008.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.009.png)

\>>> a 

(7, 5, 6, 8, 3) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)



|**Activité n°3.: Concaténation :** Il existe deux opérations de concaténation avec les opérateurs + et \*. De nouveaux |
| - |
|p-uplets sont créés.  |
|t1 = 'a', 'b'  |
|t2 = 'c', 'd' |



|print(t1 + t2)   ||
| - | :- |
|print(3 \* t1)    ||
|||
|||


|**Activité n°4.: Utilisation des indices :** Les** indices permettent d’accéder aux différents éléments d’un tuple : |
| - |
|<p>>>> t = "a", 1, "b", 2, "c", 3 ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.011.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.012.png)</p><p>>>> len(t) </p><p>6 </p><p>>>> t[2]  **# pour afficher le 3ème élément** </p><p>'b' </p><p>>>> t[-1]  **# pour afficher le dernier élément** </p><p>3 </p><p>>>> t[1:3]  **# pour afficher les éléments de l'indice 1 à l'indice 3 (non compris)** (1, 'b') </p><p>>>> t[0:5:2]  **# pour afficher les éléments de 0 à 5 (non compris) mais de 2 en 2** ('a', 'b', 'c') </p>|
||
|![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.013.png)Attention comme dans les listes (tableaux) les indices des éléments commencent à 0. |



|**Activité n°5.: Tuple de tuples :**On peut créer des tuples de tuples : ||
| - | :- |
|tuple1 = 'a', 123 , True ||
|tuple2= 13, 17 ||
|tuple= tuple1, tuple2, 'tout ça !' ||
|print(tuple) ||
|print( tuple[1][0]) # permet d’accéder à … ||
|||
|||
|Un **tuple est immuable** (on ne peut pas le modifier) mais il contient des objets muables (qu’on peut modifier)** ||



|**Activité n°6.: Parcours d’un tuples de deux manières :**  ||
| - | :- |
|prenoms="bruno","Marie" ||
|||
|for element in prenoms: **# méthode 1, elt prend à chaque tour les éléments de la séquence** ||
|print(element) ||
|||
|for i in range(len(prenoms)): **# méthode 2, on parcourt les indices de la séquence** ||
|print(prenoms[i]) ||
|||
|||


|**Activité n°7.:** Grâce au tuple, une fonction peut renvoyer plusieurs valeurs  |
| - |
|def add(a, b):  |
|c = a + b  |



|return (a, b, c)  |
| - |
||
|mon\_tuple = add(5, 8)  |
|print(f"{mon\_tuple[0]} + {mon\_tuple[1]} = {mon\_tuple[2]}") |
|<p>>>>  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.014.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.006.png)</p><p>5 + 8 = 13 </p>|
||
**Remarque** :  Les  chaines  de  caractères  formatées  (aussi  appelées  ***f-strings***)  permettent  d’inclure  la  valeur d’expressions Python dans des chaines de caractères en les préfixant avec f ou F et écrire des expressions comme {expression}. 



|**Opérations/méthodes**|` `**Description** |
| - | - |
|**Méthodes et opérations communes aux listes et tuples.** ||
|<p>x  s </p><p>in</p>|Renvoie True si un élément de s est égale à x, False sinon |
|<p>x  s </p><p>not in</p>|Renvoie True si aucun un élément de s n'est égale à x, False sinon |
|len(s)|Renvoie le nombre d'éléments de s |
|s == s1 ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.015.png)|Renvoie True si s et s1 sont de même type, ont la même longueur,et ont des éléments égaux deux à deux. |
|s[i]|Renvoie l'élément d'indice i de s. Le premier élément a pour indice 0. |
|s[i:j]|Renvoie une partie de l'indice i à j non inclus |
|s.index(x)|Renvoie l'indice de la première apparition de x dans s |
|s.count(x)|Renvoie le nombre d'apparitions de x dans s |
|s+t|Renvoie une nouvelle séquence concaténation de s et t. |
|n\*t|Renvoie une nouvelle séquence composée de la concaténation de t avec lui même n fois. |

2. **Les<a name="_page2_x40.00_y419.92"></a> tableaux** 

Sous Python, les **tableaux** sont appelés **listes** et on peut définir une liste comme une collection d’éléments séparés par des virgules, l’ensemble étant enfermé dans des crochets. Une liste est une séquence ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.016.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.017.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.018.png)**mutable.** 

Les éléments individuels qui constituent une liste peuvent être de type varié. 

Les  objets  placés  dans  une  liste  sont  rendus  accessibles  par  l’intermédiaire  d’un  index  (nombre  qui  indique l’emplacement de l’objet dans la séquence). Son premier indice a pour rang 0. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)



|**Activité n°8.: Création de listes** |
| - |
|liste\_vide = [] |
||
|liste1 = 10 \*[0] |
||
|liste2 = list(range(2,10,3)) |
|<p>>>> liste\_vide ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.019.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.020.png)</p><p>[] </p><p>>>> liste1 </p><p>[0, 0, 0, 0, 0, 0, 0, 0, 0, 0] >>> liste2 </p><p>[2, 5, 8] </p>|
||
|![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.021.png) ATTENTION : si vous avez dans un programme "range(a,b)", a est la borne inférieure et b a borne |
|supérieure. Vous ne devez surtout pas perdre de vu que **la borne inférieure est incluse**, mais que **la borne** |
|**supérieure est exclue.** |



|**Activité n° 9.**: **Construction par compréhension** L’instruction s’écrit sous la **forme [expression(i) for i in** |
| - |
|**objet]**. Ce type de construction est très spécifique au langage Python. |
||
|carres = [i\*i for i in range(11)] |
||
||
|<p>>>> carres ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.022.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.023.png)</p><p>[0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100] </p>|
||
|La compréhension de listes **évite donc d'écrire** le code “classique” suivant : |
|carres = []  A ne JAMAIS |
|for i in range(11):  faire |
|`  `carres.append(i\*i) |
||


|**Activité n° 10.**: **Construction par compréhension**  |
| - |
|multiples\_de\_3 = [3 \* i for i in range(30)] |
|multiples\_de\_6 = [2 \* n for n in multiples\_de\_3] |
||
|mon\_tab = [p for p in range(0, 5)] |
||
|liste = [1, 7, 9, 15, 5, 20, 10, 8] |
|mon\_tab2 = [element for element in liste if element > 10] |
||
|mon\_tab3 = [elm\*\*2 for elm in liste if elm < 10] |
||
|mon\_tab4 = [[[i, j] for i in range(3)] for j in range(2)] |
||
|import random |
|resultat = [random.randint(1, 6) for i in range(10)] |
||
|<p>>>> multiples\_de\_3 ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.024.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.025.png)</p><p>[0, 3, 6, 9, 12, 15, 18, 21, 24, 27] </p><p>>>> multiples\_de\_6 </p><p>[0, 6, 12, 18, 24, 30, 36, 42, 48, 54] </p><p>>>> mon\_tab </p><p>[0, 1, 2, 3, 4] </p><p>>>> mon\_tab2 </p><p>[15, 20] </p><p>>>> mon\_tab3 </p><p>[1, 49, 81, 25, 64] </p><p>>>> mon\_tab4 </p><p>[[[0, 0], [1, 0], [2, 0]], [[0, 1], [1, 1], [2, 1]]] >>> resultat </p>|
||
|mon\_tab3 permet d’obtenir une liste qui contient tous les éléments de liste élevés au carré à condition que ces |
|éléments de liste soient inférieurs à 10. |



|**Activité n°11.: Copie de liste**  |
| - |
|liste3 = [1, 49, 81, 25, 64] |
||
|liste4 = liste3[::] |
||
|liste5 = liste3[::-1] |
||
|liste6 = list(liste5) |
|**ATTENTION** :  si on copie une liste en faisant liste6 = liste5, on ne la copie pas réellement on fait seulement |
|**un lien** de la variable liste6 vers [64, 25, 81, 49, 1]. Si on modifie la liste5, alors la liste6 est également modifiée !! |



||
| :- |
|<p>>>> liste4 ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.026.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.027.png)</p><p>[1, 49, 81, 25, 64] >>> liste5 </p><p>[64, 25, 81, 49, 1] >>> liste6 </p><p>[64, 25, 81, 49, 1] </p>|
||


|**Activité n°12.:** Ajouter et supprimer des éléments ||
| - | :- |
|liste3 = [1, 49, 81, 25, 64] ||
|liste3.append("en dernier") ||
|print(liste3) ||
|liste3.pop(1) ||
|print(liste3) ||
|||
|||
**Activité n°13.: avec les chaine de caractères  :** Il existe pour les listes des méthodes très intéressantes dans le traitement des chaines de caractères. Ce sont les méthodes ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.028.png)split() et join(). Observer le code proposé et réaliser les affichages des listes créées. Penser à également utiliser la commande type(variables) afin de vérifier le type des variables créées. 

citation="Je ne cherche pas à connaître les réponses, je cherche à comprendre les questions." 

liste=citation.split(" ") phrase2=" ".join(liste) 

print(liste) print(phrase2) 

\>>> ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.029.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.030.png)

['Je', 'ne', 'cherche', 'pas', 'à', 'connaître', 'les', 'réponses,', 'je', 'cherche', 'à', 'comprendre', 'les', 'questions.'] 

Je ne cherche pas à connaître les réponses, je cherche à comprendre les questions. 

Les mêmes opérations et méthodes peuvent être appliquées aux listes qu’au tuples mais voici celles qui ne sont applicables qu’aux listes (mais pas aux tuples) 



|**Méthodes et opérations applicables aux listes (mais pas aux tuples).** ||
| - | :- |
|s.append(x)|Ajoute l'élément x à la fin de la liste s. |
|s[i] = x|Modifie la liste et affecte la valeur x à la case d'indice i. Attention, cette case doit exister. |
|s.insert(i,v)|Insère l'élément x dans s à l'indice i . Cette méthode décale les indices suivants. |
|s.remove(x)|Supprime de la liste le premier élément dont la valeur est égale à x |
|s.pop(i)|Enlève de la liste l'élément à la position i et renvoie sa valeur. En l'absence de i, c'est le dernier élément qui est supprimé et renvoyé |
|s.sort()|Modifie la liste s en la triant |
|s.reverse()|Modifie la listes en inversant l'ordre des éléments de s |

Quel **est l'intérêt d'utiliser un tuple** ? La réponse est simple : les opérations sur les tuples sont **plus "rapides".** Quand vous savez que votre liste ne sera pas modifiée, il est préférable d'utiliser un tuple à la place d'une liste. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.031.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.032.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.033.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

3. **Les<a name="_page5_x40.00_y36.92"></a> tableaux de tableaux** 

Les éléments d'un tableau peuvent être également un tableau. Ce type d'objet rappelle un objet mathématique qui s'appelle une **matrice**. Cet objet est utilisé dans de nombreux domaines, notamment dans le traitement des images. Une image est une **matrice de pixels**. 

On appelle matrice un tableau de tableaux dont chaque tableau à la même longueur. Chaque élément d'une matrice A est noté 

, où *i* est le numéro de ligne et *j* le numéro de colonne. 

On représente une matrice de taille n,m en mathématiques ainsi : 

1,1 1,2 ⋯ 1,

2,1 2,2 2,* 

- ( ⋮    ⋮ ⋱ ⋮ )

,1 ,2 ⋯ ,

Pour accéder à un élément organisé en **liste de liste**, on utilise une notation avec un double crochets. Le premier indice pointe la ligne et le deuxième indice pointe la colonne. 

Si notre matrice contient n listes de m éléments on peut la voir ainsi : 

[0][0] [0][1] [0][ − 1]

- ( [1][0] [1][1] ⋯ [1][ − 1] )* 

⋮                      ⋮ ⋱ ⋮

[ − 1][0] [ − 1][1] ⋯ [ − 1][ − 1]![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)



|**Activité n°14.: Travailler sur des listes de listes** |
| - |
|m = [[1, 3, 4], [5 ,6 ,8], [2, 1, 3], [7, 8, 15]] |
|Il est souvent plus pratique de présenter ces " listes de listes" comme suit : |
|m = [[1, 3, 4], |
|[5, 6, 8], |
|[2, 1, 3], |
|[7, 8, 15]] |
|Pour cibler un élément particulier de la matrice, on utilise la notation avec "doubles crochets" : m[ligne][colonne] |
|(sans perdre de vu que la première ligne et la première colonne ont pour indice 0) |
|<p>>>> a = m[1][2] >>> a ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.034.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.035.png)</p><p>8 </p>|
||


|**Activité n°15.: Parcours de liste de listes** Il est possible de parcourir l'ensemble des éléments d'une matrice à ||
| - | :- |
|l'aide d'une "double boucle for" :** ||
|m = [[1, 3, 4], ||
|[5, 6, 8], ||
|[2, 1, 3], ||
|[7, 8, 15]] ||
|||
|nb\_colonne, nb\_ligne = 3, 4 ||
|||
|for i in range(0, nb\_ligne): ||
|for j in range(0, nb\_colonne): ||
|a = m[i][j] ||
|print(a) ||
|||
|||
2. **Les<a name="_page6_x40.00_y36.92"></a> dictionnaires** 

Comme les listes et les tuples, les dictionnaires permettent de stocker des données Une différence essentielle entre les listes et les dictionnaires est que les éléments d’une liste sont repérés par des indices 0, 1, 2, … alors que dans les dictionnaires ils sont remplacés par des objets de type str, float, tuples que l’on appelle clé et à chaque clé correspond une valeur. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.036.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.037.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.038.png)**Ces clés ne sont pas ordonnées**. Chaque élément d’un dictionnaire est donc composé de 2 parties, on parle de pairs **« clé/valeur ».** 

1. **Création<a name="_page6_x79.00_y161.92"></a> de dictionnaires** 

Un dictionnaire est créé avec des accolades, les différents couples étant séparés par des virgules. La clé et la valeur correspondante d’un élément sont séparées par **deux-points.** 

Exemple : dico = {"A": 0, "B": 1, "C": 2, "D": 3}. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)



|**Activité  n°16.:  Création  d’un  dictionnaire**  :  Pour  ajouter  une  couple  de  clé,valeur  il  suffit  d'écrire  : ||
| - | :- |
|d[nouvelle\_clé]=nouvelle\_valeur ||
|res={'nsi' :18,'maths':17,'svt':14,'français':14,'lv1':8,'physique':12,'HG':11} ||
|#Ajouter la moyenne de 12 en lv2. ||
|res['lv2'] = 12 ||
|||
|||


|**Activité n°17.: Construction d’un dictionnaire en compréhension** (comme avec les listes) :  ||
| - | :- |
|dico1 = {x:x\*\*2 for x in range(1,5)} ||
|jours = 'lundi','mardi','mercredi','jeudi','vendredi','samedi','dimanche' ||
|dico2 = {i+1:jours[i] for i in range(len(jours))} ||
|||
|||


|**Activité n°18.: Création de dictionnaire à partir d’une liste de listes avec la fonction** dict :  |
| - |
|liste = [['A', 0], ['B', 1], ['C', 2]] |
|d = dict(liste)  |
|<p>>>> d ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.039.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.040.png)</p><p>{'A': 0, 'B': 1, 'C': 2} </p>|
||
2. **Accès<a name="_page7_x40.00_y36.92"></a> aux éléments** 



|**Activité n°19.: Avec les méthodes** keys() **et** values() **:**Accès aux éléments avec les méthodes keys et ||
| - | :- |
|values   ||
|turing={'nom':'Turing','prenom':('Alan','Mathison'),'nation':'anglaise','naissance' : ||
|1912, 'mort':1954} ||
|||
|print("Avec la méthode keys()") ||
|for i in turing.keys(): ||
|print(i) ||
|||
|print("Avec la méthode values()") ||
|for i in turing.values(): ||
|print(i) ||
|||
|||


|**Activité n°20.: Avec la méthode** item() **:** Accès à l’ensemble des couples clés-valeurs avec la méthode items||
| - | :- |
|turing={'nom':'Turing','prenom':('Alan','Mathison'),'nation':'anglaise','naissance' : ||
|1912, 'mort':1954} ||
|||
|print("Avec la méthode item()") ||
|for i in turing.items(): ||
|print(i) ||
|||
|print("Avec la méthode item() version2") ||
|for key, value in turing.items() : ||
|print("la clé {} contient la valeur {}.".format(key, value)) ||
|||
|||
|On obtient **des tuples**, pour la première méthode. ||

Remarque : dans le dernier exemple, on voit la chaine de caractère formatée avec la **méthode format** ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)



|**Activité n°21.: Test d’appartenance** : avec **l’opérateur** in ||
| - | :- |
|d = {'A': 0, 'B': 1, 'C': 2} ||
|print("A" in d)            # teste si "A" est une clé ||
|print(3 in d.values())          # teste si 3 est une valeur ||
|print(('C', 2) in d.items())     # teste si ('C', 2) est un couple clé-valeur ||
|||
|||


|**Activité n°22.: Modification d’une valeur particulière**  ||
| - | :- |
|mes\_fruits = {"poire": 3, "pomme": 4, "orange": 2} ||
|mes\_fruits["pomme"] = mes\_fruits["pomme"] - 1 ||
|print(mes\_fruits) ||
|mes\_fruits['poire'] = 10 ||
|print(mes\_fruits) ||
|||
|||


|**Activité n°23. Méthode** get : Une instruction comme v = d["E"] provoque **une erreur** car la clé ”E” n’existe pas. La ||
| - | :- |
|méthode **get permet de gérer ce genre de problème.** ||
|**S**i la clé n'existe pas la méthode get() ne génère pas d'erreur mais renvoie la valeur None.  ||
|d = {'A': 0, 'B': 1, 'C': 2} ||
|v = d.get("A") ||
|print(v) ||
|||
|v = d.get("E") ||
|print(v) ||
|||
|||


|**Activité n°24.: fonction** len() **:** Donner le nombre de couple clé-valeur d’un dictionnaire  ||
| - | :- |
|d = {'A': 0, 'B': 1, 'C': 2, 'D': 3} ||
|print(len(d))    ||
|||
|||


|**Activité n°25.: Avec la fonction** del() : ||
| - | :- |
|d = {'A': 0, 'B': 1, 'C': 2, 'D': 3} ||
|del d["D"] ||
|print(d) ||
|||
|||


|**Activité n°26.: Exemple de formatage de chaine** :  |
| - |
|mon\_dico = {"nom": "Durand", "prenom": "Christophe", "date de naissance": "29/02/1981"}  |
|print(f'Bonjour je suis {mon\_dico["prenom"]} {mon\_dico["nom"]}, je suis né le |
|{mon\_dico["date de naissance"]}')  |
||
|mon\_dico['lieu naissance'] = "Bonneville"  |
|print (f'à {mon\_dico["lieu naissance"]}') |
|<p>>>>  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.041.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.042.png)</p><p>Bonjour je suis Christophe Durand, je suis né le 29/02/1981 à Bonneville </p>|
||
L’implémentation d’un dictionnaire optimise le coût en temps de la recherche d’un élément. 

L’implémentation d’un dictionnaire **optimise le coût en temps** de la recherche d’un élément. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.043.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.044.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.045.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

3. **Exercices** 

**Exercice 1 :** ★ **Utilisation des opérations et méthodes :**  en utilisant le code ci-dessous, compléter .   **jours\_1=('lundi','mardi','mercredi','jeudi','vendredi') jours\_2=(![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.046.png)'samedi','dimanche')** 

- **Tester si samedi est un élément de jours\_1** 
- **Donner la longueur de jours\_2** 
- **Tester si jours\_1 est égal à jours\_2** 
- **Donner le deuxième élément de jours\_1** 
- **Donner la partie de jours\_1 entre le deuxième élément et le quatrième élément ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.047.png)**
- **renvoyer l'indice de dimanche dans jours\_2** 
- **Renvoyer le nombre de samedi dans jours\_2** 
- **Créer un tuple semaine par concaténation de jours\_1 et de jours\_2** 

**Exercice 2 :** ★ **Test d’appartenance :** En utilisant un parcours de tuple avec la présence d'un indice, écrire une fonction est\_dans(element,tple) qui en argument reçoit un entiers ( élément) et un tuple d'entier ( tple) qui renvoie un booleen indiquant la présence de élément dans tuple. On testera la fonction sur les scripts suivants : **est\_dans(4,(1,2,3,4,5,6)) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.048.png)**

- **qui devrait renvoyer True** 

**est\_dans(9,(1,2,3,4,5,6))** 

- **qui devrait renvoyer False** 

En Python, une fonction qui renvoie plusieurs éléments ( ex : return a,b,c ) renvoie un tuple.  

**Exercice 3 :** ★**Tuple et fonction :** Ecrire une fonction triangle(n) qui renvoie un tuple ou chaque élément est un tuple de longueur trois. Ces tuples sont constitués de trois entiers a, b,c tels que 0<a≤b≤c<n et le triangle de cotés 

a, b et c soit rectangle.  

Aide :  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.049.png)

for a in range(**1,** n): 

`    `for b in range(a**,** n): 

`        `for c in range(b**,** n): 

Ces triplets sont appelés triplets pythagoricien 

Par exemple :  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.050.png)

assert(triangle(**15**)== ((**3, 4, 5**)**,** (**5, 12, 13**)**,** (**6, 8, 10**))) 

**Exercice 4 :** ★**  **Dictionnaire et fonction**   

- Ecrire une fonction const\_dico(cle,valeur) qui renvoie le dictionnaire définie par les clés et les valeurs entrées en argument.** 
- On donne des listes de certains joueurs de League Of Legend ainsi que leur classement et leur nombre de points :** 

pseudo=['Major Alexander','KBM Wiz', 'FNC MagiFelix','Avalanche','love camile','Nobody'] ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.051.png)classement=[(12,1406),(1,1613),(4,1507),(9,1429),(16,1341),(11,1416)]

- Quel est le type de chacun des éléments?  
- Appliquer votre fonction const\_dico(cle,valeur) sur les joueurs de LOL. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Exercice 5 :** ★★ **Le chiffrement de César (version light)** : Cryptographie 

- la fonction chr() 

Pour cet exercice nous allons utiliser la fonction chr de Python qui prend en argument un entier (codé en décimal) et qui renvoie le caractère ASCII associé. 

Voici une table ASCII : ASCII.txt (**dans dossier du chapitre)** 

- Quels sont les entiers qui code l'alphabet en lettre capitale? 
- Quels scripts faut-il écrire pour obtenir l'affichage de la lettre A et du mot NSI? 
- Ecrire le script Python qui permet d'obtenir une structure de données de type dict qui doit être :  

![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.052.png)

- Le chiffrement de César 

A chaque lettre de l'alphabet on associe un nombre de à 0 à 25. On ajoute à ce nombre un nombre choisi par exemple 7. Le reste de la division euclidienne du nombre obtenue par 26 correspond au chiffre qui codera la lettre initiale. La lettre Y est associée à 24, on lui ajoute 7 on obtient 31. Le reste de la division euclidienne de 31 par 26 est 5. Ce qui donne F. Y est donc codé par F. 

- Quels scripts écrire pour obtenir le code de la lettre A et du mot NSI avec un décalage de 7. Rappel : le reste de la division euclidienne de a par b s'obtient en Python ainsi : a%b 
- Quel script écrire pour obtenir le dictionnaire de la table de codage/décodage de l'alphabet avec la méthode du chiffrement de César avec un décalage de 7? On stockera ce dictionnaire dans une variable nommée d. 
- Une fonction de codage 
  - Reprendre votre dictionnaire d et tester : 

d['A'] ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.053.png)

d['D'] 

d['E'] 

- Dans le script précédent quel est le statut de 'A', 'D' et 'E'? Clé ou valeur? 
- Ecrire une fonction en Python codage(mot) qui prend en argument un chaine de caractère écrit en lettre capitale et qui renvoie le mot codé par le chiffrement de César. 

**Exercice 6 :** ★ **Création de matrice  :** Ecrire une fonction matriceAlea(n:int,m:int)->list Python qui renvoie une matrice à n lignes et m colonnes d'entiers aléatoires entre 0 et 100. Créer deux fonctions l’une qui utilise la ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.054.png)

création en compréhension et l’autre la création en extension. 

Aide : ne pas oublier d’importer le module random ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Exercice 7 :** ★★ **Carré magique  :** Un carré magique d’ordre 3 est une matrice de 3 lignes et de 3 dans laquelle des nombres sont placés de telle sorte que la somme des nombres de chaque colonne, chaque ligne et de chacune des 

deux diagonales soit la même. De plus, le carré doit contenir une fois chaque nombre, de 1 au nombre de cases de la grille. Ecrire un script Python qui vérifie que ce carré est magique. On pourra utiliser : 

L=[ [2,7,6], ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.055.png)

`    `[9,5,1], 

`    `[4,3,8]] 

ð  Pour aller plus loin : problème France-IOI (niveau 3 → 5 -tableaux avancés): 

Un carré magique est une grille carrée dans laquelle des nombres sont placés de telle sorte que la somme des nombres de chaque colonne, chaque ligne et de chacune des deux diagonales soit la même. De plus, Le carré doit contenir une fois chaque nombre, de 1 au nombre de cases de la grille. 

Ecrivez un programme qui vérifie si une grille de nombres est un carré magique. 

**Entrée** 

La première ligne de l'entrée contient un entier *N* : le nombre de cases du côté de la grille de nombres. 

Chacune des *N* lignes suivantes contient *N* entiers séparés par des espaces : les nombres d'une ligne de la grille. 

**Sortie** 

Vous devez afficher une ligne sur la sortie, contenant le mot "yes" si le carré fourni est un carré magique, et "no" sinon. 

**Exemple** 

*entrée : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.056.png)*

3 

6 1 8 7 5 3 

2 9 4 *sortie : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.057.png)*

yes 

**Commentaires** 

Chacun des chiffres de 1 à 9 apparaît exactement une fois dans la grille. De plus, toutes les colonnes, lignes et les deux diagonales de cette grille ont pour somme 15. En effet : 

|<p>Lignes  : 6 + 1 + 8 = 15 </p><p>7 + 5 + 3 = 15 </p><p>2 + 9 + 4 = 15 </p>|<p>Colonnes  : 6 + 7 + 2 = 15 </p><p>1 + 5 + 9 = 15 </p><p>8 + 3 + 4 = 15 </p>|<p>Diagonales  : 6 + 5 + 4 = 15 </p><p>8 + 5 + 2 = 15 </p>|
| :- | :- | :- |

**Exercice 8:** ★ **avec les chaine de caractères  :** Python considère une phrase comme une séquence. Vous pouvez réaliser des essais avec cette citation célèbre du philosophe Confusius : "Je ne cherche pas à connaître les réponses, 

je cherche à comprendre les questions." De quelle type de séquence se rapproche-t-on? De la liste et/ou du tuple ? Faire des tests à partir de vos connaissances en python. 

- -\*- coding: utf-8 -\*- ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.058.png)

citation="Je ne cherche pas à connaître les réponses, je cherche à comprendre les questi ons."![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.059.png) 

- à faire : 

citation[3] citation[4]='z' citation.append('!') 

En utilisant la méthode count(), compter le nombre de 'a' dans la citation. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Exercice 9 :** ★★ **Jeu de cartes :   ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.060.png)**Un jeu de 32 cartes est composé de :  

- quatre couleurs : pique, cœur, carreau, trèfle  
- huit valeurs : roi, dame, valet,1,10,9,8,7  

**Modélisation du problème**.  

- Comment modéliser une carte en Python?  
- Comment modéliser un jeu de cartes?  

**Implémentation en Python.**  

Le but est d'implémenter un jeu de 32 cartes et se  doter de fonctions qui permettent interagir avec ce  jeu. 

Lorsque vous écrivez des fonctions : 

- Il faut typer vos fonctions. Exemple : creation\_jeu32(couleur:tuple, valeur32:tuple)->list 
- Il faut écrire une aide explicative docstring, entre " ", ou entre """ """" (si l'aide fait plusieurs lignes). 
1. Créer une fonction creation\_jeu32(couleur:tuple, valeur32:tuple)->list qui retourne un liste de 32  cartes  sous  forme  de  **liste  de  tuples** : [('Roi',  'pique'),  ('Roi',  'coeur'),  ('Roi', 'carreau'),…]

**Aide :**  

couleur = ("pique", "coeur", "carreau", "trèfle") valeur32 = ("Roi", "Dame", "Valet", 1, 10, 9, 8, 7) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.061.png)

2. Vérifier que le jeu possède 32 cartes 
2. On veut pouvoir mélanger le jeu de 32 cartes. Il existe une fonction shuffle(liste)  qui mélange les éléments d'une liste. Ecrire une fonction melange(jeu:list)->list qui renvoie le jeu de cartes mélangé. Penser à importer random 
2. On veut pouvoir tirer une carte au hasard du jeu. Si le jeu est mélangé, cela peut être la première carte. Il faut penser à retirer la carte du jeu. carte\_hasard(jeu:list)-> tuple
2. On veut pouvoir créer une "main" d’un certain nombre de cartes. Une main signifie un ensemble de cartes. Ecrire une fonction main(nombre\_cartes: int,jeu:list)->list: qui renvoie une main formée du nombre de cartes. Il faut penser à retirer la main créée du jeu de 32 cartes. 

**Vers une autre structure de données construites**. 

On veut pouvoir comparer des cartes pour réaliser par exemple des jeux. 

**Modélisation** 

- Comment modéliser la "force" d'une carte? 
- Comment modéliser le jeu de cartes avec la force de chaque carte? 

**Implémentation en Python** 

6. Ecrire une fonction force(carte:tuple)->int: qui renvoie la "force" de la carte. 
6. Ecrire une fonction jeu\_force(jeu : list) -> dict: qui renvoie le jeu des cartes associées à leur force. 
6. On  veut  comparer  deux  cartes.  Ecrire  une  fonction  en  Python compare(carte1:tuple,carte2:tuple,jeu\_force:dict)->tuple qui renvoie la carte avec la force la plus élevée. 
6. Inventer  une  notion  de  distance  entre  deux  cartes.  Ecrire  une  fonction distance(carte1:tuple,carte2:tuple)->int qui renvoie la "distance" entre deux cartes. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Exercice 10** ★★ **Tracé graphique**  

Matplotlib est une bibliothèque du langage de programmation Python destinée à tracer et visualiser des données sous formes de graphiques. Elle peut être combinée avec les bibliothèques python de calcul scientifique NumPy et SciPy. L’avantage de cette librairie est qu’elle est très simple d’utilisation et permet en quelques lignes de tracer des courbes par exemple. Il n’est donc pas nécessaire de passer par la phase (éventuellement longue et fastidieuse) de conception et de développement d’interfaces graphiques, pour des besoins de représentation qui peuvent être ponctuels par ailleurs. 

Matplotlib est distribuée librement et gratuitement sous une licence de style BSD. 

1. Créer un fichier Python graphics.py.
1. Écrire une fonction f, qui à x → x² + x – 4, et dont le prototype est le suivant : 

f(x : float) ->  float ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.062.png)

3. Compléter le code ci-dessous en utilisant une **compréhension de liste** pour liste\_x et liste\_y.
- liste\_x contient les éléments  ∈ [−3,0;3,0] par intervalle de 0,1. 
- liste\_y contient les images de x par f.

import matplotlib.pyplot as plt ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.063.png)

def f(x : float) -> float: 

- à compléter 
- à compléter liste\_x =  liste\_y =  

plt.plot(liste\_x, liste\_y, "b-", label="x² + x - 4", linewidth=3) plt.legend() 

plt.show() 

Résultat attendu : 

![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.064.png)

*courbe : x² + x – 4* 

On souhaite tracer une deuxième courbe sur le même graphique précédent dont l’équation est y = x3 – 3x + 2. 

4. Modifier votre programme en rajoutant une fonction f2 qui renvoie l’image de x pour l’équation ci-dessus. 
4. Mettre à jour une troisième liste liste\_y2 à l’aide d’une compréhension de liste. 
4. Modifier les paramètres de la fonction plot() pour obtenir le  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.065.jpeg)résultat ci-dessous.  
4. Rajouter la légende sur le graphique.  

Résultat attendu :  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Exercice 11 :** ★★ **Bulletins de vote Génération des votes:**  

On souhaite réaliser le comptage automatique d’un dépouillement d’une élection. Votre startup reçoit un fichier texte qui contient ligne par ligne les noms des candidats qui ont reçu le vote des électeurs. 

Il n’y a qu’un seul nom par ligne. Vous êtes chargé de fournir au client le nombre de votes et le total des votes reçus par candidats présents dans le fichier. 

1. Créer un fichier Python votes.py. 

On souhaite générer une liste de votes factices à partir d’une liste de noms. 

2. Ecrire une fonction qui crée un fichier texte (vote.txt) avec un nom par ligne qui a été tiré aléatoirement depuis une liste de noms. 

generate\_ballots(total : int, noise : int) -> bool ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.066.png)

- total -- nombre de bulletins 
- noise -- numero de bulletin "bruité" . Le bulletin bruité est un vote étranger (ie : d’un candidat pirate)  qui ne fait pas partie de la liste « officielle ». 
- la fonction renvoie True si Ok, ou False si erreur 

**Aide** :  

- la liste des noms : 

ballots  = ['Pikachu','Pikachu','Pikachu','Fantomas','Fantomas','Dark Vador','Dark Vador','Saruman','Saruman','Saruman'] ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.067.png)

stranger = 'Sex Pistols' 

**Rappels** :  

- on utilisera la fonction open() avec l’attribut "w"
- on utilisera la syntaxe : 

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.068.png)

- bloc à coder 

except IOError : 

return False return True 

- on utilisera le module random sur la liste ballots pour écrire un nom au hasard dans le fichier vote.txt  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.069.png)
- ne pas oublier "\n" à la fin de chaque ligne écrite et de fermer le fichier texte avec la méthode close()
3. Tester cette fonction avec total 10 et noise 2.  
3. Documenter la fonction. 

**Dépouillement :** 

5. Ajouter une fonction qui permet de dénombrer le nombre de votes pour un candidat donné. On donne le prototype de la fonction : 



|read\_ballots(filename : str) -> dic|t |||
| - | - | :- | :- |
|<p>- filename -- nom du fichier texte </p><p>- la fonction retourne un dictionnaire sous la</p>|` `forme {nom du candidat:nbr de votes}, ou None si|||

erreur 

**Aide :  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)**

- La méthode strip() et la méthode rstrip("\n") pour enlever le symbole. Les deux méthodes peuvent s’écrire sur la même ligne 

[https://www.w3schools.com/python/ref_string_strip.asp ](https://www.w3schools.com/python/ref_string_strip.asp)[https://www.w3schools.com/python/ref_string_rstrip.asp ](https://www.w3schools.com/python/ref_string_rstrip.asp)

**Rappels** :  

- on utilisera la fonction open() avec l’attribut "r" 
- on utilisera la syntaxe  

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.070.png)

- bloc à coder 

except IOError : 

return None       return #le dictionnaire 

- Ne pas oublier de fermer le fichier texte
6. Documenter la fonction (docstring). 
6. Tester les fonctions avec  

generate\_ballots(5000, 3951) print(read\_ballots("votes.txt")) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.071.png)

8. Déterminer les intrus qui se sont glissés dans le fichier et supprimer les du dictionnaire sans utiliser 'Sex Pistols' on pourra imaginer que tous les intrus ont qu’un seul vote. 
8. Afficher le nombre de votants à l’aide d’une compréhension de liste faite sur le dictionnaire retourné par la fonction read\_ballots().

**Aide :**  

- On pourra utiliser la fonction sum.  [https://www.programiz.com/python-programming/methods/built-in/sum ](https://www.programiz.com/python-programming/methods/built-in/sum)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Exercice 12 :** ★★★ **format EXIF Introduction  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.072.png)**

L’Exchangeable  Image  File  Format  ou  EXIF  est  une  spécification  de  format  de  fichier  pour  les  images  utilisées  par  les  appareils  photographiques  numériques.  Il  a  été  établi  par  le  Japan  Electronic  Industry Development Association (JEIDA). Cette spécification repose sur  des formats existants tels que JPEG, TIFF version 6.0 et RIFF format de  fichier audio WAVE, en y ajoutant des balises de métadonnées.  

Les  balises  de  métadonnées  définies  dans  le  format  EXIF  standard  couvrent un large éventail de données, dont :  

- Information de la date et de l’heure.  
- Marque et le modèle de l’appareil et des informations variables  telles  que  l’orientation,  l’ouverture,  la  vitesse  d’obturation,  la  longueur de focale, la sensibilité…  
- Informations  géographiques  provenant  d’un  éventuel  système  GPS connecté à l’appareil.  
- Description et information des droits d’auteur.  

*Source : wikipedia*  

**Utilisation du format EXIF**  

Les données EXIF des photos permettent de comprendre pourquoi telle 

photo est floue, telle autre est trop foncée ou encore pourquoi le ciel est tout blanc. De même, certains sites de publications d’images, comme Flickr par exemple, permettent de visualiser ces données. 

Ces données EXIF peuvent avoir des utilisations inattendues comme par exemple en cas de vol de votre appareil photo car le numéro de série de l’appareil est intégré dans ces données (voir le site[ Stolen Camera Finder)](https://www.stolencamerafinder.com/). 

**Lecture du format EXIF** 

La plupart des appareils photos récents et téléphones portables enregistrent les photographies avec des données géographiques (longitude, latitude, mais aussi altitude). Si ces données sont lisibles avec la majorité des logiciels photos et d’explorateurs de fichiers, il est également possible d’y accéder avec Python. 

1. Créer un fichier exif.py.
1. Écrire une fonction qui lise les données EXIF contenues dans une image. On donne le prototype de la fonction : 

get\_exif(filename : str) -> dict ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.073.png)

- filename -- fichier image 
- la fonction retourne les données EXIF si ok, ou None si erreur 

**Aide :**  

- On utilisera Image de la bibliothèque PIL :  

from PIL import Image ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.074.png)

- On utilisera la bibliothèque PIL ainsi que les méthodes associées \_getexif() et get().  from PIL.ExifTags import TAGS, GPSTAGS 
- L’appel à \_getexif() se fait de la façon suivante : 

image = Image.open(filename) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.075.png)

exif = image.\_getexif() 

- Cependant, on obtient par ce biais un dictionnaire indexé avec des identifiants numériques. Pour avoir les noms correspondants, on utilise ExifTags et on renommera les clefs du dictionnaire : 

new\_key = TAGS.get(key, key) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.076.png)

- Ne pas oublier de fermer l’image 

image.close() ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.077.png)

**Rappels : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)**

- on utilisera la syntaxe  

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.078.png)

- bloc à coder 

except IOError : 

return None return #ledictionnaire 

3. Tester la fonction avec le fichier 'valley.jpg' du dossier Ressources (à enregistrer au même endroit que le fichier exif.py). 
3. Documenter la fonction 
3. Indiquer l’auteur de la photo : 'Artist', le fabricant et le numéro de série de l’appareil. Attention aux majuscules / minuscules  
3. Ouvrir le fichier valley.jpg avec un éditeur de texte (Notepad++). Conclure. 

Comme vous pouvez le constater, nous avons un système clé:valeur (à chaque clé correspond une valeur). La clé "GPSInfo" n'est pas tout le temps présente puisqu'il s'agit des coordonnées (latitude, longitude) de la prise de vue, il faut donc que l'appareil photo intègre un GPS (ce qui est le cas des smartphones) : 

![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.079.png)

Les lignes 1, 2, 3 et 4 vont particulièrement nous intéresser : 

- ligne 1 : précise que nous sommes dans l'hémisphère Nord 
- ligne 2 : nous avons la latitude ((47, 1), (37, 1), (29107360, 1000000)) nous avons ici une latitude en degrés, 

minute, seconde. Ici : 

- 47/1=47 degrés  
- 37/1 minutes  
- et 29107360/1000000 secondes,  

aussi noté 47°37'29,107360" 

- ligne 3 : précise que nous sommes à l'ouest (W) du méridien de Greenwich 
- ligne 4 : nous avons la longitude ((3, 1), (25, 1), (42976570, 1000000)) ici aussi la longitude est donnée en 

degrés, minute, seconde (ici : 3°25'42,976570") 

7. Ajouter une fonction qui récupère les données GPS du format EXIF. On donne le prototype de la fonction : GPS\_read(filename : str) -> dict ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.062.png)
- filename -- fichier image 
- la fonction retourne les informations GPS si ok, ou None si erreur 

**Aides :  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)**

- La variable exif contient l’ensemble des métadonnées de l’image : objectif, ouverture, vitesse, auteur…  

exif = get\_exif(filename) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.080.png)

- Les données GPS sont stockées dans exif['GPSInfo'].Il est conseillé de faire afficher cette clé de dictionnaire pour obtenir les noms des champs associés aux informations GPS. Pour récupérer le couple clé, valeur il faut écrire :  

key, value in exif['GPSInfo'].items(): 

- Comme tout à l’heure il faut utiliser les ExifTags et renommer les clés 

new\_key = GPSTAGS.get(key, key) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.081.png)

**Rappels :** 

- Capturer les exceptions : s’il n’y a pas d’exif et s’il n’y a pas de 'GPSInfo' dans exif 

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.082.png)

- bloc à coder 

except KeyError : 

return None 

8. Tester la fonction avec le fichier 'mountain.jpg' du dossier Ressources (à enregistrer au même endroit que le fichier exif.py). 
8. Compléter le docstring de la fonction 

Les coordonnées géographiques sont habituellement exprimées dans le système sexagésimal, ou DMS pour degrés (°), minutes (′) et secondes (″). L’unité est le degré d’angle (1 tour = 360°), puis la minute d’angle (1° = 60′), puis la seconde d’angle (1° = 3 600″). 

Par rapport au plan équatorial, la latitude est complétée d’une lettre N (hémisphère) ou S selon qu’on se situe dans l’hémisphère Nord ou Sud. Par rapport au méridien de Greenwich, la longitude est complétée d’une lettre W ou E selon qu’on se situe à l’Ouest ou à l’Est. 

Remarque : pour obtenir un traitement automatisé des données géographiques, un format décimal est souvent plus pratique. On divise les minutes par 60 et les secondes par 3600 et on additionne le tout. La latitude est négative dans l’hémisphère Sud (S), et à l’Ouest du méridien de Greenwich (W). 

10. A partir des données GPS récupérées précédemment, écrire une fonction qui indique les coordonnées GPS[^1]. On donne le prototype de la fonction : 

get\_coordinates(GPSinfo : dict) -> list ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.083.png)

- GPSinfo -- données GPS 
- la fonction retourne les coordonnées GPS au format DMS si ok, ou None si erreur sous la forme d’une liste de liste ['valeurLatitude', 'valeurLongitude']

**Aide** : 

- Pour connaitre les données à utiliser reportez vous à la ligne 3 et la ligne 4 du tableau ci-dessus 
- Le  dictionnaire  précédent  renvoie  les  clés :   'GPSLatitudeRef',  'GPSLatitude', 'GPSLongitudeRef' et 'GPSLongitude' 
- Pour accéder à une valeur particulière : 



|>>> GPSinfo = {'GPSLatitudeRef': 'N', 'GPSLatitude': ((63, 1), (409847, 10000), (0, 1)), |
| - |
|'GPSLongitudeRef': 'W', 'GPSLongitude': ((19, 1), (318565, 10000), (0, 1)), 'GPSAltitudeRef': |
|b'\x00', 'GPSAltitude': (92709, 191), 'GPSTimeStamp': ((13, 1), (18, 1), (42000, 1000)), |
|'GPSSpeedRef': 'K', 'GPSSpeed': (23, 25), 'GPSImgDirectionRef': 'M', 'GPSImgDirection': |
|(57107, 192), 'GPSDestBearingRef': 'M', 'GPSDestBearing': (57107, 192), 'GPSDateStamp': |
|'2018:09:03', 'GPSHPositioningError': (10, 1)} |
|>>> GPSinfo['GPSLatitude'] |
|((63, 1), (409847, 10000), (0, 1)) |
|>>> GPSinfo['GPSLatitude'][0][0] |
|63 |

- Convertir chaque donnée en str pour pouvoir faire une présentation des coordonnées de ce type : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.084.png)'63.0°40.9847‘0.0"N'' 
- Pour coder le symbole de minute "‘" 
- Pour écrire une instruction sur plusieurs lignes on met \ à la fin de chaque ligne 

**Rappel** :  

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.085.png)

- bloc à coder 

except TypeError : return None 

11. Tester la fonction précédente avec le dictionnaire GPSinfo précédent 
11. Compléter le docstring de la fonction 

On souhaite combiner les fonctions pour obtenir les coordonnées GPS d’une image 

13. Ecrire une fonction qui combine les autres fonctions et qui retourne les coordonnées GPS de l’image entrée en argument. Le prototypage de la fonction  

def coordonnee\_GPS\_image(image:str) -> list: ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.086.png)

14. tester la fonction avec 'mountain.jpg'
14. documenter la fonction 
14. Créer un fichier exif\_test.py.
14. Valider les tests unitaires suivants : 

exif.get\_coordinates(exif.GPS\_read("mountain.jpg")) ==  ['63.0°40.9847‘0.0"N', ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.087.png)'19.0°31.8565‘0.0"W'] 

exif.get\_coordinates(exif.GPS\_read("turing.jpg")) == None exif.get\_coordinates(exif.GPS\_read("mountain.png")) == None exif.get\_exif("valley.jpg")['BodySerialNumber'] == "2506446" 

**Rappel :**  

- Ne pas oublier d’importer exif 

On souhaite avoir un programme qui extrait toutes les EXIF d’une photo entrée en input 

18. Créer un fichier exif\_main.py
18. Le programme doit demander la photo et retourner chaque donnée EXIF ligne par ligne : 



|indiquez un fichier>? mountain.jpg |
| - |
|ExifVersion b'0230' |
|ShutterSpeedValue (10167418, 1000000) |
|ApertureValue (1695994, 1000000) |
|DateTimeOriginal 2018:09:03 15:18:55 |
|DateTimeDigitized 2018:09:03 15:18:55 |
|BrightnessValue (17587, 1827) |
|etc… |

**Rappel :** 

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.088.png)

- bloc à coder 

except KeyboardInterrupt:       pass 

20. Tester avec le fichier mountain.jpg
20. Vérifier que toutes les fonctions soient bien documentées (docstring). **![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)**

**Exercice 13 :** ★★★ **Le chiffrement de Caesar** 

En cryptographie, le chiffrement par décalage, aussi connu comme le chiffre de César ou le code de César, est une méthode de ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.089.png)chiffrement très simple utilisée par Jules César dans ses correspondances secrètes (ce qui explique le nom « chiffre de César »). 

Le texte chiffré s'obtient en remplaçant chaque lettre du texte clair original par une lettre à distance fixe, toujours du même côté, dans l'ordre de l'alphabet. Pour les dernières lettres (dans le cas d'un décalage à droite), on reprend au début. Par exemple avec un décalage de 3 vers la droite, A est remplacé par D, B devient E, et ainsi jusqu'à W  qui  devient  Z,  puis  X  devient A  etc.  Il  s'agit  d'une  permutation  circulaire  de l'alphabet. La longueur du décalage, 3 dans l'exemple évoqué, constitue la clé du chiffrement qu'il suffit de transmettre au destinataire — s'il sait déjà qu'il s'agit d'un chiffrement de César — pour que celui-ci puisse déchiffrer le message. Dans le cas de l'alphabet latin, le chiffre de César n'a que 26 clés possibles. 

![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.090.png)

*Source :[ https://fr.wikipedia.org/wiki/Chiffrement_par_d%C3%A9calage* ](https://fr.wikipedia.org/wiki/Chiffrement_par_d%C3%A9calage)*

**Des chiffres et des lettres** 

Nous  adopterons  la  convention  suivante,  en  vert  c’est  la  partie  du  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.091.png)message  à  laquelle  tout  le  monde  a  accès  (ou  qui  pourrait  être  intercepté), c’est donc le message crypté. Alors qu’en rouge c’est la  partie du message confidentiel, c’est le message en clair.  

Pour prendre en compte aussi les dernières lettres de l’alphabet, il est  plus judicieux de représenté l’alphabet sur un anneau. Ce décalage est  un décalage circulaire sur les lettres de l’alphabet. Pour déchiffrer le  message de César, il suffit de décaler les lettres dans l’autre sens, D se  déchiffre en A, E en B,…  

Il est plus facile de manipuler des nombres que des lettres, aussi nous  passons à une formulation mathématique. Nous associons à chacune des  26 lettres de A à Z un nombre de 0 à 25. 

*Source: Arnaud Bodin & François Recher, université de Lille* 

Le code ASCII de la lettre ‘A’ a pour valeur 65, celui de la lettre ‘Z’ 90. Quel que soit le décalage appliqué, il faut rester dans l’intervalle [65 ; 90]. 

Méthode : 

1. ([65 ; 90] – 65) → [0 ; 25]  on soustrait 65 pour être dans un intervalle [0 ; 25] 
1. ([0 ; 25] + clef) → [clef ; 25 + clef]  on décale selon la clef 
1. [clef ; 25 + clef] modulo 26 → [0 ; 25]   le modulo permet de rester dans l’intervalle [0 ; 25] 
1. ([0 ; 25] + 65) → [65 ; 90]  on ajoute 65 pour revenir dans un intervalle [‘A’; ‘Z’] 

On appelle modulo d’un nombre x par N, l’opérateur qui renvoie le reste de la division entière de x par N. Exemple : 11 modulo 5 = 1 (en Python, le modulo est notée %). 

1. Créer un fichier caesar.py.
1. Écrire une fonction qui utilise la méthode de César pour crypter un message. 

Le prototype de la fonction est : caesar\_encode(text : str, key : int = 1) -> str

- text représente le texte à chiffrer,  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.092.png)
- key représente la clef de chiffrement.  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.093.png)
- La fonction doit renvoyer le texte chiffré. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.094.png)

**Aide :** 

- les caractères (lettres ou signes de ponctuations) qui ne figurent pas dans l’alphabet [A..Z] **restent inchangés**.  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.095.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.096.png)
- Utilisez les méthodes upper() (pour mettre en majuscule) et isalpha() (pour tester si c’est une lettre alphabétique)  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.097.png)
- Utilisez les fonction chr(#nombre) pour convertir en caractère et ord(‘#la lettre’) pour convertir en code ASCII 
3. Documenter la fonction 
3. Tester la fonction avec le message suivant : "ATTAQUEZ DEMAIN" avec la clé par défaut. Résultat attendu : BUUBRVFA EFNBJO
3. Écrire un programme qui permet de déchiffrer le texte chiffré précédemment. Le prototype de la fonction est : caesar\_decode(code : str, key : int = 1) -> str
- code représente le texte à déchiffrer,  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.098.png)
- key représente la clef de chiffrement.  
- La fonction doit renvoyer le texte déchiffré. 

**Aide :** 

- Le decodage de la lettre S avec une key = 19 donne Z. 
6. Documenter la fonction 
6. Factoriser le code des deux fonctions précédentes pour obtenir une fonction qui chiffre ou déchiffre. Le prototype de la fonction est : caesar(str\_in : str, key : int) -> str
- str\_in représente le texte à chiffrer/déchiffrer,  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.099.png)
- key représente la clef de chiffrement. Si key > 0 c’est un chiffrage si key < 0 c’est un déchiffrement.  
- La fonction doit renvoyer le texte déchiffré/chiffré. 
8. Documenter la fonction 

Une fonction est basée sur le modèle de la boite noire ; les sorties n’étant fonction que des entrées. Cette boite noire doit être à la fois cohérente (des entrées supposées fournir un résultat juste doivent donner un résultat juste, des entrées supposées donner un résultat faux doivent donner un résultat faux) et stable (le programme doit terminer, ne pas « crasher » ou avoir un comportement erratique). La vérification de ces deux critères se fait à travers des tests unitaires. 

9. Créer un fichier caesar\_test.py. 
9. Tests de cohérence. Écrire une série de tests unitaires qui vérifie les conditions suivantes : 

pour key = 0 et str\_in = ‘A’ : sortie = ‘A’ ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.100.png)

pour key = 1 et str\_in = ‘Z’ : sortie = ‘A’ 

pour key = 2 et str\_in = ‘Y’ : sortie = ‘A’ pour key = 26 et str\_in = ‘A’ : sortie = ‘A’ pour key = 26\*2 et str\_in = ‘A’ : sortie = ‘A’ pour key = -26 et str\_in = ‘A’ : sortie = ‘A’ pour key = 1 et str\_in = ‘’ : sortie = ‘’ pour key = 0, str\_in = ‘a’ : sortie = ‘A’ 

**Aide :** 

- utiliser l’instruction assert. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.101.png)
- Ecrire une fonction pour chaque test. Par exemple : test\_caesar\_rot0():
- Ne pas oublier d’importer le module caesar et la fonction caesar()
- Prévoir une fonction d’appel unit\_test() pour appeler chaque fonction test\_caesar…

**Décryptage** 

Décrypter consiste à retrouver le texte original à partir d'un message chiffré sans posséder la clé de (dé)chiffrement. Le challenge consiste à décrypter le message ci-dessous. 

AV WRZJ JFLMVEK TV IVMV VKIREXV VK GVEVKIREK 

`    `U’LEV WVDDV ZETFEELV, VK HLV A’RZDV, VK HLZ D’RZDV, 

`    `VK HLZ E’VJK, TYRHLV WFZJ, EZ KFLK R WRZK CR DVDV 

`    `EZ KFLK R WRZK LEV RLKIV, VK D’RZDV VK DV TFDGIVEU. 

Le chiffrement de César a été utilisé mais avec une clef différente de 1. 

11. Créer un fichier caesar\_main.py.
11. Écrire un programme afin de donner le nom de l’auteur du message crypté. 

**Aide :**  

- Ne pas oublier d’importer le module caesar et la fonction caesar()![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.102.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.103.png)
- La clef de chiffrement étant inconnue, il faut faire une boucle qui les teste toutes (technique de l’attaque par force brute). ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Exercice 14 :** ★★★ **Le chiffrement de Vigenère** 

Le chiffre de Vigenère est un système de chiffrement polyalphabétique, c’est un chiffrement par substitution, mais une même lettre du message clair peut, suivant sa position dans celui-ci, être remplacée par des lettres différentes, contrairement à un système de chiffrement mono alphabétique comme le chiffre de César (qu'il utilise cependant comme composant). Cette méthode résiste ainsi à l'analyse de fréquences, ce qui est un avantage décisif sur les chiffrements mono alphabétiques. Cependant le chiffre de Vigenère a été percé par le major prussien Friedrich Kasiski qui a publié sa méthode en 1863. Depuis cette époque, il n‘offre plus aucune sécurité. 

**Chiffrement mono-alphabétique**  

Nous avons vu que le chiffrement de César présente une sécurité très faible, la principale raison est que l’espace des clés est trop petit : il y a seulement 26 clés possibles, et on peut attaquer un message chiffré en testant toutes les clés à la main. 

Au lieu de faire correspondre circulairement les lettres, on associe maintenant à chaque lettre une autre lettre (sans ordre fixe ou règle générale). 

Par exemple : 

|A |B |C |D |E |F |G |H |I |J |K |L |M |N |O |P |Q |R |S |T |U |V |W |X |Y |Z |
| - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
|F |Q |B |M |X |I |T |E |P |A |L |W |H |S |D |O |Z |K |V |G |R |C |N |Y |J |U |

Pour crypter le message : ETRE OU NE PAS ETRE TELLE EST LA QUESTION 

On regarde la correspondance et on remplace la lettre E par la lettre X, puis la lettre T par la lettre G, puis la lettre R par la lettre K... 

Le message crypté est alors : XGKX DR SX OFV XGKX GXWWX XVG WF ZRXVGPDS Pour le décrypter, en connaissant les substitutions, on fait l’opération inverse. 

- Avantage : nous allons voir que l’espace des clés est gigantesque et qu’il n’est plus question d’énumérer toutes les possibilités. 
- Inconvénients : la clé à retenir est beaucoup plus longue, puisqu’il faut partager la clé constituée des 26 lettres "FQBMX...". Mais surtout, nous allons voir que finalement ce protocole de chiffrement est assez simple à « craquer ». 

**Attaque statistique** 

La principale faiblesse du chiffrement mono-alphabétique est qu’une même lettre est toujours chiffrée de la même façon. Par exemple, ici E devient X. Dans les textes longs, les lettres n’apparaissent pas avec la même fréquence. Ces fréquences varient suivant la langue utilisée. En français, les lettres les plus rencontrées sont dans l’ordre : 

E S A I N T R U L O D C P M V Q G F H B X J Y Z K W avec les fréquences (souvent proches et dépendant de l’échantillon utilisé) : 



|E |S |A |I |N |T |R |U |L |O |D |
| - | - | - | - | - | - | - | - | - | - | - |
|14\.69% |8\.01% |7\.54% |7\.18% |6\.89% |6\.88% |6\.49% |6\.12% |5\.63% |5\.29% |3\.66% |

Voici la méthode d’attaque : dans le texte crypté, on cherche la lettre qui apparaît le plus, et si le texte est assez long cela devrait être le chiffrement du E, la lettre qui apparaît ensuite dans l’étude des fréquences devrait être le chiffrement du S, puis le chiffrement du A... On obtient des morceaux de texte clair sous la forme d’un texte à trous et il faut ensuite deviner les lettres manquantes. 

Par exemple, déchiffrons la phrase : LHLZ HFQ BC HFFPZ WH YOUPFH MUPZH On compte les apparitions des lettres → H : 6 F : 4 P : 3 Z : 3 

On suppose donc que le H crypte la lettre E, le F la lettre S, ce qui donne : 

\*E\*\* ES\* \*\* ESS\*\* \*E \*\*\*SE \*\*\*\*E ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

D’après les statistiques P et Z devraient se décrypter en A et I (ou I et A). Le quatrième mot "HFFPZ", pour l’instant décrypté en "ESS\*\*", se complète donc en "ESSAI" ou "ESSIA". La première solution semble correcte. Ainsi P crypte A, et Z crypte I. La phrase est maintenant : 

\*E\*I ES\* \*\* ESSAI \*E \*\*\*ASE \*\*AIE 

En réfléchissant un petit peu, on décrypte le message : CECI EST UN ESSAI DE PHRASE VRAIE 

1. Créer un fichier occurrences.py. 
1. Écrire une fonction qui va compter le nombre d’occurrences de chaque lettre dans un texte. On donne le prototype :  

letter\_count(text : str) -> list

- text : texte source 
- la fonction renvoie une liste de valeurs [lettre, occurrences], triée par ordre décroissant selon le nombre d’occurrences de chaque lettre. 

**Aide** :  



<table><tr><th colspan="1">￿ </th><th colspan="1" valign="top">penser à mettre tout le texte en minuscules </th></tr>
<tr><td colspan="1">￿ </td><td colspan="1" valign="top">utiliser  la  méthode  isalpha  pour  ne  sélectionner  que  les  lettres  alphabétiques :</td></tr>
<tr><td colspan="1"></td><td colspan="1">[https://www.geeksforgeeks.org/python-string-isalpha-application/ ](https://www.geeksforgeeks.org/python-string-isalpha-application/)</td></tr>
<tr><td colspan="1">￿ </td><td colspan="1" valign="top">utiliser un dictionnaire pour compter les occurrences de chaque lettre puis créer une liste de listes à partir</td></tr>
<tr><td colspan="1"></td><td colspan="1">du dictionnaire </td></tr>
<tr><td colspan="1">￿ </td><td colspan="1" valign="top">on utilisera une fonction lambda et la méthode sort() pour trier la liste par ordre décroissant de nombre</td></tr>
<tr><td colspan="1"></td><td colspan="1">d’occurrences </td></tr>
<tr><td colspan="1" rowspan="4"></td><td colspan="1"><b>a.sort(key=lambda x: x[1]) => tri la liste a par ordre croissant des nombres en indice 1</b> </td></tr>
<tr><td colspan="1"><b>a.sort(key=lambda x: -x[1]) => tri la liste a par ordre décroissant des nombres en indice 1</b> </td></tr>
<tr><td colspan="1">[https://www.science-emergence.com/Articles/Comment-trier-une-liste-de-tuple-par-rapport-a-un-](https://www.science-emergence.com/Articles/Comment-trier-une-liste-de-tuple-par-rapport-a-un-element-donnee-en-python-/)</td></tr>
<tr><td colspan="1">[element-donnee-en-python-/ ](https://www.science-emergence.com/Articles/Comment-trier-une-liste-de-tuple-par-rapport-a-un-element-donnee-en-python-/)</td></tr>
<tr><td colspan="1"></td><td colspan="1"></td></tr>
</table>



3. Documenter la fonction 
3. Tester la fonction avec le message : ETRE OU NE PAS ETRE TELLE EST LA QUESTION. 
3. Tester la fonction avec le message : Être ou ne pas Être, telle est la question. 
3. Modifier la fonction pour que les lettres accentuées soient considérées comme non accentuées. On ajoutera avant une fonction strip\_accent(text : str) -> str
- text : lettre accentuée 
- la fonction renvoie lettre sans accent 

**Aide** :  

- passer en revue chaque lettre accentuée possible 
7. Documenter la fonction 
7. Tester la fonction avec le message : Être ou ne pas Être, telle est la question. 
7. Écrire une fonction qui va compter le nombre d’occurrences de chaque lettre dans un fichier texte. 

On donne le prototype : count\_in\_file(file : str, encode = 'utf-8') -> list

- file: nom du fichier texte 
- encode : type d’encodage du fichier (défaut utf-8) 
- la fonction renvoie une liste de valeurs [lettre, occurrences], triée par ordre décroissant selon le nombre d’occurrences de chaque lettre ou liste vide si erreur. 

**Aide :** 

- ouvrir le fichier avec la fonction open() et l’attribut ‘r’, ne pas oublier l’encodage du fichier 
- On utilisera la méthode rstrip("\n") pour enlever le symbole.  [https://www.w3schools.com/python/ref_string_rstrip.asp ](https://www.w3schools.com/python/ref_string_rstrip.asp)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)
10. Documenter la fonction 
10. Tester la fonction avec le fichier « book\_vh.txt » dans le dossier Ressources. 

**Résultat attendu** : [['e', 139996], ['a', 67618], ['s', 60385], ['i', 59208], ['t', 58033], ['u', 52989], ['r', 52377], ['n', 51021], ['l', 48412], ['o', 41961], ['d', 30221], ['c', 25215], ['m', 21676], ['p', 21393], ['v', 13206], ['q', 9631], ['g', 8972], ['f', 8856],...]

12. Modifier la fonction pour traiter le cas d’une éventuelle erreur à l’ouverture du fichier (nom incorrect, problème de droits, …). On utilisera le gestionnaire de contexte (context manager). 

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.104.png)

- bloc à coder 

except FileNotFoundError:       return [] 

13. Écrire une fonction qui va filtrer la liste de valeurs [lettre, occurrences] sur les lettres. On donne le prototype : occurrence(sorted\_list : list) -> list
- sorted\_list :  liste  de  valeurs  [lettre,  occurrences],  triée  par  ordre  décroissant  selon  le  nombre d’occurrences de chaque lettre. 
- La fonction renvoie une liste de lettres triées par ordre décroissant de fréquence d’apparition.  

**Aide :** 

- la liste renvoyée par la fonction letter\_count() est déjà triées par ordre décroissant  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.105.png)
- modifier la fonction count\_in\_file() pour qu’elle renvoie la liste de lettres triées par ordre décroissant de fréquence d’apparition en combinant les fonctions 
14. Documenter la fonction précédente 
14. Tester la fonction avec le fichier « book\_vh.txt ». 

**Résultat attendu** : ['e', 'a', 's', 'i', 't', 'u', 'r', 'n',  ...] 

16. Modifier le corps principal du programme pour appeler la fonction occurrence avec tous les fichiers texte d’extension .txt présents dans le répertoire. Conclure. 

**Super Aide :** 

- On codera de cette manière : 

import os ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.106.png)

if \_\_name\_\_ == '\_\_main\_\_': 

`    `files = [ f for f in os.listdir('.') if os.path.isfile(f) and f.startswith("book") ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.107.png)and f.endswith(".txt") ] 

`    `for f in files: 

`        `print(f, ":", count\_in\_file(f)) 

**Le chiffrement de Vigenère** 

L’espace des clés du chiffrement mono-alphabétique est immense, mais le fait qu’une lettre soit toujours cryptée de la même façon représente une trop grande faiblesse. Le chiffrement de Vigenère remédie à ce problème. On regroupe les lettres de notre texte par blocs, par exemple ici par blocs de longueur 4 : 

CETTE PHRASE NE VEUT RIEN DIRE devient : 

CETT EPHR ASEN EVEU TRIE NDIR E 

NB : les espaces sont purement indicatifs, dans la première phrase ils séparent les mots, dans la seconde ils séparent les blocs. 

Si k est la longueur d’un bloc, alors on choisit une clé constituée de k nombres de 0 à 25 : (n 1 ,n 2 ,...,n k ). ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

Le chiffrement consiste à effectuer un chiffrement de César, dont le décalage dépend du rang de la lettre dans le bloc: 

- un décalage de n 1 pour la première lettre de chaque bloc, 
- un décalage de n 2 pour la deuxième lettre de chaque bloc, 
- ... 
- un décalage de n k pour la k-ème et dernière lettre de chaque bloc. 

Pour notre exemple, si on choisit comme clé (3,1,5,2) alors pour le premier bloc "CETT" : 

- un décalage de 3 pour C donne F, 
- un décalage de 1 pour E donne F, 
- un décalage de 5 pour le premier T donne Y, 
- un décalage de 2 pour le deuxième T donne V. 

Ainsi "CETT" de vient "FFYV". Vous remarquez que les deux lettres T ne sont pas cryptées par la même lettre et que les deux F ne cryptent pas la même lettre. On continue ensuite avec le deuxième bloc... 

**Espace des clés et attaque** 

Il y a 26 k choix possibles de clés, lorsque les blocs sont de longueur k. Pour des blocs de longueur k = 4 cela en donne déjà 456 976, et même si un ordinateur teste toutes les combinaisons possibles sans problème, il n’est pas question de parcourir cette liste pour trouver le message en clair, c’est-à-dire celui qui est compréhensible ! 

Il persiste tout de même une faiblesse du même ordre que celle rencontrée dans le chiffrement mono- alphabétique : la lettre A n’est pas toujours cryptée par la même lettre, mais si deux lettres A sont situées à la même position dans deux blocs différents (comme par exemple "ALPH ABET") alors elles seront cryptées par la même lettre. 

Une attaque possible est donc la suivante : on découpe notre message en plusieurs listes, les premières lettres de chaque bloc, les deuxièmes lettres de chaque bloc... et on fait une attaque statistique sur chacun de ces regroupements. Ce type d’attaque n’est possible que si la taille des blocs est petite devant la longueur du texte. 

**Algorithme** 

Voici un petit algorithme correspondant au chiffrement de Vigenère. 

Algorithme vigenere ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.108.png)

{ attaque par force brute du chiffrement de Vigenere } 

variables 

i, j, k, index : entier 

clef : tableau[1..3] d’entiers 

car : caractère 

texte\_codé : chaîne := "ZCNUVJ LUYLNQL GXA PFPPJ LV XHKSA UFL…. (voir plus bas)" début 

Pour i := 1 à 26 faire 

Pour j := 1 à 26 faire 

Pour k := 1 à 26 faire 

clef := [i, j, k] 

index := 0 

afficher(clef) 

Pour car dans texte\_codé faire 

si car < 'A' OU car > 'Z' alors 

afficher(car) 

sinon 

afficher(caesar(car, clef[index])) 

index := (index + 1) modulo taille(clef) 

fin ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Chiffrement mono-alphabétique (**★★★★)** 

Le texte (en français) suivant a été chiffré par un code mono alphabétique. Déterminer l’auteur de ce texte. eposal, epg r’sjnp, s r’upjdp cj nrsliuaq rs isohsmlp, vp hsdqadsa. bcag-qj, vp gsag tjp qj o’sqqpleg. 

17. Créer un fichier substitution.py.
17. Afficher les occurrences des lettres du texte chiffré ci-dessus à l’aide de la fonction letter\_count() du et la fonction occurrence() module occurrences.py.

**Résultat attendu** : [['s', 11], ['p', 10],…]

**Aide :** 

- Importer les fonctions letter\_count() et occurrence()![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.109.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.110.png)
19. Enregistrer ces occurrences dans une liste : entree.
19. Enregistrer les occurrences usuelles pour un texte en français dans une liste**  

sortie = ['a', 'e', 'i', 't', 'u', 's', 'l', 'n', 'd', 'm', 'r', 'b', 'h', 'p', 'c', 'o', 'j', 'g', 'q', 'v']

21. Écrire un programme qui substitue les lettres de la liste entree par celles de la liste sortie en fonctions des occurrences rencontrées. 

**Aide :**  

- On pourra utiliser la méthode index()![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.111.png)
- il est possible que l’ordre des occurrences de la liste de sortie ne coïncide pas totalement avec les occurrences de la liste d’entrée. 

**Chiffrement de Vigenère avec clef** 

Le texte suivant a été chiffré par un chiffrement de Vigenère avec une clef de longueur 3. Quel prénom féminin apparaît dans ce texte ? 

ZCNUVJ LUYLNQL GXA PFPPJ LV XHKSA UFLPX HXJJ UFPPYL GXAGQSG JZV SHKSL GY ZCNUV XHGSZ CALE XHKSAG JZVJSNJ LUY UCNUG JA UFPPY ZCJUU FCGH 

**Indice** : le texte en clair contient le mot SAINT. 

22. Créer un fichier vigenere.py. 
22. Implémenter l’algorithme précédent. 

**Aide :**  

- ne pas revenir à la ligne après chaque print (afficher) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.112.png)
- utiliser la fonction caesar() développée dans le module de l’activité précédente. ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.113.png)
- Mettre  à la fin du script un print() indenté comme la dernière boucle for (pour un retour à la ligne) ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.114.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

**Exercice 15 :** ★★★ **Séquences nucléiques  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.115.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.116.png)Acide nucléique**  

La  **séquence**  d'un [ acide  nucléique ](https://fr.wikipedia.org/wiki/Acide_nuclÃ©ique) — [ ADN ](https://fr.wikipedia.org/wiki/Acide_dÃ©soxyribonuclÃ©ique) ou [ ARN ](https://fr.wikipedia.org/wiki/Acide_ribonuclÃ©ique) —  est  la  succession  des [ nucléotides ](https://fr.wikipedia.org/wiki/NuclÃ©otide) qui  le  constituent.  Cette  succession  contient l['information génétique ](https://fr.wikipedia.org/wiki/Information_gÃ©nÃ©tique)portée par ces[ polynucléotides,](https://fr.wikipedia.org/wiki/PolynuclÃ©otide) de  sorte qu'on la qualifie également de **séquence génétique**. Elle peut  être déterminée par des méthodes de[ séquençage de l'ADN.](https://fr.wikipedia.org/wiki/SÃ©quenÃ§age_de_l%27ADN)  

Les molécules représentées dans ce schéma sont :  

- l'**ADN**  :  support  stable  et  transmissible  de  l'information  ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.117.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.118.png)génétique. Il est composé des 4 nucléotides suivants (appelés aussi  bases) : A = adénine, T = thymine, G = guanine et C = cytosine.  Dans les cellules vivantes, l'ADN est sous la forme double brin,  c'est-à-dire que 2 séquences ADN se font face. Une séquence est  lue de gauche à droite et l'autre de droite à gauche. De plus, les  bases complémentaires l'une de l'autre se font face (A et T sont  complémentaires, G et C sont complémentaires). Un brin est donc  complémentaire et inversé par rapport à l'autre.  
- l'**ARN**  :  support  temporaire  permettant  l'expression  de  l'information génétique. Il est composé des 4 nucléotides suivants  
  - A = adénine, U = uracile, G = guanine et C = cytosine.  
- les **protéines** : outils de la cellule (enzymes, transporteurs, etc.).  Elles sont composées de 20 acides aminés différents.  

Les processus du dogme central de la biologie moléculaire, réalisés par les cellules sont les suivants : 

1. la **transcription** 
1. la **traduction** 
1. la **réplication** 

**Les séquences ADN** 

1. Créer un fichier dna.py.
1. Écrire une fonction qui vérifie si une chaîne de caractères correspond à un brin d’ADN :  cette chaîne ne doit contenir aucun autre caractère que les quatre bases A, C, G et T. Le prototype de la fonction est le suivant : 



<table><tr><th colspan="5">is_DNA_strand(strand : str) -> bool</th><th colspan="3"></th></tr>
<tr><td colspan="1" rowspan="2" valign="bottom">￿ </td><td colspan="1"></td><td colspan="2" valign="bottom">: brin d’ADN (de 1 à n </td><td colspan="3" valign="bottom">bases) </td></tr>
<tr><td colspan="2" valign="top">strand</td><td colspan="3" valign="bottom"></td><td colspan="3" valign="bottom"></td></tr>
</table>
- la fonction renvoie True si la chaîne est un brin d’ADN, False sinon 
3. Documenter la fonction 
3. Créer un fichier dna\_test.py et valider les tests unitaires suivants : 

is\_DNA\_strand("ATGCGATC") == True is\_DNA\_strand("ACKT") == False is\_DNA\_strand("") == False is\_DNA\_strand(0) == False ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.119.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)

Il est possible de générer aléatoirement une séquence ADN. La version naïve suppose que les 4 bases ont la même probabilité d'apparaître à une position donnée. 

5. Écrire une fonction qui renvoie un brin d’ADN généré aléatoirement. Le prototype de la fonction est le suivant : generate\_DNA\_strand(size : int) -> str
- size : taille du brin d’ADN (≥ 2) 
- la fonction renvoie un brin d’ADN généré aléatoirement 
6. Documenter la fonction 
6. Valider les tests unitaires suivants : 

is\_DNA\_strand(generate\_DNA\_strand(x)) pour différentes valeurs de x (au choix). 

**La transcription** 

Certaines parties spécifiques de l'ADN sont transcrites en ARN. La transcription consiste en l'assemblage de nucléotides ARN en suivant le modèle ADN et en prenant les bases complémentaires. Dans l'ADN, les bases A et T sont complémentaires, ainsi que les bases G et C. Pour passer de l'ADN à l'ARN, le A est transformé en U, le T en A, le G en C et le C en G. 

8. Écrire une fonction qui renvoie la base complémentaire. Le prototype de la fonction est le suivant : 



<table><tr><th colspan="5">complementary_base(base : str, type : str) -> st</th><th colspan="3">r </th></tr>
<tr><td colspan="1" rowspan="3" valign="top">￿ ￿ </td><td colspan="1"></td><td colspan="2" valign="bottom"><p>: nucléotide (A, T, G ou C) </p><p>` `de séquence : 'ADN' ou 'ARN' </p><p>￿  la fonction renvoie la base complémentaire, ou None si erreu</p></td><td colspan="3" valign="bottom">r </td></tr>
<tr><td colspan="2">base</td><td colspan="3" rowspan="2" valign="bottom"></td><td colspan="3" rowspan="2" valign="bottom"></td></tr>
<tr><td colspan="2" valign="top">type</td></tr>
</table>
**Aide :** 

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.120.png)

- bloc à coder 

except #exception à trouver: 

- bloc à coder 
9. Documenter la fonction 
9. Valider les tests unitaires suivants : 

complementary\_base('G', 'ADN') == 'C' complementary\_base('A', 'ARN') == 'U' complementary\_base('K', 'ADN') == None complementary\_base('G', 'ABC') == None![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.121.png) 

11. Écrire une fonction qui renvoie l'ARN construit à partir de la sous-séquence d'un brin d’ADN comprise entre les deux positions passées en paramètre, incluses. Le prototype de la fonction est le suivant : 



|transcription(strand : str, start : int, end : int) -> st|r |||
| - | - | :- | :- |
|<p>- strand : brin d’ADN </p><p>- start : position de départ dans la séquence du brin d’ADN </p><p>- end : position de fin dans la séquence du brin d’ADN </p><p>- la fonction renvoie  la séquence complémentaire du brin d’ADN transcri</p>|t, ou None si erreur |||

**Aide** : 

try : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.122.png)

- bloc à coder 

assert 

… 

except #exception à trouver: 

- bloc à coder 
12. Documenter la fonction ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)
13. Valider les tests unitaires suivants : 

transcription('TTCTTCTTCGTAC', 4, 10) == 'AAGAAGC' transcription('TTCTTCTTCGTAC', 4, 3) == None transcription('TTCTTCTTCGTAC', 10, 40) == 'CAUG' transcription('TTCTTCTTCGTAC', -4, 0) == None transcription('TTCTTCTTCGTAC', -4, 4) == None ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.123.png)

**La traduction** 

Les ARN messagers sont traduits en protéines. Le passage d'une séquence ARN composée de 4 nucléotides à une séquence protéique composée de 20 acides aminés, se fait à l'aide du code génétique. Dans ce code, chaque mot de 3 bases, appelé codon, correspond à un acide aminé. Il est possible de construire 4³ = 64 codons différents à l'aide des 4 bases. Ce code est donc dégénéré : plusieurs codons correspondent au même acide aminé. Les codons sont lus sans chevauchement, les uns à la suite des autres. 

Les acides aminés sont désignés par une lettre qui représente la forme du nom abrévié. **Le code génétique :** 

'UUU', 'UUC' : 'F' ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.124.png)

'UUA', 'UUG', 'CUU', 'CUC', 'CUA', 'CUG' :   'L' 'AUU', 'AUC', 'AUA' :    'I' 'AUG' :   'M' 'GUU', 'GUC', 'GUA', 'GUG' :    'V' 'UCU', 'UCC', 'UCA', 'UCG', 'AGU', 'AGC' :   'S' 'CCU', 'CCC', 'CCA', 'CCG' : 'P' 

'ACU', 'ACC', 'ACA', 'ACG' : 'T' 

'GCU', 'GCC', 'GCA', 'GCG' : 'A' 'UAU', 'UAC' :    'Y' 'UAA', 'UAG', 'UGA' :    '\*' 'CAU', 'CAC' : 'H' 

'CAA', 'CAG' : 'Q' 

'AAU', 'AAC' : 'N' 

'AAA', 'AAG' : 'K' 

'GAU', 'GAC' : 'D' 

'GAA', 'GAG' : 'E' 

'UGU', 'UGC' : 'C' 'UGG' :   'W' 'CGU', 'CGC', 'CGA', 'CGG', 'AGA', 'AGG' :   'R' 'GGU', 'GGC', 'GGA', 'GGG' :    'G' 

14. Écrire une fonction qui renvoie l'acide aminé correspondant au codon (ou \* pour les codons Stop). Le prototype de la fonction est le suivant : 



<table><tr><th colspan="5">genetic_code(codon: str) -> st</th><th colspan="3">r </th></tr>
<tr><td colspan="1" rowspan="2" valign="bottom">￿ </td><td colspan="1"></td><td colspan="2" valign="bottom">: codon (succession de trois le</td><td colspan="3" valign="bottom">ttres (voir ci-dessus)) </td></tr>
<tr><td colspan="2">codon</td><td colspan="3" valign="bottom"></td><td colspan="3" valign="bottom"></td></tr>
</table>
- la fonction renvoie  l'acide aminé sous la forme du nom abrévié, ou None si erreur 
15. Documenter la fonction 
15. Valider les tests unitaires suivants : 

genetic\_code('UGA') == '\*' genetic\_code('AAAA') == None genetic\_code('XYZ') == None genetic\_code(0) == None ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.125.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.094.png)

Première NSI   Chap 34 : Les types construits  Page 34/35 

17. Écrire une fonction qui renvoie la séquence protéique obtenue par la traduction de la séquence ARN. Cette traduction se fait à partir du premier nucléotide de la séquence ARN. Le prototype de la fonction est le suivant : 



|traduction(arn : str) -> st|r |||
| - | - | :- | :- |
|<p>- arn : structure ARN </p><p>- la fonction renvoie la séquence p</p>|rotéique c’est-à-dire les noms abrégés pour chaque codon, ou None|||

si erreur 

18. Documenter la fonction 
18. Valider les tests unitaires suivants : 

traduction('AUGCGAAGCCGAAAGAACACCGGCUAA') == 'MRSRKNTG\*' traduction('AUGCGAAGCCGAAAGAACACCGGCUA') == None traduction(0) == None ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.126.png)

**La réplication** 

L'ADN de chaque brin d'une double hélice est recopié de telle sorte que deux nouvelles doubles hélices sont produites, identiques à l'unique double hélice qui a servi de modèle. 

De  simples  chaînes  de  caractères  permettent  de  représenter  les  séquences  biologiques  et  les  fonctions programmées vont reproduire les processus. 

20. Écrire une fonction qui renvoie la base complémentaire. Le prototype de la fonction est le suivant : 



<table><tr><th colspan="6">replication(strand : str) -> st</th><th colspan="3">r </th></tr>
<tr><td colspan="1" rowspan="2" valign="top">￿ </td><td colspan="1"></td><td colspan="2" valign="bottom"><p>: brin d’ADN </p><p>￿  la fonction renvoie la séquence ADN </p></td><td colspan="3" valign="bottom">complémentaire et inversée (A et C sont complémentaires, T</td></tr>
<tr><td colspan="2" valign="top">strand</td><td colspan="2" valign="bottom"></td><td colspan="3" valign="bottom"></td></tr>
</table>
et G sont complémentaires), ou None si erreur 

21. Documenter la fonction 
21. Valider les tests unitaires suivants : 

replication('ACTG') == 'CAGT' replication('') == None replication(0) == None ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.127.png)

23. Créer un fichier dna\_main.py.
23. Écrire un programme qui demande de façon interactive de saisir une séquence ARN et afficher la séquence d’acides aminés correspondante. Par exemple : ![](Aspose.Words.27dc2d78-26ce-4ee4-872c-63e471312ff5.010.png)



|>>> entrez une séquence ARN>? AUGCGAAGCCGAAAGAACACCGGCUAA |
| - |
|MRSRKNTG\* |

Première NSI   Chap 5 : Les types construits  Page 35/35 

[^1]: Depuis la fin 2018, la bibliothèque Python GPSPhoto permet d’obtenir directement les coordonnées géographiques d’une photo. 