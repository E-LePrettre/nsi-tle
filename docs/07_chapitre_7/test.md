---
author: ELP
title: 07c Le Javascript
--- 

**Table des matières** 

1. [Qu'est-ce que JavaScript et à quoi sert-il ? ](#_page0_x40.00_y687.92)
2. [Comment utiliser JavaScript avec HTML et CSS ?](#_page1_x40.00_y280.92)
3. [Boite de dialogue](#_page2_x40.00_y237.92)
4. [La console](#_page2_x40.00_y113.92)
5. [Les variables](#_page2_x40.00_y641.92)
6. [Les conditions](#_page4_x40.00_y693.92)
7. [Les opérateurs logiques](#_page6_x40.00_y544.92)
8. [Les boucles](#_page6_x40.00_y626.92)
9. [Les fonctions](#_page7_x40.00_y654.92)
10. [Modeler des pages web avec js ](#_page8_x40.00_y524.92)
11. [Interactions avec l’utilisateur ](#_page14_x40.00_y95.92)
12. [Exercices ](#_page18_x40.00_y36.92)

## <H2 STYLE="COLOR:BLUE;">1. Qu'est-ce que JavaScript et à quoi sert-il ? <a name="_page0_x40.00_y687.92"></a></H2>
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.004.png)

Javascript est un langage de programmation utilisé **côté client** pour créer des fonctionnalités interactives sur les sites web. Javascript est **polyvalent, compatible** avec tous les navigateurs et permet la manipulation du contenu web en temps réel.

Le Javascript est un langage dit **client-side** c’est-à-dire que les scripts sont exécutés par le navigateur chez ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.006.png)![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.007.png)![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.008.png)l’internaute. 

Pour cela :  

- votre ordinateur **récupère le code source d'une page web** sur un serveur.  
- votre navigateur **interprète la page et les scripts** qu'elle contient.  
- la page **formatée s'affiche sur votre écran**. Les scripts, quant à eux, sont mis en mémoire et seront lancés dès que l'événement attendu se produira  
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.009.png)

## <H2 STYLE="COLOR:BLUE;">2. Comment<a name="_page1_x40.00_y280.92"></a> utiliser JavaScript avec HTML et CSS ?</H2>
### <H3 STYLE="COLOR:GREEN;">2.1. Cas<a name="_page1_x40.00_y302.92"></a> général :</H3>

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

### <H3 STYLE="COLOR:GREEN;">2.2. Fichier<a name="_page1_x40.00_y558.92"></a> js externalisé</H3>

Pour bien faire on externalise dans un dossier js. On écrit le javascript dans un fichier script.js que l’on met **généralement** dans le dossier js. On peut placer 
```html
<script src="script.js"></script>
```

- **soit dans l'en-tête** (```<head>``` ... ```</head>```), 

- **soit dans le corps** (```<body>``` ... ```</body>```) de la page HTML. 

**<H3 STYLE="COLOR:red;">Activité n°1 :</H3>** Dans la index.html rajouter le lien vers le fichier js 
```html
<!DOCTYPE html>
    <head>
        <meta charset="utf-8" />
        <link rel="stylesheet" href="css/style.css" />
        <script type="text/javascript" src="js/script.js"></script>
        <title>Logique sur les passoires</title>
    </head>
```

```type="text/javascript"``` est **facultatif**

**Activité n°1 suite:** 
**Puis il faut créer le nouveau fichier javascript :**Créer un nouveau fichier vide (si ce n’est déjà fait) sous le nom **script.js**   

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.005.png)

## <H2 STYLE="COLOR:BLUE;">3. Boite<a name="_page2_x40.00_y237.92"></a> de dialogue</H2>

**Nous allons dans la suite faire des activités indépendantes sur une nouvelle page HTML**

**<H3 STYLE="COLOR:red;">Activité n°2 :</H3>**Dans une nouvelle page html que l’on appellera **exo_JS.html**

```html
<!DOCTYPE html>
    <head>
        <meta charset="utf-8" />
        <title>Page de tests du code js</title>
    </head>
    <body>
        Page de tests du code JS
    </body>
</html>
```

**<H3 STYLE="COLOR:red;">Activité n°3 :</H3>**Dans exo_JS.html rajouter n’importe où dans les balises ```<body>```
```html
<script> alert('Hello world!');
</script>
```
Enregistrer et observer. 

**<H3 STYLE="COLOR:red;">Activité n°4 :</H3>** Dans exo_JS.html rajouter le lien vers le fichier js.
```html
<!DOCTYPE html>
    <head>
        <meta charset="utf-8" />
        <script type="text/javascript" src="exo.js"></script>
        <title>Page de tests du code js</title>
    </head>
    <body>
        Page de tests du code JS
    </body>
</html>
```

Créer un nouveau fichier vide **exo.js**

**<H3 STYLE="COLOR:red;">Activité n°5 :</H3>** Dans le fichier exo.js écrire le script suivant :
```js
alert('Hello world!');
```
Enlever de la page exo_JS.html
```html
<script> alert'Hello world!');
</script>
```
Enregistrer le tout et observer

## <H2 STYLE="COLOR:BLUE;">4. La<a name="_page2_x40.00_y113.92"></a> console</H2>

**<H3 STYLE="COLOR:red;">Activité n°6 :</H3>** Dans le fichier exo.js écrire le script suivant (**à la place** de ce qu’il y avait) :
```js
console.log('Hello world!');
```
Enregistrer le tout et observer dans **console** la page dans Firefox (ou EDGE) on fait **ctrl+Maj+I**

![](image1.png)

## <H2 STYLE="COLOR:BLUE;">5. Les<a name="_page2_x40.00_y641.92"></a> variables</H2>
### <H3 STYLE="COLOR:GREEN;">5.1. Déclarer<a name="_page2_x40.00_y663.92"></a> une variable</H3>

- ```let``` ou ```const``` permet de déclarer des variables dont la portée est limitée à celle du bloc entre {…}. Par contre une variable déclarée avec ```const``` ne peut pas être réaffectée (changée de valeur) une fois déclarée
- ```var``` , quant à lui, permet de définir une variable globale ou locale à une fonction (sans distinction des blocs utilisés dans la fonction).

```js
var maVariable ; 
maVariable = 5 ;
``` 
ou 
```js
var message = "Bonjour, visiteur";
``` 

**<H3 STYLE="COLOR:red;">Activité n°7 :</H3>** Dans le fichier *exo.js* écrire le script suivant.  
Enregistrer et observer le fichier *exo_JS.html* dans Firefox. 
```js
var myVariable = 5.5;
alert(myVariable);  
```    
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.024.png)

puis à la place :
```js
var myVariable = 5.5;
console.log(myVariable);  
```  
dans Firefox (ou EDGE) on fait **ctrl+Maj+I**

### <H3 STYLE="COLOR:GREEN;">5.2. Les<a name="_page3_x40.00_y137.92"></a> types de variables</H3>

Le Javascript est un langage typé dynamiquement : **on n’a pas besoin de déclarer le type des variables**. Il existe trois types principaux de variable : 

- Les **numbers**  
- Les **strings**  
- Les **booleans**  

### <H3 STYLE="COLOR:GREEN;">5.3. Les<a name="_page3_x40.00_y247.92"></a> chaines de caractères</H3>

Pour inclure des guillemets " ou des apostrophes dans une chaînes, il faut utiliser le caractère d'échappement ```\``` (antislash). 

**<H3 STYLE="COLOR:red;">Activité n°8 :</H3>** Dans le fichier exo.js écrire le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
// deux chaines de caracteres
var message1 = "Ceci est un \"petit\" test (pas besoin d'antislash \).";
var message2 = 'Un autre "petit" test (attention à l\'antislash \)';

// maintenant, on les affiche
console.log(message1);
console.log(message2);
```

On peut également insérer des retours à la ligne ainsi que des tabulations avec des caractères spéciaux : 

- ```\n``` : retour à la ligne. 
- ```\t``` : une tabulation (ne marche pas dans tous les cas) 
- ```\b``` : pour insérer un backspace (touche "retour arrière") 
- ```\uXXXX``` : pour insérer le caractère donc la [valeur unicode](http://fr.wikipedia.org/wiki/Table_des_caractÃ¨res_Unicode) est XXXX (en hexadécimales). 

### <H3 STYLE="COLOR:GREEN;">5.4. Tester<a name="_page3_x40.00_y503.92"></a> l’existence de variables avec typeof ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.029.png)</H3>

L’instruction ```typeof``` permet de tester l’existence d’une variable ou d’en vérifier son type. Par exemple : 

**<H3 STYLE="COLOR:red;">Activité n°9 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var number = 2;
console.log(typeof number); 

var text = 'Mon texte';
console.log(typeof text); 

var aBoolean = false;
console.log(typeof aBoolean); 
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.031.png) 

### <H3 STYLE="COLOR:GREEN;">5.5. Les<a name="_page3_x40.00_y706.92"></a> calculs</H3>

Tous les opérateurs classiques peuvent être utilisés. Ainsi on pourra écrire :

**<H3 STYLE="COLOR:red;">Activité n°10 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var divisor = 3, result1, result2, result3; 
result1 = (16 + 8) / 2 - 2 ; 
result2 = result1 / divisor; 
result3 = result1 % divisor; 

console.log(result2); 
console.log(result3); 
```
### <H3 STYLE="COLOR:GREEN;">5.6. La<a name="_page4_x40.00_y154.92"></a> concaténation</H3>

**<H3 STYLE="COLOR:red;">Activité n°11 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var hi = 'Bonjour ', name = 'toi', result; 
result = hi + name;  
console.log(result); 
```  
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.034.png)

On peut aussi concaténer des **chaines de caractères et un nombre**.  

### <H3 STYLE="COLOR:GREEN;">5.7. Interagir<a name="_page4_x40.00_y286.92"></a> avec l’utilisateur</H3>

Avec la fonction ```prompt()```. Elle s’utilise comme alert(). Elle renvoie ce que l’utilisateur a écrit sous forme d’une chaine de caractère. 

**<H3 STYLE="COLOR:red;">Activité n°12 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var userName = prompt('Entrez votre prénom :');  
console.log("Bonjour " + userName);   
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.036.png)

**<H3 STYLE="COLOR:red;">Activité n°13 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var start = 'Bonjour ', name, end = ' !', result; 

name = prompt('Quel est votre prénom ?'); 
result = start + name + end; 
console.log(result); 
```

Tout ce qui est récupéré avec ```prompt()``` est sous forme d’une chaine de caractères. Pour convertir la chaine de caractères en **nombre entier** on utilise la fonction ```parseInt()```*.* On pourra utiliser la fonction ```parseFloat()``` pour convertir une chaine de caractère en nombre décimal.* Par exemple 

**<H3 STYLE="COLOR:red;">Activité n°14 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var first, second, result;  
first = prompt('Entrez le premier chiffre :');  
second = prompt('Entrez le second chiffre :');  
result = parseInt(first) + parseInt(second);  
console.log(result); 
```

## <H2 STYLE="COLOR:BLUE;">6. Les<a name="_page4_x40.00_y693.92"></a> conditions</H2>
### <H3 STYLE="COLOR:GREEN;">6.1. Les<a name="_page4_x40.00_y715.92"></a> opérateurs de condition</H3>

Les opérations de comparaison classiques sont les mêmes : ```==``` ; ```!= ```; ```<``` ; ```<=``` etc.

Pour pouvoir comparer 4 en tant que ```number``` et 4 en tant que string il faut utiliser d’autres opérateurs : 

**<H3 STYLE="COLOR:red;">Activité n°15 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var number = 4, text = '4', result; 

result = number == text; 
console.log(result); // Affiche  « true » alors que « number » est un nombre et « text » une chaîne de caractères

result = number === text; 
console.log(result); // Affiche « false » car cet opérateur compare aussi les types des variables en plus de leurs valeurs 
```

### <H3 STYLE="COLOR:GREEN;">6.2. Les<a name="_page5_x40.00_y167.92"></a> structures conditionnelles</H3>
#### <H4 STYLE="COLOR:ORANGE;">6.2.1. La<a name="_page5_x40.00_y186.92"></a> condition « if else »</H4>

**<H3 STYLE="COLOR:red;">Activité n°16 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var userName = prompt('Entrez votre prénom :'); 

if (2 < 8 && 8 >= 4) { // Cette condition renvoie « true », le code est donc exécuté     
console.log('La condition est bien vérifiée.'); 
} 
console.log(userName);  
```

La fonction ```confirm()```. On lui passe en paramètre une chaine de caractère qui sera affichée à l’écran et elle retourne un booléen en fonction de l’action de l’utilisateur. 

**<H3 STYLE="COLOR:red;">Activité n°17 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
if (confirm('Voulez-vous exécuter le code JavaScript de cette page ?')) { 
   console.log('Le code a bien été exécuté !')}; 
```
Relancer la Web exo_Js.html en choisissant l’autre proposition. 

La structure ```else``` existe également et permet d’exécuter un certain code si la condition n’a pas été vérifiée. Par contre il est conseillé de l’écrire ainsi (directement après l’accolade de fermeture de la structure ```if```) : 
```JS
if ( /* condition */ ) {
    // Du code…
} else {
    // Du code…
}
```

La structure ```else if``` peut être aussi utilisée ainsi : 
```JS
if ( /* condition */ ) {
    // Du code…
} else if ( /* condition */ ) {
    // Du code…
} else {
    // Du code…
}
```

#### <H4 STYLE="COLOR:ORANGE;">6.2.2. La<a name="_page5_x40.00_y659.92"></a> condition ```switch```</H4>

Supposons qu’on ait besoin de nombreux ```else if``` les uns à la suite des autres. Par exemple : 

**<H3 STYLE="COLOR:red;">Activité n°18 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var tiroir = parseInt(prompt('Choisissez le tiroir à ouvrir (1 à 4) :')); 
if (tiroir == 1) { 
   console.log('Contient divers outils pour dessiner : du papier, des crayons, etc.'); 
} else if (tiroir == 2) { 
   console.log('Contient du matériel informatique : des câbles, des composants, etc.'); 
} else if (tiroir == 3) { 
   console.log('Ah ? Ce tiroir est fermé à clé ! Dommage !'); 
} else if (tiroir == 4) { 
   console.log('Contient des vêtements : des chemises, des pantalons, etc.'); 
} else { 
   console.log("Info du jour : le meuble ne contient que 4 tiroirs et, jusqu'à preuve du contraire, les tiroirs négatifs n'existent pas."); 
} 
```

Avec ```switch``` c'est un peu plus facile : 

**<H3 STYLE="COLOR:red;">Activité n°19 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var tiroir = parseInt(prompt('Choisissez le tiroir à ouvrir (1 à 4) :'));

switch (tiroir) {
    case 1:
        console.log('Contient divers outils pour dessiner : du papier, des crayons, etc.');
    break;

    case 2:
        console.log('Contient du matériel informatique : des câbles, des composants, etc.');
    break;

    case 3:
        console.log('Ah ? Ce tiroir est fermé à clé ! Dommage !');
    break;

    case 4:
        console.log('Contient des vêtements : des chemises, des pantalons, etc.');
    break;

    default:
        console.log("Info du jour : le meuble ne contient que 4 tiroirs et, jusqu'à preuve du contraire, les tiroirs négatifs n'existent pas.");
}
```

Tout ce qui suit les deux points d’un ```case``` sera exécuté si la variable analysée par le ```switch``` contient la valeur du ```case```. À chaque fin d’un ```case``` on écrit l’instruction ```break``` pour casser le ```switch``` et éviter d’afficher les autres alertes. La partie ```default``` est optionnelle.  

## <H2 STYLE="COLOR:BLUE;">7. Les<a name="_page6_x40.00_y544.92"></a> opérateurs logiques</H2>
- L’opérateur ET se note ```&&``` 
- L’opérateur OU se note ```||``` (Alt Gr + 6)  
- L’opérateur NON se note comme en Python avec ```!``` 

## <H2 STYLE="COLOR:BLUE;">8. Les<a name="_page6_x40.00_y626.92"></a> boucles</H2>
### <H3 STYLE="COLOR:GREEN;">8.1. L’incrémentation<a name="_page6_x40.00_y648.92"></a></H3>

L’incrémentation permet d’ajouter une unité à un nombre et à l’inverse, la décrémentation permet de soustraire une unité. 

**<H3 STYLE="COLOR:red;">Activité n°20 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var number1 = 0, number2 = 0; 

number1++; 
console.log(number1); 

number2--; 
console.log(number2); 
```

La position de l’opérateur ```++``` est importante si on veut récupérer le résultat de l’incrémentation :  ```var number = 0;``` Il y a deux possibilités :

- ```var output = ++number;``` → retournera 1 car retourne la valeur de number incrémentée 

- ```var output = number++``` → retournera 0 car retourne la valeur de number avant incrémentation 

### <H3 STYLE="COLOR:GREEN;">8.2. La<a name="_page7_x40.00_y168.92"></a> boucle while</H3>

À chaque fois que la boucle se répète on parle d’itération. Par exemple :  

**<H3 STYLE="COLOR:red;">Activité n°21 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
var number = 1; 

while (number < 10) {     
   number++; 
} 
console.log(number); 
```

### <H3 STYLE="COLOR:GREEN;">8.3. La<a name="_page7_x40.00_y328.92"></a> boucle do while</H3>

La boucle ```do while``` ressemble très fortement à la boucle ```while```, sauf que dans ce cas la boucle est toujours exécutée au moins une fois. La syntaxe d'une boucle ```do while``` : 
```JS
do {
    instruction_1;
    instruction_2;
    instruction_3;
} while (condition);
```

### <H3 STYLE="COLOR:GREEN;">8.4. La<a name="_page7_x40.00_y446.92"></a> boucle for</H3>

Le schéma d’une boucle ```for``` : 
```JS
for (initialisation; condition; incrémentation) {
    instruction_1;
    instruction_2;
    instruction_3;
}
```

**<H3 STYLE="COLOR:red;">Activité n°22 :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
for (var iter = 0; iter < 5; iter++) { 
   console.log('Itération n°' + iter); 
} 
```

**Attention les variables utilisées dans la boucle ```while``` ou dans la boucle ```for``` ne sont pas détruites** (comme dans Python) une fois sortie de la boucle. 

## <H2 STYLE="COLOR:BLUE;">9. Les<a name="_page7_x40.00_y654.92"></a> fonctions</H2>

Pour définir une fonction il faut le script suivant : 
```JS
function myFunction(arguments) { 
   // Le code que la fonction va devoir exécuter
} 
```

**<H3 STYLE="COLOR:red;">Activité n°23 : Exemple de fonction sans argument :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
function showMsg() { 
   console.log('Et une première fonction, une !');
} 
showMsg(); // On exécute ici le code contenu dans la fonction 
```

La fonction ```showMsg()``` exécute elle-même une autre fonction qui n'est autre que ```console.log()``` avec un message prédéfini. Bien sûr, tout code écrit dans une fonction ne s'exécute pas immédiatement, sinon aucun intérêt. C'est pourquoi à la **fin du code on appelle la fonction** afin de l'exécuter, ce qui affiche le message souhaité. Toute variable déclarée dans une fonction n'est utilisable que dans cette même fonction. Ce sont les variables locales. 

**<H3 STYLE="COLOR:red;">Activité n°24 : Exemple de fonction avec argument :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
function myFunction(arg) { // Notre argument est la variable « arg » 
   // Une fois que l'argument a été passé à la fonction, vous allez le retrouver dans la variable « arg »
   console.log('Votre argument : ' + arg); 
} 
myFunction('En voilà un beau test !'); 
```

**<H3 STYLE="COLOR:red;">Activité n°25 : Exemple de fonction avec** ```prompt()``` :</h3> Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
function myFunction(arg) { 
   console.log('Votre argument : ' + arg); 
} 
myFunction(prompt('Que souhaitez-vous passer en argument à la fonction ?')); 
```

**<H3 STYLE="COLOR:red;">Activité n°26 : Exemple de fonction avec un ```return``` :</H3>** Dans le fichier exo.js passer les lignes précédentes en commentaire ```//``` devant chaque ligne ou ```/*``` et ```*/``` et rajouter le script suivant. Enregistrer et observer le fichier exo_JS.html dans Firefox. 
```JS
function sayHello() {
   return 'Bonjour !'; 
   console.log('Attention ! Le texte arrive !'); 
} 
console.log(sayHello()); 
```

## <H2 STYLE="COLOR:BLUE;">10. Modeler<a name="_page8_x40.00_y524.92"></a> des pages web avec js</H2>

Le Javascript va modifier les pages html et css en accédant aux **éléments cible du DOM** (Document Objet Model).  

### <H3 STYLE="COLOR:GREEN;">10.1. Manipuler<a name="_page8_x40.00_y578.92"></a> les éléments HTML</H3>

- **Sélection des éléments par ID** : pour sélectionner un élément HTML en utilisant son ID, nous pouvons utiliser la méthode ```getElementById()```
```html
    <body>
        <p id="titre"> je représente le titre qui va être modifié car j'ai le bon id</p>
        <script>
        var titre = document.getElementById("titre");
        titre.style.color = "blue";
        </script>
    </body>
```

- **Sélection des éléments par nom de classe** : pour sélectionner plusieurs éléments HTML qui ont la même classe, nous pouvons utiliser la méthode ```getElementByClassName()```. Par exemple : 
```html
    <body>
        <p class="paragraphe"> je représente </br>le paragraphe </br> qui va être modifié </br> car j'ai la bonne classe</p>
        <script>
            var paragraphes = document.getElementsByClassName("paragraphe");
            for (var i = 0; i < paragraphes.length; i++) {
            paragraphes[i].style.backgroundColor = "yellow";
            }
        </script>
    </body>
```

Trouve tous les éléments ayant la classe « paragraphe »  

**<H3 STYLE="COLOR:red;">Activité n°27 :</H3>** Créer un fichier **interaction.html**, et saisir le code ci-dessous.

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
<script src="interaction.js"></script>
</html>
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.081.png)

Dans le code précédent, ```<button onclick="change_couleur()">Cliquez ici !</button>``` est une balise qui va créer **un bouton.**  

Un clic dessus va déclencher la fonction ```change_couleur()``` 

Cette fonction va être définie dans un fichier javascript (**interaction.js**) qui va être créé par ce qui suit ... Ensuite créez un fichier interaction.js dans le sous-dossier js. Saisir le code suivant. Puis enregistrer et observer le fichier interaction.html dans Firefox. 
```JS
function change_couleur() {
    var paragraphe = document.getElementById("important");
    console.log(paragraphe);
}
```

Ouvrez la console et observer dans console : 

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.086.png)

Vous devez constater que la **variable paragraphe contient maintenant la balise paragraphe et son contenu** c’est-à-dire ```<p id='important'>Ceci est un texte qu'il faut mettre en valeur !</p>```

**<H3 STYLE="COLOR:red;">Activité n°28 :</H3>** Ajouter le code ci-dessous à la fonction du fichier js (**sous console.log...**). Puis enregistrer et observer le fichier interaction.html dans Firefox.  
```JS
paragraphe.style.color="red"; 
```
![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.087.png)

Appuyez sur le bouton, et constatez le changement. Habituellement on utilise le CSS pour la mise en page.  

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.089.jpeg)

**<H3 STYLE="COLOR:red;">Activité n°29 :</H3>** Créer un fichier interaction.css. Rajouter le code suivant à la page CSS :  
```CSS
h1 {
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
<link rel="stylesheet" href="interaction.css"> 
```

Modifier le fichier JS comme suit. Puis enregistrer et observer le fichier interaction.html dans Firefox. 
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

**<H3 STYLE="COLOR:red;">Activité n°30 :</H3>** Ajouter le bouton suivant dans le html : 
```html
<button onclick="reset_couleur()">Reset</button> 
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

### <H3 STYLE="COLOR:GREEN;">10.2. Manipuler<a name="_page10_x40.00_y701.92"></a> les éléments HTML en utilisant une sélection CSS</H3>

Sélection des éléments avec ```querySelector``` et ```querySelectorAll``` : pour sélectionner des éléments HTML en utilisant une sélection CSS, nous pouvons utiliser les méthodes ```document.querySelector()``` et ```document.querySelectorAll()```.

**<H3 STYLE="COLOR:red;">Activité n°31 :</H3>**  
```html
<body> 
   <p class="paragraphe">je représente </br> un paragraphe</p>
   <p class="paragraphe">je représente </br> un autre paragraphe</p>
   <p class="paragraphe">je représente </br> un dernier paragraphe</p>
   <script>
      var premierParagraphe = document.querySelector(".paragraphe");
      premierParagraphe.style.fontWeight = "bold";

      var tousLesParagraph

es = document.querySelectorAll(".paragraphe");
      for (var i = 0; i < tousLesParagraphes.length; i++) {
      tousLesParagraphes[i].style.textAlign = "center";
      }
   </script>     
</body>
```

Une fois que nous avons **sélectionné un ou plusieurs éléments HTML**, nous pouvons les **manipuler** en utilisant leurs propriétés et méthodes. 

### <H3 STYLE="COLOR:GREEN;">10.3. Modification<a name="_page11_x40.00_y265.92"></a> de contenu de la page HTML avec la propriété ```innerHTML```</H3>

**<H3 STYLE="COLOR:red;">Activité n°32 :</H3>** Modification du contenu d'un élément : 
```html
<body>
   <h1 id="titre">je suis un titre avec un id</h1> 
   <script>
      var titre = document.getElementById("titre");
      titre.innerHTML = "Nouveau titre";
   </script>     
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°33 :</H3>** Ajout de contenu à la fin d'un élément : 
```html
<body>
   <p id="paragraphe">je suis un paragraphe avec un id</p> 
   <script>
      var paragraphe = document.getElementById("paragraphe");
      paragraphe.innerHTML += "<br>Nouveau contenu";
   </script>     
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°34 :</H3>** Modification du contenu de plusieurs éléments avec une boucle :  
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

**<H3 STYLE="COLOR:red;">Activité n°35 :</H3>** Modification du contenu en HTML en utilisant des balises HTML :    
```html
<body>
   <p id="paragraphe">ceci est un paragraphe</p>
   <script>
      var paragraphe = document.getElementById("paragraphe");
      paragraphe.innerHTML = "Contenu <b>en gras</b> et <i>italique</i>";    
   </script>
</body>
```

### <H3 STYLE="COLOR:GREEN;">10.4. Modification<a name="_page12_x40.00_y111.92"></a> de modification de style de la page HTML avec la propriété style</H3>

**<H3 STYLE="COLOR:red;">Activité n°36 :</H3>** Modification de la couleur de fond d'un élément : 
```html
<body>
   <p id="element">ceci est un paragraphe qui a un id</p>
   <script>
      var element = document.getElementById("element");
      element.style.backgroundColor = "yellow";
   </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°37 :</H3>** Modification de la couleur de police d'un élément 
```html
<body>
   <p id="element">ceci est un paragraphe qui a un id</p>
   <script>
      var element = document.getElementById("element");
      element.style.color = "blue";
   </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°38 :</H3>** Modification de la largeur d'un élément : 
```html
<body>
   <p id="element">ceci est un paragraphe qui a un id</p>
   <script>
      var element = document.getElementById("element");
      element.style.width = "70px";
   </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°39 :</H3>** Modification de plusieurs styles en même temps : 
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

**<H3 STYLE="COLOR:red;">Activité n°40 :</H3>** Modification de styles en utilisant une boucle : 
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

### <H3 STYLE="COLOR:GREEN;">10.5. Autres<a name="_page13_x40.00_y67.92"></a> manipulations d’éléments HTML</H3>

**<H3 STYLE="COLOR:red;">Activité n°41 :</H3>** Ajout ou suppression de classes CSS : 
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

Modification de l'attribut src d'une image pour changer son URL : 
```html
<body>
   <img src="dinosaur.jpg">
   <script>
      var image = document.getElementById("image");
      image.src = "nouvelle_image.jpg";
   </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°42 :</H3>** Modification de l'attribut href d'un lien pour changer son URL : 
```html
<body>
   <a id="lien" href="https://wikipedia.org/">c'est la page wikipedia</a>
   <script>
      var lien = document.getElementById("lien");
      lien.href = "http://www.google.fr";
   </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°43 :</H3>** Ajout d'un événement (par exemple, un clic) à un élément : 
```html
<body>
   <p id="bouton">c'est un paragraphe avec un id il faut cliquer dessus</p>
   <script>
      var bouton = document.getElementById("bouton");
      bouton.addEventListener("click", function() {
      console.log("Bouton cliqué");
      });
   </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°44 :</H3>** Modification de la position d'un élément en utilisant les propriétés left, right, top, et bottom : 
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

## <H2 STYLE="COLOR:BLUE;">11. Interactions<a name="_page14_x40.00_y95.92"></a> avec l’utilisateur</H2>

Les événements permettent de déclencher une fonction selon qu'une action s'est produite ou non. Par exemple, faire apparaître une fenêtre ```alert()``` lorsque l'utilisateur survole une zone d'une page web, ou ajouter un élément lors d'un clic de bouton de la souris (ou du clavier). 

### <H3 STYLE="COLOR:GREEN;">11.1. Liste<a name="_page14_x40.00_y174.92"></a> des événements en JS</H3>
Résumé des événements JS : Il est important de noter que les événements peuvent être déclenchés par des actions de l'utilisateur ou par des actions du script lui-même.  

[https://www.lehtml.com/js/even.htm](https://www.lehtml.com/js/even.htm)

<table><tr><th>click </th><th>Cliquer (appuyer puis relâcher) sur l'élément </th></tr>
<tr><td>dblclick </td><td>Double-cliquer sur l'élément </td></tr>
<tr><td>mouseover</td><td>Faire entrer le curseur sur l'élément </td></tr>
<tr><td>mouseout </td><td>Faire sortir le curseur de l'élément </td></tr>
<tr><td>mousedown</td><td>Appuyer (sans relâcher) sur le bouton gauche de la souris sur l'élément </td></tr

>
<tr><td>mouseup </td><td>Relâcher le bouton gauche de la souris sur l'élément </td></tr>
<tr><td>mousemove</td><td>Faire déplacer le curseur sur l'élément </td></tr>
<tr><td>keydown </td><td>Appuyer (sans relâcher) sur une touche de clavier sur l'élément </td></tr>
<tr><td>keyup </td><td>Relâcher une touche de clavier sur l'élément </td></tr>
<tr><td>keypress </td><td>Frapper (appuyer puis relâcher) une touche de clavier sur l'élément </td></tr>
<tr><td>focus </td><td>« Cibler » l'élément </td></tr>
<tr><td>blur </td><td>Annuler le « ciblage » de l'élément </td></tr>
<tr><td>change </td><td>Changer la valeur d'un élément spécifique aux formulaires (input, checkbox, etc.) </td></tr>
<tr><td rowspan="2">input </td><td>[Taper un caractère dans un champ de texte (son support n'est pas complet sur tous les ](https://caniuse.com/#feat=input-event)</td></tr>
<tr><td>[navigateurs) (https://caniuse.com/#feat=input-event)](https://caniuse.com/#feat/input-event) </td></tr>
<tr><td>select </td><td>Sélectionner le contenu d'un champ de texte (input, textarea, etc.) </td></tr>
<tr><td>submit </td><td>déclenché lorsque le formulaire est soumis. </td></tr>
<tr><td>resize </td><td>Resize de la fenêtre </td></tr>
<tr><td>scroll </td><td>Scroll de la fenêtre </td></tr>
</table>

### <H3 STYLE="COLOR:GREEN;">11.2. La<a name="_page14_x40.00_y550.92"></a> pratique</H3>

**<H3 STYLE="COLOR:red;">Activité n°45 :</H3>** Créer un fichier (avec tout ce qu’il faut  ) **evenement.html**, et saisir le code ci-dessous. 
```html
<body>
   <span onclick="alert('Hello')"> Cliquez ici !</span>
</body>
```

Enregistrer et observer la page html dans Firefox. Ici la fonction ```alert()``` ne se déclenche que lors d’un clic. 

**<H3 STYLE="COLOR:red;">Activité n°46 :</H3>** Afficher une alerte lorsque l'utilisateur clique sur un bouton :  
```html
<body>
   <button id="bouton">Cliquez ici !</button> 
   <script>
      var bouton = document.getElementById("bouton");
      bouton.addEventListener("click", function() {
      console.log("Bouton cliqué");
      });
   </script>
</body>
```

**<H3 STYLE="COLOR:red;">Activité n°47 :</H3>** Changer la couleur de fond d'un élément lorsque la souris passe dessus  
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

**<H3 STYLE="COLOR:red;">Activité n°48 :</H3>** Afficher le code d'une touche pressée lorsque l'utilisateur tape sur le clavier :
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

**Le mot-clé ```this```** : il s'agit d'une propriété pointant **sur l'objet actuellement en cours d'utilisation**. Donc, si vous faites appel à ce mot-clé lorsqu'un événement est déclenché, l'objet pointé sera l'élément qui a déclenché l'événement. 

**<H3 STYLE="COLOR:red;">Activité n°49 :</H3>**
```html
<body>
   <input type="text" id="input" size="50" value="Cliquez ici"
      onfocus="this.value = 'Appuyez sur la tabulation pour perdre le focus'" onblur="this.value= 'Cliquez ici !'">
</body>
```
 
Enregistrer et observer la page html dans Firefox. 

![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.140.jpeg) ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.141.png)

**Le mot clé ```this```** permet de pointer sur l'objet qui a déclenché l'évènement. 

- ```onfocus``` : se déclenchera si le "focus" est pris par la balise ```input```. 
- ```onblur``` : se déclenchera si le "focus" est perdu par la balise ```input```.

### <H3 STYLE="COLOR:GREEN;">11.3. Pour<a name="_page16_x40.00_y319.92"></a> aller plus loin avec eventListener</H3>

**<H3 STYLE="COLOR:red;">Activité n°50 :</H3>**
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

Comme vous le voyez, il est possible d'ajouter plusieurs ```EventListener``` à un même élément html. Vous pouvez aussi associer une fonction à votre ```eventListener``` sans qu'elle soit intégrée dans les paramètres, cette fonction peut être définie par la suite (comme ```RespondMouseOut```). 

**Pour aller plus loin ou avoir plus de détails** : [https://www.w3schools.com/jsref/dom_obj_all.asp](https://www.w3schools.com/jsref/dom_obj_all.asp) ![](Aspose.Words.e9d0b6b1-5c5b-49ac-81ba-f1da180d728c.005.png)

## <H2 STYLE="COLOR:BLUE;">12. Exercices<a name="_page18_x40.00_y36.92"></a></H2>

=> CAPYTALE Le code vous sera donné par votre enseignant 

**<H3 STYLE="COLOR:red;">Exercice 1 : Jeu de devinette de nombre</h3>**

**But du jeu :** L'utilisateur doit deviner un nombre aléatoire entre 1 et 100.

**Étapes :**
1. **HTML :** Créez une structure de base avec un champ de saisie pour entrer la supposition et un bouton pour soumettre la supposition.
2. **JavaScript :**
   - Générer un nombre aléatoire entre 1 et 100.
   - Ajouter un événement de clic au bouton de soumission.
   - Lorsque le bouton est cliqué, récupérer la supposition de l'utilisateur et vérifier si elle est correcte, trop élevée ou trop basse.
   - Afficher un message indiquant si la supposition est correcte, trop élevée ou trop basse.
   - Utiliser une boucle pour permettre plusieurs essais jusqu'à ce que l'utilisateur devine correctement.

**Code HTML de exo1.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Jeu de Devinette</title>
</head>
<body>
    <h1>Devinez le nombre</h1>
    <p>Je pense à un nombre entre 1 et 100. Pouvez-vous le deviner ?</p>
    <input type="number" id="guess" placeholder="Entrez votre supposition">
    <button id="submitGuess">Soumettre</button>
    <p id="result"></p>
    <script src="exo1.js"></script>
</body>
</html>
```

**Code JavaScript de exo1.js à trous à compléter**
```javascript
// exo1.js

// Question 1 : Quelle méthode permet de

 générer un nombre aléatoire entre 1 et 100 ?
// Remplissez le blanc avec la bonne méthode pour générer un nombre aléatoire.
// Indice : Utilisez Math.random() et Math.floor().
let randomNumber = ...(... * 100) + 1;

let guesses = 0;

// Question 2 : Comment ajouter un événement de clic au bouton "Soumettre" ?
document.getElementById('submitGuess').addEventListener(..., function() {

    let userGuess = parseInt(document.getElementById('guess').value);
    guesses++;
    
    // Question 3 : Où devons-nous afficher le résultat du jeu ?
    let result = document.getElementById(...);

    // Question 4 : Comment vérifier si la supposition de l'utilisateur est correcte ?
    if (... === randomNumber) {
        result.textContent = `Félicitations ! Vous avez deviné le nombre en ${guesses} essais.`;
    } else if (userGuess < randomNumber) {
        // Question 5 : Complétez le message à afficher lorsque la supposition est trop basse.
        result.textContent = ...;
    } else {
        // Question 6 : Complétez le message à afficher lorsque la supposition est trop haute.
        result.textContent = ...;
    }
});
```

**<H3 STYLE="COLOR:red;">Exercice 2 : Calculatrice de base</h3>**
**Concepts : Variables, opérateurs, fonctions**
- **Mise en contexte :** Développez une calculatrice simple où les utilisateurs peuvent entrer deux nombres et choisir une opération (addition, soustraction, multiplication, division) pour obtenir le résultat.

**Code HTML de exo2.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Calculatrice</title>
</head>
<body>
    <h1>Calculatrice Simple</h1>
    <input type="number" id="num1" placeholder="Nombre 1">
    <input type="number" id="num2" placeholder="Nombre 2">
    <select id="operation">
        <option value="add">Addition</option>
        <option value="subtract">Soustraction</option>
        <option value="multiply">Multiplication</option>
        <option value="divide">Division</option>
    </select>
    <button id="calculate">Calculer</button>
    <p id="result"></p>
    <script src="exo2.js"></script>
</body>
</html>
```

**Code JavaScript de exo2.js à trous à compléter**
```javascript
// exo2.js
document.getElementById('calculate').addEventListener('click', function() {
    let num1 = parseFloat(document.getElementById('num1').value);
    let num2 = parseFloat(document.getElementById('num2').value);
    let operation = document.getElementById('operation').value;
    let result;

    if (operation === 'add') {
        result = num1 + num2;
    } else if (operation === 'subtract') {
        result = num1 - num2;
    } else if (operation === 'multiply') {
        result = num1 * num2;
    } else if (operation === 'divide') {
        result = num1 / num2;
    }

    document.getElementById('result').textContent = 'Résultat : ' + result;
});
```

**<H3 STYLE="COLOR:red;">Exercice 3 : Liste de tâches (To-Do List)</h3>**
**Concepts : Manipulation du DOM, événements, boucles**
- **Mise en contexte :** Créez une application où les utilisateurs peuvent ajouter des tâches, les marquer comme complétées, et les supprimer.

**Code HTML de exo3.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Liste de Tâches</title>
</head>
<body>
    <h1>Liste de Tâches</h1>
    <input type="text" id="taskInput" placeholder="Nouvelle tâche">
    <button id="addTask">Ajouter</button>
    <ul id="taskList"></ul>
    <script src="exo3.js"></script>
</body>
</html>
```

**Code JavaScript de exo3.js à trous à compléter**
```javascript
// exo3.js
// Question 1 : Comment ajouter un événement de clic au bouton "Ajouter" ?
document.getElementById('addTask').addEventListener(..., function() {

    // Question 2 : Comment récupérer la valeur du champ de saisie ?
    let taskInput = document.getElementById('taskInput');
    let taskText = taskInput....;

    taskInput.value = '';

    // Question 3 : Comment créer un nouvel élément de liste (li) pour la nouvelle tâche ?
    let li = document.createElement(...);
    li.textContent = taskText;

    // Question 4 : Comment créer un bouton pour marquer la tâche comme complétée ?
    let completeButton = document.createElement(...);
    completeButton.textContent = 'Compléter';
    completeButton.addEventListener('click', function() {
        li.style.textDecoration = 'line-through';
    });

    // Question 5 : Comment créer un bouton pour supprimer la tâche ?
    let deleteButton = document.createElement(...);
    deleteButton.textContent = 'Supprimer';
    deleteButton.addEventListener('click', function() {
        li.remove();
    });

    // Question 6 : Comment ajouter les boutons à l'élément de liste ?
    li.appendChild(...);
    li.appendChild(...);

    // Question 7 : Comment ajouter l'élément de liste à la liste de tâches ?
    document.getElementById(...).appendChild(li);
});
```

**<H3 STYLE="COLOR:red;">Exercice 4 : Quiz interactif</h3>**
**Concepts : Conditions, boucles, manipulation du DOM**
- **Mise en contexte :** Créez un quiz où les utilisateurs répondent à une série de questions et reçoivent une note à la fin.

**Code HTML de exo4.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Quiz Interactif</title>
</head>
<body>
    <h1>Quiz Interactif</h1>
    <div id="quiz">
        <p>1. Quelle est la capitale de la France ?</p>
        <input type="radio" name="q1" value="Paris"> Paris<br>
        <input type="radio" name="q1" value="Londres"> Londres<br>
        <input type="radio" name="q1" value="Berlin"> Berlin<br>
        <p>2. Quelle est la capitale de l'Allemagne ?</p>
        <input type="radio" name="q2" value="Paris"> Paris<br>
        <input type="radio" name="q2" value="Londres"> Londres<br>
        <input type="radio" name="q2" value="Berlin"> Berlin<br>
        <button id="submitQuiz">Soumettre</button>
        <p id="result"></p>
    </div>
    <script src="exo4.js"></script>
</body>
</html>
```

**Code JavaScript de exo4.js à trous à compléter**
```javascript
// exo4.js
document.getElementById('submitQuiz').addEventListener('click', function() {
    let score = 0;
    let totalQuestions = 2;

    let q1 = document.querySelector('input[name="q1"]:checked');
    let q2 = document.querySelector('input[name="q2"]:checked');

    if (q1 && q1.value === 'Paris') {
        score++;
    }

    if (q2 && q2.value === 'Berlin') {
        score++;
    }

    let result = document.getElementById('result');
    result.textContent = `Vous avez obtenu ${score} sur ${totalQuestions}`;
});
```