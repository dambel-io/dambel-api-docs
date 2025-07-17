# DELETE /api/v1/comments/{comment-id}

Deletes a comment by its ID.


---

## Permissions
| Permission           | Description                                         |
|----------------------|-----------------------------------------------------|
| view (commentable)   | Must have view permission on the target resource     |
| `comments.delete`    | Delete your own comments                            |
| `comments.delete_any`| Delete any comment (admin or moderator)             |

---

## Path Parameters

| Name        | Type | Required | Description                | Example |
|-------------|------|----------|----------------------------|---------|
| comment-id  | int  | Yes      | ID of the comment to delete| 123     |

---

## Response

### 204 No Content
Comment was successfully deleted. No response body is returned.

---

### Error Responses

| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
