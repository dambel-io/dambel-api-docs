# `/api/v1/admin/states`
You can get list of the states by alphabetical order using this endpoint.

- Controller: [`App\Http\Controllers\API\V1\Admin\States\ListStateController`](../../../../src/app/Http/Controllers/API/V1/Admin/States/ListStateController.php)
- Method: `GET`

### Params

- `country_id`: You can filter by country to get states in a specific country

### Response

200:
```json
{
    "data": [
        {<state resource>},
        {<state resource>},
        {<state resource>},
        {<state resource>}
    ],
}
```

[State Resource](../../resources/state.md)
