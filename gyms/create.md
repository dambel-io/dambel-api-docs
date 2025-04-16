# `POST /api/v1/gyms`
This API creates a new gym (can be used by both user to create their own gym and also admin to create gyms for others)


## Permissions
- `gyms.create`: to create your own gym
- `gyms.create_any`: to create gym for another user as an admin

## Params

- `name`: Name of the gym (required|maxlength:255)
- `address`: Address of the gym (required|maxlength:255)
- `location_lat`: Location coord lat (float|required)
- `location_lng`: Location coord lng (float|required)
- `is_active`: optional
- `show_crowd`: optional
- `description`: optional|maxlength:2000
- `user_id`: optional|numeric (requires permission `gyms.create_any`)
- `city_id`: numeric
- `major_ids`: can be a list of IDs separated by `,`. If you want to detach all of the majors, you can pass `0` as the value

## Response

### 201 Created
:
```json
{
    "gym": {<gym resource>},
}
```

[Gym Resource](../resources/gym.md)

### 422 Unprocessable Entity
[Validation error](../validation-errors.md)

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)
