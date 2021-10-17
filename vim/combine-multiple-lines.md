# Combine multiple lines

Often times you'll need to take multiple lines and combine them into one line. For example we may want to convert the following JavaScript object.

```js
// Multiple lines
const obj = {
  propertyOne: 'value-one',
  propertyTwo: 'value-two',
};

// One line
const obj = { propertyOne: 'value-one', propertyTwo: 'value-two' };
```

To move the line below the current cursor position up and combine with the current line:
- Use the keyboard shortcut <kbd>Shift</kbd> + <kbd>j</kbd>.
  - Use the keyboard shortcut <kbd>g</kbd>, <kbd>Shift</kbd> + <kbd>j</kbd> to ignore whitespace.
- Use `visual` mode to combine multiple lines at the same time.
- Lines that end in `.` add two spaces between each line that is combined.
  - **NOTE:** this may apply for other special characters too.

**Note:** Answer found [here](https://stackoverflow.com/a/3983437).
