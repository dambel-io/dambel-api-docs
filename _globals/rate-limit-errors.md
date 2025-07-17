# Rate Limit Errors

Describes the structure of error responses when the rate limit is exceeded (HTTP 429).

---

## Error Response
When you exceed the allowed number of requests, you receive a `429` status code with the following response:

```json
{
  "error": "Too many requests. Please try again"
}
```
