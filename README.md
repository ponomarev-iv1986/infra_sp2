### Описание проекта:

Backend проекта YaMDb - базы отзывов о фильмах, книгах и музыке.

### Как запустить проект:
*Примечание:* должен быть установлен Docker.

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/ponomarev-iv1986/infra_sp2.git
```

```
cd infra_sp2/infra
```

Создать и наполнить файл ".env", например:
```
touch .env
```

```
nano .env
```

```
DB_ENGINE=django.db.backends.postgresql # работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```

```
^X # выйти с сохранением файла
```

Запустить docker-compose:
```
docker-compose up
```

Выполнить команды:
```
docker-compose exec web python manage.py makemigrations
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py collectstatic --no-input
```

Наполнить базу данных данными:
```
docker-compose cp fixtures.json web:app/
```

```
docker-compose exec web python manage.py loaddata fixtures.json
```

Чтобы войти в админку, необходимо создать суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```

Проект доступен по адресу http://localhost/

Админка доступна по адресу  http://localhost/admin/