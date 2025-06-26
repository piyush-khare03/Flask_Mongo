# Flask_Mongo

# Google Sheet Link

https://docs.google.com/spreadsheets/d/1DAInj_TpP_3PWpM82NDefSNiXsz7v0kwJ-sP9teKxe0/edit?usp=sharing

# Question 1
Create a Flask application with an /api route. When this route is accessed, it should return a JSON list. The data should be stored in a backend file, read from it, and sent as a response.

# Explaination
In this question we open and read a file call "data.json" with help of "json" module
Then converting the content of json file into python using "json.load"
Later returning the data in "json" format back to the server using "Jsonify"

# ___________________________________________________CODE_______________________________________ # 
from flask import Flask, jsonify, request
import json

app = Flask(__name__)

@app.route('/')
def home():
    return "Welcome to the Flask MongoDB App!"

@app.route('/api', methods=['GET'])
def api():
    with open('data.json') as d:
        data = json.load(d)
    return jsonify(data)

if __name__ == '__main__':
    app.run(debug=True) 
# __________________________________________________________________________________________________ #

# Question 2

Create a form on the frontend that, when submitted, inserts data into MongoDB Atlas. Upon successful submission, the user should be redirected to another page displaying the message "Data submitted successfully". If there's an error during submission, display the error on the same page without redirection.

# ________________________________________CODE_______________________________________________________ #

from flask import Flask, render_template, request, redirect
from pymongo import MongoClient

app = Flask(__name__)

client = MongoClient("mongodb+srv://admin:12345@cluster0.arqzl3c.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0")
db = client['mydatabase']
collection = db['mycollection']


@app.route('/')
def form():
    return render_template('index.html')


@app.route('/submit', methods=['POST'])
def submit():
    name = request.form['name']
    email = request.form['email']
    
    # Insert data into MongoDB
    collection.insert_one({'name': name, 'email': email})
    return redirect('/success')


@app.route('/success')
def success():
    return 'Data submitted successfully!'
 

if __name__ == '__main__':
    app.run(debug=True)
# ___________________________________________________________________________________________ #
