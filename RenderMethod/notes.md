# What is render() ?

- `render()` method is used to render react elements into the actual `DOM`.
- The main purpose of the render() is to retrun ui structure.

- The render() method must return a React element (or null if nothing should be rendered).
- React automatically calls the render() method whenever the component's state or props change. This ensures that the UI stays up-to-date with the latest state.

# render() is a pure funtion

- React’s `render()` method is a `pure function`. This means it only returns JSX (UI) based on the `props` and `state` of the component. It doesn’t change any variables outside of itself or trigger any external actions.

# render() in class components

```
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    return (
      <div>
        <h1>Hello, World!</h1>
      </div>
    );
  }
}

export default MyComponent;

```

# render() with JSX

```
render() {
  return <div>Hello</div>;
}

```
