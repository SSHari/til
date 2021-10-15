# Flow Layout

This is the default layout used by browsers. `HTML Document + No CSS = Flow Layout`. There are three display types which are important for this layout type: `inline`, `block` and `inline-block`. Flow Layout behaves like English text. **Blocks** stack **vertically** and **inline** flows from left to right.

## Inline

- Typically used for text: `<strong>I'm inline</strong>`.
- Flows horizontally.
- Some CSS properties like `width` and `height` are not respected.
- Margin and padding can be used to increase space.
  - **NOTE:** Use padding with caution because of weird behavior.
- Replaced elements like `img`, `video` and `canvas` and `button` elements are not subject to CSS restrictions.
- Subject to `line-height` which adds additional space.
  - **NOTE:** Remove this space by setting `display: block;` or setting `line-height: 0;` on the parent.
- Literal whitespace in the HTML can add space **between** elements.
  - **NOTE:** This is not a problem for other layout types like Flex Layout.
    ```html
    <-- White space between elements -->
    <div>White space</div>
    <div>White space</div>

    <-- No White space between elements -->
    <div>No white space</div><div>No white space</div>
    ```
- Text in these elements will wrap.
  - A border around these elements will wrap by starting on one line and ending on the next line.
  - Use `box-decoration-break: clone;` to avoid the above behavior and have separate borders per line break.

## Block

- Elements are stacked vertically. Two elements will not share a line regardless of width.
- Blocks are hungry. They take up as much space as they can in the parent element by defaulting to `width: auto;`.
- Make a block only take up the width of its content with `width: fit-content;` (this is useful for adding a background that only applies directly behind the content).

## Inline-Block

- Treated as inline by parents.
- Treated as block within themselves.
- The above two means that elements flow `left -> right` (don't consume a whole line) and they can be styled the same way as blocks (unlike inline which ignores some styles).
- **Here's the catch:** since they can be styled like blocks, they **can't** wrap text like inline elements. Long text will be forced to the next line instead of wrapping.
