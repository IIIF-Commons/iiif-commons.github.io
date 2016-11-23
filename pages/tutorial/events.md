---
title: Events
sidebar: tutorial_sidebar
permalink: tutorial_event.html
folder: tutorial
---

Often the state of one component will need to change, based on what is happening in other components.  Events are the way components communicate with one another.  In order for Component B to know what's going on with Component A, it listens for events.  

To see events in action, take a look at how the iiif-gallery-component updates its state based on the iiif-tree-component _treeNodeSelected_ event in [this jsbin example](http://jsbin.com/xesare/edit?html,css,output). You can also see the kind of data passed via the svg-draw-component's events flashing on the page as you create and edit shapes in [the demo](https://viewdir.github.io/svg-draw-component/examples/img.html).

However, Component A does not necessarily know how or what to listen to from Component B.  Therefore, every unique combination of components will need its own custom pubsub library that can be used to publish events and register subscribers.  The [BaseCommands definition for the Universal Viewer](https://github.com/UniversalViewer/universalviewer/blob/dev/src/modules/uv-shared-module/BaseCommands.ts) defines all the commands and their associated event identifiers so UV components can listen for these events.

## Tiny PubSub

Currently, the base-component is outfitted with [a fork of the Tiny PubSub](https://github.com/edsilv/jquery-tiny-pubsub) jQuery plugin.  This is [mixed into the the base-component](https://github.com/viewdir/base-component/blob/master/src/BaseComponent.ts#L51) and allows all components that extend the base-component to emit events.
