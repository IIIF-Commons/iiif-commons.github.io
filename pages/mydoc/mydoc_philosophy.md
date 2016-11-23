---
title: Philosophy
tags: [getting_started]
keywords:
summary: "Our thoughts on how to build sustainable, composable UIs."
sidebar: mydoc_sidebar
permalink: mydoc_philosophy.html
folder: mydoc
---

ViewDir carries the dream of interoperability to the development of software itself.  For software to be interoperable, it should adhere to principles that allow for decentralized but coordinated development.  The main objective in our approach is to remove the obstacles to distributed and collaborative UI development.  We do this through transparency, communication, strategic technology decisions, and empathy towards all collaborators.   

### Composability
Composability is a system design principle that deals with the inter-relationships of components. A highly composable system provides components that can be selected and assembled in various combinations to satisfy specific user requirements. In information systems, the essential features that make a component composable are that it be 1) self-contained and 2) stateless.

Composability is good because:

* no lock-in, swap a component out if a better one comes along
* reuse promotes code quality due to many/diverse users
* saves money because things aren't getting developed twice
* code stays small and manageable - easy to on-board
* use whatever framework you like, components are agnostic
* less risk when "buying in" to a particular software stack
* consistent design, adherence to an agreed pattern rather than some unsustainable monolith

### Balancing Flexibility and Simplicity
We are not used to thinking of client-side UIs as being composable systems, but we believe approaching web development in this way will save thousands of hours of effort and exponentially expand what is possible when it comes to the creation of client-side viewers and editors.  The need to share client-side components and patterns is evident as is proven by the popularity of projects from jQuery UI to Bootstrap to React.  

While we take inspiration from such projects, we are wary of lock-in to any particular framework.  As mobile devices become more prevalent we also aim to shrink code bloat at any opportunity.  Our goal is to improve the Developer Experience by striking the right balance between flexibility and simplicity. Viewdir aims to provide default options for software and style libraries, without being overly prescriptive. If you want to use Bootstrap or React, it should be relatively easy to do so. But it should just work (and have consistent design) "right out of the box".

### Component Library, Present and Future
The initial component library contains technology choices that we believe move us towards improved DX and purely composable UIs.  The use of TypeScript, for instance, is a decision that allows us to take advantage of typing, classes, and transpiling ES7.  Components may provide examples for others starting out, but there may be inconsistent approaches due to differing styles or exploring new ideas. For example, you may see components begin to make use of [Cycle.js](https://cycle.js.org/) which would allow us to have both stateless UI, declarative methods, and pure composition; every single Cycle.js app, no matter how complex, is a function that can be reused in a larger Cycle.js app.  This is an instance where it may make sense to adopt a lightweight framework as it gets us closer to our goals without locking us in.

To be clear, Viewdir components need not be tied to any particular technology, but some technology choices make composablity easier than others to implement. Furthermore, using common vocabulary and shared design patterns will reduce friction when collaborating with others.  Finally, we intend to come up with some basic rules around testing and coding style to make it easier for maintainers to merge pull requests. We encourage communication and dialogue around the emerging best practices, so we are [eager to hear your thoughts](https://github.com/viewdir/notes) and move forward together!

{% include links.html %}
