# What is Bundler ?

- Bundler is a tool which takes multiple files like js , ys , images , assets and combine them into single file.
- Bundler also perform additional optimizations like minification ,code splitting , tree shaking etc to improve the performance and usability of the web application.

# Why Do We Need a Bundler?

- in modern applications code is typically split across mulitple files for modularity and maintainability.
- However, browsers are not efficient when loading hundreds or thousands of individual files. This is where bundlers come in, as they help:
- Bundlers often minify JavaScript and CSS files, which reduces their file size and makes them load faster. For example, spaces, comments, and long variable names are removed.
- Bundlers like Webpack support code splitting, which allows you to split your code into smaller chunks. This means the browser will only load the necessary code for the page being viewed, speeding up the initial load.
- Tree Shaking: This is an optimization technique where the bundler removes any unused code from libraries, reducing the size of the final bundle.

# Conclusion

- A bundler simplifies the development process by allowing you to break your application into multiple modules while optimizing it for the browser. It helps reduce load times, improve performance, and provide a more maintainable and scalable architecture for your web application. By bundling and optimizing your code, a bundler ensures that you deliver the best possible experience to your users, both in terms of performance and reliability.

# types of Bundler

1. Webpack
2. Parcel
3. Vite
4. Rollup
5. Snowpack
6. Fusebox
7. esbuild
8. Tarp
9. Metro
10. Browserify
