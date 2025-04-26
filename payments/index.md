# `GET /api/v1/payments`
Users can get list of their own payments and transactions and admins can get list of all of the records in the system using this API.


## Permissions

- `payments.view_any`: To view all of the payments
- Normal users can always get list of their own records using this API

## Params

- `type`: [see available types](../resources/payment.md#type). Multiple options can be used separated by `,`
- `payable_type`: Multiple options can be used separated by `,`
- `payable_id`: Multiple options can be used separated by `,`
- `user_id`: Multiple options can be used separated by `,`
- `is_done`: True of False
- `start_date`: Start of the date range
- `end_date`: End of the date range
- `min_amount`: Minimum amount
- `max_amount`: Maximum amount
- `description`: Search in description
- `page`: Specify the page
- `sort`: `desc` or `asc` to specify newest or oldest

## Response

### 200 OK

```json
{
    "data": [
        {<payment resource>},
        {<payment resource>},
        {<payment resource>},
        {<payment resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Payment Resource](../resources/payment.md)

[Pagination Data](../pagination-data.md) (per page: 30)

### 401 Unauthorized
[Authentication error](../authentication-errors.md)
