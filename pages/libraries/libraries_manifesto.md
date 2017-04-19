---
title: Manifesto
tags: [libraries]
keywords: manifesto
summary: "Manifesto is an isomorphic node.js library designed to make working with IIIF Presentation API manifests easy on the client and server side."
sidebar: libraries_sidebar
permalink: libraries_manifesto.html
folder: libraries
---

https://github.com/viewdir/manifesto

Manifesto is an isomorphic node.js library designed to make working with IIIF Presentation API manifests easy on the client and server side. The current feature set includes:

- Loading and parsing manifests into a convenient object model
- IIIF Auth API implementation
- ‘IxIF’ support for non image-based resources (not currently a recommended specification)
- Tree hierarchy generation from ranges
- Localisation support
- Lazy loading of sub manifests/collections

Possible future features to be added by community:

- Setter functions to allow building manifests programmatically
- Serialisation of the object model back to JSON-LD

Manifesto is written in TypeScript which allows static typing. This makes it easy to catch coding errors at compile time and makes the project very resilient to refactors. There is also a well maintained mocha test suite.

[Documentation](http://viewdir.github.io/manifesto/)

[Tutorial](http://blog.edsilv.com/manifesto/)

{% include links.html %}
