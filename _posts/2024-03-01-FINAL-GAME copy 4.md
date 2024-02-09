---
toc: true
comments: false
layout: nothing
type: hacks
courses: { compsci: {week: 6} }
---

<html>
<head>
  <title>T.A.N.K.S</title>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Pixelify+Sans">
  <style>
/* Container needed to position the button. Adjust the width as needed */
  html {
    font-family: "Pixelify Sans";
  }
  .container {
    font-family: "Pixelify Sans";
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
    width: 1472px;
    height: 828px; 
  }
  /* Make the image responsive */
  .container img {
    width: 100%;
    height: auto;
  }
  /* Style the button and place it in the middle of the container/image */
  .container .btn {
    position: absolute;
    top: 76%;
    left: 28%;
    transform: translate(-28%, -76%);
    -ms-transform: translate(-28%, -76%);
    background-color: transparent;
    /* color: white; */
    font-size: 70px;
    padding: 54px 32.5px;
    border: none;
    cursor: pointer;
    /* border-radius: 5px; */
  }
  .container .btn:hover {
    font-family: "Pixelify Sans";
    /* background-color: black; */
  }
  /* button2code */
  .container .btn2 {
    font-family: "Pixelify Sans";
    position: absolute;
    top: 75%;
    left: 45.8%;
    transform: translate(-45.8%, -75%);
    -ms-transform: translate(-45.8%, -75%);
    background-color: transparent;
    color: white;
    font-size: 70px;
    padding: 54px 30px;
    border: none;
    cursor: pointer;
    /* border-radius: 5px; */
  }
  .container .btn2:hover {
    font-family: "Pixelify Sans";
    /* background-color: white; */
  }
  /* button3code */
  .container .btn3 {
    font-family: "Pixelify Sans";
    position: absolute;
    top: 75.7%;
    left: 52.3%;
    transform: translate(52.3%, -75.7%);
    -ms-transform: translate(52.3%, -75.7%);
    background-color: transparent;
    /* color: white; */
    font-size: 60px;
    padding: 54px 29px;
    border: none;
    cursor: pointer;
    /* border-radius: 5px; */
  }
  .container .btn3:hover {
    font-family: "Pixelify Sans";
    /* background-color: green; */
  }
  /*
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin> */
  
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Pixelify+Sans">

</style>
</head>
<body>
  <div class="container">
    <img src="{{site.baseurl}}/images/sprite/TANKLOADINGBLANK.png" alt="tankloadingblank">
    <button class="btn">⚙️</button>
    <button class="btn2">🎮</button>
    <button class="btn3">✏️</button>
  </div>
  

  <script>
    /*
    function startGif() {
      document.body.style.backgroundImage = 'url("{{site.baseurl}}/images/sprite/TANK LOADING SLIDE (1).gif")';
      document.querySelectorAll('.button').forEach(function(button) {
        button.style.display = 'none';
      });
    }
*/
  </script>

</body>
</html>