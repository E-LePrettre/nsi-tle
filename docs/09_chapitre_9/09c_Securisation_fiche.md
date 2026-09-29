---
author: Elisabeth Le Prettre (LePrettre)
title: 09 📜 Fiche Méthode - Sécurisation
---

# Sécurisation des communications

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur la sécurisation des communications :
    chiffrement **symétrique** et **asymétrique**, **RSA**, attaque de l'**homme du
    milieu**, **certificats** et **HTTPS / TLS**.

---

## 1. Communication web

Étapes d'une requête web :

1. **analyse de l'URL** (protocole, nom de domaine, chemin) ;
2. **DNS** : le nom de domaine est traduit en **adresse IP** ;
3. **connexion TCP** : poignée de main `SYN` → `SYN-ACK` → `ACK` ;
4. **HTTP** (port **80**) ou **HTTPS** (port **443**) ;
5. **encapsulation** : HTTP → TCP → IP → Ethernet / Wi-Fi.

!!! warning "Pourquoi HTTP en clair n'est pas sécurisé"
    En **HTTP**, tout circule **en clair** : n'importe quel intermédiaire sur le
    trajet peut **lire** et **modifier** les données (identifiants, contenu…).
    Même avec **HTTPS**, certaines **métadonnées** restent observables : l'**IP de
    destination**, le **volume** et le **rythme** des échanges, et souvent le **nom
    de domaine** (résolution DNS).

---

## 2. Objectifs et vocabulaire

| Terme | Définition |
|---|---|
| **Confidentialité** | Seul le destinataire prévu peut **lire** le message. |
| **Intégrité** | Le message n'a **pas été modifié**. |
| **Authenticité** | L'**identité** de l'expéditeur est vérifiée. |
| **Codage / décodage** | Changement de **représentation** (UTF-8, base64) — **pas** de la sécurité. |
| **Chiffrement / déchiffrement** | Rendre illisible / lisible **à l'aide d'une clé**. |
| **Décryptage** | Lire un message **sans** posséder la clé (attaque). |
| **Cryptographie** | Science de la **protection** des communications. |
| **Cryptanalyse** | Science de l'**attaque** des chiffrements. |
| **Clé** | Paramètre **secret** utilisé pour chiffrer / déchiffrer. |

---

## 3. Chiffrement symétrique

- **même clé** pour chiffrer et déchiffrer ;
- **rapide**, adapté aux **gros volumes** ;
- **problème** : comment **distribuer la clé** de façon sûre ?
- **principe de Kerckhoffs** : la sécurité repose sur le **secret de la clé**, pas
  sur le secret de l'algorithme ;
- **masque jetable** : sécurité parfaite si la clé est **aléatoire**, **aussi longue**
  que le message et **utilisée une seule fois** ;
- **AES** : algorithme symétrique standard et robuste.

!!! note "Mémo XOR"
    **Table de vérité** du XOR (`^`) :

    | a | b | a ⊕ b |
    |---|---|---|
    | 0 | 0 | 0 |
    | 0 | 1 | 1 |
    | 1 | 0 | 1 |
    | 1 | 1 | 0 |

    - la **clé est répétée** sur toute la longueur du message ;
    - on applique le XOR **octet par octet** ;
    - **double application** : `M ⊕ K ⊕ K = M` → la même opération chiffre **et** déchiffre ;
    - on travaille sur des **`bytes`** (chaîne **encodée en UTF-8**) ;
    - une **clé courte** est **attaquable par force brute**.

    ```python
    message = "Bonjour".encode("utf-8")    # type bytes
    cle     = "clef".encode("utf-8")
    chiffre = bytes(o ^ cle[i % len(cle)] for i, o in enumerate(message))
    clair   = bytes(o ^ cle[i % len(cle)] for i, o in enumerate(chiffre))  # même opération
    ```

---

## 4. Chiffrement asymétrique

| Élément | Rôle |
|---|---|
| **Clé publique** | diffusée, sert à **chiffrer** ou **vérifier** |
| **Clé privée** | secrète, sert à **déchiffrer** ou **signer** |
| **Avantage** | pas de clé secrète à transmettre directement |
| **Limite** | calcul **plus lent** |
| **Risque** | **MITM** si la clé publique n'est pas **authentifiée** |

!!! note "Diffie-Hellman"
    Permet à deux parties d'**établir un secret commun** sur un canal non sûr, sans
    se l'être transmis. Mais il **doit être authentifié** : sinon un attaquant peut
    s'intercaler (**MITM**).

---

## 5. RSA

!!! note "Définitions"
    - **Congruence** : `a ≡ b [n]` signifie que `a` et `b` ont le **même reste** modulo `n`.
    - **Modulo** : reste de la division euclidienne.
    - **PGCD** : plus grand commun diviseur.
    - **Premiers entre eux** : `PGCD = 1`.
    - **Inverse modulaire** de `e` : nombre `d` tel que `e × d ≡ 1 [φ(n)]`.
    - **Indicatrice d'Euler** `φ(n)` : nombre d'entiers `< n` premiers avec `n`.

!!! tip "Méthode (construction des clés)"
    1. choisir `p` et `q` **premiers** ;
    2. `n = p × q` ;
    3. `φ(n) = (p − 1)(q − 1)` ;
    4. choisir `e` avec `PGCD(e, φ(n)) = 1` ;
    5. trouver `d` tel que `e × d ≡ 1 [φ(n)]` ;
    6. **clé publique** `(e, n)` ;
    7. **clé privée** `(d, n)` ;
    8. **chiffrement** `C = M^e mod n` ;
    9. **déchiffrement** `M = C^d mod n`.

!!! example "Petit calcul RSA"
    1. `p = 3`, `q = 11` → `n = 33` ;
    2. `φ(n) = (3−1)(11−1) = 2 × 10 = 20` ;
    3. `e = 3` car `PGCD(3, 20) = 1` ✔ ;
    4. `d = 7` car `3 × 7 = 21 ≡ 1 [20]` ✔ ;
    5. publique `(3, 33)` · privée `(7, 33)` ;
    6. chiffrer `M = 4` : `C = 4^3 mod 33 = 64 mod 33 = 31` ;
    7. déchiffrer : `31^7 mod 33 = 4` → on retrouve bien `M`.

!!! tip "Vérifier qu'une clé publique est valide"
    Vérifier que `e > 1` et que `PGCD(e, φ(n)) = 1` (sinon il n'existe pas d'inverse
    `d`, le déchiffrement est impossible).

!!! warning "Limites de RSA"
    Calculs **coûteux** ; sécurité reposant sur la **difficulté de factoriser** `n` ;
    nécessite de **grandes clés** ; **menace quantique** (un ordinateur quantique
    pourrait casser RSA).

---

## 6. MITM et certificats

!!! danger "Attaque de l'homme du milieu (MITM)"
    Un attaquant **s'intercale** entre les deux interlocuteurs. Il **substitue sa
    propre clé publique** à celle de chacun : il déchiffre, lit (et peut modifier),
    puis rechiffre avant de transmettre. Sans **authentification** de la clé
    publique, les deux parties ne s'aperçoivent de rien.

| Notion | Définition |
|---|---|
| **Autorité de certification (AC)** | Organisme de confiance qui **signe** les certificats. |
| **Certificat** | Document liant une **identité** à une **clé publique**, signé par une AC. |
| **Sujet** | Identité **certifiée** (le titulaire). |
| **Émetteur** | **AC** qui a signé le certificat. |
| **Validité** | Période pendant laquelle le certificat est valable. |
| **Algorithme** | Algorithme de **signature** utilisé. |
| **Usages de clé** | Ce à quoi la clé est **autorisée** (signature, chiffrement…). |
| **Chaîne de certification** | Suite de certificats remontant à une **AC racine** de confiance. |
| **Magasin de confiance** | Ensemble des **AC racine** reconnues par le système / navigateur. |
| **CRL / OCSP** | Liste de **révocation** / vérification **en ligne** de l'état d'un certificat. |

!!! tip "Examiner un certificat dans un navigateur"
    Cliquer sur le **cadenas** dans la barre d'adresse → afficher le **certificat** →
    consulter le **sujet**, l'**émetteur**, la **validité** et la **chaîne** de
    certification.

---

## 7. HTTPS et TLS

!!! abstract "Définition"
    ```
    HTTPS = HTTP + TLS
    ```

| Apport de TLS | Rôle |
|---|---|
| **Authentification** | vérifier l'identité du serveur (certificat) |
| **Confidentialité** | chiffrer les données échangées |
| **Intégrité** | détecter toute modification |
| **Secret de session** | clé symétrique propre à la session |

!!! tip "Stratégie hybride"
    - **asymétrique** : **authentifier** le serveur et **établir le secret** de session ;
    - **symétrique** : **chiffrer rapidement** les données (gros volumes).

!!! info "Approfondissement — TLS 1.3"
    Échange simplifié : **ClientHello** → **ServerHello**, échange de clés
    **ECDHE**, envoi du **certificat** et d'une **signature**, calcul d'un **secret
    partagé**, dérivation des clés par **HKDF**, puis chiffrement des données avec
    **AES-GCM** ou **ChaCha20-Poly1305**.
    TLS 1.3 **n'utilise plus** l'ancien **échange de clé RSA**.

---

## 8. Applications Python

!!! note "Compétences travaillées"
    - **encoder** une chaîne en **UTF-8** (`.encode("utf-8")`) ;
    - manipuler des **`bytes`** ;
    - appliquer le **XOR** octet par octet ;
    - **répéter une clé** avec l'opérateur `%` (`cle[i % len(cle)]`) ;
    - **vérifier** le déchiffrement (retrouver le message d'origine) ;
    - **tester toutes les clés** possibles (force brute) ;
    - **mesurer un temps** d'exécution ;
    - utiliser **congruences** et **exponentiation modulaire** ;
    - programmer les **étapes simplifiées de RSA**.

---

## 9. Méthodes bac

!!! tip "Procédures à appliquer"
    - **choisir** symétrique (rapide, gros volumes) ou asymétrique (authentification, secret) ;
    - **expliquer un échange sécurisé** (hybride : asymétrique puis symétrique) ;
    - **appliquer XOR** (clé répétée, octet par octet) ;
    - **calculer** `n = p×q` et `φ(n) = (p−1)(q−1)` ;
    - **vérifier** `e` (`PGCD(e, φ(n)) = 1`) ;
    - **déterminer** `d` (inverse modulaire de `e`) ;
    - **chiffrer / déchiffrer** avec RSA (`C = M^e mod n`, `M = C^d mod n`) ;
    - **détecter un MITM** (clé publique non authentifiée) ;
    - **analyser un certificat** (sujet, émetteur, validité, chaîne) ;
    - **expliquer le fonctionnement hybride** de HTTPS.

---

## 10. Comparaison

| Technique | Clés | Rapidité | Usage principal | Limite |
|---|---|---|---|---|
| **Symétrique** | une clé partagée | rapide | données volumineuses | distribution de clé |
| **Asymétrique** | publique et privée | plus lent | authentification et secret | coût des calculs |
| **HTTPS / TLS** | combinaison des deux | efficace | communications web | nécessite des certificats fiables |

---

## 11. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **codage** (représentation) et **chiffrement** (sécurité) ;
    - confondre **déchiffrer** (avec la clé) et **décrypter** (sans la clé) ;
    - confondre **clé publique** et **clé privée** ;
    - croire qu'un **XOR à clé courte** offre une **sécurité forte** ;
    - oublier que `e` doit être **premier avec `φ(n)`** ;
    - inverser **clé publique `(e, n)`** et **clé privée `(d, n)`** ;
    - oublier qu'un **MITM** est possible **sans authentification** ;
    - croire qu'un **certificat chiffre** les données (il **authentifie**) ;
    - croire que **HTTPS masque toutes les métadonnées** (IP, volume… restent visibles) ;
    - croire que **RSA chiffre tout le trafic TLS** (le **symétrique** s'en charge).

---

## 12. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Citer les trois grands objectifs de sécurité."
    **Confidentialité**, **intégrité**, **authenticité**.

??? question "2. Quelle est la différence entre codage et chiffrement ?"
    Le **codage** change la **représentation** (UTF-8, base64) sans sécurité ; le
    **chiffrement** rend illisible **à l'aide d'une clé** secrète.

??? question "3. Pourquoi `M ⊕ K ⊕ K = M` est-il utile ?"
    Le XOR est sa propre inverse : la **même opération** chiffre et déchiffre.

??? question "4. Symétrique ou asymétrique pour chiffrer un gros fichier rapidement ?"
    **Symétrique** (rapide, adapté aux gros volumes).

??? question "5. Énoncer le principe de Kerckhoffs."
    La sécurité doit reposer **uniquement sur le secret de la clé**, pas sur le
    secret de l'algorithme.

??? question "6. Avec `p = 3` et `q = 11`, calculer `n` et `φ(n)`."
    `n = 33` ; `φ(n) = 2 × 10 = 20`.

??? question "7. Vérifier que `e = 3` est utilisable, puis donner `d`."
    `PGCD(3, 20) = 1` ✔ ; `d = 7` car `3 × 7 = 21 ≡ 1 [20]`.

??? question "8. Chiffrer `M = 4` avec la clé publique `(3, 33)`."
    `C = 4^3 mod 33 = 64 mod 33 = 31`.

??? question "9. Qu'est-ce qu'une attaque de l'homme du milieu ?"
    Un attaquant s'**intercale** et **substitue sa clé publique** à celle des
    interlocuteurs pour lire (et modifier) les échanges.

??? question "10. À quoi sert un certificat et qui le signe ?"
    Il lie une **identité** à une **clé publique** ; il est **signé** par une
    **autorité de certification**.

??? question "11. Que signifie `HTTPS = HTTP + TLS` ?"
    HTTPS, c'est HTTP transporté dans un canal **sécurisé par TLS**
    (authentification, confidentialité, intégrité).

??? question "12. Dans HTTPS, quel type de chiffrement protège réellement les données ?"
    Le chiffrement **symétrique** (clé de session) ; l'asymétrique sert à
    **authentifier** et à **établir le secret**.

---

## À retenir absolument

!!! success "Symétrique vs asymétrique"
    | | **Symétrique** | **Asymétrique** |
    |---|---|---|
    | Clés | une clé partagée | publique + privée |
    | Vitesse | rapide | plus lent |
    | Usage | gros volumes | authentification, secret |
    | Limite | distribution de clé | coût des calculs |

!!! abstract "Étapes de RSA"
    `p, q premiers` → `n = p×q` → `φ(n) = (p−1)(q−1)` → `e` avec `PGCD(e, φ) = 1`
    → `d` inverse de `e` mod `φ` → publique `(e, n)`, privée `(d, n)` →
    `C = M^e mod n`, `M = C^d mod n`.

!!! note "Rôle des certificats"
    Un **certificat**, signé par une **autorité de certification**, **authentifie**
    une clé publique et contre le **MITM**. Il **n'effectue pas** lui-même le
    chiffrement des données.

!!! quote "HTTPS hybride"
    « HTTPS combine l'**asymétrique** (authentifier le serveur et établir le secret
    de session) et le **symétrique** (chiffrer rapidement les données). »