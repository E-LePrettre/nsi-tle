---
author: Elisabeth Le Prettre (LePrettre)
title: 13 📜 Fiche Méthode - Les SOC
---

# Les SoC — System on a Chip

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur les **systèmes sur puce (SoC)** :
    repères historiques, architecture de Von Neumann, composants intégrés,
    comparaison avec un PC classique, et caractéristiques techniques.

---

## 1. Repères historiques

- **Loi de Moore** : observation selon laquelle le **nombre de transistors** d'une
  puce **double** environ tous les deux ans.
- **Miniaturisation** : les transistors deviennent de plus en plus **petits**, ce
  qui permet d'en intégrer toujours plus.
- **IBM 650** : ordinateur à **tubes à vide** (volumineux, gourmand en énergie).
- **IBM 7090** : ordinateur à **transistors** (plus rapide, plus compact, plus fiable).
- **Conséquences** : gains en **puissance**, **compacité**, **consommation** et
  **intégration**.

!!! note "Le transistor"
    Composant électronique qui agit comme un **interrupteur** commandé. Dans un
    **processeur**, il sert à réaliser les **opérations logiques** (portes logiques),
    à **commuter** (laisser passer ou bloquer le courant) et à **mémoriser** des bits.

---

## 2. PC classique

| Composant | Rôle |
|---|---|
| **CPU** | exécute les instructions et calcule |
| **RAM** | mémoire temporaire rapide |
| **GPU** | images et calculs graphiques |
| **Carte mère** | relie les composants par les **bus** |
| **Stockage** | conservation durable des données |
| **Interface réseau** | communication avec d'autres machines |

!!! note
    Dans un PC classique, les composants sont **séparés physiquement** (et reliés par
    la carte mère).

---

## 3. Architecture de Von Neumann

| Élément | Rôle |
|---|---|
| **Unité de contrôle** | dirige l'exécution des instructions |
| **ALU** (unité arithmétique et logique) | effectue les calculs et opérations logiques |
| **Registres** | petites mémoires très rapides internes au processeur |
| **Mémoire** | stocke instructions et données |
| **Entrées-sorties** | échanges avec l'extérieur |

- **bus d'adresses** : indique **où** lire / écrire ;
- **bus de données** : transporte les **données** ;
- **bus de commandes** : transmet les **ordres** (lecture / écriture).

!!! note
    Les instructions sont exécutées de manière **séquentielle** (l'une après l'autre).

---

## 4. Définition du SoC

!!! abstract "Définition"
    Un **SoC** (*System on a Chip*) est un **système informatique** largement
    **intégré sur une seule puce** : il regroupe sur un même circuit ce qui serait,
    dans un PC, réparti entre plusieurs composants.

| PC classique | SoC |
|---|---|
| composants **séparés** | composants **intégrés** |
| plus **encombrant** | **compact** |
| plus **réparable** et **évolutif** | **peu réparable** |
| communications par la **carte mère** | communications **internes rapides** |
| consommation généralement **supérieure** | consommation **optimisée** |

---

## 5. Composants d'un SoC

| Bloc | Rôle |
|---|---|
| **CPU** | calcul général |
| **Cœurs** | exécution de plusieurs tâches |
| **Cache** | données rapidement accessibles |
| **GPU** | graphismes |
| **NPU** | intelligence artificielle |
| **DSP** | traitement audio, vidéo et signaux |
| **ISP** | traitement des photos et vidéos des caméras |
| **Modem** | réseaux mobiles |
| **Wi-Fi, Bluetooth, NFC, GPS** | communications et localisation |
| **RAM** | données temporaires |
| **Mémoire flash** | stockage durable |
| **SPU** | sécurité et données sensibles |
| **PMIC** | gestion de l'énergie |

---

## 6. Exemples

- **Exynos** (Samsung) ;
- **Snapdragon** (Qualcomm) ;
- **Raspberry Pi 3 B+** et **Raspberry Pi 4**.

!!! note "Blocs d'un Snapdragon"
    | Nom commercial | Type de bloc |
    |---|---|
    | **Kryo** | CPU |
    | **Adreno** | GPU |
    | **Hexagon** | DSP |
    | **X20 LTE** | modem |
    | **Spectra** | ISP |

---

## 7. Avantages et inconvénients

| Avantages | Inconvénients |
|---|---|
| **faible consommation** | **réparation difficile** |
| **rapidité des échanges** | **absence d'évolution** matérielle |
| **performances** | **remplacement complet** en cas de panne |
| **compacité** | contraintes de **chauffe / gravure / miniaturisation** |
| **coût de fabrication** | |
| **sécurité matérielle** | |
| **intégration** de nombreux périphériques | |

---

## 8. Caractéristiques techniques

| Caractéristique | Définition |
|---|---|
| **Nombre de cœurs** | nombre d'unités de calcul indépendantes du CPU |
| **Thread** | fil d'exécution (un cœur peut en gérer plusieurs) |
| **Fréquence** | nombre de cycles par seconde (en GHz) |
| **Mémoire cache** | petite mémoire très rapide proche du CPU |
| **Finesse de gravure** | taille des plus petits éléments gravés (en nm) |
| **Surface de la puce** | aire physique du circuit |
| **Nombre / densité de transistors** | total de transistors et quantité par unité de surface |

!!! warning "Une fréquence élevée ne suffit pas"
    On **ne peut pas** conclure qu'un SoC est plus performant **seulement** parce que
    sa fréquence est plus élevée. Il faut aussi étudier l'**architecture**, le nombre
    de **cœurs**, le **cache**, le **GPU**, la **mémoire** et la **spécialisation des
    unités** (NPU, DSP, ISP…).

---

## 9. Méthodes bac

!!! tip "Procédures à appliquer"
    - **reconnaître** un SoC (système intégré sur une seule puce) ;
    - **identifier** ses blocs sur un schéma ;
    - **expliquer** le rôle d'un composant ;
    - **comparer** PC et SoC ;
    - **comparer** deux générations de SoC ;
    - **relever** des caractéristiques techniques ;
    - **justifier** un gain de **vitesse** ou de **consommation** ;
    - **argumenter** sur la **maintenance** et l'**évolution** matérielle.

---

## 10. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **SoC** (système entier) et **CPU** (un seul bloc) ;
    - confondre **CPU** et **GPU** ;
    - confondre **RAM** (temporaire) et **mémoire flash** (durable) ;
    - confondre **GPU**, **NPU**, **DSP** et **ISP** (rôles distincts) ;
    - réduire le **modem** au seul **Wi-Fi** (le modem gère les **réseaux mobiles**) ;
    - croire qu'une **fréquence élevée** garantit la **performance globale** ;
    - confondre **finesse de gravure** et **surface de la puce** ;
    - croire qu'une **forte intégration** facilite la **réparation** (au contraire) ;
    - confondre **SPU** (sécurité) et **mémoire principale** ;
    - croire que les composants d'un **PC classique** sont **regroupés** sur une seule puce.

---

## 11. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Qu'énonce la loi de Moore ?"
    Le **nombre de transistors** d'une puce **double** environ tous les deux ans.

??? question "2. Quel est le rôle d'un transistor dans un processeur ?"
    Il agit comme un **interrupteur commandé** : il sert aux **opérations logiques**,
    à la **commutation** et à la **mémorisation** de bits.

??? question "3. Citer trois éléments de l'architecture de Von Neumann."
    Par exemple : l'**unité de contrôle**, l'**ALU** et la **mémoire** (aussi :
    registres, entrées-sorties, bus).

??? question "4. Donner une définition du SoC."
    Un **système informatique** largement **intégré sur une seule puce**.

??? question "5. À quoi sert le NPU dans un SoC ?"
    Au traitement lié à l'**intelligence artificielle**.

??? question "6. Quelle est la différence entre la RAM et la mémoire flash ?"
    La **RAM** stocke des données **temporaires** (rapide) ; la **mémoire flash**
    assure un **stockage durable**.

??? question "7. Sur un schéma, à quoi reconnaît-on l'ISP ?"
    C'est le bloc dédié au **traitement des photos et vidéos** issues des **caméras**.

??? question "8. Citer un avantage et un inconvénient majeur d'un SoC."
    Avantage : **faible consommation** (ou compacité, performances…) ; inconvénient :
    **réparation difficile** (peu évolutif).

??? question "9. Comparer un PC classique et un SoC sur la réparabilité."
    Le PC, à composants **séparés**, est **réparable et évolutif** ; le SoC, **intégré**,
    est **peu réparable** (remplacement complet en cas de panne).

??? question "10. Le SoC A a une fréquence plus élevée que le SoC B. Est-il forcément plus performant ?"
    **Non** : il faut aussi considérer l'architecture, les cœurs, le cache, le GPU,
    la mémoire et la spécialisation des unités.

??? question "11. Quel bloc gère la sécurité et les données sensibles ?"
    Le **SPU**.

??? question "12. Pourquoi un SoC consomme-t-il généralement moins qu'un PC classique ?"
    Grâce à son **intégration** (communications internes courtes et rapides) et à une
    consommation **optimisée**.

---

## À retenir absolument

!!! success "Définition"
    Un **SoC** est un **système informatique intégré sur une seule puce**, regroupant
    CPU, GPU, mémoires, communications et blocs spécialisés.

!!! abstract "Composants principaux"
    **CPU** (+ cœurs, cache) · **GPU** · **NPU** · **DSP** · **ISP** · **modem** ·
    **Wi-Fi / Bluetooth / NFC / GPS** · **RAM** · **flash** · **SPU** · **PMIC**.

!!! note "PC classique vs SoC"
    | | **PC classique** | **SoC** |
    |---|---|---|
    | Composants | séparés | intégrés |
    | Taille | encombrant | compact |
    | Réparation | facile, évolutif | difficile |
    | Consommation | supérieure | optimisée |

!!! quote "Comparer deux puces"
    « On ne compare pas deux SoC sur la seule **fréquence** : il faut étudier
    l'**architecture**, le nombre de **cœurs**, le **cache**, le **GPU**, la
    **mémoire** et la **spécialisation des unités** (NPU, DSP, ISP). »

    **Avantage clé** : faible consommation et forte intégration.
    **Inconvénient majeur** : réparation difficile et absence d'évolution matérielle.