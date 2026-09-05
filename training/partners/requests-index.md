# GET /api/v1/training/partners/requests

List the training-partner requests you are a party to, in either direction.


---

## Permissions
| Permission               | Description                    |
|--------------------------|--------------------------------|
| `training_partners.view` | Read your own partner requests |

Only requests you sent or received. Other people's requests are never listed.

---

## Query Parameters
| Name        | Type   | Required | Description                                                     |
|-------------|--------|----------|-----------------------------------------------------------------|
| `direction` | string | No       | `sent` or `received`. Omit for both                              |
| `status`    | string | No       | `pending`, `accepted` or `declined`                              |
| `per_page`  | int    | No       | Results per page (default 50, **capped at 100**)                 |
| `page`      | int    | No       | Page number for pagination                                       |

Ordered by `created_at` descending, with the id as a tie-break.

---

## Response

### 200 OK
```json
{
  "data": [<training partner request resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Training Partner Request Resource](training_partner_request_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md)

---

## Error Responses
| Status | Error Type       | Reference                                                       |
|--------|------------------|-----------------------------------------------------------------|
| 401    | Unauthorized     | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden        | [Permission error](../../_globals/permission-errors.md)         |
| 422    | Validation Error | [Validation error](../../_globals/validation-errors.md)         |

---
