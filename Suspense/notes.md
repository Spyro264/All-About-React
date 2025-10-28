# What si React.Suspense ?

- React.Suspense is a react component that lets you shows a fallback UI while waiting for some content (like a lazy-loaded component or async data) to load
- in simpler words its a placeholder that react shows until the content is loaded.

# Why to use React.Suspense ?

- When we use React.lazy() components load asynchronously (i.e , react doesnt have the components code immediately)
- So if react ries to render it . ut doesnt know what toi render while the component is still loading THis casues a probelm
- React cant render something that hasnt been downloaded yet
- Thats where <Suspense> comes in
- When ever react doesnt have the code to render the component it searches for nearest <Suspense> boundary.
- that <Suspense> shoes the fallback UI until the compone is completely loaded.

```
import { lazy, Suspense } from "react";
import { Route, Routes } from "react-router-dom";

const App = () => {
  const Home = lazy(() => import("./components/Home"));
  const Contact = lazy(() => import("./components/Contact"));
  const About = lazy(() => import("./components/About"));

  return (
    <div>
      <Suspense fallback={<p>lOADING.........</p>}>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/contact" element={<Contact />} />
          <Route path="/about" element={<About />} />
        </Routes>
      </Suspense>
    </div>
  );
};

export default App;


```
