# `/api/v1/admin/majors`
You can get list of the majors using this endpoint.

- Method: `GET`

### Response

200:
```json
{
    "data": [
        {<major resource>},
        {<major resource>},
        {<major resource>},
        {<major resource>}
    ],
}
```

[Major Resource](../../resources/major.md)
