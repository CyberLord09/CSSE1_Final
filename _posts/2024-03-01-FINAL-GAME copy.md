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
      background: url("{{site.baseurl}}/images/sprite/TANK LOADING BLANK.png") no-repeat center center fixed;
      background-size: cover;
      color: #fff; /* Text color */
      font-family: 'Arial', sans-serif;
      text-align: center;
      overflow: hidden; /* Hide overflow to prevent scroll bars */
    }

    #instructionsButton {
      background-color: #fff;
      color: #000;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      position: absolute;
      top: 795%; /* Adjust to move vertically */
      left: 80%; /* Adjust to move horizontally */
    }

    #settingsButton {
      background-color: #fff;
      color: #000;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      position: absolute;
      top: 795%; /* Adjust to move vertically */
      left: 40%; /* Adjust to move horizontally */
        }

    #playButton {
      background-color: #fff;
      color: #000;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      position: absolute;
      top: 795%; /* Adjust to move vertically */
      left: 0%; /* Adjust to move horizontally */
    }
  </style>
</head>
<body>

  <!-- Button to play GIF -->
  <button id="settingsButton" onclick="startGif()">Settings</button>
  <button id="playButton" onclick="startGif()">Play</button>
  <button id="instructionsButton" onclick="startGif()">Instructions</button>

  <script>
    function startGif() {
      document.body.style.backgroundImage = 'url("{{site.baseurl}}/images/sprite/TANK LOADING SLIDE.gif")';
      document.getElementById('playButton').style.display = 'none';
      document.getElementById('settingsButton').style.display = 'none';
      document.getElementById('instructionsButton').style.display = 'none';
    }
  </script>

</body>
</html>
