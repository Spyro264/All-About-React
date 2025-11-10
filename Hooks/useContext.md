# What is useContext ?

- `useContext` is a powerful react hook which is used to share state or data between components without prop drilling.
- useContext allows to share data globally withput passing props manually.
- it is useful when multiple components needs same data fro example
  1. user login details
  2. dark mode etc.

# how it works

- React Context has 3 main parts

1. Create Context

```
const myContext = createContext()
```

2. Wrap components with Provider

```
<MyContext.Provider value={someValue}>
   <App />
</MyContext.Provider>
```

3. Consume using `usContext`

```
const data = useContext(MyContext);
```
