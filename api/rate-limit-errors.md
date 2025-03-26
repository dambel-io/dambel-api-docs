# Rate-limit errors
Some of the APIs have rate limit. Whenever you hit the limit, you will receive error `429` with this response:

```json
{
    "error": "Too many requests. Please try again"
}
```
