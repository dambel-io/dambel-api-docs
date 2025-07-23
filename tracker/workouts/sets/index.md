# GET /api/v1/tracker/workouts/{tracker-workout-id}/sets

Retrieve a list of workout set records for a workout in the tracker system.


---

## Permissions
| Permission                   | Description                |
|------------------------------|----------------------------|
| `tracker_workout_sets.view`  | View tracker workout sets  |

---

## Response

### 200 OK
```json
{
  "data": [<tracker workout set resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Tracker Workout Set Resource](tracker_workout_set_resource.md)
- See [Pagination Data](../../../_globals/pagination-data.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../../_globals/permission-errors.md)         |

---
