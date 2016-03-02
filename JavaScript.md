# JavaScript
Much of this was taken from [idiomatic-js](https://github.com/necolas/idiomatic-js). Please add to this guide if you find any particular patterns or styles that we've adopted internally. Submit a pull request to ask for feedback (if you're an employee).

## Table of Contents
1. [Naming](#naming)
1. [Syntax](#syntax)
1. [Strings](#strings)
1. [Marionette](#marionette)

## Naming
- Use the `js-` prefix for any `class` or `id` used as a JavaScript hook.
- Use the `qa-` prefix for `class` or `id` used as a testing hook.
- Do *NOT* apply styles to `js-` or `qa-` prefixed classes.

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

- Always use parenthesis and curly brackets for single lines.
  ```coffeescript
  # bad
  vent.trigger 'foo:bar', title: 'Baz'

  # good
  vent.trigger('foo:bar', { title: 'Baz' })
  ```

- Do NOT use parenthesis, curly brackets, or commas for multi-line blocks.
  ```coffeescript
  # bad
  new ItemView({
    id: 'js-item-view',
    className: 'Card Card--sm'
  })

  # good
  new ItemView
    id: 'js-item-view'
    className: 'Card Card--sm'
  ```

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
- Use newlines to group related single-line properties, favoring template/DOM attributes above others
- Each group of related properties should be alphabetized
  ```coffeescript
  # bad
  Marionette.CollectionVew.extend
    itemView: itemView
    itemViewContainer: '#js-itemview-container'
    template: tpl
    ui:
      backBtn: '#js-back'
      submitBtn: '#js-submit'
    method: ->
      console.log 'something'
    className: 'view-edit-classroom'

  # good
  Marionette.CollectionVew.extend
    className: 'view-edit-classroom'
    template: tpl

    itemView: itemView
    itemViewContainer: '#js-itemview-container'

    ui:
      backBtn: '#js-back'
      submitBtn: '#js-submit'

    method: ->
      console.log 'something'
  ```

- Order methods to follow the "lifecycle" of a `View`.
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

- Custom methods should be ordered alphabetically after the "lifecycle" methods
  ```coffeescript
  # bad
  Marionette.ItemView.extend
    myMethod: ->
    doSomething: ->
    zzzmethod: ->
    addItem: ->

  #good
  Marionette.ItemView.extend
    addItem: ->
    doSomething: ->
    myMethod: ->
    zzzmethod: ->
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
