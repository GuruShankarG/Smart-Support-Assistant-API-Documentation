# Search APIs

This section describes how to perform search operations across Tickets, Users, Organizations, and Global resources using Zendesk Search API.

---

## 🔎 Base Endpoint

```
GET https://own-48441.zendesk.com/api/v2/search.json
```

---

## 🔐 Authentication

All search APIs require authentication using:

- API Token (Basic Auth)
- Email + API Token

Example:
```
username: your_email/token
password: API_token
```

---

## 📌 1. Search Tickets

### Description
Search tickets based on filters like status, priority, type, etc.

### Endpoint
```
GET /api/v2/search.json?query=type:ticket
```

### Example Request
```
GET https://own-48441.zendesk.com/api/v2/search.json?query=type:ticket status:open
```

### Example Response
```json
{
  "results": [
    {
      "id": 123,
      "type": "ticket",
      "subject": "Login issue",
      "status": "open"
    }
  ]
}
```

---

## 👤 2. Search Users

### Description
Search users by name, email, or role.

### Endpoint
```
GET /api/v2/search.json?query=type:user
```

### Example Request
```
GET https://own-48441.zendesk.com/api/v2/search.json?query=type:user email:john@example.com
```

### Example Response
```json
{
  "results": [
    {
      "id": 456,
      "name": "John Doe",
      "email": "john@example.com"
    }
  ]
}
```

---

## 🏢 3. Search Organizations

### Description
Search organizations by name or domain.

### Endpoint
```
GET /api/v2/search.json?query=type:organization
```

### Example Request
```
GET https://own-48441.zendesk.com/api/v2/search.json?query=type:organization name:Acme
```

### Example Response
```json
{
  "results": [
    {
      "id": 789,
      "name": "Acme Corporation"
    }
  ]
}
```

---

## 🌐 4. Global Search

### Description
Search across tickets, users, and organizations in a single query.

### Endpoint
```
GET /api/v2/search.json?query=login
```

### Example Request
```
GET https://own-48441.zendesk.com/api/v2/search.json?query=type:ticket login
```

### Example Response
```json
{
  "results": [
    {
      "id": 123,
      "type": "ticket",
      "subject": "Login issue"
    },
    {
      "id": 456,
      "type": "user",
      "name": "Login Admin"
    }
  ]
}
```

---

## ⚡ Query Syntax Rules

- type:ticket
- type:user
- type:organization
- Combine filters using space (AND logic)

Example:
```
type:ticket status:open priority:high
```

---

## 🚨 Notes

- Maximum results per request: 100
- Supports pagination
- Search is case-insensitive
``` 
