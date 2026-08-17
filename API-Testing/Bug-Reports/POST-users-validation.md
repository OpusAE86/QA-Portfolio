# POST /api/users — Missing Required Field Validation

## Bug ID

BUG-API-001

## Title

POST /api/users позволяет создать пользователя без обязательного поля `name`

## Environment

**Application:** ReqRes API

**Endpoint:** `POST /api/users`

**Tool:** Postman

## Preconditions

- Пользователь зарегистрирован в ReqRes.
- API key настроен в Postman.
- Environment `ReqRes` активен.

## Steps to Reproduce

1. Открыть Postman.
2. Создать POST-запрос на `{{base_url}}/api/users`.
3. Передать `x-api-key`.
4. Передать следующий JSON:

```json
{
  "job": "QA Engineer"
}
```

5. Нажать **Send**.

## Expected Result

API должен отклонить запрос, поскольку поле `name` является обязательным.

**Expected Status Code:** `400 Bad Request`

Пользователь не должен быть создан.

## Actual Result

API возвращает:

**Status Code:** `201 Created`

Пользователь создаётся без поля `name`.

## Result

**FAIL**

## Severity

**High**

## Priority

**High**

## Additional Information

API также не выполняет ожидаемую валидацию других некорректных входных данных, включая отсутствие `job`, пустое значение `name` и числовое значение `name`.
