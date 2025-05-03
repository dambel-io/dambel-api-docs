# `GET /api/v1/admin/states`
You can get list of the states by alphabetical order using this endpoint.


## Permissions

- `states.view_all`: to access states

## Params

- `country_id`: You can filter by country to get states in a specific country

## Response

### 200 OK

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

[State Resource](state_resource.md)
