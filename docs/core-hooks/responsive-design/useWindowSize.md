---
title: useWindowSize
description: A custom hook to track the size of the browser window in real-time.
---

# useWindowSize
`useWindowSize` is a custom hook to track the size of the browser window in real-time.

# Usage  

```javascript
import { useWindowSize } from "hookify-react";

export default function WindowSizeTracker() {
  const { width, height } = useWindowSize();

  return (
    <div style={{ padding: "20px", border: "1px solid black" }}>
      <p>Window Width: {width}px</p>
      <p>Window Height: {height}px</p>
    </div>
  );
}
```

## API Reference 

### Parameters  

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| None | - | - | This hook does not take any parameters. It tracks the size of the browser window. |

### Return Value  

| Property | Type | Description |
|----------|------|-------------|
| `width` | `number` | The current width of the browser window. |
| `height` | `number` | The current height of the browser window. |

### Behavior  

- Tracks browser window dimensions (`width`, `height`).
- Uses `useLayoutEffect` to update size on resize.
- Ensures server-side rendering (SSR) safety by initializing to `0` if `window` is undefined.

