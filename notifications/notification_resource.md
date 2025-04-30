# Notification Resource


```json
{
    "id": 123,
    "type": "...",
    "data": {...},
    "read_at": "2025-01-01 00:00:00",
    "created_at": "2025-01-01 00:00:00",
}
```

## Notification Types

The `type` field represent the type of the notification and all of types have `App\Notifications\` prefix.
These are the available notification types in the system:

- `Gyms\Subscriptions\NewGymSubscriptionNotification`: Gym owner will be notified when a new subscription is purchased on their gym
