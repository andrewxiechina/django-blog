# django-blog
使用Django搭建一个简单博客

使用下列环境：
- python 3.6.4
- django 2.0.2

### 基本操作

```shell
$ django-admin startproject mysite
$ python manage.py runserver
$ python manage.py startapp polls
```
### View



### Routing

```python
# mysite/urls.py
from django.urls import include, path
from django.contrib import admin

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
```

```python
# polls/urls.py
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

### Model
```python
from django.db import models

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('dat published')

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```

### Database Migration
```
python manage.py makemigrations polls
python manage.py sqlmigrate polls 0001 # No use, give sql
python manage.py migrate
python manage.py shell # Play with db api
```
