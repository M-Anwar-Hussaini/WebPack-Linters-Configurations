# **WebPack Configurations**

1. create a folder by the name of `src`.
2. inside `src` add at least these files: `index.js`, `index.html` and `style.css`.
3. Run the following command to create `package.json` file:

```sh
npm init -y
```

4. Run following command to install webpack:

```sh
npm install webpack webpack-cli --save-dev
```

5. Search for this line of code in package.json file: `"main": "index.js,"` and replace it with `"private": "true",`.

> **package.json**

```sh
{
  "name": "project-name",
  "version": "x.x.x",
  "description": "",
- "main": "index.js",
+ "private": "true",
  .
  .
  .
}
```

6. Create a file by the name of `webpack.config.js` in the root directory of your project.
7. Search for `"scripts: {...}"` in package.json file and before closing brace `}` append `,"build": "webpack"`.

## Setting up HtmlWebpackPlugin:

1. Run the following command to install **HtmlWebpackPlugin**:

```sh
npm install --save-dev html-webpack-plugin
```

2. Make sure that the `webpack.config.js` file contains following attribute inside of **module.exports** object:

```sh
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  .
  .
  .
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html',
    }),
  ],
  .
  .
  .
};

```

## Loading CSS:

1. Run following command to install **style loader** and **css loader**:

```sh
npm install --save-dev style-loader css-loader
```

2. Make sure that the `webpack.config.js` file contains **module** attribute and its object value in the `module.exports` object.:

```sh
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  .
  .
  .
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
  .
  .
  .
};
```

## Seting up local dev server:

1. Run the following command to install the local dev server:

```sh
npm install --save-dev webpack-dev-server
```

1. Make sure that the `webpack.config.js` file's `module.exports`'s object contains **devServer** and **optimization** attributes.

```sh
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  mode: 'development',
  entry: {
    index: './src/index.js',
  },
  devServer: {
    static: './dist',
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html',
    }),
  ],
  output: {
    filename: '[name].bundle.js',
    path: path.resolve(__dirname, 'dist'),
    clean: true,
  },
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
  optimization: {
    runtimeChunk: 'single',
  },
};
```

3. Update `package.json` file and make sure that the **scripts** property contains the following key/value pairs:

```sh
.
.
.

"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
+ "start": "webpack serve --open",
  "build": "webpack"
},
.
.
.

```

4. Run:

```sh
npm run build
```

5. Run:

```sh
npm start
```
