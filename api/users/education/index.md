# `GET /api/v1/users/{user-id}/education`
You can get list of the education of a user using this API.


### Params

No parameter.

### Response

200:
```json
{
    "data": [<education resource>, ...],
}
```

[Education Resource](../../resources/education.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
