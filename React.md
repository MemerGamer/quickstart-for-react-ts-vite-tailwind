# Getting started with React and TypeScript

React is a popular JavaScript library for building user interfaces, and TypeScript is a statically typed superset of JavaScript. When combined, React with TypeScript provides a powerful and type-safe development experience for building robust and maintainable web applications. This guide will introduce you to the basics of using React with TypeScript.

## Table of Contents

- [Getting started with React and TypeScript](#getting-started-with-react-and-typescript)
  - [Table of Contents](#table-of-contents)
  - [React Introduction](#react-introduction)
  - [Setting Up a React Project with TypeScript](#setting-up-a-react-project-with-typescript)
  - [Components in React with TypeScript](#components-in-react-with-typescript)
  - [Props and Prop Types](#props-and-prop-types)
  - [State and State Types](#state-and-state-types)
  - [Handling Events](#handling-events)
  - [React Hooks with TypeScript](#react-hooks-with-typescript)
  - [Working with Forms](#working-with-forms)
  - [Type-Safe Context](#type-safe-context)
  - [React Router with TypeScript](#react-router-with-typescript)

## React Introduction

React is a JavaScript library developed by Facebook for building user interfaces. It follows a component-based architecture, where the UI is broken down into reusable components. React allows developers to efficiently update and render components, resulting in fast and responsive web applications.

## Setting Up a React Project with TypeScript

To get started with React and TypeScript, you need to set up a new project. You can use tools like Vite, [Next.js, Remix, Gatsby](https://react.dev/learn/start-a-new-react-project) or manually configure the project.

Here's an example of setting up a new React project with TypeScript using Vite (more info in the [Official docs](https://vitejs.dev/guide/)):

```bash
# npm 6.x
npm create vite@latest my-app --template react-ts

# npm 7+, extra double-dash is needed:
npm create vite@latest my-app -- --template react-ts

cd my-app
npm install
npm run dev
```
This command creates a new React project named `my-app` with TypeScript template and starts the development server.

**Note:** You can also use Create React App (CRA), but it's slowly being [deprecated](https://hackernoon.com/create-react-app-is-dead-here-are-some-alternatives) due to a lack of recent updates.

## Components in React with TypeScript

Components are the building blocks of a React application. In TypeScript, you can define components as functional components or class components. Functional components are simpler and recommended for most use cases.

Here's an example of a functional component in TypeScript:

```tsx
import React from "react";

type GreetingProps = {
  name: string;
};

const Greeting: React.FC<GreetingProps> = ({ name }) => {
  return <h1>Hello, {name}!</h1>;
};

export default Greeting;
```

In the above example, the `Greeting` component accepts a prop `name` of type `string` and renders a greeting message.

## Props and Prop Types

In React with TypeScript, you can define the types of component props to ensure type safety and provide better documentation.

Here's an example of defining prop types for a component:

```tsx
import React from "react";

type GreetingProps = {
  name: string;
  age: number;
};

const Greeting: React.FC<GreetingProps> = ({ name, age }) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>Your age is {age}.</p>
    </div>
  );
};

export default Greeting;
```

In the above example, the `Greeting` component accepts props `name` of type `string` and `age` of type `number`.

## State and State Types

State allows you to manage and update data within a component. In TypeScript, you can define the types for component state to ensure type safety.

Here's an example of managing state with TypeScript:

```tsx
import React, { useState } from "react";

type CounterState = {
  count: number;
};

const Counter: React.FC = () => {
  const [state, setState] = useState<CounterState>({ count: 0 });

  const increment = () => {
    setState((prevState) => ({ count: prevState.count + 1 }));
  };

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;
```

In the above example, the `Counter` component manages state using the `useState` hook. The state is of type `CounterState`, which includes a `count` property of type `number`.

## Handling Events

React with TypeScript allows you to handle events in a type-safe manner. You can define event handler functions with the appropriate event types.

Here's an example of handling events with TypeScript:

```tsx
import React from "react";

type ButtonProps = {
  onClick: (event: React.MouseEvent<HTMLButtonElement>) => void;
};

const Button: React.FC<ButtonProps> = ({ onClick }) => {
  return <button onClick={onClick}>Click me</button>;
};

export default Button;
```

In the above example, the `Button` component accepts an `onClick` prop, which is an event handler function for the `click` event of the button.

## React Hooks with TypeScript

React Hooks provide a way to use state and other React features in functional components. TypeScript allows you to specify the types of hooks and ensure type safety.

Here's an example of using a hook with TypeScript:

```tsx
import React, { useState } from "react";

const Counter: React.FC = () => {
  const [count, setCount] = useState<number>(0);

  const increment = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;
```

In the above example, the `useState` hook is used to manage the `count` state, which is of type `number`.

## Working with Forms

React with TypeScript allows you to handle form inputs and validate their values using types.

Here's an example of working with forms in TypeScript:

```tsx
import React, { useState } from "react";

type LoginForm = {
  email: string;
  password: string;
};

const Login: React.FC = () => {
  const [formData, setFormData] = useState<LoginForm>({
    email: "",
    password: "",
  });

  const handleChange = (event: React.ChangeEvent<HTMLInputElement>) => {
    const { name, value } = event.target;
    setFormData((prevData) => ({ ...prevData, [name]: value }));
  };

  const handleSubmit = (event: React.FormEvent<HTMLFormElement>) => {
    event.preventDefault();
    // Submit form data
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="email"
        name="email"
        value={formData.email}
        onChange={handleChange}
      />
      <input
        type="password"
        name="password"
        value={formData.password}
        onChange={handleChange}
      />
      <button type="submit">Login</button>
    </form>
  );
};

export default Login;
```

In the above example, the `Login` component handles form inputs and stores the form data of type `LoginForm`.

## Type-Safe Context

React Context provides a way to share data between components. With TypeScript, you can ensure type

safety when using context.

Here's an example of using type-safe context in TypeScript:

```tsx
import React, { createContext, useContext } from "react";

type Theme = "light" | "dark";

type ThemeContextValue = {
  theme: Theme;
  setTheme: (theme: Theme) => void;
};

const ThemeContext = createContext<ThemeContextValue | undefined>(undefined);

const ThemeProvider: React.FC = ({ children }) => {
  const [theme, setTheme] = useState<Theme>("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

const Button: React.FC = () => {
  const { theme, setTheme } = useContext(ThemeContext);

  const toggleTheme = () => {
    setTheme(theme === "light" ? "dark" : "light");
  };

  return <button onClick={toggleTheme}>Toggle Theme (Current: {theme})</button>;
};

export default Button;
```

In the above example, the `ThemeContext` is created with a specific context value type. The `ThemeProvider` component provides the context value, and the `Button` component uses the context with type safety.

## React Router with TypeScript

React Router is a library for handling routing in React applications. TypeScript can ensure type safety when working with React Router.

Here's an example of using React Router with TypeScript:

```tsx
import React from "react";
import { BrowserRouter as Router, Route, Link } from "react-router-dom";

const Home: React.FC = () => {
  return <h1>Home Page</h1>;
};

const About: React.FC = () => {
  return <h1>About Page</h1>;
};

const App: React.FC = () => {
  return (
    <Router>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
        </ul>
      </nav>

      <Route path="/" exact component={Home} />
      <Route path="/about" component={About} />
    </Router>
  );
};

export default App;
```

In the above example, the `Router`, `Route`, and `Link` components are used from React Router. TypeScript ensures that the paths and components are correctly typed.
