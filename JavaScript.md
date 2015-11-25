# JavaScript
Much of this was taken from [idiomatic-js](https://github.com/necolas/idiomatic-js). Please add to this guide if you find any particular patterns or styles that we've adopted internally. Submit a pull request to ask for feedback (if you're an employee).

## Syntax
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
  $el.on 'click', ->
    $.get(url).then =>
      console.log 'this is never used'
  ```

- Always throw Errors, not strings.
  ```coffeescript
  # bad
  throw 'expected string, got number'

  # good
  throw new TypeError 'expected string, got number'
  ```

## Naming
- Use the `js-` prefix for any `class` or `id` used by JavaScript. Do *NOT* apply styles to these classes.

## Strings
- Use single quoted strings. Only use double quoted strings when interpolation is needed.
  ```coffeescript
  # bad
  name = "Bozhidar"

  # good
  name = 'Bozhidar'
  ```

- Prefer string interpolation instead of string concatenation:
  ```coffeescript
  # bad
  emailWithName = user.name + ' <' + user.email + '>'

  # good
  emailWithName = "#{user.name} <#{user.email}>"
  ```

## Marionette
- Label `View`s with `className` exclusively. Leave `id` for events handlers only.
- Group single-line properties together at the top of the `View`.
  ```coffeescript
  # bad
  Marionette.ItemVew.extend
    template: tpl
    method: ->
      console.log 'something'
    className: 'view-edit-classroom'

  # good
  Marionette.ItemVew.extend
    template: tpl
    className: 'view-edit-classroom'

    method: ->
      console.log 'something'
  ```

- Order methods to follow the "life" of a `View`.
  ```coffeescript
  # bad
  Marionette.ItemView.extend
    onClose: ->
    serializeData: ->
    onRender: ->
    initialize: ->

  #good
  Marionette.ItemView.extend
    initialize: ->
    serializeData: ->
    onRender: ->
    onClose: ->
  ```

- Separate multi-line properties with an empty line.
  ```coffeescript
  # bad
  Marionette.ItemView.extend
    initialize: ->
      console.log 'initialized'
    serializeData: ->
      console.log 'serializeData'

  #good
  Marionette.ItemView.extend
    initialize: ->
      console.log 'initialized'

    serializeData: ->
      console.log 'serializeData'
  ```
