# `/api/v1/training/trainees`

Retrieve and search trainees.


---

## Permissions
| Permission         | Description                                              |
|--------------------|----------------------------------------------------------|
| `trainees.view`    | View your own trainers and trainees                      |
| `trainees.view_any`| View all trainee records in the system (admin only)      |

---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `user_id`           | string  | No       | Filter by trainee user IDs (comma-separated for multiple)         |
| `trainer_id`        | string  | No       | Filter by trainer user IDs (comma-separated for multiple)         |
| `training_service_id`| string | No       | Filter by training service IDs (comma-separated for multiple)     |
| `is_delivered`      | boolean | No       | Filter by delivery status                                        |
| `page`              | int     | No       | Page number for pagination                                       |
| `sort`              | string  | No       | `asc` for oldest, `desc` for latest (default: `desc`)            |

---

## Response

### 200 OK
```json
{
  "data": [<trainee resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Trainee Resource](trainee_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md) (per page: 50)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not-found error](../../_globals/not-found-errors.md)           |

---
