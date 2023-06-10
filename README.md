# **WebPack Configurations**

1. create a folder by the name of `src`.
2. insdie `src` add at least these files: `index.js`, `index.html` and `style.css`.
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

1. Run following command:

```sh
npx webpack
```

7. Create a file by the name of `webpack.config.js` in the root directory of your project.
8. Search for `"scripts: {...}"` in package.json file and befor closing brace `}` append `,"build": "webpack"`.
9. Run following command:

```sh
npm run build
```

## Setting up HtmlWebpackPlugin:

1. Run the following command:

```sh
npm install --save-dev html-webpack-plugin
```

2. copy following code to the `webpack.config.js` file:

```sh
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: {
    index: './src/index.js',
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
};

```

3. Run following command:

```sh
npm run build
```

## Loading CSS:

1. Run following command to install **style loader** and **css loader**:

```sh
npm install --save-dev style-loader css-loader
```

2. Upadate the `webpack.config.js` file to have module attribute and its object value.:

```sh
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: {
    index: './src/index.js',
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
};
```

3. Run following command:

```sh
npm run build
```

## Seting up local dev server:

1. Run the following command to install the local dev server:

```sh
npm install --save-dev webpack-dev-server
```

2. Update the `webpack.config.js` file and make sure it contains the **devServer** and **optimization** attributes.

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
"start": "webpack serve --open",
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
