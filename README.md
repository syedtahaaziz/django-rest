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

## Creating an App with Django

Now, we will create our first app with Django.

```
django-admin.py startproject restful01
```

