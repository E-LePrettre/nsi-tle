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

![image](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.004.png)

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
