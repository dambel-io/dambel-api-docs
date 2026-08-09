# DELETE /api/v1/admin/cities/{city-id}

Delete a city. Optionally transfer attached data to another city.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `cities.view_all`  | Access cities       |
| `cities.delete`    | Delete any city     |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                                      |
|------------------|---------|----------|------------------------------------------------------------------|
| `replacement_id` | integer | No       | ID of another city to transfer attached data (optional)          |

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "City deleted successfully."
}
```

Localized from `messages.admin.cities.deleted_successfully` (`fa`: “شهر با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description                                                                                                                       | Reference                                                       |
|--------|-----------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| 400    | When city has data and `replacement_id` is not provided or is not valid. Number of attached items is returned in `attached_data`. |                                                                 |
| 401    | Unauthorized                                                                                                                      | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)                                                                                                         | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                                                                                                                         | [Not-found error](../../_globals/not-found-errors.md)           |

---
