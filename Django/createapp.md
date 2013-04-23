##Create an Application
The web site thus far is just a container for applications.  We are now going to create a blog application.  So to scaffold the application we use the django cli to  create an application:

```py
	./manage.py startapp blog
```
A new folder is created within the 'mysite' container called 'blog' with files for the model and view code for the application.  We now need to include this application as part of the 'mysite' project.  Edit the "/mysite/setting.py" file by finding the "INSTALLED_APPS" section and add the 'blog' applicaiton as follows 

```py
INSTALLED_APPS = (
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.sites',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',
```

