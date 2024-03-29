---
toc: true
comments: false
layout: none
type: hacks
courses: { compsci: {week: 6} }
---

<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>T.A.N.K.S</title>
  <style>
    body {
      background: url("{{site.baseurl}}/images/sprite/TANKLOADINGBLANK.png") no-repeat center center fixed;
    }
    .container {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      -ms-transform: translate(-50%, -50%);
      width: 1472px;
      height: 828px;
      z-index: 1;
    }
    .container button {
      background-color: transparent;
      color: #fff;
      font-size: 60px;
      cursor: pointer;
      font-family: 'Arial', sans-serif;
      border: none;
      outline: none;
      position: fixed;
      transition: box-shadow 0.3s ease-out, color 0.3s ease-out;
      z-index: 2;
    }
    .container .btn1 {
      top: 65%;
      left: 27.4%;
    }
    .container .btn2 {
      top: 64.3%;
      left: 43.1%;
    }
    .container .btn3 {
      top: 65%;
      left: 58.7%;
    }
    .overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      z-index: 5;
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
      z-index: 6;
    }
    #gameContainer {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    .instructionsContainer {
      display: flex;
      width: auto;
      flex-direction: row;
      justify-content: center;
      align-items: center;
      gap: 200px;
      padding: 10px;
    }
    .choice {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 10px;
      padding: 10px;
    }
  </style>
</head>
<body>
  <script src="{{site.baseurl}}/assets/js/ready.js"></script>  
  <div class="container">
    <button class="btn1" onclick="openSettings()">⚙️</button>
    <button class="btn2" onclick="startGame()">🎮</button>
    <button class="btn3" onclick="openInstructions()">✏️</button>
  </div>

  <div id="settingsOverlay" class="overlay">
    <div class="model">
      <!-- add stuff -->
      <h2>Settings</h2>
      <!-- add stuff -->
      <button class="closeButton" onclick="closeSettings()">Close</button>
    </div>
  </div>

  <div id="instructionsOverlay" class="overlay">
    <div class="model">
      <h1 style="text-align: center; color: black;">Instructions</h1>
      <p style="text-align: center; color: black;">This is a 2 player game, where each player controls one tank. Each tank can shoot a bullet with a cooldown, and the aim of the game is to kill the other tank before they kill yours.</p>
      <div class="instructionsContainer">
        <div class="choice">
          <h2 style="color: black; text-align: center;">Player 1</h2>
          <p style="color: black; text-align: center;">Press Q to Shoot. <br> Use WASD to move.</p>
          <img src = "{{site.baseurl}}/images/sprite/tank0.png" id="p1tank">
        </div>
        <div class="choice">
          <h2 style="color: black; text-align: center;">Player 2</h2>
          <p style="color: black; text-align: center;">Press / to Shoot. <br> Use Arrow Keys to move.</p>
          <img src = "{{site.baseurl}}/images/sprite/tank1.png" id="p2tank">
        </div>
      </div>
    </div>
  </div>

  <div id="gameContainer" style="opacity: 0; transition: opacity 1s ease;">
    <canvas width="1472" height="828" style="border: 4px solid black; float:left; margin:5px; background: #6C6C6C;" id="box"></canvas>
  </div>

</body>
</html>