# Broadcasting API

This guide helps frontend developers connect to and listen for real-time events using Laravel Echo and Reverb.

## Get Started

You need:
- Access to Echo server that runs on port `9080`.
- A valid user [authentication token](../auth/login.md) (Bearer token) for private channels.
- Laravel Echo or a similar client library (e.g., Pusher JS, socket.io).

```js
import Echo from 'laravel-echo';

window.Echo = new Echo({
    broadcaster: 'reverb',
    key: 'your-key',
    host: 'ws://dambel.io:9080',
    authEndpoint: '/broadcasting/auth',
    auth: {
        headers: {
            Authorization: `Bearer YOUR_AUTH_TOKEN`
        }
    }
});
```

## Channels

- `private-App.Models.User.{id}`: Users will receive:
    - [Notifications](../notifications/notification_resource.md)
    - `ChatAdded`
    - `ChatRemoved`
    - `ChatUpdated`
- `private-App.Models.Chats.Chat.{id}`: Users will changes on a specific chat using this channel:
    - `MessageSent`
    - `MessageUpdated`
    - `MessageDeleted`
