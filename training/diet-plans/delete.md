# `/api/v1/training/diet-plans/{diet-plan-id}`

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
No content is returned when the diet plan is deleted successfully.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 404    | Not Found          | [Not-found error](../../_globals/not-found-errors.md)           |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
