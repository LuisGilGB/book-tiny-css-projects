# Chapter 8 - Designing a checkout cart

## Displaying numbers: `font-variant-numeric`

Number figures have two ways to be vertically aligned: **old style** and **modern**. Old style figures may have some
portions exceeding the meanline and the baseline, while modern figures are completely enclosed between both, what makes
them more suitable for tabular and structured design. We can set which of both to use with the `font-variant-numeric`
property and its `oldstyle-nums` and `lining-nums` values.

The `font-variant-numeric` can also be used to display other types of numbers such as ordinal numbers or fractions or to
set whether zeroes are displayed with a slash or not.

## Outlines

Outlines are a way to add a border to an element without affecting its dimensions (so neither affects the document's
layout). They are useful to add a visual cue to an element on events such as focus of hover, so the `outline` property
can be usually found in rules for selectors with the `:focus` and `:hover` pseudo-classes.

The `outline-offset` property can be used to add some space between the outline and the element's border. This offset
can be negative, so the outline can be drawn inside the element's border.

```css
button:focus {
  outline: solid 1px red;
  outline-offset: 2px;
}
```

## The `:nth-of-type()` pseudo-class

The `:nth-of-type()` pseudo-class can be used to select elements based on their position in the list of siblings of the
parent element. It can be used to select every even or odd element, or to select the specific nth child:

```css
/* Selects every even element */
.container .row:nth-of-type(even) {
  background-color: #eee;
}

/* Selects every odd element */
.container .row:nth-of-type(odd) {
  background-color: #ddd;
}

/* Selects the 3rd element */
.container .row:nth-of-type(3) {
  background-color: #ccc;
}
```

## The `box-shadow` property

The `box-shadow` property can be used to make an element to cast a shadow.

The values we pass to a `box-shadow` property are:

- The horizontal offset of the shadow
- The vertical offset of the shadow
- The blur radius of the shadow
- The spread radius of the shadow
- The color of the shadow

```css
section.card {
  box-shadow: 2px 2px 10px 0 rgba(0, 0, 0, 0.2);
}
```

We also have the change to make the shadow to be casted inset, so it will be drawn inside the element's border:

```css
section.card {
  box-shadow: inset 2px 2px 10px 0 rgba(0, 0, 0, 0.2);
}
```
