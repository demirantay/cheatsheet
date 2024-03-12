# Django Cheatsheet

https://docs.djangoproject.com/en/3.2/topics/

Table of Contents:
- [Installing Django](#installing-django)
- [Models and Databases](#models-and-databases)
  - [Models]()
- ...

### Installing Django

```
$ pip install Django
```
- Always set up a database if you are going to develop a big project and sqlite is not enough.


# Models and Databases

Generally, each model maps to a single database table. Each model is a Python class that subclasses `django.db.models.Model`. 

In order to use models always:
  - Include the app in settings INSTALLED_APPS
  - run - `manage.py makemigrations`
  - run - `manage.py migrate` 

### Models

```python
from django.db import models

class Person(models.Model):
    # if you add a primary key you override the pk
    id = models.BigAutoField(primary_key=True)
   
   # basic fields from django model class
   first_name = models.CharField(max_length=30)
    release_date = models.DateField()
    num_stars = models.IntegerField()
    text_area = models.TextField()
    
    # Photo
    profile_photo = models.ImageField(
        upload_to="profile_photo/", blank=True, null=True
    )
    
    # select, choice fields
    SHIRT_SIZES = (
        ('S', 'Small'),
        ('M', 'Medium'),
        ('L', 'Large'),
    )
    shirt_size = models.CharField(max_length=1, choices=SHIRT_SIZES)

    # META DATA
    class Meta:
        ordering = ["horn_length"]
        verbose_name_plural = "oxen"
        
    
    # Always keep your data methods full, so that
    # the business logic is kept in a single space
    # so that you can use in other views .etc
    def baby_boomer_status(self):
        "Returns the person's baby-boomer status."
        import datetime
        if self.birth_date < datetime.date(1945, 8, 1):
            return "Pre-boomer"
        elif self.birth_date < datetime.date(1965, 1, 1):
            return "Baby boomer"
        else:
            return "Post-boomer"

    @property
    def full_name(self):
        "Returns the person's full name."
        return '%s %s' % (self.first_name, self.last_name)
        
        
    # Overriding predefined model methods like .save(), delete()
    def save(self, *args, **kwargs):
        do_something()
        super().save(*args, **kwargs)  # Call the "real" save() method.
        do_something_else()

```
Relationships:
```python
from django.db import models

# Many-to-one
class Manufacturer(models.Model):
    pass

class Car(models.Model):
    manufacturer = models.ForeignKey(Manufacturer, on_delete=models.CASCADE)
    
 
# Many-to-Many
class Topping(models.Model):
    pass

class Pizza(models.Model):
    toppings = models.ManyToManyField(Topping)
    

# One-to-One
class User(models.Model):
    pass

class UserProfile(models.Model):
    user = models.OneToOneField(User)
```

### Making Queries

```python
# Creates Object
>>> from blog.models import Blog
>>> b = Blog(name='Beatles Blog', tagline='All the latest Beatles news.')
>>> b.save()

# To perform an update on a data in database
>>> b5.name = 'New name'
>>> b5.save()

# Retrieveing all objets
>>> all_entries = Entry.objects.all()

# For filtering objects
>>> Entry.objects.filter(pub_date__year=2006)

# Chaining filters
>>> Entry.objects.filter(
...     headline__startswith='What'
... ).exclude(
...     pub_date__gte=datetime.date.today()
... ).filter(
...     pub_date__gte=datetime.date(2005, 1, 30)
... )

# Retrieving a single object
>>> one_entry = Entry.objects.get(pk=1)

# Deleting objects
>>> e.delete()

# Limiting Queryset
>>> Entry.objects.all()[5:10]

# To lookup the fields of models from foreign key 
# or ther relationships use double underscores `__`
>>> Blog.objects.filter(entry__headline__contains='Lennon')

# Querying JSON Field
>>> Dog.objects.create(name='Rufus', data={
...     'breed': 'labrador',
...     'owner': {
...         'name': 'Bob',
...         'other_pets': [{
...             'name': 'Fishy',
...         }],
...     },
... })
<Dog: Rufus>
>>> Dog.objects.create(name='Meg', data={'breed': 'collie', 'owner': None})
<Dog: Meg>
>>> Dog.objects.filter(data__breed='collie')
<QuerySet [<Dog: Meg>]>

# Contains query for JSON
>>> Dog.objects.filter(data__contains={'breed': 'collie'})
<QuerySet [<Dog: Meg>]>

# Contained By
>>> Dog.objects.filter(data__contained_by={'breed': 'collie'})
<QuerySet [<Dog: Fred>]>

# Has KEY 
>>> Dog.objects.filter(data__has_key='owner')
<QuerySet [<Dog: Meg>]>


# Complex lookups with Q objects
Q(question__startswith='Who') | Q(question__startswith='What')
# -> same as: WHERE question LIKE 'Who%' OR question LIKE 'What%'
```

### Aggregation

```python
# Total number of books.
>>> Book.objects.count()
2452


# Average price across all books.
>>> from django.db.models import Avg
>>> Book.objects.all().aggregate(Avg('price'))
{'price__avg': 34.35}


# Max price across all books.
>>> from django.db.models import Max
>>> Book.objects.all().aggregate(Max('price'))
{'price__max': Decimal('81.20')}


# Difference between the highest priced book and the average price of all books.
>>> from django.db.models import FloatField
>>> Book.objects.aggregate(
...     price_diff=Max('price', output_field=FloatField()) - Avg('price'))
{'price_diff': 46.85}


# Each publisher, each with a count of books as a "num_books" attribute.
>>> from django.db.models import Count
>>> pubs = Publisher.objects.annotate(num_books=Count('book'))
>>> pubs
<QuerySet [<Publisher: BaloneyPress>, <Publisher: SalamiPress>, ...]>
>>> pubs[0].num_books
73
```

### Raw SQL Queries

The raw() manager method can be used to perform raw SQL queries that return model instances:

__Manager.raw(raw_query, params=(), translations=None)__ 

```python
# Example
>>> for p in Person.objects.raw('SELECT * FROM myapp_person'):
...     print(p)

# Another raw sql example:
>>> Person.objects.raw('''SELECT first AS first_name,
...                              last AS last_name,
...                              bd AS birth_date,
...                              pk AS id,
...                       FROM some_other_table''')


# Sometimes even Manager.raw() isn’t quite enough: you might need to 
# perform queries that don’t map cleanly to models, or directly execute 
# UPDATE, INSERT, or DELETE queries.
from django.db import connection

def my_custom_sql(self):
    with connection.cursor() as cursor:
        cursor.execute("UPDATE bar SET foo = 1 WHERE baz = %s", [self.baz])
        cursor.execute("SELECT foo FROM bar WHERE baz = %s", [self.baz])
        row = cursor.fetchone()

    return row
```

### Transactions

```python
# A common way to handle transactions on the web is to wrap each 
# request in a transaction. Set ATOMIC_REQUESTS to True in the 
# configuration of each database for which you want to enable this behavior.
# When ATOMIC_REQUESTS is enabled, it’s still possible to prevent views from running in a transaction.

from django.db import transaction

@transaction.non_atomic_requests
def my_view(request):
    do_stuff()

@transaction.non_atomic_requests(using='other')
def my_other_view(request):
    do_stuff_on_the_other_database()
    
# atomic is usable both as a decorator:
from django.db import transaction

@transaction.atomic
def viewfunc(request):
    # This code executes inside a transaction.
    do_stuff()
    
# or you can use it as a context manager:
from django.db import transaction

def viewfunc(request):
    # This code executes in autocommit mode (Django's default).
    do_stuff()

    with transaction.atomic():
        # This code executes inside a transaction.
        do_more_stuff()
```

### Multiple Databases

```python
# The first step to using more than one database with Django 
# is to tell Django about the database servers you’ll be using. 
# This is done using the DATABASES setting. 

DATABASES = {
    'default': {
        'NAME': 'app_data',
        'ENGINE': 'django.db.backends.postgresql',
        'USER': 'postgres_user',
        'PASSWORD': 's3krit'
    },
    'users': {
        'NAME': 'user_data',
        'ENGINE': 'django.db.backends.mysql',
        'USER': 'mysql_user',
        'PASSWORD': 'priv4te'
    }
}


# Django requires that a default database entry be defined, 
# but the parameters dictionary can be left blank if it will 
# not be used. To do this, you must set up DATABASE_ROUTERS 
# for all of your apps’ models

# The migrate management command operates on one database at a time.
"""
$ ./manage.py migrate --database=users
$ ./manage.py migrate --database=customers
"""

# Django also provides an API that allows you to maintain complete 
# control over database usage in your code. A manually specified 
# database allocation will take priority over a database allocated by a router.
>>> # This will run on the 'default' database.
>>> Author.objects.all()

>>> # So will this.
>>> Author.objects.using('default').all()

>>> # This will run on the 'other' database.
>>> Author.objects.using('other').all()

>>> my_object.save(using='legacy_users')
```
Django’s admin doesn’t have any explicit support for multiple databases. If you want to provide an admin interface for a model on a database other than that specified by your router chain, you’ll need to write custom ModelAdmin classes that will direct the admin to use a specific database for content.
```python
class MultiDBModelAdmin(admin.ModelAdmin):
    # A handy constant for the name of the alternate database.
    using = 'other'

    def save_model(self, request, obj, form, change):
        # Tell Django to save objects to the 'other' database.
        obj.save(using=self.using)

    def delete_model(self, request, obj):
        # Tell Django to delete objects from the 'other' database
        obj.delete(using=self.using)
        
    # ...
```

# Handling HTTP Requests

```python
# config/urls.py

# At the core module of djangos 
# urls you have to have a set of includes
from django.urls import include, path

urlpatterns = [
    # ... snip ...
    path('community/', include('aggregator.urls')),
    path('contact/', include('contact.urls')),
    # ... snip ...
]


# Another possibility is to include additional URL patterns 
# by using a list of path() instances. For example, consider this URLconf:
from django.urls import include, path

from apps.main import views as main_views
from credit import views as credit_views

extra_patterns = [
    path('reports/', credit_views.report),
    path('reports/<int:id>/', credit_views.report),
    path('charge/', credit_views.charge),
]

urlpatterns = [
    path('', main_views.homepage),
    path('help/', include('apps.help.urls')),
    path('credit/', include(extra_patterns)),
]

```
Once you create urls in your config/urls.py you have to create urls.py for each of your apps:
```python
from django.urls import path

from . import views

urlpatterns = [
    path('articles/2003/', views.special_case_2003),
    path('articles/<int:year>/', views.year_archive),
    path('articles/<int:year>/<int:month>/', views.month_archive),
    path('articles/<int:year>/<int:month>/<slug:slug>/', views.article_detail),
]

# You can also use regular expressions
```
- str - Matches any non-empty string, excluding the path separator, '/'. This is the default if a converter isn’t included in the expression.
- int - Matches zero or any positive integer. Returns an int.
- slug - Matches any slug string consisting of ASCII letters or numbers, plus the hyphen and underscore characters. For example, building-your-1st-django-site.
- uuid - Matches a formatted UUID. To prevent multiple URLs from mapping to the same page, dashes must be included and letters must be lowercase. For example, 075194d3-6885-417e-a8a8-6c931e272f00. Returns a UUID instance
- path - Matches any non-empty string, including the path separator, '/'. This allows you to match against a complete URL path rather than a segment of a URL path as with str.

```python
# You can give namespaces to your urls so that there is less collision
from django.urls import path

from . import views

app_name = 'polls'
urlpatterns = [
    path('', views.IndexView.as_view(), name='index'),
    path('<int:pk>/', views.DetailView.as_view(), name='detail'),
    ...
]

"""
{% url 'polls:index' %}
"""
```

### Writing views

```python
# Lets write a simple view template
from django.shortcuts import render, get_object_or_404, HttpResponse
from django.http import HttpResponseRedirect

def view_name(request):
    """
    view description
    """
    
    # Controller logic ... 

    data = {
        "data_items_for_templates": data_items_for_templates,
    }

    return render(request, "template_name.html", data)
```

### View Decorators

```python

# Django provides several decorators that can 
# be applied to views to support various HTTP features.

# For example: 
@require_http_methods(["GET", "POST"])
def my_view(request):
    # I can assume now that only GET or POST requests make it this far
    # ...
    pass
```
There are many decorators see them full at official docs

### Shortcut functions for views

```python
# The package django.shortcuts collects helper functions 
# and classes that “span” multiple levels of MVC. In other 
# words, these functions/classes introduce controlled 
# coupling for convenience’s sake.

def view_name(request):
  ...
  # Calls get() on a given model manager, but 
  # it raises Http404 instead of the model’s 
  # DoesNotExist exception.
  get_object_or_404(klass, *args, **kwargs)
  
  # Returns the result of filter() on a 
  # given model manager cast to a list, raising 
  # Http404 if the resulting list is empty
  get_list_or_404(klass, *args, **kwargs)
  
  # Returns an HttpResponseRedirect to the 
  # appropriate URL for the arguments passed.
  redirect(to, *args, permanent=False, **kwargs)
  
  # Combines a given template with a given context 
  # dictionary and returns an HttpResponse object
  # with that rendered text
  render(request, template_name, context=None, content_type=None, status=None, using=None)
```

### Middleware

```python
# Middleware is a framework of hooks into Django’s request/response 
# processing. It’s a light, low-level “plugin” system for globally 
# altering Django’s input or output.

def simple_middleware(get_response):
    # One-time configuration and initialization.

    def middleware(request):
        # Code to be executed for each request before
        # the view (and later middleware) are called.

        response = get_response(request)

        # Code to be executed for each request/response after
        # the view is called.

        return response

    return middleware
```
To activate a middleware component, add it to the MIDDLEWARE list in your Django settings.
```python
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```
### Sessions

```python
# simplistic usage of sessions
def login(request):
    m = Member.objects.get(username=request.POST['username'])
    if m.password == request.POST['password']:
        request.session['member_id'] = m.id
        return HttpResponse("You're logged in.")
    else:
        return HttpResponse("Your username and password didn't match."
        

""" Below are session methods prodived by django
exists()
create()
save()
delete()
load()
clear_expired()
"""
```

# Working with Forms

```html
<form method="POST" action="{% url 'viewname' %}">
  <input type="text" name="form_input">
  <input type="submit" name="form_submit_btn">
</form>
```

```python
def viewname(request):
    
    if request.POST.get("form_submit_btn"):
        input = request.POST.get("form_input")
        
        # Proecss the form here

    ...
```

# Templates

This is an overview of the Django template language’s syntax.
```html
<!-- variables -->
<p>My first name is {{ first_name }}. My last name is {{ last_name }}.</p>

<!-- tags for logic -->
{% if user.is_authenticated %}
  Hello, {{ user.username }}.
{% endif %}

<!-- filters -->
{{ django|title }}

<!-- comments -->
{# this won't be rendered #}
```

# Class Based Views

```python
# A view is a callable which takes a request and returns a response. This can be more 
# than just a function, and Django provides an example of some classes which can be 
# used as views. These allow you to structure your views and reuse code by harnessing 
# inheritance and mixins.

# Let's first see a function-based view:
def myview(request):
    if request.method == "POST":
        form = MyForm(request.POST)
        if form.is_valid():
            # <process form cleaned data>
            return HttpResponseRedirect('/success/')
    else:
        form = MyForm(initial={'key': 'value'})

    return render(request, 'form_template.html', {'form': form})
    
# Now lets turn it into CLASS Based
class MyFormView(View):
    form_class = MyForm
    initial = {'key': 'value'}
    template_name = 'form_template.html'

    def get(self, request, *args, **kwargs):
        form = self.form_class(initial=self.initial)
        return render(request, self.template_name, {'form': form})

    def post(self, request, *args, **kwargs):
        form = self.form_class(request.POST)
        if form.is_valid():
            # <process form cleaned data>
            return HttpResponseRedirect('/success/')

        return render(request, self.template_name, {'form': form})
```
You can also use decorators on class views:
```python
decorators = [never_cache, login_required]

@method_decorator(decorators, name='dispatch')
class ProtectedView(TemplateView):
    template_name = 'secret.html'

@method_decorator(never_cache, name='dispatch')
@method_decorator(login_required, name='dispatch')
class ProtectedView(TemplateView):
    template_name = 'secret.html'
```

# Migrations

Migrations are Django’s way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema
- `migrate` -- which is responsible for applying and unapplying migrations.
- `makemigrations` -- which is responsible for creating new migrations based on the changes you have made to your models.
- `sqlmigrate` -- which displays the SQL statements for a migration.
- `showmigrations` -- which lists a project’s migrations and their status.

### Version Control

Because migrations are stored in version control, you’ll occasionally come across situations where you and another developer have both committed a migration to the same app at the same time, resulting in two migrations with the same number.

Don’t worry - the numbers are just there for developers’ reference, Django just cares that each migration has a different name. Migrations specify which other migrations they depend on - including earlier migrations in the same app - in the file, so it’s possible to detect when there’s two new migrations for the same app that aren’t ordered.

### Reversing Migrations

Migrations can be reversed with migrate by passing the number of the previous migration. For example, to reverse migration `books.0003`:
```
$ python manage.py migrate books 0002
```
If you want to reverse all migrations applied for an app, use the name zero:
```
$ python manage.py migrate books zero
```
> A migration is irreversible if it contains any irreversible operations. Attempting to reverse such migrations will raise IrreversibleError:

where i left: https://docs.djangoproject.com/en/3.2/topics/migrations/#data-migrations

# Managing Files

# Testing in Django

# User Authentication in Django

# Django's cache framework

# Conditional view processing

# Cryptographic signing

# Sending Email

# Internationalization and localization

# Logging

# Pagination

# Security in Django

# Performance and optimization

# Serializing Django objects

# Django Settings

# Signals

# Writing your own checks

# External Packages

# Asynchronous support
