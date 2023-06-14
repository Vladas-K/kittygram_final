# Kittygram - социальная сеть для размещения фотографий котиков.


## **Описание проекта**

Пользователи могут регистрироваться, загружать фотографии своих котиков и смотреть котиков других пользователей.

Проект находится по адресу: https://vkitty.hopto.org/

## **Стэк технологий**

* Python 3.9
* Django 3.2.3
* djangorestframework 3.12.4
* djoser 2.1.0
* webcolors 1.11.1
* gunicorn 20.1.0
* psycopg2-binary 2.9.6
* pytest-django 4.4.0
* pytest-pythonpath 0.7.3
* pytest 6.2.4
* PyYAML 6.0
* python-dotenv 1.0.0

## Локальный запуск проекта

Клонировать репозиторий и перейти в него в командной строке:

```bash
git clone ...
cd kittygram_final
```

Cоздать и активировать виртуальное окружение, установить зависимости:

```bash
python3 -m venv venv
source venv/scripts/activate
python -m pip install --upgrade pip
pip install -r backend/requirements.txt
```

Установить [docker compose](https://www.docker.com/) на свой компьютер.

Запустить проект через docker-compose:

```bash
docker compose -f docker-compose.yml up --build -d
```

Выполнить миграции:

```bash
docker compose -f docker-compose.yml exec backend python manage.py migrate
```

Собрать статику и скопировать ее:

```bash
docker compose -f docker-compose.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.yml exec backend cp -r /app/static_backend/. /backend_static/static/
```


## Настройка CI/CD

* Файл workflow
```
kittygram/.github/workflows/main.yml
```

* Добавить секреты
```
DOCKER_PASSWORD - пароль от аккаунта DockerHub
DOCKER_USERNAME - логин DockerHub
HOST - IP адресс сервера
USER - логин на сервере
SSH_KEY - SSH ключ
SSH_PASSPHRASE - пароль от сервера
TELEGRAM_TO - ваш Telegram ID
TELEGRAM_TOKEN - токена вашего Telegram бота
```

## Автор
Владас Куодис


