# `GET /api/v1/gyms`
Using this API you can get list of the gyms and also search them using filters.


## Permissions

- `gyms.view_all`: to view all of the gyms including inactive ones as an admin. If you don't have this permission, you only get active gyms in the response

## Params

- `city_id`: specify the city (can be more than one ID separated by `,`)
- `state_id`: specify the state (can be more than one ID separated by `,`)
- `country_id`: specify the country (can be more than one ID separated by `,`)
- `gym_id`: only get one or more specific gyms (can be more than one ID separated by `,`)
- `user_id`: specify the owner of the gym (can be more than one ID separated by `,`)
- `major_id`: specify the major (can be more than one ID separated by `,`)
- `word`: search by text
- `page`: page number
- `lat` & `lng`: you can specify a location lat and lng and get the gyms sorted from the closest to that location
- `radius`: if you are using `lat` and `lng`, you can specify the radius of the results (in kilometers). default is 50km. minimum is 10 and maximum is 900,000

The gyms are sorted by the newest (if you don't specify lat and lng)

> Note: The results are firstly sorted based on marketing boosts, the `sort` logic will be applied on the second level

## Response

### 200 OK

```json
{
    "data": [
        {<gym resource>},
        {<gym resource>},
        {<gym resource>},
        {<gym resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Gym Resource](gym_resource.md)

[Pagination Data](../_globals/pagination-data.md) (per page: 30)
> NOTE: If you specify the location in the parameters, as the result is already limited to a specific radius, the pagination will be removed and all of the data will be returned in one page

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
