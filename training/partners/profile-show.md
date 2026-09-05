# GET /api/v1/training/partners/profile

Read your own training-partner profile.


---

## Permissions
| Permission                | Description                        |
|---------------------------|------------------------------------|
| `training_partners.view`  | Read your partner profile and matches |

There is no path parameter: this route serves the caller's own single profile and no other. Other
people's profiles are read through [the matches feed](matches.md), which returns only users who
have opted in.

---

## Response

### 200 OK
```json
{
  "data": <training partner profile resource>
}
```
- See [Training Partner Profile Resource](training_partner_profile_resource.md)

### 404 Not Found
Returned when you have never written a profile. There is nothing to read yet — a client renders its
"find a training partner" invitation from this, and creates the profile with
[`PUT /profile`](profile-update.md).

---

## Error Responses
| Status | Error Type    | Reference                                                       |
|--------|---------------|-----------------------------------------------------------------|
| 401    | Unauthorized  | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden     | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found     | [Not found error](../../_globals/not-found-errors.md)           |

---
