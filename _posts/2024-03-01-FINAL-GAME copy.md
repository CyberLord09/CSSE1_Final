---
toc: true
comments: false
layout: default 
type: hacks
courses: { compsci: {week: 6} }
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>T.A.N.K.S</title>
  <style>
    body, html {
      margin: 0;
      padding: 0;
      width: 100%;
      height: 100%;
    }
    body {
      background: url("{{site.baseurl}}/images/sprite/TANK LOADING BLANK (1).png") no-repeat center center fixed;
      background-size: cover;
      color: #fff;
      font-family: 'Arial', sans-serif;
      text-align: center;
      overflow: hidden;
    }
    .button {
      background-color: transparent;
      color: #fff;
      font-size: 16px;
      cursor: pointer;
      font-family: 'Arial', sans-serif;
      border: none;
      outline: none;
      position: absolute;
      transform: translateX(-50%);
      transition: box-shadow 0.3s ease-out, color 0.3s ease-out;
      z-index: 1;
    }
    #instructionsButton {
      top: 805%;
      left: 78%;
      transform: translate(-50%, -50%);
    }
    #settingsButton {
      top: 805%;
      left: 4%;
      transform: translate(-50%, -50%);
    }
    #playButton {
      top: 805%;
      left: 41%;
      transform: translate(-50%, -50%);
    }
    .button:hover {
      box-shadow: 0 0 20px #ff4500, 0 0 40px #ff4500;
      color: #ff4500;
      animation: shake 0.5s ease-in-out infinite;
    }
    @keyframes shake {
      0%, 100% {
        transform: translate(-50%, -50%);
      }
      25%, 75% {
        transform: translate(-55%, -50%);
      }
      50% {
        transform: translate(-50%, -50%);
      }
    }
    .overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      z-index: 2;
    }
    .model {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
      z-index: 3;
    }
  </style>
</head>
<body>

  <button id="settingsButton" class="button" onclick="openSettings()">Settings</button>
  <button id="playButton" class="button" onclick="startGif()">Play</button>
  <button id="instructionsButton" class="button" onclick="openInstructions()">Instructions</button>

  <div id="settingsOverlay" class="overlay">
    <div class="model">
      <!-- add stuff -->
      <h2>Settings</h2>
      <!-- add stuff -->
      <button onclick="closeSettings()">Close</button>
    </div>
  </div>

  <div id="instructionsOverlay" class="overlay">
    <div class="model">
      <!-- add stuff -->
      <h2>Instructions</h2>
      <!-- add stuff -->
      <button onclick="closeInstructions()">Close</button>
    </div>
  </div>

  <script>
    function startGif() {
      document.body.style.backgroundImage = 'url("{{site.baseurl}}/images/sprite/TANK LOADING SLIDE (1).gif")';
      document.querySelectorAll('.button').forEach(function(button) {
        button.style.display = 'none';
      });
      closeSettings();
      closeInstructions();
    }

    function openSettings() {
      document.getElementById('settingsOverlay').style.display = 'block';
    }

    function closeSettings() {
      document.getElementById('settingsOverlay').style.display = 'none';
    }

    function openInstructions() {
      document.getElementById('instructionsOverlay').style.display = 'block';
    }

    function closeInstructions() {
      document.getElementById('instructionsOverlay').style.display = 'none';
    }
  </script>

</body>
</html>