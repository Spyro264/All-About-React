# What are Web Workers ?

- Web Workers are JS features that allows us to run the script in the background on a sepearte thread frm the main UI thread of your web application.
- This can help you perform computationally expensive tasks without blocking the user interface,which improves the performance and responsiveness of your app.
- In simple words web workerks allows you to do heavy lifting wihtout freezing the browsers main thread

# How Web Workers Work ?

- Main thread (UI thread): This is where the user interface (UI) and regular JavaScript code run.
- Worker thread: This is a separate thread where Web Workers run, which means that tasks in the worker thread don't interfere with the main thread.
- You can send messages between the main thread and the worker thread using the postMessage API, and the worker can also send results back using the same method.

# How Do Web Workers Integrate with React?

- In React, you can use Web Workers to handle tasks in the background while keeping the UI thread free to interact with users. React itself doesn't have built-in support for Web Workers, but you can easily integrate them using JavaScript's native Web Worker API.

# Implemnting will be done later ?

-
