<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>A Little Birthday Surprise ❤️</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      font-family: "Trebuchet MS", cursive, sans-serif;
      text-align: center;
      color: #4a1730;
      background: linear-gradient(135deg, #ff9a9e, #fecfef, #ff758c);
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      overflow-x: hidden;
    }

    .container {
      width: 100%;
      max-width: 650px;
    }

    .screen {
      display: none;
      animation: fadeIn 0.6s ease;
    }

    .screen.active {
      display: block;
    }

    h1 {
      font-size: 2.8rem;
      margin-bottom: 10px;
      color: #a30f48;
    }

    h2 {
      font-size: 2rem;
      color: #a30f48;
    }

    p {
      font-size: 1.25rem;
      line-height: 1.5;
    }

    /* HEART */

    .heart {
      width: 150px;
      height: 150px;
      margin: 40px auto;
      background: #ff3f68;
      position: relative;
      transform: rotate(-45deg);
      cursor: pointer;
      animation: heartbeat 1.2s infinite;
      box-shadow: 0 10px 30px rgba(150, 0, 50, 0.25);
    }

    .heart:before,
    .heart:after {
      content: "";
      width: 150px;
      height: 150px;
      background: #ff3f68;
      border-radius: 50%;
      position: absolute;
    }

    .heart:before {
      top: -75px;
      left: 0;
    }

    .heart:after {
      left: 75px;
      top: 0;
    }

    .heart-text {
      position: absolute;
      z-index: 5;
      transform: rotate(45deg);
      width: 150px;
      top: 52px;
      left: 0;
      color: white;
      font-size: 1.1rem;
      font-weight: bold;
    }

    /* PUZZLE */

    .card {
      background: rgba(255, 255, 255, 0.88);
      border-radius: 25px;
      padding: 30px 25px;
      box-shadow: 0 15px 40px rgba(120, 0, 50, 0.18);
    }

    .puzzle-number {
      color: #ff4775;
      font-weight: bold;
      font-size: 1rem;
      letter-spacing: 2px;
    }

    .question {
      font-size: 1.5rem;
      font-weight: bold;
      margin: 25px 0;
    }

    .answers {
      display: flex;
      flex-direction: column;
      gap: 12px;
      max-width: 400px;
      margin: auto;
    }

    .answer {
      border: none;
      padding: 15px;
      border-radius: 15px;
      background: #ff6f91;
      color: white;
      font-size: 1.1rem;
      cursor: pointer;
      transition: 0.25s;
    }

    .answer:hover {
      transform: scale(1.04);
      background: #e94570;
    }

    .wrong {
      background: #555 !important;
      animation: shake 0.35s;
    }

    .unlocked {
      margin-top: 25px;
      font-size: 1.2rem;
      color: #a30f48;
      font-weight: bold;
    }

    .letter {
      display: inline-flex;
      width: 55px;
      height: 55px;
      justify-content: center;
      align-items: center;
      background: #ff3f68;
      color: white;
      border-radius: 15px;
      font-size: 1.7rem;
      margin: 5px;
      box-shadow: 0 5px 15px rgba(150, 0, 50, 0.2);
      animation: pop 0.5s ease;
    }

    .next-btn,
    .start-btn {
      margin-top: 25px;
      padding: 14px 30px;
      border: none;
      border-radius: 30px;
      background: #a30f48;
      color: white;
      font-size: 1.15rem;
      cursor: pointer;
      transition: 0.25s;
    }

    .next-btn:hover,
    .start-btn:hover {
      transform: scale(1.08);
      background: #7d0c38;
    }

    /* FINAL */

    .final-heart {
      font-size: 5rem;
      animation: heartbeat 1s infinite;
    }

    .invite {
      background: rgba(255, 255, 255, 0.9);
      border-radius: 25px;
      padding: 30px 20px;
      box-shadow: 0 15px 40px rgba(120, 0, 50, 0.2);
    }

    .invite h1 {
      font-size: 2.5rem;
    }

    .details {
      font-size: 1.3rem;
      margin: 20px 0;
    }

    .secret-message {
      font-size: 1.4rem;
      font-weight: bold;
      color: #a30f48;
      margin-top: 25px;
    }

    /* CONFETTI */

    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      top: -20px;
      animation: fall 3s linear forwards;
      z-index: 100;
    }

    @keyframes heartbeat {
      0%, 100% {
        transform: rotate(-45deg) scale(1);
      }

      50% {
        transform: rotate(-45deg) scale(1.12);
      }
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(15px);
      }

      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes pop {
      0% {
        transform: scale(0);
      }

      80% {
        transform: scale(1.15);
      }

      100% {
        transform: scale(1);
      }
    }

    @keyframes shake {
      0%, 100% {
        transform: translateX(0);
      }

      25% {
        transform: translateX(-8px);
      }

      75% {
        transform: translateX(8px);
      }
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(720deg);
      }
    }

    @media (max-width: 600px) {
      h1 {
        font-size: 2.2rem;
      }

      h2 {
        font-size: 1.7rem;
      }

      .heart {
        width: 120px;
        height: 120px;
      }

      .heart:before,
      .heart:after {
        width: 120px;
        height: 120px;
      }

      .heart:before {
        top: -60px;
      }

      .heart:after {
        left: 60px;
      }

      .heart-text {
        width: 120px;
        top: 40px;
      }
    }
  </style>
</head>

<body>

<div class="container">

  <!-- START SCREEN -->
  <section id="start" class="screen active">

    <h1>A Little Surprise ❤️</h1>

    <p>
      I have something special for you...
    </p>

    <p>
      But first, you have to solve a few puzzles. 🧩
    </p>

    <div class="heart" onclick="startGame()">
      <div class="heart-text">
        TAP ME
      </div>
    </div>

    <p>
      ❤️ Tap the heart to begin ❤️
    </p>

  </section>


  <!-- PUZZLE SCREEN -->
  <section id="puzzleScreen" class="screen">

    <div class="card">

      <div class="puzzle-number" id="puzzleNumber">
        PUZZLE 1 OF 7
      </div>

      <h2>🧩 Solve this!</h2>

      <div class="question" id="question"></div>

      <div class="answers" id="answers"></div>

      <div class="unlocked" id="unlocked"></div>

      <button
        class="next-btn"
        id="nextBtn"
        onclick="nextPuzzle()"
        style="display:none;">
        Next ❤️
      </button>

    </div>

  </section>


  <!-- FINAL SCREEN -->
  <section id="final" class="screen">

    <div class="invite">

      <div class="final-heart">
        ❤️
      </div>

      <h1>🎉 You're Invited! 🎉</h1>

      <p class="secret-message">
        You solved all the clues!
      </p>

      <p>
        So here's your reward...
      </p>

      <div class="details">

        <p>
          🎂 <strong>Birthday Celebration</strong>
        </p>

        <p>
          📅 <strong>Tomorrow — 7 September</strong>
        </p>

        <p>
          📍 <strong>Pacific Place, Jakarta</strong>
        </p>

      </div>

      <p>
        Can't wait to celebrate with you! ❤️
      </p>

      <p style="font-size: 2rem;">
        🎂 🎉 🥳 💕
      </p>

    </div>

  </section>

</div>


<script>

  const puzzles = [

    {
      question: "What comes next? 🍎 🍌 🍎 🍌 ?",
      answers: ["🍎", "🍊", "🍉", "🍓"],
      correct: 0,
      letter: "P"
    },

    {
      question: "How many days are in a week?",
      answers: ["5", "6", "7", "8"],
      correct: 2,
      letter: "A"
    },

    {
      question: "Which one doesn't belong?",
      answers: ["🐶", "🐱", "🐰", "🍕"],
      correct: 3,
      letter: "C"
    },

    {
      question: "What is 2 + 3?",
      answers: ["4", "5", "6", "7"],
      correct: 1,
      letter: "I"
    },

    {
      question: "Which one is a fruit? 🍎",
      answers: ["🍎 Apple", "🥕 Carrot", "🥔 Potato", "🌽 Corn"],
      correct: 0,
      letter: "F"
    },

    {
      question: "Complete the pattern: ❤️ 💕 ❤️ 💕 ?",
      answers: ["❤️", "⭐", "🌙", "🎈"],
      correct: 0,
      letter: "I"
    },

    {
      question: "What do birthdays usually have? 🎂",
      answers: ["Cake", "Homework", "Rain", "Snow"],
      correct: 0,
      letter: "C"
    }

  ];

  let currentPuzzle = 0;
  let unlockedLetters = [];


  function startGame() {

    document.getElementById("start").classList.remove("active");

    document.getElementById("puzzleScreen").classList.add("active");

    showPuzzle();

  }


  function showPuzzle() {

    const puzzle = puzzles[currentPuzzle];

    document.getElementById("puzzleNumber").textContent =
      "PUZZLE " + (currentPuzzle + 1) + " OF " + puzzles.length;

    document.getElementById("question").textContent =
      puzzle.question;

    const answersContainer =
      document.getElementById("answers");

    answersContainer.innerHTML = "";

    document.getElementById("unlocked").innerHTML = "";

    document.getElementById("nextBtn").style.display = "none";


    puzzle.answers.forEach((answer, index) => {

      const button = document.createElement("button");

      button.className = "answer";

      button.textContent = answer;

      button.onclick = function() {

        checkAnswer(index, button);

      };

      answersContainer.appendChild(button);

    });

  }


  function checkAnswer(index, button) {

    const puzzle = puzzles[currentPuzzle];

    if (index === puzzle.correct) {

      // Prevent clicking multiple times
      const allButtons =
        document.querySelectorAll(".answer");

      allButtons.forEach(btn => {
        btn.disabled = true;
      });


      unlockedLetters.push(puzzle.letter);


      document.getElementById("unlocked").innerHTML =
        "🔓 Letter unlocked!<br><br>" +
        '<span class="letter">' +
        puzzle.letter +
        "</span>";


      button.style.background = "#39a96b";

      document.getElementById("nextBtn").style.display =
        "inline-block";

    } else {

      button.classList.add("wrong");

      button.textContent = "❌ Try again!";

      setTimeout(() => {

        button.classList.remove("wrong");

        button.textContent =
          puzzle.answers[index];

      }, 700);

    }

  }


  function nextPuzzle() {

    currentPuzzle++;

    if (currentPuzzle < puzzles.length) {

      showPuzzle();

    } else {

      showFinal();

    }

  }


  function showFinal() {

    document.getElementById("puzzleScreen")
      .classList.remove("active");

    document.getElementById("final")
      .classList.add("active");

    createConfetti();

  }


  function createConfetti() {

    const symbols = ["🎉", "💕", "✨", "🎂", "❤️", "🥳"];

    for (let i = 0; i < 80; i++) {

      const confetti =
        document.createElement("div");

      confetti.className = "confetti";

      confetti.textContent =
        symbols[Math.floor(Math.random() * symbols.length)];

      confetti.style.left =
        Math.random() * 100 + "vw";

      confetti.style.animationDelay =
        Math.random() * 2 + "s";

      confetti.style.fontSize =
        (Math.random() * 15 + 10) + "px";

      document.body.appendChild(confetti);

      setTimeout(() => {
        confetti.remove();
      }, 5000);

    }

  }

</script>

</body>
</html>
