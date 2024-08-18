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

1. # <a name="_toc174920494"></a>**Rappels** 
![TCP Handshake](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.001.png)Avec les acquis du programme de première, nous pouvons comprendre exactement ce qu'il se passe lorsque l'on navigue vers un site web, par exemple « http://gs-cassaigne.fr/ ».

- - L'**URL du site** est **décodée** par le navigateur qui isole :
- - le protocole (HTTP), 
- - le **nom de domaine** (gs-cassaigne.fr) 
- - le chemin vers la ressource (ici **/**, la « racine » du site).
- - Le navigateur effectue **une résolution de nom** pour déterminer **l'adresse IP** correspondant au nom de domaine (213.186.33.16). (on peut la trouver en faisant un tracert dans la console windows)
- - Le navigateur peut alors établir une **connexion TCP** vers l'adresse IP du serveur web, sur le port 80 via un hanshaking en trois temps

- - Une fois la connexion établie, client et serveur échangent des données en utilisant le **protocole HTTP** tout en découpant les données en **paquets TCP**, eux-mêmes **encapsulés dans des paquets IP**.

![Encapsulation](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.002.png)

On se souvient aussi que les communications sur Internet utilisent un ensemble de protocoles, organisés en couches:

- - **Couche accès réseau** avec des protocoles tels que Ethernet ou 802.11 n.
- - **Couche Internet**, avec le protocole IP permettant de définir des routes, c'est-à-dire l'ensemble des machines du réseau traversées pour atteindre la machine de destination.
- - **Couche de transport** avec les protocoles UDP ou TCP, qui s'occupent en particulier de garantir l'intégrité des données transmises (garanties minimales pour UDP ou très fortes pour TCP).
- - **Couche d'application** dans laquelle se trouvent les protocoles de haut niveau : HTTP, IMAP, etc.

Ce processus a été **très peu modifié depuis la conception** de TCP/IP à la fin des années 1970. 

Chaque protocole (SMTP, FTP, puis HTTP au milieu des années 1990), s'est inséré dans ce cadre au niveau de la couche d'application.

Cependant, avec la démocratisation d'Internet, du Web et la diversification des usages, **des problèmes sont apparus**.

Les paquets IP sont envoyés par la source au prochain routeur de son sous-réseau.

Ce routeur retransmet ensuite le paquet au routeur suivant et ainsi de suite jusqu'à l'arrivée à destination. 

Chaque routeur peut donc inspecter les paquets pour en **connaître le contenu.**

![Routage](Aspose.Words.5bd2e875-ac10-4ba8-af1a-e3d7ad787223.003.png)


Cette situation n'est **clairement pas idéale.** En effet, si l'on utilise un site web pour effectuer des transactions bancaires, renseigner des informations personnelles (impôts, arrêt maladie, etc.), ou simplement exprimer son opinion, on souhaite que le contenu des messages envoyés ne soit connu que de deux entités: la source et la destination.

Ce simple constat nous permet de mettre en avant trois aspects liés à la sécurisation des communications:

- Comment chiffrer le contenu des communications afin qu'elles ne soient lisibles que par la source et la destination (garantie de **confidentialité**) ?
- Comment garantir que le serveur auquel on se connecte est bien celui auquel on pense se connecter (garantie d'**authenticité**) ?
- Comment s'assurer que le message transmis n'a pas été modifié par un tiers (garantie d'**intégrité**) ?

Le tout devant bien entendu se faire dans le cadre d'une communication en utilisant l'infrastructure d'Internet, à savoir les communications TCP/IP ?
