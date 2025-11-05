# What is Code Splitting ?

- Code splitting is a powerful optimization technique in react and javacript which is used to split the application code into smaller chunks
- Those smaller chuknks can be loaded when ever they needed or they will load on demand rather than loading the entire appliation at once
- This allows us to load only necessary code for the current page or feature . which improves the initial load of the application.

# Why do we need code splitting ?

- Code splitting is a very powerful technique which is used to optimize the initial load time of the application by loading only necessary code
- Modern js and react apps will grow faster in size as we add new features or when we use new libraries or components.
- If all the code is loaded once when the user access it first time it may result- by loading only necessary code in:
  1. Slow initila load.
  2. Heavy bundle size

# What is cide splitting used for ?

1. Improve performance : By splitting the code into smaller chunks . brower can now load only necessary code on demand. this improves the performance and decreses the initial load time .
2. Optimize Mobile and Low-End Device Performance : Code splitting reduces the amount of JavaScript that needs to be processed on mobile devices or low-end devices, improving the experience for users with less powerful hardware.

# How is Code Splitting Implemented in React ?

- React provides a multiple way to implement code splitting, typically with the help of `React Router` and `React.lazy()` or `dynamic import()`

## 1. React.lazy & Suspense

- React has bilt-in support for lazy loading components with React.lazy(). it allows you to dynaically import components only when they are needed.

# Example

```
import React, { Suspense, lazy } from 'react';

// Dynamically import the component only when it's needed
const MyComponent = lazy(() => import('./MyComponent'));

function App() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <MyComponent />
      </Suspense>
    </div>
  );
}

- here Mycomponent will be loaded when ever it is needed and while its loading a fallback ui will be rendered which is given by <Suspense>

```

## 2 . React Router & Code Splitting

- When using React Router for routing in your app, you can split the routes into chunks that will be loaded on demand.

```
import React, { Suspense, lazy } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

const Home = lazy(() => import('./Home'));
const About = lazy(() => import('./About'));

function App() {
  return (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Switch>
          <Route path="/" exact component={Home} />
          <Route path="/about" component={About} />
        </Switch>
      </Suspense>
    </Router>
  );
}

- In this example, the `Home` and `About` components will only be loaded when the user navigates to their respective routes.

```
