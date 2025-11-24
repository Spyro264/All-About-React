# Importance of Keys in React

- In React `key` plays a crucial role in `optimizing performance` and ensuring that components behave correctly when items in a list are `added` , `removed` or `updated`.
- React uses `key` to identify which items have been changed , added or deleted and minimize the number of re-renders required to update the UI.
- React uses `Reconciliation` alogo also called as `diffing` algo to efficiently update the user interface.
- When ever the state or props changes . React needs to determine which part of Ui has been changed and only update those parts rather then re-rendring whole DOM.

# How Keys Help

- React uses `key` to track individual elements in a list of array .
- When React needs to update the DOM , it compares the prev virtual DOM with new one
- React uses key prop to identify each element uniquely . so its knows which elements have been added updated ot deleted
- Without keys react needs to update whole DOM leading to performcance issues.
