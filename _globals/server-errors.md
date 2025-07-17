# Server Errors

Describes the structure of server error responses (HTTP 500) returned by the API.

---

## Error Response
When an internal server error occurs, the API returns a `500` status code with the following response:

```json
{
  "error": "Server error"
}
```

> **Note:** This only occurs in the production environment. In local and development environments, PHP errors are shown in the default way.
