#  take note of <b>Writing your first Django app, part 2</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/tutorial02/

## Use Default Database and Migrate
```
$ python manage.py migrate
```
- 這時再訪問 http://localhost:8000/admin 就正常，有個登入的頁面
  - 會帶到 http://localhost:8000/admin/login/?next=/admin/
- 這算是 Django 的特色之一，有立即可用的admin

## Create polls Model
### polls/models.py
```
from django.db import models

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```

## Activate polls Model
### edit INSTALLED_APPS
### mysite/settings.py
```
INSTALLED_APPS = [
    'polls.apps.PollsConfig',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

## Django Shell Interactive Mode
### (1)可以用來檢查驗証 API，修改 Class，仍要重新進入 shell 才有效。
### (2)反覆打指令其實蠻煩的，用腳本比較科學。


```
$ python manage.py shell


C:\2016-djangoproject\mysite>python manage.py shell
Python 3.5.2 (v3.5.2:4def2a2901a5, Jun 25 2016, 22:01:18) [MSC v.1900 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from polls.models import Question, Choice
>>> Question.objects.all()
[]
>>> from django.utils import timezone
>>> q = Question(question_text="What's new?", pub_date=timezone.now())
>>> q.save()
>>> q.id
1
>>> q.question_text
"What's new?"
>>> q.pub_date
datetime.datetime(2016, 7, 25, 10, 41, 24, 466366, tzinfo=<UTC>)
>>> q.question_text="What's up?"
>>> q.save()
>>> Question.objects.all()
[<Question: Question object>]
>>>
```

## Django Admin
    python manage.py createsuperuser
    
## Register App polls to admin
### (1) edit polls\admin.py
```
from django.contrib import admin
from .models import Question

admin.site.register(Question)
```
### (2) Refresh admin page, No need to runserver again
### (3) 這時候其實已經可以在頁面增刪改查 Question 了

## 原來 Django 是用來處理 Newsroom
### WordPress 是用來處理 BLOG
