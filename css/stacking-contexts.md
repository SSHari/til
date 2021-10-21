# Stacking Contexts

The stacking order of elements in the document is determined based on the layout algorithm which is used.

## Flow Layout

- No overlap by default.
- Use negative margin to create overlap.
- Order of the elements matters. Elements coming later will be on top.
  - **Note:** Content is painted separately from the background, so content from an earlier element will stack above the background of a later element.
- `Flow Layout` isn't really designed for layering.

## Positioned Layout

- Positioned elements will typically render on top of non-positioned elements.
  1. Browser renders all non-positioned elements (i.e. `Flow Layout`, `Flex Layout`, `Grid Layout`).
  2. Browser renders all positioned elements (i.e. `relative`, `absolute`, `fixed`, `sticky`).
- If two elements both have a `position` then DOM ordering matters.

## z-index

This property can be used to change the default browser layering.
- Only works with positioned elements or `Flex Layout` or `Grid Layout` children.
- No effect on elements rendered with `Flow Layout`.
  - **Note:** works with `Flex Layout` and `Grid Layout`.
- The default value is `auto` which is equivaent to `0`, so setting another element to any number higher will cause it to stack on top.
- Can be set to a negative number, but this shouldn't be needed.
- Only compared with elements within a given stacking context. A stacking context can be created in the following ways:
  - Setting the `position` to `absolute` or `relative` and specifying a `z-index`.
  - Setting the `position` to `fixed` or `sticky` (no need for a `z-index`).
  - Setting `opacity` to less than `1`.
  - Applying a `mix-blend-mode`.
  - Setting `display` to `flex` or `grid` and specifying a `z-index`.
  - Using `transform`, `filter`, `clip-path`, `perspective` or `mask`.
  - Using `isolation: isolate;`. This is a good way to create a stacking context without forcing random stacking with arbitrary `z-index` values.

### Example

```html
<div id="div-one" style="position: relative; z-index: 2;">
  I'm above the second div
</div>
<div id="div-two" style="position: relative; z-index: 1;">
  <p style="z-index: 100000;">
    I am below "div-one" because my stacking
    context "div-two" is below "div-one"
  </p>
</div>
```
  
**Notes:**
- [Learn about stacking contexts](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context).
- [Debug stacking contexts](https://github.com/andreadev-it/stacking-contexts-inspector).
