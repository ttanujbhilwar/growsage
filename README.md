
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
<title>Portfolio — Growsage 360°</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=Instrument+Serif:ital@0;1&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
/* ================================================
   BASE RESET & CSS VARIABLES
   ================================================ */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --ink:#0D0D0D;
  --ink2:#1A1A1A;
  --ink3:#242424;
  --smoke:#F2EDE8;
  --smoke2:#E8E2DB;
  --gold:#C9A96E;
  --gold-dim:rgba(201,169,110,0.15);
  --gold-glow:rgba(201,169,110,0.08);
  --rust:#B85C38;
  --sand:#D4B896;
  --text:#F0EAE2;
  --text-muted:rgba(240,234,226,0.45);
  --text-sub:rgba(240,234,226,0.65);
  --font-head:'Syne',sans-serif;
  --font-serif:'Instrument Serif',serif;
  --font-body:'DM Sans',sans-serif;

  /* Responsive spacing scale */
  --space-xs: 0.5rem;
  --space-sm: 0.75rem;
  --space-md: 1rem;
  --space-lg: 1.5rem;
  --space-xl: 2rem;
  --space-2xl: 3rem;
  --space-3xl: 4rem;
  --space-4xl: 5rem;
}

html{scroll-behavior:smooth;overflow-x:hidden}
body{
  font-family:var(--font-body);
  background:var(--ink);
  color:var(--text);
  overflow-x:hidden;
  cursor:none;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing:grayscale;
  min-height:100vh;
  width:100%;
}

/* ================================================
   CUSTOM CURSOR — HIDDEN ON MOBILE/TABLET
   ================================================ */
.cursor{
  position:fixed;
  pointer-events:none;
  z-index:9999;
  mix-blend-mode:difference;
  display:none; /* Hidden by default, shown on desktop */
}
.cursor-dot{
  width:8px;
  height:8px;
  background:var(--gold);
  border-radius:50%;
  transform:translate(-50%,-50%);
  transition:transform 0.1s;
}
.cursor-ring{
  width:36px;
  height:36px;
  border:1px solid rgba(201,169,110,0.5);
  border-radius:50%;
  transform:translate(-50%,-50%);
  transition:all 0.18s ease;
  top:0;
  left:0;
}

/* ================================================
   LOADING BAR
   ================================================ */
.load-bar{
  position:fixed;
  top:0;
  left:0;
  height:2px;
  background:var(--gold);
  z-index:9998;
  transition:width 0.4s ease;
  width:0;
}

/* ================================================
   NAVIGATION — MOBILE-FIRST
   ================================================ */
nav{
  position:fixed;
  top:0;
  left:0;
  right:0;
  z-index:100;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:1rem 4%; /* Reduced padding for mobile */
  border-bottom:1px solid rgba(201,169,110,0.1);
  background:rgba(13,13,13,0.9);
  backdrop-filter:blur(16px);
  -webkit-backdrop-filter:blur(16px);
  min-height:56px; /* Ensure minimum touch target height */
}
.nav-logo{
  font-family:var(--font-head);
  font-size:1.1rem; /* Slightly smaller for mobile */
  font-weight:800;
  color:var(--text);
  text-decoration:none;
  letter-spacing:-0.02em;
  flex-shrink:0;
}
.nav-logo span{color:var(--gold)}

/* Mobile hamburger menu button */
.nav-hamburger{
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  width:44px;
  height:44px;
  background:transparent;
  border:none;
  cursor:pointer;
  padding:8px;
  gap:5px;
  z-index:101;
}
.nav-hamburger span{
  display:block;
  width:24px;
  height:2px;
  background:var(--gold);
  border-radius:2px;
  transition:all 0.3s ease;
}
.nav-hamburger.active span:nth-child(1){transform:rotate(45deg) translate(5px,5px)}
.nav-hamburger.active span:nth-child(2){opacity:0}
.nav-hamburger.active span:nth-child(3){transform:rotate(-45deg) translate(5px,-5px)}

/* Mobile nav menu overlay */
.nav-mobile-menu{
  position:fixed;
  top:0;
  left:0;
  right:0;
  bottom:0;
  background:rgba(13,13,13,0.98);
  backdrop-filter:blur(20px);
  -webkit-backdrop-filter:blur(20px);
  z-index:99;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  gap:2rem;
  opacity:0;
  visibility:hidden;
  transition:all 0.4s ease;
  padding:2rem;
}
.nav-mobile-menu.active{
  opacity:1;
  visibility:visible;
}
.nav-mobile-menu a{
  font-family:var(--font-head);
  font-size:1.5rem;
  font-weight:700;
  color:var(--text);
  text-decoration:none;
  letter-spacing:0.05em;
  text-transform:uppercase;
  padding:0.75rem 1.5rem;
  transition:color 0.2s;
}
.nav-mobile-menu a:hover{color:var(--gold)}

.nav-back{
  display:none; /* Hidden on mobile, shown on desktop */
  align-items:center;
  gap:8px;
  font-family:var(--font-head);
  font-size:0.72rem;
  font-weight:600;
  letter-spacing:0.12em;
  text-transform:uppercase;
  color:var(--text-muted);
  text-decoration:none;
  transition:color 0.2s;
  min-height:44px;
}
.nav-back:hover{color:var(--gold)}

.nav-cta{
  display:none; /* Hidden on mobile, shown in hamburger menu */
  font-family:var(--font-head);
  font-size:0.72rem;
  font-weight:700;
  letter-spacing:0.1em;
  text-transform:uppercase;
  color:var(--ink);
  background:var(--gold);
  padding:0.55rem 1.4rem;
  border-radius:100px;
  text-decoration:none;
  transition:opacity 0.2s,transform 0.15s;
  white-space:nowrap;
  min-height:44px;
  align-items:center;
}
.nav-cta:hover{opacity:0.88;transform:translateY(-1px)}

/* ================================================
   HERO SECTION — MOBILE-FIRST
   ================================================ */
.port-hero{
  padding:6rem 4% 3rem; /* Reduced for mobile */
  display:flex;
  flex-direction:column; /* Stack vertically on mobile */
  gap:2rem;
  align-items:center; /* Center on mobile */
  text-align:center; /* Center text on mobile */
  border-bottom:1px solid rgba(201,169,110,0.12);
}
.ph-kicker{
  display:inline-flex;
  align-items:center;
  gap:10px;
  font-family:var(--font-head);
  font-size:0.65rem; /* Smaller for mobile */
  font-weight:700;
  letter-spacing:0.18em;
  text-transform:uppercase;
  color:var(--gold);
  margin-bottom:1rem;
}
.ph-kicker::before{
  content:'';
  width:24px; /* Shorter line on mobile */
  height:1px;
  background:var(--gold);
}
.ph-h1{
  font-family:var(--font-head);
  font-size:clamp(2rem,8vw,5.5rem); /* Mobile-first clamp */
  font-weight:800;
  line-height:1;
  letter-spacing:-0.04em;
  margin-bottom:1rem;
  word-break:break-word;
}
.ph-h1 em{
  font-family:var(--font-serif);
  font-style:italic;
  font-weight:400;
  color:var(--gold);
}
.ph-desc{
  font-size:0.9rem; /* Slightly smaller for mobile */
  line-height:1.7;
  color:var(--text-sub);
  font-weight:300;
  max-width:100%; /* Full width on mobile */
  padding:0 0.5rem;
}
.ph-right{
  display:flex;
  flex-direction:column;
  justify-content:flex-end;
  gap:1.5rem; /* Reduced gap for mobile */
  width:100%;
}

/* Stats grid — mobile optimized */
.ph-stats{
  display:grid;
  grid-template-columns:repeat(2,1fr); /* 2 columns on mobile */
  gap:1px;
  background:rgba(201,169,110,0.12);
  border:1px solid rgba(201,169,110,0.12);
  border-radius:12px; /* Slightly smaller radius on mobile */
  overflow:hidden;
}
.ph-stat{
  background:var(--ink2);
  padding:1rem 0.5rem; /* Reduced padding for mobile */
  text-align:center;
}
.ph-stat-n{
  font-family:var(--font-head);
  font-size:1.6rem; /* Smaller for mobile */
  font-weight:800;
  color:var(--gold);
  letter-spacing:-0.04em;
  line-height:1;
}
.ph-stat-l{
  font-size:0.6rem; /* Smaller for mobile */
  font-weight:500;
  letter-spacing:0.08em;
  text-transform:uppercase;
  color:var(--text-muted);
  margin-top:4px;
}

/* Filter buttons — mobile optimized */
.ph-filter-row{
  display:flex;
  gap:6px;
  flex-wrap:wrap;
  justify-content:center; /* Center on mobile */
  padding:0 0.5rem;
}
.filter-btn{
  font-family:var(--font-head);
  font-size:0.65rem; /* Smaller for mobile */
  font-weight:600;
  letter-spacing:0.06em;
  text-transform:uppercase;
  padding:6px 12px; /* Touch-friendly padding */
  border-radius:100px;
  border:1px solid rgba(201,169,110,0.25);
  color:var(--text-muted);
  background:transparent;
  cursor:pointer;
  transition:all 0.2s;
  min-height:36px; /* Minimum touch target */
  flex:1 1 auto; /* Allow buttons to grow */
  max-width:120px;
}
.filter-btn:hover,.filter-btn.active{
  border-color:var(--gold);
  color:var(--gold);
  background:var(--gold-dim);
}

/* ================================================
   PORTFOLIO GRID — MOBILE-FIRST
   ================================================ */
.port-grid-wrap{
  padding:2rem 4%; /* Reduced for mobile */
}
.port-grid{
  display:flex; /* Flexbox for mobile stacking */
  flex-direction:column;
  gap:1rem; /* Reduced gap for mobile */
}

/* ================================================
   CARDS — MOBILE-FIRST
   ================================================ */
.pc{
  border-radius:16px; /* Slightly smaller for mobile */
  overflow:hidden;
  background:var(--ink2);
  border:1px solid rgba(255,255,255,0.05);
  position:relative;
  cursor:none;
  transition:transform 0.4s cubic-bezier(0.25,0.46,0.45,0.94), border-color 0.3s;
  width:100%; /* Full width on mobile */
}
.pc:hover{
  transform:translateY(-4px); /* Reduced lift for mobile */
  border-color:rgba(201,169,110,0.3);
}

/* All cards full width on mobile */
.pc-large,.pc-medium,.pc-wide,.pc-small,.pc-half{
  width:100%;
}

.pc-thumb{
  width:100%;
  aspect-ratio:16/10;
  position:relative;
  overflow:hidden;
  background:var(--ink3);
  display:flex;
  align-items:center;
  justify-content:center;
}
.pc-thumb-inner{
  width:100%;
  height:100%;
  position:relative;
}
.pc-overlay{
  position:absolute;
  inset:0;
  background:rgba(13,13,13,0);
  transition:background 0.4s;
  display:flex;
  align-items:center;
  justify-content:center;
}
.pc:hover .pc-overlay{
  background:rgba(13,13,13,0.5);
}
.pc-play{
  width:48px; /* Smaller for mobile */
  height:48px;
  border-radius:50%;
  border:2px solid var(--gold);
  display:flex;
  align-items:center;
  justify-content:center;
  opacity:0;
  transform:scale(0.7);
  transition:all 0.3s;
  font-size:0.65rem;
  font-weight:700;
  letter-spacing:0.08em;
  text-transform:uppercase;
  font-family:var(--font-head);
  color:var(--gold);
}
.pc:hover .pc-play{
  opacity:1;
  transform:scale(1);
}

/* Scene backgrounds */
.scene-hospital{background:linear-gradient(135deg,#1a1f2e 0%,#0d1117 100%)}
.scene-banquet{background:linear-gradient(135deg,#1f1a14 0%,#120e0a 100%)}
.scene-school{background:linear-gradient(135deg,#14201a 0%,#0a130d 100%)}
.scene-cowork{background:linear-gradient(135deg,#1a1a2e 0%,#10101e 100%)}
.scene-hotel{background:linear-gradient(135deg,#201818 0%,#120d0d 100%)}
.scene-realestate{background:linear-gradient(135deg,#1a1e14 0%,#0e110a 100%)}

.scene-grid-lines{
  position:absolute;
  inset:0;
  background-image:linear-gradient(rgba(201,169,110,0.04) 1px,transparent 1px),linear-gradient(90deg,rgba(201,169,110,0.04) 1px,transparent 1px);
  background-size:40px 40px;
}
.scene-label-big{
  font-family:var(--font-head);
  font-size:2.5rem; /* Much smaller for mobile */
  font-weight:800;
  letter-spacing:-0.04em;
  opacity:0.04;
  position:absolute;
  bottom:0.5rem;
  right:0.75rem;
  color:var(--gold);
  line-height:1;
}
.scene-badge{
  position:absolute;
  top:0.75rem;
  left:0.75rem;
  background:rgba(201,169,110,0.15);
  border:1px solid rgba(201,169,110,0.3);
  border-radius:100px;
  padding:4px 10px;
  font-family:var(--font-head);
  font-size:0.55rem;
  font-weight:700;
  letter-spacing:0.1em;
  text-transform:uppercase;
  color:var(--gold);
}
.scene-360-ring{
  width:60px; /* Smaller for mobile */
  height:60px;
  border-radius:50%;
  border:1.5px solid rgba(201,169,110,0.25);
  display:flex;
  align-items:center;
  justify-content:center;
  font-family:var(--font-head);
  font-size:0.7rem;
  font-weight:800;
  color:rgba(201,169,110,0.5);
  letter-spacing:0.05em;
}
.scene-dots{position:absolute;inset:0}
.dot-pulse{
  position:absolute;
  width:8px; /* Smaller for mobile */
  height:8px;
  border-radius:50%;
  background:var(--gold);
  opacity:0.7;
  animation:dotpulse 2s ease-in-out infinite;
}
@keyframes dotpulse{
  0%,100%{transform:scale(1);opacity:0.7}
  50%{transform:scale(1.6);opacity:0.3}
}

/* Card body — mobile optimized */
.pc-body{
  padding:1rem; /* Reduced for mobile */
}
.pc-cat{
  font-family:var(--font-head);
  font-size:0.6rem;
  font-weight:700;
  letter-spacing:0.12em;
  text-transform:uppercase;
  color:var(--gold);
  margin-bottom:0.4rem;
}
.pc-name{
  font-family:var(--font-head);
  font-size:1rem; /* Smaller for mobile */
  font-weight:700;
  color:var(--text);
  margin-bottom:0.3rem;
  letter-spacing:-0.02em;
  word-break:break-word;
}
.pc-loc{
  font-size:0.75rem;
  color:var(--text-muted);
  margin-bottom:0.75rem;
  display:flex;
  align-items:center;
  gap:5px;
}
.pc-tags{
  display:flex;
  gap:4px;
  flex-wrap:wrap;
  margin-bottom:0.75rem;
}
.pc-tag{
  font-family:var(--font-head);
  font-size:0.55rem;
  font-weight:600;
  letter-spacing:0.06em;
  text-transform:uppercase;
  padding:3px 8px;
  border-radius:100px;
  background:rgba(255,255,255,0.05);
  border:1px solid rgba(255,255,255,0.08);
  color:var(--text-muted);
}
.pc-meta{
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding-top:0.75rem;
  border-top:1px solid rgba(255,255,255,0.06);
}
.pc-scenes{
  font-size:0.7rem;
  color:var(--text-muted);
}
.pc-scenes span{
  color:var(--text-sub);
  font-weight:500;
}
.pc-link{
  display:inline-flex;
  align-items:center;
  gap:6px;
  font-family:var(--font-head);
  font-size:0.6rem;
  font-weight:700;
  letter-spacing:0.08em;
  text-transform:uppercase;
  color:var(--gold);
  text-decoration:none;
  transition:gap 0.2s;
  min-height:36px; /* Touch target */
}
.pc-link:hover{gap:10px}
.pc-link-arrow{font-size:0.85rem}

/* ================================================
   TESTIMONIAL CARD — MOBILE-FIRST
   ================================================ */
.testimonial-card{
  background:var(--ink2);
  border:1px solid rgba(201,169,110,0.15);
  border-radius:16px;
  padding:1.5rem; /* Reduced for mobile */
  display:flex;
  flex-direction:column; /* Stack vertically on mobile */
  gap:1.5rem;
  position:relative;
  overflow:hidden;
}
.testimonial-card::before{
  content:'"';
  font-family:var(--font-serif);
  font-size:6rem; /* Smaller for mobile */
  color:var(--gold);
  opacity:0.08;
  position:absolute;
  top:-0.5rem;
  left:1rem;
  line-height:1;
}
.testi-item{position:relative}
.testi-stars{
  color:var(--gold);
  font-size:0.7rem;
  margin-bottom:0.5rem;
  letter-spacing:2px;
}
.testi-quote{
  font-family:var(--font-serif);
  font-style:italic;
  font-size:0.85rem; /* Smaller for mobile */
  line-height:1.6;
  color:var(--text-sub);
  margin-bottom:0.75rem;
}
.testi-name{
  font-family:var(--font-head);
  font-size:0.7rem;
  font-weight:700;
  letter-spacing:0.06em;
  color:var(--text);
}
.testi-role{
  font-size:0.65rem;
  color:var(--text-muted);
  margin-top:2px;
  line-height:1.4;
}

/* ================================================
   FULL-WIDTH BANNER — MOBILE-FIRST
   ================================================ */
.port-banner{
  padding:2.5rem 4%; /* Reduced for mobile */
  border-top:1px solid rgba(201,169,110,0.1);
  border-bottom:1px solid rgba(201,169,110,0.1);
  display:flex;
  flex-direction:column; /* Stack vertically on mobile */
  align-items:center;
  text-align:center;
  gap:1.5rem;
  background:var(--ink2);
}
.banner-text{max-width:100%}
.banner-h{
  font-family:var(--font-head);
  font-size:clamp(1.5rem,6vw,2.8rem);
  font-weight:800;
  letter-spacing:-0.03em;
  line-height:1.1;
  margin-bottom:0.75rem;
}
.banner-h em{
  font-family:var(--font-serif);
  font-style:italic;
  font-weight:400;
  color:var(--gold);
}
.banner-p{
  font-size:0.85rem;
  line-height:1.7;
  color:var(--text-muted);
  font-weight:300;
}
.banner-cta{
  flex-shrink:0;
  display:inline-flex;
  align-items:center;
  justify-content:center;
  gap:10px;
  background:var(--gold);
  color:var(--ink);
  font-family:var(--font-head);
  font-size:0.75rem;
  font-weight:700;
  letter-spacing:0.08em;
  text-transform:uppercase;
  padding:0.875rem 1.5rem; /* Touch-friendly */
  border-radius:100px;
  text-decoration:none;
  white-space:nowrap;
  transition:opacity 0.2s,transform 0.15s;
  min-height:48px; /* Minimum touch target */
  width:100%; /* Full width on mobile */
  max-width:280px;
}
.banner-cta:hover{
  opacity:0.88;
  transform:translateY(-2px);
}

/* ================================================
   FOOTER — MOBILE-FIRST
   ================================================ */
.port-footer{
  padding:1.5rem 4%; /* Reduced for mobile */
  display:flex;
  flex-direction:column; /* Stack on mobile */
  align-items:center;
  text-align:center;
  gap:0.75rem;
  border-top:1px solid rgba(201,169,110,0.1);
}
.footer-logo{
  font-family:var(--font-head);
  font-size:1.1rem;
  font-weight:800;
  color:var(--text);
}
.footer-logo span{color:var(--gold)}
.footer-copy{
  font-size:0.7rem;
  color:var(--text-muted);
}

/* ================================================
   SCROLL REVEAL — PERFORMANCE OPTIMIZED
   ================================================ */
.reveal{
  opacity:0;
  transform:translateY(20px); /* Reduced for mobile */
  transition:opacity 0.6s ease,transform 0.6s ease;
}
.reveal.visible{
  opacity:1;
  transform:none;
}

/* ================================================
   ================================================
   RESPONSIVE BREAKPOINTS
   ================================================
   ================================================ */

/* ================================================
   375px — Small phones
   ================================================ */
@media (min-width: 375px) {
  .ph-h1{font-size:clamp(2.2rem,7.5vw,5.5rem)}
  .ph-stat-n{font-size:1.8rem}
  .ph-stat-l{font-size:0.65rem}
  .filter-btn{font-size:0.68rem; padding:7px 14px}
  .pc-name{font-size:1.05rem}
  .scene-label-big{font-size:3rem}
  .scene-360-ring{width:65px; height:65px; font-size:0.75rem}
  .banner-cta{width:auto; max-width:none}
}

/* ================================================
   425px — Large phones
   ================================================ */
@media (min-width: 425px) {
  nav{padding:1.1rem 4%}
  .port-hero{padding:6.5rem 4% 3.5rem}
  .ph-h1{font-size:clamp(2.4rem,7vw,5.5rem)}
  .ph-stats{grid-template-columns:repeat(4,1fr)} /* 4 columns on larger phones */
  .ph-stat{padding:1.2rem 0.5rem}
  .ph-stat-n{font-size:2rem}
  .ph-stat-l{font-size:0.65rem}
  .filter-btn{max-width:none; flex:0 1 auto}
  .port-grid-wrap{padding:2.5rem 4%}
  .port-grid{gap:1.25rem}
  .pc-body{padding:1.25rem}
  .pc-name{font-size:1.1rem}
  .scene-label-big{font-size:3.5rem}
  .scene-360-ring{width:70px; height:70px}
  .testimonial-card{padding:2rem}
  .testi-quote{font-size:0.9rem}
  .port-banner{padding:3rem 4%}
  .banner-h{font-size:clamp(1.7rem,5.5vw,2.8rem)}
  .port-footer{padding:2rem 4%; flex-direction:row; justify-content:space-between}
}

/* ================================================
   768px — Tablets
   ================================================ */
@media (min-width: 768px) {
  /* Show desktop nav, hide hamburger */
  .nav-hamburger{display:none}
  .nav-mobile-menu{display:none !important}
  .nav-back{display:inline-flex}
  .nav-cta{display:inline-flex}

  nav{padding:1.2rem 4%}

  .port-hero{
    padding:8rem 4% 4rem;
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:3rem;
    align-items:end;
    text-align:left;
  }
  .ph-kicker{margin-bottom:1.25rem}
  .ph-kicker::before{width:32px}
  .ph-h1{font-size:clamp(2.8rem,5vw,5.5rem); margin-bottom:1.25rem}
  .ph-desc{font-size:0.95rem; max-width:420px; padding:0}
  .ph-right{gap:1.75rem}

  .ph-stats{border-radius:16px}
  .ph-stat{padding:1.4rem}
  .ph-stat-n{font-size:2.2rem}
  .ph-stat-l{font-size:0.7rem; letter-spacing:0.1em}

  .ph-filter-row{justify-content:flex-start; padding:0}
  .filter-btn{font-size:0.72rem; padding:7px 16px; letter-spacing:0.08em}

  /* Grid layout for tablets */
  .port-grid-wrap{padding:3rem 4%}
  .port-grid{
    display:grid;
    grid-template-columns:repeat(12,1fr);
    gap:16px;
  }

  .pc{border-radius:18px}
  .pc:hover{transform:translateY(-6px)}
  .pc-large{grid-column:span 7}
  .pc-medium{grid-column:span 5}
  .pc-wide{grid-column:span 8}
  .pc-small{grid-column:span 4}
  .pc-half{grid-column:span 6}

  .pc-play{width:52px; height:52px; font-size:0.68rem}
  .pc-body{padding:1.25rem}
  .pc-cat{font-size:0.65rem; letter-spacing:0.14em}
  .pc-name{font-size:1.1rem}
  .pc-loc{font-size:0.8rem; margin-bottom:1rem}
  .pc-tags{gap:6px; margin-bottom:1rem}
  .pc-tag{font-size:0.6rem; padding:4px 10px}
  .pc-meta{padding-top:1rem}
  .pc-scenes{font-size:0.75rem}
  .pc-link{font-size:0.65rem; letter-spacing:0.1em}

  .scene-label-big{font-size:4rem; right:1rem}
  .scene-badge{top:1rem; left:1rem; padding:5px 12px; font-size:0.62rem}
  .scene-360-ring{width:75px; height:75px; font-size:0.8rem}
  .dot-pulse{width:10px; height:10px}

  /* Testimonials */
  .testimonial-card{
    grid-column:span 12;
    padding:2.5rem;
    display:grid;
    grid-template-columns:1fr 1fr 1fr;
    gap:2rem;
    border-radius:18px;
  }
  .testimonial-card::before{font-size:8rem; top:-1rem; left:2rem}
  .testi-quote{font-size:0.9rem; line-height:1.7; margin-bottom:1.2rem}
  .testi-name{font-size:0.75rem}
  .testi-role{font-size:0.7rem}

  /* Banner */
  .port-banner{
    padding:4rem 4%;
    flex-direction:row;
    text-align:left;
    align-items:center;
    justify-content:space-between;
    gap:3rem;
  }
  .banner-text{max-width:500px}
  .banner-h{font-size:clamp(1.8rem,3.5vw,2.8rem)}
  .banner-p{font-size:0.9rem}
  .banner-cta{padding:1rem 2rem; font-size:0.8rem; width:auto}

  /* Footer */
  .port-footer{padding:2.5rem 4%}
  .footer-logo{font-size:1.2rem}
  .footer-copy{font-size:0.75rem}

  /* Reveal animation */
  .reveal{transform:translateY(24px)}
}

/* ================================================
   1024px — Small laptops / large tablets
   ================================================ */
@media (min-width: 1024px) {
  .cursor{display:block} /* Show custom cursor on desktop */
  body{cursor:none}

  nav{padding:1.4rem 5%}

  .port-hero{
    padding:10rem 5% 6rem;
    gap:4rem;
  }
  .ph-h1{font-size:clamp(3rem,6vw,5.5rem); margin-bottom:1.5rem}
  .ph-desc{max-width:420px}
  .ph-right{gap:2rem}

  .ph-stats{border-radius:16px}
  .ph-stat{padding:1.5rem}
  .ph-stat-n{font-size:2.2rem}
  .ph-stat-l{font-size:0.7rem}

  .port-grid-wrap{padding:4rem 5%}
  .port-grid{gap:20px}

  .pc{border-radius:20px}
  .pc-play{width:56px; height:56px; font-size:0.72rem}
  .pc-body{padding:1.5rem}
  .pc-name{font-size:1.15rem; margin-bottom:0.4rem}
  .pc-loc{margin-bottom:1rem}
  .pc-tags{gap:6px; margin-bottom:1.2rem}

  .scene-label-big{font-size:4rem}
  .scene-360-ring{width:80px; height:80px; font-size:0.85rem}

  .testimonial-card{padding:3rem; border-radius:20px}
  .testimonial-card::before{font-size:8rem}

  .port-banner{padding:5rem 5%}
  .banner-text{max-width:600px}
  .banner-h{font-size:clamp(1.8rem,3.5vw,2.8rem)}

  .port-footer{padding:2.5rem 5%}

  .reveal{transform:translateY(28px); transition:opacity 0.75s ease,transform 0.75s ease}
}

/* ================================================
   1440px+ — Large desktops
   ================================================ */
@media (min-width: 1440px) {
  .port-hero{padding:12rem 8% 7rem}
  .port-grid-wrap{padding:5rem 8%}
  .port-banner{padding:6rem 8%}
  .port-footer{padding:3rem 8%}
}

/* ================================================
   ACCESSIBILITY & PERFORMANCE
   ================================================ */
@media (prefers-reduced-motion: reduce) {
  *,*::before,*::after{
    animation-duration:0.01ms !important;
    animation-iteration-count:1 !important;
    transition-duration:0.01ms !important;
  }
  .reveal{opacity:1; transform:none; transition:none}
  html{scroll-behavior:auto}
}

/* Touch device optimizations */
@media (hover: none) {
  .pc:hover{transform:none; border-color:rgba(255,255,255,0.05)}
  .pc:hover .pc-overlay{background:rgba(13,13,13,0)}
  .pc:hover .pc-play{opacity:0; transform:scale(0.7)}
  .pc-play{opacity:1; transform:scale(1); background:rgba(201,169,110,0.2)}
  .filter-btn:hover{border-color:rgba(201,169,110,0.25); color:var(--text-muted); background:transparent}
  .filter-btn.active:hover{border-color:var(--gold); color:var(--gold); background:var(--gold-dim)}
}

/* High contrast mode support */
@media (prefers-contrast: high) {
  :root{
    --text:#FFFFFF;
    --text-sub:#E0E0E0;
    --text-muted:#B0B0B0;
    --gold:#FFD700;
  }
  .pc{border:1px solid rgba(255,255,255,0.3)}
}
</style>
<base target="_blank">
</head>
<body>

<!-- ================================================
     CUSTOM CURSOR (Desktop only)
     ================================================ -->
<div class="cursor" id="cursor">
  <div class="cursor-dot" id="cursorDot" style="position:absolute"></div>
  <div class="cursor-ring" id="cursorRing" style="position:absolute"></div>
</div>

<div class="load-bar" id="loadBar"></div>

<!-- ================================================
     NAVIGATION — MOBILE HAMBURGER + DESKTOP
     ================================================ -->
<nav>
  <a href="growsage-website.html" class="nav-back">&#8592; Growsage</a>
  <a href="#" class="nav-logo">Grow<span>sage</span></a>

  <!-- Mobile hamburger button -->
  <button class="nav-hamburger" id="navHamburger" aria-label="Toggle navigation menu" aria-expanded="false">
    <span></span>
    <span></span>
    <span></span>
  </button>

  <a href="growsage-website.html#contact" class="nav-cta">Book a Shoot</a>
</nav>

<!-- Mobile menu overlay -->
<div class="nav-mobile-menu" id="navMobileMenu">
  <a href="growsage-website.html">Home</a>
  <a href="growsage-website.html#services">Services</a>
  <a href="growsage-website.html#about">About</a>
  <a href="growsage-website.html#contact" style="color:var(--gold)">Book a Shoot</a>
</div>

<!-- ================================================
     HERO SECTION
     ================================================ -->
<section class="port-hero">
  <div>
    <div class="ph-kicker">Our Work</div>
    <h1 class="ph-h1">Spaces We've<br>Made <em>Unforgettable</em></h1>
    <p class="ph-desc">Every project is a real business, a real space, and a real result. Browse our 360° portfolio across Indore, Bhopal, and Jabalpur.</p>
  </div>
  <div class="ph-right">
    <div class="ph-stats">
      <div class="ph-stat">
        <div class="ph-stat-n">40+</div>
        <div class="ph-stat-l">Projects Delivered</div>
      </div>
      <div class="ph-stat">
        <div class="ph-stat-n">3</div>
        <div class="ph-stat-l">Cities Active</div>
      </div>
      <div class="ph-stat">
        <div class="ph-stat-n">98%</div>
        <div class="ph-stat-l">Client Retention</div>
      </div>
      <div class="ph-stat">
        <div class="ph-stat-n">5&#9733;</div>
        <div class="ph-stat-l">Google Rating</div>
      </div>
    </div>
    <div class="ph-filter-row" id="filterRow">
      <button class="filter-btn active" data-filter="all">All Work</button>
      <button class="filter-btn" data-filter="hospital">Hospitals</button>
      <button class="filter-btn" data-filter="banquet">Events</button>
      <button class="filter-btn" data-filter="realestate">Real Estate</button>
      <button class="filter-btn" data-filter="school">Education</button>
    </div>
  </div>
</section>

<!-- ================================================
     PORTFOLIO GRID
     ================================================ -->
<div class="port-grid-wrap">
  <div class="port-grid" id="portGrid">

    <!-- Card 1 - Large -->
    <div class="pc pc-large reveal" data-cat="hospital">
      <div class="pc-thumb scene-hospital">
        <div class="scene-grid-lines"></div>
        <div class="scene-360-ring">360°</div>
        <div class="scene-dots">
          <div class="dot-pulse" style="top:35%;left:45%;animation-delay:0s"></div>
          <div class="dot-pulse" style="top:60%;left:70%;animation-delay:0.7s"></div>
          <div class="dot-pulse" style="top:25%;left:20%;animation-delay:1.3s"></div>
        </div>
        <div class="scene-badge">Hospital</div>
        <div class="scene-label-big">OPD</div>
        <div class="pc-overlay"><div class="pc-play">View Tour</div></div>
      </div>
      <div class="pc-body">
        <div class="pc-cat">Healthcare</div>
        <div class="pc-name">Apex Multispeciality Hospital</div>
        <div class="pc-loc">&#128205; Vijay Nagar, Indore</div>
        <div class="pc-tags">
          <span class="pc-tag">Virtual Tour</span>
          <span class="pc-tag">Hotspots</span>
          <span class="pc-tag">GMB Optimized</span>
        </div>
        <div class="pc-meta">
          <div class="pc-scenes">Scenes: <span>12</span></div>
          <a href="#" class="pc-link">View Project <span class="pc-link-arrow">&#8594;</span></a>
        </div>
      </div>
    </div>

    <!-- Card 2 - Medium -->
    <div class="pc pc-medium reveal" data-cat="banquet">
      <div class="pc-thumb scene-banquet">
        <div class="scene-grid-lines"></div>
        <div class="scene-360-ring">360°</div>
        <div class="scene-dots">
          <div class="dot-pulse" style="top:50%;left:50%;animation-delay:0.4s"></div>
          <div class="dot-pulse" style="top:30%;left:75%;animation-delay:1s"></div>
        </div>
        <div class="scene-badge">Banquet</div>
        <div class="scene-label-big">Hall</div>
        <div class="pc-overlay"><div class="pc-play">View Tour</div></div>
      </div>
      <div class="pc-body">
        <div class="pc-cat">Events & Weddings</div>
        <div class="pc-name">Royal Garden Banquets</div>
        <div class="pc-loc">&#128205; Rajwada Area, Indore</div>
        <div class="pc-tags">
          <span class="pc-tag">360° Photos</span>
          <span class="pc-tag">GMB Live</span>
        </div>
        <div class="pc-meta">
          <div class="pc-scenes">Scenes: <span>7</span></div>
          <a href="#" class="pc-link">View Project <span class="pc-link-arrow">&#8594;</span></a>
        </div>
      </div>
    </div>

    <!-- Card 3 - Medium -->
    <div class="pc pc-medium reveal" data-cat="realestate">
      <div class="pc-thumb scene-realestate">
        <div class="scene-grid-lines"></div>
        <div class="scene-360-ring">360°</div>
        <div class="scene-dots">
          <div class="dot-pulse" style="top:40%;left:40%;animation-delay:0.2s"></div>
          <div class="dot-pulse" style="top:65%;left:65%;animation-delay:1.1s"></div>
        </div>
        <div class="scene-badge">Real Estate</div>
        <div class="scene-label-big">Flat</div>
        <div class="pc-overlay"><div class="pc-play">View Tour</div></div>
      </div>
      <div class="pc-body">
        <div class="pc-cat">Real Estate</div>
        <div class="pc-name">Skyline Residency — 3BHK</div>
        <div class="pc-loc">&#128205; Super Corridor, Indore</div>
        <div class="pc-tags">
          <span class="pc-tag">Virtual Tour</span>
          <span class="pc-tag">Under Construction</span>
        </div>
        <div class="pc-meta">
          <div class="pc-scenes">Scenes: <span>9</span></div>
          <a href="#" class="pc-link">View Project <span class="pc-link-arrow">&#8594;</span></a>
        </div>
      </div>
    </div>

    <!-- Card 4 - Wide -->
    <div class="pc pc-wide reveal" data-cat="school">
      <div class="pc-thumb scene-school" style="aspect-ratio:21/9">
        <div class="scene-grid-lines"></div>
        <div class="scene-360-ring">360°</div>
        <div class="scene-dots">
          <div class="dot-pulse" style="top:45%;left:30%;animation-delay:0s"></div>
          <div class="dot-pulse" style="top:30%;left:60%;animation-delay:0.8s"></div>
          <div class="dot-pulse" style="top:60%;left:80%;animation-delay:1.5s"></div>
        </div>
        <div class="scene-badge">Education</div>
        <div class="scene-label-big">Campus</div>
        <div class="pc-overlay"><div class="pc-play">View Tour</div></div>
      </div>
      <div class="pc-body">
        <div class="pc-cat">International School</div>
        <div class="pc-name">Sunrise International Academy</div>
        <div class="pc-loc">&#128205; Bhopal, Madhya Pradesh</div>
        <div class="pc-tags">
          <span class="pc-tag">Full Campus Tour</span>
          <span class="pc-tag">Hotspots</span>
          <span class="pc-tag">Admission Portal Embed</span>
          <span class="pc-tag">GMB Optimized</span>
        </div>
        <div class="pc-meta">
          <div class="pc-scenes">Scenes: <span>18</span></div>
          <a href="#" class="pc-link">View Project <span class="pc-link-arrow">&#8594;</span></a>
        </div>
      </div>
    </div>

    <!-- Card 5 - Small -->
    <div class="pc pc-small reveal" data-cat="banquet">
      <div class="pc-thumb scene-cowork" style="aspect-ratio:4/3">
        <div class="scene-grid-lines"></div>
        <div class="scene-360-ring">360°</div>
        <div class="scene-dots">
          <div class="dot-pulse" style="top:50%;left:50%;animation-delay:0.6s"></div>
        </div>
        <div class="scene-badge">Cowork</div>
        <div class="scene-label-big">Hub</div>
        <div class="pc-overlay"><div class="pc-play">View Tour</div></div>
      </div>
      <div class="pc-body">
        <div class="pc-cat">Coworking</div>
        <div class="pc-name">Worknest Cowork Studio</div>
        <div class="pc-loc">&#128205; Palasia, Indore</div>
        <div class="pc-tags">
          <span class="pc-tag">360° Photos</span>
        </div>
        <div class="pc-meta">
          <div class="pc-scenes">Scenes: <span>5</span></div>
          <a href="#" class="pc-link">View <span class="pc-link-arrow">&#8594;</span></a>
        </div>
      </div>
    </div>

    <!-- Card 6 - Half -->
    <div class="pc pc-half reveal" data-cat="hospital">
      <div class="pc-thumb scene-hospital">
        <div class="scene-grid-lines"></div>
        <div class="scene-360-ring">360°</div>
        <div class="scene-dots">
          <div class="dot-pulse" style="top:40%;left:55%;animation-delay:0.3s"></div>
          <div class="dot-pulse" style="top:65%;left:30%;animation-delay:1.2s"></div>
        </div>
        <div class="scene-badge">Hospital</div>
        <div class="scene-label-big">ICU</div>
        <div class="pc-overlay"><div class="pc-play">View Tour</div></div>
      </div>
      <div class="pc-body">
        <div class="pc-cat">Healthcare</div>
        <div class="pc-name">Medlink Diagnostics Centre</div>
        <div class="pc-loc">&#128205; Jabalpur, Madhya Pradesh</div>
        <div class="pc-tags">
          <span class="pc-tag">Virtual Tour</span>
          <span class="pc-tag">GMB Live</span>
        </div>
        <div class="pc-meta">
          <div class="pc-scenes">Scenes: <span>10</span></div>
          <a href="#" class="pc-link">View Project <span class="pc-link-arrow">&#8594;</span></a>
        </div>
      </div>
    </div>

    <!-- Card 7 - Half -->
    <div class="pc pc-half reveal" data-cat="realestate">
      <div class="pc-thumb scene-realestate">
        <div class="scene-grid-lines"></div>
        <div class="scene-360-ring">360°</div>
        <div class="scene-dots">
          <div class="dot-pulse" style="top:45%;left:45%;animation-delay:0.5s"></div>
          <div class="dot-pulse" style="top:30%;left:70%;animation-delay:1.4s"></div>
        </div>
        <div class="scene-badge">Villa</div>
        <div class="scene-label-big">Villa</div>
        <div class="pc-overlay"><div class="pc-play">View Tour</div></div>
      </div>
      <div class="pc-body">
        <div class="pc-cat">Luxury Real Estate</div>
        <div class="pc-name">Emerald Villas — Phase II</div>
        <div class="pc-loc">&#128205; Bhopal, Madhya Pradesh</div>
        <div class="pc-tags">
          <span class="pc-tag">Virtual Tour</span>
          <span class="pc-tag">Hotspots</span>
        </div>
        <div class="pc-meta">
          <div class="pc-scenes">Scenes: <span>14</span></div>
          <a href="#" class="pc-link">View Project <span class="pc-link-arrow">&#8594;</span></a>
        </div>
      </div>
    </div>

    <!-- TESTIMONIALS -->
    <div class="testimonial-card reveal">
      <div class="testi-item">
        <div class="testi-stars">&#9733;&#9733;&#9733;&#9733;&#9733;</div>
        <div class="testi-quote">Our hospital inquiries went up noticeably after the virtual tour went live on Google Maps. Patients now know exactly what to expect before they arrive.</div>
        <div class="testi-name">Dr. Suresh Malviya</div>
        <div class="testi-role">Director, Apex Multispeciality Hospital, Indore</div>
      </div>
      <div class="testi-item">
        <div class="testi-stars">&#9733;&#9733;&#9733;&#9733;&#9733;</div>
        <div class="testi-quote">Couples call us already convinced after seeing the 360° tour. The virtual tour has become our strongest sales tool — better than any brochure we ever made.</div>
        <div class="testi-name">Ramesh Patidar</div>
        <div class="testi-role">Owner, Royal Garden Banquets, Indore</div>
      </div>
      <div class="testi-item">
        <div class="testi-stars">&#9733;&#9733;&#9733;&#9733;&#9733;</div>
        <div class="testi-quote">Parents from other cities explore our campus virtually before admission inquiries. It saves us hours of explanation and filters in serious buyers from day one.</div>
        <div class="testi-name">Mrs. Priya Soni</div>
        <div class="testi-role">Principal, Sunrise International Academy, Bhopal</div>
      </div>
    </div>

  </div>
</div>

<!-- ================================================
     CTA BANNER
     ================================================ -->
<div class="port-banner reveal">
  <div class="banner-text">
    <div class="banner-h">Your Space Deserves<br>to Be <em>This Seen.</em></div>
    <p class="banner-p">Join 40+ businesses across Madhya Pradesh who let Growsage open their doors to the internet — permanently.</p>
  </div>
  <a href="growsage-website.html#contact" class="banner-cta">Book a Free Site Visit &#8594;</a>
</div>

<!-- ================================================
     FOOTER
     ================================================ -->
<div class="port-footer">
  <div class="footer-logo">Grow<span>sage</span></div>
  <div class="footer-copy">&#169; 2025 Growsage. Indore, Madhya Pradesh.</div>
</div>

<!-- ================================================
     JAVASCRIPT — PERFORMANCE OPTIMIZED
     ================================================ -->
<script>
// ================================================
// CUSTOM CURSOR — Desktop only, disabled on touch
// ================================================
const isTouchDevice = window.matchMedia('(hover: none)').matches || 'ontouchstart' in window;

if (!isTouchDevice) {
  const dot = document.getElementById('cursorDot');
  const ring = document.getElementById('cursorRing');
  let mx=0, my=0, rx=0, ry=0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX;
    my = e.clientY;
    dot.style.left = mx + 'px';
    dot.style.top = my + 'px';
  });

  function animRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animRing);
  }
  animRing();
}

// ================================================
// MOBILE HAMBURGER MENU
// ================================================
const hamburger = document.getElementById('navHamburger');
const mobileMenu = document.getElementById('navMobileMenu');

if (hamburger && mobileMenu) {
  hamburger.addEventListener('click', function() {
    this.classList.toggle('active');
    mobileMenu.classList.toggle('active');
    const expanded = this.classList.contains('active');
    this.setAttribute('aria-expanded', expanded);
    document.body.style.overflow = expanded ? 'hidden' : '';
  });

  // Close menu when clicking a link
  mobileMenu.querySelectorAll('a').forEach(link => {
    link.addEventListener('click', () => {
      hamburger.classList.remove('active');
      mobileMenu.classList.remove('active');
      hamburger.setAttribute('aria-expanded', 'false');
      document.body.style.overflow = '';
    });
  });
}

// ================================================
// LOADING BAR — Scroll progress
// ================================================
const lb = document.getElementById('loadBar');
let ticking = false;

window.addEventListener('scroll', () => {
  if (!ticking) {
    requestAnimationFrame(() => {
      const scrollHeight = document.body.scrollHeight - window.innerHeight;
      const p = scrollHeight > 0 ? (window.scrollY / scrollHeight) * 100 : 0;
      lb.style.width = p + '%';
      ticking = false;
    });
    ticking = true;
  }
}, { passive: true }); // Passive listener for performance

// ================================================
// SCROLL REVEAL — Intersection Observer
// ================================================
const revEls = document.querySelectorAll('.reveal');

if ('IntersectionObserver' in window) {
  const obs = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        // Stagger animation with reduced delay on mobile
        const delay = window.innerWidth < 768 ? i * 60 : i * 90;
        setTimeout(() => e.target.classList.add('visible'), delay);
        obs.unobserve(e.target);
      }
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -30px 0px' });

  revEls.forEach(el => obs.observe(el));
} else {
  // Fallback for older browsers
  revEls.forEach(el => el.classList.add('visible'));
}

// ================================================
// FILTER BUTTONS
// ================================================
document.querySelectorAll('.filter-btn').forEach(btn => {
  btn.addEventListener('click', function() {
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    this.classList.add('active');
    const f = this.dataset.filter;

    document.querySelectorAll('.pc').forEach(card => {
      if (f === 'all' || card.dataset.cat === f) {
        card.style.opacity = '1';
        card.style.transform = '';
        card.style.pointerEvents = '';
        card.style.display = '';
      } else {
        card.style.opacity = '0.2';
        card.style.transform = 'scale(0.97)';
        card.style.pointerEvents = 'none';
      }
    });
  });
});

// ================================================
// PERFORMANCE: Debounced resize handler
// ================================================
let resizeTimer;
window.addEventListener('resize', () => {
  clearTimeout(resizeTimer);
  resizeTimer = setTimeout(() => {
    // Reset any mobile-specific states on resize
    if (window.innerWidth >= 768 && hamburger) {
      hamburger.classList.remove('active');
      mobileMenu.classList.remove('active');
      hamburger.setAttribute('aria-expanded', 'false');
      document.body.style.overflow = '';
    }
  }, 250);
});
</script>
</body>
</html>
