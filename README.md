<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<style>
body { margin:0; font-family:'Roboto', sans-serif; background:#0a0a0a; color:white;}
.container { max-width:1000px; margin:auto; padding:20px; border-radius:12px; background:#111; }
header { text-align:center; margin-bottom:25px; }
header h1 { font-size:36px; color:#00ffff; margin-bottom:5px; }
header p { color:#ccc; font-size:16px; }
.section { background:#1a1a1a; border-radius:10px; padding:25px; margin-bottom:30px; }
h2 { color:#ff00ff; margin-bottom:15px; }
.card-container { display:flex; flex-wrap:wrap; justify-content:center; gap:15px; margin-top:20px; }
.card { background:#111; border-radius:10px; padding:20px; width:220px; box-shadow:0 0 8px rgba(0,255,255,0.5); text-align:center; transition:0.3s; }
.card h3 { color:#ff00ff; margin-bottom:10px; }
.card p { font-size:14px; }
.card img { width:50px; height:50px; margin-bottom:10px; }
.payBtn { padding:10px 20px; margin:5px; border:none; border-radius:8px; color:white; cursor:pointer; font-weight:bold; background:#222; box-shadow:0 0 5px rgba(0,255,255,0.3); transition:0.3s; }
.payBtn:hover { transform:scale(1.05); box-shadow:0 0 10px rgba(0,255,255,0.5); }
#openCourse { padding:12px 35px; font-size:16px; border:none; border-radius:10px; background:#ff00ff; color:white; cursor:pointer; box-shadow:0 0 5px rgba(255,0,255,0.4); transition:0.3s; }
#openCourse:hover { transform:scale(1.03); box-shadow:0 0 10px rgba(255,0,255,0.6); }
input[type=file], input[type=text] { padding:10px; width:80%; border-radius:6px; border:1px solid #555; margin-bottom:10px; text-align:center; background:#222; color:white; }
#copyMsg { color:#00ff00; display:none; font-weight:bold; margin-left:10px; }
#timer { font-size:16px; color:#ffcc00; margin-top:10px; }
footer { background:#0d47a1; color:white; padding:15px 0; text-align:center; border-radius:8px; margin-top:20px; }
@media(max-width:800px){ .card-container{ flex-direction:column; align-items:center;} input[type=file], input[type=text]{width:90%;} }
.tooltip { position:relative; display:inline-block; cursor:pointer; }
.tooltip .tooltiptext { visibility:hidden; width:200px; background:#333; color:#fff; text-align:center; border-radius:6px; padding:5px; position:absolute; z-index:1; bottom:125%; left:50%; transform:translateX(-50%); opacity:0; transition:opacity 0.3s; font-size:13px; }
.tooltip:hover .tooltiptext { visibility:visible; opacity:1; }
</style>
</head>
<body>
<div class="container">

<header>
<h1>SkillMint</h1>
<p>Learn, Earn & Grow – Step by Step for Beginners</p>
</header>

<div class="section">
<h2>🎓 Buy SkillMint Complete Course</h2>
<p><strong>Price:</strong> <input type="text" id="priceDisplay" readonly></p>
<p><strong>Deposit Number:</strong> <input type="text" id="depositNumber" readonly> <span id="copyMsg">Copied!</span></p>

<h3>Select Payment Method:</h3>
<button class="payBtn" onclick="setMethod('JazzCash')">JazzCash</button>
<button class="payBtn" onclick="setMethod('EasyPaisa')">EasyPaisa</button>
<button class="payBtn" onclick="setMethod('Binance')">Binance</button>

<h3>Upload Payment Proof <span class="tooltip">ℹ️
  <span class="tooltiptext">Select screenshot of your payment; timer will start automatically.</span>
</span></h3>
<input type="file" id="proof" accept="image/*">

<p style="font-size:14px;">Send proof via: 
<a href="mailto:example@example.com" style="color:#ff00ff;">Email</a> | 
<a href="https://wa.me/03379827882" target="_blank" style="color:#00ff00;">WhatsApp</a> | 
<a href="https://facebook.com/yourprofile" target="_blank" style="color:#1877f2;">Facebook</a> | 
<a href="https://instagram.com/yourhandle" target="_blank" style="color:#e1306c;">Instagram</a>
</p>

<div id="timer"></div>
<button id="openCourse" disabled>Open Course</button>
</div>

<div class="section">
<h2>How SkillMint Helps You</h2>
<div class="card-container">
<div class="card">
<img src="https://cdn-icons-png.flaticon.com/512/1384/1384060.png" alt="YouTube">
<h3>Learn Skills</h3>
<p>Master YouTube, Freelancing, Affiliate Marketing & Social Media from scratch.</p>
</div>
<div class="card">
<img src="https://cdn-icons-png.flaticon.com/512/1828/1828843.png" alt="Step">
<h3>Step by Step</h3>
<p>Beginner-friendly tutorials with practical examples & exercises.</p>
</div>
<div class="card">
<img src="https://cdn-icons-png.flaticon.com/512/1170/1170576.png" alt="Money">
<h3>Earn Online</h3>
<p>Apply your skills to start freelancing, monetize YouTube & affiliate marketing.</p>
</div>
<div class="card">
<img src="https://cdn-icons-png.flaticon.com/512/565/565313.png" alt="Support">
<h3>Guidance & Support</h3>
<p>Clear instructions, proof verification, and real-time course access.</p>
</div>
</div>
</div>

<footer>
<p>Contact us: Email | WhatsApp | Facebook | Instagram</p>
<p>© 2026 SkillMint</p>
</footer>

<script>
// Payment auto-fill & copy
let openBtn = document.getElementById('openCourse');
let timerDiv = document.getElementById('timer');
let priceDisplay = document.getElementById('priceDisplay');
let depositField = document.getElementById('depositNumber');
let proofInput = document.getElementById('proof');
let copyMsg = document.getElementById('copyMsg');

function setMethod(method){
    let price = 500;
    let depositNum="";
    if(method==='JazzCash') depositNum="03705519562";
    else if(method==='EasyPaisa') depositNum="03379827882";
    else if(method==='Binance') depositNum="0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F";

    priceDisplay.value = price + " PKR";
    depositField.value = depositNum;

    // Copy to clipboard
    navigator.clipboard.writeText(depositNum).then(()=>{
        copyMsg.style.display="inline";
        setTimeout(()=>{ copyMsg.style.display="none"; }, 2000);
    });

    localStorage.setItem('paymentMethod', method);
    localStorage.setItem('depositNum', depositNum);
    localStorage.setItem('price', price);
}

// Countdown timer
let savedTime = localStorage.getItem('timer') || 0;
let savedProof = localStorage.getItem('proofUploaded') === 'true';
if(savedProof && savedTime>0) startCountdown(parseInt(savedTime));

proofInput.addEventListener('change', function(){
    if(this.files.length>0){
        localStorage.setItem('proofUploaded','true');
        startCountdown(300);
    }
});

function startCountdown(duration){
    let time = duration;
    localStorage.setItem('timer', time);
    let countdown = setInterval(()=>{
        let minutes = Math.floor(time/60);
        let seconds = time%60;
        timerDiv.innerText=`Access in: ${minutes.toString().padStart(2,'0')}:${seconds.toString().padStart(2,'0')}`;
        time--;
        localStorage.setItem('timer', time);
        if(time<0){
            clearInterval(countdown);
            timerDiv.innerText="Payment verified! You can now access the course.";
            openBtn.disabled=false;
        }
    },1000);
}

openBtn.onclick = ()=>{
    window.open('https://gtv140.github.io/SkillMint-complete-course-/','_blank');
};
</script>
</body>
</html>
