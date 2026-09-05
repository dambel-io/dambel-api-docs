# POST /api/v1/training/trainees

Create a new trainee record.

Trainers can create trainees, and users can create a trainer from their side.


---

## Permissions
| Permission           | Description                                         |
|----------------------|-----------------------------------------------------|
| `trainees.create`    | Create trainees/trainers for yourself               |
| `trainees.create_any`| Create trainees/trainers for any user. Held by `super_admin` and `operator` only — this branch skips the purchase step, so it is not granted to `user` or `user_plus`. |

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
```json
{ /* trainee resource */ }
```
- See [Trainee Resource](trainee_resource.md)

When the caller — **the client buying it themselves, a trainer, or an operator** — creates an enrolment that
already exists and is **undelivered** (same client, same trainer, same service), nothing is created: the existing
record is returned with the same `201`, and **nothing is charged a second time** — no second purchase for a client,
no second commission for a trainer. A double-tapped or retried submit is therefore safe. Once the enrolment is
marked `is_delivered`, enrolling the same client again is a new sale and does charge again.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 400    | Insufficient balance — only when the client buys the service themselves | [Insufficient-balance error](../../_globals/insufficient-balance-errors.md) |
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 403    | The service's trainer does not have an approved license (`trainer_license_approved` is not `true`). Holders of `trainees.create_any` are exempt. |  |
| 422    | The service is priced below zero and cannot be purchased. Only reachable for rows written before `price` gained its `min:0` rule. |  |

*Note: who pays depends on who creates the record.*

| Caller | Charged | Amount |
|---|---|---|
| The client themselves (`user_id` is the caller) | The client | the full discounted service price |
| The service's trainer | The trainer | the platform commission, `price × monetization.gym_commission_rate` (1%) |
| A holder of `trainees.create_any` (operator) | Nobody | — |

A trainer enrolling a client has sold the service off-platform, so the platform still books its
commission against the trainer's wallet, linked to the created `Trainee`. No `purchase` or `income`
row is created — nothing was paid through the platform. A free service (`0` after discount) books no
row at all. The trainer's balance is **not** checked: a short wallet never blocks the enrolment. The
commission is booked regardless and the trainer's balance may go negative, to be settled by their next
deposit. The 400 above is only ever returned to a client buying the service for themselves.

---
