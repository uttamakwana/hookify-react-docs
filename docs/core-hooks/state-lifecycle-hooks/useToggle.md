---
title: useToggle
description: A custom React hook that manages a boolean state and provides a function to toggle it and make it true or false whenever needed.
---

# useToggle

`useToggle` is a custom React hook that manages a boolean state and provides a function to toggle it and make it true or false whenever needed.

## Usage

```javascript
  import { useToggle } from 'hookify-react';
 
  function UseToggle() {
    const [isToggled, toggle] = useToggle(false);
 
    return (
      <div>
        <button onClick={toggle}>Toggle</button>
        <button onClick={() => toggle(true)}>Toggle to true</button>
        <button onClick={() => toggle(false)}>Toggle to false</button>
        <p>Toggle is: {isToggled ? 'On' : 'Off'}</p>
      </div>
    );
  }
```

## API Reference

### Parameters

| Parameter      | Type    | Default | Description                              |
|--------------|--------|---------|------------------------------------------|
| `initialValue` | `boolean` | `false` | The initial state of the boolean value. |

### Return Value

`useToggle` returns a tuple with the following values:

| Index | Property    | Type                                | Description |
|-------|------------|------------------------------------|-------------|
| `0`   | `state`    | `boolean`                         | The current boolean state. |
| `1`   | `setValue` | `(value?: boolean) => void`       | A function to toggle the state or explicitly set it to `true` or `false`. |