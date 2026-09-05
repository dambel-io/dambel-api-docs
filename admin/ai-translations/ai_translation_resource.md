# AI Translation Resource

The JSON shape returned by the admin AI-translation endpoints.


---

## Schema
```json
{
  "id": 42,
  "locale": "fa",
  "original_text": "Whey Protein",
  "translated_text": "پروتئین وی",
  "is_protected": false,
  "created_at": "2026-09-01 10:00:00",
  "updated_at": "2026-09-01 10:00:00"
}
```

| Field             | Type   | Description                                                                                     |
|-------------------|--------|-------------------------------------------------------------------------------------------------|
| `id`              | int    | Row ID                                                                                          |
| `locale`          | string | Target locale of the translation (e.g. `fa`)                                                    |
| `original_text`   | string | The English source phrase. Immutable through the API.                                           |
| `translated_text` | string | The stored translation served to clients in this locale                                         |
| `is_protected`    | bool   | `true` once an operator has corrected the row; protected rows are never overwritten by the automatic resolution pipeline or the `ai:translations:retranslate` command |
| `created_at`      | string | Creation timestamp                                                                              |
| `updated_at`      | string | Last-update timestamp                                                                           |

The row's `text_hash` (the sha256 lookup key of `original_text`) is internal and not exposed.

---
