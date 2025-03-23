---
title: useSessionStorage
description: A custom hook for syncing state with `sessionStorage`.
---

# useSessionStorage
`useSessionStorage` is a custom hook for syncing state with `sessionStorage`.

## Usage
```javascript
import { useSessionStorage } from "hookify-react";

export default function UseSessionStorage() {
  const [name, setName] = useSessionStorage("name", "default name");

  return <p>Your name is {name}</p>;
}
```

## API Reference

### Parameters

| Parameter      | Type                         | Description |
|--------------|----------------------------|-------------|
| `key`       | `string`                    | The storage key used to retrieve and store data. |
| `defaultValue` | `T \| (() => T)` | The default value or a function returning the default value if no value is found in sessionStorage. |

### Return Value

| Property | Type | Description |
|----------|------|-------------|
| `[0]`    | `T`  | The current stored value. |
| `[1]`    | `Dispatch<SetStateAction<T>>` | Function to update the stored value. |

### Behavior
- Uses `useStorage` internally with `sessionStorage`.
- Stores and retrieves values from `sessionStorage`.


