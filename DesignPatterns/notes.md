# Design patterns in React

- Design patterns are reusable solutions to common problems in software design.
- In the context of React, these patterns help developers build maintainable, scalable, and efficient applications.
- Here are the common design patterns used in React development:

# 1. Compound Component Composition Pattern

- Compound composition is a pattern in react where a set of realated components work together to share
  state and behaviour while remaining decoulpled and flexible.
- This patterns allows componets to interact with each other in a parent -child relationship
- Where the parent manages the shared data, and child components can modify or consume that state.
- In compound component composition, the child components are not tightly coupled to each other; instead, they interact through a common parent. The parent acts as a controller that passes down props or provides shared functionality, while the children components focus on rendering UI or performing specific tasks.

## Why Do We Need to Use Compound Component Composition?

- Compound components allow you to encapsulate the shared state or behavior inside the parent, which helps avoid prop drilling or redundant state management in each individual component.
- With this pattern, you can define the behavior of your UI more declaratively by focusing on what the UI should do (composition of components) rather than managing the logic inside each child. This improves readability and reusability.
- The parent component manages the shared state, and each child component focuses on its own responsibility, whether it's rendering UI or performing specific behavior. This separation improves maintainability.

## Problems Compound Component Composition Solves?

- Avoids Prop Drilling
- Shared State Management
- Dynamic Behavior for Nested Components
- Improved Flexibility and Reusability

folder : compoundcomposition (for another example on this pattern)

## Example

```
const Button = ({ label, onClick }) => {
  return <button onClick={onClick}>{label}</button>;
};

const Form = () => {
  const handleClick = () => alert('Button clicked!');

  return (
    <div>
      <Button label="Submit" onClick={handleClick} />
    </div>
  );
};


```

# 2. Container and Presentational Components Pattern

- This pattern divides components into Container components (which manage state and logic) and Presentational components (which only handle UI).

## Advantages

1. Separates business logic from UI rendering.
2. Increases component reusability.
3. Makes components easier to test.

## Example

- The Container component handles data fetching, state management, and event handling.
- The Presentational component is concerned only with displaying data and accepting callbacks.

```
// Container Component
const UserListContainer = () => {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetchUsers().then(data => setUsers(data));
  }, []);

  return <UserList users={users} />;
};
```

```
// Presentational Component
const UserList = ({ users }) => {
  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
};
```

# 3. Higher-Order Components (HOC) Pattern

- A Higher-Order Component is a function that takes a component and returns a new component with additional props or functionality.

## Advantages

- Code reuse and logic abstraction.
- Can add additional functionality (like authentication, error handling) without changing the original component.
- Helps with cross-cutting concerns (e.g., adding loading indicators, handling errors).

## Example

- HOCs are often used for adding common features, like logging, caching, or permission checks.

```
// Higher Order Component
const withLoader = (WrappedComponent) => {
  return (props) => {
    if (props.isLoading) return <div>Loading...</div>;
    return <WrappedComponent {...props} />;
  };
};

// Wrapped Component
const DataComponent = ({ data }) => {
  return <div>{data}</div>;
};

// Using HOC
const DataComponentWithLoader = withLoader(DataComponent);

```

# 4. Render Props Pattern

- `Render Props` is a technique used to share code or logic between components by passing a function as prop.
- it allows us to share its state or code logic with other components by passing a fun as a prop.
- The receiving component calls this function with its data to decide what to render.

## Advantages

1. Flexibility in sharing logic between components.
2. Avoids deep component nesting (compared to HOCs).
3. Encourages reusable logic.

## Example

```
const DataProvider = ({ render }) => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetchData().then(response => setData(response));
  }, []);

  return render(data);
};

const App = () => {
  return (
    <DataProvider
      render={(data) => (
        <div>{data ? data : "Loading..."}</div>
      )}
    />
  );
};

```

# 5. Context API Pattern

- The Context API allows you to share values between components without having to pass props manually at every level. This is helpful for global state management.

## Advantages

1. Avoids prop drilling (passing props through many layers).
2. Provides a way to share global state like themes, authentication data, etc.
3. Can be combined with useReducer or useState for complex state management.

## Example

```
const ThemeContext = createContext();

const App = () => {
  const [theme, setTheme] = useState('light');

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Navbar />
    </ThemeContext.Provider>
  );
};

const Navbar = () => {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <div>
      <p>Current Theme: {theme}</p>
      <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Toggle Theme
      </button>
    </div>
  );
};

```

# 6. State Reducer Pattern

- The State Reducer pattern involves managing state through a reducer function (similar to how Redux works), allowing a centralized and predictable state management approach.

## Advantages

1. Centralizes state management in a single function.
2. Makes state updates predictable.
3. Can be combined with other patterns like Context API.

## Example

```
const initialState = { count: 0 };

const reducer = (state, action) => {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
};

const Counter = () => {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </div>
  );
};

```

# 7. Component as a Service (CaaS) Pattern

- This pattern allows you to create generic, reusable components that can be configured and customized through props. These components can encapsulate logic or functionality that can be reused across multiple areas of your application.

## Advantages

1. Promotes reusability.
2. Keeps UI components modular and independent.
3. Increases maintainability by separating concerns.

## Example

```
const Button = ({ label, onClick }) => {
  return <button onClick={onClick}>{label}</button>;
};

const App = () => {
  return <Button label="Click Me" onClick={() => alert("Button clicked!")} />;
};

```
