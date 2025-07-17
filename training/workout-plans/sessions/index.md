# `/api/v1/training/workout-plans/{workout-plan-id}/sessions`

Retrieve a list of sessions for a specific workout plan.


---

## Permissions
| Permission                     | Description                                 |
|--------------------------------|---------------------------------------------|
| `workout_plan_sessions.view`   | View sessions of your workout plans         |
| `workout_plans.view`           | View your own workout plans                 |

---

## Response

### 200 OK
```
{
  "data": [<workout plan session resource>, ...]
}
```
- See [Workout Plan Session Resource](workout_plan_session_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../../_globals/authentication-errors.md) |
| 404    | Not Found          | [Not-found error](../../../_globals/not-found-errors.md)           |
| 403    | Forbidden          | [Permission error](../../../_globals/permission-errors.md)         |

---
