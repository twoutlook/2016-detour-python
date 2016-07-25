#  take note of <b>Writing your first Django app, part 2</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/tutorial02/

## Use Default Database and Migrate
```
$ python manage.py migrate
```
- 這時再訪問 http://localhost:8000/admin 就正常，有個登入的頁面
  - 會帶到 http://localhost:8000/admin/login/?next=/admin/
- 這算是 Django 的特色

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
