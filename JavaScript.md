# JavaScript

## Class naming conventions
If a JavaScript hook is needed, prefix the class or ID with `js-` (e.g. – `.js-classroom-name`).

For Layouts and Views, label them with `className` exclusively. Leave `id` for events.

## Group Backbone template properties together
Group properties together logically with one line return between each. Each group should be separated by double line returns. The main group that is used most is as follows:

- `template`, `id`, `className`, `tagName`

Here is a generic example of a typical grouping:

```coffeescript
Marionette.ItemVew.extend
  template: tpl
  className: "view-edit-classroom"

  cancelEl: ".js-cancel"
  submitEl: ".js-submit"
```
