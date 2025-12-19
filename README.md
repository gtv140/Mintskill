<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Lucky Draw • Rewards Platform</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
      color: #fff;
    }
    header {
      padding: 20px;
      text-align: center;
      background: rgba(0,0,0,0.4);
    }
    header h1 {
      margin: 0;
      font-size: 28px;
    }
    .container {
      padding: 20px;
    }
    .card {
      background: rgba(255,255,255,0.1);
      border-radius: 15px;
      padding: 20px;
      margin-bottom: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    }
    .card h2 {
      margin-top: 0;
    }
    .btn {
      display: inline-block;
      padding: 12px 20px;
      background: #00c6ff;
      color: #000;
      border-radius: 25px;
      text-decoration: none;
      font-weight: bold;
      margin-top: 10px;
    }
    .stats {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 15px;
    }
    .stat {
      background: rgba(0,0,0,0.4);
      padding: 15px;
      border-radius: 12px;
      text-align: center;
    }
    footer {
      text-align: center;
      padding: 15px;
      background: rgba(0,0,0,0.5);
      font-size: 14px;
    }
    .spin-wheel {
      width: 220px;
      height: 220px;
      border-radius: 50%;
      margin: 20px auto;
      background: conic-gradient(#00c6ff 0deg 60deg, #0072ff 60deg 120deg, #00c6ff 120deg 180deg, #0072ff 180deg 240deg, #00c6ff 240deg 300deg, #0072ff 300deg 360deg);
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      color: #000;
      box-shadow: 0 0 20px rgba(0,198,255,0.8);
      animation: spin 6s linear infinite;
    }
    @keyframes spin {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }
    .login-box input {
      width: 100%;
      padding: 10px;
      margin: 8px 0;
      border-radius: 8px;
      border: none;
    }
    .mobile-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      background: rgba(0,0,0,0.7);
      display: flex;
      justify-content: space-around;
      padding: 10px 0;
    }
    .mobile-nav a {
      color: #00c6ff;
      text-decoration: none;
      font-size: 14px;
    }
  </style>
</head>
<body>
  <header>
    <h1>🎁 Lucky Draw Rewards</h1>
    <p>Daily Draw • Fair • Trusted</p>
  </header>

  <div class="container">
    <div class="card login-box">
      <h2>Login / Signup</h2>
      <input type="text" placeholder="Username">
      <input type="password" placeholder="Password">
      <a href="#" class="btn">Login</a>
    </div>

    <div class="card">
      <h2>User Dashboard</h2>
      <div class="stats">
        <div class="stat">
          <h3>Coins</h3>
          <p>1,250</p>
        </div>
        <div class="stat">
          <h3>Draws Played</h3>
          <p>32</p>
        </div>
        <div class="stat">
          <h3>Rewards Won</h3>
          <p>PKR 4,800</p>
        </div>
      </div>
    </div>

    <div class="card">
      <h2>Lucky Draw Games</h2>
      <div class="spin-wheel">SPIN</div>
      <p>Spin the wheel & win coins, vouchers or cash rewards.</p>
      <a href="#" class="btn">Spin Now</a>
    </div>

    <div class="card">
      <h2>Redeem Rewards</h2>
      <p>Redeem rewards to Easypaisa / JazzCash / Bank.</p>
      <a href="#" class="btn">Redeem Now</a>
    </div>
  </div>

  <footer>
    © 2025 Lucky Draw Platform | Demo UI • Skill & Luck Based
  </footer>

  <div class="mobile-nav">
    <a href="#">Home</a>
    <a href="#">Draw</a>
    <a href="#">Wallet</a>
    <a href="#">Profile</a>
  </div>
</body>
</html>
