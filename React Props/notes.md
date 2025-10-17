# What are Props ?

- Props are read-only values passed from parent component to child component.
- Props are used to pass data or event handlers to child components
- They allow components to be dynamic and reusable as they allow child component to recive and render databased on the parent.

# Key points about props

- Props are immutable (read-only).
- A cild components which recieves props cannot modify the props. if it wans to modify it can use state.
- Props are always passed from parent to child componets.
- Props are dynamic. the data or functions passed in props can change anytime. and whenver they change child component will re-render to reflect the new data

# Passing Props from Parent to Child

```
// Parent Component
function ParentComponent() {
  const userName = "John Doe";
  const age = 30;

  return (
    <div>
      <ChildComponent name={userName} age={age} /> {/* Passing props to the child */}
    </div>
  );
}

// Child Component
function ChildComponent(props) {
  return (
    <div>
      <h1>Hello, {props.name}!</h1> {/* Accessing props in the child */}
      <p>Age: {props.age}</p>
    </div>
  );
}

```

# Accessing Props

```

function ChildComponent(props) {
  return <h1>Hello, {props.name}</h1>;
}

```

## Destructuring Props

- You can use destructuring to make accessing props more convenient, especially when there are multiple props.

```
function ChildComponent({ name, age }) {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>Age: {age}</p>
    </div>
  );
}
```

# Passing Functions as Props

```
// Parent Component
function ParentComponent() {
  const handleClick = () => {
    alert("Button clicked in child!");
  };

  return <ChildComponent onClick={handleClick} />;
}

// Child Component
function ChildComponent({ onClick }) {
  return <button onClick={onClick}>Click Me</button>;
}

```

# Default Props

- React allows you to set default values for props in case the parent component does not provide a value. This is done using the defaultProps property.

```
function ChildComponent({ name = "spyro", age = "99" }) {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>Age: {age}</p>
    </div>
  );
}

// spyro and 99 are default props if props doesnt contains value it will use them as default

```
