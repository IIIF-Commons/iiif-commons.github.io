---
title: Mounting on the DOM
sidebar: tutorial_sidebar
permalink: tutorial_mounting-to-the-dom.html
folder: tutorial
---

The base-component provides an "element" option that allows us to mount our component on the DOM.

We are going to then append the canvas into the component element specified by the element option.  Since we don't want any external scripts to be able to manipulate the canvas, let's add it as a private member.  We can also explicitly make the options public even though `public` is the Typescript default.

```
public options: ISvgDrawComponentOptions;
private _$canvas: JQuery;
```

Then, in the `_init` method we can replace the `this._$element.append("I am an example component");` line with the canvas element we want to add to the page:

```
this._$canvas = $('<canvas id="paper"></canvas>');
this._$element.append(this._$canvas);
```

As we can see from the code above, our component will be adding a canvas to the document. It would be convenient for us to obtain the dimensions of the canvas from the default element, so let's bind it to a &lt;div&gt;, allowing us to work easily with a simple canvas, a basic image overlay, or OpenSeadragon overlay canvases.

In the `examples/index.html` page, let's change the `<div id="component"></div>` to `<div id="svgdraw"></div>` and make sure we are binding the \#svgdraw element by changing the new instance to this:

```

var svgdraw;

svgdraw = new IIIFComponents.SvgDrawComponent({

 element: "#svgdraw"

});

```

## Adding some Paper.js drawing tools

Because Paper.js is bundled into our component as a dependent, we should be able to add the following code just below where we declare our `svgdraw` variable.  This will add three drawing tools that we can use to draw on the canvas.:

```js

paper.install(window);
var tool1, tool2, tool3;

 window.onload = function() {
   // Get a reference to the canvas object
   var canvas = document.getElementById('canvas-1');

   // Create an empty project and a view for the canvas:
   paper.setup(canvas);

   // Both share the mouseDown event:
   var path;
   var rectangle = null;

   function onMouseDown(event) {
    path = new Path();
    path.strokeColor = 'red';
    path.add(event.point); }

   ////// S T R A I G H T L I N E S ////////
   tool1 = new Tool(); tool1.onMouseDown = onMouseDown;

   tool1.onMouseDrag = function(event) {
     path.add(event.point); }

   ////// C L O U D Y L I N E S /////////
   tool2 = new Tool();
   tool2.minDistance = 20;
   tool2.onMouseDown = onMouseDown;

   tool2.onMouseDrag = function(event) {
       // Use the arcTo command to draw cloudy lines
       path.arcTo(event.point); }

   ////// R E C T A N G L E /////////
   tool3 = new Tool();
   tool3.onMouseDrag = function(event) {
       if (rectangle) {
           rectangle.remove(); }
       drawRect(event.downPoint, event.point); }

   function drawRect(start, end) {
       rectangle = new Path.Rectangle(start, end);
       rectangle.strokeColor = 'red'; } };

```

Add the following HTML to your index.html:

```
 <a href="#" onclick="tool1.activate();">Lines</a> |
 <a href="#" onclick="tool2.activate();">Clouds</a> |
 <a href="#" onclick="tool3.activate();">Rect</a>
```

This should give you something like what you see in [this demo](http://sdellis.com/svg-draw-component/examples/default.html).  Ultimately, we will want to move this code into the component itself, but we will not be able to use the Paper.js functionality until we do a little more setup in our component.  We will explore how to do this later when we talk about [Mixins](/mixins.md).
