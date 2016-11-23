---
title: Demo Dependencies
sidebar: tutorial_sidebar
permalink: tutorial_demo-dependencies.html
folder: tutorial
---

Of course, no component repository is complete without a demo.  We often want to show how our component will coexist and interact with other libraries and components.  In this case, I would like to demonstrate how one can use the library to create overlays in OpenSeadragon (OSD).

The first thing we want to do is add an example dependency in `gulpfile.config.js` just underneath where we added our required dependencies (i.e. base-component and paper.js).  We need the entire directory for this one, not just the minified file, so we will create a path to the whole build directory:

```js
// libs that MAY be included in a consuming app but are used here for examples purposes
this.examplesDeps = [
     'node_modules/openseadragon/build/**/*'
];
```

Then we will add the following line to our index.html head:

```
<script src="js/openseadragon/openseadragon.min.js"></script>
```

Now, we just need to add some markup to our example `index.html` to get OSD working in the demo.  Put this in the `<head/>`:

```
<style>
    .openseadragon {
        width: 800px; height: 600px; border: 1px solid black; color: #333; background-color: black;
    }
</style>
```

And put this in the `<body/>`:

```
<div id="osd" class="openseadragon">

  <script type="text/javascript">
    var viewer = OpenSeadragon({
            id: "osd",
            prefixUrl: "/js/openseadragon/images/",
            tileSources: [{
                "@context": "http://iiif.io/api/image/2/context.json",
                "@id": "http://libimages.princeton.edu/loris2/pudl0001%2F4609321%2Fs42%2F00000002.jp2",
                "height": 7200,
                "width": 5093,
                "profile":
                    [ "http://iiif.io/api/image/2/level2.json" ],
                    "protocol": "http://iiif.io/api/image",
                    "tiles": [{ "scaleFactors": [ 1, 2, 4, 8, 16, 32 ],
                    "width": 1024 }]
            }]
        });

    // add our <canvas> element as an OSD overlay...
    var element = document.getElementById('myCanvas');
    var rect = new OpenSeadragon.Rect(0, 0, 1, viewer.viewport.getAspectRatio());

    viewer.addOverlay({
     element: element,
     location: rect
    });

  </script>
```

Reload your demo page, and you should see the overlay \(you may want to make the line color red so it's easier to see\).
