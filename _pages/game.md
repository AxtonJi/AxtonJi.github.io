---
permalink: /game/
title: "Snake Game"
excerpt: "A fun snake game"
author_profile: true
---

<div class="game-container">
  <h2>Snake Game / 贪吃蛇</h2>
  <p class="game-score">Score: <span id="score">0</span></p>
  <canvas id="gameCanvas" width="400" height="400"></canvas>
  <p class="game-controls">Use arrow keys or WASD to control / 使用方向键或WASD控制</p>
  <button id="startBtn" onclick="startGame()">Start Game / 开始游戏</button>
</div>

<style>
.game-container {
  text-align: center;
  padding: 20px;
}

#gameCanvas {
  border: 2px solid #1565c0;
  background-color: #f5f5f5;
  display: block;
  margin: 20px auto;
}

.game-score {
  font-size: 1.2em;
  font-weight: bold;
  color: #1565c0;
}

.game-controls {
  color: #666;
  font-size: 0.9em;
}

#startBtn {
  padding: 10px 20px;
  font-size: 1em;
  background-color: #1565c0;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}

#startBtn:hover {
  background-color: #0d47a1;
}
</style>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
const box = 20;
let snake, food, d, score, game;

function initGame() {
  snake = [{x: 9 * box, y: 10 * box}];
  food = {
    x: Math.floor(Math.random() * 19 + 1) * box,
    y: Math.floor(Math.random() * 19 + 1) * box
  };
  d = null;
  score = 0;
  document.getElementById('score').innerText = score;
}

function startGame() {
  if (game) clearInterval(game);
  initGame();
  game = setInterval(draw, 100);
}

document.addEventListener('keydown', direction);

function direction(event) {
  const key = event.keyCode;
  if ((key === 37 || key === 65) && d !== 'RIGHT') d = 'LEFT';
  else if ((key === 38 || key === 87) && d !== 'DOWN') d = 'UP';
  else if ((key === 39 || key === 68) && d !== 'LEFT') d = 'RIGHT';
  else if ((key === 40 || key === 83) && d !== 'UP') d = 'DOWN';
}

function collision(newHead, snake) {
  for (let i = 0; i < snake.length; i++) {
    if (newHead.x === snake[i].x && newHead.y === snake[i].y) return true;
  }
  return false;
}

function draw() {
  ctx.fillStyle = '#f5f5f5';
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  for (let i = 0; i < snake.length; i++) {
    ctx.fillStyle = i === 0 ? '#1565c0' : '#42a5f5';
    ctx.fillRect(snake[i].x, snake[i].y, box, box);
    ctx.strokeStyle = '#fff';
    ctx.strokeRect(snake[i].x, snake[i].y, box, box);
  }

  ctx.fillStyle = '#e53935';
  ctx.fillRect(food.x, food.y, box, box);

  let snakeX = snake[0].x;
  let snakeY = snake[0].y;

  if (d === 'LEFT') snakeX -= box;
  if (d === 'UP') snakeY -= box;
  if (d === 'RIGHT') snakeX += box;
  if (d === 'DOWN') snakeY += box;

  if (snakeX === food.x && snakeY === food.y) {
    score++;
    document.getElementById('score').innerText = score;
    food = {
      x: Math.floor(Math.random() * 19 + 1) * box,
      y: Math.floor(Math.random() * 19 + 1) * box
    };
  } else {
    snake.pop();
  }

  let newHead = {x: snakeX, y: snakeY};

  if (snakeX < 0 || snakeX >= canvas.width || snakeY < 0 || snakeY >= canvas.height || collision(newHead, snake)) {
    clearInterval(game);
    ctx.fillStyle = 'rgba(0,0,0,0.5)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = '#fff';
    ctx.font = '30px Arial';
    ctx.textAlign = 'center';
    ctx.fillText('Game Over!', canvas.width/2, canvas.height/2);
    ctx.font = '20px Arial';
    ctx.fillText('Score: ' + score, canvas.width/2, canvas.height/2 + 30);
    return;
  }

  snake.unshift(newHead);
}

// Initial draw
initGame();
ctx.fillStyle = '#f5f5f5';
ctx.fillRect(0, 0, canvas.width, canvas.height);
ctx.fillStyle = '#1565c0';
ctx.font = '20px Arial';
ctx.textAlign = 'center';
ctx.fillText('Press Start to Play', canvas.width/2, canvas.height/2);
</script>
