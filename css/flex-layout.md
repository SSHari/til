# Flex Layout

A layout mode which is used to position elements along a given axis (row or column).

`display: flex;` will:
- make an element **block-level**.
- change the element's children's layout.

Flex behavior is mirrored between each axis.

|                  | Row        | Column     |
| ---------------- | ---------- | ---------- |
| **Primary Axis** | horizontal | vertical   |
| **Cross Axis**   | vertical   | horizontal |

## Properties

- `justify-content` controls content along the primary axis.
  - `flex-start` puts elements at the start of the axis.
  - `flex-end` puts elements at the end of the axis.
  - `center` puts elements in the middle of the axis.
  - `space-between` puts equal space between elements and puts the first element at the start of the axis and the last element at the end of the axis.
  - `space-around` puts even space around each element which means the space between elements is double the space of the start and end of the axis (first and last elements).
  - `space-evenly` is similar to `space-around` but the space at the start and end of the axis is the same as the space between elements.
- `align-items` controls content along the cross axis.
  - `stretch` makes the children take up the full space along the axis.
  - `flex-start` puts the children at the start of the axis and lets them take up as much space as they need to display their content.
  - `flex-end` puts the children at the end of the axis and lets them take up as much space as they need to display their content.
  - `center` aligns the children with the center of the axis.
  - `baseline` aligns the children along the baseline which can be useful to keep text aligned properly (as though it were written on a piece of paper).
- `align-self` can be used on a child element to override the `align-items` property on a case by case basis.

## Growing and Shrinking

- Flex children have a **minimum** size which for row layouts is effectively `width: minimum-content;`.
- Flex children have a **hypothetical** size which is the **default** size a child would be if no other CSS properties were influencing its size.
- `flex-basis` can be used to set the **hypothetical** size the same way `height` and `width` can be used.
  - It acts differently depending on if working with a flex row (width) or flex column (height).
  - It always takes precedence over `width` or `height`.
  - It can't scale an element below its minimum content size (width can).
- `flex-grow` can be used to make a child take up the remaining white space. If there is no free white space then it effectively does nothing.
- `flex-shrink` controls the rate at which a child element shrinks in size as the flex container (parent) gets smaller.
  - It only has an effect on a child element while it's larger than its **minimum** content size.
  - Setting this to `0` will disable shrinking for the child element.
- `flex-grow` and `flex-shrink` take unit-less values that represent a ratio relative to the other children.
- The `flex: 1;` shorthand can be used to make child elements the same size by doing the following:
  - `flex-grow: 1;`
  - `flex-shrink: 1;` (this is the default)
  - `flex-basis: 0%;`
    - If this is set for all children then all the space is available to distribute via `flex-grow`.
    - See how the [flex algorithm distributes space](https://www.w3.org/TR/css-flexbox-1/images/rel-vs-abs-flex.svg).
- `max-width`, `max-height`, `min-width` and `min-height` can be used with flex to enforce constraints.
- `flex-wrap: wrap;` can be used to make elements wrap to the next line instead of introducing a horizontal scroll bar.
- `align-content` can be used with `flex-wrap` to move a group (e.g. multiple rows due to wrapping) the same way that `align-items` is used.
- Setting `margin: auto;` to one side of a child element will cause the other child elements to shift to the other end of the axis.
  ```html
  <div style="display:flex;">
    <div style="margin-right: auto;">I'm on the left</div>
    <div>I'm on the right</div>
  </div>
  ```
- `gap` can be used to add space **between** children.

## Ordering

- Using `flex-direction` with `row-reverse` or `column-reverse` can flip the order of the children **visually**.
- `order` is similar to `z-index`. `order: 2;` comes after `order: 1;` but before `order: 5;`.
- `flex-wrap: wrap-reverse;` makes elements wrap up instead of down.

## Flexbox Interactions

- A child with `Positioned Layout` (except `position: relative;`) will be ignored by its flex container.
- A stacking context is created if a flex container child has a `z-index` set to anything but `auto`.
