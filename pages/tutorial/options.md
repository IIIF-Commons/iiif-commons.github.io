---
title: Defining Options
sidebar: tutorial_sidebar
permalink: tutorial_options.html
folder: tutorial
---

Now we want to be able to create a drawing canvas, with the additional _options_ to overlay it onto an image or add it as an OpenSeaDragon overlay. Because the setup and the css is slightly different for these scenarios, let's go ahead and add an optional parameter to set the overlay type.

## Create options interfaces

In the `ISvgDrawComponentOptions.ts` file, let's add an `overlayType` parameter:

```js
namespace IIIFComponents{
 export interface ISvgDrawComponentOptions extends _Components.IBaseComponentOptions {
   overlayType?: string; // 'img' or 'osd'
 }
}
```

If no overlay is specified, it will default to a plain old canvas that we can draw on.  We also need to add an `ISvgDrawComponent.ts` interface, which will be blank for the time being:

```
namespace IIIFComponents {
 export interface ISvgDrawComponent extends _Components.IBaseComponent{

 }
}

```

Interfaces are one of the features TypeScript gives us, and they are used to type-check arguments.  In other words, Interfaces make sure that the values we pass are what is expected by the method.  More details can be found in the [Interfaces section of the TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/interfaces.html).

## Define the option upon creation

Finally, we'll have to pass in the option when we create the component instance.  Let's add an `overlayType` property to the config object and give it a value of "img":

```diff
svgdraw = new IIIFComponents.SvgDrawComponent({
    element: "#svgdraw",
+   overlayType: "img" // <-- add this line
});
```

## Set default options
We usually want to provide some default options for our component to cut down on unnecessary configuration for the most common use cases (and avoid dealing with undefined options).  For example, we may expect most people to use svg-draw-component with OpenSeadragon, and don't want them to have to explicitly set it as the overlayType.  

Setting default options is simple. Locate the `_getDefaultOptions` method and add `overlayType: "osd"` as a property.  This allows us to override the defaults via passed in options.

```diff
protected _getDefaultOptions(): ISvgDrawComponentOptions {
    return <ISvgDrawComponentOptions>{
+       overlayType: "osd"
    }
}
```

## Make sure it's working

We can do a quick test to make sure our option is coming through.  Remember the "I am an example component..." message from the boilerplate?  Well, you can do something similar in the `_init()` function by appending the value to the `_$element`:

```
...
    this._$element.append(this.options.overlayType); // <-- add this line to test
    return success
}
```

When you refresh the page, you should see the characters "img" at the top of the document.  If you remove the option from `index.html`, you should see "osd" at the top of the document. Now that we've seen it works, we can remove this line from the `init()` function.
