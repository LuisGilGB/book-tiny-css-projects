# Chapter 5 - Summary cards with hover interactions

## The `place-items` property

The `place-items` property is a shorthand for the `align-items` and `justify-items` properties. It can be used in
a `grid` layout to place the items in the center of the container, for example:

```css
.container {
  display: grid;
  place-items: center;
}
```

## The default grid setup

When no specifications about row, columns or areas are passed to a grid layout, the container will have a single
column and as many rows as items there are within it.

An unsized grid takes as much wisth as it needs to display its content.

## The `background-clip` property

The `background-clip` property can be used to define the area where the background color or image is applied. This
feature remains experimental at the time ofr writing these notes.

## The `text-fill-color` property

The `text-fill-color` property can be used to define the color of the text inside a shape. This feature may look
similar to `color`, but it supersedes it in case of collision.

## Defining a header-main-footer layout with CSS grid

A header-main-footer layout can be defined with CSS grid by using the `grid-template-rows` property with the values
`min-content 1fr min-content` or `min-content auto min-content`.

```css
.container {
  display: grid;
  grid-template-rows: min-content 1fr min-content;
}
```

## `min-content` and margins

The `min-content` value for the `width` property will make the element as wide as its content, plus the margins. The
same happens with the `height` property.
