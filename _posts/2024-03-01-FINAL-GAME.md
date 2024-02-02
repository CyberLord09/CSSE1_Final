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
    <button onclick="calculateMean()" style="color:#67dbff; background: black; border-radius: 4px; border: solid;">wanna play a game?</button>
//
    <script>
        Pacman.Map = function (size) {
    
    `    var height    = null, 
            width     = null, 
            blockSize = size,
            pillSize  = 0,
            map       = null;
        
        function withinBounds(y, x) {
            return y >= 0 && y < height && x >= 0 && x < width;
        }
        
        function isWall(pos) {
            return withinBounds(pos.y, pos.x) && map[pos.y][pos.x] === Pacman.WALL;
        }
        
        function isFloorSpace(pos) {
            if (!withinBounds(pos.y, pos.x)) {
                return false;
            }
            var peice = map[pos.y][pos.x];
            return peice === Pacman.EMPTY || 
                peice === Pacman.BISCUIT ||
                peice === Pacman.PILL;
        }
        
        function drawWall(ctx) {

            var i, j, p, line;
            
            ctx.strokeStyle = "#0000FF";
            ctx.lineWidth   = 5;
            ctx.lineCap     = "round";
            
            for (i = 0; i < Pacman.WALLS.length; i += 1) {
                line = Pacman.WALLS[i];
                ctx.beginPath();

                for (j = 0; j < line.length; j += 1) {

                    p = line[j];
                    
                    if (p.move) {
                        ctx.moveTo(p.move[0] * blockSize, p.move[1] * blockSize);
                    } else if (p.line) {
                        ctx.lineTo(p.line[0] * blockSize, p.line[1] * blockSize);
                    } else if (p.curve) {
                        ctx.quadraticCurveTo(p.curve[0] * blockSize, 
                                            p.curve[1] * blockSize,
                                            p.curve[2] * blockSize, 
                                            p.curve[3] * blockSize);   
                    }
                }
                ctx.stroke();
            }
        }
        
        function reset() {       
            map    = Pacman.MAP.clone();
            height = map.length;
            width  = map[0].length;        
        };

        function block(pos) {
            return map[pos.y][pos.x];
        };
        
        function setBlock(pos, type) {
            map[pos.y][pos.x] = type;
        };

        function drawPills(ctx) { 

            if (++pillSize > 30) {
                pillSize = 0;
            }
            
            for (i = 0; i < height; i += 1) {
                for (j = 0; j < width; j += 1) {
                    if (map[i][j] === Pacman.PILL) {
                        ctx.beginPath();

                        ctx.fillStyle = "#000";
                        ctx.fillRect((j * blockSize), (i * blockSize), 
                                    blockSize, blockSize);

                        ctx.fillStyle = "#FFF";
                        ctx.arc((j * blockSize) + blockSize / 2,
                                (i * blockSize) + blockSize / 2,
                                Math.abs(5 - (pillSize/3)), 
                                0, 
                                Math.PI * 2, false); 
                        ctx.fill();
                        ctx.closePath();
                    }
                }
            }
        };
        
        function draw(ctx) {
            
            var i, j, size = blockSize;

            ctx.fillStyle = "#000";
            ctx.fillRect(0, 0, width * size, height * size);

            drawWall(ctx);
            
            for (i = 0; i < height; i += 1) {
                for (j = 0; j < width; j += 1) {
                    drawBlock(i, j, ctx);
                }
            }
        };
        
        function drawBlock(y, x, ctx) {

            var layout = map[y][x];

            if (layout === Pacman.PILL) {
                return;
            }

            ctx.beginPath();
            
            if (layout === Pacman.EMPTY || layout === Pacman.BLOCK || 
                layout === Pacman.BISCUIT) {
                
                ctx.fillStyle = "#000";
                ctx.fillRect((x * blockSize), (y * blockSize), 
                            blockSize, blockSize);

                if (layout === Pacman.BISCUIT) {
                    ctx.fillStyle = "#FFF";
                    ctx.fillRect((x * blockSize) + (blockSize / 2.5), 
                                (y * blockSize) + (blockSize / 2.5), 
                                blockSize / 6, blockSize / 6);
                }
            }
            ctx.closePath();	 
        };

        Pacman.MAP = [
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0],
        [0, 4, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 4, 0],
        [0, 1, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 1, 0],
        [0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0],
        [0, 1, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 1, 0],
        [0, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 0],
        [0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0],
        [2, 2, 2, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 2, 2, 2],
        [0, 0, 0, 0, 1, 0, 1, 0, 0, 3, 0, 0, 1, 0, 1, 0, 0, 0, 0],
        [2, 2, 2, 2, 1, 1, 1, 0, 3, 3, 3, 0, 1, 1, 1, 2, 2, 2, 2],
        [0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0],
        [2, 2, 2, 0, 1, 0, 1, 1, 1, 2, 1, 1, 1, 0, 1, 0, 2, 2, 2],
        [0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0],
        [0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0],
        [0, 1, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 1, 0],
        [0, 4, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 4, 0],
        [0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0],
        [0, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 0],
        [0, 1, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 1, 0],
        [0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
];


</body>



