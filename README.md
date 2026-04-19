<html lang="en" data-theme="dark">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>DRIVAYAN — Where Every Drive Tells a Story</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="DRIVAYAN - Cinematic journeys, owner stories, and Indian car culture decoded.">
<meta property="og:title" content="DRIVAYAN — Where Every Drive Tells a Story">
<meta property="og:type" content="website">

<link rel="preconnect" href="https://fonts.googleapis.com/">
<link rel="preconnect" href="https://fonts.gstatic.com/" crossorigin="">
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;700;900&family=Playfair+Display:ital,wght@0,400;0,500;1,400;1,500&family=JetBrains+Mono:wght@400;700;800&display=swap" rel="stylesheet">

<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

<script>
  (function() {
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme) document.documentElement.setAttribute('data-theme', savedTheme);
  })();
</script>

<style>
  /* ===== THEME VARIABLES ===== */
  :root {
    --bg: #050505;
    --card: rgba(255,255,255,0.03);
    --border: rgba(255,255,255,0.08);
    --text: #ffffff;
    --muted: #888888;
    --accent: #ffffff;
    --nav-bg: rgba(5,5,5,0.85);
    --gold: #c8a96e;
    --gold-dim: rgba(200,169,110,0.12);
    --card-solid: #0d0d0d;
  }
  [data-theme="light"] {
    --bg: #fdfdfd;
    --card: #ffffff;
    --border: rgba(0,0,0,0.06);
    --text: #0a0a0a;
    --muted: #666666;
    --accent: #000000;
    --nav-bg: rgba(253,253,253,0.85);
    --gold: #9a6f2e;
    --gold-dim: rgba(154,111,46,0.1);
    --card-solid: #f0efe9;
  }

  /* ===== RESET ===== */
  * { margin:0; padding:0; box-sizing:border-box; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Montserrat', sans-serif;
    line-height: 1.7;
    overflow-x: hidden;
    -webkit-font-smoothing: antialiased;
    transition: background 0.5s ease;
  }

  /* ===== PROGRESS BAR ===== */
  #progress-wrap { position:fixed; top:0; left:0; width:100%; height:2px; z-index:2001; }
  #progress-bar  { width:0%; height:100%; background:var(--text); }

  /* ===== SIDE SPECS ===== */
  .side-specs {
    position:fixed; right:30px; top:50%;
    transform:translateY(-50%) rotate(90deg);
    transform-origin:right center;
    display:flex; gap:40px; z-index:10;
    pointer-events:none; opacity:0.4;
  }
  .spec-item {
    font-family:'JetBrains Mono',monospace;
    font-size:9px; letter-spacing:2px;
    text-transform:uppercase; color:var(--muted);
  }

  /* ===== LABEL ===== */
  .label {
    font-size:9px; font-weight:800; letter-spacing:4px;
    text-transform:uppercase; color:var(--muted);
    margin-bottom:15px; display:block;
  }
  h1,h2,h3,h4 {
    font-family:'Playfair Display',serif;
    font-weight:500; letter-spacing:-0.02em;
  }

  /* ===== NAVIGATION ===== */
  nav {
    position:fixed; top:0; width:100%; padding:35px 8%;
    display:flex; justify-content:space-between; align-items:center;
    z-index:1000; backdrop-filter:blur(25px); background:var(--nav-bg);
    border-bottom:1px solid var(--border);
    transition:all 0.6s cubic-bezier(0.16,1,0.3,1);
  }
  nav.scrolled { padding:18px 8%; }
  .brand { font-weight:900; letter-spacing:8px; text-decoration:none; color:var(--text); font-size:1.1rem; }
  .nav-links { display:flex; align-items:center; position:relative; gap:10px; }
  nav a { color:var(--muted); padding:10px 20px; font-size:9px; font-weight:700; letter-spacing:2px; text-decoration:none; transition:color 0.3s ease; }
  nav a:hover, nav a.active { color:var(--text); }
  .nav-pill { position:absolute; height:35px; background:var(--card); border:1px solid var(--border); border-radius:30px; z-index:-1; pointer-events:none; }

  /* ===== DROPDOWN HOVER MENUS ===== */
  .nav-item-wrap {
    position: relative;
    display: inline-flex;
    align-items: center;
  }

  .nav-item-wrap > .nav-item {
    position: relative;
    z-index: 1;
  }

  /* The chevron indicator */
  .nav-item-wrap.has-dropdown > .nav-item::after {
    content: '';
    display: inline-block;
    width: 4px;
    height: 4px;
    border-right: 1px solid var(--muted);
    border-bottom: 1px solid var(--muted);
    transform: rotate(45deg) translateY(-2px);
    margin-left: 6px;
    transition: transform 0.3s ease, border-color 0.3s ease;
    vertical-align: middle;
  }

  .nav-item-wrap.has-dropdown:hover > .nav-item::after {
    transform: rotate(225deg) translateY(-2px);
    border-color: var(--text);
  }

  /* Dropdown panel */
  .nav-dropdown {
    position: absolute;
    top: calc(100% + 18px);
    left: 50%;
    transform: translateX(-50%) translateY(-6px);
    min-width: 200px;
    background: var(--nav-bg);
    border: 1px solid var(--border);
    backdrop-filter: blur(30px);
    -webkit-backdrop-filter: blur(30px);
    padding: 8px 0;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.25s cubic-bezier(0.16,1,0.3,1),
                transform 0.25s cubic-bezier(0.16,1,0.3,1);
    z-index: 500;
  }

  /* Invisible bridge so mouse can travel from pill to dropdown */
  .nav-dropdown::before {
    content: '';
    position: absolute;
    top: -20px;
    left: 0;
    width: 100%;
    height: 20px;
  }

  /* Top accent line */
  .nav-dropdown::after {
    content: '';
    position: absolute;
    top: -1px;
    left: 20%;
    width: 60%;
    height: 1px;
    background: var(--text);
    opacity: 0.5;
  }

  .nav-item-wrap:hover .nav-dropdown {
    opacity: 1;
    pointer-events: all;
    transform: translateX(-50%) translateY(0);
  }

  /* Dropdown items */
  .nav-dropdown a {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 10px 20px;
    font-size: 9px;
    font-weight: 700;
    letter-spacing: 2px;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s, padding-left 0.2s;
    white-space: nowrap;
    border-left: 2px solid transparent;
  }

  .nav-dropdown a:hover {
    color: var(--text);
    padding-left: 26px;
    border-left-color: var(--text);
  }

  .nav-dropdown a .dd-icon {
    font-size: 10px;
    opacity: 0.5;
    flex-shrink: 0;
    font-style: normal;
  }

  .nav-dropdown .dd-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 8px;
    color: var(--muted);
    letter-spacing: 3px;
    padding: 10px 20px 4px;
    opacity: 0.5;
    display: block;
    text-transform: uppercase;
  }

  .nav-dropdown .dd-divider {
    height: 1px;
    background: var(--border);
    margin: 6px 20px;
  }

  .menu-trigger { display:none; background:none; border:none; color:var(--text); cursor:pointer; z-index:1001; }
  .mobile-overlay {
    position:fixed; top:0; left:0; width:100%; height:100%;
    background:var(--bg); z-index:999;
    display:flex; flex-direction:column; align-items:center; justify-content:center;
    gap:30px; transform:translateY(-100%);
    transition:transform 0.6s cubic-bezier(0.16,1,0.3,1);
  }
  .mobile-overlay.active { transform:translateY(0); }
  .mobile-overlay a { font-size:1.5rem; text-decoration:none; color:var(--text); font-family:'Playfair Display'; }

  /* ===== THEME TOGGLE ===== */
  .theme-toggle-btn {
    background:var(--card); border:1px solid var(--border); color:var(--text);
    width:45px; height:45px; border-radius:50%;
    display:flex; align-items:center; justify-content:center;
    cursor:pointer; transition:0.4s;
  }
  .theme-logo { filter:grayscale(1) brightness(2); transition:filter 0.5s ease, transform 0.5s ease; }
  [data-theme="light"] .theme-logo { filter:invert(1) grayscale(1) brightness(0.2); }

  /* ===== SECTIONS ===== */
  section { padding:100px 8%; }

  /* ===== HERO ===== */
  .hero {
    min-height:100vh; padding:160px 8% 100px;
    display:flex; align-items:center; justify-content:space-between; gap:80px;
  }
  .hero-content { flex:1; max-width:600px; }
  .hero h1 { font-size:clamp(3.5rem,8vw,6rem); line-height:1; margin-bottom:30px; }
  .hero p { margin-bottom:45px; color:var(--muted); font-size:1.2rem; font-weight:300; max-width:450px; }
  .hero-img-wrap { flex:1.2; position:relative; display:flex; justify-content:center; }
  .hero img { width:100%; max-width:500px; display:block; object-fit:contain; }

  /* ===== CTA ===== */
  .cta {
    display:inline-flex; align-items:center; padding:20px 45px;
    border:1px solid var(--text); font-size:10px; font-weight:800; letter-spacing:4px;
    text-decoration:none; color:var(--text); position:relative; overflow:hidden; transition:0.4s;
  }
  .cta:hover { color:var(--bg); background:var(--text); }

  /* ===== NEWS TICKER ===== */
  .news-ticker-wrap {
    width:100%; background:var(--card);
    border-top:1px solid var(--border); border-bottom:1px solid var(--border);
    padding:12px 0; overflow:hidden; white-space:nowrap; margin-bottom:40px;
  }
  .ticker-content { display:inline-block; animation:ticker 60s linear infinite; }
  .news-item {
    display:inline-block; font-family:'JetBrains Mono',monospace;
    font-size:10px; color:var(--text); text-decoration:none;
    padding-right:50px; text-transform:uppercase; letter-spacing:1px;
  }
  .news-item span { color:var(--muted); margin-right:10px; }
  @keyframes ticker { 0%{transform:translateX(0)} 100%{transform:translateX(-50%)} }

  /* ===== FEATURED ===== */
  .section-title { margin-bottom:40px; }
  .featured { display:grid; grid-template-columns:1.8fr 1fr; gap:40px; margin-bottom:80px; }
  .featured-main {
    position:relative; border-radius:12px; overflow:hidden;
    aspect-ratio:16/9; display:block; text-decoration:none;
  }
  .featured-main img { width:100%; height:100%; object-fit:cover; transition:1.2s cubic-bezier(0.16,1,0.3,1); }
  .featured-main:hover img { transform:scale(1.05); }
  .featured-text {
    position:absolute; bottom:0; left:0; width:100%; padding:60px;
    background:linear-gradient(transparent,rgba(0,0,0,0.85));
  }
  .side-card {
    padding:30px 0; border-bottom:1px solid var(--border);
    transition:0.3s; cursor:pointer; display:block; text-decoration:none; color:inherit;
  }
  .side-card:hover { padding-left:15px; border-bottom-color:var(--text); }

  /* ===== CAR GRID ===== */
  .car-grid-container {
    display:grid;
    grid-template-columns:repeat(auto-fill,minmax(320px,1fr));
    gap:30px;
    padding:20px 0;
  }
  .car-card {
    background:var(--card); border:1px solid var(--border);
    transition:all 0.5s cubic-bezier(0.16,1,0.3,1);
    text-decoration:none; color:inherit; display:block; position:relative;
  }
  .car-card:hover { border-color:var(--text); transform:translateY(-5px); }
  .car-card .img-box { aspect-ratio:16/9; overflow:hidden; background:#111; }
  .car-card img { width:100%; height:100%; object-fit:cover; opacity:0.8; transition:0.8s; }
  .car-card:hover img { opacity:1; scale:1.05; }
  .car-info { padding:25px; }
  .car-meta {
    font-family:'JetBrains Mono',monospace; font-size:9px;
    color:var(--muted); letter-spacing:1px; text-transform:uppercase;
    display:flex; justify-content:space-between; margin-bottom:10px;
  }

  /* ===== JOURNEY CARDS ===== */
  .grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(350px,1fr)); gap:40px; }
  .card {
    background:var(--card); border:1px solid var(--border); padding:25px;
    transition:all 0.5s cubic-bezier(0.16,1,0.3,1);
    text-decoration:none; color:inherit; display:block;
  }
  .card:hover { border-color:rgba(255,255,255,0.25); transform:translateY(-10px); }
  .img-container { overflow:hidden; border-radius:4px; margin-bottom:25px; aspect-ratio:16/10; position:relative; }
  .card img { width:100%; height:100%; object-fit:cover; transition:0.8s; }

  /* ===== SPEC HUD ===== */
  .spec-hud {
    position:absolute; inset:0;
    background:rgba(0,0,0,0.7); backdrop-filter:blur(4px);
    display:flex; flex-direction:column; justify-content:center;
    padding:20px; opacity:0; transition:opacity 0.4s ease; z-index:2;
  }
  .card:hover .spec-hud { opacity:1; }
  .hud-line {
    display:flex; justify-content:space-between;
    border-bottom:1px solid rgba(255,255,255,0.1);
    padding:8px 0; font-family:'JetBrains Mono',monospace;
    font-size:10px; text-transform:uppercase; color:var(--text);
  }
  .hud-value { font-weight:800; color:#fff; }

  /* ===== SAFARNAMA ===== */
  .safarnama-container { display:flex; gap:60px; align-items:center; margin:40px 0; }
  .safarnama-img ('C:\Users\user\Desktop\DRIVAYAN ALL FILES\Exterior.jpg?auto=format&fit=crop&q=80&w=1200')
    flex:1; height:600px;
    background:url('C:\Users\user\Desktop\DRIVAYAN ALL FILES\Exterior.jpg?auto=format&fit=crop&q=80&w=1200') center/cover;
    border-radius:4px;
  }
  .safarnama-content { flex:1; }
  .safarnama-content h2 { font-size:3.5rem; margin-bottom:20px; font-style:italic; }

  /* ===== LAUNCH PAD ===== */
  .launch-grid {
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(300px,1fr));
    gap:1px;
    background:var(--border);
    border:1px solid var(--border);
  }
  .launch-card {
    background:var(--bg); padding:30px;
    transition:background 0.3s ease;
    text-decoration:none; color:inherit;
  }
  .launch-card:hover { background:var(--card); }
  .status-tag {
    font-family:'JetBrains Mono',monospace; font-size:9px;
    padding:2px 8px; border:1px solid var(--text);
    display:inline-block; margin-bottom:15px;
  }
  .status-live { background:var(--text); color:var(--bg); }
  .launch-date {
    font-family:'JetBrains Mono',monospace; font-size:11px;
    color:var(--muted); display:block; margin-top:10px;
  }

  /* ===== GEAR & GUPSHUP — FIX: was completely missing ===== */
  .gupshup-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 40px;
  }
  .gupshup-item {
    position: relative;
    padding: 30px;
    border: 1px solid var(--border);
    background: var(--card);
    transition: border-color 0.3s ease;
  }
  .gupshup-item:hover { border-color: var(--text); }
  .scanner-line {
    position:absolute; top:0; left:0; width:100%; height:1px;
    background:linear-gradient(90deg,transparent 0%,var(--text) 50%,transparent 100%);
    opacity:0; pointer-events:none; z-index:5;
    box-shadow:0 0 8px var(--text);
  }

  /* ===== COMMUNITY REVIEW SECTION ===== */
  .reviews-section { padding: 0; }
  .review-form { margin-bottom: 60px; }
  .review-input {
    width:100%; background:transparent; border:none;
    border-bottom:1px solid var(--border); padding:15px 0;
    color:var(--text); font-family:'Montserrat'; font-size:13px;
    margin-bottom:20px; outline:none; transition:0.3s; display:block;
  }
  .review-input:focus { border-bottom-color:var(--text); }
  .rating-selector { display:flex; gap:10px; margin-bottom:25px; cursor:pointer; }
  .star { font-size:24px; color:var(--border); transition:all 0.3s cubic-bezier(0.16,1,0.3,1); }
  .star.active, .star:hover { color:var(--text); text-shadow:0 0 10px rgba(255,255,255,0.3); transform:scale(1.2); }
  .review-card {
    background:var(--card); border:1px solid var(--border); padding:30px;
    margin-bottom:20px; display:grid;
    grid-template-columns:60px 1fr auto; gap:20px; align-items:start;
  }
  .driver-avatar {
    width:50px; height:50px; background:var(--border);
    display:flex; align-items:center; justify-content:center;
    font-family:'JetBrains Mono'; font-size:12px;
  }

  /* ===== LOGIN OVERLAY ===== */
  .login-overlay {
    position:fixed; inset:0; background:var(--bg); z-index:2000;
    display:flex; align-items:center; justify-content:center;
    opacity:0; pointer-events:none;
    transition:0.6s cubic-bezier(0.16,1,0.3,1); backdrop-filter:blur(20px);
  }
  .login-overlay.active { opacity:1; pointer-events:all; }
  .login-card {
    width:100%; max-width:400px; padding:60px;
    border:1px solid var(--border); background:var(--card);
    text-align:center; position:relative;
  }
  .login-card h2 { font-size:2rem; margin-bottom:30px; }
  .login-field {
    width:100%; background:transparent; border:none;
    border-bottom:1px solid var(--border); padding:15px 0;
    color:var(--text); font-family:'Montserrat'; font-size:13px;
    margin-bottom:20px; outline:none; transition:0.3s;
  }
  .login-field:focus { border-bottom-color:var(--text); }
  .login-btn {
    width:100%; background:var(--text); color:var(--bg); border:none;
    padding:18px; font-size:10px; font-weight:800; letter-spacing:3px;
    cursor:pointer; margin-top:20px; transition:0.3s;
  }
  .login-btn:hover { opacity:0.9; transform:translateY(-2px); }
  .close-login { position:absolute; top:20px; right:20px; cursor:pointer; color:var(--muted); font-size:12px; letter-spacing:2px; }

  /* ===== ABOUT ===== */
  .about-logo { width:280px; height:auto; margin-bottom:50px; }

  /* ===== FOOTER ===== */
  footer { padding:120px 8% 60px; border-top:1px solid var(--border); text-align:center; }

  /* ===== RESPONSIVE ===== */
  @media(max-width:1024px) {
    .hero { flex-direction:column; text-align:center; padding-top:180px; }
    .featured { grid-template-columns:1fr; }
    .nav-links { display:none; }
    .menu-trigger { display:block; }
    .safarnama-container { flex-direction:column; }
    .gupshup-grid { grid-template-columns:1fr; }
    .side-specs { display:none; }
  }

  /* ===== SHOP NAV ACCENT ===== */
  .nav-item[style*="accent"] { position: relative; }
  .nav-item[style*="accent"]::before {
    content: '◈';
    position: absolute;
    left: 8px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 6px;
    color: var(--gold);
    opacity: 0.6;
  }

  /* ===== FIX: Ensure .reveal elements are visible as fallback ===== */
  .reveal { opacity: 0; }

  /* ===== LIVE NEWS STYLES ===== */
  @keyframes shimmer {
    0%   { transform: translateX(-100%); }
    100% { transform: translateX(100%); }
  }
  .skeleton-shimmer {
    position: absolute; inset: 0;
    background: linear-gradient(90deg, transparent 0%, rgba(255,255,255,0.04) 50%, transparent 100%);
    animation: shimmer 1.8s infinite;
  }

  @keyframes pulse-dot {
    0%, 100% { opacity: 1; transform: scale(1); }
    50%       { opacity: 0.3; transform: scale(0.7); }
  }
  .pulse-live { animation: pulse-dot 1.2s ease-in-out infinite; background: #22c55e !important; }

  @keyframes spin-refresh {
    from { transform: rotate(0deg); }
    to   { transform: rotate(360deg); }
  }
  .spinning { animation: spin-refresh 0.8s linear infinite; }

  .news-featured-grid {
    display: grid;
    grid-template-columns: 1.8fr 1fr;
    gap: 40px;
  }

  .live-featured-main {
    position: relative; border-radius: 4px; overflow: hidden;
    aspect-ratio: 16/9; display: block; text-decoration: none;
    background: var(--card); border: 1px solid var(--border);
  }
  .live-featured-main img {
    width: 100%; height: 100%; object-fit: cover;
    transition: 1.2s cubic-bezier(0.16,1,0.3,1);
    opacity: 0.85;
  }
  .live-featured-main:hover img { transform: scale(1.05); opacity: 1; }
  .live-featured-text {
    position: absolute; bottom: 0; left: 0; width: 100%; padding: 50px 40px 40px;
    background: linear-gradient(transparent, rgba(0,0,0,0.9));
  }

  .live-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 8px; letter-spacing: 3px; text-transform: uppercase;
    padding: 3px 10px; border: 1px solid rgba(255,255,255,0.3);
    color: rgba(255,255,255,0.7); display: inline-block; margin-bottom: 14px;
  }

  .live-side-card {
    padding: 28px 0; border-bottom: 1px solid var(--border);
    display: block; text-decoration: none; color: inherit;
    transition: padding-left 0.3s ease, border-bottom-color 0.3s ease;
    position: relative;
  }
  .live-side-card:last-child { border-bottom: none; }
  .live-side-card:hover { padding-left: 14px; border-bottom-color: var(--text); }

  .live-side-card .live-tag-small {
    font-family: 'JetBrains Mono', monospace;
    font-size: 8px; letter-spacing: 3px; text-transform: uppercase;
    color: var(--muted); display: block; margin-bottom: 10px;
  }

  .news-secondary-card {
    border: 1px solid var(--border); padding: 24px;
    background: var(--card); text-decoration: none; color: inherit;
    display: block; transition: all 0.4s cubic-bezier(0.16,1,0.3,1);
    position: relative; overflow: hidden;
  }
  .news-secondary-card::before {
    content: ''; position: absolute; top: 0; left: 0;
    width: 2px; height: 0; background: var(--text);
    transition: height 0.4s cubic-bezier(0.16,1,0.3,1);
  }
  .news-secondary-card:hover { border-color: rgba(255,255,255,0.2); transform: translateY(-4px); }
  .news-secondary-card:hover::before { height: 100%; }

  .news-read-more {
    font-family: 'JetBrains Mono', monospace; font-size: 9px;
    letter-spacing: 2px; color: var(--muted); text-transform: uppercase;
    display: inline-flex; align-items: center; gap: 8px;
    margin-top: 16px; transition: color 0.3s, gap 0.3s;
  }
  .news-secondary-card:hover .news-read-more { color: var(--text); gap: 12px; }

  @media(max-width:1024px) {
    .news-featured-grid { grid-template-columns: 1fr; }
  }


  /* ===== GOOGLE ADS — minimal, on-brand ===== */
  .ad-slot-wrap {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 14px 0;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    background: var(--bg);
    position: relative;
  }
  .ad-slot-label {
    position: absolute;
    top: 5px;
    right: 8%;
    font-family: 'JetBrains Mono', monospace;
    font-size: 7px;
    letter-spacing: 2px;
    color: var(--muted);
    opacity: 0.45;
    text-transform: uppercase;
    pointer-events: none;
  }
  .ad-slot-wrap ins { display: block; }

  /* In-feed ad — sits inside section flow */
  .ad-infeed {
    border: 1px solid var(--border);
    padding: 6px;
    background: var(--card);
    overflow: hidden;
  }


  /* ══════════════════════════════════════════════════
     ARTICLE VIEWER  (.av panels)
  ══════════════════════════════════════════════════ */
  .av {
    display: none;
    position: fixed; inset: 0; z-index: 1200;
    background: var(--bg);
    overflow-y: auto;
    opacity: 0;
    transition: opacity 0.45s cubic-bezier(0.16,1,0.3,1);
  }
  .av.open { display: block; opacity: 1; }

  .av-bar {
    position: sticky; top: 0; z-index: 10;
    background: rgba(5,5,5,0.92);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
    border-bottom: 1px solid var(--border);
    padding: 14px 8%;
    display: flex; align-items: center; gap: 20px;
  }
  [data-theme="light"] .av-bar {
    background: rgba(245,245,243,0.93);
  }
  .av-back {
    display: inline-flex; align-items: center; gap: 9px;
    background: none; border: 1px solid var(--border);
    color: var(--muted); padding: 8px 16px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 9px; font-weight: 700; letter-spacing: 2px;
    text-transform: uppercase; cursor: pointer; transition: all 0.25s;
  }
  .av-back:hover { border-color: var(--text); color: var(--text); }
  .av-crumb {
    font-family: 'JetBrains Mono', monospace;
    font-size: 8px; letter-spacing: 3px;
    color: var(--muted); opacity: 0.5; text-transform: uppercase;
  }

  /* article pages: override body bg with var so light theme works */
  .av header    { background: transparent !important; }
  .av article   { background: transparent !important; }
  .av body      { background: transparent !important; }
  .av [data-theme="light"] header { color: var(--text); }

  /* ══════════════════════════════════════════════════
     VIEW SYSTEM  (main / shop)
  ══════════════════════════════════════════════════ */
  #main-view { display: block; }
  #shop-view { display: none;  }
  body.shop-active #main-view { display: none;  }
  body.shop-active #shop-view { display: block; }

  /* Cart button — only shown in shop mode */
  #mainCartBtn { display: none !important; }
  body.shop-active #mainCartBtn { display: flex !important; }

  /* ══════════════════════════════════════════════════
     SHOP PAGE STYLES
  ══════════════════════════════════════════════════ */


/* ===== THEME ===== */


/* ===== PROGRESS BAR ===== */



/* ===== NAV ===== */



.brand-sub {
  font-family:'JetBrains Mono',monospace;font-size:7px;
  letter-spacing:4px;color:var(--gold);font-weight:400;
}



.nav-right { display:flex;align-items:center;gap:16px; }

/* Cart icon */
.cart-btn {
  position:relative;background:none;border:1px solid var(--border);
  color:var(--text);width:42px;height:42px;border-radius:2px;
  display:flex;align-items:center;justify-content:center;
  cursor:pointer;transition:all 0.3s;
}
.cart-btn:hover { border-color:var(--gold); }
.cart-count {
  position:absolute;top:-6px;right:-6px;background:var(--gold);
  color:#000;width:16px;height:16px;border-radius:50%;
  font-family:'JetBrains Mono',monospace;font-size:8px;font-weight:800;
  display:flex;align-items:center;justify-content:center;
  opacity:0;transform:scale(0);transition:all 0.3s cubic-bezier(0.16,1,0.3,1);
}
.cart-count.visible { opacity:1;transform:scale(1); }

.theme-btn {
  background:var(--card);border:1px solid var(--border);color:var(--text);
  width:42px;height:42px;border-radius:50%;display:flex;align-items:center;
  justify-content:center;cursor:pointer;transition:0.4s;
}



/* Mobile overlay */




/* ===== HERO ===== */
.shop-hero {
  min-height:100vh;display:flex;align-items:flex-end;
  padding:0 8% 100px;position:relative;overflow:hidden;
}
.shop-hero-bg {
  position:absolute;inset:0;
  background: radial-gradient(ellipse at 60% 40%, rgba(200,169,110,0.08) 0%, transparent 60%),
              linear-gradient(135deg, #080808 0%, #050505 100%);
}
.shop-hero-grid {
  position:absolute;inset:0;opacity:0.04;
  background-image: linear-gradient(var(--text) 1px, transparent 1px),
                    linear-gradient(90deg, var(--text) 1px, transparent 1px);
  background-size:60px 60px;
}
.shop-hero-content { position:relative;z-index:2;max-width:700px; }
.hero-eyebrow {
  font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:5px;
  color:var(--gold);text-transform:uppercase;margin-bottom:24px;display:block;
}
.shop-hero h1 {
  font-family:'Playfair Display',serif;font-size:clamp(3.5rem,8vw,7rem);
  line-height:1;letter-spacing:-0.02em;margin-bottom:30px;
}
.shop-hero h1 em { font-style:italic;color:var(--gold); }
.shop-hero p {
  color:var(--muted);font-size:1.1rem;font-weight:300;
  max-width:480px;margin-bottom:50px;line-height:1.7;
}
.hero-stats {
  display:flex;gap:50px;margin-top:60px;padding-top:40px;
  border-top:1px solid var(--border);
}
.hero-stat-val {
  font-family:'Playfair Display',serif;font-size:2rem;
  color:var(--text);display:block;
}
.hero-stat-label {
  font-family:'JetBrains Mono',monospace;font-size:8px;
  letter-spacing:3px;color:var(--muted);text-transform:uppercase;
}

/* Floating product visual */
.hero-product-float {
  position:absolute;right:8%;top:50%;transform:translateY(-50%);
  width:380px;height:380px;z-index:2;
}
.hero-product-ring {
  position:absolute;inset:0;border-radius:50%;
  border:1px solid rgba(200,169,110,0.15);
  animation:ringRotate 20s linear infinite;
}
.hero-product-ring::before {
  content:'';position:absolute;top:-4px;left:50%;width:8px;height:8px;
  background:var(--gold);border-radius:50%;transform:translateX(-50%);
}
@keyframes ringRotate { from{transform:rotate(0deg)} to{transform:rotate(360deg)} }
.hero-product-img {
  width:100%;height:100%;object-fit:cover;border-radius:4px;
  filter:grayscale(20%);
}

/* CTA */
.cta {
  display:inline-flex;align-items:center;gap:12px;padding:18px 40px;
  border:1px solid var(--text);font-size:10px;font-weight:800;letter-spacing:4px;
  text-decoration:none;color:var(--text);position:relative;overflow:hidden;
  transition:0.4s;cursor:pointer;background:none;
}
.cta::before {
  content:'';position:absolute;inset:0;background:var(--text);
  transform:translateX(-100%);transition:transform 0.4s cubic-bezier(0.16,1,0.3,1);
  z-index:-1;
}
.cta:hover { color:var(--bg); }
.cta:hover::before { transform:translateX(0); }
.cta-gold {
  border-color:var(--gold);color:var(--gold);
}
.cta-gold::before { background:var(--gold); }
.cta-gold:hover { color:#000; }

/* ===== SECTION BASE ===== */

.section-head {
  display:flex;align-items:flex-end;justify-content:space-between;
  margin-bottom:60px;padding-bottom:24px;border-bottom:1px solid var(--border);
}
.section-label {
  font-family:'JetBrains Mono',monospace;font-size:8px;
  letter-spacing:4px;color:var(--gold);text-transform:uppercase;
  display:block;margin-bottom:12px;
}
.section-title {
  font-family:'Playfair Display',serif;font-size:clamp(2rem,4vw,3rem);
  font-weight:500;letter-spacing:-0.02em;
}

/* ===== CATEGORY FILTER ===== */
.filter-bar {
  display:flex;align-items:center;gap:6px;flex-wrap:wrap;margin-bottom:50px;
}
.filter-btn {
  background:none;border:1px solid var(--border);color:var(--muted);
  padding:8px 20px;font-family:'JetBrains Mono',monospace;font-size:9px;
  letter-spacing:2px;text-transform:uppercase;cursor:pointer;
  transition:all 0.3s;border-radius:30px;
}
.filter-btn:hover { border-color:var(--text);color:var(--text); }
.filter-btn.active { background:var(--text);color:var(--bg);border-color:var(--text); }
.filter-btn.active-gold { background:var(--gold);color:#000;border-color:var(--gold); }

/* ===== PRODUCT GRID ===== */
.product-grid {
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(300px,1fr));
  gap:1px;
  background:var(--border);
  border:1px solid var(--border);
}

.product-card {
  background:var(--bg);position:relative;overflow:hidden;
  text-decoration:none;color:inherit;display:block;
  transition:background 0.4s;
  cursor:pointer;
}
.product-card:hover { background:var(--card-solid); }

.product-img-wrap {
  aspect-ratio:1/1;overflow:hidden;position:relative;
  background:#0a0a0a;
}
.product-img-wrap img {
  width:100%;height:100%;object-fit:cover;
  transition:transform 1.2s cubic-bezier(0.16,1,0.3,1),
             filter 0.6s ease;
  filter:grayscale(30%);
}
.product-card:hover .product-img-wrap img {
  transform:scale(1.06);filter:grayscale(0%);
}

/* Quick add overlay */
.product-overlay {
  position:absolute;inset:0;background:rgba(0,0,0,0.7);backdrop-filter:blur(4px);
  display:flex;align-items:center;justify-content:center;
  opacity:0;transition:opacity 0.35s;
}
.product-card:hover .product-overlay { opacity:1; }
.quick-add-btn {
  background:var(--text);color:var(--bg);border:none;
  padding:14px 32px;font-family:'JetBrains Mono',monospace;
  font-size:9px;font-weight:800;letter-spacing:3px;
  cursor:pointer;transform:translateY(8px);
  transition:transform 0.4s cubic-bezier(0.16,1,0.3,1), background 0.3s;
}
.product-card:hover .quick-add-btn { transform:translateY(0); }
.quick-add-btn:hover { background:var(--gold);color:#000; }

/* Badge */
.product-badge {
  position:absolute;top:16px;left:16px;z-index:3;
  font-family:'JetBrains Mono',monospace;font-size:8px;
  letter-spacing:2px;padding:4px 10px;font-weight:800;
  text-transform:uppercase;
}
.badge-new    { background:var(--text);color:var(--bg); }
.badge-hot    { background:var(--gold);color:#000; }
.badge-sold   { background:rgba(255,255,255,0.08);color:var(--muted);border:1px solid var(--border); }
.badge-ltd    { background:transparent;border:1px solid var(--gold);color:var(--gold); }

.product-info { padding:24px; }
.product-category {
  font-family:'JetBrains Mono',monospace;font-size:8px;
  letter-spacing:3px;color:var(--muted);text-transform:uppercase;
  margin-bottom:8px;display:block;
}
.product-name {
  font-family:'Playfair Display',serif;font-size:1.2rem;
  font-weight:500;margin-bottom:16px;line-height:1.3;
}
.product-footer {
  display:flex;align-items:center;justify-content:space-between;
}
.product-price {
  font-family:'JetBrains Mono',monospace;font-size:14px;
  font-weight:800;color:var(--text);
}
.product-price .original {
  font-size:11px;color:var(--muted);text-decoration:line-through;margin-right:8px;
}
.product-price .discounted { color:var(--gold); }
.product-sizes {
  display:flex;gap:4px;
}
.size-dot {
  width:20px;height:20px;border:1px solid var(--border);
  font-family:'JetBrains Mono',monospace;font-size:7px;
  display:flex;align-items:center;justify-content:center;
  color:var(--muted);
}

/* ===== FEATURED PRODUCT (full width) ===== */
.featured-product {
  display:grid;grid-template-columns:1fr 1fr;gap:0;
  border:1px solid var(--border);margin-bottom:120px;overflow:hidden;
}
.featured-product-img {
  aspect-ratio:4/3;overflow:hidden;position:relative;background:#080808;
}
.featured-product-img img {
  width:100%;height:100%;object-fit:cover;
  filter:grayscale(20%);transition:transform 1.4s cubic-bezier(0.16,1,0.3,1);
}
.featured-product:hover .featured-product-img img { transform:scale(1.05); }
.featured-product-details {
  padding:70px 60px;display:flex;flex-direction:column;justify-content:center;
  background:var(--card-solid);
}
.featured-tag {
  font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:4px;
  color:var(--gold);text-transform:uppercase;margin-bottom:20px;display:block;
}
.featured-product-details h2 {
  font-family:'Playfair Display',serif;font-size:clamp(1.8rem,3vw,2.8rem);
  font-weight:500;line-height:1.2;margin-bottom:20px;
}
.featured-desc {
  color:var(--muted);font-size:14px;line-height:1.8;margin-bottom:30px;
}
.featured-price {
  font-family:'JetBrains Mono',monospace;font-size:1.6rem;
  font-weight:800;margin-bottom:30px;
}
.size-selector { display:flex;gap:8px;margin-bottom:30px; }
.size-btn {
  width:40px;height:40px;border:1px solid var(--border);background:none;
  color:var(--muted);font-family:'JetBrains Mono',monospace;font-size:10px;
  cursor:pointer;transition:all 0.3s;
}
.size-btn:hover, .size-btn.selected {
  border-color:var(--text);color:var(--text);background:var(--text);color:var(--bg);
}
.size-btn.selected { background:var(--gold);border-color:var(--gold);color:#000; }

/* ===== MARQUEE BANNER ===== */
.marquee-wrap {
  background:var(--gold);padding:14px 0;overflow:hidden;
  white-space:nowrap;border-top:1px solid rgba(200,169,110,0.3);
  border-bottom:1px solid rgba(200,169,110,0.3);
  margin:0 0 0 0;
}
.marquee-track { display:inline-block;animation:marquee 25s linear infinite; }
.marquee-item {
  display:inline-block;padding:0 40px;
  font-family:'JetBrains Mono',monospace;font-size:10px;
  letter-spacing:3px;font-weight:800;color:#000;text-transform:uppercase;
}
.marquee-sep { color:rgba(0,0,0,0.35);margin:0 10px; }
@keyframes marquee { 0%{transform:translateX(0)} 100%{transform:translateX(-50%)} }

/* ===== COLLECTIONS BANNER ===== */
.collections-grid {
  display:grid;grid-template-columns:2fr 1fr 1fr;gap:1px;
  background:var(--border);border:1px solid var(--border);
  margin-bottom:120px;
}
.collection-tile {
  position:relative;overflow:hidden;cursor:pointer;text-decoration:none;color:inherit;
  display:block;
}
.collection-tile .tile-img {
  width:100%;aspect-ratio:4/5;object-fit:cover;
  filter:grayscale(40%) brightness(0.7);
  transition:filter 0.8s,transform 1s cubic-bezier(0.16,1,0.3,1);
}
.collection-tile:first-child .tile-img { aspect-ratio:3/4; }
.collection-tile:hover .tile-img { filter:grayscale(10%) brightness(0.85);transform:scale(1.04); }
.collection-label {
  position:absolute;bottom:0;left:0;width:100%;padding:30px 24px;
  background:linear-gradient(transparent,rgba(0,0,0,0.85));
}
.collection-label span {
  font-family:'JetBrains Mono',monospace;font-size:8px;
  letter-spacing:3px;color:rgba(255,255,255,0.6);text-transform:uppercase;display:block;
  margin-bottom:6px;
}
.collection-label h3 {
  font-family:'Playfair Display',serif;font-size:1.3rem;
  color:#fff;font-style:italic;
}

/* ===== CART DRAWER ===== */
.cart-drawer {
  position:fixed;top:0;right:0;width:420px;max-width:100%;height:100%;
  background:var(--bg);border-left:1px solid var(--border);z-index:2000;
  transform:translateX(100%);transition:transform 0.5s cubic-bezier(0.16,1,0.3,1);
  display:flex;flex-direction:column;
  backdrop-filter:blur(20px);
}
.cart-drawer.open { transform:translateX(0); }
.cart-overlay-bg {
  position:fixed;inset:0;background:rgba(0,0,0,0.6);z-index:1999;
  opacity:0;pointer-events:none;transition:opacity 0.4s;
}
.cart-overlay-bg.visible { opacity:1;pointer-events:all; }
.cart-header {
  padding:30px;border-bottom:1px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;
}
.cart-header h3 {
  font-family:'JetBrains Mono',monospace;font-size:11px;letter-spacing:3px;
  text-transform:uppercase;
}
.cart-close {
  background:none;border:1px solid var(--border);color:var(--muted);
  width:32px;height:32px;cursor:pointer;display:flex;align-items:center;
  justify-content:center;transition:all 0.3s;
}
.cart-close:hover { border-color:var(--text);color:var(--text); }
.cart-body { flex:1;overflow-y:auto;padding:20px 30px; }
.cart-empty {
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  height:100%;text-align:center;gap:16px;
}
.cart-empty-icon { font-size:48px;opacity:0.2; }
.cart-empty p { color:var(--muted);font-size:13px; }
.cart-item {
  display:grid;grid-template-columns:70px 1fr auto;gap:16px;
  padding:20px 0;border-bottom:1px solid var(--border);align-items:start;
}
.cart-item-img { width:70px;height:70px;object-fit:cover;background:var(--card); }
.cart-item-name { font-family:'Playfair Display',serif;font-size:0.95rem;margin-bottom:4px; }
.cart-item-meta { font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:1px; }
.cart-item-price { font-family:'JetBrains Mono',monospace;font-size:12px;font-weight:800; }
.cart-item-remove {
  background:none;border:none;color:var(--muted);cursor:pointer;
  font-size:18px;transition:color 0.2s;margin-top:4px;display:block;
}
.cart-item-remove:hover { color:var(--text); }
.cart-footer {
  padding:24px 30px;border-top:1px solid var(--border);
}
.cart-total {
  display:flex;justify-content:space-between;align-items:center;
  margin-bottom:20px;
}
.cart-total-label { font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:2px;color:var(--muted); }
.cart-total-amount { font-family:'JetBrains Mono',monospace;font-size:1.2rem;font-weight:800; }
.checkout-btn {
  width:100%;padding:18px;background:var(--gold);color:#000;border:none;
  font-family:'JetBrains Mono',monospace;font-size:10px;font-weight:800;
  letter-spacing:3px;cursor:pointer;transition:opacity 0.3s;
}
.checkout-btn:hover { opacity:0.85; }

/* ===== TOAST ===== */
.toast {
  position:fixed;bottom:40px;left:50%;transform:translateX(-50%) translateY(20px);
  background:var(--text);color:var(--bg);padding:14px 28px;
  font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:2px;
  font-weight:800;text-transform:uppercase;z-index:3000;
  opacity:0;transition:all 0.4s cubic-bezier(0.16,1,0.3,1);pointer-events:none;
  border-left:3px solid var(--gold);
}
.toast.show { opacity:1;transform:translateX(-50%) translateY(0); }

/* ===== TESTIMONIALS ===== */
.testimonials {
  display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:1px;
  background:var(--border);border:1px solid var(--border);margin-top:80px;
}
.testimonial {
  padding:40px;background:var(--bg);transition:background 0.3s;
}
.testimonial:hover { background:var(--card-solid); }
.testi-stars { color:var(--gold);font-size:12px;letter-spacing:2px;margin-bottom:16px; }
.testi-text {
  font-family:'Playfair Display',serif;font-size:1rem;font-style:italic;
  line-height:1.7;margin-bottom:24px;color:var(--text);
}
.testi-author {
  font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:2px;
  color:var(--muted);text-transform:uppercase;
}

/* ===== NEWSLETTER ===== */
.newsletter {
  padding:100px 8%;border-top:1px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;gap:60px;
}
.newsletter-content h2 {
  font-family:'Playfair Display',serif;font-size:clamp(1.8rem,3vw,2.8rem);
  font-weight:500;margin-bottom:12px;
}
.newsletter-content p { color:var(--muted);font-size:14px; }
.newsletter-form { display:flex;gap:0;min-width:400px; }
.newsletter-input {
  flex:1;background:transparent;border:1px solid var(--border);border-right:none;
  padding:16px 20px;color:var(--text);font-family:'Montserrat',sans-serif;
  font-size:12px;outline:none;transition:border-color 0.3s;
}
.newsletter-input:focus { border-color:var(--gold); }
.newsletter-input::placeholder { color:var(--muted); }
.newsletter-submit {
  background:var(--gold);color:#000;border:none;
  padding:16px 28px;font-family:'JetBrains Mono',monospace;
  font-size:9px;font-weight:800;letter-spacing:3px;cursor:pointer;transition:opacity 0.3s;
}
.newsletter-submit:hover { opacity:0.85; }

/* ===== FOOTER ===== */
footer {
  padding:80px 8% 40px;border-top:1px solid var(--border);
}
.footer-top {
  display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:60px;margin-bottom:60px;
}
.footer-brand { font-weight:900;letter-spacing:8px;font-size:1.1rem;margin-bottom:16px;display:block; }
.footer-brand-desc { color:var(--muted);font-size:13px;line-height:1.7;max-width:260px; }
.footer-col h4 {
  font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:3px;
  color:var(--gold);text-transform:uppercase;margin-bottom:20px;
}
.footer-col a {
  display:block;color:var(--muted);text-decoration:none;font-size:13px;
  margin-bottom:10px;transition:color 0.3s;
}
.footer-col a:hover { color:var(--text); }
.footer-bottom {
  display:flex;justify-content:space-between;align-items:center;
  padding-top:30px;border-top:1px solid var(--border);
}
.footer-copy { font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:2px; }

/* ===== REVEAL ===== */


/* ===== PRODUCT MODAL ===== */
.modal-bg {
  position:fixed;inset:0;background:rgba(0,0,0,0.85);z-index:1998;
  opacity:0;pointer-events:none;transition:opacity 0.4s;backdrop-filter:blur(8px);
}
.modal-bg.open { opacity:1;pointer-events:all; }
.product-modal {
  position:fixed;top:50%;left:50%;transform:translate(-50%,-60%);
  width:min(900px,92vw);max-height:90vh;overflow-y:auto;
  background:var(--bg);border:1px solid var(--border);z-index:1999;
  opacity:0;pointer-events:none;transition:all 0.5s cubic-bezier(0.16,1,0.3,1);
}
.product-modal.open { opacity:1;pointer-events:all;transform:translate(-50%,-50%); }
.modal-inner { display:grid;grid-template-columns:1fr 1fr; }
.modal-img { aspect-ratio:1;overflow:hidden;background:#080808; }
.modal-img img { width:100%;height:100%;object-fit:cover; }
.modal-details { padding:50px 40px;display:flex;flex-direction:column;gap:16px; }
.modal-close {
  position:absolute;top:20px;right:20px;background:none;border:1px solid var(--border);
  color:var(--muted);width:36px;height:36px;cursor:pointer;z-index:10;
  display:flex;align-items:center;justify-content:center;transition:all 0.3s;
}
.modal-close:hover { border-color:var(--text);color:var(--text); }

/* ===== RESPONSIVE ===== */
@media(max-width:1024px) {
  .shop-hero-content { max-width:100%; }
  .hero-product-float { display:none; }
  .featured-product { grid-template-columns:1fr; }
  .collections-grid { grid-template-columns:1fr 1fr; }
  .footer-top { grid-template-columns:1fr 1fr; }
  .newsletter { flex-direction:column; }
  .newsletter-form { min-width:auto;width:100%; }
  
  
  .modal-inner { grid-template-columns:1fr; }
}
@media(max-width:640px) {
  .collections-grid { grid-template-columns:1fr; }
  .hero-stats { flex-wrap:wrap;gap:30px; }
  .footer-top { grid-template-columns:1fr; }
  .cart-drawer { width:100%; }
}


  /* ── SUB-PAGE ARTICLE STYLES ── */

  /* ── ARTICLE: accessory ── */
/* BACK BUTTON */
.av[data-p="accessory"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="accessory"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="accessory"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="accessory"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="accessory"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE BODY */
.av[data-p="accessory"] article { padding:0 12% 140px; max-width:1000px; }
.av[data-p="accessory"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; font-weight: 300; }
.av[data-p="accessory"] article h2 { font-family: 'Playfair Display', serif; font-size: 32px; margin: 60px 0 24px; color: #fff; letter-spacing: 1px; border-left: 4px solid #fff; padding-left: 20px; }
/* GEAR SPEC BOX */
.av[data-p="accessory"] .gear-box {
      background: rgba(255,255,255,0.02);
      border: 1px solid rgba(255,255,255,0.08);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 45px;
      gap: 50px;
    }
.av[data-p="accessory"] .gear-column h3 { font-size: 13px; letter-spacing: 3px; margin-bottom: 25px; color: #fff; text-transform: uppercase; opacity: 0.8; }
.av[data-p="accessory"] .gear-column.active h3 { color: #fbbf24; }
/* Recovery Gear */
.av[data-p="accessory"] .gear-column.passive h3 { color: #60a5fa; }
/* Support Gear */
.av[data-p="accessory"] .gear-list { list-style: none; }
.av[data-p="accessory"] .gear-list li { font-size: 15px; color: #999; margin-bottom: 18px; padding-left: 20px; position: relative; line-height: 1.5; }
.av[data-p="accessory"] .gear-list li strong { color: #ddd; display: block; margin-bottom: 4px; }
.av[data-p="accessory"] .gear-list li::before { content: '—'; position: absolute; left: 0; color: #444; }
/* PULL QUOTE */
.av[data-p="accessory"] .pull-quote {
        font-family: 'Playfair Display', serif;
        font-style: italic;
        font-size: 26px;
        color: #fff;
        border-top: 1px solid rgba(255,255,255,0.1);
        border-bottom: 1px solid rgba(255,255,255,0.1);
        padding: 40px 0;
        margin: 60px 0;
        line-height: 1.4;
        text-align: center;
    }
/* FILM GRAIN */
@media max-width:768px) {
.av[data-p="accessory"] header, .av[data-p="accessory"] article { padding-left:8%; padding-right:8%; }.av[data-p="accessory"] .gear-box { grid-template-columns: 1fr; padding: 30px; }
    
}

  /* ── ARTICLE: fuel ── */
/* BACK BUTTON */
.av[data-p="fuel"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="fuel"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="fuel"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="fuel"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="fuel"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE BODY */
.av[data-p="fuel"] article { padding:0 12% 140px; max-width:1000px; }
.av[data-p="fuel"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; }
.av[data-p="fuel"] article h2 { font-size: 28px; margin: 60px 0 20px; color: #fff; letter-spacing: 1px; }
/* PROS & CONS BOX */
.av[data-p="fuel"] .comparison-box {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.1);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 40px;
      gap: 40px;
    }
.av[data-p="fuel"] .comp-column h3 { font-size: 14px; letter-spacing: 3px; margin-bottom: 20px; color: #fff; }
.av[data-p="fuel"] .comp-column.pros h3 { color: #fbbf24; }
/* Petrol Yellow */
.av[data-p="fuel"] .comp-column.cons h3 { color: #60a5fa; }
/* Diesel Blue */
.av[data-p="fuel"] .comp-list { list-style: none; }
.av[data-p="fuel"] .comp-list li { font-size: 15px; color: #999; margin-bottom: 15px; padding-left: 20px; position: relative; }
.av[data-p="fuel"] .comp-list li::before { content: '—'; position: absolute; left: 0; color: #444; }
/* FILM GRAIN */
@media max-width:768px) {
.av[data-p="fuel"] header, .av[data-p="fuel"] article { padding-left:8%; padding-right:8%; }.av[data-p="fuel"] .comparison-box { grid-template-columns: 1fr; padding: 30px; }
    
}

  /* ── ARTICLE: rajasthan ── */
/* BACK BUTTON */
.av[data-p="rajasthan"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="rajasthan"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="rajasthan"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="rajasthan"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="rajasthan"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE BODY */
.av[data-p="rajasthan"] article { padding:0 12% 140px; max-width:1000px; }
.av[data-p="rajasthan"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; font-weight: 300; }
.av[data-p="rajasthan"] article h2 { font-family: 'Playfair Display', serif; font-size: 32px; margin: 60px 0 24px; color: #fff; letter-spacing: 1px; }
/* JOURNEY STATS BOX */
.av[data-p="rajasthan"] .journey-box {
      background: linear-gradient(145deg, rgba(255,255,255,0.05) 0%, rgba(255,255,255,0) 100%);
      border: 1px solid rgba(255,255,255,0.08);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 40px;
      gap: 40px;
    }
.av[data-p="rajasthan"] .stat-column h3 { font-size: 13px; letter-spacing: 3px; margin-bottom: 25px; color: #fff; text-transform: uppercase; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 10px; }
.av[data-p="rajasthan"] .stat-list { list-style: none; }
.av[data-p="rajasthan"] .stat-list li { font-size: 15px; color: #999; margin-bottom: 18px; line-height: 1.4; }
.av[data-p="rajasthan"] .stat-list strong { color: #fff; display: block; margin-bottom: 4px; font-size: 11px; letter-spacing: 2px; text-transform: uppercase; opacity: 0.6; }
/* QUOTE SECTION */
.av[data-p="rajasthan"] .pull-quote {
        font-family: 'Playfair Display', serif;
        font-style: italic;
        font-size: 28px;
        color: #fff;
        border-left: 2px solid #fff;
        padding-left: 30px;
        margin: 60px 0;
        line-height: 1.4;
    }
/* FILM GRAIN */
@media max-width:768px) {
.av[data-p="rajasthan"] header, .av[data-p="rajasthan"] article { padding-left:8%; padding-right:8%; }.av[data-p="rajasthan"] .journey-box { grid-template-columns: 1fr; padding: 30px; }
    
}

  /* ── ARTICLE: safari ── */
/* BACK BUTTON */
.av[data-p="safari"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="safari"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="safari"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="safari"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="safari"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE BODY */
.av[data-p="safari"] article { padding:0 12% 140px; max-width:1000px; }
.av[data-p="safari"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; }
.av[data-p="safari"] article h2 { font-size: 28px; margin: 60px 0 20px; color: #fff; letter-spacing: 1px; }
/* PROS & CONS BOX */
.av[data-p="safari"] .comparison-box {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.1);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 40px;
      gap: 40px;
    }
.av[data-p="safari"] .comp-column h3 { font-size: 14px; letter-spacing: 3px; margin-bottom: 20px; color: #fff; }
.av[data-p="safari"] .comp-column.pros h3 { color: #4ade80; }
.av[data-p="safari"] .comp-column.cons h3 { color: #f87171; }
.av[data-p="safari"] .comp-list { list-style: none; }
.av[data-p="safari"] .comp-list li { font-size: 15px; color: #999; margin-bottom: 15px; padding-left: 20px; position: relative; }
.av[data-p="safari"] .comp-list li::before { content: '—'; position: absolute; left: 0; color: #444; }
/* FILM GRAIN */
@media max-width:768px) {
.av[data-p="safari"] header, .av[data-p="safari"] article { padding-left:8%; padding-right:8%; }.av[data-p="safari"] .comparison-box { grid-template-columns: 1fr; padding: 30px; }
    
}

  /* ── ARTICLE: soul ── */
/* BACK BUTTON */
.av[data-p="soul"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="soul"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="soul"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="soul"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="soul"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE BODY */
.av[data-p="soul"] article { padding:0 12% 140px; max-width:1000px; }
.av[data-p="soul"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; }
.av[data-p="soul"] article h2 { font-size: 28px; margin: 60px 0 20px; color: #fff; letter-spacing: 1px; border-left: 4px solid #fff; padding-left: 20px; }
/* PROS & CONS BOX */
.av[data-p="soul"] .comparison-box {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.1);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 40px;
      gap: 40px;
    }
.av[data-p="soul"] .comp-column h3 { font-size: 14px; letter-spacing: 3px; margin-bottom: 20px; color: #fff; text-transform: uppercase; }
.av[data-p="soul"] .comp-column.pros h3 { color: #4ade80; }
.av[data-p="soul"] .comp-column.cons h3 { color: #f87171; }
.av[data-p="soul"] .comp-list { list-style: none; }
.av[data-p="soul"] .comp-list li { font-size: 15px; color: #999; margin-bottom: 15px; padding-left: 20px; position: relative; line-height: 1.4; }
.av[data-p="soul"] .comp-list li::before { content: '•'; position: absolute; left: 0; color: #555; }
/* FILM GRAIN */
@media max-width:768px) {
.av[data-p="soul"] header, .av[data-p="soul"] article { padding-left:8%; padding-right:8%; }.av[data-p="soul"] .comparison-box { grid-template-columns: 1fr; padding: 30px; }
    
}

  /* ── ARTICLE: suv ── */
/* BACK BUTTON */
.av[data-p="suv"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="suv"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="suv"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="suv"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="suv"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE BODY */
.av[data-p="suv"] article { padding:0 12% 140px; max-width:1000px; }
.av[data-p="suv"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; }
.av[data-p="suv"] article h2 { font-size: 28px; margin: 60px 0 20px; color: #fff; letter-spacing: 1px; border-left: 4px solid #fff; padding-left: 20px; }
/* PROS & CONS BOX */
.av[data-p="suv"] .comparison-box {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.1);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 40px;
      gap: 40px;
    }
.av[data-p="suv"] .comp-column h3 { font-size: 14px; letter-spacing: 3px; margin-bottom: 20px; color: #fff; text-transform: uppercase; }
.av[data-p="suv"] .comp-column.pros h3 { color: #4ade80; }
.av[data-p="suv"] .comp-column.cons h3 { color: #f87171; }
.av[data-p="suv"] .comp-list { list-style: none; }
.av[data-p="suv"] .comp-list li { font-size: 15px; color: #999; margin-bottom: 15px; padding-left: 20px; position: relative; line-height: 1.4; }
.av[data-p="suv"] .comp-list li::before { content: '•'; position: absolute; left: 0; color: #555; }
/* FILM GRAIN */
@media max-width:768px) {
.av[data-p="suv"] header, .av[data-p="suv"] article { padding-left:8%; padding-right:8%; }.av[data-p="suv"] .comparison-box { grid-template-columns: 1fr; padding: 30px; }
    
}

  /* ── ARTICLE: v8 ── */
/* BACK BUTTON */
.av[data-p="v8"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="v8"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="v8"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="v8"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="v8"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE BODY */
.av[data-p="v8"] article { padding:0 12% 140px; max-width:1000px; }
.av[data-p="v8"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; font-weight: 300; }
.av[data-p="v8"] article h2 { font-family: 'Playfair Display', serif; font-size: 32px; margin: 60px 0 24px; color: #fff; letter-spacing: 1px; }
/* STATUS BOX */
.av[data-p="v8"] .status-box {
      background: rgba(255,255,255,0.02);
      border: 1px solid rgba(255,255,255,0.08);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 40px;
      gap: 40px;
    }
.av[data-p="v8"] .status-column h3 { font-size: 13px; letter-spacing: 3px; margin-bottom: 25px; color: #fff; text-transform: uppercase; }
.av[data-p="v8"] .status-column.survival h3 { color: #ffffff; border-bottom: 1px solid rgba(255,255,255,0.2); padding-bottom: 10px; }
.av[data-p="v8"] .status-column.threat h3 { color: #888; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 10px; }
.av[data-p="v8"] .status-list { list-style: none; }
.av[data-p="v8"] .status-list li { font-size: 15px; color: #999; margin-bottom: 18px; line-height: 1.4; }
.av[data-p="v8"] .status-list strong { color: #fff; display: block; margin-bottom: 4px; font-size: 14px; letter-spacing: 1px; }
/* FILM GRAIN */
@media max-width:768px) {
.av[data-p="v8"] header, .av[data-p="v8"] article { padding-left:8%; padding-right:8%; }.av[data-p="v8"] .status-box { grid-template-columns: 1fr; padding: 30px; }
    
}

  /* ── ARTICLE: modify ── */
.av[data-p="modify"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="modify"] .back:hover { color:#fff; }
.av[data-p="modify"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="modify"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom:20px;}
.av[data-p="modify"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
.av[data-p="modify"] article { padding:0 12% 140px; max-width:1000px; }
.av[data-p="modify"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom:32px; }
.av[data-p="modify"] article h2 { font-size:28px; margin:60px 0 20px; color:#fff; letter-spacing:1px; border-left:4px solid #fff; padding-left:20px; }
.av[data-p="modify"] .comparison-box {
background: rgba(255,255,255,0.03);
border: 1px solid rgba(255,255,255,0.1);
display: grid;
grid-template-columns: 1fr 1fr;
margin: 60px 0;
padding: 40px;
gap: 40px;
}
.av[data-p="modify"] .comp-column h3 { font-size: 14px; letter-spacing: 3px; margin-bottom: 20px; color: #fff; text-transform: uppercase; }
.av[data-p="modify"] .comp-column.pros h3 { color: #4ade80; }
.av[data-p="modify"] .comp-column.cons h3 { color: #f87171; }
.av[data-p="modify"] .comp-list { list-style: none; }
.av[data-p="modify"] .comp-list li { font-size: 15px; color: #999; margin-bottom: 15px; padding-left: 20px; position: relative; line-height: 1.4; }
.av[data-p="modify"] .comp-list li::before { content: '•'; position: absolute; left: 0; color: #555; }
@media max-width:768px) {
.av[data-p="modify"] header, .av[data-p="modify"] article { padding-left:8%; padding-right:8%; }.av[data-p="modify"] .comparison-box { grid-template-columns: 1fr; padding:30px; }

}

  /* ── ARTICLE: manifesto ── */
/* BACK BUTTON */
.av[data-p="manifesto"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="manifesto"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="manifesto"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="manifesto"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5.2rem); font-weight:900; line-height:1; margin-bottom: 25px;}
.av[data-p="manifesto"] header p { font-size:11px; letter-spacing:5px; color:#888; text-transform: uppercase; font-weight: 700; }
/* ARTICLE BODY */
.av[data-p="manifesto"] article { padding:0 12% 140px; max-width:1050px; }
.av[data-p="manifesto"] article p { font-size:18px; line-height:2; color:#ccc; margin-bottom: 35px; font-weight: 300; }
.av[data-p="manifesto"] article h2 { font-family: 'Playfair Display', serif; font-size: clamp(24px, 4vw, 36px); margin: 80px 0 30px; color: #fff; line-height: 1.2; }
.av[data-p="manifesto"] .dropcap { float: left; font-family: 'Playfair Display', serif; font-size: 85px; line-height: 60px; padding-top: 4px; padding-right: 12px; color: #fff; }
/* SECTION HIGHLIGHT BLOCKS */
.av[data-p="manifesto"] .feature-block {
      background: rgba(255,255,255,0.02);
      border-left: 1px solid rgba(255,255,255,0.1);
      margin: 70px 0;
      padding: 60px;
    }
.av[data-p="manifesto"] .feature-block h3 { font-family: 'Playfair Display', serif; font-size: 30px; margin-bottom: 20px; color: #fff; font-style: italic; }
.av[data-p="manifesto"] .feature-block span { font-size: 10px; letter-spacing: 4px; color: #666; text-transform: uppercase; display: block; margin-bottom: 15px; }
/* THREE COLUMN GRID */
.av[data-p="manifesto"] .manifesto-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 40px;
      margin: 80px 0;
    }
.av[data-p="manifesto"] .grid-item h4 { font-size: 13px; letter-spacing: 3px; color: #fff; margin-bottom: 15px; text-transform: uppercase; }
.av[data-p="manifesto"] .grid-item p { font-size: 15px; line-height: 1.6; color: #888; }
/* FILM GRAIN */
@media max-width:768px) {
.av[data-p="manifesto"] header, .av[data-p="manifesto"] article { padding-left:8%; padding-right:8%; }.av[data-p="manifesto"] .feature-block { padding: 40px 30px; }
    
}

  /* ── ARTICLE: manual ── */
/* BACK BUTTON */
.av[data-p="manual"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="manual"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="manual"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="manual"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="manual"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE CONTENT WRAPPER */
.av[data-p="manual"] .content-wrapper { 
      display: flex; 
      padding: 0 12% 140px; 
      gap: 60px; 
      max-width: 1400px;
    }
.av[data-p="manual"] article { flex: 2; }
.av[data-p="manual"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; font-weight: 300; }
.av[data-p="manual"] article h2 { font-family: 'Playfair Display', serif; font-size: 32px; margin: 60px 0 24px; color: #fff; border-left: 4px solid #fff; padding-left: 20px; }
/* STICKY IMAGE CONTAINER */
.av[data-p="manual"] .side-image-container { 
      flex: 1; 
      position: sticky; 
      top: 140px; 
      height: fit-content; 
    }
.av[data-p="manual"] .side-image-container img { 
      width: 100%; 
      border-radius: 4px; 
      filter: grayscale(0.5) contrast(1.1); 
      box-shadow: 0 20px 40px rgba(0,0,0,0.6);
      transition: 0.5s ease;
    }
.av[data-p="manual"] .side-image-container img:hover { filter: grayscale(0); }
.av[data-p="manual"] .image-caption { font-size: 10px; letter-spacing: 2px; color: #555; text-transform: uppercase; margin-top: 15px; text-align: right; }
/* BOXES */
.av[data-p="manual"] .comparison-box {
      background: rgba(255,255,255,0.02);
      border: 1px solid rgba(255,255,255,0.08);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 40px;
      gap: 40px;
    }
.av[data-p="manual"] .comp-column h3 { font-size: 13px; letter-spacing: 3px; margin-bottom: 20px; color: #fff; text-transform: uppercase; }
.av[data-p="manual"] .comp-column.pros h3 { color: #facc15; }
/* The Purist View */
.av[data-p="manual"] .comp-column.cons h3 { color: #60a5fa; }
/* The Tech View */
.av[data-p="manual"] .comp-list { list-style: none; }
.av[data-p="manual"] .comp-list li { font-size: 15px; color: #999; margin-bottom: 15px; padding-left: 20px; position: relative; }
.av[data-p="manual"] .comp-list li::before { content: '—'; position: absolute; left: 0; color: #444; }
/* FILM GRAIN */
@media max-width:1024px) {
.av[data-p="manual"] .content-wrapper { flex-direction: column; }.av[data-p="manual"] .side-image-container { position: relative; top: 0; order: -1; margin-bottom: 40px; }.av[data-p="manual"] header, .av[data-p="manual"] .content-wrapper { padding-left: 8%; padding-right: 8%; }
    
}

  /* ── ARTICLE: watches ── */
/* BACK BUTTON */
.av[data-p="watches"] .back { position:fixed; top:30px; left:30px; font-size:12px; letter-spacing:2px; color:#aaa; cursor:pointer; z-index:10; transition:0.3s; }
.av[data-p="watches"] .back:hover { color:#fff; }
/* HEADER */
.av[data-p="watches"] header { padding:140px 12% 60px; max-width:1200px; }
.av[data-p="watches"] header h1 { font-family: 'Playfair Display', serif; font-size:clamp(2.8rem,6vw,5rem); font-weight:900; line-height:1.1; margin-bottom: 20px;}
.av[data-p="watches"] header p { font-size:12px; letter-spacing:4px; color:#777; text-transform: uppercase; }
/* ARTICLE CONTENT WRAPPER */
.av[data-p="watches"] .content-wrapper { 
      display: flex; 
      padding: 0 12% 140px; 
      gap: 60px; 
      max-width: 1400px;
    }
.av[data-p="watches"] article { flex: 2; }
.av[data-p="watches"] article p { font-size:18px; line-height:1.9; color:#bbb; margin-bottom: 32px; font-weight: 300; }
.av[data-p="watches"] article h2 { font-family: 'Playfair Display', serif; font-size: 32px; margin: 60px 0 24px; color: #fff; border-left: 4px solid #fff; padding-left: 20px; }
/* STICKY IMAGE CONTAINER */
.av[data-p="watches"] .side-image-container { 
      flex: 1; 
      position: sticky; 
      top: 140px; 
      height: fit-content; 
    }
.av[data-p="watches"] .side-image-container img { 
      width: 100%; 
      border-radius: 4px; 
      filter: grayscale(0.4) contrast(1.1); 
      box-shadow: 0 20px 40px rgba(0,0,0,0.6);
      transition: 0.8s cubic-bezier(0.16, 1, 0.3, 1);
    }
.av[data-p="watches"] .side-image-container img:hover { filter: grayscale(0) scale(1.02); }
.av[data-p="watches"] .image-caption { font-size: 10px; letter-spacing: 2px; color: #555; text-transform: uppercase; margin-top: 15px; text-align: right; }
/* FEATURED QUOTE */
.av[data-p="watches"] .editorial-quote {
      font-family: 'Playfair Display', serif;
      font-style: italic;
      font-size: 24px;
      color: #fff;
      margin: 60px 0;
      padding: 40px;
      border-top: 1px solid rgba(255,255,255,0.1);
      border-bottom: 1px solid rgba(255,255,255,0.1);
      line-height: 1.4;
      text-align: center;
    }
/* SPEC BOXES */
.av[data-p="watches"] .comparison-box {
      background: rgba(255,255,255,0.02);
      border: 1px solid rgba(255,255,255,0.08);
      display: grid;
      grid-template-columns: 1fr 1fr;
      margin: 60px 0;
      padding: 40px;
      gap: 40px;
    }
.av[data-p="watches"] .comp-column h3 { font-size: 13px; letter-spacing: 3px; margin-bottom: 20px; color: #fff; text-transform: uppercase; }
.av[data-p="watches"] .comp-column.pros h3 { color: #d4af37; }
/* Gold/Watch */
.av[data-p="watches"] .comp-column.cons h3 { color: #e2e2e2; }
/* Steel/Car */
.av[data-p="watches"] .comp-list { list-style: none; }
.av[data-p="watches"] .comp-list li { font-size: 15px; color: #999; margin-bottom: 15px; padding-left: 20px; position: relative; }
.av[data-p="watches"] .comp-list li::before { content: '•'; position: absolute; left: 0; color: #444; }
/* FILM GRAIN */
@media max-width:1024px) {
.av[data-p="watches"] .content-wrapper { flex-direction: column; }.av[data-p="watches"] .side-image-container { position: relative; top: 0; order: -1; margin-bottom: 40px; }.av[data-p="watches"] header, .av[data-p="watches"] .content-wrapper { padding-left: 8%; padding-right: 8%; }
    
}

</style>

  <!-- Google AdSense -->
  <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX"
     crossorigin="anonymous"></script>
</head>

<body>
<div class="toast" id="toast"></div>
<div class="cart-overlay-bg" id="cartOverlay" onclick="closeCart()"></div>



<div id="progress-wrap"><div id="progress-bar"></div></div>

<div class="side-specs">
  <div class="spec-item">// RPM: 7200</div>
  <div class="spec-item">// GEAR: MANUAL</div>
  <div class="spec-item">// FUEL: HI-OCTANE</div>
  <div class="spec-item" id="live-time">// TIME: --:--</div>
</div>

<div class="mobile-overlay" id="mobileMenu">
  <a href="#hero">HOME</a>
  <a href="#news">NEWS</a>
  <a href="#journeys">JOURNEYS</a>
  <a href="#launch-pad">LATEST CARS</a>
  <a href="#safarnama">SAFARNAMA</a>
  <a href="#about">ABOUT</a>
  <a href="#shop" onclick="showView('shop')" style="color:var(--gold);">GARAGE SHOP</a>
</div>

<nav id="navbar">
  <a href="#article-manifesto" onclick="openAV('manifesto','ABOUT // MANIFESTO')" class="brand">DRIVAYAN</a>
  <div style="display:flex;gap:20px;align-items:center;">
    <div class="nav-links">
      <div class="nav-pill"></div>

      <!-- HOME -->
      <div class="nav-item-wrap has-dropdown">
        <a href="#hero" class="nav-item active">HOME</a>
        <div class="nav-dropdown">
          <span class="dd-label">// QUICK NAV</span>
          <a href="#hero"><i class="dd-icon">◈</i> HERO</a>
          <a href="#news"><i class="dd-icon">◈</i> LIVE WIRE</a>
          <a href="#launch-pad"><i class="dd-icon">◈</i> REGISTRY</a>
          <div class="dd-divider"></div>
          <a href="#about"><i class="dd-icon">◈</i> MANIFESTO</a>
        </div>
      </div>

      <!-- LATEST CARS -->
      <div class="nav-item-wrap has-dropdown">
        <a href="#" onclick="showView('main');jumpTo('launch-pad')" class="nav-item">LATEST CARS</a>
        <div class="nav-dropdown">
          <span class="dd-label">// BY SEGMENT</span>
          <a href="#" onclick="showView('main');jumpTo('launch-pad')"><i class="dd-icon">⚡</i> ELECTRIC</a>
          <a href="#" onclick="showView('main');jumpTo('launch-pad')"><i class="dd-icon">◈</i> SUV / 4X4</a>
          <a href="#" onclick="showView('main');jumpTo('launch-pad')"><i class="dd-icon">◈</i> SEDAN</a>
          <a href="#" onclick="showView('main');jumpTo('launch-pad')"><i class="dd-icon">◈</i> LUXURY</a>
          <div class="dd-divider"></div>
          <span class="dd-label">// BY BRAND</span>
          <a href="#" onclick="showView('main');jumpTo('launch-pad')"><i class="dd-icon">◈</i> MAHINDRA</a>
          <a href="#" onclick="showView('main');jumpTo('launch-pad')"><i class="dd-icon">◈</i> TATA</a>
          <a href="#" onclick="showView('main');jumpTo('launch-pad')"><i class="dd-icon">◈</i> MARUTI</a>
        </div>
      </div>

      <!-- NEWS -->
      <div class="nav-item-wrap has-dropdown">
        <a href="#news" class="nav-item">NEWS</a>
        <div class="nav-dropdown">
          <span class="dd-label">// CATEGORIES</span>
          <a href="#article-v8" onclick="openAV('v8','NEWS // INSIGHTS')"><i class="dd-icon">◈</i> INSIGHTS</a>
          <a href="#article-fuel" onclick="openAV('fuel','NEWS // ANALYSIS')"><i class="dd-icon">◈</i> ANALYSIS</a>
          <a href="#launches"><i class="dd-icon">◈</i> LAUNCHES</a>
          <div class="dd-divider"></div>
          <a href="#article-safari" onclick="openAV('safari','JOURNEYS // TATA SAFARI')"><i class="dd-icon">★</i> FEATURED</a>
        </div>
      </div>

      <!-- JOURNEYS -->
      <div class="nav-item-wrap has-dropdown">
        <a href="#journeys" class="nav-item">JOURNEYS</a>
        <div class="nav-dropdown">
          <span class="dd-label">// FORMATS</span>
          <a href="#article-safari" onclick="openAV('safari','JOURNEYS // TATA SAFARI')"><i class="dd-icon">◈</i> OWNERSHIP</a>
          <a href="#article-soul" onclick="openAV('soul','JOURNEYS // CULTURE')"><i class="dd-icon">◈</i> CULTURE</a>
          <a href="#article-modify" onclick="openAV('modify','JOURNEYS // LEGALITY')"><i class="dd-icon">◈</i> LEGALITY</a>
          <div class="dd-divider"></div>
          <span class="dd-label">// GEAR</span>
          <a href="#article-accessory" onclick="openAV('accessory','GEAR & GUPSHUP // OVERLAND KIT')"><i class="dd-icon">◈</i> OVERLAND KIT</a>
          <a href="#article-watches" onclick="openAV('watches','GEAR & GUPSHUP // LIFESTYLE')"><i class="dd-icon">◈</i> LIFESTYLE</a>
        </div>
      </div>

      <!-- SAFARNAMA -->
      <div class="nav-item-wrap has-dropdown">
        <a href="#safarnama" class="nav-item">SAFARNAMA</a>
        <div class="nav-dropdown">
          <span class="dd-label">// TRAVELOGUES</span>
          <a href="#article-rajasthan" onclick="openAV('rajasthan','SAFARNAMA // RAJASTHAN DIARIES')"><i class="dd-icon">◈</i> RAJASTHAN DIARIES</a>
          <a href="#" onclick="showView('main');jumpTo('safarnama')"><i class="dd-icon">◈</i> PROJECT GYPSY</a>
          <div class="dd-divider"></div>
          <a href="#article-manual" onclick="openAV('manual','GEAR & GUPSHUP // GUPSHUP')"><i class="dd-icon">◈</i> GUPSHUP</a>
        </div>
      </div>

      <!-- ABOUT -->
      <div class="nav-item-wrap has-dropdown">
        <a href="#about" class="nav-item">ABOUT</a>
        <div class="nav-dropdown">
          <span class="dd-label">// DRIVAYAN</span>
          <a href="#about"><i class="dd-icon">◈</i> MANIFESTO</a>
          <a href="https://www.instagram.com/drivayan"><i class="dd-icon">◈</i> INSTAGRAM</a>
          <a href="https://www.youtube.com/@drivayan"><i class="dd-icon">◈</i> YOUTUBE</a>
          <div class="dd-divider"></div>
          <a href="javascript:void(0)" id="openLoginNav"><i class="dd-icon">◈</i> MEMBER LOGIN</a>
        </div>
      </div>

      <!-- GARAGE SHOP -->
      <div class="nav-item-wrap has-dropdown">
        <a href="#shop" onclick="showView('shop')" class="nav-item" style="color:var(--gold);">GARAGE SHOP</a>
        <div class="nav-dropdown">
          <span class="dd-label">// THE COLLECTION</span>
          <a href="#shop" onclick="showView('shop')"><i class="dd-icon">◈</i> ALL PRODUCTS</a>
          <a href="#shop" onclick="showView('shop')"><i class="dd-icon">◈</i> COLLECTIONS</a>
          <a href="#shop" onclick="showView('shop')"><i class="dd-icon" style="color:var(--gold);">★</i> NEW DROPS</a>
          <div class="dd-divider"></div>
          <span class="dd-label">// CATEGORIES</span>
          <a href="#shop" onclick="showView('shop');setTimeout(()=>filterProducts('apparel',document.querySelector('[data-cat=apparel]')),300)"><i class="dd-icon">◈</i> APPAREL</a>
          <a href="#shop" onclick="showView('shop');setTimeout(()=>filterProducts('accessories',document.querySelector('[data-cat=accessories]')),300)"><i class="dd-icon">◈</i> ACCESSORIES</a>
          <a href="#shop" onclick="showView('shop');setTimeout(()=>filterProducts('prints',document.querySelector('[data-cat=prints]')),300)"><i class="dd-icon">◈</i> ART PRINTS</a>
          <div class="dd-divider"></div>
          <a href="#shop" onclick="showView('shop');setTimeout(()=>filterProducts('ltd',document.querySelector('[data-cat=ltd]')),300)"><i class="dd-icon" style="color:var(--gold);">◈</i> LIMITED EDITIONS</a>
        </div>
      </div>

    </div>
    <button class="cart-btn" id="mainCartBtn" onclick="toggleCart()" aria-label="Cart">
      <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4z"/>
        <line x1="3" y1="6" x2="21" y2="6"/><path d="M16 10a4 4 0 01-8 0"/>
      </svg>
      <span class="cart-count" id="cartCount">0</span>
    </button>
    <button class="theme-toggle-btn" id="themeToggle" aria-label="Toggle Theme">
      <svg class="moon-icon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
      <svg class="sun-icon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="display:none">
        <circle cx="12" cy="12" r="5"/><line x1="12" y1="1" x2="12" y2="3"/><line x1="12" y1="21" x2="12" y2="23"/>
        <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
        <line x1="1" y1="12" x2="3" y2="12"/><line x1="21" y1="12" x2="23" y2="12"/>
      </svg>
    </button>
    <button class="menu-trigger" id="menuBtn">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <line x1="3" y1="12" x2="21" y2="12"/><line x1="3" y1="6" x2="21" y2="6"/><line x1="3" y1="18" x2="21" y2="18"/>
      </svg>
    </button>
  </div>
</nav>

<div id="main-view">
<!-- ===== HERO ===== -->
<section class="hero" id="hero">
  <div class="hero-content reveal">
    <span class="label">Automotive Excellence</span>
    <h1>Where Every Drive Tells a Story</h1>
    <p>Cinematic journeys. Owner stories. Indian car culture decoded and delivered with mechanical precision.</p>
    <a href="#journeys" class="cta">DISCOVER THE ARCHIVE</a>
  </div>
  <div class="hero-img-wrap reveal">
    <img src="https://images.unsplash.com/photo-1492144534655-ae79c964c9d7?auto=format&fit=crop&q=80&w=1400"
         id="hero-img" alt="Drivayan Hero" class="theme-logo" loading="eager">
  </div>
</section>

<!-- ===== NEWS ===== -->
<section id="news" style="padding-bottom:0;">
  <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:0;">
    <div class="label section-title" style="margin-bottom:0;">Live Automotive Wire</div>
    <div style="display:flex;align-items:center;gap:16px;">
      <div id="news-status" style="display:flex;align-items:center;gap:8px;font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:2px;">
        <span id="news-pulse" style="width:6px;height:6px;border-radius:50%;background:var(--muted);display:inline-block;"></span>
        <span id="news-status-text">INITIALISING</span>
      </div>
      <button id="news-refresh-btn" onclick="fetchLiveNews()" title="Refresh news" style="background:none;border:1px solid var(--border);color:var(--muted);width:32px;height:32px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all 0.3s;border-radius:2px;" onmouseover="this.style.borderColor='var(--text)';this.style.color='var(--text)'" onmouseout="this.style.borderColor='var(--border)';this.style.color='var(--muted)'">
        <svg id="refresh-icon" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="23 4 23 10 17 10"/><path d="M20.49 15a9 9 0 1 1-2.12-9.36L23 10"/></svg>
      </button>
    </div>
  </div>

  <div class="news-ticker-wrap" style="margin-top:20px;">
    <div class="ticker-content" id="newsTicker"></div>
  </div>

  <!-- Ad Slot 1: Leaderboard — between ticker and news grid -->
  <div class="ad-slot-wrap" style="margin-bottom:36px;">
    <span class="ad-slot-label">// SPONSORED</span>
    <ins class="adsbygoogle"
         style="display:inline-block;width:728px;max-width:100%;height:90px;"
         data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
         data-ad-slot="1111111111"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
  </div>

  <!-- LIVE NEWS GRID -->
  <div id="live-news-container" style="margin-bottom:80px;">

    <!-- SKELETON LOADER -->
    <div id="news-skeleton" style="display:grid;grid-template-columns:1.8fr 1fr;gap:40px;">
      <div style="aspect-ratio:16/9;background:var(--card);border:1px solid var(--border);position:relative;overflow:hidden;">
        <div class="skeleton-shimmer"></div>
        <div style="position:absolute;bottom:0;left:0;width:100%;padding:40px;background:linear-gradient(transparent,rgba(0,0,0,0.5));">
          <div style="height:8px;width:80px;background:rgba(255,255,255,0.08);margin-bottom:16px;border-radius:2px;"></div>
          <div style="height:26px;width:90%;background:rgba(255,255,255,0.08);margin-bottom:10px;border-radius:2px;"></div>
          <div style="height:18px;width:55%;background:rgba(255,255,255,0.05);border-radius:2px;"></div>
        </div>
      </div>
      <div style="display:flex;flex-direction:column;">
        <div style="padding:30px 0;border-bottom:1px solid var(--border);position:relative;overflow:hidden;flex:1;">
          <div class="skeleton-shimmer"></div>
          <div style="height:7px;width:55px;background:var(--card);margin-bottom:14px;border-radius:2px;"></div>
          <div style="height:15px;width:88%;background:var(--card);border-radius:2px;"></div>
        </div>
        <div style="padding:30px 0;border-bottom:1px solid var(--border);position:relative;overflow:hidden;flex:1;">
          <div class="skeleton-shimmer"></div>
          <div style="height:7px;width:55px;background:var(--card);margin-bottom:14px;border-radius:2px;"></div>
          <div style="height:15px;width:75%;background:var(--card);border-radius:2px;"></div>
        </div>
        <div style="padding:30px 0;position:relative;overflow:hidden;flex:1;">
          <div class="skeleton-shimmer"></div>
          <div style="height:7px;width:55px;background:var(--card);margin-bottom:14px;border-radius:2px;"></div>
          <div style="height:15px;width:82%;background:var(--card);border-radius:2px;"></div>
        </div>
      </div>
    </div>

    <!-- LIVE CONTENT -->
    <div id="news-live-content" style="display:none;"></div>

    <!-- ERROR STATE -->
    <div id="news-error" style="display:none;padding:60px;text-align:center;border:1px solid var(--border);">
      <div style="font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:3px;margin-bottom:20px;">// SIGNAL LOST</div>
      <p style="color:var(--muted);font-size:14px;margin-bottom:30px;">Could not retrieve live feed. Showing archived stories.</p>
      <button onclick="fetchLiveNews()" class="cta" style="font-size:9px;padding:14px 30px;">RETRY CONNECTION</button>
    </div>
  </div>

  <!-- SECONDARY NEWS ROW -->
  <div id="news-secondary-row" style="display:none;margin-bottom:80px;">
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:24px;padding-bottom:12px;border-bottom:1px solid var(--border);">
      <span class="label" style="margin:0;">// LATEST DISPATCHES</span>
      <span id="news-timestamp" style="font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:2px;"></span>
    </div>
    <div id="news-secondary-grid" style="display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:24px;"></div>
  </div>

</section>

<!-- ===== AUTOMOTIVE REGISTRY ===== -->
<section id="launch-pad">
  <div class="label section-title">Automotive Registry / 2026</div>
  <div id="dynamic-car-grid" class="car-grid-container"></div>
</section>

<!-- ===== JOURNEYS ===== -->
<section id="journeys">
  <div class="label section-title">Latest Journeys</div>
  <div class="grid">
    <a href="#article-safari" onclick="openAV('safari','JOURNEYS // TATA SAFARI')" class="card reveal">
      <div class="img-container">
        <div class="spec-hud">
          <div class="hud-line"><span>Engine</span><span class="hud-value">2.0L Kryotec</span></div>
          <div class="hud-line"><span>Power</span><span class="hud-value">170 PS</span></div>
          <div class="hud-line"><span>Torque</span><span class="hud-value">350 NM</span></div>
          <div class="hud-line"><span>Drivetrain</span><span class="hud-value">FWD / AT</span></div>
        </div>
        <img src="https://images.unsplash.com/photo-1568605117036-5fe5e7bab0b7?auto=format&fit=crop&q=80&w=600" alt="Tata Safari">
      </div>
      <span class="label">Ownership</span>
      <h3>Tata Safari: Long Term</h3>
    </a>

    <a href="#article-soul" onclick="openAV('soul','JOURNEYS // CULTURE')" class="card reveal">
      <div class="img-container">
        <img src="https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?auto=format&fit=crop&q=80&w=600" loading="lazy" alt="Cars with Soul">
      </div>
      <span class="label">Culture</span>
      <h3>When Cars Had Soul</h3>
      <p style="font-size:13px;color:var(--muted);">Before screens and sensors replaced the raw feel of the wheel.</p>
    </a>

    <a href="#article-modify" onclick="openAV('modify','JOURNEYS // LEGALITY')" class="card reveal">
      <div class="img-container">
        <img src="https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?auto=format&fit=crop&q=80&w=600" loading="lazy" alt="Modify India">
      </div>
      <span class="label">Legality</span>
      <h3>Modify: The India Debate</h3>
      <p style="font-size:13px;color:var(--muted);">Why the current modification laws stifle Indian creativity.</p>
    </a>
  </div>
</section>


<!-- Ad Slot 2: In-Feed Native — between Journeys and Safarnama -->
<div style="padding: 0 8%; margin-bottom: 0;">
  <div class="ad-infeed ad-slot-wrap" style="border-top:none;border-bottom:none;padding:20px;">
    <span class="ad-slot-label" style="right:24px;">// SPONSORED</span>
    <ins class="adsbygoogle"
         style="display:block;width:100%;height:auto;"
         data-ad-format="fluid"
         data-ad-layout="in-article"
         data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
         data-ad-slot="2222222222"></ins>
    <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
  </div>
</div>

<!-- ===== SAFARNAMA ===== -->
<section id="safarnama">
  <div class="safarnama-container reveal">
   <img src="https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&q=80&w=600" loading="lazy" alt="Cars with Soul">
    <div class="safarnama-content">
      <span class="label">Safar Nama</span>
      <h2>1,001 Horses in the Thar Desert</h2>
      <p style="color:var(--muted);font-weight:300;font-size:1.1rem;margin-bottom:30px;">Jaipur to Jaisalmer in the Lamborghini Revuelto</p>
      <a href="#article-rajasthan" onclick="openAV('rajasthan','SAFARNAMA // RAJASTHAN DIARIES')" class="cta">READ TRAVELOGUES</a>
    </div>
  </div>
</section>

<!-- ===== LAUNCH PAD Q1 2026 ===== -->
<section id="launches" style="padding-top:100px;">
  <div class="label section-title">Launch Pad / Q1 2026</div>
  <div class="launch-grid">
    <a href="#" class="launch-card reveal">
      <span class="status-tag">BOOKINGS OPEN</span>
      <h3 style="font-family:'Playfair Display';">Mahindra XEV 9e <br>Cineluxe Edition</h3>
      <p style="font-size:13px;opacity:0.7;margin:10px 0;">The flagship EV gets a 'Private Lounge' treatment with triple-HD display and Satin Black finish.</p>
      <span class="launch-date">// DELIVERY: MARCH 10, 2026</span>
    </a>
    <a href="#" class="launch-card reveal">
      <span class="status-tag">PRICE REVEAL</span>
      <h3 style="font-family:'Playfair Display';">Renault Duster <br>(New Gen)</h3>
      <p style="font-size:13px;opacity:0.7;margin:10px 0;">The icon returns. Expected with a 1.5L Petrol and a strong hybrid system to challenge the mid-size SUV kings.</p>
      <span class="launch-date" id="duster-date">// REVEAL: MARCH 17, 2026</span>
    </a>
    <a href="#" class="launch-card reveal">
      <span class="status-tag status-live">JUST LAUNCHED</span>
      <h3 style="font-family:'Playfair Display';">Mercedes-Benz <br>V-Class LWB</h3>
      <p style="font-size:13px;opacity:0.7;margin:10px 0;">Ultra-luxury moving lounge launched with 2.0L Diesel and executive captain seats.</p>
      <span class="launch-date">// PRICE: ₹1.40 CR*</span>
    </a>
    <a href="#" class="launch-card reveal">
      <span class="status-tag">SPIED: UNDISGUISED</span>
      <h3 style="font-family:'Playfair Display';">Maruti Suzuki <br>Brezza Facelift</h3>
      <p style="font-size:13px;opacity:0.7;margin:10px 0;">Caught testing with a new chrome-heavy fascia and a 6-speed manual gearbox.</p>
      <span class="launch-date">// EXPECTED: MAY 2026</span>
    </a>
  </div>
</section>

<!-- ===== GEAR & GUPSHUP ===== -->
<section id="gupshup" style="border-top:1px solid var(--border);padding-top:120px;">
  <div class="label section-title">Gear &amp; Gupshup</div>
  <div class="gupshup-grid">
    <div class="gupshup-item reveal">
      <div class="scanner-line"></div>
      <span class="label">01 / Mechanical</span>
      <h3>The Overlanding Essential Kit</h3>
      <p style="color:var(--muted);font-size:14px;margin-top:15px;">A curated breakdown of the recovery gear that actually matters when the tarmac ends and the trail begins.</p>
      <a href="#article-accessory" onclick="openAV('accessory','GEAR & GUPSHUP // OVERLAND KIT')" class="side-card" style="margin-top:30px;border-bottom:none;font-size:11px;letter-spacing:2px;">VIEW THE LIST →</a>
    </div>
    <div class="gupshup-item reveal">
      <div class="scanner-line"></div>
      <span class="label">02 / Discussion</span>
      <h3>Is the Manual Dead?</h3>
      <p style="color:var(--muted);font-size:14px;margin-top:15px;">The DRIVAYAN roundtable on why enthusiasts are fighting to keep the third pedal alive in an automatic world.</p>
      <a href="#article-manual" onclick="openAV('manual','GEAR & GUPSHUP // GUPSHUP')" class="side-card" style="margin-top:30px;border-bottom:none;font-size:11px;letter-spacing:2px;">JOIN THE CONVERSATION →</a>
    </div>
    <div class="gupshup-item reveal">
      <div class="scanner-line"></div>
      <span class="label">03 / Lifestyle</span>
      <h3>Chronographs &amp; Camshafts</h3>
      <p style="color:var(--muted);font-size:14px;margin-top:15px;">Exploring the deep-rooted obsession between vintage timepieces and classic automotive engineering.</p>
      <a href="#article-watches" onclick="openAV('watches','GEAR & GUPSHUP // LIFESTYLE')" class="side-card" style="margin-top:30px;border-bottom:none;font-size:11px;letter-spacing:2px;">READ MORE →</a>
    </div>
    <div class="gupshup-item reveal">
      <div class="scanner-line"></div>
      <span class="label">04 / Restoration</span>
      <h3>Project: Gypsy King</h3>
      <p style="color:var(--muted);font-size:14px;margin-top:15px;">A technical diary of restoring a 1998 Maruti Gypsy to its former glory, with a few modern secrets under the hood.</p>
      <a href="#" onclick="showView('main');jumpTo('safarnama')" class="side-card" style="margin-top:30px;border-bottom:none;font-size:11px;letter-spacing:2px;">EXPLORE THE BUILD →</a>
    </div>
  </div>
</section>

<!-- ===== ABOUT ===== -->
<section id="about" style="text-align:center;padding:180px 8%;">
  <h2 style="font-size:clamp(2rem,4vw,3.5rem);max-width:1000px;margin:0 auto;font-style:italic;" class="reveal">
    "Where Every Drive Tells A Story"
  </h2>
  <p class="label reveal" style="margin-top:40px;">— The Drivayan Manifesto</p>
</section>
</div>

<div id="shop-view">
<!-- ===== HERO ===== -->
<section class="shop-hero">
  <div class="shop-hero-bg"></div>
  <div class="shop-hero-grid"></div>
  <div class="shop-hero-content">
    <span class="hero-eyebrow">// DRIVAYAN GARAGE — SS26 COLLECTION</span>
    <h1>Wear the<br><em>Culture.</em></h1>
    <p>Apparel and accessories for those who measure weekends in kilometres. Crafted for Indian roads, designed for the driver's soul.</p>
    <div style="display:flex;gap:16px;flex-wrap:wrap;">
      <a href="#products" class="cta cta-gold">SHOP NOW</a>
      <a href="#collections" class="cta">VIEW COLLECTIONS</a>
    </div>
    <div class="hero-stats">
      <div>
        <span class="hero-stat-val">12</span>
        <span class="hero-stat-label">Products</span>
      </div>
      <div>
        <span class="hero-stat-val">3</span>
        <span class="hero-stat-label">Collections</span>
      </div>
      <div>
        <span class="hero-stat-val">100%</span>
        <span class="hero-stat-label">Indian Made</span>
      </div>
    </div>
  </div>
  <div class="hero-product-float">
    <div class="hero-product-ring"></div>
    <img class="hero-product-img"
      src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?auto=format&fit=crop&q=80&w=600"
      alt="DRIVAYAN Tee">
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-wrap">
  <div class="marquee-track" id="marqueeTrack"></div>
</div>

<!-- ===== FEATURED PRODUCT ===== -->
<section class="section" id="featured">
  <div class="section-head reveal">
    <div>
      <span class="section-label">// EDITOR'S PICK</span>
      <h2 class="section-title">Drop of the Season</h2>
    </div>
    <a href="#products" class="cta" style="font-size:9px;padding:14px 28px;">SEE ALL DROPS</a>
  </div>

  <div class="featured-product reveal">
    <div class="featured-product-img">
      <img src="https://images.unsplash.com/photo-1620799140188-3b2a02fd9a77?auto=format&fit=crop&q=80&w=900"
           alt="Drivayan Hoodie" loading="lazy">
    </div>
    <div class="featured-product-details">
      <span class="featured-tag">// LIMITED DROP — ONLY 50 MADE</span>
      <h2>The Drivayan<br>Heavyweight Hoodie</h2>
      <p class="featured-desc">Named Your own Brand. 380GSM French terry cotton. Embroidered engine cross-section on the chest. Garment washed for that worn-in feeling from day one.</p>
      <div class="featured-price">₹3,499</div>
      <div>
        <span style="font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:2px;color:var(--muted);display:block;margin-bottom:10px;">// SELECT SIZE</span>
        <div class="size-selector">
          <button class="size-btn" onclick="selectSize(this,'S')">S</button>
          <button class="size-btn" onclick="selectSize(this,'M')">M</button>
          <button class="size-btn selected" onclick="selectSize(this,'L')">L</button>
          <button class="size-btn" onclick="selectSize(this,'XL')">XL</button>
          <button class="size-btn" onclick="selectSize(this,'XXL')">XXL</button>
        </div>
      </div>
      <div style="display:flex;gap:12px;flex-wrap:wrap;">
        <button class="cta cta-gold" onclick="addToCart('Drivayan Hoodie','₹3,499','https://images.unsplash.com/photo-1620799140188-3b2a02fd9a77?auto=format&fit=crop&q=80&w=200','APPAREL')">ADD TO GARAGE BAG</button>
        <button class="cta" style="padding:16px 24px;font-size:9px;" onclick="openModal(0)">DETAILS</button>
      </div>
    </div>
  </div>
</section>

<!-- ===== COLLECTIONS ===== -->
<section class="section" id="collections" style="padding-top:0;">
  <div class="section-head reveal">
    <div>
      <span class="section-label">// SS26 COLLECTIONS</span>
      <h2 class="section-title">By the Story</h2>
    </div>
  </div>
  <div class="collections-grid reveal">
    <a href="#products" class="collection-tile" data-filter="apparel">
      <img class="tile-img" src="https://images.unsplash.com/photo-1441986300917-64674bd600d8?auto=format&fit=crop&q=80&w=800" alt="Tarmac Collection">
      <div class="collection-label">
        <span>01 / APPAREL</span>
        <h3>The Tarmac Collection</h3>
      </div>
    </a>
    <a href="#products" class="collection-tile" data-filter="accessories">
      <img class="tile-img" src="https://images.unsplash.com/photo-1556306535-38febf6782e7?auto=format&fit=crop&q=80&w=600" alt="Pit Lane Accessories">
      <div class="collection-label">
        <span>02 / ACCESSORIES</span>
        <h3>Pit Lane Essentials</h3>
      </div>
    </a>
    <a href="#products" class="collection-tile" data-filter="prints">
      <img class="tile-img" src="https://images.unsplash.com/photo-1513364776144-60967b0f800f?auto=format&fit=crop&q=80&w=600" alt="Print Works">
      <div class="collection-label">
        <span>03 / PRINTS</span>
        <h3>Drive Stories</h3>
      </div>
    </a>
  </div>
</section>

<!-- ===== PRODUCTS ===== -->
<section class="section" id="products" style="padding-top:0;">
  <div class="section-head reveal">
    <div>
      <span class="section-label">// THE GARAGE</span>
      <h2 class="section-title">All Products</h2>
    </div>
  </div>
  <div class="filter-bar reveal">
    <button class="filter-btn active-gold" data-cat="all" onclick="filterProducts('all',this)">ALL</button>
    <button class="filter-btn" data-cat="apparel" onclick="filterProducts('apparel',this)">APPAREL</button>
    <button class="filter-btn" data-cat="accessories" onclick="filterProducts('accessories',this)">ACCESSORIES</button>
    <button class="filter-btn" data-cat="prints" onclick="filterProducts('prints',this)">PRINTS</button>
    <button class="filter-btn" data-cat="ltd" onclick="filterProducts('ltd',this)">LIMITED</button>
  </div>
  <div class="product-grid reveal" id="productGrid"></div>
</section>

<!-- ===== TESTIMONIALS ===== -->
<section class="section" style="padding-top:0;">
  <div class="section-head reveal">
    <div>
      <span class="section-label">// DRIVER VERDICTS</span>
      <h2 class="section-title">From the Community</h2>
    </div>
  </div>
  <div class="testimonials reveal">
    <div class="testimonial">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"The Kryotec hoodie is insane quality. Wore it on a Spiti road trip and it held up brilliantly. The embroidery alone is worth every rupee."</p>
      <span class="testi-author">// Arjun M. — Mumbai • Tata Safari Owner</span>
    </div>
    <div class="testimonial">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"Finally a car culture brand that understands the Indian enthusiast. Not a generic US import aesthetic — this is built for us."</p>
      <span class="testi-author">// Priya S. — Bangalore • Mahindra Thar Owner</span>
    </div>
    <div class="testimonial">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"The Rajasthan print is hanging in my garage. Every guest asks about it. Ships fast, packaged beautifully — felt premium from the box itself."</p>
      <span class="testi-author">// Rohan K. — Delhi • Classic Car Restorer</span>
    </div>
    <div class="testimonial">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"Bought the canvas tote for my daughter who's obsessed with cars. The gearshift detail is perfect. A thoughtful gift from a brand that gets it."</p>
      <span class="testi-author">// Suresh P. — Pune • Skoda Kushaq Owner</span>
    </div>
  </div>
</section>

<!-- ===== NEWSLETTER ===== -->
<div class="newsletter reveal">
  <div class="newsletter-content">
    <span class="section-label">// STAY IN THE LOOP</span>
    <h2>New Drops, First.</h2>
    <p>Get early access to limited releases and exclusive Drivayan community offers.</p>
  </div>
  <div>
    <form class="newsletter-form" onsubmit="handleNewsletter(event)">
      <input type="email" class="newsletter-input" placeholder="YOUR EMAIL ADDRESS" required>
      <button type="submit" class="newsletter-submit">SUBSCRIBE</button>
    </form>
    <p style="font-family:'JetBrains Mono',monospace;font-size:8px;color:var(--muted);letter-spacing:1px;margin-top:10px;">// No spam. Only drops. Unsubscribe anytime.</p>
  </div>
</div>

<!-- ===== FOOTER ===== -->
<footer style="padding:80px 8% 40px;border-top:1px solid var(--border);">
  <div style="display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:60px;margin-bottom:60px;">
    <div>
      <span style="font-weight:900;letter-spacing:8px;font-size:1.1rem;display:block;margin-bottom:16px;color:var(--text);">DRIVAYAN</span>
      <p style="color:var(--muted);font-size:13px;line-height:1.7;max-width:260px;">India's premier automotive storytelling platform. Wear the culture.</p>
    </div>
    <div>
      <h4 style="font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:3px;color:var(--gold);text-transform:uppercase;margin-bottom:20px;">// SHOP</h4>
      <a onclick="filterProducts('all',document.querySelector('[data-cat=all]'))" style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;cursor:pointer;text-decoration:none;" onmouseover="this.style.color='var(--text)'" onmouseout="this.style.color='var(--muted)'">All Products</a>
      <a onclick="filterProducts('apparel',document.querySelector('[data-cat=apparel]'))" style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;cursor:pointer;text-decoration:none;" onmouseover="this.style.color='var(--text)'" onmouseout="this.style.color='var(--muted)'">Apparel</a>
      <a onclick="filterProducts('accessories',document.querySelector('[data-cat=accessories]'))" style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;cursor:pointer;text-decoration:none;" onmouseover="this.style.color='var(--text)'" onmouseout="this.style.color='var(--muted)'">Accessories</a>
      <a onclick="filterProducts('prints',document.querySelector('[data-cat=prints]'))" style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;cursor:pointer;text-decoration:none;" onmouseover="this.style.color='var(--text)'" onmouseout="this.style.color='var(--muted)'">Art Prints</a>
    </div>
    <div>
      <h4 style="font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:3px;color:var(--gold);text-transform:uppercase;margin-bottom:20px;">// DRIVAYAN</h4>
      <a onclick="showView('main')" style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;cursor:pointer;text-decoration:none;" onmouseover="this.style.color='var(--text)'" onmouseout="this.style.color='var(--muted)'">Home</a>
      <a onclick="showView('main');jumpTo('journeys')" style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;cursor:pointer;text-decoration:none;" onmouseover="this.style.color='var(--text)'" onmouseout="this.style.color='var(--muted)'">Journeys</a>
      <a onclick="showView('main');jumpTo('news')" style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;cursor:pointer;text-decoration:none;" onmouseover="this.style.color='var(--text)'" onmouseout="this.style.color='var(--muted)'">News</a>
    </div>
    <div>
      <h4 style="font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:3px;color:var(--gold);text-transform:uppercase;margin-bottom:20px;">// SUPPORT</h4>
      <span style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;">Shipping Policy</span>
      <span style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;">Returns &amp; Exchanges</span>
      <a href="https://www.instagram.com/drivayan" style="display:block;color:var(--muted);font-size:13px;margin-bottom:10px;text-decoration:none;" onmouseover="this.style.color='var(--text)'" onmouseout="this.style.color='var(--muted)'">Instagram</a>
    </div>
  </div>
  <div style="display:flex;justify-content:space-between;padding-top:30px;border-top:1px solid var(--border);">
    <span style="font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:2px;">© 2026 DRIVAYAN STUDIO.</span>
    <span style="font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:2px;">// MADE IN INDIA ◈ SHIPPED ACROSS BHARAT</span>
  </div>
</footer>
</div>


<div class="av" data-p="accessory">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">GEAR & GUPSHUP // OVERLAND KIT</span>
  </div>
  <header>
    <p>Gear & Gupshup</p>
    <h1>The Overlanding Essential Kit: Beyond the Accessory Catalog</h1>
  </header>

  <article>
    <p>
      Overlanding has a marketing problem. If you spend five minutes on social media, you’d be convinced that you cannot leave the pavement without a ₹2-lakh roof-top tent, a snorkel, and enough LED light bars to be seen from the International Space Station. But at <i>DRIVAYAN</i>, we know the truth: the best overlanding kit isn’t the one that looks the best in a campsite photo; it’s the one that gets you home when the monsoon turns a trail into a river.
    </p>

    <p>
      When the tarmac ends in the remote corners of Arunachal or the deep sands of Rajasthan, your vehicle ceases to be a status symbol and becomes a life-support system. Here is a curated breakdown of the recovery and survival gear that actually matters.
    </p>

    <h2>1. The Science of Traction</h2>
    <p>
      Before you invest in a winch, invest in <strong>Traction Boards</strong>. In the Indian context—where soft silt and slushy black cotton soil are common—traction boards (like Maxtrax or high-quality equivalents) are your first line of defense. They require no anchor point, no electricity, and zero mechanical knowledge. They are the simplest way to turn a "stuck" into a "story."
    </p>

    <div class="pull-quote">
        "Recovery is not about brute force; it is about the management of friction and the respect for physics."
    </div>

    <h2>2. Kinetic Energy: The Invisible Tow</h2>
    <p>
      The traditional yellow tow strap you find in most "emergency kits" is a dangerous relic. It has no stretch, which means when the towing vehicle lunges, it sends a violent shock-load through both chassis. 
    </p>
    <p>
      The essential upgrade is a <strong>Kinetic Recovery Rope</strong>. These ropes are designed to stretch up to 30%, using the kinetic energy of the lead vehicle to gently "slingshot" the stuck vehicle out. Paired with <strong>Soft Shackles</strong>—which are safer and lighter than traditional metal D-shackles—this setup minimizes the risk of flying metal should a component fail.
    </p>

    <div class="gear-box">
      <div class="gear-column active">
        <h3>THE RECOVERY CORE</h3>
        <ul class="gear-list">
          <li><strong>Kinetic Rope:</strong> Rated for at least 3x your vehicle's Gross Vehicle Weight (GVW).</li>
          <li><strong>Traction Boards:</strong> Essential for self-recovery in sand and deep slush.</li>
          <li><strong>Heavy-Duty Compressor:</strong> Because "airing down" to 15 PSI is the best free mod for traction.</li>
          <li><strong>Long-Handle Shovel:</strong> The most underrated tool in the world. Digging is often the only way out.</li>
        </ul>
      </div>
      <div class="gear-column passive">
        <h3>THE SUPPORT SYSTEM</h3>
        <ul class="gear-list">
          <li><strong>Tire Plug Kit:</strong> A puncture in the wild is an inconvenience; two punctures are a crisis.</li>
          <li><strong>Basic Tool Roll:</strong> Specifically 10mm, 12mm, and 14mm sockets (the holy trinity of Japanese/Indian cars).</li>
          <li><strong>Fire Extinguisher:</strong> Mounted within arm's reach of the driver. No exceptions.</li>
          <li><strong>Jump Starter:</strong> A portable lithium pack to avoid being stranded by a parasitic battery drain.</li>
        </ul>
      </div>
    </div>

    <h2>3. The Air Management Strategy</h2>
    <p>
      If you are still driving on the trail with highway tire pressures, you are fighting a losing battle. Lowering your tire pressure increases the "footprint" of your tire, allowing you to float over obstacles rather than dig into them. However, you cannot air down if you cannot air back up. A high-output, hard-mounted or portable <strong>12V Air Compressor</strong> is the most utilized piece of gear in any veteran overlander's kit.
    </p>

    <h2>4. The Human Element: Gupshup & Wisdom</h2>
    <p>
      The most essential piece of kit isn't made of steel or nylon—it’s your <strong>Situational Awareness</strong>. No amount of gear can compensate for poor line choice or over-confidence. In our "Gupshup" sessions with seasoned trail-leaders, the advice is always the same: <i>Walk the obstacle before you drive it.</i> 
    </p>
    <p>
      In India, "gear" also includes local intelligence. A map that works offline (like Gaia or OnX) and a satellite communicator (where legal) or a high-gain radio can be the difference between a cold night in the car and a warm bed at home.
    </p>

    <h2>The Verdict</h2>
    <p>
      Don't build a car for the internet; build it for the terrain. Start with the basics: tires, air management, and kinetic recovery. Everything else—the fridges, the awnings, the modular kitchens—is just luxury. The goal of overlanding is to explore the world, not to carry your entire house into it.
    </p>
    <p style="font-style: italic; color: #fff;">
        Stay gritty. Stay prepared. See you where the road ends.
    </p>
  </article>
</div>

<div class="av" data-p="fuel">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">NEWS // ANALYSIS</span>
  </div>
  <header>
    <h1>Petrol vs Diesel 2026: The Final Choice at the Crossroads</h1>
    <p>A Comprehensive Guide to India's Shifting Automotive Landscape</p>
  </header>

  <article>
    <p>
      As we navigate through 2026, the age-old "Petrol or Diesel?" question has evolved into a complex equation of taxation, regulation, and maintenance. Gone are the days when a ₹10 difference at the pump made Diesel an automatic choice. Today, the decision requires a surgical look at your lifestyle, your city, and your appetite for long-term risk.
    </p>

    <h2>The Regulatory Hammer: CAFE III & RDE</h2>
    <p>
      The 2026 landscape is defined by the upcoming <b>CAFE III (Corporate Average Fuel Efficiency)</b> norms scheduled for April 2027. Manufacturers are already pivoting. Diesel engines, burdened by the need for complex Selective Catalytic Reduction (SCR) systems and DPF hardware to meet strict Nitrogen Oxide (NOx) limits, have seen their price premiums swell to ₹2–3 Lakhs over Petrol counterparts.
    </p>

    <div class="comparison-box">
      <div class="comp-column pros">
        <h3>PETROL (THE URBAN CHOICE)</h3>
        <ul class="comp-list">
          <li><b>Lower Entry Barrier:</b> Significantly lower on-road price in 2026.</li>
          <li><b>Regulatory Peace:</b> Not affected by the 10-year scrap rule in NCR.</li>
          <li><b>Simplicity:</b> No DPF clogging issues in heavy city traffic.</li>
          <li><b>Refinement:</b> Vibration-free idling and linear power delivery.</li>
          <li><b>Turbo Tech:</b> Modern Turbo-Petrols now offer Diesel-like torque.</li>
        </ul>
      </div>
      <div class="comp-column cons">
        <h3>DIESEL (THE LONG-HAULER)</h3>
        <ul class="comp-list">
          <li><b>Torque Dominance:</b> Unbeatable "pulling power" for SUVs and hills.</li>
          <li><b>Efficiency:</b> Still delivers 25-30% better real-world fuel economy.</li>
          <li><b>Range:</b> Fewer fuel stops on the 1000km+ highway runs.</li>
          <li><b>Resale Value:</b> In Tier-2/3 towns, Diesel remains the "Cash King."</li>
          <li><b>Heavy Loading:</b> The only logical choice for 7-seater load lugging.</li>
        </ul>
      </div>
    </div>

    <h2>The Math: When Does Diesel Pay Back?</h2>
    <p>
      In 2026, the "Break-Even" point has pushed further into the distance. With Petrol at ~₹105 and Diesel at ~₹92 in major metros, the fuel price gap is narrow. Combined with higher service costs—Diesel oil changes and DPF additive (AdBlue) refills—you realistically need to drive <b>1,500 km per month</b> (18,000 km/year) to justify the upfront Diesel cost within 5 years.
    </p>

    <h2>The DPF Nightmare: A City Warning</h2>
    <p>
      If your daily drive is less than 10km in bumper-to-bumper traffic, a 2026 Diesel engine is a liability. Modern Diesel Particulate Filters (DPF) require "regeneration"—which means driving at high speeds for 20 minutes. Without this, your SUV goes into "Limp Mode." For the pure city dweller, the <b>Turbo-Petrol</b> or the emerging <b>Strong Hybrid</b> has effectively replaced the small Diesel engine.
    </p>

    <h2>The Verdict</h2>
    <p>
      The year 2026 marks the "Sunset Era" for small Diesels. If you are buying a hatchback or a compact sedan, stick to <b>Petrol</b>. However, if you are eyeing a Safari, XUV700, or Scorpio-N for pan-India touring, <b>Diesel</b> remains the soul of the machine.
    </p>

    <p>
      Choose with your head for the city, but let your heart (and your highway mileage) decide for the open road.
    </p>
  </article>
</div>

<div class="av" data-p="rajasthan">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">SAFARNAMA // RAJASTHAN DIARIES</span>
  </div>
  <header>
    <h1>Safar Nama: 1,001 Horses in the Thar Desert</h1>
    <p>Jaipur to Jaisalmer in the Lamborghini Revuelto</p>
  </header>

  <article>
    <p>
      The Pink City was still asleep when the V12 woke up. In the subterranean parking of a Jaipur heritage hotel, the Lamborghini Revuelto’s cold start doesn't just make noise—it creates an atmospheric shift. This is the <i>Safar Nama</i>: a 550km pilgrimage across the golden heart of Rajasthan in the world’s first V12 High Performance Electrified Vehicle (HPEV).
    </p>

    <div class="pull-quote">
        "There is something poetic about 1,001 Italian horses galloping toward a medieval sandstone fortress."
    </div>

    <h2>Beyond the Aravallis</h2>
    <p>
      As we left the chaotic outskirts of Jaipur, the Revuelto’s 'Città' (City) mode—running purely on electricity—felt eerily respectful to the waking villages. But as the Aravalli range thinned out and the NH11 opened its arms toward Nagaur, we switched to 'Corsa'. The transition from silent electric gliding to the raw, naturally aspirated scream of the 6.5L V12 is the greatest theater currently available on four wheels.
    </p>

    <div class="journey-box">
      <div class="stat-column">
        <h3>The Machine</h3>
        <ul class="stat-list">
          <li><strong>Heart</strong> 6.5L V12 + 3 Electric Motors</li>
          <li><strong>Output</strong> 1,001 Combined HP</li>
          <li><strong>Top Speed</strong> 350+ km/h</li>
          <li><strong>Architecture</strong> Carbon Monofuselage</li>
        </ul>
      </div>
      <div class="stat-column">
        <h3>The Route</h3>
        <ul class="stat-list">
          <li><strong>Distance</strong> 558 Kilometers</li>
          <li><strong>Terrain</strong> Tarmac, Sand-drifts, Village Bypasses</li>
          <li><strong>Fuel</strong> 99 Octane (and a lot of prayer)</li>
          <li><strong>Checkpoint</strong> The Longewala Turn-off</li>
        </ul>
      </div>
    </div>

    

    <h2>Navigating the Sands</h2>
    <p>
      Driving a low-slung supercar in Rajasthan is an exercise in tactical awareness. The Revuelto’s nose-lift system became our most used feature through the speed-breakers of rural towns. However, once on the Jodhpur-Jaisalmer stretch, the road becomes a black ribbon slicing through infinite yellow. Here, the Revuelto isn't a car; it’s a low-flying jet. The downforce generated by the active aero keeps the car sucked to the tarmac even as the desert crosswinds try to push you off course.
    </p>

    <h2>The Golden Hour</h2>
    <p>
      We reached Jaisalmer as the sun began its descent. The sandstone walls of the Sonar Quila (The Golden Fort) glowed in a hue that almost matched our 'Giallo Auge' paintwork. In Jaisalmer, time usually stands still, but for a brief moment, the futuristic silhouette of the Revuelto felt like a time-traveler that had finally found its destination.
    </p>

    <h2>The Verdict</h2>
    <p>
      The <i>Safar Nama</i> proved one thing: The Revuelto isn't just a track weapon for the Nürburgring. It is a grand tourer for the bold. It handled the heat, the dust, and the unpredictability of Indian highways with a level of sophistication we didn't expect from a 1,000hp monster. 
    </p>

    <p style="font-style: italic; color: #666; margin-top: 40px;">
      In the desert, every drive is a story. This one was a symphony.
    </p>
  </article>
</div>

<div class="av" data-p="safari">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">JOURNEYS // TATA SAFARI</span>
  </div>
  <header>
    <h1>The King’s Redemption: Why the Safari Leads the Segment</h1>
    <p>A Deep Dive into the Soul of India's Flagship SUV</p>
  </header>

  <article>
    <p>
      In the hyper-competitive D-segment SUV market, specs often dictate the narrative. We talk about torque figures, screen sizes, and ADAS levels. But the Tata Safari exists in a space where logic often bows to emotion. It isn’t just a car; it is a statement of intent.
    </p>

    <h2>The OMEGARC Foundation</h2>
    <p>
      The secret to the Safari’s dominance isn’t found in its brochure, but in its bones. Derived from Land Rover’s D8 platform, the OMEGARC architecture gives the Safari a high-speed stability that its rivals struggle to match. When you are cruising at triple-digit speeds on the Samruddhi Mahamarg, the Safari feels "heavy" in the best way possible—planted, secure, and unshakeable.
    </p>

    <div class="comparison-box">
      <div class="comp-column pros">
        <h3>THE STRENGTHS</h3>
        <ul class="comp-list">
          <li>Unmatched Road Presence: Command higher than almost anything under 40 lakhs.</li>
          <li>Land Rover DNA: Exceptional high-speed stability and rugged OMEGARC chassis.</li>
          <li>Ride Quality: Glides over broken Indian roads with a sophisticated "big car" feel.</li>
          <li>Safety: A fortress on wheels with a consistent 5-star GNCAP pedigree.</li>
          <li>Captain Seat Comfort: The 6-seater version offers a genuine "boss-mode" experience.</li>
        </ul>
      </div>
      <div class="comp-column cons">
        <h3>THE COMPROMISES</h3>
        <ul class="comp-list">
          <li>No AWD/4x4: Despite the heritage, it remains a front-wheel-drive urban cruiser.</li>
          <li>Infotainment Gremlins: Software responsiveness still lags behind the hardware's beauty.</li>
          <li>Engine Noise: The Kryotec 2.0 diesel is vocal under heavy acceleration.</li>
          <li>Service Consistency: Tata’s after-sales experience remains a hit-or-miss affair.</li>
          <li>Ergonomic Quirks: Minor issues like the placement of the dead pedal.</li>
        </ul>
      </div>
    </div>

    <h2>Presence as a Priority</h2>
    <p>
      While the XUV700 leans into tech and the Scorpio-N leans into old-school ruggedness, the Safari balances both with a massive dose of "presence." It is a car you buy for the way it makes you feel when you park it and look back. The recent facelifts have elevated the interior from "good for Tata" to "genuinely premium," utilizing materials that wouldn't feel out of place in an entry-level German luxury car.
    </p>

    <h2>The Verdict after 10,000 KM</h2>
    <p>
      After the honeymoon period fades and the first 10,000 kilometers are behind you, the Safari reveals its true character. It is not a perfect machine. It has its software glitches and the diesel engine can be loud. But its ability to swallow miles, protect your family in a 5-star safety cocoon, and command respect on the road makes it the definitive choice for the Indian enthusiast.
    </p>

    <p>
      Ultimately, the Safari name matters because it represents an aspirational journey. In a segment of commuters, the Safari remains a traveler.
    </p>
  </article>
</div>

<div class="av" data-p="soul">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">JOURNEYS // CULTURE</span>
  </div>
  <header>
    <h1>When Cars Had Soul: The Era of Mechanical Purity</h1>
    <p>Beyond the Algorithms — A Tribute to Driver Connection</p>
  </header>

  <article>
    <p>
      There was a time when driving was a conversation, not a command. You didn't just "operate" a vehicle; you negotiated with it. Before the era of drive-by-wire and predictive algorithms, cars were extensions of the driver’s nervous system. Today, we sit in digital cocoons where every input is filtered, smoothed, and sanitized by a silicon brain.
    </p>

    <h2>The Mechanical Dialogue</h2>
    <p>
      In an analog car, the "soul" wasn't a marketing buzzword—it was physical. It was the vibration of the engine traveling through the steering column, telling you exactly how much grip the front tires had left. It was the smell of fuel and warm oil, and the precise, metallic "clack" of a gated shifter. These cars didn't have "driving modes"; they had character, and they demanded your undivided attention.
    </p>

    <h2>The Rise of the Rolling Computer</h2>
    <p>
      Modern cars are objectively better in every measurable metric. They are faster, safer, and more efficient. But in the pursuit of perfection, we've lost the "imperfections" that made driving memorable. Electronic Stability Control (ESC) and Torque Vectoring can make a novice driver look like a hero, but they also act as a veil, hiding the raw physics of the machine from the person behind the wheel.
    </p>

    <div class="comparison-box">
      <div class="comp-column pros">
        <h3>THE ANALOG "SOUL"</h3>
        <ul class="comp-list">
          <li><strong>Tactile Feedback:</strong> Hydraulic steering and mechanical linkages provide a direct connection to the road.</li>
          <li><strong>Simplicity:</strong> Fewer electronic components mean mechanical issues can often be diagnosed by ear or touch.</li>
          <li><strong>Timelessness:</strong> Analog gauges and physical buttons don't "date" or lag like old tablet screens.</li>
          <li><strong>Skill Reward:</strong> Without electronic aids, every perfect corner is a result of the driver's own talent.</li>
          <li><strong>Repairability:</strong> Built with metal and bolts, these machines were designed to be fixed, not just replaced.</li>
        </ul>
      </div>
      <div class="comp-column cons">
        <h3>THE DIGITAL REALITY</h3>
        <ul class="comp-list">
          <li><strong>Complexity:</strong> Proprietary software makes DIY maintenance nearly impossible for the average owner.</li>
          <li><strong>Muted Senses:</strong> Electronic power steering (EPS) often feels "dead" or artificial compared to hydraulic setups.</li>
          <li><strong>Disposable Tech:</strong> Once an ECU or a main infotainment screen fails out of warranty, repair costs can total the car.</li>
          <li><strong>Input Lag:</strong> Soft-touch buttons and touchscreens require looking away from the road, unlike physical knobs.</li>
          <li><strong>Planned Obsolescence:</strong> Modern cars are built to be "smart" gadgets that eventually lose software support.</li>
        </ul>
      </div>
    </div>

    <h2>The Purist's Rebellion</h2>
    <p>
      We are seeing a global resurgence in "analog" appreciation. Enthusiasts are flocking back to 90s icons and mechanical restomods because they miss the ceremony of driving. Even luxury brands like Ferrari are experimenting with "stripping away" digital clutter in special editions to bring back that tactile relationship between human and machine.
    </p>

    <h2>The Verdict</h2>
    <p>
      A car with a "soul" is one that allows for human error and rewards human excellence. While we cannot go back to a world without safety nets and efficiency, we must ask ourselves: are we still driving, or are we just passengers in a very fast computer? The thrill of the drive isn't found in a 12-inch screen; it’s found in the feedback from the steering wheel and the roar of a machine that breathes.
    </p>
  </article>
</div>

<div class="av" data-p="suv">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">NEWS // SUV CULTURE</span>
  </div>
  <header>
    <h1>The High Seating Revolution: India’s SUV Obsession Decoded</h1>
    <p>Beyond Ground Clearance — A Sociological Drive</p>
  </header>

  <article>
    <p>
      Look at any busy intersection in Mumbai, Delhi, or Bangalore, and the landscape is undeniable. The humble hatchback and the elegant sedan are being crowded out by high-bonneted, aggressive-looking machines. In 2024, SUVs accounted for nearly 50% of all passenger vehicle sales in India. This isn't just a trend; it's a structural shift in the Indian psyche.
    </p>

    <h2>The Psychology of the "Commanding Position"</h2>
    <p>
      In a country where traffic is chaotic and road rules are often suggestions, the SUV offers something a sedan cannot: a sense of dominance. Sitting higher allows drivers to see over the roof of the car in front, anticipate potholes, and feel psychologically "safer" in the urban jungle. For the Indian car buyer, an SUV isn't just transport; it's a shield.
    </p>

    <h2>Infrastructure vs. Aspiration</h2>
    <p>
      The primary technical justification for SUVs is India’s infrastructure. Despite the massive progress in highway construction, the "last mile" to an Indian home or a weekend getaway often involves unscientific speed breakers and water-logged craters. The peace of mind that comes with 190mm+ of ground clearance is a luxury that becomes a necessity.
    </p>

    <div class="comparison-box">
      <div class="comp-column pros">
        <h3>THE SUV ADVANTAGE</h3>
        <ul class="comp-list">
          <li><strong>Pothole Immunity:</strong> High ground clearance makes light work of monsoon-ravaged roads.</li>
          <li><strong>Road Presence:</strong> Bold styling and "muscle" command respect in tight traffic merging.</li>
          <li><strong>Ingress/Egress:</strong> Higher seats are far easier for elderly parents to enter and exit.</li>
          <li><strong>Perceived Safety:</strong> The "big car" feel provides a sense of security for the family.</li>
          <li><strong>Resale Value:</strong> Currently, SUVs hold their value significantly better than sedans in India.</li>
        </ul>
      </div>
      <div class="comp-column cons">
        <h3>THE HIDDEN COSTS</h3>
        <ul class="comp-list">
          <li><strong>Body Roll:</strong> A higher center of gravity means more swaying in corners compared to sedans.</li>
          <li><strong>Fuel Efficiency:</strong> Heavier weight and poor aerodynamics lead to lower mileage.</li>
          <li><strong>Parking Woes:</strong> Massive footprints make navigating tight city lanes and basements a chore.</li>
          <li><strong>The "Feature" Premium:</strong> You often pay more for an SUV than a better-equipped sedan of the same price.</li>
          <li><strong>Environmental Impact:</strong> Larger engines and more raw materials contribute to a higher carbon footprint.</li>
        </ul>
      </div>
    </div>

    <h2>The Death of the Three-Box Sedan?</h2>
    <p>
      As crossovers like the Creta and full-sized beasts like the Safari take over, the sedan is becoming a niche choice for the "purist." The Indian buyer has realized that while a sedan handles better on a track, an SUV handles *India* better. We are trading cornering speeds for the ability to climb a pavement when a road is blocked.
    </p>

    <h2>The Verdict</h2>
    <p>
      The obsession with SUVs in India is a mix of practical necessity and social status. It represents a nation that wants to go anywhere, sit above the chaos, and look good doing it. While the purist may mourn the loss of low-slung driving dynamics, the Indian family has spoken: they want to be high up, looking down at the road ahead.
    </p>
  </article>
</div>

<div class="av" data-p="v8">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">NEWS // INSIGHTS</span>
  </div>
  <header>
    <h1>The Last Roar: Is the V8 Engine Entering its Final Act?</h1>
    <p>Mechanical Soul in an Age of Silicon and Electricity</p>
  </header>

  <article>
    <p>
      There is a specific frequency—a low-pitched, rhythmic thrum—that defines the V8 engine. It is a sound that bypasses the ears and settles directly in the chest. For over a century, the V8 has been the heartbeat of the automotive world, powering everything from blue-collar muscle cars to the most exclusive European exotics. 
    </p>

    <p>
      But as we cross into the mid-2020s, the mechanical symphony is being met with a wall of silence. Tightening emission norms, the relentless march of electrification, and the efficiency of downsized turbocharged engines have put a target on the back of the eight-cylinder block.
    </p>

    <h2>The Hybrid Lifeline</h2>
    <p>
      The V8 isn't going down without a fight; it is simply evolving. We are seeing a new era of "Electrified Performance." Manufacturers like Lamborghini and Mercedes-AMG are no longer viewing the electric motor as a replacement, but as a forced-induction partner. By pairing a smaller high-revving V8 with high-output batteries, brands are achieving power figures that were once reserved for hypercars, all while keeping the soul of the engine alive for one more generation.
    </p>

    <div class="status-box">
      <div class="status-column survival">
        <h3>The Survival Strategy</h3>
        <ul class="status-list">
          <li><strong>Hybrid Integration</strong> Using 48V systems and PHEV tech to offset cold-start emissions.</li>
          <li><strong>Synthetic Fuels</strong> Porsche and Ferrari’s bet on e-fuels to keep internal combustion legal.</li>
          <li><strong>Ultra-Luxury Niche</strong> Transitioning from a mass-market option to a "high-jewelry" collectible.</li>
        </ul>
      </div>
      <div class="status-column threat">
        <h3>The Mounting Pressures</h3>
        <ul class="status-list">
          <li><strong>Euro 7 Standards</strong> The strictest hurdles yet for large displacement engines.</li>
          <li><strong>EV Efficiency</strong> The inability to match the instant, silent torque of quad-motor setups.</li>
          <li><strong>Corporate Image</strong> The shift in ESG goals making the V8 a difficult boardroom sell.</li>
        </ul>
      </div>
    </div>

    <h2>A Shift in Value: From Tool to Totem</h2>
    <p>
      As the V8 becomes rarer, its value is shifting. It is moving away from being a "performance tool" and becoming a "mechanical totem." Much like a mechanical Swiss watch in an era of smartwatches, the V8 is being appreciated for its complexity, its character, and its flaws. 
    </p>

    <p>
      In India, where the V8 was always a rare beast due to taxation and fuel costs, the upcoming years represent the last chance for enthusiasts to own a piece of this history. From the growl of a Mustang to the sophisticated snarl of a German twin-turbo, these engines are becoming heirloom assets.
    </p>

    <h2>The Verdict</h2>
    <p>
      The V8 engine will eventually go silent, but that day is not today. While the displacement might shrink and the turbochargers might grow, the eight-cylinder configuration remains the ultimate expression of automotive theater. We are currently living through the "Golden Sunset" of internal combustion—a time to celebrate the noise before the quiet takes over.
    </p>

    <p style="font-style: italic; color: #666;">
      At DRIVAYAN, we believe that even if the future is electric, the stories we tell will always be fueled by the roar of the past.
    </p>
  </article>
</div>

<div class="av" data-p="modify">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">JOURNEYS // LEGALITY</span>
  </div>
  <header>
<h1>Why Modifications Should Not Be Illegal in India</h1>
<p>GEAR & GUPSHUP — DRIVAYAN</p>
</header>

<article>

<p>
In India today, modifying your own car can legally turn you into a criminal. Change the exhaust note, upgrade suspension, wrap the body, alter wheels — and you risk challans, registration cancellation, even vehicle seizure. The Motor Vehicles Act, particularly after amendments in 2019, tightened interpretation around “alteration,” and enforcement often treats personalization as illegality.
</p>

<p>
But here’s the uncomfortable question: are we criminalizing creativity instead of regulating irresponsibility?
</p>

<h2>The Law vs The Spirit of Enthusiasm</h2>

<p>
Section 52 of the Motor Vehicles Act restricts structural alterations that deviate from manufacturer specifications. On paper, the intent is safety and emission compliance. That is understandable. India struggles with pollution, unsafe roads, and unregulated garages.
</p>

<p>
However, blanket restriction is not regulation. It is suppression.
</p>

<p>
Across the world — Germany, Japan, USA, Australia — car modification is not illegal. It is regulated. TÜV certification in Germany ensures modified vehicles meet engineering standards. In Japan, Shaken inspection validates safety compliance. In the US, aftermarket industries operate under emission and federal compliance norms.
</p>

<p>
India, instead of building a certification ecosystem, chose prohibition.
</p>

<h2>The Economic Argument India Is Ignoring</h2>

<p>
Automotive modification is not just “loud exhausts.” It is an industry.
</p>

<p>
Performance tuning, suspension upgrades, brake kits, detailing, restoration, body kits, wrap studios, ECU calibration — globally this is a multi-billion-dollar ecosystem generating skilled employment, fabrication expertise, and motorsport innovation.
</p>

<p>
In India, this ecosystem exists — but underground.
</p>

<p>
When you ban regulated modification, you don’t eliminate it. You push it into unregulated grey markets. That’s when unsafe welding, low-quality parts, and improper installations become real dangers.
</p>

<p>
Legal regulation would:
• Generate GST revenue  
• Create certified workshops  
• Encourage engineering standards  
• Reduce unsafe backyard jobs  
• Build motorsport culture  
</p>

<h2>Safety: The Real Concern</h2>

<p>
Let’s be honest. Not all modifications are responsible. Lift kits without geometry correction. Exhaust systems exceeding noise norms. Poorly installed HID kits blinding traffic. These are problems.
</p>

<p>
But the solution is not prohibition.
</p>

<div class="comparison-box">
<div class="comp-column pros">
<h3>REGULATED MODIFICATION</h3>
<ul class="comp-list">
<li><strong>Certification:</strong> Government-approved inspection ensures safety compliance.</li>
<li><strong>Standardized Emission Limits:</strong> ECU tuning validated within Bharat Stage norms.</li>
<li><strong>Professional Workshops:</strong> Skilled technicians with engineering accountability.</li>
<li><strong>Insurance Clarity:</strong> Transparent declaration and risk assessment.</li>
<li><strong>Economic Growth:</strong> Organized aftermarket industry.</li>
</ul>
</div>

<div class="comp-column cons">
<h3>BLANKET BAN APPROACH</h3>
<ul class="comp-list">
<li><strong>Underground Market:</strong> No quality control.</li>
<li><strong>Harassment Risk:</strong> Selective enforcement by authorities.</li>
<li><strong>Innovation Stagnation:</strong> Motorsport and engineering culture suffers.</li>
<li><strong>Lost Revenue:</strong> No taxation from regulated aftermarket.</li>
<li><strong>Fear Culture:</strong> Enthusiasts treated as offenders.</li>
</ul>
</div>
</div>

<h2>Identity, Not Illegality</h2>

<p>
Cars are not appliances. In India, they represent aspiration, identity, personality. A modified car is often an expression of craftsmanship, not recklessness.
</p>

<p>
When a young engineer tunes suspension geometry, calibrates camber angles, upgrades braking systems — that is applied engineering. That is skill development.
</p>

<p>
By making it illegal, we discourage technical curiosity.
</p>

<h2>The Global Motorsport Link</h2>

<p>
Every major automotive culture — Japan’s JDM scene, Germany’s Autobahn tuners, America’s muscle heritage — evolved because modification was allowed within legal frameworks.
</p>

<p>
India dreams of global motorsport presence. But how do you build a racing culture if grassroots customization is criminalized?
</p>

<p>
Innovation does not begin in boardrooms. It begins in garages.
</p>

<h2>What India Actually Needs</h2>

<p>
Instead of bans, India needs:
</p>

<p>
• Certified modification guidelines  
• Decibel and emission testing infrastructure  
• Structural modification inspection framework  
• Aftermarket homologation process  
• Motorsport-friendly regulatory lanes  
</p>

<p>
Regulation brings responsibility. Prohibition breeds evasion.
</p>

<h2>The Verdict — GEAR & GUPSHUP</h2>

<p>
Modifications should not be illegal in India.
</p>

<p>
Irresponsible, unsafe, emission-violating modifications should be illegal.
</p>

<p>
There is a difference.
</p>

<p>
A progressive automotive nation regulates passion — it doesn’t suppress it.
</p>

<p>
If India wants to build a mature car culture, it must shift from fear-based enforcement to engineering-based certification.
</p>

<p>
Because the future of Indian automotive enthusiasm depends on one fundamental question:
</p>

<p>
Do we treat enthusiasts as criminals — or as contributors to innovation?
</p>

</article>
</div>

<div class="av" data-p="manifesto">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">ABOUT // MANIFESTO</span>
  </div>
  <header>
    <p>The Opening Note</p>
    <h1>Introducing DRIVAYAN: Mechanical Precision, Cinematic Soul.</h1>
  </header>

  <article>
    <p>
      <span class="dropcap">W</span>elcome to the vanguard of automotive storytelling. In a world increasingly cluttered by fast-paced reviews and spec-sheet comparisons, <strong>DRIVAYAN</strong> was born from a singular, quiet realization: Cars are not just machines. They are the milestones of our personal journeys, the artifacts of our engineering ambition, and the vessels of our freedom.
    </p>

    <p>
      DRIVAYAN is more than an automotive platform; it is a digital sanctuary for the purist. We believe that the sound of a cold-start at 4:00 AM in the Himalayas tells a more profound story than any 0-100 km/h statistic ever could. We are here to decode Indian car culture, one drive at a time.
    </p>

    <div class="feature-block">
      <span>Volume I</span>
      <h3>Safar Nama: The Travelogues of the Soul</h3>
      <p style="margin-bottom:0;">
        "Safar Nama" is our cinematic lens on the road. It isn't about reaching a destination; it is about the poetry of the transit. Through Safar Nama, we document the rhythm of the Indian landscape—from the salt-crusted horizons of the Rann of Kutch to the oxygen-thin passes of Spiti. These are long-form narratives where the car is a character, and the road is the dialogue. It is automotive journalism, slowed down and rendered with mechanical reverence.
      </p>
    </div>

    <h2>Beyond the Commute</h2>
    <p>
      Why do we drive? For some, it is a necessity of the commute. For us, it is a rebellion. The Indian automotive landscape is shifting; we are moving toward a future of screens and sensors. While we embrace the new, DRIVAYAN exists to ensure that we don't forget the tactile "clack" of a gated manual or the hydraulic feedback of a steering wheel that fights back. We document the transition—celebrating the icons of the past while scrutinizing the innovators of the future.
    </p>

    <div class="feature-block">
      <span>Volume II</span>
      <h3>Gear & Gupshup: The Enthusiast's Roundtable</h3>
      <p style="margin-bottom:0;">
        If Safar Nama is the poetry, "Gear & Gupshup" is the prose. This is where the mechanical precision comes in. From deep-dives into restoration philosophy to the legal nuances of the modification industry, Gear & Gupshup is the heartbeat of the community. We talk tech, we debate culture, and we share the "Gupshup"—the raw, unfiltered conversations that happen at car meets and roadside dhabas. It is where engineering meets emotion.
      </p>
    </div>

    <h2>The Pillars of Our Manifesto</h2>
    <div class="manifesto-grid">
      <div class="grid-item">
        <h4>Cinematic Truth</h4>
        <p>We believe in high-fidelity storytelling. Every image and every word is curated to reflect the raw aesthetic of the machine.</p>
      </div>
      <div class="grid-item">
        <h4>Mechanical Honor</h4>
        <p>We respect the engineers. We look past the marketing fluff to see the metal, the oil, and the intention behind the design.</p>
      </div>
      <div class="grid-item">
        <h4>The Human Factor</h4>
        <p>A car is nothing without its driver. We focus on the bond between man and machine—the stories that make ownership meaningful.</p>
      </div>
    </div>

    <h2>The Road Ahead</h2>
    <p>
      As you navigate through DRIVAYAN, you will find a blend of high-end photography, analytical insights, and raw travelogues. We invite you to stay a while, to look past the screens, and to listen to the engine. Whether you are here for the technical breakdown of a V8 or the moonlit miles of a desert crossing, you are among those who understand.
    </p>

    <p style="font-style: italic; color: #fff; border-top: 1px solid rgba(255,255,255,0.1); padding-top: 40px;">
      Welcome to the journey. Welcome to DRIVAYAN.
    </p>
  </article>
</div>

<div class="av" data-p="manual">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">GEAR & GUPSHUP // GUPSHUP</span>
  </div>
  <header>
    <p>Gear & Gupshup Roundtable</p>
    <h1>Is the Manual Dead? The Third Pedal’s Last Stand.</h1>
  </header>

  <div class="content-wrapper">
    <article>
      <p>
        The obituary for the manual transmission has been written a thousand times over. In an era where Dual-Clutch Transmissions (DCTs) shift in milliseconds and EVs eliminate the need for gears entirely, the stick-shift seems like a mechanical anachronism—a record player in a world of lossless streaming. 
      </p>

      <p>
        But at <i>DRIVAYAN</i>, we’ve noticed something curious. As the manual becomes rarer, its value—both emotional and financial—is skyrocketing. From the Indian enthusiast hunting for an old Zen Carbon to global collectors paying premiums for manual Porsche 911s, the "dead" technology is showing a remarkable pulse.
      </p>

      <h2>The Efficiency Paradox</h2>
      <p>
        Let’s address the elephant in the room: <strong>The manual is objectively worse at going fast.</strong> No human, regardless of how many "Heel-and-Toe" videos they've watched, can shift faster than a modern ZF-8 speed or a Porsche PDK. The computer-controlled transmission knows the perfect torque curve, manages heat better, and provides superior fuel economy. 
      </p>
      <p>
        However, the goal of an enthusiast car isn't efficiency; it's <i>engagement</i>. When you remove the clutch, you remove a layer of the conversation between the car and the driver. An automatic car is a monologue; a manual car is a debate.
      </p>

      <div class="comparison-box">
        <div class="comp-column pros">
          <h3>THE PURIST PLEA</h3>
          <ul class="comp-list">
            <li><strong>Total Control:</strong> You decide when to hold a gear, regardless of what the "Eco" algorithm wants.</li>
            <li><strong>Weight Savings:</strong> Traditional manuals are significantly lighter than complex torque converters.</li>
            <li><strong>Anti-Theft:</strong> In many modern urban centers, the stick-shift has become a natural deterrent.</li>
            <li><strong>The "Click":</strong> The sensory reward of a mechanical linkage slotting into place is irreplaceable.</li>
          </ul>
        </div>
        <div class="comp-column cons">
          <h3>THE AUTOMATIC TRUTH</h3>
          <ul class="comp-list">
            <li><strong>Precision:</strong> Lightning-fast shifts keep the turbo on boost, maximizing acceleration.</li>
            <li><strong>Versatility:</strong> Seamlessly transitions from a track-monster to a bumper-to-bumper city commuter.</li>
            <li><strong>Safety:</strong> Modern ADAS systems often require automatic gearboxes to function correctly.</li>
            <li><strong>Consistency:</strong> Zero risk of a "money-shift" (accidental downshift that overrevs the engine).</li>
          </ul>
        </div>
      </div>

      <h2>The Indian Context: Bumper-to-Bumper Fatigue</h2>
      <p>
        In India, the debate is complicated by our infrastructure. The romance of a manual gearbox evaporates quickly when you are stuck on the Western Express Highway for two hours. This reality has led to the rise of AMTs (Automated Manual Transmissions)—a compromise that gives the ease of an automatic with the cost of a manual. 
      </p>
      <p>
        Yet, even in India, we see a "Weekend Purist" culture emerging. Enthusiasts are keeping an automatic SUV for the weekday grind and a manual hatchback or sedan for the early Sunday morning runs. It’s not about necessity; it’s about the <i>ceremony</i>.
      </p>

      <h2>The Final Verdict</h2>
      <p>
        Is the manual dead? In the mainstream market, yes. It is becoming a niche, high-cost option. But as we move toward a future of autonomous pods and silent motors, the manual transmission is transitioning from a "utility" to an "instrument." You don't play a piano because it’s the most efficient way to generate sound; you play it because of how it makes you feel. The third pedal isn't just a gear selector; it’s the heartbeat of the DRIVAYAN philosophy.
      </p>
    </article>

    <aside class="side-image-container">
      <img src="https://images.unsplash.com/photo-1544636331-e26879cd4d9b?auto=format&fit=crop&q=80&w=800" alt="Manual Gear Shifter">
      <p class="image-caption">The Gated Shifter: A Mechanical Symphony.</p>
    </aside>
  </div>
</div>

<div class="av" data-p="watches">
  <div class="av-bar">
    <button class="av-back" onclick="closeAV()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
      BACK
    </button>
    <span class="av-crumb">GEAR & GUPSHUP // LIFESTYLE</span>
  </div>
  <header>
    <p>Gear & Gupshup</p>
    <h1>Chronographs & Camshafts: A Tale of Two Ticking Hearts.</h1>
  </header>

  <div class="content-wrapper">
    <article>
      <p>
        There is a reason why the dashboard of a classic Bugatti or a Pagani looks more like a jeweler's display case than a cockpit. Since the dawn of the internal combustion engine, the worlds of horology and automotive engineering have been locked in a symbiotic embrace. Both are obsessed with the same core pursuit: the mastery of <i>Time</i> and <i>Motion</i>.
      </p>

      <p>
        For the enthusiast, a mechanical watch is not just a tool to tell time, and a classic car is not just a tool for transport. They are both miniature cathedrals of kinetic energy, where hundreds of tiny parts—gears, springs, escapements, and valves—must work in absolute harmony to create a soul.
      </p>

      <div class="editorial-quote">
        "One is a machine you inhabit to move through space; the other is a machine you wear to track your existence within it."
      </div>

      <h2>The Shared DNA of Precision</h2>
      <p>
        In the 1960s, this obsession reached its fever pitch. This was the era of the "Racing Chronograph." Drivers like Jacky Ickx and Jo Siffert didn't just wear watches as accessories; they were vital instruments. Before digital telemetry, a driver used the tachymeter scale on their bezel to calculate average speed over a measured mile. 
      </p>
      <p>
        The vibration of a flat-six engine at 7,000 RPM is a violent environment for a delicate balance wheel. This led to engineering breakthroughs that benefited both industries—shock protection, anti-magnetic alloys, and water-resistance were pioneered on the racetrack and refined on the wrist.
      </p>

      <div class="comparison-box">
        <div class="comp-column pros">
          <h3>THE HOROLOGICAL SOUL</h3>
          <ul class="comp-list">
            <li><strong>The Mainspring:</strong> The fuel tank of the watch, storing potential energy.</li>
            <li><strong>The Escapement:</strong> The 'valvetrain' that releases energy in precise intervals.</li>
            <li><strong>Complications:</strong> The 'turbos' of horology—features beyond simple timekeeping.</li>
            <li><strong>Manual Winding:</strong> The tactile equivalent of a gated manual gear shift.</li>
          </ul>
        </div>
        <div class="comp-column cons">
          <h3>THE AUTOMOTIVE SOUL</h3>
          <ul class="comp-list">
            <li><strong>The Crankshaft:</strong> The heart that dictates the rhythm of the machine.</li>
            <li><strong>The Camshaft:</strong> The 'brain' ensuring every breath is perfectly timed.</li>
            <li><strong>Naturally Aspirated:</strong> The pure, unadulterated delivery of power.</li>
            <li><strong>Mechanical Linkage:</strong> A direct physical connection between man and machine.</li>
          </ul>
        </div>
      </div>

      <h2>Icons of the Asphalt and the Wrist</h2>
      <p>
        The connections are legendary. The <strong>TAG Heuer Monaco</strong> became an icon not just for its square case, but because Steve McQueen wore it in <i>Le Mans</i>. The <strong>Rolex Daytona</strong> is forever tied to the "Cool Hand" himself, Paul Newman. Even in the modern era, the partnership between <strong>Richard Mille and McLaren</strong> or <strong>Breitling and Bentley</strong> proves that the obsession hasn't faded; it has simply evolved into higher-tech materials like forged carbon and titanium.
      </p>

      <h2>The Indian Perspective: The Collector's Circle</h2>
      <p>
        In India, we are seeing a resurgence of this appreciation. From the streets of Mumbai to the car meets in Delhi, the "Gear & Gupshup" at any enthusiast gathering inevitably shifts from the specs of a vintage Mercedes to the patina on a 1970s Seiko Bullhead. It is a shared language. To understand one is to respect the other.
      </p>

      <h2>The Final Verdict</h2>
      <p>
        In a digital world dominated by smartwatches and autonomous EVs, the chronograph and the camshaft represent a rebellion. They are proof that we still value craftsmanship that we can touch, hear, and feel. A ticking watch and a roaring engine are reminders that life is lived in the intervals between the beats.
      </p>
    </article>

    <aside class="side-image-container">
      <img src="https://images.unsplash.com/photo-1519641471654-76ce0107ad1b?auto=format&fit=crop&q=80&w=800" alt="Vintage Chronograph and Car Key">
      <p class="image-caption">Precision personified: When 28,800 BPH meets 8,000 RPM.</p>
    </aside>
  </div>
</div>

<!-- CART DRAWER -->
<div class="cart-drawer" id="cartDrawer">
  <div class="cart-header">
    <h3>// GARAGE BAG <span id="cartItemCount" style="color:var(--gold);">(0)</span></h3>
    <button class="cart-close" onclick="closeCart()">✕</button>
  </div>
  <div class="cart-body" id="cartBody">
    <div class="cart-empty">
      <div class="cart-empty-icon">◈</div>
      <p>Your garage bag is empty.<br>Add some fuel to your style.</p>
    </div>
  </div>
  <div class="cart-footer" id="cartFooter" style="display:none;">
    <div class="cart-total">
      <span class="cart-total-label">// TOTAL</span>
      <span class="cart-total-amount" id="cartTotal">₹0</span>
    </div>
    <button class="checkout-btn" onclick="checkout()">PROCEED TO CHECKOUT →</button>
    <p style="font-family:'JetBrains Mono',monospace;font-size:8px;color:var(--muted);text-align:center;margin-top:12px;letter-spacing:1px;">// FREE SHIPPING ABOVE ₹1,999</p>
  </div>
</div>
<!-- PRODUCT MODAL -->
<div class="modal-bg" id="modalBg" onclick="closeModal()"></div>
<div class="product-modal" id="productModal">
  <button class="modal-close" onclick="closeModal()">✕</button>
  <div class="modal-inner">
    <div class="modal-img"><img id="modalImg" src="" alt=""></div>
    <div class="modal-details" id="modalDetails"></div>
  </div>
</div>

<!-- shop JS consolidated into final script block below -->

<!-- ===== LOGIN OVERLAY ===== -->
<div class="login-overlay" id="loginOverlay">
  <div class="login-card">
    <div class="close-login" id="closeLogin">CLOSE [X]</div>
    <span class="label">Member Access</span>
    <h2>Enter the Archive</h2>
    <input type="email" class="login-field" placeholder="EMAIL ADDRESS">
    <input type="password" class="login-field" placeholder="PASSWORD">
    <button class="login-btn">SIGN IN</button>
  </div>
</div>

<!-- ===== FOOTER ===== -->
<footer>
  <section class="reviews-section">
    <div class="review-form reveal">
      <span class="label">// SUBMIT VERDICT</span>
      <h2 style="margin:20px 0;">Share Your Experience</h2>
      <div class="rating-selector" id="starRating">
        <span class="star" data-value="1">★</span>
        <span class="star" data-value="2">★</span>
        <span class="star" data-value="3">★</span>
        <span class="star" data-value="4">★</span>
        <span class="star" data-value="5">★</span>
      </div>
      <input type="text" id="reviewTitle" class="review-input" placeholder="REVIEW TITLE (e.g. Mechanical Perfection)">
      <textarea id="reviewText" class="review-input" placeholder="DETAILED ANALYSIS..." rows="4"></textarea>
      <div style="display:flex;gap:20px;">
        <input type="text" id="driverName" class="review-input" placeholder="DRIVER NAME">
        <button onclick="submitReview()" class="cta">LOG VERDICT</button>
      </div>
    </div>
    <div id="reviewsContainer"></div>
  </section>


    <!-- Ad Slot 3: Footer Responsive -->
    <div class="ad-slot-wrap" style="margin-bottom:50px;border:1px solid var(--border);">
      <span class="ad-slot-label" style="right:20px;">// SPONSORED</span>
      <ins class="adsbygoogle"
           style="display:block;"
           data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
           data-ad-slot="3333333333"
           data-ad-format="auto"
           data-full-width-responsive="true"></ins>
      <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
    </div>

  <a href="#hero" class="brand">DRIVAYAN</a>
  <div style="margin:40px 0;display:flex;justify-content:center;gap:30px;flex-wrap:wrap;">
    <a href="https://www.instagram.com/drivayan" class="label" style="margin:0">Instagram</a>
    <a href="https://www.facebook.com/Drivayan"  class="label" style="margin:0">Facebook</a>
    <a href="https://www.youtube.com/@drivayan"  class="label" style="margin:0">YouTube</a>
    <a href="#shop" onclick="showView('shop')" class="label" style="margin:0;color:var(--gold);">Garage Shop</a>
    <a href="javascript:void(0)" class="label" id="openLogin" style="margin:0;color:var(--text);">Login</a>
    <a href="#" class="label" style="margin:0">Privacy</a>
  </div>
  <div style="font-size:10px;color:var(--muted);letter-spacing:2px;opacity:0.6;">© 2026 DRIVAYAN STUDIO.</div>
</footer>

<script>
// ===== CAR REGISTRY =====
const carRegistry = [
  {
    name:"Mahindra XEV 9e", tag:"EV / FLAGSHIP",
    desc:"The triple-screen electric powerhouse with Cineluxe interior.",
    status:"BOOKINGS OPEN", link:"#",
    img:"XUV-9E.jpeg?q=80&w=600"
  },
  {
    name:"New Renault Duster", tag:"SUV / HYBRID",
    desc:"The return of the king. 4x4 capabilities with a refined hybrid heart.",
    status:"T-MINUS 15 DAYS", link:"#",
    img:"REANUALT-DUSTER.jpeg?q=80&w=600"
  },
  {
    name:"Skoda Kushaq L&K", tag:"LUXURY / TURBO",
    desc:"Refined European dynamics with the top-tier Laurin & Klement trim.",
    status:"JUST LAUNCHED", link:"#",
    img:"SKODA-KUSHAQ.jpeg?q=80&w=600"
  }
];

function renderCarGrid() {
  const container = document.getElementById('dynamic-car-grid');
  if (!container) return;
  container.innerHTML = carRegistry.map(car => `
    <a href="${car.link}" class="car-card">
      <div class="img-box">
        <img src="${car.img}" alt="${car.name}" loading="lazy">
      </div>
      <div class="car-info">
        <div class="car-meta">
          <span>${car.tag}</span>
          <span style="color:var(--text)">${car.status}</span>
        </div>
        <h3 style="font-family:'Playfair Display';margin-bottom:10px;">${car.name}</h3>
        <p style="font-size:13px;color:var(--muted);line-height:1.4;">${car.desc}</p>
      </div>
    </a>
  `).join('');
}
renderCarGrid();

// ===== NEWS TICKER =====
const newsItems = [
  "Mahindra Thar 5-Door Production version spotted near Jaipur",
  "BMW M-Series to go fully electric by 2028: Leaks suggest hybrid transition",
  "Tata Motors achieves 5-star Bharat NCAP rating for entire SUV lineup",
  "Formula 1: New engine regulations for 2026 Season explained",
  "Vintage Car Rally 2026: 1950s Jaguar takes best in show in Mumbai",
  "Hydrogen-powered heavy vehicles: The future of Indian logistics?",
  "Restoration Focus: Why the Maruti 800 is the next cult classic"
];

(function updateNewsTicker() {
  const ticker = document.getElementById('newsTicker');
  const full = [...newsItems, ...newsItems];
  ticker.innerHTML = full.map(item =>
    `<a href="#news" class="news-item"><span>[WIRE]</span> ${item.toUpperCase()}</a>`
  ).join('');
})();

// ===== LIVE CLOCK =====
setInterval(() => {
  const now = new Date();
  document.getElementById('live-time').innerText =
    `// TIME: ${String(now.getHours()).padStart(2,'0')}:${String(now.getMinutes()).padStart(2,'0')}`;
}, 1000);

// ===== LAUNCH COUNTDOWN =====
(function updateLaunchTimer() {
  const target   = new Date("March 17, 2026 10:00:00").getTime();
  const now      = Date.now();
  const distance = target - now;
  const el       = document.getElementById('duster-date');
  if (el && distance > 0) {
    const days = Math.floor(distance / (1000 * 60 * 60 * 24));
    el.innerHTML = `// T-MINUS: ${days} DAYS TO REVEAL`;
  }
})();

// ===== GSAP ANIMATIONS =====
gsap.registerPlugin(ScrollTrigger);

// Nav entrance
gsap.from(".nav-item", { y:-10, opacity:0, duration:1.2, stagger:0.08, ease:"expo.out", delay:0.3 });

// Hero entrance
gsap.from(".hero-content h1", { opacity:0, y:10, duration:1.5, delay:0.2, ease:"expo.out" });

// Scroll reveals — override the CSS .reveal { opacity:1 } AFTER GSAP takes control
gsap.utils.toArray(".reveal").forEach(el => {
  gsap.fromTo(el,
    { opacity:0, y:25 },
    { opacity:1, y:0, duration:1.2, ease:"power2.out",
      scrollTrigger:{ trigger:el, start:"top 92%" }
    }
  );
});

// Image parallax on scroll
gsap.utils.toArray(".img-container img, .safarnama-img").forEach(img => {
  gsap.from(img, {
    scale:1.15,
    scrollTrigger:{ trigger:img, start:"top 95%", end:"bottom 20%", scrub:1.5 }
  });
});

// Magnetic CTA
document.querySelectorAll('.cta').forEach(btn => {
  btn.addEventListener('mousemove', e => {
    const r = btn.getBoundingClientRect();
    gsap.to(btn, { x:(e.clientX-r.left-r.width/2)*0.2, y:(e.clientY-r.top-r.height/2)*0.2, duration:0.4, ease:"power2.out" });
  });
  btn.addEventListener('mouseleave', () => {
    gsap.to(btn, { x:0, y:0, duration:0.6, ease:"elastic.out(1,0.5)" });
  });
});

// Hero 3D parallax
const heroImgWrap = document.querySelector('.hero-img-wrap');
if (heroImgWrap) {
  document.addEventListener('mousemove', e => {
    gsap.to(heroImgWrap, {
      rotationY:(e.clientX/window.innerWidth-0.5)*15,
      rotationX:-(e.clientY/window.innerHeight-0.5)*15,
      transformPerspective:1200, duration:1.5, ease:"power1.out"
    });
  });
}

// Card hover
document.querySelectorAll('.card').forEach(card => {
  card.addEventListener('mouseenter', () => gsap.to(card, { y:-8, duration:0.5, ease:"power2.out" }));
  card.addEventListener('mouseleave', () => gsap.to(card, { y:0,  duration:0.5, ease:"power2.out" }));
});

// ===== NAVIGATION PILL & SCROLL PROGRESS =====
const pill     = document.querySelector('.nav-pill');
const navLinks = document.querySelectorAll('.nav-links .nav-item');

// Wire up login link inside dropdown
const openLoginNav = document.getElementById('openLoginNav');
if (openLoginNav) {
  openLoginNav.addEventListener('click', () => {
    document.getElementById('loginOverlay').classList.add('active');
    gsap.from(".login-card", { scale:0.98, opacity:0, duration:0.8, ease:"expo.out" });
  });
}
const sections = document.querySelectorAll('section');

function movePill(target) {
  if (target && pill) {
    gsap.to(pill, { left:target.offsetLeft, width:target.offsetWidth, duration:0.5, ease:"expo.out" });
  }
}

window.addEventListener('scroll', () => {
  const winScroll = document.documentElement.scrollTop;
  const height    = document.documentElement.scrollHeight - document.documentElement.clientHeight;
  document.getElementById("progress-bar").style.width = (winScroll / height) * 100 + "%";

  let current = "";
  sections.forEach(s => { if (window.pageYOffset >= s.offsetTop - 120) current = s.getAttribute('id'); });
  navLinks.forEach(link => {
    link.classList.remove('active');
    if (link.getAttribute('href').includes(current)) { link.classList.add('active'); movePill(link); }
  });

  document.getElementById('navbar').classList.toggle('scrolled', window.scrollY > 50);
});

// ===== MOBILE MENU =====
document.getElementById('menuBtn').addEventListener('click', () => {
  document.getElementById('mobileMenu').classList.toggle('active');
});

// ===== THEME TOGGLE =====
document.getElementById('themeToggle').addEventListener('click', () => {
  const isDark = document.documentElement.getAttribute('data-theme') !== 'light';
  document.documentElement.setAttribute('data-theme', isDark ? 'light' : 'dark');
  localStorage.setItem('theme', isDark ? 'light' : 'dark');
  document.querySelector('.sun-icon').style.display  = isDark ? 'block' : 'none';
  document.querySelector('.moon-icon').style.display = isDark ? 'none'  : 'block';
});

// ===== LOGIN OVERLAY =====
document.getElementById('openLogin').addEventListener('click', () => {
  document.getElementById('loginOverlay').classList.add('active');
  gsap.from(".login-card", { scale:0.98, opacity:0, duration:0.8, ease:"expo.out" });
});
document.getElementById('closeLogin').addEventListener('click', () => {
  document.getElementById('loginOverlay').classList.remove('active');
});

// ===== SCANNER LINES =====
window.addEventListener('load', () => {
  document.querySelectorAll('.gupshup-item').forEach(item => {
    const line = item.querySelector('.scanner-line');
    if (!line) return;
    gsap.timeline({ repeat:-1, repeatDelay: Math.random()*5+2 })
      .to(line, { opacity:0.3, duration:0.2 })
      .to(line, { top:"100%", duration:2.5, ease:"none" })
      .to(line, { opacity:0, duration:0.2 });
  });
});

// ===== STAR RATING =====
let selectedRating = 0;
const stars = document.querySelectorAll('.star');
stars.forEach(star => {
  star.addEventListener('click', () => {
    selectedRating = star.getAttribute('data-value');
    stars.forEach(s => s.classList.toggle('active', s.getAttribute('data-value') <= selectedRating));
  });
});

// ===== SUBMIT REVIEW =====
function submitReview() {
  const title = document.getElementById('reviewTitle').value;
  const text  = document.getElementById('reviewText').value;
  const name  = document.getElementById('driverName').value;
  if (!selectedRating || !title || !text || !name) { alert("Please complete all technical fields."); return; }

  const container = document.getElementById('reviewsContainer');
  const html = `
    <div class="review-card" style="opacity:0;transform:translateY(20px)">
      <div class="driver-avatar">${name.charAt(0).toUpperCase()}</div>
      <div class="review-body">
        <div style="font-family:'JetBrains Mono';font-size:9px;margin-bottom:5px;">
          // DRIVER: ${name.toUpperCase()} • ${selectedRating}/5 VERDICT
        </div>
        <h4 style="font-family:'Playfair Display';font-size:1.2rem;margin-bottom:10px;">${title}</h4>
        <p style="font-size:13px;color:var(--muted);">${text}</p>
      </div>
      <div style="font-family:'JetBrains Mono';font-size:9px;opacity:0.5;">${new Date().toLocaleDateString()}</div>
    </div>`;
  const tmp = document.createElement('div');
  tmp.innerHTML = html;
  const el = tmp.firstElementChild;
  container.prepend(el);
  gsap.to(el, { opacity:1, y:0, duration:0.8, ease:"expo.out" });

  document.getElementById('reviewTitle').value = "";
  document.getElementById('reviewText').value  = "";
  document.getElementById('driverName').value  = "";
  selectedRating = 0;
  stars.forEach(s => s.classList.remove('active'));
}

// ===== TAB ATTENTION =====
const docTitle = document.title;
window.addEventListener("blur",  () => { document.title = "Don't Miss the Drive... | DRIVAYAN"; });
window.addEventListener("focus", () => { document.title = docTitle; });

// ============================================================
// LIVE AUTO-UPDATING NEWS ENGINE — DRIVAYAN
// ============================================================

// Unsplash images mapped by category for visual variety
const NEWS_IMAGES = {
  'EV':       'https://images.unsplash.com/photo-1620714223084-8fcacc2dbe4d?q=80&w=800&auto=format',
  'SUV':      'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=800&auto=format',
  'REVIEW':   'https://images.unsplash.com/photo-1492144534655-ae79c964c9d7?q=80&w=800&auto=format',
  'RACE':     'https://images.unsplash.com/photo-1568605117036-5fe5e7bab0b7?q=80&w=800&auto=format',
  'LUXURY':   'https://images.unsplash.com/photo-1563720223185-11003d516935?q=80&w=800&auto=format',
  'CLASSIC':  'https://images.unsplash.com/photo-1504215680853-026ed2a45def?q=80&w=800&auto=format',
  'TECH':     'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?q=80&w=800&auto=format',
  'DEFAULT':  'https://images.unsplash.com/photo-1503376780353-7e6692767b70?q=80&w=800&auto=format',
};

function getNewsImage(category) {
  for (const [key, url] of Object.entries(NEWS_IMAGES)) {
    if (category && category.toUpperCase().includes(key)) return url;
  }
  return NEWS_IMAGES.DEFAULT;
}

function setNewsStatus(state) {
  const pulse = document.getElementById('news-pulse');
  const text  = document.getElementById('news-status-text');
  const icon  = document.getElementById('refresh-icon');
  if (!pulse || !text) return;

  if (state === 'loading') {
    pulse.className = '';
    pulse.style.background = 'var(--muted)';
    pulse.style.animation = '';
    text.textContent = 'FETCHING';
    if (icon) icon.classList.add('spinning');
  } else if (state === 'live') {
    pulse.className = 'pulse-live';
    text.textContent = 'LIVE';
    if (icon) icon.classList.remove('spinning');
  } else if (state === 'error') {
    pulse.className = '';
    pulse.style.background = '#ef4444';
    pulse.style.animation = '';
    text.textContent = 'OFFLINE';
    if (icon) icon.classList.remove('spinning');
  }
}

function updateTimestamp() {
  const el = document.getElementById('news-timestamp');
  if (!el) return;
  const now = new Date();
  el.textContent = `// UPDATED: ${now.toLocaleTimeString('en-IN', {hour:'2-digit', minute:'2-digit'})}`;
}

function renderFeaturedNews(articles) {
  if (!articles || articles.length < 1) return '';
  const main = articles[0];
  const sides = articles.slice(1, 4);

  const sideHTML = sides.map((a, i) => `
    <a href="${a.url || '#'}" class="live-side-card" target="_blank" rel="noopener">
      <span class="live-tag-small">${a.category || 'DISPATCH'}</span>
      <h4 style="font-family:'Playfair Display',serif;font-size:1.05rem;line-height:1.35;">${a.headline}</h4>
      ${a.summary ? `<p style="font-size:12px;color:var(--muted);margin-top:8px;line-height:1.5;">${a.summary.substring(0,90)}${a.summary.length>90?'…':''}</p>` : ''}
    </a>
  `).join('');

  return `
    <div class="news-featured-grid">
      <a href="${main.url || '#'}" class="live-featured-main" target="_blank" rel="noopener">
        <img src="${getNewsImage(main.category)}" alt="${main.headline}" loading="lazy"
             onerror="this.src='${NEWS_IMAGES.DEFAULT}'">
        <div class="live-featured-text">
          <span class="live-tag">${main.category || 'BREAKING'}</span>
          <h2 style="font-size:clamp(1.4rem,2.5vw,2.4rem);color:#fff;line-height:1.2;margin-bottom:10px;">${main.headline}</h2>
          <p style="color:rgba(255,255,255,0.65);font-size:13px;font-weight:300;max-width:500px;line-height:1.55;">${main.summary || ''}</p>
        </div>
      </a>
      <div style="display:flex;flex-direction:column;justify-content:space-between;">
        ${sideHTML}
      </div>
    </div>
  `;
}

function renderSecondaryNews(articles) {
  if (!articles || articles.length < 1) return;
  const row = document.getElementById('news-secondary-row');
  const grid = document.getElementById('news-secondary-grid');
  if (!row || !grid) return;

  grid.innerHTML = articles.map(a => `
    <a href="${a.url || '#'}" class="news-secondary-card" target="_blank" rel="noopener">
      <span style="font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:3px;color:var(--muted);text-transform:uppercase;display:block;margin-bottom:12px;">${a.category || 'NEWS'}</span>
      <h4 style="font-family:'Playfair Display',serif;font-size:1rem;line-height:1.4;margin-bottom:10px;">${a.headline}</h4>
      <p style="font-size:12px;color:var(--muted);line-height:1.55;">${(a.summary||'').substring(0,110)}${(a.summary||'').length>110?'…':''}</p>
      <span class="news-read-more">READ MORE <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></span>
    </a>
  `).join('');

  row.style.display = 'block';
  gsap.from(grid.children, { opacity:0, y:20, duration:0.8, stagger:0.1, ease:'power2.out' });
}

function updateTickerFromNews(articles) {
  if (!articles || !articles.length) return;
  const ticker = document.getElementById('newsTicker');
  if (!ticker) return;
  const all = [...articles, ...articles];
  ticker.innerHTML = all.map(a =>
    `<a href="${a.url||'#'}" class="news-item" target="_blank" rel="noopener"><span>[LIVE]</span> ${a.headline.toUpperCase()}</a>`
  ).join('');
}

async function fetchLiveNews() {
  setNewsStatus('loading');

  const skeleton = document.getElementById('news-skeleton');
  const liveContent = document.getElementById('news-live-content');
  const errorEl = document.getElementById('news-error');

  if (skeleton)     skeleton.style.display = 'grid';
  if (liveContent)  liveContent.style.display = 'none';
  if (errorEl)      errorEl.style.display = 'none';

  const prompt = `You are the news editor for DRIVAYAN, India's premier automotive storytelling platform.

Generate 8 compelling, realistic Indian automotive news stories for ${new Date().toLocaleDateString('en-IN', {day:'numeric', month:'long', year:'numeric'})}.

Mix of categories: EV launches, SUV reviews, luxury cars, racing/motorsport, classic cars, car tech, industry analysis, road trips.

Focus on Indian market but include global news relevant to Indian enthusiasts.

Respond ONLY with a valid JSON array — no markdown, no explanation, no preamble:
[
  {
    "headline": "Catchy news headline (max 12 words)",
    "summary": "2-sentence engaging summary (max 40 words)",
    "category": "ONE OF: EV / SUV / LUXURY / RACE / CLASSIC / TECH / REVIEW / INDUSTRY",
    "url": "#"
  }
]

Make headlines punchy, journalistic, specific. Mention real car models, brands, or events when possible.`;

  try {
    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 1000,
        messages: [{ role: 'user', content: prompt }]
      })
    });

    if (!response.ok) throw new Error(`HTTP ${response.status}`);

    const data = await response.json();
    const raw = data.content?.map(b => b.text || '').join('').trim();

    // Strip markdown fences if any
    const clean = raw.replace(/^```json\s*/i,'').replace(/```\s*$/,'').trim();
    const articles = JSON.parse(clean);

    if (!Array.isArray(articles) || articles.length === 0) throw new Error('Empty articles');

    // Render featured (first 4)
    if (liveContent) {
      liveContent.innerHTML = renderFeaturedNews(articles.slice(0, 4));
      liveContent.style.display = 'block';
    }
    if (skeleton) skeleton.style.display = 'none';

    // Animate featured in
    gsap.from('#news-live-content', { opacity:0, y:20, duration:1, ease:'power2.out' });

    // Render secondary row (articles 5–8)
    renderSecondaryNews(articles.slice(4));

    // Update ticker
    updateTickerFromNews(articles);

    setNewsStatus('live');
    updateTimestamp();

    // Auto-refresh every 5 minutes
    clearTimeout(window._newsRefreshTimer);
    window._newsRefreshTimer = setTimeout(fetchLiveNews, 5 * 60 * 1000);

  } catch (err) {
    console.error('News fetch failed:', err);
    if (skeleton) skeleton.style.display = 'none';
    if (errorEl)  errorEl.style.display = 'block';
    setNewsStatus('error');

    // Fallback to static content after error
    const fallback = [
      { headline: "10,000 KM in a Tata Safari: The Hard Truth", summary: "Our long-term ownership review uncovers what the brochure never tells you.", category: "REVIEW", url: "article-safari.html" },
      { headline: "The Future of V8s in India", summary: "As electrification accelerates, we ask whether the glorious V8 has a future.", category: "INDUSTRY", url: "article-v8.html" },
      { headline: "Petrol vs Diesel: 2026 Analysis", summary: "With fuel prices shifting and EVs rising, which powertrain wins in 2026?", category: "TECH", url: "article-fuel.html" },
      { headline: "Jaipur to Jaisalmer: Moonlit Miles", summary: "1,001 horses thunder across the Thar in the Lamborghini Revuelto.", category: "REVIEW", url: "article-rajasthan.html" },
    ];
    if (liveContent) {
      liveContent.innerHTML = renderFeaturedNews(fallback);
      liveContent.style.display = 'block';
    }
    updateTickerFromNews(fallback);
  }
}

// Boot the live news engine on page load
window.addEventListener('DOMContentLoaded', fetchLiveNews);

</script>

<script>

// ===== PRODUCT DATA =====
const PRODUCTS = [
  {
    id:1, name:"Kryotec Hoodie", category:"apparel", badge:"ltd", badgeText:"LIMITED",
    price:3499, originalPrice:null,
    img:"https://images.unsplash.com/photo-1620799140188-3b2a02fd9a77?auto=format&fit=crop&q=80&w=600",
    desc:"380GSM French terry cotton. Embroidered engine cross-section. Named after Tata's legendary 2.0L diesel. Garment washed.",
    sizes:["S","M","L","XL","XXL"], tag:"APPAREL"
  },
  {
    id:2, name:"Tarmac Tee — Black", category:"apparel", badge:"new", badgeText:"NEW",
    price:999, originalPrice:null,
    img:"https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?auto=format&fit=crop&q=80&w=600",
    desc:"220GSM heavyweight combed cotton. Screen-printed topographic road map of Ladakh on the back. Pre-shrunk.",
    sizes:["S","M","L","XL"], tag:"APPAREL"
  },
  {
    id:3, name:"Tarmac Tee — Khaki", category:"apparel", badge:null,
    price:999, originalPrice:null,
    img:"https://images.unsplash.com/photo-1576566588028-4147f3842f27?auto=format&fit=crop&q=80&w=600",
    desc:"Same quality as the black, in an earthy khaki. Perfect for off-road adventures.",
    sizes:["S","M","L","XL","XXL"], tag:"APPAREL"
  },
  {
    id:4, name:"Petrol Head Cap", category:"accessories", badge:"hot", badgeText:"HOT",
    price:699, originalPrice:899,
    img:"DRIVAYAN-SAFARNAMA-CAP.png?auto=format&fit=crop&q=80&w=600",
    desc:"6-panel structured cap. Embroidered DRIVAYAN wordmark. Adjustable strap. One size.",
    sizes:["ONE SIZE"], tag:"ACCESSORIES"
  },
  {
    id:5, name:"Gear & Gupshup Tote", category:"accessories", badge:null,
    price:599, originalPrice:null,
    img:"Gear & Gupshup-Tote-Bag.png?auto=format&fit=crop&q=80&w=600",
    desc:"12oz natural canvas. Screenprinted gearshift pattern. Reinforced handles. 42cm × 38cm.",
    sizes:["ONE SIZE"], tag:"ACCESSORIES"
  },
  {
    id:6, name:"Safarnama Enamel Pin Set", category:"accessories", badge:"new", badgeText:"NEW",
    price:399, originalPrice:null,
    img:"https://images.unsplash.com/photo-1566438480900-0609be27a4be?auto=format&fit=crop&q=80&w=600",
    desc:"Set of 3 hard enamel pins. Thar silhouette, petrol nozzle, compass rose. Gold plating.",
    sizes:["ONE SIZE"], tag:"ACCESSORIES"
  },
  {
    id:7, name:"Rajasthan Drive — Art Print", category:"prints", badge:"ltd", badgeText:"LIMITED",
    price:1499, originalPrice:1999,
    img:"https://images.unsplash.com/photo-1513364776144-60967b0f800f?auto=format&fit=crop&q=80&w=600",
    desc:"A2 fine art print. 260gsm archival cotton rag paper. Jaipur to Jaisalmer route map with elevation data. Edition of 100.",
    sizes:["A2","A3"], tag:"PRINTS"
  },
  {
    id:8, name:"Gypsy King Garage Poster", category:"prints", badge:null,
    price:899, originalPrice:null,
    img:"GYPSY-poster.jpeg?auto=format&fit=crop&q=80&w=600",
    desc:"A2 risograph print. Two-colour print of a 1998 Maruti Gypsy technical illustration. Bold industrial aesthetic.",
    sizes:["A2","A3"], tag:"PRINTS"
  },
  {
    id:9, name:"Manual Override Sweatshirt", category:"apparel", badge:null,
    price:2199, originalPrice:2799,
    img:"https://images.unsplash.com/photo-1556821840-3a63f15732ce?auto=format&fit=crop&q=80&w=600",
    desc:"340GSM fleece. Embroidered H-pattern gearbox graphic. Ribbed cuffs. A love letter to the manual gearbox.",
    sizes:["S","M","L","XL","XXL"], tag:"APPAREL"
  },
  {
    id:10, name:"Drivayan Sticker Pack", category:"accessories", badge:"new", badgeText:"NEW",
    price:299, originalPrice:null,
    img:"Drivayan-sticker-pack.png?auto=format&fit=crop&q=80&w=600",
    desc:"Pack of 8 die-cut vinyl stickers. UV resistant, waterproof. Perfect for helmets, laptops and bumpers.",
    sizes:["PACK OF 8"], tag:"ACCESSORIES"
  },
  {
    id:11, name:"V8 Requiem — Art Print", category:"prints", badge:"ltd", badgeText:"LIMITED",
    price:1299, originalPrice:null,
    img:"V8-Engine-Poster.png?auto=format&fit=crop&q=80&w=600",
    desc:"A2 mourning poster for the age of V8s. Engine cross-section art. Matte black with silver foil accents. Edition of 75.",
    sizes:["A2"], tag:"PRINTS"
  },
  {
    id:12, name:"Track Day Snapback", category:"accessories", badge:null,
    price:799, originalPrice:null,
    img:"https://images.unsplash.com/photo-1575428652377-a2d80e2277fc?auto=format&fit=crop&q=80&w=600",
    desc:"Flat-brim snapback. Woven patch on front. Moisture-wicking sweatband. One size.",
    sizes:["ONE SIZE"], tag:"ACCESSORIES"
  },
];

// ===== STATE =====
let cart = JSON.parse(localStorage.getItem('drivayan_cart') || '[]');
let activeFilter = 'all';
let selectedFeaturedSize = 'L';
let currentModalProduct = null;

// ===== CART =====
function saveCart() { localStorage.setItem('drivayan_cart', JSON.stringify(cart)); }

function updateCartUI() {
  const count = cart.reduce((a, i) => a + i.qty, 0);
  const total = cart.reduce((a, i) => a + (i.price * i.qty), 0);
  const countEl = document.getElementById('cartCount');
  const countLabelEl = document.getElementById('cartItemCount');
  const totalEl = document.getElementById('cartTotal');
  const footerEl = document.getElementById('cartFooter');
  const bodyEl = document.getElementById('cartBody');

  if (countEl) {
    countEl.textContent = count;
    countEl.classList.toggle('visible', count > 0);
  }
  if (countLabelEl) countLabelEl.textContent = `(${count})`;
  if (totalEl) totalEl.textContent = `₹${total.toLocaleString('en-IN')}`;
  if (footerEl) footerEl.style.display = count > 0 ? 'block' : 'none';

  if (!bodyEl) return;
  if (count === 0) {
    bodyEl.innerHTML = `<div class="cart-empty"><div class="cart-empty-icon">◈</div><p>Your garage bag is empty.<br>Add some fuel to your style.</p></div>`;
    return;
  }
  bodyEl.innerHTML = cart.map((item, idx) => `
    <div class="cart-item">
      <img class="cart-item-img" src="${item.img}" alt="${item.name}">
      <div>
        <div class="cart-item-name">${item.name}</div>
        <div class="cart-item-meta">// ${item.tag} · SIZE: ${item.size} · QTY: ${item.qty}</div>
      </div>
      <div style="text-align:right;">
        <div class="cart-item-price">₹${(item.price*item.qty).toLocaleString('en-IN')}</div>
        <button class="cart-item-remove" onclick="removeFromCart(${idx})">×</button>
      </div>
    </div>`).join('');
}

function addToCart(name, priceStr, img, tag, size) {
  const price = parseInt(priceStr.replace(/[₹,]/g,''));
  const sz = size || selectedFeaturedSize || 'M';
  const existing = cart.find(i => i.name === name && i.size === sz);
  if (existing) { existing.qty++; }
  else { cart.push({ name, price, img, tag, size: sz, qty: 1 }); }
  saveCart();
  updateCartUI();
  showToast(`${name} added to Garage Bag`);
}

function removeFromCart(idx) {
  cart.splice(idx, 1);
  saveCart();
  updateCartUI();
}

function toggleCart() {
  document.getElementById('cartDrawer').classList.toggle('open');
  document.getElementById('cartOverlay').classList.toggle('visible');
}
function closeCart() {
  document.getElementById('cartDrawer').classList.remove('open');
  document.getElementById('cartOverlay').classList.remove('visible');
}
function checkout() {
  showToast('Redirecting to checkout...');
  setTimeout(() => closeCart(), 1000);
}

// ===== TOAST =====
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2800);
}

// ===== SIZE SELECT =====
function selectSize(btn, size) {
  btn.closest('.size-selector').querySelectorAll('.size-btn').forEach(b => b.classList.remove('selected'));
  btn.classList.add('selected');
  selectedFeaturedSize = size;
}

// ===== FILTER =====
function filterProducts(cat, btn) {
  activeFilter = cat;
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active','active-gold'));
  btn.classList.add('active-gold');
  renderProducts();
}

// ===== RENDER PRODUCTS =====
function renderProducts() {
  const grid = document.getElementById('productGrid');
  if (!grid) return;
  const filtered = activeFilter === 'all'
    ? PRODUCTS
    : activeFilter === 'ltd'
    ? PRODUCTS.filter(p => p.badge === 'ltd')
    : PRODUCTS.filter(p => p.category === activeFilter);

  grid.innerHTML = filtered.map((p, i) => {
    const badgeHTML = p.badge
      ? `<div class="product-badge badge-${p.badge}">${p.badgeText || p.badge.toUpperCase()}</div>` : '';
    const priceHTML = p.originalPrice
      ? `<span class="original">₹${p.originalPrice.toLocaleString('en-IN')}</span><span class="discounted">₹${p.price.toLocaleString('en-IN')}</span>`
      : `₹${p.price.toLocaleString('en-IN')}`;
    const sizesHTML = p.sizes.slice(0,4).map(s => `<div class="size-dot">${s[0]}</div>`).join('');
    return `
    <div class="product-card" onclick="openModal(${PRODUCTS.indexOf(p)})">
      <div class="product-img-wrap">
        ${badgeHTML}
        <img src="${p.img}" alt="${p.name}" loading="lazy">
        <div class="product-overlay">
          <button class="quick-add-btn" onclick="event.stopPropagation();addToCart('${p.name}','₹${p.price}','${p.img}','${p.tag}','${p.sizes[0]}')">
            QUICK ADD
          </button>
        </div>
      </div>
      <div class="product-info">
        <span class="product-category">${p.tag}</span>
        <div class="product-name">${p.name}</div>
        <div class="product-footer">
          <div class="product-price">${priceHTML}</div>
          <div class="product-sizes">${sizesHTML}</div>
        </div>
      </div>
    </div>`;
  }).join('');
}

// ===== MODAL =====
function openModal(idx) {
  const p = PRODUCTS[idx];
  currentModalProduct = p;
  document.getElementById('modalImg').src = p.img;
  document.getElementById('modalImg').alt = p.name;
  const priceHTML = p.originalPrice
    ? `<span style="text-decoration:line-through;color:var(--muted);margin-right:8px;">₹${p.originalPrice.toLocaleString('en-IN')}</span><span style="color:var(--gold);">₹${p.price.toLocaleString('en-IN')}</span>`
    : `₹${p.price.toLocaleString('en-IN')}`;
  const sizeBtns = p.sizes.map((s,i) =>
    `<button class="size-btn ${i===0?'selected':''}" onclick="selectModalSize(this,'${s}')">${s}</button>`
  ).join('');
  document.getElementById('modalDetails').innerHTML = `
    <span style="font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:3px;color:var(--gold);">${p.tag}</span>
    <h2 style="font-family:'Playfair Display',serif;font-size:1.6rem;font-weight:500;line-height:1.2;">${p.name}</h2>
    <div style="font-family:'JetBrains Mono',monospace;font-size:1.2rem;font-weight:800;">${priceHTML}</div>
    <p style="color:var(--muted);font-size:13px;line-height:1.8;">${p.desc}</p>
    <div>
      <span style="font-family:'JetBrains Mono',monospace;font-size:8px;letter-spacing:2px;color:var(--muted);display:block;margin-bottom:10px;">// SELECT SIZE</span>
      <div class="size-selector" id="modalSizeSelector">${sizeBtns}</div>
    </div>
    <button class="cta cta-gold" style="width:100%;justify-content:center;"
      onclick="addModalToCart()">ADD TO GARAGE BAG</button>
    <p style="font-family:'JetBrains Mono',monospace;font-size:8px;color:var(--muted);letter-spacing:1px;">// Free shipping above ₹1,999 • Easy 15-day returns</p>
  `;
  document.getElementById('modalBg').classList.add('open');
  document.getElementById('productModal').classList.add('open');
}

function selectModalSize(btn, size) {
  document.getElementById('modalSizeSelector')?.querySelectorAll('.size-btn').forEach(b => b.classList.remove('selected'));
  btn.classList.add('selected');
  currentModalProduct._selectedSize = size;
}

function addModalToCart() {
  if (!currentModalProduct) return;
  const size = currentModalProduct._selectedSize || currentModalProduct.sizes[0];
  addToCart(currentModalProduct.name, `₹${currentModalProduct.price}`, currentModalProduct.img, currentModalProduct.tag, size);
  closeModal();
}

function closeModal() {
  document.getElementById('modalBg').classList.remove('open');
  document.getElementById('productModal').classList.remove('open');
}

// ===== MARQUEE =====
function buildMarquee() {
  const items = ['Free shipping above ₹1,999','SS26 Collection is Live','100% Indian Made','New Drop Every Month','Limited Editions Available','Easy 15-Day Returns'];
  const track = document.getElementById('marqueeTrack');
  const all = [...items,...items];
  track.innerHTML = all.map(t => `<span class="marquee-item">${t}<span class="marquee-sep">◈</span></span>`).join('');
}

// ===== GSAP ANIMATIONS =====
gsap.registerPlugin(ScrollTrigger);

gsap.from(".shop-hero-content > *", {
  opacity:0, y:30, duration:1.2, stagger:0.12, ease:"expo.out", delay:0.2
});

gsap.utils.toArray(".reveal").forEach(el => {
  gsap.fromTo(el,
    { opacity:0, y:30 },
    { opacity:1, y:0, duration:1.2, ease:"power2.out",
      scrollTrigger:{ trigger:el, start:"top 90%" }
    }
  );
});

// Magnetic CTAs
document.querySelectorAll('.cta').forEach(btn => {
  btn.addEventListener('mousemove', e => {
    const r = btn.getBoundingClientRect();
    gsap.to(btn, { x:(e.clientX-r.left-r.width/2)*0.15, y:(e.clientY-r.top-r.height/2)*0.15, duration:0.4, ease:"power2.out" });
  });
  btn.addEventListener('mouseleave', () => {
    gsap.to(btn, { x:0, y:0, duration:0.6, ease:"elastic.out(1,0.5)" });
  });
});

// Collection tile hover depth
document.querySelectorAll('.collection-tile').forEach(tile => {
  tile.addEventListener('click', e => {
    const cat = tile.dataset.filter;
    if (cat) {
      const btn = document.querySelector(`[data-cat="${cat}"]`);
      if (btn) filterProducts(cat, btn);
      document.getElementById('products')?.scrollIntoView({ behavior:'smooth' });
    }
  });
});

// ===== NAV SCROLL =====
window.addEventListener('scroll', () => {
  const pct = (document.documentElement.scrollTop /
    (document.documentElement.scrollHeight - document.documentElement.clientHeight)) * 100;
  document.getElementById('progress-bar').style.width = pct + '%';
  document.getElementById('navbar').classList.toggle('scrolled', window.scrollY > 50);
});

// ===== THEME =====


// ===== MOBILE MENU =====


// ===== NEWSLETTER =====
function handleNewsletter(e) {
  e.preventDefault();
  showToast('You\'re in the garage. Drops coming your way.');
  e.target.reset();
}

// ===== INIT =====
buildMarquee();
renderProducts();
updateCartUI();


/* ═══════════════════════════════════════════════════════════
   DRIVAYAN — VIEW & ARTICLE SYSTEM
   Manages: main site ↔ shop view ↔ article overlays
   Hash routing: #shop, #article-{id}
═══════════════════════════════════════════════════════════ */

// ── Helpers ────────────────────────────────────────────────
function jumpTo(id) {
  setTimeout(() => {
    const el = document.getElementById(id);
    if (el) el.scrollIntoView({ behavior: 'smooth' });
  }, 80);
}

// ── View switcher (main ↔ shop) ────────────────────────────
function showView(view) {
  closeAV(true); // silently close any open article
  const body = document.body;

  if (view === 'shop') {
    body.classList.add('shop-active');
    history.replaceState(null, '', '#shop');
    window.scrollTo({ top: 0, behavior: 'smooth' });
    renderProducts();
    updateCartUI();
    // Animate shop hero
    if (typeof gsap !== 'undefined') {
      gsap.from('.shop-hero-content > *', {
        opacity: 0, y: 30, duration: 1.2, stagger: 0.1,
        ease: 'expo.out', delay: 0.1
      });
      gsap.utils.toArray('#shop-view .reveal').forEach(el => {
        gsap.set(el, { opacity: 0, y: 30 });
        gsap.to(el, {
          opacity: 1, y: 0, duration: 1.2, ease: 'power2.out',
          scrollTrigger: { trigger: el, start: 'top 90%' }
        });
      });
      if (typeof ScrollTrigger !== 'undefined') ScrollTrigger.refresh();
    }
  } else {
    body.classList.remove('shop-active');
    history.replaceState(null, '', location.pathname);
    window.scrollTo({ top: 0, behavior: 'smooth' });
    closeCart();
  }
}

// ── Article viewer ─────────────────────────────────────────
function openAV(pid, label) {
  // Close any already-open panel
  document.querySelectorAll('.av.open').forEach(el => {
    el.classList.remove('open');
    setTimeout(() => { el.style.display = 'none'; }, 10);
  });

  const panel = document.querySelector(`.av[data-p="${pid}"]`);
  if (!panel) return;

  panel.style.display = 'block';
  // Force reflow so transition fires
  panel.getBoundingClientRect();
  panel.classList.add('open');
  panel.scrollTop = 0;

  // Update crumb label
  const crumb = panel.querySelector('.av-crumb');
  if (crumb && label) crumb.textContent = label;

  // GSAP entrance animations scoped to the panel
  if (typeof gsap !== 'undefined') {
    gsap.from(panel.querySelector('header h1'), {
      opacity: 0, y: 40, duration: 1.2, ease: 'expo.out', delay: 0.1
    });
    const animTargets = panel.querySelectorAll(
      'p, h2, .comparison-box, .gear-box, .journey-box, ' +
      '.status-box, .pull-quote, .editorial-quote, ' +
      '.feature-block, .manifesto-grid, .content-wrapper'
    );
    gsap.utils.toArray(animTargets).forEach((el, i) => {
      gsap.fromTo(el,
        { opacity: 0, y: 24 },
        { opacity: 1, y: 0, duration: 0.85, ease: 'power2.out',
          scrollTrigger: { trigger: el, start: 'top 93%', scroller: panel }
        }
      );
    });
    if (typeof ScrollTrigger !== 'undefined') ScrollTrigger.refresh();
  }

  history.replaceState(null, '', `#article-${pid}`);
}

function closeAV(silent) {
  const open = document.querySelectorAll('.av.open');
  open.forEach(el => {
    el.classList.remove('open');
    setTimeout(() => { el.style.display = 'none'; }, silent ? 0 : 480);
  });
  if (!silent) {
    const hash = location.hash;
    history.replaceState(null, '', hash === '#shop' ? '#shop' : location.pathname);
  }
}

// ── Hash routing on load ───────────────────────────────────
const AV_LABELS = {
  safari:    'JOURNEYS // TATA SAFARI',
  soul:      'JOURNEYS // CULTURE',
  modify:    'JOURNEYS // LEGALITY',
  rajasthan: 'SAFARNAMA // RAJASTHAN DIARIES',
  v8:        'NEWS // INSIGHTS',
  fuel:      'NEWS // ANALYSIS',
  suv:       'NEWS // SUV CULTURE',
  accessory: 'GEAR & GUPSHUP // OVERLAND KIT',
  manual:    'GEAR & GUPSHUP // GUPSHUP',
  watches:   'GEAR & GUPSHUP // LIFESTYLE',
  manifesto: 'ABOUT // MANIFESTO',
};

(function routeOnLoad() {
  const hash = location.hash;
  if (hash === '#shop') {
    showView('shop');
  } else if (hash.startsWith('#article-')) {
    const pid = hash.replace('#article-', '');
    setTimeout(() => openAV(pid, AV_LABELS[pid] || pid.toUpperCase()), 300);
  }
})();

window.addEventListener('popstate', () => {
  const hash = location.hash;
  if (hash === '#shop')              showView('shop');
  else if (!hash || hash === '#')    { showView('main'); closeAV(); }
  else if (hash.startsWith('#article-')) {
    const pid = hash.replace('#article-', '');
    if (!document.querySelector(`.av[data-p="${pid}"].open`))
      openAV(pid, AV_LABELS[pid]);
  }
});

</script>

</body>
</html>
