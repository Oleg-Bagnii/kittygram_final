#  Проект Kittygram
![example workflow](https://github.com/Oleg_Bagnii/kittygram_final/actions/workflows/kittygram_workflow.yml/badge.svg)

## Описание проекта:

Проект Kittygram дает возможность рассказать о ваших котах и кошках.

## Cтек использованных технологий

Python 3.9

Django 3.2.3

djangorestframework==3.12.4

PostgreSQL 13.10

## Для запуска проекта выполните следующие комнады:

### Клонируйте проект Kittygram себе на компьютер:

https://github.com/Oleg-Bagnii/kittygram_final.git

### Заполните файл .env

cd kittygram_final/

nano .env

POSTGRES_DB=<Желаемое_имя_базы_данных>

POSTGRES_USER=<Желаемое_имя_пользователя_базы_данных>

POSTGRES_PASSWORD=<Желаемый_пароль_пользователя_базы_данных>

DB_HOST=db

DB_PORT=5432

### Запуск проекта:

docker compose -f docker-compose.production.yml up

### Выполняем миграции, собераем статические файлы бэкенда и скопируем их в /backend_static/static/:

docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/

### Проект доступен:

http://localhost:9000/

# Над проектом работал:
## Багний Олег
