## Core Modules/ Packages

* User Accounts
* User Profile
* User Roles
* Collection Schema
* Automatic Form Metadata Generation
* Mailer
* XSLT Engine

### User Accounts

The purpose of this module is to provide basic functions necessary for user accounts.

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
  * A group has name, emails, and optionally a phone number
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

### XSLT Engine

This will be a core module for the whole application and should be worked out very well. The purpose of this module is to provide functions for quick transformations given a JSON document and an XSLT. Read more about XSLT transformations for JSON [here](https://www.w3.org/TR/xslt-30/#json). We will store all our data in the form of JSON documents in MongoDB collections and this is a critical module. This is a module with the following features:

* Given XSLT, convert JSON

Use Cases:

* Exporting Content to Common Cartridge
* Exporting Content to EDUPUB
* Exporting Content to NIMAS/ DAISY
* Exporting Content to POD