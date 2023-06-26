# Getting Started with ViteJS

ViteJS is a next-generation development build tool that offers a highly optimized and lightning-fast development experience for modern web applications. It focuses on instant server startup, fast hot module replacement (HMR), and quick builds. This guide will walk you through the basics of getting started with ViteJS and help you set up your first project.

## Table of Contents

- [Getting Started with ViteJS](#getting-started-with-vitejs)
  - [Table of Contents](#table-of-contents)
  - [Pre-requisites](#pre-requisites)
  - [Creating a New Project](#creating-a-new-project)
  - [Development Server](#development-server)
  - [Building for Production](#building-for-production)
  - [Using Plugins](#using-plugins)
  - [Adding Frameworks](#adding-frameworks)
  - [Conclusion](#conclusion)

## Pre-requisites

To get started with ViteJS, make sure you have Node.js installed on your machine. You can check if Node.js is installed by running the following command in your terminal:

```bash
node -v
```

If Node.js is not installed, you can download and install it from the official Node.js website (https://nodejs.org).

## Creating a New Project

To create a new Vite project, you can use the `create-vite` command-line utility. This utility is included with the Vite package, so you can run it using the `npx` command:

```bash
npm create vite@latest my-project --template <template-name>
```

Replace `<template-name>` with the desired template you want to use.Vite will automatically scaffold a basic project structure for you.

Supported templates include:

| JavaScript | TypeScript |
| ---------- | ---------- |
| vanilla    | vanilla-ts |
| vue        | vue-ts     |
| react      | react-ts   |
| preact     | preact-ts  |
| lit        | lit-ts     |
| svelte     | svelte-ts  |

Navigate into the project directory:

```bash
cd my-project
```

## Development Server

Vite comes with a built-in development server that provides fast, hot module replacement (HMR) for a seamless development experience. To start the development server, run the following command:

```bash
npm run dev
```

This will start the development server and open your project in the default browser. Any changes you make to your code will be instantly reflected in the browser without a full page reload.

## Building for Production

When you're ready to build your Vite project for production, you can use the following command:

```bash
npm run build
```

This command will generate an optimized production-ready build of your project.

## Using Plugins

Vite supports various plugins that can extend its functionality and integrate with different tools and frameworks. You can add plugins to your Vite project by installing them as dependencies and configuring them in the `vite.config.js` file.

For example, to add the TypeScript plugin, you can run the following command:

```bash
npm install --save-dev vite-plugin-typescript
```

Then, update your `vite.config.js` file to include the plugin:

```javascript
import { defineConfig } from "vite";
import ts from "vite-plugin-typescript";

export default defineConfig({
  plugins: [ts()],
});
```

## Adding Frameworks

Vite works seamlessly with popular JavaScript frameworks and libraries, such as React, Vue.js, and Preact. You can create a new Vite project with a specific framework template by specifying it during project creation.

For example, to create a Vite project with the React template, you can run the following command:

```bash
npm create vite@latest my-react-project --template react
```

This will set up a new Vite project pre-configured with React.

## Conclusion

ViteJS provides an optimized and efficient development experience for modern web applications. Its fast startup time, hot module replacement, and quick build process make

it an excellent choice for building high-performance projects. This guide covered the basics of getting started with ViteJS, including installation, project creation, using the development server, building for production, using plugins, and adding frameworks. With ViteJS, you can streamline your web development workflow and create fast, modern web applications with ease.
