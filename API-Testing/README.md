# API Testing — ReqRes

## About the project

Практический проект по тестированию REST API с использованием Postman.

В рамках проекта выполняется функциональное и негативное тестирование API, проверка HTTP-статусов, структуры JSON-ответов, типов данных, обязательных полей и форматов значений.

## Tools

- Postman
- REST API
- JavaScript
- Git
- GitHub

## Tested API

ReqRes API.

## Tested endpoints

| Method | Endpoint            | Description                    |
| ------ | ------------------- | ------------------------------ |
| GET    | `/api/users?page=2` | Получение списка пользователей |
| GET    | `/api/users/2`      | Получение пользователя         |
| POST   | `/api/users`        | Создание пользователя          |
| PUT    | `/api/users/2`      | Обновление пользователя        |
| DELETE | `/api/users/2`      | Удаление пользователя          |

## Testing scenarios

### GET `/api/users?page=2`

Проверки:

- HTTP Status Code
- Pagination
- `page`
- `per_page`
- Количество пользователей
- Обязательные поля
- Типы данных
- Формат email

### POST `/api/users`

Проверки:

- HTTP Status Code `201 Created`
- Переданные данные `name` и `job`
- Наличие `id`
- Тип `id`
- Наличие `createdAt`
- Тип `createdAt`
- Формат даты

### PUT `/api/users/2`

Проверки:

- HTTP Status Code
- Переданные данные
- Результат обновления через GET

### DELETE `/api/users/2`

Проверки:

- HTTP Status Code `204 No Content`
- Пустой Response Body
- Проверка удаления через GET

## Automated testing

Для автоматизации API-проверок использовались Postman Tests на JavaScript.

Автоматизированы проверки:

- Status Code
- Response fields
- Data types
- Pagination
- Number of returned users
- Email format
- ISO 8601 date format

## Found issues

### BUG-001 — Incorrect data type of `id`

**Endpoint:** `POST /api/users`

**Expected:**

```json
{
  "id": 271
}
```

id должен иметь тип number.

Actual:
{
"id": "271"
}
id возвращается как string.

Severity: High

Priority: High

Result: Failed automated test

Postman Collection

Postman Collection находится в:

Postman/ReqRes API Tests.postman_collection.json

Collection содержит следующие запросы:

GET users page 2
GET user
POST user
PUT user
DELETE user

## Test Results

### GET `/api/users?page=2`

| Check                      | Result  |
| -------------------------- | ------- |
| Status Code = 200          | ✅ PASS |
| Page = 2                   | ✅ PASS |
| per_page = 6               | ✅ PASS |
| Number of users = per_page | ✅ PASS |
| Required fields exist      | ✅ PASS |
| Correct data types         | ✅ PASS |
| Email format               | ✅ PASS |

**Result: 7/7 PASS**

### POST `/api/users`

| Check                               | Result  |
| ----------------------------------- | ------- |
| Status Code = 201                   | ✅ PASS |
| Name is correct                     | ✅ PASS |
| Job is correct                      | ✅ PASS |
| Response contains id                | ✅ PASS |
| ID is a number                      | ❌ FAIL |
| Response contains createdAt         | ✅ PASS |
| createdAt has valid ISO 8601 format | ✅ PASS |
| createdAt is a string               | ✅ PASS |

**Result: 7 checks — 6 PASS / 1 FAIL**

The failed test confirms that the API returns `id` as a string instead of a number.

### DELETE `/api/users/2`

| Check                              | Result  |
| ---------------------------------- | ------- |
| Status Code = 204                  | ✅ PASS |
| Response Body is empty             | ✅ PASS |
| User is unavailable after deletion | ❌ FAIL |

The DELETE request returned `204 No Content`, but a subsequent GET request returned `200 OK` and the user was still available.

## Project Status

API functional testing and basic API automation completed.

The project contains:

- Manual API test scenarios
- Negative testing
- Bug reports
- Automated Postman tests
- Postman Collection
- Git/GitHub version control
