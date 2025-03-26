# Server errors
When some internal server error happens, you will receive `500` with this response:

```json
{
    "error": "Server error"
}
```

> NOTE: This ONLY happens in production environment. In local and development environments, the PHP errors will be thrown in the normal way
