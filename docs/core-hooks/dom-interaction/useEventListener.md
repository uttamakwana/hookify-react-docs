---
title: useEventListener  
description: A custom React hook for efficiently adding event listeners to elements.  
---

# useEventListener

`useEventListener` is a custom React hook that allows you to efficiently add event listeners to elements. It ensures that the event handler remains stable across renders by utilizing `useRef`.

## Usage

```javascript
import { useRef, useState } from "react";
import { useEventListener } from "hookify-react";

export default function UseEventListener() {
  const buttonRef = useRef(null);
  const [message, setMessage] = useState("Click the button to see magic!");

  useEventListener("click", () => {
    setMessage("Button clicked! Event listener is working 🎉");
  }, buttonRef);

  useEventListener("keydown", (event) => {
    if (event.key === "Enter") {
      setMessage("You pressed the Enter key ⌨️");
    }
  });

  return (
    <div>
      <p>{message}</p>
      <button ref={buttonRef}>Click Me</button>
      <p>Try pressing "Enter" on your keyboard!</p>
    </div>
  );
}

```

### API Reference  

## API Reference

### Parameters

| Parameter    | Type                                     | Description |
|-------------|------------------------------------------|-------------|
| `eventType` | `keyof WindowEventMap`                  | The type of event to listen for (e.g., `"click"`, `"keydown"`). |
| `callback`  | `(event: WindowEventMap[K]) => void`    | The function to execute when the event fires. |
| `elementRef` | `RefObject<HTMLElement \| Window \| Document>` _(optional)_ | A React ref pointing to the target element (defaults to `window`). |
| `options`   | `boolean \| AddEventListenerOptions` _(optional)_ | Additional options for `addEventListener`. |

### Behavior

- **Automatically cleans up event listeners on unmount.**
- **Uses `useRef` to keep a stable reference to the callback function, preventing unnecessary re-registrations.**
- **Defaults to adding the event listener on the `window` object if no `elementRef` is provided.**
