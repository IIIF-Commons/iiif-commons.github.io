---
title: base-component
tags: [components]
keywords: sample
summary: "base-component is designed to underpin any components built to these proposed best practices"
sidebar: components_sidebar
permalink: components_base-component.html
folder: components
---

[https://github.com/viewdir/base-component](https://github.com/viewdir/base-component)

base-component is designed to underpin any components built to these proposed best practices: [https://gist.github.com/edsilv/83221d47fc262230d04fbcdc32dc1d98](https://gist.github.com/edsilv/83221d47fc262230d04fbcdc32dc1d98)

It is also written in TypeScript, but does not require the use of TypeScript by ancestor libraries. It provides a minimal set of bootstrapping functions and a useful `applyMixins` function to allow dynamic mixing-in of other libraries. The [TinyEmitter](https://github.com/scottcorgan/tiny-emitter) library is mixed-in using this method to provide event publishing.


{% include links.html %}
