NoSQL JSON & MongoDB
---

Nous allons travailler sur une nouvelle base de données de test qui contient des données JSON: `world_x-db` présente dans le répertoire du TP3.

```
sudo docker cp ./world_x-db/world_x.sql tp1-2-3-some-mysql-1:/tmp/
sudo docker exec -it tp1-2-3-some-mysql-1 mysql -u root -p
```

```
mysql > source /tmp/world_x.sql
```

Faites les exercices du fichier "tp3.ipynb" présent dans le projet.








