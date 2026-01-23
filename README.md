<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>SkillMint</title>

<style>
:root{--grad:linear-gradient(135deg,#6366f1,#22c55e);}
body{margin:0;font-family:system-ui,sans-serif;background:#eef2ff;color:#222;overflow-x:hidden;}
.dark{background:#0f172a;color:#e5e7eb}
.hide{display:none}

#splash{position:fixed;inset:0;background:var(--grad);display:flex;align-items:center;justify-content:center;color:#fff;font-size:26px;z-index:9999}

.header{background:var(--grad);color:#fff;padding:20px;border-radius:0 0 26px 26px;text-align:center;position:sticky;top:0;z-index:9}
.header button{background:#fff;color:#000;border:none;padding:6px 12px;border-radius:20px;margin-top:8px}

/* DASHBOARD */
.dashboard{padding:16px;display:grid;grid-template-columns:repeat(4,1fr);gap:14px}
.icon{background:#fff;border-radius:18px;text-align:center;padding:12px;box-shadow:0 6px 18px rgba(0,0,0,.1);cursor:pointer;transition:.3s}
.icon:hover{transform:translateY(-4px)}
.icon img{width:44px}
.icon span{font-size:11px;display:block;margin-top:6px}

/* SECTIONS */
.section{padding:14px;display:none}
.card{background:#fff;border-radius:20px;padding:16px;margin-bottom:14px;box-shadow:0 6px 18px rgba(0,0,0,.1)}

/* COURSES */
.course{display:flex;gap:12px;align-items:center}
.course img{width:90px;height:90px;border-radius:14px;object-fit:cover}
.price{font-weight:bold;color:#22c55e}

/* BUTTON */
button{width:100%;border:none;padding:10px;border-radius:14px;background:var(--grad);color:#fff;font-size:14px;margin-top:8px}

/* REVIEWS */
.slider{display:flex;gap:12px;overflow:hidden;scroll-behavior:smooth}
.review{min-width:240px;background:#fff;border-radius:16px;padding:12px;box-shadow:0 4px 14px rgba(0,0,0,.1)}
.review img{width:40px;height:40px;border-radius:50%}
.review b{font-size:13px}
.review p{margin:4px 0 0;font-size:12px;color:#555}

/* LOGIN */
input{width:100%;padding:10px;border-radius:12px;border:1px solid #ccc;margin-top:8px}

/* BOTTOM NAV */
.nav{position:fixed;bottom:0;left:0;width:100%;background:#fff;display:flex;justify-content:space-around;box-shadow:0 -4px 12px rgba(0,0,0,.2)}
.nav div{text-align:center;font-size:11px;padding:6px}
</style>
</head>

<body>

<div id="splash">SkillMint Loading...</div>

<div class="header">
  <h2>SkillMint</h2>
  <p>Learn Skills • Earn Online</p>
  <button onclick="toggleDark()">Dark Mode</button>
  <button id="logoutBtn" onclick="logout()" style="display:none;margin-top:8px;">Logout</button>
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
  <div class="dashboard">
    <div class="icon" onclick="openSec('courses')">
      <img src="https://img.icons8.com/fluency/96/online-course.png">
      <span>Courses</span>
    </div>
    <div class="icon" onclick="openSec('reviews')">
      <img src="https://img.icons8.com/fluency/96/group.png">
      <span>Reviews</span>
    </div>
    <div class="icon" onclick="openSec('payment')">
      <img src="https://img.icons8.com/fluency/96/credit-card.png">
      <span>Payment</span>
    </div>
    <div class="icon" onclick="openSec('ai')">
      <img src="https://img.icons8.com/fluency/96/robot.png">
      <span>AI Bot</span>
    </div>
  </div>
</div>

<!-- COURSES -->
<div id="courses" class="section">
  <div class="card course">
    <img src="https://picsum.photos/200?1">
    <div>
      <b>Digital Marketing</b><br>
      <span class="price">PKR 9,999 / $35</span>
      <button onclick="buyCourse('Digital Marketing')">Buy</button>
    </div>
  </div>
  <div class="card course">
    <img src="https://picsum.photos/200?2">
    <div>
      <b>Web Development</b><br>
      <span class="price">PKR 14,999 / $55</span>
      <button onclick="buyCourse('Web Development')">Buy</button>
    </div>
  </div>
  <div class="card course">
    <img src="https://picsum.photos/200?3">
    <div>
      <b>AI Tools + Freelancing</b><br>
      <span class="price">PKR 12,999 / $45</span>
      <button onclick="buyCourse('AI Tools')">Buy</button>
    </div>
  </div>
</div>

<!-- REVIEWS -->
<div id="reviews" class="section">
  <div class="card">
    <h3>Student Reviews</h3>
    <div class="slider" id="revBox"></div>
  </div>
</div>

<!-- PAYMENT -->
<div id="payment" class="section">
  <div class="card">
    <h3>Payment Method</h3>
    <p>JazzCash / EasyPaisa / Bank Transfer</p>
    <p>Send screenshot proof to:</p>
    <b>Email:</b> Rock.earn92@gmail.com<br>
    <b>Facebook / Instagram DM</b>
    <input type="file">
    <button onclick="startTimer()">Submit Proof</button>
    <p id="timer"></p>
  </div>
</div>

<!-- AI BOT -->
<div id="ai" class="section">
  <div class="card">
    <h3>AI Skill Bot 🤖</h3>
    <div id="chat" style="max-height:200px;overflow-y:auto;margin-bottom:6px;"></div>
    <input id="q" placeholder="Ask about courses">
    <button onclick="ask()">Ask</button>
  </div>
</div>

<!-- BOTTOM NAV -->
<div class="nav">
  <div onclick="openSec('courses')">🏠 Home</div>
  <div onclick="openSec('payment')">💳 Pay</div>
  <div onclick="openSec('ai')">🤖 AI</div>
</div>

<script>
setTimeout(()=>splash.style.display="none",1200)

/* THEME */
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
}

/* LOGOUT */
function logout(){
  localStorage.removeItem("login")
  localStorage.removeItem("lastSec")
  location.reload()
}

/* SECTIONS */
function openSec(id){
  if(!localStorage.getItem("login")) return alert("Please login first!")
  document.querySelectorAll('.section').forEach(s=>s.style.display="none")
  if(id!="loginScreen") dashboard.style.display="block"
  document.getElementById(id).style.display="block"
  localStorage.setItem("lastSec",id)
}

/* BUY COURSE */
function buyCourse(name){
  if(!localStorage.getItem("login")) return alert("Login first")
  localStorage.setItem("course",name)
  alert(name+" selected. Complete payment.")
  openSec("payment")
}

/* TIMER & COURSE UNLOCK */
function startTimer(){
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
let reviews=[
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
reviews.forEach(r=>{
  let img=Math.floor(Math.random()*70)
  revBox.innerHTML+=`
  <div class="review">
    <img src="https://i.pravatar.cc/100?img=${img}">
    <p>${r}</p>
  </div>`
})
setInterval(()=>revBox.scrollLeft+=260,2500)

/* AI BOT */
function ask(){
  chat.innerHTML+="<p><b>You:</b> "+q.value+"</p>"
  setTimeout(()=>{
    chat.innerHTML+="<p><b>Bot:</b> SkillMint courses help you learn & earn online!</p>"
    chat.scrollTop=chat.scrollHeight
  },700)
}

/* INIT */
checkLogin()
</script>

</body>
</html>
