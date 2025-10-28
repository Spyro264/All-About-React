# What is Lazy Loading ?

- Lazy Loading is a performance optimizing technique in react where components or resources are loaded only when they are needed.
- Insetad of Loading everything on the first load (initla render).
- It helps to reduce the initial budle size , speed ups the first page load , and improves user experience.

## Before implementing LazyLoading first we will understand the problem without lazyloading

1. Create # pages `Home` , `Contact` , `About` add console logs in all pages.
2. Import the pages in App.jsx

```
import Home from "./components/Home";
import Contact from "./components/Contact";

const App = () => {
  return (
    <div>
      <Home />
      <Contact />
      <About />
    </div>
  );
};

export default App;
```

3. after running the app check the logs
4. in logs u will get `home` `about` `contact`
5. But why 3 logs ? u just opened the app and you are in `Home` page but still you are getting logs of contact and about
6. That tells us that even though you are in home page its loading all the other pages unneccessarily.
7. wt if the about and contact pages are heavily loaded with 6/7 get apis which eventually makes the app slower on the initial render.
8. To overcome this performace issue we use Lazy and Suspense concepts as shown below

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

9. here we used lazy and Suspense so that it will only loads the component when they are needed.
10. by this we optimized the inital render
11. if the iniial load takes time we also mentioned fallback ui in the suspense
12. you can run the app and check the logs if u are in Home page you wiull see only Home same for others

# Note

```
import React, { lazy, Suspense } from "react";

const App = () => {
  const Home = lazy(() => import("./components/Home"));
  const Contact = lazy(() => import("./components/Contact"));
  const About = lazy(() => import("./components/About"));

  return (
    <div>
      <Suspense>
        <Home />
        <Contact />
        <About />
      </Suspense>
    </div>
  );
};
```

- Even though you used lazy and Suspense, all components load because they’re all being rendered immediately — React must fetch them all to display them. Lazy loading only helps when components are rendered conditionally or on demand
