---
title: "Django"
excerpt_separator: "<!--more-->"
tags: [python, pycharm, jupyter, package, pandas]
#layout: post
#title: Jupyter Notebook
#subtitle: Exercícios e Referências
#tags: [python, pycharm, jupyter, package]
#image: /img/posts/jupyter_icon.png
#bigimg: /img/posts/jupyter_big.png
#gh-repo: michelmetran/package_jupyter
#gh-badge: [follow, star, watch, fork]
#comments: true
---

O _Jupyter Notebook_ é a maneira que optei para escrever os códigos na linguagem _python_, visto que além de rodar os códigos, é possível:

<!--more-->

1. Documentar os _scripts_, escrevendo o significado e objetivo de cada conjunto de comandos;
2. Atualizar os meus repositórios na plataforma **GitHub**;
3. Trabalhar com uma diversidade de opções de exportação do arquivo em formatos diversos, adaptados até mesmo para as simples leitura, como PDFs e Markdowns.

Com tais caraterísticas, notei que é possível publicar _posts_ diretamente do _Jupyter Notebook_. Aqui pretendo apresentar um pouco das funções que tenho explorado para aperfeiçoar e facilitar minhas publicações no meu site pessoal: https://michelmetran.github.io. E, pesquisando pela internet, descobri que não sou o único a [_Exploring Jupyer Notebook to write a Blog_](https://medium.com/gopypi/exploring-jupyer-notebook-to-write-a-blog-1e7eaa913274), tem muito material a ser explorado...

<div class="alert alert-warning">
<b>OBSERVAÇÃO</b><br/>
    Esse <i>post</i> tem a finalidade de mostrar os comandos básicos e me deixar com uma "cola" rápida para meu uso cotidiano.<br/>
    Todas os códigos são exemplificativos e podem/devem ser alterados, indicando o nome dos arquivos e diretórios corretamente.
</div>

<div class="alert alert-info">
<b>INFORMAÇÃO</b><br/>
    <ol>
    <li>É possível acessar esse <i>post</i> em formato <a href="https://rawcdn.githack.com/michelmetran/package_juypter/master/docs/juypter.html" target="_blank"><i><b>html</b></i></a>, que possibilita ter uma visualização rápida do código;</li>
    <li>Diretamente por meio do <a href="https://github.com/michelmetran/package_juypter" target="_blank"><b>repositório</b></a>, onde está disponível este arquivo <i><b>.ipynb</b></i>, que permite fazer edições no código;</li>
    <li>Ou ainda, de maneira interativa, usando o <a href="https://mybinder.org/v2/gh/michelmetran/package_juypter/master" target="_blank"><i><b>MyBinder</b></i></a>, que possibilita rodar e editar o código sem a necessidade de instalar nada.</li>
    </ol>
</div>

```python
import os
import json
import time
import folium
import pandas as pd
from datetime import date
```

<br>

# Install

django-admin --help

Para instalar

```bash
pip3 install django
pip3 install django --upgrade
```

<br>

---

# _Create_

## _Create Project_

Primeira coisa a fazer é criar um projeto com o _framework_ do Django. Isso é feito com o seguinte comando, no terminal:

```bash
django-admin startproject {project name}
cd {project name}
```

<br>

## _Create Aplication_

Uma vez criado o projeto, é necessário adicionar uma aplicação ao projeto, com o comando abaixo.
O nome convencionado **_core_** pode ser alterado. Vi em tutoriais e aprendi assim. Achei adequado, visto que é, de fato, o **_core_** da aplicação.

```bash
python manage.py startapp core
```

Após a criação da aplicação, é necessário lista-la nas configurações do Django, no arquivo settings.py

![Settings](https://i.imgur.com/GbxMFvN.png)

<br>

---

# Runserver

Posteriormente é botar pra rodar com

```bash
python manage.py runserver
```

Um jeito interessante para se trabalhar com o PyCharm é definir o _runserver_ no PyCharm.

![Settings](https://i.imgur.com/46h6ubM.png)

<br>

---

# _Database_

É necessário definir as configurações do banco de dados do projeto.
Criei um tópico especial para tratar dessa questão.

<br>

## PostGres

É necessário criar o banco de dados com os seguintes comandos no terminal.

```sql
psql -U postgres
CREATE DATABASE opentesouro OWNER django_user;
DROP DATABASE opentesouro;
```

<br>

No arquivo **settings.py** é necessário definir as seuintes congigurações.

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'sabesp',
        'USER': 'django_user',
        'PASSWORD': '123456789',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

<br>

E, quando for utilizado o banco de dados _PostGres_, é necessário adicionar no arquivo _requirements.txt_ o

```
psycopg2==2.8.5
```

<br>

## PostGIS

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'sabesp',
        'USER': 'django_user',
        'PASSWORD': '123456789',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

<br>

## MySQL

No requirements.txt deve constar:

```
mysqlclient==1.4.6
sqlalchemy~=1.3.18
sqlparse==0.3.1
```

Code

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'OPTIONS': {
            'read_default_file': '/home/myusername/mysql_django.cnf',
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'",
            'isolation_level': 'read committed',
        },
    }
}
```

**Referência**

- https://averyuslaner.com/configuring-mysql-django/

<br>

## SQLite

```python
DATABASES = DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

No requirements.txt deve constar:

```

```

<br>

## Outros

- [How to Reset Migrations](https://simpleisbetterthancomplex.com/tutorial/2016/07/26/how-to-reset-migrations.html)
- [YouTube: Python Django with Firebase: Database Rules allow only Authenticated Users to Read | Write access](https://www.youtube.com/watch?v=yhYCoejo16g)

<br>

---

# Models.py

https://docs.djangoproject.com/en/3.0/ref/models/

```python
class Evento(models.Model):
    id = models.AutoField(primary_key=True)
    titulo = models.CharField(max_length=100)
    descricao = models.TextField(blank=True, null=True)
    data_evento = models.DateTimeField(verbose_name='Data do Evento')
    data_criacao = models.DateTimeField(auto_now=True, verbose_name='Data da Criação')
    usuario = models.ForeignKey(User, on_delete=models.CASCADE)

    class Meta:
        db_table = 'evento'

    def __str__(self):
        return self.titulo
```

Algumas das opções que podem ser contidas no banco de dados são:

```python
auto_created=True,
primary_key=True,
serialize=False,
verbose_name='ID'
```

<br>

---

# Admin.py

Uma vez criado o modelo de dados, é preciso registra-lo no arquivo admin.py, podendo ser configurado ainda a lista das colunas que irão aparecer na aba do adminstrados, bem como as opções para filtrar os dados.

```python
from django.contrib import admin
from core.models import serie_historica

# Register your models here.
class CoreAdmin(admin.ModelAdmin):
    list_display = ('data', 'descricao', 'pu_compra')
    list_filter = ('descricao',)

admin.site.register(serie_historica, CoreAdmin)
```

<br>

---

# Apps.py

No painel de administração, é possível ajustar o nome da aplicação usando o verbose name

```python
from django.apps import AppConfig

class CoreConfig(AppConfig):
    name = 'core'
    verbose_name = 'Bando de Dados'
```

<br>

Para isso é necessário inserir o comando abaixo no arquivo **_**init**.py_**

```python
default_app_config = 'core.apps.CoreConfig'
```

<br>

**Referências**

https://docs.djangoproject.com/en/3.1/ref/applications/

<br>

---

# _Migrations_

<br>

## _Make Migrations_

Não migra os models às cegas

```bash
python manage.py makemigrations
python manage.py makemigrations {app name}
python manage.py makemigrations core
```

<br>

## _SQL Migrate_

Gera os códigos que deverão ser gerados para criar as tabelas no banco de dados...
Mais transparência...

```bash
python manage.py sqlmigrate
python manage.py sqlmigrate core 0001
```

<br>

## _Migrate_

```bash
python manage.py migrate
```

<br>

---

# _Create Superuser_

Uma ver criado o superusuário, com o comando abaixo, é possível acessar o painel de administração dos usuários e modelos no [127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

```bash
python manage.py createsuperuser --email admin@example.com --username admin
python manage.py createsuperuser --email michelmetran@gmail.com --username michelmetran
```

<br>

---

# _Templates_

Criar pasta _templates_ na raiz do projeto.
Registra a pasta _templates_ no arquivo _settings.py_, usando o comando

```python
(os.path.join(BASE_DIR, 'templates'))
```

<br>

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [(os.path.join(BASE_DIR, 'templates'))],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

<br>

Inicialmente, usando o pyCharm, crie um arquivo chamado index.html, apenas para testes.

Criei três arquivos de modelo do HTML:

- \_footer.html
- \_header.html
- \_page.html

Eles serão acessórios de outros que chamar.

<br>

**Referências**

- [Django: **builtins**](https://docs.djangoproject.com/en/3.0/ref/templates/builtins/)

<br>

---

# _Static_

Para fazer com que o Django utiliza arquivos estáticos, usualmente acessários para renderizar os arquivos HTML, tais ocmo _css_, _javascript_, _fonts_, _imagens_ etc, é necessário ajustar alguns parâmetros no arquivo _settings_, conforme abaixo:

```python
# Static files (CSS, JavaScript, Images)
# The URL which will serve static files
STATIC_URL = '/static/'

# Where to look to search
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'dados/static_app'),
    os.path.join(BASE_DIR, 'sabesp/static_app'),
]

# Where locate files, and comment the AppDirectoriesFinder
STATICFILES_FINDERS = [
    'django.contrib.staticfiles.finders.FileSystemFinder',
    'django.contrib.staticfiles.finders.AppDirectoriesFinder',
]

# Name of dir that will be create
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
```

<br>

Ainda, na sessão **_Middleware_**, é necessário acrescentar o comando `'whitenoise.middleware.WhiteNoiseMiddleware'`, conforme é apresentado abaixo.

```python
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'whitenoise.middleware.WhiteNoiseMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```

<br>

Comando para reunir todos os arquivos na pasta definida em STATIC_ROOT

```bash
python manage.py collectstatic
```

<br>

É possivel procurar a fonte de um arquivo, ou seja, qual o local que ele está buscando o arquivo:

```bash
python manage.py findstatic css/base.css admin/js/core.jspython manage.py
```

<br>

## WhiteNoise

http://whitenoise.evans.io/en/stable/

<br>

**Referências**

- [YouTube: **Try Django 1.9 - 25 of 38 - Setup Static Files - CSS & Javascript & Images in Django**](https://www.youtube.com/watch?v=YH-ipgxlJzs)
- [YouTube: **Understanding Django Static Files**](https://www.youtube.com/watch?v=w9F9k-JHvcQ)
- [Medium: **Understanding static files in Django + Heroku**](https://medium.com/@vonkunesnewton/understanding-static-files-in-django-heroku-1b8d2f003977)
- [Heroku Dev Center: **Django and Static Assets**](https://devcenter.heroku.com/articles/django-assets)
- [Django: **Static Files**](https://docs.djangoproject.com/en/3.0/howto/static-files/)
- [StackOverflow: **Found another file with the destination path - where is that other file?**](https://stackoverflow.com/questions/35571256/found-another-file-with-the-destination-path-where-is-that-other-file)

<br>

---

# URLs

<br>

## _Redirect_

Usualmente as URLs do site são definidas no arquivo `{project name}/urls.py`.
Dessa forma, é possível fazer roteamento e redirecionamento/redirect das urls, quando definido um caminha em branco ('').

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('agenda/', views.lista_eventos),
    path('', views.index),
]
```

Para que isso dê certo, no arquivo **view** é preciso criar a função que faz o redirecionamento para outra view pré-existente.

```python
from django.shortcuts import render, redirect

def index(request):
    return redirect('/agenda/')
```

Outra alternativa é fazer o redirect já no arquivos urls, sem precisar criar função no views para isso.

```python
from django.views.generic import RedirectView

urlpatterns = [
    path('admin/', admin.site.urls),
    path('agenda/', views.lista_eventos),
    path('', RedirectView.as_view(url='/agenda/')),
]
```

<br>

## URLs da _Application_

Uma saída bastante elegante é definir as urls em um arquivo _urls.py_ a ser criado dentro do diretório da aplicação. Para que isso funcione, no arquivo ulrs do projeto é necessário incluir todas as urls que serão listadas na aplicação. Ainda, é necessário fazer um ajuste adicional para carregar os arquivos estáticos, logo o arquivo urls deve fazer assim

```python
from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    # ... the rest of your URL configuration goes here...
    path('', include('core.urls')),
              ] + static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
```

E o arquivo urls na pasta da aplicação deve ficar, mais ou menos, assim:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.go_home, name='home'),
]
```

<br>

---

# Views

Apenas para renderizar o arquivo que criamos, insira a seguinte função no arquivo **_view.py_**.

```python
def go_home(request):
    return render(request, 'index.html')
```

<br>

---

# Customizações

<br>

## Settings Fuso Brasil

```python
# Internationalization

LANGUAGE_CODE = 'pt-br'
TIME_ZONE = 'America/Sao_Paulo'
USE_I18N = True
USE_L10N = True
USE_TZ = False
```

<br>

---

# Custom Commands

https://docs.djangoproject.com/en/3.0/howto/custom-management-commands/

Iniciamnente é necessário criar a estrutura de pastas **management/commands** dentro do _app_.

https://www.youtube.com/watch?v=V0RfgNIwCqI

```bash
python manage.py {command name}
python manage.py update
```

<br>

---

# Autenticação

- Autentica
- Login
- Logout

**DECORADORES** é usado em cima da views para ver se o usuário está logado em uma determinada view que requer isso!

```python
from django.contrib.auth.decorators import login_required

@login_required(login_url='/login/')
```

<br>

---

# _Requirements_

```
pipreqs '.' --force --debug
```

<br>

---

# _Deploy_ no Heroku

Isso precisa constar no **_settings.py_**

```python
import django_heroku

# Deploy on Heroku
django_heroku.settings(locals())
```

<br>

Por fim, fazer o git

```bash
git init
git add . -A
git commit -m 'first commit'
git push heroku master
```

<br>

No Heroku

```bash
heroku login
heroku create {project_name}
heroku git:remote -a {project_name}
heroku git:remote -a opentesouro
```

<br>

Para migrar base de dados

```bash
heroku run python manage.py migrate
```

<br>

**Referências**

- [Heroku: django-app-configuration](https://devcenter.heroku.com/articles/django-app-configuration)
- [Heroku: Working with Django](https://devcenter.heroku.com/categories/working-with-django)
- [Medium: Deploy de uma aplicação Django no Heroku](https://medium.com/@renatojlelis/deploy-de-uma-aplica%C3%A7%C3%A3o-django-no-heroku-267ae0842410)

<br>

---

# Sitemap

Rodei o tutorial no projeto do PL 251

[Medium: How to create a Django Sitemap](https://medium.com/analytics-vidhya/django-sitemap-8f4ca0538fa)

... de quebra, aprendi o slug! Top!
https://stackoverflow.com/questions/837828/how-do-i-create-a-slug-in-django

<br>

**Referências**

[Django 3.2: Sitemaps](https://docs.djangoproject.com/en/3.2/ref/contrib/sitemaps/)

<br>

## Data

```
python manage.py dumpdata core.Students --indent 4 > users.yml
python manage.py loaddata initial_data.yml
```

<br>

---

# Monetizando

<br>

**Referências**

[**YouTube**: How To Build Affiliate Websites With Python and Django 3.0](https://www.youtube.com/watch?v=bpSOl88fhLg&list=PLCC34OHNcOtrZnQI6ZLvGPUWfQ6oh-D6H)

<br>

---

# Resorces

<br>

## Pandas

[Converting Django QuerySet to pandas DataFrame](https://stackoverflow.com/questions/11697887/converting-django-queryset-to-pandas-dataframe)

<br>

## Plotly

[Easy Django Plotly](https://www.codingwithricky.com/2019/08/28/easy-django-plotly/)

<br>

## Django Rest Framework

No arquivo views, por exemplo

```python
def go_api(request):
    df = get_dataframe()
    df = df[0:5]
    result = df.to_json(orient='records')
    parsed = json.loads(result)
    return JsonResponse(parsed, safe=False)

```

**Referências**

- [Django Rest Framework](http://www.django-rest-framework.org/)
- [**YouTube**: Django + Chart.js // Learn to intergrate Chart.js with Django](https://www.youtube.com/watch?v=B4Vmm3yZPgc)

<br>

## Pandas to Model

[**StackOverflow**: Saving a Pandas DataFrame to a Django Model](https://stackoverflow.com/questions/37688054/saving-a-pandas-dataframe-to-a-django-model)

```python
from django.conf import settings
from .defs_views import get_df_compiled
from sqlalchemy import create_engine
from datetime import date, datetime, timedelta

# Set Database
user = settings.DATABASES['default']['USER']
password = settings.DATABASES['default']['PASSWORD']
database_name = settings.DATABASES['default']['NAME']

database_url = 'postgresql://{user}:{password}@localhost:5432/{database_name}'.format(
    user=user,
    password=password,
    database_name=database_name,
)

engine = create_engine(database_url, echo=False)
```

<br>

## Folium

[Django and Folium integration](https://www.thetopsites.net/article/54173552.shtml)

<br>

---

# Erros

Encerrar o que estiver na porta 8000

```bash
sudo fuser -k 8000/tcp
```

<br>

---

# Referências

[Curso TreinaWeb](https://lp.treinaweb.com.br/python/aula1)
