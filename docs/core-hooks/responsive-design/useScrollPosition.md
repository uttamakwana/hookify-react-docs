---
title: useScrollPosition
description: A custom hook to track scroll position, direction, and activity.
---

# useScrollPosition
`useScrollPosition` is a custom hook to track scroll position, direction, and activity.

## Usage  

```javascript
import { useScrollInfo } from "hookify-react";

export default function ScrollTracker() {
  const { ref, scrollX, scrollY, scrollDirection, isScrolling, scrollProgress } =
    useScrollInfo<HTMLDivElement>();

  return (
    <div ref={ref} style={{ height: "300px", overflowY: "scroll", border: "1px solid black" }}>
      <div style={{ height: "1000px", padding: "20px" }}>
        <p>Scroll X: {scrollX}</p>
        <p>Scroll Y: {scrollY}</p>
        <p>Scroll Direction: {scrollDirection}</p>
        <p>Is Scrolling: {isScrolling ? "Yes" : "No"}</p>
        <p>Scroll Progress: {scrollProgress.toFixed(2)}%</p>
      </div>
    </div>
  );
}
```

## API Reference  

### Parameters  

| Parameter       | Type                 | Default | Description |
|---------------|----------------------|---------|-------------|
| None         | -                      | -       | This hook does not take any parameters. It tracks scroll information for either the window or a referenced element. |

### Return Value  

| Property         | Type                     | Description |
|----------------|-------------------------|-------------|
| `ref`         | `React.MutableRefObject<T \| null>` | A ref that can be attached to an element to track its scrolling behavior. If not attached, the hook tracks the window. |
| `scrollX`     | `number`                 | The current horizontal scroll position. |
| `scrollY`     | `number`                 | The current vertical scroll position. |
| `scrollDirection` | `"up" | "down" | "left" | "right" | "none"` | The direction of the latest scroll movement. |
| `isScrolling` | `boolean`                | Whether the element is actively scrolling. |
| `scrollProgress` | `number`                | The percentage (0-100) of vertical scrolling completion. |

### Behavior  

- Tracks scroll position (`scrollX`, `scrollY`) and direction (`scrollDirection`).
- Determines if the user is actively scrolling (`isScrolling`).
- Calculates the scroll progress percentage (`scrollProgress`).
- Works for both the `window` and specific elements by attaching the provided `ref`.


