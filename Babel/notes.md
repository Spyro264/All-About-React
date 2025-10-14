# What is Babel ?

- Babel is a Javascript `complier` or `transpiler` .
- its main job is to convert `modern js` ES6+ into older js so that it can run on all browsers.

# Wy do we need Babel ?

- Not all browsers supports modern `JS` fetatures like `let , const , var , destructuring , async/await`
- Babel rewrites new js into older version so that all `browser` can undertsand.
- React uses `Jsx` which is not valid js . `Bable` converts jsx into `React.createElement`

# Example

```
// ES6
const res = (a, b) => a + b;
```

```
// Transpiled ES5
var sum = function(a, b) {
  return a + b;
};
```

# How babel works ?

- Babel works in three main steps
- `Parsing` : Bable reads our code and converts them into Abstract Syntax Tree. Which is a tree representation of our code .
- `Transformation` : Babel applies transformation to that AST (e.g., convert arrow functions to regular functions, JSX to React.createElement).
- Code Generation : Babel generates the final js code from the transformed AST.

# Extra Info About Babel

- In React 17+, Babel can also convert JSX to automatic runtime, meaning you don’t always need to import `React` in files using JSX.
- Babel transpiles syntax `(like => to function) `but doesn’t automatically add missing `APIs` (like Promise or Array.includes).
- For that, you’d use polyfills (e.g., core-js) alongside Babel.

# Internal Work of Babel

```
// Original ES6 + JSX
const sum = (a, b) => a + b;
const element = <h1>Hello</h1>;
```

```
1. at first bable parses our code and transform our code into AST which looks like this

Program
├─ VariableDeclaration (const)
│   └─ VariableDeclarator
│       ├─ Identifier (sum)
│       └─ ArrowFunctionExpression
│           ├─ params: [Identifier(a), Identifier(b)]
│           └─ BinaryExpression (+)
│               ├─ Identifier(a)
│               └─ Identifier(b)
└─ VariableDeclaration (const)
    └─ VariableDeclarator
        ├─ Identifier (element)
        └─ JSXElement
            ├─ JSXOpeningElement (h1)
            ├─ JSXText ("Hello")
            └─ JSXClosingElement (h1)


2. Transformed AST after bable parses it

Program
├─ VariableDeclaration (var)
│   └─ VariableDeclarator
│       ├─ Identifier (sum)
│       └─ FunctionExpression
│           ├─ params: [Identifier(a), Identifier(b)]
│           └─ BlockStatement
│               └─ ReturnStatement
│                   └─ BinaryExpression (+)
│                       ├─ Identifier(a)
│                       └─ Identifier(b)
└─ VariableDeclaration (var)
    └─ VariableDeclarator
        ├─ Identifier (element)
        └─ CallExpression
            ├─ Callee: MemberExpression (React.createElement)
            └─ Arguments
                ├─ Literal ("h1")
                ├─ Literal (null)
                └─ Literal ("Hello")

```
