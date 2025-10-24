# Stack Reconciler ( Reacts Old Architecture )

- Before react fiber was introduced . reacts used to use a classic rendring algorithm called stack Reconciler.
- That handled the reconciliation and rendering process synchronously.
- The old algorithm was efficient for simple applications but had significant limitations when it came to performance for complex apps, especially for things like async rendering, animations, and complex user interactions.

# Key Featires of Stack Reconciler

- React's old rendering process was synchronous. This means that once a re-render was triggered, React would perform the entire reconciliation and DOM update process in one go. This could lead to performance issues, especially with large components or when rendering complex UIs.
- Because rendering was synchronous, if you had complex updates or slow network calls, the browser's UI thread would be blocked while React worked through the update process. This could lead to noticeable lags or janky UI when interacting with the application.
- React followed a single execution flow, meaning that it would complete rendering before responding to user interactions or performing other tasks. There was no ability to pause or interrupt the process and allow other important events (like user input) to take priority.
- React did not have an explicit way to prioritize updates. For example, if you triggered multiple updates at once (e.g., an animation, user input, and network data fetch), React would treat all updates the same, potentially leading to poor user experience.
- Reconciliation was done in a single phase (a "Depth First" search of the component tree). Once React encountered a change, it would traverse the whole tree and update the DOM without any breaks, making it hard to handle large apps with complex rendering needs.
