# Project1
Hello Everyone
import os, shutil, textwrap, zipfile

base = "/mnt/data/aayush_portfolio"
os.makedirs(base, exist_ok=True)
os.makedirs(os.path.join(base, "static"), exist_ok=True)
os.makedirs(os.path.join(base, "templates"), exist_ok=True)

# Copy the uploaded profile image into the website.
src = "/mnt/data/c2e4e3a9-b99e-4681-9caa-6a04057f4ec4.png"
dst = os.path.join(base, "static", "profile.png")
shutil.copy2(src, dst)

html = r'''<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Aayush Bhatta | Portfolio</title>
  <meta name="description" content="Aayush Bhatta's personal portfolio website.">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
  <div class="cursor-glow"></div>
  <div class="particles" id="particles"></div>

  <header class="navbar">
    <a class="logo" href="#home">AB<span>.</span></a>
    <button class="menu-btn" id="menuBtn" aria-label="Open menu">☰</button>
    <nav id="nav">
      <a href="#home">Home</a>
      <a href="#about">About</a>
      <a href="#skills">Skills</a>
      <a href="#projects">Projects</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="hero-content reveal">
        <p class="eyebrow">WELCOME TO MY PORTFOLIO</p>
        <h1>Hi, I'm <span>Aayush</span><br> a <span id="typing">Student</span><span class="caret">|</span></h1>
        <p class="hero-text">
          I’m a creative student who enjoys building websites, learning technology,
          and turning ideas into beautiful digital experiences.
        </p>
        <div class="hero-buttons">
          <a href="#projects" class="btn primary">View My Work</a>
          <a href="#contact" class="btn secondary">Contact Me</a>
        </div>
        <div class="social-row">
          <a href="#" aria-label="GitHub">GitHub</a>
          <a href="#" aria-label="Instagram">Instagram</a>
          <a href="#" aria-label="LinkedIn">LinkedIn</a>
        </div>
      </div>

      <div class="hero-photo reveal">
        <div class="photo-ring ring-one"></div>
        <div class="photo-ring ring-two"></div>
        <div class="photo-card">
          <img src="{{ url_for('static', filename='profile.png') }}" alt="Aayush">
        </div>
        <div class="floating-card card-top">✨ Creative</div>
        <div class="floating-card card-bottom">💻 Web Developer</div>
      </div>
    </section>

    <section class="section" id="about">
      <div class="section-heading reveal">
        <p class="eyebrow">ABOUT ME</p>
        <h2>A little bit <span>about me</span></h2>
      </div>
      <div class="about-grid">
        <div class="glass-card reveal">
          <h3>Who I Am</h3>
          <p>
            I'm Aayush Bhatta, a student interested in coding, web design and
            technology. I like experimenting with HTML, CSS, JavaScript and Python
            to create useful and attractive projects.
          </p>
        </div>
        <div class="glass-card reveal">
          <h3>My Goal</h3>
          <p>
            My goal is to keep improving my programming skills, build real projects,
            and become a confident developer who can create modern digital products.
          </p>
        </div>
      </div>
    </section>

    <section class="section" id="skills">
      <div class="section-heading reveal">
        <p class="eyebrow">MY SKILLS</p>
        <h2>What I <span>work with</span></h2>
      </div>
      <div class="skills-grid">
        <div class="skill-card reveal"><div class="skill-icon">HTML</div><h3>HTML</h3><p>Clean and structured webpages.</p><div class="bar"><i style="width:90%"></i></div></div>
        <div class="skill-card reveal"><div class="skill-icon">CSS</div><h3>CSS</h3><p>Responsive layouts and animations.</p><div class="bar"><i style="width:85%"></i></div></div>
        <div class="skill-card reveal"><div class="skill-icon">JS</div><h3>JavaScript</h3><p>Interactive and dynamic experiences.</p><div class="bar"><i style="width:75%"></i></div></div>
        <div class="skill-card reveal"><div class="skill-icon">PY</div><h3>Python</h3><p>Beginner-friendly backend projects.</p><div class="bar"><i style="width:70%"></i></div></div>
      </div>
    </section>

    <section class="section" id="projects">
      <div class="section-heading reveal">
        <p class="eyebrow">MY PROJECTS</p>
        <h2>Things I've <span>built</span></h2>
      </div>
      <div class="projects-grid">
        <article class="project-card reveal">
          <div class="project-number">01</div>
          <div class="project-art art-one"><span>&lt;/&gt;</span></div>
          <h3>Personal Portfolio</h3>
          <p>A modern portfolio made with HTML, CSS, JavaScript and Python Flask.</p>
          <div class="tags"><span>HTML</span><span>CSS</span><span>JS</span><span>Python</span></div>
        </article>
        <article class="project-card reveal">
          <div class="project-number">02</div>
          <div class="project-art art-two"><span>🍽️</span></div>
          <h3>Restaurant Website</h3>
          <p>A stylish restaurant concept with animated sections and responsive design.</p>
          <div class="tags"><span>Web</span><span>UI</span><span>Animation</span></div>
        </article>
        <article class="project-card reveal">
          <div class="project-number">03</div>
          <div class="project-art art-three"><span>🚀</span></div>
          <h3>Future Project</h3>
          <p>A space for the next project I create while learning new technologies.</p>
          <div class="tags"><span>Creative</span><span>Learning</span></div>
        </article>
      </div>
    </section>

    <section class="contact section" id="contact">
      <div class="contact-box reveal">
        <p class="eyebrow">GET IN TOUCH</p>
        <h2>Let's build something <span>awesome.</span></h2>
        <p>Have an idea or want to work together? Send me a message.</p>
        <form id="contactForm" action="/contact" method="POST">
          <div class="form-row">
            <input type="text" name="name" placeholder="Your name" required>
            <input type="email" name="email" placeholder="Your email" required>
          </div>
          <textarea name="message" placeholder="Your message..." required></textarea>
          <button class="btn primary" type="submit">Send Message ✦</button>
          <p id="formMessage" class="form-message"></p>
        </form>
      </div>
    </section>
  </main>

  <footer>
    <p>© 2026 Aayush Bhatta. Built with HTML, CSS, JavaScript & Python.</p>
  </footer>

  <script src="{{ url_for('static', filename='script.js') }}"></script>
</body>
</html>
'''

css = r'''*{box-sizing:border-box;margin:0;padding:0}
:root{--bg:#070711;--card:rgba(255,255,255,.07);--text:#f7f7fb;--muted:#a9a9bd;--accent:#8b5cf6;--accent2:#22d3ee}
html{scroll-behavior:smooth}
body{font-family:Inter,Arial,sans-serif;background:radial-gradient(circle at 20% 10%,#1b1237 0,transparent 30%),radial-gradient(circle at 90% 40%,#082c38 0,transparent 28%),var(--bg);color:var(--text);overflow-x:hidden}
body:before{content:"";position:fixed;inset:0;background-image:linear-gradient(rgba(255,255,255,.025) 1px,transparent 1px),linear-gradient(90deg,rgba(255,255,255,.025) 1px,transparent 1px);background-size:50px 50px;pointer-events:none;z-index:-3}
.cursor-glow{position:fixed;width:280px;height:280px;border-radius:50%;background:radial-gradient(circle,rgba(139,92,246,.16),transparent 65%);pointer-events:none;transform:translate(-50%,-50%);z-index:-1}
.particles{position:fixed;inset:0;pointer-events:none;z-index:-2}
.particle{position:absolute;width:3px;height:3px;background:white;border-radius:50%;opacity:.35;animation:float 8s infinite ease-in-out}
@keyframes float{0%,100%{transform:translateY(0);opacity:.2}50%{transform:translateY(-60px);opacity:.8}}
.navbar{position:fixed;top:0;left:0;right:0;height:76px;display:flex;align-items:center;justify-content:space-between;padding:0 7%;background:rgba(7,7,17,.62);backdrop-filter:blur(18px);border-bottom:1px solid rgba(255,255,255,.07);z-index:10}
.logo{font-size:1.8rem;font-weight:800;color:white;text-decoration:none}.logo span{color:var(--accent2)}
nav{display:flex;gap:30px}nav a{color:#d7d7e5;text-decoration:none;font-size:.9rem;transition:.3s}nav a:hover{color:var(--accent2)}
.menu-btn{display:none;background:none;border:0;color:white;font-size:1.6rem}
.hero{min-height:100vh;display:grid;grid-template-columns:1.1fr .9fr;align-items:center;gap:30px;padding:120px 9% 70px;max-width:1400px;margin:auto}
.eyebrow{color:var(--accent2);font-size:.75rem;font-weight:800;letter-spacing:3px;margin-bottom:16px}
h1{font-size:clamp(3rem,7vw,6.3rem);line-height:.98;letter-spacing:-4px}h1 span,h2 span{background:linear-gradient(90deg,var(--accent2),var(--accent),#ec4899);-webkit-background-clip:text;color:transparent}
.hero-text{max-width:600px;color:var(--muted);font-size:1.05rem;line-height:1.8;margin:25px 0}
.caret{color:var(--accent2);background:none;font-size:.8em;animation:blink .7s infinite!important;-webkit-text-fill-color:initial!important}
@keyframes blink{50%{opacity:0}}
.hero-buttons{display:flex;gap:14px;flex-wrap:wrap}.btn{display:inline-block;border:0;border-radius:12px;padding:14px 23px;text-decoration:none;font-weight:700;cursor:pointer;transition:.3s;font-family:inherit}.primary{color:white;background:linear-gradient(135deg,var(--accent),#6366f1);box-shadow:0 10px 30px rgba(124,58,237,.28)}.secondary{color:white;border:1px solid rgba(255,255,255,.15);background:rgba(255,255,255,.04)}.btn:hover{transform:translateY(-4px);box-shadow:0 15px 35px rgba(34,211,238,.15)}
.social-row{display:flex;gap:22px;margin-top:28px}.social-row a{color:#88889e;text-decoration:none;font-size:.85rem}.social-row a:hover{color:white}
.hero-photo{height:550px;display:grid;place-items:center;position:relative}.photo-card{width:min(390px,75vw);aspect-ratio:4/5;border-radius:32px;overflow:hidden;border:1px solid rgba(255,255,255,.18);box-shadow:0 30px 100px rgba(0,0,0,.5);transform:rotate(3deg);position:relative;z-index:2;animation:photoFloat 5s ease-in-out infinite}.photo-card img{width:100%;height:100%;object-fit:cover;display:block}
@keyframes photoFloat{50%{transform:rotate(-2deg) translateY(-12px)}}
.photo-ring{position:absolute;border:1px solid rgba(139,92,246,.35);border-radius:50%;animation:spin 15s linear infinite}.ring-one{width:480px;height:480px}.ring-two{width:550px;height:550px;border-color:rgba(34,211,238,.18);animation-duration:24s;animation-direction:reverse}
@keyframes spin{to{transform:rotate(360deg)}}
.floating-card{position:absolute;z-index:3;padding:13px 17px;border:1px solid rgba(255,255,255,.14);border-radius:13px;background:rgba(16,16,30,.75);backdrop-filter:blur(12px);font-size:.8rem;box-shadow:0 12px 40px rgba(0,0,0,.35)}.card-top{top:16%;right:3%;animation:floatCard 4s infinite}.card-bottom{bottom:14%;left:2%;animation:floatCard 5s .5s infinite}@keyframes floatCard{50%{transform:translateY(-10px)}}
.section{max-width:1200px;margin:auto;padding:110px 7%}.section-heading{text-align:center;margin-bottom:55px}.section-heading h2,.contact h2{font-size:clamp(2.2rem,5vw,4rem);letter-spacing:-2px}
.about-grid,.skills-grid,.projects-grid{display:grid;gap:20px}.about-grid{grid-template-columns:1fr 1fr}.glass-card,.skill-card,.project-card{background:var(--card);border:1px solid rgba(255,255,255,.09);border-radius:22px;padding:30px;backdrop-filter:blur(10px);transition:.4s}.glass-card:hover,.skill-card:hover,.project-card:hover{transform:translateY(-8px);border-color:rgba(139,92,246,.4);background:rgba(255,255,255,.09)}.glass-card h3,.skill-card h3,.project-card h3{margin-bottom:12px}.glass-card p,.skill-card p,.project-card p{color:var(--muted);line-height:1.7}
.skills-grid{grid-template-columns:repeat(4,1fr)}.skill-icon{display:grid;place-items:center;width:58px;height:58px;border-radius:15px;background:linear-gradient(135deg,var(--accent),#0891b2);font-size:.75rem;font-weight:800;margin-bottom:22px}.bar{height:5px;background:rgba(255,255,255,.1);border-radius:10px;margin-top:20px;overflow:hidden}.bar i{display:block;height:100%;background:linear-gradient(90deg,var(--accent2),var(--accent));border-radius:10px}
.projects-grid{grid-template-columns:repeat(3,1fr)}.project-card{position:relative;overflow:hidden}.project-number{position:absolute;right:22px;top:18px;color:rgba(255,255,255,.3);font-weight:800}.project-art{height:180px;border-radius:15px;display:grid;place-items:center;font-size:4rem;margin-bottom:24px;overflow:hidden}.project-art span{filter:drop-shadow(0 0 25px rgba(255,255,255,.3));animation:iconPulse 3s infinite}.art-one{background:linear-gradient(135deg,#17133b,#092c3c)}.art-two{background:linear-gradient(135deg,#3b1631,#39200c)}.art-three{background:linear-gradient(135deg,#092e3b,#19123d)}@keyframes iconPulse{50%{transform:scale(1.12) rotate(3deg)}}
.tags{display:flex;gap:8px;flex-wrap:wrap;margin-top:20px}.tags span{font-size:.7rem;padding:6px 9px;border-radius:7px;background:rgba(255,255,255,.07);color:#c4c4d4}
.contact{padding-bottom:100px}.contact-box{padding:55px;border-radius:30px;text-align:center;background:linear-gradient(135deg,rgba(139,92,246,.15),rgba(34,211,238,.07));border:1px solid rgba(255,255,255,.1)}.contact-box>p:not(.eyebrow){color:var(--muted);margin:15px auto 30px}.contact form{max-width:760px;margin:auto}.form-row{display:grid;grid-template-columns:1fr 1fr;gap:14px}input,textarea{width:100%;border:1px solid rgba(255,255,255,.12);background:rgba(0,0,0,.2);color:white;padding:15px;border-radius:12px;outline:none;font:inherit;margin-bottom:14px}textarea{min-height:140px;resize:vertical}input:focus,textarea:focus{border-color:var(--accent2)}.form-message{margin-top:14px!important;color:var(--accent2)!important}
footer{text-align:center;padding:30px 20px;color:#6f6f82;border-top:1px solid rgba(255,255,255,.06);font-size:.8rem}
.reveal{opacity:0;transform:translateY(35px);transition:opacity .8s ease,transform .8s ease}.reveal.show{opacity:1;transform:translateY(0)}
@media(max-width:900px){.hero{grid-template-columns:1fr;text-align:center}.hero-text{margin-left:auto;margin-right:auto}.hero-buttons,.social-row{justify-content:center}.hero-photo{height:480px}.skills-grid{grid-template-columns:1fr 1fr}.projects-grid{grid-template-columns:1fr}}
@media(max-width:650px){.navbar{padding:0 6%}.menu-btn{display:block}nav{position:absolute;top:76px;left:0;right:0;display:none;flex-direction:column;padding:20px 7%;background:rgba(7,7,17,.96);gap:18px}nav.open{display:flex}.hero{padding-left:6%;padding-right:6%}h1{letter-spacing:-2px}.photo-card{width:290px}.ring-one{width:350px;height:350px}.ring-two{width:400px;height:400px}.about-grid,.skills-grid,.projects-grid,.form-row{grid-template-columns:1fr}.section{padding:80px 6%}.contact-box{padding:35px 20px}}
'''

js = r'''const typing = document.getElementById("typing");
const words = ["Student", "Web Developer", "Designer", "Python Learner"];
let wordIndex = 0, charIndex = 0, deleting = false;

function typeEffect(){
  const word = words[wordIndex];
  typing.textContent = deleting ? word.slice(0, charIndex--) : word.slice(0, charIndex++);
  let speed = deleting ? 55 : 95;
  if(!deleting && charIndex > word.length){ deleting = true; speed = 1200
