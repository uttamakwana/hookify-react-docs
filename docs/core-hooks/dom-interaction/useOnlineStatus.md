---
title: useOnlineStatus
description: A custom hook that tracks the online/offline status of the user's network connection.
---

# useOnlineStatus
`useOnlineStatus` is a custom hook that tracks the online/offline status of the user's network connection.

## Usage

```javascript
import { useOnlineStatus } from "./useOnlineStatus";

export default function OnlineStatusExample() {
  const { onlineStatus } = useOnlineStatus();

  return (
    <div>
      {onlineStatus === "online" ? "You are online 😁" : "You are offline 😥"}
    </div>
  );
}
```

## API Reference

### Parameters

This hook does not take any parameters.

### Behavior

- Tracks the user's online/offline status using the `navigator.onLine` property.
- Listens for the `online` event to detect when the user reconnects to the internet.
- Updates the `onlineStatus` state accordingly.
- Ideal for displaying network status indicators or handling offline scenarios.

### Return Value

`useOnlineStatus` returns an object containing:

| Property      | Type               | Description                        |
|--------------|--------------------|------------------------------------|
| `onlineStatus` | `"online" | "offline"` | The current network status of the user. |