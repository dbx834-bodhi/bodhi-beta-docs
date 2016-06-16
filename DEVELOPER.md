# Developer

> this text will be pushed to the right

## Reusable Components
* Grid
* Graphical Builder
* Uploader

### Grid

A client-server table component with the following features:

* Loads data from the server using simple connectors
* Filter columns
* Sortable columns
* Full text search on (selected) columns
* Data import and export

#### Data import

* (Integrates with the Uploader component)
* Drag and drop a CSV or Excel file onto the grid
* Also, the uploader can be opened through a button
* The file is uploaded to S3 file server
* The file is processed
* As the file is being processed, for each line, a record is added and validated against some schema - and the table is updated (This should be reactive)

#### Data export

* Export data as CSV or Excel

### Graphical Builder

Any logic is a combination of multiple processes. Most of these processes can be modelled to some degree. See these examples,

* [Variant HTML builder](http://www.mediumra.re/pangaea/variant/builder.html)
* [Structor](https://github.com/ipselon/structor)

Structor is somewhat complex, but it was shared here to show what is possible. We will take inspiration from the Variant Builder.

This will be a client-server component with the following features:

* A graphical builder with a set of small components (which are defined on the server). We will call these components 'blocks'
* The front-end user can click on a block in the menu and it is added to a designated work section
* Some properties of these blocks can be edited, others can not
* The properties that can be edited should be editable inline (and not in a separate form)
* There will be certain blocks, like image blocks, which will tie-in with the uploader component
* The work section represents a document in a collection (MongoDB) with an identifier and some metadata
* The document will have the form of a list, where each list-item represents a block

### Uploader