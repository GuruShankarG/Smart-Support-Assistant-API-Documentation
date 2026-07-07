# Triggers API Documentation

## Overview
Triggers in Zendesk are business rules that automatically perform actions when conditions are met, such as notifying users or updating ticket fields.

---

## Base URL
```
https://own-48441.zendesk.com/api/v2
```

---

## Authentication
All APIs require authentication using:

- API Token Authentication OR
- Basic Auth (email/token + API token)

### Example
```
username = your_email/token
password = API token
```

---

## 1. List Triggers

### Endpoint
```
GET /triggers.json
```

### Full URL
```
https://own-48441.zendesk.com/api/v2/triggers.json
```

### Description
Retrieves a list of all available triggers in the account.

---

### Headers
```
Content-Type: application/json
Authorization: Basic Auth
```

---

### Sample Response
```json
{
  "triggers": [
    {
      "id": 28471025415196,
      "title": "Notify requester and CCs of received request",
      "active": true,
      "created_at": "2026-06-26T10:10:58Z",
      "updated_at": "2026-06-26T10:10:58Z"
    }
  ]
}
```

---

### Status Codes
- 200 Success
- 401 Unauthorized
- 403 Forbidden

---

## 2. Get Trigger

### Endpoint
```
GET /triggers/{trigger_id}.json
```

### Full URL
```
https://own-48441.zendesk.com/api/v2/triggers/{trigger_id}.json
```

### Description
Fetch detailed information about a specific trigger using its ID.

---

### Path Parameter

| Parameter  | Type    | Description        |
|------------|---------|--------------------|
| trigger_id | integer | ID of the trigger  |

---

### Example Request
```
GET https://own-48441.zendesk.com/api/v2/triggers/28471025415196.json
```

---

### Sample Response
```json
{
  "trigger": {
    "id": 28471025415196,
    "title": "Notify requester and CCs of received request",
    "active": true,
    "conditions": {},
    "actions": {},
    "created_at": "2026-06-26T10:10:58Z",
    "updated_at": "2026-06-26T10:10:58Z"
  }
}
```

---

### Status Codes
- 200 Success
- 404 Trigger not found
- 401 Unauthorized

---

## Notes
- Triggers are generally read-only via API unless admin permissions are enabled.
- Always ensure authentication is properly configured before calling endpoints.

---

## Use Case
Triggers help automate support workflows such as:
- Sending notifications to users
- Assigning tickets automatically
- Updating ticket status based on conditions
```