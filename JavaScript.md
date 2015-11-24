# JavaScript
Much of this was taken from [idiomatic-js](https://github.com/necolas/idiomatic-js). Please add to this guide if you find any particular patterns or styles that we've adopted internally. Submit a pull request to ask for feedback (if you're an employee).

- Always include a space before and after a function arrow.
  ```coffeescript
  # bad
  sum = (a,b)->a + b
  # good
  sum = (a,b) -> a + b
  ```

- No empty parameter lists
  ```coffeescript
  # bad
  foo = () ->

  # good
  foo = ->
  ```

- No unnecessary fat arrows.
  ```coffeescript
  # bad
  $el.on "click", ->
    $.get(url).then =>
      console.log "this is never used"
  ```

- Always throw Errors, not strings.
  ```coffeescript
  # bad
  throw "expected string, got number"

  # good
  throw new TypeError "expected string, got number"
  ```

## Naming
- Use the `js-` prefix for any `class` or `id` used by JavaScript. Do *NOT* apply styles to these classes.

## Backbone
- For Layouts and Views, label them with `className` exclusively. Leave `id` for events handlers only.
- Group related properties together. Groups should be separated by an empty line.
  ```coffeescript
  # bad
  Marionette.ItemVew.extend
    template: tpl
    className: "view-edit-classroom"
    cancelEl: ".js-cancel"
    submitEl: ".js-submit"

  # good
  Marionette.ItemVew.extend
    template: tpl
    className: "view-edit-classroom"

    cancelEl: ".js-cancel"
    submitEl: ".js-submit"
  ```
