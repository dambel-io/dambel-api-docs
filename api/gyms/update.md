# `/api/v1/gyms/{gym-id}`
Using this API you can update the information of one specific gym.

- Controller: [`App\Http\Controllers\API\V1\Gyms\UpdateGymController`](../../../src/app/Http/Controllers/API/V1/Gyms/UpdateGymController.php)
- Method: `PUT`
- [Requires Authentication](../auth/login.md#how-to-use-api-token)

### Permissions
- `gyms.update`: to update your own gym
- `gyms.update_any`: to update any gym as an admin
- `gyms.transfer_ownership`: to transfer the gym ownership

### Params

- `name`: Name of the gym (required|maxlength:255)
- `address`: Address of the gym (required|maxlength:255)
- `location_lat`: Location coord lat (float|required)
- `location_lng`: Location coord lng (float|required)
- `is_active`: optional
- `show_crowd`: optional
- `cword`: optional|numeric
- `description`: optional|maxlength:2000
- `user_id`: numeric (requires permission `gyms.transfer_ownership`)
- `city_id`: numeric
- `major_ids`: can be a list of IDs separated by `,`. If you want to detach all of the majors, you can pass `0` as the value

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

### Response

200:
```json
{
    "gym": {<gym resource>},
}
```

[Gym Resource](../resources/gym.md)

422: [Validation error](../validation-errors.md)

401: [Authentication error](../authentication-errors.md)

403: [Permission error](../permission-errors.md)
