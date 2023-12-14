# Простой трекер задач
# Описание проекта
Решает проблему сохранения задач.

## Требования и зависисмости
- **Django==3.2.16**
- **djangorestframework==3.12.4**
- **django-cors-headers==3.13.0**
- **psycopg2-binary==2.9.3**
- **python-dotenv==1.0.0**

## Технологии
`Django`, `Django REST Framework`, `Gunicorn`, `Nginx`, `Docker`, `Docker Compose`, `Docker Hub`, `GitHub Actions`

# Как подготовить и запустить проект
1. [Подготовка к установке Docker](#title1)
2. [Установка Docker](#title2)
3. [Настройка проекта перед запуском](#title3)
4. [Запуск проекта](#title4)

### <a id="title1">1. Подготавливаем Windowns к установке докера</a>
    Установите Windows Subsystem for Linux (WSL) или Разверните виртуальную машину с Linux или настройте гипервизор Hyper-V.

    Для Windows 10 и 11: ставим Windows Subsystem for Linux
    Установите Windows Subsystem for Linux по инструкции с официального сайта Microsoft:
    https://docs.microsoft.com/ru-ru/windows/wsl/install-win10

### <a id="title2">2. Устанавливаем докер</a>
    `sudo apt update` - Обновите репозиторий пакетов для установки в Ubuntu
    `sudo apt install curl` - Установите консольную утилиту, которая умеет скачивать файлы по команде пользователя

    `curl -fSL https://get.docker.com -o get-docker.sh` - С помощью утилиты curl скачайте скрипт для установки докера с официального сайта

    `sudo sh ./get-docker.sh` - Запустите сохранённый скрипт с правами суперпользователя

    `sudo apt-get install docker-compose-plugin` - Дополнительно к Docker установите утилиту Docker Compose

    `sudo systemctl status docker` - Проверьте, что Docker работает

    Также, скачайте версию Desktop: https://www.docker.com/products/docker-desktop

### <a id="title3">3. Настраиваем проект перед запуском</a>

    В корне проекта создайте файл .env и добавьте в него переменные для Django-проекта:

    ```
    # Переменные для postgres:
    POSTGRES_USER=django_user
    POSTGRES_PASSWORD=mysecretpassword
    POSTGRES_DB=django
    # Добавляем переменные для Django-проекта:
    DB_HOST=db
    DB_PORT=5432

    SECRET_KEY=<Ваш secret_key django-проекта>
    ALLOWED_HOSTS=<ваши домены и ip-адреса>
    либо
    ALLOWED_HOSTS = ['127.0.0.1', 'localhost']
    ```

    Создаем виртуальное окружение: `python -m venv venv`
    Активируем виртуальное окружение: `source venv/scripts/activate`
    Устанавливаем библиотеки из файла зависимостей: `pip install -r requirements.txt`

### <a id="title4">4. Запуск проекта</a>
    Перейдите в корневую директорию, где расположен docker-compose.yml и выполните команду:

    `docker compose up`

    Проверьте работу сервиса по домену

    `127.0.0.1:8000`
