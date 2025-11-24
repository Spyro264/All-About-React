# What is useMemo ?

- useMemo is react hook that memoizes(cache) the result of a computation so that is not recomputed on every render.
- It helps optimize performance by avoiding unnecessary recalculations of expensive calculation during re-renders.

# Why To Use useMemo ?

- React components re-render when ever the props or state change , which can lead to unnecessary re-calulation
- Especially when the component performs expensive computations or renders a large number of elements useMemo allows you to memoize the result so that will be recomputd or recaluckated only when its dependencies change

# How does useMemo Work ?

- useMemo takes 2 arguments
- A function that compute a value
- dependency array . if the dependencies change the function will recompute. otherwise it will return the cached value

# Implementation

```
const cachedValue = useMemo(calculateValue, dependencies);
```

# Example

- Imagine you have an expensive calculation, like filtering a large list, and you want to prevent it from running on every render.

```
import React, { useState, useMemo } from 'react';

function ExpensiveComputation() {
  const [number, setNumber] = useState(0);
  const [isChecked, setIsChecked] = useState(false);

  const expensiveResult = useMemo(() => {
    console.log('Recalculating expensive result...');
    return number * 1000;
  }, [number]);

  return (
    <div>
      <p>Expensive result: {expensiveResult}</p>
      <button onClick={() => setNumber(number + 1)}>Increase Number</button>
      <button onClick={() => setIsChecked(!isChecked)}>Toggle Check</button>
    </div>
  );
}

```

## How it Works

- Without `useMemo` the above function will run on `every state updates`
- the above fun is `dependent` on `number state` so it should be re-calculated when ever the number changes
- But try removing `usememo` for the above fun and check the logs even though you update `isChecked` whch is not at all related to `expensiveResult` function but still you will get the logs of `expensiveResult`
- Thats where `useMemo` comes to picture just implement the `useMemo` pass your `expensive calculation and dependencies` which the fun is dependent on .then try to click `isCliked` you wont see the `logs` . bcoz useMemo handles the `fun` now and recomputes only when its `dependencies` changes
