# Django-REST Framework

A hands-on guide towards creating RESTful services with Django-REST framework.



## Installations

create a virtual environment for your django project by using the following command. It is assumed that you are running python 3.5 and have install virtual environment. Cretae a new virtual enviroment will help manage the project dependencies.

```
virtualenv django-rest --python=python3
``` 

Activate your enviornment using the following command. 

```
source ~/.virtualenv/django-rest/bin/activate
```

We have created the python light-weight virtual enviroment. Lets run the following commands that will be same for linux and macOS. 


First, lets the run following command to install the django web-framework. 

```
pip install django==1.11.5
```

We have installed the django web framework. lets install the rest-framework for django.

Django REST framework works on top of Django and provide us with powerful and flexible toolkit to build REST-ful web services.

```
pip install --quiet djangorestframework==3.6.4 
```

The ``` --quiet ``` option will hide the unnecessary console details for installing the package.

## Creating a Project

Now, we will create our first project with Django.

```
django-admin.py startproject helloworld
```

if you use tree. you can look at the directory structure of Django project

```
.
├── helloworld_project
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py
``` 

The settings.py file controls our project's settings, url.py tells Django which pages to build in response to url request.
and wsgi.py which stands for web server gateway interface, helps Django to serve our eventual pages. The last file manage.py is used to execute various Django  commands such as running the server. 

Django comes with the build in server. we can start it with the following command.

``` 
python manage.py runserver 
```

## Create an App

Django uses the concept of app and project to keep the code clean and readable. Each app in the project is a single isolated working unit of a project. 
For example for e-commerce project an one app can be made for user authentication , another for paytment and so on. 

```
python manage.py startapp pages 
```
Lets examine the tree structure for pages app.
```
── pages
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── migrations
    │   └── __init__.py
    ├── models.py
    ├── tests.py
    └── views.py
 ```
 Lets review what each new pages app file does.
 
 * ```app.py``` is app own configuration file. 
 * ```admin.py``` is a configuration file for build in Django Admin app
 * ```migrations``` tracks the changes in models to keep the database sync with models. 
 * ```models.py``` there is where you write database models. Django automatically converts these models into database tables.
 * ```test.py``` is for app-specific tests
 * ```views.py``` is where we handle request / response logic for our web app.
 
 Even though our new app exists in Django project, Django doesnt know about it until we explicitly add it. 
 
 In your text editor open settings.py. Add under INSTALLED_APPS our new pages app. 
 
 ``` python 
 INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
	'pages', #new
]
 ```
 
 In Django views determine what content is displayed on the display while url conf determine where the content is going. 
 
 Lets start by editing views.py
 
 ``` python 
 from django.http import HttpResponse
 
 def homePageView(request):
 	return HttpResponse('Hello World')

```
Basically we're saying whenever this homePageView function is called, return the text "Hello World". We've imported build in HttpResponse method so that we can return the response object to the user. 

We have created a function that accepts the request object and returns a response object with "Hello World" string. 

Now, we need to configure our urls. Within the app pages create a new file urls.py. This file will used to handle all the url related to this app. 

```
touch pages/urls.py
```
Edit urls.py with the following code

``` python

from django.urls import path

from . import views 

urlpatterns = [
	path('', views.homePageView, name='home')
]
```

On the top line we've imported path from Django to power our url patterns and on the next line we've imports views. ``` . ``` the dot represents that the ```views.py``` file is in the same directory. 

Our ```urlpatterns``` has three parts: 
*  a Python regular expression for the empty string ```''```.
*  specify the view which is called ```homePageView```
*  add an optional url name of ```home```


 
 
