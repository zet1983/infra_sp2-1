# Проект YaMDb 

![Logo](https://cdn-irec.r-99.com/sites/default/files/product-images/399872/EOXOqQkXnjTMTRnIpMUSvQ.jpg)

Команда разработки: 

- ✅ [Nikita Shinkov (в роли Python-разработчика Тимлид)](https://github.com/askwlc/)
- ✅ [Igor Merkushev (в роли Python-разработчика)](https://github.com/#)
- ✅ [Sergei Tregubov (в роли Python-разработчика)](https://github.com/SergeiTregubov/)

[Описание](#описание) /
[Техническое описание](#Техническое_описание_проекта_YaMDb) /
[Разевернуть локально](#Как запустить проект)

## Описание

Проект YaMDb

Проект YaMDb собирает отзывы пользователей на произведения. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка». Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Жуки» и вторая сюита Баха. Список категорий может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»). 
Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). 
Добавлять произведения, категории и жанры может только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.
Пользователи могут оставлять комментарии к отзывам.
Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи.

### Стек технологий использованный в проекте:
[![Python](https://img.shields.io/badge/Made%20with-Python-green?logo=python&logoColor=white&color)](https://www.python.org/)
[![Docker](https://img.shields.io/static/v1?message=docker&logo=docker&labelColor=5c5c5c&color=002c66&logoColor=white&label=%20&style=plastic)](https://www.docker.com/)
[![Django](https://img.shields.io/static/v1?message=django&logo=django&labelColor=5c5c5c&color=0c4b33&logoColor=white&label=%20&style=plastic)](https://www.djangoproject.com/)
[![Nginx](https://img.shields.io/static/v1?message=nginx&logo=nginx&labelColor=5c5c5c&color=009900&logoColor=white&label=%20&style=plastic)](https://nginx.org/)
[![Postgres](https://img.shields.io/static/v1?message=postgresql&logo=postgresql&labelColor=5c5c5c&color=1182c3&logoColor=white&label=%20&style=plastic)](https://www.postgresql.org/)

## Техническое описание проекта YaMDb:

### Ресурсы API YaMDb:
- auth: аутентификация.
- users: пользователи.
- titles: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).
- categories: категории (типы) произведений («Фильмы», «Книги», «Музыка»). Одно произведение может быть привязано только к одной категории.
- genres: жанры произведений. Одно произведение может быть привязано к нескольким жанрам.
- reviews: отзывы на произведения. Отзыв привязан к определённому произведению.
- comments: комментарии к отзывам. Комментарий привязан к определённому отзыву.

### Пользовательские роли:
Аноним, Аутентифицированный пользователь, Модератор, Администратор, Суперюзер.

Реализована самостоятельная регистрация пользователей через эндпоинт /api/v1/auth/signup/ с последующим получением JWT-токена.

## Как запустить проект:

Клонировать репозиторий
```
git clone https://github.com/askwlc/infra_sp2.git
```

Перейти в папку:
```
cd infra
```
Развернуть контейнеры:
```
docker-compose up 
```
Сделать миграции, суперпользователя и собрать статику:
```
docker-compose exec web python manage.py makemigrations reviews
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```
Заполнить базу данными из копии:
```
docker-compose exec web python manage.py loaddata ../infra/fixtures.json 
```

#### Подробную документацию можно посмотреть по [ссылке](http://127.0.0.1:8000/redoc/) после запуска сервера с проектом.