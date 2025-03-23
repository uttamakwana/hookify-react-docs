---
title: useAdvancedEffect
description: A custom React hook that enhances `useEffect` with advanced dependency comparison.
---

# useAdvancedEffect

`useAdvancedEffect` is a custom React hook that enhances `useEffect` with advanced dependency comparison.

## Usage Example

```javascript
import { useState } from "react";
import { useAdvancedEffect } from "hookify-react";

export default function UseAdvancedEffectExample() {
  const [count, setCount] = useState(0);
  const [otherState, setOtherState] = useState(false);

  useAdvancedEffect(() => {
    console.log("Effect triggered:", count);
  }, [count]);

  return (
    <div style={{ textAlign: "center", fontFamily: "Arial, sans-serif" }}>
      <h2>useAdvancedEffect Hook Example</h2>
      <p>Count: <strong>{count}</strong></p>
      <button onClick={() => setCount(prev => prev + 1)}>Increment</button>
      <button onClick={() => setOtherState(prev => !prev)}>
        Toggle Other State
      </button>
      <p>Check the console for effect triggers.</p>
    </div>
  );
}
```

## API Reference

### Parameters

| Parameter      | Type               | Default | Description |
|--------------|----------------|---------|-------------|
| `effect`   | `EffectCallback`  | —       | The effect function to execute when dependencies change. |
| `deps`     | `DependencyList`  | —       | The array of dependencies that determine when the effect runs. |

### Return Value

`useAdvancedEffect` does not return anything (`void`).

### Behavior

- **Skips execution on the initial render.**
- **Runs only when dependencies change between renders.**
- **Prevents unnecessary re-executions when dependencies remain unchanged.**