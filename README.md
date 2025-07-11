# Snake Game (C# Console)

## Описание

Конзолна мини игра „Змия“, реализирана на C# като .NET console приложение. Програмата рисува правоъгълно поле в конзолата, позволява управление на змията със стрелките, изяждане на храна и отчита резултат при края на играта. При всяко ново стартиране на рунд змията се оцветява в случаен цвят.

## Основни компоненти

* **Program.cs**

  * `Main()` – управява цикъла на играта: показва меню „Welcome…“, избира случаен цвят за змията, очаква ENTER, стартира `Game()` и показва резултат.
  * `Game()` – основен игрови цикъл: чете стрелките, движи и расте змията, проверява сблъсъци, изяжда храна (SpawnFood) и връща резултат.

* **Canvas.cs**

  * Статичен клас за рисуване в конзолата.
  * Свойства:

    * `Width`, `Height` – размер на полето (в „пиксели“).
    * `SnakeColor` – текущият цвят на змията (`ConsoleColor`).
  * Методи:

    * `Draw(x,y)` – рисува блок „██“ в `SnakeColor`.
    * `Erase(x,y)` – изтрива блок на позиция.
    * `Write(x,y,text)` – отпечатва текст.
    * `Clear()` – изчиства екрана.

* **Snake.cs, GameObject.cs, Direction.cs**

  * `Snake` използва `LinkedList<GameObject>` за сегментите и методи `Move()`, `Eat()`, `GetFrontPos()`.
  * `GameObject` рисува/изтрива при създаване/Dispose.
  * `Direction` enum (битови стойности) блокира 180° обръщане.

## Технологии

* .NET 6+ (или .NET Core)
* C#
* Конзолна графика чрез `Console` API

## Файлова структура

```
SnakeGame/
├─ Program.cs
├─ Canvas.cs
├─ Snake.cs
├─ GameObject.cs
└─ Direction.cs
```

## Инсталиране и стартиране

1. Клонирай репото:

   ```bash
   git clone https://github.com/USERNAME/SnakeGame.git
   cd SnakeGame
   ```

2. Отвори с Visual Studio или VS Code (C# extension)

3. Стартирай проекта.

5. Управление със стрелките ← ↑ → ↓.

6. След края виждате `GAME OVER! Score: X`. Натиснете ENTER за нова игра.

---

# Animals Adoption

## Описание

`Animals Adoption` е уеб приложение на Flask, което позволява на потребители да публикуват и разглеждат обяви за осиновяване на животни.

## Основни функции

* Регистрация на потребители и вход (email и парола)
* Добавяне, редакция и изтриване на обяви за животни (CRUD)
* Преглед на всички обяви и детайлна страница за всяко животно
* Качване и показване на снимки на животните
* Защитени формуляри с CSRF защита (Flask-WTF)
* Управление на потребителска сесия (Flask-Login)

## Технологии и библиотеки

* Python 3.8+
* Flask
* Flask-SQLAlchemy
* Flask-WTF
* Flask-Login
* email-validator
* SQLite (по подразбиране)

## Структура на проекта

```
animals_adoption/
├─ app.py              # основен модул с конфигурация и маршрути
├─ config.py           # настройки (SECRET_KEY, база данни, папка за снимки)
├─ models.py           # SQLAlchemy модели (User, Animal)
├─ forms.py            # WTForms форми (RegistrationForm, LoginForm, AnimalForm)
├─ requirements.txt    # списък с Python зависимости
├─ static/             # статични файлове и папка uploads за снимки
│  └─ uploads/
└─ templates/          # Jinja2 HTML шаблони
   ├─ base.html
   ├─ register.html
   ├─ login.html
   ├─ animals.html
   ├─ animal_detail.html
   └─ add_animal.html
```

## Инсталиране и стартиране

1. Клонирай репото:

   ```bash
   git clone https://github.com/USERNAME/animals_adoption.git
   cd animals_adoption
   ```
2. Създай и активирай виртуална среда:

   ```bash
   python -m venv venv
   # Windows:
   .\venv\Scripts\activate
   # Linux/macOS:
   source venv/bin/activate
   ```
3. Инсталирай зависимости:

   ```bash
   pip install -r requirements.txt
   ```
4. (Опционално) Задай променливи на средата:

   ```bash
   export SECRET_KEY="твоят-секретен-ключ"
   ```
5. Стартирай приложението:

   ```bash
   python app.py
   ```
6. Отвори в браузър: [http://127.0.0.1:5000/](http://127.0.0.1:5000/)

## Конфигурация

- **SECRET_KEY**: използва се за защита на формите (Flask-WTF).
- **SQLALCHEMY_DATABASE_URI**: по подразбиране `sqlite:///animals.db`.
- **UPLOAD_FOLDER** и **ALLOWED_EXTENSIONS** са конфигурирани в `config.py`.

## Модели

- **User**: id, username, email, password_hash, animals relationship
- **Animal**: id, name, species, age, city, description, photo filename, contact, user_id

## Маршрути (routes)

| Път                    | Описание                         |
|------------------------|----------------------------------|
| `/register`            | Регистрация на потребител        |
| `/login`               | Вход                              |
| `/logout`              | Изход                             |
| `/animals`             | Списък с всички обяви            |
| `/animals/<id>`        | Детайли за животно               |
| `/animals/add`         | Добавяне на нова обява           |
| `/animals/<id>/edit`   | Редакция на обява                 |
| `/animals/<id>/delete` | Изтриване на обява                |
| `/uploads/<filename>`  | Достъп до качени снимки          |
