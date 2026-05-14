<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="theme-color" content="#020408">
<title>GrowSage — Digital Agency That Grows Brands</title>
<meta name="description" content="digital agency offering social media marketing, website development, 360° virtual tours, UI/UX design, and video editing.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Plus+Jakarta+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
/* ===================== RESET & BASE ===================== */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; -webkit-tap-highlight-color: transparent; }
body {
  font-family: 'Plus Jakarta Sans', sans-serif;
  background: #020408;
  color: #eef2ff;
  line-height: 1.6;
  font-weight: 400;
  overflow-x: hidden;
  font-size: 15px;
}
img { max-width: 100%; display: block; }
a { text-decoration: none; color: inherit; }
ul { list-style: none; }
::selection { background: #2563ff; color: #fff; }

/* ===================== CSS VARS ===================== */
:root {
  --bg: #020408;
  --bg2: #080d14;
  --bg3: #0d1520;
  --blue: #2563ff;
  --blue-light: #5b8bff;
  --purple: #7c3aed;
  --purple-light: #a78bfa;
  --cyan: #00d4ff;
  --white: #eef2ff;
  --muted: rgba(238,242,255,0.5);
  --muted2: rgba(238,242,255,0.28);
  --border: rgba(255,255,255,0.08);
  --border2: rgba(37,99,255,0.2);
  --glass: rgba(255,255,255,0.03);
  --glass2: rgba(37,99,255,0.08);
  --r: 16px;
  --r2: 20px;
  --wa: #25d366;
}

/* ===================== SCROLLBAR ===================== */
::-webkit-scrollbar { width: 3px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: var(--blue); border-radius: 2px; }

/* ===================== TYPOGRAPHY ===================== */
h1,h2,h3,h4 { font-family: 'Syne', sans-serif; font-weight: 800; line-height: 1.08; letter-spacing: -0.025em; color: var(--white); }
h1 { font-size: clamp(2.2rem, 9vw, 3.2rem); }
h2 { font-size: clamp(1.8rem, 7vw, 2.6rem); }
h3 { font-size: 1.1rem; }
p { color: var(--muted); line-height: 1.7; }

/* ===================== LAYOUT ===================== */
.wrap { max-width: 480px; margin: 0 auto; padding: 0 20px; }
@media(min-width:600px){ .wrap { max-width: 640px; padding: 0 28px; } }
@media(min-width:900px){ .wrap { max-width: 1100px; padding: 0 40px; } }

section { position: relative; }

/* gradient text helper */
.grad {
  background: linear-gradient(135deg, var(--blue-light) 0%, var(--purple-light) 60%, var(--cyan) 100%);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}

/* ===================== NOISE LAYER ===================== */
body::after {
  content:''; position:fixed; inset:0; pointer-events:none; z-index:9000; opacity:.018;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}

/* ===================== NAV ===================== */
nav {
  position: fixed; top:0; left:0; right:0; z-index:500;
  transition: background .3s, border-color .3s;
}
nav.solid {
  background: rgba(2,4,8,.92);
  border-bottom: 1px solid var(--border);
  backdrop-filter: blur(20px);
}
.nav-inner {
  display: flex; align-items: center; justify-content: space-between;
  height: 60px;
}
.logo {
  font-family: 'Syne', sans-serif; font-weight: 800;
  font-size: 1.35rem; letter-spacing: -0.04em;
  background: linear-gradient(120deg, #fff 30%, var(--cyan));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
}
.logo span { -webkit-text-fill-color: var(--blue-light); }
.nav-right { display: flex; align-items: center; gap: 10px; }
.nav-wa {
  display: flex; align-items: center; gap: 7px;
  padding: 9px 18px;
  background: var(--blue); border-radius: 100px;
  font-size: 0.82rem; font-weight: 600; color: #fff;
  transition: background .25s, transform .2s;
  box-shadow: 0 0 18px rgba(37,99,255,.35);
}
.nav-wa:active { transform: scale(.97); background: var(--blue-light); }
.nav-wa svg { width:14px; height:14px; flex-shrink:0; }

/* hamburger */
.ham { display:flex; flex-direction:column; gap:5px; cursor:pointer; padding:8px; background:none; border:none; }
.ham span { display:block; width:22px; height:2px; background:var(--white); border-radius:2px; transition:.3s; }
.ham.open span:nth-child(1) { transform: rotate(45deg) translate(5px,5px); }
.ham.open span:nth-child(2) { opacity:0; }
.ham.open span:nth-child(3) { transform: rotate(-45deg) translate(5px,-5px); }

/* desktop nav links */
.nav-links { display:none; gap:28px; }
@media(min-width:900px){
  .nav-links { display:flex; }
  .nav-links a { font-size:.82rem; font-weight:500; color:var(--muted); letter-spacing:.04em; text-transform:uppercase; transition:color .25s; }
  .nav-links a:hover { color:var(--white); }
  .ham { display:none; }
}

/* ===================== MOBILE DRAWER ===================== */
.drawer {
  position:fixed; inset:0; z-index:490;
  background: rgba(2,4,8,.97); backdrop-filter:blur(24px);
  display:flex; flex-direction:column; align-items:center; justify-content:center; gap:36px;
  transform: translateX(100%); transition: transform .4s cubic-bezier(.23,1,.32,1);
}
.drawer.open { transform:translateX(0); }
.drawer a { font-family:'Syne',sans-serif; font-size:2rem; font-weight:800; color:var(--muted); transition:color .25s; }
.drawer a:hover, .drawer a:active { color:var(--white); }
.drawer-wa {
  margin-top:8px; display:flex; align-items:center; gap:10px;
  padding:16px 36px; background:var(--wa); border-radius:100px;
  font-size:1rem; font-weight:600; color:#fff;
}

/* ===================== HERO ===================== */
#hero {
  padding: 100px 0 60px;
  background:
    radial-gradient(ellipse 90% 55% at 50% -5%, rgba(37,99,255,.18) 0%, transparent 65%),
    radial-gradient(ellipse 60% 40% at 85% 90%, rgba(124,58,237,.12) 0%, transparent 60%);
  min-height: 100svh;
  display: flex; align-items: center;
}
.hero-badge {
  display:inline-flex; align-items:center; gap:8px;
  padding:6px 14px 6px 8px;
  background:var(--glass2); border:1px solid var(--border2);
  border-radius:100px; font-size:.75rem; font-weight:600;
  color:var(--blue-light); letter-spacing:.06em; text-transform:uppercase;
  margin-bottom:22px;
}
.badge-dot { width:6px; height:6px; border-radius:50%; background:var(--cyan); animation:blink 2s infinite; }
@keyframes blink { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:.5;transform:scale(1.5)} }
.hero h1 { margin-bottom:16px; }
.hero-sub { font-size:.97rem; max-width:420px; margin-bottom:32px; }
.hero-btns { display:flex; flex-direction:column; gap:12px; }
@media(min-width:400px){ .hero-btns { flex-direction:row; flex-wrap:wrap; } }

/* STAT PILLS */
.hero-stats {
  display:flex; gap:10px; margin-top:36px; flex-wrap:wrap;
}
.stat-pill {
  background:var(--glass); border:1px solid var(--border);
  border-radius:100px; padding:8px 14px;
  font-size:.78rem; color:var(--muted);
}
.stat-pill strong { color:var(--white); font-weight:700; }

/* HERO VISUAL CARD */
.hero-card-wrap {
  margin-top:40px;
  position:relative;
}
.hero-card {
  background:rgba(13,21,32,.85); border:1px solid var(--border);
  border-radius: var(--r2); padding:22px;
  backdrop-filter:blur(30px);
  box-shadow: 0 20px 50px rgba(0,0,0,.45), inset 0 1px 0 rgba(255,255,255,.07);
  animation: card-float 5s ease-in-out infinite;
}
@keyframes card-float { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-8px)} }
.card-top { display:flex; align-items:center; gap:12px; margin-bottom:18px; }
.card-ava {
  width:40px; height:40px; border-radius:50%; flex-shrink:0;
  background:linear-gradient(135deg,var(--blue),var(--purple));
  display:flex; align-items:center; justify-content:center; font-size:1.1rem;
}
.card-ava-info h4 { font-size:.88rem; font-weight:700; font-family:'Plus Jakarta Sans',sans-serif; }
.card-ava-info p { font-size:.72rem; margin:0; }
.card-metrics { display:grid; grid-template-columns:repeat(3,1fr); gap:8px; margin-bottom:14px; }
.cm {
  background:var(--glass2); border:1px solid var(--border2);
  border-radius:10px; padding:10px 8px; text-align:center;
}
.cm-val { display:block; font-family:'Syne',sans-serif; font-size:1.25rem; font-weight:800; color:var(--white); }
.cm-lbl { font-size:.65rem; color:var(--muted); text-transform:uppercase; letter-spacing:.05em; }
.card-bar-lbl { font-size:.72rem; color:var(--muted); margin-bottom:7px; }
.bar-track { height:5px; background:var(--glass); border-radius:100px; overflow:hidden; }
.bar-fill { height:100%; width:78%; background:linear-gradient(90deg,var(--blue),var(--cyan)); border-radius:100px; animation:bar-in 1.5s ease-out; }
@keyframes bar-in { from{width:0} to{width:78%} }

/* card glow orbs */
.hero-card-wrap::before, .hero-card-wrap::after {
  content:''; position:absolute; border-radius:50%; filter:blur(50px); pointer-events:none; z-index:-1;
}
.hero-card-wrap::before { width:180px; height:180px; background:var(--blue); opacity:.18; top:-20px; right:-20px; }
.hero-card-wrap::after { width:120px; height:120px; background:var(--purple); opacity:.15; bottom:-20px; left:20px; }

@media(min-width:900px){
  .hero-grid { display:grid; grid-template-columns:1fr 1fr; gap:60px; align-items:center; }
  .hero-card-wrap { margin-top:0; }
  .hero-btns { flex-direction:row; }
}

/* ===================== BUTTONS ===================== */
.btn-primary {
  display:inline-flex; align-items:center; justify-content:center; gap:9px;
  padding:14px 26px; border-radius:100px;
  background:linear-gradient(135deg,var(--blue) 0%,var(--purple) 100%);
  font-size:.9rem; font-weight:600; color:#fff;
  transition:transform .22s, box-shadow .22s;
  box-shadow:0 4px 24px rgba(37,99,255,.4);
  -webkit-appearance:none;
}
.btn-primary:active { transform:scale(.97); }
.btn-secondary {
  display:inline-flex; align-items:center; justify-content:center; gap:9px;
  padding:13px 24px; border-radius:100px;
  background:var(--glass); border:1px solid var(--border);
  font-size:.9rem; font-weight:500; color:var(--white);
  transition:background .25s, border-color .25s;
  -webkit-appearance:none;
}
.btn-secondary:active { background:rgba(255,255,255,.07); }
.btn-wa-big {
  display:inline-flex; align-items:center; justify-content:center; gap:12px;
  padding:17px 36px; border-radius:100px;
  background:linear-gradient(135deg,#25d366 0%,#128c7e 100%);
  font-family:'Syne',sans-serif; font-size:1rem; font-weight:800; color:#fff;
  box-shadow:0 6px 32px rgba(37,211,102,.4);
  transition:transform .25s, box-shadow .25s;
}
.btn-wa-big:active { transform:scale(.97); }
.btn-wa-big svg { width:22px; height:22px; flex-shrink:0; }
.wa-svg { display:inline-block; flex-shrink:0; }

/* ===================== SECTION HEADER ===================== */
.sec-label {
  display:inline-flex; align-items:center; gap:8px;
  font-size:.72rem; font-weight:600; color:var(--blue-light);
  text-transform:uppercase; letter-spacing:.12em; margin-bottom:12px;
}
.sec-label::before { content:''; width:20px; height:1px; background:var(--blue-light); }
.sec-title { margin-bottom:12px; }
.sec-sub { font-size:.9rem; max-width:480px; margin-bottom:48px; }
.center { text-align:center; }
.center .sec-sub { margin-left:auto; margin-right:auto; }

/* ===================== TRUST ===================== */
#trust {
  padding:56px 0;
  border-top:1px solid var(--border); border-bottom:1px solid var(--border);
  background:linear-gradient(180deg,rgba(37,99,255,.04) 0%,transparent 100%);
}
.trust-grid { display:grid; grid-template-columns:1fr 1fr; gap:1px; background:var(--border); border:1px solid var(--border); border-radius:var(--r2); overflow:hidden; }
@media(min-width:600px){ .trust-grid { grid-template-columns:repeat(4,1fr); } }
.trust-item { background:var(--bg); padding:28px 16px; text-align:center; }
.trust-num {
  display:block; font-family:'Syne',sans-serif; font-size:2.2rem; font-weight:800;
  background:linear-gradient(135deg,var(--white) 0%,var(--blue-light) 100%);
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
  line-height:1; margin-bottom:6px;
}
.trust-lbl { font-size:.72rem; color:var(--muted); text-transform:uppercase; letter-spacing:.06em; }

/* ===================== SERVICES ===================== */
#services {
  padding:80px 0;
  background:radial-gradient(ellipse 80% 50% at 50% 100%,rgba(124,58,237,.08) 0%,transparent 70%);
}
.services-grid {
  display:grid; grid-template-columns:1fr; gap:12px;
}
@media(min-width:500px){ .services-grid { grid-template-columns:repeat(2,1fr); } }
@media(min-width:900px){ .services-grid { grid-template-columns:repeat(3,1fr); } }
.svc-card {
  background:var(--glass); border:1px solid var(--border);
  border-radius:var(--r2); padding:26px 22px;
  transition:border-color .3s, transform .3s, box-shadow .3s;
  position:relative; overflow:hidden;
}
.svc-card::before {
  content:''; position:absolute; inset:0;
  background:linear-gradient(135deg,rgba(37,99,255,.08) 0%,transparent 70%);
  opacity:0; transition:opacity .3s;
}
@media(hover:hover){
  .svc-card:hover { border-color:rgba(37,99,255,.4); transform:translateY(-5px); box-shadow:0 16px 40px rgba(0,0,0,.35),0 0 30px rgba(37,99,255,.12); }
  .svc-card:hover::before { opacity:1; }
}
.svc-icon {
  width:48px; height:48px; border-radius:12px;
  background:var(--glass2); border:1px solid var(--border2);
  display:flex; align-items:center; justify-content:center;
  font-size:1.3rem; margin-bottom:18px;
}
.svc-card h3 { font-size:1rem; margin-bottom:10px; }
.svc-card p { font-size:.84rem; }

/* ===================== WHY US ===================== */
#why {
  padding:80px 0;
  background:linear-gradient(180deg,transparent 0%,rgba(37,99,255,.04) 50%,transparent 100%);
}
.why-grid-outer { display:grid; gap:48px; }
@media(min-width:900px){ .why-grid-outer { grid-template-columns:1fr 1fr; align-items:center; } }
.why-cards { display:grid; grid-template-columns:repeat(2,1fr); gap:10px; }
@media(min-width:500px){ .why-cards { grid-template-columns:repeat(3,1fr); } }
@media(min-width:900px){ .why-cards { grid-template-columns:repeat(2,1fr); } }
.why-card {
  background:var(--glass); border:1px solid var(--border);
  border-radius:var(--r); padding:18px 16px;
  transition:border-color .25s, background .25s;
}
@media(hover:hover){ .why-card:hover { border-color:var(--border2); background:var(--glass2); } }
.why-ico { font-size:1.4rem; margin-bottom:10px; display:block; }
.why-card h4 { font-family:'Syne',sans-serif; font-size:.9rem; font-weight:700; margin-bottom:5px; }
.why-card p { font-size:.78rem; }

/* ===================== VIRTUAL TOUR ===================== */
#tour {
  padding:80px 0;
  background:radial-gradient(ellipse 80% 60% at 50% 50%,rgba(124,58,237,.09) 0%,transparent 70%);
}
.tour-box {
  border-radius:var(--r2); overflow:hidden;
  border:1px solid var(--border);
  background:var(--bg3);
  position:relative; height:340px;
  display:flex; align-items:center; justify-content:center;
  margin-bottom:16px;
}
@media(min-width:600px){ .tour-box { height:420px; } }
.tour-bg-glow {
  position:absolute; inset:0; pointer-events:none;
  background:
    radial-gradient(circle at 30% 50%,rgba(37,99,255,.2) 0%,transparent 55%),
    radial-gradient(circle at 70% 50%,rgba(124,58,237,.15) 0%,transparent 55%);
}
.tour-grid-bg {
  position:absolute; inset:0; pointer-events:none;
  background-image:linear-gradient(rgba(37,99,255,.07) 1px,transparent 1px),
                   linear-gradient(90deg,rgba(37,99,255,.07) 1px,transparent 1px);
  background-size:48px 48px;
}
.tour-content { position:relative; z-index:2; text-align:center; padding:20px; }
.tour-sphere {
  width:130px; height:130px; border-radius:50%; margin:0 auto 20px;
  background:radial-gradient(circle at 35% 35%,rgba(37,99,255,.55),rgba(124,58,237,.35),rgba(0,212,255,.15));
  border:2px solid rgba(37,99,255,.4);
  box-shadow:0 0 50px rgba(37,99,255,.4),inset 0 0 30px rgba(0,229,255,.12);
  animation:sphere-glow 4s ease-in-out infinite;
}
@keyframes sphere-glow {
  0%,100% { box-shadow:0 0 50px rgba(37,99,255,.4),inset 0 0 30px rgba(0,229,255,.12); }
  50% { box-shadow:0 0 70px rgba(124,58,237,.5),inset 0 0 30px rgba(0,229,255,.22); }
}
.tour-title { font-family:'Syne',sans-serif; font-size:1.2rem; font-weight:800; margin-bottom:8px; }
.tour-desc { font-size:.82rem; color:var(--muted); margin-bottom:16px; }
.tour-cta-btn {
  display:inline-flex; align-items:center; gap:6px;
  padding:9px 20px;
  background:rgba(0,212,255,.1); border:1px solid rgba(0,212,255,.3);
  border-radius:100px; font-size:.78rem; color:var(--cyan); font-weight:600;
  transition:background .25s;
}
.tour-cta-btn:active { background:rgba(0,212,255,.2); }

/* hotspots */
.hs {
  position:absolute; width:10px; height:10px; border-radius:50%;
  background:var(--cyan); cursor:pointer;
  box-shadow:0 0 0 3px rgba(0,212,255,.2),0 0 14px rgba(0,212,255,.5);
  animation:hs-pulse 2.5s infinite;
  z-index:3;
}
@keyframes hs-pulse {
  0%,100%{box-shadow:0 0 0 3px rgba(0,212,255,.2),0 0 14px rgba(0,212,255,.5)}
  50%{box-shadow:0 0 0 6px rgba(0,212,255,.1),0 0 20px rgba(0,212,255,.6)}
}
.hs-label {
  position:absolute; left:18px; top:50%; transform:translateY(-50%);
  background:rgba(8,13,20,.9); border:1px solid var(--border);
  border-radius:8px; padding:3px 9px; font-size:.65rem; white-space:nowrap;
  pointer-events:none; opacity:0; transition:opacity .25s;
}
.hs:hover .hs-label { opacity:1; }

/* tour 3 cards */
.tour-cards { display:grid; grid-template-columns:repeat(3,1fr); gap:10px; }
.tour-mini-card {
  background:var(--glass); border:1px solid var(--border);
  border-radius:var(--r); padding:16px 12px; text-align:center;
}
.tour-mini-card .ico { font-size:1.4rem; margin-bottom:8px; }
.tour-mini-card h4 { font-size:.85rem; margin-bottom:4px; }
.tour-mini-card p { font-size:.72rem; }

/* ===================== PROCESS ===================== */
#process { padding:80px 0; }
.process-list { display:grid; grid-template-columns:1fr; gap:16px; }
@media(min-width:600px){ .process-list { grid-template-columns:repeat(2,1fr); } }
@media(min-width:900px){ .process-list { grid-template-columns:repeat(4,1fr); } }
.proc-card {
  background:var(--glass); border:1px solid var(--border);
  border-radius:var(--r2); padding:26px 22px;
  position:relative; overflow:hidden;
  transition:border-color .3s, transform .3s;
}
@media(hover:hover){ .proc-card:hover { border-color:var(--border2); transform:translateY(-4px); } }
.proc-num {
  font-family:'Syne',sans-serif; font-size:3rem; font-weight:800;
  line-height:1; color:rgba(37,99,255,.12); position:absolute; top:16px; right:16px;
}
.proc-icon { font-size:1.5rem; margin-bottom:14px; display:block; }
.proc-card h3 { font-size:1rem; margin-bottom:8px; }
.proc-card p { font-size:.82rem; }

/* ===================== TESTIMONIALS ===================== */
#testimonials {
  padding:80px 0;
  background:radial-gradient(ellipse 70% 50% at 50% 100%,rgba(37,99,255,.07) 0%,transparent 70%);
}
.testi-list { display:grid; grid-template-columns:1fr; gap:12px; }
@media(min-width:600px){ .testi-list { grid-template-columns:repeat(2,1fr); } }
@media(min-width:900px){ .testi-list { grid-template-columns:repeat(3,1fr); } }
.testi-card {
  background:var(--glass); border:1px solid var(--border);
  border-radius:var(--r2); padding:26px 22px;
  transition:border-color .3s, transform .3s;
}
@media(hover:hover){ .testi-card:hover { border-color:var(--border2); transform:translateY(-4px); } }
.stars { color:#fbbf24; font-size:.85rem; letter-spacing:2px; margin-bottom:14px; }
.testi-text { font-size:.86rem; line-height:1.8; color:rgba(238,242,255,.78); font-style:italic; margin-bottom:20px; }
.testi-author { display:flex; align-items:center; gap:10px; }
.testi-ava {
  width:40px; height:40px; border-radius:50%; flex-shrink:0;
  display:flex; align-items:center; justify-content:center;
  font-family:'Syne',sans-serif; font-size:.9rem; font-weight:800; color:#fff;
}
.testi-name { font-size:.88rem; font-weight:600; color:var(--white); }
.testi-role { font-size:.72rem; color:var(--muted); }

/* ===================== FINAL CTA ===================== */
#cta {
  padding:100px 0;
  text-align:center;
  background:
    radial-gradient(ellipse 70% 60% at 50% 50%,rgba(37,99,255,.18) 0%,transparent 70%),
    radial-gradient(ellipse 40% 40% at 20% 20%,rgba(124,58,237,.12) 0%,transparent 60%);
}
.cta-badge {
  display:inline-block; padding:5px 16px;
  background:rgba(0,212,255,.1); border:1px solid rgba(0,212,255,.25);
  border-radius:100px; font-size:.72rem; color:var(--cyan);
  letter-spacing:.08em; text-transform:uppercase; margin-bottom:20px;
  font-weight:600;
}
#cta h2 { margin-bottom:14px; }
#cta p { font-size:.92rem; max-width:380px; margin:0 auto 36px; }
.cta-note { font-size:.76rem; color:var(--muted2); margin-top:16px; }

/* ===================== FOOTER ===================== */
<footer>
  <div class="wrap">
    <div class="footer-top">
      <div class="footer-brand">
        <span class="logo">Grow<span>Sage</span></span>
        <p>A premium digital agency helping local businesses, coaches, institutes, and startups grow their brand — faster and smarter.</p>
        <a href="https://wa.me/918823096017" target="_blank" class="footer-wa-link">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="#4ade80"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
          +91 88230 96017
        </a>
      </div>
      <div class="footer-col">
        <h4>Quick Links</h4>
        <a href="#services">Services</a>
        <a href="#why">Why Us</a>
        <a href="#tour">Virtual Tours</a>
        <a href="#process">Our Process</a>
        <a href="#testimonials">Reviews</a>
      </div>
      <div class="footer-col">
        <h4>Services</h4>
        <a href="https://wa.me/918823096017" target="_blank">Social Media Marketing</a>
        <a href="https://wa.me/918823096017" target="_blank">Social Management</a>
        <a href="https://wa.me/918823096017" target="_blank">360° Virtual Tours</a>
        <a href="https://wa.me/918823096017" target="_blank">Website Development</a>
        <a href="https://wa.me/918823096017" target="_blank">UI/UX Design</a>
        <a href="https://wa.me/918823096017" target="_blank">Video Editing</a>
      </div>
      <div class="footer-col">
        <h4>We Serve</h4>
        <a href="#">Local Businesses</a>
        <a href="#">Coaches & Educators</a>
        <a href="#">Institutes</a>
        <a href="#">Restaurants & Cafés</a>
        <a href="#">Real Estate Brands</a>
        <a href="#">Personal Brands</a>
      </div>
    </div>
    <div class="footer-bottom">
      <p class="footer-copy">© 2024 GrowSage Digital Agency. All rights reserved.</p>
      <div class="socials">
        <a href="#" class="soc" aria-label="Instagram">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor" stroke="none"/></svg>
        </a>
        <a href="#" class="soc" aria-label="Facebook">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M18 2h-3a5 5 0 00-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 011-1h3z"/></svg>
        </a>
        <a href="#" class="soc" aria-label="LinkedIn">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        </a>
        <a href="https://wa.me/918823096017" target="_blank" class="soc" aria-label="WhatsApp">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
        </a>
      </div>
    </div>
  </div>
</footer>

<script>
/* NAV SOLID ON SCROLL */
const nav = document.getElementById('nav');
window.addEventListener('scroll', () => nav.classList.toggle('solid', window.scrollY > 30), { passive: true });
nav.classList.add('solid');

/* HAMBURGER DRAWER */
const ham = document.getElementById('ham');
const drawer = document.getElementById('drawer');
ham.addEventListener('click', () => {
  const open = drawer.classList.toggle('open');
  ham.classList.toggle('open', open);
  document.body.style.overflow = open ? 'hidden' : '';
});
document.querySelectorAll('.drawer-link, .drawer-wa').forEach(a => {
  a.addEventListener('click', () => {
    drawer.classList.remove('open');
    ham.classList.remove('open');
    document.body.style.overflow = '';
  });
});

/* FADE IN ON SCROLL */
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('in'); obs.unobserve(e.target); } });
}, { threshold: 0.1 });
document.querySelectorAll('.fi').forEach(el => obs.observe(el));

/* COUNTER ANIMATION */
const counters = document.querySelectorAll('.trust-num[data-t]');
const cobs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (!e.isIntersecting) return;
    const el = e.target;
    const target = parseInt(el.dataset.t);
    const suffix = el.dataset.s;
    let n = 0, step = target / 55;
    const run = () => {
      n = Math.min(n + step, target);
      el.textContent = Math.floor(n) + suffix;
      if (n < target) requestAnimationFrame(run);
    };
    requestAnimationFrame(run);
    cobs.unobserve(el);
  });
}, { threshold: 0.5 });
counters.forEach(c => cobs.observe(c));
</script>
</body>
</html>
