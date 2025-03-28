# `GET /api/v1/users/{user-id}/championships`
You can get list of the championships of a user using this API.


### Params

No parameter.

### Response

200:
```json
{
    "data": [<championship resource>, ...],
}
```

[Championship Resource](../../resources/championship.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
