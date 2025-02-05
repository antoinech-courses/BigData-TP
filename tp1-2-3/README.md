Installations
---

# VS Code

Visual Studio Code (VS Code) est un éditeur de code source léger et gratuit, développé par Microsoft, qui supporte de nombreux langages de programmation. Il offre des fonctionnalités comme l'autocomplétion, le débogage, et l'intégration de contrôles de version via des extensions, pour faciliter le développement. Nous allons utiliser cet IDE dans les TP. 
Installer [Vscode](https://code.visualstudio.com/download)

Lancez Vscode, puis installez les plugins(extensions) suivants en allant dans le menu extensions (menu View > Extensions) : 
- Docker (pas obligatoire)
- Python
- Jupyter

# Installation Docker

Docker est une plateforme qui permet de créer, déployer et exécuter des applications dans des conteneurs légers et isolés. Ces conteneurs incluent tout ce dont une application a besoin pour fonctionner, garantissant une portabilité et une cohérence entre différents environnements. Nous allons nous en servir pour installer les modules nécessaires pour les TP, mais pas d'inquiétude : les commandes vous serons fournies.

Commencons par l'installation de Docker Desktop.
Docker Desktop est une application conviviale pour Windows et MacOS, offrant une interface graphique pour simplifier la gestion des conteneurs Docker. Elle inclut Docker Engine, Docker Compose, et des outils de développement, facilitant ainsi le déploiement, la gestion et le suivi des conteneurs localement, tout en intégrant des fonctionnalités comme le partage de ressources et le réseau.

Aller sur [le site de Docker Desktop](https://www.docker.com/products/docker-desktop/) et télécharger la version correspondant à votre OS.
Lancer l'installation en gardant les paramètres par défaut, mais attention à l'espace disque disponible, nous aurons besoin de 5 à 10 Go!

# Lancement des conteneurs

Maintenant que VS Code et Docker Desktop sont installés. Nous allons commencer par exécuter des conteneurs pour MySQL et un serveur Jupyter. Il est recommandé de lancer la commande dans un terminal de Vscode. Dans VS Code, cliquer sur le menu Terminal, et ensuite sur "New Terminal" pour en créer un nouveau dans la fenêtre du bas.

Lancer les commandes suivantes : 

```bash
# Lancer un conteneur avec 
docker compose build
docker compose up
```