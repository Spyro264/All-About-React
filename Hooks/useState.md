# What is useState() Hook ?

- `useState()` is a hook in react which manages ad add state to functional components .
- Before `hooks` were introduced , state could only be used in `class components`.
- But wit `useState` we can use state in functional components as well
- It is one of the common Hooks in react.

# Implementation

```
const [count , setCount] = useState(initialState);
```

## Explaination

- count = represents the current `value`
- setCount = is a `function` which is used to `update` the state
- initialState = here you can define the `default` value of the `state` . for example: if you add `useState(10)` then `count` will be `10` if useState(20) then `count` will be `20`
- initialState can be of any type `string` , `array` , `object` , `number`.

# What will useState retruns ?

- useState will always returns an `array` with `2` values.

1. State value = represents the current state value.
2. Setter function = This is a function which we wil use to update the State

## Example

```
const [count , setCount] = useState(0);
const [value , setValue] = useState(0);
```

# Note

- You can name anythig to the `state` and `setterFunction` but you need to follow this rule.

  1. State variable : should always start with 1 (count , value , isLoggedIn).
  2. Setter Function : `set followed by `camelcase` (setCount , setValue , setIsLoggedIn)

# Why Functional Updates works different from Direct State update ?

```
 const [count, setCount] = useState(5);

  function increment() {
    setCount(count +1 ); // 6
    setCount(count +1 ); // 6
  }
```

```
 const [count, setCount] = useState(5);

  function increment() {
    setCount((prev) => prev + 1); // 7
    setCount((prev) => prev + 1); // 7
  }
```

- In the above example we are seeing 2 types of outputs
- In the first one we are directly upddating state
- In the second one we are using prev which is an argument to update state

- To understand the difference b/w those outputs first we need to undertsand how react updates states
- Reacts state updates are `asynchronous` .meaning when you call setState, the state is not updated immediately.
- Inseatd react schedules the state updates and re-renders the components after the state change.
- But when you use `function form of setCount` , React ensures that the mostup-to-date state value is used for each update.

# Updating State Directly

```
function increment() {
    setCount(count + 1);  // 6
    setCount(count + 1);  // 6
}
```

- Here we are using direct update `setCount(count + 1)`.
- When we use `setCount(count + 1)` react does not update the state immediately.
- Instead `react` schedules the state update.
- However we are using `current value` `count` to update the state .
- The current value is 5.
- On the first line when we call this `setCount(count+1)` it wont update immediately. it will be schedule the state upate.
- In the second line, `setCount(count + 1)` is called again immediately. Since react hasnt updated the state yet, count is still `5`.
- So the result will be `6` for both the setState calls.

# Updating State by Functional Form

```
function increment() {
    setCount((prev) => prev + 1);  // 6
    setCount((prev) => prev + 1);  // 7
}
```

- Here we are using funcional update `setCount((prev) => prev + 1)`.
- We know that react state updates are asynchronous and it wont update the state immediately .
- But when we use `functional update` , react ensures that the most `up`-`to`-`date` `value` is used for each update.
- Remember here we are not using `count` to update.
- In the first line `setCount((prev) => prev + 1)` is called. react sees `prev` which is `5` so it calculates `5 + 1 = 6`. not updated yet.
- In the second line, `setCount((prev) => prev + 1)` is called again. React uses the new state value `(6)` because `prev` refers to the most current state, so it `calculates 6 + 1 = 7`.
- So the output will be `6` and `7`.

# A Clever Question

- As i explained earlier that React state updates are asynchronous.
- Then how `prev` will get the latest value even though the state has not been updated.
  1st- `setcount((prev)=> prev +1)` // prev is 5 so 5 + 1 = 6
- 2nd `seCount((prev) => prev +1)` // prev is 6 how ?
- I told that react batches the updates. and it wont update the state immediately.
- The question is then how the 2nd `setCount` got latest `prev`.

```
function increment() {
    setCount((prev) => prev + 1);  // schedules update and while updating count it will update prev so prev become 6
    setCount((prev) => prev + 1);  // and the above 6 is been used here
}
```

- once React starts to update state it updates it in sequence
- 1st setCount updates 1st
- 2nd setCount updates 2nd
- While updating the 1st state it prev will also get updated to new value
- and that new Val prev is used in the 2nd setCount
