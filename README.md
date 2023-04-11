# **<p align="center"> React Js </p>**

## Introduction

- React is Ui Library -> From Facebook

- React give us a way to build websites & UIs with organized and resuable componetns

- Why use React

  - Organization
  - Reuseable
  - Flexiblity
    - Just Part Of Project,
    - Mobile Apps -> React Native ,
    - Desktop app -> Electron ,
    - server side render -> Next Js )
  - Performance
  - Declarative
    - Components
    - Props
    - State
    - Events

- ### Environment setup
  - Install Node
  - Text Editor -> Vs Code
  - Git
  - Postman

---

<br />

## Installation

<br />

- Don't use create-react-app because it's not updateing with community

- ### Basic React

  - <b>Use Node Version > 16</b>

  - `npm create vite@latest`
  - select -> react

- ### With Next.js

  - `npx create-next-app`

- ### With Remix

  - `npx create-remix`

- ### With Gatsby

  - `npx create-gatsby`

- ### Expo (for native apps)
  - `npx create-expo-app`

<br />

## About JSX

<br />

- Every return HTML is wrap in the single parent element

  - you can use specific `<div></div>` or fragment `<></>` => it will not create parent elemet in DOM

- ### With Js

```js
function App() {
  return React.createElement(
    "div",
    { className: "container" },
    React.createElement("h1", {}, "My App")
  );
}
```

<br />

- ### With Jsx

```jsx
function App() {
  return (
    <div className='container'>
      <h1>This is My App </h1>
    </div>
  );
}
```

<br />

## Connect App.jsx with index.html using main.jsx or index.jsx

<br />

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## Components

## Props

- Props are the Pass to the Components , Properties of Componets
- Props are send Data Parent Components -> Children Components
- Pass props

```js
<Header text='Hello World' /> // text is Props
```

- Handle Props

```js
function Header(props) {
  return (
    <header>
      <div className='container'>
        <h2>{props.text} </h2>
      </div>
    </header>
  );
}
```

- Define Default props

```js
Header.defaultProps = {
  text: "Feedback UI",
};
```

- Props Validation (import PropTypes)

```js
Header.defaultProps = {
  text: "Feedback UI",
};
```

- Send Props Child to Parent

```js
Parent -> App.js;

function App() {
  const getHeaderData = (data) => {
    console.log(data);
  };
  return (
    <>
      <Header HeaderData={getHeaderData} />
      <h1>My App</h1>
    </>
  );
}

Child -> Header.js;

function Header(props) {
  props.HeaderData("This is Going To Child To Parent");
  return (
    <header>
      <div className='container'>
        <h2>{props.text} </h2>
      </div>
    </header>
  );
}
```

## Styling React Js

- Direct Connect .css file with Jsx File using import

- **Inline css** : `<header style={{ backgroundColor: "red", color: "green" }}>`

- **Variable Type Style**

```js
function Header(props) {
  props.HeaderData("This is Going To Child To Parent");

  const headerStyles = {
    backgroundColor: "blue",
    color: "red",
  };
  return (
    <header style={headerStyles}>
      <div className='container'>
        <h2>{props.text} </h2>
      </div>
    </header>
  );
}
```

- **Props Types Styling**

```js
<Header bgColor='green' textColor='red' />
```

```js
function Header(props) {
  const headerStyles = {
    backgroundColor: props.bgColor,
    color: props.textColor,
  };
  return (
    <header bgColor='red' style={headerStyles}>
      <div className='container'></div>
    </header>
  );
}
```

## State & UseState

- **What is State** :
  - A components data which is varing over the time to handle this type of data need to use state.
  - You can create a state using a specific Hook (useState , useRef , etc..)
- **What is Hook** :

  - A hook is spical function that lets you "Hook into" react features.

- **When would use Hook** :

  - A Componets realize that need to handle state , at that time hook is used

- **Type of state** :
  - Component Level State
    - Specific State which is use only in the specific state (open/close navigation)
  - App Level State
    - which single state is used in multiple components , that is app lavel state
- **Create Hook for State** :

  - **Function Component** :
    - const [name , setName] = hookName();
    - Eg : const [check , setCheck] = useState(true);
