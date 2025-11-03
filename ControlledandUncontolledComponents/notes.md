# What Are Controlled and Uncontrolled Components in React?

- When you build forms in React (like <input>, <textarea>, <select>), you need a way to handle user input.
- There are two ways to do that:

1. Let React control the input value
2. Let the Browser (DOM) control the input value

Let the Browser (DOM) control the input value

1. Controlled Components
2. UnControlled Components

# Controlled Components

- Controlled components is a `form element `whose values are controlled by reacts state.
- The value shown in the inout always comes from the reacts `useState`
- anyuser changes trigger an `onChange` event

```

import React, { useState } from "react";

const ControlledExample = () => {
  const [name, setName] = useState("");

  const handleChange = (e) => setName(e.target.value);
  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Submitted: ${name}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={name}       // React controls this value
        onChange={handleChange}
      />
      <button type="submit">Submit</button>
    </form>
  );
};

export default ControlledExample;

```

# Usage

Use controlled components when you need:

- Form validation
- Conditional rendring
- Dynamic or dependent inputs
- Live updates (like search filters)

# Uncontrolled Components

- Uncontrolled component is a form element that manages its own state inside the dom.
- You don’t store its value in useState.
- instead, you use a ref to access it when needed (like on form submission).
- The browser manages the input value internally, React just reads it when required.

```

import React, { useRef } from "react";

const UncontrolledExample = () => {
  const inputRef = useRef();

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Submitted: ${inputRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        ref={inputRef}      // React accesses it via ref
      />
      <button type="submit">Submit</button>
    </form>
  );
};

export default UncontrolledExample;

```

# Usage

Use uncontrolled components when:

- You don’t need real-time validation or re-renders
- Simpler forms or 3rd-party integrations
- File uploads (e.g. <input type="file" />) — since browsers handle them better
