---
author: Elisabeth Le Prettre (LePrettre)
title: 08 📜 Fiche Méthode - Les processus
---

# Les processus

!!! abstract "Fiche de révision — Terminale NSI"
    Fiche **complète, concise et lisible** sur les processus : rôle du système
    d'exploitation, ordonnancement, calculs temporels, états, interblocage,
    commandes Linux et création de processus (`fork`, `exec`).

!!! note "Exemple filé"
    Trois processus, réutilisés pour FIFO, SJF et Round Robin :

    | Processus | Arrivée | Durée CPU |
    |---|---|---|
    | **P1** | 0 | 5 |
    | **P2** | 1 | 3 |
    | **P3** | 2 | 1 |

---

## 1. Rôle du système d'exploitation

Le système d'exploitation (SE) assure :

- la **gestion du processeur**, de la **mémoire**, des **fichiers** et des **périphériques** ;
- la prise en charge des **interruptions** et des **entrées-sorties** ;
- l'**exécution des programmes** ;
- la **sécurité** et la gestion des **droits** ;
- l'**abstraction du matériel** (cacher la complexité physique).

!!! note "Mémo des commandes (fichiers et dossiers)"
    | Commande | Rôle |
    |---|---|
    | `sudo` | Exécuter en tant qu'administrateur |
    | `pwd` | Afficher le dossier courant |
    | `cd` | Changer de dossier |
    | `ls` / `ls -l` / `ls -a` | Lister / détaillé / fichiers cachés |
    | `chmod` | Modifier les droits |
    | `mkdir` / `rmdir` | Créer / supprimer un dossier (vide) |
    | `rm` / `rm -r` | Supprimer un fichier / un dossier et son contenu |
    | `mv` | Déplacer ou renommer |
    | `touch` | Créer un fichier vide |
    | `kill` | Envoyer un signal à un processus |

---

## 2. Processus

| Terme | Définition |
|---|---|
| **Programme** | Fichier **passif** contenant des instructions (sur le disque). |
| **Processus** | Programme **en cours d'exécution** (entité active). |
| **Ressource** | Élément utilisé par un processus (CPU, mémoire, fichier, E/S). |
| **PID** | Identifiant unique du processus. |
| **PPID** | PID du **processus père**. |
| **Père / fils** | Un processus en crée un autre (père → fils). |
| **Arborescence** | Organisation hiérarchique des processus (père-fils). |
| **Multitâche** | Exécution de plusieurs processus « en même temps ». |
| **Ordonnanceur** | Composant du SE qui **choisit** le processus à exécuter. |

!!! note "Contenu d'un processus"
    Un processus contient des **instructions**, un **état du processeur** (registres),
    de la **mémoire** et des **ressources** allouées.

---

## 3. Ordonnancement

| Algorithme | Principe | Avantage | Limite |
|---|---|---|---|
| **FIFO / FCFS** | ordre d'arrivée | simple | attente possible des tâches courtes |
| **SJF** | plus courte tâche **disponible** | réduit souvent l'attente moyenne | durée à connaître |
| **Round Robin** | **quantum** + file FIFO | partage équitable | dépend du quantum |
| **Priorité** | priorité la plus élevée | favorise certaines tâches | risque de **famine** |

!!! tip "Construire le diagramme de Gantt"
    - **FIFO** : placer les processus dans l'**ordre d'arrivée**, l'un après l'autre.
    - **SJF** : à chaque fin de tâche, choisir la **plus courte** parmi celles
      **déjà arrivées**.
    - **Round Robin** : exécuter chaque processus pendant **un quantum**, puis le
      renvoyer **en fin de file** s'il n'est pas terminé.
    - **Priorité** : exécuter en premier la **priorité la plus élevée**.

---

## 4. Calculs temporels

| Grandeur | Définition |
|---|---|
| **Temps d'arrivée** | Instant où le processus devient prêt. |
| **Durée d'exécution CPU** | Temps processeur total nécessaire. |
| **Temps de terminaison** | Instant de **fin** du processus. |
| **Temps de séjour** | Temps total passé dans le système. |
| **Temps d'attente** | Temps passé à attendre (hors exécution). |

!!! abstract "Formules"
    ```
    T_séjour  = T_fin − T_arrivée
    T_attente = T_séjour − durée
    ```

!!! tip "Méthode en 4 étapes"
    1. construire le **diagramme de Gantt** ;
    2. relever le **temps de fin** de chaque processus ;
    3. calculer le **temps de séjour** (`T_fin − T_arrivée`) ;
    4. calculer le **temps d'attente** (`T_séjour − durée`).

!!! example "Comparaison sur l'exemple filé"
    **FIFO** : `P1 [0–5] · P2 [5–8] · P3 [8–9]`

    | | Fin | Séjour | Attente |
    |---|---|---|---|
    | P1 | 5 | 5 | 0 |
    | P2 | 8 | 7 | 4 |
    | P3 | 9 | 7 | 6 |

    **SJF** : `P1 [0–5] · P3 [5–6] · P2 [6–9]` (à t=5, P3 est la plus courte)

    | | Fin | Séjour | Attente |
    |---|---|---|---|
    | P1 | 5 | 5 | 0 |
    | P3 | 6 | 4 | 3 |
    | P2 | 9 | 8 | 5 |

---

## 5. Round Robin

- les processus prêts sont rangés dans une **file FIFO** ;
- chacun s'exécute pendant **un quantum** (ou **jusqu'à la fin** s'il reste moins) ;
- s'il n'a pas terminé, il **retourne en fin de file** ;
- les **nouveaux arrivants** sont insérés dans la file à leur arrivée ;
- on suit le **temps restant** de chaque processus.

!!! example "Suivi Round Robin (quantum = 2) sur l'exemple filé"
    | Instant | Processus exécuté | Temps restant après | File après |
    |---|---|---|---|
    | 0 | P1 | 3 | [P2, P3, P1] |
    | 2 | P2 | 1 | [P3, P1, P2] |
    | 4 | P3 | 0 (fini) | [P1, P2] |
    | 5 | P1 | 1 | [P2, P1] |
    | 7 | P2 | 0 (fini) | [P1] |
    | 8 | P1 | 0 (fini) | [ ] |

    Fins : P3 = 5, P2 = 8, P1 = 9 → attente : P1 = 4, P2 = 4, P3 = 2.

---

## 6. États des processus

| État | Signification |
|---|---|
| **Prêt** | attend le CPU |
| **Élu / Exécution** | utilise le CPU |
| **Bloqué** | attend une ressource ou une E/S |

!!! note "Transitions"
    - **Prêt → Élu** : l'ordonnanceur **élit** le processus.
    - **Élu → Prêt** : fin du **quantum** ou **préemption**.
    - **Élu → Bloqué** : le processus **demande une E/S** ou une ressource.
    - **Bloqué → Prêt** : la **ressource / E/S devient disponible**.
    - **Élu → Terminé** : le processus **se termine**.

---

## 7. Interblocage

!!! danger "Définition"
    Un **interblocage** (*deadlock*) survient lorsque plusieurs processus s'attendent
    **mutuellement** : aucun ne peut continuer car chacun attend une ressource
    détenue par un autre.

- **processus** : entités qui demandent des ressources ;
- **ressources** : éléments en nombre limité (fichier, imprimante…) ;
- **attente circulaire** : chaîne d'attentes formant une boucle ;
- **cycle** dans le **graphe processus-ressources** → signe d'interblocage.

| Solution | Principe |
|---|---|
| **Prévention** | empêcher une des conditions d'apparition. |
| **Évitement** | n'accorder une ressource que si c'est **sûr**. |
| **Détection** | repérer un **cycle** dans le graphe. |
| **Résolution** | **interrompre** un processus ou **libérer** une ressource. |

!!! example "Construire une exécution menant à un interblocage"
    1. chaque processus prend une **première ressource** ;
    2. chacun **demande** une ressource **détenue par un autre** ;
    3. aucun ne peut continuer **ni libérer** sa première ressource → blocage total.

---

## 8. Commandes Linux des processus

| Commande | Rôle | Exemple |
|---|---|---|
| `man` | Afficher le manuel d'une commande | `man ps` |
| `ps -ef` | Lister tous les processus | `ps -ef` |
| `ps -eo pid,ppid,stat,cmd` | Lister avec colonnes choisies | `ps -eo pid,ppid,stat,cmd` |
| `pstree -p` | Afficher l'**arborescence** avec PID | `pstree -p` |
| `top` | Affichage **dynamique** des processus | `top` |
| `sleep 1000 &` | Lancer un processus en **arrière-plan** | `sleep 1000 &` |
| `pgrep -a` | Rechercher un processus par nom | `pgrep -a sleep` |
| `kill PID` | Envoyer **SIGTERM** (arrêt propre) | `kill 1234` |
| `kill -9 PID` | Envoyer **SIGKILL** (arrêt brutal) | `kill -9 1234` |

!!! note "Distinctions importantes"
    - **`ps`** : **photographie** à un instant donné ; **`top`** : **mise à jour
      dynamique**.
    - **SIGTERM (15)** : arrêt **propre** (le processus peut se fermer correctement) ;
      **SIGKILL (9)** : arrêt **brutal** (immédiat, non ignorable).

---

## 9. Création des processus

- **`fork()`** crée un **fils** en **dupliquant** le père ;
- père et fils ont des **PID différents** ;
- le **PPID** du fils correspond au **PID** du père ;
- **`exec()`** **remplace** le programme exécuté par le processus ;
- **`init`** ou **`systemd`** est généralement le **PID 1** (ancêtre de tous les processus).

!!! tip "Schéma typique"
    Un programme fait `fork()` (création du fils) puis le fils fait `exec()` pour
    **charger un autre programme**, pendant que le père continue.

---

## 10. Méthodes bac

!!! tip "Procédures à appliquer"
    - **distinguer programme et processus** (passif sur disque vs actif en exécution) ;
    - **lire PID et PPID** dans une sortie `ps` ;
    - **reconstituer une arborescence** (relier chaque PPID à son PID) ;
    - **construire un Gantt** (selon l'algorithme) ;
    - **calculer** fin, séjour (`T_fin − T_arrivée`) et attente (`séjour − durée`) ;
    - **suivre une file Round Robin** (quantum + temps restant) ;
    - **reconnaître un état** (Prêt / Élu / Bloqué) ;
    - **identifier un deadlock** (cycle d'attente) ;
    - **interpréter une commande Linux** ;
    - **expliquer `fork()` et `exec()`**.

---

## 11. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - confondre **programme** (passif) et **processus** (actif) ;
    - confondre **PID** et **PPID** ;
    - confondre **durée**, **séjour** et **attente** ;
    - oublier que **SJF** choisit **seulement parmi les processus déjà arrivés** ;
    - ne pas respecter la **file** et le **quantum** en Round Robin ;
    - confondre **Bloqué** et **Prêt** ;
    - confondre **`ps`** (photo) et **`top`** (dynamique) ;
    - confondre **SIGTERM** (propre) et **SIGKILL** (brutal) ;
    - croire qu'un processus **bloqué consomme le CPU** (il ne le consomme **pas**) ;
    - oublier qu'un **cycle d'attente** peut provoquer un **interblocage**.

---

## 12. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Quelle est la différence entre un programme et un processus ?"
    Le **programme** est un fichier **passif** (instructions sur disque) ; le
    **processus** est un programme **en cours d'exécution** (entité active).

??? question "2. Que représentent PID et PPID ?"
    Le **PID** identifie le processus ; le **PPID** est le PID de son **père**.

??? question "3. Ordonnancement FIFO de l'exemple filé : donner les temps de fin."
    `P1 [0–5]`, `P2 [5–8]`, `P3 [8–9]` → fins : P1 = 5, P2 = 8, P3 = 9.

??? question "4. SJF : pourquoi P3 passe-t-il avant P2 ?"
    À `t = 5`, P2 (durée 3) et P3 (durée 1) sont arrivés ; SJF choisit la plus
    **courte**, donc **P3**.

??? question "5. Calculer le temps de séjour et d'attente de P2 en FIFO."
    Séjour = `8 − 1 = 7` ; attente = `7 − 3 = 4`.

??? question "6. Round Robin (q=2) : quel processus s'exécute à l'instant 4 ?"
    **P3** (il termine, durée restante 1 < quantum).

??? question "7. Citer les trois états d'un processus."
    **Prêt**, **Élu (Exécution)**, **Bloqué**.

??? question "8. Quelle transition correspond à une demande d'entrée-sortie ?"
    **Élu → Bloqué**.

??? question "9. Qu'est-ce qu'une attente circulaire ?"
    Une chaîne de processus s'attendant mutuellement (chacun détient une ressource
    réclamée par le suivant), formant un **cycle** → interblocage.

??? question "10. Différence entre `ps` et `top` ?"
    `ps` donne une **photographie** à un instant donné ; `top` se **met à jour
    dynamiquement**.

??? question "11. Différence entre `kill PID` et `kill -9 PID` ?"
    `kill PID` envoie **SIGTERM (15)** : arrêt **propre** ; `kill -9 PID` envoie
    **SIGKILL (9)** : arrêt **brutal** et immédiat.

??? question "12. Que font `fork()` et `exec()` ?"
    `fork()` **crée un fils** en dupliquant le père (PID différent) ; `exec()`
    **remplace** le programme exécuté par le processus.

---

## À retenir absolument

!!! success "Définitions essentielles"
    - **programme** = passif (disque) ; **processus** = actif (en exécution) ;
    - **PID** = identifiant ; **PPID** = PID du père ;
    - l'**ordonnanceur** choisit le processus à exécuter (**multitâche**).

!!! abstract "Formules temporelles"
    ```
    T_séjour  = T_fin − T_arrivée
    T_attente = T_séjour − durée
    ```

!!! note "Ordonnanceurs"
    | Algorithme | Métrique / principe | Risque |
    |---|---|---|
    | **FIFO** | ordre d'arrivée | tâches courtes pénalisées |
    | **SJF** | plus courte arrivée | durée à connaître |
    | **Round Robin** | quantum + file | dépend du quantum |
    | **Priorité** | priorité max | **famine** |

!!! note "États & commandes"
    - **États** : Prêt (attend le CPU) · Élu (utilise le CPU) · Bloqué (attend une E/S).
    - **Commandes** : `ps -ef`, `pstree -p`, `top`, `kill` (SIGTERM 15),
      `kill -9` (SIGKILL 9), `pgrep -a`.

!!! quote "Repérer un interblocage"
    Chercher un **cycle d'attente** dans le **graphe processus-ressources** : si
    chaque processus détient une ressource réclamée par un autre, et qu'aucun ne
    peut libérer la sienne, il y a **interblocage**.