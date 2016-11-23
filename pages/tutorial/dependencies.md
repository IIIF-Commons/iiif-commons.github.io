---
title: Dependencies
sidebar: tutorial_sidebar
permalink: tutorial_dependencies.html
folder: tutorial
---

We made a conscious effort to allow as much flexibility as possible when creating components.  We don't subscribe to any particular framework, however, many components are built assuming jQuery, jsViews (for templating), and Redux (for state management).  You can include these outside of your "bundled" component as other components will use them and we can cut down on bundling redundant code.

However, for this particular component, we will want to use a third-party library that already handles the complexities of SVG drawing functions.  Why reinvent the wheel?  Let's go ahead and add Paper.js, a vector graphics scripting framework, as a svg-draw-component dependency:

`npm install paper --save`

This will add it to our package.json file, so it will be included whenever we install the component.

Next, we need to update our `gulpfile.config.js`, find the distribution in our node module library, and add the dependency so it gets bundled into our component.

```js

// libs that MUST be included in a consuming app for this component to work

 this.deps = [
 'node_modules/base-component/dist/base-component.bundle.js',
 'node_modules/paper/dist/paper-full.min.js'
 ];

```

(We are using the full, compiled version of paper.js.)

Finally, let's test it out in the examples demo.  If we include the bundled code, and add some paper.js test code in the `<body>` tag of the `index.html` file and refresh the page:

```js
<head>
...
   <script src="js/svg-draw-component.bundle.js"></script>
...
</head>
...
 <script type="text/paperscript" canvas="myCanvas">
     var path = new Path();
     path.strokeColor = 'black';
     var start = new Point(100, 100);
     path.moveTo(start);
     path.lineTo(start + [ 100, -50 ]);
 </script>
 <canvas id="myCanvas" resize></canvas>
...
```

You should see a diagonal line drawn on the screen that looks like this:

![](/assets/paperjs-example.png)
