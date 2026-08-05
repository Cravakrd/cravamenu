
<html lang="ckb" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CRAVA </title>
<meta name="description" content="کڕاڤە - شیرەی میوەی تازە و پەتاتەی گەرم، تەنها بۆ بردنەوە لە شەقامی کاوا">

<!-- Fonts: Noto Kufi Arabic for display headings, Vazirmatn for body text — both have full Kurdish/Sorani glyph support -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Kufi+Arabic:wght@500;700;800;900&family=Vazirmatn:wght@400;500;600;700&display=swap" rel="stylesheet">

<style>
/* ==========================================================================
   CRAVA — Design tokens
   Palette pulled directly from the CRAVA logo: forest green + mango gold,
   set against near-black (product-shot mood) and a warm cream (juice mood).
   ========================================================================== */
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

  --radius-lg: 28px;
  --radius-md: 18px;
  --radius-sm: 12px;

  --ease: cubic-bezier(.22,1,.36,1);
}

/* ==========================================================================
   Reset
   ========================================================================== */
*,*::before,*::after{ box-sizing:border-box; margin:0; padding:0; }
html{ scroll-behavior:smooth; }
body{
  font-family: var(--font-body);
  background: var(--cream);
  color: var(--text-dark);
  overflow-x: hidden;
  line-height: 1.6;
}
img{ max-width:100%; display:block; }
a{ color:inherit; text-decoration:none; }
ul{ list-style:none; }
button{ font-family:inherit; cursor:pointer; }
h1,h2,h3,h4,h5{ font-family: var(--font-display); line-height:1.25; }

/* respect reduced-motion users */
@media (prefers-reduced-motion: reduce){
  *{ animation-duration:0.01ms !important; animation-iteration-count:1 !important; transition-duration:0.01ms !important; scroll-behavior:auto !important; }
}

/* subtle film-grain texture layered over the whole page for depth */
.grain{
  position:fixed; inset:0; pointer-events:none; z-index:9999;
  opacity:.035; mix-blend-mode:overlay;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}

/* ==========================================================================
   Header
   ========================================================================== */
.site-header{
  position:fixed; inset-inline:0; top:0; z-index:1000;
  padding:18px 0;
  transition: padding .35s var(--ease), background-color .35s var(--ease), box-shadow .35s var(--ease);
}
.site-header.scrolled{
  padding:10px 0;
  background:rgba(16,22,15,.82);
  backdrop-filter: blur(14px);
  box-shadow:0 8px 30px rgba(0,0,0,.25);
}
.header-inner{
  max-width:1240px; margin:0 auto; padding:0 24px;
  display:flex; align-items:center; justify-content:space-between;
}
.brand-logo{ height:40px; width:auto; transition: height .35s var(--ease); }
.site-header.scrolled .brand-logo{ height:34px; }

.main-nav{ display:flex; gap:36px; }
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
  display:none; flex-direction:column; gap:5px; background:none; border:none; z-index:1100;
}
.menu-toggle span{ width:26px; height:2.5px; background:var(--white); border-radius:2px; transition: all .3s var(--ease); }
.menu-toggle.open span:nth-child(1){ transform:translateY(7.5px) rotate(45deg); }
.menu-toggle.open span:nth-child(2){ opacity:0; }
.menu-toggle.open span:nth-child(3){ transform:translateY(-7.5px) rotate(-45deg); }

/* ==========================================================================
   Hero
   ========================================================================== */
.hero{
  position:relative; min-height:100svh;
  display:flex; align-items:center; justify-content:center;
  background: radial-gradient(ellipse at 50% -10%, #1c3324 0%, var(--ink) 55%, var(--ink) 100%);
  overflow:hidden;
  padding: 140px 24px 100px;
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
  50%{ transform:translateY(-26px) rotate(8deg); }
}

.hero-inner{ position:relative; z-index:2; max-width:100%; padding:0 16px; }
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
.hero-actions{ display:flex; gap:16px; justify-content:center; flex-wrap:wrap; }

.btn{
  display:inline-flex; align-items:center; gap:10px;
  padding:15px 30px; border-radius:999px; font-weight:700; font-size:15px;
  transition: transform .3s var(--ease), box-shadow .3s var(--ease), background .3s var(--ease);
}
.btn-primary{
  background: linear-gradient(90deg,var(--gold),var(--gold-deep));
  color:var(--ink); box-shadow:0 10px 30px -8px rgba(245,166,35,.6);
}
.btn-primary svg{ transform:rotate(-90deg); }
.btn-primary:hover{ transform:translateY(-3px); box-shadow:0 16px 36px -8px rgba(245,166,35,.75); }
.btn-ghost{
  border:1.5px solid rgba(255,255,255,.35); color:var(--white);
}
.btn-ghost:hover{ background:rgba(255,255,255,.1); transform:translateY(-3px); }

.scroll-cue{
  position:absolute; bottom:28px; inset-inline-start:50%; transform:translateX(50%);
  width:26px; height:42px; border:2px solid rgba(255,255,255,.4); border-radius:20px;
}
.scroll-cue span{
  display:block; width:4px; height:8px; background:var(--gold); border-radius:2px;
  margin:6px auto; animation: scroll-dot 1.8s ease-in-out infinite;
}
@keyframes scroll-dot{
  0%{ transform:translateY(0); opacity:1; }
  70%{ transform:translateY(14px); opacity:0; }
  100%{ opacity:0; }
}

/* ==========================================================================
   Signature wave divider — echoes the swoosh in the CRAVA wordmark
   ========================================================================== */
.wave-divider{ line-height:0; margin-top:-2px; }
.wave-divider svg{ width:100%; height:60px; display:block; }
.wave-into-dark{ margin-top:-2px; }

/* ==========================================================================
   Section shells
   ========================================================================== */
.section-inner{ max-width:1240px; margin:0 auto; padding:90px 24px; }
.section-head{ max-width:640px; margin-bottom:56px; }
.section-head.light{ color:var(--white); }
.kicker{
  color:var(--forest); font-weight:700; font-size:14px; letter-spacing:.3px; margin-bottom:10px;
}
.section-head.light .kicker{ color:var(--gold-light); }
.section-title{ font-size:clamp(28px,4vw,42px); font-weight:800; margin-bottom:14px; color:var(--forest); }
.section-head.light .section-title{ color:var(--white); }
.section-desc{ color:var(--text-muted); font-size:16px; }
.section-head.light .section-desc{ color:#C9D1C3; }

/* ==========================================================================
   Item photos — plain, swappable JPGs
   Just replace the file at the given path (same filename) with your own
   photo to update what shows on a card. No code changes needed.
   ========================================================================== */
.item-photo{
  width:100%; aspect-ratio:1/1; border-radius:14px; overflow:hidden;
  margin-bottom:14px; background:var(--cream-2);
}
.item-photo img{
  width:100%; height:100%; object-fit:cover; display:block;
  transition: transform .5s var(--ease);
}
.item-photo-fries{
  width:64px; height:64px; aspect-ratio:auto; border-radius:12px;
  margin-bottom:0; flex-shrink:0; background:rgba(255,255,255,.06);
}
.fries-card:hover .item-photo-fries img{ transform:scale(1.1); }

/* ==========================================================================
   Juices
   ========================================================================== */
.juices{ background:var(--forest-dark); position:relative; }

.juice-card{ display:flex; flex-direction:column; }

.juice-feature{
  display:grid; grid-template-columns: .9fr 1.1fr; gap:48px; align-items:center;
  background:var(--white); border-radius:var(--radius-lg); padding:36px;
  box-shadow:0 30px 60px -30px rgba(27,77,46,.25); margin-bottom:64px;
}
.juice-feature-img{ position:relative; border-radius:var(--radius-md); overflow:hidden; }
.juice-feature-img img{
  width:100%; height:100%; object-fit:cover; aspect-ratio:1/1;
  transition: transform .6s var(--ease);
}
.juice-feature:hover .juice-feature-img img{ transform:scale(1.06) rotate(1deg); }
.juice-feature-badge{
  position:absolute; bottom:16px; inset-inline-start:16px;
  background:rgba(16,22,15,.75); backdrop-filter:blur(6px);
  color:var(--white); padding:10px 16px; border-radius:14px;
  display:flex; flex-direction:column; line-height:1.2;
}
.badge-num{ font-family:var(--font-display); font-weight:800; color:var(--gold-light); font-size:18px; }
.badge-txt{ font-size:12px; color:#D9DED4; }
.juice-feature-text h3{ font-size:26px; color:var(--forest); margin-bottom:14px; }
.juice-feature-text p{ color:var(--text-muted); font-size:15.5px; }

.juice-grid{
  display:grid; grid-template-columns:repeat(5,1fr); gap:18px;
}
.juice-card{
  background:var(--white); border-radius:var(--radius-md); padding:26px 18px;
  text-align:center; border:1px solid rgba(27,77,46,.08);
  transition: transform .35s var(--ease), box-shadow .35s var(--ease), border-color .35s var(--ease);
}
.juice-card:hover{
  transform:translateY(-8px) scale(1.02);
  box-shadow:0 22px 40px -20px rgba(27,77,46,.35);
  border-color:var(--gold);
}
.juice-card:hover .item-photo img{ transform:scale(1.12) rotate(-2deg); }
.juice-card h4{ font-size:15px; color:var(--text-dark); margin-bottom:10px; font-weight:700; min-height:40px; }
.juice-card .price{
  display:inline-block; font-weight:700; color:var(--forest); font-size:14px;
  background:var(--cream-2); padding:5px 14px; border-radius:999px;
}
.juice-card.featured{
  background: linear-gradient(160deg,var(--forest),var(--forest-dark)); color:var(--white);
  border-color:transparent;
}
.juice-card.featured h4{ color:var(--white); }
.juice-card.featured .price{ background:rgba(255,255,255,.15); color:var(--gold-light); }

/* ==========================================================================
   IceCrava — single-item section, sits between Juices and Fries
   ========================================================================== */
.icecrava{ background: linear-gradient(180deg,var(--cream-2) 0%, #FCE4B0 100%); }

.icecrava-card{
  display:flex; align-items:center; gap:44px;
  background:var(--white); border-radius:var(--radius-lg); padding:40px;
  box-shadow:0 30px 60px -30px rgba(217,136,18,.35);
  transition: transform .4s var(--ease), box-shadow .4s var(--ease);
}
.icecrava-card:hover{ transform:translateY(-6px); box-shadow:0 40px 70px -28px rgba(217,136,18,.45); }
.icecrava-icon{
  flex-shrink:0; width:150px; height:150px; border-radius:50%;
  overflow:hidden;
  background: radial-gradient(circle,var(--cream) 0%, var(--cream-2) 100%);
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

/* ==========================================================================
   Fries
   ========================================================================== */
.fries { 
  background: var(--gold-deep); /* یان var(--gold-light) بۆ زەردی کراوەتر */
  position: relative; 
  overflow: hidden; 
}
.fries-glow{ top:10%; inset-inline-start:50%; transform:translateX(-50%); opacity:.28; }

.fries-layout{
  display:grid; grid-template-columns: 1fr 1fr; gap:52px; align-items:center;
}
.fries-feature-img{
  position:relative; border-radius:var(--radius-lg); overflow:hidden;
  box-shadow:0 40px 80px -30px rgba(0,0,0,.6);
}
.fries-feature-img img{ transition: transform .7s var(--ease); }
.fries-feature-img:hover img{ transform:scale(1.05); }

.fries-cards{ display:flex; flex-direction:column; gap:14px; }
.fries-card{
  display:flex; align-items:center; gap:18px;
  background:rgba(255,255,255,.04); border:1px solid rgba(255,255,255,.08);
  border-radius:var(--radius-md); padding:18px 22px;
  transition: transform .3s var(--ease), background .3s var(--ease), border-color .3s var(--ease);
}
.fries-card:hover{
  transform:translateX(-6px); background:rgba(245,166,35,.08); border-color:var(--gold);
}
[dir="rtl"] .fries-card:hover{ transform:translateX(6px); }
.fc-body{ flex:1; }
.fc-body h4{ color:var(--white); font-size:17px; margin-bottom:4px; }
.fc-body p{ color:#A9B2A2; font-size:13.5px; }
.fries-card .price{ color:var(--gold-light); font-weight:700; font-size:14px; white-space:nowrap; }
.fries-card.featured{ background:linear-gradient(90deg,rgba(245,166,35,.16),rgba(245,166,35,.03)); border-color:var(--gold); }

/* ==========================================================================
   Sauces
   ========================================================================== */
.sauces{ background:var(--ink-2); padding-bottom:20px; }
.sauce-list{
  display:grid; grid-template-columns:repeat(5,1fr); gap:16px;
}
.sauce-item{
  background:rgba(255,255,255,.04); border:1px solid rgba(255,255,255,.08);
  border-radius:var(--radius-md); padding:22px 16px;
  display:flex; flex-direction:column; align-items:center; gap:10px; text-align:center;
  transition: transform .3s var(--ease), background .3s var(--ease);
}
.sauce-item:hover{ transform:translateY(-6px); background:rgba(255,255,255,.07); }
.sauce-dot{ width:26px; height:26px; border-radius:50%; box-shadow:inset 0 -3px 6px rgba(0,0,0,.2); }
.dot-red{ background:#D64545; }
.dot-white{ background:#F2EEE3; }
.dot-orange{ background:var(--gold); }
.dot-hot{ background:#E2572B; }
.dot-cream{ background:#EDE0C8; }
.sauce-name{ color:var(--white); font-weight:600; font-size:14.5px; }
.sauce-item .price{ color:var(--gold-light); font-size:13px; font-weight:700; }

/* ==========================================================================
   Takeaway marquee strip — signature motion moment
   ========================================================================== */
.takeaway-strip{
  background: linear-gradient(90deg,var(--gold-deep),var(--gold));
  overflow:hidden; padding:14px 0;
}
.marquee{ width:100%; overflow:hidden; }
.marquee-track{
  display:flex; gap:14px; white-space:nowrap; width:max-content;
  animation: marquee 3s linear infinite;
  font-family:var(--font-display); font-weight:800; font-size:15px; color:var(--ink);
}
.marquee-track span{ padding:0 6px; }
@keyframes marquee{
  from{ transform:translateX(0); }
  to{ transform:translateX(-50%); }
}
[dir="rtl"] .marquee-track{ animation-direction:reverse; }

/* ==========================================================================
   Footer
   ========================================================================== */
.site-footer{ background:var(--forest-dark); color:#D9DED4; padding-top:70px; }
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
  background:rgba(255,255,255,.06); border:1px solid rgba(255,255,255,.12);
  transition: transform .3s var(--ease), background .3s var(--ease), color .3s var(--ease);
}
.social-icon:hover{ background:var(--gold); color:var(--ink); transform:translateY(-4px) rotate(-6deg); }

.footer-bottom{
  border-top:1px solid rgba(255,255,255,.08); text-align:center; padding:22px 24px; font-size:13px; color:#8B9384;
}

/* ==========================================================================
   Scroll-reveal animation classes (toggled via JS/IntersectionObserver)
   ========================================================================== */
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

/* stagger juice/fries/sauce cards as they enter */
.juice-card.in-view, .fries-card.in-view, .sauce-item.in-view{ opacity:1; transform:none; }
.juice-card, .fries-card, .sauce-item{
  opacity:0; transform:translateY(20px);
  transition: opacity .6s var(--ease), transform .6s var(--ease), box-shadow .35s var(--ease), border-color .35s var(--ease), background .35s var(--ease);
}

/* ==========================================================================
   Responsive
   ========================================================================== */
@media (max-width: 980px){
  .juice-grid{ grid-template-columns:repeat(3,1fr); }
  .sauce-list{ grid-template-columns:repeat(3,1fr); }
  .footer-inner{ grid-template-columns:1fr 1fr; }
}

@media (max-width: 760px){
  .main-nav{
    position:fixed; inset-inline-end:0; top:0; height:100svh; width:min(78vw,320px);
    background:var(--ink); flex-direction:column; align-items:flex-start;
    padding:110px 32px 40px; gap:26px;
    transform:translateX(100%); transition: transform .4s var(--ease);
    z-index:1050;
  }
  [dir="rtl"] .main-nav{ transform:translateX(-100%); }
  .main-nav.open{ transform:translateX(0); }
  .main-nav a{ font-size:18px; }
  .menu-toggle{ display:flex; }

  .juice-feature{ grid-template-columns:1fr; }
  .fries-layout{ grid-template-columns:1fr; }
  .juice-grid{ grid-template-columns:repeat(2,1fr); }
  .sauce-list{ grid-template-columns:repeat(2,1fr); }
  .footer-inner{ grid-template-columns:1fr; text-align:center; }
  .social-row{ justify-content:center; }
  .section-inner{ padding:64px 20px; }

  .icecrava-card{ flex-direction:column; text-align:center; padding:32px 24px; }
  .icecrava-text p{ max-width:none; }
  .icecrava-icon{ width:130px; height:130px; }
}
 {
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

@media (max-width: 420px){
  .hero-title{ font-size:30px; }
  .btn{ padding:14px 22px; font-size:14px; }
  .juice-grid{ grid-template-columns:repeat(2,1fr); gap:12px; }
  .item-photo-fries{ width:52px; height:52px; }
  .fries-card{ gap:12px; padding:14px 16px; }
  .icecrava-icon{ width:110px; height:110px; }
}

</style>
</head>
<body>

<!-- ================= NOISE / GRAIN OVERLAY (purely decorative texture) ================= -->
<div class="grain" aria-hidden="true"></div>

<!-- ================= HEADER ================= -->
<header class="site-header" id="siteHeader">
  <div class="header-inner">
    <a href="#hero" class="brand">
      <img src="
      crrrlogo.jpg" alt="کڕاڤە" class="brand-logo">
    </a>

    <nav class="main-nav" id="mainNav">
      <a href="#juices">شەربەتی میوە</a>
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
  <!-- ambient glow blobs -->
  <div class="hero-glow glow-green" aria-hidden="true"></div>
  <div class="hero-glow glow-gold" aria-hidden="true"></div>

  <!-- floating fruit / fry particles -->
  <div class="floaters" aria-hidden="true">
    <span class="floater f1">🍊</span>
    <span class="floater f2">🍓</span>
    <span class="floater f3">🥝</span>
    <span class="floater f4">🍍</span>
    <span class="floater f5">🍉</span>
  </div>

  <div class="hero-inner">
    <img src="crrrlogo.jpg" alt="کڕاڤە" class="hero-logo reveal-scale">

    <p class="eyebrow reveal-up delay-1"></p>
    <h1 class="hero-title reveal-up delay-2">
    بەخێربێن <br>
      <span class="accent-text"> بۆ کڕاڤا </span>
    </h1>
    <p class="hero-sub reveal-up delay-3">شەربەتی میوەی فرێش و پەتاتەی گەرمی تازە بە جۆرەها تامی جیاواز لەگەڵ CRAVA تاقی بکەرەوە.
    </p>

    <div class="hero-actions reveal-up delay-4">
      <a href="#juices" class="btn btn-primary">
        <span>بینینی مینیو</span>
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M12 5v14M5 12l7 7 7-7" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </a>
      <a href="#footer" class="btn btn-ghost">شوێنمان بزانە</a>
    </div>
  </div>

  <div class="scroll-cue" aria-hidden="true"><span></span></div>
</section>

<!-- ================= SIGNATURE WAVE DIVIDER ================= -->
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

<!-- ================= JUICE SECTION ================= -->
<section class="juices" id="juices">
  <div class="section-inner">

    <div class="section-head">
      <p class="kicker reveal-up">تازە · سروشتی · بەبێ شەکری زیادە</p>
      <h2 class="section-title reveal-up">شیرەی میوەی تازە</h2>
      <p class="section-desc reveal-up">١٥ جۆر شیرەی میوەی تازە، هەر ڕۆژێک لە میوەی ڕەسەن دروست دەکرێت.</p>
    </div>

    <div class="juice-feature reveal-up">
      <div class="juice-feature-img">
        <img src="crglas.jpg" alt="شیرەی میوەی تازەی کڕاڤە" loading="lazy">
        <div class="juice-feature-badge">
          <span class="badge-num">١٠٠٪</span>
          <span class="badge-txt">میوەی سروشتی</span>
        </div>
      </div>
      <div class="juice-feature-text">
        <h3>لە میوە بۆ گیلاس، لەبەردەم چاوت</h3>
        <p>هەموو شیرەیەک لە میوەی تازەی ئەو ڕۆژە دروست دەکرێت، بەبێ کۆنسێرڤ و بەبێ شەکری دەرەکی. تامی ڕاستەقینەی میوە، هەر کاتێک پێویستت پێی بوو.</p>
      </div>
    </div>

    <div class="juice-grid">
      <!-- 15 juice items — placeholder names & prices, easy to swap later.
           Each card photo is a plain <img>: just replace the file in images/juice/
           (keep the same filename) with your own JPG to update the photo. -->
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-01.jpg" alt="شیرەی پرتەقاڵ" loading="lazy"></div><h4>شیرەی پرتەقاڵ</h4><span class="price">٢٥٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-02.jpg" alt="شیرەی لیمۆ و نەعنا" loading="lazy"></div><h4>شیرەی لیمۆ و نەعنا</h4><span class="price">٢٥٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-03.jpg" alt="شیرەی تووی فەرەنگی" loading="lazy"></div><h4>شیرەی تووی فەرەنگی</h4><span class="price">٣٠٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-04.jpg" alt="شیرەی مانگۆ" loading="lazy"></div><h4>شیرەی مانگۆ</h4><span class="price">٣٠٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-05.jpg" alt="شیرەی بەتیخ" loading="lazy"></div><h4>شیرەی بەتیخ</h4><span class="price">٢٠٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-06.jpg" alt="شیرەی ئەناناس" loading="lazy"></div><h4>شیرەی ئەناناس</h4><span class="price">٣٠٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-07.jpg" alt="شیرەی کیوی" loading="lazy"></div><h4>شیرەی کیوی</h4><span class="price">٣٥٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-08.jpg" alt="شیرەی سێو" loading="lazy"></div><h4>شیرەی سێو</h4><span class="price">٢٥٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-09.jpg" alt="شیرەی تیرێ" loading="lazy"></div><h4>شیرەی تیرێ</h4><span class="price">٣٠٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-10.jpg" alt="شیرەی شەفتاڵوو" loading="lazy"></div><h4>شیرەی شەفتاڵوو</h4><span class="price">٣٠٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-11.jpg" alt="شیرەی هەنار" loading="lazy"></div><h4>شیرەی هەنار</h4><span class="price">٣٥٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-12.jpg" alt="شیرەی مۆز و شیر" loading="lazy"></div><h4>شیرەی مۆز و شیر</h4><span class="price">٣٠٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-13.jpg" alt="شیرەی گێلاس" loading="lazy"></div><h4>شیرەی گێلاس</h4><span class="price">٣٥٠٠ د.ع</span></article>
      <article class="juice-card"><div class="item-photo"><img src="images/juice/juice-14.jpg" alt="شیرەی گوێز و نارگیل" loading="lazy"></div><h4>شیرەی گوێز و نارگیل</h4><span class="price">٣٥٠٠ د.ع</span></article>
      <article class="juice-card featured"><div class="item-photo"><img src="images/juice/juice-15.jpg" alt="تایبەتی کڕاڤە" loading="lazy"></div><h4>تایبەتی کڕاڤە — تێکەڵی گەرمسێری</h4><span class="price">٤٠٠٠ د.ع</span></article>
    </div>
  </div>
</section>

<!-- ================= WAVE DIVIDER (juice → icecrava) ================= -->
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

<!-- ================= ICECRAVA SECTION (single item, directly under Juices) ================= -->
<section class="icecrava" id="icecrava">
  <div class="section-inner">
    <div class="section-head">
      <p class="kicker reveal-up">نوێ · سارد و کرێمی</p>
      <h2 class="section-title reveal-up">ICECRAVA</h2>
      <p class="section-desc reveal-up">ئایسکریمی تایبەتی کڕاڤە — یەک تامی نایاب، دروستکراو لە کاوا ستریت.</p>
    </div>

    <div class="icecrava-card reveal-up">
      <div class="icecrava-icon">
        <img src="images/icecrava.jpg" alt="ئایسکڕیمی کڕاڤە" loading="lazy">
      </div>
      <div class="icecrava-text">
        <span class="icecrava-tag">تاکە تام</span>
        <h3>ئایسکڕیمی کڕاڤە</h3>
        <p>کرێمی سارد و نەرم، تێکەڵ لەگەڵ تامی میوەی تازە و تامی تایبەتی کڕاڤە. کۆتایی خۆشی ژەمەکەت.</p>
        <span class="price">٣٥٠٠ د.ع</span>
      </div>
    </div>
  </div>
</section>

<!-- ================= WAVE DIVIDER (inverted, into dark fries section) ================= -->
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

<!-- ================= FRIES SECTION ================= -->
<section class="fries" id="fries">
  <div class="hero-glow glow-gold fries-glow" aria-hidden="true"></div>

  <div class="section-inner">
    <div class="section-head ">
      <p class="kicker reveal-up">ترسکە · گەرم · تازە سرخکراو</p>
      <h2 class="section-title reveal-up">پەتاتەی کڕاڤە</h2>
      <p class="section-desc reveal-up">٥ جۆری تایبەت، هەموویان تازە دەسرخرێن دوای داواکردن.</p>
    </div>

    <div class="fries-layout">
      <div class="fries-feature-img reveal-left">
        <img src="crbox.jpg" alt="پەتاتەی ترسکەی کڕاڤە" loading="lazy">
      </div>

      <div class="fries-cards">
        <article class="fries-card reveal-up">
          <div class="item-photo item-photo-fries"><img src="images/fries/fries-01.jpg" alt="پەتاتەی کلاسیک" loading="lazy"></div>
          <div class="fc-body">
            <h4>پەتاتەی کلاسیک</h4>
            <p>پەتاتەی ترسکەی سادە لەگەڵ خوێی تایبەت</p>
          </div>
          <span class="price">٢٠٠٠ د.ع</span>
        </article>
        <article class="fries-card reveal-up">
          <div class="item-photo item-photo-fries"><img src="images/fries/fries-02.jpg" alt="پەتاتەی پەنیر" loading="lazy"></div>
          <div class="fc-body">
            <h4>پەتاتەی پەنیر</h4>
            <p>داپۆشراو بە سۆسی پەنیری گەرم</p>
          </div>
          <span class="price">٣٠٠٠ د.ع</span>
        </article>
        <article class="fries-card reveal-up">
          <div class="item-photo item-photo-fries"><img src="images/fries/fries-03.jpg" alt="پەتاتەی تیخ" loading="lazy"></div>
          <div class="fc-body">
            <h4>پەتاتەی تیخ</h4>
            <p>بەهاراتی تیژ بۆ ئەوانەی حەز لە تام دەکەن</p>
          </div>
          <span class="price">٢٥٠٠ د.ع</span>
        </article>
        <article class="fries-card reveal-up">
          <div class="item-photo item-photo-fries"><img src="images/fries/fries-04.jpg" alt="پەتاتەی سیر و مایۆنێز" loading="lazy"></div>
          <div class="fc-body">
            <h4>پەتاتەی سیر و مایۆنێز</h4>
            <p>تامێکی کرێمی لەگەڵ بۆنی سیری تازە</p>
          </div>
          <span class="price">٢٥٠٠ د.ع</span>
        </article>
        <article class="fries-card reveal-up featured">
          <div class="item-photo item-photo-fries"><img src="images/fries/fries-05.jpg" alt="پەتاتەی تایبەتی کڕاڤە" loading="lazy"></div>
          <div class="fc-body">
            <h4>پەتاتەی تایبەتی کڕاڤە</h4>
            <p>تێکەڵەی هەموو سۆسەکان + پارچە گۆشتی تایبەت</p>
          </div>
          <span class="price">٤٥٠٠ د.ع</span>
        </article>
      </div>
    </div>
  </div>
</section>

<!-- ================= SAUCES SECTION (directly under fries) ================= -->
<section class="sauces" id="sauces">
  <div class="section-inner">
    <div class="section-head light">
      <p class="kicker reveal-up">تاماوییەکان</p>
      <h2 class="section-title reveal-up">سۆسەکان</h2>
      <p class="section-desc reveal-up">هەر سۆسێک بە تامێکی جیاواز، هاوڕێی چاکی پەتاتەکەت.</p>
    </div>

    <ul class="sauce-list">
      <li class="sauce-item reveal-up"><span class="sauce-dot dot-red"></span><span class="sauce-name">کێچەپ</span><span class="price">٥٠٠ د.ع</span></li>
      <li class="sauce-item reveal-up"><span class="sauce-dot dot-white"></span><span class="sauce-name">مایۆنێز</span><span class="price">٥٠٠ د.ع</span></li>
      <li class="sauce-item reveal-up"><span class="sauce-dot dot-orange"></span><span class="sauce-name">سۆسی تایبەتی کڕاڤە</span><span class="price">٧٥٠ د.ع</span></li>
      <li class="sauce-item reveal-up"><span class="sauce-dot dot-hot"></span><span class="sauce-name">سۆسی تیخ</span><span class="price">٥٠٠ د.ع</span></li>
      <li class="sauce-item reveal-up"><span class="sauce-dot dot-cream"></span><span class="sauce-name">سۆسی سیر</span><span class="price">٥٠٠ د.ع</span></li>
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
      <p class="takeaway-note"> شەقامی کاوە(حریق)-بەرامبەر LC Waikiki </p>
    </div>

    <div class="footer-col">
      <h5>کراوەیە لە</h5>
      <p></p>
      <p>٤:٠٠ دوای نیوەڕۆ  تاوەکو  ١٢:٠٠ شەو</p>
    </div>

 
    <div class="footer-col">
      <h5>لەگەڵمان بن</h5>
      <div class="social-row">
        <a href="https://www.instagram.com/crava.krd?igsh=MWlodnU3aW9oa3Q5ag%3D%3D&utm_source=qr" class="social-icon" aria-label="ئینستاگرام">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><rect x="3" y="3" width="18" height="18" rx="5" stroke="currentColor" stroke-width="1.8"/><circle cx="12" cy="12" r="4" stroke="currentColor" stroke-width="1.8"/><circle cx="17.5" cy="6.5" r="1.2" fill="currentColor"/></svg>
        </a>
        <a href="#" class="social-icon" aria-label="فەیسبووک">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M14 8.5h2.5V5h-2.5c-2.2 0-4 1.8-4 4v2H8v3.5h2.5V21h3.5v-6.5h2.5l.5-3.5h-3V9c0-.6.4-.5 1-.5z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/></svg>
        </a>
        <a href="#" class="social-icon" aria-label="تیک تۆک">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M15 3c.4 2.2 2 3.8 4 4v3c-1.5 0-2.9-.4-4-1.2V15a5 5 0 1 1-5-5v3a2 2 0 1 0 2 2V3h3z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/></svg>
        </a>
        <a href="#" class="social-icon" aria-label="واتساپ">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M12 21a9 9 0 1 0-7.8-4.5L3 21l4.6-1.2A9 9 0 0 0 12 21z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/><path d="M8.5 9.5c0 4 3 6.5 6.5 6.5.6 0 1.5-.2 1.5-1v-1.3l-2-1-1 1c-1-.4-2.2-1.6-2.7-2.7l1-1-1-2H9c-.4 0-.5.7-.5 1.5z" fill="currentColor"/></svg>
      <!-- Snapchat -->
<a href="https://www.instagram.com/crava.krd?igsh=MWlodnU3aW9oa3Q5ag%3D%3D&utm_source=qr" target="_blank" class="social-icon" aria-label="سنەپچات">
  <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
    <path d="M12 2c-2.5 0-4.5 2-4.5 4.5v2c0 .5-.3 1-.8 1.2l-1 .5c-.3.2-.4.6-.2.9.4.5 1 .8 1.6.9.4.1.7.5.6.9-.3 1.4-1.3 2.5-2.6 2.9-.2.1-.3.3-.2.5.3.5 1 .8 1.7.8.7 0 1.3.4 1.6 1 .4.8 1.2 1.3 2.1 1.3h3.4c.9 0 1.7-.5 2.1-1.3.3-.6.9-1 1.6-1 .7 0 1.4-.3 1.7-.8.1-.2 0-.4-.2-.5-1.3-.4-2.3-1.5-2.6-2.9-.1-.4.2-.8.6-.9.6-.1 1.2-.4 1.6-.9.2-.3.1-.7-.2-.9l-1-.5c-.5-.2-.8-.7-.8-1.2v-2C16.5 4 14.5 2 12 2z"/>
  </svg>
</a>
    
        </a>
      </div>
    </div>
  </div>


  <div class="footer-bottom">
    <p>© ٢٠٢٦ کڕاڤە.   </p>
  </div>
</footer>

<script>
/* ==========================================================================
   CRAVA — site interactions
   1) Header shrinks + gains background after scrolling past the hero
   2) Mobile hamburger menu toggle
   3) Scroll-reveal animations via IntersectionObserver (fires once per element)
   ========================================================================== */

document.addEventListener('DOMContentLoaded', () => {

  /* ---------- 1) Sticky header state ---------- */
  const header = document.getElementById('siteHeader');
  const onScroll = () => {
    if (window.scrollY > 40) header.classList.add('scrolled');
    else header.classList.remove('scrolled');
  };
  window.addEventListener('scroll', onScroll, { passive: true });
  onScroll();

  /* ---------- 2) Mobile nav toggle ---------- */
  const menuToggle = document.getElementById('menuToggle');
  const mainNav = document.getElementById('mainNav');

  menuToggle.addEventListener('click', () => {
    const isOpen = mainNav.classList.toggle('open');
    menuToggle.classList.toggle('open', isOpen);
    menuToggle.setAttribute('aria-expanded', String(isOpen));
    document.body.style.overflow = isOpen ? 'hidden' : '';
  });

  // close mobile nav when a link is tapped
  mainNav.querySelectorAll('a').forEach(link => {
    link.addEventListener('click', () => {
      mainNav.classList.remove('open');
      menuToggle.classList.remove('open');
      menuToggle.setAttribute('aria-expanded', 'false');
      document.body.style.overflow = '';
    });
  });

  /* ---------- 3) Scroll-reveal ---------- */
  const revealTargets = document.querySelectorAll(
    '.reveal-up, .reveal-scale, .reveal-left, .juice-card, .fries-card, .sauce-item'
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

  // hero content is above the fold — reveal immediately on load, no scroll needed
  document.querySelectorAll('.hero .reveal-up, .hero .reveal-scale').forEach(el => {
    requestAnimationFrame(() => el.classList.add('in-view'));
  });

  /* stagger the card grids slightly for a livelier cascade */
  const staggerGroups = [
    document.querySelectorAll('.juice-card'),
    document.querySelectorAll('.fries-card'),
    document.querySelectorAll('.sauce-item')
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
