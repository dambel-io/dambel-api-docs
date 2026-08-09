# DELETE /api/v1/admin/majors/{major-id}

Delete a major. Optionally transfer attached data to another major.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `majors.view_all`     | Access majors       |
| `majors.delete`       | Delete major        |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                                      |
|------------------|---------|----------|------------------------------------------------------------------|
| `replacement_id` | integer | No       | ID of another major to transfer attached data (optional)          |

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Major deleted successfully."
}
```

Localized from `messages.admin.majors.deleted_successfully` (`fa`: “رشته با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description                                                                                                                        | Reference                                                       |
|--------|------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| 400    | When major has data and `replacement_id` is not provided or is not valid. Number of attached items is returned in `attached_data`. |                                                                 |
| 401    | Unauthorized                                                                                                                       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)                                                                                                          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                                                                                                                          | [Not-found error](../../_globals/not-found-errors.md)           |

---
