# GET /api/v1/admin/ai-translations

Search the stored AI translation cache (`ai_translations`). Operator tooling for finding and reviewing machine-produced translations of platform reference data.


---

## Permissions
| Permission                  | Description                  |
|-----------------------------|------------------------------|
| `ai_translations.view_all`  | Search the translation store |

---

## Query Parameters
| Name           | Type   | Required | Description                                                                                  | Example   |
|----------------|--------|----------|----------------------------------------------------------------------------------------------|-----------|
| `locale`       | string | No       | Filter to one target locale (max 10 chars)                                                   | `fa`      |
| `search`       | string | No       | Substring match against the English source (`original_text`) **or** the stored translation (`translated_text`). `%` and `_` are treated literally. Max 255 chars | `پروتئین` |
| `is_protected` | bool   | No       | Filter by protection state (operator-corrected rows are protected). One of `true`, `false`, `1`, `0`; anything else is a 422 | `true`    |
| `per_page`     | int    | No       | Page size, 1–100 (default 50)                                                                | `25`      |

Results are ordered newest-first.

---

## Response

### 200 OK
Returns a paginated list of AI translation resources.

#### Schema
```json
{
  "data": [
    { /* AI Translation Resource */ }
  ],
  "links": { /* Pagination Data */ },
  "meta": { /* Pagination Data */ }
}
```

For a full schema, see [AI Translation Resource](ai_translation_resource.md) and [Pagination Data](../../_globals/pagination-data.md).

---

### Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |

---
