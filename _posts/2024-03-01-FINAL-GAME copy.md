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
        <div style="text-align: center;">
            <button class="closeButton" onclick="closeInstructions()">Close</button>
        </div>
    </div>
  </div>

  <div id="gameContainer" style="opacity: 0; transition: opacity 1s ease;">
    <canvas width="1472" height="828" style="border: 4px solid black; float:left; margin:5px; background: #6C6C6C;" id="box"></canvas>
  </div>

  <script>

    function startGame() {
        document.querySelectorAll('.container button').forEach(function(button) {
          button.style.display = 'none';
        });

        document.body.style.backgroundImage = 'url("{{site.baseurl}}/images/sprite/TANKLOADINGSLIDE.gif")'; 
        document.getElementById("gameContainer").style.display = 'block';

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
        if (upPressed) {
            let upx = player1.x + Math.cos(player1.rotation * Math.PI / 180);
            let upy = player1.y + Math.sin(player1.rotation * Math.PI / 180);
            
            if (upx + player1.w / 1 <= 1472 && upx - player1.w / 10000 >= 0 && 
                upy + player1.h / 1 <= 828 && upy - player1.h / 10000 >= 0) {
                player1.x = upx;
                player1.y = upy;
            }
        }

        if(downPressed)
        {
            let downx = player1.x - Math.cos(player1.rotation * Math.PI/180);
            let downy = player1.y - Math.sin(player1.rotation * Math.PI/180);

            if (downx + player1.w / 1 <= 1472 && downx - player1.w / 10000 >= 0 && 
                downy + player1.h / 1 <= 828 && downy - player1.h / 10000 >= 0) {
                player1.x = downx;
                player1.y = downy;
            }
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
            let wx = player2.x + Math.cos(player2.rotation * Math.PI/180);
            let wy = player2.y + Math.sin(player2.rotation * Math.PI/180);

            if (wx + player2.w / 1.8 <= 1472 && wx - player2.w / 10000 >= 0 && 
                wy + player2.h / 1.8 <= 828 && wy - player2.h / 10000 >= 0) {
                player2.x = wx;
                player2.y = wy;
            }
        }

        if(sPressed)
        {
            let sx = player2.x - Math.cos(player2.rotation * Math.PI/180);
            let sy = player2.y - Math.sin(player2.rotation * Math.PI/180);

            if (sx + player2.w / 1.8 <= 1472 && sx - player2.w / 10000 >= 0 && 
                sy + player2.h / 1.8 <= 828 && sy - player2.h / 10000 >= 0) {
                player2.x = sx;
                player2.y = sy;
            }
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

            //veloshitty
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

                if (Date.now() - lastFireTime1 >= 10000) {
                    return;
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

                if (Date.now() - lastFireTime1 >= 10000) {
                    return;
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
    setInterval(drawImage, 5);

  </script>

</body>
</html>