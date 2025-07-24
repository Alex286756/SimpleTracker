# Система управления задачами (Task Management System)

Система управления задачами  
Описание:  
Упрощенный трекер задач.

Основные функции:

Создание задач  
Установка приоритетов  
Сроки выполнения  
Статус задач

Технологии:

Spring Boot  
Spring Security  
PostgreSQL  
REST API  




Описание проекта

Простая система для управления задачами с базовым функционалом. Отличный старт для освоения Spring Boot и веб-разработки.

Основные функции

Создание задач с описанием и деталями

Управление статусами (To Do, In Progress, Done)

Приоритеты задач (Low, Medium, High)

Сроки выполнения

Пользователи и их роли

Поиск и фильтрация задач

Архитектура
```classDiagram
class Attachment {
    -Long id;
    -String filename;
    -String fileType;
    -byte[] content;
    -Task task;
}
class Comment {
    -Long id;
    -String text;
    -Task task;
    -User author;
    -LocalDateTime createdAt;
}
enum Priority {
    LOW,
    MEDIUM,
    HIGH
}
class Role {
    -Long id;
    -RoleName name;
}
enum RoleName {
    ROLE_USER,
    ROLE_ADMIN
}
enum Status {
    TODO,
    IN_PROGRESS,
    DONE
}
class Task {
    -Long id;
    -String title;
    -String description;
    -Priority priority;
    -Status status;
    -LocalDate dueDate;
    -User assignee;
    -LocalDateTime createdAt;
    -LocalDateTime updatedAt;
}
class User {
    -Long id;
    -String username;
    -String password;
    -String email;
    -Set<Role> roles;
}
Attachment "1..*" -- "1" Task : task_id
Comment "1..*" -- "1" Task : task_id
Comment "1..*" -- "1" User : user_id
Task "1..*" -- "1" User : assigned_to
User "1..*" -- "1..*" Role : has
```

Технологии
Spring Boot — основа приложения

Spring Data JPA — работа с базой данных

PostgreSQL — хранение данных

Spring Security — аутентификация

REST API — взаимодействие с фронтендом

Thymeleaf — для прототипа интерфейса

Реализация
1. Настройка проекта
   Создать проект через

Добавить зависимости: web, jpa, security, thymeleaf

2. Безопасность
   Ролевая модель: USER, ADMIN

Аутентификация через форму

Защита API с помощью Spring Security

Интерфейс
Thymeleaf шаблоны для базовой верстки

Bootstrap для стилизации

JavaScript для интерактивности

Этапы разработки
Базовая структура — сущности и репозитории

Безопасность — настройка аутентификации

API — создание REST endpoints

Интерфейс — создание форм и таблиц

Тестирование — написание unit-тестов

Метрики успеха
Покрытие тестами — минимум 70%

Время отклика API — менее 100мс

Удобство использования — интуитивный интерфейс