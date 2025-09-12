# GET /api/v1/tracker/data/charts

Retrieve your tracker charts data.


---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `start_date`        | string  | No       | Start of the date range (YYYY-MM-DD)                             |
| `end_date`          | string  | No       | End of the date range (YYYY-MM-DD)                               |
| `shared_tracker_id`| string | No         | ID of a shared tracker record (default: your own data)           |
| `search`            | string  | No       | Search by notes                                                  |

---

## Response

### 200 OK
```json
{
    "weight_change_graph": {
        "labels": ["2025-01-02", "2025-02-11", "2025-03-07"],
        "data": {
            "weight": [71, 71.5, 73],
        }
    }
}
```

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
