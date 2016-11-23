---
title: Boilerplate and Setup
sidebar: tutorial_sidebar
permalink: tutorial_boilerplate.html
folder: tutorial
---

To start, we are going to replicate the `component-boilerplate` and use it as a starting template for our component. The easiest way to do this is to duplicate a repository without creating a fork.  You can follow [these instructions for duplicating the component-boilerplate project](https://help.github.com/articles/duplicating-a-repository/). Once we have replicated the component and created our own repository, we can run:

```
npm install
gulp
gulp examples
```

Then, if we point our browser to [http://localhost:8080](http://localhost:8080) we should get the javascript alert to ensure that the example demo works. In case you were wondering, this page is located in `examples/index.html` of the component-boilerplate project. This is where changes to your component will be visible while you code.

After that, we replace all instances of "ExampleComponent" with the name of our new component called "SvgDraw", as well as replacing the namespacing from "MyComponents" to "IIIFComponents".  You will generally need to do this in `src/IExampleComponentOptions.ts` and `src/ExampleComponent.ts`, and then rename those files accordingly.  In our case they would change to  `src/ISvgDrawComponentOptions.ts` and `src/SvgDrawComponent.ts`.  Then, update the title and version in your `package.json` as that is used to name your js distribution files.

Finally, we will want to "unbundle" the individual files during development.  This will make it much easier to track down bugs.  To do this, open `examples/index.html` and edit the following lines like this:

```diff
-<script src="js/component-boilerplate.bundle.js"></script>
+<script src="js/base-component.bundle.js"></script>
+<script src="js/svgdraw-component.js"></script>
```

Run `gulp` and `gulp examples` again in your terminal.  If you got no errors, make sure the example demo still works after I've made those changes.
