# Chapter 2: Designing a layout using CSS grids

## Ways to create a grid layout

| Display value | Effect                                                                                  |
|---------------|-----------------------------------------------------------------------------------------|
| `grid`        | Grid in a block level box. Uses a new line and takes the container full width.          |
| `inline-grid` | Grid in an inline-level box, following the previous content like a `span` element does. |

When a grid layout is created, the browser automatically sets one single column unless rules specify otherwise.

## Terminology

In a grid layout, **grid lines** are the vertical and horizontal lines that establish the gris-like structure with
horizontal and vertical lines. Grid lines are numbered with positive numbers starting with 1 from top to bottom for
horizontal lines and from left to right for vertical lines. Negative numbers can also be used to traverse grid lines
from bottom to top and from right to left starting from -1.

**Tracks** are the space between two parallel grid lines. Horizontal tracks (space between two horizontal grid lines)
are called **rows** and vertical tracks (space between two vertical grid lines) are called **columns**.

A **cell** is the intersection of two perpendicular tracks, or what is the same: between a row and a column.

Across a grid line, some spacing can appear separating two adjacent tracks. This spacing is called **gap**.

**Note**: The horizontal grid lines numbering might start from right in right to left languages such as Arabic.

### The `repeat()` function

The `repeat()` function allows to define a grid layout with a fixed number of columns.

- The first parameter is the number of columns.
- The second parameter is teh sizing of each column.

### The `minmax()` function

The `minmax()` function defines a range between a min and a max values provided as arguments. If max is not greater than
the min, it is ignored by the browsers. Both min and max boundaries are valid outputs.

### The `auto` keyword

When the `auto` keyword is used as max value in a `minmax()` function, it's resolved as `max-content`. When used as a
min, it resolves as the largest `min-width`/`min-height` among all the cells of that column/row.

### The flexible length unit (`fr`)

The fraction unit (`fr`) is a unit used by grid layouts to assign sizes in relationship to the other tracks. It behaves
similarly than `flex-grow` values. One track with `5fr` will take 5 times the size of a track with `1fr`.

```css
main {
  display: grid;
  grid-template-columns: repeat(4, minmax(auto, 1fr));
}
```

## Explicit vs implicit

Explicit grid layouts are defined with the `grid-template-columns` and `grid-template-rows` properties. When the browser
infers for other rules that additional tracks or cells are needed (and so it adds them), we say that's an implicit part
of the grid. Implicit behaviours can be controlled with properties such as `grid-auto-flow`, `grid-auto-columns`
and `grid-auto-rows`.

## Areas

We can set the surface taken by an element in a grid element with the `grid-column` and `grid-row` properties. This
element will take the whole area between the first and the second number we pass to that rule. This way,
a `grid-column: 1 / 4` rule will take all the area between the first and the fourth column, or in other words, it would
span through the first 3 columns. Similarly, a `grid-row: 3 / 5` rule would start in the third row and would occupy both
the third and the fourth rows, ending in the fifth horizontal grid line.

We also have the `grid-template-areas` property, which allows us to define named areas in a explicitly defined grid
layout.

```css
main {
  display: grid;
  grid-template-columns: repeat(4, minmax(auto, 1fr));
  grid-template-rows: repeat(4, minmax(auto, 1fr));
  grid-template-areas:
    "header header header header"
    "nav    main   main   bookmarks"
    "nav    main   main   aside"
    "nav    play   .      aside"
    "footer footer footer footer";
}
```

The defined names can be assigned to specific elements with the `grid-area` property.

```css
.viewport > header {
  grid-area: header;
}
```

The dotted (`.`) cell will remain empty, so the browser will jump over it to the next named area when placing elements
in the grid.

## Gaps

We have `row-gap` and `column-gap` properties, with `gap` being a shorthand for both. This gap will define the margin
between adjacent rows or columns, a term that can also appear with the name of `gutter` (usual term in graphic design).
In case two values are provided, the first `gap` value is the `row-gap` and the second one is the `column-gap`.

The default gap is 0.

`grid-gap` property is the original property for gaps in CSS grid layout, but nowadays the `gap` property is preferred.

## Notes on accessibility

Grid layout placements are not used for screen readers to determine orders and priorities, so we shouldn't rely on our
grid layout rules as a valid source for screen reading. This purpose is served by the HTML content, so it's preferred to
keep similar structure between HTML and grid layout for an intuitive understanding on how screen readers will behave.

Browsers usually include developer tools to check how screen readers and other accessibility tools will behave, so a
good idea is to check them periodically in order to confirm the structure is intuitive enough.

## Media queries

> Information about media queries is provided by the book in this chapter.

Media queries are conditional rules that are applied depending on the size of the screen. The syntax starts with
the `@media` keyword, following with the screen condition between parentheses and the rules to be applied when the
condition returns true inside brackets:

```css
@media (min-width: 500px) {
  main {
    grid-template-columns: repeat(4, minmax(auto, 1fr));
  }
}
```

## Grid layout specs

In order to follow how the grid layout module specs evolve, check the official by the
W3C: [CSS Grid Layout Specification](https://www.w3.org/TR/css-grid/).
