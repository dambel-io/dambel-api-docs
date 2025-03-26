# `/api/v1/users/{user-id}/championships/{championship-id}`
You can delete a championship from a user using this API.

- Controller: [`App\Http\Controllers\API\V1\Users\Championships\DeleteChampionshipController`](../../../../src/app/Http/Controllers/API/V1/Users\Championships\DeleteChampionshipController.php)
- Method: `DELETE`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `championships.delete`: deleting your own championships
- `championships.delete_any`: deleting championship from any user

### Params

No parameter.

### Response

204: No content when championship gets deleted

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
