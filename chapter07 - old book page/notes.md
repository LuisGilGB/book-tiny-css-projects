# Chapter 7 - Harnessing the full power of float

## About line-height

The `line-height` property can have a value with or without units. Units can be both absolute (`px`, `cm`...) or
relative (`em`, `vw`...), while a value without units affect as a multiplier of the element's text's `font-size`.

`line-height` assigns a reserved height for each line, what ends up meaning the separation between lines. The
design/printing term for this spacing between lines is "leading".

## Text justification and hyphens

Text can be justified to be aligned to both sides of a column, modifying the spacing between words to grant that
alignment effect, something widely adopted in newspapers and magazines. This is done by setting the `text-align`
property to `justify` value.

To prevent too long whitespaces between words, we need hyphens that break the words between lines as they need it. CSS
enables that hyphenation with the `hyphens` property, which can be set to `auto`, `manual` or `none`. With `auto`, the
browser can decide where to place hyphens following the ruleset for the document's language.

```css
p {
  text-align: justify;
  hyphens: auto;
}
```

## Pseudo-classes and pseudo-elements

Pseudo-classes are used to style elements based on their state, like `:hover`, `:focus`, `:active`... Pseudo-elements
are used to style parts of an element, like `::first-letter`, `::first-line`... They allow us to not to add specific
classes or elements in the document's markup for just styling reasons.

For instance, we can select the first letter of the first paragraph of a full article with the concatenation of
the `:first-of-type` pseudo-class and the `::first-letter` pseudo-element:

```css
article p:first-of-type::first-letter {
  font-size: 2em;
  font-weight: bold;
}
```

## The `float` property

The `float` property is used to move an element to the left or right of its container, allowing other elements to wrap
around it. It can be set to `left`, `right` or `none` (default value).
