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
  <title>Your Game Title</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: url("{{site.baseurl}}/images/sprite/TANK LOADING BLANK (1).png") no-repeat center center fixed;
      background-size: cover;
      color: #fff; /* Text color */
      font-family: 'Arial', sans-serif;
      text-align: center;
      overflow: hidden; /* Hide overflow to prevent scroll bars */
    }

    .button {
      background-color: transparent;
      color: #fff;
      font-size: 16px;
      cursor: pointer;
      font-family: 'Arial', sans-serif; /* Use a font suitable for a tank game */
      border: none;
      outline: none;
      position: absolute;
      top: 795%; /* Adjust to move vertically */
      transform: translateX(-50%);
      transition: box-shadow 0.3s ease-out, color 0.3s ease-out;
      z-index: 1;
    }

    #instructionsButton {
      left: 80%; /* Adjust to move horizontally */
    }

    #settingsButton {
      left: 40%; /* Adjust to move horizontally */
    }

    #playButton {
      left: 0%; /* Adjust to move horizontally */
    }

    .button:hover {
      box-shadow: 0 0 20px #ff4500, 0 0 40px #ff4500; /* Cool fire-like glow on hover */
      color: #ff4500; /* Change text color on hover */
      animation: shake 0.5s ease-in-out infinite; /* Subtle shake animation on hover */
    }

    @keyframes shake {
      0%, 100% {
        transform: translateX(-50%);
      }
      25%, 75% {
        transform: translateX(-55%); /* Adjust the shake range */
      }
      50% {
        transform: translateX(-50%);
      }
    }
  </style>
</head>
<body>

  <!-- Buttons with idle and hover styles -->
  <button id="settingsButton" class="button" onclick="startGif()">Settings</button>
  <button id="playButton" class="button" onclick="startGif()">Play</button>
  <button id="instructionsButton" class="button" onclick="startGif()">Instructions</button>

  <script>
    function startGif() {
      document.body.style.backgroundImage = 'url("{{site.baseurl}}/images/sprite/TANK LOADING SLIDE (1).gif")';
      document.querySelectorAll('.button').forEach(function(button) {
        button.style.display = 'none';
      });
    }
  </script>

</body>
</html>
