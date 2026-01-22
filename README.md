<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint – Learn & Earn Online</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Inter',sans-serif}
body{background:#f6f7fb;color:#222;padding-bottom:70px}

/* Layout */
.container{max-width:1100px;margin:auto;padding:18px}
section{margin-bottom:35px}

/* Header */
header{text-align:center;padding:30px 10px}
header h1{font-size:32px;font-weight:700}
header p{color:#555;margin-top:8px;font-size:15px}

/* Cards */
.cards{display:flex;gap:16px;flex-wrap:wrap;justify-content:center}
.card{
 background:#fff;
 border-radius:14px;
 padding:20px;
 width:240px;
 box-shadow:0 8px 20px rgba(0,0,0,.08)
}
.card h3{font-size:16px;margin-bottom:6px}
.card p{font-size:14px;color:#555}

/* Section title */
h2{font-size:22px;margin-bottom:15px;text-align:center}

/* Buttons */
.btn{
 width:100%;
 padding:12px;
 border:none;
 border-radius:10px;
 background:#2563eb;
 color:#fff;
 font-weight:600;
 font-size:15px;
 cursor:pointer
}
.btn.green{background:#16a34a}

/* Reviews */
.review{
 background:#fff;
 border-radius:12px;
 padding:16px;
 box-shadow:0 6px 16px rgba(0,0,0,.08);
 margin-bottom:12px
}
.review p{font-size:14px;color:#444}
.review span{display:block;margin-top:6px;font-size:13px;color:#2563eb}

/* FAQ */
.faq{background:#fff;border-radius:12px;padding:14px;margin-bottom:8px;box-shadow:0 4px 10px rgba(0,0,0,.06)}
.faq h4{font-size:15px;cursor:pointer}
.faq p{display:none;font-size:14px;color:#555;margin-top:6px}

/* Inputs */
input,button{font-size:14px}
input[type=file],input[type=text]{
 width:100%;
 padding:10px;
 border-radius:8px;
 border:1px solid #ccc;
 margin-bottom:8px
}

/* Chatbot */
.bot-q{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:10px}
.bot-q button{
 background:#eef2ff;
 border:none;
 padding:6px 10px;
 border-radius:8px;
 font-size:12px;
 cursor:pointer
}

/* Bottom Nav */
.bottom-nav{
 position:fixed;
 bottom:0;left:0;
 width:100%;
 background:#fff;
 display:flex;
 justify-content:space-around;
 padding:10px 0;
 box-shadow:0 -3px 12px rgba(0,0,0,.12)
}
.bottom-nav a{text-align:center;font-size:11px;color:#333}

/* WhatsApp */
.whatsapp{
 position:fixed;
 bottom:90px;
 right:18px;
 background:#25D366;
 color:#fff;
 padding:14px;
 border-radius:50%;
 font-size:22px;
 box-shadow:0 6px 20px rgba(0,0,0,.25)
}

/* Responsive */
@media(max-width:600px){
 header h1{font-size:26px}
 .card{width:100%}
}
</style>
</head>

<body>

<div class="container">

<header>
<h1>SkillMint</h1>
<p>Beginner-friendly platform to learn online skills & start earning</p>
</header>

<section id="learn-skills">
<h2>What You Will Learn</h2>
<div class="cards">
 <div class="card"><h3>YouTube Earning</h3><p>Channel setup, content, SEO, monetization step-by-step.</p></div>
 <div class="card"><h3>Freelancing</h3><p>Fiverr & Upwork setup, gigs, clients & earnings.</p></div>
 <div class="card"><h3>Affiliate Marketing</h3><p>Products promote karna aur commission earn karna.</p></div>
 <div class="card"><h3>Social Media Growth</h3><p>Instagram & Facebook organic growth strategies.</p></div>
</div>
</section>

<section>
<h2>Student Reviews</h2>
<div class="review"><p>“Mujhe YouTube bilkul zero se samajh aya.”</p><span>— Ali</span></div>
<div class="review"><p>“Freelancing ka complete roadmap mil gaya.”</p><span>— Sara</span></div>
</section>

<section id="buy-course">
<h2>Buy SkillMint Course</h2>

<p><b>Price</b></p>
<input type="text" id="price" readonly>

<p><b>Deposit Number</b></p>
<input type="text" id="number" readonly>

<button class="btn" onclick="pay('JazzCash')">JazzCash</button>
<button class="btn" onclick="pay('EasyPaisa')">EasyPaisa</button>
<button class="btn" onclick="pay('Binance')">Binance</button>

<p><b>Upload Payment Proof</b></p>
<input type="file" id="proof">

<p id="timer"></p>
<button class="btn green" id="open" disabled>Open Course</button>
</section>

<section id="faq">
<h2>FAQ</h2>
<div class="faq"><h4>Verification time?</h4><p>Normally 5 minutes.</p></div>
<div class="faq"><h4>Beginners ke liye?</h4><p>Yes, bilkul zero level se.</p></div>
</section>

<section id="chatbot">
<h2>SkillMint Bot 🤖</h2>

<div class="bot-q">
<button onclick="ask('skillmint')">What is SkillMint?</button>
<button onclick="ask('buy')">How to buy?</button>
<button onclick="ask('payment')">Payment methods?</button>
<button onclick="ask('beginner')">For beginners?</button>
</div>

<input type="text" id="q" placeholder="Type your question">
<button class="btn" onclick="reply()">Ask</button>
<p id="ans"></p>
</section>

</div>

<a class="whatsapp" href="https://wa.me/923379827882" target="_blank">💬</a>

<div class="bottom-nav">
<a href="#learn-skills">🏠<br>Home</a>
<a href="#buy-course">🎓<br>Course</a>
<a href="#faq">❓<br>FAQ</a>
<a href="#chatbot">🤖<br>Bot</a>
</div>

<script>
function pay(m){
 let p=500,n='';
 if(m=='JazzCash')n='03705519562';
 if(m=='EasyPaisa')n='03379827882';
 if(m=='Binance')n='0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F';
 price.value=p+' PKR'; number.value=n;
 navigator.clipboard.writeText(n);
}

proof.onchange=()=>{
 let t=300;
 let i=setInterval(()=>{
  timer.innerText='Access in '+t+'s';
  t--;
  if(t<0){clearInterval(i);open.disabled=false}
 },1000);
};

open.onclick=()=>window.open('https://gtv140.github.io/SkillMint-complete-course-/','_blank');

const bot=[
 {k:['skillmint'],r:'SkillMint ek beginner platform hai jahan online earning skills sikhai jati hain.'},
 {k:['buy'],r:'Payment method select karo, proof upload karo, 5 min baad access milega.'},
 {k:['payment'],r:'JazzCash, EasyPaisa aur Binance available hain.'},
 {k:['beginner'],r:'Yes, bilkul beginners ke liye hai.'}
];

function reply(){
 let qv=q.value.toLowerCase();
 let r='Please simple words use karein.';
 bot.forEach(b=>{if(b.k.some(k=>qv.includes(k)))r=b.r});
 ans.innerText=r;
}
function ask(t){q.value=t;reply();}
document.querySelectorAll('.faq h4').forEach(f=>{
 f.onclick=()=>f.nextElementSibling.style.display=
 f.nextElementSibling.style.display=='block'?'none':'block'
});
</script>

</body>
</html>
