---
toc: true
comments: false
layout: nothing
courses: { compsci: {week: 6} }
---

<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>T.A.N.K.S</title>
  <style>
/* Container needed to position the button. Adjust the width as needed */
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 1472px; /* Set container width to match image width */
    height: 828px; /* Set container height to match image height */
  }

  .container img {
    width: 100%;
    height: auto;
  }

  /* Style the button and place it in the middle of the container/image */
  .container .btn {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
    background-color: #555;
    color: white;
    font-size: 16px;
    padding: 12px 24px;
    border: none;
    cursor: pointer;
    border-radius: 5px;
  }
  .container .btn:hover {
    background-color: black;
  }
  </style>
</head>
<body>
  <div class="container">
    <img src="{{site.baseurl}}/images/sprite/TANKLOADINGBLANK.png" alt="tankloadingblank" style="width:100%">
    <button class="btn">Button</button>
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