# What is HOC ?

- Higher Order Component is a pattern in React that allows to reuse the component logic
- its not a new type of component, but rather a function that takes another component and returns a new component witdh additional props and behaviour.
- Think HOC as a wrapper that enhances the wrapped component by adding sgared behaviour state or logic.

# Key Pounst To Remember

1. HOC is a function that takes a component as an argument and returns the same component with more features
2. It doesnt mutate or modify the originla component it creates new one with added funcionality.

# Example

-- Simple Component

```
const Home = ({ message, userName }) => {
  return (
    <div>
      <h1>im Simple Component</h1>
      <h2>{message}</h2>
      <h2>{userName}</h2>
    </div>
  );
};

export default Home;
```

-- HOC Component that adds a message

```
import React from "react";

const HOC = (Component) => {
  return (props) => {
    const newProps = {
      message: "hello There",
    };
    return <Component {...props} {...newProps} />;
  };
};

export default HOC;
```

## Output

```
hello There
hiii
```
