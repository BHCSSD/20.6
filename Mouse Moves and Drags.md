# Mouse Moves and Drags

## Mouse Movement (No Buttons Pressed)

* `mouseMoved()` is a built-in p5.js function that runs when the mouse moves **without pressing** any buttons.
* If the mouse is pressed, `mouseMoved()` does **not** run.

```javascript
let cx = 200;
let cy = 200;

function setup() {
  createCanvas(400, 400);
  textAlign(CENTER);
}

function draw() {
  background(220);
  text('Move the mouse to move the dot', 200, 30);
  text('Try pressing and moving — the dot won’t move.', 200, 50);
  ellipse(cx, cy, 20, 20);
}

function mouseMoved() {
  cx = mouseX;
  cy = mouseY;
}
```

---

## Mouse Dragging (While Pressed)

* `mouseDragged()` runs when the mouse moves **while pressed**.
* Use it when you want to track dragging behavior like drawing or dragging shapes.


```javascript
let cx = 200;
let cy = 200;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
  ellipse(cx, cy, 20, 20);
}

function mouseDragged() {
  cx = mouseX;
  cy = mouseY;
}
```
