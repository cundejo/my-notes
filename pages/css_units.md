---
title: CSS Units
---

## CSS units
Recommendations of unit types per media type:

|Media | Recommended | Occasional use | Infrequent use | Not recommended|
| :--- | :--- | :--- | :--- | :--- |
| Screen | em, rem, % | px | ch, ex, vw, vh, vmin, vmax | cm, mm, in, pt, pc |
| Print | em, rem, % | cm, mm, in, pt, pc | ch, ex | px, vw, vh, vmin, vmax |
## Relative units
[Relative units](http://www.w3.org/TR/css3-values/#font-relative-lengths)
play nicely with both screen and print media types and should be
the most frequently used CSS units.

Unit | Description
:--- | :---
% | percentage, relative to the same property of the parent element
[em](http://www.w3.org/TR/css3-values/#em-unit) | relative to font size of the element
[rem](http://www.w3.org/TR/css3-values/#rem-unit) | relative to font size of the root element
[ch](http://www.w3.org/TR/css3-values/#ch-unit) | relative to width of the "0" (ZERO, U+0030) glyph in the element's font
[ex](http://www.w3.org/TR/css3-values/#ex-unit) | relative to x-height of the font

## Absolute units
Physical units (e.g. cm, mm, in, pc, and pt)
should only be used for print style sheets,
while pixels (px) should only be used for the screen.
While there are consistent conversions among all of these
[absolute length units](http://www.w3.org/TR/css3-values/#absolute-lengths),
[depending on the device, CSS units can actually mean different things](http://omnicognate.wordpress.com/2013/01/07/in-css-px-is-not-an-angular-measurement-and-it-is-not-non-linear/).
For example, while `1cm` in CSS should print as one physical centimeter,
there's no guarantee that `1cm` in CSS results in one physical centimeter
on the screen.

Unit | Description | cm | mm | in | pc | pt | px
:--- | :--- | ---: | ---: | ---: | ---: | ---: | ---:
cm | centimeter | `1cm` | `10mm` | | | |
mm | millimeter | `1/10cm` | `1mm` | | | |
in | inch | `2.54cm` | `25.4mm` | `1in` | `6pc` | `72pt` | `96px`
pc | pica | | | `1/6in` | `1pc` | `12pt` | `16px`
pt | point | | | `1/72in` | `1/12pc` | `1pt` | `4/3px`
px | pixel | | | `1/96in` | `1/16pc` | `3/4pt` | `1px`

## Viewport units

[Viewport-percentage length units](http://www.w3.org/TR/css3-values/#viewport-relative-lengths)
should be used with caution, as there is still some
[lingering bugs with their implementation](http://caniuse.com/#feat=viewport-units).

Unit | Description
:--- | :---
[vw](http://www.w3.org/TR/css3-values/#vw-unit) | relative to 1% of viewport's width
[vh](http://www.w3.org/TR/css3-values/#vh-unit) | relative to 1% of viewport's height
[vmin](http://www.w3.org/TR/css3-values/#vmin-unit) | relative to 1% of viewport's smaller dimension
[vmax](http://www.w3.org/TR/css3-values/#vmax-unit) | relative to 1% of viewport's larger dimension

# Contexts

## Document-level
Assume the root font size is `16px` but don't require it to be so. Either declare the font size as `100%` or don't declare the `font-size` property at all.

```css
html {
  font-size: 100%;
}
```

## Borders
Most likely use `px`, as most of the time, the border shouldn't need to scale.
```css
.Component {
  border-bottom: 1px solid #ccc;
}
```

## Font-size
Font-size should only be applied at the lowest possible child elements,
in order to minimize its cascading impact on relative units.
While both of the following two examples are essentially equivalent,
only the first is recommended.

**DO**:
```css
.Component {
}
.Component-heading {
  font-size: 1.2em;
}
.Component-body {
  font-size: 0.9em;
}
```
**DO NOT**:
```css
.Component {
  font-size: 1.2em;
}
.Component-heading {
  font-size: 1em;
}
.Component-body {
  font-size: 0.75em;
}
```

## Padding and margin
In order to ensure consistent use of whitespace throughout the application,
given a component could be used in a variety of contexts,
it may be best to use `rem` for margin and padding than `em`.

```css
.Component {
  margin: 1rem 0;
  padding: 1rem;
}
```

## Media queries
[Only use `em` within media query definitions, never pixels](http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/).
Until there's wider [`rem` support within media queries](http://fvsch.com/code/bugs/rem-mediaquery/),
[`rem` should be avoided in media queries as well](http://codeboxers.com/em-vs-px-vs-rem-in-media-queries/).

```css
@media (min-width: 20em) {
  .Component {
    background-color: blue;
  }
}
```
