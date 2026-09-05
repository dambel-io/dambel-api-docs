# DELETE /api/v1/training/diet-plans/{diet-plan-id}

Delete a diet plan.


---

## Permissions
| Permission        | Description                |
|-------------------|----------------------------|
| `diet_plans.delete` | Delete your own diet plans |

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
  "message": "Diet plan deleted successfully."
}
```

Localized from `messages.training.diet_plans.deleted_successfully` (`fa`: “پلن غذایی با موفقیت حذف شد.”).

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 404    | Not Found          | [Not-found error](../../_globals/not-found-errors.md)           |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
