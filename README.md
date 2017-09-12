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
