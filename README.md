# Learning Log

Web app called Learning Log that allows users to log the topics they’re interested in and to make journal entries as 
they learn about each topic. The Learning Log home page describes the site and invites users to either register or log-in. 
Once logged in, a user can create new topics, add new entries, and read and edit existing entries.

## Creating a Virtual Environment
To work with Django, we’ll first set up a virtual environment. A virtual environment is a place on your system where 
you can install packages and isolate them from all other Python packages. Separating one project’s libraries from other 
projects is beneficial and will be necessary when we deploy Learning Log to a server.
Create a new directory for the project called learning_log, switch to that directory in a terminal, and enter the 
following code to create a virtual environment:

    learning_log$ python3 -m venv ll_env 
    learning_log$


### Activating the Virtual Environment
Now we activate the virtual environment using the following command:

    learning_log$ source ll_env/bin/activate
    
    you will see : (ll_env)learning_log$

NOTE: If you’re using Windows, use the command ll_env\Scripts\activate (without the word "source") to activate the virtual 
environment. If you’re using PowerShell, you might need to capitalize "Activate".

### To stop using a virtual environment, enter "deactivate":
    
    (ll_env)learning_log$ deactivate

    you will see : learning_log$
    

## Installing Django

    ll_env)learning_log$ pip install django

    Collecting django

    --snip--
    Installing collected packages: pytz, django
    Successfully installed django-2.2.0 pytz-2018.9 sqlparse-0.2.4 

    (ll_env)learning_log$


## Creating a Project in Django

    (ll_env)learning_log$ django-admin startproject learning_log .

    (ll_env)learning_log$ ls

    learning_log ll_env manage.py

    (ll_env)learning_log$ ls learning_log

    __init__.py  settings.py  urls.py  wsgi.py


## Creating the Database

    (ll_env)learning_log$ python3 manage.py migrate 

    Operations to perform:
        Apply all migrations: admin, auth, contenttypes, sessions

    Running migrations:
        Applying contenttypes.0001_initial... OK
        Applying auth.0001_initial... OK
        --snip--
        Applying sessions.0001_initial... OK

    (ll_env)learning_log$ ls
    db.sqlite3 learning_log ll_env manage.py
     

## Viewing the Project

Run Server:
Let’s make sure that Django has set up the project properly. Enter the runserver command as follows to view the project 
in its current state:
    
    (ll_env)learning-Log % python manage.py runserver
    Watching for file changes with StatReloader
    Performing system checks...

    System check identified no issues (0 silenced).
    February 08, 2021 - 03:14:34
    Django version 3.1.6, using settings 'learning_log.settings'
    Starting development server at http://127.0.0.1:8000/
    Quit the server with CONTROL-C. 

Open a web browser and enter the URL http://localhost:8000/, or http:// 127.0.0.1:8000/ if the first one doesn’t work. 
You should see something like Figure 18-1, a page that Django creates to let you know all is working properly so far. 
Keep the server running for now, but when you want to stop the server, press cTrL-C in the terminal where the runserver 
command was issued.


# Starting an App

leave the development server running in the terminal window you opened earlier. Open a new terminal window (or tab), 
and navigate to the directory that contains manage.py. Activate the virtual environment, and then run the startapp 
command:
    
    learning_log$ source ll_env/bin/activate
    (ll_env)learning_log$ python manage.py startapp learning_logs 
    (ll_env)learning_log$ ls
    db.sqlite3 learning_log learning_logs ll_env manage.py
    (ll_env)learning_log$ ls learning_logs/
    __init__.py  admin.py  apps.py  migrations  models.py  tests.py  views.py

The command startapp appname tells Django to create the infrastructure needed to build an app.
In the project directory now, we will have a new folder called learning_logs.
Django has created __init__.py , admin.py , apps.py , migrations , models.py , tests.py , views.py files. 
The most important files are models.py, admin.py, and views.py. We’ll use models.py to define the data we want to 
manage in our app. 


Every time a Model is added we need to migrate the database.
Migrate the database and check the output by entering the following commands:

    (ll_env)learning_log$ python manage.py makemigrations learning_logs
    
    Migrations for 'learning_logs':
        learning_logs/migrations/0002_entry.py
            - Create model Entry
    
    (ll_env)learning_log$ python manage.py migrate 

    Operations to perform:
        --snip--
        Applying learning_logs.0002_entry... OK

A new migration called 0002_entry.py is generated, which tells Django how to modify the database to store information 
related to the model Entry.
