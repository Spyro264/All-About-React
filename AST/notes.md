# What is AST ?

- AST stands for Abstract Syntax Tree
- It is a tree representation of our code.
- in easy words its like a structured map of our program so that the computer can understand and manipulate.
- `Abstract` means it ignores unimportant syntax like semicolon , comma focusing on meaning and structure.

## Example analogy

- Code: `const x = 5 + 3;`
- AST is like a family tree for your code showing:
- Declaration → Identifier `x` → Operation +`→ Numbers `5`and`3`.

# Why do we need AST ?

- AST is a `best` tool for `Babel` , `Eslint` , `Typescript` , `Webpack` etc.
- Babel internally uses `AST` to convert ES6 to ES5.
- Eslint which finds `errors` and `syntax` errors uses AST internally to traverse throught the whole code .
- Tools like `UglifyJS` or `Terser` use AST to rewrite code efficiently.

# When is AST formed ?

- AST is formed during `parsing` phase of a complier or tranpiler.

## How AST looks like

```
const sum = (a, b) => a + b;
```

```
Program
 └─ VariableDeclaration (const)
     └─ VariableDeclarator
         ├─ Identifier (sum)
         └─ ArrowFunctionExpression
             ├─ params: [Identifier(a), Identifier(b)]
             └─ BinaryExpression (+)
                 ├─ Identifier(a)
                 └─ Identifier(b)
```
