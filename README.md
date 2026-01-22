<html lang="en">
<head>
<meta charset="UTF-8">
<title>SkillMint Pro – Learn Skills & Earn Online</title>
<meta name="description" content="SkillMint Pro helps you learn digital skills and earn online via AdSense, affiliate marketing, and digital services.">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
*{box-sizing:border-box;}
body{margin:0;font-family:Arial,sans-serif;background:#f4f6f9;color:#222;transition:background 0.3s, color 0.3s;}
header{background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);color:#fff;padding:50px 20px;text-align:center;}
header h1{margin:0;font-size:42px;}
header p{margin-top:10px;font-size:18px;opacity:0.9;}
nav{background:#111;padding:12px;text-align:center;position:sticky;top:0;z-index:1000;}
nav a{color:#fff;margin:0 12px;text-decoration:none;font-weight:bold;font-size:14px;}
section{background:#fff;margin:25px auto;padding:30px;max-width:1000px;border-radius:12px;box-shadow:0 6px 15px rgba(0,0,0,0.08);}
h2{margin-top:0;}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px;}
.card{background:#f9fafb;padding:20px;border-radius:10px;border:1px solid #e5e7eb;transition:transform 0.3s ease;}
.card:hover{transform:translateY(-5px);}
.btn{display:inline-block;margin-top:15px;padding:12px 22px;background:#25D366;color:#fff;text-decoration:none;border-radius:6px;font-weight:bold;font-size:14px;transition:background 0.3s;}
.btn:hover{background:#128C7E;}
footer{background:#111;color:#fff;text-align:center;padding:20px;font-size:14px;}
@media(max-width:600px){nav a{display:block;margin:8px 0;}}
.ads-placeholder{background:#eee;color:#555;text-align:center;padding:15px;border-radius:8px;margin-top:10px;}
#scrollBtn{position:fixed;bottom:20px;right:20px;background:#25D366;color:#fff;padding:12px 15px;border:none;border-radius:50%;cursor:pointer;display:none;font-size:18px;z-index:999;}
.dark-mode{background:#121212;color:#e0e0e0;}
.dark-mode header{background:linear-gradient(135deg,#2c3e50,#34495e,#1c1c1c);}
.dark-mode nav{background:#222;}
.dark-mode section{background:#1e1e1e;color:#e0e0e0;box-shadow:0 6px 15px rgba(0,0,0,0.3);}
.dark-mode .card{background:#2a2a2a;border:1px solid #555;}
/* Popup Guide */
#earningGuide {display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.85);color:#fff;overflow-y:auto;z-index:9999;padding:20px;}
#earningGuide .guide-content{max-width:800px;margin:50px auto;background:#222;border-radius:12px;padding:25px;box-shadow:0 10px 30px rgba(0,0,0,0.5);}
#earningGuide h2{color:#25D366;}
#earningGuide button{background:#25D366;color:#fff;padding:10px 15px;border:none;border-radius:5px;margin-top:15px;cursor:pointer;}
#earningGuide ul{margin-left:20px;}
</style>
</head>

<body>

<header>
<h1>SkillMint Pro</h1>
<p>Learn Skills. Build Online Income.</p>
<button onclick="toggleDarkMode()" style="margin-top:15px;padding:10px 15px;border:none;border-radius:5px;cursor:pointer;">Toggle Dark Mode</button>
<button onclick="openGuide()" style="margin-top:15px;padding:10px 15px;border:none;border-radius:5px;cursor:pointer;">View First Week Earning Guide</button>
</header>

<nav>
<a href="#about">About</a>
<a href="#earn">Earning</a>
<a href="#services">Services</a>
<a href="#affiliate">Affiliate</a>
<a href="#blog">Blog</a>
<a href="#contact">Contact</a>
</nav>

<section id="about">
<h2>About SkillMint Pro</h2>
<p>SkillMint Pro is your digital learning & earning hub. Learn practical online skills and turn them into real income with AdSense, affiliate marketing, and digital services. Beginner-friendly and future-ready.</p>
</section>

<section id="earn">
<h2>💰 How You Can Earn</h2>
<div class="grid">
<div class="card">
<h3>Google AdSense</h3>
<p>Monetize your content by displaying Google ads. Drive traffic and earn passive income.</p>
<div class="ads-placeholder">AdSense Placeholder</div>
</div>
<div class="card">
<h3>Affiliate Marketing</h3>
<p>Promote products & tools and earn commission for every sale.</p>
<a class="btn" href="#">Visit Affiliate Offer</a>
</div>
<div class="card">
<h3>Digital Services</h3>
<p>Offer services like website setup, YouTube SEO, thumbnails & logo design.</p>
<a class="btn" href="https://wa.me/03705519562">Contact on WhatsApp</a>
</div>
</div>
</section>

<section id="services">
<h2>🛠 Services We Offer</h2>
<ul>
<li>Website Design & GitHub Pages Setup</li>
<li>YouTube SEO & Channel Growth</li>
<li>Thumbnail & Logo Design</li>
<li>Affiliate Website Creation</li>
</ul>
<a class="btn" href="https://wa.me/03705519562">Contact on WhatsApp</a>
</section>

<section id="affiliate">
<h2>🔥 Recommended Tools & Affiliate Offers</h2>
<p>Check trusted tools for online earning. Using our links may earn a small commission at no extra cost to you.</p>
<a class="btn" href="#">Visit Affiliate Offer</a>
</section>

<section id="blog">
<h2>📝 Blog & Updates</h2>
<p>This section will host small guides, news, or updates to drive traffic and support AdSense earnings.</p>
</section>

<section id="contact">
<h2>📞 Contact & Support</h2>
<p>Email: <a href="mailto:rock.earn92@gmail.com">rock.earn92@gmail.com</a></p>
<p>WhatsApp: <a href="https://wa.me/03705519562">03705519562</a></p>
</section>

<section>
<h2>📄 Legal & Disclaimer (AdSense Ready)</h2>
<p><strong>Privacy Policy:</strong> We respect user privacy and never misuse personal info.<br>
<strong>Disclaimer:</strong> Earnings depend on effort, traffic, and skills. No guaranteed income.</p>
</section>

<footer>
<p>© <span id="year"></span> SkillMint Pro. All Rights Reserved.</p>
</footer>

<button id="scrollBtn" onclick="scrollToTop()">↑</button>

<!-- Interactive Earning Guide Popup -->
<div id="earningGuide">
<div class="guide-content">
<h2>🔥 First Week Earning Boost Guide</h2>
<p>Follow these steps to maximize early earning:</p>
<ul>
<li><strong>GitHub Pages Live:</strong> Ensure your website link is live.</li>
<li><strong>AdSense:</strong> Apply & integrate code in placeholder divs.</li>
<li><strong>Affiliate Links:</strong> Replace buttons with high-converting affiliate URLs.</li>
<li><strong>WhatsApp Services:</strong> Offer small services, respond quickly to clients.</li>
<li><strong>Traffic:</strong> Share link on social media, WhatsApp, Quora, Reddit.</li>
<li><strong>Blog Updates:</strong> Post small guides/news to support AdSense & SEO.</li>
<li><strong>Consistency:</strong> Daily updates, check analytics, optimize buttons.</li>
<li><strong>Track & Improve:</strong> Optimize clicks, update content for better conversion.</li>
</ul>
<button onclick="closeGuide()">Close Guide</button>
</div>
</div>

<script>
// Dark Mode Toggle
function toggleDarkMode(){document.body.classList.toggle("dark-mode");}

// Scroll-to-top button
const scrollBtn=document.getElementById("scrollBtn");
window.onscroll=function(){
  if(document.body.scrollTop>200||document.documentElement.scrollTop>200){scrollBtn.style.display="block";}
  else{scrollBtn.style.display="none";}
};
function scrollToTop(){window.scrollTo({top:0,behavior:'smooth'});}

// Dynamic Year in Footer
document.getElementById("year").textContent=new Date().getFullYear();

// Earning Guide Popup
function openGuide(){document.getElementById("earningGuide").style.display="block";}
function closeGuide(){document.getElementById("earningGuide").style.display="none";}
</script>

</body>
</html>
