release: python simple_project/manage.py migrate && python simple_project/manage.py collectstatic --noinput
web: gunicorn --pythonpath simple_project simple_project.wsgi