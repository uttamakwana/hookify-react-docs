---
title: useHistory
description: Custom hook to manage state with history tracking, supporting undo/redo functionality.
---

# useHistory

`useHistory` is a custom hook to manage state with history tracking, supporting undo/redo functionality.

## Usage

```javascript
import { useHistory } from "hookify-react";

export default function UseHistoryExample() {
  const [value, setValue, { history, pointer, back, forward, go }] = useHistory(0, { capacity: 5 });

  return (
    <div style={{ textAlign: "center", fontFamily: "Arial, sans-serif" }}>
      <h2>useHistory Hook Example</h2>
      <p>Current Value: <strong>{value}</strong></p>
      <button onClick={() => setValue(prev => prev + 1)}>Increment</button>
      <button onClick={() => setValue(prev => prev - 1)}>Decrement</button>
      <button onClick={() => setValue(0)}>Reset</button>
      <hr />
      <button onClick={back} disabled={pointer === 0}>Undo</button>
      <button onClick={forward} disabled={pointer === history.length - 1}>Redo</button>
      <button onClick={() => go(0)} disabled={pointer === 0}>Go to Start</button>
      <p>History: {JSON.stringify(history)}</p>
      <p>Pointer: {pointer}</p>
    </div>
  );
}
```

## API Reference

### Parameters

| Parameter      | Type                   | Default | Description                              |
|--------------|----------------------|---------|------------------------------------------|
| `defaultValue` | `T | (() => T)`       | —       | The initial state value or a function returning the initial value. |
| `options`     | `TUseHistoryOptions` | `{ capacity: 10 }` | Configuration options for history tracking. |
| `options.capacity` | `number` | `10` | The maximum number of history states to keep. |

### Return Value

`useHistory` returns a tuple with the following values:

| Index | Property    | Type                                      | Description |
|-------|------------|------------------------------------------|-------------|
| `0`   | `state`    | `T`                                      | The current state value. |
| `1`   | `set`      | `(value: T | ((prev: T) => T)) => void` | A function to update the state and track history. |
| `2`   | `historyObj` | `{ history: T[], pointer: number, back: () => void, forward: () => void, go: (index: number) => void }` | An object containing history management utilities. |