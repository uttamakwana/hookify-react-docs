---
title: usePrevious
description: A custom React hook to store and retrieve the previous value of a given state or prop.
---

# usePrevious

`usePrevious` is a Custom React hook to store and retrieve the previous value of a given state or prop.

---

## Usage

```javascript
 import { usePrevious } from "hookify-react";
 const [count, setCount] = useState(0);
 const prevCount = usePrevious(count);

 useEffect(() => {
   console.log(`Previous count: ${prevCount}, Current count: ${count}`);
 }, [count]);

 return (
  <div>
    <button onClick={() => setCount(prev => prev + 1)}>+1</button>
    <span>Previous count value: {prevCount}</span>
  </div>
 );
```

---

## API Reference

### Parameters

| Parameter      | Type     |  Description                          |
|----------------|----------|--------------------------------------|
| `initialValue` | `generic` | The initial value of the state.    |

### Return Value

`usePrevious` returns a `previousValue` to track

---

## See Also

- [useArray](/docs/hooks/useArray)
- [useToggle](/docs/hooks/useToggle)
- [useLocalStorage](/docs/hooks/useLocalStorage)
```