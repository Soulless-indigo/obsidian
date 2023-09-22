![[CoursBigData_INDIA2023_Partie1.pdf]]

### 1. Big Data:
- Def:
	- Big data mégadonnées ou donnee massive designe les ressources d'info:
		- volume, vélocité et variété imposent l'utilisation de technologies et de méthodes analytiques particulier pour creer du valeur.
		- qui depasee 
- Principe clé:
	- La gestion des donnees
	- l'analyse des donnees 
	- La science des donnees
	- le stockage des donnees
- Source du DATA?
	- BD CLIENTS
	- NAVIGATION SUR INTERNET
	- SOCIAL MEDIA
	- DOSSIER MEDICAUX
	- APP MOBILE
	- SYS DE TRANSACTION
	- DONNER GENERER PAR DES MACHINE
	- IoT SENSORS
- Structuration des donnees 
  ![[Big data struct.svg]]

| niveau de struct | model de donnee | exemple |Facilité|  
| -------- | -------- | -------- |-------- |  
| Struct | BD relationnel | sql db |Facile INDEXED|  
| SEMI | JSON XML CSV | Mongo db NO-SQL |Facile NON-INDEXED|
| NON | TEXT | TEXT... |NON FACILE|

### Les 4V:
- Volume:
- Variété:
- *Vélocité* de l'aquisition:
- Véracité: données douteuse: incomplete, incertaines, falsifiées, imprécises.......
### Cas d'utilisation:
- Santé
- Product Dev
- Optimization .......
### Défis:
- Capacité de traitement et coût
- Qualité et gouvernance des données 
- Coception d'un architecture
	- adaptation aux tech dispo
	- deploy et gestion de big data exigent de new competance
- Service de gestion CLOUD:
	- Necessite un controle
	- Migration de donnees est complexe
- Les pratiques et reglementations en matirer de collecte de donnees:
	- peu de restriction sur l'utilisation de donnees 
	- protection de la vie privee des consommateurs
### 2. Architecture de distribution de donnneess:

- Approche traditionnelle: Le stockage et le traitement des donnees sont centralisees dans un serveur 
![[Archi classic big data.svg]]


- Archi Distribuée - Cluster computing:
	- Le stockage des donnees est distr dans le noeuds d'un cluster et leurs traitement y est parallélisé.
	![[Archi dis cluster.svg]]
### 3. BD SQL & NoSQL:
	3.1 BD SQL:
		- Facile
		- Securisé 
		- Evolivité
		- Haute Performance, Fiable
		*rules:*
			- SGBDs at most are transactionnels
				- une transac est une unité d'action             respect 4 critere 'ACID':
					- ATOMICITY: ALL changes are                                excecuted 100% or non 
					- CONSISTENCY: respect data                                    integrity
					- ISOLATION: read and writes are                          independent from others 
					- DURABILITY: executed trans are                             saved even in a                                 system faileur or                               shutdown
	3.2: BD NoSQL:
			- NoSQL == Not Only SQL
			- flexibles shemas:
				- semi struct
				- we don't use tables
				- we don't care about data types
			- manage big volumes of data
			- traitement distribué
			- high read/write capacity
			- complexity of requests:
				- great at request that calls one                 table
				- no complex joints using WHERE 
				
![[NO SQL SYSTEM DB.svg]]

				ACP FOR NO SQL:
				C: COHERENCE
				A: AVAILABILITY
				P: PARTITION TOLERANCE
		DB SQL is pricy to maintain
			- sql offers ADMIN more than NoSql
			- sql follows ACID
			- NoSql follows CAP
	3.3 Types of NoSQL:
		3.3.1 Clé/Valeur
			- Basic DB
			- chaque obj identifies by a key unique           and it is the only way could be                 requested
			- Structure libre XML JSON .........
		3.3.2 Document DB
				- constitueted by a collection of                documents

![[Pasted image 20230922095952.png]]
```json
	{ 
	"name":"MongoDB",
	"type":"database",
	"count":1,
	"info":{
			x:203,
			y:102,
	}
	}			
```

			3.3.3 base orientees colones:
			
			
			![[Pasted image 20230922100254.png]]

			3.3.4 Paradigme graphe:

![[Pasted image 20230922100810.png]]

![[Pasted image 20230922100917.png]]

![[Pasted image 20230922100937.png]]
![[Pasted image 20230922100956.png]]

