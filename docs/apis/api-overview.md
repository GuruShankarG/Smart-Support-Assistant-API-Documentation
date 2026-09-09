# API Overview

## Overview

The **Smart Support Assistant API** uses the Zendesk REST API to manage customer support resources. Each API endpoint performs a specific operation such as creating tickets, managing users, searching records, or configuring automation.

The API enables applications to manage customer support operations including:

- Ticket management
- User management
- Organization management
- Search operations
- Views and automation
- AI-assisted ticket workflows

Each API endpoint performs a specific operation such as creating tickets, retrieving data, updating records, searching resources, or executing workflows.

---

## Zendesk Environment

| Property | Value |
|---|---|
| Platform | Zendesk REST API |
| Zendesk Domain | `https://own-48441.zendesk.com` |
| API Version | v2 |
| Base URL | `https://own-48441.zendesk.com/api/v2` |

This document provides an overview of the available API categories. Detailed documentation for each category is available in the `docs/APIs` folder.

---

## Base URL

All API requests are sent to your Zendesk subdomain.

```text
https://your-subdomain.zendesk.com/api/v2/
```

Replace `your-subdomain` with your Zendesk account subdomain.

Example:

```text
https://own-48441.zendesk.com/api/v2
```

---

## Supported HTTP Methods

The Smart Support Assistant uses the following HTTP methods:

| Method | Purpose                   |
| ------ | ------------------------- |
| GET    | Retrieve data             |
| POST   | Create new resources      |
| PUT    | Update existing resources |
| DELETE | Delete resources          |

---

## API Categories

### Ticket APIs

Manage support tickets.

Common operations include:

* Create Ticket
* Get Ticket
* Update Ticket
* Delete Ticket
* List Tickets

Documentation:

```text
docs/APIs/Ticket-APIs.md
```

---

### User APIs

Manage Zendesk users.

Common operations include:

* Create User
* Get User
* Update User
* List Users

Documentation:

```text
docs/APIs/User-APIs.md
```

---

### Organization APIs

Manage organizations.

Common operations include:

* Create Organization
* Get Organization
* Update Organization
* List Organizations

Documentation:

```text
docs/APIs/Organization-APIs.md
```

---

### Search APIs

Search tickets, users, organizations, and other resources.

Documentation:

```text
docs/APIs/Search-APIs.md
```

---

### View APIs

Retrieve ticket views and their associated tickets.

Documentation:

```text
docs/APIs/View-APIs.md
```

---

### Macro APIs

Retrieve and execute ticket macros.

Documentation:

```text
docs/APIs/Macro-APIs.md
```

---

### Trigger APIs

Retrieve and manage automation triggers.

Documentation:

```text
docs/APIs/Trigger-APIs.md
```

---

## Request Format

Most API requests use JSON.

Example:

```json
{
  "ticket": {
    "subject": "Unable to log in",
    "comment": {
      "body": "Customer cannot access the application."
    }
  }
}
```

---

## Response Format

Successful responses are returned in JSON.

Example:

```json
{
  "ticket": {
    "id": 101,
    "subject": "Unable to log in",
    "status": "open"
  }
}
```

---

## Common Response Codes

| Status Code | Description                   |
| ----------- | ----------------------------- |
| 200         | Request successful            |
| 201         | Resource created successfully |
| 204         | Resource deleted successfully |
| 400         | Bad request                   |
| 401         | Unauthorized                  |
| 403         | Forbidden                     |
| 404         | Resource not found            |
| 429         | Too many requests             |
| 500         | Internal server error         |

---

## Next Step

The following documents provide detailed information about each API category:

* Ticket APIs
* User APIs
* Organization APIs
* Search APIs
* View APIs
* Macro APIs
* Trigger APIs
 
