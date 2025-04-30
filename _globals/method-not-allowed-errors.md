# Method-not-allowed errors
When you try to call an API with wrong HTTP method, you will receive `405` with this response:

```json
{
    "error": "Method not allowed: The GET method is not supported for route api/v1/gyms/1. Supported methods: PUT, DELETE."
}
```
