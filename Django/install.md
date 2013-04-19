#Web Frameworks

Django is a prominent member of the new generation of Web frameworks.

The old approach to developing dynamic web pages is to use straight cgi scripting to print html lines.

```py
#!/usr/bin/env python

import MySQLdb

print "Content-Type: text/html\n"
print "<html><head><title>Books</title></head>"
print "<body>"
print "<h1>Books</h1>"
print "<ul>"

connection = MySQLdb.connect(user='me', passwd='letmein', db='my_db')
cursor = connection.cursor()
cursor.execute("SELECT name FROM books ORDER BY pub_date DESC LIMIT 10")

for row in cursor.fetchall():
    print "<li>%s</li>" % row[0]

print "</ul>"
print "</body></html>"

connection.close()
```

##The MVC Pattern
The best approach to python web development is to use Django, where we split the development of the application over Python files:

1. models.py, 
* views.py and 
* urls.py

###model.py (Model)
```py
from django.db import models

class User(models.Model):
    firstname = models.CharField(max_length=50)
    lastname = models.CharField(max_length=50)
    mod_date = models.DateField()
```

###views.py (View)
```py
from django.shortcuts import render_to_response
from models import User

def get_users(request):
    user_list = User.objects.order_by('-mod_date')[:10]
    return render_to_response('users.html', {'user_list': user_list})
```

###urls.py (Router or Controller)
```py
from django.conf.urls.defaults import *
import views

urlpatterns = patterns('',
    (r'^users/$', views.get_users),
)
```

### users.html (the template)

```html
<html>
	<head>
		<title>Users</title>
	</head>
	<body>
		<h1>Users</h1>
		<ul>
		{% for user in user_list %}
			<li>{{ user.firstname }} {{user.lastname}}</li>
		{% endfor %}
		</ul>
	</body>
</html>
```

The models.py file contains a description of the database table, represented by a Python class. This class is called a model. Using it, you can create, retrieve, update and delete records in your database using simple Python code rather than writing repetitive SQL statements.
The views.py file contains the business logic for the page. The get_users() function is called a view.
The urls.py file specifies which view is called for a given URL pattern. In this case, the URL /users/ will be handled by the get_users() function. In other words, if your domain is example.com, any visit to the URL http://example.com/users/ will call the get_users() function.
The users.html file is an HTML template that describes the design of the page. It uses a template language with basic logic statements – e.g., {% for user in user_list %}.


##Installation

###Installing Python [(http://www.python.org/download/)](http://www.python.org/download/)
Django itself is written purely in Python, so the first step in installing the framework is to make sure you have Python installed.  

The core Django framework works with any Python version from 2.3 to 2.7, inclusive. If you’re not sure which version of Python to install and you have complete freedom over the decision, pick the latest one in the 2.x series: version 2.7. Although Django works equally well with any version from 2.3 to 2.6, the later versions of Python have performance improvements
and additional language features you might like to use in your applications.

###Installing Django [(https://www.djangoproject.com/download/)](https://www.djangoproject.com/download/)
There are two versions available to you: Lastest official release and the bleeding-edge version.  It recommended that you download the official release.  Unzip the compressed file to a directory and run the following python command: 
```bash
sudo python setup.py install
```
Django will be installed to the "python2x/site-packages" folder.  To test the django installation run the following in the python interpreter:

```py
>>> import django
>>> django.VERSION
(1, 1, 0, 'final', 1)
```

##Starting a Project
Once you’ve installed Python and Django, it's time to start you own project.  Create a folder for your project and run the following command in the project folder:

```py
python <location>/django-admin.py startproject myfirst
```

##Running the Development Server
To start the server, change into your project directory (cd myfirst), if you haven’t already, and run this command:

```py
python manage.py runserver
```

This launches the server locally, on port 8000, accessible only to connections from your own computer. Now that it’s running, visit http://127.0.0.1:8000/ with your Web browser. You’ll see a “Welcome to Django” page shaded in a pleasant pastel blue. It worked!
