---
title: Debugging
sidebar: tutorial_sidebar
permalink: tutorial_debugging.html
folder: tutorial
---

Debugging JavaScript is not always straightforward.  Fortunately, there are a few things you can do to make your life easier when you hit errors or see output you don't expect.  We can start by using some of the developer tools in Google Chrome, although similar tools exist for most other browsers.

## Generating Non-bundled Output files

Minified JavaScript helps us to reduce the size of our code in production, but it's not very helpful in a development environment when we want to set break points on specific lines and inspect the internal workings of our programs.  The first step we will want to take is to move both minified and formatted versions into the examples directory, and while coding, use the formatted version in our demo.  When you use the formatted versions, you will need to include dependencies that might typically get bundled with your minified output.  In the example below, the etch library would typically be bundled with etch-component-test.  However, when using the non-minified version, we need to supply all the libraries separately:

```
<script type="text/javascript" src="js/etch.bundle.js"></script>
<script src="js/etch-component-test.js">
```
