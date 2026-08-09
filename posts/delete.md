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
Post was successfully deleted. Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Post deleted successfully."
}
```

Localized from `messages.posts.deleted_successfully` (`fa`: “پست با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
