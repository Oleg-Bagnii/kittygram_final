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

### Установка
1. Клонируйте проект Kittygram себе на компьютер:
```sh
git clone https://github.com/Oleg-Bagnii/kittygram_final.git
```
2. Создайте файл .env и заполните его своими данными.
```sh
POSTGRES_DB=<Желаемое_имя_базы_данных>

POSTGRES_USER=<Желаемое_имя_пользователя_базы_данных>

POSTGRES_PASSWORD=<Желаемый_пароль_пользователя_базы_данных>

DB_HOST=db

DB_PORT=5432
```
### Создание Docker-образов
1. Замените YOUR_USERNAME на свой логин на DockerHub:
2. ```sh
cd frontend
docker build -t YOUR_USERNAME/kittygram_frontend .
cd ../backend
docker build -t YOUR_USERNAME/kittygram_backend .
cd ../nginx
docker build -t YOUR_USERNAME/kittygram_gateway .
``

### Проект доступен:

http://localhost:9000/

# Над проектом работал:
## Багний Олег
