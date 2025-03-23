---
title: useLocalStorage
description: A custom hook for syncing state with `localStorage`.
---

# useLocalStorage
`useLocalStorage` is a custom hook for syncing state with `localStorage`.

## Usage
```javascript
import { useLocalStorage } from "hookify-react";

export default function UseLocalStorage() {
  const [name, setName] = useLocalStorage("name", "default name");

  return <p>Your name is {name}</p>;
}
```

## API Reference

### Parameters

| Parameter      | Type                         | Description |
|--------------|----------------------------|-------------|
| `key`       | `string`                    | The storage key used to retrieve and store data. |
| `defaultValue` | `T \| (() => T)` | The default value or a function returning the default value if no value is found in localStorage. |

### Return Value

| Property | Type | Description |
|----------|------|-------------|
| `[0]`    | `T`  | The current stored value. |
| `[1]`    | `Dispatch<SetStateAction<T>>` | Function to update the stored value. |

### Behavior
- Uses `useStorage` internally with `localStorage`.
- Stores and retrieves values from `localStorage`.
