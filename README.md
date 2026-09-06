<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>For You ❤️</title>

<style>

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  font-family: "Trebuchet MS", Arial, sans-serif;
  background: linear-gradient(135deg, #ff9a9e, #fecfef, #ff758c);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  color: #4a1730;
  overflow-x: hidden;
}

#app {
  width: 100%;
  max-width: 650px;
}

/* GENERAL */

.hidden {
  display: none !important;
}

.card {
  background: rgba(255,255,255,0.94);
  padding: 30px 25px;
  border-radius: 28px;
  box-shadow: 0 15px 45px rgba(100,0,40,0.2);
  animation: appear 0.5s ease;
}

h1 {
  color: #a30f48;
  font-size: 2.7rem;
}

h2 {
  color: #a30f48;
  font-size: 2rem;
}

p {
  font-size: 1.2rem;
  line-height: 1.5;
}

/* START HEART */

.heart {
  width: 140px;
  height: 140px;
  background: #ff3f68;
  margin: 55px auto;
  position: relative;
  transform: rotate(-45deg);
  cursor: pointer;
  animation: heartbeat 1.2s infinite;
  box-shadow: 0 12px 30px rgba(150,0,50,0.25);
}

.heart:before,
.heart:after {
  content: "";
  width: 140px;
  height: 140px;
  background: #ff3f68;
  border-radius: 50%;
  position: absolute;
}

.heart:before {
  top: -70px;
  left: 0;
}

.heart:after {
  top: 0;
  left: 70px;
}

.heart span {
  position: absolute;
  z-index: 10;
  width: 140px;
  color: white;
  font-weight: bold;
  font-size: 17px;
  transform: rotate(45deg);
  top: 52px;
  left: 0;
}

/* QUESTION */

.progress {
  color: #ff4775;
  font-weight: bold;
  letter-spacing: 2px;
  font-size: 0.9rem;
}

.question {
  font-size: 1.55rem;
  font-weight: bold;
  margin: 25px 0;
}

.answer {
  width: 100%;
  max-width: 480px;
  display: block;
  margin: 11px auto;
  padding: 15px 12px;
  border: none;
  border-radius: 18px;
  background: #ff5c82;
  color: white;
  font-size: 1.08rem;
  cursor: pointer;
  transition: 0.2s;
}

.answer:hover {
  transform: scale(1.03);
  background: #e83d69;
}

.answer.correct {
  background: #35a86b !important;
}

.answer.wrong {
  background: #555 !important;
  animation: shake 0.35s;
}

.message {
  min-height: 35px;
  margin-top: 18px;
  font-weight: bold;
  color: #a30f48;
}

.next {
  border: none;
  border-radius: 30px;
  padding: 14px 32px;
  margin-top: 15px;
  background: #a30f48;
  color: white;
  font-size: 1.1rem;
  cursor: pointer;
}

.next:hover {
  background: #790b35;
  transform: scale(1.05);
}

/* FINAL */

.final-heart {
  font-size: 75px;
  animation: heartbeat 1s infinite;
}

.invite-date {
  background: #fff0f5;
  border-radius: 20px;
  padding: 20px;
  margin: 20px 0;
}

.invite-date p {
  margin: 12px 0;
}

.final-message {
  font-size: 1.35rem;
  color: #a30f48;
  font-weight: bold;
}

/* ANIMATIONS */

@keyframes heartbeat {

  0%,100% {
    transform: rotate(-45deg) scale(1);
  }

  50% {
    transform: rotate(-45deg) scale(1.1);
  }

}

@keyframes appear {

  from {
    opacity: 0;
    transform: translateY(15px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }

}

@keyframes shake {

  0%,100% {
    transform: translateX(0);
  }

  25% {
    transform: translateX(-8px);
  }

  75% {
    transform: translateX(8px);
  }

}

.confetti {
  position: fixed;
  top: -30px;
  z-index: 100;
  font-size: 25px;
  animation: fall 3s linear forwards;
}

@keyframes fall {

  to {
    transform: translateY(110vh) rotate(720deg);
  }

}

@media(max-width:600px) {

  h1 {
    font-size: 2.2rem;
  }

  h2 {
    font-size: 1.7rem;
  }

  .card {
    padding: 25px 18px;
  }

  .heart {
    width: 115px;
    height: 115px;
  }

  .heart:before,
  .heart:after {
    width: 115px;
    height: 115px;
  }

  .heart:before {
    top: -57px;
  }

  .heart:after {
    left: 57px;
  }

  .heart span {
    width: 115px;
    top: 42px;
    font-size: 14px;
  }

}

</style>
</head>

<body>

<div id="app">

  <!-- START -->

  <div id="start">

    <h1>Hey You ❤️</h1>

    <p>
      I have a little surprise for you...
    </p>

    <p>
      But first, let's see how well you know us. 👀
    </p>

    <div class="heart" onclick="startGame()">
      <span>TAP ME</span>
    </div>

    <p>
      ❤️ Tap the heart to begin ❤️
    </p>

  </div>


  <!-- GAME -->

  <div id="game" class="card hidden">

    <div id="progress" class="progress"></div>

    <h2 id="title"></h2>

    <div id="question" class="question"></div>

    <div id="answers"></div>

    <div id="message" class="message"></div>

    <button
      id="next"
      class="next hidden"
      onclick="nextQuestion()">
      Next ❤️
    </button>

  </div>


  <!-- FINAL -->

  <div id="final" class="card hidden">

    <div class="final-heart">
      ❤️
    </div>

    <h1>YOU PASSED! 🎉</h1>

    <p>
      Okay... clearly you know me pretty well. 😌
    </p>

    <p class="final-message">
      So I think you deserve to know what's happening tomorrow...
    </p>

    <div class="invite-date">

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
      Can't wait to see you there ❤️
    </p>

    <p style="font-size:40px;">
      🎂 🎉 🥳 💕
    </p>

  </div>

</div>


<script>

/* =================================
   YOUR QUESTIONS
================================= */

const questions = [

  {
    title: "🎂 Question 1",
    question: "Whose birthday is today?",
    answers: [
      "You",
      "YOUUUUUUUU",
      "YOUUUUUUUUUUUUUUUU",
      "TE AMO"
    ],
    correct: 2
  },

  {
    title: "💕 Question 2",
    question: "Your nickname?",
    answers: [
      "Baby",
      "Magnolia",
      "Ratu Duta Kanjeng .....",
      "Princess"
    ],
    correct: 2
  },

  {
    title: "🦸 Question 3",
    question: "My fav Kamen Rider?",
    answers: [
      "Ryuki",
      "Kabuto",
      "Kyuga",
      "OOO",
      "Fourze"
    ],
    correct: 1
  },

  {
    title: "🧸 Question 4",
    question: "Your fav character?",
    answers: [
      "Lotso",
      "Stitch",
      "Hirono",
      "Unicorn"
    ],
    correct: 0
  },

  {
    title: "👗 Question 5",
    question: "My fav brand?",
    answers: [
      "Dior",
      "Chanel",
      "LV",
      "Loro Piana",
      "Kanoa"
    ],
    correct: 4
  },

  {
    title: "❤️ Final Question",
    question: "Who loves you?",
    answers: [
      "MEEEEEE",
      "Your bf",
      "William",
      "Random post",
      "All of the above"
    ],
    correct: 4
  }

];


/* =================================
   GAME VARIABLES
================================= */

let currentQuestion = 0;


/* =================================
   START
================================= */

function startGame() {

  document.getElementById("start")
    .classList.add("hidden");

  document.getElementById("game")
    .classList.remove("hidden");

  showQuestion();

}


/* =================================
   SHOW QUESTION
================================= */

function showQuestion() {

  const q = questions[currentQuestion];

  document.getElementById("progress").innerText =
    "QUESTION " +
    (currentQuestion + 1) +
    " OF " +
    questions.length;

  document.getElementById("title").innerText =
    q.title;

  document.getElementById("question").innerText =
    q.question;

  document.getElementById("message").innerText = "";

  document.getElementById("next")
    .classList.add("hidden");


  const answers =
    document.getElementById("answers");

  answers.innerHTML = "";


  q.answers.forEach(function(answer, index) {

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


/* =================================
   CHECK ANSWER
================================= */

function checkAnswer(index, button) {

  const q = questions[currentQuestion];


  /* CORRECT */

  if (index === q.correct) {

    button.classList.add("correct");

    document.getElementById("message").innerText =
      "CORRECT 😌❤️ I knew you knew this.";


    const allButtons =
      document.querySelectorAll(".answer");

    allButtons.forEach(function(btn) {

      btn.disabled = true;

    });


    document.getElementById("next")
      .classList.remove("hidden");

  }


  /* WRONG */

  else {

    button.classList.add("wrong");

    document.getElementById("message").innerText =
      "Really? 😭 You better try again.";


    setTimeout(function() {

      button.classList.remove("wrong");

      document.getElementById("message").innerText = "";

    }, 900);

  }

}


/* =================================
   NEXT QUESTION
================================= */

function nextQuestion() {

  currentQuestion++;

  if (currentQuestion >= questions.length) {

    showFinal();

  }

  else {

    showQuestion();

  }

}


/* =================================
   FINAL INVITATION
================================= */

function showFinal() {

  document.getElementById("game")
    .classList.add("hidden");

  document.getElementById("final")
    .classList.remove("hidden");

  makeConfetti();

}


/* =================================
   CONFETTI
================================= */

function makeConfetti() {

  const emojis = [
    "❤️",
    "💕",
    "🎉",
    "🎂",
    "✨",
    "🥳"
  ];


  for (let i = 0; i < 70; i++) {

    const piece =
      document.createElement("div");

    piece.className = "confetti";

    piece.innerText =
      emojis[
        Math.floor(
          Math.random() * emojis.length
        )
      ];

    piece.style.left =
      Math.random() * 100 + "vw";

    piece.style.animationDelay =
      Math.random() * 2 + "s";

    document.body.appendChild(piece);


    setTimeout(function() {

      piece.remove();

    }, 5000);

  }

}

</script>

</body>
</html>
