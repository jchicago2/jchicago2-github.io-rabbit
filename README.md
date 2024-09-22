# jchicago2-github.io-rabbit
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rabbit Guessing Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #f4f4f4;
      padding: 20px;
    }
    h1 {
      color: #333;
    }
    .game-container {
      display: flex;
      justify-content: space-around;
      margin-top: 20px;
    }
    .rabbit {
      width: 100px;
      height: 100px;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .rabbit:hover {
      transform: scale(1.1);
    }
    .message {
      margin-top: 20px;
      font-size: 1.2em;
      color: #333;
    }
    .gold-cup {
      width: 50px;
      height: 50px;
      display: none;
    }
  </style>
</head>
<body>

  <h1>Guess the Rabbit Hiding the Gold Cup!</h1>
  <div class="game-container">
    <img src="https://img.icons8.com/emoji/100/rabbit-emoji.png" alt="Rabbit 1" class="rabbit" id="rabbit1" onclick="makeGuess(1)">
    <img src="https://img.icons8.com/emoji/100/rabbit-emoji.png" alt="Rabbit 2" class="rabbit" id="rabbit2" onclick="makeGuess(2)">
    <img src="https://img.icons8.com/emoji/100/rabbit-emoji.png" alt="Rabbit 3" class="rabbit" id="rabbit3" onclick="makeGuess(3)">
    <img src="https://img.icons8.com/emoji/100/rabbit-emoji.png" alt="Rabbit 4" class="rabbit" id="rabbit4" onclick="makeGuess(4)">
  </div>
  
  <div class="message" id="message">Make a guess!</div>
  <img src="https://img.icons8.com/color/48/trophy.png" alt="Gold Cup" id="goldCup" class="gold-cup">

  <script>
    const goldPosition = Math.floor(Math.random() * 4) + 1; // Randomly choose 1-4
    const message = document.getElementById("message");
    const goldCup = document.getElementById("goldCup");

    function makeGuess(guess) {
      if (guess === goldPosition) {
        message.textContent = "Congratulations! You found the gold cup!";
        goldCup.style.display = "inline";
      } else {
        message.textContent = "Sorry, no cup under this rabbit. Try again!";
        goldCup.style.display = "none";
      }
    }
  </script>

</body>
</html>
