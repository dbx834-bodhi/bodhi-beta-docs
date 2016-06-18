# Core Packages

## User Packages

* User Accounts
* User Profile
* User Roles

### User Accounts

The purpose of this package is to provide basic functions necessary for user accounts.

### User Profile

This package consists of a collection with un-defined schema (i.e, the schema is dynamic). Other packages will build on this package. This package will essentially be a set of APIs to query the collection.

### User Roles

JSON based Access Control. Roles determine what can see what, and do what. This is a package with the following features:

* Roles should be independent of user information
* Each role can perform a number of actions
* Roles should be heirachial
* Roles should be in a JSON file
* There should be a very simple API (because we need ubiquitous role checking throught the application)
  * The API should answer 'CAN ROLE DO TASK' (returning True/False)

## Collection Packages

* Collection Schema
* Collection Helpers
* Collection Filters
* Collection Timestamps

### Collection Schema

This will be a core module for the whole application and should be worked out very well. The purpose of this package is to define structure of the data and attach validators and hydrators to it. This is essentially defensive code to check and confirm the structure of data as it goes into a collection. Any collection that will have CRUD operations **must** have schemas attached to it. This is a package with the following features:

* Declare a schema (a JSON object) that defines structure of the data
* Attach validators to fields
  * Validators can be client, server or both
  * Validators can be simple checks
  * Validators can be functions
  * Each validator should have a reasonably descriptive trace message
* Attach hydrators to fields (A hydrator is a function that returns some data, for example return a list of countries in the country dropdown)
  * A hydrator can be static array
  * Or, a function that returns data
  * (The hydrator will be used in the Automatic Form Metadata Generation package)

### Collection Helpers

The purpose of this package is to create helper functions that create transformations on the data. This is a package with the following features:

* Define transformation functions on the collection
* These functions may have any kind of logic
* They can be called on the client or on the server

### Collection Filters

https://atmospherejs.com/doctorpangloss/filter-collections

### Collection Timestamps

https://atmospherejs.com/zimme/collection-timestampable

## Form/Data Handling Packages

* Automatic Form Metadata Generation
* Autocomplete
* Validator

### Automatic Form Metadata Generation

This will be a core package for the whole application and should be worked out very well. The purpose of this package is to automate many of the Write/Edit operations. This is a package with the following features:

* Whenever a user wants to create something or edit something, this package should generate a JSON object with 'metadata'
* The metadata should be generated based upon the schema attached to the collection
* It should contain validators that have to be run on the client with associated error trace messages
* It should contain hydration data for fields, either from fields (in the case we are modifing a document), or from functions

### Autocomplete

The purpose of this package is to enable attaching an autocompelter with any input, and linking it to a server hydration source. This is a package with the following features:

* Attach auto-complete to an input
* Fetch data from the server
* Update suggestions as the user types

### Validator

https://www.npmjs.com/package/validator

## Communications Packages

* Mailer
* Mail Scheduler

### Mailer

The purpose of this package is to automate many communication operations. This is a package with the following features:

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

Use cases of this package:

* Support team sends a response to a question
* A teacher communicates with parents of children in his/her class. The parents recieve notification as emails and SMS
* WOH updates could have been done like this (SMS and WhattsApp) if the media team had some brains and their minds were open

**[Mailer API](https://bodhi-beta.com/docs/developer/core-packages/api/mailer)**

### Mail Scheduler

* Schedule mails in the future

## Reporting Packages

* Charts
* PDF Generator

### Charts

Reusable charts

https://www.npmjs.com/package/d3.chart

### PDF Generator

## Other Packages

* XSLT Engine
* Scheduled Tasks
* AWS API
* Method Hooks
* Loading
* Numeral Formatter
* Date Formatter
* Logging
* XML DOM Parser
* Create ZIP
* XML Builder
* CSV Parser
* XML to JSON
* Keypress Event Binder
* Filesize
* Image toolkit
* HTML Encoder
* WalkDir
* CamelCase
* UnCamelCase
* Sanitise Filenames
* HTML Generation on the Server
* Random

### XSLT Engine

This will be a core package for the whole application and should be worked out very well. The purpose of this package is to provide functions for quick transformations given a XSLT. Read more about XSLT transformations for JSON [here](https://www.w3.org/TR/xslt-30/#json). We will store all our data in the form of JSON documents in MongoDB collections and this is a critical package. This is a package with the following features:

* Given XSLT, convert JSON

Use Cases:

* Exporting Content to Common Cartridge
* Exporting Content to EDUPUB
* Exporting Content to NIMAS/ DAISY
* Exporting Content to POD

### Scheduled Tasks

The purpose of this package is to create cron jobs that run at a particular time. This is a package with the following features:

* Define a job on the server
* Run the job automatically

https://www.npmjs.com/package/cron

### AWS API

We will not store _any_ data locally (where the application is installed), rather we will use S3 File server for storing files. This is a standard AWS API implementation.

https://www.npmjs.com/package/aws-sdk

### Method Hooks

The purpose of this package is to attach hooks on any function and do something _before_ or _after_ that function. Note, that this only server-side. This is a package with the following features:

* The 'before function' can block execution

https://atmospherejs.com/doctorpangloss/method-hooks

### Loading

Show a loading screen on first load as the user waits.

https://atmospherejs.com/pcel/loading

### Numeral Formatter

https://atmospherejs.com/numeral/numeral
http://numeraljs.com/

### Date Formatter

https://www.npmjs.com/package/moment
http://momentjs.com/docs/

### Logging

https://www.npmjs.com/package/winston

### XML DOM Parser

https://www.npmjs.com/package/xmldom

### Create ZIP

https://www.npmjs.com/package/archiver

https://www.npmjs.com/package/decompress-zip

### XML Builder

https://www.npmjs.com/package/xmlbuilder

### CSV Parser

https://www.npmjs.com/package/csv

### XML to JSON

https://www.npmjs.com/package/xml2json

### Keypress Event Binder

https://www.npmjs.com/package/keypress

### Filesize

https://www.npmjs.com/package/filesize

### Image Toolkit

https://www.npmjs.com/package/imagemagick
https://github.com/aheckmann/gm

### Redux Logger

https://www.npmjs.com/package/redux-logger

### HTML Encoder

https://www.npmjs.com/package/he

### Walk Dir

https://www.npmjs.com/package/walkdir

### CamelCase

https://www.npmjs.com/package/camelcase

### UnCamelCase

https://github.com/sindresorhus/decamelize

### Sanitize Filenames

https://www.npmjs.com/package/sanitize-filename

### HTML Generation on the Server

https://github.com/cheeriojs/cheerio

### Random

https://atmospherejs.com/meteor/random