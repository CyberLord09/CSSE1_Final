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
      color: #fff;
      font-family: 'Arial', sans-serif;
      text-align: center;
      position: relative;
      overflow: hidden;
      align: center;
    }
    body, html {
      max-width: 1472px;
      max-height: 828px;
    }
    .button {
      background-color: transparent;
      color: #fff;
      font-size: 16px;
      cursor: pointer;
      font-family: 'Arial', sans-serif;
      border: none;
      outline: none;
      position: fixed;
      transform: translateX(-50%);
      transition: box-shadow 0.3s ease-out, color 0.3s ease-out;
      z-index: 1;
    }
    #instructionsButton {
      top: 53vh;
      left: 37vw;
    }
    #settingsButton {
      top: 57vh;
      left: 13vw;
      transform: translate(-50%, -50%);
    }
    #playButton {
      top: 55vh;
      left: 25vw;
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
    #gameContainer {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      }
  </style>
</head>
<body>
  <div class-="buttons">
    <button id="settingsButton" class="button" onclick="openSettings()">Settings</button>
    <button id="playButton" class="button" onclick="startGame()">Play</button>
    <button id="instructionsButton" class="button" onclick="openInstructions()">Instructions</button>
  </div>

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

  <div id="gameContainer" style="opacity: 0; transition: opacity 1s ease;">
    <canvas width="1472" height="828" style="border: 4px solid black; float:left; margin:5px; background: #6C6C6C;" id="box"></canvas>
  </div>

  <script>
    window.addEventListener("keydown", function(e) { if(["Space","ArrowUp","ArrowDown","ArrowLeft","ArrowRight"].indexOf(e.code) > -1) { e.preventDefault(); } }, false);

    var canvas = document.getElementById("box").getContext("2d");
    document.addEventListener ("keydown", keyDownHandler, false);
    document.addEventListener ("keyup", keyUpHandler, false);

    let tank1 = new Image();
    tank1.src = "{{site.baseurl}}/images/sprite/tank1.png";

    let tank2 = new Image () ;
    tank2.src = "{{site.baseurl}}/images/sprite/tank0.png";

    let upPressed = false;
    let downPressed = false;
    let leftPressed = false;
    let rightPressed = false;
    let zeroPressed = false;
    let wPressed = false;
    let sPressed = false;
    let dPressed = false;
    let aPressed = false;
    let spacePressed = false;
    let slasPressed = false;
    let qPressed = false;
    let started = false;

    //controls for player one and two
    function keyDownHandler(e)
    {
        if (e.keyCode == 38)
        {
            upPressed = true;
        }

        if(e.keyCode == 40)
        {
            downPressed = true;
        }

        if(e. keyCode == 37)
        {
            leftPressed = true;
        }

        if(e.keyCode == 39)
        {
            rightPressed = true;
        }

        if(e.keyCode == 32)
        {
            spacePressed = true;
        }

        if(e.keyCode == 87)
        {
            wPressed = true;
        }

        if(e.keyCode == 65)
        {
            aPressed = true;
        }

        if(e.keyCode == 83)
        {
            sPressed = true;
        }

        if(e.keyCode == 68)
        {
            dPressed = true;
        }

        if(e.keyCode == 96)
        {
            zeroPressed = true;
        }

        //bulletsa
        if(e.keyCode == 191)
        {
            slasPressed = true;
        }

        if(e.keyCode == 81)
        {
            qPressed = true;
        }
    }

    function keyUpHandler(e)
    {
        if (e.keyCode == 38)
        {
            upPressed = false;
        }

        if(e.keyCode == 40)
        {
            downPressed = false;
        }

        if(e. keyCode == 37)
        {
            leftPressed = false;
        }

        if(e.keyCode == 39)
        {
            rightPressed = false;
        }

        if(e.keyCode == 32)
        {
            spacePressed = false;
        }

        if(e.keyCode == 87)
        {
            wPressed = false;
        }

        if(e.keyCode == 65)
        {
            aPressed = false;
        }

        if(e.keyCode == 83)
        {
            sPressed = false;
        }

        if(e.keyCode == 68)
        {
            dPressed = false;
        }

        if(e.keyCode == 96)
        {
            zeroPressed = false;
        }

        if(e.keyCode == 191)
        {
            slasPressed = false;
        }

        if(e.keyCode == 81)
        {
            qPressed = false;
        }
    }

    function drawimgrotation(img, x, y, width, height, deg)
    {
        let rad = deg * Math.PI / 180;
        canvas.translate( x + width / 2, y + height / 2 );
        canvas.rotate(rad);
        canvas.drawImage( img, width / 2 * -1, height / 2 * -1, width, height);
        canvas.rotate(rad * -1);
        canvas.translate( (x + width / 2) * -1, (y + height / 2) * -1 );
    }

    function controls()
    {

        //p1
        if(leftPressed)
        {
            player1.rotation -= 1;
        }

        if(rightPressed)
        {
            player1.rotation += 1;
        }

        //diag path
        if(upPressed)
        {
            player1.x += Math.cos(player1.rotation * Math.PI/180);
            player1.y += Math.sin(player1.rotation * Math.PI/180);
        }

        if(downPressed)
        {
            player1.x -= Math.cos(player1.rotation * Math.PI/180);
            player1.y -= Math.sin(player1.rotation * Math.PI/180);
        }

        //p2
        if(aPressed)
        {
            player2.rotation -= 1;
        }

        if(dPressed)
        {
            player2.rotation += 1;
        }

        //diag path
        if(wPressed)
        {
            player2.x += Math.cos(player2.rotation * Math.PI/180);
            player2.y += Math.sin(player2.rotation * Math.PI/180);
        }

        if(sPressed)
        {
            player2.x -= Math.cos(player2.rotation * Math.PI/180);
            player2.y -= Math.sin(player2.rotation * Math.PI/180);
        }
    }

    function Player(x, y, rotation, w, h)
    {
        this.x = x;
        this.y = y;
        this.rotation = rotation;
        this.w = w;
        this.h = h;
        this.canfire = true;
        this.hit = false;
        this.score = 0;
    }

    let lastFireTime2 = 0;
    const fireCooldown2 = 500;

    function player2Bullet() {
        if (qPressed && Date.now() - lastFireTime2 > fireCooldown2) 
        {
            lastFireTime2 = Date.now();

            let rad = 5;
            let posx = player2.x+50;
            let posy = player2.y+48;

            //velocity
            let radang = player2.rotation * Math.PI / 180;
            let speed = 200;
            let velx = speed * Math.cos(radang);
            let vely = speed * Math.sin(radang);

            function draw_and_update() {
                canvas.beginPath();
                canvas.arc(posx, posy, rad, 0, 2 * Math.PI);
                canvas.fill();
                canvas.fillStyle = "black";

                posx += velx / 60;
                posy += vely / 60;

                if (posx + rad >= 1472 || posx - rad <= 0) {
                    velx = -velx;
                }

                if (posy + rad >= 828 || posy - rad <= 0) {
                    vely = -vely;
                }

                requestAnimationFrame(draw_and_update);
            }
            requestAnimationFrame(draw_and_update);
        }
    }

    let lastFireTime1 = 0;
    const fireCooldown1 = 500;

    function player1Bullet() {
        if (slasPressed && Date.now() - lastFireTime1 > fireCooldown1) 
        {
            lastFireTime1 = Date.now();

            let rad = 5;
            let posx = player1.x+50;
            let posy = player1.y+48;

            //velocity
            let radang = player1.rotation * Math.PI / 180;
            let speed = 200;
            let velx = speed * Math.cos(radang);
            let vely = speed * Math.sin(radang);

            function draw_and_update() {
                canvas.beginPath();
                canvas.arc(posx, posy, rad, 0, 2 * Math.PI);
                canvas.fill();
                canvas.fillStyle = "black";

                posx += velx / 60;
                posy += vely / 60;

                if (posx + rad >= 1472 || posx - rad <= 0) {
                    velx = -velx;
                }

                if (posy + rad >= 828 || posy - rad <= 0) {
                    vely = -vely;
                }

                requestAnimationFrame(draw_and_update);
            }
            requestAnimationFrame(draw_and_update);
        }
    }

    let player2 = new Player (50, 100, 0, 92, 92);
    let player1 = new Player (1300, 650, 180, 92, 92);

    function drawImage()
    {
        canvas.clearRect(0, 0, 1472, 828);

        controls();

        player1Bullet();

        player2Bullet();

        if(!player1.hit)
        {
            drawimgrotation(tank1, player1.x, player1.y, player1.w, player1.h, player1.rotation);
        }

        if(!player2.hit)
        {
            drawimgrotation(tank2, player2.x, player2.y, player2.w, player2.h, player2.rotation);
        }
    }

    function startGame() {
      document.querySelectorAll('.button').forEach(function(button) {
        button.style.display = 'none';
      });

      // Close any open overlays
      closeSettings();
      closeInstructions();

      document.body.style.backgroundImage = 'url("{{site.baseurl}}/images/sprite/TANKLOADINGSLIDE.gif")';
      document.querySelectorAll('.button').forEach(function(button) {
      button.style.display = 'none';
      });

      // Set a timeout to delay the fade-in effect
      setTimeout(function() {
        document.getElementById("gameContainer").style.opacity = 1;
        // Start the game loop
        setInterval(drawImage, 10);
      }, 1000); // Adjust the delay time (in milliseconds) as needed
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