# The Box Model

The box model is made up of `content`, `padding`, `border` and `margin`.
- **Content:** The actual text / child elements in an HTML node `<div>I'm the content</div>`.
- **Padding:** The space around the content.
- **Border:** Surrounds the padding.
- **Margin:** Outside the border. The space between elements.

## Box Sizing

By default, browser's apply border and padding on top of an element's height and width. Avoid this behavior with `box-sizing: border-box;`.

## Padding

- Inner space between content and border.
- Background color applied to an element will be applied to the padding.
- Can be set all at once `padding: 5px;`, per side `padding-top: 5px;` or per logical property `padding-block-start: 5px;` (`start` is the left side in English).

## Border

- Consists of `width`, `style` (dotted, solid, etc.), `color`.
- Can take a shorthand `border: 10px dotted red;`.
- Defaults to the color of the content. Can be set to the color of the content explicitly with `border-color: currentColor;`.
- `border-radius` is really more of a `corner-radius` because it rounds the corners regardless of a border's existence.
- `outline` can be used in a similar way. Outline does not affect layout and is on the outside of the border.
- Use `outline-offset` to create a gap between the outline and border.

## Margin

- Adds space between elements.
- Syntax is the same as padding.
- Accepts negative values to move an element outside its parent or move siblings closer.
- Center an element with `margin: auto;` (only works with horizontal margin).
  - If applied for vertical margin it turns to `0` margin.
  - Only works if an element has an explicit width.
- Setting negative margin to parent padding will allow the child to break out to the edge of the parent.
- Margin between elements collapses, so if two elements have `20px` margin then the total between them will be `20px` not `40px`.

### Margin Collapse Rules

- Only applies for vertical margin.
- Only collapses in [Flow Layout](flow-layout.md).
- Only adjacent elements collapse. Adding a `br` tag will stop the collapse.
- The bigger margin wins.
  - Element A has `margin-bottom: 20px;` and Element B has `margin-top: 10px;` the total margin between them is only `20px`.
- Nesting doesn't prevent margin collapse. Margin will transfer to the parent if it can to maintain this behavior.
- Margins can only collapse if they touch. Adding border, padding or even whitespace from a larger parent height stops the collapse.
- Margins can collapse in the same direction (parent and child both have top margin). The larger margin will win.
- More than two margins can collapse.
```html
<--
The parent and child margins for A collapse
into the parent and child margins for B
-->

<div style="margin-bottom: 5px;">
  <p style="margin-bottom: 20px;">A</p>
</div>
<div style="margin-top: 5px;">
  <p style="margin-top: 20px;">B</p>
</div>
```
- Negative margins collapse in reverse.
  - Element A has `margin-bottom: -20px;` and Element B has `margin-top: -10px;` the total margin between them is only `-20px`.
- A mix of positive and negative margins will be added together. A `-25px` margin and `25px` margin will cancel out.
- Multiple positive and negative margins works the same way. The largest positive and smallest negative margin are found and added together.
