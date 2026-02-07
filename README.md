<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Future Pro Hub</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">

<!-- PWA manifest -->
<link rel="manifest" href="manifest.json">

<style>
:root{
  --primary:#0f172a;
  --secondary:#1e293b;
  --accent:#3b82f6;
  --bg:#f0f2f5;
  --text:#111;
}
*{margin:0;padding:0;box-sizing:border-box;font-family:'Roboto',sans-serif;}
body{background:var(--bg);color:var(--text);transition:0.3s;}
header{background:var(--primary);color:white;padding:60px 20px;text-align:center;position:relative;}
header h1{font-size:3em;margin-bottom:10px;animation:fadeDown 1s;}
header p{font-size:1.3em;color:#a0aec0;animation:fadeUp 1s;}
@keyframes fadeDown{0%{opacity:0;transform:translateY(-30px);}100%{opacity:1;transform:translateY(0);}}
@keyframes fadeUp{0%{opacity:0;transform:translateY(30px);}100%{opacity:1;transform:translateY(0);}}

nav{display:flex;justify-content:center;gap:20px;padding:15px;background:white;box-shadow:0 2px 10px rgba(0,0,0,0.1);flex-wrap:wrap;position:sticky;top:0;z-index:100;}
nav a{text-decoration:none;color:var(--primary);font-weight:500;padding:10px 20px;border-radius:8px;transition:0.3s;font-size:1em;}
nav a:hover{background:var(--accent);color:white;transform:scale(1.05);}

section{padding:80px 20px;max-width:1200px;margin:auto;}
h2{font-size:2.2em;color:var(--primary);margin-bottom:30px;text-align:center;position:relative;}
h2::after{content:"";width:60px;height:3px;background:var(--accent);display:block;margin:10px auto 0;border-radius:2px;}

.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:30px;align-items:start;}

.card{background:white;padding:30px;border-radius:15px;box-shadow:0 6px 20px rgba(0,0,0,0.1);transition:0.4s;position:relative;overflow:hidden;cursor:pointer;}
.card:hover{transform:translateY(-10px) scale(1.02);box-shadow:0 10px 25px rgba(0,0,0,0.2);}
.card h3{margin-bottom:15px;color:var(--primary);}
.card p{color:#4a5568;line-height:1.5;}
.card button{margin-top:15px;padding:12px 20px;border:none;border-radius:8px;background:var(--accent);color:white;cursor:pointer;font-weight:500;transition:0.3s;}
.card button:hover{background:var(--secondary);transform:scale(1.05);}

/* Inputs */
input{padding:10px;margin:8px 0;width:90%;border-radius:8px;border:1px solid #ccc;transition:0.3s;}
input:focus{outline:none;border-color:var(--accent);box-shadow:0 0 5px var(--accent);}

/* Footer */
footer{background:var(--primary);color:white;text-align:center;padding:25px;margin-top:40px;letter-spacing:1px;}
footer p{font-size:0.9em;}

/* Dark Mode Toggle */
.toggle-container{position:absolute;top:20px;right:20px;}
.toggle-container input{display:none;}
.toggle-container label{cursor:pointer;width:50px;height:26px;background:#ccc;display:block;border-radius:15px;position:relative;}
.toggle-container label::after{content:"";width:22px;height:22px;background:white;position:absolute;top:2px;left:2px;border-radius:50%;transition:0.3s;}
.toggle-container input:checked + label::after{transform:translateX(24px);}
.toggle-container input:checked + label{background:var(--accent);}
body.dark{background:#111;color:white;}
body.dark header{background:#1e293b;}
body.dark nav{background:#0f172a;}
body.dark .card{background:#1a202c;color:white;}
body.dark input{background:#111;color:white;border:1px solid #555;}
body.dark footer{background:#1e293b;}
</style>
</head>
<body>

<header>
  <h1>Future Pro Hub</h1>
  <p>Modern Portfolio & Skill Hub – Learn, Track & Earn</p>

  <!-- Dark Mode Toggle -->
  <div class="toggle-container">
    <input type="checkbox" id="darkToggle">
    <label for="darkToggle"></label>
  </div>
</header>

<nav>
  <a href="#services">Services</a>
  <a href="#portfolio">Portfolio</a>
  <a href="#tools">Tools</a>
  <a href="#contact">Contact</a>
</nav>

<section id="services">
  <h2>🚀 My Services</h2>
  <div class="cards">
    <div class="card">
      <h3>Web Development</h3>
      <p>Create responsive, modern websites for clients & projects.</p>
      <button onclick="gainPoints(5)">Hire Me (+5 points)</button>
    </div>
    <div class="card">
      <h3>UI/UX Design</h3>
      <p>Design sleek, user-friendly interfaces for apps & websites.</p>
      <button onclick="gainPoints(5)">Hire Me (+5 points)</button>
    </div>
    <div class="card">
      <h3>Freelance Consulting</h3>
      <p>Guide freelancers to earn online & showcase their work.</p>
      <button onclick="gainPoints(5)">Consult (+5 points)</button>
    </div>
  </div>
</section>

<section id="portfolio">
  <h2>💼 Portfolio</h2>
  <div class="cards">
    <div class="card">
      <h3>Project 1</h3>
      <p>Responsive website with modern UI & client-ready design.</p>
      <button onclick="alert('View Project!')">View</button>
    </div>
    <div class="card">
      <h3>Project 2</h3>
      <p>Interactive dashboard for analytics & productivity.</p>
      <button onclick="alert('View Project!')">View</button>
    </div>
    <div class="card">
      <h3>Project 3</h3>
      <p>Freelance platform prototype with earning features.</p>
      <button onclick="alert('View Project!')">View</button>
    </div>
  </div>
</section>

<section id="tools">
  <h2>🛠 Mini Tools</h2>
  <div class="cards">
    <div class="card">
      <h3>Expense Tracker</h3>
      <input type="number" id="income" placeholder="Enter Income">
      <input type="number" id="expense" placeholder="Enter Expense">
      <button onclick="trackExpense()">Add & Calculate</button>
      <p id="expenseResult"></p>
    </div>
    <div class="card">
      <h3>Habit Tracker</h3>
      <input type="text" id="habit" placeholder="Enter Habit">
      <button onclick="addHabit()">Add Habit</button>
      <ul id="habitList"></ul>
    </div>
  </div>
</section>

<section id="contact">
  <h2>📩 Contact Me</h2>
  <div class="cards">
    <div class="card">
      <h3>Email</h3>
      <p>yourname@example.com</p>
      <button onclick="alert('Send Email!')">Send</button>
    </div>
    <div class="card">
      <h3>LinkedIn</h3>
      <p>linkedin.com/in/yourprofile</p>
      <button onclick="alert('Visit LinkedIn!')">Visit</button>
    </div>
    <div class="card">
      <h3>Portfolio</h3>
      <p>Full project showcase.</p>
      <button onclick="alert('View Portfolio!')">View</button>
    </div>
  </div>
</section>

<footer>
  <p>© 2026 Future Pro Hub | All Rights Reserved</p>
</footer>

<script>
let points = 0;

// Dark mode toggle
const toggle = document.getElementById('darkToggle');
toggle.addEventListener('change',()=>{document.body.classList.toggle('dark');});

// Gain points for actions
function gainPoints(p){
  points += p;
  document.getElementById('pointsDisplay').innerText = points;
}

// Expense Tracker
function trackExpense(){
  let inc = Number(document.getElementById('income').value);
  let exp = Number(document.getElementById('expense').value);
  if(!isNaN(inc) && !isNaN(exp)){
    let balance = inc - exp;
    document.getElementById('expenseResult').innerText = 'Balance: ' + balance;
    gainPoints(1);
  } else { alert('Enter valid numbers'); }
}

// Habit Tracker
function addHabit(){
  let habit = document.getElementById('habit').value;
  if(habit){
    let li = document.createElement('li');
    li.innerText = habit;
    document.getElementById('habitList').appendChild(li);
    document.getElementById('habit').value = '';
    gainPoints(1);
  }
}
</script>

</body>
</html>
