# POST /api/v1/training/workout-plans

Create a new workout plan for yourself or a trainee — empty, or as a copy of a built-in
[workout plan template](../workout-plan-templates/index.md).


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `workout_plans.create` | Create workout plan for yourself or trainee |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `title`      | string  | Yes, unless `workout_plan_template_id` is sent | Title of the workout plan (max 255). With a template, defaults to the template's title in the request locale |
| `description`| string  | No       | Description (max 2000, optional). With a template, defaults to the template's description |
| `is_active`| boolean  | No       | Set as active plan (optional, default false). It changes all other plans to false if is set to true            |
| `trainee_id` | int     | No       | Trainee ID (if creating for a trainee)      |
| `workout_plan_template_id` | int | No | A **published** template from [`GET /training/workout-plan-templates`](../workout-plan-templates/index.md) to copy |

> Note: setting `is_active` to true deactivates the **owner's** other plans — the trainee's when `trainee_id` is sent, your own otherwise. A trainer's own plans are never touched by a plan created for a trainee.

### Creating from a template
With `workout_plan_template_id`, the template's sessions, exercises, set structure (technique and parameters, rep ranges,
tempo, rest) and exercise groups are copied into the new plan in one transaction. Text — plan, session and exercise notes — is
copied in the request locale (`Accept-Language: fa` or `en`). The copy is **fully independent**: it can be edited or deleted
like any plan, and later changes to the template never reach it. Ownership, `trainee_id`, `is_active` and the trainee's
"new workout plan" notification behave exactly as for an empty plan. Templates are free (`workout_plans.create` only).

The response then also includes every session's `exercises`
([Workout Plan Exercise Resource](sessions/exercises/workout_plan_exercise_resource.md), with `exercise` and `group` loaded) —
see the [session resource](sessions/workout_plan_session_resource.md). Without a template the response shape is unchanged.

---

## Response

### 201 Created
```json
{ /* workout plan resource */ }
```
- [Workout Plan Resource](workout_plan_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error — includes `workout_plan_template_id` not naming a published template | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission, or `trainee_id` is not your trainee) | [Permission error](../../_globals/permission-errors.md)         |

---
