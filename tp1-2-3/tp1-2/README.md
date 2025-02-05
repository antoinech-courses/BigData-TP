SQL
---

# TP1 Tests de base

## MySQL

Vous pouvez vérifier dans le plugin Docker de Vscode sur la gauche dans la liste des conteneurs et y retrouver un conteneur `mysql` et un conteneur `jupyter` actifs (avec le triangle vert à côté). Une fois votre nouveau conteneur démarré, nous allons nous connect au client mysql natif présent dans le conteneur. Ce dernier est en ligne de commandes.

```bash
# Executer le client local, avec comme mot de passe rootpwd. Remplacez le nom du conteneur si nécessaire
docker exec -it tp1-some-mysql-1 mysql -u root -p
```

Normalement vous devriez avoir accès au client, avec une ligne indiquant `mysql>`. Nous allons tester quelques commandes, pour vérifier si tout va bien.

```sql 
show databases;
```
Vous devriez obtenir ce rendu :
```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

Essayez de créer une nouvelle base de données.
```sql
create database if not exists test;
show databases;
```
Vous devriez obtenir ce rendu :
```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| test               |
+--------------------+
```

```sql
drop database if exists test;
show databases;
```

Il est également possible de lancer un terminal dans un conteneur avec le plugin Docker de Vscode. Faites le test.

## Base de données Sakila

Nous allons maintenant télécharger et tester la base de données Sakila.   
Sakila est une base de données d'exemple fournie par MySQL, conçue pour illustrer des concepts de gestion de bases de données. Elle contient des tables de films, d'acteurs et de locations, permettant de pratiquer des requêtes SQL dans un contexte réaliste.
Nous utiliserons cette base de données pour ce TP et le suivant. 

Allez télécharger la base de données [Sakila](https://downloads.mysql.com/docs/sakila-db.zip). Décompressez-là dans un endroit approprié (dans un dossier db dans ce projet par exemple).

Nous allons copier les fichiers script contenant le schéma et les données de cette base à l'intérieur du conteneur, afin de les charger dans la base.
Lancez un nouveau terminal dans le dossier contenant les fichiers SQL, puis, selon votre OS :

Windows.
```console
docker cp ..\sakila\sakila-data.sql tp1-some-mysql-1:/tmp/
docker cp ..\sakila\sakila-schema.sql tp1-some-mysql-1:/tmp/
```

Linux/Mac
```bash
docker cp ../sakila/sakila-data.sql tp1-some-mysql-1:/tmp/
docker cp ../sakila/sakila-schema.sql tp1-some-mysql-1:/tmp/
```

Vous pouvez ensuite réutiliser le terminal contenant le client MySQL. Si vous l'avez fermé ou ne le retrouvez pas, vous pouvez en ouvrir un nouveau facilement : 
```bash
docker exec -it tp1-some-mysql-1 mysql -u root -p
```

Lancez les commandes suivant pour charger la structures des tables et les données :
```sql
source /tmp/sakila-schema.sql
source /tmp/sakila-data.sql
show databases;
use sakila
show tables;
```

La liste des tables est fournie. Affichez les titres des 25 premiers films avec la requête suivante :  
```sql 
SELECT title FROM film LIMIT 25;
```

Voici ce que vous devriez obtenir :

```
+----------------------+
| title                |
+----------------------+
| ACADEMY DINOSAUR     |
| ACE GOLDFINGER       |
| ADAPTATION HOLES     |
| AFFAIR PREJUDICE     |
| AFRICAN EGG          |
| AGENT TRUMAN         |
| AIRPLANE SIERRA      |
| AIRPORT POLLOCK      |
| ALABAMA DEVIL        |
| ALADDIN CALENDAR     |
| ALAMO VIDEOTAPE      |
| ALASKA PHANTOM       |
| ALI FOREVER          |
| ALICE FANTASIA       |
| ALIEN CENTER         |
| ALLEY EVOLUTION      |
| ALONE TRIP           |
| ALTER VICTORY        |
| AMADEUS HOLY         |
| AMELIE HELLFIGHTERS  |
| AMERICAN CIRCUS      |
| AMISTAD MIDSUMMER    |
| ANACONDA CONFESSIONS |
| ANALYZE HOOSIERS     |
| ANGELS LIFE          |
+----------------------+
```

## Notebook Jupyter

**Le reste de l'énoncé se trouve dans le notebook Jupyter "tp1.ipynb" présent dans le projet.**

Vous allez utiliser un serveur Jupyter compris dans un conteneur : Vscode fournit une intégration quasi transparente.
Dans ce cas pas besoin d'installer les dépendances, tout est fourni dans une image Docker. 
Le désavantage est que la copie des fichiers est un peu plus complexe : le notebook n'est pas lancé dans l'environnement local.

Un point important est que vous devez avoir Python 3.12 d'installé dans le système hôte : si vous avez une version différente cela ne fonctionnera pas.

Vous n'avez pas besoin de `venv` ou de `conda`, mais vous aurez besoin de spécifier à Vscode que vous utilisez un serveur de notebook séparé. Nous allons utiliser celui déployé avec Docker Compose : cliquez sur "Select Kernel" (en haut à droite quand le notebook est sélectionné), "Select another kernel", "Existing Jupyter Server", "Enter the URL of the running Jupyter Server" (ou `localhost` si vous l'avez déjà créé), saisissez http://localhost:8888/lab, cliquez ensuite sur Yes, et indiquez comme nom `localhost`. Sélectionnez ensuite Python 3. 

Pour les Mac : si vous avez des soucis (SSL) et que vous ne trouvez pas de moyen de les régler, utilisez un navigateur. Dans ce cas, et si un serveur Jupyter a été lancé par Vscode, il peut être nécessaire de modifier le port exposé (par exemple par 8889) dans le fichier `docker-compose.yml`.


# TP2 SQL

## Extension VsCode "Database Client"

Afin d'avoir une meilleure visibilité sur la structure de la base de données, nous allons utiliser une extension pour cela.

Installer l'extension VsCode "Database client". Celle-ci permet de se connecter à différentes bases de données, SQL et NoSQL et nous sera utile pour l'ensemble des sources de données que nous utiliserons.
Créer une nouvelle connection à MySQL avec vos identifiants en cliquant sur le logo de base de données dans les extensions, puis le petit "+" en haut. On doit pouvoir laisser les valeurs par défaut à part le mot de passe utilisé pour la création du conteneur (root par défaut). Ne pas indiquer la base de données cible. 

## TP

**Le reste de l'énoncé se trouve dans le notebook Jupyter "tp2.ipynb" présent dans le projet.** 

N'oubliez pas que les requêtes doivent commencer par le "magic" `%%sql`. 

Afin d'éviter la limite du nombre de tuples affichés, vous pouvez entrer la commande suivante dans une cellule : `%config SqlMagic.displaylimit = None`. Vous pouvez également mettre une valeur à la place de `None`.
