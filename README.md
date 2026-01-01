<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Aviator Crash Game Ultimate Demo</title>
<style>
body {margin:0; padding:0; overflow:hidden; background:#0a0a0a; font-family:Arial;}
#gameCanvas {display:block;}
.ui {
  position:absolute; top:10px; left:50%; transform:translateX(-50%); text-align:center; z-index:100; color:#fff;
}
button {padding:10px 14px; margin:3px; border:none; border-radius:6px; font-size:14px; cursor:pointer;}
.start{background:#2ecc71;}
.cash{background:#f1c40f;}
.status {margin:5px; font-size:16px;}
.mult {font-size:20px; margin:5px;}
.coins {font-size:20px; margin:5px;}
.betControl {margin:5px;}
.history {
  position:absolute; top:150px; left:50%; transform:translateX(-50%);
  background:rgba(0,0,0,0.5); padding:10px; border-radius:6px; max-height:180px; overflow-y:auto;
  font-size:14px; color:#fff;
}
</style>
</head>
<body>

<div class="ui">
  <h2>Coins: <span id="coins">100</span></h2>
  <h3>Aviator Crash Game ✈️</h3>
  <div class="status" id="status"></div>
  <div class="betControl">
    Bet Amount: <input type="number" id="betAmount" value="10" min="10" max="1000" step="10">
    Multiplier: <select id="betMultiplier"><option>1.5</option><option>2</option><option>3</option><option>5</option></select>
  </div>
  <button class="start" onclick="startGame()">Start Round</button>
  <button class="cash" onclick="cashOut()">Cash Out</button>
  <div class="mult" id="multiplier">1.00x</div>
</div>

<div class="history" id="history">History:</div>
<canvas id="gameCanvas"></canvas>

<script>
// -------- Variables --------
let coins=100;
function updateCoins(){document.getElementById('coins').innerText=coins;}

let canvas=document.getElementById('gameCanvas');
let ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight;

let running=false;
let multiplier=1.00;
let crashAt=0;
let plane={x:canvas.width/2, y:canvas.height-100, size:60, trail:[], angle:0};
let graphData=[];
let particles=[];
let clouds=[];
let history=[];

// Users bets
let userBet = {amount:0, multiplier:0, cashedOut:false, won:0};
let botUsers = [];

// Sounds
let coinSound=new Audio('https://freesound.org/data/previews/341/341695_5260870-lq.mp3');
let crashSound=new Audio('https://freesound.org/data/previews/198/198841_285997-lq.mp3');

// -------- Clouds --------
for(let i=0;i<15;i++){
  clouds.push({x:Math.random()*canvas.width, y:Math.random()*canvas.height/2, size:Math.random()*50+30});
}

// -------- Draw Scene --------
function drawScene(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  
  // Background
  ctx.fillStyle="#0a0a0a";
  ctx.fillRect(0,0,canvas.width,canvas.height);
  
  // Clouds
  ctx.fillStyle="rgba(200,200,200,0.3)";
  clouds.forEach(c=>{
    ctx.beginPath();
    ctx.arc(c.x, c.y, c.size,0,Math.PI*2);
    ctx.fill();
  });
  
  // Graph
  ctx.strokeStyle="#00ff00";
  ctx.lineWidth=3;
  ctx.beginPath();
  for(let i=0;i<graphData.length;i++){
    let x=i*5;
    let y=canvas.height-50-graphData[i]*50;
    if(i==0) ctx.moveTo(x,y); else ctx.lineTo(x,y);
  }
  ctx.stroke();
  
  // Plane trail
  plane.trail.forEach(p=>{
    ctx.fillStyle="rgba(0,255,255,0.3)";
    ctx.beginPath();
    ctx.arc(p.x, p.y, 10,0,Math.PI*2);
    ctx.fill();
  });
  
  // Plane with tilt
  ctx.save();
  ctx.translate(plane.x, plane.y);
  ctx.rotate(plane.angle);
  ctx.font=plane.size+"px Arial";
  ctx.fillText("✈️",-plane.size/2,0);
  ctx.restore();
  
  // Bet markers
  let scaleX = 5;
  if(userBet.amount>0){
    let x = graphData.length*scaleX;
    let y = canvas.height-50 - Math.min(multiplier,userBet.multiplier)*50;
    ctx.fillStyle="#f1c40f";
    ctx.beginPath();
    ctx.arc(x,y,8,0,Math.PI*2);
    ctx.fill();
  }
  botUsers.forEach(b=>{
    if(!b.cashedOut){
      let x = graphData.length*scaleX;
      let y = canvas.height-50 - Math.min(multiplier,b.multiplier)*50;
      ctx.fillStyle="rgba(255,0,0,0.7)";
      ctx.beginPath();
      ctx.arc(x,y,6,0,Math.PI*2);
      ctx.fill();
    }
  });
  
  // Particles
  for(let i=0;i<particles.length;i++){
    let p = particles[i];
    ctx.fillStyle="rgba(255,69,0,"+p.alpha+")";
    ctx.beginPath();
    ctx.arc(p.x,p.y,p.size,0,Math.PI*2);
    ctx.fill();
  }
}

// -------- Particles --------
function createParticles(x,y){
  for(let i=0;i<80;i++){
    particles.push({
      x:x, y:y,
      vx:(Math.random()-0.5)*6,
      vy:(Math.random()-0.5)*6,
      size:Math.random()*5+2,
      alpha:1
    });
  }
}

function updateParticles(){
  for(let i=particles.length-1;i>=0;i--){
    let p=particles[i];
    p.x+=p.vx; p.y+=p.vy; p.alpha-=0.02;
    if(p.alpha<=0) particles.splice(i,1);
  }
}

// -------- Start Game --------
function startGame(){
  if(running) return;
  let amt = parseInt(document.getElementById('betAmount').value);
  let mul = parseFloat(document.getElementById('betMultiplier').value);
  if(amt>coins){alert("Not enough coins"); return;}
  userBet={amount:amt,multiplier:mul,cashedOut:false,won:0};
  coins-=amt; updateCoins();
  
  // Bots
  botUsers=[];
  for(let i=0;i<3;i++){
    let bMul=(Math.random()*4+1).toFixed(2);
    let bAmt=Math.floor(Math.random()*(100)+10);
    botUsers.push({amount:bAmt,multiplier:bMul,cashedOut:false,won:0});
  }
  
  running=true;
  multiplier=1.00;
  crashAt=(Math.random()*5+1.5).toFixed(2);
  plane.x=canvas.width/2;
  plane.y=canvas.height-100;
  plane.trail=[];
  plane.angle=0;
  graphData=[];
  particles=[];
  document.getElementById('status').innerText="";
  
  let interval=setInterval(()=>{
    if(!running){clearInterval(interval); return;}
    multiplier+=0.02*(1+multiplier/10);
    document.getElementById('multiplier').innerText=multiplier.toFixed(2)+'x';
    
    // Plane tilt & trail
    plane.angle=Math.sin(multiplier/2)/5;
    let planeY=canvas.height-100-multiplier*50;
    plane.trail.push({x:plane.x,y:plane.y});
    if(plane.trail.length>20) plane.trail.shift();
    plane.y=planeY;
    
    // Clouds
    clouds.forEach(c=>{c.x-=0.3;if(c.x<0)c.x=canvas.width+Math.random()*100;});
    
    graphData.push(multiplier);
    
    // Bot cash out
    botUsers.forEach(b=>{
      if(!b.cashedOut && multiplier>=b.multiplier){
        b.cashedOut=true; b.won=Math.floor(b.amount*b.multiplier);
        coins+=b.won;
      }
    });
    
    // User auto cash out
    if(userBet.amount>0 && !userBet.cashedOut && multiplier>=userBet.multiplier){
      userBet.cashedOut=true;
      userBet.won=Math.floor(userBet.amount*userBet.multiplier);
      coins+=userBet.won;
      coinSound.play();
      history.push("User auto cash out @ "+userBet.multiplier+"x");
      updateHistory();
    }
    
    drawScene();
    updateParticles();
    
    // Crash
    if(multiplier>=crashAt){
      running=false;
      document.getElementById('status').innerHTML="<span style='color:#ff6b6b; font-size:18px;'>CRASH 💥 @ "+crashAt+"x</span>";
      if(!userBet.cashedOut){userBet.won=0; history.push("User LOST @ crash "+crashAt+"x");}
      botUsers.forEach(b=>{if(!b.cashedOut)b.won=0;});
      crashSound.play();
      createParticles(plane.x, plane.y);
      updateHistory();
    }
  },50);
}

// -------- Cash Out --------
function cashOut(){
  if(!running || userBet.cashedOut) return;
  userBet.cashedOut=true;
  userBet.won=Math.floor(userBet.amount*multiplier);
  coins+=userBet.won; updateCoins(); coinSound.play();
  history.push("User cashed out @ "+multiplier.toFixed(2)+"x");
  updateHistory();
}

// -------- History --------
function updateHistory(){
  let histEl=document.getElementById('history');
  let lines=history.slice(-10).reverse();
  botUsers.forEach((b,i)=>{if(b.cashedOut)lines.push("Bot"+(i+1)+" cashed out @ "+b.multiplier+"x");});
  histEl.innerHTML="History:<br>"+lines.join("<br>");
}
</script>
</body>
</html>
