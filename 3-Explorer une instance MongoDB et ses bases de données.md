# 1.Explorer une instance MongoDB et ses bases de données

- Dans ce workshop, vous allez créer une base de données MongoDB et l'optimiser en utilisant des index, à la fois au moyen du shell Mongo Shell et de l'interface graphique MongoDB Compass, tout en apprenant les bases des bases de données documents NoSQL.
- NoSQL signifie "Not Only SQL", SQL étant le langage commun utilisé pour piloter les bases de données relationnelles traditionnelles. 

- Il n'existe pas de solution unique qui soit parfaite pour tous les contextes. L'utilisation de bases de données NoSQL présente donc des avantages, mais aussi des inconvénients par rapport aux bases de données relationnelles. 

- Pour donner un bref aperçu, les bases de données NoSQL sacrifient certaines caractéristiques des bases de données relationnelles, telles qu'une structure bien définie et des relations strictes entre les entités, afin d'obtenir une mise à l'échelle et une réplication meilleures et plus faciles, afin de traiter de grandes quantités de données, tout en étant généralement plus flexibles, moins chères et plus faciles à gérer. 

- MongoDB est spécifiquement une base de données documentaire, qui n'est qu'un type de SGBD NoSQL. (les autres étant les bases de données clé/valeur, colonne, graphe et encaissement). Comme toute chose en ingénierie, il n'y a pas de meilleure ou de pire solution absolue, mais il y a toujours un compromis à faire, selon le contexte. Il n'est pas rare que les applications modernes utilisent plus d'un type de base de données. 

- Ainsi, dans cette première tâche, nous allons avoir un aperçu rapide de MongoDB en exécutant nos premières commandes pour explorer, voir notre premier document et ensuite créer notre première base de données.

* En utilisant la commande "show dbs", nous pouvons jeter un coup d'œil à la liste des bases de données présentes dans cette instance. 

```
show dbs
```
* Pour éxecuter : cliquer sur cette icone :

![image](https://user-images.githubusercontent.com/123749462/225691990-116048a7-1bc4-46cc-8860-940f4704585e.png)

- Puis cliquer sur Yes :

![image](https://user-images.githubusercontent.com/123749462/225692152-4b9389df-4fc1-4c94-be8b-24fe4c67a682.png)


![image](https://user-images.githubusercontent.com/123749462/225690916-3dc62698-bd9a-43da-b884-a1dd238c0325.png)

Comme vous pouvez le voir, il y a deux bases de données déjà créées par défaut. Elles sont utilisées par MongoDB lui-même pour stocker les utilisateurs, la configuration et d'autres données.

* En tant que débutants, nous ne sommes pas vraiment concernés par ces bases, mais puisqu'elles sont là et que nous sommes curieux, il n'y a aucun mal à y jeter un coup d'œil. Par exemple, voyons ce qu'il y a dans la BDD admin.

```
use admin
```
