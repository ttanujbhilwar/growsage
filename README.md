<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GrowSage — Digital Agency That Grows Brands</title>
<meta name="description" content="GrowSage is a premium digital agency offering social media marketing, website development, 360° virtual tours, UI/UX design, and video editing for local businesses, coaches, and startups.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet">
<style>
:root {
  --black: #020408;
  --dark: #080d14;
  --dark2: #0c1420;
  --blue: #2563ff;
  --blue-bright: #4d8bff;
  --blue-glow: rgba(37,99,255,0.25);
  --purple: #7c3aed;
  --purple-bright: #a855f7;
  --accent: #00e5ff;
  --accent2: #b94eff;
  --white: #f0f4ff;
  --muted: rgba(240,244,255,0.45);
  --border: rgba(255,255,255,0.07);
  --glass: rgba(255,255,255,0.04);
  --glass2: rgba(37,99,255,0.08);
  --radius: 20px;
  --radius-sm: 12px;
}
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; font-size: 16px; }
body {
  background: var(--black);
  color: var(--white);
  font-family: 'DM Sans', sans-serif;
  font-weight: 300;
  line-height: 1.65;
  overflow-x: hidden;
  cursor: none;
}
::selection { background: var(--blue); color: #fff; }

/* CURSOR */
#cursor {
  width: 12px; height: 12px;
  border-radius: 50%;
  background: var(--accent);
  position: fixed; top: 0; left: 0;
  pointer-events: none;
  z-index: 9999;
  mix-blend-mode: screen;
  transition: transform 0.15s ease;
}
#cursor-ring {
  width: 36px; height: 36px;
  border-radius: 50%;
  border: 1px solid rgba(0,229,255,0.35);
  position: fixed; top: 0; left: 0;
  pointer-events: none;
  z-index: 9998;
  transition: transform 0.4s cubic-bezier(.23,1,.32,1), width 0.3s, height 0.3s, opacity 0.3s;
}
body:hover #cursor { opacity: 1; }

/* SCROLLBAR */
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: var(--dark); }
::-webkit-scrollbar-thumb { background: var(--blue); border-radius: 2px; }

/* TYPOGRAPHY */
h1,h2,h3,h4 { font-family: 'Syne', sans-serif; font-weight: 800; line-height: 1.05; letter-spacing: -0.03em; }
h1 { font-size: clamp(2.8rem, 7vw, 6.5rem); }
h2 { font-size: clamp(2rem, 4.5vw, 3.8rem); }
h3 { font-size: clamp(1.2rem, 2vw, 1.6rem); font-weight: 700; }
p { color: var(--muted); }
a { text-decoration: none; color: inherit; }

/* LAYOUT */
.container { max-width: 1200px; margin: 0 auto; padding: 0 24px; }
section { position: relative; overflow: hidden; }

/* NOISE OVERLAY */
body::before {
  content: '';
  position: fixed; inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
  opacity: 0.022;
  pointer-events: none;
  z-index: 9000;
}

/* NAV */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 1000;
  padding: 20px 0;
  transition: background 0.4s, padding 0.4s, backdrop-filter 0.4s;
}
nav.scrolled {
  background: rgba(2,4,8,0.85);
  backdrop-filter: blur(24px);
  padding: 14px 0;
  border-bottom: 1px solid var(--border);
}
.nav-inner {
  display: flex; align-items: center; justify-content: space-between;
}
.logo {
  font-family: 'Syne', sans-serif;
  font-size: 1.5rem;
  font-weight: 800;
  letter-spacing: -0.04em;
  background: linear-gradient(135deg, #fff 0%, var(--accent) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
.logo span { color: var(--blue-bright); -webkit-text-fill-color: var(--blue-bright); }
.nav-links {
  display: flex; gap: 36px; list-style: none;
}
.nav-links a {
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--muted);
  letter-spacing: 0.02em;
  transition: color 0.3s;
  text-transform: uppercase;
}
.nav-links a:hover { color: var(--white); }
.nav-cta {
  display: flex; align-items: center; gap: 8px;
  padding: 10px 22px;
  background: var(--blue);
  border-radius: 100px;
  font-size: 0.85rem;
  font-weight: 500;
  color: #fff;
  transition: background 0.3s, transform 0.2s, box-shadow 0.3s;
  box-shadow: 0 0 20px rgba(37,99,255,0.4);
}
.nav-cta:hover { background: var(--blue-bright); transform: translateY(-1px); box-shadow: 0 0 30px rgba(37,99,255,0.6); }
.hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; padding: 4px; }
.hamburger span { display: block; width: 24px; height: 2px; background: var(--white); border-radius: 2px; transition: 0.3s; }

/* HERO */
#hero {
  min-height: 100vh;
  display: flex; align-items: center;
  padding: 120px 0 80px;
  background: radial-gradient(ellipse 80% 60% at 50% -10%, rgba(37,99,255,0.18) 0%, transparent 70%),
              radial-gradient(ellipse 60% 50% at 80% 80%, rgba(124,58,237,0.12) 0%, transparent 60%),
              var(--black);
}
.hero-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}
.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 16px 6px 8px;
  background: var(--glass2);
  border: 1px solid rgba(37,99,255,0.25);
  border-radius: 100px;
  font-size: 0.78rem;
  font-weight: 500;
  color: var(--blue-bright);
  margin-bottom: 28px;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}
.badge-dot {
  width: 6px; height: 6px;
  background: var(--accent);
  border-radius: 50%;
  animation: pulse 2s infinite;
}
@keyframes pulse {
  0%,100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.5; transform: scale(1.4); }
}
.hero-title {
  margin-bottom: 24px;
}
.hero-title em {
  font-style: normal;
  background: linear-gradient(135deg, var(--blue-bright) 0%, var(--purple-bright) 50%, var(--accent) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.hero-sub {
  font-size: 1.1rem;
  color: var(--muted);
  max-width: 480px;
  margin-bottom: 40px;
  line-height: 1.7;
}
.hero-btns {
  display: flex; gap: 14px; flex-wrap: wrap;
}
.btn-primary {
  display: inline-flex; align-items: center; gap: 10px;
  padding: 16px 32px;
  background: linear-gradient(135deg, var(--blue) 0%, var(--purple) 100%);
  border-radius: 100px;
  font-size: 0.95rem;
  font-weight: 500;
  color: #fff;
  transition: transform 0.25s, box-shadow 0.25s;
  box-shadow: 0 4px 30px rgba(37,99,255,0.45), 0 0 60px rgba(124,58,237,0.2);
}
.btn-primary:hover { transform: translateY(-3px); box-shadow: 0 8px 40px rgba(37,99,255,0.6), 0 0 80px rgba(124,58,237,0.3); }
.btn-secondary {
  display: inline-flex; align-items: center; gap: 10px;
  padding: 15px 30px;
  background: transparent;
  border: 1px solid var(--border);
  border-radius: 100px;
  font-size: 0.95rem;
  font-weight: 500;
  color: var(--white);
  transition: background 0.3s, border-color 0.3s;
  backdrop-filter: blur(8px);
}
.btn-secondary:hover { background: var(--glass); border-color: rgba(255,255,255,0.18); }
.wa-icon { width: 20px; height: 20px; }

/* HERO VISUAL */
.hero-visual {
  position: relative;
  height: 520px;
}
.hero-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.5;
}
.orb1 { width: 300px; height: 300px; background: var(--blue); top: 10%; left: 10%; animation: orb-float 8s ease-in-out infinite; }
.orb2 { width: 200px; height: 200px; background: var(--purple); bottom: 10%; right: 10%; animation: orb-float 10s ease-in-out infinite reverse; }
.orb3 { width: 150px; height: 150px; background: var(--accent); top: 50%; left: 50%; animation: orb-float 6s ease-in-out infinite 2s; }
@keyframes orb-float {
  0%,100% { transform: translate(0,0) scale(1); }
  33% { transform: translate(20px,-15px) scale(1.05); }
  66% { transform: translate(-15px,10px) scale(0.95); }
}
.hero-card-main {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  width: 340px;
  background: rgba(8,13,20,0.7);
  border: 1px solid var(--border);
  border-radius: 24px;
  padding: 28px;
  backdrop-filter: blur(40px);
  box-shadow: 0 25px 60px rgba(0,0,0,0.5), inset 0 1px 0 rgba(255,255,255,0.08);
  z-index: 2;
  animation: float-card 6s ease-in-out infinite;
}
@keyframes float-card {
  0%,100% { transform: translate(-50%,-50%) translateY(0); }
  50% { transform: translate(-50%,-50%) translateY(-12px); }
}
.card-header { display: flex; align-items: center; gap: 12px; margin-bottom: 20px; }
.card-avatar {
  width: 42px; height: 42px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--blue), var(--purple));
  display: flex; align-items: center; justify-content: center;
  font-size: 1.1rem;
}
.card-info h4 { font-size: 0.9rem; font-weight: 700; color: var(--white); font-family: 'DM Sans', sans-serif; }
.card-info p { font-size: 0.75rem; color: var(--muted); margin: 0; }
.card-metric {
  display: flex; justify-content: space-between;
  background: var(--glass2);
  border: 1px solid rgba(37,99,255,0.15);
  border-radius: 12px;
  padding: 16px;
  margin-bottom: 14px;
}
.metric-item { text-align: center; }
.metric-val { display: block; font-family: 'Syne', sans-serif; font-size: 1.5rem; font-weight: 800; color: var(--white); }
.metric-lbl { font-size: 0.7rem; color: var(--muted); text-transform: uppercase; letter-spacing: 0.05em; }
.card-bar-label { font-size: 0.75rem; color: var(--muted); margin-bottom: 8px; }
.card-bar { height: 6px; background: var(--glass); border-radius: 100px; overflow: hidden; }
.card-bar-fill { height: 100%; border-radius: 100px; background: linear-gradient(90deg, var(--blue), var(--accent)); animation: bar-grow 2s ease-out forwards; }
@keyframes bar-grow { from { width: 0; } to { width: 78%; } }

.floating-tag {
  position: absolute;
  background: rgba(8,13,20,0.85);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 10px 16px;
  font-size: 0.78rem;
  font-weight: 500;
  backdrop-filter: blur(20px);
  white-space: nowrap;
  z-index: 3;
}
.tag1 { top: 12%; left: -10%; animation: float-tag 5s ease-in-out infinite; }
.tag2 { bottom: 15%; right: -5%; animation: float-tag 7s ease-in-out infinite 1s; }
.tag3 { top: 55%; left: -5%; animation: float-tag 6s ease-in-out infinite 2s; }
@keyframes float-tag {
  0%,100% { transform: translateY(0); }
  50% { transform: translateY(-8px); }
}
.tag-dot { display: inline-block; width: 7px; height: 7px; border-radius: 50%; margin-right: 6px; }
.green { background: #22c55e; }
.orange { background: #f97316; }
.blue { background: var(--blue-bright); }

/* TRUST */
#trust {
  padding: 80px 0;
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  background: linear-gradient(180deg, rgba(37,99,255,0.04) 0%, transparent 100%);
}
.trust-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2px;
}
.trust-item {
  text-align: center;
  padding: 40px 24px;
  position: relative;
}
.trust-item:not(:last-child)::after {
  content: '';
  position: absolute; right: 0; top: 25%; bottom: 25%;
  width: 1px;
  background: var(--border);
}
.trust-num {
  font-family: 'Syne', sans-serif;
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 800;
  background: linear-gradient(135deg, var(--white) 0%, var(--blue-bright) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  line-height: 1;
  margin-bottom: 8px;
  display: block;
}
.trust-lbl {
  font-size: 0.85rem;
  color: var(--muted);
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

/* SECTION LABEL */
.section-label {
  display: inline-flex; align-items: center; gap: 8px;
  font-size: 0.75rem;
  font-weight: 500;
  color: var(--blue-bright);
  text-transform: uppercase;
  letter-spacing: 0.12em;
  margin-bottom: 16px;
}
.section-label::before {
  content: '';
  width: 24px; height: 1px;
  background: var(--blue-bright);
}
.section-title { margin-bottom: 16px; }
.section-sub { color: var(--muted); max-width: 520px; margin-bottom: 60px; }

/* SERVICES */
#services {
  padding: 120px 0;
  background: radial-gradient(ellipse 70% 50% at 50% 100%, rgba(124,58,237,0.08) 0%, transparent 70%);
}
.services-header { text-align: center; }
.services-header .section-sub { margin-left: auto; margin-right: auto; }
.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.service-card {
  background: var(--glass);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 36px 30px;
  position: relative;
  overflow: hidden;
  transition: border-color 0.4s, transform 0.4s, box-shadow 0.4s;
  cursor: default;
}
.service-card::before {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, var(--blue-glow) 0%, transparent 60%);
  opacity: 0;
  transition: opacity 0.4s;
}
.service-card:hover {
  border-color: rgba(37,99,255,0.4);
  transform: translateY(-6px);
  box-shadow: 0 20px 50px rgba(0,0,0,0.4), 0 0 40px rgba(37,99,255,0.15);
}
.service-card:hover::before { opacity: 1; }
.service-icon {
  width: 52px; height: 52px;
  border-radius: 14px;
  background: var(--glass2);
  border: 1px solid rgba(37,99,255,0.2);
  display: flex; align-items: center; justify-content: center;
  font-size: 1.4rem;
  margin-bottom: 22px;
  transition: background 0.4s, transform 0.4s;
}
.service-card:hover .service-icon {
  background: rgba(37,99,255,0.2);
  transform: scale(1.1);
}
.service-card h3 { font-size: 1.2rem; margin-bottom: 12px; color: var(--white); }
.service-card p { font-size: 0.88rem; line-height: 1.7; }
.service-arrow {
  position: absolute; bottom: 24px; right: 24px;
  width: 36px; height: 36px;
  border-radius: 50%;
  border: 1px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  font-size: 1rem;
  opacity: 0;
  transform: translateX(-8px);
  transition: opacity 0.3s, transform 0.3s;
}
.service-card:hover .service-arrow { opacity: 1; transform: translateX(0); }

/* WHY US */
#why {
  padding: 120px 0;
  background: linear-gradient(180deg, transparent 0%, rgba(37,99,255,0.04) 50%, transparent 100%);
}
.why-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}
.why-reasons {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
.why-card {
  background: var(--glass);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 24px;
  transition: border-color 0.3s, background 0.3s;
}
.why-card:hover {
  border-color: rgba(37,99,255,0.3);
  background: rgba(37,99,255,0.05);
}
.why-icon { font-size: 1.6rem; margin-bottom: 12px; display: block; }
.why-card h4 { font-family: 'Syne', sans-serif; font-size: 1rem; font-weight: 700; margin-bottom: 6px; }
.why-card p { font-size: 0.82rem; }

/* VIRTUAL TOUR */
#tour {
  padding: 120px 0;
  background: radial-gradient(ellipse 80% 60% at 50% 50%, rgba(124,58,237,0.1) 0%, transparent 70%);
}
.tour-showcase {
  position: relative;
  border-radius: 28px;
  overflow: hidden;
  border: 1px solid var(--border);
  background: var(--dark2);
  height: 520px;
  display: flex; align-items: center; justify-content: center;
}
.tour-bg {
  position: absolute; inset: 0;
  background:
    radial-gradient(circle at 30% 50%, rgba(37,99,255,0.25) 0%, transparent 50%),
    radial-gradient(circle at 70% 50%, rgba(124,58,237,0.2) 0%, transparent 50%);
  animation: tour-bg-shift 8s ease-in-out infinite;
}
@keyframes tour-bg-shift {
  0%,100% { opacity: 1; }
  50% { opacity: 0.7; }
}
.tour-grid-lines {
  position: absolute; inset: 0;
  background-image:
    linear-gradient(rgba(37,99,255,0.08) 1px, transparent 1px),
    linear-gradient(90deg, rgba(37,99,255,0.08) 1px, transparent 1px);
  background-size: 60px 60px;
}
.tour-center {
  position: relative; z-index: 2;
  text-align: center;
}
.tour-sphere {
  width: 200px; height: 200px;
  border-radius: 50%;
  border: 2px solid rgba(37,99,255,0.4);
  margin: 0 auto 32px;
  position: relative;
  background: radial-gradient(circle at 35% 35%, rgba(37,99,255,0.5), rgba(124,58,237,0.3), rgba(0,229,255,0.1));
  box-shadow: 0 0 60px rgba(37,99,255,0.4), inset 0 0 40px rgba(0,229,255,0.15);
  animation: sphere-rotate 10s linear infinite;
  cursor: pointer;
}
.tour-sphere::before, .tour-sphere::after {
  content: '';
  position: absolute; inset: -10px;
  border-radius: 50%;
  border: 1px solid rgba(37,99,255,0.15);
  animation: ring-spin 8s linear infinite;
}
.tour-sphere::after { inset: -20px; animation-duration: 12s; animation-direction: reverse; border-color: rgba(124,58,237,0.12); }
@keyframes sphere-rotate {
  0% { box-shadow: 0 0 60px rgba(37,99,255,0.4), inset 0 0 40px rgba(0,229,255,0.15); }
  50% { box-shadow: 0 0 80px rgba(124,58,237,0.5), inset 0 0 40px rgba(0,229,255,0.25); }
  100% { box-shadow: 0 0 60px rgba(37,99,255,0.4), inset 0 0 40px rgba(0,229,255,0.15); }
}
@keyframes ring-spin {
  from { transform: rotate(0deg) rotateX(70deg); }
  to { transform: rotate(360deg) rotateX(70deg); }
}
.tour-label {
  font-family: 'Syne', sans-serif;
  font-size: 1.5rem;
  font-weight: 800;
  margin-bottom: 12px;
}
.tour-sub { font-size: 0.9rem; color: var(--muted); }
.tour-badge {
  display: inline-flex; align-items: center; gap: 6px;
  margin-top: 20px;
  padding: 8px 16px;
  background: rgba(0,229,255,0.1);
  border: 1px solid rgba(0,229,255,0.3);
  border-radius: 100px;
  font-size: 0.78rem;
  color: var(--accent);
  cursor: pointer;
  transition: background 0.3s;
}
.tour-badge:hover { background: rgba(0,229,255,0.2); }
.tour-hotspot {
  position: absolute;
  width: 12px; height: 12px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 0 4px rgba(0,229,255,0.2), 0 0 20px rgba(0,229,255,0.5);
  animation: hotspot-pulse 2s infinite;
  cursor: pointer;
  z-index: 3;
}
.tour-hotspot::after {
  content: attr(data-label);
  position: absolute; left: 20px; top: 50%;
  transform: translateY(-50%);
  background: rgba(8,13,20,0.9);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 4px 10px;
  font-size: 0.72rem;
  white-space: nowrap;
  backdrop-filter: blur(10px);
  opacity: 0;
  transition: opacity 0.3s;
}
.tour-hotspot:hover::after { opacity: 1; }
@keyframes hotspot-pulse {
  0%,100% { box-shadow: 0 0 0 4px rgba(0,229,255,0.2), 0 0 20px rgba(0,229,255,0.5); }
  50% { box-shadow: 0 0 0 8px rgba(0,229,255,0.1), 0 0 30px rgba(0,229,255,0.6); }
}

/* PROCESS */
#process {
  padding: 120px 0;
}
.process-header { text-align: center; }
.process-header .section-sub { margin: 0 auto 60px; }
.process-steps {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0;
  position: relative;
}
.process-steps::before {
  content: '';
  position: absolute;
  top: 32px; left: 12.5%; right: 12.5%;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--blue), var(--purple), var(--accent), transparent);
  z-index: 0;
}
.process-step {
  text-align: center;
  padding: 0 20px;
  position: relative;
  z-index: 1;
}
.step-num {
  width: 64px; height: 64px;
  border-radius: 50%;
  background: var(--dark2);
  border: 1px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  margin: 0 auto 24px;
  font-family: 'Syne', sans-serif;
  font-size: 1.2rem;
  font-weight: 800;
  position: relative;
  transition: border-color 0.3s, background 0.3s;
}
.process-step:hover .step-num {
  border-color: var(--blue);
  background: var(--glass2);
  box-shadow: 0 0 30px rgba(37,99,255,0.3);
}
.step-icon-wrap {
  position: absolute;
  top: -8px; right: -8px;
  width: 24px; height: 24px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--blue), var(--purple));
  display: flex; align-items: center; justify-content: center;
  font-size: 0.65rem;
}
.process-step h3 { font-size: 1.1rem; margin-bottom: 10px; }
.process-step p { font-size: 0.85rem; }

/* TESTIMONIALS */
#testimonials {
  padding: 120px 0;
  background: radial-gradient(ellipse 60% 40% at 50% 100%, rgba(37,99,255,0.07) 0%, transparent 70%);
}
.testi-header { text-align: center; }
.testi-header .section-sub { margin: 0 auto 60px; }
.testi-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.testi-card {
  background: var(--glass);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 32px 28px;
  transition: border-color 0.3s, transform 0.3s;
}
.testi-card:hover {
  border-color: rgba(37,99,255,0.3);
  transform: translateY(-4px);
}
.testi-stars { color: #fbbf24; font-size: 0.85rem; margin-bottom: 16px; letter-spacing: 2px; }
.testi-text {
  font-size: 0.9rem;
  line-height: 1.75;
  color: rgba(240,244,255,0.8);
  margin-bottom: 24px;
  font-style: italic;
}
.testi-author { display: flex; align-items: center; gap: 12px; }
.testi-avatar {
  width: 44px; height: 44px;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 1.1rem;
  font-weight: 700;
  font-family: 'Syne', sans-serif;
}
.testi-name { font-size: 0.9rem; font-weight: 600; color: var(--white); }
.testi-role { font-size: 0.78rem; color: var(--muted); }

/* FINAL CTA */
#cta {
  padding: 140px 0;
  text-align: center;
  position: relative;
}
#cta::before {
  content: '';
  position: absolute; inset: 0;
  background:
    radial-gradient(ellipse 60% 60% at 50% 50%, rgba(37,99,255,0.2) 0%, transparent 70%),
    radial-gradient(ellipse 40% 40% at 30% 30%, rgba(124,58,237,0.15) 0%, transparent 60%),
    radial-gradient(ellipse 40% 40% at 70% 70%, rgba(0,229,255,0.08) 0%, transparent 60%);
}
.cta-inner { position: relative; z-index: 1; }
.cta-tag {
  display: inline-block;
  padding: 6px 18px;
  background: rgba(0,229,255,0.1);
  border: 1px solid rgba(0,229,255,0.25);
  border-radius: 100px;
  font-size: 0.8rem;
  color: var(--accent);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 24px;
}
.cta-title { margin-bottom: 20px; }
.cta-sub { font-size: 1.05rem; color: var(--muted); max-width: 460px; margin: 0 auto 48px; }
.btn-wa {
  display: inline-flex; align-items: center; gap: 12px;
  padding: 20px 44px;
  background: linear-gradient(135deg, #25d366 0%, #128c7e 100%);
  border-radius: 100px;
  font-size: 1rem;
  font-weight: 600;
  color: #fff;
  transition: transform 0.3s, box-shadow 0.3s;
  box-shadow: 0 8px 40px rgba(37,211,102,0.4);
  font-family: 'Syne', sans-serif;
}
.btn-wa:hover { transform: translateY(-4px) scale(1.02); box-shadow: 0 16px 60px rgba(37,211,102,0.6); }
.btn-wa svg { width: 24px; height: 24px; }
.cta-note { font-size: 0.8rem; color: var(--muted); margin-top: 20px; }

/* FOOTER */
footer {
  border-top: 1px solid var(--border);
  padding: 60px 0 40px;
  background: var(--dark);
}
.footer-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr;
  gap: 50px;
  margin-bottom: 50px;
}
.footer-brand p {
  font-size: 0.88rem;
  max-width: 260px;
  margin-top: 14px;
  line-height: 1.7;
}
.footer-col h4 {
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--white);
  margin-bottom: 16px;
  font-family: 'Syne', sans-serif;
}
.footer-col a {
  display: block;
  font-size: 0.85rem;
  color: var(--muted);
  margin-bottom: 10px;
  transition: color 0.3s;
}
.footer-col a:hover { color: var(--white); }
.footer-bottom {
  display: flex; align-items: center; justify-content: space-between;
  border-top: 1px solid var(--border);
  padding-top: 28px;
}
.footer-copy { font-size: 0.82rem; color: var(--muted); }
.social-links { display: flex; gap: 12px; }
.social-link {
  width: 36px; height: 36px;
  border-radius: 50%;
  background: var(--glass);
  border: 1px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  font-size: 0.85rem;
  transition: background 0.3s, border-color 0.3s;
}
.social-link:hover { background: var(--glass2); border-color: rgba(37,99,255,0.4); }
.footer-wa {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 10px 22px;
  background: rgba(37,211,102,0.12);
  border: 1px solid rgba(37,211,102,0.3);
  border-radius: 100px;
  font-size: 0.82rem;
  color: #4ade80;
  transition: background 0.3s;
}
.footer-wa:hover { background: rgba(37,211,102,0.2); }

/* MOBILE MENU */
.mobile-menu {
  display: none;
  position: fixed; inset: 0;
  background: rgba(2,4,8,0.98);
  z-index: 999;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 32px;
  backdrop-filter: blur(20px);
}
.mobile-menu.open { display: flex; }
.mobile-menu a {
  font-family: 'Syne', sans-serif;
  font-size: 2rem;
  font-weight: 800;
  color: var(--white);
  transition: color 0.3s;
}
.mobile-menu a:hover { color: var(--blue-bright); }
.mobile-close {
  position: absolute; top: 24px; right: 24px;
  font-size: 1.5rem;
  cursor: pointer;
  color: var(--muted);
}

/* ANIMATIONS */
.fade-up {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.8s cubic-bezier(.23,1,.32,1), transform 0.8s cubic-bezier(.23,1,.32,1);
}
.fade-up.visible { opacity: 1; transform: translateY(0); }
.fade-up-d1 { transition-delay: 0.1s; }
.fade-up-d2 { transition-delay: 0.2s; }
.fade-up-d3 { transition-delay: 0.3s; }
.fade-up-d4 { transition-delay: 0.4s; }
.fade-up-d5 { transition-delay: 0.5s; }

/* RESPONSIVE */
@media (max-width: 1024px) {
  .hero-grid { grid-template-columns: 1fr; gap: 60px; }
  .hero-visual { height: 380px; }
  .tag1, .tag2, .tag3 { display: none; }
  .services-grid { grid-template-columns: repeat(2, 1fr); }
  .footer-grid { grid-template-columns: 1fr 1fr; gap: 36px; }
  .process-steps { grid-template-columns: repeat(2, 1fr); gap: 40px; }
  .process-steps::before { display: none; }
}
@media (max-width: 768px) {
  .nav-links, .nav-cta { display: none; }
  .hamburger { display: flex; }
  .trust-grid { grid-template-columns: repeat(2, 1fr); }
  .trust-item:nth-child(2)::after, .trust-item:nth-child(4)::after { display: none; }
  .trust-item:nth-child(1)::after, .trust-item:nth-child(3)::after { display: block; }
  .services-grid, .testi-grid { grid-template-columns: 1fr; }
  .why-grid { grid-template-columns: 1fr; gap: 40px; }
  .footer-grid { grid-template-columns: 1fr; }
  .footer-bottom { flex-direction: column; gap: 20px; text-align: center; }
  .hero-card-main { width: 280px; }
  cursor: auto;
}
@media (max-width: 480px) {
  .process-steps { grid-template-columns: 1fr; }
  .why-reasons { grid-template-columns: 1fr; }
  .hero-btns { flex-direction: column; }
  .btn-primary, .btn-secondary { text-align: center; justify-content: center; }
}
</style>
</head>
<body>

<!-- CURSOR -->
<div id="cursor"></div>
<div id="cursor-ring"></div>

<!-- NAV -->
<nav id="navbar">
  <div class="container nav-inner">
    <a href="#" class="logo">Grow<span>Sage</span></a>
    <ul class="nav-links">
      <li><a href="#services">Services</a></li>
      <li><a href="#why">Why Us</a></li>
      <li><a href="#tour">Virtual Tour</a></li>
      <li><a href="#process">Process</a></li>
      <li><a href="#testimonials">Reviews</a></li>
    </ul>
    <a href="https://wa.me/918823096017" target="_blank" class="nav-cta">
      <svg class="wa-icon" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
      WhatsApp Us
    </a>
    <div class="hamburger" id="hamburger">
      <span></span><span></span><span></span>
    </div>
  </div>
</nav>

<!-- MOBILE MENU -->
<div class="mobile-menu" id="mobileMenu">
  <div class="mobile-close" id="mobileClose">✕</div>
  <a href="#services" onclick="closeMobile()">Services</a>
  <a href="#why" onclick="closeMobile()">Why Us</a>
  <a href="#tour" onclick="closeMobile()">Virtual Tour</a>
  <a href="#process" onclick="closeMobile()">Process</a>
  <a href="#testimonials" onclick="closeMobile()">Reviews</a>
  <a href="https://wa.me/918823096017" target="_blank">WhatsApp Us ↗</a>
</div>

<!-- HERO -->
<section id="hero">
  <div class="container">
    <div class="hero-grid">
      <div class="hero-content">
        <div class="hero-badge fade-up">
          <span class="badge-dot"></span>
          Premium Digital Agency · India
        </div>
        <h1 class="hero-title fade-up fade-up-d1">
          Grow Faster.<br>Look <em>Smarter.</em><br>Sell More.
        </h1>
        <p class="hero-sub fade-up fade-up-d2">We build brands that stop thumbs, fill inboxes, and close deals — with strategy, design, and technology that actually works.</p>
        <div class="hero-btns fade-up fade-up-d3">
          <a href="https://wa.me/918823096017" target="_blank" class="btn-primary">
            <svg class="wa-icon" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
            Book Free Consultation
          </a>
          <a href="#services" class="btn-secondary">
            View Services →
          </a>
        </div>
      </div>
      <div class="hero-visual fade-up fade-up-d2">
        <div class="hero-orb orb1"></div>
        <div class="hero-orb orb2"></div>
        <div class="hero-orb orb3"></div>
        <div class="hero-card-main">
          <div class="card-header">
            <div class="card-avatar">🚀</div>
            <div class="card-info">
              <h4>Brand Growth Dashboard</h4>
              <p>GrowSage Analytics · Live</p>
            </div>
          </div>
          <div class="card-metric">
            <div class="metric-item">
              <span class="metric-val">340%</span>
              <span class="metric-lbl">Engagement</span>
            </div>
            <div class="metric-item">
              <span class="metric-val">12K</span>
              <span class="metric-lbl">New Reach</span>
            </div>
            <div class="metric-item">
              <span class="metric-val">98%</span>
              <span class="metric-lbl">Satisfaction</span>
            </div>
          </div>
          <div class="card-bar-label">Monthly Growth Rate</div>
          <div class="card-bar"><div class="card-bar-fill"></div></div>
        </div>
        <div class="floating-tag tag1"><span class="tag-dot green"></span>Campaigns Live</div>
        <div class="floating-tag tag2"><span class="tag-dot orange"></span>3 Clients Onboarded</div>
        <div class="floating-tag tag3"><span class="tag-dot blue"></span>360° Tour Ready</div>
      </div>
    </div>
  </div>
</section>

<!-- TRUST -->
<section id="trust">
  <div class="container">
    <div class="trust-grid">
      <div class="trust-item fade-up">
        <span class="trust-num" data-target="150">0+</span>
        <span class="trust-lbl">Projects Completed</span>
      </div>
      <div class="trust-item fade-up fade-up-d1">
        <span class="trust-num" data-target="80">0+</span>
        <span class="trust-lbl">Happy Clients</span>
      </div>
      <div class="trust-item fade-up fade-up-d2">
        <span class="trust-num" data-target="340">0%</span>
        <span class="trust-lbl">Avg. Engagement Growth</span>
      </div>
      <div class="trust-item fade-up fade-up-d3">
        <span class="trust-num" data-target="30">0+</span>
        <span class="trust-lbl">Brands Worked With</span>
      </div>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="container">
    <div class="services-header">
      <div class="section-label">What We Do</div>
      <h2 class="section-title fade-up">Weapons for Your<br>Brand's Growth</h2>
      <p class="section-sub fade-up fade-up-d1">Six high-impact services designed to make your brand impossible to ignore — across every screen, platform, and space.</p>
    </div>
    <div class="services-grid">
      <div class="service-card fade-up">
        <div class="service-icon">📈</div>
        <h3>Social Media Marketing</h3>
        <p>Data-driven campaigns that put your brand in front of the right audience at exactly the right moment — turning impressions into revenue.</p>
        <div class="service-arrow">→</div>
      </div>
      <div class="service-card fade-up fade-up-d1">
        <div class="service-icon">🎯</div>
        <h3>Social Media Management</h3>
        <p>Consistent, on-brand content. Community building. Reputation management. We handle your social presence so you can focus on business.</p>
        <div class="service-arrow">→</div>
      </div>
      <div class="service-card fade-up fade-up-d2">
        <div class="service-icon">🌐</div>
        <h3>360° Virtual Tours</h3>
        <p>Immersive, interactive walkthroughs that let customers explore your space before stepping inside. Perfect for real estate, restaurants & institutes.</p>
        <div class="service-arrow">→</div>
      </div>
      <div class="service-card fade-up fade-up-d1">
        <div class="service-icon">💻</div>
        <h3>Website Development</h3>
        <p>Fast, conversion-optimized websites that look premium and perform on every device. Built to rank, built to convert, built to impress.</p>
        <div class="service-arrow">→</div>
      </div>
      <div class="service-card fade-up fade-up-d2">
        <div class="service-icon">✦</div>
        <h3>UI/UX Design</h3>
        <p>Interfaces that feel effortless and look extraordinary. We design experiences that users love and brands are proud of — from wireframe to launch.</p>
        <div class="service-arrow">→</div>
      </div>
      <div class="service-card fade-up fade-up-d3">
        <div class="service-icon">🎬</div>
        <h3>Video Editing</h3>
        <p>Cinematic edits, reels, brand films, and ads that stop the scroll. Storytelling through visuals that create emotion and drive action.</p>
        <div class="service-arrow">→</div>
      </div>
    </div>
  </div>
</section>

<!-- WHY US -->
<section id="why">
  <div class="container">
    <div class="why-grid">
      <div>
        <div class="section-label">Why GrowSage</div>
        <h2 class="section-title fade-up">We Don't Just<br>Deliver. We Deliver <em style="font-style:normal;background:linear-gradient(135deg,var(--blue-bright),var(--purple-bright));-webkit-background-clip:text;-webkit-text-fill-color:transparent;">Results.</em></h2>
        <p style="color:var(--muted);font-size:0.95rem;line-height:1.8;margin-top:16px;">Most agencies overpromise and underdeliver. We let our numbers speak. Every project is treated like our most important one — because it is.</p>
        <a href="https://wa.me/918823096017" target="_blank" class="btn-primary" style="display:inline-flex;margin-top:36px;">Let's Talk Strategy →</a>
      </div>
      <div class="why-reasons">
        <div class="why-card fade-up">
          <span class="why-icon">⚡</span>
          <h4>Fast Delivery</h4>
          <p style="font-size:0.82rem;">Rapid turnarounds without sacrificing an ounce of quality.</p>
        </div>
        <div class="why-card fade-up fade-up-d1">
          <span class="why-icon">🧠</span>
          <h4>Creative Strategy</h4>
          <p style="font-size:0.82rem;">Every move is intentional, backed by research and insight.</p>
        </div>
        <div class="why-card fade-up fade-up-d2">
          <span class="why-icon">🤖</span>
          <h4>AI-Powered Workflow</h4>
          <p style="font-size:0.82rem;">We leverage the latest AI tools for smarter, faster execution.</p>
        </div>
        <div class="why-card fade-up fade-up-d3">
          <span class="why-icon">💎</span>
          <h4>Premium Quality</h4>
          <p style="font-size:0.82rem;">High-end output at every level — design, copy, and strategy.</p>
        </div>
        <div class="why-card fade-up fade-up-d1">
          <span class="why-icon">📊</span>
          <h4>Result Driven</h4>
          <p style="font-size:0.82rem;">We measure success in real metrics: leads, sales, and growth.</p>
        </div>
        <div class="why-card fade-up fade-up-d2">
          <span class="why-icon">📱</span>
          <h4>Mobile Optimized</h4>
          <p style="font-size:0.82rem;">Everything we build performs flawlessly on every device.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- 360 TOUR -->
<section id="tour">
  <div class="container">
    <div style="text-align:center;margin-bottom:48px;">
      <div class="section-label">Immersive Experience</div>
      <h2 class="section-title fade-up">Step Inside Before<br>You <em style="font-style:normal;background:linear-gradient(135deg,var(--accent),var(--blue-bright));-webkit-background-clip:text;-webkit-text-fill-color:transparent;">Walk In</em></h2>
      <p class="section-sub fade-up fade-up-d1" style="margin:0 auto;">Our 360° virtual tours give your customers a fully immersive preview of your space — from anywhere in the world.</p>
    </div>
    <div class="tour-showcase fade-up">
      <div class="tour-bg"></div>
      <div class="tour-grid-lines"></div>
      <div class="tour-hotspot" style="top:30%;left:25%;" data-label="Living Room"></div>
      <div class="tour-hotspot" style="top:55%;right:28%;" data-label="Kitchen Area"></div>
      <div class="tour-hotspot" style="bottom:25%;left:40%;" data-label="Master Suite"></div>
      <div class="tour-center">
        <div class="tour-sphere" title="360° Interactive Tour"></div>
        <div class="tour-label">360° Interactive Experience</div>
        <div class="tour-sub">Drag · Explore · Experience</div>
        <a href="https://wa.me/918823096017" target="_blank" class="tour-badge">
          🌐 Get a Tour for Your Business
        </a>
      </div>
    </div>
    <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:20px;">
      <div style="background:var(--glass);border:1px solid var(--border);border-radius:var(--radius-sm);padding:24px;text-align:center;">
        <div style="font-size:1.8rem;margin-bottom:10px;">🏠</div>
        <h4 style="font-size:0.95rem;margin-bottom:6px;">Real Estate</h4>
        <p style="font-size:0.82rem;">Let buyers tour properties remotely and make confident decisions faster.</p>
      </div>
      <div style="background:var(--glass);border:1px solid var(--border);border-radius:var(--radius-sm);padding:24px;text-align:center;">
        <div style="font-size:1.8rem;margin-bottom:10px;">🍽️</div>
        <h4 style="font-size:0.95rem;margin-bottom:6px;">Restaurants</h4>
        <p style="font-size:0.82rem;">Show off your ambiance and fill tables before guests even arrive.</p>
      </div>
      <div style="background:var(--glass);border:1px solid var(--border);border-radius:var(--radius-sm);padding:24px;text-align:center;">
        <div style="font-size:1.8rem;margin-bottom:10px;">🎓</div>
        <h4 style="font-size:0.95rem;margin-bottom:6px;">Institutes</h4>
        <p style="font-size:0.82rem;">Give prospective students an immersive campus experience from anywhere.</p>
      </div>
    </div>
  </div>
</section>

<!-- PROCESS -->
<section id="process">
  <div class="container">
    <div class="process-header">
      <div class="section-label">How We Work</div>
      <h2 class="section-title fade-up">From Idea to<br>Impact in 4 Steps</h2>
      <p class="section-sub fade-up fade-up-d1">A clear, battle-tested process that eliminates guesswork and gets your brand moving forward — fast.</p>
    </div>
    <div class="process-steps">
      <div class="process-step fade-up">
        <div class="step-num">
          01
          <div class="step-icon-wrap">🔍</div>
        </div>
        <h3>Discovery</h3>
        <p style="font-size:0.85rem;">Deep dive into your brand, goals, audience, and competitors to uncover real opportunities.</p>
      </div>
      <div class="process-step fade-up fade-up-d1">
        <div class="step-num">
          02
          <div class="step-icon-wrap">🧭</div>
        </div>
        <h3>Strategy</h3>
        <p style="font-size:0.85rem;">A tailored game plan — content, channels, timelines, and KPIs — built around your specific goals.</p>
      </div>
      <div class="process-step fade-up fade-up-d2">
        <div class="step-num">
          03
          <div class="step-icon-wrap">⚙️</div>
        </div>
        <h3>Execution</h3>
        <p style="font-size:0.85rem;">Flawless delivery. Designs, campaigns, and content that look premium and perform powerfully.</p>
      </div>
      <div class="process-step fade-up fade-up-d3">
        <div class="step-num">
          04
          <div class="step-icon-wrap">📈</div>
        </div>
        <h3>Growth</h3>
        <p style="font-size:0.85rem;">Ongoing optimization and reporting to scale what works and double down on real results.</p>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials">
  <div class="container">
    <div class="testi-header">
      <div class="section-label">Client Stories</div>
      <h2 class="section-title fade-up">Real Brands.<br>Real Results.</h2>
      <p class="section-sub fade-up fade-up-d1">Don't just take our word for it — hear from the businesses we've helped grow.</p>
    </div>
    <div class="testi-grid">
      <div class="testi-card fade-up">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-text">"GrowSage completely transformed our restaurant's social presence. Our Instagram went from 800 to 12,000 followers in 3 months, and our tables are booked every weekend. Worth every rupee."</p>
        <div class="testi-author">
          <div class="testi-avatar" style="background:linear-gradient(135deg,#2563ff,#7c3aed);">R</div>
          <div>
            <div class="testi-name">Rahul Mehra</div>
            <div class="testi-role">Owner, Mehra's Kitchen · Indore</div>
          </div>
        </div>
      </div>
      <div class="testi-card fade-up fade-up-d1">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-text">"The 360° virtual tour they created for our institute brought in 3x more inquiries. Parents and students can now explore our campus before visiting. Truly innovative."</p>
        <div class="testi-author">
          <div class="testi-avatar" style="background:linear-gradient(135deg,#7c3aed,#a855f7);">P</div>
          <div>
            <div class="testi-name">Priya Sharma</div>
            <div class="testi-role">Director, Apex Academy</div>
          </div>
        </div>
      </div>
      <div class="testi-card fade-up fade-up-d2">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-text">"Our new website by GrowSage is stunning. We had 40 leads in the first week of launch. The design is exactly what I envisioned — premium, fast, and converts like crazy."</p>
        <div class="testi-author">
          <div class="testi-avatar" style="background:linear-gradient(135deg,#00e5ff,#2563ff);">A</div>
          <div>
            <div class="testi-name">Arjun Patel</div>
            <div class="testi-role">Founder, Patel Realty Group</div>
          </div>
        </div>
      </div>
      <div class="testi-card fade-up fade-up-d1">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-text">"As a personal brand and coach, I needed help standing out. GrowSage's content strategy and reels doubled my YouTube subscribers and helped me sell out my course in 72 hours."</p>
        <div class="testi-author">
          <div class="testi-avatar" style="background:linear-gradient(135deg,#f97316,#ea580c);">S</div>
          <div>
            <div class="testi-name">Sneha Rajput</div>
            <div class="testi-role">Business Coach · 45K Followers</div>
          </div>
        </div>
      </div>
      <div class="testi-card fade-up fade-up-d2">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-text">"GrowSage delivered a premium UI/UX design for our app that our investors loved. The team is highly responsive, creative, and actually understands business — not just design."</p>
        <div class="testi-author">
          <div class="testi-avatar" style="background:linear-gradient(135deg,#22c55e,#16a34a);">V</div>
          <div>
            <div class="testi-name">Varun Joshi</div>
            <div class="testi-role">CEO, NestStart Technologies</div>
          </div>
        </div>
      </div>
      <div class="testi-card fade-up fade-up-d3">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-text">"Our café's brand videos by GrowSage went viral locally. Over 2 lakh views in a week, 500 new followers daily, and we had to hire 3 new staff to manage the rush. Unreal results."</p>
        <div class="testi-author">
          <div class="testi-avatar" style="background:linear-gradient(135deg,#ec4899,#9333ea);">N</div>
          <div>
            <div class="testi-name">Nisha Kapoor</div>
            <div class="testi-role">Owner, Brew & Bloom Café</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FINAL CTA -->
<section id="cta">
  <div class="container">
    <div class="cta-inner">
      <div class="cta-tag fade-up">Limited Slots Available This Month</div>
      <h2 class="cta-title fade-up">Ready to Grow<br>Your Brand?</h2>
      <p class="cta-sub fade-up fade-up-d1">Join 80+ businesses that chose GrowSage to grow their digital presence. Book a free strategy call today — no commitment, just clarity.</p>
      <a href="https://wa.me/918823096017" target="_blank" class="btn-wa fade-up fade-up-d2">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
        Chat on WhatsApp — It's Free
      </a>
      <p class="cta-note fade-up">⚡ Typically responds within 15 minutes · No spam · Cancel anytime</p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="container">
    <div class="footer-grid">
      <div class="footer-brand">
        <div class="logo" style="font-size:1.8rem;">Grow<span>Sage</span></div>
        <p>A premium digital agency helping local businesses, coaches, institutes, and startups grow their brand — faster and smarter.</p>
        <a href="https://wa.me/918823096017" target="_blank" class="footer-wa" style="display:inline-flex;margin-top:20px;align-items:center;gap:8px;">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
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
        <a href="https://wa.me/918823096017" target="_blank">Social Media Management</a>
        <a href="https://wa.me/918823096017" target="_blank">360° Virtual Tours</a>
        <a href="https://wa.me/918823096017" target="_blank">Website Development</a>
        <a href="https://wa.me/918823096017" target="_blank">UI/UX Design</a>
        <a href="https://wa.me/918823096017" target="_blank">Video Editing</a>
      </div>
      <div class="footer-col">
        <h4>We Serve</h4>
        <a href="#">Local Businesses</a>
        <a href="#">Coaches & Educators</a>
        <a href="#">Institutes & Academies</a>
        <a href="#">Restaurants & Cafés</a>
        <a href="#">Real Estate Brands</a>
        <a href="#">Personal Brands</a>
      </div>
    </div>
    <div class="footer-bottom">
      <p class="footer-copy">© 2024 GrowSage Digital Agency. All rights reserved.</p>
      <div class="social-links">
        <a href="#" class="social-link" title="Instagram">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor" stroke="none"/></svg>
        </a>
        <a href="#" class="social-link" title="Facebook">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M18 2h-3a5 5 0 00-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 011-1h3z"/></svg>
        </a>
        <a href="#" class="social-link" title="LinkedIn">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        </a>
        <a href="https://wa.me/918823096017" target="_blank" class="social-link" title="WhatsApp">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
        </a>
      </div>
    </div>
  </div>
</footer>

<script>
// CURSOR
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursor-ring');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  cursor.style.transform = `translate(${mx - 6}px, ${my - 6}px)`;
});
function animateRing() {
  rx += (mx - rx - 18) * 0.12;
  ry += (my - ry - 18) * 0.12;
  ring.style.transform = `translate(${rx}px, ${ry}px)`;
  requestAnimationFrame(animateRing);
}
animateRing();
document.querySelectorAll('a, button, .service-card, .why-card, .testi-card').forEach(el => {
  el.addEventListener('mouseenter', () => {
    cursor.style.transform += ' scale(2)';
    ring.style.width = '60px'; ring.style.height = '60px';
    ring.style.opacity = '0.5';
  });
  el.addEventListener('mouseleave', () => {
    ring.style.width = '36px'; ring.style.height = '36px';
    ring.style.opacity = '1';
  });
});

// NAV SCROLL
const nav = document.getElementById('navbar');
window.addEventListener('scroll', () => {
  nav.classList.toggle('scrolled', window.scrollY > 40);
});

// HAMBURGER
const hamburger = document.getElementById('hamburger');
const mobileMenu = document.getElementById('mobileMenu');
const mobileClose = document.getElementById('mobileClose');
hamburger.addEventListener('click', () => mobileMenu.classList.add('open'));
mobileClose.addEventListener('click', () => mobileMenu.classList.remove('open'));
function closeMobile() { mobileMenu.classList.remove('open'); }

// INTERSECTION OBSERVER - fade up
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.12 });
document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

// COUNTER ANIMATION
const counters = document.querySelectorAll('.trust-num[data-target]');
const counterObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const el = entry.target;
      const target = parseInt(el.dataset.target);
      const suffix = el.textContent.includes('%') ? '%' : '+';
      let current = 0;
      const step = target / 60;
      const timer = setInterval(() => {
        current += step;
        if (current >= target) {
          current = target;
          clearInterval(timer);
        }
        el.textContent = Math.floor(current) + suffix;
      }, 25);
      counterObserver.unobserve(el);
    }
  });
}, { threshold: 0.5 });
counters.forEach(c => counterObserver.observe(c));
</script>
</body>
</html>
