---
title: Mixins
sidebar: tutorial_sidebar
permalink: tutorial_mixins.html
folder: tutorial
---

Earlier we added some Paper.js code to our `example/index.html` page, but we really would like that functionality to live in our component.  In order to access the Paper.js functionality we need to appy a mixin.  


Unfortunately, as it turns out, Paper.js uses an architecture that makes everything a global object.  This conflicts with the scoped nature of web components and it will not be possible to use Paper.js as a mixin for this component. This does not mean that we can't use Paper.js as a dependency, but our component will not be self contained and we are forced to make a decision about whether we want to go down that path.  

<div class="heads-up">
<strong>Heads up!</strong>
<p>Some libraries are created using a pattern that conflicts with Viewdir's approach to
component design. When a library creates a global, singleton API, we are not able to create new instances.  This goes against the assumption that we can have multiple instances of web components on a page.  This does not mean that we can't use these libraries.  We just can't include them as Mixins.  More on the singleton pattern can be found in <a href="https://addyosmani.com/resources/essentialjsdesignpatterns/book/#singletonpatternjavascript">Addy Osmani's JavaScript Design Patterns</a>.</p>
</div>

An example of a drawing library that can be included as a Mixin would be Etch.  Here's an [example component that demonstrates how Etch can be used as a mixin](https://github.com/edsilv/etch-component-test).
