
<html lang="ckb" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CRAVA</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Kufi+Arabic:wght@500;700;800;900&family=Vazirmatn:wght@400;500;600;700&display=swap" rel="stylesheet">

<style>
:root{
  --forest:        #1B4D2E;
  --forest-dark:   #0F2116;
  --forest-light:  #2E6E45;
  --gold:          #F5A623;
  --gold-light:    #FFC94A;
  --gold-deep:     #D98812;
  --cream:         #FFF8E9;
  --cream-2:       #FCEFD2;
  --ink:           #10160F;
  --ink-2:         #171F16;
  --white:         #FFFFFF;
  --text-dark:     #1C2318;
  --text-muted:    #5B6355;

  --font-display: 'Noto Kufi Arabic', 'Vazirmatn', sans-serif;
  --font-body:    'Vazirmatn', 'Noto Kufi Arabic', sans-serif;

  --radius-lg: 34px;
  --radius-md: 26px;
  --radius-sm: 18px;
  --radius-pill: 999px;

  --ease: cubic-bezier(.22,1,.36,1);

  /* Liquid Glass materials */
  --glass-light-fill: rgba(255,255,255,.62);
  --glass-light-fill-strong: rgba(255,255,255,.8);
  --glass-light-border: rgba(255,255,255,.75);
  --glass-dark-fill: rgba(255,255,255,.08);
  --glass-dark-fill-strong: rgba(255,255,255,.14);
  --glass-dark-border: rgba(255,255,255,.18);
  --glass-blur: blur(26px) saturate(180%);
  --glass-blur-soft: blur(18px) saturate(160%);
  --glass-shadow-light: 0 20px 50px -18px rgba(15,33,22,.28), inset 0 1px 0 rgba(255,255,255,.85), inset 0 -1px 0 rgba(255,255,255,.2);
  --glass-shadow-dark: 0 24px 60px -20px rgba(0,0,0,.5), inset 0 1px 0 rgba(255,255,255,.16), inset 0 -1px 0 rgba(0,0,0,.2);
  --glass-highlight: linear-gradient(180deg, rgba(255,255,255,.55) 0%, rgba(255,255,255,0) 40%);
}

*,*::before,*::after{ box-sizing:border-box; margin:0; padding:0; }
html{ scroll-behavior:smooth; }
body{
  font-family: var(--font-body);
  background:
    radial-gradient(720px 480px at 12% 0%, rgba(46,110,69,.14), transparent 60%),
    radial-gradient(680px 460px at 92% 18%, rgba(245,166,35,.16), transparent 60%),
    var(--cream);
  color: var(--text-dark);
  overflow-x: hidden;
  line-height: 1.6;
}
img{ max-width:100%; display:block; }
a{ color:inherit; text-decoration:none; }
ul{ list-style:none; }
button{ font-family:inherit; cursor:pointer; }
h1,h2,h3,h4,h5{ font-family: var(--font-display); line-height:1.25; }

@media (prefers-reduced-motion: reduce){
  *{ animation-duration:0.01ms !important; animation-iteration-count:1 !important; transition-duration:0.01ms !important; scroll-behavior:auto !important; }
}

.grain{
  position:fixed; inset:0; pointer-events:none; z-index:9999;
  opacity:.035; mix-blend-mode:overlay;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}

/* ================= PRELOADER ================= */
#preloader {
  position: fixed;
  inset: 0;
  z-index: 999999;
  background: var(--ink);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  transition: opacity 0.6s var(--ease), visibility 0.6s var(--ease);
}
#preloader.loaded {
  opacity: 0;
  visibility: hidden;
}
.loader-logo {
  width: 100px;
  height: auto;
  margin-bottom: 24px;
  animation: pulse 1.2s infinite alternate var(--ease);
}
.loader-spinner {
  width: 44px;
  height: 44px;
  border: 3px solid rgba(245, 166, 35, 0.2);
  border-top-color: var(--gold);
  border-radius: 50%;
  animation: spin 1s linear infinite;
}
@keyframes pulse {
  0% { transform: scale(0.9); opacity: 0.8; }
  100% { transform: scale(1.1); opacity: 1; }
}
@keyframes spin {
  to { transform: rotate(360deg); }
}

/* Header */
.site-header{
  position:fixed; inset-inline:0; top:0; z-index:1000;
  padding:18px 20px 0;
  transition: padding .35s var(--ease);
}
.site-header.scrolled{
  padding:10px 20px 0;
}
.header-inner{
  max-width:1240px; margin:0 auto; padding:10px 22px;
  display:flex; align-items:center; justify-content:space-between;
  background: var(--glass-dark-fill);
  -webkit-backdrop-filter: var(--glass-blur);
  backdrop-filter: var(--glass-blur);
  border:1px solid var(--glass-dark-border);
  border-radius: var(--radius-pill);
  box-shadow: var(--glass-shadow-dark);
  transition: background .35s var(--ease), padding .35s var(--ease), box-shadow .35s var(--ease);
}
.site-header.scrolled .header-inner{
  background: var(--glass-dark-fill-strong);
  padding:8px 22px;
  box-shadow: 0 14px 40px -14px rgba(0,0,0,.55), inset 0 1px 0 rgba(255,255,255,.2);
}
.brand-logo{ height:40px; width:auto; transition: height .35s var(--ease); border-radius:12px; }
.site-header.scrolled .brand-logo{ height:32px; }

.main-nav{ display:flex; gap:32px; }
.main-nav a{
  font-weight:600; font-size:15px; color:var(--white);
  position:relative; padding:6px 2px;
}
.main-nav a::after{
  content:""; position:absolute; inset-inline:0; bottom:-2px; height:2px;
  background: linear-gradient(90deg,var(--gold),var(--gold-light));
  transform:scaleX(0); transform-origin:right;
  transition: transform .35s var(--ease);
}
.main-nav a:hover::after{ transform:scaleX(1); }

.menu-toggle{
  display:none; flex-direction:column; align-items:center; justify-content:center; gap:5px;
  width:40px; height:40px; border-radius:50%;
  background: rgba(255,255,255,.08); border:1px solid rgba(255,255,255,.16);
  z-index:1100;
}
.menu-toggle span{ width:26px; height:2.5px; background:var(--white); border-radius:2px; transition: all .3s var(--ease); }
.menu-toggle.open span:nth-child(1){ transform:translateY(7.5px) rotate(45deg); }
.menu-toggle.open span:nth-child(2){ opacity:0; }
.menu-toggle.open span:nth-child(3){ transform:translateY(-7.5px) rotate(-45deg); }

/* Hero */
.hero{
  position:relative; min-height:100svh;
  display:flex; flex-direction:column; justify-content:center;
  background: radial-gradient(ellipse at 50% -10%, #1c3324 0%, var(--ink) 55%, var(--ink) 100%);
  overflow:hidden;
  padding: 140px 24px 60px;
  text-align:center;
}
.hero-glow{
  position:absolute; border-radius:50%; filter:blur(90px); pointer-events:none;
  opacity:.5;
}
.glow-green{ width:520px; height:520px; background:var(--forest-light); top:-160px; inset-inline-start:-120px; animation: drift 14s ease-in-out infinite; }
.glow-gold{ width:460px; height:460px; background:var(--gold); bottom:-160px; inset-inline-end:-100px; animation: drift 16s ease-in-out infinite reverse; }
@keyframes drift{
  0%,100%{ transform:translate(0,0) scale(1); }
  50%{ transform:translate(30px,-20px) scale(1.08); }
}

.floaters{ position:absolute; inset:0; pointer-events:none; }
.floater{ position:absolute; font-size:34px; opacity:.55; filter:drop-shadow(0 6px 10px rgba(0,0,0,.35)); animation: float-y 7s ease-in-out infinite; }
.f1{ top:18%; inset-inline-start:10%; animation-delay:0s; }
.f2{ top:65%; inset-inline-start:16%; animation-delay:1.2s; font-size:28px; }
.f3{ top:24%; inset-inline-end:12%; animation-delay:.6s; font-size:30px; }
.f4{ top:70%; inset-inline-end:18%; animation-delay:1.8s; }
.f5{ top:45%; inset-inline-start:4%; animation-delay:2.4s; font-size:26px; }
@keyframes float-y{
  0%,100%{ transform:translateY(0) rotate(0deg); }
  50%{ transform:translateY(-26px) rotate(-8deg); }
}

.hero-inner{ position:relative; z-index:2; max-width:100%; padding:0 16px; margin:auto 0; }
.hero-logo{ height:76px; width:auto; margin:0 auto 28px; }

.eyebrow{
  color:var(--gold-light); font-weight:600; letter-spacing:.4px; margin-bottom:18px; font-size:15px;
}
.hero-title{
  color:var(--white); font-size:clamp(32px,6vw,58px); font-weight:900; margin-bottom:20px;
}
.accent-text{
  background: linear-gradient(90deg,var(--gold-light),var(--gold));
  -webkit-background-clip:text; background-clip:text; color:transparent;
}
.hero-sub{
  color:#D9DED4; font-size:17px; max-width:560px; margin:0 auto 36px;
}
.hero-actions{ display:flex; gap:16px; justify-content:center; flex-wrap:wrap; margin-bottom:40px; }

.btn{
  position:relative;
  display:inline-flex; align-items:center; gap:10px;
  padding:15px 30px; border-radius:var(--radius-pill); font-weight:700; font-size:15px;
  isolation:isolate; overflow:hidden;
  transition: transform .3s var(--ease), box-shadow .3s var(--ease), background .3s var(--ease);
}
.btn::before{
  content:""; position:absolute; inset:0; z-index:-1;
  background: var(--glass-highlight);
  opacity:.7; pointer-events:none;
}
.btn-primary{
  background: linear-gradient(160deg,var(--gold-light),var(--gold) 55%,var(--gold-deep));
  color:var(--ink);
  box-shadow: 0 12px 30px -8px rgba(245,166,35,.65), inset 0 1px 0 rgba(255,255,255,.6), inset 0 -2px 6px rgba(150,90,0,.25);
}
.btn-primary svg{ transform:rotate(-90deg); }
.btn-primary:hover{ transform:translateY(-3px); box-shadow:0 18px 40px -10px rgba(245,166,35,.8), inset 0 1px 0 rgba(255,255,255,.65); }
.btn-ghost{
  border:1px solid rgba(255,255,255,.4); color:var(--white);
  background: rgba(255,255,255,.08);
  -webkit-backdrop-filter: var(--glass-blur-soft);
  backdrop-filter: var(--glass-blur-soft);
  box-shadow: inset 0 1px 0 rgba(255,255,255,.25);
}
.btn-ghost:hover{ background:rgba(255,255,255,.16); transform:translateY(-3px); }

/* Quick Navigation Cards */
.quick-nav-cards {
  position: relative;
  z-index: 2;
  max-width: 1000px;
  margin: 20px auto 0;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 14px;
  padding: 0 16px;
}
.quick-card {
  position: relative;
  background: var(--glass-dark-fill);
  border: 1px solid var(--glass-dark-border);
  -webkit-backdrop-filter: var(--glass-blur);
  backdrop-filter: var(--glass-blur);
  border-radius: var(--radius-md);
  padding: 14px 16px;
  display: flex;
  align-items: center;
  gap: 12px;
  text-align: right;
  box-shadow: var(--glass-shadow-dark);
  overflow: hidden;
  transition: transform .3s var(--ease), background .3s var(--ease), border-color .3s var(--ease), box-shadow .3s var(--ease);
}
.quick-card::before{
  content:""; position:absolute; inset:0 0 auto 0; height:50%;
  background: linear-gradient(180deg, rgba(255,255,255,.16), rgba(255,255,255,0));
  pointer-events:none;
}
.quick-card:hover {
  transform: translateY(-5px);
  background: var(--glass-dark-fill-strong);
  border-color: rgba(245,166,35,.55);
  box-shadow: 0 16px 40px -12px rgba(0,0,0,.45), inset 0 1px 0 rgba(255,255,255,.25);
}
.quick-card-icon {
  width: 42px;
  height: 42px;
  border-radius: 14px;
  overflow: hidden;
  background: rgba(255,255,255,0.12);
  border: 1px solid rgba(255,255,255,.18);
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}
.quick-card-icon img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform .4s var(--ease);
}
.quick-card:hover .quick-card-icon img {
  transform: scale(1.1);
}
.quick-card-info h4 {
  color: var(--white);
  font-size: 14px;
  font-weight: 700;
  margin-bottom: 2px;
}
.quick-card-info p {
  color: #C9D1C3;
  font-size: 11px;
}

/* Wave Dividers & Section Shells */
.wave-divider{ line-height:0; margin-top:-2px; }
.wave-divider svg{ width:100%; height:60px; display:block; }
.wave-into-dark{ margin-top:-2px; }

.section-inner{ max-width:1240px; margin:0 auto; padding:90px 24px; }
.section-head{ max-width:640px; margin-bottom:46px; }
.section-head.light{ color:var(--white); }
.kicker{
  color:var(--gold-light); font-weight:700; font-size:14px; letter-spacing:.3px; margin-bottom:10px;
}
.section-head.light .kicker{ color:var(--gold-light); }
.section-title{ font-size:clamp(28px,4vw,42px); font-weight:800; margin-bottom:14px; color:var(--white); }
.section-head.light .section-title{ color:var(--white); }
.section-desc{ color:#C9D1C3; font-size:16px; }
.section-head.light .section-desc{ color:#C9D1C3; }

/* Item photos */
.item-photo{
  width:100%; aspect-ratio:1/1; border-radius:20px; overflow:hidden;
  margin-bottom:14px; background:var(--cream-2);
  border:1px solid rgba(27,77,46,.08);
}
.item-photo img{
  width:100%; height:100%; object-fit:cover; display:block;
  transition: transform .5s var(--ease);
}
.item-photo-fries{
  width:64px; height:64px; aspect-ratio:auto; border-radius:16px;
  margin-bottom:0; flex-shrink:0; background:rgba(255,255,255,.06);
  border:1px solid rgba(255,255,255,.1);
}
.fries-card:hover .item-photo-fries img{ transform:scale(1.1); }

/* Juices */
.juices{ background:var(--forest-dark); position:relative; }

.juice-tabs {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-bottom: 40px;
  flex-wrap: wrap;
}
.tab-btn {
  background: var(--glass-dark-fill);
  border: 1px solid var(--glass-dark-border);
  -webkit-backdrop-filter: var(--glass-blur-soft);
  backdrop-filter: var(--glass-blur-soft);
  color: var(--white);
  padding: 10px 24px;
  border-radius: 999px;
  font-size: 15px;
  font-weight: 700;
  box-shadow: inset 0 1px 0 rgba(255,255,255,.12);
  transition: all .3s var(--ease);
}
.tab-btn:hover {
  background: var(--glass-dark-fill-strong);
}
.tab-btn.active {
  background: linear-gradient(160deg,var(--gold-light),var(--gold-deep));
  color: var(--ink);
  border-color: var(--gold);
  box-shadow: 0 8px 22px -6px rgba(245, 166, 35, 0.55), inset 0 1px 0 rgba(255,255,255,.6);
}

.juice-category {
  display: none;
  animation: fadeIn .4s var(--ease);
}
.juice-category.active {
  display: block;
}
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(15px); }
  to { opacity: 1; transform: translateY(0); }
}

.juice-grid{
  display:grid; grid-template-columns:repeat(5,1fr); gap:18px;
}
.fruit-bowl-grid{
  display:grid; grid-template-columns:repeat(4,1fr); gap:18px;
}
.juice-card{
  position:relative; isolation:isolate; overflow:hidden;
  background: var(--glass-light-fill);
  -webkit-backdrop-filter: var(--glass-blur);
  backdrop-filter: var(--glass-blur);
  border-radius:var(--radius-md); padding:26px 18px;
  text-align:center; border:1px solid var(--glass-light-border);
  display:flex; flex-direction:column;
  box-shadow: var(--glass-shadow-light);
  transition: transform .35s var(--ease), box-shadow .35s var(--ease), border-color .35s var(--ease), background .35s var(--ease);
}
.juice-card::before{
  content:""; position:absolute; inset:0 0 auto 0; height:46%; z-index:-1;
  background: var(--glass-highlight); pointer-events:none;
}
.juice-card:hover{
  transform:translateY(-8px) scale(1.02);
  background: var(--glass-light-fill-strong);
  box-shadow:0 26px 50px -20px rgba(27,77,46,.45), inset 0 1px 0 rgba(255,255,255,.9);
  border-color:var(--gold);
}
.juice-card:hover .item-photo img{ transform:scale(1.12) rotate(-2deg); }
.juice-card h4{ font-size:15px; color:var(--text-dark); margin-bottom:10px; font-weight:700; min-height:40px; }
.juice-card .price{
  display:inline-block; font-weight:700; color:var(--forest); font-size:14px;
  background:var(--cream-2); padding:5px 14px; border-radius:999px; margin-top: auto;
}
.juice-card.featured{
  background: linear-gradient(160deg, rgba(46,110,69,.85), rgba(15,33,22,.9));
  -webkit-backdrop-filter: var(--glass-blur);
  backdrop-filter: var(--glass-blur);
  color:var(--white);
  border-color: rgba(245,166,35,.4);
}
.juice-card.featured h4{ color:var(--white); }
.juice-card.featured .price{ background:rgba(255,255,255,.15); color:var(--gold-light); }

/* CRAVA Combo Section */
.combos {
  background: linear-gradient(180deg, var(--forest-dark) 0%, #153320 100%);
  position: relative;
  padding-bottom: 20px;
}
.combo-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}
.combo-card {
  background: var(--glass-dark-fill);
  -webkit-backdrop-filter: var(--glass-blur);
  backdrop-filter: var(--glass-blur);
  border: 1px solid var(--glass-dark-border);
  border-radius: var(--radius-lg);
  padding: 28px 24px;
  display: flex;
  flex-direction: column;
  position: relative;
  overflow: hidden;
  box-shadow: var(--glass-shadow-dark);
  transition: transform .35s var(--ease), border-color .35s var(--ease), box-shadow .35s var(--ease), background .35s var(--ease);
}
.combo-card::before{
  content:""; position:absolute; inset:0 0 auto 0; height:40%;
  background: linear-gradient(180deg, rgba(255,255,255,.14), rgba(255,255,255,0));
  pointer-events:none;
}
.combo-card:hover {
  transform: translateY(-8px);
  background: var(--glass-dark-fill-strong);
  border-color: var(--gold);
  box-shadow: 0 24px 50px -14px rgba(0, 0, 0, 0.5), inset 0 1px 0 rgba(255,255,255,.2);
}
.combo-card.popular {
  background: linear-gradient(165deg, rgba(245, 166, 35, 0.22) 0%, rgba(27, 77, 46, 0.45) 100%);
  -webkit-backdrop-filter: var(--glass-blur);
  backdrop-filter: var(--glass-blur);
  border: 2px solid var(--gold);
}
.combo-badge {
  position: absolute;
  top: 16px;
  inset-inline-end: 16px;
  background: var(--gold);
  color: var(--ink);
  font-size: 11px;
  font-weight: 800;
  padding: 4px 12px;
  border-radius: 999px;
  text-transform: uppercase;
  z-index: 2;
}
.combo-img {
  width: 100%;
  aspect-ratio: 16/10;
  border-radius: var(--radius-md);
  overflow: hidden;
  margin-bottom: 20px;
  background: rgba(0, 0, 0, 0.2);
  border: 1px solid rgba(255,255,255,.14);
  position: relative;
}
.combo-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform .5s var(--ease);
}
.combo-card:hover .combo-img img {
  transform: scale(1.08);
}
.combo-card h3 {
  color: var(--white);
  font-size: 20px;
  font-weight: 800;
  margin-bottom: 10px;
}
.combo-card p {
  color: #C9D1C3;
  font-size: 14px;
  margin-bottom: 20px;
  flex-grow: 1;
}
.combo-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding-top: 16px;
  margin-top: auto;
}
.combo-price {
  color: var(--gold-light);
  font-weight: 800;
  font-size: 18px;
}

/* IceCrava */
.icecrava{ background: linear-gradient(180deg,var(--cream-2) 0%, #FCE4B0 100%); }
.icecrava-card{
  position:relative; isolation:isolate; overflow:hidden;
  display:flex; align-items:center; gap:44px;
  background: var(--glass-light-fill);
  -webkit-backdrop-filter: var(--glass-blur);
  backdrop-filter: var(--glass-blur);
  border: 1px solid var(--glass-light-border);
  border-radius:var(--radius-lg); padding:40px;
  box-shadow:0 30px 60px -30px rgba(217,136,18,.35), inset 0 1px 0 rgba(255,255,255,.9);
  transition: transform .4s var(--ease), box-shadow .4s var(--ease), background .4s var(--ease);
}
.icecrava-card::before{
  content:""; position:absolute; inset:0 0 auto 0; height:45%; z-index:-1;
  background: var(--glass-highlight); pointer-events:none;
}
.icecrava-card:hover{ transform:translateY(-6px); background:var(--glass-light-fill-strong); box-shadow:0 40px 70px -28px rgba(217,136,18,.5), inset 0 1px 0 rgba(255,255,255,1); }
.icecrava-icon{
  flex-shrink:0; width:150px; height:150px; border-radius:50%;
  overflow:hidden;
  background: radial-gradient(circle,var(--cream) 0%, var(--cream-2) 100%);
  border: 1px solid rgba(255,255,255,.9);
  box-shadow: 0 14px 34px -12px rgba(217,136,18,.4), inset 0 2px 6px rgba(255,255,255,.8);
  transition: transform .4s var(--ease);
}
.icecrava-icon img{ width:100%; height:100%; object-fit:cover; }
.icecrava-card:hover .icecrava-icon{ transform:scale(1.05) rotate(-3deg); }
.icecrava-tag{
  display:inline-block; font-size:12.5px; font-weight:700; color:var(--gold-deep);
  background:var(--cream-2); padding:5px 14px; border-radius:999px; margin-bottom:12px;
}
.icecrava-text h3{ font-size:26px; color:var(--forest); margin-bottom:12px; }
.icecrava-text p{ color:var(--text-muted); font-size:15.5px; margin-bottom:18px; max-width:480px; }
.icecrava-text .price{
  display:inline-block; font-weight:700; color:var(--white); background:var(--forest);
  padding:8px 20px; border-radius:999px; font-size:15px;
}

/* Fries */
.fries { 
  background: var(--gold-deep); 
  position: relative; 
  overflow: hidden; 
}
.fries-glow{ top:10%; inset-inline-start:50%; transform:translateX(-50%); opacity:.28; }

.fries-layout{
  display:grid; grid-template-columns: 1fr 1fr; gap:52px; align-items:center;
}
.fries-feature-img{
  position:relative; border-radius:var(--radius-lg); overflow:hidden;
  border: 1px solid rgba(255,255,255,.25);
  box-shadow:0 40px 80px -30px rgba(0,0,0,.6), inset 0 1px 0 rgba(255,255,255,.25);
}
.fries-feature-img img{ transition: transform .7s var(--ease); }
.fries-feature-img:hover img{ transform:scale(1.05); }

.fries-cards{ display:flex; flex-direction:column; gap:14px; }
.fries-card{
  position:relative; overflow:hidden;
  display:flex; align-items:center; gap:18px;
  background: var(--glass-dark-fill);
  -webkit-backdrop-filter: var(--glass-blur-soft);
  backdrop-filter: var(--glass-blur-soft);
  border:1px solid var(--glass-dark-border);
  border-radius:var(--radius-md); padding:18px 22px;
  box-shadow: inset 0 1px 0 rgba(255,255,255,.14);
  transition: transform .3s var(--ease), background .3s var(--ease), border-color .3s var(--ease);
}
.fries-card:hover{
  transform:translateX(-6px); background:rgba(255,255,255,.16); border-color:var(--white);
}
[dir="rtl"] .fries-card:hover{ transform:translateX(6px); }
.fc-body{ 
  flex: 1; 
  min-width: 0; 
}
.fc-body h4{ 
  color: var(--white); 
  font-size: 15px; 
  margin-bottom: 4px; 
  word-break: break-word; 
}
.fc-body p{ 
  color: #A9B2A2; 
  font-size: 12px; 
}

/* Price Sizes for Fries */
.price-sizes {
  display: flex;
  flex-direction: column;
  gap: 6px;
  min-width: 105px;
  flex-shrink: 0;
}
.size-price {
  background: rgba(0, 0, 0, 0.22);
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(245, 166, 35, 0.25);
  padding: 4px 8px;
  border-radius: 10px;
  font-size: 12.5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 8px;
}
.size-price .size-label {
  color: #A9B2A2;
  font-weight: normal;
  font-size: 11px;
}
.size-price .size-value {
  color: var(--gold-light);
  font-weight: 700;
}
.fries-card.featured { background:linear-gradient(90deg,rgba(245,166,35,.16),rgba(245,166,35,.03)); border-color:var(--gold); }
.fries-card.featured .size-price {
  background: rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.2);
}

/* Sauces */
.sauces{ background:var(--ink-2); padding-bottom:20px; }
.sauce-list{
  display:grid; grid-template-columns:repeat(5,1fr); gap:16px;
}
.sauce-item{
  background: var(--glass-dark-fill);
  -webkit-backdrop-filter: var(--glass-blur-soft);
  backdrop-filter: var(--glass-blur-soft);
  border:1px solid var(--glass-dark-border);
  border-radius:var(--radius-md); padding:22px 16px;
  display:flex; flex-direction:column; align-items:center; gap:10px; text-align:center;
  box-shadow: inset 0 1px 0 rgba(255,255,255,.12);
  transition: transform .3s var(--ease), background .3s var(--ease);
}
.sauce-item:hover{ transform:translateY(-6px); background:var(--glass-dark-fill-strong); }
.sauce-dot{ width:26px; height:26px; border-radius:50%; box-shadow:inset 0 -3px 6px rgba(0,0,0,.2), 0 2px 6px rgba(0,0,0,.25); }
.dot-red{ background:#D64545; }
.dot-white{ background:#F2EEE3; }
.dot-orange{ background:var(--gold); }
.dot-hot{ background:#E2572B; }
.dot-cream{ background:#EDE0C8; }
.sauce-name{ color:var(--white); font-weight:600; font-size:14.5px; }
.sauce-item .price{ color:var(--gold-light); font-size:13px; font-weight:700; }

/* Takeaway strip */
.takeaway-strip{
  background: linear-gradient(90deg,var(--gold-deep),var(--gold));
  overflow: hidden;
  padding: 14px 0;
  width: 100%;
}
.marquee {
  width: 100%;
  overflow: hidden;
  display: flex;
  white-space: nowrap;
}
.marquee-track{
  display: flex;
  gap: 20px;
  width: max-content;
  animation: marquee 16s linear infinite;
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 15px;
  color: var(--ink);
}
.marquee-track span{
  display: inline-flex;
  align-items: center;
  padding: 0 6px;
}
@keyframes marquee{
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
[dir="rtl"] .marquee-track{
  animation: marquee-rtl 16s linear infinite;
}
@keyframes marquee-rtl{
  0% { transform: translateX(0); }
  100% { transform: translateX(50%); }
}

/* Footer */
.site-footer{ 
  background:var(--forest-dark); 
  color:#D9DED4; 
  padding-top:70px;
  position: relative;
  width: 100%;
  overflow: hidden;
}
.footer-inner{
  max-width:1240px; margin:0 auto; padding:0 24px 50px;
  display:grid; grid-template-columns:1.3fr 1fr 1fr 1fr; gap:40px;
}
.footer-logo{ height:34px; margin-bottom:16px; filter:brightness(0) invert(1); opacity:.92; }
.footer-brand p{ font-size:14px; color:#A9B2A2; }
.footer-col h5{ color:var(--gold-light); font-size:15px; margin-bottom:16px; }
.footer-col p{ font-size:14px; margin-bottom:8px; color:#C9D1C3; }
.takeaway-note{ color:var(--gold-light) !important; font-weight:600; }

.social-row{ display:flex; gap:10px; }
.social-icon{
  width:40px; height:40px; border-radius:50%; display:flex; align-items:center; justify-content:center;
  background: var(--glass-dark-fill);
  -webkit-backdrop-filter: var(--glass-blur-soft);
  backdrop-filter: var(--glass-blur-soft);
  border:1px solid var(--glass-dark-border);
  box-shadow: inset 0 1px 0 rgba(255,255,255,.16);
  transition: transform .3s var(--ease), background .3s var(--ease), color .3s var(--ease);
}
.social-icon:hover{ background:var(--gold); color:var(--ink); transform:translateY(-4px) rotate(-6deg); }

.footer-bottom{
  border-top:1px solid rgba(255,255,255,.08); text-align:center; padding:22px 24px; font-size:13px; color:#8B9384;
}

/* Scroll-reveal animation classes */
.reveal-up{ opacity:0; transform:translateY(28px); transition: opacity .7s var(--ease), transform .7s var(--ease); }
.reveal-up.in-view{ opacity:1; transform:translateY(0); }

.reveal-scale{ opacity:0; transform:scale(.85); transition: opacity .8s var(--ease), transform .8s var(--ease); }
.reveal-scale.in-view{ opacity:1; transform:scale(1); }

.reveal-left{ opacity:0; transform:translateX(-40px); transition: opacity .8s var(--ease), transform .8s var(--ease); }
[dir="rtl"] .reveal-left{ transform:translateX(40px); }
.reveal-left.in-view{ opacity:1; transform:translateX(0); }

.delay-1{ transition-delay:.1s; }
.delay-2{ transition-delay:.25s; }
.delay-3{ transition-delay:.4s; }
.delay-4{ transition-delay:.55s; }

.juice-card.in-view, .fries-card.in-view, .sauce-item.in-view, .combo-card.in-view{ opacity:1; transform:none; }
.juice-card, .fries-card, .sauce-item, .combo-card{
  opacity:0; transform:translateY(20px);
  transition: opacity .6s var(--ease), transform .6s var(--ease), box-shadow .35s var(--ease), border-color .35s var(--ease), background .35s var(--ease);
}

/* Responsive */
@media (max-width: 980px){
  .quick-nav-cards { grid-template-columns: repeat(2, 1fr); }
  .juice-grid{ grid-template-columns:repeat(3,1fr); }
  .fruit-bowl-grid{ grid-template-columns:repeat(2,1fr); }
  .combo-grid{ grid-template-columns: 1fr; }
  .sauce-list{ grid-template-columns:repeat(3,1fr); }
  .footer-inner{ grid-template-columns:1fr 1fr; }
}

@media (max-width: 760px){
  .main-nav{
    position:fixed; inset-inline-end:0; top:0; height:100svh; width:min(78vw,320px);
    background: rgba(15,22,14,.72);
    -webkit-backdrop-filter: blur(30px) saturate(180%);
    backdrop-filter: blur(30px) saturate(180%);
    border-inline-start: 1px solid rgba(255,255,255,.14);
    flex-direction:column; align-items:flex-start;
    padding:110px 32px 40px; gap:26px;
    transform:translateX(100%); transition: transform .4s var(--ease);
    z-index:1050;
  }
  [dir="rtl"] .main-nav{ transform:translateX(-100%); }
  .main-nav.open{ transform:translateX(0); }
  .main-nav a{ font-size:18px; }
  .menu-toggle{ display:flex; }

  .fries-layout{ grid-template-columns:1fr; }
  
  .juice-grid, .fruit-bowl-grid {
    grid-template-columns: repeat(3, 1fr) !important;
    gap: 12px;
  }
  .juice-card {
    padding: 16px 8px; 
  }
  .juice-card h4 {
    font-size: 13px; 
    min-height: 38px;
  }
  .juice-card .price {
    font-size: 12px;
    padding: 4px 10px;
  }

  .sauce-list{ grid-template-columns:repeat(2,1fr); }
  .footer-inner{ grid-template-columns:1fr; text-align:center; }
  .social-row{ justify-content:center; }
  .section-inner{ padding:64px 20px; }

  .icecrava-card{ flex-direction:column; text-align:center; padding:32px 24px; }
  .icecrava-text p{ max-width:none; }
  .icecrava-icon{ width:130px; height:130px; }
}

@media (max-width: 420px){
  .hero-title{ font-size:30px; }
  .btn{ padding:14px 22px; font-size:14px; }
  .quick-nav-cards { grid-template-columns: 1fr; }
  
  .juice-grid, .fruit-bowl-grid {
    grid-template-columns: repeat(3, 1fr) !important;
    gap: 8px;
  }
  .juice-card {
    padding: 12px 6px;
  }
  .juice-card h4 {
    font-size: 11px;
    min-height: 34px;
  }
  .juice-card .price {
    font-size: 11px;
    padding: 3px 8px;
  }

  .item-photo-fries{ width:52px; height:52px; }
  .fries-card { padding: 12px 10px; gap: 8px; }
  .size-price { padding: 3px 6px; font-size: 11px; gap: 4px; }
  .size-price .size-value { font-size: 11px; }

  .icecrava-icon{ width:110px; height:110px; }
}

html, body {
  margin: 0 !important;
  padding: 0 !important;
  width: 100% !important;
  max-width: 100% !important;
  overflow-x: hidden !important;
}

.hero {
  margin: 0 !important;
  padding-left: 0 !important;
  padding-right: 0 !important;
  width: 100% !important;
}
</style>
</head>
<body>

<!-- Preloader -->
<div id="preloader">
  <img src="crrrlogo.jpg" alt="CRAVA" class="loader-logo">
  <div class="loader-spinner"></div>
</div>

<div class="grain" aria-hidden="true"></div>

<!-- ================= HEADER ================= -->
<header class="site-header" id="siteHeader">
  <div class="header-inner">
    <a href="#hero" class="brand">
      <img src="crrrlogo.jpg" alt="کڕاڤە" class="brand-logo">
    </a>

    <nav class="main-nav" id="mainNav">
      <a href="#juices">شەربەتی میوە</a>
      <a href="#combos">کۆمبۆ</a>
      <a href="#icecrava">ئایسکراڤا</a>
      <a href="#fries">پەتاتە</a>
      <a href="#sauces">سۆسەکان</a>
      <a href="#footer">پەیوەندی</a>
    </nav>

    <button class="menu-toggle" id="menuToggle" aria-label="کردنەوەی مینیو" aria-expanded="false">
      <span></span><span></span><span></span>
    </button>
  </div>
</header>

<!-- ================= HERO ================= -->
<section class="hero" id="hero">
  <div class="hero-glow glow-green" aria-hidden="true"></div>
  <div class="hero-glow glow-gold" aria-hidden="true"></div>

  <div class="floaters" aria-hidden="true">
    <span class="floater f1">🍟</span>
    <span class="floater f2">🍓</span>
    <span class="floater f3">🥝</span>
    <span class="floater f4">🍍</span>
    <span class="floater f5">🍟</span>
  </div>

  <div class="hero-inner">
    <img src="crrrlogo.jpg" alt="کڕاڤە" class="hero-logo reveal-scale">

    <p class="eyebrow reveal-up delay-1"></p>
    <h1 class="hero-title reveal-up delay-2">
      بەخێربێن <br>
      <span class="accent-text"> بۆ کڕاڤا </span>
    </h1>
    <p class="hero-sub reveal-up delay-3">شەربەتی میوەی فرێش و پەتاتەی گەرمی تازە بە جۆرەها تامی جیاواز لەگەڵ CRAVA تاقی بکەرەوە</p>

    <div class="hero-actions reveal-up delay-4">
      <a href="#juices" class="btn btn-primary">
        <span>بینینی مینیو</span>
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M12 5v14M5 12l7 7 7-7" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </a>
      <a href="#footer" class="btn btn-ghost">شوێنمان بزانە</a>
    </div>
  </div>

  <div class="quick-nav-cards reveal-up delay-4">
    <a href="#juices" class="quick-card">
      <div class="quick-card-icon">
        <img src="juice-icon.jpg" alt="شەربەتی میوە" loading="lazy">
      </div>
      <div class="quick-card-info">
        <h4>شەربەتی میوە</h4>
        <p></p>
      </div>
    </a>
    <a href="#combos" class="quick-card">
      <div class="quick-card-icon">
        <img src="combo111.jpg" alt="کڕاڤا کۆمبۆ" loading="lazy">
      </div>
      <div class="quick-card-info">
          <h4>کڕاڤا کۆمبۆ</h4>
        <p></p>
      </div>
    </a>
    <a href="#icecrava" class="quick-card">
      <div class="quick-card-icon">
        <img src="icecr.jpg" alt="ئایسکراڤا" loading="lazy">
      </div>
      <div class="quick-card-info">
        <h4>ئایسکراڤا</h4>
        <p></p>
      </div>
    </a>
    <a href="#fries" class="quick-card">
      <div class="quick-card-icon">
        <img src="fries-icon.jpg" alt="پەتاتەی گەرم" loading="lazy">
      </div>
      <div class="quick-card-info">
        <h4>پەتاتەی گەرم</h4>
        <p></p>
      </div>
    </a>
  </div>
</section>

<div class="wave-divider" aria-hidden="true">
  <svg viewBox="0 0 1200 60" preserveAspectRatio="none">
    <path d="M0,30 C150,60 350,0 600,30 C850,60 1050,0 1200,30 L1200,60 L0,60 Z" fill="url(#waveGrad1)"/>
    <defs>
      <linearGradient id="waveGrad1" x1="0" y1="0" x2="1" y2="0">
        <stop offset="0%" stop-color="#1B4D2E"/>
        <stop offset="100%" stop-color="#F5A623"/>
      </linearGradient>
    </defs>
  </svg>
</div>

<!-- ================= JUICES ================= -->
<section class="juices" id="juices">
  <div class="section-inner">
    <div class="section-head">
      <p class="kicker reveal-up">تازە · سروشتی ·</p>
      <h2 class="section-title reveal-up">شەربەتی میوە</h2>
      <p class="section-desc reveal-up">جۆرەها شەربەتی میوەی تازە، میکسی تایبەت و میلکشەیك، هەر ڕۆژێک لە میوەی فرێش دروست دەکرێت.</p>
    </div>

    <!-- دوگمەکانی جیاکردنەوە (Tabs) -->
    <div class="juice-tabs reveal-up">
      <button class="tab-btn active" data-target="mix-juices">میکسی میوە</button>
      <button class="tab-btn" data-target="pure-juices">شەربەتی میوە</button>
      <button class="tab-btn" data-target="milkshakes">میلکشەیک</button>
      <button class="tab-btn" data-target="fruit-bowls">قاپی میوە</button>
    </div>

    <!-- Subsection 1: Mix Fruit Juices -->
    <div class="juice-category active" id="mix-juices">
      <div class="juice-grid">
        <article class="juice-card"><div class="item-photo"><img src="sunshine.jpg" alt="میکسی کوێستان" loading="lazy"></div><h4>کڕاڤا سەنشاین</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="fresh.jpg" alt="میکسی ئەنتیۆکسیدانت" loading="lazy"></div><h4>فرێش کڕاڤا</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="matrix.jpg" alt="میکسی لیمۆ و تووی فەرەنگی" loading="lazy"></div><h4>کڕاڤا ماتریکس</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="dream.jpg" alt="میکسی مانگۆ و پرتەقاڵ" loading="lazy"></div><h4>کڕاڤا دریم</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="dream.jpg" alt="میکسی سێو و کیوی" loading="lazy"></div><h4>کڕاڤا ئەکتیڤ</h4><span class="price">٣٠٠٠ د.ع</span></article>
  
        <article class="juice-card featured"><div class="item-photo"><img src="cravamix.jpg" alt="میکسی تایبەتی کڕاڤە" loading="lazy"></div><h4>کڕاڤا میکس</h4><span class="price">٤٠٠٠ د.ع</span></article>
      </div>
    </div>

    <!-- Subsection 2: Pure Fruit Juices -->
    <div class="juice-category" id="pure-juices">
      <div class="juice-grid">
        <article class="juice-card"><div class="item-photo"><img src="orange.jpg" alt="شەربەتی پرتەقاڵ" loading="lazy"></div><h4>شەربەتی پرتەقاڵ</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="hanar.jpg" alt="شەربەتی هەنار" loading="lazy"></div><h4>شەربەتی هەنار</h4><span class="price">٤٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="lemo.jpg" alt="شەربەتی لیمۆ و نەعنا" loading="lazy"></div><h4>شەربەتی لیمۆ و نەعنا</h4><span class="price">٣٥٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="sew.jpg" alt="شەربەتی سێو" loading="lazy"></div><h4>شەربەتی سێو</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="wmelon.jpg" alt="شەربەتی شوتی" loading="lazy"></div><h4>شەربەتی شوتی</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="melon.jpg" alt="شەربەتی کاڵەک" loading="lazy"></div><h4>شەربەتی کاڵەک</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="ananas.jpg" alt="شەربەتی ئەناناس" loading="lazy"></div><h4>شەربەتی ئەناناس</h4><span class="price">٤٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="stberry.jpg" alt="شەربەتی شلک" loading="lazy"></div><h4>شەربەتی شلک</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="xox.jpg" alt="شەربەتی خۆخ" loading="lazy"></div><h4>شەربەتی خۆخ</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="grape.jpg" alt="شەربەتی ترێ" loading="lazy"></div><h4>شەربەتی ترێ</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="moz.jpg" alt="شیر مۆز" loading="lazy"></div><h4>شیر مۆز</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="gezar.jpg" alt="شەربەتی گێزەر" loading="lazy"></div><h4>شەربەتی گێزەر</h4><span class="price">٣٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="mango.jpg" alt="شەربەتی مانگۆ" loading="lazy"></div><h4>شەربەتی مانگۆ</h4><span class="price">٤٠٠٠ د.ع</span></article>

         <article class="juice-card"><div class="item-photo"><img src="figs.jpg" alt="شەربەتی مانگۆ" loading="lazy"></div><h4>شەربەتی هەنجیر</h4><span class="price">٤٠٠٠ د.ع</span></article>
     
      
      </div>
    </div>

    <!-- Subsection 3: Milkshakes -->
    <div class="juice-category" id="milkshakes">
      <div class="juice-grid">
        <article class="juice-card"><div class="item-photo"><img src="shake1.jpg" alt="مانگۆ" loading="lazy"></div><h4>مانگۆ</h4><span class="price">٤٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="shake2.jpg" alt=" ئەناناس" loading="lazy"></div><h4>ئەناناس</h4><span class="price">٤٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="shake3.jpg" alt="مۆز" loading="lazy"></div><h4>مۆز</h4><span class="price">٤٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="shake4.jpg" alt="بلاکبێری" loading="lazy"></div><h4>بلاکبێری</h4><span class="price">٤٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="shake5.jpg" alt="کاڵەک" loading="lazy"></div><h4>کاڵەک</h4><span class="price">٤٠٠٠ د.ع</span></article>
        <article class="juice-card"><div class="item-photo"><img src="shake6.jpg" alt=" Shake" loading="lazy"></div><h4>خۆخ</h4><span class="price">٤٠٠٠ د.ع</span></article>
      </div>
    </div>

    <!-- Subsection 4: Fruit Bowls (قاپی میوە) -->
    <div class="juice-category" id="fruit-bowls">
      <div class="bowl">
        <article class="juice-card"><div class="item-photo"><img src="qap.jpg" alt="قاپی میوە  " loading="lazy"></div><h4>قاپی میوە </h4><span class="price">٣٠٠٠ د.ع</span></article>
      </div>
    </div>

  </div>
</section>

<!-- ================= CRAVA COMBO ================= -->
<section class="combos" id="combos">
  <div class="section-inner">
    <div class="section-head light">
      <p class="kicker reveal-up">ئۆفەری تایبەت</p>
      <h2 class="section-title reveal-up">کڕاڤە کۆمبۆ</h2>
      <p class="section-desc reveal-up">تێکەڵەی زێڕینی پەتاتەی گەرم و شەربەتی میوەی فرێش بە نرخی تایبەت.</p>
    </div>

    <div class="combo-grid">
      <article class="combo-card reveal-up">
        <div class="combo-img">
          <img src="combo11.jpg" alt="کۆمبۆی کلاسیک" loading="lazy">
        </div>
        <h3> پەتاتە +شەربەتی فرێش</h3>
        <p></p>
        <div class="combo-footer">
          <span class="combo1-price">٥,٠٠٠ د.ع</span>
        </div>
      </article>

      <article class="combo22-card reveal-up delay-2">
        <div class="combo-img">
          <img src="combo22.jpg" alt="کۆمبۆی خێزانی" loading="lazy">
        </div>
        <h3>شەربەتی فرێش +میوە </h3>
        <p></p>
        <div class="combo-footer">
          <span class="combo-price">٥٠٠٠ د.ع</span>
        </div>
      </article>
    </div>
  </div>
</section>

<div class="wave-divider" aria-hidden="true">
  <svg viewBox="0 0 1200 60" preserveAspectRatio="none">
    <path d="M0,30 C150,60 350,0 600,30 C850,60 1050,0 1200,30 L1200,60 L0,60 Z" fill="url(#waveGrad3)"/>
    <defs>
      <linearGradient id="waveGrad3" x1="0" y1="0" x2="1" y2="0">
        <stop offset="0%" stop-color="#FCEFD2"/>
        <stop offset="100%" stop-color="#F5A623"/>
      </linearGradient>
    </defs>
  </svg>
</div>

<!-- ================= ICECRAVA ================= -->
<section class="icecrava" id="icecrava">
  <div class="section-inner">
    <div class="section-head">
      <p class="kicker reveal-up">نوێ · سارد و کرێمی</p>
      <h2 class="section-title reveal-up" style="color: var(--forest);">ICECRAVA</h2>
      <p class="section-desc reveal-up" style="color: var(--text-muted);">ئایسکریمی تایبەتی کڕاڤە .</p>
    </div>

    <div class="icecrava-card reveal-up">
      <div class="icecrava-icon">
        <img src="icecr.jpg" alt="ئایسکڕیمی کڕاڤە" loading="lazy">
      </div>
      <div class="icecrava-text">
        <span class="icecrava-tag">بە تامی جۆرەها میوە</span>
        <h3>ئایس کڕاڤە</h3>
        <span class="price">٢٠٠٠ د.ع</span>
      </div>
    </div>
  </div>
</section>

<div class="wave-divider wave-into-dark" aria-hidden="true">
  <svg viewBox="0 0 1200 60" preserveAspectRatio="none">
    <path d="M0,30 C150,0 350,60 600,30 C850,0 1050,60 1200,30 L1200,60 L0,60 Z" fill="url(#waveGrad2)"/>
    <defs>
      <linearGradient id="waveGrad2" x1="0" y1="0" x2="1" y2="0">
        <stop offset="0%" stop-color="#F5A623"/>
        <stop offset="100%" stop-color="#0F2116"/>
      </linearGradient>
    </defs>
  </svg>
</div>

<!-- ================= FRIES ================= -->
<section class="fries" id="fries">
  <div class="hero-glow glow-gold fries-glow" aria-hidden="true"></div>

  <div class="section-inner">
    <div class="section-head">
      <p class="kicker reveal-up"></p>
      <h2 class="section-title reveal-up">پەتاتەی کڕاڤە</h2>
      <p class="section-desc reveal-up"> هەموویان بە تازەیی ئامادە دەکرێن دوای داواکردن، بە دوو قەبارەی جیاواز.</p>
    </div>

    <div class="fries-layout">
      <div class="fries-feature-img reveal-left">
        <img src="crbox.jpg" alt="سادە" loading="lazy">
      </div>

      <div class="fries-cards">
        <article class="fries-card reveal-up">
          <div class="item-photo item-photo-fries"><img src="crit.jpg" alt="پەتاتەی کلاسیک" loading="lazy"></div>
          <div class="fc-body">
            <h4>پەتاتەی کلاسیک</h4>
            <p></p>
          </div>
          <div class="price-sizes">
            <div class="size-price"><span class="size-label">بچووک</span><span class="size-value">٣٠٠٠ د.ع</span></div>
            <div class="size-price"><span class="size-label">گەورە</span><span class="size-value">٤٠٠٠ د.ع</span></div>
          </div>
        </article>

        <article class="fries-card reveal-up">
          <div class="item-photo item-photo-fries"><img src="crit.jpg" alt=" پەتاتە+پەنیر" loading="lazy"></div>
          <div class="fc-body">
            <h4>پەتاتە+پەنیر</h4>
            <p></p>
          </div>
          <div class="price-sizes">
            <div class="size-price"><span class="size-label">بچووک</span><span class="size-value">٣٥٠٠ د.ع</span></div>
            <div class="size-price"><span class="size-label">گەورە</span><span class="size-value">٤٥٠٠ د.ع</span></div>
          </div>
        </article>

        <article class="fries-card reveal-up">
          <div class="item-photo item-photo-fries"><img src="crit.jpg" alt="پەتاتە+کنتاکی" loading="lazy"></div>
          <div class="fc-body">
            <h4> پەتاتە+کنتاکی</h4>
            <p></p>
          </div>
          <div class="price-sizes">
            <div class="size-price"><span class="size-label">بچووک</span><span class="size-value">٣٥٠٠ د.ع</span></div>
            <div class="size-price"><span class="size-label">گەورە</span><span class="size-value">٤٥٠٠ د.ع</span></div>
          </div>
        </article>

        <article class="fries-card reveal-up">
          <div class="item-photo item-photo-fries"><img src="crit.jpg" alt="پەتاتەی+کنتاکی+پەنیر" loading="lazy"></div>
          <div class="fc-body">
            <h4>پەتاتە+کنتاکی+پەنیرز</h4>
            <p>ە</p>
          </div>
          <div class="price-sizes">
            <div class="size-price"><span class="size-label">بچووک</span><span class="size-value">٤٠٠٠ د.ع</span></div>
            <div class="size-price"><span class="size-label">گەورە</span><span class="size-value">٥٠٠٠ د.ع</span></div>
          </div>
        </article>
      </div>
    </div>
  </div>
</section>

<!-- ================= SAUCES ================= -->
<section class="sauces" id="sauces">
  <div class="section-inner">
    <div class="section-head light">
      <p class="kicker reveal-up"></p>
      <h2 class="section-title reveal-up">سۆسەکان</h2>
      <p class="section-desc reveal-up">.</p>
    </div>

    <ul class="sauce-list">
      <li class="sauce-item reveal-up"><span class="sauce-dot dot-red"></span><span class="sauce-name">کێچەپ</span><span class="price"></span></li>
      <li class="sauce-item reveal-up"><span class="sauce-dot dot-white"></span><span class="sauce-name">مایۆنێز</span><span class="price"> </span></li>
      <li class="sauce-item reveal-up"><span class="sauce-dot dot-orange"></span><span class="sauce-name">سۆسی پەنیر </span><span class="price"> </span></li>
    </ul>
  </div>
</section>

<!-- ================= TAKEAWAY STRIP ================= -->
<section class="takeaway-strip">
  <div class="marquee">
    <div class="marquee-track">
      <span>کراڤا</span><span>•</span>
      <span>شەربەتی میوەی فريش</span><span>•</span>
      <span>پەتاتەی گەرمی تازە</span><span>•</span>
      <span>کراڤا</span><span>•</span>
      <span>شەربەتی میوەی فريش</span><span>•</span>
      <span>پەتاتەی گەرمی تازە</span><span>•</span>
      <span>کراڤا</span><span>•</span>
      <span>شەربەتی میوەی فريش</span><span>•</span>
      <span>پەتاتەی گەرمی تازە</span><span>•</span>
      <span>کراڤا</span><span>•</span>
      <span>شەربەتی میوەی فريش</span><span>•</span>
      <span>پەتاتەی گەرمی تازە</span><span>•</span>
    </div>
  </div>
</section>

<!-- ================= FOOTER ================= -->
<footer class="site-footer" id="footer">
  <div class="footer-inner">
    <div class="footer-brand">
      <img src="crrrlogo.jpg" alt="کڕاڤە" class="footer-logo">
      <p></p>
    </div>

    <div class="footer-col">
      <h5>شوێنمان</h5>
      <p class="address"></p>
      <p class="takeaway-note">شەقامی کاوە(حریق)-بەرامبەر LC Waikiki</p>
    </div>

    <div class="footer-col">
      <h5>کراوەیە لە</h5>
      <p></p>
      <p>٥:٠٠ دوای نیوەڕۆ تاوەکو ١:٠٠ شەو</p>
    </div>

    <div class="footer-col">
      <h5>لەگەڵمان بن</h5>
      <div class="social-row">
        <a href="https://www.instagram.com/crava.krd?igsh=MWlodnU3aW9oa3Q5ag%3D%3D&utm_source=qr" class="social-icon" aria-label="ئینستاگرام">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><rect x="3" y="3" width="18" height="18" rx="5" stroke="currentColor" stroke-width="1.8"/><circle cx="12" cy="12" r="4" stroke="currentColor" stroke-width="1.8"/><circle cx="17.5" cy="6.5" r="1.2" fill="currentColor"/></svg>
        </a>
        <a href="https://www.facebook.com/share/19buTrkUtX/?mibextid=wwXIfr" class="social-icon" aria-label="فەیسبووک">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M14 8.5h2.5V5h-2.5c-2.2 0-4 1.8-4 4v2H8v3.5h2.5V21h3.5v-6.5h2.5l.5-3.5h-3V9c0-.6.4-.5 1-.5z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/></svg>
        </a>
        <a href="https://www.tiktok.com/@cravakrd?_r=1&_t=ZS-996w560xYzV" class="social-icon" aria-label="تیک تۆک">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M15 3c.4 2.2 2 3.8 4 4v3c-1.5 0-2.9-.4-4-1.2V15a5 5 0 1 1-5-5v3a2 2 0 1 0 2 2V3h3z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/></svg>
        </a>
        <a href="#" class="social-icon" aria-label="واتساپ">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M12 21a9 9 0 1 0-7.8-4.5L3 21l4.6-1.2A9 9 0 0 0 12 21z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/><path d="M8.5 9.5c0 4 3 6.5 6.5 6.5.6 0 1.5-.2 1.5-1v-1.3l-2-1-1 1c-1-.4-2.2-1.6-2.7-2.7l1-1-1-2H9c-.4 0-.5.7-.5 1.5z" fill="currentColor"/></svg>
        </a>
        <a href="" target="_blank" class="social-icon" aria-label="سنەپچات">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 2c-2.5 0-4.5 2-4.5 4.5v2c0 .5-.3 1-.8 1.2l-1 .5c-.3.2-.4.6-.2.9.4.5 1 .8 1.6.9.4.1.7.5.6.9-.3 1.4-1.3 2.5-2.6 2.9-.2.1-.3.3-.2.5.3.5 1 .8 1.7.8.7 0 1.3.4 1.6 1 .4.8 1.2 1.3 2.1 1.3h3.4c.9 0 1.7-.5 2.1-1.3.3-.6.9-1 1.6-1 .7 0 1.4-.3 1.7-.8.1-.2 0-.4-.2-.5-1.3-.4-2.3-1.5-2.6-2.9-.1-.4.2-.8.6-.9.6-.1 1.2-.4 1.6-.9.2-.3.1-.7-.2-.9l-1-.5c-.5-.2-.8-.7-.8-1.2v-2C16.5 4 14.5 2 12 2z"/>
          </svg>
        </a>
      </div>
    </div>
  </div>

  <div class="footer-bottom">
    <p>© ٢٠٢٦ کڕاڤە.</p>
  </div>
</footer>

<!-- ================= FIREBASE & JAVASCRIPT ================= -->
<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js";
  import { getAnalytics } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-analytics.js";
  import { getFirestore, collection, getDocs } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js";

  const firebaseConfig = {
    apiKey: "AIzaSyAamIeVeEDvabLYbmQ9Zbpspyz7TSrx2KI",
    authDomain: "cravakrdmenu.firebaseapp.com",
    projectId: "cravakrdmenu",
    storageBucket: "cravakrdmenu.firebasestorage.app",
    messagingSenderId: "911541353964",
    appId: "1:911541353964:web:33bfa5474549e63281d4c9",
    measurementId: "G-VY0XYQH6V2"
  };

  const app = initializeApp(firebaseConfig);
  const analytics = getAnalytics(app);
  const db = getFirestore(app);

  document.addEventListener('DOMContentLoaded', () => {
    const preloader = document.getElementById('preloader');
    setTimeout(() => {
      preloader.classList.add('loaded');
    }, 800);

    const header = document.getElementById('siteHeader');
    const onScroll = () => {
      if (window.scrollY > 40) header.classList.add('scrolled');
      else header.classList.remove('scrolled');
    };
    window.addEventListener('scroll', onScroll, { passive: true });
    onScroll();

    const menuToggle = document.getElementById('menuToggle');
    const mainNav = document.getElementById('mainNav');

    menuToggle.addEventListener('click', () => {
      const isOpen = mainNav.classList.toggle('open');
      menuToggle.classList.toggle('open', isOpen);
      menuToggle.setAttribute('aria-expanded', String(isOpen));
      document.body.style.overflow = isOpen ? 'hidden' : '';
    });

    mainNav.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => {
        mainNav.classList.remove('open');
        menuToggle.classList.remove('open');
        menuToggle.setAttribute('aria-expanded', 'false');
        document.body.style.overflow = '';
      });
    });

    const tabBtns = document.querySelectorAll('.tab-btn');
    const categories = document.querySelectorAll('.juice-category');

    tabBtns.forEach(btn => {
      btn.addEventListener('click', () => {
        tabBtns.forEach(b => b.classList.remove('active'));
        categories.forEach(c => c.classList.remove('active'));

        btn.classList.add('active');
        const target = document.getElementById(btn.dataset.target);
        target.classList.add('active');
        
        target.querySelectorAll('.juice-card').forEach(card => {
          card.classList.add('in-view');
        });
      });
    });

    const revealTargets = document.querySelectorAll(
      '.reveal-up, .reveal-scale, .reveal-left, .juice-card, .fries-card, .sauce-item, .combo-card'
    );

    const io = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('in-view');
          io.unobserve(entry.target);
        }
      });
    }, { threshold: 0.15, rootMargin: '0px 0px -60px 0px' });

    revealTargets.forEach(el => io.observe(el));

    document.querySelectorAll('.hero .reveal-up, .hero .reveal-scale').forEach(el => {
      requestAnimationFrame(() => el.classList.add('in-view'));
    });

    const staggerGroups = [
      document.querySelectorAll('.juice-card'),
      document.querySelectorAll('.fries-card'),
      document.querySelectorAll('.sauce-item'),
      document.querySelectorAll('.combo-card')
    ];
    staggerGroups.forEach(group => {
      group.forEach((el, i) => {
        el.style.transitionDelay = `${Math.min(i * 60, 480)}ms`;
      });
    });
  });
</script>
</body>
</html>
