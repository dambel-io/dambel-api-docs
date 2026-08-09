# DELETE /api/v1/gyms/{gym-id}

Deletes a gym by its ID. Normal users can delete their own gyms, while admins can delete any gym.


---

## Permissions
| Permission         | Description                                 |
|--------------------|---------------------------------------------|
| `gyms.delete`      | Delete your own gym                         |
| `gyms.delete_any`  | Delete any gym (admin only)                 |

---

## Path Parameters
| Name    | Type | Required | Description           | Example |
|---------|------|----------|-----------------------|---------|
| gym-id  | int  | Yes      | ID of the gym to delete| 123     |

---

## Response

### 204 No Content
Gym was successfully deleted. Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Gym deleted successfully."
}
```

Localized from `messages.gyms.deleted_successfully` (`fa`: “باشگاه با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
