---
title: usePress
description: A custom hook to check if an element is being pressed or not.
---

# usePress
`usePress` is a custom hook to check if an element is being pressed or not.

## Usage

```javascript
import { usePress } from "./usePress";

export default function PressExample() {
  const { ref, isPressed } = usePress<HTMLButtonElement>();

  return (
    <button ref={ref} style={{ padding: "10px", fontSize: "16px" }}>
      {isPressed ? "Wow that feels good! 😁" : "Please press me! 😥"}
    </button>
  );
}
```

## API Reference 

### Behavior

- Detects whether a user is pressing down on an element.
- Uses `mousedown` and `mouseup` event listeners to update the press state.
- Works with any `HTMLElement` by attaching a `ref` to it.

### Return Value

`usePress` returns an object containing:

| Property   | Type                                 | Description |
|------------|--------------------------------------|-------------|
| `ref`      | `React.MutableRefObject<T \| null>` | A ref that should be attached to the target element. |
| `isPressed` | `boolean`                          | `true` if the element is currently being pressed, otherwise `false`. |

