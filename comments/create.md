# POST /api/v1/comments

Creates a new comment on a specified resource (e.g., gym, post, or training service).


---

## Permissions
| Permission         | Description                                      |
|--------------------|--------------------------------------------------|
| `comments.create`  | Create comments as the authenticated user         |
| view (commentable) | Must have view permission on the target resource  |

---

## Request Parameters

| Name              | Type   | Required | Description                                                                 | Example      |
|-------------------|--------|----------|-----------------------------------------------------------------------------|--------------|
| commentable_type  | string | Yes      | Type of the resource to comment on. One of: `gym`, `post`, `trainingService`| "gym"       |
| commentable_id    | int    | Yes      | ID of the resource to comment on                                            | 42           |
| content           | string | Yes      | Content of the comment (max 255 characters)                                 | "Great gym!"|
| parent_comment_id | int    | No       | ID of the parent comment (for replies)                                      | 10           |

---

## Request Example

```json
{
  "commentable_type": "gym",
  "commentable_id": 42,
  "content": "Great gym!",
  "parent_comment_id": 10
}
```

---

## Response

### 201 Created
Returns the created comment resource.

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
    "commentable_type": "App\\Models\\Gyms\\Gym",
    "commentable_id": 42,
    "content": "Great gym!",
    "parent_comment_id": 10,
    "created_at": "2025-01-01 00:00:00",
    "updated_at": "2025-01-01 00:03:00"
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
