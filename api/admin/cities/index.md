# `/api/v1/admin/cities`
You can get list of the cities by alphabetical order using this endpoint.

- Method: `GET`

### Params

- `state_id`: You can filter by country to get cities in a specific state

### Response

200:
```json
{
    "data": [
        {<city resource>},
        {<city resource>},
        {<city resource>},
        {<city resource>}
    ],
}
```

[City Resource](../../resources/city.md)
