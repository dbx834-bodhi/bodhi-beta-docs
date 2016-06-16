# Developer Docs

This document intends to serve the following purposes:

* be a Software Requirement Spefification
* list out all features of the application
* be a checklist for what is done and what is not done, and when
* be a semi-technical overview
* be a meeting point between developers and everybody else

After reading this guide, you’ll know about:

1. The features of the client-side Bodhi App, which is an extension of the Generic App
2. The features of various modules

## Client application

These set of documents aim to capture what the client-side application should be like. It aims to list out functionality, user interfaces and user interactions.

* The 'Generic App' consists of basic interfaces and functionality. These are listed in this document. Visit [Generic App Docs](https://bodhi-beta.com/docs/developer/generic-app)
* The 'Bodhi App' is our product, which is built on the 'Generic App'. We plug-and-play various parts of Bodhi App into the generic app. This document aims to list out these parts and what these parts will do. Visit [Bodhi App Docs](https://bodhi-beta.com/docs/developer/bodhi-app)

## Meteor packages

Meteor is the javascript framework we will use to build our application. A package is a small fragment of code that is responsible for only **one** set of tasks. This section aims to define these packages.

* 'Core Packages' are those that will be cruicial to all parts of the application. This document aims to list out these packages, and their functionality. Visit [Core Modules Docs](https://bodhi-beta.com/docs/developer/core-modules)
* React is a library that we will use to implement our user interfaces. We will have a set of components that we will use in many places. Visit [Core React Components Docs](https://bodhi-beta.com/docs/developer/core-react-components)
* 'Bodhi Specific Packages' are those that will make our actual application work. These packages will be based on core packages. Visit [Bodhi Specific Modules Docs](https://bodhi-beta.com/docs/developer/bodhi-specific-modules)