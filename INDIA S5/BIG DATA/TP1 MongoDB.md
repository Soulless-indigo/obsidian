![[TP1 BIG DATA.pdf]]



1. **Afficher les bases de données existantes**
   
   To display the existing databases, you can use the following command:

   ```javascript
   show dbs
   ```

2. **Afficher les collections de la base de données test**

   To display the collections in the "biblio" database, you can use the following command:

   ```javascript
   use biblio
   show collections
   ```

3. **Créer la base de données ‘biblio’**

   You can create the "biblio" database using the following command:

   ```javascript
   use biblio
   ```

4. **Créer la collection ‘livres’ dans la nouvelle base de données**

   To create the "livres" collection in the "biblio" database, you can use the following command:

   ```javascript
   db.createCollection("livres")
   ```

5. **Insérer dans la collection ‘livres’ les données du fichier ‘dataLivre.json’**

   You can import data from the "dataLivre.json" file into the "livres" collection using the `mongoimport` command as you mentioned:

   ```javascript
   mongoimport -d biblio -c livres D:/MyData/Cours/BigData/dataLivre.json --jsonArray
   ```

6. **Compter le nombre de documents de la collection ‘livres’**

   To count the number of documents in the "livres" collection, you can use the following command:

   ```javascript
   db.livres.count()
   ```

7. **Afficher tous les documents de la collection livres**

   To display all documents in the "livres" collection, you can use the following command:

   ```javascript
   db.livres.find()
   ```

8. **Afficher le premier document de la collection livres**

   To display the first document in the "livres" collection, you can use the following command:

   ```javascript
   db.livres.findOne()
   ```

9. **Lister la liste des éditeurs présents dans la base**

   To list the unique publishers (éditeurs) in the collection, you can use the `distinct` command as follows:

   ```javascript
   db.livres.distinct("Editeur")
   ```

Please note that you'll need to execute these commands in the MongoDB shell as described in your provided instructions. If you have any further questions or need assistance with the remaining tasks, please let me know.

Certainly, here are the answers to the remaining questions:

11. **Compter le nombre de documents de la collection ‘livres’**

   To count the number of documents in the "livres" collection, you can use the following command:

   ```javascript
   db.livres.count()
   ```

12. **Afficher tous les documents de la collection livres**

   To display all documents in the "livres" collection, you can use the following command:

   ```javascript
   db.livres.find()
   ```

13. **Afficher le premier document de la collection livres**

   To display the first document in the "livres" collection, you can use the following command:

   ```javascript
   db.livres.findOne()
   ```

14. **Lister la liste des éditeurs présents dans la base**

   To list the unique publishers (éditeurs) in the collection, you can use the `distinct` command as follows:

   ```javascript
   db.livres.distinct("Editeur")
   ```

15. **Compter le nombre des livres d’Editeur 'Dunod’**

   To count the number of books with the publisher 'Dunod', you can use the following command:

   ```javascript
   db.livres.count({ "Editeur": "Dunod" })
   ```

16. **Chercher le premier document d’Editeur 'Dunod’**

   To find the first document with the publisher 'Dunod', you can use the following command:

   ```javascript
   db.livres.findOne({ "Editeur": "Dunod" })
   ```

17. **Chercher tous les documents de PU > 300**

   To find all documents with a "PU" value greater than 300, you can use the `$gt` operator as follows:

   ```javascript
   db.livres.find({ "PU": { $gt: 300 } })
   ```

18. **Afficher que le titre et les auteurs du premier document**

   To display only the "Titre" and "Auteur" fields of the first document, you can use the following command:

   ```javascript
   db.livres.findOne({}, { "Titre": 1, "Auteur": 1, "_id": 0 })
   ```

19. **Lister tous les documents de l’Auteur "Goron, Aurélien"**

   To list all documents with the author "Goron, Aurélien," you can use the following command:

   ```javascript
   db.livres.find({ "Auteur": "Goron, Aurélien" })
   ```

20. **Lister tous les documents qui n’ont pas d’Auteur**

   To list all documents that do not have an author, you can use the `$exists` operator as follows:

   ```javascript
   db.livres.find({ "Auteur": { $exists: false } })
   ```

21. **Compter le nombre des documents par auteur et trier le résultat par ordre croissant**

   To count the number of documents per author and sort the result in ascending order, you can use the following aggregation query:

   ```javascript
   db.livres.aggregate([
     {
       $group: {
         _id: "$Auteur",
         count: { $sum: 1 }
       }
     },
     {
       $sort: { count: 1 }
     }
   ])
   ```

22. **Lister la liste des documents de l’Auteur "Goron, Aurélien", triée par titre de livre et par nombre de pages**

   To list the documents by "Goron, Aurélien," sorted by book title and number of pages, you can use the following query:

   ```javascript
   db.livres.find({ "Auteur": "Goron, Aurélien" }).sort({ "Titre": 1, "PU": 1 })
   ```

23. **Tester si un champ a une valeur dans un ensemble donné (opérateur $in). Ici, nous cherchons les documents d’éditeurs Hermann, et Afnor.**

   To find documents with publishers "Hermann" or "Afnor," you can use the `$in` operator as follows:

   ```javascript
   db.livres.find({ "Editeur": { $in: ["Hermann", "Afnor"] } })
   ```
