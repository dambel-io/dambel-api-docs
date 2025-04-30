# Payment Resource


```json
{
    "id": 123,
    "user_id": 123,
    "type": "deposit",
    "amount": 100.0,
    "description": "...",
    "payable_type": "App\\Models\\...",
    "payable_id": 123,
    "meta": {...},
    "is_done": true,
    "created_at": "2025-01-01 00:00:00"
}
```

### Type
The type can be one of these:

- `deposit`
- `income`
- `purchase`
- `withdrawal`
- `commission`
