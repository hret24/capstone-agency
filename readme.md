# FSND Final Project

This  is the final project of the Udacity Full Stack Developer Nano Degree Program that I am partaking as part of my job goals. The goal of this project is to deploy a Flask application hosted in Render Cloud/PostgreSQL and enable Role Based Authentication and roles-based access control (RBAC) with Auth0 (a third-party authentication system we covered in the course).

I have implemented the Casting Agency model fora company called Capstone that assigns movies to actors. There are three roles within the company of Assistant, Director and Producer.

## Getting Started

### Installing Dependencies

#### Python 3.9

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

To do so, run the following commands

```bash
python3.9 -m venv venv
```

```bash
source venv/bin/activate
```

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies from the root directory by running

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

## Database Setup

With Postgres running, restore a database using the capstone_casting_agency_db.psql file provided. From the root folder in terminal run:

```bash
psql capstone_casting_agency_db<capstone_casting_agency_db.psql
```

## Running the server

From within the directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
. ./setup.sh
flask run
```
Note that the database name in setup.sh is set to my database name.

setup.sh has all the environment variables needed for the project. The app may fail if they are not set properly. If that happens just copy paste lines from setup.sh on you CLI.

# Project deployed at

https://capstone-casting-agency-pbpq.onrender.com/

### JWT will be valid for 24hrs from Sun 26 Jan 23:00. Do let me know if a new set of tokens is required.

## Testing

To run the tests, run

```
dropdb casting_agency_test
createdb casting_agency_test
psql casting_agency_test<casting_agency_test.psql
python test_flaskr.py
```

The tests print data returned from the APIs along with API logs.

#### The rests also use the Auth token set in env variables and will give an error if the tokens are expired.

## API Reference

### Error Handling

Errors are returned as JSON objects in the following format:

```
{
    "success": False,
    "error": 400,
    "message": "bad request"
}

```

### Endpoints

GET '/actors'
POST '/actors'
PATCH '/actors/<actor_id>'
DELETE '/actors/<actor_id>'
GET '/movies'
GET '/actors'
POST '/actors'
PATCH '/actors/<actor_id>'
DELETE '/actors/<actor_id>'

GET '/movies'
Fetches an array of movies
Required URL Arguments: None
Required Data Arguments: None
Returns: Returns Json data about movies
Success Response:

```
{
   "movies":[
      {
         "genre":"SuperHero",
         "id":9,
         "release_date":"2019-01-02",
         "title":"Avengers"
      },
      {
         "genre":"SuperHero",
         "id":10,
         "release_date":"2019-01-02",
         "title":"Avengers"
      }
   ],
   "success":True
}
```

GET '/actors'
Fetches an array of actors
Required Data Arguments: None
Returns: Json data about actors
Success Response:

```
  {
   "actors":[
      {
         "age":22,
         "gender":"male",
         "id":10,
         "name":"bob"
      }
   ],
   "success":True
}
```

DELETE '/movies/<int:movie_id>'
Deletes the movie_id of movie
Required URL Arguments: movie_id: movie_id_integer
Required Data Arguments: None
Returns: deleted movie's ID
Success Response:

```
{'deleted': 8, 'success': True}
```

DELETE '/actors/<int:actor_id>'
Deletes the actor_id of actor
Required URL Arguments: actor_id: actor_id_integer
Required Data Arguments: None
Returns:the deleted actor's ID
Success Response:

```
{'deleted': 9, 'success': True}
```

POST '/movies'
Post a new movie in a database.
Required URL Arguments: None
Required Data Arguments: Json data
Success Response:

```
{'movie_id': 11, 'success': True}
```

POST '/actors'
Post a new actor in a database.

Required URL Arguments: None

Required Data Arguments: Json data

Success Response:

```
{'actor_id': 11, 'success': True}
```

PATCH '/movies/<int:movie_id>'
Updates the movie_id of movie
Required URL Arguments: movie_id: movie_id_integer
Required Data Arguments: None
Returns: Json data about the updated movie
Success Response:

```
{
   "movie":{
      "genre":"SuperHero",
      "id":9,
      "release_date":"2019-01-02",
      "title":"Avengers 2"
   },
   "success":True
}
```

PATCH '/actors/<int:actor_id>'
Updates the actor_id of actor
Required URL Arguments: actor_id: actor_id_integer
Required Data Arguments: None
Returns: Json data about the modified actor's ID
Success Response:

```
{
   "actor":{
      "age":22,
      "gender":"male",
      "id":10,
      "name":"bob"
   },
   "success":True
}
```
