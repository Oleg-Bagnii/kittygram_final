![Build Status](https://github.com/Oleg-Bagnii/kittygram_final/actions/workflows/main.yml/badge.svg)

#  Kittygram — социальная сеть для обмена фотографиями любимых питомцев.

## Описание проекта

Пользователи могут регистрироваться, загружать фотографии с описанием и смотреть питомцев других пользователей.

## Cтек использованных технологий:

- Python 3.9

- Django 3.2.3

- djangorestframework==3.12.4

- PostgreSQL 13.10

## Для запуска проекта выполните следующие комнады:

### Клонируйте проект Kittygram себе на компьютер:
```sh
git clone https://github.com/Oleg-Bagnii/kittygram_final.git
```
### Заполните файл .env
```sh
cd kittygram_final/
```
```sh
nano .env
```
POSTGRES_DB=<Желаемое_имя_базы_данных>

POSTGRES_USER=<Желаемое_имя_пользователя_базы_данных>

POSTGRES_PASSWORD=<Желаемый_пароль_пользователя_базы_данных>

DB_HOST=db

DB_PORT=5432

### Запуск проекта:
```sh
docker compose -f docker-compose.production.yml up
```
### Выполняем миграции, собераем статические файлы бэкенда и скопируем их в /backend_static/static/:
```sh
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```
```sh
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```
```sh
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```

### Проект доступен:

http://localhost:9000/

# Над проектом работал:
## Багний Олег
