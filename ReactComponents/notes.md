# Whar are Components ?

- Components are building blocks of react application .
- They allow you to break down the ui into smaller , reusable peices.
- Components can neither be functional or class-based components

# Types of Components in React

1. Functional components
2. Class-based components

# Functional Components

- These are simple javascript functions which returns JSX to describe hwat ui should look like.
- Stateless in nature but with the introduction of React hooks (useState, useEffect, etc.), they can now manage state and side effects as well.
- Preferred for most modern React development due to simplicity and better performance.

```
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

```

# Class Components

- These are ES6 class-based components that extend React.Component.
- They have methods like render() and can hold state and lifecycle methods (e.g., componentDidMount, componentDidUpdate).
- While still supported, class components are less commonly used today in favor of functional components.

```
class Greeting extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

```
