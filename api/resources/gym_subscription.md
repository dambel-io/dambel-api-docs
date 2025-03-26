# Gym Subscription Resource

- [`App\Http\Resources\V1\GymSubscriptionResource`](../../../src/app/Http/Resources/V1/GymSubscriptionResource.php)

```json
{
    "id": 123,
    "user_id": 123,
    "gym_plan": <gym plan resource>,
    "expires_at": "2025-01-01",
    "available_sessions_count": 16,
    "checkins": [<gym subscription checkin resource>, ...]
}
```

[Gym Plan Resource](gym_plan.md)

[Gym Subscription Checkin Resource](gym_subscription_checkin.md)
