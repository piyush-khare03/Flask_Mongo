# Flask_Mongo
# Question 1
Create a Flask application with an /api route. When this route is accessed, it should return a JSON list. The data should be stored in a backend file, read from it, and sent as a response.

In this question we open and read a file call "data.json" with help of "json" module
Then converting the content of json file into python using "json.load"
Later returning the data in "json" format back to the server using "Jsonify"

