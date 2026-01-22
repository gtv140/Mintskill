<html lang="en">
<head>
<meta charset="UTF-8">
<title>SkillMint – Learn Skills & Earn Online</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:'Roboto',sans-serif;background:#f4f6f9;color:#222;}
header{background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);color:#fff;padding:60px 20px;text-align:center;}
header h1{font-size:48px;margin-bottom:10px;}
header p{font-size:20px;margin-bottom:20px;}
header .cta-btn{padding:12px 25px;background:#25D366;color:#fff;border-radius:6px;font-weight:bold;}
nav{background:#111;padding:12px;text-align:center;}
nav a{color:#fff;margin:0 10px;text-decoration:none;font-weight:bold;}
nav a:hover{color:#25D366;}
section{background:#fff;margin:25px auto;padding:25px;border-radius:12px;max-width:1000px;box-shadow:0 6px 15px rgba(0,0,0,0.08);}
h2{text-align:center;margin-bottom:15px;}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px;}
.card{background:#f9fafb;padding:20px;border-radius:10px;border:1px solid #e5e7eb;transition:transform 0.3s;}
.card:hover{transform:translateY(-5px);box-shadow:0 10px 20px rgba(0,0,0,0.2);}
.btn{display:inline-block;margin-top:10px;padding:10px 18px;background:#25D366;color:#fff;border-radius:6px;font-weight:bold;transition:0.3s;}
.btn:hover{background:#128C7E;}
input,textarea{width:100%;padding:12px;margin:8px 0;border-radius:6px;border:1px solid #ccc;}
input[type=file]{padding:5px;}
#timerDisplay{font-weight:bold;font-size:18px;margin-top:10px;text-align:center;color:#d9534f;}
#downloadBtn{background:#007bff;display:block;margin:15px auto;text-align:center;pointer-events:none;opacity:0.5;}
#downloadBtn.active{pointer-events:auto;opacity:1;}
iframe{width:100%;height:500px;border:1px solid #ccc;border-radius:8px;margin-top:15px;}
</style>
</head>

<body>

<header>
<h1>SkillMint</h1>
<p>Learn Skills & Build Your Online Income</p>
<a href="#payments" class="cta-btn">Start Earning</a>
</header>

<nav>
<a href="#about">About</a>
<a href="#earn">Earn</a>
<a href="#payments">Payments</a>
<a href="#course">Course</a>
</nav>

<section id="about">
<h2>About SkillMint</h2>
<p>SkillMint helps beginners learn digital skills & start earning online through AdSense, affiliate marketing, freelancing & digital services.</p>
</section>

<section id="earn">
<h2>💰 How You Can Earn</h2>
<div class="grid">
<div class="card">
<h3>Google AdSense</h3>
<p>Monetize your content & earn passive income.</p>
<a class="btn" href="#">Learn More</a>
</div>
<div class="card">
<h3>Affiliate Marketing</h3>
<p>Promote products & earn commission.</p>
<a class="btn" href="#">Visit Offer</a>
</div>
<div class="card">
<h3>Digital Services</h3>
<p>Offer services like website setup, YouTube SEO, logos, thumbnails.</p>
<a class="btn" href="https://wa.me/03705519562">Contact on WhatsApp</a>
</div>
</div>
</section>

<section id="payments">
<h2>💳 Payment Options</h2>
<div class="grid">

<div class="card">
<h3>Binance / Crypto</h3>
<p>Send payment directly to our wallet:</p>
<p><strong>0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F</strong></p>
<button class="btn" onclick="payBinance()">Pay with Binance</button>
</div>

<div class="card">
<h3>JazzCash</h3>
<p>Send payment via JazzCash: <strong>03705519562</strong></p>
<button class="btn" onclick="payJazzCash()">Pay with JazzCash</button>
</div>

<div class="card">
<h3>EasyPaisa</h3>
<p>Send payment via EasyPaisa: <strong>03379827882</strong></p>
<button class="btn" onclick="payEasyPaisa()">Pay with EasyPaisa</button>
</div>

<div class="card">
<h3>Instagram</h3>
<a class="btn" href="https://instagram.com/mr_nazim073" target="_blank">Send DM</a>
</div>

<div class="card">
<h3>Facebook</h3>
<a class="btn" href="https://www.facebook.com/profile.php?id=100084218946114" target="_blank">Send Message</a>
</div>

<div class="card">
<h3>Email Confirmation</h3>
<a class="btn" href="mailto:rock.earn92@gmail.com">Send Email</a>
</div>

</div>
</section>

<section id="course">
<h2>📚 Course Access</h2>
<p>Upload your payment screenshot below. Timer will start once you upload. After timer ends, you can download the course.</p>

<input type="file" id="paymentProof" accept="image/*">
<p id="timerDisplay">Timer: 00:00</p>
<a href="SkillMint_Course.pdf" id="downloadBtn" download>Download Course</a>

<h3>Preview of Course (PDF)</h3>
<iframe src="SkillMint_Course.pdf"></iframe>
</section>

<script>
// Payment buttons auto-copy + app open
function payJazzCash(){
  navigator.clipboard.writeText("03705519562");
  alert("JazzCash number copied. Open app and paste.");
  window.location.href = "intent://#Intent;scheme=jazzcash;package=com.techlogix.mobilinkcustomer;end";
}
function payEasyPaisa(){
  navigator.clipboard.writeText("03379827882");
  alert("EasyPaisa number copied. Open app and paste.");
  window.location.href = "intent://#Intent;scheme=easypaisa;package=pk.com.telenor.phoenix;end";
}
function payBinance(){
  navigator.clipboard.writeText("0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F");
  alert("Wallet address copied. Open Binance app and paste.");
  window.location.href = "https://www.binance.com/en";
}

// Countdown Timer with Local Storage
let timerDuration = 5*60; // 5 min
let timerDisplay = document.getElementById('timerDisplay');
let downloadBtn = document.getElementById('downloadBtn');

function startTimer(duration){
    let timer = duration;
    localStorage.setItem('timerEnd', Date.now() + timer*1000);
    let interval = setInterval(function(){
        let remaining = Math.floor((localStorage.getItem('timerEnd') - Date.now())/1000);
        if(remaining <= 0){
            clearInterval(interval);
            timerDisplay.textContent = "✅ Timer Complete! Download Now.";
            downloadBtn.classList.add('active');
        } else {
            let min = Math.floor(remaining/60);
            let sec = remaining%60;
            timerDisplay.textContent = `Timer: ${min.toString().padStart(2,'0')}:${sec.toString().padStart(2,'0')}`;
        }
    },1000);
}

// Check if timer already running
if(localStorage.getItem('timerEnd')){
    let remaining = Math.floor((localStorage.getItem('timerEnd') - Date.now())/1000);
    if(remaining>0){
        startTimer(remaining);
    } else {
        downloadBtn.classList.add('active');
        timerDisplay.textContent = "✅ Timer Complete! Download Now.";
    }
}

// Start timer on file upload
document.getElementById('paymentProof').addEventListener('change', function(){
    startTimer(timerDuration);
});
</script>

</body>
</html>
