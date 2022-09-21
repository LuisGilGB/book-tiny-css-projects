# Chapter 10 - Styling forms

## The not pseudo-class

The `:not()` pseudo-class is a CSS3 feature that allows us to select elements that do not meet a particular criteria. We
can set different selectors to avoid separated by commas.

```css
input:not([type="radio"],[type="checkbox"]) {
  border: 1px solid #ccc;
}
```
