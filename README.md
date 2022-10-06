# Text-Editor

## Table of Contents 

<details>
<summary>Table of Contents</summary>

- [Overview](#overview)
  - [Description](#description)
  - [Installation](#installation)
  - [Usage](#usage)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
- [Author](#author)

</details>

## Overview

### Description

Using PWAs to create notes or code snippets with or without an internet connection.

### Installation

Clone repo from Github, run both `npm install` and `npm start` from the root directory. Or watching and using the app has deployed from `https://text-editor-app-6408.herokuapp.com/`.

### Usage

This product has been deployed in `https://text-editor-app-6408.herokuapp.com/`. Users can download the app. It can be installed in any device.

### The challenge

Users should be able to:

- write notes with or without an internet connection.
- install app.
- reopen the editor after closing it, the content has been retrieved.


### Screenshot

![](./assets/images/FireShot%20Capture%20045%20-%20J.A.T.E%20-%201.png)
![](./assets/images/FireShot%20Capture%20046%20-%20J.A.T.E%20-%202.png)

### Links

- Solution URL: [https://github.com/YangLongWang/Text-Editor](https://github.com/YangLongWang/Text-Editor)
- Deployed URL: [https://text-editor-app-6408.herokuapp.com/](https://text-editor-app-6408.herokuapp.com/)

## My process

### Built with

- JavaScript

### What I learned

- using webpack to bundle JavaScript files
- using IndexedDB to save data
- using service worker and manifest

To see how I add code snippets, see below:

```JS
    mode: 'production',
    entry: {
      main: './src/js/index.js',
      install: './src/js/install.js'
    },
    output: {
      filename: '[name].bundle.js',
      path: path.resolve(__dirname, 'dist'),
    },
    plugins: [
      new HtmlWebpackPlugin({
        template: './index.html',
        title: 'Webpack Plugin',
      }),
      new InjectManifest({
        swSrc: './src-sw.js',
        swDest: 'service-worker.js',
      }),
      new WebpackPwaManifest({
        name: 'Just Another Text Editor',
        short_name: 'J.A.T.E',
        description: 'Best text editor!',
        background_color: '#7eb4e2',
        theme_color: '#7eb4e2',
        start_url: './',
        publicPath: './',
        icons: [
          {
            src: path.resolve('src/images/logo.png'),
            sizes: [96, 128, 192, 256, 384, 512],
            destination: path.join('assets', 'icons'),
          },
          {
            src: path.resolve('src/images/logo.png'),
            size: '1024x1024',
            destination: path.join('assets', 'icons'),
            purpose: 'maskable'
          }
        ],
      })
    ],

    module: {
      rules: [
        {
          test: /\.(png|svg|jpg|jpeg|gif|ico)$/i,
          type: 'asset/resource',
        },
        {
          test: /\.css$/i,
          use: ['style-loader', 'css-loader'],
        },
        {
          test: /\.m?js$/,
          exclude: /node_modules/,
          use: {
            loader: 'babel-loader',
            options: {
              presets: [
                ['@babel/preset-env', { targets: "defaults" }]
              ]
            }
          }
        }
      ],
    }
```

## Author

- Github - [Longyang Wang](https://github.com/YangLongWang)
