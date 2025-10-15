# What is JSX ?

- JSX (java script XML) is a sysntax extension for Javascript.
- It allows us to write html like code directly within the js. Which makes it easier to build ui
- JSX look same as HTML but its not an HTML its an jsx extension.
- We can also embed js expression isnside jsx using curly braxes {}.
- JSX allows you to use attributes similar to HTML, but with some differences.
- `className` instead of class (since class is a reserved word in JavaScript).
- `htmlFor` instead of for (since for is also a reserved word).
- `camelCase` for attribute names (e.g., onClick instead of onclick, onChange instead of onchange).
- Babel converts JSX into regular js while compling.

## Syntax

```
const element = <h1>Hello, world!</h1>;
```

## Javascript expression inside jsx

```
const name = "John";
const greeting = <h1>Hello, {name}!</h1>;
```
