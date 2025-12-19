<Lucky>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lucky Draw App</title>
<script type="module">
  // Firebase imports
  import { initializeApp } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-app.js";
  import { getFirestore, doc, getDoc, setDoc, updateDoc, increment } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore.js";

  // 🔥 Your Firebase Config
  const firebaseConfig = {
    apiKey: "AIzaSyA0_NaAYDKQuoEO58Od7LhZ5enZA-GIP9M",
    authDomain: "lucky-draw-12ebd.firebaseapp.com",
    projectId: "lucky-draw-12ebd",
    storageBucket: "lucky-draw-12ebd.firebasestorage.app",
    messagingSenderId: "695988718336",
    appId: "1:695988718336:web:0917d70fe19646992481e5"
  };

  const app = initializeApp(firebaseConfig);
  const db = getFirestore(app);
  let currentUser = null;

  // Login / Signup
  async function loginUser() {
    const username = document.getElementById('username').value.trim();
    if(!username){ alert('Enter username'); return; }
    currentUser = username;
    const userRef = doc(db, "users", username);
    const userSnap = await getDoc(userRef);
    if(!userSnap.exists()){
      await setDoc(userRef, { coins: 1250, draws: 0, rewards: 0 });
    }
    document.getElementById('login-page').style.display = 'none';
    document.getElementById('app-page').style.display = 'block';
    loadUserData();
  }

  // Load user data
  async function loadUserData(){
    const userRef = doc(db, "users", currentUser);
    const userSnap = await getDoc(userRef);
    const data = userSnap.data();
    document.getElementById('coins').innerText = data.coins;
    document.getElementById('draws').innerText = data.draws;
    document.getElementById('rewards').innerText = data.rewards;
  }

  // Spin Wheel
  async function spinWheel(){
    const reward = Math.floor(Math.random()*500+50);
    alert('You won '+reward+' coins!');
    const userRef = doc(db, "users", currentUser);
    await updateDoc(userRef, {
      coins: increment(reward),
      draws: increment(1),
      rewards: increment(reward)
    });
    loadUserData();
  }

  // Buy Chance
  async function buyChances(){
    const count = parseInt(document.getElementById('buy-chances').value);
    if(isNaN(count)||count<=0){ alert('Enter valid number'); return; }
    const userRef = doc(db, "users", currentUser);
    const userSnap = await getDoc(userRef);
    const cost = count*100;
    if(userSnap.data().coins < cost){ alert('Not enough coins'); return; }
    await updateDoc(userRef, { coins: increment(-cost) });
    loadUserData();
  }

  // Deposit
  async function depositCoins(){
    const amount = parseInt(document.getElementById('deposit-amount').value);
    if(isNaN(amount)||amount<=0){ alert('Enter valid amount'); return; }
    const userRef = doc(db, "users", currentUser);
    await updateDoc(userRef, { coins: increment(amount) });
    loadUserData();
  }

  // Withdraw
  async function withdrawCoins(){
    const amount = parseInt(document.getElementById('withdraw-amount').value);
    if(isNaN(amount)||amount<=0){ alert('Enter valid amount'); return; }
    const userRef = doc(db, "users", currentUser);
    const userSnap = await getDoc(userRef);
    if(userSnap.data().coins < amount){ alert('Not enough coins'); return; }
    await updateDoc(userRef, { coins: increment(-amount) });
    loadUserData();
  }
</script>

<style>
body { margin:0; font-family:'Segoe UI',sans-serif; background:#121212; color:#fff; }
header{background:#1f1f1f; padding:15px; text-align:center; font-size:24px; font-weight:bold; }
.container{padding:20px;}
.card{background:#1e1e1e; border-radius:12px; padding:20px; margin-bottom:15px; box-shadow:0 5px 15px rgba(0,0,0,0.5);}
.btn{background:#00c6ff; color:#000; padding:10px 18px; border:none; border-radius:25px; cursor:pointer; font-weight:bold; margin-top:10px;}
.input-field{width:100%; padding:10px; border-radius:8px; margin:6px 0; border:none; background:#2a2a2a; color:#fff;}
.stats{display:flex; justify-content:space-around; margin-top:15px;}
.stat{text-align:center;}
.spin-wheel{width:200px; height:200px; margin:20px auto; border-radius:50%; background:conic-gradient(#00c6ff 0deg 60deg,#0072ff 60deg 120deg,#00c6ff 120deg 180deg,#0072ff 180deg 240deg,#00c6ff 240deg 300deg,#0072ff 300deg 360deg); display:flex; align-items:center; justify-content:center; font-weight:bold; color:#000; box-shadow:0 0 15px #00c6ff;}
footer{text-align:center; padding:10px; background:#1f1f1f; font-size:14px;}
</style>

<body>
<header>🎰 Lucky Draw App</header>

<div class="container" id="login-page">
  <div class="card">
    <h2>Login / Signup</h2>
    <input type="text" placeholder="Enter username" id="username" class="input-field">
    <button class="btn" onclick="loginUser()">Login</button>
  </div>
</div>

<div class="container" id="app-page" style="display:none;">
  <div class="card">
    <h2>User Dashboard</h2>
    <div class="stats">
      <div class="stat"><h3>Coins</h3><p id="coins">0</p></div>
      <div class="stat"><h3>Draws</h3><p id="draws">0</p></div>
      <div class="stat"><h3>Rewards</h3><p id="rewards">0</p></div>
    </div>
  </div>

  <div class="card">
    <h2>Spin Wheel</h2>
    <div class="spin-wheel">SPIN</div>
    <button class="btn" onclick="spinWheel()">Spin Now</button>
  </div>

  <div class="card">
    <h2>Buy Chance</h2>
    <input type="number" id="buy-chances" class="input-field" placeholder="Number of chances">
    <button class="btn" onclick="buyChances()">Buy</button>
  </div>

  <div class="card">
    <h2>Deposit Coins</h2>
    <input type="number" id="deposit-amount" class="input-field" placeholder="Coins to deposit">
    <button class="btn" onclick="depositCoins()">Deposit</button>
  </div>

  <div class="card">
    <h2>Withdraw Coins</h2>
    <input type="number" id="withdraw-amount" class="input-field" placeholder="Coins to withdraw">
    <button class="btn" onclick="withdrawCoins()">Withdraw</button>
  </div>
</div>

<footer>© 2025 Lucky Draw | Firebase Ready</footer>
</body>
</html>
