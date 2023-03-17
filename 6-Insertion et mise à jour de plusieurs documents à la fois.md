# 6.Insertion et mise à jour de plusieurs documents à la fois

 Dans cette tâche, vous allez apprendre comment insérer et mettre à jour plusieurs documents à la fois. Il existe une commande shell, appelée `insertMany`, qui vous permet d'insérer plus d'un document à la fois. Cette commande accepte un tableau d'objets :
 
 ```js
 
db.posts.insertMany(
	[
		{
			title: 'Awsome Post',
			body: 'Body of Awsome Post',
			date: ISODate('2023-03-30T03:30:00Z')
		},
		{
			title: 'Awsome Post',
			body: 'Body of Awsome Post number 2',
			likes: 3,
			date: ISODate('2025-03-30T02:30:00Z'),
			location: {
				type: 'Point',
				coordinates: [-97,74, 30.27]
			}
		}
	]
	)
```

![image](https://user-images.githubusercontent.com/123749462/225780422-124846fa-cf8c-4013-9f26-53287b094f9e.png)
Comme vous pouvez le voir, MongoDB nous a confirmé que les deux documents ont été stockés.

Disons que nous voulons mettre à jour tous les articles de blog, avec un booléen `published`, pour determiner si l'article a été publié ou non.

```js
db.posts.update(
	{},
	{
		$set: {
			published: false
		}
	}
)
```
![image](https://user-images.githubusercontent.com/123749462/225781816-a34ec05b-0690-46ee-8940-c67cf9e1248d.png)

Comme vous pouvez le voir. Nous avons 4 documents dans notre base de données de blog, mais le writeResult ici dit qu'un seul a été trouvé et qu'un seul a été modifié. 

Que se passe-t-il ? C'est parce que la commande `update`, par défaut, met à jour un seul document. Dans ce cas, elle n'a mis à jour que le premier document qu'elle a trouvé. Pour savoir lequel, nous pouvons rechercher les documents qui contiennent effectivement ce champ : nous pouvons le faire en utilisant l'opérateur `$exists`:

```js
db.posts.find(
		{
			published: {
				$exists: true
			}
		}
	).pretty()
```

![image](https://user-images.githubusercontent.com/123749462/225782007-250ded34-dcb0-4515-962a-fe94c7b726b6.png)

Maintenant, nous aimerions réparer cela. Nous voulons mettre à jour tous les documents en même temps. Pour ce faire, nous devons spécifier des options pour notre méthode de mise à jour. 
```js
db.posts.update(
	{},
	{
		$set: {
			published: false
		}
	},
	{multi: true}
)
```
![image](https://user-images.githubusercontent.com/123749462/225782169-42f290a4-4f42-484d-a926-77891d5d4c3b.png)

- Maintenant c'est beaucoup mieux. Il dit qu'il a fait correspondre 4 documents, et qu'il a modifié 3 documents. C'est parce que, bien sûr, l'un de nos documents avait déjà le champ publié à false.

* Retrouver nos deux postes portant le même titre :
```
db.posts.find({title: 'Awsome Post'})
```
![image](https://user-images.githubusercontent.com/123749462/225782348-c52a66b1-9e9f-4156-ae24-5bc46d249401.png)

* Trouver le seul article qui a le champ "likes":
```js
db.posts.find(
		{
			$and: [
				{
					title: 'Awsome Post'
				},
				{
					likes: {
						$exists: true
					}
				}
			]
		}
	)
```
![image](https://user-images.githubusercontent.com/123749462/225782488-af9abd7b-3384-462a-9e06-14b2a4d59de0.png)

Seul le document avec le titre "Awesome Post" et le champ likes présent a été trouvé et renvoyé. 

Félicitations ! Vous avez appris à insérer et à mettre à jour plus d'un document à la fois. Vous avez également appris à rechercher l'existence d'un champ.


