# Chapter 10 - Styling forms

## The not pseudo-class

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
