# `/api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}`

Delete a session from a specific workout plan.


---

## Permissions
| Permission                     | Description                                 |
|--------------------------------|---------------------------------------------|
| `workout_plan_sessions.delete` | Delete sessions for your workout plans       |
| `workout_plans.update`         | Update your own workout plans               |

---

## Response

### 204 No Content
No content is returned when the session is deleted successfully.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../../_globals/authentication-errors.md) |
| 404    | Not Found          | [Not-found error](../../../_globals/not-found-errors.md)           |
| 403    | Forbidden          | [Permission error](../../../_globals/permission-errors.md)         |

---
