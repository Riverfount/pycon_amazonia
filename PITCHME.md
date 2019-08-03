### REST API's with Django and Django Rest Framework

#### A Powerful way to do REST API's

---

@snap[north text-white span-100]
@size[1.3em]@color[#000](Bom, então, quem sou eu?)
@snapend

@snap[west about-team-pic]
![Riverfount](assets/img/FotoPerfilVicente.jpg)
@snapend

@snap[east text-06]
Riverfount, a.k.a. Vicente Marçal
<br><br>
@fa[twitter icones](@vicentemarcal)
<br>@fa[telegram icones](@Riverfount)
<br>@fa[envelope icones](vicente.marcal@gmail.com)
<br>
Professor do Departamento de Filosofia<br>da Universidade Federal de Rondônia<br>Pythonista por Hobby
@snapend

---
### Introduction
- What's a Rest?
- The Constraints|
- The foundations of REST|
- REST vs. SOAP|
- The best practices of HTTP that guide REST|
- Some practices to use our resources|
- References|

---
### What's a REST?

- It had its origin in Roy Fielding' PhD Thesis|
- Roy Fielding was one of the authors of HTTP protocol|
- REST means REpresentational State Transfer|
- REST or RESTFul??|
- Roy proposed some constraints to define the REST architecture|

+++
### The Constraints
- Client-Server
  - The main purpose of this constraint is to separate the responsibilities of each part of the application|
  - Servers are not concerned with the user interface or user state so that servers can be simpler and more scalable.|
  - Servers and clients may also be replaced and developed independently, as long as the interface is not altered.|

+++
### The Constraints
- Stateless
  - Essentially, what this means is that the necessary state to handle the request is contained within the request itself, whether as part of the URI, query-string parameters, body, or headers.|
  - In REST, the client must include all information for the server to fulfill the request, resending state as necessary if that state must span multiple requests.|
  
+++
### The Constraints
- Cacheable
  - As on the World Wide Web, clients can cache responses. Responses must therefore, implicitly or explicitly, define themselves as cacheable, or not, to prevent clients reusing stale or inappropriate data in response to further requests. Well-managed caching partially or completely eliminates some client–server interactions, further improving scalability and performance.|
  
+++
### The Constraints
- Uniform Interface
  - The uniform interface constraint defines the interface between clients and servers. It simplifies and decouples the architecture, which enables each part to evolve independently. The four guiding principles of the uniform interface are:|
    - Resource-Based: Individual resources are identified in requests using URIs as resource identifiers.|

+++
### The Constraints
- Uniform Interface
  - four guiding principles (continuation)  
    - Manipulation of Resources Through Representations: When a client holds a representation of a resource it has enough information to modify or delete the resource on the server, provided it has permission to do so.|
    - Self-descriptive Messages: Each message includes enough information to describe how to process the message.|

+++
### The Constraints
- Uniform Interface
  - four guiding principles (continuation)  
    - Hypermedia as the Engine of Application State (HATEOAS): Clients deliver state via body contents, query-string parameters, request headers and the requested URI (the resource name). Services deliver state to clients via body content, response codes, and response headers. This is technically referred-to as hypermedia.

+++
### The Constraints
- Layered System
  - A client cannot ordinarily tell whether it is connected directly to the end server, or to an intermediary along the way. Intermediary servers may improve system scalability by enabling load-balancing and by providing shared caches. Layers may also enforce security policies.

+++
### The Constraints
- Code on Demand (optional)
  - Servers are able to temporarily extend or customize the functionality of a client by transferring logic to it that it can execute. Examples of this may include compiled components such as Java applets and client-side scripts such as JavaScript.

---

### The foundations of REST

- The first concept fundamental in REST is the resource
  - Basically, the resource is the most important concept that we need to understand;| 
  - The resource is the set of data that traffics by the protocol;|
  - The resources define how our URLs will be described.|

---

### The foundations of REST

- The second concept fundamental in REST is the representation
  - The representation is the form that the information is exchanged between client and server;| 
  - The representation can be a JSON, XML, HTML, JPG, PNG, MP3, MP4 etc;|

---
### REST vs. SOAP
- REST is an architecture model.
- SOAP is a protocol.

| REST                                        | SOAP                                    | 
|---------------------------------------------|-----------------------------------------|
| architecture model                          | Protocol                                |
| Simple HTTP Request                         | Invokes services by calling RPC method  |
| Support many types like XML, JSON, and YAML | Support only XML                         |

---
### The best practices of HTTP that guide REST

- Appropriate use of HTTP methods;
  - GET, POST, PUT, PUSH and DELETE (but not only!!)
- Appropriate use of URLs; |
- Appropriate use of HTTP status code to represent success or fails;|
  - The families: 100, 200, 300, 400 and 500|
- Appropriate use of HTTP headers;|
- The possibility to link various different resources.|

---
#### Some practices to use our resources - 1:

1 Use nouns, not verbs
   - The resources are a set of data about somewhere or something, then use nouns not verbs, 
   e.g. as follow 

<br>

| Resource  | GET read               | POST create              | PUT update             | DELETE                 |
|-----------|------------------------|--------------------------|------------------------|------------------------|
| /cars     | Returns a list of cars | Create a new car         | Bulk update of cars    | Delete all cars        |
| /cars/711 | Returns a specific car | Method not allowed (405) | Updates a specific car | Deletes a specific car |

---
#### Some practices to use our resources - 2a:

2 The HTTP methods
  - The best practice in REST is the appropriate use of HTTP methods: GET, POST, PUT, PUSH and DELETE|
  - GET: This method is used to return a list of all objects of our resource or all data about a specific object of our resource, to return a specific object we use the ID of it.|
  - POST: This method is used to create a new instance of an object into our resource.|

---
#### Some practices to use our resources - 2b:

2 The HTTP methods
  - PUT: This method is used to update all data of a specific object of our resource.|
  - PUSH: This method is similar to PUT, but it can update a partial data of a specific object of our resource.|
  - DELETE: Well, with this method we can delete all objects of our resource, if we call it into a root of our resource, or we can delete a specific object of our resource with its ID.|

---
#### Some practices to use our resources - 3:
3 GET method and query parameters should not alter the state of our resources
  - To alter the state of our resources we shold use the POST, PUT, PUSH or DELETE methods;|
  - The common error is use something like:|
    - GET /cars/711?activate|
    - GET /cars/711/activate|
  - That is not a good practice, the GET method is used to return a list of all objects or a specific object with its ID|
  
---
#### Some practices to use our resources - 4a:
4 Use HTTP status code
  - The HTTP standard provides over 70 status codes to describe the return values. 
  - We don’t need them all, but  there should be used at least a mount of 10:|
  - Family 200:|
    - 200 – OK – Eyerything is working|
    - 201 – OK – New resource has been created|
    - 204 – OK – The resource was successfully deleted|

---
#### Some practices to use our resources - 4b:
4 Use HTTP status code
  - Family 300:
    - 304 – Not Modified – The client can use cached data|
  - Family 400:|
    - 400 – Bad Request – The request was invalid or cannot be served. The exact error should be explained in the error payload. E.g. "The JSON is not valid"|
---
#### Some practices to use our resources - 4c:
4 Use HTTP status code
  - Family 400:    
    - 401 – Unauthorized – The request requires an user authentication|
    - 403 – Forbidden – The server understood the request, but is refusing it or the access is not allowed.|
    - 404 – Not found – There is no resource behind the URI.|
  
---
#### Some practices to use our resources - 4d:
4 Use HTTP status code
  - Family 400:
    - 405 – Method not allowed – Indicates that the request method is known by the server but has been disabled and cannot be used.|
    - 422 – Unprocessable Entity – Should be used if the server cannot process the enitity, e.g. if an image cannot be formatted or mandatory fields are missing in the payload.|
---
#### Some practices to use our resources - 4e:
4 Use HTTP status code
  - Family 500:
    -  500 – Internal Server Error – API developers should avoid this error. If an error occurs in the global catch blog, the stracktrace should be logged and not returned as response.
---
### References

- Fielding, Roy Thomas. [Representational State Transfer (REST)](http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm). In: Architectural Styles and the Design of Network-based Software Architectures. Doctoral dissertation, University of California, Irvine, 2000.
- Mozilla Developer Network - [HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- [REST: Construa API's inteligentes de maneira simples](https://www.casadocodigo.com.br/products/livro-rest)
- [RESTful Web APIs: Services for a Changing World](https://www.amazon.com.br/RESTful-Web-APIs-Services-Changing-ebook/dp/B00F5BS966?__mk_pt_BR=ÅMÅŽÕÑ&crid=1BZRSA6D9SLUW&keywords=Restful+Web+API&qid=1523476637&sprefix=django+rest+fra%2Caps%2C276&sr=8-2&ref=sr_1_2)

---
### References

- [Django RESTful Web Services: The easiest way to build Python RESTful APIs and web services with Django](https://www.amazon.com.br/Django-RESTful-Web-Services-services-ebook/dp/B079GZ949B?__mk_pt_BR=ÅMÅŽÕÑ&crid=1RJDGXRK5MIC9&keywords=django+restful+web+services&qid=1523476696&sprefix=Django+Restful%2Cdigital-text%2C284&sr=8-1-fkmrnull&ref=sr_1_fkmrnull_1)
- [http://www.restapitutorial.com](http://www.restapitutorial.com)
- [Entendendo e documentando REST / RESTful APIs](https://www.udemy.com/restful-apis/learn/v4/overview)


---
## REST API's with Django and Django Rest Framework

### Second Part - Bulding API only in Django

---
### Introdução
- Objetivo: apresentar como podemos construir em Django uma RESTfull API sem o auxílio de um framework auxiliar
- Configuração do ambiente e instalação das ferramentas |
- Criação do projeto e da app com o Django |
- Construção da API: models, views e urls |

---
### Configuração do ambiente

@title[O básico do ambiente]

O básico do ambiente

```bash
> mkdir drf_api
> cd drf_api
drf_api> python3 -m venv .venv
drf_api> source .venv/bin/activate
(.venv) drf_api>
```

@[1]
@[2]
@[3]
@[4]
@[5]


---
#### Instalando as ferramentas 

@title[O uso do pip]
O uso do *pip*

```bash
(.venv) drf_api> pip install Django
...
Installing collected packages: pytz, django
Successfully installed django-2.0.5 pytz-2018.4
(.venv) drf_api> pip install python-decouple
Collecting python-decouple
Installing collected packages: python-decouple
Successfully installed python-decouple-3.1
(.venv) drf_api> pip install dj-database-url
...
Installing collected packages: dj-database-url
Successfully installed dj-database-url-0.5.0
(.venv) drf_api> pip install gunicorn
...
Installing collected packages: gunicorn
Successfully installed gunicorn-19.8.1
(.venv) drf_api> pip install psycopg2
...
Installing collected packages: psycopg2
Successfully installed psycopg2-2.7.4
(.venv) drf_api>
```

@[1-4]
@[5-8]
@[9-12]
@[13-16]
@[17-21]


---
### Mantendo os requisitos da nossa aplicação

@title[Criando nosso requirements.txt]

Criando nosso requirements.txt

```bash
(.venv) drf_api> pip freeze
dj-database-url==0.5.0
Django==2.0.5
gunicorn==19.8.1
psycopg2==2.7.4
python-decouple==3.1
pytz==2018.4
(.venv) drf_api> pip freeze > requirements.txt
(.venv) drf_api>
```

@[1]
@[2-7]
@[8-9]


---
### Criando o projeto no Django

@title[Projeto vmtodo no Django]

Projeto *vmtodo* no Django
```Bash
(.venv) drf_api> django-admin startproject vmtodo .
(.venv) drf_api>
```

@[1]
@[2]

---
#### Criando nossa aplicação no Django

@title[A app core]

A app *core*

```bash
(.venv) drf_api> python manage.py startapp core
(.venv) drf_api>
```

@[1]
@[2]

---
#### Nossa estrutura de arquivos após as criações do projeto e da app core

@title[Estrutura dos Arquivos]

Estrutura dos Arquivos

```bash
(.venv) drf_api> tree
.
├── LICENSE
├── manage.py
├── README.md
├── requirements.txt
└── vmtodo
    ├── core
    │   ├── admin.py
    │   ├── apps.py
    │   ├── __init__.py
    │   ├── migrations
    │   │   ├── __init__.py
    │   ├── models.py
    │   ├── templates
    │   ├── tests.py
    │   └── views.py
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

@[1]
@[3]
@[4]
@[5]
@[6]
@[7-8, 18-21]
@[8-17]

---
#### Instalando nossa app no Django

@title[settings.py - Installed Apps]

settigs.py - Installed Apps

```python
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'vmtodo.core', ## Aqui inserimos nossa app!!!
]

```

@[1-9]
@[10]

---
#### Desabilitando o CSRF

@title[settings.py - Middleware]

settings.py - Middleware

```python
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    # 'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```

@[5]

---
### Configurações gerais do Django

- Obviamente que precisamos usar as libs que importamos com o *python-decouple* e o *dj-database-url* para fazer as configurações necessárias no Django, principalmente para a separação entre instâncias de nossa aplicação. Veremos isso quando implementarmos esse código daqui a pouco.

---
#### Criando nosso Model e ModelForm

@title[models.py]

models.py

```python
from django import forms
from django.db import models


class Tasks(models.Model):
    task = models.CharField(max_length=100)
    disable = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True, )

    class Meta:
        verbose_name = 'Tarefa'
        verbose_name_plural = 'Tarefas'
        ordering = ('-created_at',)

    def __str__(self):
        return self.task


class TaskForm(forms.ModelForm):
    class Meta:
        model = Tasks
        fields = 'task disable'.split()

```

@[1-2]
@[5-8]
@[10-13]
@[15-16]
@[19-22]

---
#### Configurando nossas rotas (endpoints)

@title[urls.py]

urls.py

```python
from django.contrib import admin
from django.urls import path

from vmtodo.core.views import get_post_tasks, 
                              get_delete_put_task_datail

urlpatterns = [
    path('api/v1/tasks/', get_post_tasks),
    path('api/v1/tasks/<int:pk>', 
        get_delete_put_task_datail),
    path('admin/', admin.site.urls),
]
```

@[1-2]
@[4-5]
@[7-12]
@[8]
@[9-10]
@[11]

---
#### O coração de nossa API

@title[views.py]

views.py

```python
import json
from django.forms import model_to_dict
from django.http import JsonResponse
from vmtodo.core.models import Tasks, TaskForm


def get_post_tasks(request):
    if request.method == 'GET':
        obj = list(Tasks.objects.all().values())
        return JsonResponse(obj, safe=False)
    elif request.method == 'POST':
        form = TaskForm(request.POST)
        if form.is_valid():
            form.save()
            return JsonResponse(data=form.data, status=201)
        else:
            return JsonResponse(data={
                                'message': 'Invalid format'
                                }, 
                                status=400)


def get_delete_put_task_datail(request, pk):
    if request.method == 'GET':
        try:
            obj = model_to_dict(Tasks.objects.get(pk=pk))
            return JsonResponse(data=obj, safe=False)
        except Tasks.DoesNotExist:
            return JsonResponse(data={
                                'message': 'Task not found'
                                },
                                status=404)
    elif request.method == 'DELETE':
        obj = Tasks.objects.filter(pk=pk).delete()
        if obj[0]:
            data = {
              'message': 'Task was deleted with success!'
            }
        else:
            data = {
              'message': 'Object does not found!'
            }
        return JsonResponse(data=data, status=204)
    elif request.method == 'PUT':
        task = Tasks.objects.get(pk=pk)
        put_data = json.loads(request.body)
        put_data['id'] = pk
        form = TaskForm(instance=task, data=put_data)
        if form.is_valid():
            form.save()
            return JsonResponse(data=form.data, status=204)
        else:
            return JsonResponse(data={
                                'message': 'Invalid format'
                                },
                                status=400)
```

@[1] 
@[2]
@[3]
@[4]
@[7-20]
@[8-10]
@[9]
@[10]
@[11-20]
@[12]
@[13]
@[14]
@[15]
@[16-20]
@[23-55]
@[24-32]
@[26-27]
@[29-32]
@[33-43]
@[34]
@[35-38]
@[39-42]
@[43]
@[44-56]
@[45]
@[46-47]
@[48]
@[49-51]
@[52-56]

---
## REST API's with Django and Django Rest Framework

#### Third Part - Bulding API in Django with Djanto Rest Framework (Finally!!)

---
### Introdução
- **Objetivo**: apresentar como construir em Django uma RESTfull API com o auxílio do Django Rest Framework (DRF)
- Instalação do DRF|
- Criação da app com o Django e DRF|
- Construção da API: models, views, serializers e urls |

---
### Intalação do Django Rest Framework

@title[Um simples `pip install`]

Um simples `pip install`

```bash
(.venv) drf_api> pip install djangorestframework
...
Installing collected packages: djangorestframework
Successfully installed djangorestframework-3.8.2
(.venv) drf_api>
```

@[1]
@[2-4]
@[5]

---
### Mantendo os requisitos da nossa aplicação

@title[Atualizando nosso requirements.txt]

Atualizando nosso requirements.txt

```bash
(.venv) drf_api> pip freeze
dj-database-url==0.5.0
Django==2.0.5
djangorestframework==3.8.2
gunicorn==19.8.1
psycopg2==2.7.4
python-decouple==3.1
pytz==2018.4
(.venv) drf_api> pip freeze > requirements.txt
(.venv) drf_api>
```

@[1]
@[2-8]
@[4]
@[9-10]


---
### O projeto no Django

@title[Projeto vmtodo e app core criados na apresntação anterior]

Projeto vmtodo e app core criados no Django
```bash
(.venv) drf_api> tree
.
├── LICENSE
├── manage.py
├── README.md
├── requirements.txt
└── vmtodo
    ├── core
    │   ├── admin.py
    │   ├── apps.py
    │   ├── __init__.py
    │   ├── migrations
    │   │   ├── __init__.py
    │   ├── models.py
    │   ├── templates
    │   ├── tests.py
    │   └── views.py
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```
@[1]
@[2-7]
@[8-21]


---
#### Criando nossa aplicação no Django

@title[A app drf]

A app *drf*

```bash
(.venv) drf_api> python manage.py startapp drf
(.venv) drf_api>
```

@[1]
@[2]

---
#### Nossa estrutura de arquivos após de nossa nova app

@title[Estrutura dos Arquivos]

Estrutura dos Arquivos

```bash
(.venv) drf_api> tree
.
├── LICENSE
├── manage.py
├── README.md
├── requirements.txt
└── vmtodo
    ├── core
    │   (...)
    ├── drf
    │   ├── admin.py
    │   ├── apps.py
    │   ├── __init__.py
    │   ├── migrations
    │   ├── models.py
    │   ├── tests.py
    │   └── views.py
    │   (...)
```
@[10-18]

---
#### Instalando nossa app e o DRF no Django

@title[settings.py - Installed Apps]

settigs.py - Installed Apps

```python
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'rest_framework',
    'vmtodo.core',
    'vmtodo.drf',
]

```

@[1-9]
@[10]
@[11]
@[12]

---
#### Sobre a Desabilitação do CSRF

@title[settings.py - Middleware]

settings.py - Middleware

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

@[5]

---
#### Criando nosso Model

@title[models.py]

models.py

```python
from django.db import models


class Tasks(models.Model):
    task = models.CharField(max_length=100)
    disable = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True, )

    class Meta:
        ordering = ('-created_at',)
```

@[1]
@[4-7]
@[9-10]

---
#### Configurando nossas rotas (endpoints)

@title[urls.py]

urls.py

```python
from django.contrib import admin
from django.urls import path

from vmtodo.core.views import get_post_tasks, get_delete_put_task_datail
from vmtodo.drf.views import TaskList, TaskDetails

urlpatterns = [
    path('drf/api/v1/tasks/', TaskList.as_view()),
    path('drf/api/v1/tasks/<int:pk>', TaskDetails.as_view()),
    path('api/v1/tasks/', get_post_tasks),
    path('api/v1/tasks/<int:pk>', get_delete_put_task_datail),
    path('admin/', admin.site.urls),
]
```

@[1-2]
@[4]
@[5]
@[7-13]
@[8]
@[9]
@[10-13]

---
#### O coração de nossa API

@title[core/views.py]

core/views.py

```python
import json
from django.forms import model_to_dict
from django.http import JsonResponse
from vmtodo.core.models import Tasks, TaskForm


def get_post_tasks(request):
    if request.method == 'GET':
        obj = list(Tasks.objects.all().values())
        return JsonResponse(obj, safe=False)
    elif request.method == 'POST':
        form = TaskForm(request.POST)
        if form.is_valid():
            form.save()
            return JsonResponse(data=form.data, status=201)
        else:
            return JsonResponse(data={
                                'message': 'Invalid format'
                                },
                                status=400)


def get_delete_put_task_detail(request, pk):
    if request.method == 'GET':
        try:
            obj = model_to_dict(Tasks.objects.get(pk=pk))
            return JsonResponse(data=obj, safe=False)
        except Tasks.DoesNotExist:
            return JsonResponse(data={
                                'message': 'Task not found'
                                },
                                status=404)
    elif request.method == 'DELETE':
        obj = Tasks.objects.filter(pk=pk).delete()
        if obj[0]:
            data = {
              'message': 'Task was deleted with success!'
            }
        else:
            data = {
              'message': 'Object does not found!'
            }
        return JsonResponse(data=data, status=204)
    elif request.method == 'PUT':
        task = Tasks.objects.get(pk=pk)
        put_data = json.loads(request.body)
        put_data['id'] = pk
        form = TaskForm(instance=task, data=put_data)
        if form.is_valid():
            form.save()
            return JsonResponse(data=form.data, status=204)
        else:
            return JsonResponse(data={
                                'message': 'Invalid format'
                                },
                                status=400)
```

@[1-4]
@[7-20]
@[23-56]

---
#### O coração de nossa API - Views e Serializers

@title[serializers.py]

serializers.py

```python
from rest_framework import serializers
from vmtodo.drf.models import Tasks


class TaskSerializer(serializers.ModelSerializer):
    class Meta:
        model = Tasks
        fields = ('id', 'task', 'disable', 'created_at')

```
@[1] (Impotamos o serializers do drf)
@[2] (Importamos nosso models)
@[5-8] (Criamos a Classe TaskSerializer que ficará responsável pela serialização e deserialização)
@[6] (Criamos uma Classe Meta)
@[7] (Definimos qual o model a ser utilizado)
@[8] (Definimos quais os campos queremos que sejam utilizados)
---
#### O coração de nossa API - Views e Serializers

@title[drf/views.py]

drf/views.py

```python
from vmtodo.drf.models import Tasks
from vmtodo.drf.serializers import TaskSerializer
from rest_framework import generics


class TaskList(generics.ListCreateAPIView):
    queryset = Tasks.objects.all()
    serializer_class = TaskSerializer


class TaskDetails(generics.RetrieveUpdateDestroyAPIView):
    queryset = Tasks.objects.all()
    serializer_class = TaskSerializer

```
@[1](Importamos nosso models)
@[2](Importamos nosso serializer)
@[3](Importamos a classe Generics do DRF)
@[6-8](Definmos nossa classe para o GET e POST)
@[7](Construímos uma queryset)
@[8](Definimos qual serializer utilizar)
@[11-13](Definimos nossa classe para o Get, PUT e DELETE)
@[12](Construímos uma queryset)
@[13](Definimos qual serilizer utilizar)
---
## Vamos aos testes!!


---
## Obrigado

