
# Spark Streaming (suite)

## Prérequis

Nous allons utiliser un nouveau docker-compose comprenant une installation de Kafka.

## Exemple 

[ThingSpeak](https://thingspeak.mathworks.com/) est une solution d'import de données Big Data pour Matlab. Elle propose sur son site un dépôt d'API REST JSON de streaming participatif et public. 

Le notebook [init-thingspeak-kafka.ipynb](init-thingspeak-kafka.ipynb) permet l'insertion dans Kafka des informations de l'API. Vous pouvez ensuite exécuter le notebook [thingspeak-wind.ipynb](thingspeak-wind.ipynb), qui illustre l'utilisation de Kafka et de fenêtres glissantes.