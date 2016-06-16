# Developer

> this text will be pushed to the right

## Reusable Components
* Grid
* Graphical Builder

### Grid

A client-server table component with the following properties:

* Loads data from the server using simple connectors
* Filter columns
* Sortable columns
* Full text search on (selected) columns
* Data import and export

#### Data import

* Drag and drop a CSV or Excel file onto the grid
* Also, the uploader can be opened through a button
* The file is uploaded to S3 file server
* The file is processed
* As the file is being processed, for each line, a record is added and validated against some schema - and the table is updated (This should be reactive)

#### Data export

* Export data as CSV or Excel

### Graphical Builder


