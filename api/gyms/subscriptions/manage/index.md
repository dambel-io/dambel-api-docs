# `GET /api/v1/gyms/{gym-id}/subscriptions/manage`
You can get list of subscriptions on a gym using this API.


### Permissions

- `gym_subscriptions.view`: view subscriptions of your own gyms
- `gym_subscriptions.view_any`: view subscriptions of any gym

### Params

- `page`: Page number
- `user_id`: specify the user (can be more than one ID separated by `,`)
- `gym_plan_id`: specify the plan (can be more than one ID separated by `,`)
- `expires_at_from`: filter to get subscriptions that expire after the specified date
- `expires_at_to`: filter to get subscriptions that expire before the specified date

### Response

200:
```json
{
    "data": [
        {<gym subscription resource>},
        {<gym subscription resource>},
        {<gym subscription resource>},
        {<gym subscription resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Gym Subscription Resource](../../../resources/gym_subscription.md)

404: Invalid gym id or gym plan id passed

401: [Authentication error](../../../authentication-errors.md)

403: [Permission error](../../../permission-errors.md)
