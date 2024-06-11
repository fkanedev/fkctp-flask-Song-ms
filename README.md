![Python](https://img.shields.io/badge/Python-3.9-blue.svg)
![Built with Flask](https://img.shields.io/badge/Built%20with-Flask-b5f05d.svg)
![MongoDB](https://img.shields.io/badge/MongoDB-4.1.1-green.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

# Songs Microservice Project

This project involves developing a microservice for retrieving song lyrics and implementing CRUD endpoints. Its primary goal is to showcase the practical application of Flask and MongoDB in a real-world scenario. It's part of my training in the [IBM Back-End Development Professional Certificate](https://www.coursera.org/professional-certificates/ibm-backend-development), utilizing a [template](https://github.com/ibm-developer-skills-network/hvlga-Back-End-Development-Songs) provided by IBM Developer Skills Network.

## Table of Contents
1. [Introduction](#introduction)
2. [Technologies Used](#technologies-used)
3. [Installation and Configuration](#installation-configuration)
4. [Usage](#usage)
5. [Development](#development)
6. [Sources](#sources)
7. [License](#license)
8. [Contact](#contact)

## 1. Introduction <a name="introduction"></a>

### Project Objective:
The main objective of this project is to create a microservice for retrieving song lyrics and implementing CRUD (Create, Read, Update, Delete) endpoints using Flask and MongoDB. This microservice, along with the [Pictures Microservice](https://github.com/fkanedev/fkctp-flask-Pictures-ms), will be integrated into the backend of a [main application built with Django](https://github.com/fkanedev/fkctp-django-Music-Band-Site-ma-ui). The project demonstrates the usage and implementation of these technologies in a practical scenario.
### Key Features:
- Retrieve song lyrics from a MongoDB database.
- Implement CRUD operations for managing song data.
- Provide endpoints for health check, count, and CRUD operations.
- Utilize Flask framework for building the microservice.
- Integrate MongoDB for data storage and retrieval.
- Integrate with a Django-based main application as part of a larger backend architecture.

## 2. Technologies Used <a name="technologies-used"></a>

### Programming Languages:
- Python 3.9

### Tools and Frameworks:
- Flask 2.2.2: A micro web framework for Python.
- MongoDB: A NoSQL database for storing song data.
- pymongo: A Python driver for MongoDB.
- gunicorn: A Python WSGI HTTP Server for UNIX.
- pytest: A framework for testing Python code.

## 3. Installation and Configuration <a name="installation-configuration"></a>

### Prerequisites:
- Python 3.9 installed on your system.
- MongoDB server set up and running.
- Virtual environment tool (e.g., venv).

### Installation Steps:
1. Clone the GitHub repository:
    ```bash
    git clone https://github.com/fkanedev/fkctp-flask-Song-ms
    cd fkctp-flask-Song-ms
    ```

2. Create and activate a virtual environment:
    ```bash
    python3.8 -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. Install the dependencies:
    ```bash
    pip install -r requirements.txt
    ```

### Environment Configuration:
Ensure the Python environment is properly set up with Python 3.8. Dependencies should be installed via pip.

### Environment Variables:
- `FLASK_ENV=development`
- `MONGODB_SERVICE=localhost`
- `MONGODB_USERNAME=root`
- `MONGODB_PASSWORD=password`

## 4. Usage <a name="usage"></a>

### Usage Instructions:
To start the MongoDB server, use the following command:
```bash
start_mongo
```
To start the Flask application, use the following command:
```bash
MONGODB_SERVICE=localhost MONGODB_USERNAME=root MONGODB_PASSWORD=password flask --app app run --debugger --reload
```
Replace MONGODB_SERVICE and MONGODB_PASSWORD with your own values. The MONGODB_USERNAME variable should stay as root. 
Since your main application is in a file called app.py, you don't have to specify it. The following command has the same result:
```bash
MONGODB_SERVICE=localhost MONGODB_USERNAME=root MONGODB_PASSWORD=password flask run --reload --debugger
```
### Use Case Examples:
- Retrieve all songs:
```bash
curl --request GET -i -w '\n' --url http://localhost:5000/song
```
- Retrieve a song by ID: GET /song/<id>
```bash
curl --request GET -i -w '\n' --url http://localhost:5000/song/1
```
- Add a new song: POST /song
```bash
curl --request POST \
-i -w '\n' \
--url http://localhost:5000/song \
--header 'Content-Type: application/json' \
--data '{
        "id": 323,
        "lyrics": "Integer tincidunt ante vel ipsum. Praesent blandit lacinia erat. Vestibulum sed magna at nunc commodo placerat.\n\nPraesent blandit. Nam nulla. Integer pede justo, lacinia eget, tincidunt eget, tempus vel, pede.",
        "title": "in faucibus orci luctus et ultrices"
    }'
```
- Update an existing song: PUT /song/<id>
```bash
curl --request PUT \
-i -w '\n' \
--url http://localhost:5000/song/1 \
--header 'Content-Type: application/json' \
--data '{
        "lyrics": "yay hey yay yay",
        "title": "yay song"
    }'
```
- Delete a song: DELETE /song/<id>
```bash
curl --request DELETE \
-i -w '\n' \
--url http://localhost:5000/song/14 \
--header 'Content-Type: "application/json"'
```

## 5. Development <a name="development"></a>

### Project Structure:
This backend project is primarily organized around the Flask framework. The directory structure includes the following folders:

- `backend/`: Contains the core of the microservice, specifically `routes.py`, which defines the API endpoints and their logic.
- `backend/data`: Contains the all data about songs lyrics, in `songs.json` file.
- `tests/`: Contains the unit tests for the microservice, specifically `test_routes.py`, which tests the functionality of the API endpoints.

```plaintext
.
├── backend/
│   └── data/
│   │   └── songs.json
│   ├── __init__.py
│   └── routes.py
├── bin/
│   └── ...
├── tests/
│   └── ...
├── LICENSE
├── README.md
├── requirements.txt
└── ....
```
### Database :
MongoDB serves as the database, accessible through the connection URI specified in the environment variables. The pymongo library acts as the interface for interacting with MongoDB. The database stores song data and allows for CRUD operations.

### Data Model :
The data model for this project includes the following fields for a song:

- id: Unique identifier for the song.
- title: Title of the song.
- artist: Artist of the song.
- lyrics: Lyrics of the song.
- year: Year of release.

## 6. Sources <a name="sources"></a>

- **Template: [IBM Developer Skills Network - Songs service template](https://github.com/ibm-developer-skills-network/hvlga-Back-End-Development-Songs)**

- **Useful links**:
  - **[Back-end Application Development Capstone Project](https://www.coursera.org/learn/backend-development-capstone-project/home/module/2)**
  - **[IBM Back-End Development Professional Certificate](https://www.coursera.org/professional-certificates/ibm-backend-development)**

## 7. License <a name="license"></a>

This project is licensed under the MIT License - see the [LICENSE](/LICENSE) file for details.

## 8. Contact <a name="contact"></a>

### Contact Information :

- Send me email : **fkanecloudtech@gmail.com**
- Connect with me on [LinkedIn](https://www.linkedin.com/in/your-profile/)
- Visit my [portfolio](https://yourname.github.io) to explore my projects and services.


### Contribution and Support :

Contributions are welcome. Please refer to the [CONTRIBUTING](/CONTRIBUTING) file for more information on how to contribute.
