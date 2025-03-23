---
title: useOnScreen
description: A custom hook to check if an element is visible within the viewport.
---

# useOnScreen
`useOnScreen` is a custom hook to check if an element is visible within the viewport.

## Usage

```javascript
import { useOnScreen } from "./useOnScreen";

export default function OnScreenExample() {
  const { ref, isVisible } = useOnScreen("100px");

  return (
    <div>
      <div style={{ height: "100vh" }}>Scroll down to see the box</div>
      <div
        ref={ref}
        style={{
          height: "200px",
          backgroundColor: isVisible ? "lightgreen" : "lightcoral",
          display: "flex",
          alignItems: "center",
          justifyContent: "center",
          fontSize: "20px",
        }}
      >
        {isVisible ? "I'm visible! 🎉" : "Not in view 👀"}
      </div>
    </div>
  );
}
```

## API Reference

### Parameters

| Parameter   | Type     | Default | Description |
|------------|---------|---------|-------------|
| rootMargin | string  | `"0px"` | Margin around the root, similar to CSS margin properties. Adjusting this can help detect elements earlier or later when scrolling. |

### Behavior

- Uses the `IntersectionObserver` API to determine whether an element is visible within the viewport.
- Updates the `isVisible` state when the element enters or exits the viewport.
- Ideal for lazy loading images, animations on scroll, or triggering events when an element comes into view.

### Return Value

`useOnScreen` returns an object containing:

| Property   | Type                                 | Description |
|------------|--------------------------------------|-------------|
| `ref`      | `React.MutableRefObject<T \| null>` | A ref that should be attached to the target element. |
| `isVisible` | `boolean`                          | `true` if the element is visible on the screen, otherwise `false`. |