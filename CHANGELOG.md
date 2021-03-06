AutoForm
=========================

AutoForm is a smart package for Meteor that adds handlebars helpers to easily create basic
forms with automatic insert and update events, and automatic reactive validation. 

## Change Log

### 0.4.1

Improve handling of key names that use dot notation to indicate a property of
an object in an array, for example, `friends.0.name`.

### 0.4.0

Backwards-compatibility break! Handling of `Date` fields was limited and saved
`Date` objects were not correct. If you have previously saved `Date` objects
from an autoform `date` input, you will have to manually convert the saved values
to correct them after upgrading to this release. If it is only the date you care
about and not the time, all dates in your mongo collections must represent
midnight in the UTC time zone on the morning of the correct date. Refer to the
[Dates](https://github.com/aldeed/meteor-autoform#dates) section of the README
for details about how date inputs work now.

### 0.3.6

Support min/max functions

### 0.3.5

Add framework override support; current usage is only to specify "none" to skip the bootstrap3 classes

### 0.3.4

Fix object expansion

### 0.3.3

Improve object collapsing. Ensures that the values of keys with dot notation appear in the fields for edit forms.

### 0.3.2

Fix IE<10 errors

### 0.3.1

Fixes to date inputs

### 0.3.0

Updated to work with 0.2.0 versions of collection2 and simple-schema packages. The autoform features should be backwards-compatible, but the collection2 and simple-schema APIs have changed, so you may need to make changes. To make sure everything works as you expect, it's strongly recommended that you include a unique `id` attribute on every `autoForm` helper.

### 0.2.3

* Fix IE<10 issue

### 0.2.2

* Use `submit form` event handler instead of button click handlers
* Add support for binding an `onSubmit` handler to an autoForm using the `onSubmit` helper attribute.
* Don't include `form-control` class on radio buttons and check boxes
* Submit the form normally after validating if none of the special actions are used

### 0.2.1

Fix input helper to use value passed in `value` attribute if no doc is attached to the autoform.

### 0.2.0

* For autoforms that call a server method, server-side validation is no longer performed automatically. This had to be removed to fix a security issue. After updating to 0.2.0, you must call `check()` in the Meteor method.
* Add `formToDoc` and `docToForm` functions. See the readme.
* Improve keyup validation
* Allow direct binding of Collection2 or AutoForm object to autoForm helper through the schema attribute. Passing in the string name of a global object is still supported, but binding is the preferred method now.