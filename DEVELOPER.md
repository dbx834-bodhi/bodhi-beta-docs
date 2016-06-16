# Developer

This document intends to serve the following purposes:
* Software Requirement Spefification
* List out all features of the application
* Be a checklist for what is done and what is not done
* List out all features that we want in the future

## Core Modules/ Packages
* User Accounts
* User Profile
* User Roles
* Collection Schema
* Automatic Form Metadata Generation
* Mailer
* ClientCore

### User Accounts

### User Profile

This module consists of a collection with un-defined schema (i.e, the schema is dynamic). Other modules will build on this module. This module will essentially be a set of APIs to query the collection.

### User Roles

JSON based Access Control. Roles determine what can see what, and do what. This is a module with the following features:

* Roles should be independent of user information
* Each role can perform a number of actions
* Roles should be heirachial
* Roles should be in a JSON file
* There should be a very simple API (because we need ubiquitous role checking throught the application)
  * The API should answer 'CAN ROLE DO TASK' (returning True/False)


### Collection Schema

This will be a core module for the whole application and should be worked out very well. The purpose of this module is to define structure of the data and attach validators and hydrators to it. This is essentially defensive code to check and confirm the structure of data as it goes into a collection. Any collection that will have CRUD operations **must** have schemas attached to it. This is a module with the following features:

* Declare a schema (a JSON object) that defines structure of the data
* Attach validators to fields
  * Validators can be client, server or both
  * Validators can be simple checks
  * Validators can be functions
  * Each validator should have a reasonably descriptive trace message
* Attach hydrators to fields (A hydrator is a function that returns some data, for example return a list of countries in the country dropdown)
  * A hydrator can be static array
  * Or, a function that returns data
  * (The hydrator will be used in the Automatic Form Metadata Generation module)

### Automatic Form Metadata Generation

This will be a core module for the whole application and should be worked out very well. The purpose of this module is to automate many of the Write/Edit operations. This is a module with the following features:

* Whenever a user wants to create something or edit something, this module should generate a JSON object with 'metadata'
* The metadata should be generated based upon the schema attached to the collection
* It should contain validators that have to be run on the client with associated error trace messages
* It should contain hydration data for fields, either from fields (in the case we are modifing a document), or from functions

### Mailer

The purpose of this module is to automate many communication operations. This is a module with the following features:

* Templates
  * Server side default templates
  * Templates use [Foundation for Emails 2](http://foundation.zurb.com/emails/email-templates.html)
  * Each template will have some blocks that are un-alterable (ex. footer and header)
  * Each template will have some blocks that can be edited (ex. custom message)
  * Each template will have some blocks that are auto-generated based on some rules (ex. 5 latest blog entries in 'news' block)
* Groups (Mailing List)
  * Show a list of groups
  * Uses the [Grid component](https://bodhi-beta.com/docs/developer#developer-reusable-components-grid)
  * Each record must have email
  * For each email, check it's health (it exists)
  * Optionally, there can be a phone number too
* Design and Send
  * Uses the [Graphical Builder component](https://bodhi-beta.com/docs/developer#developer-reusable-components-graphical-builder)
  * Preview the mail
    * The preview maybe displayed in a modal
    * The modal will have three tabs to show how the mail will look on a desktop, a tablet and a mobile screen
  * Select who to send the mail to
    * Select one or more groups
    * Add email/s
    * Must have at-least one recepient
    * Send asynchronously
    * Send Email, SMS, or both
  * Send Emails using [SendGrid](https://sendgrid.com/)
  * Send SMS using [Amazon SNS](http://docs.aws.amazon.com/sns/latest/dg/SMSMessages.html)
* Sent mails  - a historical log of sent mails
  * Show a list of sent mails
  * Uses the [Grid component](https://bodhi-beta.com/docs/developer#developer-reusable-components-grid)
  * The log should contain who sent what, and to whom
  * Preview the sent mail
* Future Ideas:
  * Integrate with [WhattsApp](http://whatsmate.github.io/2016-02-17-send-whatsapp-message-nodejs/)

Use cases of this module:

* Support team sends a response to a question
* A teacher communicates with parents of children in his/her class. The parents recieve notification as emails and SMS
* WOH updates could have been done like this (SMS and WhattsApp) if the media team had some brains and their minds were open

## Client Application

The purpose of this section is to define generic functionality, user interface and user interactions that should be in the client app.

* Base
* Sidebar
* Header
* WorkArea
* Accounts

### Base

* Detect if there is no internet and show a blocking message (i.e, user should not be able to do anything)

### Sidebar


### Header


### WorkArea


### Accounts


## Reusable Components
* Grid
* Graphical Builder
* Uploader
* History

### Grid

A table component with the following features:

* Loads data from the server using simple connectors
* Filter columns
* Sortable columns
* Full text search on (selected) columns
* Data import
  * (Integrates with the Uploader component)
  * Drag and drop a CSV or Excel file onto the grid
  * Also, the uploader can be opened through a button
  * The file is uploaded to S3 file server
  * The file is processed
  * As the file is being processed, for each line, a record is added and validated against some schema - and the table is updated (This should be reactive)


### Graphical Builder

Any logic is a combination of multiple processes. Most of these processes can be modelled to some degree. See these examples,

* [Variant HTML builder](http://www.mediumra.re/pangaea/variant/builder.html)
* [Structor](https://github.com/ipselon/structor)

Structor is somewhat complex, but it was shared here to show what is possible. We will take inspiration from the Variant Builder.

This will be a component with the following features:

* A graphical builder with a set of small components (which are defined on the server). We will call these components 'blocks'
* The front-end user can click on a block in the menu and it is added to a designated work section
* Some properties of these blocks can be edited, others can not
* The properties that can be edited should be editable inline (and not in a separate form)
* There will be certain blocks, like image blocks, which will tie-in with the uploader component
* The work section represents a document in a collection (MongoDB) with an identifier and some metadata
* The document will have the form of a list, where each list-item represents a block

### Uploader

The component should have the following features:

* Upload directly to S3
* Show progress
* Setting headers must be configurable. Some files will be public, like images. Other files will be private, and will be accessible by only some users.
* On successful upload, file information should be added to the document we are working on in the collection

Candidates : [react-s3-uploader](https://github.com/odysseyscience/react-s3-uploader)

### History

This is a component that shall have the following features:

* Purpose: "log events for any item"
* Attach a history JSON block to any document in any collection
* When viewing the item, the history block renders as a well-formatted block, in the form of a timeline, of the actions taken
* Show only 5 most recent events, hide the rest. Show 'view complete history' - when user clicks this, show full history
* Each event in history should be in the form of "Who did what, when" (ex. "User1 edited blog-entry-123, 12:30:30 PM")
* Enable limiting history to 'x'.



