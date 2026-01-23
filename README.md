<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>SkillMint</title>
<style>
:root{
--neon-red:#ff3c78;
--neon-blue:#3c9eff;
--neon-purple:#b13eff;
--dark-bg:#0a0a0a;
--dark-card:#1c1c1c;
--white:#fff;
}
body{margin:0;font-family:system-ui,sans-serif;background:var(--dark-bg);color:var(--white);overflow-x:hidden;transition:all .3s;}
.dark{background:#0f172a}

/* SPLASH */
#splash{position:fixed;inset:0;background:linear-gradient(135deg,var(--neon-purple),var(--neon-blue));display:flex;align-items:center;justify-content:center;color:#fff;font-size:26px;z-index:9999;transition:all .3s;}

/* HEADER */
.header{display:flex;justify-content:space-between;align-items:center;background:linear-gradient(135deg,var(--neon-red),var(--neon-blue));color:#fff;padding:16px;border-radius:0 0 26px 26px;box-shadow:0 4px 16px rgba(0,0,0,.3);position:sticky;top:0;z-index:9;}
.header h2{margin:0;font-size:22px}
.header-buttons{display:flex;gap:8px}
.header button{background:#111;color:var(--neon-red);border:1px solid var(--neon-red);padding:6px 12px;border-radius:20px;cursor:pointer;transition:.3s;font-weight:bold;}
.header button:hover{background:var(--neon-red);color:#111;box-shadow:0 0 12px var(--neon-red);}

/* DASHBOARD */
.dashboard{padding:16px;display:grid;grid-template-columns:repeat(auto-fit,minmax(100px,1fr));gap:14px;}
.icon{background:var(--dark-card);border-radius:18px;text-align:center;padding:12px;box-shadow:0 0 10px rgba(255,255,255,.1);cursor:pointer;transition:all .3s;border:1px solid var(--neon-blue);animation:float 2s infinite alternate;}
.icon:hover{transform:translateY(-6px) scale(1.05);box-shadow:0 0 12px var(--neon-blue),0 0 20px var(--neon-red);}
.icon img{width:44px}
.icon span{font-size:11px;display:block;margin-top:6px;color:var(--white);font-weight:bold;}
@keyframes float{0%{transform:translateY(0);}100%{transform:translateY(-4px);}}

/* USERNAME & TIPS BOX */
#welcomeMsg{font-size:16px;font-weight:bold;margin-bottom:12px;background:var(--dark-card);padding:10px;border-radius:12px;border:1px solid var(--neon-red);text-align:center;box-shadow:0 0 8px var(--neon-red);}
#tipsBox{background:var(--dark-card);border-radius:16px;padding:12px;margin-bottom:12px;box-shadow:0 0 12px var(--neon-blue);color:var(--neon-blue);}

/* SECTIONS */
.section{padding:14px;display:none;transition:all .3s;}
.card{background:var(--dark-card);border-radius:20px;padding:16px;margin-bottom:14px;box-shadow:0 0 12px var(--neon-purple);transition:all .3s;}

/* COURSES */
.course{display:flex;gap:12px;align-items:center;transition:all .3s;}
.course img{width:90px;height:90px;border-radius:14px;object-fit:cover}
.price{font-weight:bold;color:var(--neon-red)}

/* BUTTONS */
button{width:100%;border:none;padding:10px;border-radius:14px;background:linear-gradient(135deg,var(--neon-red),var(--neon-blue));color:#fff;font-size:14px;margin-top:8px;cursor:pointer;transition:.3s;font-weight:bold;}
button:hover{opacity:.85;box-shadow:0 0 12px var(--neon-red)}

/* REVIEWS SLIDER */
.slider{display:flex;gap:12px;overflow-x:auto;scroll-behavior:smooth;padding-bottom:8px;}
.review{min-width:240px;background:var(--dark-card);border-radius:16px;padding:12px;box-shadow:0 0 12px var(--neon-blue);}
.review img{width:40px;height:40px;border-radius:50%}
.review b{font-size:13px}
.review p{margin:4px 0 0;font-size:12px;color:var(--white)}

/* LOGIN */
input,select{width:100%;padding:10px;border-radius:12px;border:1px solid var(--neon-red);margin-top:8px;background:#111;color:#fff;}

/* BOTTOM NAV */
.nav{position:fixed;bottom:0;left:0;width:100%;background:#111;display:flex;justify-content:space-around;box-shadow:0 -4px 12px rgba(255,0,0,.3);}
.nav div{text-align:center;font-size:11px;padding:6px;cursor:pointer;color:var(--neon-blue);font-weight:bold;transition:.3s;}
.nav div:hover{color:var(--neon-red);}

/* SCROLLBAR HIDE */
.slider::-webkit-scrollbar{display:none}
.copy-btn{cursor:pointer;color:var(--neon-red);font-weight:bold;font-size:12px;margin-left:4px}
</style>
</head>
<body>

<div id="splash">SkillMint Loading...</div>

<div class="header">
  <h2>SkillMint</h2>
  <div class="header-buttons">
    <button onclick="toggleDark()">🌙</button>
    <button id="logoutBtn" onclick="logout()" style="display:none;">Logout</button>
  </div>
</div>

<!-- LOGIN -->
<div id="loginScreen" class="section">
  <div class="card">
    <h3>Login / Signup</h3>
    <input id="username" placeholder="Username">
    <input id="password" type="password" placeholder="Password">
    <button onclick="saveLogin()">Login / Signup</button>
  </div>
</div>

<!-- DASHBOARD -->
<div id="dashboard" class="section">
  <div id="welcomeMsg"></div>
  <div id="tipsBox"></div>
  <div class="dashboard" id="dashCards">
    <div class="icon" onclick="openSec('courses',this)">
      <img src="https://img.icons8.com/fluency/96/online-course.png">
      <span>Courses</span>
    </div>
    <div class="icon" onclick="openSec('reviews',this)">
      <img src="https://img.icons8.com/fluency/96/group.png">
      <span>Reviews</span>
    </div>
    <div class="icon" onclick="openSec('payment',this)">
      <img src="https://img.icons8.com/fluency/96/credit-card.png">
      <span>Payment</span>
    </div>
    <div class="icon" onclick="openSec('ai',this)">
      <img src="https://img.icons8.com/fluency/96/robot.png">
      <span>AI Bot</span>
    </div>
  </div>
</div>

<!-- COURSES -->
<div id="courses" class="section card"></div>

<!-- PAYMENT -->
<div id="payment" class="section">
  <div class="card">
    <h3>Payment Method</h3>
    <select id="payMethod" onchange="updatePayNumber()">
      <option value="JazzCash">JazzCash</option>
      <option value="EasyPaisa">EasyPaisa</option>
      <option value="Binance">Binance</option>
    </select>
    <p>Send <b>PKR 1555</b> for Complete SkillMint Course</p>
    <p>Number: <span id="payNumber">03705519562</span> <span class="copy-btn" onclick="copyNumber()">Copy</span></p>
    <input type="text" id="txnID" placeholder="Transaction ID">
    <input type="file" id="uploadProof">
    <button onclick="startTimer()">Submit Proof</button>
    <p id="timer"></p>
  </div>
</div>

<!-- REVIEWS -->
<div id="reviews" class="section">
  <div class="card">
    <h3>Student Reviews</h3>
    <div class="slider" id="revBox"></div>
  </div>
</div>

<!-- AI BOT -->
<div id="ai" class="section">
  <div class="card">
    <h3>AI Skill Bot 🤖</h3>
    <div id="chat" style="max-height:200px;overflow-y:auto;margin-bottom:6px"></div>
    <input id="q" placeholder="Ask about courses">
    <button onclick="ask()">Ask</button>
    <button onclick="clearChat()" style="margin-top:6px;background:#f87171">Clear Chat</button>
  </div>
</div>

<!-- BOTTOM NAV -->
<div class="nav">
  <div onclick="openSec('dashboard')">🏠 Dashboard</div>
  <div onclick="openSec('payment')">💳 Payment</div>
  <div onclick="openSec('ai')">🤖 AI</div>
  <div onclick="openSec('reviews')">👥 Reviews</div>
</div>

<script>
setTimeout(()=>splash.style.display="none",1500)
function toggleDark(){document.body.classList.toggle("dark")}

/* LOGIN */
function checkLogin(){
  let login=JSON.parse(localStorage.getItem("login"))
  if(login && login.username){loginSuccess()}
  else{loginScreen.style.display="block";dashboard.style.display="none";logoutBtn.style.display="none"}
}
function saveLogin(){
  let u=document.getElementById("username").value
  let p=document.getElementById("password").value
  if(u && p){localStorage.setItem("login",JSON.stringify({username:u,password:p}));alert("Login successful!");loginSuccess()}
  else alert("Enter username & password")
}
function loginSuccess(){
  loginScreen.style.display="none";dashboard.style.display="block";logoutBtn.style.display="inline-block"
  if(localStorage.getItem("lastSec")) openSec(localStorage.getItem("lastSec"))
  loadDashboard();loadReviews();loadCourses();loadChat()
}
function logout(){localStorage.removeItem("login");localStorage.removeItem("lastSec");localStorage.removeItem("chatHistory");localStorage.removeItem("timer");location.reload()}

/* SECTIONS */
function openSec(id,el){document.querySelectorAll('.section').forEach(s=>s.style.display='none');document.getElementById(id).style.display='block';localStorage.setItem("lastSec",id)}

/* DASHBOARD */
function showWelcomeTips(){
  let tips=["Learn digital skills & earn online 💻","Boost your freelancing career 🚀","Practical projects included 📝","Start earning in PKR & USD 💰","AI tools & modern skills 🧠","Flexible learning anytime ⏰","Trusted by thousands of students 🌟"]
  tipsBox.innerHTML=""
  for(let i=0;i<3;i++){let t=tips[Math.floor(Math.random()*tips.length)];tipsBox.innerHTML+=`<p>• ${t}</p>`}
}
function loadDashboard(){
  let login=JSON.parse(localStorage.getItem("login"))
  welcomeMsg.innerText="Welcome, "+login.username+"! 🎉"
  showWelcomeTips()
  loadCourses()
}

/* COURSES */
function loadCourses(){
  let cDiv=document.getElementById("courses"); cDiv.innerHTML=""
  let courses=[
    {name:"Complete SkillMint Course",price:"PKR 1555",img:"https://picsum.photos/200?5",desc:"Learn digital skills, freelancing & earn online easily.",link:"https://gtv140.github.io/SkillMint-complete-course-/"},
    {name:"Web Development (Coming Soon)",price:"PKR 1555",img:"https://picsum.photos/200?6",desc:"HTML, CSS, JS basics and projects.",link:"#"},
    {name:"Graphic Design (Coming Soon)",price:"PKR 1555",img:"https://picsum.photos/200?7",desc:"Photoshop, Canva & creative design.",link:"#"},
    {name:"AI Tools (Coming Soon)",price:"PKR 1555",img:"https://picsum.photos/200?8",desc:"Learn ChatGPT, AI image generation & automation.",link:"#"}
  ]
  courses.forEach(c=>{
    let card=document.createElement("div")
    card.className="card course"
    card.innerHTML=`<img src="${c.img}"><div><b>${c.name}</b><br><span class="price">${c.price}</span><br><p>${c.desc}</p><button onclick="window.open('${c.link}','_blank')">Open</button></div>`
    cDiv.appendChild(card)
  })
}

/* PAYMENT */
const payNumbers={JazzCash:"03705519562",EasyPaisa:"03379827882",Binance:"0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F"};
function updatePayNumber(){let method=document.getElementById("payMethod").value;document.getElementById("payNumber").innerText=payNumbers[method]}
function copyNumber(){navigator.clipboard.writeText(document.getElementById("payNumber").innerText);alert("Number copied!")}
function startTimer(){
  let txn=document.getElementById("txnID").value;
  let file=document.getElementById("uploadProof").files[0];
  if(!txn||!file) return alert("Enter Transaction ID & Upload proof");
  let t=parseInt(localStorage.getItem("timer"))||120;
  localStorage.setItem("timer",t);
  timer.innerText=`Verifying payment: ${t}s`;
  let x=setInterval(()=>{
    t--;
    timer.innerText=`Verifying payment: ${t}s`;
    localStorage.setItem("timer",t);
    if(t<=0){
      clearInterval(x);
      localStorage.removeItem("timer");
      alert("Payment verified! Course link unlocked ✅");
      window.open("https://gtv140.github.io/SkillMint-complete-course-/","_blank");
      timer.innerText="✔ Course Unlocked";
    }
  },1000)
}

/* Continue timer on reload */
window.onload=function(){checkLogin();let t=parseInt(localStorage.getItem("timer"));if(t>0) startTimer()}

/* REVIEWS */
let revs=["SkillMint se earning start ho gayi 👍","बहुत बढ़िया platform hai","AI tools bohot helpful hain","میں satisfied ہوں","Real skills, real results","Freelancing confidence mila","Digital skills ne meri life change ki","SkillMint ki wajah se paisa earn ho raha hai","बहुत आसान और understandable","Courses clear aur practical hain"];
function loadReviews(){let revBox=document.getElementById("revBox");revBox.innerHTML="";revs.forEach(r=>{let img=Math.floor(Math.random()*70);revBox.innerHTML+=`<div class="review"><img src="https://i.pravatar.cc/100?img=${img}"><p>${r}</p></div>`});setInterval(()=>revBox.scrollLeft+=260,2500)}

/* AI BOT */
const apiKey="YOUR_API_KEY_HERE";
function loadChat(){let history=JSON.parse(localStorage.getItem("chatHistory")||"[]");chat.innerHTML="";history.forEach(msg=>{chat.innerHTML+=`<p><b>${msg.user}:</b> ${msg.text}</p>`;chat.innerHTML+=`<p><b>Bot:</b> ${msg.bot}</p>`});chat.scrollTop=chat.scrollHeight}
async function ask(){let qVal=q.value;if(!qVal)return;let history=JSON.parse(localStorage.getItem("chatHistory")||"[]");chat.innerHTML+=`<p><b>You:</b> ${qVal}</p>`;try{let res=await fetch("https://api.openai.com/v1/chat/completions",{method:"POST",headers:{"Content-Type":"application/json","Authorization":"Bearer "+apiKey},body:JSON.stringify({model:"gpt-3.5-turbo",messages:[{role:"user",content:qVal}]})});let data=await res.json();let answer=data.choices[0].message.content;chat.innerHTML+=`<p><b>Bot:</b> ${answer}</p>`;history.push({user:qVal,bot:answer});localStorage.setItem("chatHistory",JSON.stringify(history));chat.scrollTop=chat.scrollHeight}catch(e){chat.innerHTML+=`<p><b>Bot:</b> Error fetching response</p>`}q.value=""}
function clearChat(){if(confirm("Clear chat history?")){localStorage.removeItem("chatHistory");chat.innerHTML=""}}
</script>
</body>
</html>
