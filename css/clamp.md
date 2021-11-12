# Clamp

The `clamp` property can be used to constrain CSS values.

It takes 3 values:

1. The minimum value
2. The ideal value
3. The maximum value

## Basic Clamp

```css
/* Without clamp */
.clamped {
  min-width: 600px;
  width: 50%;
  max-width: 900px;
}

/* With clamp */
.clamped {
  width: clamp(600px, 50%, 900px);
}
```

The above two examples will do the same thing. That said, there's a problem at smaller screen sizes. Since the minimum value is `600px`, screens which are smaller will have to introduce a horizontal scroll bar to make sure the content is accessible.

No worries. Try this...

## Max Width Clamp

```css
.clamped {
  width: clamp(600px, 50%, 900px);
  max-width: 100%;
}
```

`clamp` is superior because it allows for the use of `max-width` as well. In this case, the idea is that the element with the `.clamped` class can't be larger than `900px` **or** `100%` which prevents the horizontal scroll bar on smaller screens.

## Clamp Anything

The `clamp` util is powerful because it can be used for other properties.

```css
.clamp-anything {
  font-size: clamp(12px, 1rem, 24px);
}
```

## Demos

Check out these [clamp demos](https://thesshguy.com/demos/clamp/).
