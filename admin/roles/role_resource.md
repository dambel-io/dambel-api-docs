# Role Resource

Represents a role in the system.


---

## Schema
| Field          | Type    | Description                                 |
|--------------- |---------|---------------------------------------------|
| `id`           | integer | Role ID                                     |
| `name`         | string  | Role name                                   |
| `permissions`  | array   | List of [Permission Resource](../permissions/permission_resource.md) |

---

## Example
```
{
  "id": 123,
  "name": "...",
  "permissions": [<permission resource>, ...]
}
```

---

