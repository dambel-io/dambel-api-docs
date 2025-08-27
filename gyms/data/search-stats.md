# GET /api/v1/gyms/{gym-id}/search-stats

Receive chart data of search stats in the given date range and filters for the gym.


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
| Name         | Type    | Required | Description                                                      | Example                |
|--------------|---------|----------|------------------------------------------------------------------|------------------------|
| start_date   | string  | No       | Start of date range (YYYY-MM-DD)                                 | "2024-01-01"          |
| end_date     | string  | No       | End of date range (YYYY-MM-DD)                                   | "2024-01-31"          |
| group_by  | string  | No       | How to group the chart data: "day", "week", "month"                                            | "day"          |

---

## Request Example
```
GET /api/v1/gyms/42/search-stats?group=day&start_date=2024-01-01&end_date=2024-01-31
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns chart data.

#### Example
```json
{
  "labels": ["2025-01", "2025-02", "2025-03"],
  "data": {
    "views": [1200, 800, 1000],
    "clicks": [50, 60, 80],
  }
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
