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
 
 * app.py is app own configuration file. 
 * admin.py is a configuration file for build in Django Admin app
 * migrations tracks the changes in models to keep the database sync with models. 
 * models.py there is where you write database models. Django automatically converts these models into database tables.
 * test.py is for app-specific tests
 * views.py is where we handle request / response logic for our web app.
 
 Even though our new app exists in Django project, Django doesnt know about it until we explicitly add it. 
 
 
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
 
 
