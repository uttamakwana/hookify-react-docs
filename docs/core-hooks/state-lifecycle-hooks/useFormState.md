---
title: useFormState
description: Custom hook to manage form state with validation and error tracking
---

# useFormState

`useFormState` is a Custom hook to manage form state with validation and error tracking

--- 
## Usage

```javascript
import React from "react";
import { useFormState } from "./useFormState";

export default function ExampleForm() {
  // Define validation rules
  const namePredicates = [
    (name: string) => (name.trim().length < 3 ? "Name must be at least 3 characters" : undefined),
    (name: string) => (name.includes("badword") ? "Name contains forbidden words" : undefined),
  ];

  const [name, setName, { errors, isValid, status }] = useFormState("", namePredicates);

  return (
    <div style={{ maxWidth: "400px", margin: "auto", fontFamily: "Arial, sans-serif" }}>
      <h2>Sign Up</h2>
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Enter your name"
        style={{
          width: "100%",
          padding: "8px",
          border: "1px solid #ccc",
          borderRadius: "4px",
          marginBottom: "8px",
        }}
      />
      {errors.length > 0 && (
        <ul style={{ color: "red", padding: 0, listStyle: "none" }}>
          {errors.map((error, index) => (
            <li key={index}>{error}</li>
          ))}
        </ul>
      )}
      <p>Status: <strong>{status}</strong></p>
      <p>Form is {isValid ? "✅ Valid" : "❌ Invalid"}</p>
    </div>
  );
}
```

## API Reference

### Parameters

| Parameter       | Type                                           | Default | Description |
|----------------|----------------------------------------------|---------|-------------|
| `defaultValue` | `T \| () => T`                               | -       | The initial state value or a function returning the initial value. |
| `predicates`   | `Array<(value: T) => string \| undefined>`   | `[]`    | An array of validation functions that return an error message or `undefined`. |
| `options`      | `{ emptyInputValidation?: boolean }`         | `{ emptyInputValidation: true }` | Optional configuration options. |

### Return Value

`useFormState` returns a tuple containing the following values:

| Index | Property  | Type                                        | Description |
|-------|----------|--------------------------------------------|-------------|
| `0`   | `value`  | `T`                                        | The current value of the form state. |
| `1`   | `setValue` | `(value: T \| ((prev: T) => T)) => void` | A function to update the state. Supports both direct values and updater functions. |
| `2`   | `metadata` | `{ errors: string[]; isValid: boolean; status: "idle" \| "valid" \| "error" }` | An object containing validation errors, validity status, and form status. |

### Validation Status

| Status  | Description |
|---------|-------------|
| `"idle"`  | No changes from the initial value. |
| `"valid"` | The input is valid and has passed all validation rules. |
| `"error"` | The input has validation errors. |

---