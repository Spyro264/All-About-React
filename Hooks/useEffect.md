# What is useEffect() ?

- useEffect is a powerfull react hook which is used to perform side effects in functional components.
- A side Effect refers to any operation that effects something outside the scope or component
- Essentially it is an operation that intercats with external world.
- A side effect could be things like
  1. Fetching data from an Api.
  2. setting up subscriptions or timers
  3. Running cleanup functions when the component unmounts.

# Syntax

```
useEffect(() => {
  // Code that runs after render
}, [dependencies]);
```

- The first argument is the function that contains the code for the side effect.
- The second argument is the optional array of dependencies. the effect will run f the dependencies change.

# Key points

1. Effect Runs After Render : useEffect runs after the component redners. This ensures that any changes caused by the side effect don't block the initial render.
2. Dependency Array : if you pass an empty array `[]` effect will run only once after the initial render . similar to `componentDidMount` in class components.
3. if we pass dependencies in the array the effect will run when ever the dependencues change.
4. Cleanup Function : You can return a cleanup function from useEffect. This function is called when the component unmounts or when the dependencies change before running the effect again. This is useful for cleaning up subscriptions or timers.

## Note

1. Subscription means : If your component subscribes to external data (like a WebSocket or a global state service), it’s a side effect because it’s establishing an external dependency that doesn’t directly relate to rendering.
2. Subscribing to a service or API that updates the component when new data is available.
