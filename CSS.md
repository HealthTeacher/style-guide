# CSS

## Misc
- Avoid nesting Sass more than three levels. If you find yourself needing this
  much specificity, take a step back and reconsider your organization or markup.
- Always prepend decimals values with a zero (e.g. – `0.25em`).
- Do not use the [Bourbon position add-on](http://bourbon.io/docs/#position),
  use the standard CSS attributes instead (i.e. – `position`, `top`, `right`,
`bottom` , `left`).

## Order
- Nested selectors should be in the following order:
  1. Element states
  2. Additive classes
  3. Nested child selectors
- Within a Sass selector, declarations should be in the following order:
  1. `@extend`'s
  2. Single line `@import`'s
  3. CSS attributes
  4. Multi line `@imports`'s


#### Example
```scss
.parent {
  @extend %placholder;
  @import transition(background 0.3s linear);
  font-size: 1.5em;

  @import media($medium-up) {
    @include span-columns(6);
  }

  &:hover {
    color: $white;
  }

  &.additive-class {
    background: $red;
  }

  .child {
    border-radius: 0.5em;
  }
}
```

## Class naming conventions
Never references a `js-` prefixed class names from CSS files. `js-` are used
exclusively for JS files.

Use the `is-` prefix for state rules that are shared between CSS and JS.

## Specificity (classes vs ids)
Never use IDs in your CSS, only refer to elements by their class name.

## Animations & Transitions
- All major transitions are initiated in JavaScript, leveraging the
  `jquery.transit.js` plugin to animate CSS properties (like `translateX`
instead of `left`/`right`).
- All hover interactions should rely on CSS. JavaScript should only be used when
  necessary to add a hover class for more complex interactions.
