# Game State Management

Use a variable to track what "screen" or "mode" the game is in.

```js
let gameState= "menu" //could be "menu", "playing", "paused", "gameOver" etc

function draw() {
  background(220) 
  
  if (gameState === "menu") {
    text("Press SPACE to Start", width /2, height /2) 
  } 
  else if (gameState === "playing") {
    playGame() //your main gameplay logic here
  } 
  else if (gameState === "paused") {
    text("Game Paused\nPress P to Resume", width /2, height /2) 
  }
  else if (gameState === "gameOver") {
       text("Game Over!\nPress R to Restart", width /2, height /2) 
  }
}

function keyPressed() {
  if (gameState === "menu" && key === " ") {
    gameState="playing" 
  } 
  else if (gameState === "playing" && key === "p") {
    gameState="paused" //Pause the game
  } 
  else if (gameState === "paused" && key === "p") {
    gameState="playing" //Resume the game
  } 
  else if (gameState === "gameOver" && key === "r") {
    gameState="menu" //Restart to menu
  }
}
```

**Use `"paused"` as its own state**
- don’t stop your `draw()` with `noLoop()`, just skip gameplay logic.
- this makes it easier to show pause menus and resume with a key.

