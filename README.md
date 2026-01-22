<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint Pro</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
body{margin:0;font-family:Arial,sans-serif;background:#f3f6fb;color:#111;padding-bottom:140px;overflow-x:hidden;}
.header{background:linear-gradient(90deg,#2563eb,#22c55e);color:#fff;padding:25px;text-align:center;position:sticky;top:0;z-index:99;box-shadow:0 4px 12px rgba(0,0,0,.1);}
.header h1{font-size:26px;margin:0;text-shadow:1px 1px 2px rgba(0,0,0,.3);}
.header p{margin-top:6px;font-size:15px;opacity:.95;}
.section{padding:18px;}
.section h2{font-size:20px;margin-bottom:14px;text-align:center;}
.cards{display:flex;flex-direction:column;gap:14px;}
.card{background:#fff;border-radius:16px;padding:18px;box-shadow:0 6px 18px rgba(0,0,0,.08);transition:all 0.3s;cursor:pointer;}
.card:hover{transform:translateY(-6px);box-shadow:0 10px 22px rgba(0,0,0,.12);}
.card img{width:100%;border-radius:12px;margin-bottom:10px;}
.card h3{margin:0;font-size:17px;color:#2563eb;}
.card p{margin-top:6px;font-size:14px;color:#555;}
.badge{display:inline-block;background:#16a34a;color:#fff;padding:2px 8px;border-radius:10px;font-size:11px;margin-top:6px;}
.btn{width:100%;padding:14px;border:none;border-radius:14px;font-size:15px;background:#2563eb;color:#fff;margin-top:10px;cursor:pointer;transition:0.3s;}
.btn:hover{background:#1e40af;}
.btn.green{background:#16a34a;}
input{width:100%;padding:12px;border-radius:10px;border:1px solid #ccc;margin-top:6px;font-size:14px;}
.nav{position:fixed;bottom:0;left:0;width:100%;background:#fff;display:flex;justify-content:space-around;padding:12px 0;box-shadow:0 -4px 14px rgba(0,0,0,.15);}
.nav a{text-align:center;font-size:11px;color:#333;text-decoration:none;}
.chat{position:fixed;right:16px;bottom:100px;background:#22c55e;color:#fff;padding:14px;border-radius:50%;font-size:20px;text-decoration:none;display:flex;align-items:center;justify-content:center;box-shadow:0 4px 12px rgba(0,0,0,.2);}
.slider{display:flex;overflow-x:auto;gap:10px;padding-bottom:10px;scroll-behavior:smooth;}
.review{min-width:220px;background:#fff;padding:12px;border-radius:14px;box-shadow:0 4px 14px rgba(0,0,0,.08);flex-shrink:0;transition:0.3s;}
.review img{width:40px;height:40px;border-radius:50%;margin-right:8px;vertical-align:middle;}
.review p{font-size:14px;margin:0;display:inline;}
.review span{font-size:13px;color:#2563eb;margin-left:6px;}
.faq{background:#fff;border-radius:14px;padding:14px;margin-bottom:10px;box-shadow:0 4px 12px rgba(0,0,0,.06);}
.faq h4{font-size:15px;cursor:pointer;margin:0;}
.faq p{display:none;font-size:14px;color:#555;margin-top:6px;}
.active-users{font-size:12px;color:#16a34a;text-align:center;margin-top:6px;font-weight:bold;}
.progress-bar{height:8px;background:#d1d5db;border-radius:6px;margin-top:6px;}
.progress{height:8px;background:#2563eb;width:0%;border-radius:6px;transition:width 0.5s;}
.icons{display:flex;justify-content:space-around;flex-wrap:wrap;gap:12px;margin-bottom:14px;}
.icon-card{background:#fff;padding:12px;border-radius:14px;flex:1 0 22%;text-align:center;box-shadow:0 4px 12px rgba(0,0,0,.08);cursor:pointer;transition:0.3s;display:none;}
.icon-card:hover{transform:translateY(-4px);box-shadow:0 8px 20px rgba(0,0,0,.12);}
.icon-card i{font-size:28px;color:#2563eb;margin-bottom:6px;display:block;}
.more-btn{background:#2563eb;color:#fff;padding:10px 14px;border-radius:12px;cursor:pointer;text-align:center;margin-top:10px;}
@media(min-width:768px){.cards{flex-direction:row;flex-wrap:wrap}.card{width:48%;}}
</style>
</head>
<body>

<div class="header">
<h1>SkillMint Pro</h1>
<p>Learn skills, earn online & build your future. Trusted by beginners and professionals alike.</p>
<img src="https://picsum.photos/seed/banner/1200/400" alt="Banner" style="width:100%;border-radius:12px;margin-top:10px;">
</div>

<div class="section" id="home">
<h2>What SkillMint Offers</h2>
<p style="text-align:center;max-width:600px;margin:0 auto 12px auto;">
SkillMint helps beginners learn online skills step-by-step, gain confidence, and earn from YouTube, freelancing, affiliate marketing, and social media. All courses are beginner-friendly, practical, and trusted by thousands of students.
</p>

<div class="slider" id="reviewSlider"></div>
<p class="active-users" id="activeUsers">Active Users: 0</p>

<div class="icons">
 <div class="icon-card" id="icon1" onclick="scrollToSection('courses')"><i class="fas fa-video"></i> YouTube</div>
 <div class="icon-card" id="icon2" onclick="scrollToSection('courses')"><i class="fas fa-laptop-code"></i> Freelancing</div>
 <div class="icon-card" id="icon3" onclick="scrollToSection('courses')"><i class="fas fa-dollar-sign"></i> Affiliate</div>
 <div class="icon-card" id="icon4" onclick="scrollToSection('courses')"><i class="fas fa-users"></i> Social Media</div>
 <div class="more-btn" id="showIconsBtn">More</div>
</div>
</div>

<div class="section" id="courses">
<h2>Courses You Will Learn</h2>
<div class="cards">
 <div class="card"><img src="https://picsum.photos/seed/course1/400/250" alt="YouTube"><h3>YouTube Earning</h3><p>Zero se channel setup, content, SEO aur monetization step by step.</p><span class="badge">Beginner Friendly</span></div>
 <div class="card"><img src="https://picsum.photos/seed/course2/400/250" alt="Freelancing"><h3>Freelancing</h3><p>Fiverr & Upwork complete roadmap, gigs, clients & earnings.</p><span class="badge">Most Popular</span></div>
 <div class="card"><img src="https://picsum.photos/seed/course3/400/250" alt="Affiliate"><h3>Affiliate Marketing</h3><p>Products promote kar ke commission earn karna.</p><span class="badge">High ROI</span></div>
 <div class="card"><img src="https://picsum.photos/seed/course4/400/250" alt="Social Media"><h3>Social Media Growth</h3><p>Instagram & Facebook organic growth strategies step by step.</p><span class="badge">Trending</span></div>
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
<div class="progress-bar"><div class="progress" id="progress"></div></div>
<p id="status" style="font-size:13px;margin-top:6px"></p>
<button class="btn green" id="open" disabled>Open Course</button>
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
<div style="margin-top:6px;">
<button class="btn" onclick="botQuick('price')">Price</button>
<button class="btn" onclick="botQuick('payment')">Payment</button>
<button class="btn" onclick="botQuick('youtube')">YouTube</button>
<button class="btn" onclick="botQuick('freelance')">Freelancing</button>
</div>
<button class="btn" onclick="bot()">Ask</button>
<p id="a" style="margin-top:8px;font-size:14px"></p>
</div>

<a class="chat" href="https://wa.me/923379827882" target="_blank">💬</a>

<div class="nav">
<a href="#home">🏠<br>Home</a>
<a href="#courses">🎓<br>Courses</a>
<a href="#faq">❓<br>FAQ</a>
<a href="#bot">🤖<br>Bot</a>
<a href="https://www.facebook.com/profile.php?id=100084218946114" target="_blank">📘<br>FB</a>
<a href="https://www.instagram.com/mr_nazim073?igsh=MXd4d2hmcWNvNjVsdQ==" target="_blank">📸<br>IG</a>
<a href="mailto:Rock.earn92@gmail.com">✉️<br>Email</a>
</div>

<script>
// Scroll to section
function scrollToSection(id){document.getElementById(id).scrollIntoView({behavior:'smooth'});}

// Payment
function pay(m){
 let priceValue="500 PKR";
 price.value=priceValue;
 if(m==="jazz") num.value="03705519562";
 if(m==="easy") num.value="03379827882";
 if(m==="binance") num.value="0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F";
 navigator.clipboard.writeText(num.value);
 alert("Deposit number copied ✅");
 localStorage.setItem("lastPaymentMethod", m);
 localStorage.setItem("lastDepositNumber", num.value);
 localStorage.setItem("lastPrice", price.value);
}

// Proof verification countdown with localStorage
let totalTime = 300;
let savedTime = localStorage.getItem("timerLeft");
if(savedTime){ totalTime = parseInt(savedTime); }

let timerInterval;
function startTimer(){
 timerInterval = setInterval(()=>{
  if(totalTime <= 0){
   clearInterval(timerInterval);
   document.getElementById("status").innerText = "Access Granted ✔";
   document.getElementById("open").disabled = false;
   document.getElementById("progress").style.width = "100%";
   localStorage.removeItem("timerLeft");
  } else {
   document.getElementById("status").innerText = "Verifying... " + totalTime + "s";
   document.getElementById("progress").style.width = ((300 - totalTime)/300*100) + "%";
   totalTime--;
   localStorage.setItem("timerLeft", totalTime);
  }
 },1000);
}

proof.onchange=()=>{
 startTimer();
 localStorage.setItem("proofUploaded","true");
}

// Open Course
open.onclick=()=>{window.open("https://gtv140.github.io/SkillMint-complete-course-/","_blank");}

// FAQ toggle
document.querySelectorAll(".faq h4").forEach(f=>{f.onclick=()=>{f.nextElementSibling.style.display=f.nextElementSibling.style.display==="block"?"none":"block";}})

// Bot
function bot(){let x=q.value.toLowerCase(),r="Please ask a simple question.";
if(x.includes("price")) r="Course price: 500 PKR.";
if(x.includes("payment")) r="Payment methods: JazzCash, EasyPaisa, Binance.";
if(x.includes("beginner")) r="Yes, course is beginner friendly.";
if(x.includes("youtube")) r="You will learn YouTube earning step by step.";
if(x.includes("freelance")) r="Complete Freelancing roadmap included.";
a.innerText=r;}
function botQuick(qs){q.value=qs;bot();}

// Active Users
let activeCount=50;
setInterval(()=>{
 activeCount=Math.floor(50+Math.random()*100);
 document.getElementById("activeUsers").innerText="Active Users: "+activeCount;
 localStorage.setItem("activeUsers", activeCount);
},3000);

// Reviews
const reviews=[
{avatar:"https://picsum.photos/seed/avatar1/50/50",text:"Amazing course, YouTube setup clear." ,name:"Ali"},
{avatar:"https://picsum.photos/seed/avatar2/50/50",text:"Freelancing roadmap is perfect.",name:"Sara"},
{avatar:"https://picsum.photos/seed/avatar3/50/50",text:"Affiliate marketing helped me earn.",name:"Ahmed"},
{avatar:"https://picsum.photos/seed/avatar4/50/50",text:"Social Media strategies are excellent.",name:"Hina"},
{avatar:"https://picsum.photos/seed/avatar5/50/50",text:"I learned everything step by step.",name:"Bilal"},
{avatar:"https://picsum.photos/seed/avatar6/50/50",text:"Loved the bot feature.",name:"Zara"},
{avatar:"https://picsum.photos/seed/avatar7/50/50",text:"Payment verification is smooth.",name:"Tariq"},
{avatar:"https://picsum.photos/seed/avatar8/50/50",text:"Great beginner friendly instructions.",name:"Amna"},
{avatar:"https://picsum.photos/seed/avatar9/50/50",text:"I can now earn online.",name:"Fahad"},
{avatar:"https://picsum.photos/seed/avatar10/50/50",text:"SkillMint helped me a lot.",name:"Sana"}
];
const slider=document.getElementById("reviewSlider");
let reviewIndex=0;
function showReviews(){
 slider.innerHTML="";
 for(let i=0;i<3;i++){
  const r=reviews[(reviewIndex+i)%reviews.length];
  slider.innerHTML+=`<div class="review"><img src="${r.avatar}" alt="Avatar"><p>"${r.text}"</p><span>— ${r.name}</span></div>`;
 }
 reviewIndex=(reviewIndex+1)%reviews.length;
}
showReviews();setInterval(showReviews,5000);

// Icons logic: initially hidden, show on More click
const iconCards=document.querySelectorAll(".icon-card");
const showBtn=document.getElementById("showIconsBtn");
showBtn.onclick=()=>{
 iconCards.forEach(c=>c.style.display="block");
 showBtn.style.display="none";
};
</script>

</body>
</html>
