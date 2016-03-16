# HTML
Much of this was inspired by [idiomatic-html](https://github.com/necolas/idiomatic-html). Please add to this guide if you find any particular patterns or styles that we've adopted internally. Submit a pull request to ask for feedback (if you're an employee).

## Table of Contents
1. [General principles](#general-principles)
1. [Whitespace](#whitespace)
1. [Format](#format)
1. [Attribute order](#attribute-order)
1. [Naming](#naming)
1. [Practical example](#practical-example)


## General principles
- All code in any code-base should look like a single person typed it, no
  matter how many people contributed.
- Strictly enforce the agreed upon style.
- If in doubt when deciding upon a style, use existing, common patterns.


## Whitespace
Only one style should exist across the entire source of your code-base. Always
be consistent in your use of whitespace. Use whitespace to improve
readability.

- Never mix spaces and tabs for indentation.
- Use soft indents (spaces) NOT real tabs.
- Use 2 spaces for indents.

*Tip: configure your editor to "show invisibles". This will allow you to eliminate end of line
whitespace, eliminate unintended blank line whitespace, and avoid polluting commits.*


## Format
- Keep line-length to 100 columns or fewer.
- Always use lowercase tag and attribute names.
- Write one discrete element per line.
- Use one additional level of indentation for each nested element.
- Use valueless boolean attributes (e.g. `checked` rather than
  `checked="checked"`).
- Always use double quotes to quote attribute values.
- Omit the `type` attributes from `link` stylesheet, `style` and `script`
  elements.
- Always include closing tags.
- Don't include a trailing slash in self-closing elements.

Example:

```html
<div class="Tweet">
  <a href="path/to/somewhere">
    <img src="path/to/image.png" alt="">
  </a>
  <p>[tweet text]</p>
  <button disabled>Reply</button>
</div>
```

### Exceptions and slight deviations

Elements with multiple attributes can have attributes arranged across multiple lines in an effort to
improve readability and produce more useful diffs.

Example:

```html
<a class="[value]"
  data-action="[value]"
  data-id="[value]"
  href="[url]">
  <span>[text]</span>
</a>
```


## Attribute order
HTML attributes should be listed in an order that reflects the fact that class names are the primary
interface through which CSS selects elements.

1. `class`
2. `id`
3. `data-*`
4. Everything else

Example:
````html
<a class="[value]" id="[value]" data-name="[value]" href="[url]">[text]</a>
````


## Naming
Naming is hard, but very important. It's a crucial part of the process of
developing a maintainable code base, and ensuring that you have a relatively
scalable interface between your HTML and CSS/JS.

- Use clear, thoughtful, and appropriate names for HTML classes. The names
  should be informative both within HTML and CSS files.
- Avoid _systematic_ use of abbreviated class names. Don't make things
  difficult to understand.

Example with bad names:

```html
<div class="cb s-scr"></div>
```

```css
.cb {
  background: #000;
}

.s-scr {
  overflow: auto;
}
```

Example with better names:
```html
<div class="ColumnBody u-isScrollable"></div>
```

```css
.ColumnBody {
  background: #000;
}

.u-isScrollable {
  overflow: auto;
}
```


## Practical example
An example of various conventions.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Document</title>
    <link rel="stylesheet" href="main.css">
    <script src="main.js"></script>
  </head>
  <body>
    <article class="Post" id="1234">
      <time class="Timestamp">March 15, 2012</time>
      <a data-id="1234"
        data-analytics-category="[value]"
        data-analytics-action="[value]"
        href="[url]">[text]</a>
      <ul>
        <li>
          <a href="[url]">[text]</a>
          <img src="[url]" alt="[text]">
        </li>
        <li>
          <a href="[url]">[text]</a>
        </li>
      </ul>

      <a class="LinkComplex" href="[url]">
        <span class="LinkComplex-target">[text]</span>
        [text]
      </a>

      <input value="text" readonly>
    </article>
  </body>
</html>
```
