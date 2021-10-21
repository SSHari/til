# Offset

The position values `top`, `left`, `right` and `bottom` can be used to move positioned elements on the page, but they behave differently based on the `position` value.

## Relative

Shifts an element relative to its default location in the document.

## Absolute

Shifts an element relative to its [**containing block**](positioned-layout.md#containing-block).

## Fixed

Shifts an element relative to the viewport.

## Sticky

The offset values determine the minimum gap between the element and the given edge.
  - `top: 10px;` sets the minimum gap to `10px` from the top.
  - Only applies while the parent element is in view. When a parent element is scrolled out of view, the **sticky** element is also scrolled out of view.
