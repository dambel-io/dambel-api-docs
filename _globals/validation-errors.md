# Validation Errors

Describes the structure of error responses when request parameters fail validation (HTTP 422).

---

## Error Response
When validation errors occur, the API returns a `422` status code with the following structure:

```json
{
  "errors": {
    "<field name>": [
      "error 1",
      "error 2"
    ],
    "email": [
      "Email field is required"
    ]
  }
}
```
