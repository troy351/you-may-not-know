# you-may-not-know

## JavaScript

- `CanvasRenderingContext2D.globalCompositeOperation` can sets the type of compositing operation to apply when drawing new shapes, very useful when drawing complex shapes.
- how to implement `drag`?
  - bind `mousedown` on target element
  - in `mousedown` callback, bind `mousemove` and `mouseup` on `window`
  - in `mouseup` callback, unbind `mousemove` and `mouseup` on `window`
  - why bind on `window`? bind `mousemove` and `mouseup` on `window` rather than the target element/`body`/`document` could prevent event trigger unexpectedly when moving outside target element or browser window
- bind the same event with the same callback multiple times will only take effect once, see [MDN](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#Multiple_identical_event_listeners)

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

## SVG

- `begin` attribute of `<animateTransform>` element actually stands for the loaded time of the page (i.e. the load time of svg element) even if it was appended dynamically.

## Others

- Chrome Bug: `mousedown` event will trigger a `mousemove` event immediately, even if the cursor not moved at all.
- Undo/Redo: whenever an `undoStop` created, `redoStack` should be cleared.

- to be continued
