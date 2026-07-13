<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sudhanshu Kumar Swain — Frontend Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@400;500;600;700;800&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#080A12;
    --bg-alt:#0D1020;
    --surface:#11142280;
    --surface-solid:#12152a;
    --border:#242847;
    --text:#E9ECF7;
    --muted:#8A90AC;
    --violet:#7C6FFF;
    --violet-soft:#7C6FFF33;
    --cyan:#43E7D0;
    --amber:#FFB86B;
    --font-display:'Sora',sans-serif;
    --font-body:'Inter',sans-serif;
    --font-mono:'JetBrains Mono',monospace;
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--text);
    font-family:var(--font-body);
    overflow-x:hidden;
    cursor:none;
  }
  @media (max-width:900px){ body{cursor:auto;} }
  ::selection{background:var(--violet);color:#fff;}

  /* ---------- custom cursor ---------- */
  .cursor-dot, .cursor-ring{
    position:fixed; top:0; left:0; pointer-events:none; z-index:9999;
    border-radius:50%; transform:translate(-50%,-50%);
  }
  .cursor-dot{width:6px;height:6px;background:var(--cyan);}
  .cursor-ring{width:32px;height:32px;border:1px solid var(--violet);transition:width .2s,height .2s,opacity .2s,border-color .2s;}
  .cursor-ring.hover{width:56px;height:56px;border-color:var(--cyan);opacity:.6;}
  @media (max-width:900px){ .cursor-dot,.cursor-ring{display:none;} }

  /* ---------- background atmosphere ---------- */
  .noise-overlay{
    position:fixed;inset:0;pointer-events:none;z-index:1;opacity:.035;mix-blend-mode:overlay;
    background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  }
  .blob{position:fixed;border-radius:50%;filter:blur(110px);z-index:0;opacity:.35;pointer-events:none;}
  .blob-1{width:520px;height:520px;background:var(--violet);top:-160px;left:-120px;animation:float1 22s ease-in-out infinite;}
  .blob-2{width:460px;height:460px;background:var(--cyan);bottom:-140px;right:-100px;animation:float2 26s ease-in-out infinite;}
  .blob-3{width:340px;height:340px;background:var(--amber);top:40%;left:50%;opacity:.12;animation:float3 30s ease-in-out infinite;}
  @keyframes float1{0%,100%{transform:translate(0,0)}50%{transform:translate(60px,80px)}}
  @keyframes float2{0%,100%{transform:translate(0,0)}50%{transform:translate(-70px,-50px)}}
  @keyframes float3{0%,100%{transform:translate(-50%,-50%) scale(1)}50%{transform:translate(-40%,-55%) scale(1.2)}}

  section, header, footer{position:relative;z-index:2;}

  /* ---------- nav ---------- */
  nav{
    position:fixed;top:0;left:0;right:0;z-index:1000;
    display:flex;align-items:center;justify-content:space-between;
    padding:20px 6vw;backdrop-filter:blur(16px);
    background:rgba(8,10,18,.55);border-bottom:1px solid var(--border);
  }
  .logo{font-family:var(--font-mono);font-weight:600;font-size:1rem;color:var(--text);letter-spacing:.5px;}
  .logo span{color:var(--cyan);}
  .nav-links{display:flex;gap:36px;list-style:none;}
  .nav-links a{
    color:var(--muted);text-decoration:none;font-size:.88rem;font-weight:500;
    position:relative;transition:color .3s;
  }
  .nav-links a::after{
    content:'';position:absolute;left:0;bottom:-6px;width:0;height:1px;background:var(--cyan);transition:width .3s;
  }
  .nav-links a:hover{color:var(--text);}
  .nav-links a:hover::after{width:100%;}
  @media (max-width:800px){.nav-links{display:none;}}

  /* ---------- hero ---------- */
  header.hero{
    min-height:100vh;display:flex;flex-direction:column;justify-content:center;
    padding:120px 6vw 60px;position:relative;
  }
  .hero-grid{display:grid;grid-template-columns:1.1fr .9fr;gap:60px;align-items:center;}
  @media (max-width:900px){.hero-grid{grid-template-columns:1fr;}}
  .eyebrow{
    display:inline-flex;align-items:center;gap:8px;font-family:var(--font-mono);
    font-size:.78rem;color:var(--cyan);letter-spacing:1.5px;text-transform:uppercase;
    border:1px solid var(--border);padding:6px 14px;border-radius:99px;margin-bottom:26px;
    opacity:0;animation:riseIn .8s .1s forwards;
  }
  .eyebrow::before{content:'';width:7px;height:7px;border-radius:50%;background:var(--cyan);box-shadow:0 0 12px var(--cyan);animation:pulse 2s infinite;}
  @keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}
  h1.name{
    font-family:var(--font-display);font-weight:800;font-size:clamp(2.6rem,6vw,4.6rem);
    line-height:1.03;letter-spacing:-.02em;
    opacity:0;animation:riseIn .8s .25s forwards;
  }
  h1.name .grad{
    background:linear-gradient(100deg,var(--violet),var(--cyan) 70%);
    -webkit-background-clip:text;background-clip:text;color:transparent;
  }
  .role-line{
    font-family:var(--font-mono);color:var(--muted);font-size:clamp(1rem,2vw,1.25rem);margin-top:20px;
    opacity:0;animation:riseIn .8s .4s forwards;
  }
  .role-line .cursor-blink{display:inline-block;width:2px;height:1.1em;background:var(--cyan);vertical-align:middle;margin-left:2px;animation:blink 1s steps(1) infinite;}
  @keyframes blink{50%{opacity:0;}}
  .hero-desc{
    max-width:520px;color:var(--muted);font-size:1rem;line-height:1.7;margin-top:22px;
    opacity:0;animation:riseIn .8s .55s forwards;
  }
  .hero-cta{display:flex;gap:16px;margin-top:36px;opacity:0;animation:riseIn .8s .7s forwards;}
  .btn{
    font-family:var(--font-body);font-weight:600;font-size:.92rem;padding:14px 28px;border-radius:10px;
    text-decoration:none;display:inline-flex;align-items:center;gap:8px;transition:transform .35s cubic-bezier(.2,.8,.2,1),box-shadow .35s;
    position:relative;overflow:hidden;
  }
  .btn-primary{background:linear-gradient(100deg,var(--violet),#5C4DFF);color:#fff;box-shadow:0 8px 30px -8px var(--violet-soft);}
  .btn-primary:hover{transform:translateY(-3px);box-shadow:0 14px 34px -6px rgba(124,111,255,.55);}
  .btn-ghost{border:1px solid var(--border);color:var(--text);}
  .btn-ghost:hover{transform:translateY(-3px);border-color:var(--cyan);color:var(--cyan);}

  @keyframes riseIn{from{opacity:0;transform:translateY(24px);}to{opacity:1;transform:translateY(0);}}

  /* code window */
  .code-window{
    background:var(--surface-solid);border:1px solid var(--border);border-radius:14px;
    box-shadow:0 30px 80px -30px rgba(0,0,0,.6), 0 0 0 1px rgba(124,111,255,.06);
    opacity:0;animation:riseIn .9s .5s forwards, floatCard 6s ease-in-out 1.4s infinite;
    overflow:hidden;
  }
  @keyframes floatCard{0%,100%{transform:translateY(0)}50%{transform:translateY(-10px)}}
  .code-topbar{display:flex;align-items:center;gap:8px;padding:12px 16px;border-bottom:1px solid var(--border);background:#0d0f1c;}
  .dot{width:11px;height:11px;border-radius:50%;}
  .dot.r{background:#ff5f57;}.dot.y{background:#febc2e;}.dot.g{background:#28c840;}
  .code-title{margin-left:10px;font-family:var(--font-mono);font-size:.75rem;color:var(--muted);}
  .code-body{padding:22px 24px;font-family:var(--font-mono);font-size:.86rem;line-height:1.85;min-height:230px;}
  .tk-key{color:#7C6FFF;}.tk-str{color:#43E7D0;}.tk-fn{color:#FFB86B;}.tk-punc{color:#7d84a3;}.tk-com{color:#565d7d;font-style:italic;}
  #typewriter{white-space:pre-wrap;}

  /* scroll cue */
  .scroll-cue{
    position:absolute;bottom:34px;left:50%;transform:translateX(-50%);
    display:flex;flex-direction:column;align-items:center;gap:8px;color:var(--muted);
    font-family:var(--font-mono);font-size:.7rem;letter-spacing:1px;opacity:0;animation:riseIn 1s 1.1s forwards;
  }
  .scroll-cue .line{width:1px;height:34px;background:linear-gradient(var(--cyan),transparent);animation:scrollLine 1.8s infinite;}
  @keyframes scrollLine{0%{transform:scaleY(0);transform-origin:top;}50%{transform:scaleY(1);transform-origin:top;}51%{transform-origin:bottom;}100%{transform:scaleY(0);transform-origin:bottom;}}

  /* ---------- section shell ---------- */
  .section{padding:130px 6vw;}
  .section-head{margin-bottom:60px;}
  .tag{
    font-family:var(--font-mono);color:var(--cyan);font-size:.78rem;letter-spacing:2px;text-transform:uppercase;
    display:block;margin-bottom:14px;
  }
  .tag::before{content:'// ';color:var(--violet);}
  h2{font-family:var(--font-display);font-size:clamp(1.8rem,3.6vw,2.6rem);font-weight:700;letter-spacing:-.01em;}

  .reveal{opacity:0;transform:translateY(34px);transition:opacity .8s cubic-bezier(.2,.7,.2,1),transform .8s cubic-bezier(.2,.7,.2,1);}
  .reveal.visible{opacity:1;transform:translateY(0);}

  /* ---------- about ---------- */
  .about-wrap{display:grid;grid-template-columns:1fr 1fr;gap:60px;}
  @media (max-width:900px){.about-wrap{grid-template-columns:1fr;}}
  .about-text p{color:var(--muted);line-height:1.85;font-size:1.02rem;}
  .stat-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;align-content:start;}
  .stat-card{
    border:1px solid var(--border);border-radius:14px;padding:24px;background:var(--surface);
    transition:transform .4s,border-color .4s;
  }
  .stat-card:hover{transform:translateY(-6px);border-color:var(--violet);}
  .stat-num{font-family:var(--font-display);font-size:2rem;font-weight:800;color:var(--cyan);}
  .stat-label{color:var(--muted);font-size:.82rem;margin-top:6px;}

  /* ---------- skills ---------- */
  .skill-cats{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:22px;}
  .skill-card{
    border:1px solid var(--border);border-radius:16px;padding:26px;background:var(--surface);
    transition:transform .4s cubic-bezier(.2,.7,.2,1),box-shadow .4s;
  }
  .skill-card:hover{transform:translateY(-8px);box-shadow:0 20px 50px -20px rgba(124,111,255,.35);}
  .skill-card h3{font-family:var(--font-display);font-size:1.02rem;margin-bottom:16px;color:var(--text);}
  .skill-tags{display:flex;flex-wrap:wrap;gap:9px;}
  .skill-tag{
    font-family:var(--font-mono);font-size:.76rem;padding:7px 12px;border-radius:8px;
    border:1px solid var(--border);color:var(--muted);transition:all .3s;
  }
  .skill-tag:hover{color:var(--bg);background:var(--cyan);border-color:var(--cyan);transform:scale(1.06);}

  /* ---------- timeline ---------- */
  .timeline{position:relative;padding-left:36px;}
  .timeline::before{content:'';position:absolute;left:6px;top:6px;bottom:6px;width:1px;background:linear-gradient(var(--violet),var(--cyan));
    transform:scaleY(0);transform-origin:top;transition:transform 1.2s ease;}
  .timeline.visible::before{transform:scaleY(1);}
  .tl-item{position:relative;margin-bottom:44px;}
  .tl-item::before{
    content:'';position:absolute;left:-36px;top:4px;width:13px;height:13px;border-radius:50%;
    background:var(--bg);border:2px solid var(--cyan);box-shadow:0 0 0 4px rgba(67,231,208,.12);
  }
  .tl-role{font-family:var(--font-display);font-size:1.15rem;font-weight:700;}
  .tl-meta{font-family:var(--font-mono);color:var(--cyan);font-size:.78rem;margin:6px 0 12px;}
  .tl-item ul{color:var(--muted);line-height:1.8;padding-left:20px;font-size:.95rem;}

  /* ---------- projects ---------- */
  .project-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(310px,1fr));gap:26px;}
  .project-card{
    border:1px solid var(--border);border-radius:18px;padding:30px;background:var(--surface);
    position:relative;overflow:hidden;transition:transform .15s ease-out,border-color .4s;
    transform-style:preserve-3d;
  }
  .project-card::before{
    content:'';position:absolute;inset:0;opacity:0;transition:opacity .4s;
    background:radial-gradient(400px circle at var(--mx,50%) var(--my,50%),rgba(124,111,255,.16),transparent 60%);
  }
  .project-card:hover::before{opacity:1;}
  .project-card:hover{border-color:var(--violet);}
  .proj-index{font-family:var(--font-mono);color:var(--violet);font-size:.78rem;}
  .proj-title{font-family:var(--font-display);font-size:1.25rem;font-weight:700;margin:12px 0 10px;}
  .proj-desc{color:var(--muted);font-size:.92rem;line-height:1.7;margin-bottom:18px;}
  .proj-stack{display:flex;flex-wrap:wrap;gap:8px;}
  .proj-stack span{
    font-family:var(--font-mono);font-size:.72rem;color:var(--cyan);border:1px solid rgba(67,231,208,.3);
    padding:5px 10px;border-radius:6px;
  }

  /* ---------- education ---------- */
  .edu-grid{display:grid;grid-template-columns:1fr 1fr;gap:24px;}
  @media (max-width:800px){.edu-grid{grid-template-columns:1fr;}}
  .edu-card{border:1px solid var(--border);border-radius:16px;padding:28px;background:var(--surface);transition:transform .4s;}
  .edu-card:hover{transform:translateY(-6px);}
  .edu-degree{font-family:var(--font-display);font-weight:700;font-size:1.1rem;}
  .edu-school{color:var(--muted);margin:8px 0;font-size:.92rem;}
  .edu-cgpa{font-family:var(--font-mono);color:var(--cyan);font-size:.85rem;}

  /* ---------- achievements ---------- */
  .ach-list{display:flex;flex-direction:column;gap:0;}
  .ach-item{
    display:flex;gap:20px;align-items:flex-start;padding:22px 0;border-bottom:1px solid var(--border);
    transition:padding-left .3s;
  }
  .ach-item:hover{padding-left:12px;}
  .ach-icon{font-family:var(--font-mono);color:var(--amber);font-size:.85rem;padding-top:2px;}
  .ach-text{color:var(--muted);line-height:1.7;font-size:.96rem;}
  .ach-text strong{color:var(--text);}

  /* ---------- footer / contact ---------- */
  footer{padding:110px 6vw 50px;text-align:center;}
  footer h2{margin-bottom:18px;}
  footer p.sub{color:var(--muted);max-width:480px;margin:0 auto 40px;line-height:1.7;}
  .contact-row{display:flex;justify-content:center;gap:18px;flex-wrap:wrap;margin-bottom:70px;}
  .foot-meta{
    display:flex;justify-content:space-between;flex-wrap:wrap;gap:14px;
    border-top:1px solid var(--border);padding-top:26px;color:var(--muted);font-family:var(--font-mono);font-size:.78rem;
  }
  .foot-meta a{color:var(--muted);text-decoration:none;transition:color .3s;}
  .foot-meta a:hover{color:var(--cyan);}

  ::-webkit-scrollbar{width:9px;}
  ::-webkit-scrollbar-track{background:var(--bg);}
  ::-webkit-scrollbar-thumb{background:var(--border);border-radius:10px;}
  ::-webkit-scrollbar-thumb:hover{background:var(--violet);}
</style>
</head>
<body>

<div class="cursor-dot" id="cdot"></div>
<div class="cursor-ring" id="cring"></div>
<div class="noise-overlay"></div>
<div class="blob blob-1"></div>
<div class="blob blob-2"></div>
<div class="blob blob-3"></div>

<nav>
  <div class="logo">SKS<span>.</span>dev</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<header class="hero">
  <div class="hero-grid">
    <div>
      <span class="eyebrow">Available for hire</span>
      <h1 class="name">Sudhanshu Kumar<br><span class="grad">Swain.</span></h1>
      <div class="role-line">Frontend Developer <span class="cursor-blink"></span></div>
      <p class="hero-desc">I build production-ready React.js interfaces — responsive, accessible, and animated down to the last micro-interaction. Currently shipping features for a live LMS and company site at Techgenius Balaji Solutions.</p>
      <div class="hero-cta">
        <a href="#projects" class="btn btn-primary">View Projects →</a>
        <a href="#contact" class="btn btn-ghost">Get in Touch</a>
      </div>
    </div>
    <div class="code-window">
      <div class="code-topbar">
        <span class="dot r"></span><span class="dot y"></span><span class="dot g"></span>
        <span class="code-title">developer.jsx</span>
      </div>
      <div class="code-body"><span id="typewriter"></span></div>
    </div>
  </div>
  <div class="scroll-cue"><span>SCROLL</span><span class="line"></span></div>
</header>

<section class="section" id="about">
  <div class="section-head reveal">
    <span class="tag">About</span>
    <h2>Turning interfaces into experiences</h2>
  </div>
  <div class="about-wrap">
    <div class="about-text reveal">
      <p>Frontend Developer with hands-on industry experience building production-ready React.js applications. Currently working as a Frontend Developer Intern at Techgenius Balaji Solutions Pvt. Ltd., developing the company's landing page and contributing to its Learning Management System (LMS).</p><br>
      <p>Skilled in building responsive, accessible, and animated user interfaces with React.js, JavaScript, Tailwind CSS, and Framer Motion. Seeking a Frontend Developer role to build engaging, high-performance web experiences.</p>
    </div>
    <div class="stat-grid reveal">
      <div class="stat-card"><div class="stat-num">4+</div><div class="stat-label">Projects Shipped</div></div>
      <div class="stat-card"><div class="stat-num">8.3</div><div class="stat-label">MCA CGPA</div></div>
      <div class="stat-card"><div class="stat-num">2026</div><div class="stat-label">Current Intern</div></div>
      <div class="stat-card"><div class="stat-num">5+</div><div class="stat-label">Certifications</div></div>
    </div>
  </div>
</section>

<section class="section" id="skills">
  <div class="section-head reveal">
    <span class="tag">Core Skills</span>
    <h2>The stack I build with</h2>
  </div>
  <div class="skill-cats">
    <div class="skill-card reveal">
      <h3>Frontend</h3>
      <div class="skill-tags">
        <span class="skill-tag">React.js</span><span class="skill-tag">JavaScript ES6+</span>
        <span class="skill-tag">Tailwind CSS</span><span class="skill-tag">Bootstrap</span>
        <span class="skill-tag">Context API</span><span class="skill-tag">React Router</span>
        <span class="skill-tag">Framer Motion</span><span class="skill-tag">Responsive Design</span>
      </div>
    </div>
    <div class="skill-card reveal">
      <h3>Backend (Learning)</h3>
      <div class="skill-tags">
        <span class="skill-tag">Node.js</span><span class="skill-tag">Express.js</span>
        <span class="skill-tag">REST APIs</span><span class="skill-tag">MongoDB</span>
      </div>
    </div>
    <div class="skill-card reveal">
      <h3>Tools & Platforms</h3>
      <div class="skill-tags">
        <span class="skill-tag">Git</span><span class="skill-tag">GitHub</span>
        <span class="skill-tag">VS Code</span><span class="skill-tag">Chrome DevTools</span>
        <span class="skill-tag">NPM</span><span class="skill-tag">Vite</span>
      </div>
    </div>
    <div class="skill-card reveal">
      <h3>Frontend Craft</h3>
      <div class="skill-tags">
        <span class="skill-tag">Page Transitions</span><span class="skill-tag">UI Animation</span>
        <span class="skill-tag">Cross-Device Optimization</span><span class="skill-tag">SEO Basics</span>
      </div>
    </div>
  </div>
</section>

<section class="section" id="experience">
  <div class="section-head reveal">
    <span class="tag">Experience</span>
    <h2>Where I've been building</h2>
  </div>
  <div class="timeline reveal">
    <div class="tl-item">
      <div class="tl-role">Frontend Developer Intern</div>
      <div class="tl-meta">Techgenius Balaji Solutions Pvt. Ltd. — June 2026 – Present</div>
      <ul>
        <li>Developed the company's official landing page using React.js and Tailwind CSS.</li>
        <li>Built responsive, reusable UI components with smooth, animation-driven interactions.</li>
        <li>Contributing to the company's Learning Management System (LMS), including responsive dashboards.</li>
        <li>Integrated frontend components with backend REST APIs.</li>
        <li>Collaborated with designers and senior developers to deliver production-ready features.</li>
        <li>Improved UI responsiveness and performance across desktop, tablet, and mobile devices.</li>
      </ul>
    </div>
  </div>
</section>

<section class="section" id="projects">
  <div class="section-head reveal">
    <span class="tag">Projects</span>
    <h2>Selected work</h2>
  </div>
  <div class="project-grid">
    <div class="project-card reveal">
      <div class="proj-index">01</div>
      <div class="proj-title">CareConnect</div>
      <div class="proj-desc">A fully responsive doctor appointment booking web application, optimized across mobile, tablet, desktop, and all browser zoom levels.</div>
      <div class="proj-stack"><span>React.js</span><span>JavaScript</span><span>Tailwind CSS</span></div>
    </div>
    <div class="project-card reveal">
      <div class="proj-index">02</div>
      <div class="proj-title">Personal Portfolio</div>
      <div class="proj-desc">A modern, animated portfolio with fully responsive layouts, smooth page transitions, and micro-interactions built with Framer Motion.</div>
      <div class="proj-stack"><span>React.js</span><span>Tailwind CSS</span><span>Framer Motion</span></div>
    </div>
    <div class="project-card reveal">
      <div class="proj-index">03</div>
      <div class="proj-title">Company Website (Production)</div>
      <div class="proj-desc">Deployed responsive landing page for Techgenius Balaji Solutions, with reusable components optimized across all devices.</div>
      <div class="proj-stack"><span>React.js</span><span>JavaScript</span><span>Tailwind CSS</span><span>Vite</span></div>
    </div>
    <div class="project-card reveal">
      <div class="proj-index">04</div>
      <div class="proj-title">Learning Management System</div>
      <div class="proj-desc">Production-level LMS with responsive dashboards, REST API integration, and enhanced UI/UX for a better learning experience.</div>
      <div class="proj-stack"><span>React.js</span><span>REST APIs</span><span>Tailwind CSS</span><span>Git</span></div>
    </div>
  </div>
</section>

<section class="section" id="education">
  <div class="section-head reveal">
    <span class="tag">Education</span>
    <h2>Academic background</h2>
  </div>
  <div class="edu-grid">
    <div class="edu-card reveal">
      <div class="edu-degree">Master of Computer Applications (MCA)</div>
      <div class="edu-school">NIIS Institute of Business Administration · 2024 – 2026</div>
      <div class="edu-cgpa">CGPA: 8.3</div>
    </div>
    <div class="edu-card reveal">
      <div class="edu-degree">Bachelor of Computer Applications (BCA)</div>
      <div class="edu-school">&nbsp;</div>
      <div class="edu-cgpa">CGPA: 7.01</div>
    </div>
  </div>
</section>

<section class="section" id="achievements">
  <div class="section-head reveal">
    <span class="tag">Achievements & Certifications</span>
    <h2>Beyond the code</h2>
  </div>
  <div class="ach-list">
    <div class="ach-item reveal"><span class="ach-icon">✦</span><div class="ach-text"><strong>Labmentix Pvt. Ltd.</strong> — Web Development Internship</div></div>
    <div class="ach-item reveal"><span class="ach-icon">✦</span><div class="ach-text"><strong>12-Hour Warehouse Hackathon (BPUT)</strong> — Built and contributed to a real-time solution under strict time constraints, demonstrating strong teamwork, logical thinking, and rapid development skills.</div></div>
    <div class="ach-item reveal"><span class="ach-icon">✦</span><div class="ach-text"><strong>AWS</strong> — Introduction to Generative AI</div></div>
    <div class="ach-item reveal"><span class="ach-icon">✦</span><div class="ach-text"><strong>Coursera</strong> — Cloud Computing Certification</div></div>
    <div class="ach-item reveal"><span class="ach-icon">✦</span><div class="ach-text"><strong>TCS Virtual Internship</strong> — Web Development Experience</div></div>
  </div>
</section>

<footer id="contact">
  <div class="reveal">
    <span class="tag" style="justify-content:center;display:flex;">Contact</span>
    <h2>Let's build something together</h2>
    <p class="sub">Open to Frontend Developer roles. Reach out by email or phone, or connect on LinkedIn.</p>
    <div class="contact-row">
      <a class="btn btn-primary" href="mailto:kumarswainsudhanshu@gmail.com">Email Me →</a>
      <a class="btn btn-ghost" href="tel:+916371932861">+91 6371932861</a>
      <a class="btn btn-ghost" href="https://www.linkedin.com/in/sudhanshu-kumar-swain-972863329/" target="_blank" rel="noopener">LinkedIn</a>
    </div>
  </div>
  <div class="foot-meta">
    <span>© 2026 Sudhanshu Kumar Swain</span>
    <span>Bhubaneswar, Khordha, 752054</span>
    <a href="mailto:kumarswainsudhanshu@gmail.com">kumarswainsudhanshu@gmail.com</a>
  </div>
</footer>

<script>
  // custom cursor
  const cdot = document.getElementById('cdot'), cring = document.getElementById('cring');
  let mx=0,my=0,rx=0,ry=0;
  window.addEventListener('mousemove', e=>{
    mx=e.clientX; my=e.clientY;
    cdot.style.left=mx+'px'; cdot.style.top=my+'px';
  });
  (function loop(){
    rx += (mx-rx)*0.15; ry += (my-ry)*0.15;
    cring.style.left=rx+'px'; cring.style.top=ry+'px';
    requestAnimationFrame(loop);
  })();
  document.querySelectorAll('a, .skill-tag, .project-card, .stat-card, .edu-card').forEach(el=>{
    el.addEventListener('mouseenter',()=>cring.classList.add('hover'));
    el.addEventListener('mouseleave',()=>cring.classList.remove('hover'));
  });

  // typewriter hero code
  const codeLines = [
    {t:'const ',c:'tk-key'},{t:'developer',c:''},{t:' = {\n',c:'tk-punc'},
    {t:'  name: ',c:''},{t:'"Sudhanshu Kumar Swain"',c:'tk-str'},{t:',\n',c:'tk-punc'},
    {t:'  role: ',c:''},{t:'"Frontend Developer"',c:'tk-str'},{t:',\n',c:'tk-punc'},
    {t:'  stack: [',c:''},{t:'"React"',c:'tk-str'},{t:', ',c:'tk-punc'},{t:'"Tailwind"',c:'tk-str'},{t:', ',c:'tk-punc'},{t:'"Framer Motion"',c:'tk-str'},{t:'],\n',c:'tk-punc'},
    {t:'  status: ',c:''},{t:'"Open to work"',c:'tk-str'},{t:',\n',c:'tk-punc'},
    {t:'  build: ',c:''},{t:'() ',c:'tk-fn'},{t:'=> ',c:'tk-punc'},{t:'"pixel-perfect UI"',c:'tk-str'},{t:',\n',c:'tk-punc'},
    {t:'};',c:'tk-punc'},
    {t:'\n\n',c:''},
    {t:'export default ',c:'tk-key'},{t:'developer',c:''},{t:';',c:'tk-punc'},
    {t:'\n',c:''},
    {t:'// LMS + landing page in production',c:'tk-com'}
  ];
  const twEl = document.getElementById('typewriter');
  let li=0, ci=0, buf='';
  function typeStep(){
    if(li>=codeLines.length) return;
    const seg = codeLines[li];
    if(ci < seg.t.length){
      ci++;
      renderBuf(li,ci);
      setTimeout(typeStep, 14);
    } else {
      li++; ci=0;
      setTimeout(typeStep, 14);
    }
  }
  function renderBuf(upToLine, partial){
    let html='';
    for(let i=0;i<upToLine;i++){
      const s=codeLines[i];
      html += s.c ? `<span class="${s.c}">${escapeHtml(s.t)}</span>` : escapeHtml(s.t);
    }
    const cur = codeLines[upToLine];
    if(cur){
      const partialText = cur.t.slice(0,partial);
      html += cur.c ? `<span class="${cur.c}">${escapeHtml(partialText)}</span>` : escapeHtml(partialText);
    }
    twEl.innerHTML = html;
  }
  function escapeHtml(s){return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');}
  setTimeout(typeStep, 900);

  // scroll reveal
  const revealEls = document.querySelectorAll('.reveal, .timeline');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach((entry,idx)=>{
      if(entry.isIntersecting){
        setTimeout(()=>entry.target.classList.add('visible'), idx*60);
        io.unobserve(entry.target);
      }
    });
  },{threshold:0.15});
  revealEls.forEach(el=>io.observe(el));

  // project card tilt + glow
  document.querySelectorAll('.project-card').forEach(card=>{
    card.addEventListener('mousemove', e=>{
      const r = card.getBoundingClientRect();
      const x = e.clientX - r.left, y = e.clientY - r.top;
      card.style.setProperty('--mx', x+'px');
      card.style.setProperty('--my', y+'px');
      const rx = ((y / r.height) - 0.5) * -8;
      const ry = ((x / r.width) - 0.5) * 8;
      card.style.transform = `perspective(700px) rotateX(${rx}deg) rotateY(${ry}deg) translateY(-4px)`;
    });
    card.addEventListener('mouseleave', ()=>{ card.style.transform = ''; });
  });

  // nav active link on scroll
  const sections = document.querySelectorAll('section, header');
  const navA = document.querySelectorAll('.nav-links a');
  window.addEventListener('scroll', ()=>{
    let cur='';
    sections.forEach(s=>{
      if(window.scrollY >= s.offsetTop - 200) cur = s.getAttribute('id');
    });
    navA.forEach(a=>{
      a.style.color = a.getAttribute('href') === '#'+cur ? 'var(--text)' : '';
    });
  });
</script>
</body>
</html>
