<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cevora | Sites que Convertem</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --cyan: #00FFEA;
    --cyan-dim: #00C9B8;
    --cyan-dark: #007A6F;
    --black: #050808;
    --black-2: #0D1111;
    --black-3: #141A1A;
    --black-4: #1C2424;
    --text: #E8F0EF;
    --text-muted: #7A9A97;
    --border: rgba(0, 255, 234, 0.12);
    --border-hover: rgba(0, 255, 234, 0.35);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    overflow-x: hidden;
    cursor: default;
  }

  /* ── CURSOR ── */
  .cursor {
    width: 10px; height: 10px;
    border-radius: 50%;
    background: var(--cyan);
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s ease, width 0.2s, height 0.2s, opacity 0.2s;
    mix-blend-mode: difference;
  }

  /* ── GRID BG ── */
  .grid-bg {
    position: fixed; inset: 0; z-index: 0;
    background-image:
      linear-gradient(rgba(0,255,234,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,234,0.04) 1px, transparent 1px);
    background-size: 48px 48px;
    pointer-events: none;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.25rem 5vw;
    background: rgba(5,8,8,0.85);
    backdrop-filter: blur(14px);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    font-family: 'Space Mono', monospace;
    font-size: 1.35rem;
    color: var(--cyan);
    letter-spacing: -0.02em;
    text-decoration: none;
  }
  .nav-logo span { color: var(--text); }

  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    color: var(--text-muted);
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--cyan); }

  .nav-cta {
    background: transparent;
    border: 1px solid var(--cyan);
    color: var(--cyan);
    font-family: 'Space Mono', monospace;
    font-size: 0.8rem;
    padding: 0.55rem 1.2rem;
    cursor: pointer;
    transition: background 0.2s, color 0.2s;
    letter-spacing: 0.06em;
    text-decoration: none;
  }
  .nav-cta:hover { background: var(--cyan); color: var(--black); }

  /* ── HERO ── */
  #hero {
    position: relative; z-index: 1;
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center; align-items: flex-start;
    padding: 8rem 5vw 4rem;
    overflow: hidden;
  }

  .hero-tag {
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    color: var(--cyan);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    display: flex; align-items: center; gap: 0.6rem;
  }
  .hero-tag::before {
    content: '';
    display: inline-block;
    width: 28px; height: 1px;
    background: var(--cyan);
  }

  .hero-title {
    font-size: clamp(3rem, 8vw, 7rem);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.03em;
    max-width: 800px;
    margin-bottom: 2rem;
  }
  .hero-title .accent { color: var(--cyan); }

  .hero-sub {
    font-size: 1.1rem;
    color: var(--text-muted);
    max-width: 480px;
    line-height: 1.7;
    margin-bottom: 2.8rem;
  }

  .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; }

  .btn-primary {
    background: var(--cyan);
    color: var(--black);
    border: none;
    font-family: 'Space Mono', monospace;
    font-size: 0.85rem;
    font-weight: 700;
    letter-spacing: 0.05em;
    padding: 0.9rem 2rem;
    cursor: pointer;
    transition: background 0.2s, transform 0.15s;
    text-decoration: none;
  }
  .btn-primary:hover { background: var(--cyan-dim); transform: translateY(-2px); }

  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border-hover);
    font-family: 'Space Mono', monospace;
    font-size: 0.85rem;
    letter-spacing: 0.05em;
    padding: 0.9rem 2rem;
    cursor: pointer;
    transition: border-color 0.2s, color 0.2s;
    text-decoration: none;
  }
  .btn-ghost:hover { border-color: var(--cyan); color: var(--cyan); }

  /* ── FLOATING CIRCLES ── */
  .orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
  }
  .orb-1 {
    width: 500px; height: 500px;
    background: rgba(0,255,234,0.06);
    right: -120px; top: 20%;
    animation: float 8s ease-in-out infinite;
  }
  .orb-2 {
    width: 300px; height: 300px;
    background: rgba(0,200,184,0.04);
    right: 20%; top: 60%;
    animation: float 12s ease-in-out infinite reverse;
  }
  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-40px); }
  }

  /* ── SCAN LINE ── */
  .scanline {
    position: absolute; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--cyan), transparent);
    top: 0;
    animation: scan 6s linear infinite;
    opacity: 0.3;
  }
  @keyframes scan {
    0% { top: 0; opacity: 0; }
    10% { opacity: 0.3; }
    90% { opacity: 0.3; }
    100% { top: 100%; opacity: 0; }
  }

  /* ── STATS ── */
  .stats-bar {
    position: relative; z-index: 1;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    display: flex; align-items: stretch;
  }
  .stat-item {
    flex: 1;
    padding: 2rem;
    text-align: center;
    border-right: 1px solid var(--border);
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }
  .stat-item:last-child { border-right: none; }
  .stat-item:hover { background: rgba(0,255,234,0.04); }
  .stat-num {
    font-family: 'Space Mono', monospace;
    font-size: 2.4rem;
    color: var(--cyan);
    display: block;
    line-height: 1;
    margin-bottom: 0.4rem;
  }
  .stat-label {
    font-size: 0.8rem;
    color: var(--text-muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  /* ── SECTION ── */
  section { position: relative; z-index: 1; padding: 6rem 5vw; }

  .section-tag {
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    color: var(--cyan);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }

  .section-title {
    font-size: clamp(1.8rem, 3.5vw, 3rem);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -0.02em;
    margin-bottom: 1rem;
  }

  .section-sub {
    font-size: 1rem;
    color: var(--text-muted);
    max-width: 480px;
    line-height: 1.7;
    margin-bottom: 3rem;
  }

  /* ── SERVIÇOS ── */
  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
  }

  .service-card {
    background: var(--black-2);
    padding: 2.5rem 2rem;
    transition: background 0.3s;
    cursor: default;
    position: relative;
    overflow: hidden;
  }
  .service-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    width: 0; height: 2px;
    background: var(--cyan);
    transition: width 0.4s ease;
  }
  .service-card:hover { background: var(--black-3); }
  .service-card:hover::after { width: 100%; }

  .service-icon {
    font-family: 'Space Mono', monospace;
    font-size: 1.8rem;
    color: var(--cyan);
    margin-bottom: 1.2rem;
    display: block;
  }

  .service-title {
    font-size: 1.1rem;
    font-weight: 800;
    margin-bottom: 0.7rem;
  }

  .service-desc {
    font-size: 0.88rem;
    color: var(--text-muted);
    line-height: 1.65;
  }

  /* ── PROCESSO ── */
  #processo { background: var(--black-2); }

  .process-list {
    display: flex;
    flex-direction: column;
    gap: 0;
    max-width: 760px;
  }

  .process-step {
    display: grid;
    grid-template-columns: 56px 1fr;
    gap: 0 1.5rem;
    padding: 2rem 0;
    border-bottom: 1px solid var(--border);
    position: relative;
  }
  .process-step:last-child { border-bottom: none; }

  .step-num {
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    color: var(--cyan);
    padding-top: 0.2rem;
    letter-spacing: 0.05em;
  }

  .step-title {
    font-size: 1.1rem;
    font-weight: 800;
    margin-bottom: 0.4rem;
  }

  .step-desc {
    font-size: 0.9rem;
    color: var(--text-muted);
    line-height: 1.6;
  }

  /* ── PORTFOLIO ── */
  .portfolio-tabs {
    display: flex; gap: 0; margin-bottom: 2rem;
    border: 1px solid var(--border); width: fit-content; flex-wrap: wrap;
  }
  .tab-btn {
    background: transparent; color: var(--text-muted);
    border: none; border-right: 1px solid var(--border);
    font-family: 'Space Mono', monospace; font-size: 0.75rem;
    letter-spacing: 0.08em; padding: 0.65rem 1.3rem; cursor: pointer;
    transition: background 0.2s, color 0.2s; text-transform: uppercase;
  }
  .tab-btn:last-child { border-right: none; }
  .tab-btn:hover { color: var(--cyan); background: rgba(0,255,234,0.04); }
  .tab-btn.active { background: var(--cyan); color: var(--black); font-weight: 700; }

  .portfolio-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.5rem;
  }
  .portfolio-card {
    background: var(--black-3); border: 1px solid var(--border);
    aspect-ratio: 16/10; position: relative; overflow: hidden;
    cursor: pointer; transition: border-color 0.3s, transform 0.3s;
  }
  .portfolio-card:hover { border-color: var(--border-hover); transform: translateY(-3px); }
  .portfolio-card:hover .portfolio-overlay { opacity: 1; }
  .portfolio-card.hidden { display: none; }

  .portfolio-mock {
    width: 100%; height: 100%; display: flex; flex-direction: column;
    padding: 10px 12px 28px; gap: 6px;
  }
  .portfolio-shot {
    width: 100%; height: 100%; object-fit: cover; object-position: top;
    display: block; filter: saturate(0.9); transition: transform 0.4s ease, filter 0.4s ease;
  }
  .portfolio-card:hover .portfolio-shot { transform: scale(1.04); filter: saturate(1); }
  .mock-header { display: flex; gap: 4px; margin-bottom: 4px; }
  .mock-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--border-hover); opacity: 0.5; }
  .mock-hero-block { width: 100%; height: 44px; background: rgba(0,255,234,0.06); border-radius: 2px; }
  .mock-lines { display: flex; flex-direction: column; gap: 5px; padding-top: 4px; }
  .mock-btn-row { display: flex; gap: 6px; margin-top: 4px; }
  .mock-btn { height: 10px; width: 60px; background: var(--cyan); opacity: 0.6; border-radius: 2px; }
  .mock-two-col { display: flex; gap: 8px; flex: 1; align-items: flex-start; padding-top: 4px; }
  .mock-col-text { flex: 1; display: flex; flex-direction: column; gap: 5px; }
  .mock-col-img { width: 60px; height: 52px; background: rgba(0,255,234,0.08); border-radius: 2px; flex-shrink: 0; }
  .mock-cards-row { display: flex; gap: 6px; margin-top: 6px; }
  .mock-card-sm { flex: 1; height: 20px; background: rgba(0,255,234,0.06); border-radius: 2px; }
  .mock-product-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; padding-top: 4px; flex: 1; }
  .mock-product { background: rgba(0,255,234,0.07); border-radius: 2px; min-height: 32px; }

  .portfolio-mock-bar { height: 5px; background: var(--border); border-radius: 2px; position: relative; overflow: hidden; }
  .portfolio-mock-bar::after {
    content: ''; position: absolute; left: 0; top: 0; height: 100%;
    background: var(--cyan); animation: barpulse 2s ease-in-out infinite;
  }
  @keyframes barpulse { 0%, 100% { opacity: 0.3; } 50% { opacity: 1; } }

  .portfolio-label {
    position: absolute; bottom: 0; left: 0; right: 0;
    padding: 0.8rem 1rem;
    background: linear-gradient(transparent, rgba(5,8,8,0.97));
    font-size: 0.85rem; font-weight: 600;
  }
  .portfolio-sub { font-size: 0.72rem; color: var(--text-muted); font-family: 'Space Mono', monospace; }
  .portfolio-overlay {
    position: absolute; inset: 0; background: rgba(0,255,234,0.07);
    opacity: 0; transition: opacity 0.3s; display: flex; align-items: center; justify-content: center;
  }
  .portfolio-overlay span {
    font-family: 'Space Mono', monospace; font-size: 0.8rem; color: var(--cyan);
    letter-spacing: 0.1em; border: 1px solid var(--cyan); padding: 0.5rem 1.2rem;
  }

  /* ── CTA FINAL ── */
  #cta {
    background: var(--black-2);
    text-align: center;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
  }

  .cta-terminal {
    font-family: 'Space Mono', monospace;
    font-size: 0.8rem;
    color: var(--text-muted);
    background: var(--black-4);
    border: 1px solid var(--border);
    display: inline-block;
    padding: 0.5rem 1.2rem;
    margin-bottom: 2rem;
    text-align: left;
    max-width: 380px;
    width: 100%;
  }
  .cta-terminal .prompt { color: var(--cyan); }
  .cta-terminal .cursor-blink {
    display: inline-block;
    width: 8px; height: 14px;
    background: var(--cyan);
    vertical-align: middle;
    animation: blink 1s step-end infinite;
    margin-left: 2px;
  }
  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

  #cta .section-title { margin: 0 auto 1rem; max-width: 600px; }
  #cta .section-sub { margin: 0 auto 2.5rem; }

  /* ── FOOTER ── */
  footer {
    position: relative; z-index: 1;
    padding: 2rem 5vw;
    border-top: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .footer-logo {
    font-family: 'Space Mono', monospace;
    font-size: 1rem;
    color: var(--cyan);
  }

  .footer-copy {
    font-size: 0.78rem;
    color: var(--text-muted);
    font-family: 'Space Mono', monospace;
  }

  /* ── SCROLL FADE IN ── */
  .reveal {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── RESPONSIVO ── */
  @media (max-width: 640px) {
    nav { padding: 1rem 4vw; }
    .nav-links { display: none; }
    .stats-bar { flex-direction: column; }
    .stat-item { border-right: none; border-bottom: 1px solid var(--border); }
    .stat-item:last-child { border-bottom: none; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="grid-bg"></div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">CEV<span>ORA</span></a>
  <ul class="nav-links">
    <li><a href="#servicos">Serviços</a></li>
    <li><a href="#processo">Processo</a></li>
    <li><a href="#portfolio">Portfólio</a></li>
    <li><a href="#cta">Contato</a></li>
  </ul>
  <a href="https://wa.me/5518991159643" class="nav-cta">Iniciar Projeto →</a>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="scanline"></div>
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>

  <div class="hero-tag">Agência Digital · Est. 2024</div>

  <h1 class="hero-title">
    Sites que<br>
    <span class="accent">convertem.</span><br>
    Ponto final.
  </h1>

  <p class="hero-sub">
    Criamos landing pages e sites que transformam visitantes em clientes.
    Design preciso, tecnologia moderna, resultados reais.
  </p>

  <div class="hero-actions">
    <a href="#cta" class="btn-primary">Quero meu site</a>
    <a href="#portfolio" class="btn-ghost">Ver portfólio</a>
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-item reveal">
    <span class="stat-num">97%</span>
    <span class="stat-label">Taxa de satisfação</span>
  </div>
  <div class="stat-item reveal">
    <span class="stat-num">+3x</span>
    <span class="stat-label">Conversão média</span>
  </div>
  <div class="stat-item reveal">
    <span class="stat-num">48h</span>
    <span class="stat-label">Primeiro rascunho</span>
  </div>
  <div class="stat-item reveal">
    <span class="stat-num">∞</span>
    <span class="stat-label">Suporte contínuo</span>
  </div>
</div>

<!-- SERVIÇOS -->
<section id="servicos">
  <p class="section-tag reveal">// O que fazemos</p>
  <h2 class="section-title reveal">Nossos serviços</h2>
  <p class="section-sub reveal">Do conceito ao ar — entregamos cada projeto com atenção cirúrgica a cada detalhe.</p>

  <div class="services-grid">
    <div class="service-card reveal">
      <span class="service-icon">&lt;/&gt;</span>
      <h3 class="service-title">Landing Pages</h3>
      <p class="service-desc">Páginas criadas para converter. Cada elemento pensado para guiar o visitante à ação certa no momento certo.</p>
    </div>
    <div class="service-card reveal">
      <span class="service-icon">⬡</span>
      <h3 class="service-title">Sites Institucionais</h3>
      <p class="service-desc">Presença digital profissional que comunica credibilidade e diferencia sua marca da concorrência.</p>
    </div>
    <div class="service-card reveal">
      <span class="service-icon">◈</span>
      <h3 class="service-title">UI/UX Design</h3>
      <p class="service-desc">Interfaces que as pessoas entendem na primeira visita — intuitivas, bonitas e funcionais ao mesmo tempo.</p>
    </div>
    <div class="service-card reveal">
      <span class="service-icon">⚡</span>
      <h3 class="service-title">Performance & SEO</h3>
      <p class="service-desc">Sites rápidos, indexáveis e bem posicionados. Velocidade de carregamento e visibilidade orgânica que geram tráfego real.</p>
    </div>
  </div>
</section>

<!-- PROCESSO -->
<section id="processo">
  <p class="section-tag reveal">// Como trabalhamos</p>
  <h2 class="section-title reveal">Do briefing ao ar<br>em 4 etapas</h2>
  <p class="section-sub reveal">Um processo claro e direto, com você no controle de cada decisão.</p>

  <div class="process-list">
    <div class="process-step reveal">
      <span class="step-num">01 /</span>
      <div>
        <h3 class="step-title">Descoberta</h3>
        <p class="step-desc">Entendemos seu negócio, público-alvo e objetivos. Quanto mais soubermos sobre você, mais cirúrgico será o projeto.</p>
      </div>
    </div>
    <div class="process-step reveal">
      <span class="step-num">02 /</span>
      <div>
        <h3 class="step-title">Estratégia & Wireframe</h3>
        <p class="step-desc">Definimos estrutura, hierarquia e fluxo de conteúdo antes de qualquer pixel de design. A base de tudo.</p>
      </div>
    </div>
    <div class="process-step reveal">
      <span class="step-num">03 /</span>
      <div>
        <h3 class="step-title">Design & Desenvolvimento</h3>
        <p class="step-desc">Transformamos estratégia em interface. Codificamos com tecnologias modernas, performáticas e escaláveis.</p>
      </div>
    </div>
    <div class="process-step reveal">
      <span class="step-num">04 /</span>
      <div>
        <h3 class="step-title">Entrega & Suporte</h3>
        <p class="step-desc">Deploy, treinamento e suporte pós-lançamento. Seu site no ar e você independente para gerenciá-lo.</p>
      </div>
    </div>
  </div>
</section>

<!-- PORTFÓLIO -->
<section id="portfolio">
  <p class="section-tag reveal">// Trabalhos recentes</p>
  <h2 class="section-title reveal">Portfólio</h2>
  <p class="section-sub reveal">Uma amostra do que construímos. Cada projeto, uma solução sob medida.</p>

  <div class="portfolio-tabs reveal">
    <button class="tab-btn active" data-filter="all">Todos</button>
    <button class="tab-btn" data-filter="landing">Landing Pages</button>
    <button class="tab-btn" data-filter="institucional">Institucionais</button>
  </div>

  <div class="portfolio-grid" id="portfolio-grid">

    <div class="portfolio-card reveal" data-cat="institucional">
      <div class="portfolio-mock" style="padding:0;">
        <img class="portfolio-shot" src="data:image/jpeg;base64,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IgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiCUUKUBSoRBKIiKIilQEREBSoRBKIiKKVCIJRQpQEREEooRQSihSgIiIJRQpQEUKUBERAREQERFAREQEREBERAREVBERAREQEREBFCIJUIiAiIgIiIChEQEREFpERbZEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAUqEQSpUKVAREQFKhEVKKFKgIiIJREQEREBSoRFSihEEoiIClQiCUUZUoCIigIiICIiApUIglFCIJRQiBlMoiBlERAUqEQSoREBERARQiCUUIqGUREBERARFGUBEREW0UotIhFKIIRSiCEUoghFn2m2G61ckPpEdMyKGSofJIHODWsGTsNysip09U0xuXFNC9tvgjqC5hJErJC0NLdu8PB3wsTqVidszy1FJmMvIRbHctGVttZQOkqIXCtljhb6r24c9rXA7j1hhwyW5wdlZq9LVFLeZ7b6Q10lPTy1D3PifGMRgkgBwBOeHY9FiNfTnmJX27eHhIvVks8bNPQ3QXCJ5mkMLacRv4+MAEjOMbBwOc7q7d9NzWmmfKaunqDBN6NUsi4swS8JdwnIGeh3G2QVr3aZxlNk9XiovdtWlqq72ae4QzxMbE57Qx7XblkfMOXAYbt0yRk7K1U6fmpdO0l3fMDHVjiYwRP2HE5u78cIOWnbOVPepnbnnouy2M4eOi9+/6Qr9OxSS1UkUjGTNha6MkiTLC7I+WC0jqCFNVo+vo7/brTLJCJrg1pY8Z4WEkgtO3VpGCpGvpzGYk9u3TDX0UquaCWnkMc0T4ngA8LwQcEZHmCCuzGFtF7c2nmsbauTcoJ33MtETRG9vCC8sySR3OBH8VerdHVtFf6K1GWN8tbngcWuZwgOLSXNcA4AcJOcbjcLl71PPn8urft28fcteRbBR6RrKvUNdaOcxktE0vc4Me8PALQC0NGTniB+SootJ11fcrnRQvhMltD+M5JbI5pIDWnG5dg4+Snv6cd/me3bx8nhIsx9vkjssFzL2mKaZ8DWjPEC1rXE/L1gvRr9JXG3Wt9wnAFM1kD2vwcSc1uQGnvI71qdSkYiZSKzLwkWxwaNqprrc6A1dOyS3ENeQ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raJgV8+X3r/uTny+9f8AcqEUxBlXz5fev+5OfL71/wByoRMQZV8+X3r/ALlPPl96/wA1bRMQZXOfL71/mnPl96/zVtExBlc58vvX+ac+X3r/ADVtExBlc58vvX/co58vvX/cqETEGVfPl96/7k58vvX/AHKhExBlXz5fev8AuU8+X3r/ALlbRMQZXOfL71/mnPl96/zVtExBlc58vvX+ac+X3r/NW0TEGVzny+9f5qOfL71/3KhExBlXz5fev+5OfL71/wByoRMQZV8+X3r/ALk58vvX/cqETEGVzny+9f5pz5fev81bRMQZVOe9+OJxdjxKpRFQREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERBcZ7J+aqVDOhVSglFCIJRERRSFClAUqFKAiIoCIiApUIglSoUoCKFKAiIgIiIHcidyIClQpQEUIglFCICIiqCIiKIiIClQiCUUIiJRQiDFREVBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERBWzoVUqWdCqkBERQEREBTlQiolTlQiglFCKiUUKVBKKEQSpUZTKCUyoRBOUyoRBKKFKCUUIglFCZQSijKZVEooRBKhEUBERAREQSiIqCIiAiIgxUREBERAUqFKAiIgIiIIRSoQEREBEUoCLKmtVwpqRtVPb6uGnf7MskD2sPycRhYqAiIghFKhAREQERSgIiICLYdOaE1Fqygra2z281FPRDMry9rBnGeFufadjfAWvJmJ4MIRSoQEREBEVTI3yOwxjnkDOGgnb6IIREQEREBQpUICIiAiIglERAREQFCZHiEQEREBFVwP5fM4HcGccWDjPz6KlAUoiAiIgKFKhAREQEREBSiICIiCpnRVKlnQqpAREQEREBERBKIigIiKgpChEEoiKAiKVRCKUQQilEAIilBCIpwQMkKCFKhSqCIiAiIgBSoClQEUIglFClAREVBERAREQYyIioIiICIiAiIiL1JLFBVxyz0zKqJpy6F73MDx4EtII+i+hbT2X6CuHZzDqp9mq2F9A6sdTivkIBDSS0HrjI6r50HVfWGmv8Au5U/9Ry/3Hrz68zERiXXTiJzl85Ud50vJOBcNJllO4jLqK4S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tnMzmfPXn/TtvpGvHPERiHO6qpkraqaqmdxSTvdI8nvLjk/8VuvZBZY7rrhlRIwOit8ZqMY2L84Z/E5+i86oj0tp+pNRb7jLf52HMEb6YxQxnudITu/H5QAD37bL0OzHWFHpnUlXNdXubBXR8L5ms4uB4dxAkDuOT06L6fqbXv6e8aUT047fl16PLpRFdSN8sfX9TU6l7Tqylp8yPEzaKBv+7t/xyVuvaoPwfRVk0rQtdI55A4WDJcyJvXA8XHP0WqS3vT9m1tLdaGrkuZqazmvlEJY2nhc/Lw0O3c8jIzsAM43O3odoWrLLc7sbna7i+tqHUZpIYxC5jafiJ43lzsZJBIAA78k7Lx7LzfRrFZ21jx3x38f1dt0RW8zPM/4c0RMJhfaeERMJhAREVQREQERMKKImEwgImEwgIiKoIiICImEURMJhQETCYQERFUEREBERRREwmEBEwmEBERVBERBWz2T81Khnsn5qpSVQilMIqEU4TCCEU4REQilEEKURAUqEUBVRe2fkqVVF7Z+Sork9gqJeg+amT2Col6N+aKo70KIiJi9s/JXVai9s/JXkEEZGFQYs/wA7+CqceFuSqeaPylFVNHC0DOVKpDiRkNKnJ/IfNALAXZO6iT2fqpDwTg5B+Kh/s/VBSEREQREUFLuhVf8AmPoqD0Vf+Y+iorVDvaKuK272iioREQEREBEREEREFhERVBERAREUBERAREVURERBERARERRERARERBERBXBJyaiOUsbII3h3A7o7Bzg/Are9aatsWuWUNRI+stVVSsMZiMImiIJB2IcCOnh0WgouN9Gt7VvPWOn9XSt5rE17S2S1323aZl9LtEM9XdA0iOqq2tYyAkYLmRgnLsd7jt4LXpppaieSeaR0ksji973HJcTuSVQi1XTiszbvLM2mYx2ERFtkREVUREQEREBERARERBERQERFQREQEREBERQEREBERUEREBERARERRERAREUQREVBERAREUBERBWz2T81Khnsn5qUUREQEREURERBERFEREBERAVUXtn5KlVRe2fkguSewVEvQfNTJ+7KiXo35oihEUIqqL2z8ldVqL2z8ldRFMn7sq0QrsnsFWj0QXmewFKpj/dhVILUoy76KonLBvuok9v6KkDCCcIiICIiCD0Vf+Y+ioPRV/5j6IK1Q72iq1Q72iioREQEREBERARE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" alt="Site Fábio Lima Advogado">
      </div>
      <div class="portfolio-overlay"><span>VER PROJETO →</span></div>
      <div class="portfolio-label">Fábio Lima Advogado<div class="portfolio-sub">Site Institucional · Jurídico</div></div>
    </div>

    <div class="portfolio-card reveal" data-cat="landing">
      <div class="portfolio-mock" style="padding:0;">
        <img class="portfolio-shot" src="data:image/jpeg;base64,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hQAIFAAAIUgUAIAAAEAAAABUBSAAAAIUgAAAQABQgAAgAUAAAhSAAAUACEAAAQAACFIFAABAUhQAAAhSAAAZEABiQABkQAEyoAQZAAFAhSGgABqAIUhqFAAUQAACFIFAAAAAH0QAMOIIAAIAVQAgAAAACBQAgAAgAAgUAAAAACABQgBUCABQAACAEAAhVACAAAAAIFACAAAAIAAAAUAIAAAAgAAAgAABQgAAgAAABQAACAFAAhAAAUIAAAIAAAAAhQAAAAACAEkCAGQIUhlQAGQAIYAAAAAagQAGgAIahQAGhAAaAAgAABQgADYAA+jIAZcQQAKEAAAAAQAKAEAAEAAECgAAAEAAAAQAAQAqgAAEAIABCgAQKAAACAAAQKAEApAAABAqkAAAAAQAAAQAAABAAoQAKAEAoIAAAKABCAAABAAAIAoAQCk2AUAAAAAAgAAEBJUAIZFIAZkAQGZAAGQAITApADUAAQ0oADUACA0BADSgAAEAAAAAAAPoiAGXGEAAAAAQAKEAAAACAACAAKAACAAAQAAQAqgAAgAIAAKIAAqAAAAAIAAqAACAAAAAqAAAAABAAAAAgAChAABAAoAABAAAAKAAIIAABAAAACoAABACgAAAAAEAAEAAAAihADIAAzIgAMyAAIBAABACgADShADUAPcAaEABVQAAAAAIAAAAH//Z" alt="Site Clínica Rosa Lúcia">
      </div>
      <div class="portfolio-overlay"><span>VER PROJETO →</span></div>
      <div class="portfolio-label">Clínica Rosa Lúcia<div class="portfolio-sub">Landing Page · Estética</div></div>
    </div>

    <div class="portfolio-card reveal" data-cat="institucional">
      <div class="portfolio-mock" style="padding:0;">
        <img class="portfolio-shot" src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAcFBQYFBAcGBgYIBwcICxILCwoKCxYPEA0SGhYbGhkWGRgcICgiHB4mHhgZIzAkJiorLS4tGyIyNTEsNSgsLSz/2wBDAQcICAsJCxULCxUsHRkdLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCz/wAARCAGYA4QDASIAAhEBAxEB/8QAHQABAAEFAQEBAAAAAAAAAAAAAAYBAgUHCAQDCf/EAF4QAAEDAwEEBAYJDgsGBQMFAAEAAgMEBREGBxIhMRMiQVEIFGFxkbEVMjdScoGhsrMWJzM1NkJzdHWSk5TR0hcYIzRUVVZkZYLBJCY4YmOiJUPCw9OE4eJ2g6Pw8f/EABsBAQADAQEBAQAAAAAAAAAAAAABAgMEBQYH/8QAPBEBAAEDAgMECAUBBgcAAAAAAAECAxEEITFBUQUSYXEGE3KRobHB0RQWIjLwgRUzNEJSYiM1Q1NjsuH/2gAMAwEAAhEDEQA/AOeEREBEWVsOm7pqWrkp7XTtldEzpJHPkbGxjc4yXOIA4qldym3TNdc4iOcpiJmcQxSKR0WgdSV93rrbFbw2poCBUdLKyNjCfajeJwc9mOaW3QGpbrWVtLTW4iWhkEM4llbGGvPJgLjgk9wWE63TxmZuU7YnjHCeHvX9XX0lHEX3NHUNrzROic2pEvQmN3Ah+d3B+PgpHcNmuqrZrKk0tUWzN4rGCSGGOVrw5pzx3gcADdOc8sLpic7wzRVFKLjs61NatT26wVVva2vuZApAyZj45cnHB4O7wPPuX0p9meqKnWVZpaOihF2ooumnidUMa1rMNOd8nB4OCkRNFsTT+yG9VWuJbDe6eWlFNRmvlNPLC4vi5NLHucGEF3DOeGCvNc9lF8ZeNQQ2eNlfRWSMVEsrp4g4ROaXtJDXEF2GnIaTy8qCCIpjHsp1dLUWKBtvi6S/xOnoQalg6RjWB5J49XqkHBXytOzHVt8sEt5t9r6ajiMgB6ZjXydH7fcYTl+MHl3IImildFsz1ZcNJnUlLauktoifMHdKwSPjacOe2PO8WjvAUUQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEW39n+yixao0ZTXevqa9s875GlsMjWtAa4tHNp7lJf4CNK/0u6/pmfuL52/6R6KxcqtVzOaZmJ26OynRXa6Yqjm57RdCfwEaV/pd1/TM/cT+AjSv9Luv6Zn7iy/NGg6z7lvwF1z2i6E/gI0r/S7r+mZ+4n8BGlf6Xdf0zP3E/NGg6z7j8Bdc9ouhP4CNK/0u6/pmfuJ/ARpX+l3X9Mz9xPzRoOs+4/AXXPaLoT+AjSv9Luv6Zn7ifwEaV/pd1/TM/cT80aDrPuPwF1z2i6E/gI0r/S7r+mZ+4n8BGlv6Vdf0zP3E/NGg6z7j8Bdc9ouhP4CNK/0u6/pmfuJ/ARpX+l3X9Mz9xPzRoOs+4/AXXPaLoT+AjS39Luv6Zn7i0zraxU2mtaXG0UkkslPTPaGOlILsFjXcSMd679D2zptfcm3ZmcxGd4/nVld01dqO9UwKIi9hzCIiAiIgKYaBrTSC8MraCWrsNTTthuT4iA6BjnYZIPKHdih6yli1HddNVclTaqrxeSVnRvBY17XtznBa4EHiuXV2qr1mq3TxnrmOfWOE9J5S0t1RTVEy2bUUFbbLbrKjuFc+4Tx3K24qJPbSML2lhPl3cBe6skkqNdaktNdBUQ2uuu8Lae4wEb1JWhjTGcdoPBaxotd6kt93rbnBc3+NVxBqHSMa8SEcstIxw7MDglt15qW01dZU0l0eJq6TpZ3SMbJvP8AfYcDg+ULwJ7J1P6pzTM4jHGN8Ub7Rtiacxxic4mMOr8RRtx/mfuyukLRVVm3C12y4SGpqW3dvjD856QsfvOd8e6St/VVJXP206Fu1wjaypqKa507g2RrwAzpHM4tJHtXhcv2bUl1sOoo77b6rcuUbnvbO9jZDvOBDjhwIycnj5V7qHXmpLZS2uno7m6BlpqJKqkLY270b353+OMkHJyDkcV9NRE00xEuKd5bK2aWrUk+stEVFykgqLdTUNbV2qJpa0xtaHDDjgY67m8SSpfWUNTT7XrhW1sbWVFw0U+aYBweBI1gY8bw4HBbzWka3afq643Oor6q6iSoqKJ9ucegjDRA/wBsxrQ3Dc944+VW23aZqu0VFBPR3GOOS3UbrfTl1NG/dgJBLDlvW4gcTxV0N62zxIGj8fbK6kGzhvTiEgSGPeGd3PDOM4zwWC2EGzS0+taa1tqmWqukpqOEVZaZd2VsjBvFvDOT2LVsO1fWcGpZ7+27h1xqKYUj3vponN6EHIYGFu6BnjwHerBtR1c241dcy5Rx1FZJTyzOZSxNDnQHeiOA3Awe7n25QdIVnRx7S9mtLEQWUXsjRjH/AEoWsPytK1xTw6hqNFbOo9K1ENPdzNeOjkl3d0N3nb44gji3PYtbjalq9t0oLj7Kt8at0tRNTvNPGdx85JlOMYOcnny7ML5WraXq6yWCey2+8PgoZy8lgjYXNL/b7jiN5mcnkRzQbr0x9q9I/wD6Mr/nMXNLfaN8wUqo9pOrbfpN2mqW8yRWp0bouiEbC5rHe2YH43g09wKiyAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiDKadpaetvsMFVA+oiLXkxsOC4hpI4ZBPHHAEE8hxUhl09QQUt5c2ibNNTThkbY3SShjTFvdhBGD77OORyoUmB3D0IJtU2jT9JQ2ueWIObJJTsqDHK7LQ+LecX5OBxILd3uIK8lTYbbRePUMz2mpoaNj5pmyZHSumaCQORAY7l51FMDuTA7ggmlXp+3svlLSzW40NE+rdFHU+N58ajDSWnjy3iB1xho3sJFY6B1yoG1VqfTVE0Ez5aBkrn7hacMfulweQePVBycZCiU9ZPUU9PBK8OipmlkTd0DdBOT5+K+CD3XqkZQ3yspYwwMhlc1oZJ0jQO4OOMrwoiDJ6dpaesv1PBVQvnhdvExsOC4hpI7RnjjgCCeQ4qRM09RsuFfHFbWXCaOohj8WZUOaIonMy5+eDuB4cfa9uVCkwO5BN3adsw03cKiIGd0LqvoqnfIyIyOj453eIJ4EdbswvTLpuxey1thjha5ksr45BHK8jhAH4fk53i45G7wI4c1r/AznAymB3BB7rzA2mussTKc07W4xGWubjgOxxJHxleFMY5cEQZLTtJT1+pLfS1Td6CaZrHje3cjz9iktLp+2yVuJreYpzQPnfRb75OjeJQ1pwHB3FpJ3c+VQhUwMYwMeZBKqiislLpkzVMXRVsz6hsbWmTfa5rwGjGSA0AnO9x7lkJtO2ptVFG6k6Cm8cpoaep8YJ8ejeeueeBw45bjHIqDYwmB3BBPLTpvTtUy1SVdQInunlE0JlwZ29KWMDe4ggZ8nFeX2Ct3sXZpG0m8aqZjZ5uvgAzlhG9vbreqBwxntUNwO4JgZ5D0IJtU2SxUtwtLqdjaqlr66WFzXzEOjZvNaGuweBaS7j28CvnbbPba6SR8dsbO015p5mtqHNFJCAP5TJPb1jl2R1cdqhuB3BMDuQSmey0A0XLXQQ70sTz/tL5COkHS7o3QDjO7jLCA7tyQosiICk1ptNPUWCOobbfZCSR8rah/jPReKta0Fh7hnicuyDjAUZT4kEvZp+3m2Q1rov5GaCkDJOl4OmdIBK0ceeM8Oxe6o0/ZG6ihggpDPE+Gd27DI57C5sha3gXB5IA6wae4jIUCwO5MDuCCbUWnLe6plhNEyrYK+SnqZGVR3aKEYw8HhnmTvOGOrjGV4Kiz0LdECvhg/lmOGah8hHSZkLRugEtPDGWkBw58QoxgdwRAREQS2hslun0JLXyQ5qhHO/pd9w3XMc3dHPdGQTwIyexXyabhp9SXGIUD54WQmShpzIQKlw3MgOBy7Ac44BycKH4Gc4GUAA5AIJpFYLd7I1jYqLxmeNtOTRGZxEG+CZeLTvO3Dgc+GePJRm9UTLdfa2jjLSyCVzG7r98Y7OtgZ868OB3BOSAsvpmko62+Mir2h1OIpZHAkgZawuHIg8xyB4rEIgllPZLZXWK4VTHRR1Uxe6gjEhblsQBdhriSd7iOJ4YX2uum6Gm0vPXwwNbBGyHxesbOXOqHu3d4OZyA4uxjGNwgqGq5sj2xvja9zWPxvNBIDscsjtQWoiIOltjnuXW78LP8ASOU4cSGktG8QOA7z3LXWyO9Wul2a0MFRcqOCZks29HJOxjhmQkcCc8ipr9UNl/ri3frUf7V+M9p2rk629MUz+6rl4vpbFUeqp35QjEGo7m63VM0dYKqobbZqmeLxcN8Snbjdj5ceO8N12Sd3PIr6svtybQx+P1pt8Pj0lPNVSRM34GNjy0OwNwFzuTsYwR2lSP6orN/XNv8A1uP95fGpvFgrKWWmnu1vfDK0se3xtgyDzHByn1kTO9n4b/LHw8+eYx/uYe46jrqSG1vpi+sjbGKqumbSFu/DvBmd08WE5c7/ACeVeW56i1DT1N0ipqYPhirWthqeiy2OJpYHtPe4743T3E+9UmZf7IxjWtvFvDWgADxuPhj/ADKv1Q2X+ubf+tx/tVaLkU4/4OfPzz0/p5bJmM/5kdl1BcR9UwZVNE1AJ/Fo8MduhuN0lmN48+ZOCqyXu9S2m+vcXUdZbDC0BkIc1zi0bxG8DvNOd4HmOXepF9UVm/rm3/rcf7yp9UNl/rm3/rcf7U9Z/wCHpy8vDniff72P9zB3y73C2189OyvLJYII3UkLoGuNwkJIc0kDyAYbjGcngslqO4T0JomNqvEKeZ72zVO6124Q3LW5cC1u8eG8R2Y7V6/qisw5Xm3/AK3H+1U+qGyjlebeP/q4/wBqyzOaZ9Vw8OO3l/XfO/gnbf8AUiztTXef2Kkp3SCOeCN0r307Wt3jUdGXPHEtBA+9PAkHksjT3Kqqda1kO7NBR1AdSU9R0WcSRAFxBOWnOXjGOcfblZn6orN/XNv/AFuP95U+qGy/1zb/ANaj/atKrmYmIs44/HeOXJER1qYa33S6G22SSaoMsldFPJM58A6pbGS0YaAcZHnPJerSF0qbpbZnVVR4zLFIGmVrWhjssaeqWgZGT2gEcjxGV7/qhsv9c2/9bj/an1Q2Y87zbz/9XH+1UuTNdMxFrEz4cN5np0nH9ExiJz3mRPJcw7WPdSvXw4/omLo36obLj7cW79aj/aubdp9VBWbS7xPTTRzwuezdkjcHNOI2g4I4HiF9F6J266dXXNUY/TPzhx9oVRNuMTzRNERfpLxRERARXdTvd6E6ne70KBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWorup3u9CdTvd6EFqK7qd7vQnU73ehBaiu6ne70J1O93oQWkA8wD8Sput9630K/qd7vQnU73ehTkWbrfet9Cbrfet9Cv6ne70J1O93oTIs3W+9b6E3W+9b6Ff1O93oTqd7vQmRZut9630Jut9630K/qd7vQnU73ehMizdb71voTdb71voV/U73ehOp3u9CZFm633rfQm633rfQr+p3u9CdTvd6EyLN1vvW+hN1vvW+hX9Tvd6E6ne70JkWbrfet9Cqrup3u9CdTvd6EyLUV3U73ehOp3u9CgWorup3u9CILURFIIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIq46uVRAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREF4H8iT5VYvoB/szj/wAy+aiAREUgiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIg+zR/sbz/zBfFfdo/8Pef+cL4KtPNMiIisgREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQelg/8MkP/UC8y9bB/wCEyn/qBeRUp5pkREV0CIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiD2xj/AMFlP/VC8S90f2imP/WavCs6OfmmRERaIEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQFmWaQ1DJG17LPVOa4BwIaOIPEdqwyput96PQs64rn9kxHnGfrCYxzZz6jdR/wBS1f5o/avBT2urqLzHahEWVb5hBuO5tdnHHzLxbrfet9C+9HWVFvqm1NJM6CZgIa9nAtyCDju4EqmLuJzMTPLaY398p/SzcWjqt94uVtfV08c1AN7k53TA8QWNA3iMYOccARwVtJpKoraS1TQ1lM72TmbA0AOIic4kAPIGAeHEc+I5ryxamvMFQ6oZcZumcxsZkdhzsN4N4kE5HYeY71ZFqG7QU9NBFXSMjpHtkiDQ3qubndOcZON44znGSueaNXjaqOXy35dd2mbfR7odJTzVVwp21sDZKFgeWuY8PkyCeDMb2BjiccMhWw6SqqmktU1PU08xucgjY1u9iMnPBzsYBABJHMcOBXkh1FdaaeeaCrML5wA8xxsbyBAIAHVOCeIweJVgv10FLTUza6VkVK9skIbhpa5ud05AycZOMk4yVPc1XKqOXy35dd0Zt9GUo9GVFxrIY6KugqIJ6d9RHOyOQ7wY/cc3cxvZye7kvONKVr66kpWTU8j6qrmo2uY4uaDGRvPJA9rh2cjsBXmk1Hd5avxk18rZej6EFgDA1m9vYAAAHHjwHNWNv10ZIJGV0rHh0rw5uGkGUYkIwOG9gclEUar/AFR/M+Hl0M2+iyrtNVSXyS0uZv1TJugAb984nAx5DkY86ytRo6ooblX01fX0tLBQiMvqiHuY7pPaboA3jnj2cMFYo3e4OukdxdVyurY93dnJy8bow057wAOK+8OprzDO2ZtxmdIIxDmTEmWB28Ad4HOCcjPEdivXTqZiO7McN/PbhtP9NufgiJo5ro9OVk1huF3ifFJTUEoicWknpOIy5vDi0ZbnOPbBZIaHqfZOipPHaaXxipjppDHvAwvewSAHI45bniM8QsQL/dm0z6cXCfoZBIHx73Vf0nt8jtJ7yvpJqe9TT0sz7jKZKRwfCcNG64AAO4DicADJzwCpVRq5mcVRz+W3L+Z8ExNvnDKRaFrbhU1otj2yR0tTFTls2WyAPGd4jHJv3x7uK831IVYqpInVVM1kVRU08knW3WiBoe9/LJGDwHMrHC+XNolEdZJCJnB7xEBGHENLeTQPvSRjtyrm3+6tqRUCul6UTPqN7h9keAHu5cd4DBHIhRFvVx/mjGPp905t9Hrt+l6i719XT22rp6tlNT+MdM0ODX8ODACMhxPDB7RzXnsNimv9RPFBKyLoIDO4ua52WhzRgADJPWCN1LeY6mSojuU8UsjmOc6MhmSwYYMAAYGeA5eReaiulZb55pqabo3ztLJOo1we0kEgggjGQDy7Fp3dRiqMxnbH1zt9Fc0ZhkItMzTWaO4x1kDmvqBT9GA4uYS7dBcQMNzzAOMjl3LISaArorrPQmspy6CA1DiGPJwJOjxu43s54jvHFYRl9ucdCKNlY9lOHh+4GtHEO3hxxnG9xxyzxwrae83Clq6qqiqSJqvPTucxruky7eO8CCDxAPJUqo1U5xXHPHwxy8+qYm30feSyCCzsrp7jTQvmY+SCncHb8rGvLCQcYByDgE8cFev6jbiZLuxj4n+xUbZJCN7EmW7263hz3d48ce1Kxzb3cmWx9ubVvFJJvZjwOROSAcZAJAJAOF9mamvccj3sudQ10j+keWuxvu3dzJ7+rwweCtVTqd+7Mc/nGOXTMc+pE0c10Onama526hbNCJLhTtqI3HOGtIccHhz6p9KtFikktdvq4KmKaS4TdBFThjhIXcATxGCASBkdvmK+bdQXRraQNrHA0Td2Bwa3ejGCMA4zjBPA96q3UF0ayja2sc3xHHixDGh0WM4wcZ7T6cqZp1OeMfzPh5fFGaGRk0ZU093r6GqrqWnFC2N7p3B5ZIJHNa0twM4JcOY715ptK3Gns1dcpQxsdDVGllZkl28DuucOGN0OLRz++C+UOp71BN0zLjMZOibDvPw87jXbzRlwPJ3EHmF8vZ66mjfSG4VBp3tex0Zflrg5287I7STxyePlVKadXGM1Ry/+8uf84bzM2+jHoiLvZCIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgyEQ/3fnP8A1m/6LHrIxD/duoP/AF2+oLHLK3xq81p5CIi1VEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEVQN5wHecLfkXgrXGWFkg1VSgOaHfzN3aPhINBIugP4qVy/tVS/qbv3k/ipXL+1VL+pu/eQc/otzaQ8HWu1bpWjvcWoqemZVb+InUznFu69zee8Pe5WZd4KVz3Tu6qpCfLSOH/qQaARbG11sQ1XoW3vuU7YLjbY8dJUUhJ6Id72kZA8vELXKAi3RpPwcbjqnSduvg1BT0ja+ETNhdTOcWA8uO8M8OK8G0HYLX6C0lLfpL3BXxwyMY+JlO5hAccZyXHtwg1Mi2ls32JVO0fTUl3pr9BQ9FUOp3Qvp3PIIAOchw5hy8W0/ZBWbM6O31M91iuLK2R8f8nCY9wtAPHJOc/6INdItnbNNildtI0/UXaG8Q2+KGoNOGyQGQuIaCTkEe+Xg2m7KqjZtPbIJbtHc5rjv7scUDmFu6WjvOcl2EEARbu0p4MmoLxQxVd9uUVkEgDhTiIzTAf83EBp8mSspefBVrYaV8lm1LFVTNGRFVU5iDj3bzScehBz6iy9Tpm5W7VjNO3SB9BXeMMp3tkGd0ucAHcOY45BHMLdP8VK5f2rpf1N37yDn9FM9MbOp9TbTKnR0dxip5ad87DUuiLmu6IkHq5zxx3qcam8G6v01pa5XqTUlNUMoIHzmJtK5peGjOM73BBpRERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREGTiH+7FQf7w31BYxZWEf7q1J/vDfUFilja41ef2Wq5CIi2VEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQVacPB7iCusLV4Sukaqoorey3XgSzPjgaXRR7ocSGj7/AJZK5OWT0391do/HYPpGoP0FWn7r4SWkrTeKy2z268OmpJnwPLIoy0ua4tOOvy4Lb/YuBdbe6BqD8o1H0jkHX+xSQTbHrFK0EB7ZXDPcZnlffVm1Sw6M1bbLBdYqwT3JrXRzRsa6Nm8/cG9xBHHuBXk2Ge4npz8C/wCletabeLFdL3tl0rFbqCoqiYIgXRxOc1v8uSSS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JiduMcJnnLk1FU1XKpkREXpsBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERBJ6QfWwuJ/v8AH6gowpRSD61txP8AiEfqCi649Lxue19IaV8I8hERdjMREQEREBERAREQEREGVj+wRfAb6lcrY/sEXwG+pXKI4EiIikEREBERAREQEREBERAREQEREBERAREQEREBeSv5xfBPrXrXkr+cXwT61EjxoiKQREQEREBERAREQEREBERAREQEREBERAREQEREBdN7JtseiNLbMLTZ7tdn09dTNeJIxSyvDcyOI4taQeBC5kRBsPbNq+16q2l+zen6t09OynhayUxujIewk8nAHnhdA2/whtASWymfWXiSGqdE0zR+JzHdfgbwyG4PHPJceYPcqINkbTteU1y2y/VZpauc9sDYHwTGNzOuxuCC1wBx2HvBW9dH+ERpC+W2L2aqhY7iABJHMHGJx72PAIx58EfKuQkQdsXXbhs9tNK6U6ip6xwGRFRgzPd5BgY9JC5c2obSKzaRqVtbLCaWhpmmOkpt7JY0nJc49rjwz5gOxQviqDjy4oCHi0jyIq4Pcg6Podrmi4LbTQyXWQPjhYxw8VlOCGgH71aQ15daO966ulyoJTLS1EgdG8tLcjdA5HiOIUfwe5UwV4ug7F0+gu1XrUzMzGN8dc9IdN7U13qYpqTnZrtDdoqtmgq43z2uqIdI1nt43DhvtHbw4EdvxLdlNtN0bVQCVuoKWMYzuy7zHD4iFy3g9ycVh2h6P6XXXPXVTNNU8cc17OsrtU92N4b31ttmtcFrmotNzOq6yZpZ4yGFscIPMjPFzu7hhas0NrKp0XqDx5jDPTzN6Oph3sF7c5yD74HiP/uo3gqmCurS9j6XTWKtPTGYq454z/OWGdzU3K64rmeDqC37U9G3GnbIL1DSuIyY6lpjc3z5GPQVidS7ZtO2qhkFonF1riCI2xtIiae9ziBw8gzlc7cfKmCvKo9FNHTc70zVMdMx9nRPaFyYxs+1ZVz19dNWVUhlnneZJHnm5xOSVvHQm0zSlk0LardX3F8VVTxFsjBTyOwd4nmBg81ofBVcHuXs9odmWdfaps3cxETnbHl0lzWb9VmqaqUz2p6htuptZCvtU5nphTRx7xY5nWBORggHtCharg9youvTaenTWqbNHCmMbs665rqmqeYiIuhQREQE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" alt="Site SOS Acadêmico">
      </div>
      <div class="portfolio-overlay"><span>VER PROJETO →</span></div>
      <div class="portfolio-label">SOS Acadêmico<div class="portfolio-sub">Rebuild + SEO · Educação</div></div>
    </div>

  </div>
</section>
<!-- CTA -->
<section id="cta">
  <div class="cta-terminal">
    <span class="prompt">$ </span>novo_projeto --start<span class="cursor-blink"></span>
  </div>
  <h2 class="section-title reveal">Pronto para<br>começar?</h2>
  <p class="section-sub reveal" style="margin:0 auto 2.5rem;">
    Fale com a gente. Sem enrolação, sem promessas vazias. Apenas resultados.
  </p>
  <div style="display:flex; gap:1rem; justify-content:center; flex-wrap:wrap;">
    <a href="https://wa.me/5518991159643" class="btn-primary">Falar com a Cevora</a>
    <a href="https://wa.me/5518991159643" class="btn-ghost">WhatsApp ↗</a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span class="footer-logo">CEVORA</span>
  <span class="footer-copy">© 2024 Cevora · Todos os direitos reservados</span>
</footer>

<script>
  const cursor = document.getElementById('cursor');
  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top = e.clientY + 'px';
  });

  const observer = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  document.querySelectorAll('.tab-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      const filter = btn.dataset.filter;
      document.querySelectorAll('#portfolio-grid .portfolio-card').forEach(card => {
        if (filter === 'all' || card.dataset.cat === filter) {
          card.classList.remove('hidden');
        } else {
          card.classList.add('hidden');
        }
      });
    });
  });
</script>
</body>
</html>

