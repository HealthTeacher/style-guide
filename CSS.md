# CSS

## Naming
- Adhere to the [SuitCSS naming conventions](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md).

## Coding Style
- Within a selector, declarations should be in the following order:
  1. `@extend`'s
  2. Single line `@import`'s
  3. CSS attributes
  4. Multi line `@imports`'s

  ```scss
  // bad
  .Component {
    @import transition(background 0.3s linear);
    @extend $placeholder;

    @import media($medium-up) {
      @include span-columns(6);
    }

    font-size: 1.5rem;
  }

  // good
  .Component {
    @extend %placholder;
    @import transition(background 0.3s linear);
    font-size: 1.5rem;

    @import media($medium-up) {
      @include span-columns(6);
    }
  }
  ```
- Only use nested selectors for browser states (e.g. – `hover`, `focus`, etc).
  ```scss
  // bad
  .Component {
    &.is-expanded {}

    .Component-child {}
  }

  // good
  .Component {
    &:hover {}
  }

  .Component.is-expanded {}

  .Component-child {}
  ```
- Never apply styles to a `js-` prefixed class name.
- Never target an element by it's `id`, always use `class` names.
- Avoid using JavaScript for simple hover interactions. Rely solely on CSS when possible.
- Use the [Velocity.js](http://julian.com/research/velocity/) for complex animations.
- Always prepend decimals values with a zero.
  ```scss
  // bad
  font-size: .25rem;

  // good
  font-size: 0.25rem;
  ```

- Do _not_ use the [Bourbon position add-on](http://bourbon.io/docs/#position), use the CSS attributes instead (i.e. – `position`, `top`, `right`, `bottom` , `left`).
