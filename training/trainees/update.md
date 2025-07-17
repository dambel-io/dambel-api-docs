# `/api/v1/training/trainees/{trainee-id}`

Update a trainee record.


---

## Permissions
| Permission           | Description                                         |
|----------------------|-----------------------------------------------------|
| `trainees.update`    | Update your own trainees/trainers                   |
| `trainees.update_any`| Update trainees/trainers for any user               |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                                        |
|--------------|---------|----------|--------------------------------------------------------------------|
| `notes`      | string  | No       | Optional notes                                                     |
| `is_delivered`| boolean| No       | Specify if the service is delivered (only trainer can update this) |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

---

## Response

### 200 OK
```
<trainee resource>
```
- See [Trainee Resource](trainee_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
