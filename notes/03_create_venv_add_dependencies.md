# Virtual Environment and Dependencies

`python -m venv venv`

```bash
flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$ python -m venv venv
flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$
```

`source ./venv/bin/activate`

```bash
flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$ source ./venv/bin/activate
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$
```


```bash
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$ pip list
Package Version
------- -------
pip     24.0
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$
```

```bash
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$ which python
/home/flynntknapp/Programming/simple-prod-django-app/venv/bin/python
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$
```

```bash
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$ which pip
/home/flynntknapp/Programming/simple-prod-django-app/venv/bin/pip
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$
```

`pip install django gunicorn psycopg2-binary`

`pip list`

```bash
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$ pip list
Package         Version
--------------- -------
asgiref         3.8.1
Django          5.2
gunicorn        23.0.0
packaging       25.0
pip             24.0
psycopg2-binary 2.9.10
sqlparse        0.5.3
(venv) flynntknapp@DELL-DESKTOP:~/Programming/simple-prod-django-app$
```
