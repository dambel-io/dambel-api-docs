# GET /api/v1/training/services

Retrieve a list of training services.


**No authentication required.** A token is honoured when present (optional auth), which is what lets trainers see their own unlisted services and admins see every service.

---

## Permissions
| Permission                   | Description                                                                                              |
|------------------------------|----------------------------------------------------------------------------------------------------------|
| `training_services.view_all` | List every service, including those whose trainer's license is not approved (admin only).                |

> **Visibility:** a service is publicly listed only while its trainer's `trainer_license_approved` is `true`. Services belonging to a trainer whose license is pending (`null`) or rejected (`false`) are hidden from everyone except that trainer and admins, and they cannot be purchased — see [Create Trainee](../trainees/create.md).

---

## Query Parameters
| Name         | Type   | Required | Description                                                             |
|--------------|--------|----------|-------------------------------------------------------------------------|
| `service_id` | string | No       | Filter by training service ID(s); comma-separated for multiple          |
| `user_id`    | string | No       | Filter by user IDs (comma-separated for multiple)                       |
| `category`   | string | No       | Filter by categories (comma-separated): `diet_plan`, `workout_plan`, `other` |
| `major_ids`  | string | No       | Filter by major IDs (comma-separated for multiple)                      |
| `search`     | string | No       | Search by title, description, and trainer name                          |
| `page`       | int    | No       | Page number for pagination                                              |
| `sort`       | string | No       | `asc` for oldest, `desc` for latest (default: `desc`)                   |

> **Note:** Results are first sorted by marketing boosts; `sort` applies secondarily.

---

## Response

### 200 OK
Returns a paginated list of training service resources.

```json
{
  "data": [ { /* training service resource */ }, ... ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

See [Training Service Resource](training_service_resource.md) and [Pagination Data](../../_globals/pagination-data.md) (per page: 50).
