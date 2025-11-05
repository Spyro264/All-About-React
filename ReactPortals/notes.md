# What are React Portals ?

- In React , `Portals` provide a way to render child component outside of its parent components DOM hierarchy.
- While React normally renders children inside the parent component's DOM element. a Portal allows you to render children into a different part of the DOM entirely.

# Why do we need React Portals?

- React Portals are essential when we need to manage modals, tooltips, dropdowns, or overlays that need to be placed outside the usual parent-child DOM hierarchy but still need to function within the React component tree.
- Without Portals, these elements would be rendered inside their parent component’s container, which can create issues like:
- Css styling Issue , Z-index issue , Event Propagation Issues

# problem without React Portal

- here i have a navar with signup button
- When i click on signup a model needs to be redndered
- but the problem is we are using modal inside navbar and navbar has postion relative
- Which means modal will redner only inside navbar which doesnt look good
- we need modal to be in the center of the screen but here coz of parent css styling modal is getting effected

## Modal.jsx

```
import React from "react";
import ReactDOM from "react-dom";

const Modal = ({ open, setOpen }) => {
  return (
    <div
      style={{
        position: "absolute",
        top: "50%",
        left: "50%",
        transform: "translate(-50%, -50%)",
        width: "50%",
        height: "50%",
        backgroundColor: "red", // just to make it visible
        display: open ? "flex" : "none",
        alignItems: "center",
        justifyContent: "center",
        zIndex: 600,
        border: "2px solid red",
        flexDirection: "column",
        gap: 10,
      }}
    >
      <div style={{ background: "white", padding: 20 }}>
        I'm a modal (non-portal)
        <h1>Signup Page</h1>
      </div>
      <div>
        <button onClick={() => setOpen(false)}>Close</button>
      </div>
    </div>
  );
};

export default Modal;

```

## Navbar.jsx

```
import { useState } from "react";
import logo from "../assets/react.svg";
import Modal from "./Modal";

const Navbar = () => {
  const [open, setOpen] = useState(false);
  return (
    <div
      style={{
        backgroundColor: "black",
        display: "flex",
        justifyContent: "space-between",
        alignItems: "center",
        padding: 10,
        position: "relative",
        zIndex: 500,
        overflow: "hidden",
        height: "8vh",
      }}
    >
      <div>
        <img src={logo} alt="" />
      </div>
      <div>
        <ul style={{ display: "flex", gap: 20 }}>
          <li style={{ color: "white", listStyle: "none" }}>Home</li>
          <li style={{ color: "white", listStyle: "none" }}>Contact</li>
          <li style={{ color: "white", listStyle: "none" }}>About</li>
        </ul>
      </div>
      <div>
        <button style={{ padding: 1 }} onClick={() => setOpen(true)}>
          Signup
        </button>
      </div>

      {open && <Modal open={open} setOpen={setOpen} />}
    </div>
  );
};

export default Navbar;

```

- copy paste the above Modal and Navbar.jsx and click on signup button u will get to know the issue
- To overcome this kind of css , Zindex issues we have way called portals.
- Which allows us to render child components outside its parents container DOM hierarchy.
- even though if it is outisde parents DOM heirarchy . it will work as same as it is inside its parents DOM.

# Modal.jsx with Portal

```
import React from "react";
import ReactDOM from "react-dom";

const Modal = ({ open, setOpen }) => {
  return ReactDOM.createPortal(
    <div
      style={{
        position: "absolute",
        top: "50%",
        left: "50%",
        transform: "translate(-50%, -50%)",
        width: "50%",
        height: "50%",
        backgroundColor: "red", // just to make it visible
        display: open ? "flex" : "none",
        alignItems: "center",
        justifyContent: "center",
        zIndex: 600,
        border: "2px solid red",
        flexDirection: "column",
        gap: 10,
      }}
    >
      <div style={{ background: "white", padding: 20 }}>
        I'm a modal (non-portal)
        <h1>Signup Page</h1>
      </div>
      <div>
        <button onClick={() => setOpen(false)}>Close</button>
      </div>
    </div>,
    document.getElementById("modal-root")
  );
};

export default Modal;

```

# Navbar.jsx

```
import { useState } from "react";
import logo from "../assets/react.svg";
import Modal from "./Modal";

const Navbar = () => {
  const [open, setOpen] = useState(false);
  return (
    <div
      style={{
        backgroundColor: "black",
        display: "flex",
        justifyContent: "space-between",
        alignItems: "center",
        padding: 10,
        position: "relative",
        zIndex: 500,
        overflow: "hidden",
        height: "8vh",
      }}
    >
      <div>
        <img src={logo} alt="" />
      </div>
      <div>
        <ul style={{ display: "flex", gap: 20 }}>
          <li style={{ color: "white", listStyle: "none" }}>Home</li>
          <li style={{ color: "white", listStyle: "none" }}>Contact</li>
          <li style={{ color: "white", listStyle: "none" }}>About</li>
        </ul>
      </div>
      <div>
        <button style={{ padding: 1 }} onClick={() => setOpen(true)}>
          Signup
        </button>
      </div>

      {open && <Modal open={open} setOpen={setOpen} />}
    </div>
  );
};

export default Navbar;


```

# At last in your index.html add this

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>react-portals</title>
  </head>
  <body>
    <div id="root"></div>
    <div id="modal-root"></div>   /// you need to add this
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>

```

# How React Portals Work

- React provides the `ReactDOM.createPortal()` method to create a portal. This method takes two arguments:

1. The JSX content to render (the child elements you want to display).
2. The DOM node to render the content into (where the child will be injected in the DOM).

# git repo react-portal
