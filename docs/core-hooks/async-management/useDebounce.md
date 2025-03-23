---
title: useDebounce
description: A Custom hook that delays the execution of a callback function until after a specified delay has elapsed since the last change in dependencies.
---

# useDebounce
`useDebounce` is a custom hook that delays the execution of a callback function until after a specified delay has elapsed since the last change in dependencies.

## Usage

```javascript
import { useState } from "react";
import useDebounce from "./useDebounce";

function SearchComponent() {
  const [query, setQuery] = useState("");

  useDebounce(() => {
    console.log("Searching for:", query);
  }, 500, [query]);

  return (
    <input
      type="text"
      placeholder="Search..."
      value={query}
      onChange={(e) => setQuery(e.target.value)}
    />
  );
}

export default SearchComponent;
```

## API Reference - useDebounce

### Parameters

| Parameter   | Type         | Default | Description |
|------------|-------------|---------|-------------|
| `callback` | `() => void` | `-`     | Function to be executed after the debounce delay. |
| `delay`    | `number`     | `-`     | Delay in milliseconds before executing the callback. |
| `deps`     | `unknown[]`  | `[]`    | Array of dependencies that trigger the debounce effect. |

### Behavior

- Resets the debounce timer whenever dependencies in `deps` change.
- Calls `clear` to remove the timeout when the component unmounts.
- Ideal for search inputs, API calls, and other performance-sensitive scenarios.