# Positioned Layout

This layout system allows for elements to break out of the flow of the document. It's controlled by the `position` property which can take the values: `static`, `initial`, `relative`, `absolute`, `fixed` and `sticky`.

## Static (Initial)

- The default value for the `position` property (the element isn't using the `Positioned Layout` algorithm).
- To force *positioned* elements to not use this system, set the `position` to `static` or `initial` (which should just mean `static`).

## Relative

Setting an element to `position: relative;` may not have an obvious effect, but it does the following:
- Constrains certain children.
- Enables the CSS offset properties `top`, `left`, `right` and `bottom` (which can be used to move an element *relative* to its natural position).
- Negative offset will shift an element in the opposite direction.
- Doesn't move other elements on the page (differs from `margin` in this way).
  - A `block` element with `width: auto;` will resize when `margin-left` increases, but will only shift an element right when `left` increases without resizing.
- Can be used for both `inline` and `block` elements.
- Inherits most of its behavior from the overall layout algorithm (e.g. `Flow Layout`).

## Absolute

- Allows elements to break out of the flow of the document.
- The same properties are enabled as `position: relative;`.
- The offset properties move relative to the **containing block**.
- If no offset is defined the element will sit in its **default** in-flow position.
- Other elements will ignore an `absolute` positioned element, which means other elements will stack below (or above) the `absolute` positioned element.
- Parent elements ignore `absolute` elements, so these children aren't used to determine parent height.
  - If it's the only element then the parent element will collapse with a height of `0`.
- `block` and `inline` display are ignored and therefore behave the same.
- `absolute` elements will grow with their content until they hit their **containing block**. Content which is too long will break out of the parent and introduce a horizontal scroll bar.
- Center an `absolute` element with the following:
  - `position: absolute;`
  - `margin: auto;`
  - Fixed size (i.e. explicit `width` and `height`)
  - Equal distance from each edge (ideally `0px`, e.g. `top: 0;`)

## Fixed

- Similar to `position: absolute;`, but can only be constrained by the viewport.
  - Any ancestor (e.g. parent or grandparent) with the CSS property `transform` set or the CSS declaration `will-change: transform;` will act as a `position: fixed;` element's **containing block**, effectively making the element behave like an `absolute` positioned element.
- Immune to scrolling.

## Sticky

- Allow elements to **stick** to an edge. Effectively transitions an element from `relative` to `fixed` as you scroll.
- Needs to have an edge to stick to defined (e.g. `top: 0`). It can stick to a horizontal and vertical edge at the same time (i.e. `top: 0;` and `left: 0;`).
- Only **sticky** in relation to its parent. When the parent is scrolled off screen, the **sticky** child is as well.
- Takes up space in the flow of the document like `relative` (unlike `absolute` or `fixed`). Sibling elements will not try to stack on these elements by default.
- Can only stick to one context (viewport or an ancestor element with `overflow` set).

## Containing Block

- A rectangular boundary that every element has around it.
- In `Flow Layout`, elements are contained by their parents (i.e. size and shape of parent element's content box).
- `absolute` elements are contained by any ancestor which uses `Positioned Layout` (i.e. `absolute`, `relative`, `fixed` and `sticky`). If there is no ancestor which uses `position` then the element is contained by the viewport.
- `fixed` elements are typically constrained by the viewport, unless an ancestor has a `transform` set or `will-change: transform;`.
