# `/api/v1/users/{user-id}/championships/{championship-id}`
You can update a championship using this API.

- Controller: [`App\Http\Controllers\API\V1\Users\Championships\UpdateChampionshipController`](../../../../src/app/Http/Controllers/API/V1/Users\Championships\UpdateChampionshipController.php)
- Method: `PUT`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `championships.update`: update your own championships
- `championships.update_any`: update championships for any user

### Params

- `title`: Title of the championship (maxlength 255)
- `description`: An optional description for the championship (maxlength 2000)
- `date`: Date of the championship (required date format)

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

### Response

200:
```json
<championship resource>
```

[Championship Resource](../../resources/championship.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
