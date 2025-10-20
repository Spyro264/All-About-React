# React Component Life Cycle

- In React, Components have lifecycle that consists of different phases
- Each phase has a set of lifecycle methods that are called at specific points in the component lifecycle.
- These methods allow you to control the components behaviour and perform specificactions at different stages of its lifecycle.

# A Components lifecycle has three main phases

1. Mounting phase
2. Updating phase
3. Unmounting Phase

- Mounting phase begins when an component is first created and inserted into the `DOM`.
- Updating phase occurs when a components state or props changes.
- Unmounting phase occurs when an component is removed from the `DOM`.

# Mounting Phase

- Mounting phase begins when an component is first created and inserted into the `DOM`.
- During this phase several lifecycle methods are invoked by react to enable the developer to configure the component.
- The mounting phase has four main lifecycle methods that are called in order:

1. constructor()
2. getDerivedStateFromProps()
3. render()
4. componentDidMount()

# Constructor()

- the constructor() method is called once the component is first created
- It use it to initialize the component's state and bind methods to the component's instance.
-

## Example

```
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(prevState => ({
      count: prevState.count + 1
    }));
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.handleClick}>Increment</button>
      </div>
    );
  }
}

export default Counter;
```

- In this example, the constructor() method sets the initial state of the component to an object with a count property set to 0, and binds the handleClick method to the component's instance. The handleClick method increments the count state property when the button is clicked.

# render()

- render() is responsible for generating the components virtual Dom representation based on its current state and props.
- It is called every time whene ever the components needs to be re-rendered . either coz props or state chnages or parent component has been re-rendered.

## Example

```
render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.handleClick}>Increment</button>
      </div>
    );
  }
}
```

- The `render` method displays the current count value and a button. When the button is clicked, the handleClick method is invoked. This triggers a state update, causing a re-render, and the updated count is displayed.

# getDerviedStateFromProps()

- getDerivedStateFromProps() is a lifecycle method available in React 16.3 and later versions .
- getDerivedStateFromProps() is invoked during the mounting and updating phase of a component.
- During the mounting phase, getDerivedStateFromProps() is called after the constructor and before render().
- This method is called for every render cycle and provides an opportunity to update the component's state based on changes in props before the initial render.

# The signature of getDerivedStateFromProps() is as follows:

```
static getDerivedStateFromProps(props, state)
```

- it takes 2 parameters.
- `props` and `state`.
- The method should return an object that represents the updated state of the component, or null if no state update is necessary.
- It's important to note that getDerivedStateFromProps() is a static method, which means it does not have access to the this keyword and cannot interact with the component's instance methods or properties.

# Component DIdMount()

- The componentDidMount() method is called once the component has been mounted into the DOM.
- It is typically used to set up any necessary event listeners or timers, perform any necessary API calls or data fetching, and perform other initialization tasks that require access to the browser's DOM API.

## Example

```
import React from 'react';
import ReactDOM from 'react-dom';
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritefood: "rice"};
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({favoritefood: "pizza"})
    }, 1000)
  }
  render() {
    return (
      <h1>My Favorite Food is {this.state.favoritefood}</h1>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

# Updating Phase

- This phase occurs when a component's props or state changes, and the component needs to be updated in the DOM.
- This phase has 4 lifecycle methods

1. shouldComponentUpdate()
2. componentWillUpdate()
3. componentDidUpdate()
4. getSnapshotBeforeUpdate

# shouldComponentUpdate()

- The shouldComponentUpdate() method is called before a component is updated.
- It takes two arguments: nextProps and nextState
- This method returns a boolean value that determines whether the component should update or not.
- If this method returns true, the component will update, and if it returns false, the component will not update.

## Example

```
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class Header extends Component {
  constructor(props) {
    super(props);
    this.state = { favoriteFood: 'rice' };
  }

  shouldComponentUpdate(nextProps, nextState) {
    // Only re-render if the favoriteFood state has changed
    return this.state.favoriteFood !== nextState.favoriteFood;
  }

  changeFood = () => {
    this.setState({ favoriteFood: 'Pizza' });
  }

  render() {
    return (
      <div>
        <h1>My Favorite Food is {this.state.favoriteFood}</h1>
        <button type="button" onClick={this.changeFood}>Change food</button>
      </div>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```

# componentWillUpdate()

- componentWillUpdate() method will gets called just before the component update cycle starts.
- It receives the next prop and state as arguments and allows you to perform any necessary actions before the component updates.
- But this method is not recommended for updating the state, as it can cause an infinite loop of rendering.
- It is primarily used for tasks such as making API calls, updating the DOM, or preparing the component to receive new data.
- componentWillUpdate() is often used in conjunction with componentDidUpdate() to handle component updates.

## Example

```
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class MyComponent extends Component {
  state = {
    count: 0,
  };

  handleClick = () => {
    this.setState({ count: this.state.count + 1 });
  };

  componentWillUpdate(nextProps, nextState) {
    if (nextState.count !== this.state.count) {
      console.log(`Count is about to update from ${this.state.count} to ${nextState.count}.`);
    }
  }

  render() {
    return (
      <div>
        <h1>Count: {this.state.count}</h1>
        <button type="button" onClick={this.handleClick}>
          Increment
        </button>
      </div>
    );
  }
}

const rootElement = document.getElementById('root');
```

-In this example, the componentWillUpdate method is called whenever the component is about to update. In this method, we can access the nextProps and nextState arguments to check if there are any changes to the component's state or props. If there are changes, we can perform some actions or log messages before the update happens.

# componentDidUpdate()

- The componentDidUpdate() method is a lifecycle method in React that is called after a component has been updated and re-rendered.
- It is useful for performing side effects or additional operations when the component's props or state have changed.

## Example

```
import React, { Component } from 'react';

class ExampleComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  componentDidUpdate(prevProps, prevState) {
    if (prevState.count !== this.state.count) {
      console.log('Count has been updated:', this.state.count);
    }
  }

  handleClick() {
    this.setState(prevState => ({
      count: prevState.count + 1
    }));
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.handleClick()}>Increment</button>
      </div>
    );
  }
}

export default ExampleComponent;
```

- As of React 16.3, the componentDidUpdate() method can receive two additional arguments: prevProps and prevState. These arguments provide access to the previous props and state values, which can be useful for performing comparisons.
- But if you are using a more recent version of React, you can utilize the useEffect() hook with dependency array to achieve similar functionality.

# getSnapshotBeforeUpdate()

- The getSnapshotBeforeUpdate() method is called just before the component's UI is updated.
- It allows the component to capture some information about the current state of the UI, such as the scroll position before it changes.
- This method returns a value that is passed as the third parameter to the componentDidUpdate() method.

## Example

```
import React from 'react';
import ReactDOM from 'react-dom';

class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritefood: "rice"};
  }
  componentDidMount() {
    setTimeout(() => {
      this.setState({favoritefood: "pizza"})
    }, 1000)
  }
  getSnapshotBeforeUpdate(prevProps, prevState) {
    document.getElementById("div1").innerHTML =
    "Before the update, the favorite was " + prevState.favoritefood;
  }
  componentDidUpdate() {
    document.getElementById("div2").innerHTML =
    "The updated favorite food is " + this.state.favoritefood;
  }
  render() {
    return (
      <div>
        <h1>My Favorite Food is {this.state.favoritefood}</h1>
        <div id="div1"></div>
        <div id="div2"></div>
      </div>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));

```

# Unmounting Phase

- Unmounting phase is the last stage of reacts component life cycle.
- The unmounting phase refers to the lifecycle stage when a component is being removed from the DOM (Document Object Model) and is no longer rendered or accessible.
- During this phase, React performs a series of cleanup operations to ensure that the component and its associated resources are properly disposed of.
- This can happen for various reasons, such as when the component is no longer needed, the parent component is re-rendered without including the child component, or when the application is navigating to a different page or view.

# componentWillUnmount()

- This method is called just before the component is removed from the DOM.
- It allows you to perform any necessary cleanup, such as canceling timers, removing event listeners, or clearing any data structures that were set up during the mounting phase.
- After componentWillUnmount() is called, the component is removed from the DOM and all of its state and props are destroyed

## Example

```
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class MyComponent extends Component {
  state = {
    showChild: true,
  };

  handleDelete = () => {
    this.setState({ showChild: false });
  };

  render() {
    const { showChild } = this.state;

    return (
      <div>
        {showChild && <Child />}
        <button type="button" onClick={this.handleDelete}>
          Delete Header
        </button>
      </div>
    );
  }
}

class Child extends Component {
  componentWillUnmount() {
    alert('The component named Child is about to be unmounted.');
  }

  render() {
    return <h1>Hello World!</h1>;
  }
}

const rootElement = document.getElementById('root');
ReactDOM.render(<MyComponent />, rootElement);

```

- It's important to note that once a component is unmounted, it cannot be mounted again. If you need to render the component again, you will need to create a new instance of it.
