#Learning Log

Web app called Learning Log that allows users to log the topics they’re interested in and to make journal entries as 
they learn about each topic. The Learning Log home page describes the site and invites users to either register or log in. 
Once logged in, a user can create new topics, add new entries, and read and edit existing entries.

###Creating a Virtual Environment
To work with Django, we’ll first set up a virtual environment. A virtual environment is a place on your system where 
you can install packages and isolate them from all other Python packages. Separating one project’s libraries from other 
projects is beneficial and will be necessary when we deploy Learning Log to a server in Chapter 20.
Create a new directory for your project called learning_log, switch to that directory in a terminal, and enter the 
following code to create a virtual environment:

learning_log$ python3 -m venv ll_env 
learning_log$


###Activating the Virtual Environment
Now we need to activate the virtual environment using the following command:

learning_log$ source ll_env/bin/activate
(ll_env)learning_log$

NOTE: If you’re using Windows, use the command ll_env\Scripts\activate (without the word source) to activate the virtual 
environment. If you’re using PowerShell, you might need to capitalize Activate.