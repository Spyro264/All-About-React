# What is CompundComposition

- Compound composition is a pattern in react where a set of realated components work together to share
  state and behaviour while remoining decoulpled and flexible.
- This patterns allows componets to interact with each other in a parent -child relationship
- Where the parent manages the shared data, and child components can modify or consume that state.
- In compound component composition, the child components are not tightly coupled to each other; instead, they interact through a common parent. The parent acts as a controller that passes down props or provides shared functionality, while the children components focus on rendering UI or performing specific tasks.

# Why Do We Need to Use Compound Component Composition?

- Compound components allow you to encapsulate the shared state or behavior inside the parent, which helps avoid prop drilling or redundant state management in each individual component.
- With this pattern, you can define the behavior of your UI more declaratively by focusing on what the UI should do (composition of components) rather than managing the logic inside each child. This improves readability and reusability.
- The parent component manages the shared state, and each child component focuses on its own responsibility, whether it's rendering UI or performing specific behavior. This separation improves maintainability.

# Problems Compound Component Composition Solves?

- Avoids Prop Drilling
- Shared State Management
- Dynamic Behavior for Nested Components
- Improved Flexibility and Reusability

folder : compoundcomposition
