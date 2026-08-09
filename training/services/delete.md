# /api/v1/training/services/{training-service-id}

Delete a training service from a user.


---

## Permissions
| Permission                 | Description                                         |
|----------------------------|-----------------------------------------------------|
| `training_services.delete` | Delete your own training services                   |
| `training_services.delete_any` | Delete training services from any user           |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Training service deleted successfully."
}
```

Localized from `messages.training.services.deleted_successfully` (`fa`: “سرویس تمرینی با موفقیت حذف شد.”).

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not-found error](../../_globals/not-found-errors.md)           |

---
