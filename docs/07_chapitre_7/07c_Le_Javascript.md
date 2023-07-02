---
author: ELP
title: 07c Le Javascript
--- 

**Table des matières** 

1. [Qu'est-ce que JavaScript et à quoi sert-il ? ](#_page0_x40.00_y687.92)
2. [Comment utiliser JavaScript avec HTML et CSS ?](#_page1_x40.00_y280.92)
3. [La syntaxe ](#_page2_x40.00_y113.92)
4. [Boite de dialogue](#_page2_x40.00_y237.92)
5. [Les variables](#_page2_x40.00_y641.92)
6. [Les conditions](#_page4_x40.00_y693.92)
7. [Les opérateurs logiques](#_page6_x40.00_y544.92)
8. [Les boucles](#_page6_x40.00_y626.92)
9. [Les fonctions](#_page7_x40.00_y654.92)
10. [Modeler des pages web avec js ](#_page8_x40.00_y524.92)
11. [Interactions avec l’utilisateur ](#_page14_x40.00_y95.92)
12. [Exercices ](#_page18_x40.00_y36.92)


## **1. Qu'est-ce que JavaScript et à quoi sert-il ? <a name="_page0_x40.00_y687.92"></a> **
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.004.png)

JavaScript est un langage de programmation de scripts côté client. Il est utilisé pour créer des  pages web **interactives** et **dynamiques** en ajoutant des fonctionnalités telles que les  **animations**, les **formulaires interactifs**, les **scripts de validation**, les **galeries d'images,** etc.  sans avoir besoin de charger une nouvelle page du serveur. 

JavaScript  peut  être  utilisé  conjointement  avec  HTML  et  CSS  pour  créer  des  pages  web  complètes et riches en fonctionnalités. Il fonctionne dans les navigateurs web modernes sur les  ordinateurs de bureau et les appareils mobiles, ce qui en fait un outil de développement web très puissant et largement utilisé.s![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.005.png)

Le Javascript est un langage dit **client-side** c’est-à-dire que les scripts sont exécutés par le navigateur chez ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.006.png)![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.007.png)![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.008.png)l’internaute. 

Pour cela :  

- votre ordinateur récupère le code  source d'une page web sur un  serveur.  
- votre navigateur interprète la  page et les scripts qu'elle  contient.  
- la page formatée s'affiche sur  votre écran. Les scripts, quant à  eux, sont mis en mémoire et  seront lancés dès que l'événement  attendu se produira  
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.009.png)

## **2. Comment<a name="_page1_x40.00_y280.92"></a> utiliser JavaScript avec HTML et CSS ?** 
### **2.1. Cas<a name="_page1_x40.00_y302.92"></a> général :** 

En intégrant le code JavaScript directement dans la page HTML, à l'intérieur de la balise ```<script>``` et ```</script>``` 
```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      /* Votre feuille de style CSS */
    </style>
  </head>
  <body>
    <!-- Votre contenu HTML -->
    <script>
      // Votre code JavaScript
    </script>
  </body>
</html>
```

On peut les placer **soit dans l'en-tête** (```<head>``` ... ```</head>```;), **soit dans le corps** (```<body>``` ... ```</body>```;) de la page HTML. 

### **2.2. Fichier<a name="_page1_x40.00_y558.92"></a> js externalisé  **
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.013.png)

Pour bien faire on externalise dans un dossier js. 

On écrit le javascript dans un fichier script.js que l’on mettra aussi  dans le dossier js.  

**Activité n°1.:** Dans la index.html rajouter le lien vers le fichier js 
```html
<!DOCTYPE html>
    <head>
        <meta charset="utf-8" />
        <link rel="stylesheet" href="css/style.css" />
        <script type="text/javascript" src="js/script.js"></script>
        <title>Logique sur les passoires</title>
    </head>
```


```type="text/javascript"``` est facultatif 

Créer un nouveau fichier vide avec l’éditeur. Enregistrer-le dans le dossier js sous le nom ***script.js***  ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.005.png)

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.015.png)

## **3. La<a name="_page2_x40.00_y113.92"></a> syntaxe** 
- Les instructions sont séparées par des **points-virgules** 
- Les commentaires se placent entre ```/*``` et ```*/``` 
- Les scripts peuvent s’intégrer directement dans la page dans des balise ```<script>``` ou peuvent être dans un fichier .js par exemple : ```<script src="js/hello.js"></script>``` 
## **4. Boite<a name="_page2_x40.00_y237.92"></a> de dialogue** 

Le fichier javascript est appelé depuis la page Web au moyen de l’élément ```<script>``` et ```scr``` avec l’URL du fichier .js*.* 
La fonction ```alert()``` existe déjà dans javascript donc on peut directement l’écrire dans la page Web. 

**Activité n°2.:** Dans la index.html rajouter n’importe où dans les balises ```<body>``` 
```html
<script>
     </script>
```

Enregistrer et observer la index.html dans Firefox. 

Externalisons le code :  



**Activité n°3.**Dans le fichier script.js écrire le script suivant :
```js
alert('Hello world!');
```


Enregistrer le tout et observer la index.html dans Firefox  La suite du cours sur le javascript se fera sur des fichiers  extérieurs.  

**Activité n°4.:** Dans une nouvelle page html que l’on appelera exo\_JS.html rajouter le lien vers le fichier js. Le fichier sera enregistré dans le dossier Documents\site. 

```html
<!DOCTYPE html>
    <head>
        <meta charset="utf-8" />
        <script type="text/javascript" src="js/exo.js"></script>
        <title>Page de tests du code js</title>
    </head>
    <body>
        Page de tests du code JS
    </body>
</html>
```



Créer un nouveau fichier vide avec l’éditeur. Enregistrer-le dans le dossier js sous le nom exo.js

## **5. Les<a name="_page2_x40.00_y641.92"></a> variables** 
### **5.1. Déclarer<a name="_page2_x40.00_y663.92"></a> une variable** 

```let``` permet de déclarer des variables dont la **portée est limitée** à celle du bloc dans lequel elles sont déclarées. Le mot-clé ```var``` , quant à lui, permet de définir une **variable globale ou locale** à une fonction (sans distinction des blocs utilisés dans la fonction). 

La déclaration d’une variable se fait avec le mot clé *var* ou *const* (mais elle a besoin d’une valeur initiale): 

- ```var maVariable ; maVariable = 5 ;``` 
- ou ```var message = "Bonjour, visiteur";``` 

**Activité n°5.:** Dans le fichier *exo.js* écrire le script suivant.  
Enregistrer et observer le fichier *exo\_JS.html* dans Firefox.     
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.024.png)
```JS
var myVariable = 5.5;
alert(myVariable);  
```
### **5.2. Les<a name="_page3_x40.00_y137.92"></a> types de variables  **
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.026.png)

Le Javascript est un langage typé dynamiquement : on n’a pas besoin de déclarer le type des variables. Il existe trois types principaux de variable : 

- Les **numbers**  
- Les **strings**  
- Les **booleans**  

### **5.3. Les<a name="_page3_x40.00_y247.92"></a> chaines de caractères**  

Pour inclure des guillemets " ou des apostrophes dans une chaînes, il faut utiliser le caractère d'échappement \ (antislash). 

Exemple : 
```JS
// deux chaines de caracteres
var message1 = "Ceci est un \"petit\" test (pas besoin d'antislash \).";
var message2 = 'Un autre "petit" test (attention à l\'antislash)';

// maintenant, on les affiche
alert(message1);
alert(message2);
```


On peut également insérer des retours à la ligne ainsi que des tabulations avec des caractères spéciaux : 

- ```\n``` : retour à la ligne. 
- ```\t``` : une tabulation (ne marche pas dans tous les cas) 
- ```\b``` : pour insérer un backspace (touche "retour arrière") 
- ```\uXXXX``` : pour insérer le caractère donc la[ valeur unicode ](http://fr.wikipedia.org/wiki/Table_des_caractÃ¨res_Unicode)est XXXX (en hexadécimales). 
### **5.4. Tester<a name="_page3_x40.00_y503.92"></a> l’existence de variables avec typeof![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.029.png)**

L’instruction ```typeof``` permet de tester l’existence d’une variable ou d’en vérifier son type. Par exemple : 

**Activité n°6.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var number = 2;
alert(typeof number); 

var text = 'Mon texte';
alert(typeof text); 

var aBoolean = false;
alert(typeof aBoolean); 
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.031.png) 

### **5.5. Les<a name="_page3_x40.00_y706.92"></a> calculs** 

Tous les opérateurs classiques peuvent être utilisée. Ainsi on pourra écrire 

**Activité n°7.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var divisor = 3, result1, result2, result3; 
result1 = (16 + 8) / 2 - 2 ; 
result2 = result1 / divisor; 
result3 = result1 % divisor; 

alert(result2); 
alert(result3); 
```
 

### **5.6. La<a name="_page4_x40.00_y154.92"></a> concaténation** 

**Activité n°8.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var hi = 'Bonjour ', name = 'toi', result; 
result = hi + name;  
alert(result); 
```  
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.034.png)

On peut aussi concaténer des chaines de caractères et un  nombre.  

### **5.7. Interagir<a name="_page4_x40.00_y286.92"></a> avec l’utilisateur** 

Avec la fonction prompt(). Elle s’utilise comme alert(). Elle renvoie ce que l’utilisateur a écrit sous forme d’une chaine de caractère. 

**Activité n°9.:** Dans le fichier exo.js passer les lignes  précédentes en  commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le  fichier exo\_JS.html dans Firefox.  
```JS
var userName = prompt('Entrez votre prénom :');  
alert(userName);   
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.036.png)

On peut également  dire bonjour à nos visiteurs 

**Activité n°10.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var start = 'Bonjour ', name, end = ' !', result; 

name   = prompt('Quel est votre prénom ?'); 
result = start + name + end; 
alert(result); 
```
Tout ce qui est récupéré avec ```prompt()``` est sous forme d’une chaine de caractères. Pour convertir la chaine de caractères en **nombre entier** on utilise la fonction ```parseInt()```*.* On pourra utiliser la fonction ```parseFloat()``` pour convertir une chaine de caractère en nombre décimal.* Par exemple 

**Activité n°11.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var first, second, result;  
first = prompt('Entrez le premier chiffre :');  
second = prompt('Entrez le second chiffre :');  
result = parseInt(first) + parseInt(second);  
alert(result); 
```
## **6. Les<a name="_page4_x40.00_y693.92"></a> conditions** 
### **6.1. Les<a name="_page4_x40.00_y715.92"></a> opérateur de condition** 

Les opérations de comparaison classiques sont les mêmes : ```==``` ; ```!= ```; ```<``` ; ```<=``` etc 

Pour pouvoir comparer 4 en tant que ```number``` et 4 en tant que string  il faut utiliser d’autres opérateurs : 

**Activité n°12.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var number = 4, text = '4', result; 

result = number == text; 
alert(result); // Affiche  « true » alors que « number » est un nombre et « text » une chaîn e de caractères![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.041.png) 

result = number === text; 
alert(result); // Affiche « false » car cet opérateur compare aussi les types des variables en plus de leurs valeurs ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.042.png)
```

### **6.2. Les<a name="_page5_x40.00_y167.92"></a> structures conditionnelles** 
#### **6.2.1. La<a name="_page5_x40.00_y186.92"></a> condition « if else *»* ** 

**Activité n°13.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var userName = prompt('Entrez votre prénom :'); 

if (2 < 8 && 8 >= 4) { // Cette condition renvoie « true », le code est donc exécuté     
alert('La condition est bien vérifiée.'); 
} 
alert(userName);  
```

La fonction ```confirm()```. On lui passe en paramètre une chaine de caractère qui sera affichée à l’écran et elle retourne un booléen en fonction de l’action de l’utilisateur. 

**Activité n°14.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
if (confirm('Voulez-vous exécuter le code JavaScript de cette page ?')) { 
   alert('Le code a bien été exécuté !')}; 
```
Relancer la Web exo\_Js.html en choisissant l’autre proposition. 

La structure ```else``` existe également et permet d’exécuter un certain code si la condition n’a pas été vérifié. Par contre il est conseillé de l’écrire ainsi (directement après l’accolade de fermeture de la structure ```if```) : 
```JS
if ( /* condition */ ) {
    // Du code…
} else {
    // Du code…
}
```
La structure ```else if```  peut être aussi utilisé ainsi 
```JS
if ( /* condition */ ) {
    // Du code…
} else if ( /* condition */ ) {
    // Du code…
} else {
    // Du code…
}
```


#### **6.2.2. La<a name="_page5_x40.00_y659.92"></a> condition ```switch```**

Supposons qu’on est besoin de nombreux ```else if``` les uns à la suite des autres. Par exemple : 

**Activité n°15.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var tiroir = parseInt(prompt('Choisissez le tiroir à ouvrir (1 à 4) :')); 
if (tiroir == 1) { 
   alert('Contient divers outils pour dessiner : du papier, des crayons, etc.'); 
} else if (tiroir == 2) { 
   alert('Contient du matériel informatique : des câbles, des composants, etc.'); 
} else if (tiroir == 3) { 
   alert('Ah ? Ce tiroir est fermé à clé ! Dommage !'); 
} else if (tiroir == 4) { 
   alert('Contient des vêtements : des chemises, des pantalons, etc.'); 
} else { 
   alert("Info du jour : le meuble ne contient que 4 tiroirs et, jusqu'à preuve du contrair e, les tiroirs négatifs n'existent pas."); 
} 
```
Avec ```switch``` c'est un peu plus facile : 

**Activité n°16.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var tiroir = parseInt(prompt('Choisissez le tiroir à ouvrir (1 à 4) :'));

switch (tiroir) {
    case 1:
        alert('Contient divers outils pour dessiner : du papier, des crayons, etc.');
    break;

    case 2:
        alert('Contient du matériel informatique : des câbles, des composants, etc.');
    break;

    case 3:
        alert('Ah ? Ce tiroir est fermé à clé ! Dommage !');
    break;

    case 4:
        alert('Contient des vêtements : des chemises, des pantalons, etc.');
    break;

    default:
        alert("Info du jour : le meuble ne contient que 4 tiroirs et, jusqu'à preuve du contraire, les tiroirs négatifs n'existent pas.");
}
```
Tout ce qui suit les deux points d’un ```case``` sera exécuté si la variable analysée par le ```switch``` contient la valeur du ```case```. A chaque fin d’un ```case``` on écrit l’instruction ```break``` pour casser le ```switch``` et éviter d’afficher les autres alertes. 

La partie ```default``` est optionnel.  

## **7. Les<a name="_page6_x40.00_y544.92"></a> opérateurs logiques  **
- L’opérateur ET se note ```&&``` 
- L’opérateur OU se note ```||```  (Alt Gr +6)  
- L’opérateur NON se note comme en Python avec ```!``` 

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.059.png)

## **8. Les<a name="_page6_x40.00_y626.92"></a> boucles** 
### **8.1. L’incrémentation<a name="_page6_x40.00_y648.92"></a>** 

L’incrémentation permet d’ajouter une unité à un nombre et à l’inverse, la décrémentation permet de soustraire une unité. 

**Activité n°17.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var number1 = 0, number2 = 0; 

number1++; 
alert(number1); 

number2--; 
alert(number2) ; 
```
La position de l’opérateur ```++``` est important si on veut récupérer le résultat de l’incrémentation :  ```var number = 0;``` Il y a deux possibilités : 

- ```var output = ++number;``` → retournera 1 car retourne la valeur de number incrémentée 
- ```var output = number++``` → retournera 0 car retourne la valeur de number avant incrémentation 

### **8.2. la<a name="_page7_x40.00_y168.92"></a> boucle while** 

A chaque fois que la boucle se répète on parle d’itération. Par exemple :  

**Activité n°18.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
var number = 1; 

while (number < 10) {     
   number++; 
} 
alert(number); 
```

### **8.3. la<a name="_page7_x40.00_y328.92"></a> boucle do while**

La boucle ```do while``` ressemble très fortement à la boucle ```while```, sauf que dans ce cas la boucle est toujours exécutée au moins une fois. La syntaxe d'une boucle ```do while```: 
```JS
do {
    instruction_1;
    instruction_2;
    instruction_3;
} while (condition);
```

### **8.4. La<a name="_page7_x40.00_y446.92"></a> boucle for** 

Le schéma d’une boucle ```for``` : 
```JS
for (initialisation; condition; incrémentation) {
    instruction_1;
    instruction_2;
    instruction_3;
}
```


**Activité n°19.:** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
for (var iter = 0; iter < 5; iter++) { 
   alert('Itération n°' + iter); 
} 
```
Attention les variables utilisées dans la boucle ```while```  ou dans la boucle ```for``` ne sont pas détruites (comme dans Python) une fois sortie de la boucle. 

## **9. Les<a name="_page7_x40.00_y654.92"></a> fonctions** 

Pour définir une fonction il faut le script suivant : 
```JS
function* myFunction(arguments) { 
   // Le code que la fonction va devoir exécuter
} 
```

**Activité n°20.: Exemple de fonction sans argument** : Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
function showMsg() { 
   alert('Et une première fonction, une !');
} 
showMsg(); // On exécute ici le code contenu dans la fonction 
```

La fonction ```showMsg()``` exécute elle-même une autre fonction qui n'est autre que ```alert()``` avec un message prédéfini. Bien sûr, tout code écrit dans une fonction ne s'exécute pas immédiatement, sinon aucun intérêt. C'est pourquoi à la **fin du code on appelle la fonction** afin de l'exécuter, ce qui affiche le message souhaité. 

Toute variable déclarée dans une fonction n'est utilisable que dans cette même fonction. Ce sont les variables locales. 

**Activité n°21.: Exemple de fonction avec argument** : Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
function myFunction(arg) { // Notre argument est la variable « arg » 
   // Une fois que l'argument a été passé à la fonction, vous allez le retrouver dans la va riable « arg »
   alert('Votre argument : ' + arg); 
} 
myFunction('En voilà un beau test !'); 
```

**Activité n°22.: Exemple de fonction avec** ```prompt()``` *:* Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
function myFunction(arg) { 
   alert('Votre argument : ' + arg); 
} 
myFunction(prompt('Que souhaitez-vous passer en argument à la fonction ?')); 
```
**Activité n°23.: Exemple de fonction avec un ```return```** *:* Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo\_JS.html dans Firefox. 
```JS
function sayHello() {
   return 'Bonjour !'; 
   alert('Attention ! Le texte arrive !'); 
} 
alert(sayHello()); 
```
## **10. Modeler<a name="_page8_x40.00_y524.92"></a> des pages web avec js**

Le Javascript va modifier les pages html et css en accédant aux éléments cible du DOM (Document Objet Model).  

### **10.1. Manipuler<a name="_page8_x40.00_y578.92"></a> les éléments HTML**  
- **Sélection des éléments par ID** : pour sélectionner un élément HTML en utilisant son ID, nous pouvons utiliser la méthode ```getElementById()```
```html
    <body>
        <p id = "titre"> je représente le titre qui va être modifié car j'ai le bon id</p>
        <script>
        var titre = document.getElementById("titre");
        titre.style.color = "blue";
        </script>
    </body>
```

- **Sélection des éléments par nom de classe** : pour sélectionner plusieurs éléments HTML qui ont la même classe, nous pouvons utiliser la méthode ```getElementByClassName()```. Par exemple : 
```html
    <body>
        <p class = "paragraphe"> je représente </br>le paragraphe </br> qui va être modifié </br> car j'ai la bonne classe</p>
        <script>
            var paragraphes = document.getElementsByClassName("paragraphe");
            for (var i = 0; i < paragraphes.length; i++) {
            paragraphes[i].style.backgroundColor = "yellow";
            }
        </script>
    </body>
```


Trouve tous les éléments ayant la classe « paragraphe »  
**Activité n°24.:** Créer un fichier interaction.html*,* dans site et saisir le code ci-dessous.

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.081.png)
```html
<!DOCTYPE html>
<head>
    <meta charset="UTF-8">
    <title>Interaction html/css et JS</title>
</head>
<body>
    <h1>Voici un joli titre.</h1>
    <p id='important'>Ceci est un texte qu'il faut mettre en valeur !</p>
    <button onclick="change_couleur()">Cliquez ici !</button>
</body>
<script src="js/interaction.js"></script>
</html>
```


Dans le code précédent, ```<button onclick="change\_couleur()">Cliquez ici !</button>``` est une balise qui va créer **un bouton.**  

Un click dessus va déclencher la fonction ```change_couleur()``` 

Cette fonction va être définie dans un fichier javascript (interraction.js) qui va être créé par ce qui suit ... Ensuite créez un fichier interaction.js dans le sous-dossier js. Saisir le code suivant. Puis enregistrer et observer le fichier interaction.html dans Firefox. 
```JS
function change_couleur() {
    var paragraphe = document.getElementById("important");
    console.log(paragraphe);
}
```


Ouvrez la console des outils de développement web (CTRL Maj I). Cliquer sur le bouton et observer dans console : 

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.086.png)

Vous devez constater que la variable paragraphe contient maintenant la balise paragraphe et son contenu. Dans la variable paragraphe, l'élément d'ID (identifiant) "important" est stocké. 

**Activité n°25.:** Ajouter le code ci-dessous à la fonction du fichier js. Puis  enregistrer et observer le fichier interaction.html dans Firefox.  
```JS
paragraphe.style.color="red"; 
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.087.png)

Appuyez sur le bouton, et constatez le changement. Habituellement on  utilise le CSS pour la mise en page.  

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.089.jpeg)

**Activité n°26.:** Créer un fichier interaction.css dans le dossier css. Rajouter le code suivant à la page CSS  
```CSS
h1{
    text-align: center;
    font-size: 40px;
}
.rouge { 
    color:red;
    font-size:30px;
}
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.091.png)


Puis ajouter la ligne suivante dans le html pour lier le CSS avec le html.  
```html
<link rel="stylesheet" href="css/interaction.css"> 
```

Modifier le fichier Js comme suit. Puis enregistrer et observer le fichier interaction.html dans Firefox. 
```JS
function change_couleur() {
    var paragraphe = document.getElementById("important");
    console.log(paragraphe);
    paragraphe.classList.add("rouge");
}
```


Ce code aura pour effet d'ajouter la classe "rouge" à notre élément "paragraphe" sélectionné. 

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.094.png)

On va à présent modifier la couleur 

**Activité n°27.:** Ajouter le bouton suivant dans le html 
```html
<button onclick="reset\_couleur()">Reset</button> 
```


Puis ajouter la fonction suivante dans le JS : 

```JS
function reset_couleur() {
    var paragraphe = document.getElementById("important");
    console.log(paragraphe);
    paragraphe.classList.remove("rouge");
}
```


![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.097.png) ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.098.png)

### **10.2. Manipuler<a name="_page10_x40.00_y701.92"></a> les éléments HTML en utilisant une sélection CSS** 

Sélection des éléments avec ```querySelector``` et ```querySelectorAll``` : pour sélectionner des éléments HTML en utilisant une  sélection  CSS,  nous  pouvons  utiliser  les  méthodes  ```document.querySelector()``` et ```document.querySelectorAll()```

**Activité n°28.:**  
```html
   <body> 
   <p class="paragraphe">je représente </br> un paragraphe</p>
   <p class="paragraphe">je représente </br> un autre paragraphe</p>
   <p class="paragraphe">je représente </br> un dernier paragraphe</p>
   <script>
      var premierParagraphe = document.querySelector(".paragraphe");
      premierParagraphe.style.fontWeight = "bold";

      var tousLesParagraphes = document.querySelectorAll(".paragraphe");
      for (var i = 0; i < tousLesParagraphes.length; i++) {
      tousLesParagraphes[i].style.textAlign = "center";
      }
   </script>     
   </body>
```


Une fois que nous avons sélectionné un ou plusieurs éléments HTML, nous pouvons les manipuler en utilisant leurs propriétés et méthodes. 

### **10.3. Modification<a name="_page11_x40.00_y265.92"></a> de contenu de la page HTML avec la propriété ```innerHTML```**

**Activité n°29.:** Modification du contenu d'un élément : 
```html
   <body>
   <h1 id="titre">je suis un titre avec un id</h1> 
   <script>
      var titre = document.getElementById("titre");
      titre.innerHTML = "Nouveau titre";
   </script>     
   </body>
```


**Activité n°30.:** Ajout de contenu à la fin d'un élément : 
```html
   <body>
   <p id="paragraphe">je suis un paragraphe avec un id</p> 
   <script>
      var paragraphe = document.getElementById("paragraphe");
      paragraphe.innerHTML += "<br>Nouveau contenu";
   </script>     
   </body>
```


**Activité n°31.:** Modification du contenu de plusieurs éléments avec une boucle :  
```html
   <body>
   <ol>
      <li></li>
      <li></li>
      <li></li>
   </ol>
   <script>
      var listeElements = document.getElementsByTagName("li");
      for (var i = 0; i < listeElements.length; i++) {
      listeElements[i].innerHTML = "Element " + (i + 1);
      }
   </script>     
   </body>
```


On cible chaque élément de la liste et on le remplace par « Element » et le numéro 

**Activité n°32.:** Modification du contenu en HTML en utilisant des balises HTML :    
```html
   <body>
      <p id="paragraphe">ceci est un paragraphe</p>
      <script>
         var paragraphe = document.getElementById("paragraphe");
         paragraphe.innerHTML = "Contenu <b>en gras</b> et <i>italique</i>";    
      </script>
   </body>
```


### **10.4. Modification<a name="_page12_x40.00_y111.92"></a> de modification de style de la page HTML avec la propriété style**

**Activité n°33.:** Modification de la couleur de fond d'un élément : 
```html
   <body>
      <p id="element">ceci est un paragraphe qui a un id</p>
      <script>
         var element = document.getElementById("element");
         element.style.backgroundColor = "yellow";
      </script>
   </body>
```

**Activité n°34.:** Modification de la couleur de police d'un élément 
```html
   <body>
      <p id="element">ceci est un paragraphe qui a un id</p>
      <script>
         var element = document.getElementById("element");
         element.style.color = "blue";
      </script>
   </body>
```


**Activité n°35.:** Modification de la largeur d'un élément : 
```html
   <body>
      <p id="element">ceci est un paragraphe qui a un id</p>
      <script>
         var element = document.getElementById("element");
         element.style.width = "70px";
      </script>
   </body>
```


**Activité n°36.:** Modification de plusieurs styles en même temps : 
```html
   <body>
      <p id="element">ceci est un paragraphe qui a un id</p>
      <script>
         var element = document.getElementById("element");
         element.style.backgroundColor = "yellow";
         element.style.color = "blue";
         element.style.width = "70px";
      </script>
   </body>
```


**Activité n°37.:** Modification de styles en utilisant une boucle : 
```html
   <body>
      <ul>
         <li>framboise</li>
         <li>fraise</li>
         <li>pomme</li>
      </ul>
      <script>
         var listeElements = document.getElementsByTagName("li");
         for (var i = 0; i < listeElements.length; i++) {
         listeElements[i].style.backgroundColor = "yellow";
         listeElements[i].style.color = "blue";
         }
      </script>
   </body>
```


### **10.5. Autres<a name="_page13_x40.00_y67.92"></a> manipulations d’éléments HTML** 

**Activité n°38.:** Ajout ou suppression de classes CSS : 
```html
   <body>
      <p id="element">je suis un paragraphe avec un id</p>
      <script>
         var element = document.getElementById("element");
         element.classList.add("nvlclasse");
         
         var premierParagraphe = document.querySelector(".nvlclasse");
         premierParagraphe.style.fontWeight = "bold";
         
         element.classList.remove("nvlclasse");
      </script>
   </body>
```


- Modification de l'attribut src d'une image pour changer son URL : 
```html
   <body>
      <img src="dinosaur.jpg">
      <script>
         var image = document.getElementById("image");
         image.src = "nouvelle_image.jpg";
      </script>
   </body>
```


**Activité n°39.:** Modification de l'attribut href d'un lien pour changer son URL : 
```html
   <body>
      <a id="lien" href="https://wikipedia.org/">c'est la page wikipedia</a>
      <script>
         var lien = document.getElementById("lien");
         lien.href = "http://www.google.fr";
      </script>
   </body>
```


**Activité n°40.** Ajout d'un événement (par exemple, un clic) à un élément : 
```html
   <body>
      <p id="bouton">c'est un paragraphe avec un id il faut cliquer dessus</p>
      <script>
         var bouton = document.getElementById("bouton");
         bouton.addEventListener("click", function() {
         alert("Bouton cliqué");
         });
      </script>
   </body>
```


**Activité n°41.:** Modification de la position d'un élément en utilisant les propriétés left, right, top, et bottom : 
```html
   <body>
      <p id="element">c'est un paragraphe avec un id</p>
      <script>
         var element = document.getElementById("element");
         element.style.position = "absolute";
         element.style.left = "100px";
         element.style.top = "100px";        
      </script>
   </body>
```


## **11. Interactions<a name="_page14_x40.00_y95.92"></a> avec l’utilisateur** 

Les événements permettent de déclencher une fonction selon qu'une action s'est produite ou non. Par exemple, faire apparaître une fenêtre ```alert()``` lorsque l'utilisateur survole une zone d'une page web, ou ajouter un élément lors d'un clic de bouton de la souris (ou du clavier). 

### **11.1. Liste<a name="_page14_x40.00_y174.92"></a> des événements en JS:**  
Résumé des événements JS : Il est important de noter que les événements peuvent être déclenchés par des  actions de l'utilisateur ou par des actions du script lui-même.  

[https://www.lehtml.com/js/even.htm](https://www.lehtml.com/js/even.htm)

<table><tr><th colspan="1">click </th><th colspan="1">Cliquer (appuyer puis relâcher) sur l'élément </th></tr>
<tr><td colspan="1">dblclick </td><td colspan="1">Double-cliquer sur l'élément </td></tr>
<tr><td colspan="1">mouseover</td><td colspan="1">Faire entrer le curseur sur l'élément </td></tr>
<tr><td colspan="1">mouseout </td><td colspan="1">Faire sortir le curseur de l'élément </td></tr>
<tr><td colspan="1">mousedown</td><td colspan="1">Appuyer (sans relâcher) sur le bouton gauche de la souris sur l'élément </td></tr>
<tr><td colspan="1">mouseup </td><td colspan="1">Relâcher le bouton gauche de la souris sur l'élément </td></tr>
<tr><td colspan="1">mousemove</td><td colspan="1">Faire déplacer le curseur sur l'élément </td></tr>
<tr><td colspan="1">keydown </td><td colspan="1">Appuyer (sans relâcher) sur une touche de clavier sur l'élément </td></tr>
<tr><td colspan="1">keyup </td><td colspan="1">Relâcher une touche de clavier sur l'élément </td></tr>
<tr><td colspan="1">keypress </td><td colspan="1">Frapper (appuyer puis relâcher) une touche de clavier sur l'élément </td></tr>
<tr><td colspan="1">focus </td><td colspan="1">« Cibler » l'élément </td></tr>
<tr><td colspan="1">blur </td><td colspan="1">Annuler le « ciblage » de l'élément </td></tr>
<tr><td colspan="1">change </td><td colspan="1">Changer la valeur d'un élément spécifique aux formulaires (input,checkbox, etc.) </td></tr>
<tr><td colspan="1" rowspan="2">input </td><td colspan="1">[Taper un caractère dans un champ de texte (son support n'est pas compvar sur tous les ](https://caniuse.com/#feat=input-event)</td></tr>
<tr><td colspan="1">[navigateurs) (https://caniuse.com/#feat=input-event)](https://caniuse.com/#feat=input-event) </td></tr>
<tr><td colspan="1">select </td><td colspan="1">Sélectionner le contenu d'un champ de texte (input,textarea, etc.) </td></tr>
<tr><td colspan="1">submit </td><td colspan="1">déclenché lorsque le formulaire est soumis. </td></tr>
<tr><td colspan="1">resize </td><td colspan="1">Resize de la fenêtre </td></tr>
<tr><td colspan="1">scroll </td><td colspan="1">Scroll de la fenêtre </td></tr>
</table>

### **11.2. La<a name="_page14_x40.00_y550.92"></a> pratique** 

**Activité n°42.:** Créer un fichier (avec tout ce qu’il faut  ) evenement.html*,* dans Documents\site et saisir le code ci-dessous. 
```html
   <body>
      <span onclick="alert('Hello')" > Cliquez ici !</span>
   </body>
```


Enregistrer et observer la page html dans Firefox.  

Ici la fonction ```alert()``` ne se déclenche que lors d’un click. 

**Activité n°43.:** Afficher une alerte lorsque l'utilisateur clique sur un bouton :  
```html
   <body>
      <button id="bouton">Cliquez ici !</button> 
      <script>
         var bouton = document.getElementById("bouton");
         bouton.addEventListener("click", function() {
         alert("Bouton cliqué");
         });
      </script>
   </body>
```


**Activité n°44.:** Changer la couleur de fond d'un élément lorsque la souris passe dessus  
```html
   <body>
      <p id="maDiv">c'est un paragraphe avec un id</p>
      <script>
         var div = document.getElementById("maDiv");
         div.addEventListener("mouseover", function() {
         div.style.backgroundColor = "red";
         });
      </script>
   </body>
```


**Activité n°45.:** Afficher le code d'une touche pressée lorsque l'utilisateur tape sur le clavier :
```html
   <body>
      <p>c'est un paragraphe </p>
      <script>
         document.addEventListener("keydown", function(event) {
         console.log("Touche pressée : " + event.keyCode);
         });
      </script>
   </body>
```  


Le mot-clé ```this``` : il s'agit d'une propriété pointant **sur l'objet actuellement en cours d'utilisation**. Donc, si vous faites appel à ce mot-clé lorsqu'un événement est déclenché, l'objet pointé sera l'élément qui a déclenché l'événement. 


**Activité n°46.**
```html
   <body>
      <input type="text" id="input" size="50" value="Cliquez ici"
         onfocus="this.value = 'Appuyez sur la tabulation pour perdre le focus'" onblur="this.value= 'Cliquez ici !'">
   </body>
```
 

Enregistrer et observer la page html dans Firefox. 

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.140.jpeg)

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.141.png)

Le mot clé ```this``` permet de pointer sur l'objet qui a déclenché l'évènement. 

- ```onfocus``` : se déclenchera si le "focus" est pris par la balise ```input```. 
- ```onblur``` : se déclenchera si le "focus" est perdu par la balise ```input```. 

On va séparer le code javascript du code html. 

### **11.3. Pour<a name="_page16_x40.00_y319.92"></a> aller plus loin avec eventListener**



**Activité n°47.**
```html
<!DOCTYPE html>
<html>
<body>
    <button id="clickIt">Cliquez ici !</button> 
    <p id="hoverPara">Passez la souris sur ce texte !</p>
    <b id="effect"></b>
    <script>
        const x = document.getElementById("clickIt");
        const y = document.getElementById("hoverPara");
        x.addEventListener("click", RespondClick);
        y.addEventListener("mouseover", RespondMouseOver);
        y.addEventListener("mouseout", RespondMouseOut); 
        function RespondMouseOver() {
            document.getElementById("effect").innerHTML +=
                       "MouseOver Event" + "<br>";
        }
        function RespondMouseOut() {
            document.getElementById("effect").innerHTML +=
                      "MouseOut Event" + "<br>";
        }
        function RespondClick() {
            document.getElementById("effect").innerHTML +=
                      "Click Event" + "<br>";
        }
    </script>
</body>
</html>
```



Enregistrer et observer la page html dans Firefox.  


![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.149.png)

Comme vous le voyez, il est possible d'ajouter plusieurs ```EventListener``` à un même élément html. 

Vous pouvez aussi associer une fonction à votre ```eventListener``` sans qu'elle soit intégrée dans les paramètres, cette fonction peut être définie par la suite (comme ```RespondMouseOut```). 

**Pour aller plus loin  ou avoir plus de détails** :[ https://www.w3schools.com/jsref/dom_obj_all.asp ](https://www.w3schools.com/jsref/dom_obj_all.asp)![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.005.png)



## **12. Exercices<a name="_page18_x40.00_y36.92"></a>** 

Ecrire  directement  le  script  dans  le  html  entre  balise  ```<script>…</script>```.  Les  fichiers  HTML exercice\_numéro.html sont à compléter pour le dossier Ressources 

**Exercice 1 : Ecrire une fonction simple** 

Vous utiliserez les fonctions ```alert()``` (qui affiche une chaîne de caractères) et ```prompt()``` (qui invite à la saisie d'une donnée), dont voici les syntaxes : 

- ```alert(Chaîne à afficher à l'écran)``` 
- ```variable=prompt(Question à afficher à l'écran)```
1. Complétez le  fichier exercice1.html pour  que le click  sur le bouton lance  une  fonction.  Cette  fonction demande la saisie d'une largeur, d'une longueur et affiche la surface du rectangle correspondant. 
2. Remplacez ce calcul par celui du périmètre (double de la somme de la longueur et de la largeur). 

**Exercice 2 : Ecrire une fonction renvoyant une valeur** 

1. Créez une fonction qui : 
   1. demande la saisie d'un rayon ; 
   1. retourne la surface du cercle de ce rayon 
1. Affichez le résultat de l'appel à cette fonction en cliquant sur le bouton. 

**Exercice 3 : Changements de couleurs** 

Les changements de couleurs d'une zone de texte font appel à ```onmouseover```, ```onmouseout```, ```onclick``` et ```ondblclick```, ainsi qu'aux méthodes de contrôle du style par JavaScript appliquées à l'objet courant indiqué par ```this```.

Exemple : Ceci est un texte dont la couleur va changer au passage de la souris.  

Créer une page web comportant une phrase, dont un groupe de mots, de couleur noire au chargement, doit prendre la couleur : 

1. rouge au passage de la souris ; 
1. citron vert (lime) en réponse à un click ; 
1. bleu marine (navy) en réponse à un double click. 

**Exercice 4 : Manipulation des méthodes d’accès aux éléments** 

On a utilisé les méthodes ```getElementById```, ```getElementsByName``` et ```getElementsByTagName```.  

1. Créer une fonction ```modif_paragraphe()```, appelée en cliquant sur le titre. Cette fonction sélectionne le paragraphe en utilisant son identifiant, puis le modifie avec la propriété ```innerHTML```, en remplaçant le mot **original** en caractères droit par le mot **corrigé**, en italique. 
1. Créer une fonction ```centrage_h1()```, appelée en cliquant sur le paragraphe. Cette fonction détecte d'abord les éléments portant le nom de balise h1. Elle sélectionne ensuite le premier d'entre eux et modifie son attribut ```align```, en lui affectant la valeur "```center```", à l'aide de la méthode ```setAttribute```.... 

**Aide :** ```titre.setAttribute("align", "center");```
