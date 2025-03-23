---
title: useArray
description: A custom React hook for managing arrays. It provides utility functions for common operations like adding, removing, updating, and resetting array elements.
---

# useArray

`useArray` is a custom React hook for managing arrays. It provides utility functions for common operations like adding, removing, updating, and resetting array elements.

## Usage

```javascript
import React from "react";
import { useArray } from "hookify-react";

type User = {
  id: number;
  name: string;
};

export default function UserList() {
  const initialUsers: User[] = [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" },
  ];

  const [users, setUsers, { push, pop, removeByIndex, updateByIndex, clear }] =
    useArray<User>(initialUsers);

  return (
    <div className="p-4 border rounded shadow-md max-w-md mx-auto">
      <h2 className="text-lg font-bold mb-2">User List</h2>

      <ul className="list-disc pl-5">
        {users.map((user, index) => (
          <li key={user.id}>
            {user.name}{" "}
            <button
              className="ml-2 text-red-500"
              onClick={() => removeByIndex(index)}
            >
              ❌
            </button>
          </li>
        ))}
      </ul>

      <div className="mt-4 space-x-2">
        <button
          className="px-3 py-1 bg-blue-500 text-white rounded"
          onClick={() =>
            push({ id: users.length + 1, name: `User ${users.length + 1}` })
          }
        >
          Add User
        </button>
        <button
          className="px-3 py-1 bg-yellow-500 text-white rounded"
          onClick={() => updateByIndex(0, { id: 1, name: "Updated Alice" })}
        >
          Update First User
        </button>
        <button
          className="px-3 py-1 bg-red-500 text-white rounded"
          onClick={() => pop()}
        >
          Remove Last User
        </button>
        <button
          className="px-3 py-1 bg-gray-500 text-white rounded"
          onClick={clear}
        >
          Clear Users
        </button>
      </div>
    </div>
  );
}
```

## API Reference

### Parameters

| Parameter      | Type     | Default      | Description                          |
|--------------|----------|--------------|--------------------------------------|
| `initialValue` | `T[]`   | `[]`         | The initial array value.            |

### Return Value

`useArray` returns a tuple containing the state, a state setter function, and an object with the following utility functions:

| Property        | Type       | Description                                      |
|----------------|-----------|--------------------------------------------------|
| `state`        | `T[]`     | The current value of the array.                 |
| `setState`     | `function` | Function to manually update the state.          |
| `push`         | `function` | Adds a value to the end of the array. Returns the new length. |
| `pop`          | `function` | Removes and returns the last element of the array. |
| `shift`        | `function` | Removes and returns the first element of the array. |
| `unshift`      | `function` | Adds a value to the beginning of the array. Returns the new length. |
| `removeByIndex` | `function` | Removes an element from the array by index. |
| `removeByValue` | `function` | Removes the first occurrence of a specified value from the array. |
| `clear`        | `function` | Clears all elements from the array. |
| `replace`      | `function` | Replaces the current array with a new array. |
| `reset`        | `function` | Resets the array to its initial value. |
| `filter`       | `function` | Filters the array based on a predicate function and updates the state. |
| `updateByIndex` | `function` | Updates the value of an element at a specific index. |
| `updateByValue` | `function` | Updates the first occurrence of a specific value with a new value. |
