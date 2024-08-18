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


