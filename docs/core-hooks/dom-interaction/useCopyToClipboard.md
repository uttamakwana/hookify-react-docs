---
title: useCopyToClipboard
description: A custom React hook to copy text to the clipboard with feedback.
---

# useCopyToClipboard

`useCopyToClipboard` is a custom React hook that allows users to copy text to the clipboard while providing success and error feedback. It leverages the `navigator.clipboard` API for modern and reliable text copying.

## Usage

```javascript
import { useCopyToClipboard } from "hookify-react";

export default function UseCopyToClipboardExample() {
  const { copy, isCopied, error } = useCopyToClipboard();

  return (
    <div style={{ textAlign: "center", fontFamily: "Arial, sans-serif" }}>
      <h2>useCopyToClipboard Hook Example</h2>
      <button onClick={() => copy("Hello, Clipboard!")}>
        Copy to Clipboard
      </button>
      {isCopied && <p style={{ color: "green" }}>Copied successfully!</p>}
      {error && <p style={{ color: "red" }}>Error copying: {error}</p>}
    </div>
  );
}
```

## API Reference

### Return Value

`useCopyToClipboard` returns an object with the following properties:

| Property    | Type                      | Description |
|------------|---------------------------|-------------|
| `copy`     | `(text: string) => Promise<void>` | A function to copy text to the clipboard. |
| `isCopied` | `boolean`                  | `true` if the text was copied successfully, otherwise `false`. |
| `error`    | `string \| null`           | Any error message if copying fails, otherwise `null`. |

### Behavior

- **Uses `navigator.clipboard.writeText` to copy text.**
- **Sets `isCopied` to `true` on successful copy and resets it after 2 seconds.**
- **Handles clipboard API unavailability and other errors.**
