#  take note of <b>Writing your first Django app, part 1</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/tutorial01/

## My Working Environment 

```
C:\2016-djangoproject>python -m django --version
1.9.7

C:\2016-djangoproject>python --version
Python 3.5.2
```

## Create Project mysite 

```
C:\2016-djangoproject>django-admin startproject mysite

C:\2016-djangoproject>tree mysite /F
C:\2016-DJANGOPROJECT\MYSITE
│  manage.py
│
└─mysite
        settings.py
        urls.py
        wsgi.py
        __init__.py
```

## Run Development Server 

```
C:\2016-djangoproject\mysite>python manage.py runserver
Performing system checks...

System check identified no issues (0 silenced).

You have unapplied migrations; your app may not work properly until they are applied.
Run 'python manage.py migrate' to apply them.
July 25, 2016 - 13:58:35
Django version 1.9.7, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.

```

## Create App polls 

```
C:\2016-djangoproject\mysite>python manage.py startapp polls

C:\2016-djangoproject\mysite>tree polls /F
C:\2016-DJANGOPROJECT\MYSITE\POLLS
│  admin.py
│  apps.py
│  models.py
│  tests.py
│  views.py
│  __init__.py
│
└─migrations
        __init__.py

```

## Make polls Working
### (1) edit polls/views.py
### (2) cretae polls/urls.py
### (1) edit mysilte/urls.py

## Check Current Status
### (1) http://localhost:8000/polls/

```
中文是不是可以顯示? Hello, world. You're at the polls index.
```

## 心得

### (1) 一個 project 通常有多個 app，訪問 app 通常就是在次目錄。 
    系統自帶有 app admin
### (2) 要一個 view 能正常運行，必需三個地方都做對。 
    是不是可以開發出整合的開發系統?
### (3) 正式環境的掛放不是問題，可以在開發環境安心開發。
    http://www.thecodeship.com/deployment/deploy-django-apache-virtualenv-and-mod_wsgi/


 


