# React-useContext
**useContext** hook is used to create common data that can be accessed throughout the component hierarchy without passing the props down manually to each level. Context defined will be available to all the child components without involving `props`.

React Context is a way to manage state globally. It can be used together with the `useState` Hook to share state between deeply nested components more easily than with just `useState` alone.

# Problem

- [x] State should be held by the highest parent component in the stack that requires access to the state.

To demonstrate, we have many nested components. The component at the top and bottom of the stack need access to the state.

In order to do this without Context, we will need to pass the state as **props** through each nested component. This is called **prop drilling**.

