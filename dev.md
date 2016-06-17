# Introduction

Bodhi is the Next Generation Digital Learning Environment (NGDLE) comprising school information system, lessons planner, assessment engine and an analytical engine. It provides educators and learners an opportunity to save time and effort in achieving desired levels of learning outcomes.The mission envisages best of the breed technologies to attain the required project outcomes. It follows Commercial Open Source Business Model that ensures to reach the market fast, superior product quality, lower operational costs, and sell more easily attracting significantly direct revenue.

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

## SIF Compliance

The Schools Interoperability Framework, or SIF, is a data sharing open specification for academic institutions. Bodhi implements SIF 3.0. [This document](https://bodhi-beta.com/docs/developer/schools-interoperability-framework-compliance) describes this adoption in greater detail.