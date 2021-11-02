# django [[web developement]]
Django is a python web framework that encourages rapid developement and clean design. It takes care of alot of hassle. It is free and open source. 

# installing django

pip install django [[installation]].

# starting a django project 
Procedure to start a django project: #cmd 
1. open cmd prompt 
2. navigate to working directory (cd WORKINGDIRECTORY) [[cmd]]
3. use command "startproject PROJECTNAME"

This creates a project folder called PROJECTNAME in the chosen working directory

# running django server on local port 8000 

Procedure to run django server on local port: #cmd
1. change directory into PROJECTNAME (cd PROJECTNAME)
2. use command "python manage.py runserver"

**NOTE:** if you need to run on another server change command to python manage.py runserver 5050"

This will allow us to connect to local port 8000. The link can be copy and pasted into browser of choice to display project

# Creating Apps
An application is ran from an environment

Procedure to create a django app on a server: #cmd
1. change directory into PROJECTNAME (cd PROJECTNAME)
2. use command "python manage.py startapp APPNAME"
3. Rerun server using procedure above

Creates a new directory inside PROJECTNAME directory at same level as manage.py

# Views
Views can be thought of as a **web page**. 

The code in a PROJECTNAME/main/views.py handles the https requests and shows it on website #folderstructure

always add to the header: 
from django.http import HttpResonse #imports

Views are added as functions with a return of HttpResponse(HTML Code)
ex: 
	def index(response): #views
		return HttpResponse("<h1>this is a header!</h1>")

# urls

urls are stored inside the main folder in a python script called urls.py (you will need to create this) #folderstructure

urls.py define the paths to the different web pages (or views)

at the top of the urls.py include:
from django.urls import path #imports 

from . import views [[python]]    (this imports every view from current directory)

#urlpatterns
This function is added to urls.py under the imports
urlpatterns=[
path("", views.index, name="index"),
]

This function means that home path (" ") directs the user to the views.index page which is the index function defined in the main / views.py function!


# linking applications to project
to points apps (main folder, and any other app you have on the project) to the project you have to open the urls.py file from the PROJECTNAME folder.

modify the import from djano.urls import path to:
	from djano.urls import path, include


# navigating to the home page
if a path call in #urlpatterns is left blank then it will be the home page. e.g.:

urlpatterns = [
	path("", include("main.urls"))
]

This means that if there is no path it will automatically direct to the main/urls.py file. This opens the main urls.py file and cross references against the url patterns function define in there. The path with the matching path is the homepage. In this instance (from function above is views.index.