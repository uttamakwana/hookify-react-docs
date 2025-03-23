---
title: useHover
description: A custom hook to track hover state on an element.
---

# useHover

`useHover` is a custom React hook that allows you to detect when an element is being hovered. It provides a `ref` to attach to any element and a boolean state (`isHovered`) that updates based on mouse interactions. This is useful for building interactive UI components without relying on CSS-only hover effects.

## Usage

```javascript
import { useHover } from "hookify-react";

export default function UseHover() {
  const { ref, isHovered } = useHover();

  return (
    <div
      ref={ref}
      style={{
        width: "200px",
        height: "100px",
        display: "flex",
        alignItems: "center",
        justifyContent: "center",
        background: isHovered ? "blue" : "gray",
        color: "white",
        fontSize: "18px",
        borderRadius: "8px",
        transition: "background 0.3s ease",
      }}
    >
      {isHovered ? "Hovered! 🎯" : "Hover over me!"}
    </div>
  );
}
```

## API Reference

### Return Value

`useHover` returns an object with the following properties:

| Property    | Type                                  | Description |
|-------------|---------------------------------------|-------------|
| `ref`      | `React.MutableRefObject<T \| null>`   | A ref to attach to an element for hover detection. |
| `isHovered` | `boolean`                            | `true` if the element is hovered, otherwise `false`. |

### Behavior

- **Uses `useRef` to store a reference to the target element.**
- **Attaches `mouseenter` and `mouseleave` event listeners** using `useEventListener` to track hover state.
- **Updates `isHovered` state dynamically** when the user interacts with the element.
- **Cleans up event listeners automatically** when the component unmounts.
