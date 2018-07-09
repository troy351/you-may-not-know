# you-may-not-know

## JavaScript

- `CanvasRenderingContext2D.globalCompositeOperation` can sets the type of compositing operation to apply when drawing new shapes, very useful when drawing complex shapes.

## CSS

- `pointer-events: none` can make elements ignore all mouse events even it's on top
- with `flex` layout, children will expaned when content too long, set `width: 0` to avoid it
- scaling down image may causing it blurry, use code below to prevent it
```css
image-rendering: -moz-crisp-edges;         /* Firefox */
image-rendering: -o-crisp-edges;         /* Opera */
image-rendering: -webkit-optimize-contrast;/* Webkit (non-standard naming) */
image-rendering: crisp-edges;
-ms-interpolation-mode: nearest-neighbor;  /* IE (non-standard property) */
```
- only `inline` or `inline-block` elements have `vertical-align` and its default value is `baseline`.
  what is `baseline`? check the last inline element, if no content `baseline` is its rect bottom, otherwise `baseline` is the last line's character baseline  

## Others

- Chrome Bug: `mousedown` event will trigger a `mousemove` event immediately, even if the cursor not moved at all.

- to be continued
