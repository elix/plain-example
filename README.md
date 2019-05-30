This repository shows how a typical web project can consume any web component, including any web component from the [Elix](https://component.kitchen/Elix) library.


# Quick start

Enter the following in a terminal window:

```
git clone git@github.com:elix/simple-example.git
cd simple-example
npm install
npx http-server
```

Then open [http://localhost:8080](http://localhost:8080) to view the sample page.


# Using web components

Web components like the ones in the Elix library are defined as JavaScript classes that you can manipulate as markup in HTML or directly in your JavaScript/TypeScript code.


## Instantiating web components in markup

Load the source file for the desired Elix component as a module. You can bundle it into your application using a bundler like webpack, or load it directly as shown here:

```html
<html>
  <head>
    <script type="module" src="./node_modules/elix/src/DateComboBox.js"></script>
  </head>
  <body>
    <elix-date-combo-box date="1 Jan 2020"></elix-date-combo-box>
  </body>
</html>
```

Once the component module is loaded, you can then instantiate the component with its tag name. The tag name for the [DateComboBox](https://component.kitchen/elix/DateComboBox) component is `elix-date-combo-box`. If desired, you can then set properties on the component as attributes, such as `date="1 Jan 2020"`.


## Instantiating web components in Javascript

Each Elix component module exposes a default export that you can `import` into your JavaScript (or TypeScript, etc.) application. You can then instantiate the component with `new`, set properties or invoke methods on it, and add it to the DOM like a regular HTML element:

```js
// Import the Elix components we want to use.
import DateComboBox from './node_modules/elix/src/DateComboBox.js';

// Instantiate an Elix component.
const dateComboBox = new DateComboBox();

// You can set custom properties on the component, invoke methods, etc.
dateComboBox.date = new Date('1 Jan 2021');

// We can add the components to the page like any other HTML elements.
document.body.appendChild(dateComboBox);
```


# Bundling components for production use

Elix components are written in plain JavaScript, and so require _no build step_ to be usable. For production use, you will generally want to use webpack or some similar bundler to create a smaller set of JavaScript files. When using a bundler, the `import` statement above can generally be simplified to:

```js
// Import the Elix components we want to use.
import DateComboBox from 'elix/src/DateComboBox.js';
```
