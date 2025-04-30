# `POST /api/v1/payments/withdrawal`
You can make a withdrawal request using this API.


## Permissions

No specific permission is required.

## Params

- `amount`: Required decimal
- `description`: Optional description for the request (maxlength: 2000)

## Response

### 201 Created
When request is created successfully.

### 400 Bad Request
Insufficient balance.

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)
