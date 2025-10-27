# What is Render Props ?

- `Render Props` is a technique used to share code or logic between components by passing a function as prop.
- it allows us to share its state or code logic with other components by passing a fun as a prop.
- The receiving component calls this function with its data to decide what to render.

# How Render Prop Works ?

- A render prop is a function that a component uses to know what to render.
- Insetad of passing JSX elements directly as a children or other props.
- Parent component pass fun as a prop to child componet
- Parent component means where you use the counter thats the parent component , child component is <Counter />
- so from parent component we pass a fun as prop to the child component
- Child component <Counter /> will recieve the fun sent by parent and calls it with some data or state

# Why to use Render Props ?

- logic reusability.
- The render prop pattern is a way to make a component reusable while giving other components the flexibility to render what they need based on the shared data.

# Example

- lets create a scenario where u need to build <Counter /> component
- But the challenge is you have to render that <Counter /> component in 2 pages.
- But you have to render that <Counter /> component in 2 different UI.
- Brute force approach just copy paste the <Counter /> and make it as <Counter2 /> an change its ui.
- this idea works but its not flexible wayto do this . coz think in future you have to render that <Counter /> in 8/9 pages with diff Ui
- You cant do what you did last time
- At this time Render Props technique will help you
- Observe carefully you just needed different `UI ` not the different logic
- So we can use the same logic but with different UI
- Yes Render Props allow us to share the code/logic betwen components by passing function as prop
- Where components use that prop to render the state or data with desired UI they want.
- With this we share the logic and use them with desired UI

# Example

## Implementing Counter With Render Prop

```
import React, { useState } from "react";

const Counter = ({ render }) => {
  const [count, setCount] = useState(0);

  //   function to increment count
  const increment = () => setCount((prev) => prev + 1);
  //   function to decrement count
  const decrement = () => setCount((prev) => prev - 1);

  // The render prop receives a function to render the UI based on the count
  return render({ count, increment, decrement });
};

export default Counter;

```

# Using Counter With 2 Different UI,s but With same logic

## First UI

```
    <Counter
          render={({ count, increment, decrement }) => (
            <div
              style={{
                border: "2px solid red",
                width: "50%",
                display: "flex",
                justifyContent: "center",
                alignItems: "center",
                flexDirection: "column",
                gap: 2,
                padding: 10,
              }}
            >
              <p
                style={{
                  backgroundColor: "black",
                  color: "white",
                  padding: 10,
                }}
              >
                First UI
              </p>
              <h1 style={{ margin: 0, padding: 0 }}>{count}</h1>
              <button onClick={increment}>Increment</button>
              <button onClick={decrement}>Decrement</button>
            </div>
          )}
        />
```

## Second UI

```
    <Counter
          render={({ count, increment, decrement }) => (
            <div
              style={{
                border: "2px solid red",
                width: "50%",
                display: "flex",
                justifyContent: "center",
                alignItems: "center",
                flexDirection: "column",
                gap: 2,
                padding: 10,
              }}
            >
              <p
                style={{
                  backgroundColor: "black",
                  color: "white",
                  padding: 10,
                }}
              >
                First UI
              </p>
              <h1 style={{ margin: 0, padding: 0 }}>{count}</h1>
              <button onClick={increment}>Increment</button>
              <button onClick={decrement}>Decrement</button>
            </div>
          )}
        />
```
