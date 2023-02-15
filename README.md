![workflow status](https://github.com/viator3m/foodgram-project-react/actions/workflows/foodgram_workflow.yml/badge.svg)

### Проект Foodgram – Продуктовый помощник
На этом сервисе пользователи смогут публиковать рецепты, подписываться 
на публикации других пользователей и т.д.

#### Запуск проекта в контейнерах

- Клонирование удаленного репозитория
```bash
git clone git@github.com:Danila747/foodgram-project-react.git
cd infra
```
- В директории /infra создайте файл .env, с переменными окружения, как .env.example
- Сборка контейнеров
```bash
docker-compose up -d --build
```
```bash
docker-compose exec backend python manage.py makemigrations
docker-compose exec backend python manage.py migrate
docker-compose exec backend python manage.py collectstatic --no-input
docker-compose exec backend python manage.py createsuperuser
```
- Наполните базу данных
```bash
docker-compose exec backend python manage.py load_data
```
- или наполните базу тестовыми данными
```bash
docker-compose exec backend python manage.py loaddata data/data.json 
```
#### Запуск проекта локально

```bash
cd backend
python -m venv venv
source venv/Scripts/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```
```bash
python manage.py makemigrations
python manage.py migrate
python manage.py collectstatic --noinput
```
- Наполнение базы данных
```bash
python manage.py load_data
```

- Запуск сервера
```bash
python manage.py runserver 
```