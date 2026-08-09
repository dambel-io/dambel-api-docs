# Broadcasting API

This guide explains how to connect to and listen for real-time events using Laravel Echo and Reverb.

---

## Getting Started
- Access to the Echo server running on port `9080` is required.
- A valid user [authentication token](../auth/login.md) (Bearer token) is needed for private channels.
- Use Laravel Echo or a compatible client library (e.g., Pusher JS, socket.io).

```js
import Echo from 'laravel-echo';

window.Echo = new Echo({
  broadcaster: 'reverb',
  key: 'application-key',
  host: 'ws://api.dambel.io:9080',
  authEndpoint: 'https://api.dambel.io/broadcasting/auth',
  auth: {
    headers: {
      Authorization: `Bearer YOUR_AUTH_TOKEN`
    }
  }
});
```

---

## Channels

Every chat event's payload is tabulated in [Broadcasting § Chat Events](../../broadcasting.md#chat-events).
Those tables are the complete contract — a field not listed there does not arrive.

- `private-App.Models.User.{id}`: Users receive:
  - `Illuminate\Notifications\Events\BroadcastNotificationCreated` (see [Notifications](../notifications/notification_resource.md))
  - `App\Events\Chats\ChatAdded` — `{ chat_id, user_ids, updated_at }`
  - `App\Events\Chats\ChatRemoved` — `{ chat_id, user_ids, updated_at }`
  - `App\Events\Chats\ChatUpdated` — `{ chat_id, user_ids, updated_at }`
- `private-App.Models.Chats.Chat.{id}`: Users receive chat-specific events:
  - `App\Events\Chats\MessageSent` — `{ message }`, a [Chat Message Resource](../chats/messages/chat_message_resource.md)
  - `App\Events\Chats\MessageUpdated` — `{ message }`, a [Chat Message Resource](../chats/messages/chat_message_resource.md)
  - `App\Events\Chats\MessageDeleted` — `{ message_id, chat_id }`
