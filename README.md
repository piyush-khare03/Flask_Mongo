# Flask_Mongo
# Question 1
Create a Flask application with an /api route. When this route is accessed, it should return a JSON list. The data should be stored in a backend file, read from it, and sent as a response.

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
