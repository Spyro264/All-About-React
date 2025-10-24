# What is Diffing ?

- Diffing is the process of comparing old virtual DOM with new virtual DOM to determine the changes and then applying minimal changes
  to the real DOM.

# How Does Diffing Work ?

- When the react app first loads Virtual DOM is created.
- the virtual DOM is directly updated to real DOm coz its a first load.
- now if there are any prop or state chages react creates new virtual DOM and compares that with old virtual DOM to determine the changes (this is diffing ).
- if react finds out any changes it will calculate minimal updates and updates the real dom with those minimal updates.

# How React Differs Between Virtual DOMs

- Component-level comparison: React compares components at the same level first. If it detects that two components have the same type (like two <div> elements), it can optimize by assuming they will behave similarly.

- Element-level comparison: For elements like <div>, <h1>, <button>, etc., React checks if the type (tag) of the element has changed. If it’s the same tag (e.g., <h1>), it compares the children inside that element to see if they’ve changed.

# Key Optimization:

- Keys in lists: When React renders lists (like an array of items), it uses keys to track each item’s identity. This helps React know if an item has been added, removed, or moved.
- Without keys, React has to compare each item in the list and make guesses about what changed. With keys, React can directly correlate items in the old and new virtual DOMs, resulting in faster diffing.

# Efficient Update:

- After identifying what has changed, React calculates the minimal set of updates needed to make the real DOM match the new virtual DOM.
- React only updates changed parts of the real DOM, which improves performance and avoids unnecessary re-renders.
