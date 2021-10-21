# Hidden Content

The following are methods to hide elements on the page.

## `display: none;`

- Elements are effectively removed from the DOM.
- Can't be selected or focused via keyboard navigation.
- Can be useful to show different elements / styles between desktop vs mobile.

## `visibility: hidden;`

- Elements aren't visible on the screen, but they still take up space.
- Blocks of white space will exist in place of the element.
- Can be useful to "hold" space for elements which you know will be visible later.

## `opacity: <0 - 1>;`

- Controls an element's transparency. So `opacity: 0.5;` will make the element 50% transparent.
- Don't use this to hide elements because they can still be selected or focused via keyboard navigation.
- Can be useful to transition an element's visibility (i.e. make the element fade out).
