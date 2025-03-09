# Projet

L'objectif principal de ce projet est de permettre aux étudiants de développer des compétences pratiques dans la gestion et l'analyse de données massives. En choisissant une source de données parmi celles proposées, les étudiants - en groupe de 4 - devront mettre en oeuvre un pipeline complet, allant de la collecte à l’analyse et à la visualisation des résultats.

Choisissez parmi les sujets suivants :

## Sujets

- Mobilité : [API temps réel Naolib](https://data.nantesmetropole.fr/explore/dataset/244400404_api-temps-reel-tan/information/)
- Mobilité : [Plateform Régionale d'information pour la mobilité (Ile de France) ](https://prim.iledefrance-mobilites.fr/fr)
- Aviation : [OpenSkyNetwork API](https://openskynetwork.github.io/opensky-api/index.html)
- Réseaux sociaux : [Bluesky]([https://docs.bsky.app/docs/category/http-reference])
- Transports : [SNCF API Open-Data](https://numerique.sncf.com/startup/api/)
- Transports : [Here maps](https://developer.here.com/develop/rest-apis)

### Autres ?

Si vous souhaitez analyser une autre API, faites-moi une proposition par mail.

### Conseils

Attention aux limites d'utilisation (rate limit) : vérifiez bien celles de l'API que vous utilisez pour éviter d'être bloqués. N'hésitez pas à créer plusieurs comptes si nécessaire et évitez de consommer tous vos crédits trop vite.

## Consignes

Les groupes devront être compter 4 élèves (sauf si nombre impaire dans la promo). Pour ceux qui sont en difficulté avec les installations (problème de mémoire ou de puissance de leur machine), veillez bien à vous inclure dans un groupe n'ayant pas de soucis à ce niveau.

Vous devrez, à l'aide de Minio et Apache Spark pour l'une des APIs :
- effectuer des requêtes en mode streaming
- effectuer une requête en mode batch et présenter les résultats à l'aide de Pandas et Seaborn

Optionnel au choix :
- Utiliser Kafka pour faire du streaming sur la même ou une autre API (des slides et un TP sont disponibles sur Moodle et le repo de tp pour vous aider, il existe aussi beaucoup de ressources en ligne)
- Relier vos requêtes de streaming à un dashboard
- Mixer l'utilisation de plusieurs APIs pour obtenir des résultats plus intéressants
- Utiliser l'une des bases NoSQL présentée en tuto ou Neo4J au lieu de Minio (attention à choir une BD adaptée aux requêtes à effectuer et à la nature des données)

Pour Minio, comme pour Kafka, une première étape sera d'insérer les données. Vous pouvez prendre comme modèle les scripts des TPs respectifs.
Le dashboard pourra s'alimenter auprès de n'importe quelle source.

Les requêtes développées devront avoir du sens en regard des données : gardez à l'esprit que vous devrez préciser une synthèse des résultats obtenus et expliquer leur signification. Il faut donner de la VALEUR aux données.

## Critères d'évaluation approximatifs

Collecte des données (script d'initialisation dans Minio) : 20 %
Mise en oeuvre technique (jobs Spark) : 40 %
Analyse et conclusions : 30 %
Qualité de la présentation : 10 %

Bonus