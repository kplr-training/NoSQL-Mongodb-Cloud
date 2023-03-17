# 5.Requêtes et mise à jour de documents

## 3.1. Requêtes

Dans cette tâche, nous allons commencer à interroger la base de données et apprendre à mettre à jour un document. 

* Ajoutons un deuxième document dans notre collection posts:

```js
db.posts.insert({
	likes: 5,
	title: 'Second Post',
	author: {
		name: 'Zineb',
		surname: 'Zannouti'
	},
	body: 'Body of our second post',
	date: ISODate('2023-03-30T03:00:00Z')
})
```

![image](https://user-images.githubusercontent.com/123749462/225776627-08441dd3-e21f-40ad-938e-a0873d37d039.png)

* Vérifier le document:
```
db.posts.find().pretty()
```

![image](https://user-images.githubusercontent.com/123749462/225777012-25b8e2fc-89e0-478a-be47-b48477f53a60.png)

- Comme vous pouvez le voir, nous avons maintenant les deux documents stockés. De plus, notre deuxième document n'a pas de *tags* ni de *location*. De plus, l'ordre des champs n'a pas d'importance. Ceci est dû au fait que MongoDB est *schema-less*. Cela signifie que nous n'avons pas eu à définir un schéma pour contraindre la forme de tout ce qui est stocké dans le système. Si vous êtes familier avec les bases de données relationnelles, cela peut sembler étrange. Cependant, c'est l'une des raisons pour lesquelles NoSQL est si puissant à l'échelle. 

* Maintenant, disons que nous voulons trouver notre deuxième article. Pour ce faire, nous pouvons utiliser la méthode `find()` et chercher par son titre. C'est ce qu'on appelle communément l'interrogation de la base de données. 

```
db.posts.find({title: 'Second Post'}).pretty()
```
![image](https://user-images.githubusercontent.com/123749462/225777222-38e83b60-f0d2-4196-bd2f-e22c0a265cdb.png)
* trouver tous les documents et ensuite les trier par le champ title dans l'ordre ascendant (-1 pour l'ordre descendant):
```
db.posts.find().sort({title: 1}).pretty()
```

![image](https://user-images.githubusercontent.com/123749462/225777799-d32ad4cc-f81e-482b-a453-5ada6c79f0f1.png)


* Trouver tous les posts qui ont plus de deux likes en utilisant `$gt` (greater than) 
```
db.posts.find({likes: {$gt: 2}}).pretty()
```
![image](https://user-images.githubusercontent.com/123749462/225778305-53302ac1-cd57-498d-bcdb-928da40851ad.png)

* Trouver tous les posts qui ont au moins deux likes en utilisant `$gte` (greater than or equal)
```
db.posts.find({likes: {$gte: 2}}).pretty()
```

* Trouver tous les posts qui ont au moins deux likes en utilisant `$gte` (greater than or equal) et les trier par ordre descendant des nombres de likes :
```
db.posts.find({likes: {$gte: 2}}).pretty().sort({like: -1}).pretty()
```
Nous pouvons également faire l'inverse, en utilisant les opérateurs " inférieur à " et " inférieur ou égal ", c'est-à-dire `$lt` ou `$lte`. Nous pouvons également rechercher une égalité en utilisant l'opérateur `$eq`, ou une inégalité en utilisant l'opérateur non égal, `$neq`...

Lisez : [Opérateurs Logiques et opérateurs de comparaison dans MongoDB](https://kinsta.com/fr/blog/operateurs-mongodb/)

## 3.2. Mise à jour de documents

Disons que nous voulons ajouter des `tags` et `location` à notre deuxième message. Pour ce faire, nous utilisons la méthode `update()` en lui passant 2 paramètres. Le premier indique le document à mettre à jour, et fonctionne de la même manière que la méthode `find()`. Le deuxième paramètre est soit un document complet, si vous voulez changer le document complètement, ou nous pouvons utiliser l'opérateur `$set`, pour dire à MongoDB que nous voulons mettre à jour ou ajouter des champs spécifiques.

```js

db.posts.update({
			title: 'Second Post'
		},
		{
			$set: {
				tags: ['tag1'],
				location: {
					type: 'Point',
					coordinates: [-73.97, 40.77]
				}
			}
		}
	)
```

![image](https://user-images.githubusercontent.com/123749462/225778633-c8894f61-d665-447e-81c7-6f38d3faca8e.png)


* Vérifier la mise à jour :
```
db.posts.find({title: 'Second Post'}).pretty()
```

![image](https://user-images.githubusercontent.com/123749462/225779462-2449feb1-a92f-4afd-9231-52dddb545524.png)
* Supprimer le champs `tags` dans `Second Post`

```js
db.posts.update({
			title: 'Second Post'
		},
		{
			$unset: {
				tags: ''
			}
		}
	)
```
* Vérifier la mise à jour :
```
db.posts.find({title: 'Second Post'}).pretty()
```
![image](https://user-images.githubusercontent.com/123749462/225779692-be949a30-fba4-4e9f-a404-8be5d1ab7db3.png)


Super ! Vous avez appris les bases de l'insertion et de la mise à jour de documents, ainsi que de l'interrogation et du tri. Dans les prochaines tâches, vous apprendrez à insérer et à mettre à jour plusieurs documents à la fois.
