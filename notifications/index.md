# GET /api/v1/notifications

Retrieves a paginated list of the latest notifications for the authenticated user.


---

## Response

### 200 OK
Returns a paginated list of notification resources.

#### Schema
```json
{
  "data": [
    { /* Notification Resource */ }
  ],
  "links": { /* Pagination Data */ },
  "meta": { /* Pagination Data */ }
}
```

#### Example
```json
{
  "data": [
    {
      "id": 123,
      "type": "Comments\\NewCommentNotification",
      "data": {
        "comment_id": 456,
        "content": "Great post!"
      },
      "read_at": "2025-01-01 00:00:00",
      "created_at": "2025-01-01 00:00:00"
    }
  ],
  "links": {
    "first": "https://api.example.com/api/v1/notifications?page=1",
    "last": "https://api.example.com/api/v1/notifications?page=5",
    "prev": null,
    "next": "https://api.example.com/api/v1/notifications?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 5,
    "path": "https://api.example.com/api/v1/notifications",
    "per_page": 50,
    "to": 50,
    "total": 250
  }
}
```

For a full schema, see [Notification Resource](notification_resource.md) and [Pagination Data](../_globals/pagination-data.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
