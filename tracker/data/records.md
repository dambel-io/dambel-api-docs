# GET /api/v1/tracker/data/records

Retrieve highest records of your exercises.


---

## Query Parameters
| Name                | Type    | Required | Description                                                       |
|---------------------|---------|----------|-------------------------------------------------------------------|
| `by_rep`            | boolean | No       | Set to true if you want to get highest reps instead of the weight |
| `shared_tracker_id` | string  | No       | ID of a shared tracker record (default: your own data)           |

---

## Response

### 200 OK
```json
{
  "data": [<tracker exercise set resource>]
}
```

[Tracker Exercise Set Resource](../workouts/sets/tracker_workout_set_resource.md): The `exercise` is also pre-loaded.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
