<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint</title>

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Arial,sans-serif}
body{background:#f4f6fa;color:#222;padding-bottom:90px}

/* Layout */
.container{max-width:1000px;margin:auto;padding:14px}
section{margin-bottom:28px}

/* Header */
header{text-align:center;padding:24px 10px}
header h1{font-size:26px}
header p{font-size:14px;color:#555;margin-top:6px}

/* Cards */
.cards{
 display:flex;
 gap:14px;
 flex-wrap:wrap;
}
.card{
 background:#fff;
 border-radius:12px;
 padding:16px;
 width:100%;
 box-shadow:0 6px 14px rgba(0,0,0,.08)
}
.card h3{font-size:16px;margin-bottom:6px}
.card p{font-size:14px;color:#555}

/* Buttons */
button{
 width:100%;
 padding:14px;
 border:none;
 border-radius:10px;
 background:#2563eb;
 color:#fff;
 font-size:15px;
 margin-top:8px
}

/* Inputs */
input{
 width:100%;
 padding:12px;
 border-radius:8px;
 border:1px solid #ccc;
 margin-top:6px
}

/* FAQ */
.faq{
 background:#fff;
 padding:14px;
 border-radius:10px;
 margin-bottom:8px
}
.faq h4{font-size:15px}
.faq p{display:none;font-size:14px;color:#555;margin-top:6px}

/* Chatbot */
.bot-qs{
 display:flex;
 flex-wrap:wrap;
 gap:6px;
 margin-bottom:10px
}
.bot-qs button{
 background:#eef2ff;
 color:#222;
 font-size:12px;
 padding:6px 10px;
 border-radius:8px
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
 box-shadow:0 -2px 12px rgba(0,0,0,.15)
}
.bottom-nav a{
 font-size:11px;
 text-align:center;
 color:#222
}

/* WhatsApp */
.whatsapp{
 position:fixed;
 right:16px;
 bottom:90px;
 background:#25D366;
 color:#fff;
 padding:14px;
 border-radius:50%;
 font-size:22px
}

/* Desktop */
@media(min-width:768px){
 .cards{flex-direction:row}
 .card{width:48%}
 header h1{font-size:32px}
}
</style>
</head>

<body>

<div class="container">

<header>
<h1>SkillMint</h1>
<p>Learn Online Skills & Start Earning</p>
</header>

<section id="learn-skills">
<h2>Courses</h2>
<div class="cards">
 <div class="card"><h3>YouTube Earning</h3><p>Channel setup, content, SEO & monetization.</p></div>
 <div class="card"><h3>Freelancing</h3><p>Fiverr & Upwork complete guide.</p></div>
 <div class="card"><h3>Affiliate Marketing</h3><p>Products promote & earn commission.</p></div>
</div>
</section>

<section id="buy">
<h2>Buy Course</h2>
<input value="500 PKR" readonly>
<input value="JazzCash / EasyPaisa / Binance" readonly>
<input type="file">
<button>Submit Proof</button>
</section>

<section id="faq">
<h2>FAQ</h2>
<div class="faq"><h4>Beginners ke liye?</h4><p>Yes, bilkul zero se start.</p></div>
<div class="faq"><h4>Verification time?</h4><p>5 minutes.</p></div>
</section>

<section id="chat">
<h2>SkillMint Bot</h2>

<div class="bot-qs">
<button onclick="ask('skillmint')">What is SkillMint?</button>
<button onclick="ask('buy')">How to buy?</button>
<button onclick="ask('payment')">Payment?</button>
</div>

<input id="q" placeholder="Type question">
<button onclick="reply()">Ask</button>
<p id="a"></p>
</section>

</div>

<a class="whatsapp" href="https://wa.me/923379827882">💬</a>

<div class="bottom-nav">
<a href="#learn-skills">🏠<br>Home</a>
<a href="#buy">🎓<br>Buy</a>
<a href="#faq">❓<br>FAQ</a>
<a href="#chat">🤖<br>Bot</a>
</div>

<script>
const bot=[
 {k:['skillmint'],r:'SkillMint ek beginner platform hai.'},
 {k:['buy'],r:'Payment karo, proof upload karo, access milega.'},
 {k:['payment'],r:'JazzCash, EasyPaisa aur Binance.'}
];
function reply(){
 let t=q.value.toLowerCase(),res='Simple words use karo.';
 bot.forEach(b=>{if(b.k.some(k=>t.includes(k)))res=b.r});
 a.innerText=res;
}
function ask(x){q.value=x;reply();}
document.querySelectorAll('.faq h4').forEach(f=>{
 f.onclick=()=>f.nextElementSibling.style.display=
 f.nextElementSibling.style.display=='block'?'none':'block'
});
</script>

</body>
</html>
