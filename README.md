<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Crash Game Demo</title>
<style>
body {margin:0; padding:0; font-family:Arial; background:#121212; color:#fff; overflow:hidden;}
canvas {display:block;}
.ui {position:absolute; top:10px; left:50%; transform:translateX(-50%); text-align:center; z-index:100;}
button {padding:10px 16px; margin:5px; border:none; border-radius:8px; cursor:pointer; font-size:16px;}
.start{background:#2ecc71;}
.cash{background:#f1c40f;}
.status {margin:5px;}
.coins {font-size:24px; margin:10px;}
h3 {margin-bottom:5px;}
.mult {font-size:20px; margin:5px;}
</style>
</head>
<body>

<div class="ui">
  <h2>Coins: <span id="coins">100</span></h2>
  <h3>Crash Game ✈️</h3>
  <div class="status" id="status"></div>
  <button class="start" onclick="startGame()">Start</button>
  <button class="cash" onclick="cashOut()">Cash Out</button>
  <div class="mult" id="multiplier">1.00x</div>
</div>

<canvas id="gameCanvas"></canvas>

<script>
// -------- Variables --------
let coins=100;
function updateCoins(){document.getElementById('coins').innerText=coins;}

let canvas=document.getElementById('gameCanvas');
let ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight;

// Game State
let running=false;
let multiplier=1.00;
let crashAt=0;
let plane={x:50, y:canvas.height-100};
let graphData=[];

// Sounds
let coinSound=new Audio('https://freesound.org/data/previews/341/341695_5260870-lq.mp3');
let crashSound=new Audio('https://freesound.org/data/previews/198/198841_285997-lq.mp3');

// -------- Draw Scene --------
function drawScene(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  
  // Background
  ctx.fillStyle="#121212";
  ctx.fillRect(0,0,canvas.width,canvas.height);
  
  // Graph
  ctx.strokeStyle="#2ecc71";
  ctx.lineWidth=3;
  ctx.beginPath();
  for(let i=0;i<graphData.length;i++){
    let x=i*5; 
    let y=canvas.height-50-graphData[i]*50;
    if(i==0) ctx.moveTo(x,y); else ctx.lineTo(x,y);
  }
  ctx.stroke();
  
  // Plane
  ctx.font="50px Arial";
  ctx.fillText("✈️",plane.x,plane.y);
}
drawScene();

// -------- Game Functions --------
function startGame(){
  if(running) return;
  running=true; multiplier=1.00; crashAt=(Math.random()*5+1.5).toFixed(2);
  plane.x=50; plane.y=canvas.height-100; graphData=[];
  document.getElementById('status').innerText="";
  
  let interval=setInterval(()=>{
    if(!running) {clearInterval(interval); return;}
    multiplier+=0.02;
    document.getElementById('multiplier').innerText=multiplier.toFixed(2)+'x';
    
    // Plane movement along graph
    plane.x+=5; plane.y=canvas.height-100 - multiplier*50;
    graphData.push(multiplier);
    
    drawScene();
    
    // Crash check
    if(multiplier>=crashAt){
      running=false;
      document.getElementById('status').innerHTML="<span style='color:#ff6b6b'>CRASH 💥 @ "+crashAt+"x</span>";
      coins-=10; updateCoins(); crashSound.play();
    }
  },50);
}

function cashOut(){
  if(!running) return;
  running=false;
  document.getElementById('status').innerText="Cashed out @ "+multiplier.toFixed(2)+'x';
  coins+=Math.floor(10*multiplier); updateCoins(); coinSound.play();
}
</script>
</body>
</html>
