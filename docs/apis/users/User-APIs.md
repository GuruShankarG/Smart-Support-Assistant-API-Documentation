# User APIs - Smart Support Assistant

Base URL:
https://own-48441.zendesk.com/api/v2

---

# Authentication (Required for all APIs)

All requests must use Zendesk API Token Authentication.

## Headers
Content-Type: application/json

## Auth Type (Postman)
Basic Auth:
- Username: your_email/token
- Password: ZENDESK_API_TOKEN

---

# 1. Get User by ID

## Method: GET
## Endpoint:
/users/{user_id}.json

## Example Request:
https://own-48441.zendesk.com/api/v2/users/123456.json

## Headers:
Content-Type: application/json

## Response:
```json
{
  "user": {
    "id": 123456,
    "name": "John Doe",
    "email": "john@example.com",
    "role": "end-user"
  }
}
```

---

# 2. List Users

## Method: GET
## Endpoint:
/users.json

## Example Request:
https://own-48441.zendesk.com/api/v2/users.json

## Headers:
Content-Type: application/json

## Response:
```json
{
  "users": [
    {
      "id": 1,
      "name": "User One",
      "email": "one@example.com"
    },
    {
      "id": 2,
      "name": "User Two",
      "email": "two@example.com"
    }
  ]
}
```

---

# 3. Create User

## Method: POST
## Endpoint:
/users.json

## Example Request:
https://own-48441.zendesk.com/api/v2/users.json

## Headers:
Content-Type: application/json

## Body:
```json
{
  "user": {
    "name": "New User",
    "email": "newuser@example.com",
    "role": "end-user"
  }
}
```

## Response:
```json
{
  "user": {
    "id": 999,
    "name": "New User",
    "email": "newuser@example.com",
    "role": "end-user"
  }
}
```

---

# 4. Update User

## Method: PUT
## Endpoint:
/users/{user_id}.json

## Example Request:
https://own-48441.zendesk.com/api/v2/users/123456.json

## Headers:
Content-Type: application/json

## Body:
```json
{
  "user": {
    "name": "Updated Name",
    "email": "updated@example.com"
  }
}
```

## Response:
```json
{
  "user": {
    "id": 123456,
    "name": "Updated Name",
    "email": "updated@example.com"
  }
}
```

---

# 5. Search Users

## Method: GET
## Endpoint:
/users/search.json?query={keyword}

## Example Request:
https://own-48441.zendesk.com/api/v2/users/search.json?query=john

## Headers:
Content-Type: application/json

## Response:
```json
{
  "users": [
    {
      "id": 123,
      "name": "John Doe",
      "email": "john@example.com"
    }
  ]
}
```

---