<h1>Банковское веб-приложение на Django</h1>
<h3>Безопасное управление счетами, транзакциями и клиентами</h3>

<h2>📌 Оглавление</h2>
<ol>
    <li>Описание проекта</li>
<li>Технологии</li>
<li>Установка и запуск</li>
<li>Структура проекта</li>
<li>Основные функции</li>
<li>Безопасность</li>
<li>Тестирование</li>
<li>Развертывание</li>
</ol>

<h2>📋 Описание проекта</h2>
<p>Веб-приложение для виртуального банка, разработанное на Django. Позволяет:</p>
<ul>
<li>Управлять клиентскими счетами</li>
<li>Проводить транзакции (переводы, пополнения)</li>
<li>Просматривать историю операций</li>
<li>Обеспечивает защиту от основных веб-угроз (SQL-инъекции, XSS, CSRF)</li>
</ul>
<h2>🛠 Технологии</h2>
<ul><li>Backend:</li>
<ul><li>Python 3.8+</li>
<li>Django 4.2+</li>
<li>Django ORM</li>
    </ul>
<li>База данных: SQLite (по умолчанию), можно подключить PostgreSQL/MySQL</li>
<li>Фронтенд: HTML, CSS, Django Templates</li>
<li>Безопасность:</li>
<ul><li>CSRF-токены</li>
<li>HTTPS (рекомендуется в production)</li>
<li>Защита от SQL-инъекций через ORM</li>
<li>Валидация форм</li>
    </ul>
</ul>
<h2>🚀 Установка и запуск</h2>
<p>1. Клонирование и настройка</p>
<p>git clone https://ваш-репозиторий.git<br>
cd shcoderProject</p>
<p>2. Установка зависимостей</p>
<p>pip install django</p>
<p>3. Настройка базы данных</p>
<p>По умолчанию используется SQLite. Для PostgreSQL/MySQL измените settings.py:</p>
<p>DATABASES = {<br>
    'default': {<br>
        'ENGINE': 'django.db.backends.postgresql',<br>
        'NAME': 'ваша_бд',<br>
        'USER': 'пользователь',<br>
        'PASSWORD': 'пароль',<br>
        'HOST': 'localhost',<br>
        'PORT': '5432',<br>
    }<br>
}</p>
<p>4. Миграции и суперпользователь</p>
<p>python manage.py migrate<br>
python manage.py createsuperuser  # для доступа в админку</p>
<p>5. Запуск сервера</p>
<p>python manage.py runserver</p>
<p>Сервер запустится на http://127.0.0.1:8000/</p>
<p>6. Откройте в браузере</p>
<li>Основное приложение: http://127.0.0.1:8000/</li>
<li>Админ-панель: http://127.0.0.1:8000/admin (используйте логин/пароль из шага 5)</li>

<h2>📂 Структура проекта</h2>
shcoderProject/<br>
├── manage.py            # Управление Django<br>
├── bank_app/            # Основное приложение<br>
│   ├── migrations/      # Миграции БД<br>
│   ├── templates/       # HTML-шаблоны<br>
│   ├── __init__.py<br>
│   ├── admin.py         # Админ-панель<br>
│   ├── apps.py<br>
│   ├── forms.py         # Формы (например, для транзакций)<br>
│   ├── models.py        # Модели (Client, Account, Transaction)<br>
│   ├── tests.py         # Тесты<br>
│   ├── urls.py          # Маршруты приложения<br>
│   └── views.py         # Логика представлений<br>
└── shcoderProject/      # Настройки проекта<br>
    ├── __init__.py<br>
    ├── urls.py          # Главные URL<br>
    ├── asgi.py<br>
    ├── settings.py      # Конфигурация<br>
    └── wsgi.py<br>
<h2>🔧 Основные функции</h2>
<ol>
    <li>Управление счетами</li>
<ul>
    <li>Создание/закрытие счетов</li>
<li>Просмотр баланса</li>
</ul>
<li>Транзакции</li>
<ul>
    <li>Переводы между счетами</li>
<li>Пополнение и снятие средств</li>
</ul>
<li>Администрирование</li>
<ul>
    <li>Доступ через /admin (требует createsuperuser)</li>
</ul>
<li>Безопасность</li>
<ul>
    <li>Автоматическая защита от CSRF</li>
<li>Валидация данных в формах (forms.py)</li>
</ul>
</ol>
<h2>🔒 Безопасность</h2>
<p>Реализованные меры:</p>
<ol>
<li>Защита от SQL-инъекций (Django ORM)</li>

<li>CSRF-токены во всех формах</li>

<li>Валидация данных (на стороне сервера)</li>

<li>HTTPS (рекомендуется для production)</li>
</ol>

<h2>🧪 Тестирование</h2>
<p>Запуск тестов:</p>

python manage.py test bank_app
<h2>☁️ Развертывание</h2>
<p>1. Настройка ALLOWED_HOSTS</p>
<p>В settings.py:</p>
<p>ALLOWED_HOSTS = ['ваш-домен.ru', 'localhost']</p>
<p>2. Запуск через Gunicorn + Nginx</p>
<p>
pip install gunicorn<br>
gunicorn --bind 0.0.0.0:8000 shcoderProject.wsgi</p>
<p>Настройте Nginx для статических файлов и HTTPS.</p>
