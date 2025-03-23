---
title: useTimeout
description: A custom hook for managing a timeout.
---

# useTimeout
`useTimeout` is a custom hook for managing a timeout.

## Usage

```javascript
import { useState } from "react";
import useTimeout from "./useTimeout";

function TimeoutComponent() {
  const [message, setMessage] = useState("Waiting...");
  const { set, clear, reset } = useTimeout(() => {
    setMessage("Timeout executed!");
  }, 2000);

  return (
    <div>
      <p>{message}</p>
      <button onClick={set}>Start Timeout</button>
      <button onClick={clear}>Clear Timeout</button>
      <button onClick={reset}>Reset Timeout</button>
    </div>
  );
}

export default TimeoutComponent;
```

# API Reference

## Parameters

| Parameter   | Type         | Default | Description |
|------------|-------------|---------|-------------|
| `callback` | `() => void` | `-`     | Function to be executed when the timeout completes. |
| `delay`    | `number`     | `-`     | Delay in milliseconds before executing the callback. |

## Behavior

- Executes the `callback` function after the specified `delay`.
- Provides functions to manually start, clear, or reset the timeout.
- Automatically clears the timeout when the component unmounts.
- The `callback` function reference is updated whenever it changes.

## Return Value

`useTimeout` returns an object with the following methods:

| Property  | Type           | Description                         |
|-----------|---------------|-------------------------------------|
| `set`     | `() => void`   | Starts the timeout.                |
| `clear`   | `() => void`   | Clears the timeout before execution. |
| `reset`   | `() => void`   | Resets the timeout by clearing and starting a new one. |
