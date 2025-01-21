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
```sh
cd frontend
docker build -t YOUR_USERNAME/kittygram_frontend .
cd ../backend
docker build -t YOUR_USERNAME/kittygram_backend .
cd ../nginx
docker build -t YOUR_USERNAME/kittygram_gateway .
```
2. Загрузите образы на DockerHub:
```sh
docker push YOUR_USERNAME/kittygram_frontend
docker push YOUR_USERNAME/kittygram_backend
docker push YOUR_USERNAME/kittygram_gateway
```
### Деплой на сервере
1. Подключитесь к удаленному серверу
```sh
ssh -i PATH_TO_SSH_KEY/SSH_KEY_NAME YOUR_USERNAME@SERVER_IP_ADDRESS
```
2. Создайте на сервере директорию kittygram:
```sh
mkdir kittygram
```
3. Установите Docker Compose на сервер:
```sh
sudo apt update
sudo apt install curl
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo apt install docker-compose
```
4. Скопируйте файлы docker-compose.production.yml и .env в директорию kittygram/ на сервере:
```sh
scp -i PATH_TO_SSH_KEY/SSH_KEY_NAME docker-compose.production.yml YOUR_USERNAME@SERVER_IP_ADDRESS:/home/YOUR_USERNAME/kittygram/docker-compose.production.yml
```
Где:

- PATH_TO_SSH_KEY - путь к файлу с вашим SSH-ключом
- SSH_KEY_NAME - имя файла с вашим SSH-ключом
- YOUR_USERNAME - ваше имя пользователя на сервере
- SERVER_IP_ADDRESS - IP-адрес вашего сервера
5. Запустите Docker Compose в режиме демона:
```sh
sudo docker-compose -f /home/YOUR_USERNAME/kittygram/docker-compose.production.yml up -d
```
6. Выполните миграции, соберите статические файлы бэкенда и скопируйте их в /backend_static/static/:
```sh
sudo docker-compose -f /home/YOUR_USERNAME/kittygram/docker-compose.production.yml exec backend python manage.py migrate
sudo docker-compose -f /home/YOUR_USERNAME/kittygram/docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker-compose -f /home/YOUR_USERNAME/kittygram/docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```
7. Откройте конфигурационный файл Nginx в редакторе nano:
```sh
sudo nano /etc/nginx/sites-enabled/default
```
8. Измените настройки location в секции server:
```sh
location / {
    proxy_set_header Host $http_host;
    proxy_pass http://127.0.0.1:9000;
}
```
9. Проверьте правильность конфигурации Nginx:
```sh
sudo nginx -t
```
Если вы получаете следующий ответ, значит, ошибок нет:
```sh
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
10. Перезапустите Nginx:
```sh
sudo service nginx reload
```
### Настройка CI/CD 
1. Файл workflow уже написан и находится в директории:
```sh
kittygram/.github/workflows/main.yml
```
2. Для адаптации его к вашему серверу добавьте секреты в GitHub Actions:
```sh
DOCKER_USERNAME                # имя пользователя в DockerHub
DOCKER_PASSWORD                # пароль пользователя в DockerHub
HOST                           # IP-адрес сервера
USER                           # имя пользователя
SSH_KEY                        # содержимое приватного SSH-ключа (cat ~/.ssh/id_rsa)
SSH_PASSPHRASE                 # пароль для SSH-ключа

TELEGRAM_TO                    # ID вашего телеграм-аккаунта (можно узнать у @userinfobot, команда /start)
TELEGRAM_TOKEN                 # токен вашего бота (получить токен можно у @BotFather, команда /token, имя бота)
```


## Над проектом работал:
### Багний Олег
