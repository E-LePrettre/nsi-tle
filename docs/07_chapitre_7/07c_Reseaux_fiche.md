---
author: Elisabeth Le Prettre (LePrettre)
title: 07 📜 Fiche Méthode - Les protocoles de routage
---

# Les protocoles de routage

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur le routage : modèle TCP/IP, adressage
    IP, transport fiable, paquet IP, table de routage, **RIP**, **OSPF** et
    **Dijkstra**.

!!! warning "Conventions"
    Certaines valeurs dépendent de l'énoncé (métrique RIP d'un réseau directement
    connecté, formule de coût OSPF). **Suis toujours la convention donnée.**

---

## 1. Modèle TCP/IP

| Couche | Rôle | Protocoles | Données | Informations ajoutées |
|---|---|---|---|---|
| **Application** | Dialogue entre logiciels | HTTP, HTTPS, FTP, SMTP (`GET`, `POST`) | Message / requête | Données applicatives (ports **80** HTTP, **443** HTTPS) |
| **Transport** | Acheminement de bout en bout | **TCP**, **UDP** | **Segment** | Ports, numéros de **séquence**, ACK |
| **Internet / Réseau** | Routage entre réseaux | **IP** | **Paquet** | IP source, IP destination, TTL |
| **Accès réseau** | Transmission sur le lien physique | Ethernet, Wi-Fi | **Trame** | Adresses **MAC** |

!!! note "Définitions"
    - **Protocole** : ensemble de **règles** régissant les échanges.
    - **Couche** : niveau du modèle, ayant un rôle précis.
    - **Encapsulation** : chaque couche **enveloppe** les données de la couche
      supérieure en ajoutant ses propres informations (en-tête).
    - **Interface** : point de contact entre deux couches (ou entre une machine et
      le réseau).

---

## 2. Adressage IP

- une **IP = partie réseau + partie hôte** ;
- le **masque** (ou notation **CIDR** `/n`) sépare ces deux parties ;
- **adresse réseau = IP AND masque** ;
- nombre **total** d'adresses : `2^h` (`h` = nombre de bits hôte) ;
- nombre d'**hôtes utilisables** : `2^h − 2` ;
- **réseau** = première adresse (bits hôte à 0) ; **broadcast** = dernière (bits
  hôte à 1) ; **première / dernière utilisables** = réseau + 1 / broadcast − 1 ;
- communication **locale** (même sous-réseau) ou **via la passerelle** (sous-réseau
  différent) ;
- **IPv6** : utilise un **préfixe** (ex. `/64`).

| Service | Rôle |
|---|---|
| **MAC** | Adresse physique de la carte réseau. |
| **ARP** | Trouve l'adresse **MAC** correspondant à une **IP**. |
| **DHCP** | Attribue automatiquement une **IP** à une machine. |
| **DNS** | Traduit un **nom de domaine** en **adresse IP**. |

!!! example "Méthode : déterminer le réseau d'une IPv4"
    *Exemple : `192.168.1.130 /25`*
    1. **Masque** : `/25` → `255.255.255.128`, soit `h = 32 − 25 = 7` bits hôte.
    2. **AND** sur le dernier octet : `130 = 10000010` AND `10000000` → `10000000 = 128`.
    3. **Réseau** = `192.168.1.128` ; **broadcast** = `192.168.1.255`.
    4. **Plage utilisable** : `192.168.1.129` → `192.168.1.254` (`2^7 − 2 = 126` hôtes).

!!! tip "Deux machines sont-elles dans le même sous-réseau ?"
    Calculer l'**adresse réseau** de chacune (IP AND masque) : si elles sont
    **identiques**, les machines communiquent **localement** ; sinon, elles passent
    par la **passerelle**.

---

## 3. Transport fiable

| | **TCP** | **UDP** |
|---|---|---|
| Connexion | Oui (fiable) | Non |
| Contrôle | Séquence + ACK + réémission | Aucun |
| Usage | Données fiables (web, mail) | Rapidité (streaming, jeux) |

- les données sont découpées en **segments** numérotés (**numéros de séquence**) ;
- le récepteur confirme par un **ACK** ;
- en cas de **perte**, le segment est **réémis** (après un **timeout**).

!!! note "Protocole du bit alterné"
    L'émetteur marque chaque envoi d'un **drapeau alterné `0` / `1`**. Il attend
    l'**ACK** correspondant avant d'envoyer le suivant. Si l'ACK n'arrive pas avant
    le **timeout**, il **réémet**. Le récepteur repère un **doublon** grâce au
    drapeau (même numéro reçu deux fois).

---

## 4. Paquet IP

| Champ | Rôle |
|---|---|
| **IP source** | Adresse de l'expéditeur. |
| **IP destination** | Adresse du destinataire. |
| **TTL / Hop Limit** | Durée de vie : nombre maximal de sauts. |

- le **routeur** **aiguille** les paquets vers la bonne destination ;
- à chaque routeur traversé, le **TTL diminue de 1** ; si le TTL atteint **0**, le
  paquet est **détruit** → cela évite les **boucles** infinies.

---

## 5. Table de routage

| Destination | Masque | Passerelle | Interface | Métrique |
|---|---|---|---|---|
| `192.168.1.0` | `/24` | On-link | `eth0` | 0 |
| `10.0.0.0` | `/8` | `192.168.1.254` | `eth0` | 10 |
| `0.0.0.0` | `/0` | `192.168.1.254` | `eth0` | 1 |

!!! note "Notions clés"
    - **Réseau directement connecté** : joignable sans passerelle (**On-link**).
    - **Prochain saut** : adresse de la **passerelle** vers laquelle envoyer le paquet.
    - **Route statique** : saisie **manuellement** par l'administrateur.
    - **Route dynamique** : **apprise** automatiquement (RIP, OSPF).
    - **Route par défaut** `0.0.0.0/0` : utilisée quand **aucune** autre route ne
      correspond.
    - **Choix de la route** : on retient le **préfixe le plus précis** (le masque le
      plus long qui correspond).

!!! tip "Suivre la route d'un paquet"
    1. Prendre l'**IP de destination**.
    2. Pour chaque ligne, calculer `IP AND masque` et comparer à la destination de la route.
    3. Garder les routes qui **correspondent**, choisir celle au **préfixe le plus long**.
    4. Envoyer vers la **passerelle** (ou directement si **On-link**) par l'**interface** indiquée.

---

## 6. RIP

!!! abstract "Fiche synthèse RIP"
    - **Type** : protocole à **vecteur de distance**.
    - **Échanges** : avec les **voisins**, **toutes les 30 secondes**.
    - **Métrique** : **nombre de sauts**.
    - **Calcul** : distance reçue d'un voisin **+ 1**.
    - **Mise à jour** : on **ajoute** une route inconnue, on **remplace** par une
      route plus courte, on **conserve** sinon.
    - **Convergence** : état stable atteint après propagation des informations.
    - **Vision** : **locale uniquement** (ne connaît que ses voisins).
    - **Limite** : maximum **15** sauts ; **16 = inaccessible**.
    - **Panne** : l'**absence prolongée** d'un voisin invalide ses routes.

| Avantages | Limites |
|---|---|
| Simple à configurer | Réseaux **petits** uniquement (max 15 sauts) |
| Léger | **Convergence lente** ; ne tient pas compte du débit |

!!! warning "Convention de l'énoncé"
    La **métrique d'un réseau directement connecté** vaut **0 ou 1** selon les
    énoncés : utilise la **convention donnée** dans le sujet.

---

## 7. OSPF

!!! abstract "Fiche synthèse OSPF"
    - **Type** : protocole à **état de liens** (*link state*).
    - **LSA** : messages décrivant l'**état des liens**, échangés dans le réseau.
    - **Vision** : chaque routeur reconstitue une **carte complète** du réseau.
    - **Calcul** : algorithme de **Dijkstra**.
    - **Métrique** : **somme des coûts** des liens du chemin.
    - **Coût** : dépend de la **bande passante**.

!!! note "Formule du coût"
    ```
    coût = 10^8 / (débit en bit/s)
    ```
    - le **coût minimal** vaut **1** dans les exemples du cours ;
    - **suivre la formule fournie** par l'énoncé ;
    - distinguer **bande passante** (capacité du lien) et **débit** (quantité par seconde) ;
    - **additionner** les coûts des liens pour comparer deux chemins.

    *Exemples :* 100 Mbit/s = `10^8` bit/s → coût `1` ; 10 Mbit/s = `10^7` → coût `10`.

---

## 8. Dijkstra

!!! tip "Méthode pas à pas (poids strictement positifs)"
    1. distance du **sommet de départ = 0**, tous les autres à **l'infini** ;
    2. choisir le sommet **non fixé** de **distance provisoire minimale** ;
    3. **fixer** ce sommet (sa distance est définitive) ;
    4. **actualiser** ses voisins (si un chemin plus court est trouvé) ;
    5. **noter les prédécesseurs** ;
    6. **poursuivre** jusqu'à fixer tous les sommets ;
    7. **reconstituer** le chemin en remontant les prédécesseurs.

!!! example "Tableau-type (départ A)"
    Graphe : `A-B=1`, `A-C=4`, `B-C=2`, `B-D=6`, `C-D=3`.

    | Sommet fixé | A | B | C | D |
    |---|---|---|---|---|
    | — (init) | 0 | ∞ | ∞ | ∞ |
    | **A** (0) | 0 | 1 (A) | 4 (A) | ∞ |
    | **B** (1) | 0 | 1 (A) | 3 (B) | 7 (B) |
    | **C** (3) | 0 | 1 (A) | 3 (B) | 6 (C) |
    | **D** (6) | 0 | 1 (A) | 3 (B) | 6 (C) |

    Chemin de A à D : on remonte `D ← C ← B ← A`, soit **A → B → C → D**, coût **6**.

---

## 9. Comparaison des routages

| Routage | Construction | Métrique | Vision du réseau | Chemin choisi |
|---|---|---|---|---|
| **Statique** | manuelle | définie par l'administrateur | routes saisies | route configurée |
| **RIP** | échanges entre voisins | nombre de sauts | locale | moins de sauts |
| **OSPF** | états de liens | somme des coûts | complète | coût minimal |

---

## 10. Méthodes bac

!!! tip "Procédures à appliquer"
    - **convertir** masque ↔ CIDR (`/24` ↔ `255.255.255.0`) ;
    - **calculer** réseau (`IP AND masque`), broadcast et plage utilisable (`2^h − 2`) ;
    - **décider local ou distant** (comparer les adresses réseau) ;
    - **attribuer** les adresses aux interfaces (réseau et broadcast exclus) ;
    - **compléter** une table de routage ;
    - **choisir** une route (préfixe le plus précis) ;
    - **calculer** une métrique RIP (distance reçue + 1) ;
    - **calculer** les coûts OSPF (`10^8 / débit`) ;
    - **appliquer** Dijkstra (distances + prédécesseurs) ;
    - **reconstituer** un chemin (remonter les prédécesseurs).

---

## 11. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **réseau**, **hôte** et **broadcast** ;
    - **oublier de retirer** le réseau et le broadcast (`2^h − 2`) ;
    - confondre **passerelle** et **interface** ;
    - mettre une **passerelle** sur un réseau **directement connecté** (c'est On-link) ;
    - **oublier la route par défaut** `0.0.0.0/0` ;
    - mal **choisir entre plusieurs préfixes** (prendre le plus **long**) ;
    - confondre **RIP** (sauts, vision locale) et **OSPF** (coûts, vision complète) ;
    - **mal convertir** le débit en **bit/s** avant le calcul de coût ;
    - **ne pas additionner** les coûts d'un chemin OSPF ;
    - **oublier les prédécesseurs** dans Dijkstra (chemin impossible à reconstituer).

---

## 12. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Sur quelle couche TCP/IP agit le protocole IP, et quelle donnée manipule-t-il ?"
    Couche **Internet / Réseau** ; il manipule des **paquets**.

??? question "2. Quels ports utilisent HTTP et HTTPS ?"
    HTTP → port **80** ; HTTPS → port **443**.

??? question "3. Convertir le masque `/26` en notation décimale et donner le nombre d'hôtes utilisables."
    `/26` → `255.255.255.192` ; `h = 6` → `2^6 − 2 = 62` hôtes.

??? question "4. Donner l'adresse réseau et le broadcast de `172.16.5.10 /24`."
    Réseau : `172.16.5.0` ; broadcast : `172.16.5.255`.

??? question "5. Deux machines `192.168.1.130/25` et `192.168.1.10/25` sont-elles dans le même sous-réseau ?"
    Non : `.130` → réseau `192.168.1.128` ; `.10` → réseau `192.168.1.0`. Elles
    passent par la **passerelle**.

??? question "6. À quoi sert la route par défaut et quelle est sa notation ?"
    Elle est utilisée quand **aucune autre route** ne correspond ; notation
    `0.0.0.0/0`.

??? question "7. Entre deux routes correspondantes, laquelle est choisie ?"
    Celle au **préfixe le plus précis** (masque le plus **long**).

??? question "8. Dans RIP, comment met-on à jour la distance reçue d'un voisin ?"
    On **ajoute 1** à la distance reçue (un saut de plus).

??? question "9. Que signifie une métrique RIP de 16 ?"
    Le réseau est **inaccessible** (15 est le maximum atteignable).

??? question "10. Calculer le coût OSPF d'un lien à 10 Mbit/s."
    `10^8 / 10^7 = 10`.

??? question "11. Comparer deux chemins OSPF : A→B (coût 1) → D (coût 10) et A→C (coût 5) → D (coût 5)."
    Premier chemin : `1 + 10 = 11` ; second : `5 + 5 = 10`. On choisit le **second**
    (coût minimal).

??? question "12. Dans Dijkstra, pourquoi note-t-on les prédécesseurs ?"
    Pour pouvoir **reconstituer le chemin** en remontant de l'arrivée vers le départ.

---

## À retenir absolument

!!! abstract "Formules essentielles"
    - **adresse réseau** = `IP AND masque` ;
    - **total d'adresses** = `2^h` ; **hôtes utilisables** = `2^h − 2` ;
    - **coût OSPF** = `10^8 / débit (bit/s)` (minimum 1) ;
    - **métrique RIP** = distance reçue **+ 1** (max 15, 16 = inaccessible).

!!! note "Champs d'une table de routage"
    **destination · masque · passerelle · interface · métrique** — route choisie =
    **préfixe le plus précis** ; route par défaut = `0.0.0.0/0`.

!!! success "RIP vs OSPF"
    | | **RIP** | **OSPF** |
    |---|---|---|
    | Type | vecteur de distance | état de liens |
    | Métrique | nombre de sauts | somme des coûts |
    | Vision | locale | complète |
    | Chemin | moins de sauts | coût minimal |

!!! quote "Étapes de Dijkstra"
    départ à 0, autres à ∞ → choisir la **distance provisoire minimale** → **fixer**
    le sommet → **actualiser** les voisins → **noter les prédécesseurs** → poursuivre
    → **reconstituer** le chemin (poids **positifs**).