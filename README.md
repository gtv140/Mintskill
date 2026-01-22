<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>SkillMint – Learn Skills & Earn Online</title>
<meta name="description" content="SkillMint helps you learn digital skills and earn online via AdSense, affiliate marketing, and digital services.">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">

<style>
/* Basic Reset */
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:'Roboto',sans-serif;background:#f4f6f9;color:#222;transition:background 0.3s,color 0.3s;}
a{text-decoration:none;}

/* Header */
header{background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);color:#fff;padding:80px 20px;text-align:center;position:relative;overflow:hidden;}
header h1{font-size:48px;margin-bottom:15px;}
header p{font-size:20px;opacity:0.9;margin-bottom:20px;}
header .cta-btn{padding:15px 30px;background:#25D366;color:#fff;border-radius:6px;font-weight:bold;transition:0.3s;}
header .cta-btn:hover{background:#128C7E;}
header .hero-bg{position:absolute;top:0;left:0;width:100%;height:100%;background:radial-gradient(circle,rgba(255,255,255,0.1),transparent);animation:rotate 20s linear infinite;z-index:0;}
@keyframes rotate{0%{transform:rotate(0deg);}100%{transform:rotate(360deg);}}

/* Nav */
nav{background:#111;padding:12px;text-align:center;position:sticky;top:0;z-index:1000;}
nav a{color:#fff;margin:0 12px;font-weight:bold;font-size:14px;transition:0.3s;}
nav a:hover{color:#25D366;}

/* Sections */
section{background:#fff;margin:25px auto;padding:30px;max-width:1000px;border-radius:12px;box-shadow:0 6px 15px rgba(0,0,0,0.08);}
h2{text-align:center;margin-bottom:20px;}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px;}
.card{background:#f9fafb;padding:20px;border-radius:10px;border:1px solid #e5e7eb;transition:transform 0.3s,box-shadow 0.3s;}
.card:hover{transform:translateY(-8px);box-shadow:0 10px 20px rgba(0,0,0,0.25);}
.card img{width:100%;border-radius:8px;margin-bottom:10px;}
.btn{display:inline-block;margin-top:15px;padding:12px 22px;background:#25D366;color:#fff;border-radius:6px;font-weight:bold;transition:0.3s;}
.btn:hover{background:#128C7E;}

/* Testimonials */
.testimonial{background:#f1f5f9;padding:20px;border-radius:10px;text-align:center;box-shadow:0 5px 15px rgba(0,0,0,0.1);}
.testimonial img{width:60px;height:60px;border-radius:50%;margin-bottom:10px;}
.testimonial p{font-style:italic;}

/* FAQ Accordion */
.accordion{border-radius:8px;border:1px solid #ccc;overflow:hidden;margin-bottom:10px;}
.accordion button{background:#25D366;color:#fff;padding:15px;width:100%;border:none;text-align:left;cursor:pointer;font-weight:bold;transition:0.3s;}
.accordion button:hover{background:#128C7E;}
.accordion .panel{padding:15px;background:#f9fafb;display:none;}

/* Newsletter */
.newsletter input[type=email]{padding:12px;width:70%;border-radius:5px;border:1px solid #ccc;}
.newsletter button{padding:12px 20px;border:none;background:#25D366;color:#fff;border-radius:5px;font-weight:bold;transition:0.3s;}
.newsletter button:hover{background:#128C7E;}

/* Floating WhatsApp */
.floating-whatsapp{position:fixed;bottom:20px;right:20px;background:#25D366;color:#fff;padding:15px;border-radius:50%;font-size:20px;text-align:center;cursor:pointer;z-index:1000;box-shadow:0 5px 15px rgba(0,0,0,0.3);}
.floating-whatsapp:hover{background:#128C7E;}

/* Footer */
footer{background:#111;color:#fff;text-align:center;padding:20px;font-size:14px;}

/* Scroll Button */
#scrollBtn{position:fixed;bottom:90px;right:20px;background:#25D366;color:#fff;padding:12px 15px;border:none;border-radius:50%;cursor:pointer;display:none;font-size:18px;z-index:999;}
#scrollBtn:hover{background:#128C7E;}

/* Dark Mode */
.dark-mode{background:#121212;color:#e0e0e0;}
.dark-mode header{background:linear-gradient(135deg,#2c3e50,#34495e,#1c1c1c);}
.dark-mode nav{background:#222;}
.dark-mode section{background:#1e1e1e;color:#e0e0e0;box-shadow:0 6px 15px rgba(0,0,0,0.3);}
.dark-mode .card{background:#2a2a2a;border:1px solid #555;}
</style>
</head>

<body>

<header>
<div class="hero-bg"></div>
<h1>SkillMint</h1>
<p>Learn Skills. Build Your Online Income.</p>
<a href="#earn" class="cta-btn">Start Learning & Earning</a>
<button onclick="toggleDarkMode()" style="position:absolute;top:15px;right:15px;padding:10px 12px;border:none;border-radius:5px;cursor:pointer;">🌙</button>
</header>

<nav>
<a href="#about">About</a>
<a href="#earn">Earn</a>
<a href="#services">Services</a>
<a href="#testimonials">Testimonials</a>
<a href="#faq">FAQ</a>
<a href="#contact">Contact</a>
</nav>

<section id="about">
<h2>About SkillMint</h2>
<p>SkillMint is your digital learning & earning hub. Learn practical online skills and turn them into real income with AdSense, affiliate marketing, and digital services. Beginner-friendly & future-ready.</p>
<img src="https://picsum.photos/800/300?grayscale&random=1" alt="Learning Skills Image" style="border-radius:10px;margin-top:15px;">
</section>

<section id="earn">
<h2>💰 How You Can Earn</h2>
<div class="grid">
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=2" alt="Earn Money Online">
<h3>Google AdSense</h3>
<p>Monetize your content by displaying ads. Drive traffic & earn passive income.</p>
<a class="btn" href="#">Learn More</a>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=3" alt="Affiliate Marketing">
<h3>Affiliate Marketing</h3>
<p>Promote products & earn commission for every sale.</p>
<a class="btn" href="#">Visit Offer</a>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=4" alt="Digital Services">
<h3>Digital Services</h3>
<p>Offer services like website setup, YouTube SEO, thumbnails & logos.</p>
<a class="btn" href="https://wa.me/03705519562">Contact on WhatsApp</a>
</div>
</div>
</section>

<section id="services">
<h2>🛠 Services We Offer</h2>
<div class="grid">
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=5" alt="Website Services">
<p>Website Design & GitHub Pages Setup</p>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=6" alt="YouTube SEO">
<p>YouTube SEO & Channel Growth</p>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=7" alt="Thumbnail Design">
<p>Thumbnail & Logo Design</p>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=8" alt="Affiliate Website">
<p>Affiliate Website Creation</p>
</div>
</div>
<a class="btn" href="https://wa.me/03705519562">Contact on WhatsApp</a>
</section>

<section id="testimonials">
<h2>💬 Testimonials</h2>
<div class="grid">
<div class="testimonial card">
<img src="https://picsum.photos/60/60?random=1" alt="User">
<p>"SkillMint helped me earn my first $100 online in just one week!" – Ali</p>
</div>
<div class="testimonial card">
<img src="https://picsum.photos/60/60?random=2" alt="User">
<p>"Amazing resources & guidance. Highly recommend!" – Sara</p>
</div>
<div class="testimonial card">
<img src="https://picsum.photos/60/60?random=3" alt="User">
<p>"Professional & easy to follow courses. Love it!" – Khan</p>
</div>
</div>
</section>

<section id="faq">
<h2>❓ FAQ</h2>

<div class="accordion">
<button onclick="toggleAccordion(this)">How long before I earn?</button>
<div class="panel"><p>Depends on your traffic & effort, usually 1-2 weeks for initial earnings.</p></div>
</div>
<div class="accordion">
<button onclick="toggleAccordion(this)">Do I need coding skills?</button>
<div class="panel"><p>No, all guides are beginner-friendly and step-by-step.</p></div>
</div>
<div class="accordion">
<button onclick="toggleAccordion(this)">Is this free or paid?</button>
<div class="panel"><p>Basic resources are free. Optional services / packages are paid.</p></div>
</div>

</section>

<section id="newsletter">
<h2>📩 Subscribe for Tips & Guides</h2>
<form class="newsletter">
<input type="email" placeholder="Your Email" required>
<button type="submit">Subscribe</button>
</form>
</section>

<section id="pricing">
<h2>💎 Packages</h2>
<div class="grid">
<div class="card">
<h3>Starter</h3>
<p>$10 – Basic guide & 1 service consultation</p>
<a class="btn" href="https://wa.me/03705519562">Buy Now</a>
</div>
<div class="card">
<h3>Pro</h3>
<p>$30 – Complete earning guide + 3 services</p>
<a class="btn" href="https://wa.me/03705519562">Buy Now</a>
</div>
<div class="card">
<h3>Premium</h3>
<p>$50 – Full resources + lifetime support</p>
<a class="btn" href="https://wa.me/03705519562">Buy Now</a>
</div>
</div>
</section>

<section id="contact">
<h2>📞 Contact & Support</h2>
<form action="mailto:rock.earn92@gmail.com" method="post" enctype="text/plain">
<input type="text" name="Name" placeholder="Your Name" required>
<input type="email" name="Email" placeholder="Your Email" required>
<textarea name="Message" placeholder="Your Message" required></textarea>
<button type="submit" class="btn">Send Message</button>
</form>

<p>Or Contact Directly on WhatsApp!</p>
<a href="https://wa.me/03705519562" class="btn">WhatsApp</a>

<div style="margin-top:15px;">
<a href="https://www.facebook.com/profile.php?id=100084218946114" target="_blank" class="btn" style="background:#3b5998;">Facebook</a>
<a href="https://www.instagram.com/mr_nazim073?igsh=MXd4d2hmcWNvNjVsdQ==" target="_blank" class="btn" style="background:#E1306C;">Instagram</a>
</div>
</section>

<footer>
<p>© <span id="year"></span> SkillMint. All Rights Reserved.</p>
</footer>

<div class="floating-whatsapp" onclick="window.open('https://wa.me/03705519562')">💬</div>
<button id="scrollBtn" onclick="scrollToTop()">↑</button>

<script>
function toggleDarkMode(){document.body.classList.toggle("dark-mode");}
function scrollToTop(){window.scrollTo({top:0,behavior:'smooth'});}
window.onscroll=function(){document.getElementById("scrollBtn").style.display=(window.scrollY>200)?'block':'none';}
document.getElementById("year").textContent=new Date().getFullYear();

function toggleAccordion(el){
let panel=el.nextElementSibling;
panel.style.display=(panel.style.display==='block')?'none':'block';
}
</script>

</body>
</html>
