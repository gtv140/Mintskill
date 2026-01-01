<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Lucky Draw - Live Casino Crash</title>
<style>
body {margin:0; padding:0; overflow:hidden; background:#0a0a0a; font-family:Arial;}
#gameCanvas {display:block;}
.title{
  position:absolute; top:10px; left:50%; transform:translateX(-50%);
  font-size:36px; font-weight:bold; color:#ff00ff; text-shadow:0 0 30px #ff00ff;
  z-index:200;
}
.ui {position:absolute; top:70px; left:50%; transform:translateX(-50%); text-align:center; z-index:100; color:#0fffe0; text-shadow:0 0 15px #0fffe0;}
button {padding:10px 14px; margin:3px; border:none; border-radius:6px; font-size:14px; cursor:pointer; font-weight:bold; color:#0a0a0a;}
.start{background:#00ff99; box-shadow:0 0 10px #00ff99;}
.cash{background:#ff00ff; box-shadow:0 0 10px #ff00ff;}
.status {margin:5px; font-size:18px; font-weight:bold;}
.mult {font-size:22px; margin:5px; text-shadow:0 0 20px #0fffec;}
.coins {font-size:22px; margin:5px;}
.betControl {margin:5px;}
.history, .botBox {position:absolute; left:50%; transform:translateX(-50%); background:rgba(0,0,0,0.5); padding:10px; border-radius:10px; font-size:14px; color:#fff; text-shadow:0 0 5px #0fffe0; max-height:200px; overflow-y:auto;}
.botBox{top:180px;}
.history{top:450px;}
</style>
</head>
<body>

<div class="title">Lucky Draw</div>

<div class="ui">
  Coins: <span id="coins">100</span> <br>
  Bet Amount: <input type="number" id="betAmount" value="10" min="10" max="1000" step="10">
  Multiplier: <select id="betMultiplier"><option>1.5</option><option>2</option><option>3</option><option>5</option></select><br>
  <button class="start" onclick="startGame()">Start Round</button>
  <button class="cash" onclick="cashOut()">Cash Out</button>
  <div class="mult" id="multiplier">1.00x</div>
  <div class="status" id="status"></div>
</div>

<div class="botBox" id="botBox">Bots Info:</div>
<div class="history" id="history">History:</div>
<canvas id="gameCanvas"></canvas>

<script>
// Variables
let coins=100;
function updateCoins(){document.getElementById('coins').innerText=coins;}
let canvas=document.getElementById('gameCanvas');
let ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight;

let running=false;
let multiplier=1.00;
let crashAt=0;
let plane={x:canvas.width/2, y:canvas.height-100, size:60, trail:[], angle:0, scale:1};
let graphData=[];
let particles=[];
let clouds=[];
let history=[];
let userBet={amount:0,multiplier:0,cashedOut:false,won:0};
let botUsers=[];

// Sounds
let crashSound=new Audio('https://freesound.org/data/previews/341/341700_5260870-lq.mp3');
let coinSound=new Audio('https://freesound.org/data/previews/341/341695_5260870-lq.mp3');
let startSound=new Audio('https://freesound.org/data/previews/501/501469_5121236-lq.mp3');

// Clouds
for(let i=0;i<20;i++){clouds.push({x:Math.random()*canvas.width, y:Math.random()*canvas.height/2, size:Math.random()*50+20});}

// Helpers
function randomName(){const names=['NeoPilot','SkyFury','JetAce','StarFly','CloudRider','TurboJet','AeroMax','WindSeeker','AirBlaze','StormWing']; return names[Math.floor(Math.random()*names.length)]+Math.floor(Math.random()*999);}
function randomBet(){return Math.floor(Math.random()*486)+15;} // 15-500

// Draw Scene
function drawScene(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle="#0a0a0a"; ctx.fillRect(0,0,canvas.width,canvas.height);
  
  // Clouds
  ctx.fillStyle="rgba(0,255,255,0.1)";
  clouds.forEach(c=>{ctx.beginPath(); ctx.arc(c.x,c.y,c.size,0,Math.PI*2); ctx.fill();});
  
  // Graph
  ctx.strokeStyle="#00ffcc"; ctx.lineWidth=3; ctx.shadowColor="#00ffcc"; ctx.shadowBlur=10;
  ctx.beginPath();
  for(let i=0;i<graphData.length;i++){let x=i*5; let y=canvas.height-50-graphData[i]*50; if(i==0)ctx.moveTo(x,y);else ctx.lineTo(x,y);}
  ctx.stroke(); ctx.shadowBlur=0;
  
  // Crash line
  if(!running && multiplier>0){
    let crashY=canvas.height-50-crashAt*50;
    ctx.strokeStyle="#ff00ff"; ctx.lineWidth=3; ctx.shadowColor="#ff00ff"; ctx.shadowBlur=15;
    ctx.beginPath(); ctx.moveTo(0,crashY); ctx.lineTo(canvas.width,crashY); ctx.stroke(); ctx.shadowBlur=0;
  }
  
  // Plane trail
  plane.trail.forEach(p=>{ctx.fillStyle="rgba(0,255,255,0.4)"; ctx.beginPath(); ctx.arc(p.x,p.y,10*plane.scale,0,Math.PI*2); ctx.fill();});
  
  // Plane with zoom
  ctx.save(); ctx.translate(plane.x, plane.y); ctx.scale(plane.scale,plane.scale); ctx.rotate(plane.angle); ctx.font=plane.size+"px Arial"; ctx.shadowColor="#00ffff"; ctx.shadowBlur=20; ctx.fillText("✈️",-plane.size/2,0); ctx.restore(); ctx.shadowBlur=0;
  
  // Bot markers
  let scaleX=5;
  botUsers.forEach(b=>{if(!b.cashedOut){let x=graphData.length*scaleX; let y=canvas.height-50-Math.min(multiplier,b.multiplier)*50; ctx.fillStyle="#ff33cc"; ctx.shadowColor="#ff33cc"; ctx.shadowBlur=10; ctx.beginPath(); ctx.arc(x,y,6,0,Math.PI*2); ctx.fill(); ctx.shadowBlur=0;}});
  
  // User marker
  if(userBet.amount>0){let x=graphData.length*scaleX; let y=canvas.height-50-Math.min(multiplier,userBet.multiplier)*50; ctx.fillStyle="#ffcc00"; ctx.shadowColor="#ffcc00"; ctx.shadowBlur=10; ctx.beginPath(); ctx.arc(x,y,8,0,Math.PI*2); ctx.fill(); ctx.shadowBlur=0;}
  
  // Particles
  for(let i=0;i<particles.length;i++){let p=particles[i]; ctx.fillStyle="rgba(255,0,255,"+p.alpha+")"; ctx.beginPath(); ctx.arc(p.x,p.y,p.size,0,Math.PI*2); ctx.fill();}
}

// Particles
function createParticles(x,y){for(let i=0;i<150;i++){particles.push({x:x,y:y,vx:(Math.random()-0.5)*8,vy:(Math.random()-0.5)*8,size:Math.random()*5+2,alpha:1});}}
function updateParticles(){for(let i=particles.length-1;i>=0;i--){let p=particles[i]; p.x+=p.vx; p.y+=p.vy; p.alpha-=0.02; if(p.alpha<=0)particles.splice(i,1);}}

// Bot Box
function updateBotBox(){let box=document.getElementById('botBox'); let html="Bots Info:<br>"; botUsers.forEach(b=>{html+=b.name+" | Bet: "+b.amount+" | Auto: "+b.multiplier+"x<br>";}); box.innerHTML=html;}

// Start Game
function startGame(){
  if(running)return;
  startSound.play();
  let amt=parseInt(document.getElementById('betAmount').value);
  let mul=parseFloat(document.getElementById('betMultiplier').value);
  if(amt>coins){alert("Not enough coins"); return;}
  userBet={amount:amt,multiplier:mul,cashedOut:false,won:0}; coins-=amt; updateCoins();
  
  // Bots 15–500
  botUsers=[]; let botCount=Math.floor(Math.random()*486)+15;
  for(let i=0;i<botCount;i++){botUsers.push({name:randomName(),amount:randomBet(),multiplier:(Math.random()*4+1).toFixed(2),cashedOut:false,won:0});}
  updateBotBox();
  
  running=true; multiplier=1.00; crashAt=(Math.random()*5+1.5).toFixed(2); plane.x=canvas.width/2; plane.y=canvas.height-100; plane.trail=[]; plane.angle=0; plane.scale=1; graphData=[]; particles=[]; document.getElementById('status').innerText="";
  
  let interval=setInterval(()=>{
    if(!running){clearInterval(interval); return;}
    multiplier+=0.02*(1+multiplier/10);
    document.getElementById('multiplier').innerText=multiplier.toFixed(2)+'x';
    
    // Plane animation
    plane.angle=Math.sin(multiplier/2)/5;
    plane.scale=1+multiplier/10; 
    let planeY=canvas.height-100-multiplier*50; plane.trail.push({x:plane.x,y:plane.y}); if(plane.trail.length>20)plane.trail.shift(); plane.y=planeY;
    clouds.forEach(c=>{c.x-=0.3;if(c.x<0)c.x=canvas.width+Math.random()*100;});
    graphData.push(multiplier);
    
    // Bots cash-out
    botUsers.forEach(b=>{if(!b.cashedOut && multiplier>=b.multiplier){b.cashedOut=true; b.won=Math.floor(b.amount*b.multiplier); coins+=b.won;}});
    
    // User auto cash-out
    if(userBet.amount>0 && !userBet.cashedOut && multiplier>=userBet.multiplier){userBet.cashedOut=true; userBet.won=Math.floor(userBet.amount*userBet.multiplier); coins+=userBet.won; coinSound.play(); history.push("User auto cash out @ "+userBet.multiplier+"x"); updateHistory();}
    
    drawScene(); updateParticles();
    
    if(multiplier>=crashAt){
      running=false; 
      document.getElementById('status').innerHTML="<span style='color:#ff33ff; font-size:18px;'>CRASH 💥 @ "+crashAt+"x</span>"; 
      if(!userBet.cashedOut){userBet.won=0; history.push("User LOST @ crash "+crashAt+"x");} 
      botUsers.forEach(b=>{if(!b.cashedOut)b.won=0;}); 
      crashSound.play(); createParticles(plane.x, plane.y); updateHistory();
    }
    
    updateBotBox();
  },50);
}

// Cash Out
function cashOut(){if(!running || userBet.cashedOut)return; userBet.cashedOut=true; userBet.won=Math.floor(userBet.amount*multiplier); coins+=userBet.won; updateCoins(); coinSound.play(); history.push("User cashed out @ "+multiplier.toFixed(2)+"x"); updateHistory();}

// History
function updateHistory(){let histEl=document.getElementById('history'); let lines=history.slice(-15).reverse(); botUsers.forEach((b,i)=>{if(b.cashedOut)lines.push(b.name+" cashed out @ "+b.multiplier+"x");}); histEl.innerHTML="History:<br>"+lines.join("<br>");}
</script>

</body>
</html>
