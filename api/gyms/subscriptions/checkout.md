# `/api/v1/gyms/{gym-id}/subscriptions/checkout/{subscription-id}`
User or gym owner can checkout the last opened checkin on a subscription.

- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Response

200:
```json
{
    "message": "Checked out successfully"
}
```

404: if gym or gym subscription ID is wrong or is inactive

400: if there is no open checkin to be checked out

403: attempting to checkout on a subscription that user has not permission to or gym is inactive ([Permission error](../../permission-errors.md))

401: [Authentication error](../../authentication-errors.md)
