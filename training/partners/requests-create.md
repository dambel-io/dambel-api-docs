# POST /api/v1/training/partners/requests

Ask another user to train together.


---

## Permissions
| Permission                 | Description              |
|----------------------------|--------------------------|
| `training_partners.create` | Send a partner request   |

---

## Request Body
| Name                | Type   | Required | Description                                     |
|---------------------|--------|----------|-------------------------------------------------|
| `addressee_user_id` | int    | Yes      | The user you are asking. Cannot be yourself      |
| `message`           | string | No       | Max 500 characters                              |

The addressee must have an **active** partner profile. A user who has not opted in — or has opted
out — returns **404**, not 403: somebody who does not take part in partner matching is not
reachable through this endpoint, and a 403 would confirm that their account exists.

---

## Response

### 201 Created
The request was created, with status `pending` and no chat.

### 200 OK
A request from you to this user already exists. **The existing row is returned untouched**, so a
double tap creates one request rather than two, and re-sending does not reset a request the
addressee has already declined.

```json
{
  "data": <training partner request resource>
}
```
- See [Training Partner Request Resource](training_partner_request_resource.md)

The pair is unique per direction, so the other user may still send their own request back to you.

---

## Error Responses
| Status | Error Type       | Reference                                                       |
|--------|------------------|-----------------------------------------------------------------|
| 401    | Unauthorized     | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden        | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found        | [Not found error](../../_globals/not-found-errors.md)           |
| 422    | Validation Error | [Validation error](../../_globals/validation-errors.md)         |

---
