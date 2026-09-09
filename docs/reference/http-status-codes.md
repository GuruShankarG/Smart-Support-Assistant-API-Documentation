# HTTP Status Codes

## Overview

HTTP status codes indicate the outcome of an API request. They help developers determine whether a request was successful or identify the reason for a failure.

The Smart Support Assistant uses standard HTTP status codes returned by the Zendesk API.

---

# Success Status Codes (2xx)

## 200 OK

**Description**

The request was successful, and the server returned the requested data.

**Example Usage**

- Search tickets
- Get ticket details
- Get ticket comments
- Retrieve users
- Retrieve organizations

---

## 201 Created

**Description**

The request was successful, and a new resource was created.

**Example Usage**

- Create a new ticket
- Create a user
- Create an organization

---

## 204 No Content

**Description**

The request was successful, but there is no content to return.

**Example Usage**

- Delete a resource
- Update a resource without returning data

---

# Client Error Status Codes (4xx)

## 400 Bad Request

**Description**

The request contains invalid data or missing parameters.

**Possible Causes**

- Invalid request body
- Missing required field
- Incorrect parameter

**Recommended Action**

Verify the request before sending it.

---

## 401 Unauthorized

**Description**

Authentication failed.

**Possible Causes**

- Invalid email
- Invalid API token
- Missing authentication

**Recommended Action**

Verify your authentication credentials.

---

## 403 Forbidden

**Description**

The authenticated user does not have permission to perform the requested operation.

**Possible Causes**

- Insufficient permissions
- Restricted resource

**Recommended Action**

Verify user permissions.

---

## 404 Not Found

**Description**

The requested resource could not be found.

**Possible Causes**

- Invalid Ticket ID
- Invalid User ID
- Incorrect endpoint

**Recommended Action**

Verify the resource identifier.

---

## 409 Conflict

**Description**

The request conflicts with the current state of the resource.

**Possible Causes**

- Duplicate operation
- Resource conflict

**Recommended Action**

Review the existing resource before retrying.

---

## 422 Unprocessable Entity

**Description**

The request is valid, but the submitted data failed validation.

**Possible Causes**

- Missing required fields
- Invalid field values

**Recommended Action**

Correct the validation errors and resend the request.

---

## 429 Too Many Requests

**Description**

The API rate limit has been exceeded.

**Possible Causes**

- Too many requests in a short period

**Recommended Action**

Wait for the duration specified in the **Retry-After** header before retrying.

---

# Server Error Status Codes (5xx)

## 500 Internal Server Error

**Description**

An unexpected error occurred on the server.

**Recommended Action**

Retry the request later.

---

## 502 Bad Gateway

**Description**

The server received an invalid response from an upstream service.

**Recommended Action**

Retry after a short delay.

---

## 503 Service Unavailable

**Description**

The service is temporarily unavailable.

**Recommended Action**

Wait and retry the request later.

---

## Status Code Summary

| Status Code | Meaning | Category |
|-------------|---------|----------|
| 200 | OK | Success |
| 201 | Created | Success |
| 204 | No Content | Success |
| 400 | Bad Request | Client Error |
| 401 | Unauthorized | Client Error |
| 403 | Forbidden | Client Error |
| 404 | Not Found | Client Error |
| 409 | Conflict | Client Error |
| 422 | Unprocessable Entity | Client Error |
| 429 | Too Many Requests | Client Error |
| 500 | Internal Server Error | Server Error |
| 502 | Bad Gateway | Server Error |
| 503 | Service Unavailable | Server Error |

---

# Best Practices

- Always check the HTTP status code before processing the response.
- Handle both success and error responses appropriately.
- Display user-friendly error messages.
- Log unexpected errors for troubleshooting.
- Implement retry logic for temporary server errors and rate limits.

---

# Summary

Understanding HTTP status codes helps developers identify the outcome of API requests, troubleshoot issues efficiently, and build reliable integrations with the Zendesk API. 
