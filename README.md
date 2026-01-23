<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>SkillMint</title>

<style>
:root{--grad:linear-gradient(135deg,#6366f1,#22c55e);}
body{margin:0;font-family:system-ui,sans-serif;background:#eef2ff;color:#222;overflow-x:hidden;transition:all .3s}
.dark{background:#0f172a;color:#e5e7eb}
.hide{display:none}

/* SPLASH */
#splash{position:fixed;inset:0;background:var(--grad);display:flex;align-items:center;justify-content:center;color:#fff;font-size:26px;z-index:9999;transition:all .3s}

/* HEADER */
.header{background:var(--grad);color:#fff;padding:16px;border-radius:0 0 26px 26px;text-align:center;position:sticky;top:0;z-index:9;display:flex;justify-content:space-between;align-items:center;box-shadow:0 4px 12px rgba(0,0,0,.2)}
.header h2{margin:0;font-size:22px}
.header-buttons{display:flex;gap:8px}
.header button{background:#fff;color:#000;border:none;padding:6px 12px;border-radius:20px;cursor:pointer;transition:.3s}
.header button:hover{opacity:.8}

/* DASHBOARD */
.dashboard{padding:16px;display:grid;grid-template-columns:repeat(auto-fit,minmax(100px,1fr));gap:14px}
.icon{background:#fff;border-radius:18px;text-align:center;padding:12px;box-shadow:0 6px 18px rgba(0,0,0,.1);cursor:pointer;transition:.3s}
.icon:hover{transform:translateY(-4px)}
.icon img{width:44px}
.icon span{font-size:11px;display:block;margin-top:6px}

/* DASHBOARD TIPS */
#welcomeMsg{font-size:16px;font-weight:bold;margin-bottom:12px}
#tipsBox{background:#fff;border-radius:16px;padding:12px;margin-bottom:12px;box-shadow:0 4px 14px rgba(0,0,0,.1)}

/* SECTIONS */
.section{padding:14px;display:none;transition:all .3s}
.card{background:#fff;border-radius:20px;padding:16px;margin-bottom:14px;box-shadow:0 6px 18px rgba(0,0,0,.1);transition:all .3s}

/* COURSES */
.course{display:flex;gap:12px;align-items:center;transition:all .3s}
.course img{width:90px;height:90px;border-radius:14px;object-fit:cover}
.price{font-weight:bold;color:#22c55e}

/* BUTTON */
button{width:100%;border:none;padding:10px;border-radius:14px;background:var(--grad);color:#fff;font-size:14px;margin-top:8px;cursor:pointer;transition:.3s}
button:hover{opacity:.85}

/* REVIEWS */
.slider{display:flex;gap:12px;overflow-x:auto;scroll-behavior:smooth;padding-bottom:8px}
.review{min-width:240px;background:#fff;border-radius:16px;padding:12px;box-shadow:0 4px 14px rgba(0,0,0,.1);transition:all .3s}
.review img{width:40px;height:40px;border-radius:50%}
.review b{font-size:13px}
.review p{margin:4px 0 0;font-size:12px;color:#555}

/* LOGIN */
input,select{width:100%;padding:10px;border-radius:12px;border:1px solid #ccc;margin-top:8px}

/* BOTTOM NAV */
.nav{position:fixed;bottom:0;left:0;width:100%;background:#fff;display:flex;justify-content:space-around;box-shadow:0 -4px 12px rgba(0,0,0,.2)}
.nav div{text-align:center;font-size:11px;padding:6px;cursor:pointer;transition:.3s}
.nav div:hover{opacity:.8}

/* SCROLLBAR HIDE */
.slider::-webkit-scrollbar{display:none}
.copy-btn{cursor:pointer;color:#6366f1;font-weight:bold;font-size:12px;margin-left:4px}
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

<!-- LOGIN SCREEN -->
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
  <div class="dashboard" id="dashCards"></div>
</div>

<!-- PAYMENT -->
<div id="payment" class="section">
  <div class="card">
    <h3>Payment Method</h3>
    <select id="payMethod" onchange="updatePayNumber()">
      <option value="JazzCash">JazzCash</option>
      <option value="EasyPaisa">EasyPaisa</option>
      <option value="Binance">Binance</option>
    </select>
    <p>Send <b id="courseName">-</b> payment of <b id="coursePrice">-</b></p>
    <p>Number: <span id="payNumber">03001234567</span> <span class="copy-btn" onclick="copyNumber()">Copy</span></p>
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
setTimeout(()=>splash.style.display="none",1200)

/* DARK MODE */
function toggleDark(){document.body.classList.toggle("dark")}

/* LOGIN CHECK */
function checkLogin(){
  let login=JSON.parse(localStorage.getItem("login"))
  if(login && login.username){
    loginSuccess()
  }else{
    loginScreen.style.display="block"
    dashboard.style.display="none"
    logoutBtn.style.display="none"
  }
}

/* LOGIN / SIGNUP */
function saveLogin(){
  let u=document.getElementById("username").value
  let p=document.getElementById("password").value
  if(u && p){
    localStorage.setItem("login",JSON.stringify({username:u,password:p}))
    alert("Login successful!")
    loginSuccess()
  }else alert("Enter username & password")
}

function loginSuccess(){
  loginScreen.style.display="none"
  dashboard.style.display="block"
  logoutBtn.style.display="inline-block"
  if(localStorage.getItem("lastSec")){
    openSec(localStorage.getItem("lastSec"))
  }
  loadDashboard()
  loadReviews()
  showWelcomeTips()
  loadChat()
}

/* LOGOUT */
function logout(){
  localStorage.removeItem("login")
  localStorage.removeItem("lastSec")
  localStorage.removeItem("course")
  localStorage.removeItem("chatHistory")
  location.reload()
}

/* SECTIONS */
function openSec(id){
  if(!localStorage.getItem("login")) return alert("Please login first!")
  document.querySelectorAll('.section').forEach(s=>s.style.display="none")
  if(id=="dashboard") dashboard.style.display="block"
  else document.getElementById(id).style.display="block"
  localStorage.setItem("lastSec",id)
}

/* DASHBOARD RANDOM CARDS */
function loadDashboard(){
  let dash=document.getElementById("dashCards")
  dash.innerHTML=""
  let courses=[
    {name:"Digital Marketing",price:"PKR 9,999 / $35",img:"https://picsum.photos/200?1"},
    {name:"Web Development",price:"PKR 14,999 / $55",img:"https://picsum.photos/200?2"},
    {name:"AI Tools + Freelancing",price:"PKR 12,999 / $45",img:"https://picsum.photos/200?3"},
    {name:"Graphic Designing",price:"PKR 8,999 / $32",img:"https://picsum.photos/200?4"}
  ]
  courses.forEach(c=>{
    let card=document.createElement("div")
    card.className="card course"
    card.innerHTML=`<img src="${c.img}"><div><b>${c.name}</b><br><span class="price">${c.price}</span><button onclick="selectCourse('${c.name}','${c.price}')">Buy</button></div>`
    dash.appendChild(card)
  })
}

/* SHOW WELCOME + RANDOM TIPS */
function showWelcomeTips(){
  let login=JSON.parse(localStorage.getItem("login"))
  welcomeMsg.innerText="Welcome, "+login.username+"! 🎉"
  let tips=[
    "Learn digital skills & earn online 💻",
    "Boost your freelancing career 🚀",
    "Practical projects included 📝",
    "Start earning in PKR & USD 💰",
    "AI tools & modern skills 🧠",
    "Flexible learning anytime ⏰",
    "Trusted by thousands of students 🌟"
  ]
  tipsBox.innerHTML=""
  for(let i=0;i<3;i++){
    let t=tips[Math.floor(Math.random()*tips.length)]
    tipsBox.innerHTML+=`<p>• ${t}</p>`
  }
}

/* SELECT COURSE FOR PAYMENT */
function selectCourse(name,price){
  localStorage.setItem("course",name)
  document.getElementById("courseName").innerText=name
  document.getElementById("coursePrice").innerText=price
  openSec("payment")
}

/* PAYMENT NUMBER COPY & AUTO-FILL */
const payNumbers={JazzCash:"03001234567",EasyPaisa:"03101234567",Binance:"bc1qxyz..."}
function updatePayNumber(){
  let method=document.getElementById("payMethod").value
  document.getElementById("payNumber").innerText=payNumbers[method]
}
function copyNumber(){
  navigator.clipboard.writeText(document.getElementById("payNumber").innerText)
  alert("Number copied!")
}

/* TIMER & COURSE UNLOCK */
function startTimer(){
  let file=document.getElementById("uploadProof").files[0]
  let txn=document.getElementById("txnID").value
  if(!file || !txn) return alert("Add Transaction ID and upload proof")
  let t=180
  localStorage.setItem("timer",t)
  timer.innerText="Verifying payment: "+t+"s"
  let x=setInterval(()=>{
    t--
    timer.innerText="Verifying payment: "+t+"s"
    localStorage.setItem("timer",t)
    if(t<=0){
      clearInterval(x)
      timer.innerText="✔ Course Unlocked"
      alert("Course link activated!")
      window.open("https://gtv140.github.io/SkillMint-complete-course-/","_blank")
      localStorage.removeItem("timer")
    }
  },1000)
}

/* REVIEWS */
let revs=[
"SkillMint se earning start ho gayi 👍",
"बहुत बढ़िया platform hai",
"AI tools bohot helpful hain",
"میں satisfied ہوں",
"Real skills, real results",
"Freelancing confidence mila",
"Digital skills ne meri life change ki",
"SkillMint ki wajah se paisa earn ho raha hai",
"बहुत आसान और understandable",
"Courses clear aur practical hain"
]
function loadReviews(){
  let revBox=document.getElementById("revBox")
  revBox.innerHTML=""
  revs.forEach(r=>{
    let img=Math.floor(Math.random()*70)
    revBox.innerHTML+=`<div class="review"><img src="https://i.pravatar.cc/100?img=${img}"><p>${r}</p></div>`
  })
  setInterval(()=>revBox.scrollLeft+=260,2500)
}

/* REAL AI BOT */
const apiKey = "YOUR_API_KEY_HERE" // <- replace with your API key
function loadChat(){
  let history=JSON.parse(localStorage.getItem("chatHistory")||"[]")
  chat.innerHTML=""
  history.forEach(msg=>{
    chat.innerHTML+=`<p><b>${msg.user}:</b> ${msg.text}</p>`
    chat.innerHTML+=`<p><b>Bot:</b> ${msg.bot}</p>`
  })
  chat.scrollTop=chat.scrollHeight
}

async function ask(){
  let qVal=q.value
  if(!qVal) return
  let history=JSON.parse(localStorage.getItem("chatHistory")||"[]")
  chat.innerHTML+=`<p><b>You:</b> ${qVal}</p>`
  // --- API CALL ---
  try{
    let res=await fetch("https://api.openai.com/v1/chat/completions",{
      method:"POST",
      headers:{
        "Content-Type":"application/json",
        "Authorization":"Bearer "+apiKey
      },
      body:JSON.stringify({
        model:"gpt-3.5-turbo",
        messages:[{role:"user",content:qVal}]
      })
    })
    let data=await res.json()
    let answer=data.choices[0].message.content
    chat.innerHTML+=`<p><b>Bot:</b> ${answer}</p>`
    history.push({user:qVal,bot:answer})
    localStorage.setItem("chatHistory",JSON.stringify(history))
    chat.scrollTop=chat.scrollHeight
  }catch(e){
    chat.innerHTML+=`<p><b>Bot:</b> Error fetching response</p>`
  }
  q.value=""
}

/* CLEAR CHAT */
function clearChat(){
  if(confirm("Clear chat history?")){
    localStorage.removeItem("chatHistory")
    chat.innerHTML=""
  }
}

/* INIT */
checkLogin()
</script>

</body>
</html>
