# `/api/v1/gyms/{gym-id}/plans`
You can get list of the subscription plans of a gym using this API.

- Controller: [`App\Http\Controllers\API\V1\Gyms\Plans\ListGymPlanController`](../../../../src/app/Http/Controllers/API/V1/Gyms/Plans/ListGymPlanController.php)
- Method: `GET`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `gyms.view_any`: is needed if you are trying to read list of plans for an inactive gym or seeing inactive plans

### Params

No parameter.

### Response

200:
```json
{
    "data": [<gym plan resource>, ...],
}
```

[Gym Plan Resource](../../resources/gym_plan.md)
