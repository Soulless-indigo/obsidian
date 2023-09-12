## 1- Sys Dis:
- Ensemble composé *d'élément (Composants)*:
	- Collaborent á une ou plusieurs taches communes
	-  "" ""       par l'intermédiaire 'protocole'

Avantage des systèmes distribués:
- Performance
- Transparence à la localisation
- Transparence daccèss
- ...

example: RPC(Remote Procedure Call)
## 2- Organisation des app dis:
- a- architecture client serveur
- b- architecture 3-tiers
- c- architecture N-tiers
- d- architecture MVC(MODEL - CONTROLEUR - VUE)
- e- Middleware: couche de logiciel(réparti):
	- Classes:
		- O O dis: JAVA RMI,CORBA
		- O COMP DIS: EJB,CCM
		- O TRANS: JTS de SUN, MTS de MS
		- o Msg :JMS de SUN, ...
## 3- Web Services:
![[WhatsApp Image 2023-09-11 at 14.52.37.jpeg]]

- web services: uses (TCP/IP, URI/URL, HTTP/HTTPS, SOAP..... POR LE TANSPORT , PUIS XML pour le contenu)
- Interopérabilité: 
	- Different Apps
	- different OS 
	- different HW

![[Pasted image 20230911145854.png]]

Exemples: 
- Google Web Services:
![[Pasted image 20230911150105.png]]
3.1- Architecture d'un web service:
![[Pasted image 20230911150356.png]]
3.2- SOAP:
![[Pasted image 20230911150804.png]]
![[Pasted image 20230911150847.png]]
![[Pasted image 20230911150922.png]]
3.3- Architecture REST:
- REST (*Re*presentational *S*tate *T*ransfer)
REST est un style d'architecture logicielle définissant un ensemble de contraintes à utiliser pour créer des services web. Les services web conformes au style d'architecture REST, aussi appelés services web RESTful, établissent une interopérabilité entre les ordinateurs sur Internet.
![[Pasted image 20230911151210.png]]
![[Pasted image 20230911151325.png]]
Ex RESTful and JAX-RS DIAGRAM :

Ex Django:
![[Pasted image 20230911151716.png]]

### 3.3.1 what is REST?:
- Ressource:
	- est un objet identifiable sur le système
	- identifié par URI(http://127.0.0.1:8082/restful3-livre/rest/livres)
	- est no
- HTTP METHODES(CRUD):
	- GET
	- POST
	- UPDATE
	- DELETE

![[Pasted image 20230911152357.png]]
![[Pasted image 20230911152703.png]]
![[Pasted image 20230911152803.png]]
![[Pasted image 20230911152857.png]]
![[Pasted image 20230911153146.png]]
![[Pasted image 20230911153259.png]]
![[Pasted image 20230911153629.png]]
![[Pasted image 20230911154116.png]]
