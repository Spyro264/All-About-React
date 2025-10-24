# What is React Fiber ?

- react fiber is the coplete rewrit of old reacts core algorithm.
- it is introduced to handle asynchronous rendring and improve performance in react apps , especially for large, complex UIs and heavy animations.

# Key Feature of React Fiber

1. `Asynchronous Rendring` : Before Fiber, React rendered updates synchronously (all at once). Fiber allows React to break up rendering work into smaller chunks and perform it asynchronously. This means React can pause rendering when needed (e.g., to handle user interactions) and then resume later, ensuring the UI remains responsive.

2. `Incremental Rendering` : Fiber introduces incremental rendering where React can render small portions of the UI over multiple frames. This avoids UI blocking, especially during complex operations like animations, large data fetching, or deep component trees.

3. `Prioritization of Updates `: React Fiber allows for prioritizing updates. For example, urgent updates like user interactions (clicks, typing) are processed before less important updates, like data fetching or background tasks. This ensures that the app responds to user input immediately, without being blocked by less urgent tasks.

4. `Concurrency` : Concurrent Mode (an experimental feature) introduced with React Fiber enables concurrent rendering. React can pause rendering work in the middle and perform other tasks before coming back to finish the rendering. This improves the interactivity of the app by ensuring updates don’t block the UI thread.

5. `Fiber Nodes` : The traditional reconciliation used a tree of React elements. With Fiber, React uses a fiber tree where each node represents a unit of work in the rendering process. This allows React to better track the state, priority, and lifecycle methods of each component during rendering.

6. `Granular Control Over Work `: React Fiber enables fine-grained control over how work is done. Instead of rendering all components in a single pass, React breaks down updates into small units of work that can be scheduled, paused, and resumed. This helps to maintain smooth user interactions and avoids blocking the main thread.

7. `Error Handling` : React Fiber introduces better error boundaries. React can catch errors during rendering and display fallback UIs without crashing the entire app. This is especially useful in large applications where a single error could otherwise cause the entire page to fail.

# How Does React Fober Works

- At a high level, React Fiber works by breaking down the rendering work into fiber nodes, which represent units of work in the reconciliation process. These fiber nodes contain all the information React needs to perform a render cycle for a component, including its state, props, and lifecycle methods.
- The rendering work is scheduled and can be paused, resumed, or interrupted based on priority. This process allows React to manage complex UI updates in a non-blocking way, making the UI feel more responsive.

## Here’s a simplified breakdown of how it works:

- Component Rendering: Each component gets assigned a fiber node that represents its work.

- Work Units: React breaks down rendering into small, incremental work units, which can be scheduled for execution in chunks.

- Work Scheduling: React schedules these units of work based on their priority.

- Concurrency: React can pause and resume work, allowing for smoother updates and responsive interactions.

- Fiber Tree: Each node in the fiber tree represents a unit of work that React will perform as part of the rendering cycle.
