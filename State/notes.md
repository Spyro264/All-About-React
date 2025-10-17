# What is State ?

- State is an object that stores data or information about the components current situation.
- React components re-render when ever th state updates helps the UI to update accordingly.

# State Initialization

- State is initialized when a component is created and can be updated throughout the lifecycle of the component. It can be set to any value, such as a number, string, boolean, array, or even an object.

```
// Example with different types of state
const [count, setCount] = useState(0);          // Number
const [name, setName] = useState('John');       // String
const [isVisible, setIsVisible] = useState(true); // Boolean
const [items, setItems] = useState([]);         // Array
const [user, setUser] = useState({ name: 'Alice', age: 30 }); // Object

```

# Setting Up State in Class Components

```
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    // Initializing state
    this.state = { count: 0 };
  }

  increment = () => {
    // Updating state
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}

export default Counter;

```

# State in Functional Components (Using Hooks)

```
import React, { useState } from 'react';

function Counter() {
  // Declare state variable and updater function
  const [count, setCount] = useState(0);

  const increment = () => {
    // Updating state
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

export default Counter;

```

# State is Asynchronous

- State updates in React are asynchronous. React batches state updates for performance reasons. So, you cannot immediately access the updated state right after calling the setter function.
- To solve this, if the updated state depends on the previous state, you can use a functional update: setCount(prevCount => prevCount + 1);

```
const [count, setCount] = useState(0);

const increment = () => {
  setCount(count + 1);  // This won't immediately reflect in the next line
  console.log(count);  // This will log the old value, not the updated one
};

```

# Lifecycle of State

- Initialization: State is initialized when a component is created.
- Update: The state is updated when an event or user interaction happens.
- Re-render: The component is re-rendered to reflect the updated state.
