# DELETE /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/groups/{group-id}

Dissolve a group. Its exercises are **kept** in the session, ungrouped.


---

## Permissions
| Permission                        | Description                                 |
|------------------------------------|---------------------------------------------|
| `workout_plan_exercises.delete`    | Delete exercises for your workout plans     |
| `workout_plan_sessions.update`     | Update sessions of your workout plans       |
| `workout_plans.update`             | Update your own workout plans               |

---

## Response

### 204 No Content
No response body. The exercises that were in the group are kept, now ungrouped (`group` and
`group_position` become `null`).

---

## Error Responses
| Status | Description               | Reference                                                             |
|--------|---------------------------|-----------------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../../../_globals/authentication-errors.md) |
| 404    | Not found — also when the group is not in this session, or the session not in this plan | [Not-found error](../../../../_globals/not-found-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../../../_globals/permission-errors.md)         |

---
