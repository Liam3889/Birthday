<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Birthday Invitation</title>
  <style>
    body {
      margin: 0;
      font-family: cursive, sans-serif;
      text-align: center;
      background: linear-gradient(135deg, #ff9a9e, #fecfef, #ff758c);
      color: #333;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      padding: 20px;
    }

    h1 {
      font-size: 3em;
      color: #b0134d;
      margin-bottom: 10px;
    }

    p {
      font-size: 1.5em;
      margin: 10px 0;
    }

    .buttons {
      margin-top: 20px;
      position: relative;
      height: 80px;
    }

    button {
      font-size: 1.5em;
      padding: 12px 25px;
      border: none;
      cursor: pointer;
      border-radius: 30px;
      margin: 5px;
      transition: all 0.3s ease;
    }

    .yes {
      background-color: #ff4d4d;
      color: white;
    }

    .yes:hover {
      background-color: #ff1a1a;
      transform: scale(1.1);
    }

    .no {
      background-color: #333;
      color: white;
      position: absolute;
    }

    .invite {
      display: none;
      margin-top: 40px;
      background: rgba(255,255,255,0.7);
      padding: 20px;
      border-radius: 15px;
    }
  </style>
</head>

<body>

  <h1>Will you come celebrate your Birthday?</h1>

  <p>
    🎂 Let's celebrate <strong>tomorrow, 7 September</strong>
    at <strong>Pacific Place, Jakarta</strong> 🎉
  </p>

  <div class="buttons">
    <button class="yes" onclick="showInvite()">Yes</button>
    <button class="no" id="noBtn" onmouseover="moveNo()">No</button>
  </div>

  <div class="invite" id="invite">
    <h2>🎉 You're Invited! 🎉</h2>
    <p>📅 Date: 7 September</p>
    <p>📍 Location: Pacific Place, Jakarta</p>
    <p>Can't wait to see you there! ❤️</p>
  </div>

  <script>
    let yesSize = 1.5;

    function showInvite() {
      document.getElementById("invite").style.display = "block";
    }

    function moveNo() {
      const noBtn = document.getElementById("noBtn");

      noBtn.style.top =
        Math.random() * (window.innerHeight - 50) + "px";

      noBtn.style.left =
        Math.random() * (window.innerWidth - 100) + "px";

      // Grow the Yes button
      const yesBtn = document.querySelector(".yes");
      yesSize += 0.3;
      yesBtn.style.fontSize = yesSize + "em";
    }
  </script>

</body>
</html>
