# Authentication Errors

Describes the structure of error responses when authentication is required but missing or invalid (HTTP 401).

---

## Error Response
When you access an API that requires authentication without a valid bearer token, you receive a `401` status code with the following response:

```json
{
  "error": "You are not authenticated"
}
```

---

## How to Authenticate
See [How to use API tokens](../auth/login.md#how-to-use-api-token) for details on authenticating API requests.
