<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>SkillMint</title>

<style>
body{
 margin:0;
 font-family:system-ui,Arial;
 background:#f6f7fb;
 color:#111;
 padding-bottom:80px;
}

/* Header */
.header{
 background:#2563eb;
 color:#fff;
 padding:20px 14px;
 text-align:center;
}
.header h1{margin:0;font-size:22px}
.header p{margin-top:6px;font-size:13px;opacity:.9}

/* Section */
.section{
 padding:16px 14px;
}
.section h2{
 font-size:18px;
 margin-bottom:12px;
}

/* Card */
.card{
 background:#fff;
 border-radius:14px;
 padding:14px;
 margin-bottom:12px;
 box-shadow:0 6px 16px rgba(0,0,0,.08);
}
.card h3{margin:0;font-size:15px}
.card p{margin-top:6px;font-size:13px;color:#555}

/* Button */
.btn{
 width:100%;
 padding:14px;
 border:none;
 border-radius:14px;
 font-size:15px;
 background:#2563eb;
 color:#fff;
 margin-top:10px;
}
.btn.green{background:#16a34a}

/* Input */
input{
 width:100%;
 padding:13px;
 border-radius:12px;
 border:1px solid #ccc;
 font-size:14px;
 margin-top:6px;
}

/* Bottom Nav */
.nav{
 position:fixed;
 bottom:0;
 left:0;
 width:100%;
 background:#fff;
 display:flex;
 justify-content:space-around;
 padding:8px 0;
 box-shadow:0 -4px 12px rgba(0,0,0,.15);
}
.nav a{
 font-size:11px;
 text-align:center;
 color:#333;
 text-decoration:none;
}

/* Chat bubble */
.chat{
 position:fixed;
 right:14px;
 bottom:90px;
 background:#22c55e;
 color:#fff;
 padding:14px;
 border-radius:50%;
 font-size:20px;
}
</style>
</head>

<body>

<div class="header">
<h1>SkillMint</h1>
<p>Learn skills • Earn online • Beginner friendly</p>
</div>

<div class="section" id="home">
<h2>Skills You Will Learn</h2>

<div class="card">
<h3>YouTube Earning</h3>
<p>Zero se channel, content, SEO aur earning.</p>
</div>

<div class="card">
<h3>Freelancing</h3>
<p>Fiverr & Upwork complete roadmap.</p>
</div>

<div class="card">
<h3>Affiliate Marketing</h3>
<p>Products promote kar ke commission.</p>
</div>

<div class="card">
<h3>Social Media Growth</h3>
<p>Instagram & Facebook organic growth.</p>
</div>
</div>

<div class="section" id="course">
<h2>Buy Course</h2>

<label>Price</label>
<input id="price" readonly placeholder="Select payment">

<label>Deposit Number</label>
<input id="num" readonly placeholder="Auto fill">

<button class="btn" onclick="pay('jazz')">JazzCash</button>
<button class="btn" onclick="pay('easy')">EasyPaisa</button>
<button class="btn" onclick="pay('binance')">Binance</button>

<label>Payment Proof</label>
<input type="file" id="proof">

<p id="status" style="font-size:13px;margin-top:6px"></p>
<button class="btn green" id="open" disabled>Open Course</button>
</div>

<div class="section" id="bot">
<h2>SkillMint Bot 🤖</h2>
<input id="q" placeholder="Ask anything">
<button class="btn" onclick="bot()">Ask</button>
<p id="a" style="margin-top:8px;font-size:14px"></p>
</div>

<a class="chat" href="https://wa.me/923379827882">💬</a>

<div class="nav">
<a href="#home">🏠<br>Home</a>
<a href="#course">🎓<br>Course</a>
<a href="#bot">🤖<br>Bot</a>
</div>

<script>
function pay(x){
 price.value="500 PKR";
 if(x=="jazz") num.value="03705519562";
 if(x=="easy") num.value="03379827882";
 if(x=="binance") num.value="0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F";
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

open.onclick=()=>{
 window.open("https://gtv140.github.io/SkillMint-complete-course-/","_blank");
}

function bot(){
 let x=q.value.toLowerCase();
 let r="Simple sawal pocho.";
 if(x.includes("price")) r="Course price 500 PKR hai.";
 if(x.includes("payment")) r="JazzCash, EasyPaisa, Binance available.";
 if(x.includes("beginner")) r="Yes, beginners ke liye perfect.";
 a.innerText=r;
}
</script>

</body>
</html>
