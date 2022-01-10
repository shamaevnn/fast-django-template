release: python manage.py migrate --noinput
web: gunicorn --bind :$PORT --workers 4 --worker-class uvicorn.workers.UvicornWorker prod_django.asgi:application
worker: celery -A prod_django worker -P prefork --loglevel=INFO
beat: celery -A prod_django beat --loglevel=INFO --scheduler django_celery_beat.schedulers:DatabaseScheduler
