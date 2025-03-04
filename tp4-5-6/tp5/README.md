# Spark SQL

Dans ce TP, nous utilisons les mêmes outils que dans le TP précédent (WSL ou le conteneur Jupyter dans Docker).

Le notebook [spark_sql.ipynb](spark_sql.ipynb) reprend les jobs vus en cours. Executez-les différentes cellules et observez les résultats obtenus. Vous aurez à retirer les modules Docker des précédents TP. Vous pouvez le faire avec la commande `docker compose down` dans les répertoires appropriés ou en vous servant du plugin Docker de VsCode.

Ensuite, répondez aux questions suivantes. Vous aurez besoin de créer un nouveau notebook.

## Ensemble de données

Le fichier [departuresdelay.csv.zip] comprend des données concernant des vols internes aux Etats-Unis (données extraites de https://catalog.data.gov).

Les données ont 5 colonnes :
- date : contient des chaînes comme 02190925, pour 02-19 09:25am ;
- delay : retard en minutes entre l'heure prévue et l'heure réelle de départ, des départs anticipés sont représentés par des nombres négatifs ;
- distance : la distance en miles entre aéroport de départ et d'arrivée ;
- origin et destination : les codes IATA des aéroports de départ et d'arrivée.

Décompressez le fichier `departuredelays.zip` et placez le fichier `departuredelays.csv` dans le conteneur Jupyter (utilisez la commande `docker cp departuredelays.csv jupyter:/departuredelays.csv` dans ce cas). Utilisez ensuite minio comme dans le TP précédent.

### Première requête

Combien de lignes a cette table ?

Répondre à la requête de deux manières :

- en utilisant une vue et une requête SQL sur cette vue ;
- en utilisant simplement l'API des blocs de données / DataFrames.

## Requêtes

Ecrire les requêtes suivantes des deux manières (cf transparents "DataFrames vs Views" et "Projection et sélection" du cours 6) :

- Quels sont les vols dont la distance est supérieure à 1000 miles ?
- Trier ces vols par ordre descendant. Voici un exemple de tri utilisant l'API où df est un bloc de données comportant une colonne id : df.sort(col("id").asc()).
- Quels sont les vols entre San Francisco (SFO) et Chicago (ORD) qui ont au moins deux heures de retard ?

## Puzzle

En utilisant l'API des blocs de données et les fonctions qui permettent de transformer des chaînes en dates, transformer la colonne date en un format lisible et déterminer quand ces retards sont les plus fréquents.