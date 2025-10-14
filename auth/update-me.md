# PUT /api/v1/auth/me

Allows the currently authenticated user to update their own profile information.


---

## Permissions
This endpoint requires authentication but does not require any special permissions. Users can only update their own profile.

---

## Request Body Parameters
| Name         | Type    | Required | Description                                             |
|--------------|---------|----------|---------------------------------------------------------|
| `first_name` | string  | No       | First name (max 255 characters)                         |
| `last_name`  | string  | No       | Last name (max 255 characters)                          |
| `email`      | string  | No       | Email address (must be valid email format, unique)      |
| `username`   | string  | No       | Username (max 255 characters, unique)                   |
| `height`     | integer | No       | User's height in centimeters                            |
| `birth_date` | date    | No       | User's birth date (format: YYYY-MM-DD)                  |

**Notes:**
- All parameters are optional. If omitted, they will not be updated.
- Email and username must be unique across all users.
- Users can reuse their own current email and username when updating other fields.

---

## Request Example
```http
PUT /api/v1/auth/me
Authorization: Bearer {token}
Content-Type: application/json

{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john.doe@example.com",
  "username": "johndoe",
  "height": 180,
  "birth_date": "1990-05-15"
}
```

---

## Response

### 200 OK
Returns the updated user resource.

#### Example
```json
{
  "data": {
    "id": 1,
    "first_name": "John",
    "last_name": "Doe",
    "email": "john.doe@example.com",
    "username": "johndoe",
    "height": 180,
    "birth_date": "1990-05-15",
    "created_at": "2023-01-01T00:00:00.000000Z",
    "updated_at": "2023-01-15T10:30:00.000000Z",
    ...
  }
}
```

For a full schema, see [User Resource](../users/user_resource.md).

---

### Error Responses
| Status | Description                                  | Reference                                      |
|--------|----------------------------------------------|------------------------------------------------|
| 401    | Unauthorized (not authenticated)             | [Authentication error](../_globals/authentication-errors.md) |
| 409    | Conflict (email or username already in use)  | See below                                      |
| 422    | Validation error (invalid input)             | [Validation error](../_globals/validation-errors.md) |

#### 409 Conflict - Email Already in Use
```json
{
  "error": "This email is already in use."
}
```

#### 409 Conflict - Username Already in Use
```json
{
  "error": "This username is already in use."
}
```

#### 422 Validation Error Examples
```json
{
  "message": "The email field must be a valid email address.",
  "errors": {
    "email": ["The email field must be a valid email address."]
  }
}
```

```json
{
  "message": "The height field must be an integer.",
  "errors": {
    "height": ["The height field must be an integer."]
  }
}
```

```json
{
  "message": "The birth date field must be a valid date.",
  "errors": {
    "birth_date": ["The birth date field must be a valid date."]
  }
}
```

---

## Related Resources
- [GET /api/v1/auth/me](me.md) - Get current user information
- [User Resource](../users/user_resource.md) - User resource schema

