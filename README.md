# API YaMDB

![Workflow repository status](https://github.com/mdkostrov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

### Описание проекта.

Проект представляет собой сервис для любителей различных произведений.
Проект YaMDb собирает отзывы пользователей на произведения. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка». Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Жуки» и вторая сюита Баха. Список категорий может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).
Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»).
Добавлять произведения, категории и жанры может только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.
Пользователи могут оставлять комментарии к отзывам.
Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи.
Настоящий репозиторий - API для данного проекта.

##### Технологии.

В проекте использованы следующие технологии:
Python 3.7, Django 3.2, Django REST Framework 3.12.4, Simple JWT, Gunicorn 20.1.0, nginx 1.21.3-alpine, PostgreSQL 13.0-alpine.

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```bash
git clone https://github.com/mdkostrov/infra_sp2.git
```

```bash
cd yamdb_final
```

Cоздать и активировать виртуальное окружение (для Windows):

```bash
python -m venv venv
```

```bash
source venv/scripts/activate
```

Обновить установщик пакетов pip:

```bash
python -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

```bash
pip install -r requirements.txt
```

Перейти в папку с файлом docker-compose.yaml:

```bash
cd infra
```

Поднять контейнеры (db, web, nginx):

```bash
docker-compose up -d --build
```

Выполнить миграции:

```bash
docker-compose exec web python manage.py makemigrations
```

```bash
docker-compose exec web python manage.py migrate
```

Создать суперпользователя:

```bash
docker-compose exec web python manage.py createsuperuser
```

Собрать статику:

```bash
docker-compose exec web python manage.py collectstatic --no-input
```

Создать дамп базы данных (нет в текущем репозитории):

```bash
docker-compose exec web python manage.py dumpdata > fixtures.json
```

Остановить контейнеры:

```bash
docker-compose down -v
```

### Шаблон наполнения файла .env с переменными окружения (infra/.env):

```bash
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

### Документация
Документация с доступными для запросов эндпоинтами после запуска DEV-сервера проекта доступна по адресу:

```bash
http://localhost/redoc/
```

### Об авторах:

Над проектом работали:

**Костров Михаил (тимлид)**
[GitHub](https://github.com/mdkostrov/)

**Александр Морозов**
[GitHub](https://github.com/notebad)

**Иван Наливайко**
[GitHub](https://github.com/nemanick)

Студенты курса "Разработчик Python" (47 когорта).
