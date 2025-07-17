# `/api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}`

Update a session in a specific workout plan.


---

## Permissions
| Permission                     | Description                                 |
|--------------------------------|---------------------------------------------|
| `workout_plan_sessions.update` | Update sessions for your workout plans       |
| `workout_plans.update`         | Update your own workout plans               |

---

## Request Body Parameters
| Name          | Type    | Required | Description                                 |
|---------------|---------|----------|---------------------------------------------|
| `title`       | string  | No       | Title of the session (max 255, e.g. Leg Day)|
| `day`         | string  | No       | Weekday of the session (`saturday`, etc.)   |
| `description` | string  | No       | Description (max 2000, optional)            |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
```
<workout plan session resource>
```
- See [Workout Plan Session Resource](workout_plan_session_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../../_globals/authentication-errors.md) |
| 404    | Not Found          | [Not-found error](../../../_globals/not-found-errors.md)           |
| 403    | Forbidden          | [Permission error](../../../_globals/permission-errors.md)         |

---
