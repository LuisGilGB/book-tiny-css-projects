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
