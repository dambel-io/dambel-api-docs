# DELETE /api/v1/ratings/{rating-id}

Deletes a rating by its ID.


---

## Permissions
| Permission         | Description                                 |
|--------------------|---------------------------------------------|
| view (ratable)     | Must have view permission on the ratable     |
| `ratings.delete`   | Delete your own ratings                      |
| `ratings.delete_any`| Delete any rating (admin only)               |

---

## Path Parameters
| Name      | Type | Required | Description           | Example |
|-----------|------|----------|-----------------------|---------|
| rating-id | int  | Yes      | ID of the rating to delete| 123     |

---

## Response

### 204 No Content
Rating was successfully deleted. Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Rating deleted successfully."
}
```

Localized from `messages.ratings.deleted_successfully` (`fa`: “امتیاز با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
