# Notification Resource

Represents a notification sent to a user, including its type, data, read status, and timestamps.


---

## Schema
| Field      | Type   | Description                                                      |
|------------|--------|------------------------------------------------------------------|
| id         | int    | Unique identifier for the notification                           |
| type       | string | Type of the notification (see Notification Types below)          |
| data       | object | Notification-specific data payload                               |
| read_at    | string | Timestamp when the notification was read, or null if unread      |
| created_at | string | Creation timestamp (ISO 8601 format)                             |

---

## Example
```json
{
  "id": 123,
  "type": "Comments\\NewCommentNotification",
  "data": {
    "comment_id": 456,
    "content": "Great post!"
  },
  "read_at": "2025-01-01 00:00:00",
  "created_at": "2025-01-01 00:00:00"
}
```

---

## Notification Types
The `type` field represents the type of the notification. All types have the `App\Notifications\` prefix. Available types include:

- `Comments\NewCommentNotification`: Notifies users when a comment is added under their comment/commentable
- `Payments\UserPremiumSubscriptionPurchasedNotification`: Notifies users when their premium purchase is complete
- `Ratings\NewRatingNotification`: Notifies users when their ratable is rated (only the score is shown)
- `Users\RoleAssignedNotification`: Notifies users when a new permission role is assigned to their account
- `Gyms\Subscriptions\GymSubscriptionCheckInNotification`: Notifies users/gym owners when a check-in is done
- `Gyms\Subscriptions\NewGymSubscriptionNotification`: Notifies gym owners when a new subscription is purchased
- `Gyms\Subscriptions\GymSubscriptionCheckOutNotification`: Notifies users/gym owners when a check-out is done
- `Reports\NewReportNotification`: Notifies admins when a new report is created
- `Chats\NewMessageNotification`: Notifies users of new chat messages
- `Chats\YouAreAddedToChatNotification`: Notifies users when they are added to a new chat
- `Training\Trainees\NewTraineeNotification`: Notifies trainees/trainers when a trainee record is created
- `Training\Trainees\TraineeDeliveredNotification`: Notifies trainees when their record is marked as delivered
- `Training\DietPlans\DietPlanCreatedNotification`: Notifies trainees when a diet plan is created
- `Training\DietPlans\DietPlanUpdatedNotification`: Notifies trainees when a diet plan or its meals are updated
