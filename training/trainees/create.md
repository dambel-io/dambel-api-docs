# `/api/v1/training/trainees`

Create a new trainee record.

Trainers can create trainees, and users can create a trainer from their side.


---

## Permissions
| Permission           | Description                                         |
|----------------------|-----------------------------------------------------|
| `trainees.create`    | Create trainees/trainers for yourself               |
| `trainees.create_any`| Create trainees/trainers for any user               |

---

## Request Body Parameters
| Name                | Type    | Required | Description                        |
|---------------------|---------|----------|------------------------------------|
| `user_id`           | int     | Yes      | ID of the trainee user account     |
| `training_service_id`| int    | Yes      | ID of the training service         |
| `notes`             | string  | No       | Optional notes                     |

---

## Response

### 201 Created
```
<trainee resource>
```
- See [Trainee Resource](trainee_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 400    | Bad Request        | Insufficient account balance for training service payment.      |
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

*Note: Payment is not required if creation is from the trainer side.*

---
