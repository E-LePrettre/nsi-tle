---
author: Elisabeth Le Prettre (LePrettre)
title: 03 📜 Fiche Méthode - Base de Données 
---

# Modèles relationnels, SGBD et SQL

!!! abstract "Fiche de révision — Terminale NSI · Chapitre 3"
    Fiche **complète mais concise** sur le modèle relationnel, les SGBD et le
    langage SQL. Tous les exemples utilisent un même schéma de quatre tables :
    `film`, `realisateur`, `genre`, `nationalite`.

!!! info "Schéma de référence utilisé dans les exemples"
    ```
    nationalite(id_nat, libelle)
    genre(id_genre, libelle)
    realisateur(id_real, nom, prenom, #id_nat)
    film(id_film, titre, annee, #id_real, #id_genre)
    ```
    Le symbole `#` indique une **clé étrangère**. Les clés primaires sont
    soulignées dans un schéma : ici `id_nat`, `id_genre`, `id_real`, `id_film`.

---

## 1. Définitions

| Terme | Définition |
|---|---|
| **Base de données** | Ensemble structuré de données organisées pour être consultées et modifiées. |
| **Relation / table** | Tableau à deux dimensions regroupant des données de même nature. |
| **Tuple** | Une **ligne** de la table (un enregistrement). |
| **Attribut** | Une **colonne** de la table (une propriété). |
| **Domaine** | Ensemble des valeurs possibles pour un attribut (son type). |
| **Degré** | Nombre d'**attributs** (colonnes) d'une relation. |
| **Cardinalité** | Nombre de **tuples** (lignes) d'une relation. |
| **Vue** | Table « virtuelle » issue d'une requête, sans stockage propre des données. |
| **Schéma relationnel** | Description de la **structure** : tables, attributs, clés. |
| **Diagramme relationnel** | Représentation graphique des tables et de leurs liens (clés étrangères). |

!!! note "Structure ≠ contenu"
    La **structure** décrit l'organisation de la base (tables, attributs, clés,
    domaines) ; le **contenu** correspond aux **tuples** réellement stockés. On
    peut modifier le contenu sans changer la structure, et inversement.

---

## 2. Clés, intégrité et anomalies

### Clés et contraintes

| Notion | Définition |
|---|---|
| **Clé primaire** | Attribut (ou groupe d'attributs) identifiant de façon **unique** chaque tuple. Composée si elle réunit plusieurs attributs. |
| **Clé étrangère** | Attribut qui **référence** la clé primaire d'une autre table, pour créer un lien. |
| **Contrainte de domaine** | La valeur d'un attribut doit appartenir à son domaine (type, `NOT NULL`…). |
| **Contrainte de relation** | Chaque clé primaire est **unique** et non nulle (intégrité d'entité). |
| **Contrainte de référence** | Une clé étrangère doit pointer vers une clé primaire **existante** (intégrité référentielle). |

### Redondance et anomalies

!!! warning "Conséquences d'une mauvaise modélisation"
    - **Redondance** : une même information est répétée dans plusieurs tuples.
    - **Anomalie d'insertion** : impossible d'ajouter une donnée sans en connaître
      une autre (ex. : ajouter un genre sans saisir un film).
    - **Anomalie de mise à jour** : une modification doit être répétée partout ;
      un oubli rend la base **incohérente**.
    - **Anomalie de suppression** : supprimer un tuple efface une information qu'on
      voulait conserver.

!!! tip "Correction : séparer les tables"
    On **décompose** la table redondante en plusieurs tables reliées par des clés
    étrangères. *Exemple :* au lieu de stocker le nom du réalisateur dans chaque
    film, on crée une table `realisateur` et `film` n'y fait référence que par
    `#id_real`. L'information n'est alors stockée **qu'une seule fois**.

---

## 3. SGBD

Un **SGBD** (Système de Gestion de Base de Données) est un logiciel qui gère
l'accès aux données et rend les services suivants :

| Service | Rôle |
|---|---|
| **CRUD** | Create, Read, Update, Delete : créer, lire, modifier, supprimer des données. |
| **Persistance** | Les données sont conservées durablement, même après l'arrêt du programme. |
| **Sécurité** | Gestion des droits d'accès (qui peut lire / écrire). |
| **Sauvegarde / réplication** | Copies de secours et duplication pour éviter la perte de données. |
| **Transactions / verrous** | Une transaction est exécutée **entièrement ou pas du tout** ; les verrous protègent les données pendant une opération. |
| **Concurrence** | Plusieurs utilisateurs peuvent accéder à la base **en même temps** sans incohérence. |
| **Efficacité des requêtes** | Optimisation des recherches pour des réponses rapides. |

!!! note "SGBD vs SGBDR · 2-tiers vs 3-tiers"
    - **SGBD** : gère des bases de données en général ; **SGBDR** : SGBD
      **relationnel**, fondé sur des tables liées entre elles.
    - **Architecture 2-tiers** : client ↔ serveur de base de données (le client
      dialogue directement avec le SGBD).
    - **Architecture 3-tiers** : client ↔ serveur d'application ↔ serveur de base
      de données (une couche intermédiaire sépare l'interface et les données).

---

## 4. Mémo SQL par familles

### Structure (définition des tables)

| Commande | Rôle | Exemple |
|---|---|---|
| `CREATE TABLE` | Créer une table | voir bloc ci-dessous |
| Types | Domaine des attributs | `INTEGER`, `TEXT`, `REAL` |
| `NOT NULL` | Valeur obligatoire | `titre TEXT NOT NULL` |
| `UNIQUE` | Valeurs distinctes | `libelle TEXT UNIQUE` |
| `PRIMARY KEY` | Clé primaire | `id_film INTEGER PRIMARY KEY` |
| `AUTOINCREMENT` | Numérotation auto | `id_film INTEGER PRIMARY KEY AUTOINCREMENT` |
| `FOREIGN KEY … REFERENCES` | Clé étrangère | `FOREIGN KEY (id_real) REFERENCES realisateur(id_real)` |
| `DROP TABLE` | Supprimer une table | `DROP TABLE genre;` |
| `ALTER TABLE … ADD COLUMN` | Ajouter une colonne | `ALTER TABLE film ADD COLUMN duree INTEGER;` |
| `ALTER TABLE … DROP COLUMN` | Supprimer une colonne | `ALTER TABLE film DROP COLUMN duree;` |

```sql
CREATE TABLE film (
    id_film INTEGER PRIMARY KEY AUTOINCREMENT,
    titre   TEXT NOT NULL,
    annee   INTEGER,
    id_real INTEGER,
    id_genre INTEGER,
    FOREIGN KEY (id_real)  REFERENCES realisateur(id_real),
    FOREIGN KEY (id_genre) REFERENCES genre(id_genre)
);
```

### Données (modification du contenu)

| Commande | Rôle | Exemple |
|---|---|---|
| `INSERT INTO … VALUES` | Ajouter un tuple | `INSERT INTO genre (libelle) VALUES ('Drame');` |
| Insertion multiple | Ajouter plusieurs tuples | `INSERT INTO genre (libelle) VALUES ('Drame'), ('Comédie');` |
| `DELETE FROM … WHERE` | Supprimer des tuples | `DELETE FROM film WHERE annee < 1950;` |
| `UPDATE … SET … WHERE` | Modifier des tuples | `UPDATE film SET annee = 1994 WHERE id_film = 3;` |
| `INSERT INTO … SELECT DISTINCT` | Insérer depuis une requête | `INSERT INTO genre (libelle) SELECT DISTINCT libelle FROM import;` |
| `UPPER` / `LOWER` | Majuscules / minuscules | `SELECT UPPER(titre) FROM film;` |
| `SUBSTR` | Extraire une sous-chaîne | `SELECT SUBSTR(titre, 1, 3) FROM film;` |

!!! warning "Apostrophe dans une chaîne SQL"
    Une apostrophe à l'intérieur d'un texte doit être **doublée** :
    ```sql
    INSERT INTO film (titre) VALUES ('L''Aventure');
    ```

### Interrogation (`SELECT`)

| Élément | Rôle | Exemple |
|---|---|---|
| `SELECT … FROM … WHERE` | Sélectionner avec condition | `SELECT titre FROM film WHERE annee > 2000;` |
| Comparaisons, `AND`, `OR` | Combiner des conditions | `WHERE annee >= 1990 AND annee <= 2000` |
| `LIKE` avec `%` | Filtre sur un motif | `WHERE titre LIKE 'Le%'` |
| `IN` / `NOT IN` | Appartenance à une liste | `WHERE id_genre IN (1, 2)` |
| `ORDER BY ASC/DESC` | Trier (multicritère possible) | `ORDER BY annee DESC, titre ASC` |
| `LIMIT` | Limiter le nombre de lignes | `SELECT titre FROM film LIMIT 5;` |
| `DISTINCT` | Éliminer les doublons | `SELECT DISTINCT annee FROM film;` |
| `SELECT *` | Toutes les colonnes | `SELECT * FROM film;` |
| Alias `AS` | Renommer une colonne | `SELECT titre AS film FROM film;` |
| Concaténation `||` | Assembler des textes | `SELECT nom || ' ' || prenom FROM realisateur;` |
| `UNION` | Réunir deux résultats | `SELECT titre FROM film UNION SELECT libelle FROM genre;` |
| `COUNT, SUM, AVG, MIN, MAX` | Agrégats | `SELECT COUNT(*) FROM film;` |

### Jointures et sous-requêtes

| Élément | Rôle | Exemple |
|---|---|---|
| `JOIN … ON` | Relier deux tables | `SELECT f.titre, r.nom FROM film AS f JOIN realisateur AS r ON f.id_real = r.id_real;` |
| Alias de table | Raccourcir les noms | `film AS f`, `realisateur AS r` |
| Sous-requête avec `=` | Comparer à un résultat unique | voir bloc ci-dessous |
| Sous-requête avec `IN` | Comparer à un ensemble | voir bloc ci-dessous |

**Jointure de plusieurs tables** (film → réalisateur → nationalité → genre) :

```sql
SELECT f.titre, r.nom, n.libelle, g.libelle
FROM film AS f
JOIN realisateur AS r ON f.id_real = r.id_real
JOIN nationalite AS n ON r.id_nat = n.id_nat
JOIN genre AS g       ON f.id_genre = g.id_genre;
```

**Sous-requêtes** (se construisent **de l'intérieur vers l'extérieur**) :

```sql
-- avec =  : la sous-requête renvoie UNE valeur
SELECT titre FROM film
WHERE id_real = (SELECT id_real FROM realisateur WHERE nom = 'Kubrick');

-- avec IN : la sous-requête renvoie PLUSIEURS valeurs
SELECT titre FROM film
WHERE id_genre IN (SELECT id_genre FROM genre WHERE libelle LIKE 'Com%');
```

---

## 5. Méthodes bac

### Lire un schéma et repérer les clés

1. Repérer l'attribut qui **identifie** chaque tuple → **clé primaire**.
2. Repérer les attributs qui **référencent** une autre table (souvent `id_…` précédé de `#`) → **clé étrangère**.
3. Suivre les flèches du diagramme pour comprendre les **liens**.

### Calculer degré et cardinalité

- **Degré** = nombre d'**attributs** (compter les colonnes).
- **Cardinalité** = nombre de **tuples** (compter les lignes).

### Repérer une anomalie

- Une information **répétée** → redondance.
- Une donnée **impossible à ajouter / modifier / supprimer** proprement →
  anomalie d'insertion / mise à jour / suppression. La correction passe par la
  **séparation en plusieurs tables**.

### Choisir tables, champs et conditions

1. Quelles **données** veut-on afficher ? → colonnes du `SELECT`.
2. Dans quelle(s) **table(s)** se trouvent-elles ? → `FROM` (+ `JOIN`).
3. Quelle **condition** filtre les tuples ? → `WHERE`.

### Écrire une requête dans le bon ordre

!!! tip "Ordre des clauses"
    `SELECT` → `FROM` → `JOIN … ON` → `WHERE` → `ORDER BY` → `LIMIT`

### Construire une jointure

1. Identifier les **deux tables** à relier.
2. Trouver la **clé étrangère** et la **clé primaire** correspondantes.
3. Écrire `JOIN table2 ON table1.cle = table2.cle`.
4. Préfixer les colonnes ambiguës avec l'**alias** de table.

### Construire une sous-requête

1. Écrire d'abord la **requête intérieure** (celle qui renvoie la valeur cherchée).
2. La placer entre **parenthèses** après `=` (une valeur) ou `IN` (plusieurs).
3. Tester la requête intérieure **seule** avant de l'imbriquer.

### Choisir la bonne commande

| Objectif | Commande |
|---|---|
| Ajouter des données | `INSERT` |
| Lire / interroger | `SELECT` |
| Modifier des données | `UPDATE` |
| Supprimer des données | `DELETE` |
| Créer une table | `CREATE` |
| Modifier la structure | `ALTER` |
| Supprimer une table | `DROP` |

---

## 6. Pièges

!!! danger "Erreurs fréquentes à éviter"
    - **oublier `WHERE`** dans `UPDATE` ou `DELETE` → toute la table est modifiée
      ou vidée ;
    - **confondre clé primaire et clé étrangère** (l'une identifie, l'autre référence) ;
    - **mauvaise condition de jointure** (`ON` qui ne relie pas les bonnes clés) →
      produit cartésien / résultats erronés ;
    - **texte non placé entre apostrophes** : `WHERE nom = Kubrick` ❌ →
      `WHERE nom = 'Kubrick'` ✅ ;
    - **oublier de doubler une apostrophe** dans un texte (`'L''Aventure'`) ;
    - **mauvais usage de `LIKE`, `%` ou `IN`** (`%` est le joker de `LIKE` ;
      `IN` attend une liste) ;
    - **`UNION` avec des colonnes incompatibles** (nombre / type de colonnes différents) ;
    - **oublier `DISTINCT`** quand des doublons faussent le résultat ;
    - **modification / suppression interdite** car un tuple est **référencé** par
      une clé étrangère (intégrité référentielle) ;
    - **confondre structure et données** (`ALTER`/`DROP` touchent la structure,
      `UPDATE`/`DELETE` touchent le contenu).

---

## 7. Entraînement

!!! tip "Conseil d'utilisation"
    Cherche la réponse, **puis** déplie la correction.

??? question "1. Quelle est la différence entre degré et cardinalité d'une relation ?"
    Le **degré** est le nombre d'attributs (colonnes) ; la **cardinalité** est le
    nombre de tuples (lignes).

??? question "2. Qu'est-ce qu'une clé étrangère ?"
    Un attribut d'une table qui **référence la clé primaire** d'une autre table,
    afin de créer un lien entre les deux. *Ex. : `film.id_real` référence
    `realisateur.id_real`.*

??? question "3. Donner un exemple d'anomalie de suppression."
    Si le nom d'un genre n'existe que parce qu'un seul film l'utilise, supprimer ce
    film **efface aussi** l'information sur ce genre. On corrige en plaçant les
    genres dans une table séparée.

??? question "4. Citer trois services rendus par un SGBD."
    Par exemple : la **persistance** des données, la gestion de la **concurrence**
    (accès simultanés), et les **transactions** (exécution complète ou nulle).
    *(Autres réponses valables : sécurité, sauvegarde/réplication, CRUD.)*

??? question "5. Dans le schéma, comment reconnaître la clé primaire de `film` ?"
    C'est l'attribut qui **identifie de façon unique** chaque film, ici `id_film`
    (souligné dans le schéma).

??? question "6. Écrire une requête affichant les titres des films sortis après 2000, triés par année décroissante."
    ```sql
    SELECT titre FROM film
    WHERE annee > 2000
    ORDER BY annee DESC;
    ```

??? question "7. Insérer un nouveau genre « Science-fiction »."
    ```sql
    INSERT INTO genre (libelle) VALUES ('Science-fiction');
    ```

??? question "8. Corriger cette requête : `UPDATE film SET annee = 1994;`"
    Il manque la clause `WHERE`, sinon **tous** les films sont modifiés :
    ```sql
    UPDATE film SET annee = 1994 WHERE id_film = 3;
    ```

??? question "9. Afficher le titre de chaque film avec le nom de son réalisateur (jointure)."
    ```sql
    SELECT f.titre, r.nom
    FROM film AS f
    JOIN realisateur AS r ON f.id_real = r.id_real;
    ```

??? question "10. Afficher les titres des films dont le genre est « Drame » à l'aide d'une sous-requête."
    ```sql
    SELECT titre FROM film
    WHERE id_genre = (SELECT id_genre FROM genre WHERE libelle = 'Drame');
    ```

---

## À retenir absolument

!!! success "Définitions essentielles"
    - **table** = relation ; **tuple** = ligne ; **attribut** = colonne ;
    - **degré** = nb de colonnes ; **cardinalité** = nb de lignes ;
    - **clé primaire** identifie ; **clé étrangère** référence ;
    - **structure** (tables, clés) ≠ **contenu** (tuples) ;
    - une mauvaise modélisation se corrige en **séparant les tables**.

!!! abstract "Ordre des clauses SQL"
    `SELECT` → `FROM` → `JOIN … ON` → `WHERE` → `ORDER BY` → `LIMIT`

!!! note "Commandes à connaître"
    - **Structure** : `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE` ;
    - **Données** : `INSERT`, `UPDATE`, `DELETE` ;
    - **Interrogation** : `SELECT … FROM … WHERE`, `ORDER BY`, `DISTINCT`, `LIMIT` ;
    - **Liens** : `JOIN … ON`, sous-requêtes (`=`, `IN`) ;
    - **Agrégats** : `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`.

!!! quote "Formulations utiles au bac"
    - « `id_real` est une **clé étrangère** car elle référence la clé primaire de
      la table `realisateur`. »
    - « Cette table présente une **redondance**, car l'information `…` est répétée
      à chaque tuple. »
    - « On utilise une **jointure** car les données demandées sont réparties dans
      deux tables reliées par `…`. »
    - « La condition de jointure est `f.id_real = r.id_real`, qui relie la clé
      étrangère à la clé primaire correspondante. »