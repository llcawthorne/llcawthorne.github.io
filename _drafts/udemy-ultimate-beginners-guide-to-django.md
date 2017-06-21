---
layout: post
title: "Udemy - The Ultimate Beginners Guide to Django"
date: 2017-06-
tags: django python video web
---

It starts with a quick refresher on Python syntax.  I found it useful to get
me thinking in Python and not too terribly slow.

Django starts projects a lot leaner than Rails, but it lacks the structure
that a Rails app provides.  Running `django-admin startproject [name]`
only creates a basic project of one subdirectory and about five files.  The
settings.py and urls.py files are the most relevant to getting stuff done.
settings.py contains a number of global settings, and urls.py is used to
route requests.  Both files are well documented with Django project URL's,
if you need the reference.

The urls.py file starts with a mapping for /admin/ and nothing else.  If you
go to an undefined path while in debug mode, the error page points you
towards the urls.py file as where you need to define the route.  Each URL
is a regex matched with a Python function.  Here's the simple Hello World
example.  urls.py:

```python
from django.conf.urls import url
from django.contrib import admin
from . import views

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^hello/', views.hello),
]
```

And views.py in the same directory as urls.py:

```python
from django.http import HttpResponse

def hello(request):
    return HttpResponse("Hello World!")
```

Nothing too crazy.  First thing we want to do is response with HTML instead
of raw text.  You normally make a subdirectory in your main project
directory called "templates" to hold HTML templates.  You have to add the
name of your templates folder to the TEMPLATES DIRS in settings.py.  You
modify your views.py to render a "home.html" template as follows:

```python
from django.http import HttpResponse
from django.shortcuts import render

def hello(request):
    return render(request, 'home.html')
```

So, there's a bit more configuration than getting started with Rails, but
it's all pretty straightforward to get your view to render a template.  So
starting from this base, the video goes on to create the first of three
projects it will be building, a Pig Latin Translator.  It's pretty simple,
but displays some of the basic functionality of Django.

The second project is a personal blog.  It uses the database, unlike the
first project.  It's going to be designed with Bootstrap and use Disqus
for comments.  For this one you also set up a virtual environment with
virtualenv.

Django splits a site into apps to manage complexity.  Each app has its own
models.py, views.py and tests.py files.  Kinda weird putting multiple models
in one models.py file, but it works.  After any changes to a model, you run
`./manage.py makemigrations` and it will automatically create the necessary
migrations.  `./manage.py migrate` will apply unapplied migrations.  The
admin site that is available by default is really nice, but I'm pretty sure
that I'll always forget to register my models before going to it and finding
them missing.  You run `./manage.py createsuperuser` to make an account for
the admin page.

He didn't even split out parts of the page to different templates in the
blog app, but he says he will in the Reddit app.  It was just straight copy
and paste the heads to a couple of different pages.  We've also made it
awfully far into this tutorial with no mention of testing.
