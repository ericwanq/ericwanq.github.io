<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Eric — Marketing Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
:root {
  --bg: #f8f6f1;
  --ink: #141210;
  --mid: #6b6560;
  --soft: #e8e3da;
  --line: rgba(20,18,16,0.1);
  --pop: #d4522a;
  --pop-light: #faeee9;
}
*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior: smooth; }
body {
  background: var(--bg);
  color: var(--ink);
  font-family: 'DM Sans', sans-serif;
  font-weight: 300;
  overflow-x: hidden;
  cursor: none;
}
.cursor {
  position: fixed; width: 10px; height: 10px;
  background: var(--pop); border-radius: 50%;
  pointer-events: none; z-index: 9999;
  transform: translate(-50%,-50%);
  transition: width .2s, height .2s;
}
.cursor-trail {
  position: fixed; width: 36px; height: 36px;
  border: 1.5px solid var(--ink); border-radius: 50%;
  pointer-events: none; z-index: 9998;
  transform: translate(-50%,-50%);
  opacity: 0.3;
  transition: width .3s, height .3s, opacity .3s;
}

/* NAV */
nav {
  position: fixed; top:0; left:0; right:0; z-index:100;
  display: flex; justify-content: space-between; align-items: center;
  padding: 24px 52px;
  transition: background .3s, border-color .3s;
}
nav.scrolled {
  background: rgba(248,246,241,0.92);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--line);
}
.nav-logo {
  font-family: 'Syne', sans-serif;
  font-size: 18px; font-weight: 700;
  letter-spacing: 0.04em;
  color: var(--ink); text-decoration: none;
}
.nav-logo span { color: var(--pop); }
.nav-right { display: flex; align-items: center; gap: 40px; }
.nav-links { display: flex; gap: 32px; list-style: none; }
.nav-links a {
  font-size: 12px; font-weight: 400;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: var(--mid); text-decoration: none;
  transition: color .2s; cursor: none;
}
.nav-links a:hover { color: var(--ink); }
.nav-hire {
  font-size: 11px; font-weight: 500;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: var(--bg); background: var(--ink);
  padding: 10px 22px; border-radius: 2px;
  text-decoration: none; cursor: none;
  transition: background .25s;
}
.nav-hire:hover { background: var(--pop); }

/* PAGES */
.page { display: none; }
.page.active { display: block; }

/* ======= HOME ======= */
.hero {
  min-height: 100vh;
  padding: 140px 52px 80px;
  display: grid;
  grid-template-columns: 1fr 420px;
  gap: 40px;
  align-items: end;
}
.hero-left { padding-bottom: 20px; }
.hero-status {
  display: inline-flex; align-items: center; gap: 8px;
  background: var(--pop-light);
  border: 1px solid rgba(212,82,42,0.2);
  padding: 6px 14px; border-radius: 20px;
  font-size: 11px; font-weight: 500;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: var(--pop); margin-bottom: 36px;
  opacity: 0; animation: up .7s ease forwards .1s;
}
.status-dot {
  width: 6px; height: 6px;
  background: var(--pop); border-radius: 50%;
  animation: pulse 2s ease infinite;
}
@keyframes pulse {
  0%,100% { opacity:1; transform:scale(1); }
  50% { opacity:0.5; transform:scale(1.4); }
}
.hero-h1 {
  font-family: 'Syne', sans-serif;
  font-size: clamp(58px, 7.5vw, 108px);
  font-weight: 800; line-height: 0.9;
  letter-spacing: -0.03em;
  margin-bottom: 36px;
  opacity: 0; animation: up .8s ease forwards .25s;
}
.hero-h1 .line2 {
  font-family: 'Libre Baskerville', serif;
  font-weight: 400; font-style: italic;
  color: var(--pop);
}
.hero-sub {
  font-size: 16px; font-weight: 300;
  line-height: 1.8; color: var(--mid);
  max-width: 520px; margin-bottom: 48px;
  opacity: 0; animation: up .8s ease forwards .4s;
}
.hero-actions {
  display: flex; align-items: center; gap: 24px;
  opacity: 0; animation: up .8s ease forwards .55s;
}
.btn-primary {
  display: inline-flex; align-items: center; gap: 10px;
  background: var(--ink); color: var(--bg);
  padding: 15px 30px; border-radius: 2px;
  font-size: 12px; font-weight: 500;
  letter-spacing: 0.15em; text-transform: uppercase;
  text-decoration: none; cursor: none;
  transition: background .25s, gap .25s;
}
.btn-primary:hover { background: var(--pop); gap: 16px; }
.btn-ghost {
  font-size: 12px; font-weight: 400;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: var(--mid); text-decoration: none; cursor: none;
  border-bottom: 1px solid var(--line);
  padding-bottom: 2px;
  transition: color .2s, border-color .2s;
}
.btn-ghost:hover { color: var(--ink); border-color: var(--ink); }

.hero-right {
  opacity: 0; animation: fadeIn .9s ease forwards .5s;
}
.hero-card {
  background: var(--ink); color: var(--bg);
  border-radius: 8px; padding: 32px;
  margin-bottom: 16px;
}
.hero-card-label {
  font-size: 10px; font-weight: 500;
  letter-spacing: 0.25em; text-transform: uppercase;
  color: rgba(248,246,241,0.4);
  margin-bottom: 20px;
}
.hero-card-disciplines { display: flex; flex-wrap: wrap; gap: 8px; }
.disc-tag {
  font-size: 12px; font-weight: 400;
  letter-spacing: 0.08em;
  background: rgba(255,255,255,0.08);
  padding: 6px 14px; border-radius: 20px;
  border: 1px solid rgba(255,255,255,0.1);
}
.disc-tag.hot { background: var(--pop); border-color: var(--pop); }
.hero-mini-stats {
  display: grid; grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.mini-stat {
  background: var(--soft); border-radius: 6px;
  padding: 18px 20px;
}
.mini-stat-n {
  font-family: 'Syne', sans-serif;
  font-size: 28px; font-weight: 700;
  color: var(--ink); line-height: 1;
  margin-bottom: 4px;
}
.mini-stat-l {
  font-size: 10px; font-weight: 400;
  letter-spacing: 0.18em; text-transform: uppercase;
  color: var(--mid);
}

/* WORK SECTION */
.work-section { padding: 100px 52px; }
.section-head {
  display: flex; justify-content: space-between;
  align-items: baseline; margin-bottom: 56px;
  padding-bottom: 18px; border-bottom: 1px solid var(--line);
}
.section-title {
  font-family: 'Syne', sans-serif;
  font-size: 36px; font-weight: 700;
  letter-spacing: -0.02em;
}
.section-sub {
  font-size: 12px; font-weight: 400;
  letter-spacing: 0.15em; text-transform: uppercase;
  color: var(--mid);
}

.projects-list { display: flex; flex-direction: column; gap: 1px; background: var(--line); border: 1px solid var(--line); border-radius: 6px; overflow: hidden; }
.project-row {
  background: var(--bg);
  display: grid;
  grid-template-columns: 60px 1fr auto auto;
  align-items: center;
  gap: 24px;
  padding: 28px 32px;
  transition: background .2s, padding-left .25s;
  cursor: none;
}
.project-row:hover { background: var(--soft); padding-left: 44px; }
.proj-num {
  font-family: 'Syne', sans-serif;
  font-size: 13px; font-weight: 700;
  color: var(--pop); letter-spacing: 0.05em;
}
.proj-main {}
.proj-title {
  font-family: 'Syne', sans-serif;
  font-size: 20px; font-weight: 600;
  letter-spacing: -0.01em; margin-bottom: 5px;
}
.proj-desc {
  font-size: 13px; color: var(--mid);
  line-height: 1.5; max-width: 480px;
}
.proj-tags { display: flex; gap: 6px; flex-wrap: wrap; justify-content: flex-end; }
.proj-tag {
  font-size: 10px; font-weight: 500;
  letter-spacing: 0.12em; text-transform: uppercase;
  padding: 4px 10px; border-radius: 20px;
  background: var(--soft); color: var(--mid);
  border: 1px solid var(--line);
}
.proj-tag.featured { background: var(--pop-light); color: var(--pop); border-color: rgba(212,82,42,.2); }
.proj-arrow {
  font-size: 18px; color: var(--mid);
  transition: transform .25s, color .2s;
}
.project-row:hover .proj-arrow { transform: translate(4px,-4px); color: var(--pop); }

/* SKILLS ROW */
.skills-band {
  margin: 0 52px 100px;
  border: 1px solid var(--line);
  border-radius: 6px;
  padding: 40px 48px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 32px;
}
.skill-col-title {
  font-size: 10px; font-weight: 500;
  letter-spacing: 0.25em; text-transform: uppercase;
  color: var(--pop); margin-bottom: 16px;
}
.skill-item {
  display: flex; align-items: center; gap: 8px;
  font-size: 13px; font-weight: 300;
  color: var(--mid); margin-bottom: 10px;
}
.skill-dot { width: 4px; height: 4px; background: var(--line); border-radius: 50%; flex-shrink: 0; }

/* ======= ABOUT ======= */
.about-hero {
  padding: 140px 52px 80px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  min-height: 100vh;
  align-items: center;
  border-bottom: 1px solid var(--line);
}
.about-eyebrow {
  font-size: 10px; font-weight: 500;
  letter-spacing: 0.3em; text-transform: uppercase;
  color: var(--pop); margin-bottom: 24px;
}
.about-h {
  font-family: 'Syne', sans-serif;
  font-size: clamp(42px, 4.5vw, 62px);
  font-weight: 800; line-height: 1.0;
  letter-spacing: -0.025em;
  margin-bottom: 32px;
}
.about-h em {
  font-family: 'Libre Baskerville', serif;
  font-weight: 400; font-style: italic;
  color: var(--pop);
}
.about-p {
  font-size: 15px; font-weight: 300;
  line-height: 1.85; color: var(--mid);
  margin-bottom: 18px;
}
.about-edu {
  margin-top: 40px; padding-top: 32px;
  border-top: 1px solid var(--line);
}
.edu-label {
  font-size: 10px; font-weight: 500;
  letter-spacing: 0.25em; text-transform: uppercase;
  color: var(--mid); margin-bottom: 16px;
}
.edu-row {
  display: flex; justify-content: space-between;
  align-items: baseline;
}
.edu-degree {
  font-family: 'Syne', sans-serif;
  font-size: 18px; font-weight: 600;
}
.edu-year {
  font-size: 12px; color: var(--mid);
  font-style: italic;
}
.edu-school {
  font-size: 13px; color: var(--mid); margin-top: 3px;
}

.about-right-col { display: flex; flex-direction: column; gap: 20px; }
.about-photo-placeholder {
  width: 100%; aspect-ratio: 4/5;
  background: var(--soft);
  border-radius: 6px;
  display: flex; align-items: center; justify-content: center;
  font-family: 'Syne', sans-serif;
  font-size: 80px; font-weight: 800;
  color: var(--line);
  position: relative; overflow: hidden;
}
.about-photo-placeholder::before {
  content: 'E';
  position: absolute;
  font-size: 220px;
  color: rgba(20,18,16,0.04);
  font-weight: 800;
}
.about-tools {
  background: var(--ink); border-radius: 6px;
  padding: 24px 28px;
}
.tools-label {
  font-size: 10px; font-weight: 500;
  letter-spacing: 0.25em; text-transform: uppercase;
  color: rgba(248,246,241,0.35);
  margin-bottom: 14px;
}
.tools-grid { display: flex; flex-wrap: wrap; gap: 8px; }
.tool-chip {
  font-size: 11px; font-weight: 400;
  padding: 5px 12px; border-radius: 20px;
  background: rgba(255,255,255,0.07);
  border: 1px solid rgba(255,255,255,0.1);
  color: rgba(248,246,241,0.7);
}

/* ======= CONTACT ======= */
.contact-hero {
  padding: 140px 52px 80px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  min-height: 100vh;
  align-items: center;
}
.contact-h {
  font-family: 'Syne', sans-serif;
  font-size: clamp(44px, 5vw, 68px);
  font-weight: 800; line-height: 0.95;
  letter-spacing: -0.03em;
  margin-bottom: 24px;
}
.contact-h em {
  font-family: 'Libre Baskerville', serif;
  font-weight: 400; font-style: italic;
  color: var(--pop);
}
.contact-p {
  font-size: 15px; font-weight: 300;
  line-height: 1.8; color: var(--mid);
  max-width: 400px; margin-bottom: 48px;
}
.contact-item {
  display: flex; align-items: center;
  justify-content: space-between;
  padding: 22px 0;
  border-bottom: 1px solid var(--line);
  text-decoration: none; color: var(--ink);
  cursor: none;
  transition: padding-left .25s;
}
.contact-item:hover { padding-left: 10px; }
.c-label {
  font-size: 10px; font-weight: 500;
  letter-spacing: 0.2em; text-transform: uppercase;
  color: var(--mid); margin-bottom: 4px;
}
.c-value {
  font-family: 'Syne', sans-serif;
  font-size: 18px; font-weight: 600;
}
.c-arrow {
  font-size: 20px; color: var(--mid);
  transition: transform .25s, color .2s;
}
.contact-item:hover .c-arrow { transform: translate(4px,-4px); color: var(--pop); }

.contact-form-wrap { background: var(--soft); border-radius: 8px; padding: 40px; }
.form-title {
  font-family: 'Syne', sans-serif;
  font-size: 20px; font-weight: 700;
  margin-bottom: 28px;
}
.fg { margin-bottom: 22px; }
.fl {
  display: block; font-size: 10px; font-weight: 500;
  letter-spacing: 0.22em; text-transform: uppercase;
  color: var(--mid); margin-bottom: 8px;
}
.fi, .ft, .fs {
  width: 100%; background: var(--bg);
  border: 1px solid var(--line);
  border-radius: 4px; padding: 12px 16px;
  font-family: 'DM Sans', sans-serif;
  font-size: 14px; font-weight: 300;
  color: var(--ink); outline: none;
  transition: border-color .25s; cursor: none;
}
.fi:focus, .ft:focus, .fs:focus { border-color: var(--pop); }
.ft { resize: none; height: 110px; }
.fs { appearance: none; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.submit-btn {
  width: 100%; background: var(--ink); color: var(--bg);
  border: none; border-radius: 4px;
  padding: 15px; margin-top: 8px;
  font-family: 'Syne', sans-serif;
  font-size: 12px; font-weight: 700;
  letter-spacing: 0.2em; text-transform: uppercase;
  cursor: none; transition: background .25s;
  display: flex; align-items: center; justify-content: center; gap: 10px;
}
.submit-btn:hover { background: var(--pop); }

/* FOOTER */
footer {
  border-top: 1px solid var(--line);
  padding: 28px 52px;
  display: flex; justify-content: space-between; align-items: center;
}
.footer-name {
  font-family: 'Syne', sans-serif;
  font-size: 13px; font-weight: 700;
  letter-spacing: 0.05em;
}
.footer-name span { color: var(--pop); }
.footer-r { display: flex; align-items: center; gap: 28px; }
.footer-link {
  font-size: 11px; letter-spacing: 0.12em;
  text-transform: uppercase; color: var(--mid);
  text-decoration: none; cursor: none;
  transition: color .2s;
}
.footer-link:hover { color: var(--ink); }

/* ANIMATIONS */
@keyframes up {
  from { opacity:0; transform:translateY(20px); }
  to { opacity:1; transform:translateY(0); }
}
@keyframes fadeIn {
  from { opacity:0; }
  to { opacity:1; }
}
.reveal { opacity:0; transform:translateY(18px); transition: opacity .6s ease, transform .6s ease; }
.reveal.visible { opacity:1; transform:none; }

@media(max-width:768px){
  nav { padding: 20px 24px; }
  .nav-right { gap: 20px; }
  .nav-links { display: none; }
  .hero, .about-hero, .contact-hero { grid-template-columns:1fr; padding: 120px 24px 60px; gap: 40px; }
  .work-section, .skills-band { padding: 70px 24px; margin: 0; }
  .skills-band { grid-template-columns: 1fr 1fr; }
  .project-row { grid-template-columns: 40px 1fr; padding: 22px 20px; }
  .proj-tags, .proj-arrow { display: none; }
  footer { padding: 24px; flex-direction: column; gap: 16px; }
  body { cursor: auto; }
  .cursor, .cursor-trail { display: none; }
}
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-trail" id="trail"></div>

<nav id="nav">
  <a class="nav-logo" href="#" onclick="show('home');return false;">Eric<span>.</span></a>
  <div class="nav-right">
    <ul class="nav-links">
      <li><a href="#" onclick="show('home');return false;">Work</a></li>
      <li><a href="#" onclick="show('about');return false;">About</a></li>
      <li><a href="#" onclick="show('contact');return false;">Contact</a></li>
    </ul>
    <a class="nav-hire" href="#" onclick="show('contact');return false;">Hire Me</a>
  </div>
</nav>

<!-- ======= HOME ======= -->
<div class="page active" id="page-home">
  <section class="hero">
    <div class="hero-left">
      <div class="hero-status">
        <div class="status-dot"></div>
        Open to full-time roles
      </div>
      <h1 class="hero-h1">
        Marketing<br/>
        <span class="line2">that moves</span><br/>
        people.
      </h1>
      <p class="hero-sub">Hi, I'm Eric — a marketing graduate with a passion for brand storytelling, campaign strategy, and content that actually connects. Here's a selection of my best work.</p>
      <div class="hero-actions">
        <a class="btn-primary" href="#" onclick="document.querySelector('.work-section').scrollIntoView({behavior:'smooth'});return false;">See My Work →</a>
        <a class="btn-ghost" href="#" onclick="show('contact');return false;">Get in Touch</a>
      </div>
    </div>
    <div class="hero-right">
      <div class="hero-card">
        <div class="hero-card-label">Disciplines</div>
        <div class="hero-card-disciplines">
          <span class="disc-tag hot">Brand Strategy</span>
          <span class="disc-tag hot">Campaigns</span>
          <span class="disc-tag">Social Media</span>
          <span class="disc-tag">Content</span>
          <span class="disc-tag">Market Research</span>
          <span class="disc-tag">Copywriting</span>
          <span class="disc-tag">Analytics</span>
          <span class="disc-tag">SEO</span>
        </div>
      </div>
      <div class="hero-mini-stats">
        <div class="mini-stat">
          <div class="mini-stat-n">8+</div>
          <div class="mini-stat-l">Projects</div>
        </div>
        <div class="mini-stat">
          <div class="mini-stat-n">B.S.</div>
          <div class="mini-stat-l">Marketing</div>
        </div>
        <div class="mini-stat">
          <div class="mini-stat-n">3</div>
          <div class="mini-stat-l">Internships</div>
        </div>
        <div class="mini-stat">
          <div class="mini-stat-n">2025</div>
          <div class="mini-stat-l">Grad Year</div>
        </div>
      </div>
    </div>
  </section>

  <section class="work-section">
    <div class="section-head reveal">
      <h2 class="section-title">Selected Work</h2>
      <span class="section-sub">8 Projects</span>
    </div>
    <div class="projects-list">
      <div class="project-row reveal">
        <div class="proj-num">01</div>
        <div class="proj-main">
          <div class="proj-title">Rebrand Campaign — Student-Run Agency</div>
          <div class="proj-desc">End-to-end brand refresh for a local nonprofit, including new positioning, visual identity guidelines, and a launch campaign across digital channels.</div>
        </div>
        <div class="proj-tags">
          <span class="proj-tag featured">Featured</span>
          <span class="proj-tag">Branding</span>
          <span class="proj-tag">Strategy</span>
        </div>
        <div class="proj-arrow">↗</div>
      </div>
      <div class="project-row reveal" style="transition-delay:.05s">
        <div class="proj-num">02</div>
        <div class="proj-main">
          <div class="proj-title">Social Media Growth Strategy</div>
          <div class="proj-desc">Developed a 3-month content calendar and growth playbook for a campus food brand. Resulted in 2.4× follower increase and 40% engagement lift in class simulation.</div>
        </div>
        <div class="proj-tags">
          <span class="proj-tag featured">Featured</span>
          <span class="proj-tag">Social Media</span>
          <span class="proj-tag">Content</span>
        </div>
        <div class="proj-arrow">↗</div>
      </div>
      <div class="project-row reveal" style="transition-delay:.1s">
        <div class="proj-num">03</div>
        <div class="proj-main">
          <div class="proj-title">Consumer Behavior Research Study</div>
          <div class="proj-desc">Led a team of 4 conducting a mixed-methods study on Gen Z purchasing habits in the sustainable fashion space. Presented findings and strategic recommendations to a panel.</div>
        </div>
        <div class="proj-tags">
          <span class="proj-tag">Research</span>
          <span class="proj-tag">Analytics</span>
        </div>
        <div class="proj-arrow">↗</div>
      </div>
      <div class="project-row reveal" style="transition-delay:.15s">
        <div class="proj-num">04</div>
        <div class="proj-main">
          <div class="proj-title">Integrated Marketing Plan — Capstone</div>
          <div class="proj-desc">360-degree marketing plan for a real-world client brief, covering market analysis, target segmentation, channel mix, budget allocation, and KPIs.</div>
        </div>
        <div class="proj-tags">
          <span class="proj-tag featured">Capstone</span>
          <span class="proj-tag">IMC</span>
          <span class="proj-tag">Strategy</span>
        </div>
        <div class="proj-arrow">↗</div>
      </div>
      <div class="project-row reveal" style="transition-delay:.2s">
        <div class="proj-num">05</div>
        <div class="proj-main">
          <div class="proj-title">Email Campaign — Internship Project</div>
          <div class="proj-desc">Wrote and designed a 5-part nurture email sequence for a B2B SaaS company during my summer internship. A/B tested subject lines; achieved 34% open rate.</div>
        </div>
        <div class="proj-tags">
          <span class="proj-tag">Email</span>
          <span class="proj-tag">Copywriting</span>
        </div>
        <div class="proj-arrow">↗</div>
      </div>
      <div class="project-row reveal" style="transition-delay:.25s">
        <div class="proj-num">06</div>
        <div class="proj-main">
          <div class="proj-title">SEO Content Strategy</div>
          <div class="proj-desc">Audited and rebuilt the content strategy for a lifestyle blog, performing keyword research, on-page SEO, and publishing 12 optimized articles over one semester.</div>
        </div>
        <div class="proj-tags">
          <span class="proj-tag">SEO</span>
          <span class="proj-tag">Content</span>
        </div>
        <div class="proj-arrow">↗</div>
      </div>
      <div class="project-row reveal" style="transition-delay:.3s">
        <div class="proj-num">07</div>
        <div class="proj-main">
          <div class="proj-title">Paid Social Ad Campaign</div>
          <div class="proj-desc">Designed and managed a $500 Meta ads simulation for a course project, including audience targeting, creative testing, and performance reporting with ROAS analysis.</div>
        </div>
        <div class="proj-tags">
          <span class="proj-tag">Paid Social</span>
          <span class="proj-tag">Analytics</span>
        </div>
        <div class="proj-arrow">↗</div>
      </div>
      <div class="project-row reveal" style="transition-delay:.35s">
        <div class="proj-num">08</div>
        <div class="proj-main">
          <div class="proj-title">Brand Voice & Messaging Guide</div>
          <div class="proj-desc">Created a comprehensive brand voice document for a student organization, defining tone, audience personas, and messaging pillars used across all communications.</div>
        </div>
        <div class="proj-tags">
          <span class="proj-tag">Branding</span>
          <span class="proj-tag">Copywriting</span>
        </div>
        <div class="proj-arrow">↗</div>
      </div>
    </div>
  </section>

  <div class="skills-band reveal">
    <div>
      <div class="skill-col-title">Strategy</div>
      <div class="skill-item"><div class="skill-dot"></div>Brand positioning</div>
      <div class="skill-item"><div class="skill-dot"></div>Market research</div>
      <div class="skill-item"><div class="skill-dot"></div>Competitive analysis</div>
      <div class="skill-item"><div class="skill-dot"></div>Campaign planning</div>
    </div>
    <div>
      <div class="skill-col-title">Content</div>
      <div class="skill-item"><div class="skill-dot"></div>Copywriting</div>
      <div class="skill-item"><div class="skill-dot"></div>Social media</div>
      <div class="skill-item"><div class="skill-dot"></div>Email marketing</div>
      <div class="skill-item"><div class="skill-dot"></div>SEO / blogging</div>
    </div>
    <div>
      <div class="skill-col-title">Analytics</div>
      <div class="skill-item"><div class="skill-dot"></div>Google Analytics</div>
      <div class="skill-item"><div class="skill-dot"></div>Meta Ads Manager</div>
      <div class="skill-item"><div class="skill-dot"></div>A/B testing</div>
      <div class="skill-item"><div class="skill-dot"></div>Reporting & KPIs</div>
    </div>
    <div>
      <div class="skill-col-title">Tools</div>
      <div class="skill-item"><div class="skill-dot"></div>HubSpot</div>
      <div class="skill-item"><div class="skill-dot"></div>Canva / Figma</div>
      <div class="skill-item"><div class="skill-dot"></div>Mailchimp</div>
      <div class="skill-item"><div class="skill-dot"></div>Excel / Sheets</div>
    </div>
  </div>

  <footer>
    <span class="footer-name">Eric<span>.</span></span>
    <div class="footer-r">
      <a class="footer-link" href="#" onclick="show('about');return false;">About</a>
      <a class="footer-link" href="#" onclick="show('contact');return false;">Contact</a>
      <span style="font-size:11px;color:var(--mid);letter-spacing:.1em;">© 2025</span>
    </div>
  </footer>
</div>

<!-- ======= ABOUT ======= -->
<div class="page" id="page-about">
  <div class="about-hero">
    <div>
      <p class="about-eyebrow">About Me</p>
      <h2 class="about-h">Marketing mind.<br/><em>Creative</em> at heart.</h2>
      <p class="about-p">I'm Eric, a recent marketing graduate who genuinely loves the craft — figuring out what makes people tick, building stories that stick, and translating strategy into work that actually drives results.</p>
      <p class="about-p">Throughout school I worked on projects spanning brand strategy, social campaigns, content creation, and consumer research. I'm equally comfortable in a spreadsheet and a creative brief.</p>
      <p class="about-p">Right now I'm looking for a full-time role where I can keep growing fast and make a real contribution from day one.</p>
      <div class="about-edu">
        <div class="edu-label">Education</div>
        <div class="edu-row">
          <div class="edu-degree">B.S. in Marketing</div>
          <div class="edu-year">2025</div>
        </div>
        <div class="edu-school">Your University Name · GPA: X.X</div>
      </div>
    </div>
    <div class="about-right-col">
      <div class="about-photo-placeholder"></div>
      <div class="about-tools">
        <div class="tools-label">Tools & Platforms</div>
        <div class="tools-grid">
          <span class="tool-chip">HubSpot</span>
          <span class="tool-chip">Mailchimp</span>
          <span class="tool-chip">Google Analytics</span>
          <span class="tool-chip">Meta Ads</span>
          <span class="tool-chip">Canva</span>
          <span class="tool-chip">Figma</span>
          <span class="tool-chip">Hootsuite</span>
          <span class="tool-chip">SEMrush</span>
          <span class="tool-chip">Excel</span>
          <span class="tool-chip">Notion</span>
        </div>
      </div>
    </div>
  </div>
  <footer>
    <span class="footer-name">Eric<span>.</span></span>
    <div class="footer-r">
      <a class="footer-link" href="#" onclick="show('home');return false;">← Work</a>
      <a class="footer-link" href="#" onclick="show('contact');return false;">Contact</a>
    </div>
  </footer>
</div>

<!-- ======= CONTACT ======= -->
<div class="page" id="page-contact">
  <div class="contact-hero">
    <div>
      <p class="about-eyebrow">Contact</p>
      <h2 class="contact-h">Let's work<br/><em>together.</em></h2>
      <p class="contact-p">I'm actively looking for full-time marketing roles. Whether you have an opening, a project, or just want to connect — my inbox is open.</p>
      <div>
        <a href="mailto:hello@eric.com" class="contact-item">
          <div><div class="c-label">Email</div><div class="c-value">hello@eric.com</div></div>
          <div class="c-arrow">↗</div>
        </a>
        <a href="#" class="contact-item">
          <div><div class="c-label">LinkedIn</div><div class="c-value">linkedin.com/in/eric</div></div>
          <div class="c-arrow">↗</div>
        </a>
        <a href="#" class="contact-item">
          <div><div class="c-label">Resume</div><div class="c-value">Download PDF</div></div>
          <div class="c-arrow">↗</div>
        </a>
      </div>
    </div>
    <div class="contact-form-wrap">
      <div class="form-title">Send a message</div>
      <form onsubmit="handleForm(event)">
        <div class="form-row">
          <div class="fg"><label class="fl">Name</label><input class="fi" type="text" placeholder="Your name" required/></div>
          <div class="fg"><label class="fl">Email</label><input class="fi" type="email" placeholder="you@company.com" required/></div>
        </div>
        <div class="fg">
          <label class="fl">Company / Role</label>
          <input class="fi" type="text" placeholder="Acme Inc. — Marketing Manager"/>
        </div>
        <div class="fg">
          <label class="fl">I'm reaching out about</label>
          <select class="fs">
            <option value="">Select one…</option>
            <option>Full-time opportunity</option>
            <option>Freelance / contract work</option>
            <option>Collaboration</option>
            <option>Just saying hi</option>
          </select>
        </div>
        <div class="fg"><label class="fl">Message</label><textarea class="ft" placeholder="Tell me more…" required></textarea></div>
        <button class="submit-btn" type="submit">Send Message <span>→</span></button>
      </form>
    </div>
  </div>
  <footer>
    <span class="footer-name">Eric<span>.</span></span>
    <div class="footer-r">
      <a class="footer-link" href="#" onclick="show('home');return false;">← Work</a>
      <a class="footer-link" href="#" onclick="show('about');return false;">About</a>
    </div>
  </footer>
</div>

<script>
const cur = document.getElementById('cursor');
const trail = document.getElementById('trail');
let mx=0,my=0,tx=0,ty=0;
document.addEventListener('mousemove', e => {
  mx=e.clientX; my=e.clientY;
  cur.style.left=mx+'px'; cur.style.top=my+'px';
});
(function loop(){ tx+=(mx-tx)*.13; ty+=(my-ty)*.13;
  trail.style.left=tx+'px'; trail.style.top=ty+'px';
  requestAnimationFrame(loop); })();

window.addEventListener('scroll', ()=>{
  document.getElementById('nav').classList.toggle('scrolled', window.scrollY>10);
});

function show(name){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.getElementById('page-'+name).classList.add('active');
  window.scrollTo({top:0,behavior:'smooth'});
  setTimeout(initReveal, 80);
}

function initReveal(){
  const els = document.querySelectorAll('.page.active .reveal');
  const obs = new IntersectionObserver(entries=>{
    entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('visible'); obs.unobserve(e.target); }});
  },{threshold:0.08});
  els.forEach(el=>obs.observe(el));
}

function handleForm(e){
  e.preventDefault();
  const btn = e.target.querySelector('.submit-btn');
  btn.textContent = 'Message Sent ✓';
  btn.style.background='#3a7a3a';
  setTimeout(()=>{ btn.innerHTML='Send Message <span>→</span>'; btn.style.background=''; e.target.reset(); },3000);
}

initReveal();
</script>
</body>
</html>
