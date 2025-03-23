---
title: useCounter
description: A custom hook for managing a counter with increment, decrement, and reset functionality.
---

# useCounter

`useCounter` is a custom React hook that provides functionality for managing a counter. It allows for incrementing, decrementing, and resetting the counter, as well as incrementing and decrementing by a specific value.

## Usage

```javascript
import { useCounter } from 'hookify-react';

export default function CounterComponent() {
  const { count, increment, decrement, reset } = useCounter(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
      <button onClick={reset}>Reset</button>
    </div>
  );
}
```

## API Reference

### Parameters

| Parameter      | Type     | Default | Description                          |
|----------------|----------|---------|--------------------------------------|
| `initialValue` | `number` | `0`     | The initial value of the counter.    |

### Return Value

`useCounter` returns an object with the following properties:

| Property           | Type       | Description                                      |
|--------------------|------------|--------------------------------------------------|
| `count`            | `number`   | The current value of the counter.                |
| `increment`        | `function` | Increments the counter by 1.                     |
| `incrementByValue` | `function` | Increments the counter by a specified value.     |
| `decrement`        | `function` | Decrements the counter by 1.                     |
| `decrementByValue` | `function` | Decrements the counter by a specified value.     |
| `reset`            | `function` | Resets the counter to its initial value.         |

## Example: Incrementing and Decrementing by a Specific Value

```javascript
import { useCounter } from 'hookify-react';

export default function CounterComponent() {
  const { count, incrementByValue, decrementByValue } = useCounter(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => incrementByValue(5)}>Increment by 5</button>
      <button onClick={() => decrementByValue(5)}>Decrement by 5</button>
    </div>
  );
}
```