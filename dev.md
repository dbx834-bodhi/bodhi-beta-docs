# Introduction

Bodhi is the Next Generation Digital Learning Environment (NGDLE) comprising school information system, lessons planner, assessment engine and an analytical engine. It provides educators and learners an opportunity to save time and effort in achieving desired levels of learning outcomes.

# Developer Docs

This document intends to serve the following purposes:

* be a Software Requirement Spefification
* list out all features of the application
* be a checklist for what is done and what is not done, and when
* be a semi-technical overview
* be a meeting point between developers and everybody else

## Code Guide

Guidelines for Bodhi code. The Bodhi App must have consistent code style. [Read the guide](https://bodhi-beta.com/docs/developer/code-guide).

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

## Knowledge base

A very important part of Bodhi will be it's knowledge base. The purpose of having such a support system is to **enable successful implementation and adoption of Bodhi** when an end-user subscribe to Bodhi. The knowledge base can be categorised as, 

* Static knowledge base - guides and tutorials, support articles, introductory articles, frequently-asked-questions, video tutorials, introductory videos, articles about use cases and benefits, etc
* Responsive support - contact us form, ticketing, forums, call support, training, etc

These set of documents define what this knowledge should be like.

> ### References
> [1] A very good model to follow is the [implementation by PowerSchools](http://www.powerschool.com/implementation/). They assign _one person to each subscriber for one year_. Quoted, "An expert PowerSchool 'buddy' will be assigned who will assist during your crucial first year and beyond with PowerSchool"
