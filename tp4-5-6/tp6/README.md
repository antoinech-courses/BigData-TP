# Spark Streaming 

## Requête du cours 

Vous aurez à retirer les modules Docker des précédents TP. Vous pouvez le faire avec la commande `docker compose down` dans les répertoires appropriés ou en vous servant du plugin Docker de VsCode.

## Ensemble de données

L'archive disponible sur Moodle contient un ensemble d'articles du journal Le Monde publiés depuis 2016 (les noms de fichiers commencent par la date de parution papier de l'article sous la forme "YYMMdd").

## Calcul des mots les plus fréquents en batch

Pour travailler sur la requête, on va commencer en batch en reprenant le schéma général du TP précédent dans un objet WordCount (qui crée une session Spark) :
- lire dans un bloc de données lines les données d'un des fichiers, par exemple, allData/160109-histoire.txt (comme son extension l'indique, il s'agit d'un fichier au format text) ;
- transformer ces lignes en des mots ;
- à l'aide d'une agrégation (groupBy().count()) et d'un tri, calculer une table des mots et de leur compte en rangeant les mots les plus fréquents en premier.

Dans un deuxième temps, modifier la requête afin de ne sélectionner que les mots de longueur supérieure ou égale à 6.

## Calcul des mots les plus fréquents en micro-batch

Il s'agit maintenant de reprendre la requête précédente pour l'appliquer incrémentalement à tous les fichiers du répertoire data (initialement vide).

Définir un nouvel objet StreamingWordCount et reprendre les 5 "étapes pour définir une requête" :

- définir la source : le répertoire data avec des fichiers au format text ;
- transformer les données : is suffit de reprendre la requête précédente ;
- définir la sortie et son mode : on utilise la console. Il est possible d'augmenter le nombre de lignes affichées en utilisant l'option "numRows" dont la valeur est bien sûr le nombre de lignes que l'on veut afficher ;
- préciser les détails de traitement : on utilise le déclenchement par défaut, avec un répertoire de reprise "checkpoint" à la racine du projet ;
- démarrer la requête.

Il faut ensuite "donner à manger" à la requête. Pour cela, il suffit de copier, petit à petit pour observer l'incrémentalité du calcul, des fichiers du répertoire allData au répertoire data.

Une manière simple de faire est de se placer dans un shell à la racine du projet, puis de copier les fichiers d'un répertoire à l'autre année par année (en attendant que des premiers résultats aient été produits avant de passer à l'année suivante). Pour cela, servez-vous du notebook [tp-files-init.ipynb](tp-files-init.ipynb) dont le but est de copier dans Minio les fichiers à étudier (10 par 10). N'hésitez pas à stopper le traitement et utiliser la cellule de remise à zéro pour la mise au point.

...

Pour mémoire :

- réexécuter le programme depuis le départ demande d'effacer le répertoire qui stocke le point de reprise, sinon l'exécution reprend de ce point de reprise. Utilisez la cellule correspondante dans le notebook [tp-files-init.ipynb](tp-files-init.ipynb).
- il est possible de visualiser des détails concernant l'exécution via http://localhost:4040/ (il n'y a pas de rafraîchissement automatique).

### Variations

Il est possible d'affiner le filtrage. Etendez la requête :

- en considérant un ensemble de mot exclus val excludedWords = Set("quelques", "toujours", ...) et en ne gardant les mots word qui n'appartiennent pas à cet ensemble donc tels que ! excludedWords.contains(word) ;
- en considérant des mots de plus de 7 lettres ;
- en effacant les signes de ponctuation en fin de mot.

## Exercice supplémentaire

De nombreuses API REST sont disponibles dans le cadre de l'OpenData. L'[API TAN/Naolib](https://open.tan.fr/doc/openapi) en est un bon exemple.
- Préparez un job de streaming récupérant les prochains passages à l'arrêt Chantrerie-Grandes Ecoles, et calculant et affichant la durée entre les deux prochains bus C6 (direction Hermeland). Le code de l'arrêt Chantrerie-Grandes Ecoles est "CTRE".
Conseil: utilisez Minio pour et traiter les fichiers JSON de l'API.