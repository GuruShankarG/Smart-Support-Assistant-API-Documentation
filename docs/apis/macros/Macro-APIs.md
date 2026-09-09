# Macro APIs

## Overview

Macros in Zendesk are predefined sets of actions that agents can apply to tickets. These APIs allow you to:

- List available macros
- Retrieve a macro by ID
- Apply a macro to a ticket

---

## Base URL

```
https://own-48441.zendesk.com/api/v2
```

---

## Authentication

These APIs use **Basic Authentication** with a Zendesk API Token.

### Username

```
your_email/token
```

### Password

```
your_api_token
```

### Required Headers

| Header | Value |
|---------|-------|
| Authorization | Basic Authentication |
| Content-Type | application/json |
| Accept | application/json |

---

# 1. List Macros

Retrieves all active macros available in the Zendesk account.

## Endpoint

```
GET /api/v2/macros.json
```

### Full URL

```
https://own-48441.zendesk.com/api/v2/macros.json
```

### Headers

| Header | Required |
|---------|----------|
| Authorization | Yes |
| Content-Type | application/json |

### Path Parameters

None

### Query Parameters

None

### Sample Request

```http
GET /api/v2/macros.json HTTP/1.1
Host: own-48441.zendesk.com
Authorization: Basic <Base64EncodedCredentials>
Content-Type: application/json
```

### Sample Response

```json
{
  "macros": [
    {
      "id": 28471046373404,
      "title": "Close and redirect to topics",
      "active": true
    }
  ]
}
```

### Success Response

| Status Code | Description |
|--------------|-------------|
| 200 OK | Macros retrieved successfully |

### Error Responses

| Status Code | Description |
|--------------|-------------|
| 401 Unauthorized | Invalid authentication credentials |
| 403 Forbidden | Access denied |
| 404 Not Found | Resource not found |

### Notes

- Returns all active macros.
- Each macro includes its ID, title, and status.

---

# 2. Get Macro

Retrieves detailed information about a specific macro.

## Endpoint

```
GET /api/v2/macros/{macro_id}.json
```

### Full URL

```
https://own-48441.zendesk.com/api/v2/macros/28471046373404.json
```

### Path Parameters

| Name | Type | Description |
|------|------|-------------|
| macro_id | Integer | Unique Macro ID |

### Headers

| Header | Required |
|---------|----------|
| Authorization | Yes |
| Content-Type | application/json |

### Sample Request

```http
GET /api/v2/macros/28471046373404.json HTTP/1.1
Host: own-48441.zendesk.com
Authorization: Basic <Base64EncodedCredentials>
Content-Type: application/json
```

### Sample Response

```json
{
  "macro": {
    "id": 28471046373404,
    "title": "Close and redirect to topics",
    "active": true,
    "created_at": "2026-06-26T10:09:32Z",
    "updated_at": "2026-06-26T10:09:32Z"
  }
}
```

### Success Response

| Status Code | Description |
|--------------|-------------|
| 200 OK | Macro retrieved successfully |

### Error Responses

| Status Code | Description |
|--------------|-------------|
| 401 Unauthorized | Invalid authentication credentials |
| 404 Not Found | Macro not found |

### Notes

- Returns complete information for the specified macro.

---

# 3. Apply Macro

Applies a macro to an existing ticket.

## Endpoint

```
PUT /api/v2/tickets/{ticket_id}.json?macro_id={macro_id}
```

### Full URL

```
https://own-48441.zendesk.com/api/v2/tickets/1.json?macro_id=28471046373404
```

### Path Parameters

| Name | Type | Description |
|------|------|-------------|
| ticket_id | Integer | Ticket ID |

### Query Parameters

| Name | Type | Description |
|------|------|-------------|
| macro_id | Integer | Macro ID to apply |

### Headers

| Header | Required |
|---------|----------|
| Authorization | Yes |
| Content-Type | application/json |

### Request Body

```json
{}
```

### Sample Request

```http
PUT /api/v2/tickets/1.json?macro_id=28471046373404 HTTP/1.1
Host: own-48441.zendesk.com
Authorization: Basic <Base64EncodedCredentials>
Content-Type: application/json
```

### Sample Response

```json
{
  "ticket": {
    "id": 1,
    "status": "closed"
  }
}
```

### Success Response

| Status Code | Description |
|--------------|-------------|
| 200 OK | Macro applied successfully |

### Error Responses

| Status Code | Description |
|--------------|-------------|
| 401 Unauthorized | Invalid authentication credentials |
| 404 Not Found | Ticket or Macro not found |
| 422 Unprocessable Entity | Invalid request |

### Notes

Applying a macro may automatically update:

- Ticket status
- Priority
- Assignee
- Tags
- Custom fields
- Internal/Public comments

---

# Summary

| API | HTTP Method | Description |
|------|-------------|-------------|
| List Macros | GET | Retrieve all active macros |
| Get Macro | GET | Retrieve a macro by ID |
| Apply Macro | PUT | Apply a macro to a ticket |

--- 
