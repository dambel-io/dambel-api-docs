# Training Partner Request Resource

Returned by [`GET /requests`](requests-index.md), [`POST /requests`](requests-create.md) and
[`PUT /requests/{request-id}`](requests-respond.md).


```json
{
  "id": 4,
  "requester_user_id": 42,
  "requester_user": <user resource>,
  "addressee_user_id": 51,
  "addressee_user": <user resource>,
  "status": "accepted",
  "message": "Want to train legs on Tuesdays?",
  "chat_id": 9,
  "responded_at": "2026-09-04 12:30:00",
  "created_at": "2026-09-04 12:00:00"
}
```

| Field               | Type          | Description                                                        |
|---------------------|---------------|--------------------------------------------------------------------|
| `id`                | int           | Request id                                                          |
| `requester_user_id` | int           | Who asked                                                           |
| `requester_user`    | object        | See [User Resource](../../users/user_resource.md)                   |
| `addressee_user_id` | int           | Who was asked — the only user who may answer                        |
| `addressee_user`    | object        | See [User Resource](../../users/user_resource.md)                   |
| `status`            | string        | `pending`, `accepted` or `declined`                                 |
| `message`           | string\|null  | The requester's note                                                |
| `chat_id`           | int\|null     | The chat acceptance opened. `null` until the addressee accepts      |
| `responded_at`      | string\|null  | When the request was answered                                       |
| `created_at`        | string        | When the request was sent                                           |

`chat_id` is the record of mutual consent, and what a client opens the conversation from.

The two user objects are present only where the endpoint loaded them; all three request endpoints
do. `UserResource` does its own gating of the sensitive fields.

---
