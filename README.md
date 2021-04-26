# musical-giggle
##setup the system

1. Setup codebase
 
    1. clone the code in a directory
      
            git clone https://github.com/sahasrara62/filed_audio_file_server.git
    2. go in the directory `cd filed_audio_file_server`
    3. install all project requirements, use command
        `python -m pipenv install -r requirements.txt`
    4. go in `pipenv` virtualenv by `python -m pipenv shell`
    5. set up flask env variable, run commands
        1. `export FLASK_APP=main.py`
        2. `export FLASK_ENV=developement`
2. create database
        
      in postgresql create database "audioserver" and grant permission to user, in postgresql shell run command .
      
       1. create db audioserver;
       2. GRANT ALL PRIVILEGES ON DATABASE audioserver to "prashant"; # my username
3. create the table in audioserver database
     1. in `.env` file add the data as below
            
            # example
            # DATABASE_URL="postgresql://prashant:rana@localhost:5432/audioserver"
            DATABASE_URL="postgresql://<username>:<password>@<server host>:<port>/<database name>
            SECRET_KEY="this-is-a-sample-secret-key"
            FLASK_ENV="development"
            SQLALCHEMY_TRACK_MODIFICATIONS=True
     2. lets do migrations, run following commands
        1. `flask db init`
        2. `flask db migrate`
        3. `flask db upgrade`
       
        this  will create a migration folder, and create table in the database
4. run app, activate envrionment `pipenv shell` and run the command to run server
    `flask run`
5. check if server is running, in browser go to `localhost:5000/`, you will get `server is running` msg.
            
     
# challenge Description
Write a Flask / FastAPI Web API that simulates the behavior of an audio file server
while using a MongoDB / SQL database.
Requirements: You have one of three audio files which structures are defined below
Audio file type can be one of the following:
    1 – Song
    2 – Podcast
    3 – Audiobook
    
##`Song` file fields:
- `ID` – (mandatory, integer, unique)
- `Name of the song` – (mandatory, string, cannot be larger than 100
characters)
- `Duration in number of seconds` – (mandatory, integer, positive)
- `Uploaded time` – (mandatory, Datetime, cannot be in the past)
## `Podcast` file fields:
- `ID` – (mandatory, integer, unique)
- `Name of the podcast` – (mandatory, string, cannot be larger than 100
characters)
- `Duration in number of seconds` – (mandatory, integer, positive)
- `Uploaded time` – (mandatory, Datetime, cannot be in the past)
- `Host` – (mandatory, string, cannot be larger than 100 characters)
- `Participants` – (optional, list of strings, each string cannot be larger than
100 characters, maximum of 10 participants possible)
##`Audiobook` file fields:
- `ID` – (mandatory, integer, unique)
- `Title of the audiobook` – (mandatory, string, cannot be larger than 100
characters)
- `Author of the title` (mandatory, string, cannot be larger than 100
characters)
- `Narrator` - (mandatory, string, cannot be larger than 100 characters)
- `Duration in number of seconds` – (mandatory, integer, positive)
- `Uploaded time` – (mandatory, Datetime, cannot be in the past)
API structuture is define in documentation folder. it is postman structure
Test challenge summary is define in documentation folder
