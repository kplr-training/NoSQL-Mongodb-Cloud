# MongoDB Atlas Search

- MongoDB Atlas Search est un service de recherche intégré dans MongoDB Atlas, qui permet de rechercher des données dans les collections MongoDB de manière rapide et efficace en utilisant des requêtes de recherche complexes.

- MongoDB Atlas Search offre des fonctionnalités avancées telles que la recherche en texte intégral, la recherche géospatiale, la recherche par champ, la recherche par agrégation, la pondération des termes de recherche, la suggestion de termes de recherche et bien d'autres encore.

- Le service utilise des index de recherche, qui sont créés automatiquement en fonction des schémas de données de votre collection. Les index de recherche sont optimisés pour la vitesse de recherche et permettent de rechercher efficacement dans les collections MongoDB.

- MongoDB Atlas Search est particulièrement utile pour les applications qui nécessitent une recherche complexe et rapide de données. Le service est facile à configurer et à intégrer avec les applications, car il est intégré dans MongoDB Atlas. Il offre également une évolutivité horizontale et une haute disponibilité pour les applications en production.

# Créer un idex de recherche avec la collection listingsAndReviews de la base de donées sample_airbnb :

- Aller sur search :

![image](https://user-images.githubusercontent.com/123749462/226069383-10e305f2-32ae-4365-9194-34e36972a8c3.png)

- Cliquer sur Create Search Index :

![image](https://user-images.githubusercontent.com/123749462/226071736-a6cc2edb-bf86-4ec7-9b97-6a5e392adfa8.png)

- Cliquer sur Visual Editor > Next :

![image](https://user-images.githubusercontent.com/123749462/226072623-5e3af41a-64a2-4c2e-a976-948fe45fc2eb.png)

- Le Visual Editor est une interface graphique pour créer et modifier des index de recherche en utilisant une approche plus intuitive. 
- Les utilisateurs peuvent sélectionner les champs à inclure dans l'index, configurer les options de recherche et de tri, et visualiser les résultats en temps réel. 
- Le Visual Editor est plus convivial pour les utilisateurs moins expérimentés ou pour ceux qui préfèrent une approche visuelle.

- Donner un nom à votre index , choisir le nom de la database sample_airbnb et la collection listingAndReviews > Cliquer sur Next 

![image](https://user-images.githubusercontent.com/123749462/226072783-0bf0f68a-d83b-4ef7-8778-f49f80dc00fa.png)

- Cliquer sur Refine Your Index : 
![image](https://user-images.githubusercontent.com/123749462/226073464-d0398d71-a135-4712-ad86-2713ce301e4d.png)

![image](https://user-images.githubusercontent.com/123749462/226073593-db03e36b-1aa5-451b-814d-9ec145c90d28.png)

-Dans MongoDB Atlas Search, l'index analyzer "lucene.standard" est utilisé pour traiter le texte à indexer dans un moteur de recherche. Tout comme dans Lucene, l'analyseur transforme le texte en tokens ou termes qui sont ensuite indexés pour permettre des recherches rapides et précises. L'analyseur "lucene.standard" dans MongoDB Atlas Search inclut également la suppression des mots vides et la racinisation des termes.

- Le search analyzer "lucene.standard" est utilisé lors de la recherche dans MongoDB Atlas Search. Il effectue un traitement similaire à l'index analyzer, mais peut également inclure des stratégies de recherche telles que la normalisation des termes et l'expansion de requête.

- On va maintenant Configurez un champ spécifique (name) de votre collection à indexer > Add:

![image](https://user-images.githubusercontent.com/123749462/226074012-35582f9e-e9cd-49bf-9f39-743572d4ff53.png)

- Voilà ! Vous avez un premier name field mapping .
- Maintenant , on va créer un autre field mapping (summary) :

![image](https://user-images.githubusercontent.com/123749462/226074157-420594a0-b303-4bcb-ac1d-a9730f638f9c.png)

- Modifier lucene.standard et la remplacer par lucene.english > Cliquer sur Add :

![image](https://user-images.githubusercontent.com/123749462/226074260-e99c8c2e-a226-462d-ab60-471d29cd18ca.png)

![image](https://user-images.githubusercontent.com/123749462/226074304-a37e7eec-1e98-4eb8-b067-90929cb6db3a.png)

- Spécifier le champ "last_scraped" et le DATA Type : Date > Add :

![image](https://user-images.githubusercontent.com/123749462/226074436-77427b43-5d97-4bc0-badd-49ebe5847fdb.png)

- Cliquer sur Save changes :

![image](https://user-images.githubusercontent.com/123749462/226074524-5e086aea-569e-4428-b80f-a0a9c49723a4.png)

- Puis , cliquer sur Create Search Index :

![image](https://user-images.githubusercontent.com/123749462/226074545-5e6f95e5-9207-4c73-86bc-232ab7f1d9f7.png)

- Attendre  ce que notre search index passe du status NotStarted à Active

![image](https://user-images.githubusercontent.com/123749462/226074744-ffa02df5-0699-41d9-a884-44ad513fe905.png)

![image](https://user-images.githubusercontent.com/123749462/226074779-8f4d1f64-65d5-4f40-8b59-c454913940a6.png)

- Cliquer sur query :
![image](https://user-images.githubusercontent.com/123749462/226074916-331f8b93-19d3-48aa-857e-8ceeb7cadcc3.png)

-   Dans Search tester on peut rechercher des documents dans MongoDB Atlas Search :

![image](https://user-images.githubusercontent.com/123749462/226075247-b86771b0-853f-450d-9161-7c3ebbf00f2b.png)

- Par exemple si on veut chercher les document qui contient le mot PARIS il suffit de faire une recherche avec Search Tester :

![image](https://user-images.githubusercontent.com/123749462/226075378-46e03957-fb2d-4395-942e-8cf3f7f7756a.png)









