![[TP2Bigdata_INDIA_2023_2024.pdf]]
### Exercice1.

1. Se connecter à MongoDB via le shell : C:\mongosh-1.10.6-win32-x64\bin\mongosh

  

2. Afficher les bases de données existantes

```JAVASCRIPT

show databases

```

  

3. Afficher la liste de collections de la base biblio

```JAVASCRIPT

show collections

```

  

4. Compter le nombre de documents de la collection ‘livres’

```JAVASCRIPT

db.livres.aggregate([{$count : 'nbreDoc'}])

db.livres.aggregate([{ $group : { _id : "null", count : { $sum : 1}}}])

```

  

5. Compter le nombre de documents par Editeur

```JAVASCRIPT

db.livres.aggregate([ {$group : {_id : "$Editeur", nb_doc : {$sum : 1}}} ])

```

  

6. Rechercher dans la collection livres tous les documents (titre, et prix) qui ont un prix entre 200 et 400.

```JAVASCRIPT

db.livres.find({PU:{"$gte":200, "$lte":400}},{"Titre":1, "PU":1, "_id":0})

```

  

7. Compter le nombre de documents ayant PU > 500

```JAVASCRIPT

db.livres.aggregate([ {$match : {PU : {"$gte":500}}}, {$count : 'nb_doc_PU>500'} ])

```

ou

```JAVASCRIPT

db.livres.find({PU:{"$gte":500}},{"Titre":1, "PU":1, "_id":0}).count()

```

  

8. Rechercher la valeur maximale puis minimale que prend la variable PU sur tous les documents

```JAVASCRIPT

db.livres.aggregate([ {$group : {"_id":null, "max_PU" : {$max : "$PU"}, "min_PU" : {$min : "$PU"}} }  ])

```

  

9. Afficher le nom de l'éditeur, le prix du livre le plus cher et le moins cher pour cet éditeur

```JAVASCRIPT

db.livres.aggregate([ {$group : {"_id":"$Editeur", "max_PU" : {$max : "$PU"}, "min_PU" : {$min : "$PU"}} }  ])

```

  

10. Afficher le nom de l'éditeur, le prix du livre le plus cher et le moins cher pour cet éditeur, ceci pour les éditeurs ayant édité plus d'un livre.

```JAVASCRIPT

db.livres.aggregate([ {$group : {"_id":"$Editeur", "max_PU" : {$max : "$PU"}, "min_PU" : {$min : "$PU"}, nbre:{$sum:1}} }, {$match: {'nbre':{"$gte":2}}}  ])

```

  

11. Récupérer le premier document (titre, auteur et PU) dont le titre contient « dévelop ».

```JAVASCRIPT

db.livres.findOne({Titre : /^dévelop/}, {"_id":0, "Titre":1, "Auter":1, "PU":1})

```

ou

```JAVASCRIPT

db.livres.find({Titre : /^dévelop/}, {"_id":0, "Titre":1, "Auter":1, "PU":1}).limit(1)

```

  

12. Créer dans la base de données biblio les deux collections « etudiants », et « emprunts »

```JAVASCRIPT

db.createCollection('etudiants')

db.createCollection('emprunts')
```


  

13. Insérer dans la collection etudiants les données du fichier dataetudiant.json, et vérifier l’insertion

```JAVASCRIPT

mongoimport -d biblio -c etudiants \*chemin_acces*\DataEtudiant.json --jsonArray

```

  

14. Insérer dans la collection emprunts les données suivantes, et vérifier l’insertion
```JAVASCRIPT
{ noetud: 'E1', noliv: 2, datesortie: '15/01/2023', dateretour: '' },

{ noetud: 'E2', noliv: 1, datesortie: '17/01/2023', dateretour: '18/01/2023' },

{ noetud: 'E1', noliv: 2, datesortie: '20/01/2023', dateretour: '' },

{ noetud: 'E3', noliv: 4, datesortie: '15/01/2023', dateretour: '' },

{ noetud: 'E3', noliv: 5, datesortie: '15/01/2023', dateretour: '16/01/2023' },

{ noetud: 'E6', noliv: 6, datesortie: '16/01/2023', dateretour: '' },

{ noetud: 'E4', noliv: 7, datesortie: '14/01/2023', dateretour: '16/01/2023' },

{ noetud: 'E4', noliv: 12, datesortie: '20/01/2023', dateretour: '' },

{ noetud: 'E5', noliv: 7, datesortie: '22/01/2023', dateretour: '' }
```
  

```JAVASCRIPT

>db.emprunts.insertMany([

   { noetud: 'E1', noliv: 2, datesortie: '15/01/2023', dateretour: '' },

   { noetud: 'E2', noliv: 1, datesortie: '17/01/2023', dateretour: '18/01/2023' },

   { noetud: 'E1', noliv: 2, datesortie: '20/01/2023', dateretour: '' },

   { noetud: 'E3', noliv: 4, datesortie: '15/01/2023', dateretour: '' },

   { noetud: 'E3', noliv: 5, datesortie: '15/01/2023', dateretour: '16/01/2023' },

   { noetud: 'E6', noliv: 6, datesortie: '16/01/2023', dateretour: '' },

   { noetud: 'E4', noliv: 7, datesortie: '14/01/2023', dateretour: '16/01/2023' },

   { noetud: 'E4', noliv: 12, datesortie: '20/01/2023', dateretour: '' },

   { noetud: 'E5', noliv: 7, datesortie: '22/01/2023', dateretour: '' }

])

```

  

15. Lister le nombre d'emprunt de chaque livre (noliv).

```JAVASCRIPT

db.emprunts.aggregate([{$group:{"_id":"$noliv", nbrePret:{$sum:1}}}])

```

  

16. Sélectionner les livres ayant été empruntés plus qu’une seule fois.

```JAVASCRIPT

db.emprunts.aggregate([{$group:{"_id":"$noliv", nbrePret:{$sum:1}}}, {$match:{"nbrePret" : {"$gt":1}}}])

```

  


17. Lister noliv et date sortie des livres empruntés :

```JAVASCRIPT
db.emprunts.find({datesortie: {$ne: ""}}, {noliv: 1, datesortie: 1, _id: 0})
```

19. Lister noliv, titre et date sortie des livres empruntés et non retournés :

```JAVASCRIPT
db.emprunts.find({dateretour: ""}, {noliv: 1, datesortie: 1}).forEach(function(emprunt) {
    var livre = db.livres.findOne({codeLivre: emprunt.noliv}, {Titre: 1});
    print("noliv: " + emprunt.noliv + ", Titre: " + livre.Titre + ", datesortie: " + emprunt.datesortie);
})
```

20. Trouver noliv, titre des livres empruntés (non retournés), numéro et le nom de leur emprunteur. Cette requête nécessite une opération de jointure entre les collections `emprunts` et `etudiants. Voici une approche pour obtenir ces informations :

```JAVASCRIPT
db.emprunts.find({dateretour: ""}).forEach(function(emprunt) {
    var livre = db.livres.findOne({codeLivre: emprunt.noliv}, {Titre: 1});
    var etudiant = db.etudiants.findOne({noetud: emprunt.noetud}, {nom: 1, prenom: 1});
    print("noliv: " + emprunt.noliv + ", Titre: " + livre.Titre + ", noetud: " + emprunt.noetud + ", Emprunteur: " + etudiant.nom + " " + etudiant.prenom);
})
```

21. Pour insérer le document dans la collection emprunts, utilisez la commande suivante :

```JAVASCRIPT
db.emprunts.insert({
    noetud: 'E7',
    noliv: 10,
    datesortie: '16/02/2023',
    dateretour: ''
})
```

22. Pour modifier les dates d'emprunt du livre 10, utilisez la commande suivante :

```JAVASCRIPT
db.emprunts.update(
    { noliv: 10 },
    {
        $set: {
            datesortie: '17/02/2020',
            dateretour: '18/02/2020'
        }
    }
)
```

23. Pour supprimer les livres de dateretour nulle dans la collection "emprunts", utilisez la commande suivante :

```JAVASCRIPT
db.emprunts.deleteMany({ dateretour: "" })
```