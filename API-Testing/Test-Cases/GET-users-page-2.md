# GET /api/users?page=2 — Test Case

## Test Case ID

TC-API-001

## Title

Получение списка пользователей второй страницы

## Request

**Method:** GET

**Endpoint:**
`{{base_url}}/api/users?page=2`

## Preconditions

- Пользователь зарегистрирован в ReqRes.
- API key настроен в Postman.
- Environment `ReqRes` активен.

## Steps

1. Отправить GET-запрос на `{{base_url}}/api/users?page=2`.
2. Передать `x-api-key`.
3. Проверить Status Code.
4. Проверить параметры пагинации.
5. Проверить количество пользователей.
6. Проверить структуру данных пользователя.

## Expected Result

- Status Code: `200 OK`.
- `page` = `2`.
- `per_page` = `6`.
- `total` = `12`.
- `total_pages` = `2`.
- В массиве `data` содержится 6 пользователей.
- Каждый пользователь содержит:
  - `id`;
  - `email`;
  - `first_name`;
  - `last_name`;
  - `avatar`.

- `id` имеет числовой тип.
- Остальные перечисленные поля имеют строковый тип.
- `avatar` содержит корректный URL.

## Actual Result

- Status Code: `200 OK`.
- `page` = `2`.
- `per_page` = `6`.
- `total` = `12`.
- `total_pages` = `2`.
- В `data` содержится 6 пользователей.
- Все необходимые поля присутствуют.
- `id` имеет числовой тип.
- `email`, `first_name`, `last_name`, `avatar` имеют строковый тип.
- URL `avatar` открывается корректно.

## Result

**PASS**

## Notes

Пользователи второй страницы имеют ID от 7 до 12, что соответствует пагинации при 6 пользователях на странице.
