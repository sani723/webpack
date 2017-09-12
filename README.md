# Introduction to webpack

This is sort of a cookbook of how to get things done with webpack. Start with this guide as your webpack docs, then dig into the official docs for more high-level information on the core notions behind webpack.

## What is webpack?

> webpack is a module bundler for modern JavaScript applications. When webpack processes your application, it recursively builds a dependency graph that includes every module your application needs, then packages all of those modules into a small number of bundles - often only one - to be loaded by the browser. and it is incredibly configurable.

Ok in plain words, from the very core thing `webpack is simply a program that compiles one JavaScript file into another`.

In order to do this run following command in your terminal.
```
webpack app.js build.js
```
app.js - name of the file that you want to be compiled
build.js - name of the file that you want app.js compiled into


webpack ia an all-round tool that provides number of different features including 
* Module bundling
* File minification
* Sass/Scss compilation
* Inline CSS
* ES6 code commpilation
* Code Linting
* Code splitting (loading only the JavaScript code page by page basis)
* and much much more 

Being able to use these features not only makes developing website easier but also helps to optimize your code so that you have efficient and blazing fast websites. 

## Why webpack?

webpack is not the only module bundler out there. If you are choosing between using webpack or any other bundler, then do feature-by-feature comparison and you will find how webpack fares against the current competition.

Simply put, Webpack is such a powerful tool that it can already perform the vast majority of the tasks you'd otherwise do through a task runner. For instance, Webpack already provides options for `minification` and `sourcemaps` for your bundle. In addition, Webpack can be run as `middleware` through a custom server called `webpack-dev-server`, which supports both `live reloading` and `hot reloading`. By using loaders, you can also add ES6 to ES5 transpilation, and CSS pre- and post-processors.

The major drawback to using Webpack is that it is rather difficult to configure, which is unattractive if you're trying to quickly get a project up and running.

### Bundling vs. Loading

It's important to note some key differences between loading and bundling modules. A tool like SystemJS, which can be found under the hood of JSPM, is used to load and transpile modules at runtime in the browser. This differs significantly from webpack, where modules are transpiled (through "loaders") and bundled before hitting the browser.

Each method has its advantages and disadvantages. Loading and transpiling modules at runtime can add a lot of overhead for larger sites and applications comprised of many modules. For this reason, SystemJS makes more sense for smaller projects where fewer modules are required. However, this may change a bit as HTTP/2 will improve the speed at which files can be transferred from server to client. Note that HTTP/2 doesn't change anything about transpiling modules, which will always take longer when done client-side.

## Core concepts

* **Entry** The entry point tells webpack where to start and follows the graph of dependencies to know what to bundle. You can think of your application's entry point as the contextual root or the `first file to kick off your app`.

In webpack we define entry points using the `entry` property in webpack configuration object.
```js
// webpack.config.js

module.exports = {
  entry: './app.js'  // path to entry file
};
```

* **Output** Once you've bundled all of your assets together, you still need to tell webpack where to bundle your application. The webpack output property tells webpack how to treat bundled code.
```js
// webpack.config.js

module.exports = {
  entry: './app.js',  // path to entry file
  output: {
    filename: "./build.js"
  },
};
```

* **Loaders** in webpack transform all assets files into modules as they are added to your dependency graph. In plain words `Loaders` identify which file or files should be transformed by a certain Loader using its `test` property, and then transform those files so that they can be added to your dependency graph and eventually your bundle through `loader` property.
```js
// webpack.config.js

module.exports = {
  entry: './app.js',  // path to entry file
  output: {
    filename: "./build.js"
  },
  module: {
   rules: [
    { test: /\.js$/, loader: "jshint-loader" },
   ]
  } 
};
```
The configuration above has defined a `rules` property for a single module with two required properties: `test` and `use`. This tells webpack's compiler the following:
> Hey webpack compiler, when you come across a path that resolves to a '.txt' file inside of a require()/import statement, use the raw-loader to transform it before you add it to the bundle.

* **Plugins** While `Loaders` only execute transforms on a per-file basis, plugins are most commonly used to perform actions and custom functionality on "compilations" of your bundled modules.

In order to use a plugin, you just need to `require()` it and add it to the `plugins` array. Most plugins are customizable via options. Since you can use a plugin multiple times in a config for different purposes, you need to create an instance of it by calling it with `new`.
```js
// webpack.config.js

const HtmlWebpackPlugin = require('html-webpack-plugin'); //installed via npm

module.exports = {
  entry: './app.js',  // path to entry file
  output: {
    filename: "./build.js"
  },
  module: {
   rules: [
    { test: /\.js$/, loader: "jshint-loader" },
   ]
  },
  plugins: [
    new HtmlWebpackPlugin({template: './src/index.html'})
  ] 
};
```
