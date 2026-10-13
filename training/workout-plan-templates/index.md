# GET /api/v1/training/workout-plan-templates

List the built-in workout plan templates — ready-made plans curated by Dambel that a user can copy into a plan of
their own with [`POST /api/v1/training/workout-plans`](../workout-plans/create.md) and `workout_plan_template_id`.


Templates are read-only: they are seeded from `src/database/data/workout_plan_templates.json` and cannot be created or
edited through the API. Text (`title`, `description`, session titles, exercise notes) is returned in the request locale
(`Accept-Language: fa` or `en`; anything else falls back to English). Templates are free — any user who may create a
workout plan may list and use them.

---

## Permissions
| Permission             | Description                                  |
|------------------------|----------------------------------------------|
| `workout_plans.create` | Create workout plans (and start one from a template) |

---

## Query Parameters
None. The list is **not paginated**: it is a small curated catalog returned whole, in display order (`sort_order`,
then `id`). Unpublished templates are never returned.

---

## Response

### 200 OK
```json
{
  "data": [<workout plan template resource>, ...]
}
```
- [Workout Plan Template Resource](workout_plan_template_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
