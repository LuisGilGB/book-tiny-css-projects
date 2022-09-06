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
