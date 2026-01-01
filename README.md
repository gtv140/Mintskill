<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Mini Gambling Demo (Coins Only)</title>
<style>
  body{font-family:Arial;background:#0f1220;color:#fff;text-align:center}
  .box{max-width:500px;margin:20px auto;padding:20px;border-radius:12px;background:#1b1f3b}
  h2{margin-bottom:10px;}
  .mult,.coins{font-size:24px;margin:10px 0;}
  button{padding:10px 16px;border:0;border-radius:8px;margin:5px;font-size:16px;cursor:pointer}
  .start{background:#2ecc71}
  .cash{background:#f1c40f}
  .crash{color:#ff6b6b}
  .cards,.fish{margin:10px 0;}
  .card{display:inline-block;width:60px;height:80px;margin:3px;line-height:80px;font-size:24px;background:#fff;color:#000;border-radius:8px;}
</style>
</head>
<body>

<div class="box">
  <h2>Coins: <span id="coins">100</span></h2>

  <!-- Aviator -->
  <h3>Aviator ✈️</h3>
  <div class="mult" id="aviMult">1.00x</div>
  <div id="aviStatus"></div>
  <button class="start" onclick="startAviator()">Start Aviator</button>
  <button class="cash" onclick="cashOutAviator()">Cash Out</button>

  <hr style="margin:20px 0;border-color:#555">

  <!-- Cards -->
  <h3>Cards 🎴</h3>
  <div class="cards" id="cardsArea"></div>
  <button class="start" onclick="playCards()">Play Cards</button>
  <div id="cardsStatus"></div>

  <hr style="margin:20px 0;border-color:#555">

  <!-- Fishing -->
  <h3>Fishing 🎣</h3>
  <div class="fish" id="fishArea">🎣</div>
  <button class="start" onclick="playFishing()">Catch Fish</button>
  <div id="fishStatus"></div>
</div>

<script>
let coins = 100;

/* --------- Aviator --------- */
let running=false, m=1.00, timer=null, crashAt=0;
function startAviator(){
  if(running) return;
  running=true; m=1.00;
  crashAt = (Math.random()*3 + 1.2).toFixed(2);
  document.getElementById('aviStatus').innerText="";
  timer=setInterval(()=>{
    m+=0.02;
    document.getElementById('aviMult').innerText=m.toFixed(2)+"x";
    if(m>=crashAt){
      clearInterval(timer);
      running=false;
      document.getElementById('aviStatus').innerHTML="<span class='crash'>CRASH 💥 @ "+crashAt+"x</span>";
      coins-=10; updateCoins();
    }
  },100);
}
function cashOutAviator(){
  if(!running) return;
  clearInterval(timer);
  running=false;
  document.getElementById('aviStatus').innerText="Cashed out @ "+m.toFixed(2)+"x";
  coins += Math.floor(10*m); updateCoins();
}

/* --------- Cards --------- */
function playCards(){
  let suits = ["♠","♥","♦","♣"];
  let nums = ["A","2","3","4","5","6","7","8","9","10","J","Q","K"];
  let area = document.getElementById('cardsArea');
  area.innerHTML="";
  for(let i=0;i<3;i++){
    let card = document.createElement("div");
    card.className="card";
    let n = nums[Math.floor(Math.random()*nums.length)];
    let s = suits[Math.floor(Math.random()*suits.length)];
    card.innerText = n+s;
    area.appendChild(card);
  }
  // Simple win/lose
  let win = Math.random() < 0.5;
  document.getElementById('cardsStatus').innerText = win ? "You won 15 coins!" : "You lost 10 coins!";
  coins += win?15:-10; updateCoins();
}

/* --------- Fishing --------- */
function playFishing(){
  let fish = ["🐟","🐠","🦈","🐡","🐬"];
  let catchFish = fish[Math.floor(Math.random()*fish.length)];
  document.getElementById('fishArea').innerText = catchFish;
  let win = Math.random() < 0.6; // 60% chance
  document.getElementById('fishStatus').innerText = win ? "Fish caught! +10 coins" : "Fish escaped! -5 coins";
  coins += win?10:-5; updateCoins();
}

function updateCoins(){
  document.getElementById('coins').innerText = coins;
}
</script>

</body>
</html>
