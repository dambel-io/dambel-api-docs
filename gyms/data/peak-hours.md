# GET /api/v1/gyms/{gym-id}/peak-hours

Retrieves peak hours graph data for a gym on a specific weekday within a given date range.


---

## Permissions
| Permission                   | Description                                 |
|------------------------------|---------------------------------------------|
| `gyms.view_own_data_reports` | View data reports for your own gym          |
| `gyms.view_all_data_reports` | View data reports for all gyms              |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 42      |

---

## Query Parameters
| Name       | Type   | Required | Description                        | Example      |
|------------|--------|----------|------------------------------------|--------------|
| weekday    | string | Yes      | Name of the weekday (e.g., "monday") | "monday"    |
| start_date | string | Yes      | Start date for the range (YYYY-MM-DD) | "2024-01-01" |
| end_date   | string | Yes      | End date for the range (YYYY-MM-DD)   | "2024-01-31" |

---

## Request Example
```
GET /api/v1/gyms/42/peak-hours?weekday=monday&start_date=2024-01-01&end_date=2024-01-31
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns an object with hour keys and visit counts for the specified weekday.

#### Example
```json
{
  "monday": {
    "00": 15,
    "01": 15,
    "02": 15,
    "...": 15,
    "22": 15,
    "23": 15
  }
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../permission-errors.md) |
| 404    | Not found                  | [Not-found error](../not-found-errors.md) |
