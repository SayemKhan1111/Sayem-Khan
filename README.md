<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sayem Khan — AI/ML Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Syne:wght@700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --neon: #00f5d4;
    --neon2: #7b2fff;
    --neon3: #ff6b6b;
    --gold: #f7c948;
    --bg: #060614;
    --bg2: #0d0d2b;
    --bg3: #12123a;
    --card: rgba(255,255,255,0.04);
    --border: rgba(123,47,255,0.3);
    --text: #e8e8ff;
    --muted: #8888aa;
    --font: 'Space Grotesk', sans-serif;
    --mono: 'JetBrains Mono', monospace;
    --display: 'Syne', sans-serif;
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font);
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  #cursor {
    position: fixed; width: 12px; height: 12px; border-radius: 50%;
    background: var(--neon); pointer-events: none; z-index: 9999;
    transform: translate(-50%, -50%); transition: transform 0.1s;
    mix-blend-mode: screen;
  }
  #cursor-trail {
    position: fixed; width: 36px; height: 36px; border-radius: 50%;
    border: 1px solid rgba(0,245,212,0.4); pointer-events: none; z-index: 9998;
    transform: translate(-50%, -50%); transition: left 0.12s ease, top 0.12s ease;
  }

  /* Stars canvas */
  #starfield {
    position: fixed; inset: 0; z-index: 0; pointer-events: none;
  }

  /* Main wrapper */
  .wrap { position: relative; z-index: 1; max-width: 960px; margin: 0 auto; padding: 0 24px; }

  /* ───── HERO ───── */
  .hero {
    min-height: 100vh; display: flex; flex-direction: column;
    justify-content: center; align-items: center; text-align: center;
    padding: 80px 0 60px; position: relative;
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(0,245,212,0.1); border: 1px solid rgba(0,245,212,0.3);
    color: var(--neon); font-family: var(--mono); font-size: 12px;
    padding: 6px 16px; border-radius: 100px; margin-bottom: 32px;
    animation: pulse-border 2s ease-in-out infinite;
  }
  @keyframes pulse-border {
    0%,100%{border-color:rgba(0,245,212,0.3);box-shadow:0 0 0 0 rgba(0,245,212,0)}
    50%{border-color:rgba(0,245,212,0.8);box-shadow:0 0 20px rgba(0,245,212,0.2)}
  }
  .dot-live { width: 7px; height: 7px; background: var(--neon); border-radius: 50%; animation: blink 1.2s ease-in-out infinite; }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.2} }

  .hero h1 {
    font-family: var(--display); font-size: clamp(52px,9vw,110px);
    font-weight: 800; line-height: 0.9; letter-spacing: -3px;
    margin-bottom: 20px;
    background: linear-gradient(135deg, #ffffff 0%, #a78bfa 40%, #00f5d4 80%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    animation: gradient-shift 4s ease-in-out infinite alternate;
    background-size: 200% 200%;
  }
  @keyframes gradient-shift {
    0%{background-position:0% 50%}100%{background-position:100% 50%}
  }

  .hero-title-line2 {
    font-family: var(--display); font-size: clamp(24px,4vw,48px);
    font-weight: 700; letter-spacing: -1px; color: var(--neon2);
    opacity: 0.9; display: block; margin-bottom: 28px;
  }

  .hero-tags {
    display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;
    margin-bottom: 44px;
  }
  .tag {
    font-family: var(--mono); font-size: 12px; padding: 6px 14px;
    border-radius: 6px; border: 1px solid; cursor: default;
    transition: all 0.3s; user-select: none;
  }
  .tag:hover { transform: translateY(-3px) scale(1.05); }
  .tag-1 { border-color: var(--neon); color: var(--neon); background: rgba(0,245,212,0.08); }
  .tag-2 { border-color: var(--neon2); color: var(--neon2); background: rgba(123,47,255,0.1); }
  .tag-3 { border-color: var(--neon3); color: var(--neon3); background: rgba(255,107,107,0.08); }
  .tag-4 { border-color: var(--gold); color: var(--gold); background: rgba(247,201,72,0.08); }

  .hero-cta { display: flex; gap: 16px; flex-wrap: wrap; justify-content: center; }

  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 13px 28px; border-radius: 8px; font-family: var(--font);
    font-size: 14px; font-weight: 600; text-decoration: none;
    transition: all 0.3s; cursor: pointer;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--neon2), var(--neon));
    color: #000; border: none;
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 30px rgba(0,245,212,0.4); }
  .btn-outline {
    background: transparent; color: var(--text);
    border: 1px solid rgba(255,255,255,0.2);
  }
  .btn-outline:hover { border-color: var(--neon); color: var(--neon); transform: translateY(-2px); }

  /* Scroll indicator */
  .scroll-hint {
    position: absolute; bottom: 32px; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    color: var(--muted); font-size: 11px; font-family: var(--mono);
  }
  .scroll-arrow {
    width: 20px; height: 20px; border-right: 2px solid var(--muted);
    border-bottom: 2px solid var(--muted); transform: rotate(45deg);
    animation: bounce-down 1.5s ease-in-out infinite;
  }
  @keyframes bounce-down { 0%,100%{transform:rotate(45deg) translateY(0)} 50%{transform:rotate(45deg) translateY(5px)} }

  /* ───── SECTION ───── */
  section { padding: 100px 0; }
  .section-label {
    font-family: var(--mono); font-size: 11px; color: var(--neon);
    letter-spacing: 3px; text-transform: uppercase; margin-bottom: 12px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: linear-gradient(90deg,rgba(0,245,212,0.4),transparent); }
  .section-title {
    font-family: var(--display); font-size: clamp(32px,5vw,52px);
    font-weight: 800; line-height: 1; letter-spacing: -1px;
    margin-bottom: 56px; color: #fff;
  }

  /* ───── STATS BAR ───── */
  .stats-bar {
    display: grid; grid-template-columns: repeat(4, 1fr);
    gap: 1px; background: var(--border); border: 1px solid var(--border);
    border-radius: 16px; overflow: hidden; margin-bottom: 100px;
  }
  .stat-item {
    background: var(--card); padding: 32px 24px; text-align: center;
    backdrop-filter: blur(10px); transition: background 0.3s;
  }
  .stat-item:hover { background: rgba(123,47,255,0.12); }
  .stat-num {
    font-family: var(--display); font-size: 42px; font-weight: 800;
    color: var(--neon); line-height: 1;
  }
  .stat-label { font-size: 12px; color: var(--muted); margin-top: 6px; font-family: var(--mono); }

  /* ───── SKILLS ───── */
  .skills-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px; }
  .skill-card {
    background: var(--card); border: 1px solid var(--border); border-radius: 14px;
    padding: 24px; transition: all 0.35s; cursor: default;
    position: relative; overflow: hidden;
  }
  .skill-card::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, transparent, rgba(123,47,255,0.06));
    opacity: 0; transition: opacity 0.3s;
  }
  .skill-card:hover { border-color: rgba(0,245,212,0.5); transform: translateY(-4px); }
  .skill-card:hover::before { opacity: 1; }
  .skill-head { display: flex; align-items: center; gap: 12px; margin-bottom: 18px; }
  .skill-icon {
    width: 44px; height: 44px; border-radius: 10px; display: flex;
    align-items: center; justify-content: center; font-size: 20px;
    flex-shrink: 0;
  }
  .skill-name { font-weight: 600; font-size: 15px; color: #fff; }
  .skill-cat { font-family: var(--mono); font-size: 11px; color: var(--muted); margin-top: 2px; }
  .skill-items { display: flex; flex-wrap: wrap; gap: 7px; }
  .pill {
    font-family: var(--mono); font-size: 11px; padding: 4px 10px;
    background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.12);
    border-radius: 100px; color: var(--muted); transition: all 0.2s;
  }
  .skill-card:hover .pill { color: var(--text); border-color: rgba(0,245,212,0.25); }

  /* ───── PROJECTS ───── */
  .projects-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px; }
  .project-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 28px; transition: all 0.35s;
    position: relative; overflow: hidden; cursor: default;
  }
  .project-card::after {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: linear-gradient(90deg, var(--neon2), var(--neon));
    transform: scaleX(0); transform-origin: left; transition: transform 0.4s;
  }
  .project-card:hover { border-color: rgba(0,245,212,0.4); transform: translateY(-5px);
    box-shadow: 0 20px 60px rgba(0,0,0,0.5); }
  .project-card:hover::after { transform: scaleX(1); }
  .project-num {
    font-family: var(--mono); font-size: 11px; color: var(--neon2);
    margin-bottom: 12px; opacity: 0.7;
  }
  .project-title { font-weight: 700; font-size: 17px; color: #fff; margin-bottom: 10px; line-height: 1.3; }
  .project-desc { font-size: 13px; color: var(--muted); line-height: 1.7; margin-bottom: 18px; }
  .project-stack { display: flex; flex-wrap: wrap; gap: 6px; }
  .stack-tag {
    font-family: var(--mono); font-size: 10px; padding: 3px 9px;
    background: rgba(123,47,255,0.15); border: 1px solid rgba(123,47,255,0.3);
    color: #a78bfa; border-radius: 4px;
  }

  /* ───── ABOUT ───── */
  .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: start; }
  .about-text p { font-size: 16px; color: var(--muted); line-height: 1.9; margin-bottom: 20px; }
  .about-text strong { color: var(--text); font-weight: 600; }
  .about-highlights { display: flex; flex-direction: column; gap: 14px; }
  .highlight-item {
    display: flex; align-items: flex-start; gap: 14px;
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; padding: 16px 20px; transition: all 0.3s;
  }
  .highlight-item:hover { border-color: rgba(0,245,212,0.4); transform: translateX(4px); }
  .hi-icon { font-size: 20px; flex-shrink: 0; margin-top: 1px; }
  .hi-text { font-size: 14px; color: var(--text); line-height: 1.5; }
  .hi-sub { font-size: 12px; color: var(--muted); margin-top: 2px; }

  /* ───── TECH GRID ───── */
  .tech-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(90px, 1fr));
    gap: 14px;
  }
  .tech-item {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; padding: 18px 8px;
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    transition: all 0.3s; cursor: default;
  }
  .tech-item:hover {
    transform: translateY(-4px) scale(1.05);
    border-color: rgba(0,245,212,0.5);
    box-shadow: 0 8px 30px rgba(0,245,212,0.1);
  }
  .tech-logo { font-size: 28px; line-height: 1; }
  .tech-name { font-family: var(--mono); font-size: 10px; color: var(--muted); text-align: center; }

  /* ───── TIMELINE ───── */
  .timeline { position: relative; }
  .timeline::before {
    content: ''; position: absolute; left: 20px; top: 0; bottom: 0;
    width: 1px; background: linear-gradient(180deg,var(--neon2),transparent);
  }
  .tl-item { display: flex; gap: 32px; margin-bottom: 40px; }
  .tl-dot {
    width: 40px; height: 40px; border-radius: 50%; background: var(--bg2);
    border: 2px solid var(--neon2); display: flex; align-items: center;
    justify-content: center; font-size: 14px; flex-shrink: 0;
    box-shadow: 0 0 20px rgba(123,47,255,0.3);
  }
  .tl-content {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; padding: 20px 24px; flex: 1;
  }
  .tl-date { font-family: var(--mono); font-size: 11px; color: var(--neon); margin-bottom: 6px; }
  .tl-title { font-weight: 600; font-size: 16px; color: #fff; margin-bottom: 6px; }
  .tl-desc { font-size: 13px; color: var(--muted); line-height: 1.6; }

  /* ───── CONTACT ───── */
  .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
  .contact-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 28px; text-decoration: none;
    color: var(--text); transition: all 0.35s; display: flex;
    align-items: center; gap: 18px;
  }
  .contact-card:hover { transform: translateY(-4px); border-color: var(--neon); box-shadow: 0 12px 40px rgba(0,245,212,0.15); }
  .cc-icon {
    width: 54px; height: 54px; border-radius: 12px; display: flex;
    align-items: center; justify-content: center; font-size: 24px; flex-shrink: 0;
  }
  .cc-label { font-size: 12px; color: var(--muted); font-family: var(--mono); margin-bottom: 4px; }
  .cc-value { font-weight: 600; font-size: 15px; color: #fff; }

  /* ───── FOOTER ───── */
  footer {
    border-top: 1px solid rgba(255,255,255,0.06); padding: 48px 0;
    text-align: center; color: var(--muted); font-size: 13px;
    font-family: var(--mono);
  }
  footer span { color: var(--neon2); }

  /* ───── TYPING ANIMATION ───── */
  #typed-text { color: var(--neon); }
  .cursor-blink {
    display: inline-block; width: 2px; height: 1em;
    background: var(--neon); margin-left: 2px; vertical-align: text-bottom;
    animation: blink 0.8s step-end infinite;
  }

  /* ───── SCANLINE OVERLAY ───── */
  .scanline {
    position: fixed; inset: 0; z-index: 0; pointer-events: none;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.03) 2px, rgba(0,0,0,0.03) 4px);
  }

  /* ───── GLOW ORBS ───── */
  .orb {
    position: fixed; border-radius: 50%; filter: blur(120px);
    pointer-events: none; z-index: 0; opacity: 0.12;
  }
  .orb-1 { width: 600px; height: 600px; background: var(--neon2); top: -200px; right: -200px; animation: float1 8s ease-in-out infinite; }
  .orb-2 { width: 500px; height: 500px; background: var(--neon); bottom: 10%; left: -200px; animation: float2 10s ease-in-out infinite; }
  .orb-3 { width: 400px; height: 400px; background: var(--neon3); top: 40%; right: 10%; animation: float3 12s ease-in-out infinite; }
  @keyframes float1 { 0%,100%{transform:translate(0,0)}50%{transform:translate(-30px,40px)} }
  @keyframes float2 { 0%,100%{transform:translate(0,0)}50%{transform:translate(40px,-30px)} }
  @keyframes float3 { 0%,100%{transform:translate(0,0)}50%{transform:translate(-20px,20px)} }

  /* ───── NAV ───── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 16px 40px; display: flex; justify-content: space-between; align-items: center;
    background: rgba(6,6,20,0.7); backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }
  .nav-logo { font-family: var(--display); font-size: 18px; font-weight: 800; color: #fff; }
  .nav-logo span { color: var(--neon); }
  .nav-links { display: flex; gap: 28px; list-style: none; }
  .nav-links a { font-size: 13px; color: var(--muted); text-decoration: none; font-family: var(--mono); transition: color 0.2s; }
  .nav-links a:hover { color: var(--neon); }

  /* Appear animations */
  .appear { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .appear.visible { opacity: 1; transform: translateY(0); }

  @media (max-width: 720px) {
    .stats-bar { grid-template-columns: repeat(2,1fr); }
    .skills-grid,.projects-grid,.about-grid,.contact-grid { grid-template-columns: 1fr; }
    nav { padding: 14px 20px; }
    .nav-links { display: none; }
  }
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-trail"></div>
<canvas id="starfield"></canvas>
<div class="scanline"></div>
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<nav>
  <div class="nav-logo">SK<span>.</span></div>
  <ul class="nav-links">
    <li><a href="#about">about</a></li>
    <li><a href="#skills">skills</a></li>
    <li><a href="#projects">projects</a></li>
    <li><a href="#stack">stack</a></li>
    <li><a href="#contact">contact</a></li>
  </ul>
</nav>

<main>
  <div class="wrap">

    <!-- ── HERO ── -->
    <section class="hero">
      <div class="hero-badge"><div class="dot-live"></div>Open to opportunities</div>
      <h1>Sayem<br>Khan</h1>
      <span class="hero-title-line2">AI/ML Engineer</span>
      <p style="font-family:var(--mono);font-size:15px;color:var(--muted);margin-bottom:32px;min-height:24px;">
        &gt; <span id="typed-text"></span><span class="cursor-blink"></span>
      </p>
      <div class="hero-tags">
        <span class="tag tag-1">Machine Learning</span>
        <span class="tag tag-2">Deep Learning</span>
        <span class="tag tag-1">Computer Vision</span>
        <span class="tag tag-3">Generative AI</span>
        <span class="tag tag-4">RAG &amp; Agents</span>
        <span class="tag tag-2">NLP</span>
        <span class="tag tag-1">Python</span>
        <span class="tag tag-3">LangChain</span>
      </div>
      <div class="hero-cta">
        <a href="mailto:sayemkhanraqraq@gmail.com" class="btn btn-primary">✉ Get In Touch</a>
        <a href="https://github.com/SayemKhan1111" target="_blank" class="btn btn-outline">⌘ GitHub</a>
        <a href="https://www.linkedin.com/in/sayem-khan-3b5bb727a/" target="_blank" class="btn btn-outline">in LinkedIn</a>
      </div>
      <div class="scroll-hint"><div class="scroll-arrow"></div>scroll</div>
    </section>

    <!-- ── STATS ── -->
    <div class="stats-bar appear">
      <div class="stat-item">
        <div class="stat-num" data-count="4">0</div>
        <div class="stat-label">Featured Projects</div>
      </div>
      <div class="stat-item">
        <div class="stat-num" data-count="10">0</div>
        <div class="stat-label">Tech Skills</div>
      </div>
      <div class="stat-item">
        <div class="stat-num" data-count="3">0</div>
        <div class="stat-label">Domains Mastered</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">∞</div>
        <div class="stat-label">Learning Mindset</div>
      </div>
    </div>

    <!-- ── ABOUT ── -->
    <section id="about" class="appear">
      <div class="section-label">// 01 — who i am</div>
      <div class="section-title">About Me</div>
      <div class="about-grid">
        <div class="about-text">
          <p>I'm a <strong>BCA AI &amp; ML student from India</strong> with a burning passion for building intelligent systems that solve real-world problems. From garbage detection to voice-powered AI agents — I love turning complex ML concepts into working products.</p>
          <p>Currently diving deep into <strong>RAG pipelines, AI automation</strong>, and <strong>multi-agent frameworks</strong>. I believe the future belongs to those who can bridge research with practical engineering.</p>
          <p>When I'm not training models, I'm exploring the cutting edge of <strong>Generative AI</strong> and building tools that make people's lives meaningfully better.</p>
        </div>
        <div class="about-highlights">
          <div class="highlight-item">
            <div class="hi-icon">🎓</div>
            <div>
              <div class="hi-text">BCA — Artificial Intelligence &amp; Machine Learning</div>
              <div class="hi-sub">Currently enrolled · India</div>
            </div>
          </div>
          <div class="highlight-item">
            <div class="hi-icon">🔭</div>
            <div>
              <div class="hi-text">Building AI Automation, RAG Agents &amp; ML systems</div>
              <div class="hi-sub">Active — shipping projects consistently</div>
            </div>
          </div>
          <div class="highlight-item">
            <div class="hi-icon">🌱</div>
            <div>
              <div class="hi-text">Learning FastAPI, Cloud AI &amp; Model Deployment</div>
              <div class="hi-sub">Always expanding the tech radar</div>
            </div>
          </div>
          <div class="highlight-item">
            <div class="hi-icon">📊</div>
            <div>
              <div class="hi-text">Python · ML · DL · CV · NLP · Power BI</div>
              <div class="hi-sub">Core expertise areas</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ── SKILLS ── -->
    <section id="skills" class="appear">
      <div class="section-label">// 02 — what i know</div>
      <div class="section-title">Skills &amp; Expertise</div>
      <div class="skills-grid">
        <div class="skill-card">
          <div class="skill-head">
            <div class="skill-icon" style="background:rgba(0,245,212,0.12);">🤖</div>
            <div>
              <div class="skill-name">Machine Learning</div>
              <div class="skill-cat">CORE DOMAIN</div>
            </div>
          </div>
          <div class="skill-items">
            <span class="pill">Scikit-learn</span><span class="pill">Regression</span><span class="pill">Classification</span>
            <span class="pill">Clustering</span><span class="pill">Feature Eng.</span><span class="pill">Model Eval</span>
          </div>
        </div>
        <div class="skill-card">
          <div class="skill-head">
            <div class="skill-icon" style="background:rgba(123,47,255,0.15);">🧠</div>
            <div>
              <div class="skill-name">Deep Learning</div>
              <div class="skill-cat">NEURAL SYSTEMS</div>
            </div>
          </div>
          <div class="skill-items">
            <span class="pill">TensorFlow</span><span class="pill">CNNs</span><span class="pill">RNNs</span>
            <span class="pill">Transfer Learning</span><span class="pill">EfficientNet</span><span class="pill">ResNet</span>
          </div>
        </div>
        <div class="skill-card">
          <div class="skill-head">
            <div class="skill-icon" style="background:rgba(255,107,107,0.12);">👁</div>
            <div>
              <div class="skill-name">Computer Vision</div>
              <div class="skill-cat">VISUAL AI</div>
            </div>
          </div>
          <div class="skill-items">
            <span class="pill">OpenCV</span><span class="pill">Image Classification</span><span class="pill">Object Detection</span>
            <span class="pill">Segmentation</span><span class="pill">YOLO</span>
          </div>
        </div>
        <div class="skill-card">
          <div class="skill-head">
            <div class="skill-icon" style="background:rgba(247,201,72,0.12);">✨</div>
            <div>
              <div class="skill-name">Generative AI &amp; NLP</div>
              <div class="skill-cat">LANGUAGE MODELS</div>
            </div>
          </div>
          <div class="skill-items">
            <span class="pill">LangChain</span><span class="pill">RAG</span><span class="pill">GPT APIs</span>
            <span class="pill">Embeddings</span><span class="pill">Vector DBs</span><span class="pill">AI Agents</span>
          </div>
        </div>
        <div class="skill-card">
          <div class="skill-head">
            <div class="skill-icon" style="background:rgba(0,245,212,0.12);">🔧</div>
            <div>
              <div class="skill-name">Dev &amp; Infra</div>
              <div class="skill-cat">ENGINEERING</div>
            </div>
          </div>
          <div class="skill-items">
            <span class="pill">FastAPI</span><span class="pill">Docker</span><span class="pill">Git</span>
            <span class="pill">GitHub</span><span class="pill">PostgreSQL</span><span class="pill">MySQL</span>
          </div>
        </div>
        <div class="skill-card">
          <div class="skill-head">
            <div class="skill-icon" style="background:rgba(123,47,255,0.15);">📊</div>
            <div>
              <div class="skill-name">Data &amp; Analytics</div>
              <div class="skill-cat">DATA SCIENCE</div>
            </div>
          </div>
          <div class="skill-items">
            <span class="pill">Pandas</span><span class="pill">NumPy</span><span class="pill">Matplotlib</span>
            <span class="pill">Seaborn</span><span class="pill">Power BI</span><span class="pill">Jupyter</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ── PROJECTS ── -->
    <section id="projects" class="appear">
      <div class="section-label">// 03 — what i built</div>
      <div class="section-title">Featured Projects</div>
      <div class="projects-grid">
        <div class="project-card">
          <div class="project-num">project_01.py</div>
          <div class="project-title">🧠 RAG AI Voice Business Agent</div>
          <div class="project-desc">Intelligent voice-powered AI agent capable of handling complex business queries, scheduling meetings autonomously, and managing end-to-end automation workflows using RAG architecture.</div>
          <div class="project-stack">
            <span class="stack-tag">Python</span><span class="stack-tag">LLM APIs</span><span class="stack-tag">RAG</span><span class="stack-tag">LangChain</span><span class="stack-tag">Vector DB</span>
          </div>
        </div>
        <div class="project-card">
          <div class="project-num">project_02.py</div>
          <div class="project-title">🗑️ Smart Garbage Classification</div>
          <div class="project-desc">High-accuracy waste detection and classification model using EfficientNetV2B2 with transfer learning. Real-time image classification for smart recycling systems and waste management.</div>
          <div class="project-stack">
            <span class="stack-tag">TensorFlow</span><span class="stack-tag">OpenCV</span><span class="stack-tag">EfficientNetV2</span><span class="stack-tag">Python</span>
          </div>
        </div>
        <div class="project-card">
          <div class="project-num">project_03.py</div>
          <div class="project-title">📩 AI Newsletter Automation</div>
          <div class="project-desc">Fully automated newsletter generation pipeline using GPT APIs and Google Sheets integration. Creates, personalizes, and schedules content delivery with zero human intervention.</div>
          <div class="project-stack">
            <span class="stack-tag">GPT API</span><span class="stack-tag">Google Sheets</span><span class="stack-tag">Python</span><span class="stack-tag">Automation</span>
          </div>
        </div>
        <div class="project-card">
          <div class="project-num">project_04.py</div>
          <div class="project-title">📊 COVID-19 Data Analysis</div>
          <div class="project-desc">Comprehensive data analysis and visualization project tracking COVID-19 trends globally. Interactive dashboards built with Python visualization libraries revealing key epidemiological patterns.</div>
          <div class="project-stack">
            <span class="stack-tag">Pandas</span><span class="stack-tag">Matplotlib</span><span class="stack-tag">Seaborn</span><span class="stack-tag">NumPy</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ── TECH STACK ── -->
    <section id="stack" class="appear">
      <div class="section-label">// 04 — my arsenal</div>
      <div class="section-title">Tech Stack</div>
      <div class="tech-grid">
        <div class="tech-item"><div class="tech-logo">🐍</div><div class="tech-name">Python</div></div>
        <div class="tech-item"><div class="tech-logo">🔶</div><div class="tech-name">TensorFlow</div></div>
        <div class="tech-item"><div class="tech-logo">👁</div><div class="tech-name">OpenCV</div></div>
        <div class="tech-item"><div class="tech-logo">⚡</div><div class="tech-name">FastAPI</div></div>
        <div class="tech-item"><div class="tech-logo">🔗</div><div class="tech-name">LangChain</div></div>
        <div class="tech-item"><div class="tech-logo">🐳</div><div class="tech-name">Docker</div></div>
        <div class="tech-item"><div class="tech-logo">🐘</div><div class="tech-name">PostgreSQL</div></div>
        <div class="tech-item"><div class="tech-logo">🐬</div><div class="tech-name">MySQL</div></div>
        <div class="tech-item"><div class="tech-logo">📊</div><div class="tech-name">Power BI</div></div>
        <div class="tech-item"><div class="tech-logo">🤗</div><div class="tech-name">HuggingFace</div></div>
        <div class="tech-item"><div class="tech-logo">🐙</div><div class="tech-name">GitHub</div></div>
        <div class="tech-item"><div class="tech-logo">🚀</div><div class="tech-name">Scikit-learn</div></div>
      </div>
    </section>

    <!-- ── LEARNING JOURNEY ── -->
    <section class="appear">
      <div class="section-label">// 05 — my journey</div>
      <div class="section-title">Learning Path</div>
      <div class="timeline">
        <div class="tl-item">
          <div class="tl-dot">🎓</div>
          <div class="tl-content">
            <div class="tl-date">CURRENT</div>
            <div class="tl-title">BCA — AI &amp; Machine Learning</div>
            <div class="tl-desc">Deep-diving into AI fundamentals, mathematics behind ML, and practical engineering. Building a strong academic foundation while shipping real projects simultaneously.</div>
          </div>
        </div>
        <div class="tl-item">
          <div class="tl-dot">🤖</div>
          <div class="tl-content">
            <div class="tl-date">ACTIVE</div>
            <div class="tl-title">RAG &amp; AI Agent Development</div>
            <div class="tl-desc">Architecting Retrieval-Augmented Generation systems and autonomous AI agents. Exploring LangChain, vector databases, and multi-step reasoning pipelines.</div>
          </div>
        </div>
        <div class="tl-item">
          <div class="tl-dot">⚡</div>
          <div class="tl-content">
            <div class="tl-date">LEARNING</div>
            <div class="tl-title">Cloud AI &amp; Model Deployment</div>
            <div class="tl-desc">Mastering FastAPI for production-ready model serving, Docker for containerization, and cloud platforms for scalable AI deployment pipelines.</div>
          </div>
        </div>
        <div class="tl-item">
          <div class="tl-dot">🔮</div>
          <div class="tl-content">
            <div class="tl-date">NEXT</div>
            <div class="tl-title">MLOps &amp; Production AI Systems</div>
            <div class="tl-desc">Building towards expertise in MLOps, model monitoring, A/B testing for ML, and building enterprise-grade AI infrastructure.</div>
          </div>
        </div>
      </div>
    </section>

    <!-- ── CONTACT ── -->
    <section id="contact" class="appear">
      <div class="section-label">// 06 — let's connect</div>
      <div class="section-title">Get In Touch</div>
      <p style="color:var(--muted);font-size:16px;margin-bottom:40px;max-width:500px;line-height:1.8;">
        Open to collaborations, internships, and interesting AI/ML projects. Let's build something extraordinary together.
      </p>
      <div class="contact-grid">
        <a href="mailto:sayemkhanraqraq@gmail.com" class="contact-card">
          <div class="cc-icon" style="background:rgba(255,107,107,0.12);color:#ff6b6b;">✉</div>
          <div>
            <div class="cc-label">EMAIL</div>
            <div class="cc-value">sayemkhanraqraq@gmail.com</div>
          </div>
        </a>
        <a href="https://www.linkedin.com/in/sayem-khan-3b5bb727a/" target="_blank" class="contact-card">
          <div class="cc-icon" style="background:rgba(0,119,181,0.12);color:#0077b5;">in</div>
          <div>
            <div class="cc-label">LINKEDIN</div>
            <div class="cc-value">sayem-khan-3b5bb727a</div>
          </div>
        </a>
        <a href="https://github.com/SayemKhan1111" target="_blank" class="contact-card">
          <div class="cc-icon" style="background:rgba(255,255,255,0.08);color:#fff;">⌘</div>
          <div>
            <div class="cc-label">GITHUB</div>
            <div class="cc-value">SayemKhan1111</div>
          </div>
        </a>
        <div class="contact-card" style="border-color:rgba(0,245,212,0.25);">
          <div class="cc-icon" style="background:rgba(0,245,212,0.1);color:var(--neon);">📍</div>
          <div>
            <div class="cc-label">LOCATION</div>
            <div class="cc-value">India 🇮🇳 &nbsp;·&nbsp; Remote Friendly</div>
          </div>
        </div>
      </div>
    </section>

  </div>
</main>

<footer>
  <p>Crafted with <span>♥</span> by <span>Sayem Khan</span> &nbsp;·&nbsp; AI/ML Engineer &nbsp;·&nbsp; India</p>
  <p style="margin-top:8px;font-size:11px;opacity:0.5;">Building the future, one model at a time.</p>
</footer>

<script>
// ── Cursor ──
const cursor = document.getElementById('cursor');
const trail = document.getElementById('cursor-trail');
document.addEventListener('mousemove', e => {
  cursor.style.left = e.clientX + 'px';
  cursor.style.top = e.clientY + 'px';
  setTimeout(() => { trail.style.left = e.clientX + 'px'; trail.style.top = e.clientY + 'px'; }, 80);
});
document.querySelectorAll('a,button,.tech-item,.project-card,.skill-card').forEach(el => {
  el.addEventListener('mouseenter', () => { cursor.style.transform = 'translate(-50%,-50%) scale(2.5)'; cursor.style.opacity = '0.6'; });
  el.addEventListener('mouseleave', () => { cursor.style.transform = 'translate(-50%,-50%) scale(1)'; cursor.style.opacity = '1'; });
});

// ── Starfield ──
const canvas = document.getElementById('starfield');
const ctx = canvas.getContext('2d');
let stars = [], W, H;
function resize() { W = canvas.width = window.innerWidth; H = canvas.height = window.innerHeight; }
resize(); window.addEventListener('resize', resize);
for (let i = 0; i < 160; i++) {
  stars.push({ x: Math.random()*1920, y: Math.random()*1080, r: Math.random()*1.5+0.3, s: Math.random()*0.4+0.1, o: Math.random(), d: Math.random() > 0.5 ? 1 : -1 });
}
function animStars() {
  ctx.clearRect(0,0,W,H);
  stars.forEach(s => {
    s.o += 0.003 * s.d;
    if (s.o > 1 || s.o < 0) s.d *= -1;
    ctx.beginPath(); ctx.arc(s.x % W, s.y % H, s.r, 0, Math.PI*2);
    ctx.fillStyle = `rgba(180,180,255,${s.o})`;
    ctx.fill();
  });
  requestAnimationFrame(animStars);
}
animStars();

// ── Typing effect ──
const phrases = [
  'Building AI systems that matter...',
  'Training models on real-world data...',
  'Crafting RAG agents from scratch...',
  'Turning ideas into intelligent code...',
  'Engineering the future with Python...',
];
let pi = 0, ci = 0, deleting = false, paused = false;
function type() {
  const el = document.getElementById('typed-text');
  if (!el) return;
  const word = phrases[pi];
  if (!deleting) {
    el.textContent = word.slice(0, ci+1); ci++;
    if (ci === word.length) { paused = true; setTimeout(() => { deleting = true; paused = false; }, 2000); }
  } else {
    el.textContent = word.slice(0, ci-1); ci--;
    if (ci === 0) { deleting = false; pi = (pi+1) % phrases.length; }
  }
  if (!paused) setTimeout(type, deleting ? 40 : 70);
}
setTimeout(type, 1200);

// ── Counter animation ──
function animateCounter(el, target) {
  let start = 0; const dur = 1800;
  const step = timestamp => {
    if (!start) start = timestamp;
    const p = Math.min((timestamp - start) / dur, 1);
    el.textContent = Math.round(p * target);
    if (p < 1) requestAnimationFrame(step);
    else el.textContent = target + '+';
  };
  requestAnimationFrame(step);
}

// ── Intersection Observer ──
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
      if (e.target.classList.contains('stats-bar')) {
        e.target.querySelectorAll('[data-count]').forEach(el => animateCounter(el, +el.dataset.count));
      }
    }
  });
}, { threshold: 0.12 });
document.querySelectorAll('.appear').forEach(el => observer.observe(el));
</script>
</body>
</html>
