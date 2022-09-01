# Starting Point

## To create you own boiler plate

- start by creating a Directory "Name" to house your project
- create a README and also write the command npm init and git init inside your newly created Directory "Name".
- Dont forget your .gitignore ( keeps you node modules out the way)
- create an src with an index.js file and a public folder to house your index.html and style.css
- Create a components folder with App.js inside.

## Webpack Configuration

- use this command in the terminal : `npm i -D webpack webpack-cli webpack-dev-server`
- by default webpack looks for webpack.config.js so create that in your base path
- Utilize this code by pasting it inside your webpack.config.js

```
module.exports = {
  mode: 'development',
  entry: ['./src/index.js'],
  output: {
    path: __dirname + '/public',
    filename: 'bundle.js',
  },
  context: __dirname,
  devtool: 'source-map',
  devServer: {
    static: {
      directory: __dirname + '/public',
    },
  },
  module: {
   rules: [
    {
       test: /jsx?$/,
       exclude: /node_modules/,
       loader: 'babel-loader',
       options: {
         presets: ['@babel/preset-env', '@babel/preset-react'],
       },
     },
   ],
  },
};
```

## Configuring your HTML file.

(Lets configure your HTML file your created previously in your public folder)

- Us the shortcut " ! " to create a basic html outline.
- then on line 7 make a new line and type in the command " link:css " this will link to your style.css
- Then place "<script type="text/javascript" src="/bundle.js"></script>" this Line of code below your body tag.
- Add a div with the id of "app".

## Babel

- start by installing these packages from babel

* Babel-loader _ @babel/core _ @babel/preset-env \* babel/preset-react

- `npm install --save-dev @babel/core babel-loader @babel/preset-env @babel/preset-react`
- Your babel should already be configured in your webpack.

## Setup scripts package.json

- Inside your scripts section, create a new script that looks like "start": "webpack serve"
- Create "build":"webpack" then run the command `npm run build`. This will build your bundle for you.

# React

- install `npm i react react-dom`

# format Entry Point

```
import React from 'react'
import { createRoot } from 'react-dom/client'
import App from './components/App'

const root = createRoot(document.getElementById('app'))
root.render(<App/>)

```

# Redux Toolkit ( optional for redux )

- `npm i @reduxjs/toolkit react-redux`
- Create a store.js inside your src folder( this will be where you configure the store )

```
import { configureStore } from "@reduxjs/toolkit";

export const store = configureStore({
  reducer: {},
});
```
