# Chapter 1: CSS Introduction

## Stylesheet origins and priority

| Type                       | Description                                                                   |
|----------------------------|-------------------------------------------------------------------------------|
| **User-agent stylesheets** | The ones provided by the user's browser and operating system.                 |
| **Author stylesheets**     | The ones provided by the author of the document.                              |
| **User stylesheets**       | The ones set by the user by use of tools such as browser settings or plugins. |

User stylesheets have the highest priority and user-agent stylesheets have the lowest one. Among multiple author
stylesheets, the last ones to be imported have higher priority than the ones imported before.

To reduce browser and OS impact, author stylesheets that reset or normalize the user-agent stylesheets rules can be
imported.

## Specificity

Elements can inherit properties from parent elements when those properties can be inherited (like text color or font
family), but other properties must be applied to the element itself. Inherited properties are overridden by the element
properties.

When there are multiple rules for the same property at the same element, the rule that is finally applied is the one
with highest specificity. This specificity is calculated by adding the values of the selectors of that rule (being the
last one to be imported the winner in case of a tie). The values of each kind of selector are:

| Type               | Value | Description                                                                     |
|--------------------|-------|---------------------------------------------------------------------------------|
| Universal selector | 0     | Selects every element                                                           |
| Type selector      | 1     | Type of HTML element (div, h1, article, img...)                                 |
| Attribute selector | 10    | Classes and other HTML attributes such as name, data-, etc., and pseudo-classes |
| Id selector        | 100   | HTML ids                                                                        |

## !important

`!important` is a CSS property that can be used to override the rules of a stylesheet. In case of multiple `!important`
rules are found, the style will be resolved with the usual priority algorithm among all the rules with `!important`.

Its use is not recommended.

## Combinators

Combinators allow us to select elements by using selectors of other elements related to it such as parents and siblings.

| Character | Type of combinator          |
|-----------|-----------------------------|
| `space`   | Descendant combinator       |
| `>`       | Child combinator            |
| `+`       | Adjacent sibling combinator |
| `~`       | General sibling combinator  |

## Pseudo-classes

Pseudo-classes are used to select elements based on their state or characteristics. To express pseudo-classes, we use
the `:` character followed by the name of the pseudo-class.

- `:link`: Selects links that are not currently being visited.
- `:visited`: Selects links that have been visited.
- `:hover`: Selects elements that have the cursor over them.
- `:active`: Selects elements that are being pressed (click/press still not released).
- `:focus`: Selects elements that are focused. This means the one that will receive the keyboard events.
- `focus-within`: Selects elements that are parent of the currently focused element.
- `focus-visible`: Selects focused elements when that focused state has been gained with interaction through keyboard.
- `:target`: Selects the element which has the id that matches the URL current fragment (being this notes
  on www.link.com/profile#notes).

## Pseudo-elements

Pseudo-elements are used to select specific parts of an element. To express pseudo-elements, we use the `::` character.

## Attribute selectors

Attribute selectors are used to select elements based on their attributes. To express attribute selectors, we use the
`[` character followed by the name of the attribute and the value of the attribute.

```css
[href="https://www.link.com"]:link {
  color: red;
}
```

## Universal selector

The `*` selector selects all elements.

## Namespaces

We can declare namespaces in HTML using `xmlns` attribute.

```html

<svg xmlns="http://www.w3.org/2000/svg">
    <!--SVG Code-->
</svg>
```

Namespaces are used to distinguish between different kinds of elements such as HTML, SVG or MathML.

In CSS, namespaces are declared with `@namespace` rule. The value of the rule is the name of the namespace and the value
of the attribute is the URL of the namespace.

```css
@namespace svg "http://www.w3.org/2000/svg";
@namespace xlink "http://www.w3.org/1999/xlink";
```

Namespaces can be used to limit the spread of a universal selector to those elements within a given namespace with
the `|` operator:

- `*|*`: Selects all elements regardless of its namespace (same as just `*`).
- `ns|*`: Selects all elements within the `ns` namespace.
- `|*`: Selects all elements without any defined namespace.

```css
svg|* {
  fill: #EDEDED;
}
```

Namespaces can also be used to target specific elements with the `|` operator:

```css
svg|circle {
  fill: #EDEDED;
}
```

## Shorthand properties

Shorthand properties are properties that can be expressed in a single rule. Examples are `margin`, `padding`
and `border`. They not only allow us to reduce the verbosity of the rules, but can also be more performant in case we
want to apply the same value multiple times.

`padding` is a shorthand property that can apply the same value to `paddingTop`, `paddingRight`, `paddingBottom`
and `paddingLeft`. I can accept from 1 to 4 values:

| Rule                       | Effect                                                                                                                                  |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| `padding: 1px`             | applies the same value to all sides.                                                                                                    |
| `padding: 1px 2px`         | applies 1 px to vertical paddings (`paddingTop` and `paddingBottom`) and 2px to horizontal paddings (`paddingRight` and `paddingLeft`). |
| `padding: 1px 2px 3px`     | applies 1 px to `paddingTop`, 2px to horizontal paddings (`paddingRight` and `paddingLeft`) and 3px to `paddingBottom`.                 |
| `padding: 1px 2px 3px 4px` | applies 1 px to `paddingTop`, 2px to `paddingRight`, 3px to `paddingBottom` and 4px to `paddingLeft`.                                   |

Notice the usual order of the values: `top`, `right`, `bottom` and `left`.
