
# Ingénierie des données graphes avec Neo4j, Spark et GraphFrames

## Prérequis

Pour cette séance, nous allons utiliser dans les deux types de configuration (Windows et Mac) le fichier `docker-compose-jupyter.yml` pour déployer les dépendances. Pour rappel, ce fichier déploie un serveur Jupyter aux côtés des modules au lieu d'utiliser celui du système hôte.

Commencez par construire les images Docker nécessaires pour le fonctionnement :
```bash
docker compose -f ./docker-compose-jupyter.yml build
```

Vous pouvez ensuite déployer l'ensemble des modules (et le serveur Jupyter) avec la commande suivante : 
```bash
docker compose -f ./docker-compose-jupyter.yml up -d
```

Pour les étudiants sous Windows, vous pouvez indiquer à VsCode d'utiliser le serveur Jupyter pour exécuter le code, ce qui rend les choses plus pratiques (le conteneur Jupyter peut directement discuter avec les conteneurs Spark et Neo4J): 
- dans un notebook, cliquez sur "Select Kernel" (en haut à droite).
- cliquez sur "Existing Jupyter Server"
- cliquez sur "Enter the URL of the running Jupyter server"
- Entrez l'adresse du serveur : "http://localhost:8888" 
- Gardez le nom par défaut
- Sélectionnez le kernel Python 3

Les étudiants sous Mac restent contraints d'utiliser le navigateur.

## Sujet du TP 

Ce sujet a pour but d'aborder les bases NoSQL orientées graphe (ici Neo4j), leurs langages de requête (ici Cypher), et leur intégration avec l'ecosystème bigdata (Spark).
Nous utiliserons le notebook [neo4j_data_engineering.ipynb](http://localhost:8888).
