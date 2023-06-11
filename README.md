1. Clone this repository.
2. Initialize `npm`:

```sh
npm init -y
```

3. Install WebPack

```sh
npm install webpack webpack-cli --save-dev
```

4. Install style-loader and css-loader.

```sh
npm install --save-dev style-loader css-loader
```

5. install HtmlWebpackPlugin plugin:

```sh
npm install --save-dev html-webpack-plugin
```

6. Install webpack-dev-server:

```sh
npm install --save-dev webpack-dev-server
```

7. Go to the `package.json` file and in the script property replace the following code with its previous value:

```sh
"test": "echo \"Error: no test specified\" && exit 1",
"start": "webpack serve --open",
"build": "webpack"
```

8. Run following command to generate dist directory and its necessary file:

```sh
npm run build
```

9. Run following command to run project on the default browser using webpack-dev-server:

```sh
npm start
```
10. 