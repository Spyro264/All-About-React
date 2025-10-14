# What is React.createElement()

- `React.createElement()` is a method which is used to create an react element
- When we use React.createElement() it returns us an obj and the obj represents vitrual dome node.
- `createElement()` methods accpets 3 args they are `type` , `props` , `children`
- TYPE : here u need to specify which element u want to create like `div` `li` `ul` etc.
- PROPS (optional): here u can pass attributes for the element u creatred like `calssName` , `id` , `style` etc.
- CHILDREN (optional): here u cn pass other elements or text which will be nested insid the current element

# Creating Element Using JSX

```
<h1 class="greeting">Hello, world!</h1>
```

# Creating Element Using createElement() method

```
const h1 = React.createElement("h1", {className:"greeting}, "hello world");

```

- When ever we write like this using jsx `<h1 class="greeting">Hello, world!</h1>` will get transformed into like this internally.
  `const h1 = React.createElement("h1", {className:"greeting}, "hello world");`

# Why Use `createElement()`?

- Without JSX: `React.createElement()` is the only way to create elements. JSX is just syntactic sugar over this function.

# Example with More Complex Structure:

```
<div class="container">
  <h1 class="title">Welcome</h1>
  <p class="description">This is a description.</p>
</div>

```

```
const element = React.createElement(
  'div',
  { className: 'container' },
  React.createElement('h1', { className: 'title' }, 'Welcome'),
  React.createElement('p', { className: 'description' }, 'This is a description.')
);

```

# Conclusion:

- `React.createElement()` is how React internally creates elements that are rendered to the DOM.
- JSX is a shorthand for this function, making it easier to work with and more readable.
