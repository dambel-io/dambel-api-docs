# POST /api/v1/gyms/{gym-id}/subscriptions/manage

Creates a new subscription for a user in a specific gym.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_subscriptions.create`    | Create subscriptions for your own gyms      |
| `gym_subscriptions.create_any`| Create subscriptions for any gym            |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Body Parameters
| Name        | Type | Required | Description                | Example |
|-------------|------|----------|----------------------------|---------|
| gym_plan_id | int  | Yes      | ID of the gym plan         | 10      |
| user_id     | int  | Yes      | ID of the user             | 789     |

---

## Request Example
```json
{
  "gym_plan_id": 10,
  "user_id": 789
}
```

---

## Response

### 201 Created
Returns the created gym subscription resource.

If the member already holds a **live** subscription to the same plan (`expires_at` in the future or `null`),
nothing is created: the existing subscription is returned with the same `201`, and **no second commission is
booked**. A double-tapped or retried submit is therefore safe. Once a subscription has expired, adding the
member again is a renewal and does book its own commission.

#### Example
```json
{ /* gym subscription resource */ }
```

For a full schema, see [Gym Subscription Resource](../gym_subscription.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym or plan) |  |
| 422    | Validation error           | [Validation error](../../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |

---

## Commission

The membership was sold off-platform, so the platform books its commission —
`plan price after discount × monetization.gym_commission_rate` (1%) — against the **gym owner's**
wallet, linked to the created `GymSubscription`. That holds even when a gym admin is the one calling:
the gym's money is the owner's.

No `purchase` or `income` row is created — nothing was paid through the platform. A free plan
(`0` after discount) books no row at all, and holders of `gym_subscriptions.create_any` (operators
acting on a support request) are exempt. The owner's balance is **not** checked: a short wallet never
blocks the enrolment. The commission is booked regardless and the owner's balance may go negative, to be
settled by their next deposit. This endpoint therefore never returns an insufficient-balance error, and a
gym admin is never shown anything about the owner's wallet.

See [Commission](../../../../payments.md#commission).

## Notifications

On success, matching the in-app [subscribe](../subscribe.md) path:

- the **subscriber** receives `Gyms\Subscriptions\GymSubscriptionAddedNotification`;
- the **gym owner** receives `Gyms\Subscriptions\NewGymSubscriptionNotification` when someone else
  (a gym admin or an operator) made the addition.

The caller is never notified about their own action. See the
[notification catalogue](../../../notifications/notification_resource.md).
