## Generic App

The purpose of this section is to define generic functionality, user interface and user interactions that should be in the client app. We will use the beautiful [Metronic App Template](http://keenthemes.com/preview/metronic/theme/admin_1_rounded/) as inspiration and reference for user interface elements. Please note that we don't have to copy everything. Metronic does many things well and is a good place to learn. The client application will have these generic modules:

* Base
* Sidebar
* Header
* WorkArea
* Accounts

### Base

The purpose of this module is to define generic behind-the scenes functionality of the app. This is a module with the following features:

* Detect if there is no internet and show a blocking message (i.e, user should not be able to do anything)

### Sidebar

The purpose of this module is to define user interface for the sidebar of the app. This is a module with the following features:

* The sidebar should be docked on the left
* It should somewhat be like the sidebar in [Metronic App Template](http://keenthemes.com/preview/metronic/theme/admin_1_rounded/) but more traditional
* It should be fixed (Try 'fixing' the sidebar in the template in the settings menu)
* The sidebar should be scrollable in and of itself - reaching bottom of the sidebar should not change anything in the UI anywhere else. See the sidebar in [Asana App](https://app.asana.com/)
* The sidebar should have links to everything one can do
* The links should be presented in dropdown-style menus with contextual headings

### Header

* The header should be fixed

### Accounts

* Log out
* View profile
* Update profile

### WorkArea

* The workarea is the remaining space (white space in the image below)

![Bodhi Core](https://bodhi-beta.com/assets-docs/img/app_core.png "Bodhi Core")