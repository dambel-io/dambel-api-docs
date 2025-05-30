# `GET /api/v1/training/trainees`
You can list and search trainees using this API.


## Permissions

- `trainees.view`: To view your own trainers and trainees
- `trainees.view_any`: To view all the trainee records in the system as an admin

## Params

- `user_id`: to specify the trainee user (can assign multiple by separating ids using `,`)
- `trainer_id`: to specify the trainer user (can assign multiple by separating ids using `,`)
- `training_service_id`: to specify the training service (can assign multiple by separating ids using `,`)
- `is_delivered`: A boolean to filter only delivered/not delivered records
- `page`: specify the data page
- `sort`: use `asc` to see oldest and `desc` to latest. Default is `desc`

## Response

### 200 OK

```json
{
    "data": [<trainee resource>, ...],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Trainee Resource](trainee_resource.md)

[Pagination Data](../../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
