<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Ultimate Gambling Game Demo</title>
<style>
body {
    margin:0; padding:0; font-family:Arial; background:#0f1220; color:#fff; overflow:hidden;
}
canvas {display:block;}
.ui {
    position:absolute; top:10px; left:50%; transform:translateX(-50%);
    text-align:center; z-index:100;
}
button {
    padding:10px 16px; margin:5px; border:none; border-radius:8px; cursor:pointer;
    font-size:16px;
}
.start{background:#2ecc71;}
.cash{background:#f1c40f;}
.status {margin:5px;}
.coins {font-size:24px; margin:10px;}
</style>
</head>
<body>

<div class="ui">
  <h2>Coins: <span id="coins">100</span></h2>

  <!-- Aviator -->
  <h3>Aviator ✈️</h3>
  <div class="status" id="aviStatus"></div>
  <button class="start" onclick="startAviator()">Start Aviator</button>
  <button class="cash" onclick="cashOutAviator()">Cash Out</button>
  <div class="mult" id="aviMult">1.00x</div>

  <hr style="margin:20px 0;border-color:#555">

  <!-- Cards -->
  <h3>Cards 🎴</h3>
  <div class="status" id="cardsStatus"></div>
  <button class="start" onclick="playCards()">Play Cards</button>
  <div class="mult" id="cardsMult">1.00x</div>

  <hr style="margin:20px 0;border-color:#555">

  <!-- Fishing -->
  <h3>Fishing 🎣</h3>
  <div class="status" id="fishStatus"></div>
  <button class="start" onclick="playFishing()">Catch Fish</button>
  <div class="mult" id="fishMult">1.00x</div>
</div>

<canvas id="gameCanvas"></canvas>

<script>
// -------- Setup --------
let coins=100;
function updateCoins(){document.getElementById('coins').innerText=coins;}

let canvas=document.getElementById('gameCanvas');
let ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight;

// -------- Aviator Variables --------
let aviRunning=false, aviM=1.00, aviTimer=null, crashAt=0;
let plane={x:50, y:canvas.height-100};

// -------- Cards Variables --------
let cardsRunning=false;

// -------- Fishing Variables --------
let fishRunning=false, fishY=canvas.height-100, fishX=50;

// -------- Sounds --------
let flySound=new Audio('https://freesound.org/data/previews/341/341695_5260870-lq.mp3'); // plane sound
let crashSound=new Audio('https://freesound.org/data/previews/198/198841_285997-lq.mp3'); // crash
let coinSound=new Audio('https://freesound.org/data/previews/341/341695_5260870-lq.mp3'); // coin

// -------- Aviator Functions --------
function startAviator(){
    if(aviRunning) return;
    aviRunning=true; aviM=1.00; crashAt=(Math.random()*3+1.5).toFixed(2);
    plane.x=50; plane.y=canvas.height-100;
    document.getElementById('aviStatus').innerText="";
    flySound.play();
    aviTimer=setInterval(()=>{
        aviM+=0.02;
        document.getElementById('aviMult').innerText=aviM.toFixed(2)+'x';
        plane.x+=5; plane.y-=2.5;
        if(aviM>=crashAt){
            clearInterval(aviTimer);
            aviRunning=false;
            document.getElementById('aviStatus').innerHTML="<span style='color:#ff6b6b'>CRASH 💥 @ "+crashAt+"x</span>";
            coins-=10; updateCoins(); crashSound.play();
        }
        drawScene();
    },50);
}

function cashOutAviator(){
    if(!aviRunning) return;
    clearInterval(aviTimer); aviRunning=false;
    document.getElementById('aviStatus').innerText="Cashed out @ "+aviM.toFixed(2)+'x';
    coins+=Math.floor(10*aviM); updateCoins(); coinSound.play();
}

// -------- Cards Functions --------
function playCards(){
    if(cardsRunning) return;
    cardsRunning=true;
    let multiplier=1.00; let count=0;
    document.getElementById('cardsStatus').innerText="";
    let interval=setInterval(()=>{
        if(count>20){clearInterval(interval); cardsRunning=false; return;}
        multiplier+=0.05; document.getElementById('cardsMult').innerText=multiplier.toFixed(2)+'x';
        count++;
    },100);
    setTimeout(()=>{
        let win=Math.random()<0.5;
        document.getElementById('cardsStatus').innerText=win?"You won 15 coins!":"You lost 10 coins!";
        coins+=win?15:-10; updateCoins(); coinSound.play();
    },2200);
}

// -------- Fishing Functions --------
function playFishing(){
    if(fishRunning) return;
    fishRunning=true; fishY=canvas.height-100; fishX=50;
    let multiplier=1.00; let count=0;
    document.getElementById('fishStatus').innerText="";
    let interval=setInterval(()=>{
        if(count>20){clearInterval(interval); fishRunning=false; return;}
        multiplier+=0.05;
        document.getElementById('fishMult').innerText=multiplier.toFixed(2)+'x';
        fishY-=3; fishX+=2; count++;
        drawScene();
    },80);
    setTimeout(()=>{
        let win=Math.random()<0.6;
        document.getElementById('fishStatus').innerText=win?"Fish caught! +10 coins":"Fish escaped! -5 coins";
        coins+=win?10:-5; updateCoins(); coinSound.play();
    },1800);
}

// -------- Draw Scene --------
function drawScene(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    // Background
    ctx.fillStyle="#0f1220"; ctx.fillRect(0,0,canvas.width,canvas.height);
    // Plane
    ctx.fillStyle="#fff"; ctx.font="50px Arial"; ctx.fillText("✈️",plane.x,plane.y);
    // Fish
    ctx.fillText("🎣",fishX,fishY);
}

drawScene();
</script>
</body>
</html>
