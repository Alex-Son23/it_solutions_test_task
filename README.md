# Тестовое задание для компании IT-Solutions
## О решении

Тезисно о том что есть в решении:
 - API с обязательной аутентификацией для запросов
 - Документация к API(swagger, redoc)
 - Авторизация по JWT token
 - Сборка проекта с помощью docker compose(2 версии: prod и develop)
 - Для prod-версси предусмотрен Nginx(в нем закомментирован код для использования сертификатов и домена)
 - Осущетвлена пагинация и фильтраця по условиям задачи
 - Возможность выбора СУБД: SQLite, PostgreSQL
 - Реализованы unit-тесты для api
 - Реализована валидация данных и обработка ошибок

В данном решении я использовал:
 - Django, DRF
 - poetry
 - drf-spectatcular
 - pytest
 - docker, docker-compose
 - nginx
 - postgresql
 - JWT

### Запуск проекта:

#### Перед запуском проекта скопируйте файл .env.template и переименуйте его в .env и в нем заполните все нунжые поля

#### Для запуска проекта в dev-режиме из корневой директории запустите командку
```
docker compose -f docker-compose.dev.yml up --build
```

#### Для запуска проекта в prod-режиме из корневой директории запустите командку
```
docker compose up --build
```

### Начало работы...
##### Запросы:
Для отправки запросов требуется авторизация, для этого сделайте post-запрос на 
```
localhost:8000/api/token/
```
с телом запроса заполненным вашими данными:
```
{
  "username": "",
  "password": ""
}
```
Скопируйте access-token и далее в загаловках запроса указывайте
```
{
  ...
  "Authorization": "Bearer {ВАШ ACCESS-TOKEN}"
  ...
}
```


## Если есть какие-то вопросы пишите в телеграм @hopeswl
