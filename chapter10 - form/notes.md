# Chapter 10 - Styling forms

## The `:not()` pseudo-class

The `:not()` pseudo-class is a CSS3 feature that allows us to select elements that do not meet a particular criteria. We
can set different selectors to avoid separated by commas.

```css
input:not([type="radio"],[type="checkbox"]) {
  border: 1px solid #ccc;
}
```

## The `:where()` and `:is()` pseudo-classes

The `:where()` and `:is()` pseudo-classes allow us to select an element that matches one piece of criteria among
multiple options. `:is()` is equivalent to `:where()` but with higher specifity (0 of `:where()` vs max specifity among
all the selectors of `:is()`).

```css
input:is([type="radio"],[type="checkbox"]):not(:checked) {
  border: 1px solid #ccc;
}
```

They're useful to reduce the verbosity of selectors.

## The `current-color` keyword

The `current-color` keyword is a CSS3 feature that allows us to set any color property with the color of the parent
element. This can be used to make the border share the color with parent's text.

```css
input {
  border: 1px solid currentColor;
}
```

## The `linear-gradient()` function

The `linear-gradient()` function is a CSS3 feature that allows us to create a linear gradient. It takes a list of color
and position references as arguments. The first color is the starting color and the last color is the ending color. The
position references are optional and they're used to define the position of the color in the gradient. If no position is
specified, the color is evenly distributed in the gradient.

The arguments can be preceded by an angle or direction that sets the gradient direction. This direction takes 0 degrees
as from bottom to top, 90 degrees as left to right, 180 degrees as top to bottom and 270 degrees as right to left. In
other words, it takes clockwise direction with 0 at top.

```css
input {
  background: linear-gradient(90deg, #ccf, #aad 33%, #99c);
}
```

## Styling a textarea

Textarea elements don't inherit `color` and `font-size` by default, so if one of them or any other similar property has
to share the value with parents and siblings, the `inherit` value must be used.

Textarea elements can be resized both horizontally and vertically, but sometimes we don't want to support that
capability (for example, resizing width can end up making your form look bad). To have more control over how a textarea
can be resized, the `resize` property is available with values such as `none`, `both`, `horizontal` or `vertical`.

```css
textarea {
  resize: vertical;
}
```

## Styling radio inputs and checkboxes

The `accent-color` property allows us to change the color of the checkmark in radio inputs and checkboxes.

For more advanced customization, we can prevent the native controls from being rendered and use custom ones instead.
This is done by using the `appearance` property with the `none` value.

```css
input[type="radio"] {
  appearance: none;
  border: 1px solid currentColor;
  border-radius: 50%;
  width: 1em;
  height: 1em;
}
```

Checkmarks are styled by using the `::before` or `::after` pseudo-elements and the `content` property. Visibility should
be controlled with the `:checked()` pseudo class and colorized with the background property.

```css
input[type="radio"]:checked::before {
  content: "";
  display: block;
  width: 0.5em;
  height: 0.5em;
  background-color: currentColor;
  border-radius: 50%;
}
```

## Styling select elements

The `select` element is a bit more complex than the previous ones. It relies on native supports from the operating
system that are harder to override.

The first thing we need to completely restyle s `select` element is to hide the native control. This is done by using
the `appearance` property with the `none` value. Then we can add our custom design for a control with the `background-`
properties.

```css
select {
  appearance: none;
  background-size: 1rem 1rem;
  background-image: linear-gradient(135deg, white 50%, transparent 50%), linear-gradient(90deg, #ccf, #aad 33%, #99c); /* Add all the stuff you need for your design */
  background-repeat: no-repeat;
  background-position: right 0.5em top 50%, 0 0;
}
```

Child `option` elements only allow us to style the text and the background; but we can't style the background of the
selected `option`.
