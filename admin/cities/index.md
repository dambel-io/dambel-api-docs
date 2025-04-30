# `GET /api/v1/admin/cities`
You can get list of the cities by alphabetical order using this endpoint.


## Params

- `state_id`: You can filter by country to get cities in a specific state

## Response

### 200 OK

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

[City Resource](city_resource.md)
