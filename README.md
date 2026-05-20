<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tinsae Bahiru — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Rajdhani:wght@300;400;500;600;700&family=Share+Tech+Mono&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --gold: #c9a84c;
    --gold-dim: #8a6e2f;
    --cyan: #00d9ff;
    --red: #e63946;
    --white: #f0ece2;
    --dim: #8a8375;
    --bg: #060608;
    --bg2: #0d0d12;
    --bg3: #12121a;
    --card: #0f0f16;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--white);
    font-family: 'Rajdhani', sans-serif;
    overflow-x: hidden;
    cursor: default;
  }

  /* ── FILM GRAIN OVERLAY ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 9999;
    opacity: 0.4;
  }

  /* ── SCANLINES ── */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(0,0,0,0.05) 3px, rgba(0,0,0,0.05) 4px);
    pointer-events: none;
    z-index: 9998;
  }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
    padding: 2rem;
    text-align: center;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 0%, rgba(201,168,76,0.08) 0%, transparent 60%),
      radial-gradient(ellipse 60% 40% at 20% 80%, rgba(0,217,255,0.05) 0%, transparent 50%),
      radial-gradient(ellipse 50% 50% at 80% 50%, rgba(230,57,70,0.04) 0%, transparent 50%),
      var(--bg);
  }

  /* Stars */
  .stars {
    position: absolute;
    inset: 0;
    overflow: hidden;
  }
  .star {
    position: absolute;
    width: 2px;
    height: 2px;
    background: white;
    border-radius: 50%;
    animation: twinkle var(--d) var(--delay) ease-in-out infinite;
  }
  @keyframes twinkle {
    0%, 100% { opacity: 0.1; transform: scale(1); }
    50% { opacity: 0.9; transform: scale(1.4); }
  }

  /* Horizontal beam lines */
  .beam {
    position: absolute;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    opacity: 0;
    animation: beam-sweep 8s ease-in-out infinite;
  }
  .beam:nth-child(1) { width: 60%; top: 30%; animation-delay: 0s; }
  .beam:nth-child(2) { width: 40%; top: 65%; animation-delay: 3s; }
  .beam:nth-child(3) { width: 80%; top: 85%; animation-delay: 6s; }
  @keyframes beam-sweep {
    0% { opacity: 0; transform: translateX(-120%); }
    30% { opacity: 0.6; }
    70% { opacity: 0.3; }
    100% { opacity: 0; transform: translateX(120%); }
  }

  .hero-content { position: relative; z-index: 2; }

  .studio-label {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.4em;
    color: var(--gold);
    text-transform: uppercase;
    opacity: 0;
    animation: fade-in 1s 0.5s ease forwards;
    margin-bottom: 1.5rem;
  }

  .hero-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(4rem, 12vw, 10rem);
    line-height: 0.9;
    letter-spacing: 0.05em;
    color: var(--white);
    text-shadow: 0 0 80px rgba(201,168,76,0.3);
    opacity: 0;
    transform: translateY(40px) scale(0.95);
    animation: hero-rise 1.2s 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    position: relative;
  }
  .hero-name span { color: var(--gold); }

  .hero-tagline {
    font-size: 1.1rem;
    letter-spacing: 0.3em;
    color: var(--dim);
    text-transform: uppercase;
    margin-top: 1.2rem;
    opacity: 0;
    animation: fade-in 1s 1.8s ease forwards;
  }

  .hero-tagline em {
    color: var(--cyan);
    font-style: normal;
  }

  .hero-divider {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin: 2rem auto;
    width: 320px;
    opacity: 0;
    animation: fade-in 1s 2.2s ease forwards;
  }
  .hero-divider::before, .hero-divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold-dim));
  }
  .hero-divider::after { background: linear-gradient(90deg, var(--gold-dim), transparent); }
  .hero-divider-icon { color: var(--gold); font-size: 0.6rem; letter-spacing: 0.3em; }

  .hero-roles {
    display: flex;
    gap: 0.8rem;
    justify-content: center;
    flex-wrap: wrap;
    opacity: 0;
    animation: fade-in 1s 2.5s ease forwards;
  }
  .role-pill {
    font-size: 0.75rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    padding: 0.4rem 1rem;
    border: 1px solid var(--gold-dim);
    color: var(--gold);
    background: rgba(201,168,76,0.04);
    clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
  }

  .scroll-cue {
    position: absolute;
    bottom: 2.5rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
    opacity: 0;
    animation: fade-in 1s 3.5s ease forwards;
  }
  .scroll-cue span {
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    color: var(--dim);
    text-transform: uppercase;
  }
  .scroll-arrow {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, var(--gold), transparent);
    animation: scroll-pulse 2s ease-in-out infinite;
  }
  @keyframes scroll-pulse {
    0%, 100% { opacity: 0.3; transform: scaleY(0.8); }
    50% { opacity: 1; transform: scaleY(1); }
  }

  @keyframes fade-in {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  @keyframes hero-rise {
    to { opacity: 1; transform: translateY(0) scale(1); }
  }

  /* ── SECTION BASE ── */
  section {
    padding: 5rem 2rem;
    max-width: 1100px;
    margin: 0 auto;
    position: relative;
  }

  .section-eyebrow {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.5em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 0.5rem;
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }
  .section-eyebrow::before {
    content: '';
    width: 24px;
    height: 1px;
    background: var(--gold);
  }

  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(2.5rem, 6vw, 4.5rem);
    line-height: 1;
    letter-spacing: 0.04em;
    margin-bottom: 3rem;
  }

  /* ── ABOUT ── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
  }
  @media (max-width: 700px) { .about-grid { grid-template-columns: 1fr; } }

  .about-text p {
    font-size: 1.05rem;
    line-height: 1.8;
    color: #b0a898;
    margin-bottom: 1.2rem;
  }
  .about-text p strong { color: var(--white); font-weight: 600; }

  .stat-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }
  .stat-card {
    background: var(--card);
    border: 1px solid rgba(201,168,76,0.12);
    padding: 1.4rem;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s;
  }
  .stat-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
    background: var(--gold);
    opacity: 0.6;
  }
  .stat-card:hover { border-color: rgba(201,168,76,0.4); }
  .stat-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2.5rem;
    color: var(--gold);
    line-height: 1;
    margin-bottom: 0.3rem;
  }
  .stat-label {
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    color: var(--dim);
    text-transform: uppercase;
  }

  /* ── SKILLS ── */
  .skills-container { position: relative; }

  .skill-category {
    margin-bottom: 3rem;
  }
  .skill-cat-title {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.35em;
    color: var(--cyan);
    text-transform: uppercase;
    margin-bottom: 1.2rem;
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }
  .skill-cat-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: rgba(0,217,255,0.15);
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.6rem;
  }
  .skill-tag {
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.85rem;
    font-weight: 500;
    letter-spacing: 0.08em;
    padding: 0.4rem 0.9rem;
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(255,255,255,0.08);
    color: #c0bab0;
    transition: all 0.25s;
    clip-path: polygon(6px 0%, 100% 0%, calc(100% - 6px) 100%, 0% 100%);
    cursor: default;
  }
  .skill-tag:hover {
    background: rgba(201,168,76,0.08);
    border-color: rgba(201,168,76,0.35);
    color: var(--gold);
  }
  .skill-tag.highlight {
    background: rgba(0,217,255,0.06);
    border-color: rgba(0,217,255,0.2);
    color: var(--cyan);
  }

  /* ── FOCUS AREAS ── */
  .focus-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5rem;
  }

  .focus-card {
    background: var(--card);
    border: 1px solid rgba(255,255,255,0.06);
    padding: 2rem 1.8rem;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s, border-color 0.3s;
  }
  .focus-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(201,168,76,0.04) 0%, transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .focus-card:hover {
    transform: translateY(-4px);
    border-color: rgba(201,168,76,0.25);
  }
  .focus-card:hover::after { opacity: 1; }

  .focus-icon {
    font-size: 1.8rem;
    margin-bottom: 1rem;
    display: block;
  }
  .focus-card h3 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.4rem;
    letter-spacing: 0.06em;
    color: var(--white);
    margin-bottom: 0.6rem;
  }
  .focus-card p {
    font-size: 0.9rem;
    line-height: 1.7;
    color: var(--dim);
  }
  .focus-number {
    position: absolute;
    top: 1.2rem;
    right: 1.5rem;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 3rem;
    color: rgba(201,168,76,0.06);
    line-height: 1;
  }

  /* ── CURRENTLY ── */
  .currently-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  .currently-item {
    display: grid;
    grid-template-columns: 2rem 1fr;
    gap: 1rem;
    align-items: start;
    padding: 1.2rem 1.5rem;
    background: var(--card);
    border-left: 2px solid transparent;
    border-image: linear-gradient(to bottom, var(--gold), transparent) 1;
    transition: background 0.2s;
  }
  .currently-item:hover { background: rgba(201,168,76,0.04); }
  .curr-icon {
    font-size: 1.1rem;
    padding-top: 0.15rem;
  }
  .curr-text strong {
    display: block;
    font-size: 1rem;
    font-weight: 600;
    color: var(--white);
    margin-bottom: 0.25rem;
  }
  .curr-text span {
    font-size: 0.85rem;
    color: var(--dim);
  }

  /* ── CONTACT ── */
  .contact-section {
    text-align: center;
    padding: 6rem 2rem;
    border-top: 1px solid rgba(201,168,76,0.1);
    background: radial-gradient(ellipse 70% 50% at 50% 0%, rgba(201,168,76,0.05) 0%, transparent 70%);
  }
  .contact-section .section-eyebrow { justify-content: center; }
  .contact-section .section-eyebrow::before { display: none; }

  .contact-big {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(3rem, 8vw, 7rem);
    letter-spacing: 0.05em;
    line-height: 1;
    margin: 0.5rem 0 2.5rem;
    color: var(--white);
  }
  .contact-big span { color: var(--gold); }

  .contact-links {
    display: flex;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
    margin-bottom: 3rem;
  }
  .contact-link {
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.85rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    padding: 0.8rem 2rem;
    text-decoration: none;
    color: var(--white);
    border: 1px solid rgba(255,255,255,0.15);
    transition: all 0.3s;
    clip-path: polygon(10px 0%, 100% 0%, calc(100% - 10px) 100%, 0% 100%);
    display: inline-block;
  }
  .contact-link:hover {
    background: var(--gold);
    color: var(--bg);
    border-color: var(--gold);
  }
  .contact-link.primary {
    background: var(--gold);
    color: var(--bg);
    border-color: var(--gold);
  }
  .contact-link.primary:hover {
    background: transparent;
    color: var(--gold);
  }

  /* ── GITHUB STATS PLACEHOLDER ── */
  .stats-section { text-align: center; }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 1.2rem;
    margin-top: 2rem;
  }
  .stats-card {
    background: var(--card);
    border: 1px solid rgba(201,168,76,0.1);
    padding: 1.8rem 1.2rem;
    transition: border-color 0.3s, transform 0.3s;
    position: relative;
    overflow: hidden;
  }
  .stats-card::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    width: 100%;
    height: 2px;
    background: linear-gradient(90deg, var(--gold), var(--cyan));
    opacity: 0;
    transition: opacity 0.3s;
  }
  .stats-card:hover { border-color: rgba(201,168,76,0.3); transform: translateY(-3px); }
  .stats-card:hover::before { opacity: 1; }

  .stats-icon { font-size: 1.5rem; margin-bottom: 0.7rem; display: block; }
  .stats-value {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2.2rem;
    color: var(--gold);
    line-height: 1;
    margin-bottom: 0.3rem;
  }
  .stats-desc {
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    color: var(--dim);
    text-transform: uppercase;
  }

  /* ── FOOTER ── */
  footer {
    text-align: center;
    padding: 2rem;
    border-top: 1px solid rgba(255,255,255,0.04);
  }
  footer p {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.3em;
    color: rgba(138,131,117,0.4);
    text-transform: uppercase;
  }

  /* ── SEPARATORS ── */
  .cinematic-sep {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 0 2rem;
    max-width: 1100px;
    margin: 0 auto;
    opacity: 0.3;
  }
  .cinematic-sep::before, .cinematic-sep::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold-dim));
  }
  .cinematic-sep::after { background: linear-gradient(90deg, var(--gold-dim), transparent); }
  .sep-text {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.55rem;
    letter-spacing: 0.4em;
    color: var(--gold-dim);
  }

  /* ── SCROLL REVEAL ── */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── TYPING TEXT ── */
  .typewriter {
    border-right: 2px solid var(--cyan);
    white-space: nowrap;
    overflow: hidden;
    animation: typing 3s steps(40) 1s forwards, blink 0.8s step-end infinite;
    max-width: 0;
  }
  @keyframes typing {
    to { max-width: 100%; }
  }
  @keyframes blink {
    50% { border-color: transparent; }
  }
</style>
</head>
<body>

<!-- ═══ HERO ═══ -->
<div class="hero">
  <div class="hero-bg"></div>

  <!-- Stars -->
  <div class="stars" id="stars"></div>

  <!-- Beam sweeps -->
  <div class="beam"></div>
  <div class="beam"></div>
  <div class="beam"></div>

  <div class="hero-content">
    <p class="studio-label">// Portfolio · README · v2.0</p>

    <h1 class="hero-name">
      Tinsae<br><span>Bahiru</span>
    </h1>

    <p class="hero-tagline">
      Machine Learning &nbsp;·&nbsp; <em>Data Science</em> &nbsp;·&nbsp; AI Developer
    </p>

    <div class="hero-divider">
      <span class="hero-divider-icon">◆</span>
    </div>

    <div class="hero-roles">
      <span class="role-pill">Computer Vision</span>
      <span class="role-pill">Deep Learning</span>
      <span class="role-pill">NLP</span>
      <span class="role-pill">MLOps</span>
      <span class="role-pill">Generative AI</span>
    </div>
  </div>

  <div class="scroll-cue">
    <span>Scroll</span>
    <div class="scroll-arrow"></div>
  </div>
</div>

<div class="cinematic-sep"><span class="sep-text">Chapter 01 · Origin</span></div>

<!-- ═══ ABOUT ═══ -->
<section>
  <p class="section-eyebrow reveal">About</p>
  <h2 class="section-title reveal">The Mission</h2>

  <div class="about-grid">
    <div class="about-text reveal">
      <p>
        An aspiring <strong>Machine Learning Engineer, Data Scientist, and AI Developer</strong> passionate about building intelligent systems that solve real-world problems.
      </p>
      <p>
        My work fuses <strong>machine learning, deep learning, computer vision, NLP, predictive analytics, and MLOps</strong> into scalable AI solutions that matter.
      </p>
      <p>
        I turn raw data into insight, and insight into automated decision systems — from model architecture to cloud deployment.
      </p>
    </div>

    <div class="stat-grid reveal">
      <div class="stat-card">
        <div class="stat-num">5+</div>
        <div class="stat-label">Focus Domains</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">∞</div>
        <div class="stat-label">Problems to Solve</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">4</div>
        <div class="stat-label">Cloud Platforms</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">100%</div>
        <div class="stat-label">Committed</div>
      </div>
    </div>
  </div>
</section>

<div class="cinematic-sep"><span class="sep-text">Chapter 02 · Arsenal</span></div>

<!-- ═══ SKILLS ═══ -->
<section class="reveal">
  <p class="section-eyebrow">Skills</p>
  <h2 class="section-title">Technical Arsenal</h2>

  <div class="skills-container">

    <div class="skill-category">
      <p class="skill-cat-title">Machine Learning</p>
      <div class="skill-tags">
        <span class="skill-tag highlight">Scikit-Learn</span>
        <span class="skill-tag highlight">XGBoost</span>
        <span class="skill-tag">Supervised Learning</span>
        <span class="skill-tag">Unsupervised Learning</span>
        <span class="skill-tag">Feature Engineering</span>
        <span class="skill-tag">Model Evaluation</span>
        <span class="skill-tag">Predictive Modeling</span>
      </div>
    </div>

    <div class="skill-category">
      <p class="skill-cat-title">Deep Learning & AI</p>
      <div class="skill-tags">
        <span class="skill-tag highlight">PyTorch</span>
        <span class="skill-tag highlight">TensorFlow</span>
        <span class="skill-tag highlight">Hugging Face</span>
        <span class="skill-tag">CNNs</span>
        <span class="skill-tag">RNNs / LSTMs</span>
        <span class="skill-tag">Transformers</span>
        <span class="skill-tag">Computer Vision</span>
        <span class="skill-tag">NLP</span>
        <span class="skill-tag">Generative AI</span>
      </div>
    </div>

    <div class="skill-category">
      <p class="skill-cat-title">Data Science</p>
      <div class="skill-tags">
        <span class="skill-tag highlight">Python</span>
        <span class="skill-tag highlight">Pandas</span>
        <span class="skill-tag highlight">NumPy</span>
        <span class="skill-tag">Matplotlib</span>
        <span class="skill-tag">Seaborn</span>
        <span class="skill-tag">Plotly</span>
        <span class="skill-tag">SQL</span>
        <span class="skill-tag">Statistical Analysis</span>
        <span class="skill-tag">EDA</span>
      </div>
    </div>

    <div class="skill-category">
      <p class="skill-cat-title">MLOps & Cloud</p>
      <div class="skill-tags">
        <span class="skill-tag highlight">Docker</span>
        <span class="skill-tag highlight">AWS</span>
        <span class="skill-tag highlight">GCP</span>
        <span class="skill-tag">FastAPI</span>
        <span class="skill-tag">Flask</span>
        <span class="skill-tag">MLflow</span>
        <span class="skill-tag">Model Monitoring</span>
        <span class="skill-tag">CI/CD for ML</span>
        <span class="skill-tag">Git</span>
        <span class="skill-tag">Linux</span>
      </div>
    </div>

  </div>
</section>

<div class="cinematic-sep"><span class="sep-text">Chapter 03 · Expertise</span></div>

<!-- ═══ FOCUS AREAS ═══ -->
<section>
  <p class="section-eyebrow reveal">Domains</p>
  <h2 class="section-title reveal">Focus Areas</h2>

  <div class="focus-grid">
    <div class="focus-card reveal">
      <span class="focus-number">01</span>
      <span class="focus-icon">🧠</span>
      <h3>Machine Learning</h3>
      <p>Supervised & unsupervised models, feature engineering, predictive analytics, and rigorous model evaluation pipelines.</p>
    </div>
    <div class="focus-card reveal">
      <span class="focus-number">02</span>
      <span class="focus-icon">👁️</span>
      <h3>Computer Vision</h3>
      <p>CNNs, object detection, image segmentation, and visual recognition systems using PyTorch and TensorFlow.</p>
    </div>
    <div class="focus-card reveal">
      <span class="focus-number">03</span>
      <span class="focus-icon">🗣️</span>
      <h3>NLP</h3>
      <p>Transformers, text classification, sentiment analysis, and language model fine-tuning with Hugging Face.</p>
    </div>
    <div class="focus-card reveal">
      <span class="focus-number">04</span>
      <span class="focus-icon">📊</span>
      <h3>Data Science</h3>
      <p>End-to-end data pipelines — cleaning, EDA, visualization, statistical analysis, and business insight generation.</p>
    </div>
    <div class="focus-card reveal">
      <span class="focus-number">05</span>
      <span class="focus-icon">⚙️</span>
      <h3>MLOps</h3>
      <p>Model deployment, API integration, Docker containers, cloud scaling, and production monitoring systems.</p>
    </div>
    <div class="focus-card reveal">
      <span class="focus-number">06</span>
      <span class="focus-icon">✨</span>
      <h3>Generative AI</h3>
      <p>Large language models, prompt engineering, diffusion models, and building AI-powered applications.</p>
    </div>
  </div>
</section>

<div class="cinematic-sep"><span class="sep-text">Chapter 04 · Current Status</span></div>

<!-- ═══ CURRENTLY ═══ -->
<section>
  <p class="section-eyebrow reveal">Now</p>
  <h2 class="section-title reveal">Current Operations</h2>

  <div class="currently-list reveal">
    <div class="currently-item">
      <span class="curr-icon">🔭</span>
      <div class="curr-text">
        <strong>Active Projects</strong>
        <span>Building AI, Machine Learning, and Data Science projects end-to-end</span>
      </div>
    </div>
    <div class="currently-item">
      <span class="curr-icon">🧪</span>
      <div class="curr-text">
        <strong>Deep Research</strong>
        <span>Exploring Transformers, Reinforcement Learning, and production MLOps workflows</span>
      </div>
    </div>
    <div class="currently-item">
      <span class="curr-icon">☁️</span>
      <div class="curr-text">
        <strong>Cloud Deployment</strong>
        <span>Scaling AI systems on AWS, GCP, and Docker for real-world impact</span>
      </div>
    </div>
    <div class="currently-item">
      <span class="curr-icon">📘</span>
      <div class="curr-text">
        <strong>Knowledge Sharing</strong>
        <span>Explaining and sharing ML/AI concepts to help others on the journey</span>
      </div>
    </div>
    <div class="currently-item">
      <span class="curr-icon">🎯</span>
      <div class="curr-text">
        <strong>Generative AI</strong>
        <span>Experimenting with LLMs, diffusion models, and AI-powered applications</span>
      </div>
    </div>
  </div>
</section>

<div class="cinematic-sep"><span class="sep-text">Chapter 05 · Metrics</span></div>

<!-- ═══ STATS ═══ -->
<section class="stats-section">
  <p class="section-eyebrow reveal" style="justify-content:center; padding-left:0;">before::before{display:none}</p>
  <p class="section-eyebrow reveal" style="justify-content:center;">Profile Stats</p>
  <h2 class="section-title reveal">GitHub Activity</h2>

  <div class="stats-grid reveal">
    <div class="stats-card">
      <span class="stats-icon">⭐</span>
      <div class="stats-value">Stars</div>
      <div class="stats-desc">Earned from repos</div>
    </div>
    <div class="stats-card">
      <span class="stats-icon">🔥</span>
      <div class="stats-value">Streak</div>
      <div class="stats-desc">Days consecutive</div>
    </div>
    <div class="stats-card">
      <span class="stats-icon">📦</span>
      <div class="stats-value">Repos</div>
      <div class="stats-desc">Public projects</div>
    </div>
    <div class="stats-card">
      <span class="stats-icon">🤝</span>
      <div class="stats-value">PRs</div>
      <div class="stats-desc">Contributions</div>
    </div>
  </div>

  <p style="margin-top: 2rem; font-family: 'Share Tech Mono', monospace; font-size: 0.65rem; color: var(--dim); letter-spacing: 0.2em;">
    📌 Embed live stats via github-readme-stats or streak-stats on the real README
  </p>
</section>

<!-- ═══ CONTACT ═══ -->
<div class="contact-section">
  <p class="section-eyebrow">Contact</p>
  <h2 class="contact-big">Let's <span>Build</span><br>Something.</h2>

  <div class="contact-links">
    <a href="https://github.com/TinsaeBahiru" class="contact-link primary">GitHub</a>
    <a href="https://linkedin.com/in/tinsaebahiru" class="contact-link">LinkedIn</a>
    <a href="mailto:tinsae@email.com" class="contact-link">Email</a>
    <a href="#" class="contact-link">Portfolio</a>
  </div>

  <p style="font-family: 'Share Tech Mono', monospace; font-size: 0.65rem; letter-spacing: 0.3em; color: var(--dim);">
    // Open to collaborations · Research · Projects · Opportunities
  </p>
</div>

<!-- ═══ FOOTER ═══ -->
<footer>
  <p>Tinsae Bahiru · Built with Precision · © 2025 · All Rights Reserved</p>
</footer>

<script>
// Generate stars
const starsEl = document.getElementById('stars');
for (let i = 0; i < 120; i++) {
  const s = document.createElement('div');
  s.className = 'star';
  s.style.cssText = `left:${Math.random()*100}%;top:${Math.random()*100}%;--d:${2+Math.random()*4}s;--delay:${Math.random()*5}s;opacity:${0.1+Math.random()*0.6};width:${Math.random()<0.8?1:2}px;height:${Math.random()<0.8?1:2}px`;
  starsEl.appendChild(s);
}

// Fix the section-eyebrow that got duplicated
document.querySelectorAll('.section-eyebrow').forEach(el => {
  if (el.textContent.includes('before::before')) el.remove();
});

// Scroll reveal
const reveals = document.querySelectorAll('.reveal');
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry, i) => {
    if (entry.isIntersecting) {
      setTimeout(() => entry.target.classList.add('visible'), i * 60);
    }
  });
}, { threshold: 0.1 });
reveals.forEach(el => observer.observe(el));
</script>

</body>
</html>
