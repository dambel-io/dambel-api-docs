# DELETE /api/v1/posts/{post-id}

Deletes a post by its ID.


---

## Permissions
| Permission         | Description                                 |
|--------------------|---------------------------------------------|
| view (profile)     | Must have view permission on the profile     |
| `posts.delete`     | Delete your own posts                        |
| `posts.delete_any` | Delete any post (admin only)                 |

---

## Path Parameters
| Name     | Type | Required | Description           | Example |
|----------|------|----------|-----------------------|---------|
| post-id  | int  | Yes      | ID of the post to delete| 123     |

---

## Response

### 204 No Content
Post was successfully deleted. No response body is returned.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
