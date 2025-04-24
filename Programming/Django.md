```
django-admin startproject <project name> .
```

setup a new project.

```
python manage.py migrate
```

create the database.

```
python manage.py runserver
```

start the server.

```
python manage.py startapp <app name>
```

setup date to create an app.

update `<app name>/models.py`.

update `<app name>/settings.py` with `<app name>`.

```
python manage.py makemigrations <app name>
```

generate migration files after models edit.

```
python manage.py migrate
```

migrate the database using latest modifications.

```
python manage.py createsuperuser
```

setup admin account.

update `<app name>/admin.py` with models.

```
python manage.py shell
```

run a shell.

update `<project name>/urls.py` and include app urls.

create `<app name>/urls.py`.

update `<app name>/views.py`.

generate template under `<app name>/templates`.