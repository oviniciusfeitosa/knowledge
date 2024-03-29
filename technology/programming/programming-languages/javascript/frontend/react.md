# React

## Components

### Override props

In the example below it is possible to override properties from a newly created component.

{% code title="/src/modules/core/components/Row/index.tsx" %}
```typescript
import React, { HtmlHTMLAttributes } from 'react';

interface RowProps extends HtmlHTMLAttributes<HTMLDivElement> {}

const Row = ({ children, ...props }: RowProps) => {
  props.className = "row " + props.className;
  return (
  <>
    <div {...props}>
      {children}
    </div>
  </>);
};

```
{% endcode %}

## [Plus (+) symbol before the parameter](https://stackoverflow.com/a/6683020/1330323)

{% hint style="info" %}
The plus (`+`) operator returns the numeric representation of the object. So in your particular case, it would appear to be predicting the if on whether or not `d` is a non-zero number.

Reference [here](http://en.wikibooks.org/wiki/JavaScript/Operators). And, as pointed out in comments, [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic\_Operators#Unary\_plus\_\(.2B\)).\

{% endhint %}

## Recommended

* ****[**How to Setup ESLint and Prettier for Your React Apps**](https://thomlom.dev/setup-eslint-prettier-react/)****
* ****[**React examples**](https://reactjsexample.com/)****
*   **REACT HOOKS VS REDUX**

    > **React Hooks** provides an easy way of handling the component behavior and share the component logic. Redux **should be used** in applications that have several features. With these features sharing chunks of the same information.
    >
    >
    >
    > **Redux** is a library for managing the global application state. In this library, we can find several tools that help us, developers, to be in touch with the state of the application and also transform it by giving the user the ability to emit actions.
    >
    > * Single source of truth: the global state of your application is stored in an object tree within a single store.
    > * The State is read-only: The only way to change the store is by emitting actions.
    > * Changes are made with pure functions: To update the store, the reducer should be written as a pure function.
    >
    >
    >
    > **Redux** and **React** **Hooks** should be seen as complements and also as different things. While with the new React Hooks additions, useContext and useReducer, you can manage the global state, in projects with larger complexity you can rely on Redux to help you manage the application data.
    >
    >
    >
    > If you’re thinking about building an application, both can be used. While Redux holds the global state and actions that can be dispatched, the React Hooks features to handle the local component state.
    >
    >
    >
    > You don’t always need Redux for every app, or every component. If your app consists of a single view, doesn’t save or load state, and has no asynchronous I/O, I can’t think of a good reason to add the complexity of Redux.



    * ****[**DEMYSTIFYING REACT HOOKS VS REDUX**](https://www.imaginarycloud.com/blog/react-hooks-vs-redux/)****
    * ****[**Do React Hooks Replace Redux**](https://medium.com/javascript-scene/do-react-hooks-replace-redux-210bab340672)****
* ****[**Criando container personalizaveis em React**](https://blog.matheuscastiglioni.com.br/criando-containers-personalizaveis-em-react/)****
* ****[**Build a financial dashboard with React**](https://www.telerik.com/blogs/lets-build-a-financial-dashboard-with-react)****
* ****[**React Admin - Authentication**](https://marmelab.com/react-admin/Authentication.html)****

## Known issues

#### Could not find a declaration file for module 'react-router-dom'

if you are using **yarn**:

```
yarn add @types/react @types/react-dom @types/react-router-dom -D
```

if you are using **npm**:

```
npm install @types/react @types/react-dom @types/react-router-dom --save-dev
```

