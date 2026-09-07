<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Flicker</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Unbounded:wght@500;700;800&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#0c0c10;
    --surface:#18181e;
    --surface-2:#212129;
    --surface-3: #2a2a34;
    --border:#2a2a33;
    --text:#f3f1ea;
    --text-muted:#96959f;
    --accent:#e8b84b;
    --accent-dim:#7a6329;
    --accent-2:#3fa9a0;
    --danger:#e1543a;
    --radius:16px;
    --radius-sm:10px;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:var(--bg);
    color:var(--text);
    font-family:'Inter',system-ui,sans-serif;
    -webkit-font-smoothing:antialiased;
    overflow-x:hidden;
  }
  h1,h2,h3,.brand,.display{
    font-family:'Unbounded',system-ui,sans-serif;
  }
  a{color:inherit;text-decoration:none;}
  button{font-family:inherit;cursor:pointer;}
  img{-webkit-user-drag:none;user-select:none;}
  ::selection{background:var(--accent);color:#141414;}

  /* ---------- layout ---------- */
  .app{min-height:100vh;display:flex;flex-direction:column;}
  .topbar{
    position:sticky;top:0;z-index:40;
    display:flex;align-items:center;gap:18px;
    padding:14px 24px;
    background:rgba(12,12,16,.86);
    backdrop-filter:blur(10px);
    border-bottom:1px solid var(--border);
  }
  .brand{
    font-size:20px;font-weight:800;letter-spacing:.2px;
    display:flex;align-items:center;gap:8px;cursor:pointer;flex-shrink:0;
  }
  .brand .dot{width:10px;height:10px;border-radius:50%;background:var(--accent);
    box-shadow:0 0 0 4px rgba(232,184,75,.18);}
  .search{
    flex:1;max-width:520px;display:flex;align-items:center;
    background:var(--surface);border:1px solid var(--border);
    border-radius:999px;padding:9px 16px;gap:8px;
    transition:border-color .2s;
  }
  .search:focus-within{border-color:var(--accent-dim);}
  .search input{
    background:none;border:none;outline:none;color:var(--text);
    font-size:14px;width:100%;
  }
  .search input::placeholder{color:var(--text-muted);}
  .search svg{flex-shrink:0;opacity:.6;}
  .top-actions{display:flex;align-items:center;gap:12px;margin-left:auto;position:relative;}
  .icon-btn{
    width:38px;height:38px;border-radius:50%;border:1px solid var(--border);
    background:var(--surface);display:flex;align-items:center;justify-content:center;
    color:var(--text);transition:background .18s, transform .12s;
  }
  .icon-btn:hover{background:var(--surface-2);}
  .icon-btn:active{transform:scale(.92);}
  .avatar{
    width:38px;height:38px;border-radius:50%;object-fit:cover;
    border:2px solid var(--border);cursor:pointer;transition:border-color .18s;
    flex-shrink:0;
  }
  .avatar:hover{border-color:var(--accent-dim);}

  .body-row{display:flex;flex:1;min-height:0;}
  .sidebar{
    width:220px;flex-shrink:0;padding:18px 12px;
    border-right:1px solid var(--border);
    display:flex;flex-direction:column;gap:2px;
    position:sticky;top:65px;height:calc(100vh - 65px);
  }
  .nav-item{
    display:flex;align-items:center;gap:14px;
    padding:11px 14px;border-radius:12px;
    color:var(--text-muted);font-size:14.5px;font-weight:500;
    transition:background .16s, color .16s;
  }
  .nav-item:hover{background:var(--surface);color:var(--text);}
  .nav-item.active{background:var(--surface-2);color:var(--accent);}
  .nav-item svg{flex-shrink:0;}
  .sidebar .sep{height:1px;background:var(--border);margin:12px 6px;}
  .sidebar-note{padding:14px 14px 6px;font-size:12px;color:var(--text-muted);line-height:1.5;}

  .main{flex:1;min-width:0;padding:22px 26px 80px;}
  .view-enter{animation:viewIn .32s ease both;}
  @keyframes viewIn{
    from{opacity:0;transform:translateY(10px);}
    to{opacity:1;transform:translateY(0);}
  }

  /* ---------- create dropdown ---------- */
  .create-menu{
    position:absolute;top:48px;right:0;
    background:var(--surface-2);border:1px solid var(--border);
    border-radius:14px;padding:8px;min-width:200px;
    box-shadow:0 18px 40px rgba(0,0,0,.45);
    transform-origin:top right;
    animation:menuIn .16s ease both;
  }
  @keyframes menuIn{from{opacity:0;transform:scale(.92) translateY(-6px);}to{opacity:1;transform:scale(1) translateY(0);}}
  .create-menu button{
    width:100%;display:flex;align-items:center;gap:10px;
    background:none;border:none;color:var(--text);
    padding:10px 12px;border-radius:10px;font-size:14px;font-weight:500;
    transition:background .14s;
  }
  .create-menu button:hover{background:var(--surface-3);}

  /* ---------- section heading ---------- */
  .section-head{display:flex;align-items:baseline;justify-content:space-between;margin:26px 0 14px;}
  .section-head h2{font-size:16px;font-weight:700;margin:0;letter-spacing:.2px;}
  .section-head .see-all{font-size:12.5px;color:var(--accent-2);font-weight:600;}

  /* ---------- reels strip ---------- */
  .reels-strip{display:flex;gap:12px;overflow-x:auto;padding-bottom:6px;scrollbar-width:thin;}
  .reels-strip::-webkit-scrollbar{height:6px;}
  .reels-strip::-webkit-scrollbar-thumb{background:var(--surface-3);border-radius:6px;}
  .reel-card{
    position:relative;flex-shrink:0;width:150px;height:250px;
    border-radius:var(--radius);overflow:hidden;background:var(--surface);
    cursor:pointer;border:1px solid var(--border);
    transition:transform .22s ease, box-shadow .22s ease;
  }
  .reel-card:hover{transform:translateY(-5px);box-shadow:0 14px 30px rgba(0,0,0,.4);}
  .reel-card video,.reel-card img{width:100%;height:100%;object-fit:cover;display:block;}
  .reel-card .rc-overlay{
    position:absolute;inset:0;background:linear-gradient(180deg,rgba(0,0,0,0) 45%,rgba(0,0,0,.85) 100%);
    display:flex;flex-direction:column;justify-content:flex-end;padding:10px;
  }
  .reel-card .rc-title{font-size:12.5px;font-weight:600;line-height:1.3;}
  .reel-card .rc-views{font-size:11px;color:#e6e6e6;margin-top:4px;display:flex;align-items:center;gap:4px;}
  .reel-badge{
    position:absolute;top:9px;right:9px;background:rgba(0,0,0,.5);
    border-radius:999px;padding:4px 6px;display:flex;align-items:center;
  }

  /* ---------- feed grid ---------- */
  .feed{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:22px 18px;}
  .video-card{cursor:pointer;}
  .thumb-wrap{
    position:relative;border-radius:var(--radius);overflow:hidden;
    aspect-ratio:16/9;background:var(--surface);border:1px solid var(--border);
  }
  .thumb-wrap img{width:100%;height:100%;object-fit:cover;display:block;
    transition:transform .35s ease;}
  .video-card:hover .thumb-wrap img{transform:scale(1.06);}
  .duration-badge{
    position:absolute;bottom:7px;right:7px;background:rgba(0,0,0,.75);
    font-size:11px;padding:2px 6px;border-radius:5px;font-weight:600;letter-spacing:.3px;
  }
  .video-meta{display:flex;gap:10px;margin-top:11px;}
  .video-meta img.avatar{width:36px;height:36px;}
  .video-meta .vm-title{font-size:14px;font-weight:600;line-height:1.35;margin:0 0 4px;
    display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;}
  .video-meta .vm-sub{font-size:12.5px;color:var(--text-muted);line-height:1.5;}
  .video-meta .vm-sub span{display:block;}

  /* ---------- post card ---------- */
  .post-card{
    grid-column:1/-1;background:var(--surface);border:1px solid var(--border);
    border-radius:var(--radius);padding:16px 18px;max-width:640px;
  }
  .post-head{display:flex;align-items:center;gap:11px;margin-bottom:10px;}
  .post-head .ph-name{font-size:14px;font-weight:600;}
  .post-head .ph-time{font-size:12px;color:var(--text-muted);}
  .post-text{font-size:14.5px;line-height:1.55;margin:0 0 10px;color:#eceae3;}
  .post-image{width:100%;border-radius:12px;margin-bottom:10px;display:block;max-height:380px;object-fit:cover;}
  .post-actions{display:flex;align-items:center;gap:18px;}

  /* ---------- like / subscribe buttons ---------- */
  .like-btn{
    display:flex;align-items:center;gap:7px;background:none;border:none;
    color:var(--text-muted);font-size:13.5px;font-weight:600;padding:6px 4px;
    transition:color .18s;
  }
  .like-btn svg{transition:transform .18s ease;}
  .like-btn.liked{color:var(--danger);}
  .like-btn.liked svg{fill:var(--danger);stroke:var(--danger);}
  .like-btn.pop svg{animation:likePop .38s ease;}
  @keyframes likePop{0%{transform:scale(1);}35%{transform:scale(1.45);}60%{transform:scale(.92);}100%{transform:scale(1);}}

  .subscribe-btn{
    background:var(--accent);color:#151107;border:none;font-weight:700;
    font-size:13px;padding:9px 18px;border-radius:999px;
    transition:background .22s, color .22s, transform .12s;
    white-space:nowrap;
  }
  .subscribe-btn:active{transform:scale(.95);}
  .subscribe-btn.subbed{background:var(--surface-3);color:var(--text);}
  .subscribe-btn.small{padding:6px 13px;font-size:12px;}

  .float-heart{
    position:fixed;pointer-events:none;z-index:999;font-size:22px;
    animation:floatUp .9s ease forwards;
  }
  @keyframes floatUp{
    0%{opacity:1;transform:translate(-50%,-50%) scale(.5) rotate(0deg);}
    30%{transform:translate(-50%,-140%) scale(1.3) rotate(-8deg);}
    100%{opacity:0;transform:translate(-50%,-260%) scale(1.1) rotate(10deg);}
  }

  /* ---------- watch page ---------- */
  .watch-wrap{max-width:900px;}
  .player{
    width:100%;aspect-ratio:16/9;background:#000;border-radius:var(--radius);
    overflow:hidden;border:1px solid var(--border);
  }
  .player video{width:100%;height:100%;display:block;}
  .watch-title{font-size:20px;font-weight:700;margin:18px 0 4px;line-height:1.35;}
  .watch-stats{font-size:13px;color:var(--text-muted);}
  .watch-row{display:flex;align-items:center;justify-content:space-between;
    margin:14px 0 18px;padding-bottom:18px;border-bottom:1px solid var(--border);flex-wrap:wrap;gap:14px;}
  .watch-channel{display:flex;align-items:center;gap:12px;}
  .watch-channel img{width:46px;height:46px;}
  .watch-channel .wc-name{font-size:14.5px;font-weight:700;}
  .watch-channel .wc-subs{font-size:12px;color:var(--text-muted);}
  .watch-actions{display:flex;align-items:center;gap:10px;}
  .pill-btn{
    display:flex;align-items:center;gap:7px;background:var(--surface);
    border:1px solid var(--border);border-radius:999px;padding:9px 15px;
    font-size:13px;font-weight:600;color:var(--text);transition:background .16s;
  }
  .pill-btn:hover{background:var(--surface-2);}
  .watch-desc{background:var(--surface);border-radius:12px;padding:14px 16px;
    font-size:13.5px;line-height:1.6;color:#dad8d0;white-space:pre-wrap;}

  /* ---------- reels page ---------- */
  .reels-page{
    height:calc(100vh - 65px);display:flex;justify-content:center;
    scroll-snap-type:y mandatory;overflow-y:scroll;scrollbar-width:none;
    margin:-22px -26px -80px;
  }
  .reels-page::-webkit-scrollbar{display:none;}
  .reel-item{
    scroll-snap-align:start;height:calc(100vh - 65px);flex-shrink:0;
    display:flex;align-items:center;justify-content:center;position:relative;
    width:100%;
  }
  .reel-stage{
    position:relative;height:92%;aspect-ratio:9/16;max-width:100%;
    border-radius:20px;overflow:hidden;background:#000;
    border:1px solid var(--border);
  }
  .reel-stage video{width:100%;height:100%;object-fit:cover;display:block;cursor:pointer;}
  .reel-gradient{
    position:absolute;inset:0;pointer-events:none;
    background:linear-gradient(180deg,rgba(0,0,0,.35) 0%,rgba(0,0,0,0) 22%,rgba(0,0,0,0) 62%,rgba(0,0,0,.8) 100%);
  }
  .reel-info{position:absolute;left:16px;right:76px;bottom:18px;color:#fff;}
  .reel-info .ri-name{font-size:14px;font-weight:700;margin-bottom:4px;}
  .reel-info .ri-title{font-size:13px;line-height:1.4;color:#f0efe9;}
  .reel-rail{
    position:absolute;right:12px;bottom:20px;display:flex;flex-direction:column;
    align-items:center;gap:20px;color:#fff;
  }
  .reel-rail .ra-item{display:flex;flex-direction:column;align-items:center;gap:4px;}
  .reel-rail button{
    background:rgba(20,20,24,.55);border:none;color:#fff;width:46px;height:46px;
    border-radius:50%;display:flex;align-items:center;justify-content:center;
    backdrop-filter:blur(4px);transition:transform .15s, background .2s;
  }
  .reel-rail button:active{transform:scale(.88);}
  .reel-rail button.liked{background:rgba(225,84,58,.85);}
  .reel-rail button.liked svg{fill:#fff;stroke:#fff;}
  .reel-rail button.pop{animation:likePop .38s ease;}
  .reel-rail .ra-count{font-size:11.5px;font-weight:600;}
  .reel-rail img.avatar{width:44px;height:44px;border:2px solid #fff;}
  .reel-mini-sub{
    width:20px;height:20px;border-radius:50%;background:var(--accent);
    display:flex;align-items:center;justify-content:center;margin-top:-14px;
    border:2px solid #101013;color:#151107;transition:background .2s;
  }
  .reel-mini-sub.subbed{background:var(--surface-3);color:var(--accent);}
  .reels-empty-nav{position:absolute;top:14px;left:50%;transform:translateX(-50%);
    color:#fff;font-size:12px;background:rgba(0,0,0,.4);padding:5px 12px;border-radius:999px;}

  /* ---------- profile page ---------- */
  .profile-header{display:flex;align-items:center;gap:22px;padding:8px 0 26px;
    border-bottom:1px solid var(--border);margin-bottom:22px;flex-wrap:wrap;}
  .profile-header img.avatar{width:96px;height:96px;border-width:3px;}
  .profile-name{font-size:22px;font-weight:800;margin:0 0 4px;}
  .profile-handle{font-size:13.5px;color:var(--text-muted);margin-bottom:8px;}
  .profile-bio{font-size:13.5px;color:#d8d6cf;max-width:480px;line-height:1.5;}
  .profile-subs{font-size:12.5px;color:var(--text-muted);margin-top:6px;}
  .profile-actions{margin-left:auto;display:flex;gap:10px;align-self:flex-start;}
  .tab-row{display:flex;gap:6px;margin-bottom:20px;}
  .tab-btn{
    background:none;border:1px solid var(--border);color:var(--text-muted);
    padding:8px 16px;border-radius:999px;font-size:13px;font-weight:600;
    transition:all .18s;
  }
  .tab-btn.active{background:var(--accent);border-color:var(--accent);color:#151107;}
  .empty-state{padding:60px 20px;text-align:center;color:var(--text-muted);font-size:13.5px;}
  .empty-state .es-icon{font-size:30px;margin-bottom:10px;}

  /* ---------- modal ---------- */
  .modal-backdrop{
    position:fixed;inset:0;background:rgba(6,6,8,.66);backdrop-filter:blur(3px);
    display:flex;align-items:flex-end;justify-content:center;z-index:100;
    animation:backdropIn .2s ease both;
  }
  @media(min-width:640px){.modal-backdrop{align-items:center;}}
  @keyframes backdropIn{from{opacity:0;}to{opacity:1;}}
  .modal{
    background:var(--surface-2);border:1px solid var(--border);
    width:100%;max-width:480px;border-radius:20px 20px 0 0;
    padding:22px 22px 26px;max-height:88vh;overflow-y:auto;
    animation:modalUp .28s cubic-bezier(.22,1,.36,1) both;
  }
  @media(min-width:640px){.modal{border-radius:20px;}}
  @keyframes modalUp{from{opacity:0;transform:translateY(40px);}to{opacity:1;transform:translateY(0);}}
  .modal h3{margin:0 0 18px;font-size:17px;font-weight:700;}
  .field{margin-bottom:14px;}
  .field label{display:block;font-size:12.5px;font-weight:600;color:var(--text-muted);margin-bottom:6px;}
  .field input[type=text],.field textarea{
    width:100%;background:var(--surface);border:1px solid var(--border);
    border-radius:10px;padding:11px 13px;color:var(--text);font-size:14px;font-family:inherit;
    outline:none;transition:border-color .16s;resize:vertical;
  }
  .field input[type=text]:focus,.field textarea:focus{border-color:var(--accent-dim);}
  .type-toggle{display:flex;gap:8px;margin-bottom:16px;}
  .type-toggle button{
    flex:1;padding:10px;border-radius:10px;border:1px solid var(--border);
    background:var(--surface);color:var(--text-muted);font-weight:600;font-size:13px;
    transition:all .16s;
  }
  .type-toggle button.active{background:var(--accent);border-color:var(--accent);color:#151107;}
  .file-drop{
    border:1.5px dashed var(--border);border-radius:12px;padding:16px;
    display:flex;align-items:center;gap:12px;cursor:pointer;transition:border-color .16s;
    font-size:13px;color:var(--text-muted);
  }
  .file-drop:hover{border-color:var(--accent-dim);}
  .file-drop img,.file-drop video{width:52px;height:52px;border-radius:8px;object-fit:cover;}
  .modal-actions{display:flex;gap:10px;margin-top:18px;}
  .btn-full{flex:1;text-align:center;padding:12px;border-radius:12px;font-weight:700;font-size:14px;border:none;}
  .btn-primary{background:var(--accent);color:#151107;}
  .btn-primary:active{transform:scale(.98);}
  .btn-secondary{background:var(--surface);color:var(--text);border:1px solid var(--border);}
  .avatar-pick{display:flex;align-items:center;gap:16px;margin-bottom:16px;}
  .avatar-pick img{width:64px;height:64px;border-radius:50%;object-fit:cover;border:2px solid var(--border);}
  .avatar-pick label{
    background:var(--surface);border:1px solid var(--border);padding:8px 14px;
    border-radius:999px;font-size:12.5px;font-weight:600;cursor:pointer;
  }

  /* ---------- toast ---------- */
  .toast{
    position:fixed;bottom:24px;left:50%;transform:translateX(-50%);
    background:var(--surface-3);border:1px solid var(--border);color:var(--text);
    padding:11px 20px;border-radius:999px;font-size:13px;font-weight:600;z-index:200;
    animation:toastIn .25s ease both, toastOut .25s ease 1.9s both;
  }
  @keyframes toastIn{from{opacity:0;transform:translate(-50%,10px);}to{opacity:1;transform:translate(-50%,0);}}
  @keyframes toastOut{to{opacity:0;transform:translate(-50%,10px);}}

  @media(max-width:860px){
    .sidebar{display:none;}
    .main{padding:16px 14px 70px;}
    .search{display:none;}
    .topbar{padding:12px 14px;}
  }
  @media(prefers-reduced-motion:reduce){
    *{animation-duration:.001s !important;transition-duration:.001s !important;}
  }
</style>
</head>
<body>

<div class="app">
  <header class="topbar">
    <div class="brand" onclick="navigate({name:'home'})">
      <span class="dot"></span>Flicker
    </div>
    <div class="search">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="7"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      <input id="searchInput" type="text" placeholder="Search videos, reels, posts" oninput="onSearch(this.value)">
    </div>
    <div class="top-actions">
      <button class="icon-btn" title="Create" onclick="toggleCreateMenu(event)">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
      </button>
      <img class="avatar" id="topAvatar" src="" onclick="navigate({name:'profile', userId:'me'})" title="Your channel">
      <div id="createMenuRoot"></div>
    </div>
  </header>

  <div class="body-row">
    <nav class="sidebar" id="sidebar"></nav>
    <main class="main view-enter" id="main"></main>
  </div>
</div>

<div id="modalRoot"></div>
<div id="toastRoot"></div>

<script>
/* ============ ICONS ============ */
const ICONS = {
  home:'<svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 11l9-8 9 8"/><path d="M5 10v10h14V10"/></svg>',
  reels:'<svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="4" y="2" width="16" height="20" rx="3"/><path d="M8 7l2.5 2-2.5 2M13 16h4"/></svg>',
  profile:'<svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 3.5-6 8-6s8 2 8 6"/></svg>',
  heart:'<svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 21s-7.5-4.6-10-9.3C0.3 8 2 4.5 5.6 4.1c2-.2 3.7 1 4.4 2.7.7-1.7 2.4-2.9 4.4-2.7C18 4.5 19.7 8 22 11.7 19.5 16.4 12 21 12 21z"/></svg>',
  eye:'<svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M1 12s4-7 11-7 11 7 11 7-4 7-11 7-11-7-11-7z"/><circle cx="12" cy="12" r="3"/></svg>',
  comment:'<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 11.5a8.4 8.4 0 01-.9 3.8 8.5 8.5 0 01-7.6 4.7 8.4 8.4 0 01-3.8-.9L3 21l1.9-5.7a8.4 8.4 0 01-.9-3.8 8.5 8.5 0 014.7-7.6 8.4 8.4 0 013.8-.9h.5a8.48 8.48 0 018 8v.5z"/></svg>',
  share:'<svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="18" cy="5" r="3"/><circle cx="6" cy="12" r="3"/><circle cx="18" cy="19" r="3"/><line x1="8.6" y1="13.5" x2="15.4" y2="17.5"/><line x1="15.4" y1="6.5" x2="8.6" y2="10.5"/></svg>',
  plus:'<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>',
  check:'<svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg>',
  mute:'<svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"/><line x1="23" y1="9" x2="17" y2="15"/><line x1="17" y1="9" x2="23" y2="15"/></svg>',
  sound:'<svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"/><path d="M15.5 8.5a5 5 0 010 7"/><path d="M18.5 5.5a9 9 0 010 13"/></svg>',
  film:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="3" width="20" height="18" rx="2"/><path d="M7 3v18M17 3v18M2 8h5M2 16h5M17 8h5M17 16h5"/></svg>',
  post:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 20h9"/><path d="M16.5 3.5a2.1 2.1 0 013 3L7 19l-4 1 1-4z"/></svg>',
  clip:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="4" y="2" width="16" height="20" rx="3"/><path d="M9 8l5 3-5 3z"/></svg>',
  camera:'<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M23 19a2 2 0 01-2 2H3a2 2 0 01-2-2V8a2 2 0 012-2h4l2-3h6l2 3h4a2 2 0 012 2z"/><circle cx="12" cy="13" r="4"/></svg>',
};

/* ============ SAMPLE MEDIA ============ */
const SAMPLE_VIDEOS = [
  'https://storage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/ForBiggerBlazes.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/ForBiggerEscapes.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/ForBiggerFun.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/ForBiggerJoyrides.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/ForBiggerMeltdowns.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/Sintel.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/TearsOfSteel.mp4',
  'https://storage.googleapis.com/gtv-videos-bucket/sample/WeAreGoingOnBullrun.mp4',
];
function randomSample(){ return SAMPLE_VIDEOS[Math.floor(Math.random()*SAMPLE_VIDEOS.length)]; }
function thumb(seed){ return `https://picsum.photos/seed/${seed}/600/338`; }
function avatarUrl(n){ return `https://i.pravatar.cc/150?img=${n}`; }

/* ============ STATE ============ */
const state = {
  currentView:{name:'home'},
  query:'',
  reelsMuted:true,
  viewed:new Set(),
  users:[
    {id:'u1', name:'Maya Ortiz', handle:'@mayaortiz', bio:'Documenting small towns, one frame at a time.', avatar:avatarUrl(32), subs:128400, subscribed:false},
    {id:'u2', name:'Denzel Cole', handle:'@denzelcole', bio:'Home cook turned recipe archiver.', avatar:avatarUrl(14), subs:54200, subscribed:false},
    {id:'u3', name:'Priya Nandakumar', handle:'@priyanandakumar', bio:'Product teardowns and tech explainers, no hype.', avatar:avatarUrl(47), subs:892000, subscribed:true},
    {id:'u4', name:'The Loose Threads', handle:'@loosethreads', bio:'Three friends, one mic, zero filter.', avatar:avatarUrl(60), subs:231000, subscribed:false},
    {id:'me', name:'You', handle:'@you', bio:'Welcome to your channel — upload something to get started.', avatar:avatarUrl(5), subs:0, subscribed:false, isMe:true},
  ],
  videos:[
    {id:'v1', type:'video', ownerId:'u1', title:'A Diner That Never Closed', desc:'Three days at a 24-hour diner off Route 9, talking to whoever sat down.', duration:'12:04', thumb:thumb('diner'), src:SAMPLE_VIDEOS[0], views:84210, likes:5210, liked:false, time:'3 days ago'},
    {id:'v2', type:'video', ownerId:'u3', title:'I Took Apart the New Fold Phone', desc:'Full teardown, hinge mechanism, and whether the durability claims hold up.', duration:'18:22', thumb:thumb('foldphone'), src:SAMPLE_VIDEOS[1], views:412300, likes:30210, liked:true, time:'1 week ago'},
    {id:'v3', type:'video', ownerId:'u2', title:'Braising Short Ribs Until They Fall Apart', desc:'Low and slow for six hours. Recipe and timings in the description.', duration:'9:47', thumb:thumb('shortribs'), src:SAMPLE_VIDEOS[8], views:61240, likes:4310, liked:false, time:'5 days ago'},
    {id:'v4', type:'video', ownerId:'u4', title:'We Debated Whether Cereal Is Soup', desc:'It got heated. Timestamps in the description for each argument.', duration:'34:10', thumb:thumb('cereal'), src:SAMPLE_VIDEOS[7], views:198340, likes:15200, liked:false, time:'2 weeks ago'},
    {id:'v5', type:'video', ownerId:'u1', title:'The Last Payphone in Millbrook', desc:'It still works. Nobody knows who pays the bill.', duration:'7:58', thumb:thumb('payphone'), src:SAMPLE_VIDEOS[9], views:29840, likes:2210, liked:false, time:'1 month ago'},
    {id:'v6', type:'video', ownerId:'u3', title:'Is the Budget Laptop Actually Worth It', desc:'Benchmarks, thermals, and a week of real use.', duration:'15:03', thumb:thumb('laptop'), src:SAMPLE_VIDEOS[2], views:154200, likes:12040, liked:false, time:'4 days ago'},
  ],
  reels:[
    {id:'r1', type:'reel', ownerId:'u3', title:'This phone hinge sound though', src:SAMPLE_VIDEOS[2], views:512000, likes:88400, liked:false},
    {id:'r2', type:'reel', ownerId:'u2', title:'45 second garlic confit', src:SAMPLE_VIDEOS[4], views:302000, likes:61200, liked:false},
    {id:'r3', type:'reel', ownerId:'u4', title:'POV: the aux cord debate begins', src:SAMPLE_VIDEOS[5], views:190000, likes:40210, liked:true},
    {id:'r4', type:'reel', ownerId:'u1', title:'Foggy morning, empty diner', src:SAMPLE_VIDEOS[6], views:88000, likes:15230, liked:false},
    {id:'r5', type:'reel', ownerId:'u3', title:'Unboxing but it is upside down', src:SAMPLE_VIDEOS[3], views:220000, likes:51230, liked:false},
  ],
  posts:[
    {id:'p1', ownerId:'u2', text:'Tested 6 supermarket olive oils side by side. Results were... humbling.', image:thumb('oliveoil'), likes:812, liked:false, time:'2 days ago'},
    {id:'p2', ownerId:'u4', text:'New episode drops Friday. Topic: is a hot dog a taco. Send your arguments now.', image:null, likes:340, liked:false, time:'6 hours ago'},
    {id:'p3', ownerId:'u1', text:'Back on the road next week, small towns in the Midwest. Send suggestions.', image:null, likes:501, liked:true, time:'1 day ago'},
  ],
};

/* ============ HELPERS ============ */
function getUser(id){ return state.users.find(u=>u.id===id); }
function formatCount(n){
  if(n>=1000000) return (n/1000000).toFixed(n%1000000<100000?0:1)+'M';
  if(n>=1000) return (n/1000).toFixed(n%1000<100?0:1)+'K';
  return String(n);
}
function animateCount(elNode, from, to){
  const dur=420, start=performance.now();
  function step(now){
    const p=Math.min(1,(now-start)/dur);
    const eased=1-Math.pow(1-p,3);
    const val=Math.round(from+(to-from)*eased);
    elNode.textContent=formatCount(val);
    if(p<1) requestAnimationFrame(step);
  }
  requestAnimationFrame(step);
}
function findItem(id){
  return state.videos.find(v=>v.id===id) || state.reels.find(v=>v.id===id) || state.posts.find(p=>p.id===id);
}
function showToast(msg){
  const root=document.getElementById('toastRoot');
  const t=document.createElement('div');
  t.className='toast';
  t.textContent=msg;
  root.appendChild(t);
  setTimeout(()=>t.remove(),2200);
}
function closeCreateMenu(){
  document.getElementById('createMenuRoot').innerHTML='';
  document.removeEventListener('click', outsideCreateMenu);
}
function outsideCreateMenu(e){
  const root=document.getElementById('createMenuRoot');
  if(!root.contains(e.target) && !e.target.closest('.icon-btn')) closeCreateMenu();
}

/* ============ NAVIGATION ============ */
function navigate(view){
  closeCreateMenu();
  state.currentView=view;
  renderSidebar();
  renderMain();
  window.scrollTo({top:0,behavior:'smooth'});
}
function renderSidebar(){
  const v=state.currentView.name;
  document.getElementById('sidebar').innerHTML = `
    <div class="nav-item ${v==='home'?'active':''}" onclick="navigate({name:'home'})">${ICONS.home}<span>Home</span></div>
    <div class="nav-item ${v==='reels'?'active':''}" onclick="navigate({name:'reels'})">${ICONS.reels}<span>Reels</span></div>
    <div class="nav-item ${v==='profile' && state.currentView.userId==='me'?'active':''}" onclick="navigate({name:'profile',userId:'me'})">${ICONS.profile}<span>Your channel</span></div>
    <div class="sep"></div>
    <div class="sidebar-note">CHANNELS YOU FOLLOW</div>
    ${state.users.filter(u=>u.subscribed).map(u=>`
      <div class="nav-item" onclick="navigate({name:'profile',userId:'${u.id}'})">
        <img class="avatar" style="width:26px;height:26px;border:none" src="${u.avatar}"><span>${u.name}</span>
      </div>`).join('')}
  `;
}

function renderMain(){
  const main=document.getElementById('main');
  main.classList.remove('view-enter');
  void main.offsetWidth;
  const v=state.currentView;
  if(v.name==='home') main.innerHTML=renderHome();
  else if(v.name==='reels') main.innerHTML=renderReelsPage();
  else if(v.name==='watch') main.innerHTML=renderWatch(v.id);
  else if(v.name==='profile') main.innerHTML=renderProfile(v.userId);
  main.classList.add('view-enter');

  if(v.name==='watch') afterWatchMount(v.id);
  if(v.name==='reels') afterReelsMount();
}

/* ============ HOME ============ */
function renderHome(){
  const q=state.query.toLowerCase();
  const vids=state.videos.filter(v=>!q || v.title.toLowerCase().includes(q));
  const reels=state.reels.filter(r=>!q || r.title.toLowerCase().includes(q));
  const posts=state.posts.filter(p=>!q || p.text.toLowerCase().includes(q));

  const reelsHtml = reels.length ? `
    <div class="section-head"><h2>Reels</h2><span class="see-all" style="cursor:pointer" onclick="navigate({name:'reels'})">Open Reels →</span></div>
    <div class="reels-strip">
      ${reels.map(r=>{
        const u=getUser(r.ownerId);
        return `<div class="reel-card" onclick="navigate({name:'reels'})">
          <img src="${thumb(r.id)}" alt="">
          <div class="reel-badge">${ICONS.clip}</div>
          <div class="rc-overlay">
            <div class="rc-title">${r.title}</div>
            <div class="rc-views">${ICONS.eye}${formatCount(r.views)}</div>
          </div>
        </div>`;
      }).join('')}
    </div>` : '';

  const feedItems = [
    ...vids.map(v=>({...v,_kind:'video'})),
    ...posts.map(p=>({...p,_kind:'post'})),
  ];

  const feedHtml = feedItems.length ? `
    <div class="section-head"><h2>For you</h2></div>
    <div class="feed">
      ${feedItems.map(item=> item._kind==='video' ? videoCardHtml(item) : postCardHtml(item)).join('')}
    </div>` : `<div class="empty-state"><div class="es-icon">🔍</div>No results for "${state.query}"</div>`;

  return reelsHtml + feedHtml;
}

function videoCardHtml(v){
  const u=getUser(v.ownerId);
  return `
  <div class="video-card" onclick="navigate({name:'watch', id:'${v.id}'})">
    <div class="thumb-wrap">
      <img src="${v.thumb}" alt="">
      <div class="duration-badge">${v.duration}</div>
    </div>
    <div class="video-meta">
      <img class="avatar" src="${u.avatar}">
      <div>
        <p class="vm-title">${v.title}</p>
        <div class="vm-sub"><span>${u.name}</span><span>${formatCount(v.views)} views · ${v.time}</span></div>
      </div>
    </div>
  </div>`;
}

function postCardHtml(p){
  const u=getUser(p.ownerId);
  return `
  <div class="post-card">
    <div class="post-head" style="cursor:pointer" onclick="navigate({name:'profile',userId:'${u.id}'})">
      <img class="avatar" style="width:38px;height:38px" src="${u.avatar}">
      <div><div class="ph-name">${u.name}</div><div class="ph-time">${p.time}</div></div>
    </div>
    <p class="post-text">${p.text}</p>
    ${p.image?`<img class="post-image" src="${p.image}">`:''}
    <div class="post-actions">
      ${likeButtonHtml(p.id,'posts')}
      <button class="like-btn" onclick="showToast('Link copied')">${ICONS.share} Share</button>
    </div>
  </div>`;
}

function likeButtonHtml(id, collection){
  const item = findItem(id);
  return `<button class="like-btn ${item.liked?'liked':''}" data-like-id="${id}" onclick="onLikeClick(event,'${id}')">
    ${ICONS.heart}<span data-count-for="${id}">${formatCount(item.likes)}</span>
  </button>`;
}

function subscribeButtonHtml(userId, small){
  const u=getUser(userId);
  if(u.isMe) return '';
  return `<button class="subscribe-btn ${small?'small':''} ${u.subscribed?'subbed':''}" data-sub-id="${userId}" onclick="onSubscribeClick(event,'${userId}')">
    ${u.subscribed?'Subscribed':'Subscribe'}
  </button>`;
}

/* ============ WATCH ============ */
function renderWatch(id){
  const v = state.videos.find(x=>x.id===id) || state.reels.find(x=>x.id===id);
  const u = getUser(v.ownerId);
  const related = state.videos.filter(x=>x.id!==id).slice(0,4);
  return `
  <div class="watch-wrap">
    <div class="player"><video id="watchVideo" src="${v.src}" controls autoplay></video></div>
    <h1 class="watch-title">${v.title}</h1>
    <div class="watch-stats"><span data-count-for="views-${v.id}">${formatCount(v.views)}</span> views · ${v.time||'today'}</div>
    <div class="watch-row">
      <div class="watch-channel" style="cursor:pointer" onclick="navigate({name:'profile',userId:'${u.id}'})">
        <img class="avatar" src="${u.avatar}">
        <div><div class="wc-name">${u.name}</div><div class="wc-subs" data-subs-for="${u.id}">${formatCount(u.subs)} subscribers</div></div>
      </div>
      <div class="watch-actions">
        ${subscribeButtonHtml(u.id)}
        ${likeButtonHtml(v.id)}
        <button class="pill-btn" onclick="showToast('Link copied')">${ICONS.share} Share</button>
      </div>
    </div>
    <div class="watch-desc">${v.desc||'No description provided.'}</div>
  </div>
  <div class="section-head"><h2>More like this</h2></div>
  <div class="feed">${related.map(videoCardHtml).join('')}</div>
  `;
}
function afterWatchMount(id){
  const v = state.videos.find(x=>x.id===id) || state.reels.find(x=>x.id===id);
  if(!state.viewed.has(id)){
    state.viewed.add(id);
    const from=v.views;
    v.views += Math.floor(Math.random()*40)+8;
    const node=document.querySelector(`[data-count-for="views-${id}"]`);
    if(node) animateCount(node, from, v.views);
  }
}

/* ============ REELS ============ */
function renderReelsPage(){
  return `<div class="reels-page" id="reelsScroller">
    ${state.reels.map(reelItemHtml).join('')}
  </div>`;
}
function reelItemHtml(r){
  const u=getUser(r.ownerId);
  return `
  <div class="reel-item">
    <div class="reel-stage">
      <video data-reel-id="${r.id}" src="${r.src}" loop playsinline muted onclick="toggleReelPlay(this)"></video>
      <div class="reel-gradient"></div>
      <div class="reel-info">
        <div class="ri-name">${u.name} <span style="color:#c9c8c2;font-weight:400">${u.handle}</span></div>
        <div class="ri-title">${r.title}</div>
      </div>
      <div class="reel-rail">
        <div class="ra-item">
          <img class="avatar" src="${u.avatar}" onclick="navigate({name:'profile',userId:'${u.id}'})">
          ${u.isMe?'':`<div class="reel-mini-sub ${u.subscribed?'subbed':''}" data-sub-id="${u.id}" onclick="onSubscribeClick(event,'${u.id}')">${u.subscribed?ICONS.check:ICONS.plus}</div>`}
        </div>
        <div class="ra-item">
          <button class="${r.liked?'liked':''}" data-like-id="${r.id}" onclick="onLikeClick(event,'${r.id}')">${ICONS.heart}</button>
          <span class="ra-count" data-count-for="${r.id}">${formatCount(r.likes)}</span>
        </div>
        <div class="ra-item">
          <button onclick="showToast('Comments coming soon')">${ICONS.comment}</button>
          <span class="ra-count">Chat</span>
        </div>
        <div class="ra-item">
          <button onclick="showToast('Link copied')">${ICONS.share}</button>
          <span class="ra-count">Share</span>
        </div>
        <div class="ra-item">
          <button onclick="toggleReelsMute()" id="muteBtn">${state.reelsMuted?ICONS.mute:ICONS.sound}</button>
        </div>
      </div>
    </div>
  </div>`;
}
let reelObserver=null;
function afterReelsMount(){
  const scroller=document.getElementById('reelsScroller');
  const videos=[...scroller.querySelectorAll('video')];
  if(reelObserver) reelObserver.disconnect();
  reelObserver = new IntersectionObserver((entries)=>{
    entries.forEach(entry=>{
      const vid=entry.target;
      vid.muted=state.reelsMuted;
      if(entry.isIntersecting && entry.intersectionRatio>0.6){
        vid.play().catch(()=>{});
        const id=vid.dataset.reelId;
        if(!state.viewed.has(id)){
          state.viewed.add(id);
          const r=state.reels.find(x=>x.id===id);
          const from=r.views;
          r.views += Math.floor(Math.random()*30)+5;
        }
      } else {
        vid.pause();
      }
    });
  }, {threshold:[0,0.6,1], root:scroller});
  videos.forEach(v=>reelObserver.observe(v));
}
function toggleReelPlay(vid){ vid.paused ? vid.play() : vid.pause(); }
function toggleReelsMute(){
  state.reelsMuted=!state.reelsMuted;
  document.querySelectorAll('#reelsScroller video').forEach(v=>v.muted=state.reelsMuted);
  const btn=document.getElementById('muteBtn');
  if(btn) btn.innerHTML = state.reelsMuted?ICONS.mute:ICONS.sound;
}

/* ============ PROFILE ============ */
function renderProfile(userId){
  const u=getUser(userId);
  const tab = state.currentView.tab || 'videos';
  const myVideos = state.videos.filter(v=>v.ownerId===userId);
  const myReels = state.reels.filter(r=>r.ownerId===userId);
  const myPosts = state.posts.filter(p=>p.ownerId===userId);

  let body='';
  if(tab==='videos'){
    body = myVideos.length ? `<div class="feed">${myVideos.map(videoCardHtml).join('')}</div>`
      : emptyState('🎬','No videos yet');
  } else if(tab==='reels'){
    body = myReels.length ? `<div class="reels-strip" style="flex-wrap:wrap">${myReels.map(r=>{
        return `<div class="reel-card" onclick="navigate({name:'reels'})">
          <img src="${thumb(r.id)}" alt="">
          <div class="rc-overlay"><div class="rc-title">${r.title}</div><div class="rc-views">${ICONS.eye}${formatCount(r.views)}</div></div>
        </div>`;
      }).join('')}</div>`
      : emptyState('🎞️','No reels yet');
  } else {
    body = myPosts.length ? `<div class="feed">${myPosts.map(postCardHtml).join('')}</div>`
      : emptyState('📝','No posts yet');
  }

  return `
  <div class="profile-header">
    <img class="avatar" src="${u.avatar}">
    <div>
      <h1 class="profile-name">${u.name}</h1>
      <div class="profile-handle">${u.handle}</div>
      <div class="profile-bio">${u.bio}</div>
      <div class="profile-subs" data-subs-for="${u.id}">${formatCount(u.subs)} subscribers · ${myVideos.length+myReels.length} videos</div>
    </div>
    <div class="profile-actions">
      ${u.isMe ? `<button class="pill-btn" onclick="openEditProfileModal()">Edit profile</button>` : subscribeButtonHtml(u.id)}
    </div>
  </div>
  <div class="tab-row">
    <button class="tab-btn ${tab==='videos'?'active':''}" onclick="setProfileTab('${userId}','videos')">Videos</button>
    <button class="tab-btn ${tab==='reels'?'active':''}" onclick="setProfileTab('${userId}','reels')">Reels</button>
    <button class="tab-btn ${tab==='posts'?'active':''}" onclick="setProfileTab('${userId}','posts')">Posts</button>
  </div>
  ${body}
  `;
}
function emptyState(icon,text){
  return `<div class="empty-state"><div class="es-icon">${icon}</div>${text}</div>`;
}
function setProfileTab(userId, tab){
  state.currentView = {name:'profile', userId, tab};
  renderMain();
}

/* ============ INTERACTIONS ============ */
function onLikeClick(evt, id){
  evt.stopPropagation();
  const item = findItem(id);
  item.liked = !item.liked;
  item.likes += item.liked ? 1 : -1;

  document.querySelectorAll(`[data-like-id="${id}"]`).forEach(btn=>{
    btn.classList.toggle('liked', item.liked);
    btn.classList.remove('pop'); void btn.offsetWidth; btn.classList.add('pop');
  });
  document.querySelectorAll(`[data-count-for="${id}"]`).forEach(node=>{
    animateCount(node, item.likes + (item.liked?-1:1), item.likes);
  });

  if(item.liked){
    const heart=document.createElement('div');
    heart.className='float-heart';
    heart.textContent='❤️';
    heart.style.left = evt.clientX+'px';
    heart.style.top = evt.clientY+'px';
    document.body.appendChild(heart);
    setTimeout(()=>heart.remove(),900);
  }
}

function onSubscribeClick(evt, userId){
  evt.stopPropagation();
  const u=getUser(userId);
  u.subscribed = !u.subscribed;
  u.subs += u.subscribed ? 1 : -1;

  document.querySelectorAll(`[data-sub-id="${userId}"]`).forEach(node=>{
    if(node.classList.contains('subscribe-btn')){
      node.classList.toggle('subbed', u.subscribed);
      node.textContent = u.subscribed ? 'Subscribed' : 'Subscribe';
    } else {
      node.classList.toggle('subbed', u.subscribed);
      node.innerHTML = u.subscribed ? ICONS.check : ICONS.plus;
    }
  });
  document.querySelectorAll(`[data-subs-for="${userId}"]`).forEach(node=>{
    const suffix = node.textContent.includes('subscribers')
      ? node.textContent.replace(/^[\d.,A-Za-z]+/, formatCount(u.subs))
      : formatCount(u.subs);
    node.textContent = suffix;
  });
  renderSidebar();
  showToast(u.subscribed ? `Subscribed to ${u.name}` : `Unsubscribed from ${u.name}`);
}

function onSearch(val){
  state.query = val;
  if(state.currentView.name!=='home') navigate({name:'home'});
  else renderMain();
}

/* ============ CREATE MENU ============ */
function toggleCreateMenu(evt){
  evt.stopPropagation();
  const root=document.getElementById('createMenuRoot');
  if(root.innerHTML){ closeCreateMenu(); return; }
  root.innerHTML = `
    <div class="create-menu">
      <button onclick="closeCreateMenu();openUploadModal('video')">${ICONS.film} Upload a video</button>
      <button onclick="closeCreateMenu();openUploadModal('reel')">${ICONS.clip} Upload a reel</button>
      <button onclick="closeCreateMenu();openPostModal()">${ICONS.post} Create a post</button>
    </div>`;
  setTimeout(()=>document.addEventListener('click', outsideCreateMenu),0);
}

/* ============ MODALS ============ */
let pendingVideoFile=null, pendingThumbFile=null, pendingPostImage=null, pendingAvatar=null;

function closeModal(){
  document.getElementById('modalRoot').innerHTML='';
  pendingVideoFile=null; pendingThumbFile=null; pendingPostImage=null; pendingAvatar=null;
}

function openUploadModal(kind){
  pendingVideoFile=null; pendingThumbFile=null;
  const root=document.getElementById('modalRoot');
  root.innerHTML = `
  <div class="modal-backdrop" onclick="if(event.target===this)closeModal()">
    <div class="modal">
      <h3>${kind==='reel'?'Upload a reel':'Upload a video'}</h3>
      <div class="type-toggle">
        <button class="${kind==='video'?'active':''}" onclick="openUploadModal('video')">${ICONS.film} Video</button>
        <button class="${kind==='reel'?'active':''}" onclick="openUploadModal('reel')">${ICONS.clip} Reel</button>
      </div>
      <div class="field">
        <label>Video file</label>
        <div class="file-drop" onclick="document.getElementById('videoFileInput').click()" id="videoDrop">
          ${ICONS.camera}<span id="videoDropLabel">Choose a file, or leave empty to use a sample clip</span>
        </div>
        <input type="file" id="videoFileInput" accept="video/*" style="display:none" onchange="onVideoFileChosen(this)">
      </div>
      <div class="field">
        <label>Title</label>
        <input type="text" id="uploadTitle" placeholder="${kind==='reel'?'Give your reel a title':'What is this video about?'}">
      </div>
      ${kind==='video' ? `<div class="field"><label>Description</label><textarea id="uploadDesc" rows="3" placeholder="Add details for viewers"></textarea></div>` : ''}
      <div class="modal-actions">
        <button class="btn-full btn-secondary" onclick="closeModal()">Cancel</button>
        <button class="btn-full btn-primary" onclick="submitUpload('${kind}')">Publish</button>
      </div>
    </div>
  </div>`;
}
function onVideoFileChosen(input){
  const file=input.files[0];
  if(!file) return;
  pendingVideoFile=URL.createObjectURL(file);
  document.getElementById('videoDropLabel').textContent = file.name;
}
function submitUpload(kind){
  const title=document.getElementById('uploadTitle').value.trim() || (kind==='reel'?'Untitled reel':'Untitled video');
  const descEl=document.getElementById('uploadDesc');
  const desc = descEl ? descEl.value.trim() : '';
  const id = (kind==='reel'?'r':'v') + 'me' + Date.now();
  const src = pendingVideoFile || randomSample();

  if(kind==='reel'){
    state.reels.unshift({id, type:'reel', ownerId:'me', title, src, views:0, likes:0, liked:false});
    closeModal();
    showToast('Reel published');
    navigate({name:'reels'});
  } else {
    state.videos.unshift({id, type:'video', ownerId:'me', title, desc, duration:'0:00', thumb:thumb(id), src, views:0, likes:0, liked:false, time:'just now'});
    closeModal();
    showToast('Video published');
    navigate({name:'watch', id});
  }
}

function openPostModal(){
  pendingPostImage=null;
  document.getElementById('modalRoot').innerHTML = `
  <div class="modal-backdrop" onclick="if(event.target===this)closeModal()">
    <div class="modal">
      <h3>Create a post</h3>
      <div class="field">
        <label>What's on your mind?</label>
        <textarea id="postText" rows="4" placeholder="Share an update with your subscribers"></textarea>
      </div>
      <div class="field">
        <label>Image (optional)</label>
        <div class="file-drop" onclick="document.getElementById('postImgInput').click()" id="postImgDrop">
          ${ICONS.camera}<span id="postImgLabel">Add a photo to your post</span>
        </div>
        <input type="file" id="postImgInput" accept="image/*" style="display:none" onchange="onPostImageChosen(this)">
      </div>
      <div class="modal-actions">
        <button class="btn-full btn-secondary" onclick="closeModal()">Cancel</button>
        <button class="btn-full btn-primary" onclick="submitPost()">Post</button>
      </div>
    </div>
  </div>`;
}
function onPostImageChosen(input){
  const file=input.files[0];
  if(!file) return;
  const reader=new FileReader();
  reader.onload=()=>{
    pendingPostImage=reader.result;
    document.getElementById('postImgDrop').innerHTML = `<img src="${reader.result}"><span>${file.name}</span>`;
  };
  reader.readAsDataURL(file);
}
function submitPost(){
  const text=document.getElementById('postText').value.trim();
  if(!text){ showToast('Write something first'); return; }
  const id='p_me_'+Date.now();
  state.posts.unshift({id, ownerId:'me', text, image:pendingPostImage, likes:0, liked:false, time:'just now'});
  closeModal();
  showToast('Post published');
  navigate({name:'home'});
}

function openEditProfileModal(){
  const u=getUser('me');
  pendingAvatar=null;
  document.getElementById('modalRoot').innerHTML = `
  <div class="modal-backdrop" onclick="if(event.target===this)closeModal()">
    <div class="modal">
      <h3>Edit your channel</h3>
      <div class="avatar-pick">
        <img id="avatarPreview" src="${u.avatar}">
        <label>Change photo<input type="file" accept="image/*" style="display:none" onchange="onAvatarChosen(this)"></label>
      </div>
      <div class="field">
        <label>Name</label>
        <input type="text" id="editName" value="${u.name}">
      </div>
      <div class="field">
        <label>Description</label>
        <textarea id="editBio" rows="3">${u.bio}</textarea>
      </div>
      <div class="modal-actions">
        <button class="btn-full btn-secondary" onclick="closeModal()">Cancel</button>
        <button class="btn-full btn-primary" onclick="submitProfileEdit()">Save changes</button>
      </div>
    </div>
  </div>`;
}
function onAvatarChosen(input){
  const file=input.files[0];
  if(!file) return;
  const reader=new FileReader();
  reader.onload=()=>{
    pendingAvatar=reader.result;
    document.getElementById('avatarPreview').src=reader.result;
  };
  reader.readAsDataURL(file);
}
function submitProfileEdit(){
  const u=getUser('me');
  u.name=document.getElementById('editName').value.trim()||u.name;
  u.bio=document.getElementById('editBio').value.trim()||u.bio;
  if(pendingAvatar) u.avatar=pendingAvatar;
  closeModal();
  document.getElementById('topAvatar').src=u.avatar;
  showToast('Profile updated');
  navigate({name:'profile', userId:'me'});
}

/* ============ INIT ============ */
function init(){
  document.getElementById('topAvatar').src = getUser('me').avatar;
  renderSidebar();
  renderMain();
}
init();
</script>
</body>
</html>
