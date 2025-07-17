# Method Not Allowed Errors

Describes the structure of error responses when an unsupported HTTP method is used (HTTP 405).

---

## Error Response
When you call an API with an unsupported HTTP method, you receive a `405` status code with the following response:

```json
{
  "error": "Method not allowed: The GET method is not supported for route api/v1/gyms/1. Supported methods: PUT, DELETE."
}
```
