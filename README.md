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
