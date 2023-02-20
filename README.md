# YaMDb API
![workflow](https://github.com/sHvostom/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?branch=master&event=push)

### Описание проекта:

Проект YaMDb собирает отзывы пользователей на произведения, позволяет ставить произведениям оценку и комментировать чужие отзывы.

Произведения делятся на категории, и на жанры. Список произведений, категорий и жанров может быть расширен администратором.

Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

Доступ к БД проекта осуществляется через Api.

Полный список запросов и эндпоинтов описан в документации ReDoc, доступна после запуска проекта по адресу:
```
http://127.0.0.1:8000/redoc/
```

### Настройка и запуск сервера в контейнере:
**Клонировать репозиторий**
```bash
git clone
```
**Перейти в папку:**
```bash
cd infra
```
**Развернуть контейнеры:**
```bash
docker-compose up -d --build
```

**Сделать миграции, суперпользователя и собрать статику:**
```bash
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

**Заполнить базу данными из копии:**
```bash
docker-compose exec web python manage.py loaddata ../infra/fixtures.json
```

