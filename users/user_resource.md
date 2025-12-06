# User Resource

Represents a user in the system.


---

## Schema
| Field                    | Type            | Description                                                                 |
|--------------------------|-----------------|-----------------------------------------------------------------------------|
| `id`                     | integer         | User ID                                                                     |
| `email`                  | string          | User email address *(hidden for limited access)*                           |
| `phone`                  | string          | User phone number *(hidden for limited access)*                            |
| `username`               | string          | Username                                                                   |
| `first_name`             | string          | First name                                                                 |
| `last_name`              | string          | Last name                                                                  |
| `created_at`             | string (date)   | Account creation timestamp                                                 |
| `referral_code`          | string          | User's referral code                                                       |
| `referrer_user_id`       | integer\|null   | Referring user ID, if any *(hidden for limited access)*                    |
| `height`                 | integer\|null   | User's height in CM                                                        |
| `birth_date`             | string (date)\|null| User's birth date                                                       |
| `referral_score`         | integer         | User's referral score *(hidden for limited access)*                        |
| `roles`                  | array           | List of [Role Resource](../admin/roles/role_resource.md) *(hidden for limited access)* |
| `media`                  | array           | List of [Media Resource](../media/media_resource.md)                       |
| `current_subscription`   | object\|null    | [User Premium Subscription Resource](../payments/user_premium_subscription_resource.md) |

**Note:** Fields marked with *(hidden for limited access)* are only included when the authenticated user has `users.view_all` permission or when a user with `users.view_limited` permission is viewing their own profile. Users with only `users.view_limited` permission will not see other users' sensitive fields, but can see their own.

---

## Example
```json
{
  "id": 123,
  "email": "test@example.com",
  "phone": "+12345678",
  "username": "test_username",
  "first_name": "John",
  "last_name": "Doe",
  "created_at": "1970-01-01 00:00:00",
  "referral_code": "XFER543D4...",
  "referrer_user_id": null,
  "height": 180,
  "birth_date": "1990-01-01",
  "referral_score": 5,
  "roles": [<role resource>, ...],
  "media": [<media resource>, ...],
  "current_subscription": <user premium subscription resource>
}
```

---

## Referral Score
This number is calculated based on the number of people that this user has invited to the platform + half of their score too.

So if we have a tree like this:

- User 1
    - User 2
        - User 3

These are gonna be the scores:

- User 1: 1 + 0.5 (half of 1) = 1.5
- User 2: 1
- User 3: 0

The depth has no limit.

---

## Related Resources
- [Role Resource](../admin/roles/role_resource.md)
- [Media Resource](../media/media_resource.md)
- [User Premium Subscription Resource](../payments/user_premium_subscription_resource.md)

---
