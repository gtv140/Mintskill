<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<style>
:root{
 --bg:#f3f6fb;
 --card:#ffffff;
 --text:#111;
 --primary:#2563eb;
 --success:#16a34a;
}
body.dark{
 --bg:#0f172a;
 --card:#020617;
 --text:#e5e7eb;
}

*{box-sizing:border-box}
body{
 margin:0;
 font-family:system-ui,Arial;
 background:var(--bg);
 color:var(--text);
 padding-bottom:120px;
 transition:.3s;
}

/* HEADER */
.header{
 background:linear-gradient(90deg,#2563eb,#22c55e);
 color:#fff;
 padding:22px;
 text-align:center;
}
.header img{
 width:100%;
 border-radius:14px;
 margin-top:10px;
}

/* SECTIONS */
.section{padding:18px}
h2{text-align:center}

/* CARDS */
.cards{display:flex;flex-direction:column;gap:14px}
.card{
 background:var(--card);
 border-radius:16px;
 padding:16px;
 box-shadow:0 6px 18px rgba(0,0,0,.1);
 transition:.3s;
}
.card:hover{transform:translateY(-5px)}
.card img{width:100%;border-radius:12px}

/* ICONS */
.icons{display:flex;gap:12px;flex-wrap:wrap;justify-content:center}
.icon{
 background:var(--card);
 width:22%;
 min-width:70px;
 padding:12px;
 border-radius:14px;
 text-align:center;
 box-shadow:0 4px 12px rgba(0,0,0,.1);
 display:none;
 cursor:pointer;
 transition:.3s;
}
.icon:hover{transform:scale(1.05)}
.icon i{font-size:26px;color:var(--primary)}

/* BUTTONS */
.btn{
 width:100%;
 padding:14px;
 border:none;
 border-radius:14px;
 background:var(--primary);
 color:#fff;
 font-size:15px;
 margin-top:8px;
 cursor:pointer;
}
.btn.green{background:var(--success)}

/* REVIEWS */
.slider{display:flex;gap:10px;overflow:hidden}
.review{
 background:var(--card);
 min-width:220px;
 padding:12px;
 border-radius:14px;
 box-shadow:0 4px 14px rgba(0,0,0,.1);
}

/* NAV */
.nav{
 position:fixed;
 bottom:0;left:0;
 width:100%;
 background:var(--card);
 display:flex;
 justify-content:space-around;
 padding:10px 0;
 box-shadow:0 -4px 14px rgba(0,0,0,.2);
}
.nav a{text-decoration:none;font-size:11px;color:var(--text);text-align:center}

/* DARK MODE BTN */
.toggle{
 position:fixed;
 top:14px;
 right:14px;
 background:#fff;
 padding:8px 10px;
 border-radius:50%;
 cursor:pointer;
}

/* MOBILE */
@media(min-width:768px){
 .cards{flex-direction:row;flex-wrap:wrap}
 .card{width:48%}
}
</style>
</head>

<body>

<div class="toggle" onclick="toggleMode()">🌙</div>

<!-- HEADER -->
<div class="header">
 <h1>SkillMint</h1>
 <p>Learn Skills • Earn Online • Trusted Platform</p>
 <img src="https://picsum.photos/seed/banner/1200/400">
</div>

<!-- HOME -->
<div class="section">
 <h2>About SkillMint</h2>
 <p style="text-align:center;max-width:650px;margin:auto">
 SkillMint ek trusted online learning platform hai jo beginners ko
 **YouTube, Freelancing, Affiliate Marketing aur Social Media**
 se earning sikhata hai — step by step, simple aur practical tareeke se.
 </p>

 <p id="users" style="text-align:center;color:#16a34a;font-weight:bold"></p>

 <div class="slider" id="reviews"></div>

 <div class="icons">
  <div class="icon" onclick="go('courses')"><i class="fa fa-video"></i><br>YouTube</div>
  <div class="icon" onclick="go('courses')"><i class="fa fa-laptop-code"></i><br>Freelance</div>
  <div class="icon" onclick="go('courses')"><i class="fa fa-dollar-sign"></i><br>Affiliate</div>
  <div class="icon" onclick="go('courses')"><i class="fa fa-users"></i><br>Social</div>
 </div>

 <div class="btn" onclick="showIcons()">More</div>
</div>

<!-- COURSES -->
<div class="section" id="courses">
 <h2>Courses</h2>
 <div class="cards">
  <div class="card"><img src="https://picsum.photos/seed/1/400/250"><h3>YouTube Earning</h3></div>
  <div class="card"><img src="https://picsum.photos/seed/2/400/250"><h3>Freelancing</h3></div>
  <div class="card"><img src="https://picsum.photos/seed/3/400/250"><h3>Affiliate Marketing</h3></div>
  <div class="card"><img src="https://picsum.photos/seed/4/400/250"><h3>Social Media Growth</h3></div>
 </div>
</div>

<!-- FLOAT CHAT -->
<a href="https://wa.me/923379827882" style="
position:fixed;right:16px;bottom:90px;
background:#22c55e;color:#fff;
padding:14px;border-radius:50%">💬</a>

<!-- NAV -->
<div class="nav">
 <a href="#">🏠<br>Home</a>
 <a href="#courses">🎓<br>Courses</a>
 <a href="https://www.facebook.com/profile.php?id=100084218946114">📘<br>FB</a>
 <a href="https://www.instagram.com/mr_nazim073">📸<br>IG</a>
 <a href="mailto:Rock.earn92@gmail.com">✉️<br>Email</a>
</div>

<script>
// DARK MODE
function toggleMode(){
 document.body.classList.toggle("dark");
 localStorage.setItem("mode",document.body.classList.contains("dark"));
}
if(localStorage.getItem("mode")==="true") document.body.classList.add("dark");

// ICONS
function showIcons(){
 document.querySelectorAll(".icon").forEach(i=>i.style.display="block");
}

// REVIEWS
const reviews=[
"SkillMint se earning start ho gai",
"Beginner friendly aur trusted",
"Simple steps, real support",
"Courses worth it hain",
"Best platform for beginners"
];
let r=document.getElementById("reviews"),i=0;
setInterval(()=>{
 r.innerHTML=`<div class="review">${reviews[i%reviews.length]}</div>`;
 i++;
},3500);

// ACTIVE USERS
setInterval(()=>{
 document.getElementById("users").innerText=
 "Active Users: "+(100+Math.floor(Math.random()*200));
},2500);

// SCROLL
function go(id){
 document.getElementById(id).scrollIntoView({behavior:"smooth"});
}
</script>

</body>
</html>
