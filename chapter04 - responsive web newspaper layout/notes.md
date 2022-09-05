# Chapter 4 - Creating a responsive web newspaper layout

## Importing fonts

Fonts can be imported in a CSS file with the `åimport` rule and the `url()` function:

```css
@import url('https://fonts.googleapis.com/css?family=Roboto:400,700');
```

## `font` shorthand property

The `font` shorthand property takes the following properties in this order:

```
font: font-style font-variant font-weight font-stretch font-size/line-height font-family
```

## Styling block quotes

The `<blockqupte>` element is the element defined in the HTML specs for blocks that contain a quotation. There's an
inline version that is the `<q>` element. Both have a `cite` attribute that is used to point to external sources of
information that add context to the quote. For more complete quotations, it can be used in conjunction with the
`<figure>`, `<figcaption>` and `<cite>` elements.

```html

<figure>
    <blockquote cite="https://www.huxley.net/bnw/four.html">
        <p>
            Words can be like X-rays, if you use them properly—they’ll go through anything. You read and you’re pierced.
        </p>
    </blockquote>
    <figcaption>—Aldous Huxley, <cite>Brave New World</cite></figcaption>
</figure>
```

Quotation marks can be added by CSS with the `::before` and `::after` pseudo-elements by setting the desired `content`
property for each one. Valid `content` values are wither character codes or the `open-quote` and `close-quote` keywords,
which use the open and close quotation mark characters from the document language (different marks are used in English
and in French, for instance). In case we want custom quotation marks that can be references with the said keywords, we
can use the `quotes` property to set them.

```css
blockquote {
  quotes: "«" "»" "“" "”";
}

blockquote::before {
  content: open-quote;
}

blockquote::after {
  content: close-quote;
}
```

## Styling list item bullets

We can use the `list-style-type` property to change the bullet style of a list. Valid values for `list-style-image`
property are disc, circle, square, numbers or letters. `list-style-position` is also available to set if the bullet will
be `inside` or `outside` of the list item element. A shorthand `list-style` property is available to set values for both
properties.

We can also define custom list elements with the `counter-style` at rule. This at rule allows us to define the symbol,
the system and the suffix. Playing with the counting system is what gives this at rule its power and specific use case,
as it tells the browser how to keep track of the list counting system and its relationship with its bullets.

The symbol is set with the `symbols` property. It admits one or more values, which can be a character value or any
custom value placed directly. An example of this are emojis, which have a Unicode value but can also be used directly:

```css
@counter-style my-counter {
  symbols: "\2615";
  symbols: "👍" "👎";
}
```

Unicode values are usually listed with a `U+` prefix, but in CSS that prefix is usually replaced with a backlash (`\`).

The system is set with the `system` property. It can be `cyclic`, `fixed`, `numeric`, `alphabetic`, `symbolic`
or `additive`. The `cyclic` system will repeat the symbols in the order they are defined, being the same symbol used
everywhere if only one is provided.

The suffix is set with the `suffix` property. It stores the string that is used following the bullet symbol (a dot in
case of default ordered lists with bullets such as  `1.`, `c.` or `IV.`).

Custom `counter-style` at rules are given a name that can be referenced in the `list-style-type` property of a list.

```css
@counter-style my-counter {
  system: cyclic;
  symbols: "👍" "👎";
  suffix: " ";
}

ul {
  list-style-type: my-counter;
}
```
