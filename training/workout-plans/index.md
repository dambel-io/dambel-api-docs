# `GET /api/v1/training/workout-plans`
You can get list of your own and trainee's workout plans using this API.


## Permissions

- `workout_plans.view`: To view workout plans

## Params

- `trainee_id`: to specify the trainee (can assign multiple by separating ids using `,`)
- `search`: to search based on title and description
- `page`: specify the data page
- `sort`: use `asc` to see oldest and `desc` to latest. Default is `desc`

## Response

### 200 OK

```json
{
    "data": [<workout plan resource>, ...],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Workout Plan Resource](workout_plan_resource.md)

[Pagination Data](../../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
