---
title: SQL
description: 
published: true
date: 2024-05-21T15:07:06.384Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:07:06.384Z
---

# SQL

## La structure

### Les types de données

Il existe différents types de données en SQL, qui dépendent du type de SGBD (Système de Gestion de Base de Données).

Pour le SGBD Microsoft SQL Server :

| Types | Description |
|--|---
| `CHAR(x)` et `NCHAR(x)` | Chaine de caractère de longueur fix de taille `x` |
| `VARCHAR(x)` et `NVARCHAR(x)` | chaine de caractère ayant une taille allant jusqu'à `x`. On peut remplacer `x` par `max` pour de long texte. |
| `BIT` | Valeur que `0` et `1`. Utile pour simuler les booleans |
| `TINYINT` | Valeur de `0` à `255` (*1 octet*)|
| `SMALLINT` | Valeur de -2<sup>15</sup> (`-32,768`) à 2<sup>15</sup>-1 (`32,767`) (*2 octets*) |
| `INT` | Valeur de -2<sup>31</sup> (`-2,147,483,648`) à 2<sup>31</sup>-1 (`2,147,483,647`) (*4 octets*) |
| `BIGINT` | Valeur de -2<sup>63</sup> (`-9,223,372,036,854,775,808`) à 2<sup>63</sup>-1 (`-263 (-9,223,372,036,854,775,808) to 263-1 (9,223,372,036,854,775,807)`) (*8 octets*) |
| `DATE` | Date en format `YYYY-MM-DD` |
| `TIME` | Date en format `hh:mm:ss` |
| `DATETIME` | Date en format `YYYY-MM-DD hh:mm:ss` |
| `FLOAT(x)` | Nombre decimal non précis, **x** pour définir la taille de ce nombre |
| `DECIMAL(x, y)` | Nombre decimal, **x** pour le nombre de chiffres total et **y** pour le nombre de chiffres après la virgule |
| `MONEY`| Pas assez précis, il vaut mieux utiliser `DECIMAL` |

#### Convertir une date dans un certain format

On peut utiliser la fonction `FORMAT` :
```sql
SELECT FORMAT(nom_colonne_date, 'MMM/yyyy');
```

#### Cast

```sql
CAST('1950-10-23' AS DATE);
```

### Création de la base de donnée

```sql
CREATE DATABASE db_nom_base_donnee;
```

Ensuite il faudra préciser sur quel base de donnée les commandes suivantes devront être executé :

```sql
-- Création de la base de donnée
CREATE DATABASE db_test;

-- On précise que l'on veut executer les prochaines requêtes sur cette base de donnée
USE db_test;
```

### Création de tables

Lors de la création des tables, on doit également définir les différentes colonnes qui définissents toutes les données qui y seront stockés.

```sql
CREATE TABLE nom_table(
  table_id INT NOT NULL UNIQUE,
  avion_id TINYINT NOT NULL,
  pilote_id TINYINT NOT NULL,
  du_text VARCHAR(150) NULL,
  description NVARCHAR(32) NOT NULL DEFAULT 'Description par défaut.',
  nombre_positif SMALLINT NOT NULL CHECK (nombre_positif >= 0),
  code_securite_social CHAR(13) NOT NULL UNIQUE
);
```

On doit définir obligatoirement une clée primaire par table, mais une clée primaire peut être définir avec plusieurs colonnes.

Pour ce faire on défini une contrainte de type clée primaire :

```sql
CREATE TABLE ma_table(
  table_id INT IDENTITY;
  -- ...
  CONSTRAINT PK_tables_id PRIMARY KEY (table_id)
);
```

On peut également définir des vérifications pour obliger ou interdir l'ajout de certaines données :

```sql
CREATE TABLE ma_table(
  -- ...
  age INT NOT NULL CHECK (age >= 18),
  -- ...
);

Ces vérifications peuvent également être défini avec des contraintes.

#### Les contraintes

##### Clés primaires
```sql
CREATE TABLE mes_tables(
  table_id INT IDENTITY;
  -- ...
  CONSTRAINT PK_tables_id PRIMARY KEY (table_id)
);
```

Pour définir une clé primaire sur plusieurs colonnes :

```sql
CREATE TABLE mes_tables(
  table_premier_id INT IDENTITY;
  table_deuxieme_id VARCHAR NOT NULL UNIQUE;
  table_troisieme_id INT NOT NULL UNIQUE;
  -- ...
  CONSTRAINT PK_tables_id_multiple PRIMARY KEY (table_premier_id, table_deuxieme_id, table_troisieme_id)
);
```

##### Clés étrangère

```sql
CREATE TABLE clients(
  client_id INT IDENTITY,
  client_first_name NVARCHAR(32) NOT NULL,
  -- ...*
  CONSTRAINT PK_clients_id PRIMARY KEY (client_id)
);

CREATE TABLE transactions(
  transaction_id INT IDENTITY,
  transaction_client_id INT NOT NULL,
  -- ...
  CONSTRAINT FK_transactions_clients_id FOREIGN KEY transaction_client_id REFERENCES clients(client_id)
);

-- Pour ajouter une clée secondaire à une table existante
ALTER TABLE transactions ADD CONSTRAINT FK_transactions_clients_id FOREIGN KEY transactions_client_id REFERENCES clients(cllient_id); 
```

###### Suppression / mise à jour en cascades

Quand plusieurs clés étrangère, impossiblité supprimer data quand dépendances,

Ajout cascade, quand supprime clé primaire data, on supprime la clé étrangère

```sql
-- Pour supprimer la clé primaire avec la clé étrangere
CONSTRAINT FK_toto FOREIGN KEY (attribut_mgr) REFERENCES emp(empno)
  ON DELETE CASCADE;
-- Pour modifier en même temps la clée étrangére en même temps que la clée primaire
CONSTRAINT FK_toto FOREIGN KEY (attribut_mgr) REFERENCES emp(empno)
  ON UPDATE CASCADE;
```

### Modification de tables

#### Ajout de colonnes

```sql
ALTER TABLE table_existante ADD nom_colonne NVARCHAR(16) NULL;
```

#### Suppression de colonnes

```sql
ALTER TABLE table_existante DROP COLUMN nom_colonne_a_supprimer;
```

#### Modification d'une colonne

Il faut faire attention lors de la modification d'une colonne, par exemple si vous obliger après coup des valeurs non `null`, il vous faudra également modifier toutes les lignes comportant la valeur `null`.

```sql
ALTER TABLE ma_table ALTER COLUMN nom_colonne_a_modifier SMALLINT NULL;
```

Pour modifier l'ensemble des colonnes de valeur `null` avant modification :

```sql
-- On remplace toutes les valeurs null par la valeur 'quelque chose'
UPDATE ma_table SET colonne_a_modifier='quelque chose' WHERE colonne_a_modifier IS NULL;

-- On peut ensuite rajouter l'obligation de données pour cette colonne
ALTER TABLE ma_table ALTER COLUMN colonne_a_modifier NVARCHAR(16) NOT NULL;
```

## Les données

### Ajout de données

```sql
INSERT INTO ma_table(table_id, autre_colonne_char_3, colonne_varchar) VALUES
   (1, 'abc', 'un exemple'),
   (2, 'cba', 'un autre exemple'),
   (3, 'xyz', 'dernier exemple');
```

### Suppression de données

```sql
DELETE FROM ma_table
	WHERE id = 1;
```

### Modification de données

```sql
-- Changer des valeurs de données à partir d'une condition
UPDATE nom_table SET colonne_id = 15, colonne_text = N'toto' WHERE colonne_id = 14;

-- Changer toutes les données de la table
UPDATE nom_table SET colonne_text = N'tata';
```

### Selection de données

```sql
SELECT nom_colonne1, nom_colonne2 FROM nom_table AS alias_table;
```

Si on ne veut qu'une seul occurence de données pour la colonne selectionné, on peut utiliser `DISTINCT` :

```sql
SELECT DISTINCT nom_colonne FROM nom_table AS alias_table;
```

Si on veut exclure de la requête le résultat d'une autre requête, on peut utiliser `EXCEPT` :

```sql
SELECT address FROM table1
	EXCEPT
	SELECT address FROM table2 -- On retire les adresses de table2 du resultat 
```

#### Conditionner la selection

```sql
SELECT colonne1, colonne2 FROM ma_table
	WHERE -- différentes confitions...
    ;
    
SELECT colonne1, colonne2 FROM ma_table
	WHERE colonne1 = 'toto' AND colonne2 IN ('tata', 'titi');
```

Quelques possibilités pour définir la condition de selection :

```sql
-- Chaque ligne à partir du WHERE correspond à un type de conditions ou mot clé. 
SELECT colonne1, colonne2 FROM ma_table
	WHERE colonne1 = 'abc' 
          colonne1 = 1
          colonne1 == 1 OR colonne1 >= 10 OR colonne1 <= 15 OR colonne1 <> 13
          colonne1 IN (1, 2, 4)
          colonne1 BETWEEN 2 AND 4
          colonne1 LIKE 'a%' -- tous les string commençant par "a" suivi d'1 ou plusieurs lettres
          colonne1 LIKE 'a_' -- tous les string commençant par "a" suivi d'1 seul lettre
```

| Mot clés | Description
|---|---
| IN | Pour tester sur plusieurs données
| BETWEEN | Pour tester si une valeur est entre deux valeurs
| LIKE | Pour tester si la valeur correspond au motif de recherche. `%` pour 0, 1 ou plusieurs charactères remplacés, `_` pour 0 ou 1 caractère remplacé.

#### Agrégation (regroupement) de données

On peut vouloir réaliser une selection de donnée en les regroupants. Par exemple on peut vouloir récupérer la moyenne d'un ensemble de donnés, le maximum, etc.

Dans le cas de la selection de plusieurs colonnes, il vous faudra regrouper les données non regroupé par le mot clé `GROUP BY`.

```sql
SELECT AVG(colonne1) AS average_colonne1, colonne2 FROM ma_table
	GROUP BY colonne2;
```

Lorsque l'ont veut réaliser des tries dans une agrégation de données, on ne peut plus utiliser `WHERE`, il faut utiliser à la place le mot clé `HAVING`.

```sql
SELECT AVG(colonne1) AS average_colonne1 FROM ma_table
	HAVING average_colonne1 > 15;
```

Mots clés disponible pour l'agrégation de données :

| Mot clé | Description
|---|---
| `MIN(colonne)` | Selectionner le minimum
| `MAX(colonne)` | Selectionner le maximum
| `COUNT(colonne)` | Retourne le nombre de données différentes disponible de la colonne. `COUNT(*)` renvoie le nombre de données dans la table
 | `AVG(colonne)` | Renvoie la moyenne de l'ensemble des données de la colonne
 | `SUM(colonne)` | Renvoie la somme de toutes les données de la colonne


#### Jointures

Elles permettent de regrouper les tables lors de la selection grace aux clés étrangéres et leur clés primaires.

Il existe 5 jointures :

| Nom | Quelles données selectionnées | Représentation
|---|---|---
| `INNER JOIN` | Celles dans les 2 tables | [![Réprésentation jointure INNER JOIN](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/aIXkJPplev073tr2-inner-join.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/aIXkJPplev073tr2-inner-join.png)
| `LEFT JOIN` | Celles de la première table avec les données de la deuxième table relié à elle | [![LEFT_JOIN.png](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/STENra0qADzqZ4br-left-join.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/STENra0qADzqZ4br-left-join.png)
| `RIGHT JOIN` | Celles de la deuxième table avec les données de la première table relié à elle | [![RIGHT_JOIN.png](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/s0h0MT79GPTOe9Ny-right-join.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/s0h0MT79GPTOe9Ny-right-join.png)
| `FULL OUTER JOIN` | Toutes les données des deux tables | [![FULL_OUTER_JOIN.png](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/K8fDqUjWBzlutJBL-full-outer-join.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/K8fDqUjWBzlutJBL-full-outer-join.png)
| `CROSS JOIN` | On relie chacune des données à toutes les données de l'autre table, dans les deux tables

Représentation graphique de quelques jointures :
 [![Visual_SQL_JOINS_orig.jpg](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/0fQJmiHlk0qdK1qG-visual-sql-joins-orig.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/0fQJmiHlk0qdK1qG-visual-sql-joins-orig.jpg)

```sql
-- On selectionne le nom et la ville de chaque personnes
SELECT personnes.nom, adresses.ville FROM peronnes
	INNER JOIN adresses ON personnes.id_adresse = adresses.id;
```

## Autres

### Diagnostiquer une base de donnée existantes

#### Voir les différentes données possible d'un champ

```sql
select distinct MON_CHAMP from MA_TABLE;
```

### Les variables

Pour l'utilisation de variable pour par exemple stocker le résultat de calculs.

```sql
-- Initialisation de la variable
DECLARE @ma_variable NVARVHAR(25);

-- Enregistrer du contenu dans la variable
SET @ma_variable = 'toto';
SET @ma_variable = 'tata';

-- Afficher le contenu de la variable
SELECT @ma_variable
-- ou
PRINT @ma_variable
```

### Les procedures stockées

Le nom de la procédure : commence en `sp_` pour celle de Microsoft SQL.

Comment exécuter une procédure :

```sql
EXEC sp_rename PARAMS
EXEC sp_rename 'employee', 'nouveau_nom_employee';
```

Exemple de création d'une procédure :

```sql
CREATE PROCEDURE afficher_employe @nom_employe VARCHAR(50) AS
  SELECT ename, sal, job, mgr FROM emp
  WHERE ename = @nom_employe;

EXEC afficher_employe 'KING';
```

Attention : **NE PAS UTILISER "SP" en début du nom de la procédure car réservé à Microsoft SQL Server**

### Les trigger

- DML (Data manipulation language) trigger : DML events are INSERT, UPDATE, or DELETE statements on a table or view. DML triggers execute when a user tries to modify data through a data manipulation language (DML) event.
- DDL (Data definition language) Trigger :

#### Trigger DML

<https://www.sqlservertutorial.net/sql-server-triggers/sql-server-create-trigger/>

```sql
CREATE TRIGGER [schema_name.] trigger_name
ON {table_name | view_name }
AFTER  {[INSERT],[UPDATE],[DELETE]}
[NOT FOR REPLICATION]
AS
	{sql_statements}
```

Exemple de trigger:

```sql
CREATE TRIGGER client_date_ajout_avant_today
	ON clients
	AFTER INSERT, UPDATE
	AS
    BEGIN
    	-- On va réaliser l'action si la date d'ajout est supérieur à la date d'ajourd'hui
    	IF (inserted.date_ajout > GETDATE()) 
        BEGIN
        	ROLLBACK TRANSACTION -- Annulation de la requête
        	PRINT('La date d\'ajout ne peut être plus récent que la date de maintenant')
        END
    END
GO;
```

Pour l'ensemble des événements tels que l'ajout (INSERT), la modification (UPDATE) et la suppression (DELETE) de donnée, nous pouvons accéder à une table virtuelle qui va contenir la modification en cours / qui intérviendra :

| Operation | Table ***deleted*** | Table ***inserted***
|---|---|---
| INSERT | *NON APPLICABLE* | Contient la ligne qui sera inséré
| DELETE | Contient la ligne qui sera supprimé | *NON APPLICABLE*
| UPDATE | Contient l'ancienne ligne, avant application de l'UPDATE | Contient la nouvelle ligne après application de l'UPDATE

<https://www.sqlservertutorial.net/sql-server-triggers/sql-server-instead-of-trigger/>

```sql
CREATE TRIGGER [schema_name.] trigger_name
ON {table_name | view_name }
INSTEAD OF {[INSERT] [,] [UPDATE] [,] [DELETE] }
AS
	{sql_statements}
```

Voici un exemple d'unb trigger DML pour une base de donnée d'une banque : Lorsqu'on réalise une transaction, on vérifie que l'utilisateur a assez d'argent sur son compte.

#### Trigger DDL

<https://www.sqlservertutorial.net/sql-server-triggers/sql-server-ddl-trigger/>

```sql
CREATE TRIGGER trigger_name
ON { DATABASE | ALL SERVER}
[WITH ddl_trigger_option]
FOR {event_type | event_group }
AS
	{sql_statement}
```

```sql
CREATE TRIGGER trigger_product
ON product
AFTER INSERT, DELETE
AS
BEGIN
	
```

### Quelques commandes intéréssantes

#### Annuler la requête SQL (utile pour les trigger)

```sql
CREATE OR ALTER TRIGGER nom_trigger ON nom_table
AFTER INSERT, UPDATE, DELETE,
AS
BEGIN
	IF (@une_valeur IS NOT NULL)
    BEGIN
    	ROLLBACK TRANSACTION -- On annule la requête
        PRINT('On annule la requête')
    END
END
GO
```

#### Echapper le caractère `'`

Lorsqu'on veut utiliser un guillemet, on peut l'échapper avec un autre guillemet :

```sql
PRINT('Vous n''avez pas terminé');
-- Va afficher "Vous n'avez pas terminé"
```
