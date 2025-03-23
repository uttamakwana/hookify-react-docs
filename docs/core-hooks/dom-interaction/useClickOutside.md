---
title: useClickOutside
description: A custom React hook that listens for clicks outside of a specified element and triggers a callback function.
---

# useClickOutside
`useClickOutside` is a custom React hook that listens for clicks outside of a specified element and triggers a callback function.

## Usage

```javascript
import { useClickOutside } from "./useClickOutside";
import { useState } from "react";

export default function ClickOutsideExample() {
  const [isOpen, setIsOpen] = useState(true);
  const { ref } = useClickOutside<HTMLDivElement>(() => setIsOpen(false));

  return (
    <div>
      <button onClick={() => setIsOpen(true)}>Open Modal</button>
      {isOpen && (
        <div ref={ref} style={{ padding: "20px", border: "1px solid black", width: "200px" }}>
          Click outside of this box to close it.
        </div>
      )}
    </div>
  );
}
```

## API Reference

### Parameters

| Parameter   | Type           | Default | Description |
|------------|---------------|---------|-------------|
| `callback` | `() => void`   | `-`     | Function to be executed when a click occurs outside the element. |

### Behavior

- Detects clicks or touches outside the referenced element.
- Executes the provided `callback` function when an outside click is detected.
- Uses event listeners for `"mousedown"` and `"touchstart"` on the document body.
- Ideal for closing modals, dropdowns, or any UI component that requires outside click detection.

### Return Value

`useClickOutside` returns an object containing:

| Property | Type                          | Description                         |
|----------|------------------------------|-------------------------------------|
| `ref`    | `React.MutableRefObject<T>`  | A ref that should be attached to the target element. |
