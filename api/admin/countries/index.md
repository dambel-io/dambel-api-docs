# `/api/v1/admin/countries`
You can get list of the countries by alphabetical order using this endpoint.

- Method: `GET`

### Response

200:
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

[Country Resource](../../resources/country.md)
