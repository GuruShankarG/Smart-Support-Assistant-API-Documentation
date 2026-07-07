# Organization APIs

Base URL:
https://own-48441.zendesk.com/api/v2

Authentication:
All APIs require authentication using API token or OAuth.

Format:
Authorization: Basic {your_email}/token:{your_zendesk_api_token}

---

## 1. Get Organization by ID

### Endpoint
GET /organizations/{organization_id}.json

### Full URL
https://own-48441.zendesk.com/api/v2/organizations/{organization_id}.json

### Headers
Authorization: Basic {your_email}/token:{your_zendesk_api_token}

### Example Request
GET https://own-48441.zendesk.com/api/v2/organizations/28471046361500.json

### Sample Response
```json
{
  "organization": {
    "id": 28471046361500,
    "name": "own",
    "external_id": null,
    "created_at": "2026-06-26T10:09:31Z",
    "updated_at": "2026-06-26T10:09:31Z"
  }
}
```

---

## 2. List Organizations

### Endpoint
GET /organizations.json

### Full URL
https://own-48441.zendesk.com/api/v2/organizations.json

### Headers
Authorization: Basic {your_email}/token:{your_zendesk_api_token}

### Example Request
GET https://own-48441.zendesk.com/api/v2/organizations.json

### Sample Response
```json
{
  "organizations": [
    {
      "id": 28471046361500,
      "name": "own",
      "shared_tickets": false
    }
  ]
}
```

---

## 3. Create Organization

### Endpoint
POST /organizations.json

### Full URL
https://own-48441.zendesk.com/api/v2/organizations.json

### Headers
Content-Type: application/json
Authorization: Basic {your_email}/token:{your_zendesk_api_token}

### Request Body
```json
{
  "organization": {
    "name": "New Organization",
    "notes": "Created from API",
    "shared_tickets": true
  }
}
```

### Sample Response
```json
{
  "organization": {
    "id": 123456789,
    "name": "New Organization",
    "shared_tickets": true
  }
}
```

---

## 4. Update Organization

### Endpoint
PUT /organizations/{organization_id}.json

### Full URL
https://own-48441.zendesk.com/api/v2/organizations/{organization_id}.json

### Headers
Content-Type: application/json
Authorization: Basic {your_email}/token:{your_zendesk_api_token}

### Request Body
```json
{
  "organization": {
    "name": "Updated Organization Name",
    "notes": "Updated via API",
    "shared_tickets": false
  }
}
```

### Sample Response
```json
{
  "organization": {
    "id": 28471046361500,
    "name": "Updated Organization Name"
  }
}
```

---

## 5. Search Organizations

### Endpoint
GET /organizations/search.json?query={search_text}

### Full URL
https://own-48441.zendesk.com/api/v2/organizations/search.json?query=own

### Headers
Authorization: Basic {your_email}/token:{your_zendesk_api_token}

### Example Request
GET https://own-48441.zendesk.com/api/v2/organizations/search.json?query=own

### Sample Response
```json
{
  "organizations": [
    {
      "id": 28471046361500,
      "name": "own"
    }
  ]
}
```