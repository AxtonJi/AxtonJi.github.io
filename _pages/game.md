---
permalink: /game/
title: "Snake Game"
excerpt: "A fun snake game"
author_profile: true
---

<div markdown="1">

# Snake Game / 贪吃蛇

Use arrow keys or WASD to control. 使用方向键或WASD控制。

</div>

<div style="text-align: center; margin: 20px 0;">
  <p style="font-size: 1.2em; color: #1565c0; font-weight: bold;">Score / 分数: <span id="score">0</span></p>
  <canvas id="game" width="400" height="400" style="border: 2px solid #1565c0; background: #fafafa;"></canvas>
  <br>
  <button id="startBtn" style="margin-top: 15px; padding: 10px 25px; font-size: 1em; background: #1565c0; color: white; border: none; border-radius: 5px; cursor: pointer;">Start / 开始</button>
</div>

<script>
var canvas = document.getElementById('game');
var ctx = canvas.getContext('2d');
var box = 20;
var snake = [];
var food = {};
var dir = '';
var score = 0;
var game = null;

function init() {
  snake = [{x: 10 * box, y: 10 * box}];
  food = newFood();
  dir = '';
  score = 0;
  document.getElementById('score').innerText = score;
}

function newFood() {
  return {
    x: Math.floor(Math.random() * 20) * box,
    y: Math.floor(Math.random() * 20) * box
  };
}

function draw() {
  ctx.fillStyle = '#fafafa';
  ctx.fillRect(0, 0, 400, 400);

  // Draw food
  ctx.fillStyle = '#e53935';
  ctx.fillRect(food.x, food.y, box, box);

  // Draw snake
  for (var i = 0; i < snake.length; i++) {
    ctx.fillStyle = i === 0 ? '#1565c0' : '#42a5f5';
    ctx.fillRect(snake[i].x, snake[i].y, box, box);
    ctx.strokeStyle = '#fff';
    ctx.strokeRect(snake[i].x, snake[i].y, box, box);
  }

  var headX = snake[0].x;
  var headY = snake[0].y;

  if (dir === 'LEFT') headX -= box;
  if (dir === 'UP') headY -= box;
  if (dir === 'RIGHT') headX += box;
  if (dir === 'DOWN') headY += box;

  // Check collision
  if (headX < 0 || headX >= 400 || headY < 0 || headY >= 400 || collision(headX, headY)) {
    clearInterval(game);
    ctx.fillStyle = 'rgba(0,0,0,0.6)';
    ctx.fillRect(0, 0, 400, 400);
    ctx.fillStyle = '#fff';
    ctx.font = '24px Times New Roman';
    ctx.textAlign = 'center';
    ctx.fillText('Game Over!', 200, 180);
    ctx.fillText('Score: ' + score, 200, 220);
    return;
  }

  // Eat food
  if (headX === food.x && headY === food.y) {
    score++;
    document.getElementById('score').innerText = score;
    food = newFood();
  } else {
    snake.pop();
  }

  snake.unshift({x: headX, y: headY});
}

function collision(x, y) {
  for (var i = 0; i < snake.length; i++) {
    if (x === snake[i].x && y === snake[i].y) return true;
  }
  return false;
}

document.addEventListener('keydown', function(e) {
  var key = e.keyCode;
  if ((key === 37 || key === 65) && dir !== 'RIGHT') dir = 'LEFT';
  else if ((key === 38 || key === 87) && dir !== 'DOWN') dir = 'UP';
  else if ((key === 39 || key === 68) && dir !== 'LEFT') dir = 'RIGHT';
  else if ((key === 40 || key === 83) && dir !== 'UP') dir = 'DOWN';
});

document.getElementById('startBtn').addEventListener('click', function() {
  if (game) clearInterval(game);
  init();
  game = setInterval(draw, 100);
});

// Initial screen
init();
ctx.fillStyle = '#fafafa';
ctx.fillRect(0, 0, 400, 400);
ctx.fillStyle = '#1565c0';
ctx.font = '18px Times New Roman';
ctx.textAlign = 'center';
ctx.fillText('Click Start to Play', 200, 200);
</script>
