# Notification Resource

Represents a notification sent to a user, including its type, data, read status, and timestamps.


---

## Schema
| Field      | Type   | Description                                                      |
|------------|--------|------------------------------------------------------------------|
| id         | int    | Unique identifier for the notification                           |
| type       | string | Type of the notification (see Notification Types below)          |
| data       | object | Notification-specific data payload. Always includes a `__text` field with a user-friendly message. |
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
    "content": "Great post!",
    "__text": "A new comment was posted by user #42: \"Great post!\""
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
- `Training\WorkoutPlans\WorkoutPlanUpdatedNotification`: Notifies trainees when a workout plan is updated by the trainer
- `Training\WorkoutPlans\WorkoutPlanCreatedNotification`: Notifies trainees when a workout plan is created by the trainer
- `Users\ReferralScoreIncreased`: Notifies users when their referral score is increased
- `Users\ReferralRewardReceived`: Notifies users when they receive a referral reward

---

## Data Field and `__text` Usage

Each notification's `data` object contains notification-specific fields, as well as a `__text` field. The `__text` field provides a ready-to-display, human-readable summary of the notification. **Client applications should use the `__text` field as the default message to show to users.**

- The `__text` value is always present and is consistent with the notification's type and context.
- Other fields in `data` provide structured information for advanced or custom UI needs.
- For most use cases, displaying `data.__text` is sufficient for a clear, user-friendly notification experience.

### Example Usage

```js
// Example: Displaying notification in a client app
const notification = /* fetched notification object */;
const message = notification.data.__text;
showNotification(message); // Display to user
```
