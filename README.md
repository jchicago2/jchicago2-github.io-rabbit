<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rabbit Car Dodge</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      overflow: hidden;
      background-color: #f0f0f0;
    }
    h1 {
      text-align: center;
      color: #333;
    }
    .game-area {
      position: relative;
      width: 100%;
      height: 100vh;
      background-color: #87CEEB;
      overflow: hidden;
    }
    .road {
      position: absolute;
      width: 100%;
      height: 100%;
      background: #555;
      left: 0;
      top: 0;
    }
    .car {
      position: absolute;
      width: 60px;
      height: 100px;
      background-size: cover;
      bottom: 20px;
      left: calc(50% - 30px); /* Start at the middle */
    }
    .rabbit-hole {
      position: absolute;
      width: 60px;
      height: 60px;
      background-image: url('https://img.icons8.com/emoji/60/hole-emoji.png');
      background-size: cover;
      top: -60px;
    }
    .score {
      position: absolute;
      top: 10px;
      left: 10px;
      font-size: 18px;
      color: white;
    }
    .game-over {
      display: none;
      position: absolute;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.7);
      color: white;
      font-size: 40px;
      text-align: center;
      line-height: 100vh;
    }
  </style>
</head>
<body>

<h1>Rabbit Car Dodge</h1>
<div class="game-area">
  <div class="road"></div>
  <div class="car" id="car"></div>
  <div class="score" id="score">Score: 0</div>
  <div class="game-over" id="gameOver">Game Over! Press F5 to Restart</div>
</div>

<script>
  // Game variables
  const gameArea = document.querySelector('.game-area');
  const car = document.getElementById('car');
  const scoreDisplay = document.getElementById('score');
  const gameOverDisplay = document.getElementById('gameOver');
  let score = 0;
  let gameSpeed = 5;
  let gameRunning = true;

  // Key controls for car movement
  document.addEventListener('keydown', function(event) {
    if (!gameRunning) return;
    
    let left = parseInt(window.getComputedStyle(car).getPropertyValue('left'));

    if (event.key === 'ArrowLeft' && left > 10) {
      car.style.left = left - 20 + 'px';
    } else if (event.key === 'ArrowRight' && left < window.innerWidth - 70) {
      car.style.left = left + 20 + 'px';
    }
  });

  // Function to create and move rabbit holes
  function createRabbitHole() {
    const rabbitHole = document.createElement('div');
    rabbitHole.classList.add('rabbit-hole');
    rabbitHole.style.left = Math.random() * (window.innerWidth - 60) + 'px';
    gameArea.appendChild(rabbitHole);

    let holeInterval = setInterval(function() {
      let holeTop = parseInt(window.getComputedStyle(rabbitHole).getPropertyValue('top'));

      if (holeTop > window.innerHeight) {
       

