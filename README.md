# React-useContext
**useContext** hook is used to create common data that can be accessed throughout the component hierarchy without passing the props down manually to each level. Context defined will be available to all the child components without involving `props`.

React Context is a way to manage state globally. It can be used together with the `useState` Hook to share state between deeply nested components more easily than with just `useState` alone.

# Problem
> State should be held by the highest parent component in the stack that requires access to the state.

To demonstrate, we have many nested components. The component at the top and bottom of the stack need access to the state.

In order to do this without Context, we will need to pass the state as **"props"** through each nested component. This is called **"prop drilling"**.

## Example: 

`Passing "props" through nested components`:

```js
import { useState } from "react";
import ReactDOM from "react-dom/client";

function Component1() {
  const [user, setUser] = useState("Dev");

  return (
    <>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </>
  );
}

function Component2({ user }) {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 user={user} />
    </>
  );
}

function Component3({ user }) {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 user={user} />
    </>
  );
}

function Component4({ user }) {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 user={user} />
    </>
  );
}

function Component5({ user }) {
  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Component1 />);
```
Even though components 2-4 did not need the state, they had to pass the state along so that it could reach component 5.

# Solution
> Create a context

To create context, you must Import `createContext` and initialize it:



