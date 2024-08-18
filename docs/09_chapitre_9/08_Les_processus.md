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

