# PUT /api/v1/comments/{comment-id}

Updates the content of an existing comment by its ID.


---

## Permissions
| Permission         | Description                        |
|--------------------|------------------------------------|
| `comments.update`  | Update your own comment             |

---

## Path Parameters
| Name        | Type | Required | Description                | Example |
|-------------|------|----------|----------------------------|---------|
| comment-id  | int  | Yes      | ID of the comment to update| 123     |

---

## Request Body Parameters
| Name    | Type   | Required | Description                        | Example         |
|---------|--------|----------|------------------------------------|-----------------|
| content | string | Yes      | New content for the comment (max 255 characters) | "Updated comment!" |

---

## Request Example
```json
{
  "content": "Updated comment!"
}
```

---

## Response

### 200 OK
Returns the updated comment resource.

#### Schema
```json
{
  "comment": { /* Comment Resource */ }
}
```

#### Example
```json
{
  "comment": {
    "id": 123,
    "user_id": 456,
    "user": { /* User Resource (commenter) */ },
    "commentable_type": "App\\Models\\Gyms\\Gym",
    "commentable_id": 42,
    "content": "Updated comment!",
    "parent_comment_id": 10,
    "created_at": "2025-01-01 00:00:00",
    "updated_at": "2025-01-01 00:10:00"
  }
}
```

For a full schema, see [Comment Resource](comment_resource.md).

---

### Error Responses

| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
