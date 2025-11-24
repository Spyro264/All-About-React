# What is useRef ?

- useRef is one of the powerful hook in react which lets you to reference a value thats not needed for rendering.
- in simpler words useref is a hook that allows you to persist values across renders without triggering a re-render.
- when we say "reference a value" it means useRef provides a way to store a mutable value that doesnt need to cause re-renders.
- useRef returns an `Object` with a single property called `current`.
- initially the `current` property is set to the initial value that you pass ex: `useRef(100)` current prop is set to 100
- useref accepts one argument that is initial value .and that initial value be assigned to .current property

## Implementation

```
const ref = useRef(initialValue)
```

- Reference :` useref(initialValue)`

# Usage

- Referencing a value with ref
- Accesing and manipulating Dom with a ref
- Avoiding recreating of ref contents.

# Things to watch out for

- We can mutate `ref.current` property it is mutable.
- However if it holds an Object that is used for rendring then we should not mutate the object.
- When we change `ref.current` property . React does not re-render our component . React is now aware of what you change and when you change bcoz ref persists across re-renders.
- Do not read or write `ref.current` during rendring , except for initialization This makes your components behaviour unpredictable.

# Note

- mutating ref does not trigger a re-render , so refs are not appropriate for storing info which u need to display on the screen.
- If you have to read or write something during rendering, use state instead.
- React will not reinitialzie or reset refs value during re-render
