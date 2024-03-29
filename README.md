# you-may-not-know

## JavaScript

- `CanvasRenderingContext2D.globalCompositeOperation` can sets the type of compositing operation to apply when drawing new shapes, very useful when drawing complex shapes.
- How to implement `drag`?
  - bind `mousedown` on target element
  - in `mousedown` callback, bind `mousemove` and `mouseup` on `window`
  - in `mouseup` callback, unbind `mousemove` and `mouseup` on `window`
  - why bind on `window`? bind `mousemove` and `mouseup` on `window` rather than the target element/`body`/`document` could prevent event trigger unexpectedly when moving outside target element or browser window
- Bind the same event with the same callback and same parameters multiple times will only take effect once, see [MDN](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#Multiple_identical_event_listeners)
- How to replay audio? `audio.pause(); audio.currentTime = 0; audio.play();`
- Safari won't load audio unless user click. Solution: play just 1ms, after user clicked.
```javascript
const el = document.getElementsById(elName);
const audio = new Audio(audioPath);
let audioLoader = () => {
    audio.play();
    setTimeout(() => {
        audio.pause();
    }, 1)
    
    document.body.removeEventListener('click', audioLoader);
}
document.body.addEventListener('click', audioLoader);
```
- Sort Array by Dict. Assume there is an array `const arr = [{name:'John', age: 10}, {name:'Bob', age: 12}, {name:'Jack', age: 10}]`. How to sort the array by `age` and if same then by `name`?
`arr.sort((a, b) => a.age - b.age || a.name.localeCompare(b.name))`
- `Array.indexOf` vs `Array.includes`
  ```js
  [NaN].includes(NaN) // true, using SameValueZero for comparison under the hood
  [NaN].indexOf(NaN) // -1, using === for comparison under the hood
  ```
- `clearTimeout` and `clearInterval` can replace each other.

## CSS

- `pointer-events: none` can make elements ignore all mouse events even it's on top
- With `flex` layout, children will expaned when content too long, set `width: 0` when `flex-direction: 'row'` and `height: 0` when `flex-direction: 'column'` to avoid it
- Scaling down image may causing it blurry, use code below to prevent it
```css
image-rendering: -moz-crisp-edges;         /* Firefox */
image-rendering: -o-crisp-edges;         /* Opera */
image-rendering: -webkit-optimize-contrast;/* Webkit (non-standard naming) */
image-rendering: crisp-edges;
-ms-interpolation-mode: nearest-neighbor;  /* IE (non-standard property) */
```
- Only `inline` or `inline-block` elements have `vertical-align` and its default value is `baseline`.
  what is `baseline`? check the last inline element, if no content `baseline` is its rect bottom, otherwise `baseline` is the last line's character baseline
- How to make text with `letter-spacing` centered? Add `text-indent` with the same value as `letter-spacing`
- How to make `text-align: justify;` work with single line text Chinese and Japanese charactors? using `text-align-last: justify;`

## SVG

- `begin` attribute of `<animateTransform>` element actually stands for the loaded time of the page (i.e. the load time of svg element) even if it was appended dynamically.
- `<img>` with svg source image could not always get the correct `naturalWidth`/ `naturalHeight`.
  see https://github.com/whatwg/html/issues/3510#issuecomment-369982529

## Cool Effects

- [Shape-shifter](https://github.com/kennethcachia/shape-shifter)
- [Breathing-halftone](https://github.com/desandro/breathing-halftone)

## Others

- Chrome Bug: `mousedown` event will trigger a `mousemove` event immediately, even if the cursor not moved at all.
- Undo/Redo: whenever an `undoStop` created, `redoStack` should be cleared.
- Chrome will block videos with sound autoplay when click refresh button, manually run `video.play()` or just add `mute` attribute should solve this.

- to be continued
