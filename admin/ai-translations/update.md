# PUT /api/v1/admin/ai-translations/{ai-translation-id}

Correct a stored AI translation. The correction takes effect on the next request that renders the phrase, and the row is marked protected so the automatic resolution pipeline and the `ai:translations:retranslate` command never overwrite it.

**Protection is one-way and permanent.** Nothing in the API, the MCP tools or the artisan command clears `is_protected` once this endpoint has set it, so a phrase corrected here — including one corrected by mistake — is excluded from every future re-translation run for good. The only way back is a direct database edit. Correcting the same row again is fine; un-protecting it is not currently possible.


---

## Permissions
| Permission                  | Description                    |
|-----------------------------|--------------------------------|
| `ai_translations.view_all`  | Access the translation store   |
| `ai_translations.update`    | Correct a stored translation   |

---

## Request Body Parameters
| Name              | Type   | Required | Description                          |
|-------------------|--------|----------|--------------------------------------|
| `translated_text` | string | Yes      | The corrected translation (max 5000) |

`locale`, `original_text` and the internal `text_hash` identify the row to the resolution pipeline and are immutable through this API — values sent for them are ignored.

---

## Response

### 200 OK
```json
{
  "data": { /* AI Translation Resource, with is_protected: true */ }
}
```
- [AI Translation Resource](ai_translation_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../_globals/not-found-errors.md)           |

---
