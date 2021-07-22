---
layout: post
preview: "Visual Studio Code Configuration"
title: "Visual Studio Code Configuration"
date: 2021-07-16 02:02:21 +0530
author: Sirajudheen Mohamed Ali
categories:
  - "code"
  - "programming"
  - "Visual Studio"
tag: javascript, code
---

Install the important extensions:

Search for "Prettier" and install it.
This extension will help to format your prettier. This is opinionated code formatter.

You can configure and customize this according to your taste.

create a `.prettierrc` file to keep your customizations for this extension.
For example

```json
{
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": false,
  "singleQuote": true
}
```

More configuration can be found at [Prettier Docs](https://prettier.io/docs/en/configuration.html).

Install Live Server:

Search for `Live Server` and install it.

This will help to launch a browser tab with current code loaded. This is extremely useful, if you are developing `JavaScript`.

Once installed, there will be a `Go Live` link on your Code Window, if you click on it, this will launch live server from the current directory on the browser.

Every time you make changes to your code, the server will reload the page on the browser.

You can also install this live-server package using npm. Make sure you have `node.js` installed on your machine by executing `node -v`. Then install using `npm install live-server -g` command to install globally. You can start the server for the current directory, by executing `live-server` on your terminal or command prompt.
