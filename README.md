<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Portfolio — Joan Noah</title>

<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,600;0,700;1,300;1,600&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"/>

<style>
/* ─── RESET ─────────────────────────────────────────── */
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}

/* ─── TOKENS ─────────────────────────────────────────── */
:root{
  --bg:        #080a0f;
  --surface:   #0f1218;
  --surface2:  #161b24;
  --border:    rgba(255,255,255,0.07);
  --lime:      #b8ff35;
  --lime-dim:  rgba(184,255,53,0.10);
  --lime-glow: rgba(184,255,53,0.22);
  --white:     #f0f2f5;
  --muted:     #7a8494;
  --faint:     #1e2430;
  --serif:     'Cormorant Garamond', Georgia, serif;
  --sans:      'Syne', sans-serif;
  --ease:      cubic-bezier(0.16,1,0.3,1);
}

body{
  background:var(--bg);
  color:var(--white);
  font-family:var(--sans);
  overflow-x:hidden;
  cursor:none;
}

/* ── Custom cursor ── */
.cursor{
  position:fixed; width:10px; height:10px;
  background:var(--lime); border-radius:50%;
  pointer-events:none; z-index:9999;
  transform:translate(-50%,-50%);
  transition:width .2s var(--ease), height .2s var(--ease);
  mix-blend-mode:difference;
}
.cursor-ring{
  position:fixed; width:36px; height:36px;
  border:1px solid var(--lime); border-radius:50%;
  pointer-events:none; z-index:9998;
  transform:translate(-50%,-50%);
  opacity:.45;
}

::-webkit-scrollbar{width:3px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--lime)}

/* ─── NAV ────────────────────────────────────────────── */
nav{
  position:fixed; top:0; left:0; right:0;
  display:flex; justify-content:space-between; align-items:center;
  padding:1.2rem 4rem;
  background:rgba(8,10,15,0.88);
  backdrop-filter:blur(18px);
  border-bottom:1px solid var(--border);
  z-index:100;
}
.nav-logo{
  font-family:var(--sans); font-weight:800; font-size:1.15rem;
  text-decoration:none; color:var(--white); letter-spacing:.06em;
}
.nav-logo span{color:var(--lime)}
.nav-links{list-style:none; display:flex; gap:2.5rem}
.nav-links a{
  text-decoration:none; font-size:.7rem; letter-spacing:.18em;
  color:var(--muted); text-transform:uppercase; font-weight:700;
  position:relative; transition:color .3s;
}
.nav-links a::after{
  content:''; position:absolute; bottom:-4px; left:0;
  width:0; height:1px; background:var(--lime);
  transition:width .35s var(--ease);
}
.nav-links a:hover{color:var(--white)}
.nav-links a:hover::after{width:100%}

/* ─── HERO ───────────────────────────────────────────── */
#hero{
  min-height:100vh;
  display:grid; grid-template-columns:1fr 1fr;
  align-items:center; padding:0 4rem;
  position:relative; overflow:hidden;
}

/* moving dot grid */
#hero::before{
  content:'';
  position:absolute; inset:0;
  background-image:radial-gradient(rgba(184,255,53,.18) 1px, transparent 1px);
  background-size:36px 36px;
  animation:dotMove 25s linear infinite;
}
@keyframes dotMove{
  0%{background-position:0 0}
  100%{background-position:36px 36px}
}

/* ambient glow */
#hero::after{
  content:'';
  position:absolute; top:10%; left:-5%;
  width:700px; height:700px;
  background:radial-gradient(circle, rgba(184,255,53,.07) 0%, transparent 65%);
  pointer-events:none;
}

.hero-content{position:relative; z-index:1}

.hero-eyebrow{
  display:inline-flex; align-items:center; gap:.7rem;
  font-size:.68rem; letter-spacing:.22em; text-transform:uppercase;
  color:var(--lime); font-weight:700; margin-bottom:1.8rem;
  opacity:0; animation:fadeUp .8s var(--ease) .2s forwards;
}
.hero-eyebrow::before{
  content:''; display:block; width:28px; height:1px; background:var(--lime);
}

.hero-title{
  font-family:var(--serif); font-size:5.5rem; line-height:1;
  font-weight:300; margin-bottom:1.5rem;
  opacity:0; animation:fadeUp .8s var(--ease) .4s forwards;
}
.hero-title strong{
  display:block; font-weight:700; font-style:italic;
  color:var(--lime); font-size:6.5rem;
}

.hero-subtitle{
  max-width:360px; color:var(--muted); line-height:1.85; font-size:.92rem;
  opacity:0; animation:fadeUp .8s var(--ease) .6s forwards;
}

.hero-cta{
  display:inline-flex; align-items:center; gap:.8rem;
  margin-top:2.5rem; padding:.9rem 2.2rem;
  background:var(--lime); color:var(--bg);
  font-weight:800; font-size:.75rem; letter-spacing:.12em; text-transform:uppercase;
  text-decoration:none;
  transition:transform .3s var(--ease), box-shadow .3s var(--ease);
  opacity:0; animation:fadeUp .8s var(--ease) .8s forwards;
}
.hero-cta:hover{
  transform:translateY(-4px);
  box-shadow:0 24px 48px var(--lime-glow);
}

.hero-visual{
  position:relative; z-index:1;
  display:flex; justify-content:center; align-items:center;
  opacity:0; animation:fadeIn 1.2s var(--ease) .5s forwards;
}
.hero-avatar-wrap{position:relative; width:340px; height:340px}

.hero-avatar-wrap::before{
  content:''; position:absolute; inset:-14px;
  border:1px solid var(--lime);
  animation:rotateSlow 14s linear infinite;
}
.hero-avatar-wrap::after{
  content:''; position:absolute; inset:-28px;
  border:1px dashed rgba(184,255,53,.25);
  animation:rotateSlow 20s linear infinite reverse;
}
@keyframes rotateSlow{ to{transform:rotate(360deg)} }

.hero-avatar{
  width:100%; height:100%;
  background:var(--surface2);
  border:1px solid var(--border);
  display:flex; align-items:center; justify-content:center;
  font-size:6.5rem; color:var(--lime);
  position:relative; overflow:hidden;
}
.hero-avatar::after{
  content:''; position:absolute; inset:0;
  background:linear-gradient(135deg,transparent 55%,rgba(184,255,53,.08));
}

.hero-badge{
  position:absolute; bottom:-18px; right:-18px;
  background:var(--lime); color:var(--bg);
  padding:1rem 1.3rem;
  font-size:.62rem; font-weight:800;
  letter-spacing:.14em; text-transform:uppercase; line-height:1.5;
  animation:floatBadge 3s ease-in-out infinite;
}
@keyframes floatBadge{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-10px)}
}

@keyframes fadeUp{
  from{opacity:0;transform:translateY(32px)}
  to{opacity:1;transform:translateY(0)}
}
@keyframes fadeIn{
  from{opacity:0} to{opacity:1}
}

/* ─── SHARED SECTION ─────────────────────────────────── */
section{padding:7rem 4rem}

.section-tag{
  display:inline-flex; align-items:center; gap:.6rem;
  color:var(--lime); letter-spacing:.22em; font-size:.66rem;
  text-transform:uppercase; font-weight:700; margin-bottom:1rem;
}
.section-tag::before{
  content:''; display:block; width:22px; height:1px; background:var(--lime);
}

.section-heading{
  font-family:var(--serif); font-size:3.5rem; font-weight:300;
  line-height:1.1; margin-bottom:3rem;
}
.section-heading em{font-style:italic; color:var(--lime)}

/* ─── ABOUT ──────────────────────────────────────────── */
#about{background:var(--surface)}

.about-grid{
  display:grid; grid-template-columns:1fr 1.4fr;
  gap:5rem; align-items:center;
}

.about-image{
  position:relative; height:420px;
  background:var(--surface2); border:1px solid var(--border);
  display:flex; align-items:center; justify-content:center;
  font-size:5rem; color:var(--lime); overflow:hidden;
}
.about-image::before{
  content:''; position:absolute; bottom:0; left:0; right:0; height:45%;
  background:linear-gradient(to top, rgba(184,255,53,.05), transparent);
}
.img-label{
  position:absolute; bottom:1rem; left:1.2rem;
  font-size:.62rem; letter-spacing:.14em; text-transform:uppercase;
  color:var(--lime); font-weight:700;
}

.about-info p{
  color:var(--muted); line-height:1.9; margin-bottom:1.2rem; font-size:.93rem;
}

.about-stats{
  display:grid; grid-template-columns:repeat(3,1fr);
  gap:1px; margin-top:2.5rem;
  background:var(--border); border:1px solid var(--border);
}
.stat-item{
  background:var(--surface); padding:1.6rem 1rem; text-align:center;
}
.stat-number{
  font-family:var(--serif); font-size:2.6rem; font-weight:700;
  color:var(--lime); display:block; line-height:1;
}
.stat-label{
  font-size:.62rem; text-transform:uppercase; letter-spacing:.14em;
  color:var(--muted); margin-top:.5rem;
}

/* ─── SKILLS ─────────────────────────────────────────── */
#skills{background:var(--bg)}

.skills-grid{
  display:grid; grid-template-columns:repeat(auto-fit,minmax(175px,1fr));
  gap:1px; margin-top:1rem;
  background:var(--border); border:1px solid var(--border);
}
.skill-card{
  background:var(--surface); padding:2.5rem 2rem;
  display:flex; flex-direction:column; align-items:flex-start; gap:1rem;
  position:relative; overflow:hidden;
  transition:background .3s var(--ease);
}
.skill-card::after{
  content:''; position:absolute; bottom:0; left:0; right:0; height:2px;
  background:var(--lime); transform:scaleX(0); transform-origin:left;
  transition:transform .4s var(--ease);
}
.skill-card:hover{background:var(--surface2)}
.skill-card:hover::after{transform:scaleX(1)}
.skill-card:hover .skill-icon{background:var(--lime); color:var(--bg)}

.skill-icon{
  width:50px; height:50px; background:var(--lime-dim);
  display:flex; align-items:center; justify-content:center;
  font-size:1.3rem; color:var(--lime);
  transition:all .3s var(--ease);
}
.skill-name{
  font-size:.75rem; font-weight:700; letter-spacing:.1em;
  text-transform:uppercase; color:var(--white);
}

/* ─── PROJECTS ───────────────────────────────────────── */
#projects{background:var(--surface)}

.projects-list{
  display:grid; grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
  gap:1px; margin-top:1rem;
  background:var(--border); border:1px solid var(--border);
}
.proj-card{
  background:var(--surface); padding:2.5rem;
  position:relative; overflow:hidden;
  transition:background .4s var(--ease);
}
.proj-card::before{
  content:''; position:absolute; top:0; left:0; right:0; height:2px;
  background:linear-gradient(90deg,var(--lime),transparent);
  transform:scaleX(0); transform-origin:left;
  transition:transform .5s var(--ease);
}
.proj-card:hover{background:var(--surface2)}
.proj-card:hover::before{transform:scaleX(1)}

.proj-num{
  font-family:var(--serif); font-size:3.5rem; font-weight:700;
  color:var(--faint); line-height:1; margin-bottom:.8rem;
  transition:color .4s;
}
.proj-card:hover .proj-num{color:rgba(184,255,53,.15)}

.proj-title{
  font-family:var(--serif); font-size:1.55rem; font-weight:600;
  line-height:1.2; margin-bottom:.8rem; color:var(--white);
}
.proj-desc{color:var(--muted); line-height:1.8; font-size:.88rem}

.proj-tags{margin-top:1.5rem; display:flex; flex-wrap:wrap; gap:.5rem}
.proj-tag{
  background:var(--lime-dim); border:1px solid rgba(184,255,53,.22);
  padding:.3rem .75rem; font-size:.62rem; color:var(--lime);
  font-weight:700; letter-spacing:.1em; text-transform:uppercase;
}

/* ─── CONTACT ────────────────────────────────────────── */
#contact{background:var(--bg)}

.contact-grid{
  display:grid; grid-template-columns:1fr 1.2fr;
  gap:5rem; align-items:start; margin-top:1rem;
}
.contact-info p{
  color:var(--muted); line-height:1.9; margin-bottom:2rem; font-size:.92rem;
}
.contact-detail{
  display:flex; align-items:center; gap:1rem;
  margin:.8rem 0; color:var(--white); font-size:.88rem;
}
.contact-detail-icon{
  width:42px; height:42px; background:var(--lime-dim);
  border:1px solid rgba(184,255,53,.2);
  display:flex; align-items:center; justify-content:center;
  color:var(--lime); font-size:.9rem; flex-shrink:0;
}

.form-group{margin-bottom:1.1rem}

.contact-grid input,
.contact-grid textarea{
  width:100%; padding:1rem 1.2rem;
  background:var(--surface); border:1px solid var(--border);
  font-family:var(--sans); font-size:.88rem; color:var(--white);
  outline:none;
  transition:border-color .3s, box-shadow .3s;
}
.contact-grid input::placeholder,
.contact-grid textarea::placeholder{color:var(--muted)}
.contact-grid input:focus,
.contact-grid textarea:focus{
  border-color:var(--lime); box-shadow:0 0 0 3px var(--lime-dim);
}
.contact-grid textarea{height:140px; resize:vertical}

.contact-grid button{
  padding:1rem 2.5rem; background:var(--lime); color:var(--bg);
  border:none; font-family:var(--sans);
  font-size:.75rem; font-weight:800;
  letter-spacing:.12em; text-transform:uppercase; cursor:pointer;
  display:inline-flex; align-items:center; gap:.7rem;
  transition:transform .3s var(--ease), box-shadow .3s var(--ease);
}
.contact-grid button:hover{
  transform:translateY(-4px);
  box-shadow:0 20px 44px var(--lime-glow);
}

#form-status{
  margin-top:.8rem; font-size:.78rem;
  color:var(--lime); letter-spacing:.05em;
}

/* ─── FOOTER ─────────────────────────────────────────── */
footer{
  background:var(--surface); color:var(--muted);
  padding:2rem 4rem;
  display:flex; justify-content:space-between; align-items:center;
  border-top:1px solid var(--border);
  font-size:.75rem; letter-spacing:.06em;
}
.social-icons{display:flex; gap:.8rem}
.social-icons a{
  width:38px; height:38px; border:1px solid var(--border);
  display:flex; align-items:center; justify-content:center;
  color:var(--muted); font-size:.85rem; text-decoration:none;
  transition:all .3s var(--ease);
}
.social-icons a:hover{
  border-color:var(--lime); color:var(--lime); background:var(--lime-dim);
}

/* ─── SCROLL REVEAL ──────────────────────────────────── */
.reveal{
  opacity:0; transform:translateY(40px);
  transition:opacity .85s var(--ease), transform .85s var(--ease);
}
.reveal.visible{opacity:1; transform:none}

.reveal-group > *{
  opacity:0; transform:translateY(30px);
  transition:opacity .6s var(--ease), transform .6s var(--ease);
}
.reveal-group.visible > *:nth-child(1){opacity:1;transform:none;transition-delay:.0s}
.reveal-group.visible > *:nth-child(2){opacity:1;transform:none;transition-delay:.1s}
.reveal-group.visible > *:nth-child(3){opacity:1;transform:none;transition-delay:.2s}
.reveal-group.visible > *:nth-child(4){opacity:1;transform:none;transition-delay:.3s}
.reveal-group.visible > *:nth-child(5){opacity:1;transform:none;transition-delay:.4s}

/* ─── GRAIN TEXTURE ──────────────────────────────────── */
body::before{
  content:''; position:fixed; inset:0; pointer-events:none; z-index:9997;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  opacity:.016;
}
</style>
</head>

<body>

<!-- CURSOR -->
<div class="cursor"      id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <a href="#hero" class="nav-logo">JN<span>.</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-content">
    <p class="hero-eyebrow">MCA Student &amp; Data Analyst</p>
    <h1 class="hero-title">
      Hi, I'm
      <strong>Joan Noah</strong>
    </h1>
    <p class="hero-subtitle">
      MCA student bridging business strategy and technology through data management, visualization, and analytical solutions.
    </p>
    <div style="display:flex;gap:1rem;flex-wrap:wrap;align-items:center;">
      <a href="#projects" class="hero-cta">
        View My Work <i class="fas fa-arrow-right"></i>
      </a>
      <a href="c:\Users\Joan Noah\Downloads\noah mca data analyst resume.pdf" download="Joan_Noah_Resume.pdf" class="hero-cta" style="background:transparent;color:var(--lime);border:1px solid var(--lime);">
        Resume <i class="fas fa-download"></i>
      </a>
    </div>
  </div>

 
</section>

<!-- ABOUT -->
<section id="about">
  <p class="section-tag">About</p>
  <h2 class="section-heading reveal">About <em>Me</em></h2>

  

    <div class="about-info reveal">
      <p>I am a Master of Computer Applications (MCA) student at SRM University, Chennai, with a B.Com background (CGPA 8.90). I bridge business strategy and technological solutions with an innovative, analytical mindset.</p>
      <p>My interests span data management, visualization tools (Power BI, Tableau), programming in Java and Python, and delivering data-driven solutions in dynamic environments.</p>

      <div class="about-stats reveal-group">
        <div class="stat-item"><span class="stat-number">4+</span><span class="stat-label">Projects</span></div>
        <div class="stat-item"><span class="stat-number">8+</span><span class="stat-label">Technologies</span></div>
        <div class="stat-item"><span class="stat-number">4+</span><span class="stat-label">Certifications</span></div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <p class="section-tag">Skills</p>
  <h2 class="section-heading reveal">Technologies <em>I Use</em></h2>

  <div class="skills-grid reveal-group">
    <div class="skill-card">
      <div class="skill-icon"><i class="fab fa-java"></i></div>
      <span class="skill-name">Java Programming</span>
    </div>
    <div class="skill-card">
      <div class="skill-icon"><i class="fab fa-python"></i></div>
      <span class="skill-name">Python</span>
    </div>
    <div class="skill-card">
      <div class="skill-icon"><i class="fas fa-database"></i></div>
      <span class="skill-name">SQL</span>
    </div>
    <div class="skill-card">
      <div class="skill-icon"><i class="fas fa-leaf"></i></div>
      <span class="skill-name">MongoDB</span>
    </div>
    <div class="skill-card">
      <div class="skill-icon"><i class="fas fa-chart-bar"></i></div>
      <span class="skill-name">Power BI</span>
    </div>
    <div class="skill-card">
      <div class="skill-icon"><i class="fas fa-chart-line"></i></div>
      <span class="skill-name">Tableau</span>
    </div>
    <div class="skill-card">
      <div class="skill-icon"><i class="fas fa-file-excel"></i></div>
      <span class="skill-name">MS Excel</span>
    </div>
    <div class="skill-card">
      <div class="skill-icon"><i class="fab fa-html5"></i></div>
      <span class="skill-name">HTML &amp; CSS</span>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <p class="section-tag">Work</p>
  <h2 class="section-heading reveal">Selected <em>Projects</em></h2>

  <div class="projects-list reveal-group">
    <div class="proj-card">
      <div class="proj-num">01</div>
      <h3 class="proj-title">IoT Monitoring Dashboard</h3>
      <p class="proj-desc">Designed an interactive, real-time dashboard using data visualization tools from connected devices and sensors in manufacturing and smart building environments.</p>
      <div class="proj-tags">
        <span class="proj-tag">Data Visualization</span>
        <span class="proj-tag">IoT</span>
        <span class="proj-tag">Real-Time</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-num">02</div>
      <h3 class="proj-title">Sales Data Dashboard</h3>
      <p class="proj-desc">Developed an interactive dashboard using Power BI and Tableau for visualizing sales insights and performance trends across business units.</p>
      <div class="proj-tags">
        <span class="proj-tag">Power BI</span>
        <span class="proj-tag">Tableau</span>
        <span class="proj-tag">Data Analytics</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-num">03</div>
      <h3 class="proj-title">Healthcare Access Case Study</h3>
      <p class="proj-desc">Conducted data-driven research and proposed IT-enabled solutions for improving healthcare accessibility for low-income families in India.</p>
      <div class="proj-tags">
        <span class="proj-tag">Research</span>
        <span class="proj-tag">Data Analysis</span>
        <span class="proj-tag">IT Solutions</span>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <p class="section-tag">Contact</p>
  <h2 class="section-heading reveal">Get In <em>Touch</em></h2>

  <div class="contact-grid reveal">
    <div class="contact-info">
      <p>If you would like to collaborate or discuss projects, feel free to contact me.</p>
      <div class="contact-detail">
        <div class="contact-detail-icon"><i class="fas fa-phone"></i></div>
        +91-9677222196
      </div>
      <div class="contact-detail">
        <div class="contact-detail-icon"><i class="fas fa-envelope"></i></div>
        joannoah11@gmail.com
      </div>
      <div class="contact-detail">
        <div class="contact-detail-icon"><i class="fas fa-map-marker-alt"></i></div>
        Tamil Nadu, India
      </div>
      <div class="contact-detail">
        
    </div>

    <div>
      <form id="contact-form" onsubmit="sendMail(); return false;">
        <div class="form-group">
          <input type="text" id="name" placeholder="Your Name" required />
        </div>
        <div class="form-group">
          <input type="email" id="email" placeholder="Email Address" required />
        </div>
        <div class="form-group">
          <textarea id="message" placeholder="Your Message" required></textarea>
        </div>
        <button type="submit">Send Message <i class="fas fa-paper-plane"></i></button>
      </form>
      <p id="form-status"></p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p>© 2026 Joan Noah — Built with passion.</p>
  <div class="social-icons">
    <a href="https://github.com/joannoah11-afk" target="_blank" rel="noopener noreferrer"><i class="fab fa-github"></i></a>
    <a href="https://linkedin.com/in/joannoah-dataanalyst" target="_blank" rel="noopener noreferrer"><i class="fab fa-linkedin"></i></a>
  </div>
</footer>

<!-- EmailJS -->
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>

<script>
  /* ── EmailJS ── */
  (function(){
    emailjs.init({ publicKey: "sRbpdvF3xRpIHLFZL" });
  })();

  function sendMail() {
    var status = document.getElementById('form-status');
    var abc = {
      name:    document.getElementById("name").value,
      email:   document.getElementById("email").value,
      message: document.getElementById("message").value,
    };
    status.textContent = 'Sending…';
   emailjs.send("service_zgsdp8n", "template_2z2wtkw", abc)
  .then(function() {
    document.getElementById('contact-form').reset();
    status.textContent = 'Message sent successfully! ✓';
    setTimeout(function() { status.textContent = ''; }, 4000);
  }, function(error) {
    status.textContent = 'Failed to send. Please try again.';
    setTimeout(function() { status.textContent = ''; }, 4000);
    console.error('EmailJS error:', error);
  });
  }

  /* ── Custom cursor ── */
  const cursor = document.getElementById('cursor');
  const ring   = document.getElementById('cursorRing');
  let rx=0, ry=0, cx=0, cy=0;

  document.addEventListener('mousemove', e => {
    cx = e.clientX; cy = e.clientY;
    cursor.style.left = cx+'px';
    cursor.style.top  = cy+'px';
  });

  (function animRing(){
    rx += (cx-rx)*0.1;
    ry += (cy-ry)*0.1;
    ring.style.left = rx+'px';
    ring.style.top  = ry+'px';
    requestAnimationFrame(animRing);
  })();

  document.querySelectorAll('a,button,.skill-card,.proj-card').forEach(el=>{
    el.addEventListener('mouseenter',()=>{
      cursor.style.width='18px'; cursor.style.height='18px';
      ring.style.width='54px';   ring.style.height='54px';
      ring.style.opacity='0.8';
    });
    el.addEventListener('mouseleave',()=>{
      cursor.style.width='10px'; cursor.style.height='10px';
      ring.style.width='36px';   ring.style.height='36px';
      ring.style.opacity='0.45';
    });
  });

  /* ── Scroll reveal ── */
  const obs = new IntersectionObserver(entries=>{
    entries.forEach(e=>{
      if(e.isIntersecting){ e.target.classList.add('visible'); obs.unobserve(e.target); }
    });
  },{ threshold:0.1 });

  document.querySelectorAll('.reveal,.reveal-group').forEach(el=>obs.observe(el));
</script>

<script src="script.js"></script>
</body>
</html>
