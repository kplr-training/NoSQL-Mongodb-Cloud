# 4. Créer un document pour une collection d'articles de blog 


* Dans cette tâche, nous allons créer notre premier document.
- commençons notre premier document. Pour ce projet, nous voulons stocker des articles de blog:

* Créons une base de données pour notre blog. 

```
use blog
```

![image](https://user-images.githubusercontent.com/123749462/225769527-1e739f91-19d0-4362-a881-48d790e6764f.png)


* Maintenant nous allons utiliser la méthode insert() pour une collection de billets. Comme cette collection n'existe pas, MongoDB va la créer pour nous:

```js
db.posts.insert({
	title: 'MongoDB rules',
	body: 'My First MongoDB document',
	date: ISODate('2023-03-30T18:30:00Z'),
	tags: ['mongodb', 'databases'],
	likes: 2,
	author: {
		name: 'Douaâ',
		surname: 'Hayel'
	},
	location: {
		type: 'Point',
		coordinates: [-112.45, 37.76]
	}
})
```

![image](https://user-images.githubusercontent.com/123749462/225769774-db5df6dc-135e-4adc-93f8-17e83ab4ab8c.png)

* Retrouvons le document:
```
db.posts.find()
```

![image](https://user-images.githubusercontent.com/123749462/225770880-066c3686-7b11-41f7-b9c4-eab94fad3a39.png)

- Comme vous pouvez le voir, MongoDB a ajouté un champ pour nous, qui s'appelle `_id`. Il s'agit d'un identifiant unique de notre document. Si nous l'avions voulu, nous aurions pu passer outre en ajoutant un champ `_id` à notre propre document, lors de son insertion, avec une clé primaire qui aurait pu avoir un sens pour nous. 

Nous avons donc appris comment lancer notre premier document et certains des types de données que MongoDB gère, comme les chaînes de caractères, les tableaux de dates et les entiers, les documents intégrés et les GeoJSON. Donc, dans la prochaine tâche, nous allons commencer à interroger notre base de données et à mettre à jour les documents.

