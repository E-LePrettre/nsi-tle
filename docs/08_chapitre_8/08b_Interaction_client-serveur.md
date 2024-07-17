---
author: ELP
title: 08b Interaction client-serveur - Requête
---


**Table des matières** 

1. [Modèle client/serveur=](#_page0_x40.00_y516.92)
1. [Le protocole HTTP=](#_page1_x40.00_y233.92)
3. [Coder l’envoi d’une requête par le navigateur](#_page3_x40.00_y617.92)
4. [APPLICATION : Création d’une page web dynamique](#_page8_x40.00_y503.92)
5. [POUR ALLER PLUS LOIN : Formulaire d’une page Web version Flask](#_page13_x40.00_y36.92)


## **1. Modèle<a name="_page0_x40.00_y516.92"></a> client/serveur** 
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.004.png)

Deux  ordinateurs  en  réseau  peuvent  s’échanger  des  **données**.  Un ordinateur A va souvent se contenter de **demander** (faire une **requête**)  des ressources à un ordinateur B. L’ordinateur B va lui se contenter de  **fournir**  des  ressources  à tous les ordinateurs  qui lui  en feront la  demande. On dira que A est le **client** alors que B est le **serveur**.   

Un client peut être défini comme une application logicielle qui **envoie** des requêtes à un serveur. Un serveur peut être défini comme une application logicielle qui **attend** et **traite les requêtes** provenant de clients.  

La communication entre un client et un serveur se fait généralement à l'aide d'un **protocole de communication spécifique**.(par exemple : HTTP entre navigateurs web et serveurs web) 

Les serveurs sont aujourd’hui **capables de générer eux-mêmes du code HTML**. Les résultats qui s’affichent à l’écran dépendent des demandes effectuées par l’utilisateur du site : le web est devenu **dynamique** 

Différents langages de programmation peuvent être utilisés « coté serveur » afin de permettre au serveur de générer lui-même le code HTML à envoyer. Le plus utilisé encore aujourd’hui se nomme **PHP**. D’autres langages sont utilisables côté serveur : Java, Python,… 

Par exemple : 
```php
<?php 
$heure = date("H:i"); 
echo '<h1>Bienvenue sur mon site</h1> 
	<p>Il est '.$heure.'</p>'; 
?> 
```


Si un client se connecte à un serveur web qui exécute ce code à 18h23, le serveur enverra au client le code HTML ci-dessous : 
```html
<h1>Bienvenue sur mon site</h1> 
<p>Il est 18h23</p>
```


## **2. Le<a name="_page1_x40.00_y233.92"></a> protocole HTTP** 
### **2.1. Qu’est<a name="_page1_x40.00_y255.92"></a> ce que c’est et quel est son rôle ?** 

Le **HTTP (HyperText Transfert Protocol)** va permettre au client **d’effectuer des requêtes** à destination d’un serveur web. En retour, le serveur web va envoyer **une réponse**.  

Le rôle de HTTP dans les interactions client-serveur est de fournir **une structure pour les requêtes et les réponses.**  La requête HTTP est composée de plusieurs lignes de texte qui **décrivent ce que le client demande au serveur**.  La réponse HTTP est également composée de plusieurs lignes de texte qui **décrivent ce que le serveur renvoie au client.** 

### **2.2. Les<a name="_page1_x40.00_y417.92"></a> codes de statut HTTP** 

Les **codes de statuts** sont des codes numériques qui indiquent **le résultat** d'une requête HTTP :  

- 200 et suivants indiquent une **réussite**.  
- 300 et suivants indiquent **un déplacement de la ressource demandée**.  
- 400 et suivants indiquent une **erreur du client** : requête mal formulée ou ressource inexistante (400: "Bad Request", 401: "Unauthorized", 402: "Payment Required", 403: "Forbidden", 404: "Not Found",...) 
- 500 et suivants indiquent une **erreur du serveur.** (500: "Internal Server Error", 501: "Not Implemented", 502: "Bad Gateway", 503: "Service Unavailable",...)

### **2.3. Principe<a name="_page1_x40.00_y564.92"></a> d’une requête** 

Composition simplifiée d’une requête HTTP (client vers serveur) : 

- La **méthode employée** pour effectuer la requête 
- L’**URL** de la ressource 
- La **version du protocole** utilisé par le client (souvent HTTP 1.1) 
- Le **navigateur employé** (Firefox, Chrome) et sa **version** 
- Le **type du document demandé** (par exemple HTML) 

#### **2.3.1. Ligne de Requête**
La première ligne d'une requête HTTP est la ligne de requête, qui spécifie le type de requête (méthode HTTP), l'URL de la ressource demandée, et la version du protocole HTTP.

**Exemple:**
```
GET /index.html HTTP/1.1
```
- **GET** : Méthode HTTP utilisée (GET, POST, PUT, DELETE, etc.).
- **/index.html** : URL de la ressource demandée.
- **HTTP/1.1** : Version du protocole HTTP.

#### **2.3.2. En-têtes de Requête (Headers)**
Les en-têtes de requête fournissent des informations supplémentaires sur la requête ou sur le client lui-même. Ils sont placés après la ligne de requête, chaque en-tête étant sur une nouvelle ligne.

**Exemple:**
```
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
```
- **Host** : Spécifie le domaine de destination (nécessaire pour les serveurs hébergeant plusieurs domaines).
- **User-Agent** : Fournit des informations sur le client (navigateur, système d'exploitation).
- **Accept** : Indique les types MIME que le client accepte.
- **Accept-Language** : Indique les langues préférées du client.

#### **2.3.3. Corps de la Requête (Request Body)**
Le corps de la requête est utilisé pour envoyer des données au serveur. Il est généralement utilisé avec les méthodes POST, PUT, et PATCH. Dans une requête GET, le corps est généralement vide.

**Exemple:**
Pour une requête POST envoyant des données de formulaire :
```
POST /submit-form HTTP/1.1
Host: www.example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

name=John&age=30&city=Paris
```
- **Content-Type** : Spécifie le type de données envoyées dans le corps de la requête.
- **Content-Length** : Spécifie la longueur du corps de la requête.
- Le corps de la requête : Contient les données réelles (ex: `name=John&age=30&city=Paris`).

Une requête HTTP utilise une méthode (c’est une commande qui demande au serveur d’effectuer une certaine action). Il y a plusieurs méthodes disponibles :
-	**GET** : c’est la méthode la plus courante pour demander une ressource. Elle est sans effet sur la ressource.
-	**POST** : cette méthode est utilisée pour soumettre des données en vue d’un traitement (côté serveur). Typiquement c’est la méthode employée lorsque l’on envoie au serveur les données issues d’un formulaire.
-	**DELETE** : cette méthode permet de supprimer une ressource sur le serveur.
-	**PUT** : cette méthode permet de modifier une ressource sur le serveur
-	**PATCH** : pour modifier une ressource existante

#### **2.3.4. Composition Complète de la Requête**
Voici à quoi ressemble une requête HTTP complète en utilisant une requête POST comme exemple :

```
POST /submit-form HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

name=John&age=30&city=Paris
```

- **Ligne de requête** : Début de la requête, spécifiant la méthode, l'URL et la version du protocole.
- **En-têtes de requête** : Informations supplémentaires sur la requête ou le client.
- **Corps de la requête** : Données envoyées au serveur (utilisé principalement dans les requêtes POST et PUT).

### **2.4. Réponse HTTP du Serveur avec PHP**

#### **2.4.1. En-têtes de Réponse**
Les en-têtes de réponse restent les mêmes.

**Exemple:**
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: [calculated automatically by server]
Connection: keep-alive
```
**Ligne de Statut** :
   - `HTTP/1.1 200 OK` : Indique que la requête a été traitée avec succès et que le serveur renvoie la page demandée.

**En-têtes de Réponse** :
   - `Content-Type: text/html; charset=UTF-8` : Indique que le contenu de la réponse est une page HTML encodée en UTF-8.
   - `Content-Length: [calculated automatically by server]` : La longueur du corps de la réponse est calculée automatiquement par le serveur.
   - `Connection: keep-alive` : Indique que la connexion doit rester ouverte pour les requêtes suivantes.

#### **2.4.2. Corps de la Réponse avec PHP**

Le corps de la réponse contient le code HTML avec du PHP pour afficher dynamiquement les informations.

**Exemple:**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Bienvenue</title>
</head>
<body>
    <?php
    // Récupérer les données POST
    $name = $_POST['name'];
    $city = $_POST['city'];
    ?>
    <h1>Bienvenue sur mon site, <?php echo htmlspecialchars($name); ?> de <?php echo htmlspecialchars($city); ?>!</h1>
    <p>Nous sommes heureux de vous accueillir.</p>
</body>
</html>
```
**Corps de la Réponse avec PHP** :
   - Utilise PHP pour récupérer les données de la requête POST.
   - Utilise `htmlspecialchars` pour échapper correctement les caractères spéciaux et éviter les attaques XSS.
   - Génère dynamiquement le message de bienvenue avec le nom et la ville fournis.


Une fois la requête reçue, le serveur va renvoyer une réponse, par exemple : 
```html
Date: Thu, 15 feb 2019 12:02:32 GMT 
Server: Apache/2.0.54 (Debian GNU/Linux) DAV/2 SVN/1.1.4 
Connection: close 
Transfer-Encoding: chunked 
Content-Type: text/html; charset=ISO-8859-1 

<!doctype html> 
<html lang="fr"> 
<head> 
<meta charset="utf-8"> 
<title>Voici mon site</title> 
</head> 
<body> 
<h1>Hello World! Ceci est un titre</h1> 
<p>Ceci est un <strong>paragraphe</strong>. Avez-vous bien compris ?</p> 
</body> 
</html>
```


Le **HTTPS** est la version « sécurisée » du protocole HTTP : les données **sont chiffrées avant d’être transmises sur le réseau.** Lorsque la communication avec un site WEB est sécurisée, la barre d’adresse commence par un **cadenas**. 


![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.028.jpeg)

### **2.4. Syntaxe<a name="_page3_x40.00_y314.92"></a> complète des URL** 

La syntaxe des URL est de la forme ```protocole://nom-ou-adresse:port/document?n1=v1&…nk=vk#id```

- Le port est **le port TCP** sur lequel effectuer la connexion.  
- Le document est écrit comme **chemin relatif** à partir du répertoire où est stocké le site sur le serveur. La partie marquée par un « ? » est la liste des **paramètres de requête**.  
- Ces paramètres sont des paires ni=vi où ni est le **nom du paramètre** et vi sa **valeur**. La portion finale #id est appelé un **signet** et permet de cibler un élément particulier dans la ressource demandée. 



**Activité n°1.** Passage de paramètre  un serveur 

- Aller sur[ HTTPs://fr.wikipedia.org ](https://fr.wikipedia.org/)
- Dans la zone de recherche taper informatique 
- Noter URL complète obtenue 
- Aller sur[ HTTPs://fr.wikipedia.org/w/index.php?search=informatique.](https://fr.wikipedia.org/w/index.php?search=informatique) Que remarque-t-on ? 
- Aller sur[ HTTPs://fr.wikipedia.org/wiki/Informatique#Algorithmique.](https://fr.wikipedia.org/wiki/Informatique#Algorithmique) Que remarque-t-on ? 

En fait sur la page la portion de code HTML correspondant est : 

```<span… id="Algorithmique">Algorithmique</span>```

## **3.  Coder l’envoi d’une requête par le navigateur<a name="_page3_x40.00_y617.92"></a>** 

Il existe plusieurs manières d'envoyer une requête HTTP depuis un navigateur. Voici quelques-unes des méthodes les plus courantes : 

- **En utilisant une URL dans la barre d'adresse du navigateur** : le navigateur envoie une requête **GET** à la ressource indiquée dans la URL. 
- **En utilisant un formulaire HTML** : un formulaire HTML peut être soumis en utilisant la méthode **GET** ou la méthode **POST**. La requête envoyée inclura les données saisies dans les champs du formulaire.
- **En utilisant JavaScript** : en utilisant JavaScript, vous pouvez envoyer une requête HTTP en utilisant l'objet **XMLHttpRequest** ou en utilisant une bibliothèque telle que jQuery. Cela permet de faire des requêtes **GET**, **POST**, **PUT**, **DELETE**, etc. en fonction de vos besoins. 

### **3.1. Exemples<a name="_page4_x40.00_y36.92"></a> de formulaire HTML**
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.039.png)


**Activité n°2.** : Ouvrir un bloc note. Ajouter le script suivant et vérifier ce qu’on obtient dans le navigateur. Enregistrer le sous index.html **ATTENTION** à bien sélectionner tous les fichiers !

![](AZE.png)
```html
<!DOCTYPE html>
<head>
  <meta charset="UTF-8">
  <title>requête</title>
</head>
<body>
<form method='GET' action='./login'>
    <input name='user' type='text' required>
    <input name='password' type='password' required>
    <button type='submit'>login</button>
</form>
</body>
```



**Activité n°3. :** Remplir ce formulaire et le soumettre fera envoyer une requête GET vers l'URL ./login. Observer la nouvelle URL

Avec la méthode GET, les données du formulaire seront encodées **dans l'URL.**  

Si on saisit trois valeurs par exemple «Dupont », « azerty » et qu’on clique sur le bouton, alors le navigateur charge la page correspondante à ```user=dupont&password=*****```

 

**Activité n°4. :** Modifier la page pour pouvoir la soumettre avec une requête POST. Remplir ce formulaire et le soumettre fera envoyer une requête POST et observer la nouvelle URL.

Dans le cas d'un POST ils seront alors encodés **dans le corps de la requête**. 

### **3.2. Les<a name="_page4_x40.00_y568.92"></a> éléments d’un formulaire HTML**

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.047.jpeg)

| Type         | Description                                                                            |
|--------------|----------------------------------------------------------------------------------------|
| `<button>`   | Définit un bouton cliquable.                                                           |
| `<fieldset>` | Regroupe les éléments liés dans un formulaire.                                         |
| `<form>`     | Définit le conteneur de formulaire.                                                    |
| `<input>`    | Définit un champ de saisie. HTML5 définit plus de 20 types d'entrée différents.        |
| `<label>`    | Définit une étiquette pour un élément d’entrée de formulaire.                          |
| `<legend>`   | Définit l'étiquette d'un groupe de champs.                                             |
| `<option>`   | Définit une option dans une liste multi-éléments.                                      |
| `<optgroup>` | Définit un groupe d'options connexes dans une liste à éléments multiples.              |
| `<select>`   | Définit une liste à choix multiples.                                                   |
| `<textarea>` | Définit une zone de saisie de texte multiligne.                                        |


### **3.3. Elément<a name="_page5_x40.00_y275.92"></a> ```<input>``` : quelques exemples**

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.050.png)

### **3.4. Elément<a name="_page5_x40.00_y485.92"></a> ```<select>``` : quelques exemples**

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.052.png)

### **3.5. Elément<a name="_page6_x40.00_y36.92"></a> value dans ```<select>```**

L'attribut value de l'élément est utilisé pour spécifier quelle valeur sera renvoyée au serveur. L'attribut value est **facultatif**. S’il n’est pas spécifié, alors **le texte** dans le conteneur **est envoyé à la place** 

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.055.png)

### **3.6. Les<a name="_page6_x40.00_y300.92"></a> boutons de commande** 

| Type                      | Description                                                                                                                                                       |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `<input type="submit">`   | Crée un bouton qui soumet les données du formulaire au serveur.                                                                                                    |
| `<input type="reset">`    | Crée un bouton qui efface les données de formulaire déjà entrées par l’utilisateur.                                                                                |
| `<input type="button">`   | Crée un bouton personnalisé. Ce bouton peut nécessiter l’ajout de Javascript à toute action.                                                                       |
| `<input type="image">`    | Crée un bouton de soumission personnalisé qui utilise une image pour son affichage.                                                                                |
| `<button>`                | Crée un bouton personnalisé. L'élément `<button>` diffère de `<input type="button">` en ce que vous pouvez complètement personnaliser ce qui apparaît dans le bouton. |
|                           | En l’utilisant, vous pouvez par exemple inclure à la fois des images et du texte ou ignorer entièrement le traitement côté serveur à l’aide de liens hypertexte.     |
|                           | Vous pouvez transformer le bouton en bouton de soumission en utilisant l’attribut type = = `submit`.                                                                 |                                                                 |
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.057.png)

**ATTENTION** à ne pas confondre :

-	```<button>``` avec ```<input type=’button’>```

-	```<input type=’submit’>``` avec ```<button type=’submit’>```



### **3.7. Comment<a name="_page7_x40.00_y36.92"></a> le formulaire interagit avec le serveur ?** 

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.059.jpeg)

### **3.8. Précision<a name="_page7_x40.00_y370.92"></a> sur la méthode GET ou POST** 

Lors de l’utilisation de la méthode GET dans un formulaire**, les données sont transmises en clair** dans la barre d’adresse du navigateur. Dans les faits, on obtient ```action.php?identifiant=<texte entré>```.  

L’intérêt de la méthode GET est que toutes l’information nécessaire est contenue dans l’URL. Il est donc possible de recharger plusieurs fois la même URL.  

**Par exemple** :[ HTTPs://www.data.gouv.fr/fr/search/?q=informatique.](https://www.data.gouv.fr/fr/search/?q=informatique) 

Par contre les URL ne peuvent **pas être de taille longue** : si le **champ du formulaire est long** le serveur peut renvoyer un **code d’erreur 414.**  

De plus, les mots de passes sont affichés comme une suite d’étoile dans l’URL mais lorsqu’ on clique sur le bouton le navigateur exécute la requête et affiche sans sa barre d’adresse URL **le mot de passe en clair**, et une personne présente à proximité de l’écran peut le voir. 

Les caractéristique de la méthode POST sont exactement inverses. Lors du processus de soumission, l’URL n’est pas suffisante : il faut que les paramètres soient passés dans le corps de la requête. On ne pourra **pas sauvegarder l’URL**. **Si la taille des paramètres** envoyés est **trop importante** alors seule la méthode POST garanti que la requête ne sera pas tronquée. De même, pour les formulaires demandant un **mot de passe**, la méthode POST ne rendra **pas visible** ce dernier dans la barre d’adresse.  

GET : 

- Les données transmises sont visibles dans la barre d’adresse 
- Les données restent dans l’historique du navigateur et dans le cache 
- Les données peuvent être stockées dans un signet 
- Limite le nombre de caractères dans les données de formulaire renvoyées 

POST : 

- Les données peuvent contenir des données binaires 
- Les données sont masquées à l’utilisateur 
- Les données soumises ne sont pas stockées dans le cache, l’historique ou les signets 

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.061.jpeg)

GET vs POST 

### **3.9. Les<a name="_page8_x40.00_y290.92"></a> cookies** 

Il est important pour un site web de pouvoir identifier ces différents clients. Il utilise des **cookies**. C’est une petite quantité de données. Il est composé d’un nom, d’une valeur et optionnellement d’une date d’expiration. Le nom, la valeur et la durée de vie sont choisie par le serveur.  

Lorsqu’un serveur veut déposer un cookie particulier chez un client, il l’envoie comme un entête de réponse HTTP.  **Par exemple** 
```html
HTTP/1.1 200 OK  
Server: nginx/1.10.3 (Ubuntu)  
Date: Thu, 15 feb 2019 12:02:32 GMT  
Content-Type: text/html 
Content-Length: 1023 
Set-Cookie: test=42; Expire=Mon, 30 May 2019 18:10:12 GMT; 
... 
```

Le navigateur Web du client voit que le serveur lui envoie un **cookie** dont le nom est test, la valeur est 42 et la date d’expiration est le 30 mai 2019 à 18h10,12.  

Le **navigateur stocke le cookie** en l’associant au nom de domaine du site visité. Lorsque le navigateur effectue une nouvelle connexion, il **renvoie le cookie** au serveur dans sa requête, si la date d’expiration n’est pas dépassée. 

## **4. APPLICATION<a name="_page8_x40.00_y503.92"></a> : Création d’une page web dynamique**
### **4.1. Mise<a name="_page8_x40.00_y525.92"></a> en place d’un serveur en Python ou un serveur Apache Lamp**
En fin d’année ….  
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.067.png)

2. **Mise<a name="_page8_x40.00_y565.92"></a> en place d’un serveur Apache Wamp**  

Installer un serveur sous Windows avec uniform server (version super  simple et light) :  

[https://sourceforge.net/projects/miniserver/files/ ](https://sourceforge.net/projects/miniserver/files/) 

Il se trouve déjà dans C:\UniServerZ  
```
1 Start UniController (click cancel)
2 Create a server certificate:
   From UniController: Apache >  Apache SSL > click "Server Certificate and Key generator"  
   Server Certificate and Key generator form opens click "Generate" button
   A confirmation pop-up displayed, click OK button
3 From UniController enable module: Apache > Edit Basic and Modules > click "Apache Modules Enable/Disable"
   Apache Modules Enable/Disable form opens.
   Navigate to entry "http2_module" and click check box to the left of it.
   Close form, click cross top right.
4 Firefox download and install the following  Firefox plugin:
    https://addons.mozilla.org/fr/firefox/addon/http2-indicator/
----
Test
----
5 Start Apache server
6 Click "View ssl" page button
   Firefox "This connection is untrusted", click "I understand the risks" and click  "Add exception"
   The add security exception form is displayed, click "Confirm Security Exception"
7 Firefox lightning indicator in browser address bar confirms http2 is working.
```


### **4.3. Formulaire<a name="_page9_x40.00_y154.92"></a> d’une page Web version php**
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.072.png)

PHP est un langage de programmation qui s'intègre dans vos pages  HTML. Le sigle PHP est un acronyme récursif pour : PHP **Hypertext  Preprocessor** ! Il permet la **génération automatisée** (Preprocessor)  de vos pages Web (Hypertext). Celles-ci peuvent ainsi **s'adapter à la  demande ou suivant certaines conditions**. C'est pour cela que l'on  parle de pages **web dynamiques.**   

Cas très simple où le serveur va renvoyer au client une simple page HTML statique. Le  serveur Web Apache a été configuré pour qu'il envoie vers le client une page HTML située  dans un répertoire nommé "www", ce répertoire "www" devant se trouver dans votre répertoire UniServerZ. 



**Activité n°5.** Créer un fichier "index.html", placez ce fichier "index.html" dans le répertoire "www".

**Activité n°6.** Copier le code HTML ci-dessous dans le fichier "index.html". 
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Utilisation d'Apache</title>
    </head>
    <body>
        <p>Le serveur Apache fonctionne parfaitement</p>
    </body>
</html>
```



**Activité n°7. :** Ouvrir votre navigateur Web et taper dans la barre d'adresse "localhost". On devrait voir la page Web s'afficher. 

Avec le "localhost", on indique au navigateur que le serveur Web se trouve sur le même ordinateur que lui (on parle de machine locale). Dans un cas normal, la barre d'adresse devrait être renseignée avec l'adresse du serveur Web. 

Pour l'instant, le site est **statique** : la page reste identique, quelles que soient les actions des visiteurs. Pour avoir un **site dynamique**, nous allons **exécuter, côté serveur, un programme qui va créer de toute pièce une page HTML**, cette page HTML sera ensuite envoyée au client par l'intermédiaire du serveur Web. Il existe différents langages de programmation qui permettent de générer des pages HTML à la volée **: Python, Java, Ruby...** Dans notre cas, nous allons utiliser le **PHP.**  

Le PHP est un langage très utilisé même si dans le monde professionnel Java, Python, Ruby,... sont préférés au PHP.  

Il est très important de bien comprendre les processus mis en œuvre : 

- **le client (le navigateur Web) envoie** une requête HTTP vers un serveur Web 
- en fonction de la requête reçue **le serveur "fabrique" une page HTML** grâce à l'exécution d'un programme écrit en PHP (ou en Python, Java...) 
- **le serveur Web envoie la page nouvellement créée au** client 
- une fois reçue, **la page HTML est affichée dans le navigateur** Web 

Le langage PHP est déjà installé sur l'ordinateur avec UniServerZ. 

**Activité n°8. :** Après avoir supprimé le fichier "index.html" préalablement créé dans le répertoire "www", créer un fichier "index.php", toujours dans le répertoire "www". 

**Activité n°9. :** Copier le code PHP ci-dessous dans le fichier "index.php" 
```php
<?php
$heure = date("H:i");
echo '<h1>Bienvenue sur mon site</h1>
      <p>Il est '.$heure.'</p>';
?>
```

**Activité n°10** Ouvrir votre navigateur Web et taper dans la barre d'adresse "localhost". 

On doit avoir une page HTML qui donne l'heure, si on **actualise** la page, **l'heure évolue**. On a donc bien une page dynamique : le serveur PHP crée la page Web au moment où elle est demandée. À chaque fois que la page est actualisée, la page HTML est générée de nouveau. 

L’extension ".html" a été remplacée par ".php". Au moment de la requête, le programme contenu dans ce fichier a été exécuté et la page HTML a été générée. Dans les 2 cas, le fichier se nomme "index", car par défaut, le serveur prend en compte un fichier nommé "index" ("index.php" ou "index.html" selon les cas).  

**Comment ça marche ?** 

- "```$heure = date("H:i");```", "```$heure```" est une variable (en **PHP les variables commencent** par **un "**$**"**), cette variable "contient" une chaîne de caractères qui correspond à l'heure courante 
- **l'instruction "**```echo```**" permet d'afficher la chaîne de caractères** **qui suit l'instruction**. 

Dans  notre  cas,  la  chaîne  de  caractères  est  "```<h1>Bienvenue  sur  mon  site</h1>  <p>Il  est '.$heure.'</p>```" ce qui correspond à du HTML à l'exception de "$heure" qui permet d'afficher le contenu de la variable "```$heure```".  

La page Web générée contiendra le code HTML et le contenu de la variable "$heure".  

**Le point "**.**" est, en PHP, l'opérateur de concaténation** (alors que par exemple en Python, l'opérateur de concaténation est le "+")  

Si un client effectue une requête à 18h23, le serveur enverra au client le code HTML ci-dessous : 
```html
<h1>Bienvenue sur mon site</h1> 
<p>Il est 18h23</p> 
```
**Activité n°11. :** Après avoir supprimé le fichier "index.php" préalablement créé dans le répertoire "www", créer un fichier "index.html", et un fichier « trait_form.php » toujours dans le répertoire "www". 

**Activité n°12. :** Copier le code HTML ci-dessous dans le fichier "index.html". 
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Le formulaire</title>
    </head>
    <body>
        <form action="trait_form.php" method="post">
                <label>Nom</label> : <input type="text" name="nom" />
                <label>Prénom</label> : <input type="text" name="prenom" />
                <input type="submit" value="Envoyer" />
        </form>
    </body>
</html>
```


Et le code PHP dans le fichier « trait_form.php » 
```php
<?php
    $n=$_POST['nom'];
    $p=$_POST['prenom'];
    echo "<p>Bonjour ".$p." ".$n.", j'espère que vous allez bien.</p>";
?>
```


**Activité n°13. :** Ouvrir le navigateur Web et taper dans la barre d'adresse "localhost". Une fois la page Web affichée dans votre navigateur, remplir le formulaire proposé et valider en cliquant sur le bouton "Envoyer" 

**Comment ça marche ?** 

- **Dans la page en HTML** :   

Dans la balise ```<form>``` du code HTML, il y a 2 attributs : « action » et « method ».  

- L’attribut ```action="trait_form.php"```  indique que le client enverra une requête http vers le serveur en cas de click sur le bouton « envoyer ». Pour répondre à cette requête du client, le serveur devra exécuter le programme PHP contenu dans le fichier « trait_form.php ».  
- La ```method="post"``` indique que la méthode utilisée pour effectuer cette requête http est une méthode « POST » . 

Au niveau des deux balises « input » permettant de saisir le nom et le prénom, on voit l’attribut « name »   

- **Dans la page en PHP** :  
- la ligne ```$n=$\_POST['nom'];``` permet d’attribuer à la variable $n la chaine de caractères qui a été saisie par l’utilisateur dans le formulaire : balise input ayant l’attribut name="nom". Le nom de ```$_POST['nom']``` est directement lié au nom de l’attribut ```name="nom"```.
- Le principe est le même pour la variable $p : le ```prenom``` de ```$_POST['prenom']``` est directement lié au prenom de l’attribut ```name="prenom"```.
Un ```$_POST['toto']```  contiendra  la  chaine  de  caractère  saisie  par  l’utilisateur  dans  le  champ correspondant à une balise input possédant un attribut ```name="toto"```. 

- ```echo "<p>Bonjour ".$p." ".$n.", j'espère que vous allez bien.</p>"```  contient l’instruction echo déjà vu précédemment 

Un clic sur le bouton "Envoyer" **déclenche une requête HTTP** vers le serveur et que les informations saisies dans le formulaire sont envoyées vers le serveur (puisqu'il est possible de récupérer ces informations au niveau du code PHP : une fois de plus, le code **PHP est uniquement exécuté du côté serveur**).  

Ces informations transitent entre le client et le serveur selon méthode utilisée par la requête HTTP. Dans l'exemple ci-dessus, la méthode utilisée est la méthode "POST" ("```method="post```"). 

**Activité n°14. :** Ouvrir le navigateur Web et taper dans la barre d'adresse "localhost". Une fois la page Web affichée dans le navigateur, Saisissez "Sophie" pour le prénom et "Martin" pour le nom puis valider en cliquant sur le bouton "Envoyer". Observer attentivement la barre d'adresse du navigateur.  

Dans la barre d'adresse, rien de spécial à signaler, on constate que le fichier "trait_form.php" a bien été utilisé. Il est possible d'utiliser une méthode HTTP "GET" à la place de la méthode "POST" (dans la suite du cours) 

**Activité n°15. :** Modifier les fichiers "index.html" et "trait_form.php" comme suit : 
Pour index.html
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Le formulaire</title>
    </head>
    <body>
        <form action="trait_form.php" method="get">
                <label>Nom</label> : <input type="text" name="nom" />
                <label>Prénom</label> : <input type="text" name="prenom" />
                <input type="submit" value="Envoyer" />
        </form>
    </body>
</html>
```


Pour trait_form.php 
```php
<?php
    $n=$_GET['nom'];
    $p=$_GET['prenom'];
    echo "<p>Bonjour ".$p." ".$n.", j'espère que vous allez bien.</p>";
?>
```



**Activité n°16. :** Ouvrir le navigateur Web et taper dans la barre d'adresse "localhost". Une fois la page Web affichée dans votre navigateur, Saisir le prénom et le nom puis valider en cliquant sur le bouton "Envoyer". **Observer attentivement la barre d'adresse du navigateur.** 

Cette  fois-ci,  les  informations  du  formulaire  sont  transmises  au  serveur  par  l'intermédiaire  de  l'url  : ```localhost/trait_form.php?nom=tartempion&prenom=tartiflette```

Dans le cas de l'utilisation d'une méthode "POST" les données issues d'un formulaire sont envoyées au serveur **sans être directement visibles**, alors que dans le cas de l'utilisation d'une méthode "GET", les données **sont visibles** (et accessibles) puisqu'elles sont envoyées par l'intermédiaire de l'url. 

Les données envoyées par l'intermédiaire d'une méthode "GET" peuvent être modifiées directement dans l'url. 

**Activité n°17. :** Ouvrir le navigateur Web et taper dans la barre d'adresse "localhost". Une fois la page Web affichée dans votre navigateur, Saisir le prénom et le nom puis valider en cliquant sur le bouton "Envoyer". Modifier l'url : "```localhost/trait_form.php?nom=Martin&prenom=Jean-Pierre```", validez votre modification en appuyant sur la touche "Entrée". 

Normalement la page a bien été modifiée : "Bonjour Jean-Pierre Martin, j'espère que vous allez bien." 

Même si dans notre cas cette opération de modification d'URL est inoffensive, il faut bien se douter que dans des situations plus complexes, une telle modification pourrait entrainer des conséquences plus problématiques (piratage). **Il faut donc éviter d'utiliser la méthode "**GET**" pour transmettre les données issues d'un formulaire vers un serveur.** 

Il est important de bien comprendre que la méthode "POST" **n'offre pas non plus une sécurité absolue** puisque toute personne ayant un bagage technique minimum sera capable de lire les données transmises à l'aide de la méthode "POST" en analysant la requête HTTP, même si ces données ne sont pas directement visibles dans l'URL. Seule l'utilisation du **protocole sécurisé HTTPS** garantit un transfert sécurisé des données entre le client et le serveur (les données sont chiffrées et donc illisibles pour une personne ne possédant pas la clé de déchiffrement). 

Si le PHP vous passionne :  

- Introduction.[ http://www.phpdebutant.org/article118.php ](http://www.phpdebutant.org/article118.php)
- Afficher une phrase ou une image.[ http://www.phpdebutant.org/article14.php ](http://www.phpdebutant.org/article14.php) 
- Afficher la date et l'heure.[ http://www.phpdebutant.org/article53.php ](http://www.phpdebutant.org/article53.php) 
- PHP dans du code HTML.[ http://www.phpdebutant.org/article54.php ](http://www.phpdebutant.org/article54.php) 
- La concaténation.[ http://www.phpdebutant.org/article55.php ](http://www.phpdebutant.org/article55.php) 
- Récupérer les valeurs d'un formulaire.[ http://www.phpdebutant.org/article56.php ](http://www.phpdebutant.org/article56.php) 
- Les structures de contrôle.[ http://www.phpdebutant.org/article57.php ](http://www.phpdebutant.org/article57.php) 
- Ecrire et lire dans un fichier texte.[ http://www.phpdebutant.org/article58.php ](http://www.phpdebutant.org/article58.php) 
- Les fonctions utilisateurs.[ http://www.phpdebutant.org/article59.php ](http://www.phpdebutant.org/article59.php) 
- Les variables d'environnement.[ http://www.phpdebutant.org/article60.php ](http://www.phpdebutant.org/article60.php) 
- Quelques fonctions utiles.[ http://www.phpdebutant.org/article61.php ](http://www.phpdebutant.org/article61.php) 
- Les sessions.[ http://www.phpdebutant.org/article69.php ](http://www.phpdebutant.org/article69.php) 

Editeurs PHP en ligne : 

- [http://phpfiddle.org/ ](http://phpfiddle.org/) 
- [https://www.runphponline.com/ ](https://www.runphponline.com/) ![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.008.png)

## **5. POUR<a name="_page13_x40.00_y36.92"></a>  ALLER  PLUS  LOIN :  Formulaire  d’une  page  Web  version  Flask**  
![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.102.png)

Vérification  que  **flask**  est  installée :  dans  la  console  python   

**Activité n°18. :**  
```python
>>> import flask 
```
Si flask n’est pas installé : lancer **l’invite de commande  windows** en mode administrateur (taper cmd dans la barre  de recherche de windows) puis bouton droit et « exécuter  en tant qu’administrateur ».  

Mise à jour de l’installateur *pip* de python : 
```
python -m pip install --upgrade pip 
```
Installation de flask :  
```
python -m pip install flask 
```
on peut en profiter pour installer d’autres bibliothèques : 
```
python -m pip install pillow numpy pygame matplotlib ipython jupyter pandas sympy nose 

ou python -m pip install -U matplotlib 
ou python -m pip install --user pygame --user 
```
-U est l’abréviation de --user. De même python peut être remplacé par py. 

Comme déjà évoqué dans la partie consacrée au modèle client-serveur, **un serveur web** (aussi appelé serveur HTTP) **permet de répondre à une requête HTTP effectuée par un client** (très souvent un navigateur web). On va travailler avec le serveur web qui est installé sur l’ordinateur. La configuration est un peu particulière puisque le client et le serveur vont se trouver sur la même machine. Cette configuration est classique lorsque l'on désire effectuer de **simples tests**. Il y aura donc 2 logiciels sur le même ordinateur :  

- **le client (navigateur web)**  
- **le serveur (serveur web),**  

Ces 2 logiciels vont communiquer en utilisant le protocole **HTTP.** Il existe de nombreux serveurs web, mais le plus utilisé se nomme **Apache** (qui  été aperçu dans un autre épisode). Ici, on va travailler avec le **framework Python Flask**. Ce framework va nous permettre de générer des pages web côté serveur, il **possède son propre serveur web**. 

### **5.1. Cas<a name="_page13_x40.00_y512.92"></a> très simple où le serveur va renvoyer au client une simple page HTML statique.**  

**Activité n°19. :** Dans le répertoire Documents , créez un répetoire nommé "flask". 

**Activité n°20. :** À l'aide d’un éditeur python (Idle ou PyCharm ou …), créer un fichier Python "views.py" (ce fichier devra  être  sauvegardé  dans  le  répertoire  "flask"  précédemment  créé).  Saisir  le  code  suivant  dans  le  fichier "views.py" 
```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
  return "<p>Tout fonctionne parfaitement</p>"

app.run(debug=True)
```


**Activité n°21.**  Après avoir exécuté le programme ci-dessus, ouvrir le navigateur web et taper dans la barre d'adresse "localhost:5000". 

On devrait voir la phrase "Tout fonctionne parfaitement" s'afficher dans votre navigateur. 

**Activité n°22. :** Stopper l'exécution du programme **Comment ça marche ?** 

- Le serveur et le client se trouvent sur la même machine, avec le "localhost", on indique au navigateur que le serveur web se trouve sur le même ordinateur que lui (on parle de machine locale). Dans un cas normal, la barre d'adresse devrait être renseignée avec l'adresse du serveur web. Le "5000" indique le **port**. 
- En exécutant le programme Python ci-dessus, le framework Flask a lancé un serveur web. Ce **serveur web attend des requêtes HTTP sur le port 5000**. En ouvrant un navigateur web et en tapant "localhost:5000", nous faisons une **requête HTTP**, le serveur web fourni avec Flask répond à cette requête HTTP en envoyant une page web contenant uniquement "```<p>Tout fonctionne parfaitement</p>```". 



```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
  return "<p>Tout fonctionne parfaitement</p>"


app.run(debug=True)
```
- Import de la bibliothèque Flask
- Création d’un objet app (toujours nécessaire)
- Décoration (ne sera pas traitée en NSI)
- Fonction qui sera exécutée si le serveur reçoit une requete http avec une URL correspondant à la racine du site (‘/’), c’est-à-dire dans l’exemple, le cas où on saisie dans la barre d’adresse  « localhost:5000/ » (ou « localhost:5000 »)
- En cas de requête http d’un client avec l’URL « / » , le serveur renvoie vers le client une page HTML contenant uniquement la ligne entre les balises <p>
- Permet de lancer le serveur (toujours nécessaire)

**Activité n°23. :** modifier le fichier Python "views.py" : 
```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
  return "<p>Tout fonctionne parfaitement</p>"
@app.route('/about')
def about():
  return "<p>Une autre page</p>"
app.run(debug=True)
```


**Activité n°24. :** Après avoir exécuté le programme ci-dessus, saisir "localhost:5000/about" dans la barre d'adresse du navigateur. 

Le serveur renvoie dans ce cas une autre page. Évidemment l'URL racine ("/") reste disponible, on peut passer d'une page à l'autre en modifiant l'URL dans la barre d'adresse ("localhost:5000" ou "localhost:5000/about") 

**Écrire le code HTML qui devra être renvoyé au client dans le programme Python n'est pas très pratique, Flask propose une autre solution bien plus satisfaisante.** 

**Activité n°25. :** Dans votre répertoire "flask", créer un répertoire "templates". Dans ce répertoire templates, créer un fichier rindex.html. Saisir le code HTML ci-dessous dans ce fichier index.html (avec un éditeur HTML notepad++, VisualStudio…) 
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Ma page</title>
    </head>
    <body>
      <h1>Mon super site</h1>
      <p>Tout fonctionne parfaitement</p>
    </body>
</html>
```


**Activité n°26. :** Modifier le programme views.py comme suit :  
```python
from flask import Flask, render_template

app = Flask(__name__) 

@app.route('/') 

def index(): 

    return render_template("index.html") 

app.run(debug=True) 
```

**Activité n°27. :** Relancer le programme Python et taper "localhost:5000" dans la barre d'adresse de votre navigateur. Dans Firefox CTRL+MAJ+K observer les requêtes qui apparaissent dans la console > requetes de Firefox 

Le serveur renvoie maintenant au client la page HTML correspondant au fichier "index.html" qui a été créé dans le répertoire "templates". Attention, les fichiers HTML devront systématiquement se trouver dans un répertoire nommé "templates". N.B. **le "**debug=True**" de la dernière ligne permet de modifier les fichiers HTML sans être obligé de redémarrer le programme "**views.py**".** 

### **5.2. Cas<a name="_page15_x40.00_y246.92"></a> où le serveur va renvoyer au client une simple page HTML dynamique**  

Pour l'instant le **site est statique** : la page reste identique, quelles que soient les actions des visiteurs. Flask permet de créer des pages dynamiques : 

- **le client (le navigateur web) envoie une requête HTTP** vers un serveur web 
- en fonction de la requête reçue et de différents paramètres, **Flask "fabrique" une page HTML différente** 
- le **serveur web associé à Flask envoie la page nouvellement créée** au client 
- une fois reçue, la **page HTML est affichée dans le navigateur web** 

**Activité n°28. :** Arrêter le programme précédant et modifier le fichier views.py comme suit : 
```python
from flask import Flask, render_template 
import datetime 

app = Flask(__name__) 

@app.route('/') 
def index(): 
    date = datetime.datetime.now() 
    h = date.hour 
    m = date.minute 
    s = date.second 
    return render_template("index.html"**,** heure = h**,** minute = m**,** seconde = s) 

app.run(debug=True) 
```
Dans le programme ci-dessus on importe le module "datetime" afin de pouvoir déterminer la date et l'heure courante.  Après l'exécution des 3 lignes ci-dessus, les variables h, m et s contiennent l'heure courante. 

La fonction "render_template" contient 3 paramètres de plus par rapport à l'exemple de l’application précédente : le paramètre "heure", le paramètre "minute" et le paramètre "seconde", on va retrouver ces 3 paramètres dans le fichier HTML. 

**Activité n°29. :** Modifier le fichier "index.html" comme suit : 
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Utilisation de Flask</title>
    </head>
    <body>
      <h1>Mon super site</h1>
      <p>Le serveur fonctionne parfaitement, il est {{heure}} h {{minute}} minutes et {{seconde}} secondes</p>
    </body>
</html>
```


**Activité n°30. :** Tester ces modifications en saisissant "localhost:5000" dans la barre de votre navigateur web. 

La page affichée est une **page dynamique**, puisqu'à chaque fois que le client actualise la page dans son navigateur, l'heure courante s'affiche. En fait,  à chaque fois que le client actualise la page, il effectu**e une nouvelle requête** et en réponse à cette requête, le serveur envoie une **nouvelle page HTML.** 

Attention, il est bien important de comprendre que la **page HTML envoyée par le serveur au client ne contient plus les paramètres** {{heure}}, {{minute}} et {{seconde}}**.** Au moment de créer la page, le serveur remplace ces paramètres par les valeurs passées en paramètres de la fonction "render_template" (s'il est 14 h 45 minutes et 31 secondes, le serveur remplacera "Le serveur fonctionne parfaitement, il est {{heure}} h {{minute}} minutes et {{seconde}} secondes" par "Le serveur fonctionne parfaitement, il est 15 h 45 minutes et 31 secondes"). 

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.116.png)

Le fichier "index.html" ne contient donc pas du HTML (même si cela ressemble beaucoup  à du HTML), car les paramètres {{heure}}, {{minute}} et {{seconde}} n'existent pas en  HTML. Le fichier "index.html" contient en fait un langage de template nommé **Jinja**. Jinja  ressemble beaucoup au HTML, mais il rajoute beaucoup de fonctionnalités par rapport au  HTML (notamment les paramètres entourés d'une double accolade comme {{heure}}). Si on  utilise Jinja seul (sans un framework comme Flask), les paramètres ne seront pas remplacés  et le navigateur affichera "Le serveur fonctionne parfaitement, il est {{heure}}  h {{minute}} minutes et {{seconde}} secondes". 

### **5.3. Gestion<a name="_page16_x40.00_y321.92"></a> des formulaires**  

**Activité n°31. :** Modifier le fichier "index.html" comme suit : 
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Le formulaire</title>
    </head>
    <body>
        <form action="http://localhost:5000/resultat" method="post">
                <label>Nom</label> : <input type="text" name="nom" />
                <label>Prénom</label> : <input type="text" name="prenom" />
                <input type="submit" value="Envoyer" />
        </form>
    </body>
</html>
```

 

**Activité n°32. :** créer un fichier "resultat.html" (dans le répertoire "templates"), ce fichier devra contenir le code suivant : 
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Résultat</title>
    </head>
    <body>
        <p>Bonjour {{prenom}} {{nom}}, j'espère que vous allez bien.</p>
    </body>
</html>
```


**Activité n°33. :** Arrêter le programme précédant et modifier le fichier views.py comme suit :
```python 
from flask import Flask, render_template, request

app = Flask(__name__) 

@app.route('/') 
def index(): 
    return render_template('index.html') 

@app.route('/resultat',methods = ['POST']) 
def resultat(): 
    result = request.form 
    n = result['nom'] 
    p = result['prenom'] 
    return render_template("resultat.html", nom=n, prenom=p) 

app.run(debug=True) 
```

**Activité n°34. :** Après avoir relancé "views.py", tester en saisissant "localhost:5000" dans la barre d'adresse du navigateur web. Saisir le nom et le prénom dans les champs "Nom" et "Prénom" du formulaire, et appuyer sur le bouton "Envoyer". 

**Que sait-il passé** ?  

On effectue une requête HTTP avec l'URL "/", le serveur génère une page web à partir du fichier "index.html", cette  page,  qui  contient  un  **formulaire**  (balise  ```<form  action="http://localhost:5000/resultat" method="post">```**)** est envoyée vers le client.  

On  remarque  2  **attributs**  dans  cette  balise  form  :  ```action="http://localhost:5000/resultat"```  et ```method="post"```.  Ces  2  attributs indiquent  que le  client  devra  effectuer  une  **requête  de  type  POST**  dès  que l'utilisateur  appuiera  sur  le  bouton  "Envoyer".  Cette  requête  POST  **sera  envoyée  à  l'URL** "```http://localhost:5000/resultat```" (voir l'attribut "action"). Les données saisies dans le formulaire seront envoyées au serveur par l'intermédiaire de cette requête. 

**N.B La méthode à employer pour effectuer la requête HTTP n'est pas précisée dans le "**```@app.route('/')```**". Si rien n'est précisé, par défaut, c'est la méthode GET qui est utilisée.** 

Côté serveur c’est la fonction "resultat" qui est exécutée pour traiter la requete POST 
```python
def resultat():
  result = request.form
  n = result['nom']
  p = result['prenom']
  return render_template('resultat.html', nom=n, prenom=p)
```
"request.form" est un dictionnaire Python qui a pour clés les attributs "name" des balises "input" du formulaire (dans notre cas les clés sont donc "nom" et "prenom") et comme valeurs ce qui a été saisi par l'utilisateur. Si l'utilisateur saisit "Martin" et "Sophie", le dictionnaire "request.form" sera :
```{'nom':'Martin', 'prenom':'Sophie'}```



En réponse à la requête POST, le serveur renvoie une page HTML créée à partir du template "resultat.html" et des paramètres "nom" et "prenom". Si l'utilisateur a saisi "Martin" et "Sophie", le navigateur affichera "Bonjour Sophie Martin, j'espère que vous allez bien." 

Pour gérer le formulaire, il est possible d'utiliser une méthode HTTP "GET" à la place de la méthode "POST" : 

**Activité n°35. :** Modifier les fichiers comme suit : 

Pour le fichier index.html 
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Le formulaire</title>
    </head>
    <body>
        <form action="http://localhost:5000/resultat" method="get">
                <label>Nom</label> : <input type="text" name="nom" />
                <label>Prénom</label> : <input type="text" name="prenom" />
                <input type="submit" value="Envoyer" />
        </form>
    </body>
</html>
```


Pour resultat.html
```html
<!doctype html>
<html lang="fr">
    <head>
        <meta charset="utf-8">
        <title>Résultat</title>
    </head>
    <body>
        <p>Bonjour {{prenom}} {{nom}}, j'espère que vous allez bien.</p>
    </body>
</html>
```
 

Pour views.py
```python
from flask import Flask, render_template, request 

app = Flask(__name__) 

@app.route('/') 
def index(): 
    return render_template('index.html') 

@app.route('/resultat',methods = ['GET']) 
def resultat(): 
    result=request.args 
    n = result['nom'] 
    p = result['prenom'] 
    return render_template("resultat.html", nom=n, prenom=p) 

app.run(debug=True) 
```
Dans "index.html", la méthode POST a été remplacée par la méthode GET. Dans le fichier "views.py" POST a été aussi remplacé par GET, et on utilise "request.args" à la place de "request.form". 

**Activité n°36. :** Relancer l'exécution de "views.py" et saisissez "localhost:5000" dans la barre d'adresse d'un navigateur web. Une fois la page web affichée dans votre navigateur, Saisir "Sophie" pour le prénom et "Martin" pour  le  nom  puis  validez  en  cliquant  sur  le  bouton  "Envoyer".  Observer  attentivement  la  barre  d'adresse  du navigateur.  

Cette  fois-ci,  les  informations  du  formulaire  sont  transmises  au  serveur  par  l'intermédiaire  de  l'URL  : ```localhost:5000/resultat?nom=Martin&prenom=Sophie``` 

Dans le cas de l'utilisation d'une méthode "POST" les données issues d'un formulaire sont envoyées au serveur sans être directement visibles, alors que dans le cas de l'utilisation d'une méthode "GET", les données sont visibles (et accessibles) puisqu'elles sont envoyées par l'intermédiaire de l'URL. 

Les données envoyées par l'intermédiaire d'une méthode "GET" peuvent être modifiées directement dans l'URL :

**Activité n°37. :** Ouvrir le  navigateur Web et taper dans la barre d'adresse "localhost:5000". Une fois la page web affichée dans le navigateur, saisir "Sophie" pour le prénom et "Martin" pour le nom puis valider en cliquant sur le bouton "Envoyer".  

Une fois que le message "Bonjour Sophie Martin, j'espère que vous allez bien." apparait, modifier l'URL : passer de "```localhost:5000/resultat?nom=Martin&prenom=Sophie```"  à "```localhost:5000/resultat?nom=Martin&prenom=Jean-Pierre```",  valider  la  modification  en  appuyant  sur  la touche "Entrée". 

Normalement la page a bien été modifiée : "Bonjour Jean-Pierre Martin, j'espère que vous allez bien." 

Même si dans notre cas cette opération de modification d'URL est inoffensive, il faut bien se douter que dans des situations plus complexes, une telle modification pourrait entrainer des conséquences plus problématiques (piratage).  

Il faut donc éviter d'utiliser la méthode "GET" pour transmettre les données issues d'un formulaire vers un serveur. 

Il est important de bien comprendre que la méthode "POST" n'offre pas non plus une sécurité absolue puisque toute personne ayant un bagage technique minimum sera capable de lire les données transmises à l'aide de la méthode "POST" en analysant la requête HTTP, même si ces données ne sont pas directement visibles dans l'URL. Seule l'utilisation du **protocole sécurisé HTTPS** garantit un transfert sécurisé des données entre le client et le serveur (les données sont chiffrées et donc illisibles pour une personne ne possédant pas la clé de déchiffrement). 

Pour  approfondir  ce  cours  sur  la  création  d’applications  web  avec  Flask : [https://openclassrooms.com/fr/courses/1654786-creez-vos-applications-web-avec-flask/1655132-requetes-et- reponses ](https://openclassrooms.com/fr/courses/1654786-creez-vos-applications-web-avec-flask/1655132-requetes-et-reponses)![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.008.png)

## **6. Exercices** 

**Exercice n°1 :** Réaliser le visuel du formulaire suivant :

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.129.jpeg)

Pour cela : 

- vous utilisez les balises input et select,  
- vous préciserez le type lors de l'utilisation d'une balise input, 
- vous préciserez le name dans chacun des cas (attribut name utilisé plus tard pour retrouver la valeur d'un élément d'un formulaire).
- vous proposerez deux types de carte bancaire possibles : 'Visa' et 'Bleue' (carte par défaut). 
- Attention ! Sans Javascript, votre bouton 'Valider le paiement' sera sans effet.

**Exercice n°2 :** Expliquer ce que fait ce code. 
```html
<form>
<p> Choix d'une nationalité :</p>
    <select id="choix" name="lang" onchange="selection()">
        <option value="ras">Choisir sa nationalité</option>
        <option value="fr">Français</option>
        <option value="zh">Chinois</option>
        <option value="it">Italien</option>
    </select>
<p> Vous avez choisi comme nationalité :<span id="nat">  </span> </p>
</form>
```


**Pour aller plus loin (avec du JS) : Exercice n°3 :** 

Pour l'exercice on a besoin de trois instructions (déjà vues) : 

- **getElementById('id')** est une méthode qui récupère l'objet de la page identifié par 'id'. 

document.getElementById('id') récupère l'objet de la page en cours identifié par 'id'.

- **selectedIndex** est une méthode qui renvoie la valeur l'option choisie par une liste déroulante ; plus généralement, cette méthode indique le rang à partir de 0 de l'élément de la liste qui a été sélectionnée par l'utilisateur.

selecteur.selectedIndex renvoie l'indice du choix fait par l'utilisateur de la liste déroulante nommée 'selecteur'. 

- **innerHTML** est une méthode qui permet de récupérer tout le contenu HTML d'un élément d'une page html.

document.getElementById('ici').innerHTML intégre du contenu html à l'emplacement de la page identifié par l'id nommé 'ici'. 

voilà le script d'une fonction écrite en javascript :
```JS
function selection() {
        const selecteur = document.getElementById('choix');
        const monChoix = selecteur[selecteur.selectedIndex];
        console.log(monChoix.value +' '+ monChoix.text);
        document.getElementById('nat').innerHTML = monChoix.text;
    }
```


1. Intégrer au code de l'exercice 2 ci-dessus ce script, soit directement, soit avec un lien vers un fichier javascript. 
1. Relancer le code ainsi augmenté de l'exercice 2. Que remarquez-vous ? 
1. Commenter chaque ligne de cette fonction écrite en JavaScript. 

Utiliser la console de votre navigateur afin de voir l'effet d'une des lignes. 

**Pour aller plus loin (avec du JS) : Exercice n°4 :**  

Ecrire un formulaire qui demande votre âge et qui indique dans la même page si vous êtes majeur ou mineur. 

![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.136.png) ![](Aspose.Words.bec3aaa5-551c-40be-9a61-cdd26a2bc5a1.137.jpeg)

**Pour aller plus loin (avec du JS) : Exercice n°5 :**  

On donne le code suivant : 
```html
<form>
    <fieldset>
        <legend>Veuillez sélectionner vos spécialités l'année prochaine :
        </legend>
        <div>
            <input type="checkbox" id="nsi" name="interest" value="nsi">
            <label for="nsi">NSI</label>
        </div>
        <div>
            <input type="checkbox" id="ma" name="interest" value="ma">
            <label for="ma">Maths</label>
        </div>
        <div>
            <input type="checkbox" id="svt" name="interest" value="svt">
            <label for="svt">SVT</label>
        </div>
    </fieldset>
</form>
```


En vous inspirant de l'exercice précédent, faire un formulaire qui demande quelles spécialités vous allez conserver l'année prochaine 

Vous ferez une question pour la première 

La réponse sera affichée dans la page HTML. 

Si la réponse contient NSI, la page HTML doit afficher : "Bravo, bon choix !". 
