# DELETE /api/v1/tracker/workouts/{tracker-workout-id}/sets/{workout-set-id}

Delete a workout set record in the tracker system.


---

## Permissions
| Permission                      | Description                |
|----------------------------------|----------------------------|
| `tracker_workout_sets.delete`    | Delete tracker workout set |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
No content is returned when the workout set record is deleted successfully.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../../_globals/permission-errors.md)         |

---
