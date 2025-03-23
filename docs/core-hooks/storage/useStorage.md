---
title: useStorage
description: A custom hook to synchronize state with localStorage or sessionStorage.
---

# useStorage
`useStorage` is a custom hook to synchronize state with localStorage or sessionStorage.

## Usage
```javascript
import { useLocalStorage } from "hookify-react";

export default function Example() {
  const [name, setName] = useLocalStorage("name", "default name");

  return (
    <div>
      <p>Your name is {name}</p>
      <button onClick={() => setName("John Doe")}>Change Name</button>
    </div>
  );
}
```

## API Reference

### Parameters

| Parameter      | Type                         | Description |
|--------------|----------------------------|-------------|
| `key`       | `string`                    | The storage key used to retrieve and store data. |
| `defaultValue` | `T \| (() => T)` | The default value or a function returning the default value if no value is found in storage. |
| `storage`    | `Storage`                   | The Storage object (either `localStorage` or `sessionStorage`). |

### Return Value

| Property | Type | Description |
|----------|------|-------------|
| `[0]`    | `T`  | The current stored value. |
| `[1]`    | `Dispatch<SetStateAction<T>>` | Function to update the stored value. |

### Behavior
- Retrieves the stored value from the given `storage` (`localStorage` or `sessionStorage`).
- Parses JSON values stored in the given storage.
- If no stored value is found, it initializes with `defaultValue`.
- Automatically updates the storage when the value changes.
- If the value is `undefined`, it removes the key from storage.
