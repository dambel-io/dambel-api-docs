# DELETE /api/v1/gyms/{gym-id}/buffet-items/{buffet-item-id}

Deletes a buffet item from a gym by its ID.


---

## Permissions
| Permission                    | Description                                         |
|-------------------------------|-----------------------------------------------------|
| `gym_buffet_items.delete`     | Delete buffet items from your own gym               |
| `gym_buffet_items.delete_any` | Delete buffet items from any gym (admin only)       |

---

## Path Parameters
| Name           | Type | Required | Description                | Example |
|----------------|------|----------|----------------------------|---------|
| gym-id         | int  | Yes      | ID of the gym              | 123     |
| buffet-item-id | int  | Yes      | ID of the buffet item      | 5       |

---

## Response

### 204 No Content
Buffet item was successfully deleted. Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Buffet item deleted successfully."
}
```

Localized from `messages.gyms.buffet_items.deleted_successfully` (`fa`: “مورد بوفه با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
