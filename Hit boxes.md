# Hit boxes
## Cheat Sheet

| Test                | Useful For                      | Function/Event Used             |
| ------------------- | ------------------------------- | ------------------------------- |
| Point–Circle        | Button clicks, bullets, scoring | `mousePressed()` + `distance()` |
| Circle–Circle       | Collisions,enemies,powerups   | `distance()` + radii            |
| Point–Rectangle     | UI buttons,area tests          | mouseX/Y and bounds             |
| Rectangle–Rectangle | Physics,dragging,layout tests | bounding box comparison         |

## Point Inside a Circle

**AKA** Is the mouse inside a circle?

###  Rule:

A point is inside a circle if:
- distance between the point and center ≤ radius


### Distance Formula (use this often!)

```javascript
function distance(x0,y0,x1,y1) {
  return sqrt((x1 - x0) ** 2 + (y1 - y0) ** 2)
}
```

### Count clicks inside the circle

```javascript
let cx,cy,r
let hits = 0

function setup() {
  createCanvas(400,400)
  cx = width/2
  cy = height/2
  r = 50
}

function draw() {
  background(220)
  fill(100,200,100)
  ellipse(cx,cy,r * 2)

  fill(0)
  textSize(16)
  text(`Hits: ${hits}`,10,20)
}

function mousePressed() {
  if (dist(mouseX,mouseY,cx,cy) <= r) {
    hits++
  }
}
```

---

## Circle-Circle Intersection

**AKA** Are two circles touching or overlapping?

###  Rule:

They intersect if:
- distance between centers ≤ sum of radii

### Click to move a circle

```javascript
let cx1,cy1,r1
let cx2,cy2,r2

function setup() {
  createCanvas(400,400)
  cx1 = width/3
  cy1 = height/2
  r1 = 50

  cx2 = (2 * width)/3
  cy2 = height/2
  r2 = 50
}

function draw() {
  background(220)

  let d = distance(cx1,cy1,cx2,cy2)

  fill(d <= r1 + r2 ? 'green' : 'orange')
  ellipse(cx1,cy1,r1 * 2)
  ellipse(cx2,cy2,r2 * 2)
}

function mousePressed() {
  cx2 = mouseX
  cy2 = mouseY
}
```

---

## Point Inside a Rectangle

**AKA:** Is the mouse inside this box?

###  Rule:


mouseX between left and right
**AND**
mouseY between top and bottom

### Click to count hits in a box

```javascript
let x,y,w,h
let hits = 0

function setup() {
  createCanvas(400,400)
  x = width/4
  y = height/4
  w = width/2
  h = height/2
}

function draw() {
  background(220)
  fill(100,200,100)
  rect(x,y,w,h)

  fill(0)
  textSize(16)
  text(`Hits: ${hits}`,10,20)
}

function mousePressed() {
  if (mouseX >= x && mouseX <= x + w &&
      mouseY >= y && mouseY <= y + h) {
    hits++
  }
}
```

---

## Rectangle-Rectangle Intersection

**AKA:** Are two rectangles touching?

###  Rule:

They overlap if:

```text
right1 ≥ left2
AND right2 ≥ left1
AND bottom1 ≥ top2
AND bottom2 ≥ top1
```

### Drag second rectangle into the first

```javascript
let x1,y1,w1,h1
let x2,y2,w2,h2

function setup() {
  createCanvas(400,400)
  x1 = 50 y1 = 50 w1 = 100 h1 = 100
  x2 = 200 y2 = 200 w2 = 100 h2 = 100
}

function draw() {
  background(220)

  let overlapping = rectsIntersect(x1,y1,w1,h1,x2,y2,w2,h2)
  fill(overlapping ? 'green' : 'red')

  rect(x1,y1,w1,h1)
  rect(x2,y2,w2,h2)
}

function mousePressed() {
  x2 = mouseX - w2/2
  y2 = mouseY - h2/2
}

function rectsIntersect(x1,y1,w1,h1,x2,y2,w2,h2) {
  return (
    x1 + w1 >= x2 &&
    x2 + w2 >= x1 &&
    y1 + h1 >= y2 &&
    y2 + h2 >= y1
  )
}
```

---



