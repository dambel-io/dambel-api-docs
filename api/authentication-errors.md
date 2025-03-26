# Authentication errors
When you try to access an API that requires authentication but you have not passed the bearer token, you will receive `401` error with this response:

```json
{
    "error": "You are not authenticated"
}
```
