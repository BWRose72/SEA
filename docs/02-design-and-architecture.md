# 02. Design and Architecture

## 1. Тип и структура на приложението

Приложението **MedicBay** е уеб базирана система за управление на лекарски графици и записване на часове.

### Тип:
- Уеб приложение (client-server архитектура)

### Структура:
Проектът е изграден с Laravel framework и следва MVC архитектура:

- **app/**
  - Models – бизнес логика и ORM модели
  - Http/Controllers – обработка на заявки
- **resources/**
  - views / js – frontend (Inertia/Vue)
- **routes/**
  - web.php – дефиниция на маршрути
- **database/**
  - migrations – структура на базата
  - seeders – начални данни

### Основни модули:
- Authentication (регистрация, вход)
- Управление на лекари
- Записване на часове
- Управление на роли (admin, doctor, patient)
- Преглед на графици

---

## 2. Модел на данните

### Основни таблици:

#### users
- id
- name
- email
- password

#### doctors
- id
- user_id (FK → users)
- name
- phone
- bio

#### patients
- id
- user_id (FK → users)

#### appointments
- id
- doctor_id (FK → doctors)
- patient_id (FK → patients)
- starts_at
- status

#### specialisations
- id
- name

#### doctor_specialisation
- doctor_id
- specialisation_id

### Връзки:
- User → Doctor (1:1)
- User → Patient (1:1)
- Doctor → Appointments (1:N)
- Patient → Appointments (1:N)
- Doctor ↔ Specialisation (M:N)

---

## 3. Диаграма

Диаграмата е налична във файла:

`docs/diagram.png`

---

## 4. Потребителски поток

### Основни екрани:
- Начална страница
- Регистрация / Вход
- Dashboard
- Списък с лекари
- Детайли за лекар
- Записване на час

### Поток:
1. Потребителят се регистрира
2. Получава роля **patient**
3. Преглежда лекари
4. Избира лекар
5. Записва час
6. Вижда записите в dashboard

### Администратор:
- Добавя лекари
- Управлява потребители

### Лекар:
- Вижда график
- Управлява часове

---

## 5. Използвани технологии

### Езици:
- PHP
- JavaScript
- HTML/CSS

### Framework:
- Laravel

### Frontend:
- Vue.js (Inertia)

### База данни:
- MariaDB

### Библиотеки:
- Spatie Roles & Permissions

### Причини за избор:
- Laravel → стабилен MVC framework
- MariaDB → надеждна релационна база
- Vue/Inertia → лесна интеграция без сложен SPA
- Spatie → готово решение за роли
