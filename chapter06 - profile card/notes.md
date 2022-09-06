# Chapter 6 - Creating a profile card

## Description lists

In HTML, a description list (`<dl>`) is a group of terms that have the term element (`<dt>`) and a variable number of
description elements (`<dd>`).

```html

<dl>
    <dt>Posts</dt>
    <dd>512</dd>
    <dt>Likes</dt>
    <dd>789</dd>
</dl>
```

## CSS custom properties

**CSS custom properties** allow the storage of values that can be used across multiple rules. This behaviour is similar
to the one of variables in programming languages, so that's why custom properties are also known as **CSS variables**.

CSS custom properties declaration syntax consists in preceding a variable name with a double dash (`--`), and then
assigning a value to it after a colon (`:`). CSS custom properties must be declared inside a selector, just as any other
rule.

```css
body {
  --primary-color: #f00;
}
```

CSS custom properties are used by invoking the `var()` function inside the value definition of a rule.

```css
body {
  background-color: var(--primary-color);
}
```

## Fitting images

To make an image fit a container without losing its aspect ratio neither leaving empty spaces, the `object-fit` property
is used with the `cover` value.

By default, the image is centered inside the container, but it can be positioned using the `object-position` property.

```css
img {
  object-fit: cover;
  object-position: 0 0;
}
```

## Calculating values

In CSS, values can be calculated from others using the `calc()` function. The function accepts any valid CSS expression,
so not only absolute values area valid, but also other functions. This includes the `var()` function, which allows the
use of CSS variables inside these calculations.

```css
body {
  --padding: 1rem;
  width: calc(100% - 2 * var(--padding));
}
```

## Background images with gradients

We can add background shapes to an element using the `background-image` property. The value of this property is a list
of one or more images, separated by commas. Each image can be a URL to an image file, or a gradient.

An example of a gradient is `radial-gradient()`, which creates a gradient that changes from a center to outside in any
direction, being the pace of that change proportional to a particular shape. The function takes that shape as its first
parameter (which can go with additional information about its size and position), and then a list of colors and their
thresholds, which are relative to the container sizes (if the container has a max size of 200px, 50% will be at 100px
from the center in a circle shape).

Additional properties can be used to define the background shape characteristics, such as `background-size`
, `background-position` and `background-repeat`.

```css
.profile-card {
  background-image: radial-gradient(circle at 50% 50%, #fff 0%, #fff 50%, #000 50%, #000 100%);
  background-size: 100% 100%;
  background-position: 0 0;
  background-repeat: no-repeat;
}
```

## Advanced flex

In a flex element, each child can take space in function of the demands of its content. To control how much space can be
taken, each child can define a `flex-basis` rule that sets the default space it will take within the flex container.
This is useful to allow all the child elements take the same space in a `space-around` distribution by giving each one
of them the same `flex-basis` value.

It might happen that the basis size is too much. To allow these child elements to shrink, the `flex-shrink` rule is used
with a positive value. A `fles-shrink` value of 0 means that the child element will never shrink.
