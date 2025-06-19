# Projectile Logic (Bullets)

Bullets are objects that move independently and may hit enemies or targets. Here’s how to create and manage them using object-oriented programming in p5.js.

### Step 1: Create a Bullet Using an basic Objects

```js
// function to make each object
function createBullet(x, y) {
  return {
    x: x,
    y: y,
    speed: 5
  }
}
```

---

### Step 2: Manage Bullets in an Array

```js
let bullets=[]
let playerX=200
let playerY=350

function fireBullet() {
  let b=createBullet(playerX, playerY)
  bullets.push(b)
}
```

---

### Step 3: Update and Show Bullets

```js
function draw() {
  background(0)


  fill(0, 255, 0)
  rect(playerX - 10, playerY, 20, 20)

  // Update and display bullets
  for (let i=bullets.length - 1; i >= 0; i--) {
    let b=bullets[i]

    b.y -= b.speed

    fill(255, 0, 0)
    ellipse(b.x, b.y, 10, 10)

    if (b.y < 0) {
      bullets.splice(i, 1)
    }//end of  if
  }//end of for
}
```

---

### Add Firing with a Key

```js
function keyPressed() {
  if (key === ' ') {
    fireBullet()
  }//end of if
}//end of key pressed
```

---

## using OOP
### Step 1: Create a `Bullet` Class

```js
class Bullet {
  constructor(x, y) {
    this.x=x
    this.y=y
    this.speed=5
  }
  
  update() {
    this.y -= this.speed
  }//end of update
  
  show() {
    fill(255, 0, 0)
    ellipse(this.x, this.y, 10, 10)
  }//end of show

  offScreen() {
    return this.y < 0
  }//end of offscreen
}//end of bullet
```

---

### Step 2: Manage Bullets in an Array

```js
let bullets=[]

function fireBullet() {
  bullets.push(new Bullet(playerX, playerY))
}

function draw() {
  background(0)
  
  for (let i=bullets.length - 1; i >= 0; i--) {
    bullets[i].update()
    bullets[i].show()

    if (bullets[i].offScreen()) {
      bullets.splice(i, 1)
    }//end of if
  }//end of for
}//end of draw
```

