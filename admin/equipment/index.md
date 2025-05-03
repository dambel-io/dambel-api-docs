# `GET /api/v1/admin/equipment`
You can get list of the equipment by alphabetical order using this endpoint.


## Permissions

- `equipment.view_all`: to access equipment

## Response

### 200 OK

```json
{
    "data": [
        {<equipment resource>},
        {<equipment resource>},
        {<equipment resource>},
        {<equipment resource>}
    ],
}
```

[Equipment Resource](equipment_resource.md)
