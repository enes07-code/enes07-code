<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Enes'in Oyunu</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body, html {
      height: 100%;
      font-family: Arial, sans-serif;
      overflow-x: hidden;
    }
    .splash {
      background-color: white;
      color: black;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      font-size: 5rem;
      font-weight: bold;
      animation: fadeOut 1s forwards;
    }
    @keyframes fadeOut {
      0% { opacity: 1; }
      100% { opacity: 0; visibility: hidden; }
    }
    .game-container {
      display: none;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      background: #f5f5f5;
      padding: 20px;
      text-align: center;
      position: relative;
    }
    .game-container h1 {
      color: black;
      margin-bottom: 20px;
    }
    .game-container .title {
      font-size: 24px;
      color: black;
      margin-bottom: 10px;
      font-weight: bold;
    }
    .question {
      font-size: 20px;
      margin: 20px 0;
    }
    .options button {
      margin: 10px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      border: none;
      background-color: #333;
      color: white;
      border-radius: 5px;
      transition: background-color 0.3s;
    }
    .options button:hover {
      background-color: #555;
    }
    .result {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
    }
    .insta-follow {
      margin-top: 30px;
    }
    .insta-follow img {
      width: 100px;
      border-radius: 50%;
      margin-bottom: 10px;
    }
    .insta-follow a {
      font-size: 18px;
      color: #d6249f;
      text-decoration: none;
      font-weight: bold;
    }
    .hidden {
      display: none;
    }
    .confetti {
      position: absolute;
      top: 0;
      width: 100%;
      height: 0;
      overflow: visible;
      pointer-events: none;
    }
    .confetti-piece {
      width: 10px;
      height: 10px;
      position: absolute;
      background-color: red;
      animation: fall linear forwards;
    }
    @keyframes fall {
      0% { transform: translateY(0); opacity: 1; }
      100% { transform: translateY(100vh); opacity: 0; }
    }
  </style>
</head>
<body>
  <div class="splash" id="splash">Enes</div>
  <div class="game-container" id="game">
    <h1>Benimle bir oyuna var mısın?</h1>
    <div class="title">Enes😐</div>
    <div class="question">237 x (15 + 8) - 129 = ?</div>
    <div class="options">
      <button onclick="checkAnswer(false)">5247</button>
      <button onclick="checkAnswer(true)">5232</button>
    </div>
    <div class="result" id="result"></div>
    <div class="insta-follow hidden" id="follow">
      <img src="https://instagram.fist13-1.fna.fbcdn.net/v/t51.2885-19/387225207_859078018823338_2384066940476648471_n.jpg?stp=dst-jpg_s150x150&_nc_ht=instagram.fist13-1.fna.fbcdn.net&_nc_cat=106&_nc_ohc=1q5eAKkP3gsQ7kNvgG0cXQm&edm=APs17CUBAAAA&ccb=7-5&oh=00_AYB5j79OUAieY7PSSkAmMaLk0M4ktEvh7VE1_2r_4p1edA&oe=664F419A&_nc_sid=10d13b" alt="Enes Instagram">
      <p>Kaybettin! Şimdi beni Instagram'da takip et:</p>
      <a href="https://www.instagram.com/_eness._07_?igsh=b2lsNG5rMjJpaW5p" target="_blank">@_eness._07_</a>
    </div>
    <div class="insta-follow hidden" id="follow-win">
      <p>İstersen beni Instagram'da da takip edebilirsin:</p>
      <a href="https://www.instagram.com/_eness._07_?igsh=b2lsNG5rMjJpaW5p" target="_blank">@_eness._07_</a>
    </div>
    <div class="confetti" id="confetti"></div>
  </div>

  <script>
    setTimeout(() => {
      document.getElementById("splash").style.display = "none";
      document.getElementById("game").style.display = "flex";
    }, 1000);

    let answered = false;
    function checkAnswer(isCorrect) {
      if (answered) return;
      answered = true;
      const result = document.getElementById("result");
      const follow = document.getElementById("follow");
      if (isCorrect) {
        result.textContent = "Kazandın! Tebrikler! 🎉";
        document.getElementById("follow-win").classList.remove("hidden");
        launchConfetti();
      } else {
        result.textContent = "Yanlış cevap!";
        follow.classList.remove("hidden");
      }
    }

    function launchConfetti() {
      const confettiContainer = document.getElementById("confetti");
      for (let i = 0; i < 100; i++) {
        const confetti = document.createElement("div");
        confetti.classList.add("confetti-piece");
        confetti.style.left = Math.random() * 100 + "%";
        confetti.style.backgroundColor = getRandomColor();
        confetti.style.animationDuration = 2 + Math.random() * 3 + "s";
        confettiContainer.appendChild(confetti);
        setTimeout(() => confetti.remove(), 5000);
      }
    }

    function getRandomColor() {
      const colors = ["#ff0", "#0f0", "#0ff", "#f0f", "#f00", "#00f"];
      return colors[Math.floor(Math.random() * colors.length)];
    }
  </script>
</body>
</html>
