# User Resource

Represents a user in the system.


---

## Schema
| Field                    | Type            | Description                                                                 |
|--------------------------|-----------------|-----------------------------------------------------------------------------|
| `id`                     | integer         | User ID                                                                     |
| `email`                  | string          | User email address *(hidden for limited access)*                           |
| `phone`                  | string          | User phone number *(hidden for limited access)*                            |
| `bank_account_number`    | string\|null    | Bank account number *(hidden for limited access)*                          |
| `trainer_license_image`  | string\|null    | Filename of the uploaded trainer license document *(hidden for limited access)* |
| `trainer_license_link`   | string\|null    | Download path for the license document, or `null` when none is uploaded *(hidden for limited access)* |
| `trainer_license_approved` | boolean\|null | `null` = pending review, `true` = approved, `false` = rejected *(hidden for limited access)* |
| `trainer_license_rejection_reason` | string\|null | Operator's reason when rejected *(hidden for limited access)*     |
| `username`               | string          | Username                                                                   |
| `first_name`             | string          | First name                                                                 |
| `last_name`              | string          | Last name                                                                  |
| `created_at`             | string (date)   | Account creation timestamp                                                 |
| `referral_code`          | string          | User's referral code                                                       |
| `referrer_user_id`       | integer\|null   | Referring user ID, if any *(hidden for limited access)*                    |
| `height`                 | integer\|null   | User's height in CM                                                        |
| `birth_date`             | string (date)\|null| User's birth date                                                       |
| `gender`             | string\|null| User's gender (`male`, `female`, `other`)                                                       |
| `referral_score`         | integer         | User's referral score *(hidden for limited access)*                        |
| `roles`                  | array           | List of [Role Resource](../admin/roles/role_resource.md) *(hidden for limited access)* |
| `media`                  | array           | List of [Media Resource](../media/media_resource.md). Excludes purpose-bearing rows such as the trainer license |
| `current_subscription`   | object\|null    | [User Premium Subscription Resource](../payments/user_premium_subscription_resource.md) |

**Trainer license:** the document is identity PII. It is never attached to the public `media` array, and `trainer_license_link` points at the standard media download route, which refuses to serve purpose-bearing media to anyone but the subject and holders of `users.view_all`. See [Download Media](../media/download.md).

**Note:** Fields marked with *(hidden for limited access)* are only included when the viewer is the user themself or an authenticated user with the `users.view_all` permission. All other viewers — including unauthenticated guests (e.g. on public endpoints that embed a user, such as the training services list) and users with only `users.view_limited` — do not receive these fields.

---

## Example
```json
{
  "id": 123,
  "email": "test@example.com",
  "phone": "+12345678",
  "bank_account_number": "IR123456789012345678901234",
  "trainer_license_image": "9f2c1b7e4a.jpg",
  "trainer_license_link": "/api/v1/media/456/9f2c1b7e4a.jpg",
  "trainer_license_approved": true,
  "trainer_license_rejection_reason": null,
  "username": "test_username",
  "first_name": "John",
  "last_name": "Doe",
  "created_at": "1970-01-01 00:00:00",
  "referral_code": "XFER543D4...",
  "referrer_user_id": null,
  "height": 180,
  "birth_date": "1990-01-01",
  "gender": "male",
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
