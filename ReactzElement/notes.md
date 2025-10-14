# What is React Element

- React element is a plain `Object` that representes a Dom node
- A React element describes what you want to see on the `screen`.
- React elements are created using either JSX syntax or `React.createElement()`.
- React elements are immutable, meaning once they're created, they don’t change. Instead of modifying existing elements, React creates new elements for the next render cycle. This allows React to efficiently manage changes to the UI.

# How to create an Element

```
const h1 =  React.createElement('h1', {}, 'Hello, world!');

```

# React Element vs React Component

- A React element is a simple object describing a DOM node or component.
- A React component is a function or class that returns React elements. Components are reusable, and they can return elements based on props or state.
