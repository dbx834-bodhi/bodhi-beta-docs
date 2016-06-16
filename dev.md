# Developer Docs

This document intends to serve the following purposes:

* be a Software Requirement Spefification
* list out all features of the application
* be a checklist for what is done and what is not done, and when
* be a semi-technical overview
* be a meeting point between developers and everybody else

## Client application

These set of documents define what the client-side application should be like. It lists out functionality, user interfaces and user interactions.

* The 'Generic App' consists of basic interfaces and functionality. These are listed in [this document](https://bodhi-beta.com/docs/developer/generic-app).
* The 'Bodhi App' is our product, which is built on the 'Generic App'. We plug-and-play various parts of Bodhi App into the generic app. [This document](https://bodhi-beta.com/docs/developer/bodhi-app) lists out these modules and what these modules will do.

## Meteor packages

Meteor is the javascript framework we will use to build our application. A package is a small fragment of code that is responsible for only **one** set of tasks. These set of documents define these packages and what the packages do.

* 'Core Packages' are those that will be cruicial to all parts of the application. [This document](https://bodhi-beta.com/docs/developer/core-modules) lists out these packages and their functionality.
* React is a library that we will use to implement our user interfaces. We will have a set of components that we will use in many places. [This document](https://bodhi-beta.com/docs/developer/core-react-components) describes these re-usable components.
* 'Bodhi Specific Packages' are those that will make our actual application work. These packages will be based on core packages. [This document](https://bodhi-beta.com/docs/developer/bodhi-specific-modules) describes these packages.