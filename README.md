<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Birthday Surprise ❤️</title>

<style>

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  font-family: Arial, sans-serif;
  text-align: center;
  background: linear-gradient(135deg, #ff9a9e, #fecfef, #ff758c);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  color: #4a1730;
}

#app {
  width: 100%;
  max-width: 600px;
}

/* HEART */

.heart {
  width: 130px;
  height: 130px;
  background: #ff3f68;
  margin: 50px auto;
  transform: rotate(-45deg);
  position: relative;
  cursor: pointer;
  animation: beat 1.2s infinite;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

.heart:before,
.heart:after {
  content: "";
  width: 130px;
  height: 130px;
  background: #ff3f68;
  border-radius: 50%;
  position: absolute;
}

.heart:before {
  top: -65px;
  left: 0;
}

.heart:after {
  top: 0;
  left: 65px;
}

.heart span {
  position: absolute;
  z-index: 10;
  color: white;
  font-weight: bold;
  font-size: 18px;
  width: 130px;
  transform: rotate(45deg);
  top: 48px;
  left: 0;
}

@keyframes beat {

  0%,100% {
    transform: rotate(-45deg) scale(1);
  }

  50% {
    transform: rotate(-45deg) scale(1.1);
  }

}

/* CARD */

.card {
  background: rgba(255,255,255,0.92);
  padding: 30px;
  border-radius: 25px;
  box-shadow: 0 15px 40px rgba(0,0,0,0.2);
}

h1 {
  color: #a30f48;
  font-size: 2.5rem;
}

h2 {
  color: #a30f48;
}

p {
  font-size: 1.2rem;
  line-height: 1.5;
}

.question {
  font-size: 1.4rem;
  font-weight: bold;
  margin: 25px 0;
}

.answer {
  display: block;
  width: 100%;
  max-width: 400px;
  margin: 10px auto;
  padding: 15px;
  border: none;
  border-radius: 15px;
  background: #ff5c82;
  color: white;
  font-size: 1.1rem;
  cursor: pointer;
}

.answer:hover {
  background: #e93666;
  transform: scale(1.03);
}

.next {
  margin-top: 20px;
  padding: 14px 30px;
  border: none;
  border-radius: 30px;
  background: #a30f48;
  color: white;
  font-size: 1.1rem;
  cursor: pointer;
}

.next:hover {
  background: #7d0c38;
}

.letter {
  display: inline-block;
  background: #ff3f68;
  color: white;
  padding: 10px 17px;
  border-radius: 12px;
  font-size: 25px;
  font-weight: bold;
  margin-top: 15px;
}

.wrong {
  background: #555 !important;
}

.hidden {
  display: none;
}

/* CONFETTI */

.confetti {
  position: fixed;
  top: -30px;
  font-size: 25px;
  animation: fall 3s linear forwards;
}

@keyframes fall {

  from {
    transform: translateY(0) rotate(0deg);
  }

  to {
    transform: translateY(110vh) rotate(720deg);
  }

}

</style>
</head>

<body>

<div id="app">

  <!-- START -->

  <div id="start">

    <h1>A Little Surprise ❤️</h1>

    <p>
      I have something special for you...
    </p>

    <p>
      But first, solve a few puzzles! 🧩
    </p>

    <div class="heart" onclick="startGame()">
      <span>TAP ME</span>
    </div>

    <p>❤️ Tap the heart ❤️</p>

  </div>


  <!-- PUZZLE -->

  <div id="game" class="card hidden">

    <p id="counter"></p>

    <h2>🧩 Solve the Puzzle</h2>

    <div id="question" class="question"></div>

    <div id="answers"></div>

    <div id="result"></div>

    <button
      id="next"
      class="next hidden"
      onclick="nextPuzzle()">
      Next ❤️
    </button>

  </div>


  <!-- FINAL -->

  <div id="final" class="card hidden">

    <div style="font-size:70px;">
      ❤️
    </div>

    <h1>🎉 You're Invited! 🎉</h1>

    <p>
      You solved all the puzzles!
    </p>

    <hr>

    <p>
      🎂 <strong>Birthday Celebration</strong>
    </p>

    <p>
      📅 <strong>Tomorrow — 7 September</strong>
    </p>

    <p>
      📍 <strong>Pacific Place, Jakarta</strong>
    </p>

    <p>
      Can't wait to see you there! ❤️
    </p>

    <p style="font-size:35px;">
      🎂 🎉 🥳 💕
    </p>

  </div>

</div>


<script>

/*
====================================
PUZZLES
====================================
*/

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
    question: "Which one is a fruit?",
    answers: [
      "🍎 Apple",
      "🥕 Carrot",
      "🥔 Potato",
      "🥦 Broccoli"
    ],
    correct: 0,
    letter: "F"
  },

  {
    question: "Complete the pattern: ❤️ 💕 ❤️ 💕 ?",
    answers: [
      "❤️",
      "⭐",
      "🌙",
      "🎈"
    ],
    correct: 0,
    letter: "I"
  },

  {
    question: "What do birthdays usually have? 🎂",
    answers: [
      "Cake 🎂",
      "Homework 📚",
      "Rain 🌧️",
      "Snow ❄️"
    ],
    correct: 0,
    letter: "C"
  }

];


/*
====================================
GAME VARIABLES
====================================
*/

let current = 0;

let letters = [];


/*
====================================
START GAME
====================================
*/

function startGame() {

  document.getElementById("start").classList.add("hidden");

  document.getElementById("game").classList.remove("hidden");

  showPuzzle();

}


/*
====================================
SHOW PUZZLE
====================================
*/

function showPuzzle() {

  const puzzle = puzzles[current];

  document.getElementById("counter").innerText =
    "Puzzle " + (current + 1) + " of " + puzzles.length;

  document.getElementById("question").innerText =
    puzzle.question;

  document.getElementById("result").innerHTML = "";

  document.getElementById("next").classList.add("hidden");

  const answers =
    document.getElementById("answers");

  answers.innerHTML = "";


  puzzle.answers.forEach(function(answer, index) {

    const button =
      document.createElement("button");

    button.className = "answer";

    button.innerText = answer;

    button.onclick = function() {

      checkAnswer(index, button);

    };

    answers.appendChild(button);

  });

}


/*
====================================
CHECK ANSWER
====================================
*/

function checkAnswer(index, button) {

  const puzzle = puzzles[current];


  if (index === puzzle.correct) {

    letters.push(puzzle.letter);

    button.style.background = "#35a86b";

    document.getElementById("result").innerHTML =
      "<p>🎉 Correct!</p>" +
      "<p>You unlocked:</p>" +
      '<div class="letter">' +
      puzzle.letter +
      "</div>";


    document.getElementById("next")
      .classList.remove("hidden");


    const buttons =
      document.querySelectorAll(".answer");

    buttons.forEach(function(btn) {

      btn.disabled = true;

    });

  }

  else {

    button.classList.add("wrong");

    button.innerText = "❌ Nope! Try again";

    setTimeout(function() {

      button.classList.remove("wrong");

      button.innerText =
        puzzle.answers[index];

    }, 800);

  }

}


/*
====================================
NEXT PUZZLE
====================================
*/

function nextPuzzle() {

  current++;

  if (current >= puzzles.length) {

    showFinal();

  }

  else {

    showPuzzle();

  }

}


/*
====================================
FINAL
====================================
*/

function showFinal() {

  document.getElementById("game")
    .classList.add("hidden");

  document.getElementById("final")
    .classList.remove("hidden");

  confetti();

}


/*
====================================
CONFETTI
====================================
*/

function confetti() {

  const emojis = [
    "🎉",
    "❤️",
    "💕",
    "✨",
    "🎂",
    "🥳"
  ];


  for (let i = 0; i < 80; i++) {

    const item =
      document.createElement("div");

    item.className = "confetti";

    item.innerText =
      emojis[Math.floor(Math.random() * emojis.length)];

    item.style.left =
      Math.random() * 100 + "vw";

    item.style.animationDelay =
      Math.random() * 2 + "s";

    document.body.appendChild(item);

    setTimeout(function() {

      item.remove();

    }, 5000);

  }

}

</script>

</body>
</html>
