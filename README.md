<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LexCity — Equality. Justice. For Everyone.</title>
<style>
  :root{
    --ink:#23303a;
    --panel:#1c2730;
    --marble:#EFEDE8;
    --gold:#B69B74;
    --maroon:#6E3E3E;
    --slate:#9aa3a4;
    --line:rgba(239,237,232,0.14);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--ink);
    color:var(--marble);
    font-family:'Georgia','Iowan Old Style',serif;
    overflow-x:hidden;
    cursor:default;
  }
  ::selection{background:var(--gold);color:var(--ink);}

  #glow{
    position:fixed; top:0; left:0; width:520px; height:520px; z-index:0;
    pointer-events:none; border-radius:50%;
    background:radial-gradient(circle, rgba(182,155,116,0.10), transparent 70%);
    transform:translate(-50%,-50%);
    transition:opacity .4s;
    opacity:0;
  }

  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.001ms !important; animation-iteration-count:1 !important; transition-duration:0.001ms !important; scroll-behavior:auto !important;}
  }

  nav{
    position:fixed; top:0; left:0; right:0; z-index:50;
    display:flex; align-items:center; justify-content:space-between;
    padding:22px 6vw;
    backdrop-filter:blur(10px);
    background:linear-gradient(to bottom, rgba(35,48,58,0.88), transparent);
  }
  .brand{
    font-size:1.3rem; letter-spacing:0.12em; font-weight:700;
    text-transform:uppercase;
  }
  .brand span{color:var(--gold);}
  .nav-links{display:flex; gap:34px; font-family:'Helvetica Neue',Arial,sans-serif;}
  .nav-links a{
    color:var(--marble); text-decoration:none; font-size:0.78rem;
    letter-spacing:0.14em; text-transform:uppercase; opacity:0.75;
    transition:opacity .3s, color .3s; position:relative; padding-bottom:6px;
  }
  .nav-links a::after{
    content:''; position:absolute; left:0; bottom:0; width:100%; height:1px;
    background:var(--gold); transform:scaleX(0); transform-origin:right;
    transition:transform .45s cubic-bezier(.65,0,.35,1);
  }
  .nav-links a:hover{opacity:1; color:var(--gold);}
  .nav-links a:hover::after{transform:scaleX(1); transform-origin:left;}
  @media (max-width:700px){ .nav-links{display:none;} }

  #hero{
    position:relative; height:100vh; width:100%;
    display:flex; align-items:center; justify-content:center;
  }
  #scales-canvas{
    position:absolute; inset:0; width:100%; height:100%; display:block;
  }
  .hero-text{
    position:relative; z-index:2; text-align:center; max-width:880px; padding:0 6vw;
    pointer-events:none;
  }
  .eyebrow{
    font-family:'Helvetica Neue',Arial,sans-serif;
    letter-spacing:0.3em; text-transform:uppercase; font-size:0.72rem;
    color:var(--gold); opacity:0; animation:riseIn 1.2s cubic-bezier(.16,1,.3,1) forwards 0.2s;
  }
  h1.title{
    font-size:clamp(2.6rem, 8vw, 5.6rem);
    line-height:1.05; font-weight:400; margin:18px 0 22px;
    opacity:0; animation:riseIn 1.3s cubic-bezier(.16,1,.3,1) forwards 0.45s;
  }
  h1.title em{font-style:italic; color:var(--gold);}
  .sub{
    font-family:'Helvetica Neue',Arial,sans-serif;
    font-size:1.05rem; line-height:1.7; color:var(--slate);
    opacity:0; animation:riseIn 1.3s cubic-bezier(.16,1,.3,1) forwards 0.8s;
  }
  @keyframes riseIn{
    from{opacity:0; transform:translateY(34px) scale(.985); filter:blur(6px);}
    to{opacity:1; transform:translateY(0) scale(1); filter:blur(0);}
  }
  .scroll-hint{
    position:absolute; bottom:34px; left:50%; transform:translateX(-50%);
    width:1px; height:46px; background:var(--line); overflow:hidden; z-index:2;
    opacity:0; animation:fadeInOnly 1s ease forwards 1.4s;
  }
  @keyframes fadeInOnly{ to{opacity:1;} }
  .scroll-hint::after{
    content:''; position:absolute; top:-100%; left:0; width:100%; height:100%;
    background:var(--gold); animation:drip 2.2s cubic-bezier(.65,0,.35,1) infinite;
  }
  @keyframes drip{
    0%{top:-100%;} 55%{top:100%;} 100%{top:100%;}
  }

  section{
    padding:140px 6vw; position:relative; max-width:1200px; margin:0 auto;
  }
  .label{
    font-family:'Helvetica Neue',Arial,sans-serif;
    font-size:0.72rem; letter-spacing:0.28em; text-transform:uppercase;
    color:var(--gold); display:block; margin-bottom:18px;
  }
  h2{
    font-size:clamp(1.9rem, 4.2vw, 3.2rem); font-weight:400; line-height:1.15;
    margin-bottom:28px; max-width:760px;
  }
  p.lead{
    font-family:'Helvetica Neue',Arial,sans-serif;
    font-size:1.05rem; line-height:1.85; color:var(--slate); max-width:620px;
  }

  .reveal{
    opacity:0; transform:translateY(46px); filter:blur(4px);
    transition:opacity 1s cubic-bezier(.16,1,.3,1), transform 1s cubic-bezier(.16,1,.3,1), filter 1s cubic-bezier(.16,1,.3,1);
  }
  .reveal.in{opacity:1; transform:translateY(0); filter:blur(0);}

  .pillars{
    display:grid; grid-template-columns:repeat(3,1fr); gap:1px;
    background:var(--line); border:1px solid var(--line); margin-top:60px;
  }
  @media (max-width:760px){ .pillars{grid-template-columns:1fr;} }
  .pillar{
    background:var(--ink); padding:46px 34px;
    transition:background .45s cubic-bezier(.16,1,.3,1), transform .45s cubic-bezier(.16,1,.3,1);
    border-bottom:2px solid transparent;
  }
  .pillar:hover{
    background:var(--panel); transform:translateY(-6px);
    border-bottom:2px solid var(--maroon);
  }
  .pillar .num{
    font-family:'Helvetica Neue',Arial,sans-serif; color:var(--gold);
    font-size:0.78rem; letter-spacing:0.2em;
    transition:letter-spacing .4s;
  }
  .pillar:hover .num{letter-spacing:0.32em;}
  .pillar h3{font-size:1.4rem; font-weight:400; margin:18px 0 14px;}
  .pillar p{
    font-family:'Helvetica Neue',Arial,sans-serif; color:var(--slate);
    font-size:0.92rem; line-height:1.7;
  }

  #balance{
    padding:0; text-align:center; max-width:none;
  }
  .balance-wrap{
    position:relative; height:60vh; min-height:380px;
    display:flex; align-items:center; justify-content:center;
    border-top:1px solid var(--line); border-bottom:1px solid var(--line);
  }
  #balance-canvas{position:absolute; inset:0; width:100%; height:100%;}
  .balance-caption{
    position:relative; z-index:2; font-size:clamp(1.4rem,3.4vw,2.2rem);
    max-width:680px; padding:0 6vw; pointer-events:none;
  }
  .balance-caption .gold{color:var(--gold); font-style:italic;}

  .quote-block{text-align:center; max-width:780px;}
  .quote-block q{
    font-size:clamp(1.5rem,3.4vw,2.4rem); line-height:1.4; font-style:italic;
    display:block; margin-bottom:22px;
  }
  .quote-block cite{
    font-family:'Helvetica Neue',Arial,sans-serif; color:var(--gold);
    font-size:0.8rem; letter-spacing:0.18em; text-transform:uppercase;
  }

  #join{text-align:center;}
  .btn{
    display:inline-block; margin-top:30px; padding:16px 42px;
    border:1px solid var(--gold); color:var(--gold); text-decoration:none;
    font-family:'Helvetica Neue',Arial,sans-serif; font-size:0.8rem;
    letter-spacing:0.18em; text-transform:uppercase;
    transition:color .4s; position:relative; overflow:hidden; z-index:1;
  }
  .btn::before{
    content:''; position:absolute; inset:0; background:var(--gold);
    transform:scaleX(0); transform-origin:left; z-index:-1;
    transition:transform .45s cubic-bezier(.65,0,.35,1);
  }
  .btn:hover{color:var(--ink);}
  .btn:hover::before{transform:scaleX(1);}
  .btn:focus-visible{outline:2px solid var(--maroon); outline-offset:3px;}

  footer{
    padding:50px 6vw; text-align:center;
    font-family:'Helvetica Neue',Arial,sans-serif; color:var(--slate);
    font-size:0.78rem; letter-spacing:0.08em; border-top:1px solid var(--line);
  }
  footer .brand{font-size:0.9rem; margin-bottom:8px; display:block;}
</style>
</head>
<body>
<div id="glow"></div>

<nav>
  <div class="brand">Lex<span>City</span></div>
  <div class="nav-links">
    <a href="#mission">Mission</a>
    <a href="#balance">Balance</a>
    <a href="#join">Join</a>
  </div>
</nav>

<section id="hero">
  <canvas id="scales-canvas"></canvas>
  <div class="hero-text">
    <span class="eyebrow">A City Built On Even Ground</span>
    <h1 class="title">Where <em>equality</em><br>holds the line.</h1>
    <p class="sub">LexCity is a civic platform for people who believe justice shouldn't depend on who you are, where you're from, or what you can afford.</p>
  </div>
  <div class="scroll-hint"></div>
</section>

<section id="mission">
  <span class="label">01 — Mission</span>
  <h2 class="reveal">Justice isn't an ideal we wait for. It's infrastructure we build.</h2>
  <p class="lead reveal">LexCity exists to make fairness visible and actionable — connecting people to legal aid, civic education, and the organizers fighting to close the gap between the law as written and the law as lived.</p>

  <div class="pillars">
    <div class="pillar reveal" style="transition-delay:0s">
      <span class="num">01</span>
      <h3>Equal Access</h3>
      <p>Free legal resources and plain-language guides, so understanding your rights never depends on your income.</p>
    </div>
    <div class="pillar reveal" style="transition-delay:0.12s">
      <span class="num">02</span>
      <h3>Transparent Process</h3>
      <p>We track how policy actually plays out in communities, and publish what we find — no spin, no gatekeeping.</p>
    </div>
    <div class="pillar reveal" style="transition-delay:0.24s">
      <span class="num">03</span>
      <h3>Collective Action</h3>
      <p>Tools for organizers and neighbors to coordinate, petition, and hold institutions accountable together.</p>
    </div>
  </div>
</section>

<section id="balance">
  <div class="balance-wrap">
    <canvas id="balance-canvas"></canvas>
    <p class="balance-caption reveal">Two sides. <span class="gold">One standard.</span> The scale only means something when it stays level for everyone who steps on it.</p>
  </div>
</section>

<section id="quote">
  <div class="quote-block reveal" style="margin:0 auto; text-align:center;">
    <q>The arc of the moral universe is long, but it bends toward justice.</q>
    <cite>— Inspiration for the LexCity Charter</cite>
  </div>
</section>

<section id="join">
  <span class="label">02 — Get Involved</span>
  <h2 class="reveal" style="margin:0 auto 10px; max-width:680px;">Equality moves at the speed of people who show up.</h2>
  <p class="lead reveal" style="margin:0 auto;">Join LexCity and add your weight to the right side of the scale.</p>
  <a href="#" class="btn reveal">Become A Member</a>
</section>

<footer>
  <span class="brand">LexCity</span>
  Built on equality. Maintained by everyone.
</footer>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
const reveals = document.querySelectorAll('.reveal');
const obs = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('in'); } });
},{threshold:0.18});
reveals.forEach(el=>obs.observe(el));

(function(){
  const canvas = document.getElementById('scales-canvas');
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(45, window.innerWidth/window.innerHeight, 0.1, 100);
  camera.position.set(0, 0.6, 9);

  const renderer = new THREE.WebGLRenderer({canvas, antialias:true, alpha:true});
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

  const gold = new THREE.Color('#B69B74');
  const matGold = new THREE.MeshStandardMaterial({color:gold, metalness:0.55, roughness:0.3});
  const matDark = new THREE.MeshStandardMaterial({color:'#3a2424', metalness:0.3, roughness:0.6});

  const rig = new THREE.Group();
  scene.add(rig);

  const post = new THREE.Mesh(new THREE.CylinderGeometry(0.05,0.05,4,16), matGold);
  post.position.y = -0.2;
  rig.add(post);

  const base = new THREE.Mesh(new THREE.ConeGeometry(0.6,0.8,32), matDark);
  base.position.y = -2.1;
  rig.add(base);

  const beamGroup = new THREE.Group();
  beamGroup.position.y = 1.8;
  rig.add(beamGroup);
  const beam = new THREE.Mesh(new THREE.CylinderGeometry(0.035,0.035,4.4,16), matGold);
  beam.rotation.z = Math.PI/2;
  beamGroup.add(beam);

  function makePan(x){
    const group = new THREE.Group();
    group.position.x = x;
    const chainL = new THREE.Mesh(new THREE.CylinderGeometry(0.012,0.012,1.1,8), matGold);
    chainL.position.set(-0.32, -0.55, 0);
    chainL.rotation.z = 0.3;
    group.add(chainL);
    const chainR = new THREE.Mesh(new THREE.CylinderGeometry(0.012,0.012,1.1,8), matGold);
    chainR.position.set(0.32, -0.55, 0);
    chainR.rotation.z = -0.3;
    group.add(chainR);
    const pan = new THREE.Mesh(new THREE.CylinderGeometry(0.55,0.5,0.08,32), matGold);
    pan.position.y = -1.1;
    group.add(pan);
    return group;
  }
  const panL = makePan(-2.1);
  const panR = makePan(2.1);
  beamGroup.add(panL, panR);

  scene.add(new THREE.AmbientLight('#ffffff', 0.55));
  const key = new THREE.PointLight('#e8d3ac', 60, 30);
  key.position.set(5,6,6);
  scene.add(key);
  const rim = new THREE.PointLight('#6e3e3e', 35, 30);
  rim.position.set(-6,-2,4);
  scene.add(rim);

  let mouseX = 0, mouseY = 0, smX = 0, smY = 0;
  window.addEventListener('mousemove', (e)=>{
    mouseX = (e.clientX/window.innerWidth - 0.5);
    mouseY = (e.clientY/window.innerHeight - 0.5);
    const glow = document.getElementById('glow');
    glow.style.opacity = 1;
    glow.style.left = e.clientX+'px';
    glow.style.top = e.clientY+'px';
  });
  window.addEventListener('mouseleave', ()=>{ document.getElementById('glow').style.opacity = 0; });

  let t = 0;
  function animate(){
    t += 0.01;
    smX += (mouseX - smX)*0.05;
    smY += (mouseY - smY)*0.05;
    rig.rotation.y = Math.sin(t*0.4)*0.25 + smX*0.45;
    rig.rotation.x = smY*0.18;
    beamGroup.rotation.z = Math.sin(t*0.8)*0.05;
    camera.position.x += (smX*0.6 - camera.position.x)*0.04;
    camera.lookAt(0,0,0);
    renderer.render(scene, camera);
    requestAnimationFrame(animate);
  }
  animate();

  window.addEventListener('resize', ()=>{
    camera.aspect = window.innerWidth/window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  });
})();

(function(){
  const canvas = document.getElementById('balance-canvas');
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(50, window.innerWidth/600, 0.1, 50);
  camera.position.z = 8;

  const renderer = new THREE.WebGLRenderer({canvas, antialias:true, alpha:true});
  renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));

  function resize(){
    const w = canvas.clientWidth, h = canvas.clientHeight;
    renderer.setSize(w,h,false);
    camera.aspect = w/h;
    camera.updateProjectionMatrix();
  }

  const count = 140;
  const geo = new THREE.BufferGeometry();
  const positions = new Float32Array(count*3);
  const speeds = [];
  for(let i=0;i<count;i++){
    positions[i*3] = (Math.random()-0.5)*14;
    positions[i*3+1] = (Math.random()-0.5)*7;
    positions[i*3+2] = (Math.random()-0.5)*6;
    speeds.push(0.2+Math.random()*0.6);
  }
  geo.setAttribute('position', new THREE.BufferAttribute(positions,3));
  const mat = new THREE.PointsMaterial({color:'#B69B74', size:0.06, transparent:true, opacity:0.85});
  const points = new THREE.Points(geo, mat);
  scene.add(points);

  scene.add(new THREE.AmbientLight('#ffffff',0.6));

  let visible = false;
  const io = new IntersectionObserver(es=>{ es.forEach(e=>{ visible = e.isIntersecting; }); },{threshold:0.1});
  io.observe(canvas);

  let t=0;
  function animate(){
    t += 0.008;
    const pos = geo.attributes.position.array;
    for(let i=0;i<count;i++){
      pos[i*3+1] += Math.sin(t*speeds[i]+i)*0.0009;
    }
    geo.attributes.position.needsUpdate = true;
    points.rotation.y = t*0.05;
    if(visible) renderer.render(scene, camera);
    requestAnimationFrame(animate);
  }
  resize();
  animate();
  window.addEventListener('resize', resize);
})();
</script>
</body>
</html>
