# Overflow

- Defaults to `visible` which allows content to spill outside its parent.
- `overflow` is shorthand for `overflow-x` and `overflow-y`.
- `scroll` will hide the content and provide a scroll bar to make the content accessible.
  - The scroll bar will always be visible even if the content is small enough to fit in its parent.
  - This can be useful to make dynamic content more smooth (adding / removing a scroll bar can be jarring).
- `auto` will work like `scroll` but will only add the scroll bar if needed.
- `hidden` will hide the content like `scroll`, but there won't be a way to access it (no scroll bar).
  - Useful for truncating text via ellipses.
  - Useful for artistic designs.
- `visible` can't be used with other `overflow` values. You can't hide content on one axis and show it on another axis (i.e. clip the content in one direction).
  - If an element is set to `overflow-x: hidden;` and `overflow-y: visible;` then the `overflow-y` will effectively be set to `auto`, so the content will be hidden and a scroll bar will be visible if needed.
  - As soon as `overflow` is added, the element becomes a **scroll container** which prevents content from breaking out of its parent.
- To add horizontal scroll for inline elements:
  - `white-space: nowrap;` to remove `inline` wrapping behavior.
  - `overflow: auto;` to introduce the `scroll` behavior.
- `position: absolute;` elements will only respect `overflow` which is set on its [**containing block**](positioned-layout.md#containing-block).
- `position: fixed;` elements don't have an effect on overflow because the **containing block** is the viewport which doesn't have a `position` value.
