![[TP3Bigdata_INDIA_2023_2024.pdf]]
# BIG DATA

## TD3 : NEO4J

  

### Exercice1.

  

1. En utilisant Neo4j Desktop, créer un nouvel utilisateur (user1/user1)

  

2. Accéder à l’interface utilisateur via votre navigateur préféré : http://localhost:7474/

  

3. Reprendre les requetes du tableau « Prise en main du langage Cypher (Neo4j) » pour créer le graphe

suivant

  

4. Afficher le schéma actuel du graphique.

  

5. Afficher la liste des nœuds personnes

```

MATCH (n:Person) RETURN n

```

  

6. Afficher les noms des 3 premieres personnes

```

MATCH (n:Person) RETURN n LIMIT 3

```

  

7. Récupérer le nœud de l’acteur Keanu Reeves

```

MATCH (n:Person {name:'Keanu Reeves'}) RETURN n

```

```

MATCH (n:Person) WHERE n.name = 'Keanu Reeves' RETURN n

```

  

8. Afficher la liste actuelle des clés de propriété dans le graphe

```

call db.propertyKeys

```

  

9. Afficher la liste des co-acteurs de Keanu Reeves

```

MATCH (keanu:Person)-[:ACTED_IN]->(movie:Movie),

(coActor:Person)-[:ACTED_IN]->(movie)

WHERE keanu.name = 'Keanu Reeves'

RETURN DISTINCT coActor.name;

```

```

MATCH (keanu:Person {name : 'Keanu Reeves'})-[:ACTED_IN]->(movie:Movie)<-[:ACTED_IN]-(coActor:Person)

RETURN DISTINCT coActor.name;

```

  

10. Afficher tous les nœuds connectés au film, The Matrix, ainsi que leurs relations.

```

MATCH (n)-[relation]->(movie:Movie {title : 'The Matrix'}) RETURN DISTINCT n, relation

```

  

11. Afficher les titres des films de Keanu Reeves ainsi que les rôles qu’il a joué

```

MATCH (keanu:Person {name : 'Keanu Reeves'})-[r:ACTED_IN]->(movie:Movie)

RETURN movie.title, r.roles

```

  

12. Qui a réalisé le film " The Matrix " ?

```

MATCH (n:Person)-[:DIRECTED]->(m:Movie {title : 'The Matrix'}) RETURN n.name

```

  

13. Comment les gens sont-ils reliés au film "The Matrix" (le nom et le role de chaque personne)

```

MATCH (n:Person)-[relation]-(m:Movie {title:'The Matrix'}) RETURN n.name, type(relation)

```

  

14. Afficher les noms des acteurs avec le nombre de films pour chacun. Trier les résultats par nombre de

films dans l’ordre décroissant

```

MATCH (p:Person)-[:ACTED_IN]->(m:Movie)

RETURN p.name, COUNT(m)

ORDER BY COUNT(m) DESC

```

  

15. Retourner le nombre d’acteurs

```

MATCH (p:Person)-[:ACTED_IN]->()

RETURN COUNT(p)

```

  

16. Retourner le nombre de personnes

```

MATCH (p:Person)

RETURN COUNT(p)

```

  

17. Retourner le nombre d’acteurs et le nombre de personnes

```

MATCH (person:Person)

RETURN COUNT(CASE WHEN (person)-[:ACTED_IN]->() THEN 1 ELSE null END) AS NombreActeurs,

COUNT(person) AS NombrePersonnes

```

  
  

18. Ajouter la propriété « gender » au nœud Person.

```

  

```