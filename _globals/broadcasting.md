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

- `private-App.Models.User.{id}`: Users receive:
  - `Illuminate\Notifications\Events\BroadcastNotificationCreated` (see [Notifications](../notifications/notification_resource.md))
  - `App\Events\Chats\ChatAdded`
  - `App\Events\Chats\ChatRemoved`
  - `App\Events\Chats\ChatUpdated`
- `private-App.Models.Chats.Chat.{id}`: Users receive chat-specific events:
  - `App\Events\Chats\MessageSent`
  - `App\Events\Chats\MessageUpdated`
  - `App\Events\Chats\MessageDeleted`
