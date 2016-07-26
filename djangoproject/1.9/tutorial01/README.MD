#  take note of <b>Writing your first Django app, part 1</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/tutorial01/

## My Working Environment 
- 確認工作環境
- 創建項目 Project
- 運行開發環境 Web Server
- 創建應用 App/Application
- 套用學習 urlpatterns 
  -  url(r'^$', views.index, name='index'),  
    - r'^$' 是什麼意思? 這是正則表示法的課題
    


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

```
from django.http import HttpResponse

def index(request):
    return HttpResponse("中文是不是可以顯示? Hello, world. You're at the polls index.")
```


### (2) cretae polls/urls.py
```
from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^$', views.index, name='index'),
]

```



### (3) edit mysilte/urls.py

```
from django.conf.urls import url, include
from django.contrib import admin

urlpatterns = [
    url(r'^polls/', include('polls.urls')),
    url(r'^admin/', admin.site.urls),
]
```

## Check Current Status
### (1) http://localhost:8000/polls/

```
中文是不是可以顯示? Hello, world. You're at the polls index.
```

### (2) http://localhost:8000/

```
Page not found (404)
```

### (3) http://localhost:8000/admin

```
OperationalError at /admin/
```



## 心得

### (1) 一個 project 通常有多個 app，訪問 app 通常就是在次目錄。 
    系統自帶有 app admin
### (2) 要一個 view 能正常運行，必需三個地方都做對。 
    是不是可以開發出整合的開發系統?
### (3) 正式環境的掛放不是問題，可以在開發環境安心開發。
- https://docs.djangoproject.com/en/1.9/howto/deployment/wsgi/modwsgi/
- http://www.thecodeship.com/deployment/deploy-django-apache-virtualenv-and-mod_wsgi/


 


