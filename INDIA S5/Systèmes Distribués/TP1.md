```python
import flask

import json

from flask import Flask, request, jsonify

  

app = flask.Flask(__name__)

app.config["DEBUG"] = True

  

@app.route('/', methods=['GET']) # le type de requêtes http autorisées.

def home():

    return '''<h1> API RestFul</h1>

    <p> Création d'API Web RESTful à l'aide de Flask et Python.</p>'''

  

nom_file='./data.json'

  

@app.route('/person/getAll', methods=['GET'])

def get_all():

    with open(nom_file) as f:

        data = json.load(f)

    return jsonify(data)

  

@app.route('/person/getId', methods=['GET'])

def get_records_id():

    if 'id' in request.args:

        id = int(request.args['id'])

        with open(nom_file) as f:

            data = json.load(f)

            return jsonify(data[id])

  

    else:

        return "Erreur : id n'existe pas"

@app.route('/person/post', methods=['GET','POST'])

def post_records():

    if 'id' and 'nom' and 'email' in request.args:

        id = int(request.args['id'])

        nom = str(request.args['nom'])

        email = str(request.args['email'])

  

        item = {'id' : id, 'nom' : nom, 'email' : email}

  

        with open(nom_file, "r") as f:

            data = json.load(f)

            data.append(item)

        with open(nom_file, "w") as f:

            json.dump(data, f)

  

        return jsonify(data)

  

    else:

        return "Erreur : id ou nom ou email n'existe pas"

  
  

@app.route('/person/del', methods=['GET','DELETE'])

def del_record_id():

    if 'id' in request.args:

        id = int(request.args['id'])

  

        with open(nom_file, "r") as f:

            data = json.load(f)

            for idx, obj in enumerate(data):

                if obj['id'] == id:

                    item = data.pop(idx)

            with open(nom_file, "w") as f:

                json.dump(data, f)

            return jsonify(item)

  

    else:

        return "Erreur : id n'existe pas"

  

if __name__ == '__main__':

    app.run(port=5005)
```



