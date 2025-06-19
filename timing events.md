# Timing events

You can use `frameCount` to trigger events at specific intervals—such as every few frames. This is useful for cooldowns, spawn delays, and animation timing.

### Use `frameCount` to trigger actions every few frames

```js
function draw() {
  if (frameCount % 60 === 0) {
   print("1 second has passed (at 60 FPS)")
  }
}
```

### Use `frameCount` for cooldowns or spawn delays

```js
let lastFired=0
let fireRate=15// frames between bullets

function draw() {
  if (keyIsDown(32)) {// keycode for Spacebar
    if (frameCount-lastFired > fireRate) {
      fireBullet()
      lastFired=frameCount
    }
  }
}
```


* `frameCount` starts at 0 and increases by 1 each time `draw()` runs.
* Use `millis()` if you prefer to measure in milliseconds, but `frameCount` is easier when working with frame-based logic like cooldowns or animation delays.
