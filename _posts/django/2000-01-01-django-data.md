---
title: "Django: Data"
excerpt_separator: "<!--more-->"
tags: [python, pycharm, jupyter, package, pandas]

---



### *Dump Data*

Com a função dump é possível obter os dados e compreende-los!

[manage.py dumpdata](https://docs.djangoproject.com/pt-br/3.0/ref/django-admin/#django-admin-dumpdata)

```bash
python manage.py dumpdata
python manage.py dumpdata --format=json core > core/fixtures/all_data.json
```



### [Fornecendo dados iniciais para modelos](https://docs.djangoproject.com/pt-br/3.2/howto/initial-data/)

Depois basta sss

```bash
python manage.py loaddata admin.json
python manage.py loaddata initial_data.json
python manage.py loaddata students.json
```



### No Heroku

```
heroku run python manage.py loaddata admin.json --app openescola
heroku run python manage.py loaddata initial_data.json --app openescola
heroku run python manage.py loaddata students.json --app openescola
```

