# Chapter 3 - Creating a responsive animated loading screen

SVG images can be used in HTML in three ways:

- As a background image (`background-image: url(“myImage.svg”);`).
- As an `img` element that imports a `.svg` file as its `src` attribute value (`<img src=”myImage.svg” alt=””>`).
- As an SVG element (`<svg>...</svg>`).

Only the third one makes possible the manipulation of the graphic elements within the SVG image.

## Viewport

The **viewport** is the area in which the SVG is visible (rendered). Whatever overflows the boundaries of the viewport
will remain hidden. The analogy is a frame that contains the picture. Resizing the viewport does not resize its content.

Viewport size can be set with the `width` and `height` attributes of a `<svg>` element.

```html

<svg width="100%" height="300px">
  ...
</svg>
```

A `width` of 100% will assign the same width the container element has.

## Viewbox

The **viewbox** is what defines the position, width and height of a graphic element within the viewport. It's the set of
rules that allow us to scale graphics. We can set the `viewBox` attribute of a `<svg>` element to assign the needed
values with the syntax `viewBox="min-x min-y width height"`.

- `min-x`: the leftmost position of the graphic element within the viewport (usually 0).
- `min-y`: the topmost position of the graphic element within the viewport (usually 0).
- `width`: the width of the graphic element within the viewport.
- `height`: the height of the graphic element within the viewport.

## Styling

SVG elements have their own presentation attributes apart from the usual CSS properties. These presentation attributes
can also be given a value inline within the element. A list of all the presentation attributes is available
at [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/Presentation).

## CSS animations

Animation properties:

- `animation-name`
- `animation-timing-function`
- `animation-iteration-count`
- `animation-fill-mode`
- `animation-duration`
- `animation-delay`
- `animation-direction`
- `animation-play-state`

They can be set with the `animation` shorthand property.

### Keyframes

Keyframes are the definition of a single animation through beginning to its end with any intermediate state. For each
one
of the milestones, a set of properties is defined and that animation will return exactly that set of properties when the
frame time along the animation duration matches the one assigned for that state.

They are defined with the `@keyframes` at rule and are given a name that will be used by the `animation-name` property
to attach the animation defined by the property to the elements that match to the selector of the `animation-name` rule.

The beginning state can be defined with `from` and the end state with `to`. Percentages can be used to set intermediate
states, being `0%` the same as `from` (beginning) and `100%` the same as `to` (end). Any frame that doesn't match with
any of the explicit states is calculated by the browser to interpolate frames and guarantee a smooth animation. This
process is known as *in-betweening*.

```css
@keyframes my-animation {
  from { transform: translateX(0) }
  50% { transform: translateX(100px) }
  to { transform: translateX(0px) }
}

.animated-square {
  animation-name: my-animation;
  animation-duration: 3s;
  animation-iteration-count: infinite;
}
```

### Transforming elements

During animations, we might be interested in changing the position, size, rotation, etc. of an element, but remain the
surrounding elements untouched. Because of this reason, we must avoid modifying properties that affect layout such
as `width`, `height`, `top`, `left`, etc. Instead, we can make use of the `transform` property, which allows us the use
of functions to scale, translate or rotate, among others, elements.

A full list of available transform functions can be
found [here](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function).

By default, SVG elements have their center on their 0,0 coordinates, which is the top-left corner. To set a different
center that will act as a point of reference, the `transform-origin` property can be used. This property accepts
absolute numbers, percentages and keywords such as `center`, `top` or `right`. It can also take up to three values to
set the origin coordinates in the x, y and z axis.

### Reduced motion

Due to accessibility reasons, browsers allow the users to select a reduced motion mode that can be used to reduce or
disable the rate of the animations. CSS provides us the `prefers-reduced-motion` media query to detect if the user has
checked that option.

The `prefers-reduced-motion` media query has two possible values: `no-preference` and `reduce`. Being the first the one
for when the reduced motion option is disabled and the second the one that applies when the option is enabled.

```css
@media (prefers-reduced-motion: reduce) {
  rect { animation: none }
}
```

## Special control properties

To control the color of native form controls such as check marks, radio inputs or progress bars, we have a new CSS
property called `accent-color`.

```css
progress {
  height: 24px;
  width: 100%;
  accent-color: #128688;
}
```

In case of progress bars, changing the background color of the empty area requires vendor properties. Vendor properties
are the ones that are prefixed following specific browsers and engines, like `-webkit-` and `-moz-`.

To reset the user-agent styles, we can set the `appearance` property to `none`. For compatibility issues, the vendor
prefixed options like `-webkit-appearance` and `-moz-appearance` can be used in combination too. By removing the
appearance, the `accent-color` property will stop making any effect.

Some progress bar specific vendor properties are:

- `::-webkit-progress-inner-element` - Pseudo element of outermost part of the progress bar.
- `::-webkit-progress-bar` - Pseudo element of the bar itself, with no progress indicator. Child
  of `::-webkit-progress-inner-element`.
- `::-webkit-progress-value` - Pseudo element of the progress indicator. Child of `::-webkit-progress-bar`.

Mozilla only provides the pseudo class `::-moz-progress-bar`, which works as `::-webkit-progress-value`. For editing
other styles not directly related to the bar, styling the progress element itself is required.
