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

- `Comments\NewCommentNotification`: Users will be notified when a comment is added under their comment/commentable
- `Payments\UserPremiumSubscriptionPurchasedNotification`: User will be notified when their premium purchase is done and active
- `Ratings\NewRatingNotification`: Users will be notified when their ratable is rated. They cannot see name of the user who rated, they will only see the score
- `Users\RoleAssignedNotification`: User will be notified when a new permission role is assigned to their account by another admin
- `Gyms\Subscriptions\GymSubscriptionCheckInNotification`: User/Gym owner will be notified when a checkin is done by Gym owner/User on their subscription
- `Gyms\Subscriptions\NewGymSubscriptionNotification`: Gym owner will be notified when a new subscription is purchased on their gym
- `Gyms\Subscriptions\GymSubscriptionCheckOutNotification`: User/Gym owner will be notified when a checkout is done by Gym owner/User on their subscription
- `Reports\NewReportNotification`: Report related admins will receive this notification when a new report is created and needs their review
- `Chats/NewMessageNotification`: User will be notified when they have a new message in the chat
- `Chats/YouAreAddedToChatNotification`: User will be notified when they are added to a new chat
- `Training\Trainees\NewTraineeNotification`: Trainee/Trainer will receive a notification if the trainee record is created from the opposite side or by admin (they both get notified then)
- `Training\Trainees\TraineeDeliveredNotification`: Trainee will receive this notification once trainer changes the status of the trainne record to delivered
