# CI/CD API сервиса YaMDb
![ci/cd_api_yamdb workflow](https://github.com/methodologyCode/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# Проект YaMDb
Проект YaMDb собирает отзывы пользователей на произведения.
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
## Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка».
Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Жуки» и вторая сюита Баха. Список категорий может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).
### Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»).
Добавлять произведения, категории и жанры может только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.
Пользователи могут оставлять комментарии к отзывам.
Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи.

### Ресурсы API YaMDb
- Ресурс auth: аутентификация.
- Ресурс users: пользователи.
- Ресурс titles: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).
- Ресурс categories: категории (типы) произведений («Фильмы», «Книги», «Музыка»).
- Ресурс genres: жанры произведений.
- Ресурс reviews: отзывы на произведения.
- Ресурс comments: комментарии к отзывам.


#### Запуск проекта

#### Запуск проекта в Docker.

- Create .env file in directory infra_sp2/infra/

```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=your password
DB_HOST=db
DB_PORT=5432
```

- Build container docker and run.

```
- docker-compose up -d --build
- docker-compose up
```

- Migrate, superuser, collect static and filling the database.

```
- docker-compose exec web python manage.py makemigrations
- docker-compose exec web python manage.py migrate
- docker-compose exec web python manage.py createsuperuser
- docker-compose exec web python manage.py collectstatic --no-input
- docker-compose exec web python manage.py load_csv_data
```

### В API доступны следующие эндпоинты:

```
http://IP/api/v1/ - Список всех эндпоинтов.
http://IP/redoc/ - Документация.
```
