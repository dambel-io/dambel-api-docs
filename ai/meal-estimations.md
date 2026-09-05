# POST /api/v1/ai/meal-estimations

Estimates the nutritional content of a meal from a single photograph, returning machine-readable macros
in the shape [`POST /api/v1/tracker/meals`](../tracker/meals/create.md) accepts without transformation.


The photo is sent to the model as an inline base64 `data:` URI and **discarded with the request** — it is
not stored, not attached to a meal, and never written to a log. Nothing about the estimate is logged
either, beyond the caller's id, the model, the token counts and the cost.

---

## Permissions
No permission is required beyond authentication. The call is metered against the caller's own rolling
24-hour AI spend budget, exactly as an AI chat message is — see [AI usage limits](../../ai.md).

---

## Request Body Parameters
| Name  | Type | Required | Description                                                        | Example  |
|-------|------|----------|--------------------------------------------------------------------|----------|
| image | file | Yes      | One photo of the meal: `image/jpeg`, `image/png` or `image/webp`, max 10 MB | meal.jpg |

The request must be sent as `multipart/form-data`. One image per call — this endpoint does not accept a
list, and it does not accept PDFs.

---

## Request Example
```
POST /api/v1/ai/meal-estimations
Content-Type: multipart/form-data

image=@meal.jpg
```

---

## Response

### 200 OK

```json
{
  "data": {
    "description": "Grilled chicken breast, white rice, and a side salad",
    "calories": 620,
    "protein": 52,
    "carb": 61,
    "fat": 14,
    "confidence": "medium",
    "advisory": true
  }
}
```

| Field         | Type            | Description |
|---------------|-----------------|-------------|
| `description` | string          | What the model identified, including any portion-size assumption it had to make. For a photo that is not food, this says so. |
| `calories`    | integer \| null | Energy of the whole portion shown, in kilocalories. |
| `protein`     | integer \| null | Grams of protein in the whole portion shown. |
| `carb`        | integer \| null | Grams of carbohydrate in the whole portion shown. |
| `fat`         | integer \| null | Grams of fat in the whole portion shown. |
| `confidence`  | string          | `high`, `medium` or `low`. `medium` means the portion size was assumed; `low` means the food itself is partly guesswork. |
| `advisory`    | boolean         | Always `true`. Part of the contract: the estimate is advisory, not clinical, and must be presented as an editable suggestion rather than a fact. |

The four numbers carry the same names and the same integer type as the nullable columns on
`tracker_meals`, so the object can be handed to the meal form unchanged.

**Any of the four may be `null`, and a null is a real answer.** A figure the model could not judge is
returned as `null` rather than as a guess or a zero — a photo that is not food comes back with all four
`null` and a `description` saying so, never with fabricated numbers.

**Macros are checked against the calories** by the same invariant the meal-writing AI tool enforces
(protein and carbohydrate at 4 kcal/g, fat at 9 kcal/g, within a tolerance). An answer that contradicts
itself is asked for once more; if the second answer contradicts itself too, `calories` is returned as
`null` rather than passed on. `calories` is the field that goes because it is the one derivable from the
other three.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 422    | Validation error — missing image, disallowed MIME type, or over 10 MB | [Validation error](../_globals/validation-errors.md) |
| 429    | AI usage budget exceeded — the caller's rolling 24-hour AI spend (USD) reached their tier budget. Body is `{"error": "…"}`, the same shape as [POST .../messages](threads/messages/create.md). | |
| 429    | Rate limit — more than 10 requests per minute to this endpoint | [Rate limit error](../_globals/rate-limit-errors.md) |
| 500    | The model's answer could not be read. No estimate is invented in this case. | [Server error](../_globals/server-errors.md) |

> **Two distinct 429s.** The budget refusal is decided per user over a rolling 24-hour window; the rate
> limit is `throttle:10,1` and is decided per minute. This endpoint is throttled harder than the chat
> endpoint's `30,1` because every call is a paid vision completion.

---

## Metering
A successful call writes one `ai_usage_events` row (`feature = meal_photo_estimate`) carrying the served
model, the token counts and the USD cost. That table is summed alongside `ai_thread_messages` when the
budget is checked, so a meal estimate and an AI chat message draw on the same daily allowance. A retried
estimate is billed twice, because it is two completions.
