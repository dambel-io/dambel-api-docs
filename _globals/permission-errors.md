# Permission Errors

Describes the structure of error responses when the user lacks required permissions (HTTP 403).

---

## Error Response
When you call an API without the necessary permissions, you receive a `403` status code with the following response:

```json
{
  "error": "You do not have permission to perform this action"
}
```
