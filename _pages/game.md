---
permalink: /game/
title: "Mini Game"
excerpt: "A fun mini game"
author_profile: true
---

<div class="game-container" markdown="1">

# Click Challenge / 点击挑战

<p>Click the button as many times as you can in 10 seconds!</p>
<p>10秒内尽可能多地点击按钮！</p>

<div class="game-box">
  <p class="game-score">Score: <span id="score">0</span></p>
  <p class="game-timer">Time: <span id="timer">10</span>s</p>
  <button id="clickBtn" class="click-btn" onclick="handleClick()">CLICK ME!</button>
  <button id="startBtn" class="start-btn" onclick="startGame()">Start / 开始</button>
</div>

</div>

<style>
.game-container {
  text-align: center;
}

.game-box {
  padding: 20px;
  margin: 20px 0;
}

.game-score, .game-timer {
  font-size: 1.3em;
  font-weight: bold;
  color: #1565c0;
  margin: 10px 0;
}

.click-btn {
  width: 150px;
  height: 150px;
  font-size: 1.2em;
  font-weight: bold;
  background: #1565c0;
  color: white;
  border: none;
  border-radius: 50%;
  cursor: pointer;
  margin: 20px;
  transition: transform 0.1s;
}

.click-btn:hover {
  background: #0d47a1;
}

.click-btn:active {
  transform: scale(0.95);
}

.click-btn:disabled {
  background: #ccc;
  cursor: not-allowed;
}

.start-btn {
  padding: 10px 30px;
  font-size: 1em;
  background: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  display: block;
  margin: 10px auto;
}

.start-btn:hover {
  background: #388e3c;
}
</style>

<script>
var score = 0;
var timeLeft = 10;
var gameActive = false;
var timerInterval;

function startGame() {
  score = 0;
  timeLeft = 10;
  gameActive = true;
  document.getElementById('score').innerText = score;
  document.getElementById('timer').innerText = timeLeft;
  document.getElementById('clickBtn').disabled = false;
  document.getElementById('startBtn').disabled = true;

  timerInterval = setInterval(function() {
    timeLeft--;
    document.getElementById('timer').innerText = timeLeft;
    if (timeLeft <= 0) {
      endGame();
    }
  }, 1000);
}

function handleClick() {
  if (gameActive) {
    score++;
    document.getElementById('score').innerText = score;
  }
}

function endGame() {
  gameActive = false;
  clearInterval(timerInterval);
  document.getElementById('clickBtn').disabled = true;
  document.getElementById('startBtn').disabled = false;
  alert('Game Over! Your score: ' + score + '\n游戏结束！你的分数：' + score);
}

// Initial state
document.getElementById('clickBtn').disabled = true;
</script>
