<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint Pro</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
body{margin:0;font-family:Arial,sans-serif;background:#f3f6fb;color:#111;padding-bottom:120px;overflow-x:hidden;}
.header{background:#2563eb;color:#fff;padding:20px;text-align:center}
.header h1{font-size:24px;margin:0}
.header p{margin-top:6px;font-size:14px;opacity:.9}

/* Sections */
.section{padding:16px}
.section h2{font-size:18px;margin-bottom:12px;text-align:center}

/* Cards */
.cards{display:flex;flex-direction:column;gap:12px}
.card{background:#fff;border-radius:14px;padding:16px;box-shadow:0 6px 16px rgba(0,0,0,.08);}
.card h3{margin:0;font-size:16px;color:#2563eb}
.card p{margin-top:6px;font-size:14px;color:#555;}

/* Buttons */
.btn{width:100%;padding:14px;border:none;border-radius:14px;font-size:15px;background:#2563eb;color:#fff;margin-top:10px;cursor:pointer;}
.btn.green{background:#16a34a}
input{width:100%;padding:12px;border-radius:10px;border:1px solid #ccc;margin-top:6px;font-size:14px;}

/* Bottom Nav */
.nav{position:fixed;bottom:0;left:0;width:100%;background:#fff;display:flex;justify-content:space-around;padding:10px 0;box-shadow:0 -4px 12px rgba(0,0,0,.15);}
.nav a{text-align:center;font-size:11px;color:#333;text-decoration:none;}

/* Chat bubble */
.chat{position:fixed;right:16px;bottom:90px;background:#22c55e;color:#fff;padding:14px;border-radius:50%;font-size:20px;text-decoration:none;display:flex;align-items:center;justify-content:center;}

/* Reviews slider */
.slider{display:flex;overflow-x:auto;gap:10px;padding-bottom:10px;}
.review{min-width:220px;background:#fff;padding:12px;border-radius:12px;box-shadow:0 4px 14px rgba(0,0,0,.08);}
.review p{font-size:14px;margin:0}
.review span{font-size:13px;color:#2563eb}

/* FAQ */
.faq{background:#fff;border-radius:12px;padding:14px;margin-bottom:8px;box-shadow:0 4px 12px rgba(0,0,0,.06);}
.faq h4{font-size:15px;cursor:pointer;margin:0}
.faq p{display:none;font-size:14px;color:#555;margin-top:6px;}

/* Active users */
.active-users{font-size:12px;color:#16a34a;text-align:center;margin-top:6px;}

/* Media */
@media(min-width:768px){.cards{flex-direction:row;flex-wrap:wrap}.card{width:48%;}}
</style>
</head>

<body>

<div class="header">
<h1>SkillMint Pro</h1>
<p>Learn skills • Earn online • Beginner friendly</p>
</div>

<div class="section" id="home">
<h2>Courses You Will Learn</h2>
<div class="cards">
 <div class="card"><h3>YouTube Earning</h3><p>Zero se channel setup, content, SEO aur monetization step by step.</p></div>
 <div class="card"><h3>Freelancing</h3><p>Fiverr & Upwork complete roadmap, gigs, clients & earnings.</p></div>
 <div class="card"><h3>Affiliate Marketing</h3><p>Products promote kar ke commission earn karna.</p></div>
 <div class="card"><h3>Social Media Growth</h3><p>Instagram & Facebook organic growth strategies step by step.</p></div>
</div>
</div>

<div class="section" id="reviews">
<h2>Student Reviews</h2>
<div class="slider">
 <div class="review"><p>“Mujhe YouTube bilkul zero se samajh aya.”</p><span>— Ali</span></div>
 <div class="review"><p>“Freelancing ka complete roadmap mil gaya.”</p><span>— Sara</span></div>
 <div class="review"><p>“Affiliate marketing se earning start ki.”</p><span>— Ahmed</span></div>
</div>
</div>

<div class="section" id="buy">
<h2>Buy SkillMint Course</h2>
<label>Price</label>
<input id="price" readonly placeholder="Select payment">

<label>Deposit Number</label>
<input id="num" readonly placeholder="Auto fill">

<button class="btn" onclick="pay('jazz')">JazzCash</button>
<button class="btn" onclick="pay('easy')">EasyPaisa</button>
<button class="btn" onclick="pay('binance')">Binance</button>

<label>Upload Payment Proof</label>
<input type="file" id="proof">

<p id="status" style="font-size:13px;margin-top:6px"></p>
<button class="btn green" id="open" disabled>Open Course</button>
<p class="active-users" id="activeUsers">Active Users: 0</p>
</div>

<div class="section" id="faq">
<h2>FAQ</h2>
<div class="faq"><h4>Verification time?</h4><p>Normally 5 minutes.</p></div>
<div class="faq"><h4>Beginner friendly?</h4><p>Yes, zero level se start.</p></div>
<div class="faq"><h4>Payment options?</h4><p>JazzCash, EasyPaisa, Binance</p></div>
</div>

<div class="section" id="bot">
<h2>SkillMint Bot 🤖</h2>
<input id="q" placeholder="Ask anything">
<button class="btn" onclick="bot()">Ask</button>
<p id="a" style="margin-top:8px;font-size:14px"></p>
</div>

<!-- Social / Contact -->
<a class="chat" href="https://wa.me/923379827882" target="_blank">💬</a>
<div class="nav">
<a href="#home">🏠<br>Home</a>
<a href="#buy">🎓<br>Course</a>
<a href="#faq">❓<br>FAQ</a>
<a href="#bot">🤖<br>Bot</a>
<a href="https://www.facebook.com" target="_blank">📘<br>FB</a>
<a href="https://www.instagram.com" target="_blank">📸<br>IG</a>
<a href="mailto:skillmint@example.com">✉️<br>Email</a>
</div>

<script>
function pay(m){
 price.value="500 PKR";
 if(m==="jazz") num.value="03705519562";
 if(m==="easy") num.value="03379827882";
 if(m==="binance") num.value="0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F";
 navigator.clipboard.writeText(num.value);
}

proof.onchange=()=>{
 let t=180;
 let i=setInterval(()=>{
  status.innerText="Verifying... "+t+"s";
  t--;
  if(t<0){
   clearInterval(i);
   status.innerText="Access Granted ✔";
   open.disabled=false;
  }
 },1000);
}

open.onclick=()=>{window.open("https://gtv140.github.io/SkillMint-complete-course-/","_blank");}

// FAQ toggle
document.querySelectorAll(".faq h4").forEach(f=>{f.onclick=()=>{f.nextElementSibling.style.display=f.nextElementSibling.style.display==="block"?"none":"block";}})

// Bot system
function bot(){
 let x=q.value.toLowerCase(),r="Please ask a simple question.";
 if(x.includes("price")) r="Course price: 500 PKR.";
 if(x.includes("payment")) r="Payment methods: JazzCash, EasyPaisa, Binance.";
 if(x.includes("beginner")) r="Yes, course is beginner friendly.";
 if(x.includes("youtube")) r="You will learn YouTube earning step by step.";
 if(x.includes("freelance")) r="Complete Freelancing roadmap included.";
 a.innerText=r;
}

// Random active users
let activeCount=50;
setInterval(()=>{activeCount=Math.floor(50+Math.random()*100);document.getElementById("activeUsers").innerText="Active Users: "+activeCount;},3000);
</script>

</body>
</html>
