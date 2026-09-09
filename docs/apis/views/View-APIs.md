# View APIs

## Overview

Views are predefined ticket filters in Zendesk. They help agents quickly access tickets that match specific conditions such as:

- Open tickets
- Pending tickets
- Solved tickets
- High priority tickets
- Tickets assigned to the current agent

This document explains how to retrieve available views, get details of a specific view, and execute a view to retrieve matching tickets.

---

## Base URL

```
https://own-48441.zendesk.com/api/v2
```

---

## Authentication

All View APIs require Basic Authentication using:

- Email Address
- API Token

Example

```
Authorization:
Basic Base64(email/token:api_token)
```

---

# 1. List Views

## Description

Returns all active ticket views available in the Zendesk account.

---

### HTTP Request

```
GET /api/v2/views.json
```

---

### Full URL

```
GET https://own-48441.zendesk.com/api/v2/views.json
```

---

### Headers

| Header | Value |
|---------|-------|
| Authorization | Basic Authentication |
| Content-Type | application/json |

---

### Request Body

None

---

### Successful Response (200)

```json
{
  "views": [
    {
      "id": 28471025429404,
      "title": "Your unsolved tickets",
      "active": true
    },
    {
      "id": 28471025500000,
      "title": "Recently solved"
    }
  ]
}
```

---

### Status Codes

| Code | Meaning |
|------|----------|
|200|Success|
|401|Unauthorized|
|403|Forbidden|
|500|Server Error|

---

### Notes

- Returns all active views.
- Each view has a unique View ID.
- The View ID is required for Get View and Execute View APIs.

---

# 2. Get View

## Description

Returns detailed information about a specific view.

---

### HTTP Request

```
GET /api/v2/views/{view_id}.json
```

---

### Example

```
GET /api/v2/views/28471025429404.json
```

---

### Full URL

```
https://own-48441.zendesk.com/api/v2/views/28471025429404.json
```

---

### Path Parameters

| Parameter | Description |
|-----------|-------------|
|view_id|Unique View ID|

---

### Headers

| Header | Value |
|---------|-------|
|Authorization|Basic Authentication|
|Content-Type|application/json|

---

### Successful Response (200)

```json
{
  "view": {
    "id": 28471025429404,
    "title": "Your unsolved tickets",
    "active": true,
    "position": 1
  }
}
```

---

### Status Codes

| Code | Meaning |
|------|----------|
|200|Success|
|401|Unauthorized|
|404|View Not Found|

---

### Notes

Returns complete metadata of the selected view.

---

# 3. Execute View

## Description

Executes a view and returns all tickets matching the view conditions.

---

### HTTP Request

```
GET /api/v2/views/{view_id}/execute.json
```

---

### Example

```
GET /api/v2/views/28471025429404/execute.json
```

---

### Full URL

```
https://own-48441.zendesk.com/api/v2/views/28471025429404/execute.json
```

---

### Path Parameters

| Parameter | Description |
|-----------|-------------|
|view_id|Unique View ID|

---

### Headers

| Header | Value |
|---------|-------|
|Authorization|Basic Authentication|
|Content-Type|application/json|

---

### Request Body

None

---

### Successful Response (200)

```json
{
  "rows": [
    {
      "id": 1,
      "subject": "Unable to login",
      "status": "Open",
      "priority": "High",
      "requester_id": 28471045896860
    }
  ]
}
```

---

### Status Codes

| Code | Meaning |
|------|----------|
|200|Success|
|401|Unauthorized|
|404|View Not Found|

---

### Notes

- Returns ticket records matching the view conditions.
- Results change automatically as tickets are updated.
- Useful for dashboards and reporting.

---

# Summary

| API | Method | Endpoint |
|------|--------|----------|
|List Views|GET|/api/v2/views.json|
|Get View|GET|/api/v2/views/{view_id}.json|
|Execute View|GET|/api/v2/views/{view_id}/execute.json|
 
