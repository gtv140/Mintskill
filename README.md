<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>SkillMint</title>
<style>
body{margin:0;font-family:'Segoe UI',Arial,sans-serif;background:#f2f5f9;color:#222;overflow-x:hidden;}
header{background:linear-gradient(135deg,#0f9d58,#0b7d46);color:#fff;padding:18px 15px;text-align:center;border-bottom-left-radius:20px;border-bottom-right-radius:20px;}
header h1{margin:0;font-size:22px;}
header p{margin:4px 0;font-size:12px;}
.container{padding:12px;}
.card{background:#fff;border-radius:16px;padding:14px;margin-bottom:14px;box-shadow:0 6px 18px rgba(0,0,0,0.08);transition:transform 0.3s;}
.card:hover{transform:scale(1.03);}
.icons{display:flex;justify-content:space-around;margin:10px 0;}
.icon{cursor:pointer;font-size:12px;text-align:center;flex:1;}
.icon img{width:42px;margin-bottom:4px;}
button{background:linear-gradient(135deg,#0f9d58,#0b7d46);color:#fff;border:none;padding:10px 12px;border-radius:10px;cursor:pointer;margin-top:6px;width:100%;}
button:hover{opacity:.9;}
input{width:100%;padding:8px;margin-top:6px;border-radius:8px;border:1px solid #ccc;}
#chatbot{position:fixed;bottom:70px;right:10px;width:90%;max-width:300px;background:#fff;border-radius:16px;box-shadow:0 6px 18px rgba(0,0,0,.3);display:flex;flex-direction:column;height:350px;z-index:999;}
#chatHeader{background:#0f9d58;color:#fff;padding:10px;text-align:center;cursor:pointer;font-size:14px;border-top-left-radius:16px;border-top-right-radius:16px;}
#chatBody{flex:1;padding:8px;overflow-y:auto;font-size:13px;}
#chatInput{display:flex;border-top:1px solid #ccc;}
#chatInput input{flex:1;padding:6px;border:none;font-size:13px;}
#chatInput button{padding:6px;background:#0f9d58;color:#fff;border:none;cursor:pointer;font-size:13px;}
.nav{position:fixed;bottom:0;left:0;width:100%;background:#fff;display:flex;justify-content:space-around;padding:8px 0;box-shadow:0 -4px 12px rgba(0,0,0,0.15);z-index:999;}
.nav a{text-align:center;font-size:10px;color:#222;text-decoration:none;flex:1;}
.dark-mode{background:#121212;color:#fff;}
.dark-mode .card{background:#1e1e1e;color:#fff;}
.dark-mode input{background:#222;color:#fff;border:1px solid #444;}
.carousel{overflow:hidden;height:140px;border-radius:12px;margin-bottom:14px;position:relative;}
.carousel-inner{display:flex;width:300%;animation:slide 12s infinite;}
.carousel-inner img{width:100%;flex-shrink:0;border-radius:12px;}
@keyframes slide{0%,33%{transform:translateX(0);}33%,66%{transform:translateX(-33.33%);}66%,100%{transform:translateX(-66.66%);}}
.review-box{overflow:hidden;height:100px;border-radius:12px;}
.review-inner{display:flex;flex-direction:column;animation:scrollReviews 25s linear infinite;}
@keyframes scrollReviews{0%{transform:translateY(0);}100%{transform:translateY(-100%);}}
.course-grid{display:flex;gap:8px;flex-wrap:wrap;justify-content:space-between;}
.course-item{flex:1 1 30%;min-width:100px;}
.course-item img{border-radius:10px;width:100%;}
</style>
</head>
<body>

<header>
<h1>SkillMint</h1>
<p>Learn Skills & Earn Online – Trusted Platform</p>
</header>

<div class="container">

<!-- Sliding Banner -->
<div class="carousel">
<div class="carousel-inner">
<img src="https://picsum.photos/400/140?1">
<img src="https://picsum.photos/400/140?2">
<img src="https://picsum.photos/400/140?3">
</div>
</div>

<div class="card">
<h3>About SkillMint</h3>
<p>SkillMint ek modern mobile app style platform hai jahan students real skills seekh kar online earning start karte hain. Clean cards, bottom navbar & tapable icons, real app feel.</p>
</div>

<div class="card icons">
<div class="icon" onclick="scrollToSection('courses')">
<img src="https://img.icons8.com/fluency/96/online-course.png"><br>Courses
</div>
<div class="icon" onclick="scrollToSection('reviews')">
<img src="https://img.icons8.com/fluency/96/star.png"><br>Reviews
</div>
<div class="icon" onclick="scrollToSection('buy')">
<img src="https://img.icons8.com/fluency/96/credit-card.png"><br>Buy
</div>
<div class="icon" onclick="scrollToSection('more')">
<img src="https://img.icons8.com/fluency/96/menu.png"><br>More
</div>
</div>

<div id="courses" class="card">
<h3>Popular Courses</h3>
<div class="course-grid">
<div class="course-item"><img src="https://picsum.photos/200?1"><br>Digital Marketing<br><button onclick="buyCourse('Digital Marketing')">Buy</button></div>
<div class="course-item"><img src="https://picsum.photos/200?2"><br>Graphic Designing<br><button onclick="buyCourse('Graphic Designing')">Buy</button></div>
<div class="course-item"><img src="https://picsum.photos/200?3"><br>Web Development<br><button onclick="buyCourse('Web Development')">Buy</button></div>
</div>
</div>

<div id="reviews" class="card">
<h3>Students Reviews</h3>
<div class="review-box"><div id="reviewBox" class="review-inner"></div></div>
</div>

<div id="buy" class="card">
<h3>Buy Course</h3>
<p id="selectedCourse" style="font-weight:bold"></p>
<label>Deposit Number</label>
<input id="number" readonly>
<button onclick="pay('jazz')">JazzCash</button>
<button onclick="pay('easy')">EasyPaisa</button>
<button onclick="pay('binance')">Binance</button>
<label>Upload Payment Proof</label>
<input type="file" id="proof">
<p id="verifyStatus"></p>
<button id="openCourse" disabled>Open Course</button>
</div>

<div id="more" class="card">
<h3>Contact & Trust</h3>
<p>Email: Rock.earn92@gmail.com</p>
<p>👥 Active Users: <b id="users"></b></p>
<p><a href="https://www.facebook.com/profile.php?id=100084218946114">Facebook</a> | <a href="https://www.instagram.com/mr_nazim073">Instagram</a></p>
<button onclick="toggleDark()">Toggle Dark Mode</button>
</div>

</div>

<div id="chatbot">
<div id="chatHeader" onclick="toggleChat()">💬 AI Chat</div>
<div id="chatBody"></div>
<div id="chatInput">
<input type="text" id="userMsg" placeholder="Type your question...">
<button onclick="sendMsg()">Send</button>
</div>
</div>

<div class="nav">
<a href="#">🏠<br>Home</a>
<a href="#buy">🎓<br>Buy</a>
<a href="https://www.facebook.com/profile.php?id=100084218946114">📘<br>FB</a>
<a href="https://www.instagram.com/mr_nazim073">📸<br>IG</a>
<a href="mailto:Rock.earn92@gmail.com">✉️<br>Email</a>
</div>

<script>
function scrollToSection(id){document.getElementById(id).scrollIntoView({behavior:'smooth'});}
let selected="";
function buyCourse(name){selected=name;selectedCourse.innerText="Selected Course: "+name;scrollToSection('buy');}
function pay(method){
let num={jazz:"03705519562",easy:"03379827882",binance:"0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F"}[method];
number.value=num;
navigator.clipboard.writeText(num);
alert("Deposit number copied ✅");
localStorage.setItem("timer",300);
startTimer();
}
function startTimer(){
let t=localStorage.getItem("timer")||300;
let int=setInterval(()=>{
if(t<=0){clearInterval(int);verifyStatus.innerText="Payment Verified ✔";openCourse.disabled=false;localStorage.removeItem("timer");}
else{verifyStatus.innerText="Verifying... "+t+"s";t--;localStorage.setItem("timer",t);}
},1000);
}
proof.onchange=startTimer;
openCourse.onclick=()=>alert("Course Opened: "+selected);

const reviews=["Best platform 👍","SkillMint changed my life ❤️","Courses are practical","Highly trusted","Earned my first income","Support helpful","Easy on mobile","Worth every rupee","Professional learning","Recommended"];
function loadReviews(){let box=document.getElementById("reviewBox");box.innerHTML="";for(let i=0;i<25;i++){let r=reviews[Math.floor(Math.random()*reviews.length)];box.innerHTML+=`<div style="margin-bottom:4px;">⭐ ${r}</div>`;}}
loadReviews();

setInterval(()=>{document.getElementById("users").innerText=Math.floor(1200+Math.random()*800);},2000);

let chatOpen=true;
function toggleChat(){let body=document.getElementById("chatBody");let parent=body.parentElement;parent.style.height = chatOpen?"40px":"350px";chatOpen=!chatOpen;}
async function sendMsg(){
let input=document.getElementById("userMsg");let text=input.value.trim();if(!text)return;
addChat("You",text);input.value="";addChat("Bot","Typing...");
let response=await fetch("https://api.openai.com/v1/chat/completions",{method:"POST",headers:{"Content-Type":"application/json","Authorization":"Bearer sk-nvQzX7O9jfiKIfOTE0Bd2516424a40B7A9EeD3E2Cf521760"},body:JSON.stringify({model:"gpt-4o-mini",messages:[{role:"system",content:"You are a helpful assistant for SkillMint website."},{role:"user",content:text}]})});
let data=await response.json();let botText=data.choices?.[0]?.message?.content||"Sorry, I can't answer right now.";
let bodyDiv=document.getElementById("chatBody");bodyDiv.lastElementChild.innerHTML="<b>Bot:</b> "+botText;bodyDiv.scrollTop=bodyDiv.scrollHeight;
}
function addChat(sender,msg){let body=document.getElementById("chatBody");let div=document.createElement("div");div.innerHTML="<b>"+sender+":</b> "+msg;body.appendChild(div);body.scrollTop=body.scrollHeight;}
function toggleDark(){document.body.classList.toggle("dark-mode");}
</script>

</body>
</html>
