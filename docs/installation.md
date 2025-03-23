---
sidebar_position: 2
id: installation
title: Installation
---

# Installation

Install **hookfy-react** using

### npm

```sh
npm i hookify-react
```
or

### yarn

```sh
yarn i hookify-react
```

or 

### pnpm

```sh
pnpm i hookify-react
```

### Peer Dependencies
Since hookify-react is built for React, ensure you have React 18+ installed in your project:

```javascript
"dependencies": {
  "react": "^18.0.0",
  "react-dom": "^18.0.0"
}
```

If you don’t have React installed, add it using:

```sh
npm i react react-dom
```

## Usage

### 🚀 Getting Started with hookify-react

Once you’ve installed hookify-react, you can start using the hooks immediately. Below is a basic example to help you get started quickly.

#### ✨ Example: Using `useToggle`

The `useToggle` hook helps you easily manage boolean state, such as toggling UI elements.

```typescript
import { useToggle } from 'hookify-react';

function UseToggle() {
  const [isToggled, toggle] = useToggle(false);

  return (
    <div>
      <button onClick={toggle}>Toggle</button>
      <button onClick={() => toggle(true)}>Toggle to true</button>
      <button onClick={() => toggle(false)}>Toggle to false</button>
      <p>Toggle is: {isToggled ? 'On' : 'Off'}</p>
    </div>
  );
}
```
