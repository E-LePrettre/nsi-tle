---
author: ELP
title: 08 Les processus
---


**Table des matières**

[1.	Rappels	](#_toc174920494)

[2.	Vocabulaire	](#_toc174920495)

[3.	Introduction	](#_toc174920496)

[4.	Le chiffrement	](#_toc174920497)

[5.	Le protocole HTTPS	](#_toc174920506)

[6.	Exercices	](#_toc174920509)

[7.	Projet	](#_toc174920510)

**Compétences évaluables :**

- Décrire les principes de chiffrement symétrique (clef partagée) et asymétrique (avec clef privée/clef publique)
- Décrire l’échange d’une clef symétrique en utilisant un protocole asymétrique pour sécuriser une communication HTTPS

## <a name="_toc174920494"></a>**1. Rappels** 

![TCP Handshake](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.001.png){: .center}

Avec les acquis du programme de première, nous pouvons comprendre exactement ce qu'il se passe lorsque l'on navigue vers un site web, par exemple « http://gs-cassaigne.fr/ ».

- L'**URL du site** est **décodée** par le navigateur qui isole :
- le protocole (HTTP), 
- le **nom de domaine** (gs-cassaigne.fr) 
- le chemin vers la ressource (ici **/**, la « racine » du site).
- Le navigateur effectue **une résolution de nom** pour déterminer **l'adresse IP** correspondant au nom de domaine (213.186.33.16). (on peut la trouver en faisant un tracert dans la console windows)
- Le navigateur peut alors établir une **connexion TCP** vers l'adresse IP du serveur web, sur le port 80 via un hanshaking en trois temps

- Une fois la connexion établie, client et serveur échangent des données en utilisant le **protocole HTTP** tout en découpant les données en **paquets TCP**, eux-mêmes **encapsulés dans des paquets IP**.

![Encapsulation](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.002.png){: .center}

On se souvient aussi que les communications sur Internet utilisent un ensemble de protocoles, organisés en couches:

- **Couche accès réseau** avec des protocoles tels que Ethernet ou 802.11 n.
- **Couche Internet**, avec le protocole IP permettant de définir des routes, c'est-à-dire l'ensemble des machines du réseau traversées pour atteindre la machine de destination.
- **Couche de transport** avec les protocoles UDP ou TCP, qui s'occupent en particulier de garantir l'intégrité des données transmises (garanties minimales pour UDP ou très fortes pour TCP).
- **Couche d'application** dans laquelle se trouvent les protocoles de haut niveau : HTTP, IMAP, etc.

Ce processus a été **très peu modifié depuis la conception** de TCP/IP à la fin des années 1970. 

Chaque protocole (SMTP, FTP, puis HTTP au milieu des années 1990), s'est inséré dans ce cadre au niveau de la couche d'application.

Cependant, avec la démocratisation d'Internet, du Web et la diversification des usages, **des problèmes sont apparus**.

Les paquets IP sont envoyés par la source au prochain routeur de son sous-réseau.

Ce routeur retransmet ensuite le paquet au routeur suivant et ainsi de suite jusqu'à l'arrivée à destination. 

Chaque routeur peut donc inspecter les paquets pour en **connaître le contenu.**

![Routage](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.003.png){: .center}

Cette situation n'est **clairement pas idéale.** En effet, si l'on utilise un site web pour effectuer des transactions bancaires, renseigner des informations personnelles (impôts, arrêt maladie, etc.), ou simplement exprimer son opinion, on souhaite que le contenu des messages envoyés ne soit connu que de deux entités: la source et la destination.

Ce simple constat nous permet de mettre en avant trois aspects liés à la sécurisation des communications:

- Comment chiffrer le contenu des communications afin qu'elles ne soient lisibles que par la source et la destination (garantie de **confidentialité**) ?
- Comment garantir que le serveur auquel on se connecte est bien celui auquel on pense se connecter (garantie d'**authenticité**) ?
- Comment s'assurer que le message transmis n'a pas été modifié par un tiers (garantie d'**intégrité**) ?

Le tout devant bien entendu se faire dans le cadre d'une communication en utilisant l'infrastructure d'Internet, à savoir les communications TCP/IP ?


## <a name="_toc174920495"></a>**2. Vocabulaire**

- **Coder**, c'est représenter l'information par un ensemble de signes prédéfinis. **Décoder**, c'est interpréter un ensemble de signes pour en extraire l'information qu'ils représentent.

  Coder et décoder s'emploient lorsqu'il n'y a pas de secret. Par exemple on peut coder/décoder des entiers relatifs par une suite de bits par un «codage en complément à deux».

- La **cryptographie** est une discipline veillant à protéger des messages (pour en assurer la confidentialité, l'authenticité et l'intégrité), par l'intermédiaire de **clés de chiffrements**.

- La cryptographie est utilisée depuis au moins l'antiquité.

- La **cryptanalyse** est la technique qui consiste à déduire un texte en clair d’un texte chiffré **sans posséder la clé de chiffrement**. Le processus par lequel on tente de comprendre un message en particulier est appelé **une attaque**.
- **Chiffrer** un message, c'est rendre une suite de symboles incompréhensible au moyen d'une **clé de chiffrement**.
- **Déchiffrer** ou **décrypter**, c'est retrouver la suite de symboles originale à partir du message chiffré. On utilise **déchiffrer** quand on utilise la clé de chiffrement pour récupérer le texte original, et **décrypter** lorsqu'on arrive à retrouver le message original sans connaitre la clé de chiffrement.

## <a name="_toc174920496"></a>**3. Introduction** 
**Vidéo** : Comprendre le chiffrement SSL \_ TLS avec des emojis \_et le HTTPS

## <a name="_toc174920497"></a>**4. Le chiffrement** 
**Exemple** : Alice veut transmettre un message secret à Bob via un réseau non sécurisé, comme Internet. C’est-à-dire que le message peut être intercepté par une autre personne. Un réseau sécurisé serait par exemple un câble unique allant directement de l’ordinateur d’Alice  à celui de Bob sans intermédiaire et sans autre connexion.  

Le message **doit être chiffré** (crypté) à l’aide d’un algorithme de chiffrement et d’une clé.

### <a name="_toc174920498"></a>**4.1. Le chiffrement symétrique**
#### <a name="_toc174920499"></a>**4.1.1. Le principe**
Dans un chiffrement symétrique, c'est **la même clé** qui va servir au chiffrement et au déchiffrement.

![image](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.004.png){: .center}

**Qu'appelle-t-on une clé ?** 

La clé est un renseignement permettant de chiffrer ou déchiffrer un message. Cela peut être :

- un nombre (dans un simple décalage des lettres de l'alphabet, comme [le chiffre de César](https://fr.wikipedia.org/wiki/Chiffrement_par_d%C3%A9calage))
- une phrase (dans la méthode du [masque jetable](https://fr.wikipedia.org/wiki/Masque_jetable))
- une image (imaginez un chiffrement où on effectue un XOR par les pixels d'une image)

Un chiffrement **est dit symétrique** lorsque la connaissance de la clé **ayant servi au chiffrement permet de déchiffrer** le message.


**Quel est l'avantage d'un chiffrement symétrique ?** 

Les chiffrements symétriques sont souvent **rapides**, consommant **peu de ressources** et donc adaptés au chiffrement de flux important d'informations.

Comme nous le verrons, la sécurisation des données transitant par le **protocole HTTPS** est basée sur un chiffrement symétrique.

**Quel est l'inconvénient d'un chiffrement symétrique ?**

**L’inconvénient majeur** est de **donner la clef au destinataire** avant l’envoyer le message. En effet, si j’envoie la clef à mon destinataire, elle ne doit pas être chiffrée, toute personne qui intercepte le message peut récupérer la clef partagée et donc intercepter mes futurs messages pour les déchiffrer.

**Un chiffrement symétrique est-il un chiffrement de mauvaise qualité ?** 

NON ! S'il est associé naturellement à des chiffrements simples et faibles (comme le décalage de César), un chiffrement symétrique **peut être très robuste**... voire inviolable.

C'est le cas du masque jetable. Si le masque avec lequel on effectue le XOR sur le message est aussi long que le message, alors il est **impossible** de retrouver le message initial. Pourquoi ?

Imaginons qu'Alice veuille transmettre le message clair "LUNDI". Elle le chiffre avec un masque jetable (que connait aussi Bob), et Bob reçoit donc "KHZOK". Si Marc a intercepté le message "KHZOK", *même s'il sait que la méthode de chiffrement utilisée est celle du masque jetable* (*principe de Kerckhoffs*), il n'a pas d'autre choix que de tester tous les masques de 5 lettres possibles.

Ce qui lui donne 26<sup>5</sup> possibilités (plus de 11 millions) pour le masque, et par conséquent (propriété de bijectivité du XOR) 26<sup>5</sup> possibilités pour le message «déchiffré»...

**Quels sont les chiffrements symétriques modernes ?** 

L'algorithme de chiffrement symétrique le plus utilisé actuellement est le chiffrement [AES](https://fr.wikipedia.org/wiki/Advanced_Encryption_Standard), pour Advanced Encryption Standard.

- chiffrement par bloc de 128 bits, répartis dans une matrice de 16 octets (matrice carrée de taille 4).
- ces 128 bits sont transformés par des rotations, multiplications, transpositions, [...] de la matrice initiale, en faisant intervenir dans ces transformations une clé de 128, 192 ou 256 bits.
- pour l'AES-256 (avec une clé de 256 bits), l'attaque par force brute nécessiterait 2<sup>256</sup> opérations, soit un nombre à 78 chiffres...
- il n'existe pas d'attaque connue efficace à ce jour.

#### <a name="_toc174920500"></a>**4.1.2. Réalisation**

<b>1<sup>ère</sup> étape : le message :</b> Soit le message Hello World! en binaire :
```
010010000110010101101100011011000110111100100000010101110110111101110010011011000110010000100001
```

On a simplement utilisé le code ASCII de chaque caractère (par exemple, on peut vérifier que le H correspond bien à l'octet 01001000). Pour effectuer la "conversion" texte vers code binaire ASCII ou vis versa, vous pouvez utiliser le site <https://www.rapidtables.com/convert/number/ascii-to-binary.html>

<b>2<sup>ème</sup> étape la clef</b> : On choisit un mot (ou une phrase) qui nous servira de clé de chiffrement, prenons pour exemple le mot "toto". "toto" nous donne en binaire :
```
01110100011011110111010001101111
```



<b>3<sup>ème</sup> étape le chiffrement</b> : Pour chiffrer le message nous allons effectuer un XOR bit à bit. Pour rappel, vous trouverez la table de vérité du XOR ci-dessous :

Table de vérité "XOR" :

![Image](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.006.png)

Comme la clé est plus courte que le message, il faut "reproduire" la clé vers la droite autant de fois que nécessaire (si la taille du message n'est pas un multiple de la taille de la clé, on peut reproduire seulement quelques bits de la clé pour la fin du message):

```
 
  010010000110010101101100011011000110111100100000010101110110111101110010011011000110010000100001
⊕
 
  011101000110111101110100011011110111010001101111011101000110111101110100011011110111010001101111
  ________________________________________________________________________________________________
  001111000000101000011000000000110001101101001111001000110000000000000110000000110001000001001110
```   

Si on cherche à afficher le message chiffré avec un éditeur de texte) : 
![Image](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.007.png)

Maintenant ce message est prêt pour être envoyé à son destinataire B. Si P intercepte le message et cherche à le lire avec un éditeur de texte, il obtiendra la suite de caractère ![Image](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.007.png)

<b>4<sup>ème</sup> étape le déchiffrement</b> : Bob a maintenant reçu le message chiffré, il possède la clé (toto), il va donc pouvoir déchiffrer le message <b>en appliquant un XOR</b> entre le message chiffré et la clé (on applique exactement la même méthode que ci-dessus).

```  
 
  001111000000101000011000000000110001101101001111001000110000000000000110000000110001000001001110
⊕   
 
  011101000110111101110100011011110111010001101111011101000110111101110100011011110111010001101111
  ________________________________________________________________________________________________
  010010000110010101101100011011000110111100100000010101110110111101110010011011000110010000100001

```  


On retrouve bien le code binaire d'origine. Pour ne pas s’embêter à vérifier bit par bit, on peut utiliser ce [site](https://www.rapidtables.com/convert/number/binary-to-ascii.html) (<https://www.rapidtables.com/convert/number/binary-to-ascii.html>) qui vous permettra de repasser du code binaire ASCII au texte.

On retrouve bien le message d'origine : Hello World!, B a pu lire le message envoyé par A alors que pour P, malgré le fait qu'il a pu intercepter le message, il n'a pas pu prendre connaissance de son contenu sans la clé.

**Activité n° 1  : Application du chiffrement symétrique :** 
- Créer une fonction chiffre(message, masque) qui chiffre message en le XOR avec masque.
- Cette fonction doit pouvoir **aussi** servir à déchiffrer le message chiffré.

clé de chiffrement :  Vive la NSI !!  

on chiffrera la phrase : Je suis en spécialité NSI et j’adore 


### <a name="_toc174920501"></a>**4.2. Le chiffrement asymétrique**
Le chiffrement asymétrique permet au poste destinataire de messages de générer une unique paire de clefs :

- Une **clef privée** gardée secrète sur le poste destinataire des messages et stockée de manière sécurisée 
- Une **clef publique** diffusée par le destinataire à tous les postes distants 


#### <a name="_toc174920502"></a>**4.2.1. Le principe** 
**Exemple :** 

Alice crée deux clés, une clé de **chiffrement** 🔓 qu’elle rend **publique** et une clé de **déchiffrement** 🔑 qui reste **privée** (uniquement en possession de Alice). 

Bob récupère la clé publique 🔓 et peut chiffrer les messages. Seul Alice, qui possède la clé privée 🔑, peut les déchiffrer.

![Image](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.009.png){: .center}

![Image](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.010.png){: .center}

![Image](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.011.png){: .center}

**Avantage** : Même si quelqu’un intercepte le message, **il n’a pas la clef privée** donc ne peut déchiffrer le message

**Inconvénients** : on doit générer **autant de clefs que d’expéditeurs potentiels**. De même, l’expéditeur doit avoir **autant de clef publique que de destinataire** à qui il envoie des messages. De plus, il est relativement lent même s’il existe des algorithmes (par exemple avec [l'algorithme de Rivest, Shamir et Adleman](https://fr.wikipedia.org/wiki/Chiffrement_RSA)) qui sont relativement rapides

**Cependant, un problème reste à régler, il s'agit du problème de l'authentification : la sureté des communications dépend essentiellement sur le fait qu'Alice et Bob soient certains de communiquer avec la bonne personne.**

#### <a name="_toc174920503"></a>**4.2.2. Echange de clé symétrique avec clés asymétriques : méthode de Diffie-Hellman**
En 1976, [Martin Hellman](https://fr.wikipedia.org/wiki/Martin_Hellman) a coécrit avec [Whit Diffie](https://fr.wikipedia.org/wiki/Whitfield_Diffie) un [article](https://ee.stanford.edu/~hellman/publications/24.pdf) où est décrit le protocole suivant, utilisant **les clefs asymétriques pour échanger des clefs symétriques**. On illustre le protocole par un message 📃 placé dans une boîte 📦 fermée par des cadenas.

1. ![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.012.png)Alice met le message 📃 dans la boîte 📦 , puis la ferme avec sa clef publique 🔓 ;
1. ![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.013.png)Alice envoie la boîte fermée 📦🔒 à Bob  ;
1. ![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.014.png)![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.015.png)![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.016.png)![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.017.png)Bob ne peut pas ouvrir la boîte 📦🔒 car il n'a pas la clef privée 🔑 d'Alice ; alors il rajoute sa clef publique 📦🔒🔒
1. ![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.018.png)![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.019.png)Bob envoie la boîte fermée deux fois 📦🔒🔒 à Alice ;
1. ![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.020.png)![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.021.png)Alice utilise sa clef privée 🔑 pour ouvrir partiellement la boîte 📦🔓 ;
1. ![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.022.png)Alice renvoie la boîte 📦🔒 à Bob.
1. ![](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.023.png)Bob utilise sa clef privée 🔑 pour ouvrir la boîte 📦.
1. Bob peut alors récupérer le message 📃 .

Pour HTTPS, le message 📃 partagé entre Alice et Bob est **une clef symétrique** 🔐. La sécurisation de la communication est assurée parce qu'il est impossible à Marc 👽 de [se faire passer](https://fr.wikipedia.org/wiki/Attaque_de_l%27homme_du_milieu) pour Alice ou pour Bob sans disposer de **la clé privée** 🔑 de l'un des deux.

Le protocole de Diffie-Hellman permet donc d'échanger une clé de chiffrement symétrique 🔐 à l'aide du chiffrement asymétrique. <https://www.venafi.com/fr/blog/en-quoi-les-echange-de-cles-diffie-hellman-et-rsa-different-ils> 
