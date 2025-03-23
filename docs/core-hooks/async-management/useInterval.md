---
title: useInterval
description: A custom hook to execute a callback at a specified interval.
---

# useInterval
`useInterval` is a custom hook to execute a callback at a specified interval.

## Usage

```tsx
import { useState } from "react";
import useInterval from "./useInterval";

function TimerComponent() {
  const [count, setCount] = useState(0);
  const { clear } = useInterval(() => setCount((prev) => prev + 1), 1000);

  return (
    <div>
      <p>Counter: {count}</p>
      <button onClick={clear}>Stop Timer</button>
    </div>
  );
}

export default TimerComponent;
```

## API Reference

### Parameters

| Parameter   | Type         | Default | Description |
|------------|-------------|---------|-------------|
| `callback` | `() => void` | `-`     | Function to be executed at each interval. |
| `interval` | `number`     | `1000`  | Time in milliseconds between executions. |

### Behavior

- Executes the `callback` function at the specified `interval`.
- Returns a `clear` function to stop the interval manually.
- Automatically clears the interval when the component unmounts.

### Return Value

`useInterval` returns an object with the following method:

| Property  | Type       | Description                         |
|-----------|-----------|-------------------------------------|
| `clear`   | `() => void` | Stops the interval when called. |