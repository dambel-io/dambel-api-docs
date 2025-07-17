# User Resource

Represents a user in the system.


---

## Schema
| Field                    | Type            | Description                                 |
|--------------------------|-----------------|---------------------------------------------|
| `id`                     | integer         | User ID                                     |
| `email`                  | string          | User email address                          |
| `phone`                  | string          | User phone number                           |
| `first_name`             | string          | First name                                  |
| `last_name`              | string          | Last name                                   |
| `created_at`             | string (date)   | Account creation timestamp                  |
| `referral_code`          | string          | User's referral code                        |
| `referrer_user_id`       | integer\|null   | Referring user ID, if any                   |
| `roles`                  | array           | List of [Role Resource](../admin/roles/role_resource.md) |
| `media`                  | array           | List of [Media Resource](../media/media_resource.md)     |
| `current_subscription`   | object\|null    | [User Premium Subscription Resource](../payments/user_premium_subscription_resource.md) |

---

## Example
```
{
  "id": 123,
  "email": "test@example.com",
  "phone": "+12345678",
  "first_name": "John",
  "last_name": "Doe",
  "created_at": "1970-01-01 00:00:00",
  "referral_code": "XFER543D4...",
  "referrer_user_id": null,
  "roles": [<role resource>, ...],
  "media": [<media resource>, ...],
  "current_subscription": <user premium subscription resource>
}
```

---

## Related Resources
- [Role Resource](../admin/roles/role_resource.md)
- [Media Resource](../media/media_resource.md)
- [User Premium Subscription Resource](../payments/user_premium_subscription_resource.md)

---
