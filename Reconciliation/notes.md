# What is Reconciliation ?

- Reconciliation is th process that react uses to update DOM efficiently when something changes in the react app.
- React compares old virtual DOM with new virtual DOM and updates only the parts of the DOM that need to change.
- This makes React apps fast and efficient since React minimizes unnecessary DOM updates.

# How Does Reconciliation Work ?

- React's core idea is to compare the current state to the new state after a change this process is called `Diffing`.

## 1. initial render

- When the app loads first time react creates a virtual DOM . it then renders this virtual DOM to the DOM in the browser.

## 2. When something changes.

- When something changes react triggers a re-render
- it rebuilds a new virtual DOM and compares it with the previous virtual DOM

## 3. Diffing.

- React compares the new virtual DOM to old virtual DOM in a smart way:
- it only updates parts of the UI that have changed.
- it does this by walking through both virtual Doms and comparing the differences.

## 4. Minimal DOM updates.

- Once react knows what has changed. it caluclates the minimal set of updates required to make the real DOM
  match the new virtual DOM.

# Why is Reconciliation Important ?

- Efficiency: React doesn’t just update the entire DOM every time something changes. It makes the smallest updates possible, which keeps the app fast.
- Declarative UI: React allows you to describe the UI based on your app’s state, and React takes care of figuring out how to efficiently update the DOM. You don’t need to worry about DOM manipulations yourself.

# Why Reconciliation is Smart:

- Component-based Approach:
  React treats each component as a unit. If only a single component changes (like a button), React only updates that component and not the entire UI.
- Efficient Updates:
  React avoids unnecessary updates, and updates only those parts of the UI that actually need to change, which minimizes performance overhead.
- Re-render Optimization:
  React uses a key system to identify which items in a list have changed (like in a dynamic list of items). This helps it efficiently update only the changed items rather than the entire list.
