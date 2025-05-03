# `GET /api/v1/admin/countries`
You can get list of the countries by alphabetical order using this endpoint.


## Permissions

- `countries.view_all`: to access countries

## Response

### 200 OK

```json
{
    "data": [
        {<country resource>},
        {<country resource>},
        {<country resource>},
        {<country resource>}
    ],
}
```

[Country Resource](country_resource.md)
