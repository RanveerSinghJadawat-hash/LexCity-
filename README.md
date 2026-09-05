<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kessler Voss — Precision Counsel</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300;9..144,500;9..144,600;9..144,700&family=Sora:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#0a0618;
    --bg2:#120a2e;
    --violet:#7c3aed;
    --violet-2:#a78bfa;
    --magenta:#ff2e92;
    --cyan:#22e6d6;
    --gold:#ffc93c;
    --ink:#f6f3ff;
    --muted:#b8aed9;
    --line:rgba(246,243,255,0.12);
    --glass:rgba(255,255,255,0.045);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--ink);
    font-family:'Sora',sans-serif;
    overflow-x:hidden;
    -webkit-font-smoothing:antialiased;
  }
  ::selection{background:var(--magenta);color:#fff;}
  h1,h2,h3,.serif{font-family:'Fraunces',serif;}
  a{color:inherit;text-decoration:none;}

  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.01ms !important; animation-iteration-count:1 !important; transition-duration:0.01ms !important;}
  }

  /* ---------- background texture ---------- */
  .noise-bg{
    position:fixed; inset:0; z-index:0; pointer-events:none;
    background:
      radial-gradient(60% 50% at 15% 10%, rgba(124,58,237,0.35), transparent 60%),
      radial-gradient(50% 40% at 90% 0%, rgba(255,46,146,0.22), transparent 60%),
      radial-gradient(40% 35% at 80% 90%, rgba(34,230,214,0.14), transparent 60%),
      var(--bg);
  }

  /* ---------- nav ---------- */
  header{
    position:fixed; top:0; left:0; right:0; z-index:50;
    display:flex; align-items:center; justify-content:space-between;
    padding:26px 5vw;
    backdrop-filter:blur(14px);
    background:linear-gradient(180deg, rgba(10,6,24,0.75), rgba(10,6,24,0));
  }
  .logo{
    font-family:'Fraunces',serif; font-weight:600; font-size:1.15rem;
    letter-spacing:0.01em;
  }
  .logo span{color:var(--gold);}
  nav ul{list-style:none; display:flex; gap:2.6rem; font-size:0.92rem; color:var(--muted);}
  nav ul li a{transition:color .25s ease; position:relative;}
  nav ul li a:hover{color:var(--ink);}
  .nav-cta{
    padding:11px 22px; border-radius:100px;
    background:linear-gradient(120deg,var(--magenta),var(--violet));
    font-size:0.88rem; font-weight:600; color:#fff;
    box-shadow:0 8px 24px rgba(255,46,146,0.28);
    transition:transform .25s ease, box-shadow .25s ease;
    white-space:nowrap;
  }
  .nav-cta:hover{transform:translateY(-2px); box-shadow:0 12px 30px rgba(255,46,146,0.4);}
  .navlinks{display:flex; align-items:center; gap:2.6rem;}
  @media (max-width:860px){ nav ul{display:none;} }

  /* ---------- hero ---------- */
  .hero{
    position:relative; min-height:100vh; display:flex; align-items:center;
    padding:0 5vw; z-index:1;
  }
  #hero-canvas{
    position:absolute; top:0; right:0; width:56%; height:100%;
    z-index:1; pointer-events:none;
  }
  @media (max-width:900px){ #hero-canvas{width:100%; opacity:0.5;} }
  .hero-inner{max-width:640px; position:relative; z-index:2; padding-top:6rem;}
  .eyebrow{
    display:inline-flex; align-items:center; gap:10px;
    font-size:0.82rem; color:var(--cyan); font-weight:500;
    padding-bottom:1.4rem;
  }
  .eyebrow::before{content:''; width:26px; height:1px; background:var(--cyan);}
  .hero h1{
    font-size:clamp(2.6rem, 5.4vw, 4.6rem);
    font-weight:600; line-height:1.04; letter-spacing:-0.01em;
    background:linear-gradient(100deg, var(--ink) 30%, var(--violet-2) 65%, var(--magenta) 100%);
    -webkit-background-clip:text; background-clip:text; color:transparent;
  }
  .hero p{
    margin-top:1.6rem; font-size:1.08rem; line-height:1.7; color:var(--muted);
    max-width:480px;
  }
  .hero-actions{display:flex; align-items:center; gap:1.6rem; margin-top:2.6rem;}
  .btn-primary{
    padding:15px 30px; border-radius:100px; font-weight:600; font-size:0.95rem;
    background:linear-gradient(120deg,var(--gold),#ff9d4d); color:#1a0f00;
    box-shadow:0 10px 30px rgba(255,201,60,0.25);
    transition:transform .25s ease, box-shadow .25s ease;
  }
  .btn-primary:hover{transform:translateY(-3px); box-shadow:0 16px 36px rgba(255,201,60,0.4);}
  .btn-ghost{font-size:0.92rem; color:var(--ink); border-bottom:1px solid var(--line); padding-bottom:3px; transition:border-color .25s ease;}
  .btn-ghost:hover{border-color:var(--cyan); color:var(--cyan);}

  .scroll-hint{
    position:absolute; bottom:2.6rem; left:5vw; z-index:2;
    display:flex; align-items:center; gap:12px; font-size:0.78rem; color:var(--muted);
  }
  .scroll-hint .dot{
    width:8px; height:8px; border-radius:50%; background:var(--gold);
    box-shadow:0 0 14px var(--gold);
    animation:pulse 2.4s ease-in-out infinite;
  }
  @keyframes pulse{ 0%,100%{opacity:0.4; transform:scale(0.8);} 50%{opacity:1; transform:scale(1.15);} }

  /* ---------- section shell ---------- */
  section{position:relative; z-index:1; padding:8rem 5vw;}
  .section-head{max-width:620px; margin-bottom:4rem;}
  .section-tag{font-size:0.82rem; color:var(--cyan); font-weight:500; margin-bottom:1rem; display:block;}
  .section-head h2{font-size:clamp(1.9rem,3.4vw,2.8rem); font-weight:600; line-height:1.15;}
  .section-head p{color:var(--muted); margin-top:1.1rem; font-size:1.02rem; line-height:1.7; max-width:520px;}

  /* ---------- stats ---------- */
  .stats{
    display:grid; grid-template-columns:repeat(4,1fr); gap:1px;
    background:var(--line); border:1px solid var(--line); border-radius:20px; overflow:hidden;
  }
  .stat{background:var(--bg2); padding:2.6rem 2rem; text-align:left;}
  .stat .num{font-family:'Fraunces',serif; font-size:clamp(2.1rem,3.4vw,3rem); font-weight:600; color:var(--ink);}
  .stat .num .accent{color:var(--gold);}
  .stat .label{color:var(--muted); font-size:0.86rem; margin-top:0.6rem;}
  @media (max-width:760px){ .stats{grid-template-columns:1fr 1fr;} }

  /* ---------- practice areas (3D tilt cards) ---------- */
  .practice-grid{
    display:grid; grid-template-columns:repeat(3,1fr); gap:1.6rem;
    perspective:1400px;
  }
  @media (max-width:940px){ .practice-grid{grid-template-columns:1fr 1fr;} }
  @media (max-width:620px){ .practice-grid{grid-template-columns:1fr;} }
  .p-card{
    background:var(--glass);
    border:1px solid var(--line);
    border-radius:22px;
    padding:2.4rem 2rem;
    transform-style:preserve-3d;
    transition:transform .15s ease, border-color .3s ease, background .3s ease;
    cursor:default;
  }
  .p-card:hover{border-color:rgba(255,255,255,0.28); background:rgba(255,255,255,0.07);}
  .p-icon{
    width:52px; height:52px; border-radius:14px; margin-bottom:1.6rem;
    display:flex; align-items:center; justify-content:center;
    transform:translateZ(30px);
    font-size:1.4rem;
  }
  .p-card h3{font-size:1.24rem; font-weight:600; margin-bottom:0.7rem; transform:translateZ(20px);}
  .p-card p{color:var(--muted); font-size:0.92rem; line-height:1.65; transform:translateZ(10px);}
  .p-card:nth-child(1) .p-icon{background:linear-gradient(135deg,var(--violet),var(--magenta));}
  .p-card:nth-child(2) .p-icon{background:linear-gradient(135deg,var(--cyan),var(--violet));}
  .p-card:nth-child(3) .p-icon{background:linear-gradient(135deg,var(--gold),var(--magenta));}
  .p-card:nth-child(4) .p-icon{background:linear-gradient(135deg,var(--magenta),var(--cyan));}
  .p-card:nth-child(5) .p-icon{background:linear-gradient(135deg,var(--violet),var(--gold));}
  .p-card:nth-child(6) .p-icon{background:linear-gradient(135deg,var(--cyan),var(--gold));}

  /* ---------- approach ---------- */
  .approach{background:var(--bg2); border-radius:32px; margin:0 5vw; padding:6rem 5vw; width:auto;}
  .steps{display:flex; flex-direction:column;}
  .step{
    display:grid; grid-template-columns:90px 1fr; gap:2rem;
    padding:2.2rem 0; border-top:1px solid var(--line);
    align-items:start;
  }
  .step:last-child{border-bottom:1px solid var(--line);}
  .step .idx{font-family:'Fraunces',serif; font-size:1.6rem; color:var(--muted); font-weight:300;}
  .step h3{font-size:1.2rem; font-weight:600; margin-bottom:0.5rem;}
  .step p{color:var(--muted); font-size:0.95rem; line-height:1.7; max-width:560px;}

  /* ---------- team ---------- */
  .team-grid{display:grid; grid-template-columns:repeat(4,1fr); gap:1.6rem;}
  @media (max-width:940px){ .team-grid{grid-template-columns:1fr 1fr;} }
  .member{border-radius:20px; overflow:hidden; border:1px solid var(--line);}
  .member .avatar{
    height:220px; position:relative;
    display:flex; align-items:center; justify-content:center;
    font-family:'Fraunces',serif; font-size:2.6rem; font-weight:600; color:#fff;
  }
  .member:nth-child(1) .avatar{background:linear-gradient(150deg,var(--violet),var(--magenta));}
  .member:nth-child(2) .avatar{background:linear-gradient(150deg,var(--cyan),var(--violet));}
  .member:nth-child(3) .avatar{background:linear-gradient(150deg,var(--gold),var(--magenta) 80%);}
  .member:nth-child(4) .avatar{background:linear-gradient(150deg,var(--magenta),var(--cyan));}
  .member .info{padding:1.3rem 1.4rem; background:var(--glass);}
  .member .info h4{font-size:1rem; font-weight:600;}
  .member .info span{color:var(--muted); font-size:0.84rem;}

  /* ---------- testimonial ---------- */
  .quote-wrap{
    border-radius:28px; padding:5rem 6vw; text-align:left; position:relative;
    background:linear-gradient(120deg, rgba(124,58,237,0.16), rgba(255,46,146,0.1));
    border:1px solid var(--line);
  }
  .quote-wrap .mark{font-family:'Fraunces',serif; font-size:5rem; color:var(--gold); line-height:0.5; opacity:0.8;}
  .quote-wrap blockquote{
    font-family:'Fraunces',serif; font-size:clamp(1.5rem,2.6vw,2.2rem); font-weight:500;
    line-height:1.45; max-width:820px; margin-top:1.4rem;
  }
  .quote-wrap .who{margin-top:2rem; color:var(--muted); font-size:0.92rem;}

  /* ---------- cta / footer ---------- */
  .cta-final{text-align:center; padding-top:9rem; padding-bottom:5rem;}
  .cta-final h2{font-size:clamp(2.2rem,4.6vw,3.6rem); font-weight:600; max-width:760px; margin:0 auto; line-height:1.15;}
  .cta-final p{color:var(--muted); margin:1.4rem auto 2.4rem; max-width:480px;}
  footer{
    border-top:1px solid var(--line); padding:3rem 5vw; z-index:1; position:relative;
    display:flex; justify-content:space-between; flex-wrap:wrap; gap:1.6rem;
    color:var(--muted); font-size:0.85rem;
  }
  footer .logo{margin-bottom:0.6rem;}
</style>
</head>
<body>

<div class="noise-bg"></div>

<header>
  <div class="logo">KESSLER<span>·</span>VOSS</div>
  <div class="navlinks">
    <ul>
      <li><a href="#practice">Practice</a></li>
      <li><a href="#approach">Approach</a></li>
      <li><a href="#team">Team</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <a href="#contact" class="nav-cta">Book Consultation</a>
  </div>
</header>

<section class="hero">
  <canvas id="hero-canvas"></canvas>
  <div class="hero-inner">
    <span class="eyebrow">TRIAL &amp; TRANSACTIONAL LAW</span>
    <h1>Precision counsel for high-stakes moments.</h1>
    <p>Kessler Voss represents founders, funds, and litigants who cannot afford an ordinary outcome. Twenty-two years of judgment, sharpened for the cases that decide everything.</p>
    <div class="hero-actions">
      <a href="#contact" class="btn-primary">Book Consultation</a>
      <a href="#practice" class="btn-ghost">See our practice areas</a>
    </div>
  </div>
  <div class="scroll-hint"><span class="dot"></span> Scroll to explore</div>
</section>

<section id="stats-section">
  <div class="stats">
    <div class="stat"><div class="num"><span class="accent" data-count="317">0</span></div><div class="label">Cases won at trial</div></div>
    <div class="stat"><div class="num">$<span class="accent" data-count="940">0</span>M</div><div class="label">Recovered for clients</div></div>
    <div class="stat"><div class="num"><span class="accent" data-count="22">0</span></div><div class="label">Years in practice</div></div>
    <div class="stat"><div class="num"><span class="accent" data-count="96">0</span>%</div><div class="label">Client retention rate</div></div>
  </div>
</section>

<section id="practice">
  <div class="section-head">
    <span class="section-tag">PRACTICE AREAS</span>
    <h2>Six disciplines, one standard of rigor.</h2>
    <p>We keep our docket deliberately narrow so every matter gets partner-level attention, from first filing to final ruling.</p>
  </div>
  <div class="practice-grid" id="practice-grid">
    <div class="p-card"><div class="p-icon">⚖️</div><h3>Commercial Litigation</h3><p>Contract disputes, shareholder actions, and courtroom strategy for companies with real exposure.</p></div>
    <div class="p-card"><div class="p-icon">🤝</div><h3>M&amp;A &amp; Corporate</h3><p>Structuring, diligence, and closing for deals where the fine print determines the outcome.</p></div>
    <div class="p-card"><div class="p-icon">💠</div><h3>Intellectual Property</h3><p>Patent, trademark, and trade secret defense for teams whose ideas are the whole business.</p></div>
    <div class="p-card"><div class="p-icon">🏛️</div><h3>Regulatory &amp; Compliance</h3><p>Navigating agency scrutiny before it becomes an enforcement action.</p></div>
    <div class="p-card"><div class="p-icon">🏢</div><h3>Real Estate</h3><p>Acquisition, financing, and disputes across commercial and mixed-use portfolios.</p></div>
    <div class="p-card"><div class="p-icon">👪</div><h3>Private Client</h3><p>Estate structuring and succession planning for founders and family enterprises.</p></div>
  </div>
</section>

<section id="approach">
  <div class="approach">
    <div class="section-head" style="margin-bottom:2.5rem;">
      <span class="section-tag">HOW WE WORK</span>
      <h2>A process built for pressure.</h2>
    </div>
    <div class="steps">
      <div class="step"><div class="idx">01</div><div><h3>Case assessment</h3><p>A senior partner reviews the matter within 48 hours and gives you a candid read on exposure, timeline, and cost before you commit to anything.</p></div></div>
      <div class="step"><div class="idx">02</div><div><h3>Strategy &amp; staffing</h3><p>We assemble the smallest team that can win the matter — no bench-warming associates billing to learn on your dollar.</p></div></div>
      <div class="step"><div class="idx">03</div><div><h3>Active counsel</h3><p>You get direct partner access throughout, with a standing biweekly briefing so nothing surprises you.</p></div></div>
      <div class="step"><div class="idx">04</div><div><h3>Resolution</h3><p>Settlement, verdict, or close — we push for the outcome that actually serves your position, not the one that's easiest to bill.</p></div></div>
    </div>
  </div>
</section>

<section id="team">
  <div class="section-head">
    <span class="section-tag">THE PARTNERS</span>
    <h2>Judgment you can call directly.</h2>
  </div>
  <div class="team-grid">
    <div class="member"><div class="avatar">MK</div><div class="info"><h4>Marisol Kessler</h4><span>Founding Partner, Litigation</span></div></div>
    <div class="member"><div class="avatar">DV</div><div class="info"><h4>Daniel Voss</h4><span>Founding Partner, Corporate</span></div></div>
    <div class="member"><div class="avatar">RA</div><div class="info"><h4>Renata Aoki</h4><span>Partner, Intellectual Property</span></div></div>
    <div class="member"><div class="avatar">JT</div><div class="info"><h4>Julian Thorne</h4><span>Partner, Regulatory</span></div></div>
  </div>
</section>

<section id="testimonial">
  <div class="quote-wrap">
    <div class="mark">"</div>
    <blockquote>They gave us a real number on day one, then delivered a better one at trial. That kind of honesty is rare in litigation counsel.</blockquote>
    <div class="who">— General Counsel, mid-market logistics company</div>
  </div>
</section>

<section id="contact" class="cta-final">
  <h2>Your case deserves a direct line to the partner handling it.</h2>
  <p>Consultations are confidential and typically scheduled within three business days.</p>
  <a href="#" class="btn-primary">Book Consultation</a>
</section>

<footer>
  <div>
    <div class="logo">KESSLER<span>·</span>VOSS</div>
    <div>110 Meridian Ave, Suite 1900 · New York, NY</div>
  </div>
  <div>© 2026 Kessler Voss LLP. Attorney advertising.</div>
</footer>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r160/three.min.js"></script>
<script>
/* ---------------- 3D HERO SCENE ---------------- */
(function(){
  const canvas = document.getElementById('hero-canvas');
  if(!canvas || !window.THREE) return;
  const prefersReduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  const renderer = new THREE.WebGLRenderer({canvas, alpha:true, antialias:true});
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(45, 1, 0.1, 100);
  camera.position.set(0, 0, 9);

  function resize(){
    const w = canvas.clientWidth, h = canvas.clientHeight;
    renderer.setSize(w, h, false);
    camera.aspect = w / h;
    camera.updateProjectionMatrix();
  }

  // lights — vivid, colored, for glassy refractive highlights
  scene.add(new THREE.AmbientLight(0x201035, 1.4));
  const l1 = new THREE.PointLight(0xff2e92, 60, 30); l1.position.set(4, 3, 4); scene.add(l1);
  const l2 = new THREE.PointLight(0x22e6d6, 50, 30); l2.position.set(-4, -2, 3); scene.add(l2);
  const l3 = new THREE.PointLight(0xffc93c, 40, 30); l3.position.set(0, 4, -3); scene.add(l3);
  const l4 = new THREE.PointLight(0x7c3aed, 45, 30); l4.position.set(-3, 3, -2); scene.add(l4);

  // core gem — refractive icosahedron
  const gemGeo = new THREE.IcosahedronGeometry(2.15, 1);
  const gemMat = new THREE.MeshPhysicalMaterial({
    color: 0xffffff,
    metalness: 0.1,
    roughness: 0.08,
    transmission: 1,
    thickness: 2.2,
    ior: 1.5,
    iridescence: 1,
    iridescenceIOR: 1.3,
    iridescenceThicknessRange: [100, 500],
    clearcoat: 1,
    clearcoatRoughness: 0.05,
    envMapIntensity: 1.4
  });
  const gem = new THREE.Mesh(gemGeo, gemMat);
  scene.add(gem);

  // wireframe shell rotating opposite direction, for extra faceted sparkle
  const wireGeo = new THREE.IcosahedronGeometry(2.5, 1);
  const wireMat = new THREE.MeshBasicMaterial({color:0xa78bfa, wireframe:true, transparent:true, opacity:0.22});
  const wire = new THREE.Mesh(wireGeo, wireMat);
  scene.add(wire);

  // orbiting satellite shapes
  const satellites = [];
  const satGeoTypes = [
    new THREE.OctahedronGeometry(0.28),
    new THREE.TetrahedronGeometry(0.3),
    new THREE.TorusGeometry(0.26, 0.08, 12, 24)
  ];
  const satColors = [0xff2e92, 0x22e6d6, 0xffc93c];
  for(let i=0;i<9;i++){
    const geo = satGeoTypes[i % satGeoTypes.length];
    const mat = new THREE.MeshStandardMaterial({
      color: satColors[i % satColors.length],
      emissive: satColors[i % satColors.length],
      emissiveIntensity: 0.6,
      metalness: 0.4,
      roughness: 0.3
    });
    const mesh = new THREE.Mesh(geo, mat);
    const radius = 3.4 + Math.random()*1.6;
    const angle = (i/9) * Math.PI * 2;
    const yOff = (Math.random()-0.5) * 3;
    satellites.push({mesh, radius, angle, yOff, speed: 0.15 + Math.random()*0.25});
    scene.add(mesh);
  }

  // faint starfield points
  const starCount = 220;
  const starGeo = new THREE.BufferGeometry();
  const starPos = new Float32Array(starCount*3);
  for(let i=0;i<starCount;i++){
    starPos[i*3] = (Math.random()-0.5)*20;
    starPos[i*3+1] = (Math.random()-0.5)*20;
    starPos[i*3+2] = (Math.random()-0.5)*20 - 4;
  }
  starGeo.setAttribute('position', new THREE.BufferAttribute(starPos, 3));
  const starMat = new THREE.PointsMaterial({color:0xffffff, size:0.035, transparent:true, opacity:0.5});
  const stars = new THREE.Points(starGeo, starMat);
  scene.add(stars);

  let mouseX = 0, mouseY = 0;
  window.addEventListener('mousemove', (e)=>{
    mouseX = (e.clientX / window.innerWidth - 0.5);
    mouseY = (e.clientY / window.innerHeight - 0.5);
  });

  resize();
  window.addEventListener('resize', resize);

  const clock = new THREE.Clock();
  function animate(){
    requestAnimationFrame(animate);
    const t = clock.getElapsedTime();

    if(!prefersReduced){
      gem.rotation.y = t * 0.28;
      gem.rotation.x = Math.sin(t*0.2) * 0.25;
      wire.rotation.y = -t * 0.16;
      wire.rotation.x = -Math.sin(t*0.15) * 0.2;

      satellites.forEach(s=>{
        const a = s.angle + t * s.speed;
        s.mesh.position.set(Math.cos(a)*s.radius, s.yOff + Math.sin(t*0.4+s.angle)*0.4, Math.sin(a)*s.radius*0.6);
        s.mesh.rotation.x += 0.01;
        s.mesh.rotation.y += 0.015;
      });

      stars.rotation.y = t * 0.01;

      camera.position.x += (mouseX*1.4 - camera.position.x) * 0.03;
      camera.position.y += (-mouseY*1.0 - camera.position.y) * 0.03;
      camera.lookAt(0,0,0);
    }

    renderer.render(scene, camera);
  }
  animate();
})();

/* ---------------- stat counters ---------------- */
(function(){
  const els = document.querySelectorAll('[data-count]');
  const animateCount = (el)=>{
    const target = parseInt(el.getAttribute('data-count'), 10);
    const dur = 1400;
    const start = performance.now();
    function step(now){
      const p = Math.min((now-start)/dur, 1);
      const eased = 1 - Math.pow(1-p, 3);
      el.textContent = Math.floor(eased * target);
      if(p < 1) requestAnimationFrame(step);
      else el.textContent = target;
    }
    requestAnimationFrame(step);
  };
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(entry=>{
      if(entry.isIntersecting){
        animateCount(entry.target);
        io.unobserve(entry.target);
      }
    });
  }, {threshold:0.5});
  els.forEach(el=>io.observe(el));
})();

/* ---------------- 3D tilt on practice cards ---------------- */
(function(){
  const cards = document.querySelectorAll('.p-card');
  cards.forEach(card=>{
    card.addEventListener('mousemove', (e)=>{
      const r = card.getBoundingClientRect();
      const x = (e.clientX - r.left)/r.width - 0.5;
      const y = (e.clientY - r.top)/r.height - 0.5;
      card.style.transform = `rotateY(${x*14}deg) rotateX(${-y*14}deg) translateY(-4px)`;
    });
    card.addEventListener('mouseleave', ()=>{
      card.style.transform = 'rotateY(0) rotateX(0) translateY(0)';
    });
  });
})();
</script>
</body>
</html>
