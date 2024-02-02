---
toc: true
comments: false
layout: post
title: Final Game 
description: A pretty advanced use of JS, HTML, CSS, and Sprite animations to create a single-player game. 
type: hacks
courses: { compsci: {week: 6} }
---


<style>
.text-center{
    text-align:center;
    margin-left:auto;
    margin-right:auto;
}
</style>


<body>
<div id="text-center">
    <canvas id="background">
    </canvas>
</div>








<body>

<script>
  const canvas = document.createElement('canvas');
  const ctx = canvas.getContext('2d');
  document.body.appendChild(canvas);

  // Constants
  const gridSize = 32;
  const rows = 16;
  const cols = 16;
  canvas.width = gridSize * cols;
  canvas.height = gridSize * rows;



  const grid =[[1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
               [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]];

   //game state
   const robber = {x: 8:, y: 2}
   const police = {x: 8, y: 15}

   //function to draw the grid

   function drawGrid() {
    for (let i=0; i < rows; i++){
        for (let j = 0; j < cols; j++){
            let color;

            switch (grid[i][j]) {
                case 0:
                    color = 'green';
                    break;
                
                case 1:
                    color = 'gray';
                    break;
                
                default:
                    color = 'white':
            }
        
        ctx.fillStyle = color;
        ctx.fillRect(j * gridSize, i * gridSize, gridSize, gridSize)

        }
     }
   }



</script>