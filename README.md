# simple-django-project-heroku
## Adapting Your Django App for Heroku
This guide will help you adapt your Django application to deploy it on Heroku. It covers common issues faced during deployment and provides solutions. This is not a step by step tutorial!

### 1. Procfile
Heroku uses a Procfile to determine how to run your application. Create a Procfile in your project directory to specify the processes to run. I had many issues to run my application and this solution is working. Pay attention to your wsgi.py file location.

```python
release: python simple_project/manage.py migrate && python simple_project/manage.py collectstatic --noinput
web: gunicorn --pythonpath simple_project simple_project.wsgi
```

### 2. Managing Secret Keys
It's crucial to keep your secret keys secure. Instead of hardcoding them in your settings, it's recommended to use environment variables. You can store your secret keys in a .env file, and then set them in Heroku's Config Vars.
Create a .env file in your project's root directory and add your secret key as an environment variable. You need `django-heroku` package for that to work.

```python
SECRET_KEY=mysecretkey
```

### 3. Installing Required Packages and updating the requirements.txt file
Don't forget to install all required packages and add them to requirements.txt file :)
