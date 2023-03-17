# Comment créer un pipeline d'agrégation dans MongoDB Atlas :


- Aller sur Atlas MongoDB :
- Accéder au cluster qu'on a déjà créer : Deployment > Database > Cliquer sur Cluster0 :

![image](https://user-images.githubusercontent.com/123749462/225948624-186b4810-224e-40dd-ab38-f006e32b1ec0.png)

- Dans MongoDB Atlas, "Sample Dataset" fait référence à un ensemble de données fictives pré-remplies dans une base de données de test que vous pouvez utiliser pour explorer les fonctionnalités de MongoDB. Ce jeu de données est conçu pour montrer des exemples de schémas et de requêtes courantes que vous pouvez utiliser dans vos propres projets.

- Le Sample Dataset comprend plusieurs collections, chacune avec des données liées à un domaine spécifique. Par exemple, la collection "restaurants" contient des informations sur les restaurants, tels que leur nom, leur adresse et leur type de cuisine. La collection "airbnb" contient des informations sur les annonces de location sur Airbnb, telles que leur emplacement, leur prix et leur disponibilité.

- L'utilisation du Sample Dataset peut vous aider à comprendre comment structurer vos données, comment interroger les données à l'aide du langage de requête de MongoDB (MongoDB Query Language, ou MQL), et comment utiliser les fonctionnalités avancées de MongoDB, telles que les agrégations et les index.
- Pour utiliser Sample Dataset : Cliquer sur cette icone de trois point :

![image](https://user-images.githubusercontent.com/123749462/225950564-b4d0b8eb-283e-4dfb-8c44-0ddfd6c0ae20.png)

- Puis cliquer sur Load Sample Dataset .

![image](https://user-images.githubusercontent.com/123749462/225950859-af9f5d6f-e719-4727-91aa-fa521d65a8b5.png)

- Attendre jusqu'à la création du sample dataset .
- Pour pouvoir visualiser les databases qu'on a créé : 
- Allez sur Collections :

![image](https://user-images.githubusercontent.com/123749462/225951838-fcc125a8-700e-4626-9a18-2d36a134dd3e.png)

- Vous pouvez voir ici qu'on a créé 10 databases avec 24 collections : 

![image](https://user-images.githubusercontent.com/123749462/225952463-6b65aad3-6346-4609-a60c-ac6abfbd137c.png)

- Vous pouvez utiliser l'interface utilisateur Atlas pour traiter vos données en créant 
pipelines d'agrégation

# pipelines d'agrégation

- Les pipelines d'agrégation transforment vos documents en résultats agrégés en fonction des 
étapes du pipeline .

- Le générateur de pipeline d'agrégation Atlas est principalement conçu pour créer des pipelines, plutôt que de les exécuter.
- Dans MongoDB Atlas, l'onglet "Aggregations" permet d'effectuer des agrégations de données sur une collection MongoDB. Les agrégations sont des opérations avancées de traitement de données qui permettent de regrouper, de filtrer et de transformer les données dans une collection MongoDB.

- L'onglet Aggregations de MongoDB Atlas vous permet de créer des pipelines d'agrégation, qui sont des séquences d'étapes de traitement de données appliquées à une collection MongoDB. 
- Vous pouvez utiliser les pipelines d'agrégation pour effectuer des opérations telles que le filtrage de données, le tri, la mise en correspondance, la projection, le regroupement, la jointure et l'agrégation de données. Les pipelines d'agrégation sont créés à l'aide d'une syntaxe basée sur des opérateurs de pipeline MongoDB.

- L'onglet Aggregations de MongoDB Atlas offre une interface graphique conviviale pour créer, tester et exécuter des pipelines d'agrégation. 
- Sélectionner la collection movies de la base de donnée sample_mflix :

![image](https://user-images.githubusercontent.com/123749462/225972015-557acb05-b164-43ca-add1-badf2bf4b8c7.png)

- Aller sur Aggregation : 

![image](https://user-images.githubusercontent.com/123749462/225972485-6cabe038-a362-44a5-bf2b-c77a1d36d6a1.png)

![image](https://user-images.githubusercontent.com/123749462/225973340-300d8fbc-3b37-4d65-8e06-1111c68adb1c.png)

- Sélectionner $match : 

![image](https://user-images.githubusercontent.com/123749462/225973473-aae232bc-d0d6-4dd7-83b1-2d2af0c284c7.png)

![image](https://user-images.githubusercontent.com/123749462/225973923-c202cdab-703d-450e-94d9-49f7a03d837c.png)

- Ajouter à la place de query : 

```
cast : "Ryan Reynolds"

```
![image](https://user-images.githubusercontent.com/123749462/225975030-b1b566eb-52c3-4f1e-8089-4a37d4bd545b.png)

- Ajouter un autre stage avec $unwind 
- La fonction d'agrégation $unwind est une fonctionnalité de MongoDB qui permet de dérouler (ou "déplier") un tableau (ou une liste) contenue dans un document de la collection, créant ainsi une nouvelle copie de ce document pour chaque élément du tableau. 
- Cela permet de transformer une liste de valeurs en plusieurs documents, chacun contenant une seule valeur de cette liste.

![image](https://user-images.githubusercontent.com/123749462/225976999-47616fe9-560b-4b1d-a7b5-bc785e79ac7f.png)

![image](https://user-images.githubusercontent.com/123749462/225977755-2085a06b-1a09-4bd6-b7b0-9ab92741555b.png)

![image](https://user-images.githubusercontent.com/123749462/225978168-e35aea94-95cb-4b05-ac35-e2ccc1b2331c.png)


- Remplacer 
```
{
  path: path,
  includeArrayIndex: 'string',
  preserveNullAndEmptyArrays: boolean
}
```
- Par :
```
{
  path: "$cast"
}
```
![image](https://user-images.githubusercontent.com/123749462/225979337-2902f492-8111-4895-84b4-168a1db06b22.png)

- Ajouter un nouveau stage avec add stage :
- Avec la fonction d'aggregation $match 
- Le deuxième $match avec la condition "cast: 'ryan reynolds'" est utilisé pour filtrer à nouveau les documents, cette fois-ci en recherchant ceux qui ont "Ryan Reynolds" dans leur liste de casting individuelle (et non dans leur liste de casting globale). 
- Cela permet de trouver tous les documents qui ont "Ryan Reynolds" comme acteur principal, plutôt que comme l'un des nombreux acteurs du casting.






