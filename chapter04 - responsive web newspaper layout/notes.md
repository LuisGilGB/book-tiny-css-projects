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
