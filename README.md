# Kittygram

## Описание
**Kittygram — социальная сеть для обмена фотографиями любимых питомцев.**

Реализованный функционал: регистрация и авторизация на сайте, создание и редактирование карточки котика, добавление фото.

## Как запустить проект:
1. **Устанавливаем Docker и Docker Compose:**
    ```bash
    sudo apt update
    sudo apt install curl
    curl -fSL https://get.docker.com -o get-docker.sh
    sudo sh ./get-docker.sh
    sudo apt install docker-compose-plugin 
    ```

2. **Клонируем репозиторий и переходим в папку с файлом docker-compose.yml:**
    ```bash
    git clone git@github.com:Mitsushidu/foodgram-project-react.git
    cd infra
    ```

3. **Создаем файл .env в папке infra:**
    ```bash
    sudo nano .env
    ```
    **Заполняем его следующими данными:**
    ```
    POSTGRES_DB=название_базы_данных
    POSTGRES_USER=имя_пользователя
    POSTGRES_PASSWORD=пароль

    DB_HOST=db
    DB_PORT=5432

    SECRET_KEY=сгенерированный_секретный_ключ
    ALLOWED_HOSTS=разрешенные_хосты 
    ```
    Разрешенные хосты: '127.0.0.1 localhost'

4. **Запускаем контейнеры Docker**
    ```bash
    sudo docker compose -f docker-compose.production.yml up
    ```

5. **Создаем миграции, собираем статику бэкенда и копируем ее:**
    ```bash
    sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
    sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
    sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
    ```

6. **Переходим по ссылке https://localhost:8000/**



## Технический стек:
* Django = 3.2.3
* djangorestframework = 3.12.4
* djoser = 2.1.0
* Pillow = 9.0.0
* Nginx
* Postgres
* Docker


## Автор: mitsushidu
