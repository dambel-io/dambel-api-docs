# Validation errors
When you pass some params to an API and there are some validation errors, errors will be returned in this structure in all of the APIs with status code `422`:

```json
{
    "errors": {
        "<field name>": [
            "error 1",
            "error 2",
            "..."
        ],
        "email": [
            "Email field is required",
        ]
    }
}
```
