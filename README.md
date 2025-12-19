<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Lucky Draw • Firebase Free</title>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore-compat.js"></script>
<style>
body { margin:0; font-family:Arial,sans-serif; background:linear-gradient(135deg,#0f2027,#203a43,#2c5364); color:#fff; }
header { padding:20px; text-align:center; background:rgba(0,0,0,0.4); }
header h1{margin:0;font-size:28px;}
.container{padding:20px;}
.card{background:rgba(255,255,255,0.1); border-radius:15px; padding:20px; margin-bottom:20px; box-shadow:0 10px 30px rgba(0,0,0,0.3);}
.card h2{margin-top:0;}
.btn{display:inline-block;padding:12px 20px;background:#00c6ff;color:#000;border-radius:25px;text-decoration:none;font-weight:bold;margin-top:10px;cursor:pointer;}
.input-field{width:100%; padding:10px; margin:8px 0; border-radius:8px; border:none;}
.stats{display:grid; grid-template-columns:repeat(auto-fit,minmax(150px,1fr)); gap:15px;}
.stat{background:rgba(0,0,0,0.4);padding:15px;border-radius:12px;text-align:center;}
.spin-wheel{width:220px;height:220px;border-radius:50%;margin:20px auto;background:conic-gradient(#00c6ff 0deg 60deg,#0072ff 60deg 120deg,#00c6ff 120deg 180deg,#0072ff 180deg 240deg,#00c6ff 240deg 300deg,#0072ff 300deg 360deg);display:flex;align-items:center;justify-content:center;font-weight:bold;color:#000;box-shadow:0 0 20px rgba(0,198,255,0.8);animation:spin 6s linear infinite;}
@keyframes spin{from{transform:rotate(0deg);}to{transform:rotate(360deg);}}
.mobile-nav{position:fixed; bottom:0; left:0; right:0; background:rgba(0,0,0,0.7); display:flex; justify-content:space-around; padding:10px 0;}
.mobile-nav a{color:#00c6ff; text-decoration:none; font-size:14px; cursor:pointer;}
</style>
</head>
<body>

<header>
<h1>Lucky Draw • Firebase Free</h1>
</header>

<!-- Login -->
<div class="container" id="login-page">
<div class="card">
<h2>Login / Signup</h2>
<input type="text" placeholder="Username" id="username" class="input-field">
<button class="btn" onclick="loginUser()">Login</button>
</div>
</div>

<!-- Dashboard -->
<div class="container" id="dashboard-page" style="display:none;">
<div class="card">
<h2>User Dashboard</h2>
<div class="stats">
<div class="stat"><h3>Coins</h3><p id="user-coins">0</p></div>
<div class="stat"><h3>Draws Played</h3><p id="draws-played">0</p></div>
<div class="stat"><h3>Rewards Won</h3><p id="rewards-won">0</p></div>
</div>
</div>

<div class="card">
<h2>Spin Wheel</h2>
<div class="spin-wheel" id="spin-wheel">SPIN</div>
<button class="btn" onclick="spinWheel()">Spin Now</button>
</div>

<div class="card">
<h2>Buy Chance</h2>
<input type="number" placeholder="Number of chances" id="buy-chances" class="input-field">
<button class="btn" onclick="buyChances()">Buy</button>
</div>

<div class="card">
<h2>Manual Deposit</h2>
<input type="number" placeholder="Coins to deposit" id="deposit-amount" class="input-field">
<button class="btn" onclick="depositCoins()">Deposit</button>
</div>

<div class="card">
<h2>Manual Withdrawal</h2>
<input type="number" placeholder="Coins to withdraw" id="withdraw-amount" class="input-field">
<button class="btn" onclick="withdrawCoins()">Withdraw</button>
</div>
</div>

<footer>© 2025 Lucky Draw | Firebase Free Tier</footer>

<div class="mobile-nav">
<a onclick="showDashboard()">Home</a>
<a onclick="scrollToDraw()">Draw</a>
<a>Wallet</a>
<a>Profile</a>
</div>

<script>
// Firebase config - replace with your project config
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
firebase.initializeApp(firebaseConfig);
const db = firebase.firestore();

let currentUser = null;

function loginUser() {
  const username = document.getElementById('username').value.trim();
  if(!username){ alert('Enter username'); return; }
  currentUser = username;
  const userRef = db.collection('users').doc(username);
  userRef.get().then(doc=>{
    if(!doc.exists){
      userRef.set({ coins:1250, draws:0, rewards:0 });
    }
    document.getElementById('login-page').style.display='none';
    document.getElementById('dashboard-page').style.display='block';
    loadUserData();
  });
}

function loadUserData(){
  const userRef = db.collection('users').doc(currentUser);
  userRef.get().then(doc=>{
    const data = doc.data();
    document.getElementById('user-coins').innerText = data.coins;
    document.getElementById('draws-played').innerText = data.draws;
    document.getElementById('rewards-won').innerText = data.rewards;
  });
}

function spinWheel(){
  const reward = Math.floor(Math.random()*500+50);
  alert('You won '+reward+' coins!');
  const userRef = db.collection('users').doc(currentUser);
  db.runTransaction(transaction=>{
    return transaction.get(userRef).then(doc=>{
      const newCoins = doc.data().coins + reward;
      const newDraws = doc.data().draws +1;
      transaction.update(userRef,{coins:newCoins, draws:newDraws});
    });
  }).then(()=>loadUserData());
}

function buyChances(){
  const buy = parseInt(document.getElementById('buy-chances').value);
  if(isNaN(buy)||buy<=0){ alert('Enter valid number'); return; }
  const userRef = db.collection('users').doc(currentUser);
  db.runTransaction(transaction=>{
    return transaction.get(userRef).then(doc=>{
      const coinsCost = buy*100;
      if(doc.data().coins<coinsCost){ alert('Not enough coins'); return; }
      transaction.update(userRef,{coins:doc.data().coins-coinsCost});
    });
  }).then(()=>loadUserData());
}

function depositCoins(){
  const dep = parseInt(document.getElementById('deposit-amount').value);
  if(isNaN(dep)||dep<=0){ alert('Enter valid amount'); return; }
  const userRef = db.collection('users').doc(currentUser);
  db.update(userRef,{coins:firebase.firestore.FieldValue.increment(dep)}).then(()=>loadUserData());
}

function withdrawCoins(){
  const wit = parseInt(document.getElementById('withdraw-amount').value);
  if(isNaN(wit)||wit<=0){ alert('Enter valid amount'); return; }
  const userRef = db.collection('users').doc(currentUser);
  db.runTransaction(transaction=>{
    return transaction.get(userRef).then(doc=>{
      if(doc.data().coins<wit){ alert('Not enough coins'); return; }
      transaction.update(userRef,{coins:doc.data().coins-wit});
    });
  }).then(()=>loadUserData());
}

function showDashboard(){
  document.getElementById('login-page').style.display='none';
  document.getElementById('dashboard-page').style.display='block';
  loadUserData();
}

function scrollToDraw(){
  document.getElementById('spin-wheel').scrollIntoView({behavior:'smooth'});
}
</script>

</body>
</html>
