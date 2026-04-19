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
  <link
    href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;700;900&family=Playfair+Display:ital,wght@0,400;0,500;1,400;1,500&family=JetBrains+Mono:wght@400;700;800&display=swap"
    rel="stylesheet">

  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

  <script>
    (function () {
      const savedTheme = localStorage.getItem('theme');
      if (savedTheme) document.documentElement.setAttribute('data-theme', savedTheme);
    })();

    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-8414217468850148"
     crossorigin="anonymous">
       
       </script>

  <style>
    /* ===== THEME VARIABLES ===== */
    :root {
      --bg: #050505;
      --card: rgba(255, 255, 255, 0.03);
      --border: rgba(255, 255, 255, 0.08);
      --text: #ffffff;
      --muted: #888888;
      --accent: #ffffff;
      --nav-bg: rgba(5, 5, 5, 0.85);
      --gold: #c8a96e;
      --gold-dim: rgba(200, 169, 110, 0.12);
    }

    [data-theme="light"] {
      --bg: #fdfdfd;
      --card: #ffffff;
      --border: rgba(0, 0, 0, 0.06);
      --text: #0a0a0a;
      --muted: #666666;
      --accent: #000000;
      --nav-bg: rgba(253, 253, 253, 0.85);
      --gold: #9a6f2e;
      --gold-dim: rgba(154, 111, 46, 0.1);
    }

    /* ===== RESET ===== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    img,
    video,
    svg,
    canvas {
      max-width: 100%;
      height: auto;
      display: block;
    }

    html {
      overflow-x: hidden;
    }

    body {
      overflow-x: hidden;
      -webkit-text-size-adjust: 100%;
    }

    a,
    button {
      -webkit-tap-highlight-color: transparent;
      touch-action: manipulation;
    }

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
    #progress-wrap {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 2px;
      z-index: 2001;
    }

    #progress-bar {
      width: 0%;
      height: 100%;
      background: var(--text);
    }

    /* ===== SIDE SPECS ===== */
    .side-specs {
      position: fixed;
      right: 30px;
      top: 50%;
      transform: translateY(-50%) rotate(90deg);
      transform-origin: right center;
      display: flex;
      gap: 40px;
      z-index: 10;
      pointer-events: none;
      opacity: 0.4;
      max-width: 0;
      overflow: visible;
    }

    .spec-item {
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--muted);
    }

    /* ===== LABEL ===== */
    .label {
      font-size: 9px;
      font-weight: 800;
      letter-spacing: 4px;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 15px;
      display: block;
    }

    h1,
    h2,
    h3,
    h4 {
      font-family: 'Playfair Display', serif;
      font-weight: 500;
      letter-spacing: -0.02em;
    }

    /* ===== NAVIGATION ===== */
    nav {
      position: fixed;
      top: 0;
      width: 100%;
      padding: 0 5%;
      height: 68px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 1000;
      backdrop-filter: blur(25px);
      -webkit-backdrop-filter: blur(25px);
      background: var(--nav-bg);
      border-bottom: 1px solid var(--border);
      transition: height 0.6s cubic-bezier(0.16, 1, 0.3, 1),
                  background 0.6s cubic-bezier(0.16, 1, 0.3, 1);
      gap: 0;
    }

    nav.scrolled { height: 56px; }

    /* ── Brand (left) ── */
    .brand {
      font-weight: 900;
      letter-spacing: 7px;
      text-decoration: none;
      color: var(--text);
      font-size: 1rem;
      flex-shrink: 0;
      white-space: nowrap;
    }

    /* ── Centre link group ── */
    .nav-links {
      display: flex;
      align-items: center;
      position: relative;
      gap: 0;
      flex: 1;
      justify-content: center;
    }

    /* tighten individual link padding so 8 items fit */
    nav a {
      color: var(--muted);
      padding: 8px 11px;
      font-size: 8.5px;
      font-weight: 700;
      letter-spacing: 1.5px;
      text-decoration: none;
      transition: color 0.3s ease;
      white-space: nowrap;
    }

    nav a:hover,
    nav a.active { color: var(--text); }

    .nav-pill {
      position: absolute;
      height: 32px;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 30px;
      z-index: -1;
      pointer-events: none;
    }

    /* ── Right controls group ── */
    .nav-controls {
      display: flex;
      align-items: center;
      gap: 8px;
      flex-shrink: 0;
    }

    /* ===== DROPDOWN HOVER MENUS ===== */
    .nav-item-wrap {
      position: relative;
      display: inline-flex;
      align-items: center;
    }

    .nav-item-wrap>.nav-item {
      position: relative;
      z-index: 1;
    }

    /* The chevron indicator */
    .nav-item-wrap.has-dropdown>.nav-item::after {
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

    .nav-item-wrap.has-dropdown:hover>.nav-item::after {
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
      transition: opacity 0.25s cubic-bezier(0.16, 1, 0.3, 1),
        transform 0.25s cubic-bezier(0.16, 1, 0.3, 1);
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

    /* ── Menu trigger: animated bars ── */
    .menu-trigger {
      display: none;
      background: none;
      border: none;
      color: var(--text);
      cursor: pointer;
      z-index: 1101;
      padding: 6px;
      flex-direction: column;
      justify-content: center;
      gap: 5.5px;
    }

    .menu-trigger .bar {
      display: block;
      width: 22px;
      height: 1.5px;
      background: var(--text);
      transition: transform 0.38s cubic-bezier(0.16, 1, 0.3, 1), opacity 0.25s;
      transform-origin: center;
    }

    .menu-trigger.open .bar:nth-child(1) {
      transform: translateY(7px) rotate(45deg);
    }

    .menu-trigger.open .bar:nth-child(2) {
      opacity: 0;
      transform: scaleX(0);
    }

    .menu-trigger.open .bar:nth-child(3) {
      transform: translateY(-7px) rotate(-45deg);
    }

    /* ── Scrim behind drawer ── */
    .mobile-scrim {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.52);
      z-index: 1099;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.38s ease;
    }

    .mobile-scrim.visible {
      opacity: 1;
      pointer-events: all;
    }

    /* ── Drawer: slides from right ── */
    .mobile-overlay {
      position: fixed;
      top: 0;
      right: 0;
      width: min(340px, 92vw);
      height: 100%;
      background: var(--bg);
      z-index: 1100;
      display: flex;
      flex-direction: column;
      padding: 90px 0 32px;
      border-left: 1px solid var(--border);
      transform: translateX(100%);
      transition: transform 0.48s cubic-bezier(0.16, 1, 0.3, 1);
      overflow-y: auto;
      overflow-x: hidden;
    }

    .mobile-overlay.active {
      transform: translateX(0);
      box-shadow: -24px 0 60px rgba(0, 0, 0, 0.45);
    }

    /* ── Top-level accordion buttons ── */
    .mob-nav-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      width: 100%;
      padding: 15px 28px;
      background: none;
      border: none;
      border-bottom: 1px solid var(--border);
      font-family: 'Playfair Display', serif;
      font-size: 1.2rem;
      color: var(--text);
      cursor: pointer;
      text-align: left;
      transition: color 0.22s, padding-left 0.22s;
      min-height: 52px;
      /* touch target */
    }

    .mob-nav-item:hover,
    .mob-nav-item:focus {
      color: var(--muted);
      padding-left: 34px;
      outline: none;
    }

    .mob-nav-item a {
      text-decoration: none;
      color: inherit;
      flex: 1;
      pointer-events: none;
    }

    .mob-chevron {
      font-family: 'JetBrains Mono', monospace;
      font-size: 10px;
      color: var(--muted);
      transition: transform 0.32s cubic-bezier(0.16, 1, 0.3, 1);
      flex-shrink: 0;
      margin-left: 8px;
    }

    .mob-nav-item.open .mob-chevron {
      transform: rotate(180deg);
    }

    /* ── Accordion sub-panel ── */
    .mob-sub {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.38s cubic-bezier(0.16, 1, 0.3, 1);
      background: var(--card);
      border-bottom: 1px solid var(--border);
    }

    .mob-sub.open {
      max-height: 500px;
    }

    .mob-sub a {
      display: flex;
      align-items: center;
      min-height: 44px;
      /* touch target */
      padding: 10px 28px 10px 42px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--muted);
      text-decoration: none;
      border-bottom: 1px solid var(--border);
      transition: color 0.18s, padding-left 0.18s;
    }

    .mob-sub a:last-child {
      border-bottom: none;
    }

    .mob-sub a:hover {
      color: var(--text);
      padding-left: 48px;
    }

    .mob-sub-label {
      display: block;
      padding: 8px 28px 4px 42px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 7px;
      letter-spacing: 3px;
      color: var(--muted);
      opacity: 0.45;
      text-transform: uppercase;
    }

    .mob-divider {
      border-top: 1px solid var(--border);
      margin: 3px 0;
    }

    /* ── Bottom utility strip ── */
    .mob-footer {
      margin-top: auto;
      padding: 18px 28px;
      display: flex;
      gap: 20px;
      border-top: 1px solid var(--border);
      flex-wrap: wrap;
    }

    .mob-footer a {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      color: var(--muted);
      text-decoration: none;
      transition: color 0.2s;
      min-height: 44px;
      display: flex;
      align-items: center;
    }

    .mob-footer a:hover {
      color: var(--text);
    }

    /* ===== THEME TOGGLE ===== */
    .theme-toggle-btn {
      background: var(--card);
      border: 1px solid var(--border);
      color: var(--text);
      width: 38px;
      height: 38px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: 0.4s;
      flex-shrink: 0;
    }

    .theme-logo {
      filter: grayscale(1) brightness(2);
      transition: filter 0.5s ease, transform 0.5s ease;
    }

    [data-theme="light"] .theme-logo {
      filter: invert(1) grayscale(1) brightness(0.2);
    }

    /* ===== SECTIONS ===== */
    section {
      padding: 100px 8%;
    }

    /* ===== HERO ===== */
    .hero {
      min-height: 100vh;
      padding: 160px 8% 100px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 80px;
    }

    .hero-content {
      flex: 1;
      max-width: 600px;
    }

    .hero h1 {
      font-size: clamp(1.9rem, 7vw, 6rem);
      line-height: 1.05;
      margin-bottom: 30px;
    }

    .hero p {
      margin-bottom: 45px;
      color: var(--muted);
      font-size: 1.2rem;
      font-weight: 300;
      max-width: 450px;
    }

    .hero-img-wrap {
      flex: 1.2;
      position: relative;
      display: flex;
      justify-content: center;
    }

    .hero img {
      width: 100%;
      max-width: 500px;
      display: block;
      object-fit: contain;
    }

    /* ===== CTA ===== */
    .cta {
      display: inline-flex;
      align-items: center;
      padding: 20px 45px;
      border: 1px solid var(--text);
      font-size: 10px;
      font-weight: 800;
      letter-spacing: 4px;
      text-decoration: none;
      color: var(--text);
      position: relative;
      overflow: hidden;
      transition: 0.4s;
    }

    .cta:hover {
      color: var(--bg);
      background: var(--text);
    }

    /* ===== NEWS TICKER ===== */
    .news-ticker-wrap {
      width: 100%;
      background: var(--card);
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      padding: 12px 0;
      overflow: hidden;
      white-space: nowrap;
      margin-bottom: 40px;
    }

    .ticker-content {
      display: inline-block;
      animation: ticker 60s linear infinite;
    }

    .news-item {
      display: inline-block;
      font-family: 'JetBrains Mono', monospace;
      font-size: 10px;
      color: var(--text);
      text-decoration: none;
      padding-right: 50px;
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .news-item span {
      color: var(--muted);
      margin-right: 10px;
    }

    @keyframes ticker {
      0% {
        transform: translateX(0)
      }

      100% {
        transform: translateX(-50%)
      }
    }

    /* ===== FEATURED ===== */
    .section-title {
      margin-bottom: 40px;
    }

    .featured {
      display: grid;
      grid-template-columns: 1.8fr 1fr;
      gap: 40px;
      margin-bottom: 80px;
    }

    .featured-main {
      position: relative;
      border-radius: 12px;
      overflow: hidden;
      aspect-ratio: 16/9;
      display: block;
      text-decoration: none;
    }

    .featured-main img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: 1.2s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .featured-main:hover img {
      transform: scale(1.05);
    }

    .featured-text {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      padding: 60px;
      background: linear-gradient(transparent, rgba(0, 0, 0, 0.85));
    }

    .side-card {
      padding: 30px 0;
      border-bottom: 1px solid var(--border);
      transition: 0.3s;
      cursor: pointer;
      display: block;
      text-decoration: none;
      color: inherit;
    }

    .side-card:hover {
      padding-left: 15px;
      border-bottom-color: var(--text);
    }

    /* ===== CAR GRID ===== */
    .car-grid-container {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 30px;
      padding: 20px 0;
    }

    .car-card {
      background: var(--card);
      border: 1px solid var(--border);
      transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
      text-decoration: none;
      color: inherit;
      display: block;
      position: relative;
    }

    .car-card:hover {
      border-color: var(--text);
      transform: translateY(-5px);
    }

    .car-card .img-box {
      aspect-ratio: 16/9;
      overflow: hidden;
      background: #111;
    }

    .car-card img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      opacity: 0.8;
      transition: 0.8s;
    }

    .car-card:hover img {
      opacity: 1;
      scale: 1.05;
    }

    .car-info {
      padding: 25px;
    }

    .car-meta {
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      color: var(--muted);
      letter-spacing: 1px;
      text-transform: uppercase;
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
    }

    /* ===== JOURNEY CARDS ===== */
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
      gap: 40px;
    }

    .card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 25px;
      transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
      text-decoration: none;
      color: inherit;
      display: block;
    }

    .card:hover {
      border-color: rgba(255, 255, 255, 0.25);
      transform: translateY(-10px);
    }

    .img-container {
      overflow: hidden;
      border-radius: 4px;
      margin-bottom: 25px;
      aspect-ratio: 16/10;
      position: relative;
    }

    .card img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: 0.8s;
    }

    /* ===== SPEC HUD ===== */
    .spec-hud {
      position: absolute;
      inset: 0;
      background: rgba(0, 0, 0, 0.7);
      backdrop-filter: blur(4px);
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 20px;
      opacity: 0;
      transition: opacity 0.4s ease;
      z-index: 2;
    }

    .card:hover .spec-hud {
      opacity: 1;
    }

    .hud-line {
      display: flex;
      justify-content: space-between;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      padding: 8px 0;
      font-family: 'JetBrains Mono', monospace;
      font-size: 10px;
      text-transform: uppercase;
      color: var(--text);
    }

    .hud-value {
      font-weight: 800;
      color: #fff;
    }

    /* ===== SAFARNAMA ===== */
    .safarnama-container {
      display: flex;
      gap: 60px;
      align-items: center;
      margin: 40px 0;
    }

    .safarnama-img ('C:\Users\user\Desktop\DRIVAYAN ALL FILES\Exterior.jpg?auto=format&fit=crop&q=80&w=1200') flex:1;
    height:600px;
    background:url('C:\Users\user\Desktop\DRIVAYAN ALL FILES\Exterior.jpg?auto=format&fit=crop&q=80&w=1200') center/cover;
    border-radius:4px;
    }

    .safarnama-content {
      flex: 1;
    }

    .safarnama-content h2 {
      font-size: clamp(1.8rem, 5vw, 3.5rem);
      margin-bottom: 20px;
      font-style: italic;
    }

    /* ===== LAUNCH PAD ===== */
    .launch-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 1px;
      background: var(--border);
      border: 1px solid var(--border);
    }

    .launch-card {
      background: var(--bg);
      padding: 30px;
      transition: background 0.3s ease;
      text-decoration: none;
      color: inherit;
    }

    .launch-card:hover {
      background: var(--card);
    }

    .status-tag {
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      padding: 2px 8px;
      border: 1px solid var(--text);
      display: inline-block;
      margin-bottom: 15px;
    }

    .status-live {
      background: var(--text);
      color: var(--bg);
    }

    .launch-date {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      color: var(--muted);
      display: block;
      margin-top: 10px;
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

    .gupshup-item:hover {
      border-color: var(--text);
    }

    .scanner-line {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 1px;
      background: linear-gradient(90deg, transparent 0%, var(--text) 50%, transparent 100%);
      opacity: 0;
      pointer-events: none;
      z-index: 5;
      box-shadow: 0 0 8px var(--text);
    }

    /* ===== COMMUNITY REVIEW SECTION ===== */
    .reviews-section {
      padding: 0;
    }

    .review-form {
      margin-bottom: 60px;
    }

    .review-input {
      width: 100%;
      background: transparent;
      border: none;
      border-bottom: 1px solid var(--border);
      padding: 15px 0;
      color: var(--text);
      font-family: 'Montserrat';
      font-size: 13px;
      margin-bottom: 20px;
      outline: none;
      transition: 0.3s;
      display: block;
    }

    .review-input:focus {
      border-bottom-color: var(--text);
    }

    .rating-selector {
      display: flex;
      gap: 10px;
      margin-bottom: 25px;
      cursor: pointer;
    }

    .star {
      font-size: 24px;
      color: var(--border);
      transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .star.active,
    .star:hover {
      color: var(--text);
      text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
      transform: scale(1.2);
    }

    .review-card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 30px;
      margin-bottom: 20px;
      display: grid;
      grid-template-columns: 60px 1fr auto;
      gap: 20px;
      align-items: start;
    }

    .driver-avatar {
      width: 50px;
      height: 50px;
      background: var(--border);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'JetBrains Mono';
      font-size: 12px;
    }

    /* ===== LOGIN OVERLAY ===== */
    .login-overlay {
      position: fixed;
      inset: 0;
      background: var(--bg);
      z-index: 2000;
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      pointer-events: none;
      transition: 0.6s cubic-bezier(0.16, 1, 0.3, 1);
      backdrop-filter: blur(20px);
    }

    .login-overlay.active {
      opacity: 1;
      pointer-events: all;
    }

    .login-card {
      width: 100%;
      max-width: 400px;
      padding: 60px;
      border: 1px solid var(--border);
      background: var(--card);
      text-align: center;
      position: relative;
    }

    .login-card h2 {
      font-size: 2rem;
      margin-bottom: 30px;
    }

    .login-field {
      width: 100%;
      background: transparent;
      border: none;
      border-bottom: 1px solid var(--border);
      padding: 15px 0;
      color: var(--text);
      font-family: 'Montserrat';
      font-size: 13px;
      margin-bottom: 20px;
      outline: none;
      transition: 0.3s;
    }

    .login-field:focus {
      border-bottom-color: var(--text);
    }

    .login-btn {
      width: 100%;
      background: var(--text);
      color: var(--bg);
      border: none;
      padding: 18px;
      font-size: 10px;
      font-weight: 800;
      letter-spacing: 3px;
      cursor: pointer;
      margin-top: 20px;
      transition: 0.3s;
    }

    .login-btn:hover {
      opacity: 0.9;
      transform: translateY(-2px);
    }

    .close-login {
      position: absolute;
      top: 20px;
      right: 20px;
      cursor: pointer;
      color: var(--muted);
      font-size: 12px;
      letter-spacing: 2px;
    }

    /* ===== ABOUT ===== */
    .about-logo {
      width: 280px;
      height: auto;
      margin-bottom: 50px;
    }

    /* ===== FOOTER ===== */
    footer {
      padding: 120px 8% 60px;
      border-top: 1px solid var(--border);
      text-align: center;
    }

    /* ===== RESPONSIVE ===== */
    /* ═══════════════════════════════════════════════════════
     RESPONSIVE — 1024px (Tablet)
  ═══════════════════════════════════════════════════════ */
    @media(max-width:1024px) {
      .hero {
        flex-direction: column;
        text-align: center;
        padding-top: 180px;
      }

      .featured {
        grid-template-columns: 1fr;
      }

      .news-featured-grid {
        grid-template-columns: 1fr;
      }

      .nav-links {
        display: none;
      }

      .menu-trigger {
        display: flex;
      }

      /* On tablet/mobile brand stays left, controls stay right */
      nav {
        padding: 0 5%;
      }

      .safarnama-container {
        flex-direction: column-reverse;
      }

      .gupshup-grid {
        grid-template-columns: 1fr;
      }

      .side-specs {
        display: none !important;
      }
    }

    /* ═══════════════════════════════════════════════════════
     RESPONSIVE — 768px (Large phone / phablet)
  ═══════════════════════════════════════════════════════ */
    @media(max-width:768px) {

      /* ── Global section spacing ── */
      section {
        padding: 60px 5% !important;
      }

      #blog {
        padding: 60px 5% !important;
      }

      #about {
        padding: 80px 5% !important;
      }

      footer {
        padding: 60px 5% 36px !important;
      }

      /* ── Nav ── */
      nav {
        padding: 18px 5%;
      }

      .brand {
        font-size: 1rem;
        letter-spacing: 6px;
      }

      /* ── Hero ── */
      .hero {
        padding: 110px 5% 60px;
        gap: 36px;
      }

      .hero p {
        font-size: 1rem;
        max-width: 100%;
      }

      .hero-img-wrap {
        display: none;
      }

      /* ── CTA — thumb-friendly touch targets ── */
      .cta {
        padding: 16px 28px;
        font-size: 13px !important;
        min-height: 48px;
        width: 100%;
        justify-content: center;
        letter-spacing: 2px;
      }

      .blog-write-cta {
        padding: 15px 24px;
        font-size: 13px !important;
        min-height: 48px;
        width: 100%;
        justify-content: center;
      }

      /* ── HIGH-DENSITY 3-UP car grid ── */
      .car-grid-container {
        grid-template-columns: repeat(3, 1fr) !important;
        gap: 1px !important;
        background: var(--border);
        border: 1px solid var(--border);
        padding: 0 !important;
      }

      .car-card {
        border: none;
        border-radius: 0;
      }

      .car-card:hover {
        transform: none;
      }

      /* no lift on touch */
      .car-card .img-box {
        aspect-ratio: 4/3;
      }

      /* taller crop for 3-col */
      .car-info {
        padding: 10px 8px;
      }

      .car-info h3 {
        font-size: 0.7rem;
        line-height: 1.2;
        margin-bottom: 4px;
      }

      .car-meta {
        font-size: 6px;
        letter-spacing: 0.5px;
        gap: 4px;
        flex-wrap: wrap;
      }

      /* ── HIGH-DENSITY 3-UP journey grid ── */
      .grid {
        grid-template-columns: repeat(3, 1fr) !important;
        gap: 1px !important;
        background: var(--border);
      }

      .card {
        padding: 10px;
        border-radius: 0;
        border: none;
      }

      .card:hover {
        transform: none;
      }

      .img-container {
        margin-bottom: 10px;
        aspect-ratio: 4/3;
      }

      .card h3,
      .card h2 {
        font-size: 0.75rem !important;
        line-height: 1.2;
      }

      /* ── HIGH-DENSITY 3-up blog grid ── */
      .blog-grid {
        grid-template-columns: repeat(3, 1fr) !important;
      }

      .blog-card-body {
        padding: 10px;
      }

      .blog-card-footer {
        padding: 8px 10px;
      }

      .blog-card-title {
        font-size: 0.75rem;
        line-height: 1.2;
      }

      .blog-card-meta {
        font-size: 6px;
        letter-spacing: 0.5px;
        gap: 6px;
      }

      .blog-card-excerpt {
        -webkit-line-clamp: 2;
        font-size: 10px;
      }

      /* Featured post: force single-col on mobile */
      .blog-card-featured {
        grid-column: 1/-1 !important;
        grid-template-columns: 1fr !important;
      }

      .blog-section-head {
        flex-direction: column;
        gap: 16px;
        align-items: flex-start;
      }

      .blog-empty {
        padding: 50px 16px;
      }

      /* ── Spec HUD — always visible, simplified on touch ── */
      .spec-hud {
        opacity: 1 !important;
        background: linear-gradient(transparent 40%, rgba(0, 0, 0, 0.78)) !important;
        backdrop-filter: none !important;
        justify-content: flex-end !important;
        padding: 10px 12px !important;
      }

      .hud-line {
        font-size: 8px;
        padding: 4px 0;
      }

      .hud-line:nth-child(n+3) {
        display: none;
      }

      /* show only top 2 rows */
      /* Tap card to expand all hud lines */
      .card.hud-expanded .hud-line:nth-child(n+3) {
        display: flex;
      }

      .card.hud-expanded .spec-hud {
        background: rgba(0, 0, 0, 0.88) !important;
        justify-content: center !important;
      }

      .hud-tap-hint {
        position: absolute;
        bottom: 6px;
        right: 8px;
        z-index: 3;
        font-family: 'JetBrains Mono', monospace;
        font-size: 7px;
        letter-spacing: 1px;
        color: rgba(255, 255, 255, 0.35);
        pointer-events: none;
      }

      /* ── Safarnama ── */
      .safarnama-container {
        flex-direction: column-reverse;
        gap: 28px;
      }

      .safarnama-img {
        height: 220px !important;
      }

      /* ── Featured news ── */
      .news-featured-grid {
        grid-template-columns: 1fr;
        gap: 20px;
      }

      .featured {
        grid-template-columns: 1fr;
        gap: 20px;
        margin-bottom: 40px;
      }

      .live-featured-text {
        padding: 24px 18px 18px;
      }

      .live-featured-text h3 {
        font-size: 1rem !important;
      }

      #news-secondary-grid {
        grid-template-columns: 1fr !important;
      }

      /* ── Launch pad ── */
      .launch-grid {
        grid-template-columns: repeat(3, 1fr) !important;
      }

      .launch-card {
        min-height: auto;
        padding: 15px;
      }

      /* ── Login overlay — full-width comfortable typing ── */
      .login-card {
        width: 100%;
        max-width: 100%;
        margin: 0;
        padding: 40px 24px;
        border-left: none;
        border-right: none;
        border-top: none;
        border-radius: 0;
        min-height: 100dvh;
        display: flex;
        flex-direction: column;
        justify-content: center;
      }

      .login-field {
        font-size: 16px;
      }

      /* 16px prevents iOS zoom on focus */

      /* ── Blog editor overlay — full-width ── */
      .blog-editor-overlay {
        touch-action: pan-y;
      }

      .blog-editor-body {
        grid-template-columns: 1fr;
      }

      .editor-ai-panel {
        display: none;
      }

      .editor-preview-panel {
        display: none;
      }

      .editor-canvas-inner {
        padding: 24px 16px;
      }

      .blog-editor-topbar {
        padding: 12px 16px;
        flex-wrap: wrap;
        gap: 8px;
      }

      .editor-topbar-right {
        gap: 8px;
        flex-wrap: wrap;
      }

      .editor-btn {
        padding: 8px 14px;
        font-size: 8px;
        min-height: 44px;
      }

      .editor-toolbar {
        padding: 8px 16px;
        gap: 4px;
        overflow-x: auto;
      }

      .blog-editor-overlay .editor-canvas {
        -webkit-overflow-scrolling: touch;
      }

      /* ── Blog reader ── */
      .blog-reader {
        margin: 0;
        padding: 40px 20px;
        border: none;
        min-height: 100dvh;
      }

      /* ── Footer ── */
      footer>div[style*="flex"] {
        flex-direction: column;
        gap: 14px;
      }

      /* ── Ad slots ── */
      .ad-slot-wrap {
        padding: 10px 0;
      }
    }

    /* ═══════════════════════════════════════════════════════
     RESPONSIVE — 480px (Standard phone portrait)
  ═══════════════════════════════════════════════════════ */
    @media(max-width:480px) {
      .hero h1 {
        font-size: clamp(1.7rem, 9.5vw, 2.8rem);
        line-height: 1.1;
      }

      .hero {
        padding: 96px 5% 48px;
      }

      .safarnama-content h2 {
        font-size: clamp(1.5rem, 8vw, 2.2rem);
      }

      section {
        padding: 48px 5% !important;
      }

      /* On very small screens collapse 3-col grids to 2-col if min-width won't fit */
      .car-grid-container {
        grid-template-columns: repeat(3, 1fr) !important;
      }

      /* keep 3-up */
      .grid {
        grid-template-columns: repeat(2, 1fr) !important;
      }

      /* journeys: 2-col */
      .launch-grid {
        grid-template-columns: repeat(2, 1fr) !important;
      }

      .brand {
        font-size: 0.9rem;
        letter-spacing: 4px;
      }

      .cta {
        font-size: 12px !important;
        padding: 14px 18px;
        letter-spacing: 1px;
      }

      /* Blog: keep 2-col but tighter */
      .blog-grid {
        grid-template-columns: repeat(2, 1fr) !important;
      }

      .blog-card-title {
        font-size: 0.78rem;
      }

      .blog-card-body {
        padding: 10px;
      }

      .blog-card-footer {
        padding: 8px 10px;
      }

      .blog-card-excerpt {
        display: none;
      }

      /* drop excerpt on tiny screens */

      #about {
        padding: 60px 5% !important;
      }

      .ad-slot-wrap[data-slot="leaderboard"] {
        display: none;
      }
    }

    /* ═══════════════════════════════════════════════════════
     RESPONSIVE — 360px (Smallest Androids)
  ═══════════════════════════════════════════════════════ */
    @media(max-width:360px) {
      .hero h1 {
        font-size: 1.6rem;
      }

      nav {
        padding: 14px 4%;
      }

      .brand {
        font-size: 0.82rem;
        letter-spacing: 3px;
      }

      section {
        padding: 40px 4% !important;
      }

      .cta {
        font-size: 11px !important;
        padding: 13px 14px;
      }
    }

    /* ===== SHOP NAV ACCENT ===== */
    .nav-item[style*="accent"] {
      position: relative;
    }

    .nav-item[style*="accent"]::before {
      content: '◈';
      position: absolute;
      left: 8px;
      top: 50%;
      transform: translateY(-50%);
      font-size: 6px;
      color: var(--accent);
      opacity: 0.6;
    }

    /* ===== FIX: Ensure .reveal elements are visible as fallback ===== */
    .reveal {
      opacity: 1 !important;
      transform: none !important;
    }

    /* ===== LIVE NEWS STYLES ===== */
    @keyframes shimmer {
      0% {
        transform: translateX(-100%);
      }

      100% {
        transform: translateX(100%);
      }
    }

    .skeleton-shimmer {
      position: absolute;
      inset: 0;
      background: linear-gradient(90deg, transparent 0%, rgba(255, 255, 255, 0.04) 50%, transparent 100%);
      animation: shimmer 1.8s infinite;
    }

    @keyframes pulse-dot {

      0%,
      100% {
        opacity: 1;
        transform: scale(1);
      }

      50% {
        opacity: 0.3;
        transform: scale(0.7);
      }
    }

    .pulse-live {
      animation: pulse-dot 1.2s ease-in-out infinite;
      background: #22c55e !important;
    }

    @keyframes spin-refresh {
      from {
        transform: rotate(0deg);
      }

      to {
        transform: rotate(360deg);
      }
    }

    .spinning {
      animation: spin-refresh 0.8s linear infinite;
    }

    .news-featured-grid {
      display: grid;
      grid-template-columns: 1.8fr 1fr;
      gap: 40px;
    }

    .live-featured-main {
      position: relative;
      border-radius: 4px;
      overflow: hidden;
      aspect-ratio: 16/9;
      display: block;
      text-decoration: none;
      background: var(--card);
      border: 1px solid var(--border);
    }

    .live-featured-main img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: 1.2s cubic-bezier(0.16, 1, 0.3, 1);
      opacity: 0.85;
    }

    .live-featured-main:hover img {
      transform: scale(1.05);
      opacity: 1;
    }

    .live-featured-text {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      padding: 50px 40px 40px;
      background: linear-gradient(transparent, rgba(0, 0, 0, 0.9));
    }

    .live-tag {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 3px;
      text-transform: uppercase;
      padding: 3px 10px;
      border: 1px solid rgba(255, 255, 255, 0.3);
      color: rgba(255, 255, 255, 0.7);
      display: inline-block;
      margin-bottom: 14px;
    }

    .live-side-card {
      padding: 28px 0;
      border-bottom: 1px solid var(--border);
      display: block;
      text-decoration: none;
      color: inherit;
      transition: padding-left 0.3s ease, border-bottom-color 0.3s ease;
      position: relative;
    }

    .live-side-card:last-child {
      border-bottom: none;
    }

    .live-side-card:hover {
      padding-left: 14px;
      border-bottom-color: var(--text);
    }

    .live-side-card .live-tag-small {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--muted);
      display: block;
      margin-bottom: 10px;
    }

    .news-secondary-card {
      border: 1px solid var(--border);
      padding: 24px;
      background: var(--card);
      text-decoration: none;
      color: inherit;
      display: block;
      transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
      position: relative;
      overflow: hidden;
    }

    .news-secondary-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 2px;
      height: 0;
      background: var(--text);
      transition: height 0.4s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .news-secondary-card:hover {
      border-color: rgba(255, 255, 255, 0.2);
      transform: translateY(-4px);
    }

    .news-secondary-card:hover::before {
      height: 100%;
    }

    .news-read-more {
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 2px;
      color: var(--muted);
      text-transform: uppercase;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      margin-top: 16px;
      transition: color 0.3s, gap 0.3s;
    }

    .news-secondary-card:hover .news-read-more {
      color: var(--text);
      gap: 12px;
    }

    /* news-featured-grid 1024px → handled in main responsive block */


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

    .ad-slot-wrap ins {
      display: block;
    }

    /* In-feed ad — sits inside section flow */
    .ad-infeed {
      border: 1px solid var(--border);
      padding: 6px;
      background: var(--card);
      overflow: hidden;
    }


    /* ═══════════════════════════════════════════════════════════
     BLOG FEATURE — DRIVAYAN WIRE
  ═══════════════════════════════════════════════════════════ */

    /* ── Blog section wrapper ── */
    #blog {
      padding: 120px 8%;
      border-top: 1px solid var(--border);
    }

    .blog-section-head {
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      margin-bottom: 60px;
      padding-bottom: 24px;
      border-bottom: 1px solid var(--border);
    }

    .blog-section-label {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 4px;
      color: var(--gold);
      text-transform: uppercase;
      display: block;
      margin-bottom: 10px;
    }

    .blog-section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 500;
      letter-spacing: -0.02em;
      line-height: 1.1;
    }

    /* ── Blog posts grid ── */
    .blog-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
      gap: 1px;
      background: var(--border);
      border: 1px solid var(--border);
      margin-bottom: 60px;
    }

    .blog-card {
      background: var(--bg);
      cursor: pointer;
      position: relative;
      overflow: hidden;
      transition: background 0.35s;
    }

    .blog-card:hover {
      background: var(--card);
    }

    .blog-card-img {
      aspect-ratio: 16/9;
      overflow: hidden;
      background: #0a0a0a;
      position: relative;
    }

    .blog-card-img img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      filter: grayscale(20%);
      transition: transform 1.2s cubic-bezier(0.16, 1, 0.3, 1), filter 0.6s;
    }

    .blog-card:hover .blog-card-img img {
      transform: scale(1.05);
      filter: grayscale(0%);
    }

    .blog-card-cat {
      position: absolute;
      top: 14px;
      left: 14px;
      z-index: 2;
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      padding: 4px 10px;
      font-weight: 800;
      text-transform: uppercase;
      background: var(--gold);
      color: #000;
    }

    .blog-card-body {
      padding: 28px;
    }

    .blog-card-meta {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      color: var(--muted);
      margin-bottom: 12px;
      display: flex;
      gap: 16px;
    }

    .blog-card-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.25rem;
      font-weight: 500;
      line-height: 1.3;
      margin-bottom: 12px;
      transition: color 0.3s;
    }

    .blog-card:hover .blog-card-title {
      color: var(--gold);
    }

    .blog-card-excerpt {
      color: var(--muted);
      font-size: 13px;
      line-height: 1.7;
      display: -webkit-box;
      -webkit-line-clamp: 3;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }

    .blog-card-footer {
      padding: 16px 28px;
      border-top: 1px solid var(--border);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .blog-card-author {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      color: var(--muted);
    }

    .blog-read-link {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      color: var(--gold);
      text-decoration: none;
      font-weight: 800;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: gap 0.3s;
    }

    .blog-card:hover .blog-read-link {
      gap: 10px;
    }

    /* ── Empty state ── */
    .blog-empty {
      padding: 100px 40px;
      text-align: center;
      grid-column: 1/-1;
      background: var(--bg);
    }

    .blog-empty-icon {
      font-size: 48px;
      opacity: 0.15;
      margin-bottom: 20px;
    }

    .blog-empty p {
      color: var(--muted);
      font-size: 14px;
      margin-bottom: 30px;
    }

    /* ── Write button ── */
    .blog-write-cta {
      display: inline-flex;
      align-items: center;
      gap: 12px;
      padding: 18px 40px;
      border: 1px solid var(--gold);
      color: var(--gold);
      font-size: 10px;
      font-weight: 800;
      letter-spacing: 4px;
      text-decoration: none;
      position: relative;
      overflow: hidden;
      transition: 0.4s;
      cursor: pointer;
      background: none;
      font-family: 'Montserrat', sans-serif;
    }

    .blog-write-cta::before {
      content: '';
      position: absolute;
      inset: 0;
      background: var(--gold);
      transform: translateX(-100%);
      transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
      z-index: -1;
    }

    .blog-write-cta:hover {
      color: #000;
    }

    .blog-write-cta:hover::before {
      transform: translateX(0);
    }

    /* ═══════════════════════════════════════════════════════════
     BLOG EDITOR OVERLAY
  ═══════════════════════════════════════════════════════════ */
    .blog-editor-overlay {
      position: fixed;
      inset: 0;
      background: var(--bg);
      z-index: 1500;
      display: flex;
      flex-direction: column;
      transform: translateY(100%);
      transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
      overflow: hidden;
    }

    .blog-editor-overlay.open {
      transform: translateY(0);
    }

    .blog-editor-topbar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 20px 5%;
      border-bottom: 1px solid var(--border);
      background: var(--bg);
      flex-shrink: 0;
      backdrop-filter: blur(20px);
      z-index: 2;
    }

    .editor-brand {
      font-family: 'JetBrains Mono', monospace;
      font-size: 10px;
      letter-spacing: 4px;
      color: var(--gold);
      font-weight: 800;
    }

    .editor-topbar-right {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .editor-status {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      color: var(--muted);
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .editor-status-dot {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--muted);
      transition: background 0.3s;
    }

    .editor-status-dot.active {
      background: #22c55e;
      animation: blink 1.5s ease-in-out infinite;
    }

    .editor-status-dot.generating {
      background: var(--gold);
      animation: blink 0.6s ease-in-out infinite;
    }

    @keyframes blink {

      0%,
      100% {
        opacity: 1
      }

      50% {
        opacity: 0.3
      }
    }

    .editor-btn {
      background: none;
      border: 1px solid var(--border);
      color: var(--muted);
      padding: 9px 20px;
      min-height: 44px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 2px;
      font-weight: 800;
      cursor: pointer;
      transition: all 0.3s;
      text-transform: uppercase;
      display: inline-flex;
      align-items: center;
    }

    .editor-btn:hover {
      border-color: var(--text);
      color: var(--text);
    }

    .editor-btn.primary {
      background: var(--gold);
      border-color: var(--gold);
      color: #000;
    }

    .editor-btn.primary:hover {
      opacity: 0.85;
    }

    .editor-btn.danger {
      border-color: rgba(255, 80, 80, 0.4);
      color: rgba(255, 80, 80, 0.7);
    }

    .editor-btn.danger:hover {
      border-color: #ff5050;
      color: #ff5050;
    }

    .editor-close {
      background: none;
      border: 1px solid var(--border);
      color: var(--muted);
      width: 38px;
      height: 38px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s;
      font-size: 18px;
    }

    .editor-close:hover {
      border-color: var(--text);
      color: var(--text);
    }

    /* ── Editor layout ── */
    .blog-editor-body {
      display: grid;
      grid-template-columns: 280px 1fr 300px;
      flex: 1;
      overflow: hidden;
      min-height: 0;
    }

    /* Left: AI Controls */
    .editor-ai-panel {
      border-right: 1px solid var(--border);
      overflow-y: auto;
      padding: 28px 24px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      background: var(--bg);
    }

    .ai-panel-section {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .ai-panel-label {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 3px;
      color: var(--gold);
      text-transform: uppercase;
      display: block;
    }

    .ai-input {
      width: 100%;
      background: var(--card);
      border: 1px solid var(--border);
      color: var(--text);
      padding: 12px 14px;
      font-family: 'Montserrat', sans-serif;
      font-size: 12px;
      outline: none;
      transition: border-color 0.3s;
      resize: vertical;
    }

    .ai-input:focus {
      border-color: var(--gold);
    }

    .ai-input::placeholder {
      color: var(--muted);
    }

    .ai-select {
      width: 100%;
      background: var(--card);
      border: 1px solid var(--border);
      color: var(--text);
      padding: 10px 14px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 1px;
      outline: none;
      cursor: pointer;
      transition: border-color 0.3s;
      appearance: none;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' fill='none'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%23888' stroke-width='1.5'/%3E%3C/svg%3E");
      background-repeat: no-repeat;
      background-position: right 14px center;
    }

    .ai-select:focus {
      border-color: var(--gold);
    }

    .ai-tag-list {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }

    .ai-tag {
      padding: 5px 12px;
      border: 1px solid var(--border);
      background: none;
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 1px;
      color: var(--muted);
      cursor: pointer;
      transition: all 0.25s;
      border-radius: 30px;
    }

    .ai-tag:hover,
    .ai-tag.selected {
      border-color: var(--gold);
      color: var(--gold);
      background: var(--gold-dim);
    }

    .ai-generate-btn {
      width: 100%;
      padding: 14px;
      background: var(--gold);
      border: none;
      color: #000;
      font-family: 'JetBrains Mono', monospace;
      font-size: 10px;
      font-weight: 800;
      letter-spacing: 3px;
      cursor: pointer;
      transition: opacity 0.3s;
      position: relative;
      overflow: hidden;
      text-transform: uppercase;
    }

    .ai-generate-btn:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }

    .ai-generate-btn:not(:disabled):hover {
      opacity: 0.85;
    }

    .ai-progress-bar {
      position: absolute;
      left: 0;
      top: 0;
      height: 100%;
      background: rgba(0, 0, 0, 0.2);
      width: 0%;
      transition: width 0.3s;
      pointer-events: none;
    }

    .ai-suggestions {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .ai-suggestion-pill {
      padding: 8px 12px;
      background: var(--card);
      border: 1px solid var(--border);
      font-size: 11px;
      color: var(--muted);
      cursor: pointer;
      transition: all 0.3s;
      text-align: left;
      font-family: 'Montserrat', sans-serif;
      line-height: 1.4;
    }

    .ai-suggestion-pill:hover {
      border-color: var(--gold);
      color: var(--text);
      background: var(--gold-dim);
    }

    .ai-divider {
      border: none;
      border-top: 1px solid var(--border);
      margin: 4px 0;
    }

    .word-counter {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      color: var(--muted);
      text-align: right;
    }

    /* Center: Editor canvas */
    .editor-canvas {
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      background: var(--bg);
    }

    .editor-canvas-inner {
      max-width: 760px;
      margin: 0 auto;
      padding: 60px 40px;
      width: 100%;
    }

    .editor-title-input {
      width: 100%;
      background: transparent;
      border: none;
      outline: none;
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 500;
      color: var(--text);
      line-height: 1.2;
      margin-bottom: 8px;
      letter-spacing: -0.02em;
      resize: none;
      overflow: hidden;
    }

    .editor-title-input::placeholder {
      color: rgba(255, 255, 255, 0.1);
    }

    [data-theme="light"] .editor-title-input::placeholder {
      color: rgba(0, 0, 0, 0.15);
    }

    .editor-meta-row {
      display: flex;
      gap: 16px;
      align-items: center;
      flex-wrap: wrap;
      margin-bottom: 32px;
      padding-bottom: 24px;
      border-bottom: 1px solid var(--border);
    }

    .editor-meta-input {
      background: transparent;
      border: none;
      outline: none;
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 2px;
      color: var(--muted);
      padding: 6px 0;
      min-width: 80px;
      border-bottom: 1px solid transparent;
      transition: border-color 0.3s;
    }

    .editor-meta-input:focus {
      border-bottom-color: var(--gold);
      color: var(--text);
    }

    .editor-meta-input::placeholder {
      color: var(--muted);
      opacity: 0.5;
    }

    .editor-meta-sep {
      color: var(--border);
      font-size: 18px;
    }

    /* Toolbar */
    .editor-toolbar {
      display: flex;
      gap: 2px;
      padding: 10px 40px;
      border-bottom: 1px solid var(--border);
      flex-shrink: 0;
      background: var(--bg);
      flex-wrap: wrap;
    }

    .toolbar-btn {
      background: none;
      border: none;
      color: var(--muted);
      padding: 6px 10px;
      font-size: 13px;
      cursor: pointer;
      transition: color 0.2s;
      border-radius: 2px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 10px;
      letter-spacing: 1px;
    }

    .toolbar-btn:hover {
      color: var(--text);
      background: var(--card);
    }

    .toolbar-btn.active {
      color: var(--gold);
      background: var(--gold-dim);
    }

    .toolbar-sep {
      width: 1px;
      background: var(--border);
      margin: 4px 6px;
    }

    .editor-body-input {
      width: 100%;
      background: transparent;
      border: none;
      outline: none;
      font-family: 'Montserrat', sans-serif;
      font-size: 15px;
      line-height: 1.9;
      color: var(--text);
      resize: none;
      min-height: 60vh;
    }

    .editor-body-input::placeholder {
      color: rgba(255, 255, 255, 0.08);
    }

    [data-theme="light"] .editor-body-input::placeholder {
      color: rgba(0, 0, 0, 0.1);
    }

    /* ── AI generating shimmer ── */
    .editor-generating-overlay {
      position: absolute;
      inset: 0;
      background: var(--bg);
      z-index: 5;
      display: none;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      gap: 20px;
    }

    .editor-generating-overlay.show {
      display: flex;
    }

    .gen-spinner {
      width: 48px;
      height: 48px;
      border: 2px solid var(--border);
      border-top-color: var(--gold);
      border-radius: 50%;
      animation: spin 0.8s linear infinite;
    }

    @keyframes spin {
      to {
        transform: rotate(360deg)
      }
    }

    .gen-label {
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 4px;
      color: var(--gold);
      text-transform: uppercase;
    }

    .gen-steps {
      display: flex;
      flex-direction: column;
      gap: 6px;
      align-items: center;
    }

    .gen-step {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      color: var(--muted);
      transition: color 0.4s;
    }

    .gen-step.current {
      color: var(--gold);
    }

    .gen-step.done {
      color: #22c55e;
    }

    /* Right: Preview panel */
    .editor-preview-panel {
      border-left: 1px solid var(--border);
      overflow-y: auto;
      padding: 28px 24px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      background: var(--bg);
    }

    .preview-section-label {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 3px;
      color: var(--muted);
      text-transform: uppercase;
      display: block;
      margin-bottom: 14px;
    }

    .preview-card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 20px;
    }

    .preview-card-title {
      font-family: 'Playfair Display', serif;
      font-size: 1rem;
      font-weight: 500;
      margin-bottom: 8px;
      line-height: 1.3;
    }

    .preview-card-excerpt {
      font-size: 12px;
      color: var(--muted);
      line-height: 1.6;
      display: -webkit-box;
      -webkit-line-clamp: 3;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }

    .preview-publish-info {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .preview-info-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 1px;
      padding: 10px 0;
      border-bottom: 1px solid var(--border);
      color: var(--muted);
    }

    .preview-info-row span:last-child {
      color: var(--text);
    }

    /* Featured image drop zone */
    .image-drop-zone {
      border: 1px dashed var(--border);
      padding: 30px 20px;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s;
      position: relative;
      overflow: hidden;
    }

    .image-drop-zone:hover {
      border-color: var(--gold);
      background: var(--gold-dim);
    }

    .image-drop-zone.has-image {
      padding: 0;
      border-style: solid;
    }

    .image-drop-zone img {
      width: 100%;
      aspect-ratio: 16/9;
      object-fit: cover;
      display: block;
    }

    .image-drop-zone input {
      position: absolute;
      inset: 0;
      opacity: 0;
      cursor: pointer;
    }

    .image-drop-label {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 2px;
      color: var(--muted);
      display: block;
      margin-bottom: 6px;
    }

    /* Toast */
    .blog-toast {
      position: fixed;
      bottom: 40px;
      left: 50%;
      transform: translateX(-50%) translateY(20px);
      background: var(--text);
      color: var(--bg);
      padding: 12px 24px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 2px;
      font-weight: 800;
      z-index: 3000;
      opacity: 0;
      pointer-events: none;
      transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
      border-left: 3px solid var(--gold);
    }

    .blog-toast.show {
      opacity: 1;
      transform: translateX(-50%) translateY(0);
    }

    /* ── Blog reader modal ── */
    .blog-reader-overlay {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.88);
      z-index: 1400;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.4s;
      backdrop-filter: blur(12px);
      overflow-y: auto;
    }

    .blog-reader-overlay.open {
      opacity: 1;
      pointer-events: all;
    }

    .blog-reader {
      max-width: 760px;
      margin: 80px auto;
      padding: 60px 40px;
      background: var(--bg);
      border: 1px solid var(--border);
      position: relative;
      min-height: 60vh;
    }

    .reader-close {
      position: absolute;
      top: 20px;
      right: 20px;
      background: none;
      border: 1px solid var(--border);
      color: var(--muted);
      width: 36px;
      height: 36px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s;
      font-size: 18px;
    }

    .reader-close:hover {
      border-color: var(--text);
      color: var(--text);
    }

    .reader-cat {
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      letter-spacing: 3px;
      color: var(--gold);
      text-transform: uppercase;
      display: block;
      margin-bottom: 16px;
    }

    .reader-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.8rem, 4vw, 2.8rem);
      font-weight: 500;
      line-height: 1.2;
      margin-bottom: 20px;
      letter-spacing: -0.02em;
    }

    .reader-meta {
      font-family: 'JetBrains Mono', monospace;
      font-size: 9px;
      letter-spacing: 2px;
      color: var(--muted);
      display: flex;
      gap: 20px;
      flex-wrap: wrap;
      padding-bottom: 28px;
      border-bottom: 1px solid var(--border);
      margin-bottom: 36px;
    }

    .reader-featured-img {
      width: 100%;
      aspect-ratio: 16/9;
      object-fit: cover;
      margin-bottom: 36px;
      filter: grayscale(20%);
    }

    .reader-body {
      font-size: 16px;
      line-height: 1.9;
      color: var(--text);
      font-family: 'Montserrat', sans-serif;
      font-weight: 300;
    }

    .reader-body p {
      margin-bottom: 24px;
    }

    .reader-body h2 {
      font-family: 'Playfair Display', serif;
      font-size: 1.5rem;
      margin: 36px 0 16px;
      font-style: italic;
    }

    .reader-body h3 {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--gold);
      margin: 30px 0 12px;
    }

    .reader-body blockquote {
      border-left: 2px solid var(--gold);
      padding: 4px 24px;
      margin: 30px 0;
      color: var(--muted);
      font-style: italic;
      font-size: 1.1rem;
    }

    .reader-actions {
      display: flex;
      gap: 12px;
      margin-top: 48px;
      padding-top: 28px;
      border-top: 1px solid var(--border);
    }

    /* blog editor responsive → handled in main responsive block */
  </style>

  <!-- Google AdSense -->
  <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX"
    crossorigin="anonymous"></script>
</head>

<body>

  <div id="progress-wrap">
    <div id="progress-bar"></div>
  </div>

  <div class="side-specs">
    <div class="spec-item">// RPM: 7200</div>
    <div class="spec-item">// GEAR: MANUAL</div>
    <div class="spec-item">// FUEL: HI-OCTANE</div>
    <div class="spec-item" id="live-time">// TIME: --:--</div>
  </div>

  <!-- Mobile scrim -->
  <div class="mobile-scrim" id="mobileScrim" onclick="closeMobileMenu()"></div>

  <div class="mobile-overlay" id="mobileMenu" role="navigation" aria-label="Mobile Navigation">

    <!-- HOME -->
    <button class="mob-nav-item" onclick="closeMobileMenuAndGo('#news')">
      <span>HOME</span>
    </button>

    <!-- LATEST CARS -->
    <button class="mob-nav-item" onclick="toggleMobSub('mob-cars',this)">
      <span>LATEST CARS</span><span class="mob-chevron">▾</span>
    </button>
    <div class="mob-sub" id="mob-cars">
      <span class="mob-sub-label">// BY SEGMENT</span>
      <a href="GRID.html#ev" onclick="closeMobileMenu()">⚡ ELECTRIC</a>
      <a href="GRID.html#suv" onclick="closeMobileMenu()">◈ SUV / 4X4</a>
      <a href="GRID.html#sedan" onclick="closeMobileMenu()">◈ SEDAN</a>
      <a href="GRID.html#luxury" onclick="closeMobileMenu()">◈ LUXURY</a>
      <div class="mob-divider"></div>
      <span class="mob-sub-label">// BY BRAND</span>
      <a href="GRID.html#mahindra" onclick="closeMobileMenu()">◈ MAHINDRA</a>
      <a href="GRID.html#tata" onclick="closeMobileMenu()">◈ TATA</a>
      <a href="GRID.html#maruti" onclick="closeMobileMenu()">◈ MARUTI</a>
    </div>

    <!-- NEWS -->
    <button class="mob-nav-item" onclick="toggleMobSub('mob-news',this)">
      <span>NEWS</span><span class="mob-chevron">▾</span>
    </button>
    <div class="mob-sub" id="mob-news">
      <a href="article-v8.html" onclick="closeMobileMenu()">◈ INSIGHTS</a>
      <a href="article-fuel.html" onclick="closeMobileMenu()">◈ ANALYSIS</a>
      <a href="#launches" onclick="closeMobileMenuAndGo('#launches')">◈ LAUNCHES</a>
      <a href="article-safari.html" onclick="closeMobileMenu()">★ FEATURED</a>
      <div class="mob-divider"></div>
      <a href="#blog" onclick="closeMobileMenuAndGo('#blog')">✎ COMMUNITY BLOG</a>
    </div>

    <!-- JOURNEYS -->
    <button class="mob-nav-item" onclick="toggleMobSub('mob-journeys',this)">
      <span>JOURNEYS</span><span class="mob-chevron">▾</span>
    </button>
    <div class="mob-sub" id="mob-journeys">
      <a href="journeys.html" onclick="closeMobileMenu()">◈ ALL JOURNEYS</a>
      <a href="MODIfy.html" onclick="closeMobileMenu()">◈ LEGALITY</a>
      <div class="mob-divider"></div>
      <a href="Accessory.html" onclick="closeMobileMenu()">◈ OVERLAND KIT</a>
      <a href="watches.html" onclick="closeMobileMenu()">◈ LIFESTYLE</a>
    </div>

    <!-- SAFARNAMA -->
    <button class="mob-nav-item" onclick="closeMobileMenu();window.location='safarnama.html'">
      <span>SAFARNAMA</span>
    </button>

    <!-- ABOUT -->
    <button class="mob-nav-item" onclick="closeMobileMenuAndGo('#about')">
      <span>ABOUT</span>
    </button>

    <!-- GARAGE SHOP -->
    <button class="mob-nav-item" style="border-top:2px solid var(--border);">
      <a href="Coming SOON.html" style="color:var(--gold,#c8a96e);pointer-events:all;">✦ GARAGE SHOP</a>
    </button>

    <div class="mob-footer">
      <a href="https://www.instagram.com/drivayan">Instagram</a>
      <a href="https://www.youtube.com/@drivayan">YouTube</a>
      <a href="javascript:void(0)"
        onclick="document.getElementById('loginOverlay').classList.add('active');closeMobileMenu();">
        Login
      </a>
    </div>

  </div>

  <nav id="navbar">
    <a href="DRIVAYAN.html" class="brand">DRIVAYAN</a>

    <div class="nav-links">
      <div class="nav-pill"></div>

        <!-- HOME -->
        <div class="nav-item-wrap has-dropdown">
          <a href="#news" class="nav-item active">HOME</a>
          <div class="nav-dropdown">
            <span class="dd-label">// QUICK NAV</span>
            <a href="#news"><i class="dd-icon">◈</i> LIVE WIRE</a>
            <a href="#launch-pad"><i class="dd-icon">◈</i> REGISTRY</a>
            <a href="#launches"><i class="dd-icon">◈</i> LAUNCHES</a>
            <div class="dd-divider"></div>
            <a href="#about"><i class="dd-icon">◈</i> MANIFESTO</a>
          </div>
        </div>

        <!-- LATEST CARS -->
        <div class="nav-item-wrap has-dropdown">
          <a href="GRID.html" class="nav-item">LATEST CARS</a>
          <div class="nav-dropdown">
            <span class="dd-label">// BY SEGMENT</span>
            <a href="GRID.html#ev"><i class="dd-icon">⚡</i> ELECTRIC</a>
            <a href="GRID.html#suv"><i class="dd-icon">◈</i> SUV / 4X4</a>
            <a href="GRID.html#sedan"><i class="dd-icon">◈</i> SEDAN</a>
            <a href="GRID.html#luxury"><i class="dd-icon">◈</i> LUXURY</a>
            <div class="dd-divider"></div>
            <span class="dd-label">// BY BRAND</span>
            <a href="GRID.html#mahindra"><i class="dd-icon">◈</i> MAHINDRA</a>
            <a href="GRID.html#tata"><i class="dd-icon">◈</i> TATA</a>
            <a href="GRID.html#maruti"><i class="dd-icon">◈</i> MARUTI</a>
          </div>
        </div>

        <!-- NEWS -->
        <div class="nav-item-wrap has-dropdown">
          <a href="#news" class="nav-item">NEWS</a>
          <div class="nav-dropdown">
            <span class="dd-label">// CATEGORIES</span>
            <a href="article-v8.html"><i class="dd-icon">◈</i> INSIGHTS</a>
            <a href="article-fuel.html"><i class="dd-icon">◈</i> ANALYSIS</a>
            <a href="#launches"><i class="dd-icon">◈</i> LAUNCHES</a>
            <div class="dd-divider"></div>
            <a href="article-safari.html"><i class="dd-icon">★</i> FEATURED</a>
            <div class="dd-divider"></div>
            <a href="#blog" onclick="document.getElementById('blog').scrollIntoView({behavior:'smooth'})"><i
                class="dd-icon" style="color:var(--gold);">✎</i> COMMUNITY BLOG</a>
          </div>
        </div>

        <!-- JOURNEYS -->
        <div class="nav-item-wrap has-dropdown">
          <a href="journeys.html" class="nav-item">JOURNEYS</a>
          <div class="nav-dropdown">
            <span class="dd-label">// FORMATS</span>
            <a href="article-safari.html"><i class="dd-icon">◈</i> OWNERSHIP</a>
            <a href="article-soul.html"><i class="dd-icon">◈</i> CULTURE</a>
            <a href="MODIfy.html"><i class="dd-icon">◈</i> LEGALITY</a>
            <div class="dd-divider"></div>
            <span class="dd-label">// GEAR</span>
            <a href="Accessory.html"><i class="dd-icon">◈</i> OVERLAND KIT</a>
            <a href="watches.html"><i class="dd-icon">◈</i> LIFESTYLE</a>
          </div>
        </div>

        <!-- SAFARNAMA -->
        <div class="nav-item-wrap has-dropdown">
          <a href="safarnama.html" class="nav-item">SAFARNAMA</a>
          <div class="nav-dropdown">
            <span class="dd-label">// TRAVELOGUES</span>
            <a href="article-rajasthan.html"><i class="dd-icon">◈</i> RAJASTHAN DIARIES</a>
            <a href="project-gypsy.html"><i class="dd-icon">◈</i> PROJECT GYPSY</a>
            <div class="dd-divider"></div>
            <a href="gupshup-manual.html"><i class="dd-icon">◈</i> GUPSHUP</a>
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
          <a href="Coming SOON.html" class="nav-item" style="color:var(--gold);">✦ SHOP</a>
          <div class="nav-dropdown">
            <span class="dd-label">// THE COLLECTION</span>
            <a href="shop.html#products"><i class="dd-icon">◈</i> ALL PRODUCTS</a>
            <a href="shop.html#collections"><i class="dd-icon">◈</i> COLLECTIONS</a>
            <a href="shop.html#featured"><i class="dd-icon" style="color:var(--gold);">★</i> NEW DROPS</a>
            <div class="dd-divider"></div>
            <span class="dd-label">// CATEGORIES</span>
            <a href="shop.html?filter=apparel"><i class="dd-icon">◈</i> APPAREL</a>
            <a href="shop.html?filter=accessories"><i class="dd-icon">◈</i> ACCESSORIES</a>
            <a href="shop.html?filter=prints"><i class="dd-icon">◈</i> ART PRINTS</a>
            <div class="dd-divider"></div>
            <a href="shop.html?filter=ltd"><i class="dd-icon" style="color:var(--gold);">◈</i> LIMITED EDITIONS</a>
          </div>
        </div>

    </div>

    <!-- Right: theme toggle + hamburger -->
    <div class="nav-controls">
      <button class="theme-toggle-btn" id="themeToggle" aria-label="Toggle Theme">
        <svg class="moon-icon" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor"
          stroke-width="2">
          <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z" />
        </svg>
        <svg class="sun-icon" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor"
          stroke-width="2" style="display:none">
          <circle cx="12" cy="12" r="5" />
          <line x1="12" y1="1" x2="12" y2="3" />
          <line x1="12" y1="21" x2="12" y2="23" />
          <line x1="4.22" y1="4.22" x2="5.64" y2="5.64" />
          <line x1="18.36" y1="18.36" x2="19.78" y2="19.78" />
          <line x1="1" y1="12" x2="3" y2="12" />
          <line x1="21" y1="12" x2="23" y2="12" />
        </svg>
      </button>
      <button class="menu-trigger" id="menuBtn" aria-label="Toggle menu" aria-expanded="false">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>
    </div>
  </nav>

  <!-- ===== NEWS ===== -->
  <section id="news" style="padding-top:110px;padding-bottom:0;">
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:0;">
      <div class="label section-title" style="margin-bottom:0;">Live Automotive Wire</div>
      <div style="display:flex;align-items:center;gap:16px;">
        <div id="news-status"
          style="display:flex;align-items:center;gap:8px;font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:2px;">
          <span id="news-pulse"
            style="width:6px;height:6px;border-radius:50%;background:var(--muted);display:inline-block;"></span>
          <span id="news-status-text">INITIALISING</span>
        </div>
        <button id="news-refresh-btn" onclick="fetchLiveNews()" title="Refresh news"
          style="background:none;border:1px solid var(--border);color:var(--muted);width:32px;height:32px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all 0.3s;border-radius:2px;"
          onmouseover="this.style.borderColor='var(--text)';this.style.color='var(--text)'"
          onmouseout="this.style.borderColor='var(--border)';this.style.color='var(--muted)'">
          <svg id="refresh-icon" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor"
            stroke-width="2.5">
            <polyline points="23 4 23 10 17 10" />
            <path d="M20.49 15a9 9 0 1 1-2.12-9.36L23 10" />
          </svg>
        </button>
      </div>
    </div>

    <div class="news-ticker-wrap" style="margin-top:20px;">
      <div class="ticker-content" id="newsTicker"></div>
    </div>

    <!-- Ad Slot 1: Leaderboard — between ticker and news grid -->
    <div class="ad-slot-wrap" style="margin-bottom:36px;">
      <span class="ad-slot-label">// SPONSORED</span>
      <ins class="adsbygoogle" style="display:inline-block;width:728px;max-width:100%;height:90px;"
        data-ad-client="ca-pub-XXXXXXXXXXXXXXXX" data-ad-slot="1111111111"></ins>
      <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
    </div>

    <!-- LIVE NEWS GRID -->
    <div id="live-news-container" style="margin-bottom:80px;">

      <!-- SKELETON LOADER -->
      <div id="news-skeleton" style="display:grid;grid-template-columns:1.8fr 1fr;gap:40px;">
        <div
          style="aspect-ratio:16/9;background:var(--card);border:1px solid var(--border);position:relative;overflow:hidden;">
          <div class="skeleton-shimmer"></div>
          <div
            style="position:absolute;bottom:0;left:0;width:100%;padding:40px;background:linear-gradient(transparent,rgba(0,0,0,0.5));">
            <div style="height:8px;width:80px;background:rgba(255,255,255,0.08);margin-bottom:16px;border-radius:2px;">
            </div>
            <div style="height:26px;width:90%;background:rgba(255,255,255,0.08);margin-bottom:10px;border-radius:2px;">
            </div>
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
        <div
          style="font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:3px;margin-bottom:20px;">
          // SIGNAL LOST</div>
        <p style="color:var(--muted);font-size:14px;margin-bottom:30px;">Could not retrieve live feed. Showing archived
          stories.</p>
        <button onclick="fetchLiveNews()" class="cta" style="font-size:9px;padding:14px 30px;">RETRY CONNECTION</button>
      </div>
    </div>

    <!-- SECONDARY NEWS ROW -->
    <div id="news-secondary-row" style="display:none;margin-bottom:80px;">
      <div
        style="display:flex;align-items:center;justify-content:space-between;margin-bottom:24px;padding-bottom:12px;border-bottom:1px solid var(--border);">
        <span class="label" style="margin:0;">// LATEST DISPATCHES</span>
        <span id="news-timestamp"
          style="font-family:'JetBrains Mono',monospace;font-size:9px;color:var(--muted);letter-spacing:2px;"></span>
      </div>
      <div id="news-secondary-grid"
        style="display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:24px;"></div>
    </div>


    <!-- ===== COMMUNITY BLOG — inside News section ===== -->
    <div id="blog" style="margin-top:80px;padding-top:60px;border-top:1px solid var(--border);">

      <div class="blog-section-head reveal">
        <div>
          <span class="blog-section-label">// DRIVAYAN WIRE</span>
          <h2 class="blog-section-title">Community<br><em style="font-style:italic;color:var(--gold)">Blog.</em></h2>
        </div>
        <div style="display:flex;gap:12px;align-items:center;">
          <div style="display:flex;gap:8px;flex-wrap:wrap;" id="blogFilterBar">
            <button class="ai-tag selected" data-filter="ALL" onclick="filterBlogPosts('ALL',this)">ALL</button>
            <button class="ai-tag" data-filter="EV" onclick="filterBlogPosts('EV',this)">EV</button>
            <button class="ai-tag" data-filter="REVIEW" onclick="filterBlogPosts('REVIEW',this)">REVIEW</button>
            <button class="ai-tag" data-filter="ROAD TRIP" onclick="filterBlogPosts('ROAD TRIP',this)">ROAD
              TRIPS</button>
            <button class="ai-tag" data-filter="CULTURE" onclick="filterBlogPosts('CULTURE',this)">CULTURE</button>
            <button class="ai-tag" data-filter="TECH" onclick="filterBlogPosts('TECH',this)">TECH</button>
          </div>
          <button class="blog-write-cta" onclick="openBlogEditor()">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7" />
              <path d="M18.5 2.5a2.121 2.121 0 013 3L12 15l-4 1 1-4 9.5-9.5z" />
            </svg>
            WRITE A POST
          </button>
        </div>
      </div>

      <div class="blog-grid" id="blogGrid">
        <div class="blog-empty">
          <div class="blog-empty-icon">✎</div>
          <p>No posts yet. Be the first voice on the Drivayan Wire.</p>
          <button class="blog-write-cta" onclick="openBlogEditor()">WRITE THE FIRST POST</button>
        </div>
      </div>
    </div>

  </section>

  <!-- ===== AUTOMOTIVE REGISTRY ===== -->
  <section id="launch-pad">
    <div class="label section-title">Automotive Registry / 2026</div>
    <div id="dynamic-car-grid" class="car-grid-container"></div>
  </section>

  <!-- Journeys moved to journeys.html -->





  <!-- Safarnama moved to safarnama.html -->

  <!-- ===== LAUNCH PAD Q1 2026 ===== -->
  <section id="launches" style="padding-top:100px;">
    <div class="label section-title">Launch Pad / Q1 2026</div>
    <div class="launch-grid">
      <a href="#" class="launch-card reveal">
        <span class="status-tag">BOOKINGS OPEN</span>
        <h3 style="font-family:'Playfair Display';">Mahindra XEV 9e <br>Cineluxe Edition</h3>
        <p style="font-size:13px;opacity:0.7;margin:10px 0;">The flagship EV gets a 'Private Lounge' treatment with
          triple-HD display and Satin Black finish.</p>
        <span class="launch-date">// DELIVERY: MARCH 10, 2026</span>
      </a>
      <a href="#" class="launch-card reveal">
        <span class="status-tag">PRICE REVEAL</span>
        <h3 style="font-family:'Playfair Display';">Renault Duster <br>(New Gen)</h3>
        <p style="font-size:13px;opacity:0.7;margin:10px 0;">The icon returns. Expected with a 1.5L Petrol and a strong
          hybrid system to challenge the mid-size SUV kings.</p>
        <span class="launch-date" id="duster-date">// REVEAL: MARCH 17, 2026</span>
      </a>
      <a href="#" class="launch-card reveal">
        <span class="status-tag status-live">JUST LAUNCHED</span>
        <h3 style="font-family:'Playfair Display';">Mercedes-Benz <br>V-Class LWB</h3>
        <p style="font-size:13px;opacity:0.7;margin:10px 0;">Ultra-luxury moving lounge launched with 2.0L Diesel and
          executive captain seats.</p>
        <span class="launch-date">// PRICE: ₹1.40 CR*</span>
      </a>
      <a href="#" class="launch-card reveal">
        <span class="status-tag">SPIED: UNDISGUISED</span>
        <h3 style="font-family:'Playfair Display';">Maruti Suzuki <br>Brezza Facelift</h3>
        <p style="font-size:13px;opacity:0.7;margin:10px 0;">Caught testing with a new chrome-heavy fascia and a 6-speed
          manual gearbox.</p>
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
        <p style="color:var(--muted);font-size:14px;margin-top:15px;">A curated breakdown of the recovery gear that
          actually matters when the tarmac ends and the trail begins.</p>
        <a href="Accessory.html" class="side-card"
          style="margin-top:30px;border-bottom:none;font-size:11px;letter-spacing:2px;">VIEW THE LIST →</a>
      </div>
      <div class="gupshup-item reveal">
        <div class="scanner-line"></div>
        <span class="label">02 / Discussion</span>
        <h3>Is the Manual Dead?</h3>
        <p style="color:var(--muted);font-size:14px;margin-top:15px;">The DRIVAYAN roundtable on why enthusiasts are
          fighting to keep the third pedal alive in an automatic world.</p>
        <a href="gupshup-manual.html" class="side-card"
          style="margin-top:30px;border-bottom:none;font-size:11px;letter-spacing:2px;">JOIN THE CONVERSATION →</a>
      </div>
      <div class="gupshup-item reveal">
        <div class="scanner-line"></div>
        <span class="label">03 / Lifestyle</span>
        <h3>Chronographs &amp; Camshafts</h3>
        <p style="color:var(--muted);font-size:14px;margin-top:15px;">Exploring the deep-rooted obsession between
          vintage timepieces and classic automotive engineering.</p>
        <a href="watches.html" class="side-card"
          style="margin-top:30px;border-bottom:none;font-size:11px;letter-spacing:2px;">READ MORE →</a>
      </div>
      <div class="gupshup-item reveal">
        <div class="scanner-line"></div>
        <span class="label">04 / Restoration</span>
        <h3>Project: Gypsy King</h3>
        <p style="color:var(--muted);font-size:14px;margin-top:15px;">A technical diary of restoring a 1998 Maruti Gypsy
          to its former glory, with a few modern secrets under the hood.</p>
        <a href="project-gypsy.html" class="side-card"
          style="margin-top:30px;border-bottom:none;font-size:11px;letter-spacing:2px;">EXPLORE THE BUILD →</a>
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

  <!-- ===== BLOG EDITOR OVERLAY ===== -->
  <div class="blog-editor-overlay" id="blogEditorOverlay">

    <!-- Top bar -->
    <div class="blog-editor-topbar">
      <span class="editor-brand">// DRIVAYAN WIRE — EDITOR</span>
      <div class="editor-topbar-right">
        <div class="editor-status">
          <div class="editor-status-dot" id="editorStatusDot"></div>
          <span id="editorStatusText">READY</span>
        </div>
        <button class="editor-btn" onclick="saveDraft()">SAVE DRAFT</button>
        <button class="editor-btn primary" onclick="publishPost()">PUBLISH</button>
        <button class="editor-close" onclick="closeBlogEditor()">✕</button>
      </div>
    </div>

    <!-- Toolbar -->
    <div class="editor-toolbar">
      <button class="toolbar-btn" onclick="formatText('bold')" title="Bold"><strong>B</strong></button>
      <button class="toolbar-btn" onclick="formatText('italic')" title="Italic"><em>I</em></button>
      <button class="toolbar-btn" onclick="formatText('h2')">H2</button>
      <button class="toolbar-btn" onclick="formatText('h3')">H3</button>
      <div class="toolbar-sep"></div>
      <button class="toolbar-btn" onclick="formatText('quote')">❝</button>
      <button class="toolbar-btn" onclick="formatText('bullet')">≡</button>
      <div class="toolbar-sep"></div>
      <button class="toolbar-btn" id="wordCountBtn" style="cursor:default;">0 words</button>
    </div>

    <!-- 3-column body -->
    <div class="blog-editor-body">

      <!-- LEFT: AI panel -->
      <div class="editor-ai-panel">

        <div class="ai-panel-section">
          <span class="ai-panel-label">// AI ASSIST</span>
          <textarea class="ai-input" id="aiTopicInput" rows="3"
            placeholder="e.g. Mahindra BE 6 after 6000 km, EV charging problems in Pune..."></textarea>
          <select class="ai-select" id="aiToneSelect">
            <option value="editorial">Editorial — Journalistic, authoritative</option>
            <option value="personal">Personal — First-person ownership story</option>
            <option value="technical">Technical — Spec-heavy deep dive</option>
            <option value="opinion">Opinion — Bold take, hot take</option>
            <option value="narrative">Narrative — Cinematic road story</option>
          </select>
          <select class="ai-select" id="aiLengthSelect">
            <option value="short">Short — ~400 words</option>
            <option value="medium" selected>Medium — ~800 words</option>
            <option value="long">Long — ~1400 words</option>
          </select>
        </div>

        <div class="ai-panel-section">
          <span class="ai-panel-label">// CATEGORY</span>
          <div class="ai-tag-list" id="aiCategoryTags">
            <button class="ai-tag selected" data-cat="EV">EV</button>
            <button class="ai-tag" data-cat="REVIEW">REVIEW</button>
            <button class="ai-tag" data-cat="ROAD TRIP">ROAD TRIP</button>
            <button class="ai-tag" data-cat="CULTURE">CULTURE</button>
            <button class="ai-tag" data-cat="TECH">TECH</button>
            <button class="ai-tag" data-cat="OPINION">OPINION</button>
            <button class="ai-tag" data-cat="INDUSTRY">INDUSTRY</button>
            <button class="ai-tag" data-cat="CLASSIC">CLASSIC</button>
          </div>
        </div>

        <hr class="ai-divider">

        <button class="ai-generate-btn" id="aiGenerateBtn" onclick="generateBlogWithAI()">
          <div class="ai-progress-bar" id="aiProgressBar"></div>
          ✦ GENERATE WITH AI
        </button>

        <hr class="ai-divider">

        <div class="ai-panel-section">
          <span class="ai-panel-label">// QUICK PROMPTS</span>
          <div class="ai-suggestions" id="aiQuickPrompts">
            <button class="ai-suggestion-pill" onclick="loadQuickPrompt(this)">My first road trip in an EV — what nobody
              tells you</button>
            <button class="ai-suggestion-pill" onclick="loadQuickPrompt(this)">Why the manual gearbox deserves to
              survive electrification</button>
            <button class="ai-suggestion-pill" onclick="loadQuickPrompt(this)">6000 km in the Mahindra Thar — real
              ownership verdict</button>
            <button class="ai-suggestion-pill" onclick="loadQuickPrompt(this)">The problem with Indian car journalism in
              2026</button>
            <button class="ai-suggestion-pill" onclick="loadQuickPrompt(this)">Driving from Delhi to Spiti: altitude,
              cold, and survival</button>
          </div>
        </div>

        <hr class="ai-divider">

        <div class="ai-panel-section">
          <span class="ai-panel-label">// AI TOOLS</span>
          <button class="editor-btn" style="width:100%;margin-bottom:6px;" onclick="aiImproveTitle()">✦ IMPROVE
            TITLE</button>
          <button class="editor-btn" style="width:100%;margin-bottom:6px;" onclick="aiContinueWriting()">✦ CONTINUE
            WRITING</button>
          <button class="editor-btn" style="width:100%;" onclick="aiWriteConclusion()">✦ WRITE CONCLUSION</button>
        </div>

      </div>

      <!-- CENTER: Writing canvas -->
      <div class="editor-canvas" id="editorCanvas">
        <div class="editor-canvas-inner" style="position:relative;">

          <!-- Generating overlay -->
          <div class="editor-generating-overlay" id="generatingOverlay">
            <div class="gen-spinner"></div>
            <span class="gen-label" id="genLabel">GENERATING</span>
            <div class="gen-steps">
              <span class="gen-step" id="genStep1">◈ Researching the topic</span>
              <span class="gen-step" id="genStep2">◈ Crafting the narrative</span>
              <span class="gen-step" id="genStep3">◈ Polishing the prose</span>
              <span class="gen-step" id="genStep4">◈ Finalising the draft</span>
            </div>
          </div>

          <textarea id="blogTitleInput" class="editor-title-input" placeholder="Your headline here..." rows="2"
            oninput="autoResize(this);updatePreview()"></textarea>

          <div class="editor-meta-row">
            <input type="text" id="blogAuthorInput" class="editor-meta-input" placeholder="YOUR NAME"
              oninput="updatePreview()">
            <span class="editor-meta-sep">·</span>
            <input type="text" id="blogDateInput" class="editor-meta-input" placeholder="DATE" style="min-width:120px;"
              readonly>
            <span class="editor-meta-sep">·</span>
            <span id="editorReadTime"
              style="font-family:'JetBrains Mono',monospace;font-size:9px;letter-spacing:2px;color:var(--muted);">0 MIN
              READ</span>
          </div>

          <textarea id="blogBodyInput" class="editor-body-input"
            placeholder="Start writing your story...&#10;&#10;Use the AI panel on the left to generate a full draft, or write your own.&#10;&#10;The toolbar above supports basic formatting — or just write freely."
            oninput="updatePreview();updateWordCount()"></textarea>

        </div>
      </div>

      <!-- RIGHT: Preview & metadata -->
      <div class="editor-preview-panel">

        <div>
          <span class="preview-section-label">// FEATURED IMAGE</span>
          <div class="image-drop-zone" id="imageDropZone" onclick="document.getElementById('imageFileInput').click()">
            <span class="image-drop-label">CLICK TO UPLOAD</span>
            <span style="font-size:24px;opacity:0.3;">⬆</span>
            <input type="file" id="imageFileInput" accept="image/*" onchange="handleImageUpload(event)"
              style="position:absolute;inset:0;opacity:0;cursor:pointer;">
          </div>
        </div>

        <hr class="ai-divider">

        <div>
          <span class="preview-section-label">// CARD PREVIEW</span>
          <div class="preview-card" id="previewCard">
            <div
              style="font-family:'JetBrains Mono',monospace;font-size:8px;color:var(--muted);letter-spacing:2px;margin-bottom:8px;"
              id="previewCat">EV</div>
            <div class="preview-card-title" id="previewTitle">Your headline will appear here</div>
            <div class="preview-card-excerpt" id="previewExcerpt">Your opening paragraph will show as the excerpt in the
              blog grid...</div>
          </div>
        </div>

        <hr class="ai-divider">

        <div>
          <span class="preview-section-label">// POST DETAILS</span>
          <div class="preview-publish-info" id="publishInfo">
            <div class="preview-info-row"><span>CATEGORY</span><span id="previewCatLabel">EV</span></div>
            <div class="preview-info-row"><span>AUTHOR</span><span id="previewAuthor">—</span></div>
            <div class="preview-info-row"><span>DATE</span><span id="previewDate">—</span></div>
            <div class="preview-info-row"><span>WORDS</span><span id="previewWords">0</span></div>
            <div class="preview-info-row"><span>READ TIME</span><span id="previewReadTime">0 MIN</span></div>
          </div>
        </div>

      </div>

    </div>
  </div>

  <!-- ===== BLOG READER OVERLAY ===== -->
  <div class="blog-reader-overlay" id="blogReaderOverlay" onclick="handleReaderClick(event)">
    <div class="blog-reader" id="blogReaderContent">
      <button class="reader-close" onclick="closeBlogReader()">✕</button>
      <span class="reader-cat" id="readerCat"></span>
      <h1 class="reader-title" id="readerTitle"></h1>
      <div class="reader-meta" id="readerMeta"></div>
      <img class="reader-featured-img" id="readerFeaturedImg" src="" alt="" style="display:none;">
      <div class="reader-body" id="readerBody"></div>
      <div class="reader-actions">
        <button class="blog-write-cta" onclick="closeBlogReader();openBlogEditor()">✎ WRITE A RESPONSE</button>
      </div>
    </div>
  </div>

  <!-- BLOG TOAST -->
  <div class="blog-toast" id="blogToast"></div>


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
        <input type="text" id="reviewTitle" class="review-input"
          placeholder="REVIEW TITLE (e.g. Mechanical Perfection)">
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
      <ins class="adsbygoogle" style="display:block;" data-ad-client="ca-pub-XXXXXXXXXXXXXXXX" data-ad-slot="3333333333"
        data-ad-format="auto" data-full-width-responsive="true"></ins>
      <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
    </div>

    <a href="#news" class="brand">DRIVAYAN</a>
    <div style="margin:40px 0;display:flex;justify-content:center;gap:30px;flex-wrap:wrap;">
      <a href="https://www.instagram.com/drivayan" class="label" style="margin:0">Instagram</a>
      <a href="https://www.facebook.com/Drivayan" class="label" style="margin:0">Facebook</a>
      <a href="https://www.youtube.com/@drivayan" class="label" style="margin:0">YouTube</a>
      <a href="shop.html" class="label" style="margin:0;color:var(--accent);">Garage Shop</a>
      <a href="javascript:void(0)" class="label" id="openLogin" style="margin:0;color:var(--text);">Login</a>
      <a href="#" class="label" style="margin:0">Privacy</a>
    </div>
    <div style="font-size:10px;color:var(--muted);letter-spacing:2px;opacity:0.6;">© 2026 DRIVAYAN STUDIO.</div>
  </footer>

  <script>
    // ===== CAR REGISTRY =====
    const carRegistry = [
      {
        name: "Mahindra BE 6", tag: "EV / FLAGSHIP",
        desc: "The triple-screen electric powerhouse with Cineluxe interior.",
        status: "BOOKINGS OPEN", link: "Article-BE6.html",
        img: "XUV-9E.jpeg?q=80&w=600"
      },
      {
        name: "New Renault Duster", tag: "SUV / HYBRID",
        desc: "The return of the king. 4x4 capabilities with a refined hybrid heart.",
        status: "T-MINUS 15 DAYS", link: "#",
        img: "REANUALT-DUSTER.jpeg?q=80&w=600"
      },
      {
        name: "Skoda Kushaq L&K", tag: "LUXURY / TURBO",
        desc: "Refined European dynamics with the top-tier Laurin & Klement trim.",
        status: "JUST LAUNCHED", link: "#",
        img: "SKODA-KUSHAQ.jpeg?q=80&w=600"
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
        `// TIME: ${String(now.getHours()).padStart(2, '0')}:${String(now.getMinutes()).padStart(2, '0')}`;
    }, 1000);

    // ===== LAUNCH COUNTDOWN =====
    (function updateLaunchTimer() {
      const target = new Date("March 17, 2026 10:00:00").getTime();
      const now = Date.now();
      const distance = target - now;
      const el = document.getElementById('duster-date');
      if (el && distance > 0) {
        const days = Math.floor(distance / (1000 * 60 * 60 * 24));
        el.innerHTML = `// T-MINUS: ${days} DAYS TO REVEAL`;
      }
    })();

    // ===== GSAP ANIMATIONS =====
    gsap.registerPlugin(ScrollTrigger);

    // ── Mobile/reduced-motion detection ──────────────────────────────────
    const isMobile = window.matchMedia('(max-width:768px)').matches
      || ('ontouchstart' in window)
      || (navigator.maxTouchPoints > 0);
    const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion:reduce)').matches;
    const useHeavyFX = !isMobile && !prefersReducedMotion;

    // ── Scroll reveals ────────────────────────────────────────────────────
    // On mobile: lightweight IntersectionObserver (no GSAP overhead, no battery drain)
    // On desktop: full GSAP ScrollTrigger with stagger
    if (isMobile || prefersReducedMotion) {
      // Make sure reveals start invisible (override the !important fallback)
      const styleTag = document.createElement('style');
      styleTag.textContent = '.reveal { opacity:0 !important; transform:translateY(14px) !important; transition:opacity 0.45s ease, transform 0.45s ease !important; } .reveal.visible { opacity:1 !important; transform:none !important; }';
      document.head.appendChild(styleTag);

      const revealObs = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible');
            revealObs.unobserve(entry.target);
          }
        });
      }, { threshold: 0.08, rootMargin: '0px 0px -32px 0px' });
      document.querySelectorAll('.reveal').forEach(el => revealObs.observe(el));
    } else {
      // Desktop: full GSAP ScrollTrigger
      gsap.utils.toArray(".reveal").forEach(el => {
        gsap.fromTo(el,
          { opacity: 0, y: 25 },
          {
            opacity: 1, y: 0, duration: 1.2, ease: "power2.out",
            scrollTrigger: { trigger: el, start: "top 92%" }
          }
        );
      });
    }

    if (useHeavyFX) {
      // Nav entrance
      gsap.from(".nav-item", { y: -10, opacity: 0, duration: 1.2, stagger: 0.08, ease: "expo.out", delay: 0.3 });

      // Hero entrance
      gsap.from(".hero-content h1", { opacity: 0, y: 10, duration: 1.5, delay: 0.2, ease: "expo.out" });

      // Image parallax
      gsap.utils.toArray(".img-container img, .safarnama-img").forEach(img => {
        gsap.from(img, {
          scale: 1.15,
          scrollTrigger: { trigger: img, start: "top 95%", end: "bottom 20%", scrub: 1.5 }
        });
      });

      // Magnetic CTA (pointer device only)
      document.querySelectorAll('.cta').forEach(btn => {
        btn.addEventListener('mousemove', e => {
          const r = btn.getBoundingClientRect();
          gsap.to(btn, { x: (e.clientX - r.left - r.width / 2) * 0.2, y: (e.clientY - r.top - r.height / 2) * 0.2, duration: 0.4, ease: "power2.out" });
        });
        btn.addEventListener('mouseleave', () => {
          gsap.to(btn, { x: 0, y: 0, duration: 0.6, ease: "elastic.out(1,0.5)" });
        });
      });

      // Hero 3D parallax (mouse-only)
      const heroImgWrap = document.querySelector('.hero-img-wrap');
      if (heroImgWrap) {
        document.addEventListener('mousemove', e => {
          gsap.to(heroImgWrap, {
            rotationY: (e.clientX / window.innerWidth - 0.5) * 15,
            rotationX: -(e.clientY / window.innerHeight - 0.5) * 15,
            transformPerspective: 1200, duration: 1.5, ease: "power1.out"
          });
        });
      }

      // Card hover lift
      document.querySelectorAll('.card').forEach(card => {
        card.addEventListener('mouseenter', () => gsap.to(card, { y: -8, duration: 0.5, ease: "power2.out" }));
        card.addEventListener('mouseleave', () => gsap.to(card, { y: 0, duration: 0.5, ease: "power2.out" }));
      });
    }


    // ===== SPEC HUD — tap-to-expand on touch =====
    if ('ontouchstart' in window || navigator.maxTouchPoints > 0) {
      document.addEventListener('click', e => {
        const card = e.target.closest('.card');
        if (!card) return;
        if (e.target.tagName === 'A') return;          // don't block links
        const wasExpanded = card.classList.contains('hud-expanded');
        // Collapse all
        document.querySelectorAll('.card.hud-expanded').forEach(c2 => c2.classList.remove('hud-expanded'));
        if (!wasExpanded) card.classList.add('hud-expanded');
      });
    }

    // ===== NAVIGATION PILL & SCROLL PROGRESS =====
    const pill = document.querySelector('.nav-pill');
    const navLinks = document.querySelectorAll('.nav-links .nav-item');

    // Wire up login link inside dropdown
    const openLoginNav = document.getElementById('openLoginNav');
    if (openLoginNav) {
      openLoginNav.addEventListener('click', () => {
        document.getElementById('loginOverlay').classList.add('active');
        gsap.from(".login-card", { scale: 0.98, opacity: 0, duration: 0.8, ease: "expo.out" });
      });
    }
    const sections = document.querySelectorAll('section');

    function movePill(target) {
      if (target && pill) {
        gsap.to(pill, { left: target.offsetLeft, width: target.offsetWidth, duration: 0.5, ease: "expo.out" });
      }
    }

    window.addEventListener('scroll', () => {
      const winScroll = document.documentElement.scrollTop;
      const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
      document.getElementById("progress-bar").style.width = (winScroll / height) * 100 + "%";

      let current = "";
      sections.forEach(s => { if (window.pageYOffset >= s.offsetTop - 120) current = s.getAttribute('id'); });
      navLinks.forEach(link => {
        link.classList.remove('active');
        if (link.getAttribute('href').includes(current)) { link.classList.add('active'); movePill(link); }
      });

      document.getElementById('navbar').classList.toggle('scrolled', window.scrollY > 50);
    });

    // ===== MOBILE MENU — slide-right drawer with accordion =====
    const _menuBtn = document.getElementById('menuBtn');
    const _mobileMenu = document.getElementById('mobileMenu');
    const _mobileScrim = document.getElementById('mobileScrim');

    function openMobileMenu() {
      _mobileMenu.classList.add('active');
      _mobileScrim.classList.add('visible');
      _menuBtn.classList.add('open');
      _menuBtn.setAttribute('aria-expanded', 'true');
      document.body.style.overflow = 'hidden';
    }
    function closeMobileMenu() {
      _mobileMenu.classList.remove('active');
      _mobileScrim.classList.remove('visible');
      _menuBtn.classList.remove('open');
      _menuBtn.setAttribute('aria-expanded', 'false');
      document.body.style.overflow = '';
      // Collapse all open sub-panels
      document.querySelectorAll('.mob-sub.open').forEach(s => s.classList.remove('open'));
      document.querySelectorAll('.mob-nav-item.open').forEach(b => b.classList.remove('open'));
    }
    function closeMobileMenuAndGo(hash) {
      closeMobileMenu();
      setTimeout(() => {
        const el = document.querySelector(hash);
        if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' });
      }, 300);
    }
    function toggleMobSub(subId, btn) {
      const sub = document.getElementById(subId);
      const isOpen = sub.classList.contains('open');
      // Close all subs first
      document.querySelectorAll('.mob-sub.open').forEach(s => s.classList.remove('open'));
      document.querySelectorAll('.mob-nav-item.open').forEach(b => b.classList.remove('open'));
      if (!isOpen) { sub.classList.add('open'); btn.classList.add('open'); }
    }

    _menuBtn.addEventListener('click', () => {
      _mobileMenu.classList.contains('active') ? closeMobileMenu() : openMobileMenu();
    });

    // Swipe-right gesture to close
    let _swipeStartX = 0;
    _mobileMenu.addEventListener('touchstart', e => {
      _swipeStartX = e.changedTouches[0].screenX;
    }, { passive: true });
    _mobileMenu.addEventListener('touchend', e => {
      if (e.changedTouches[0].screenX - _swipeStartX > 55) closeMobileMenu();
    }, { passive: true });

    // Escape key
    document.addEventListener('keydown', e => {
      if (e.key === 'Escape' && _mobileMenu.classList.contains('active')) closeMobileMenu();
    });

    // ===== THEME TOGGLE =====
    document.getElementById('themeToggle').addEventListener('click', () => {
      const isDark = document.documentElement.getAttribute('data-theme') !== 'light';
      document.documentElement.setAttribute('data-theme', isDark ? 'light' : 'dark');
      localStorage.setItem('theme', isDark ? 'light' : 'dark');
      document.querySelector('.sun-icon').style.display = isDark ? 'block' : 'none';
      document.querySelector('.moon-icon').style.display = isDark ? 'none' : 'block';
    });

    // ===== LOGIN OVERLAY =====
    document.getElementById('openLogin').addEventListener('click', () => {
      document.getElementById('loginOverlay').classList.add('active');
      gsap.from(".login-card", { scale: 0.98, opacity: 0, duration: 0.8, ease: "expo.out" });
    });
    document.getElementById('closeLogin').addEventListener('click', () => {
      document.getElementById('loginOverlay').classList.remove('active');
    });

    // ===== SCANNER LINES =====
    window.addEventListener('load', () => {
      document.querySelectorAll('.gupshup-item').forEach(item => {
        const line = item.querySelector('.scanner-line');
        if (!line) return;
        gsap.timeline({ repeat: -1, repeatDelay: Math.random() * 5 + 2 })
          .to(line, { opacity: 0.3, duration: 0.2 })
          .to(line, { top: "100%", duration: 2.5, ease: "none" })
          .to(line, { opacity: 0, duration: 0.2 });
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
    const API_BASE = 'http://localhost:3001/api'; // change to your deployed URL in production

    function submitReview() {
      const title = document.getElementById('reviewTitle').value;
      const text = document.getElementById('reviewText').value;
      const name = document.getElementById('driverName').value;
      if (!selectedRating || !title || !text || !name) { alert("Please complete all technical fields."); return; }

      // Optimistic UI
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
      gsap.to(el, { opacity: 1, y: 0, duration: 0.8, ease: "expo.out" });

      // Persist to backend
      fetch(`${API_BASE}/reviews`, {
        method: 'POST', headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ title, text, driverName: name, stars: selectedRating })
      }).catch(() => { }); // silent fail — UI already updated

      document.getElementById('reviewTitle').value = "";
      document.getElementById('reviewText').value = "";
      document.getElementById('driverName').value = "";
      selectedRating = 0;
      stars.forEach(s => s.classList.remove('active'));
    }

    // ===== TAB ATTENTION =====
    const docTitle = document.title;
    window.addEventListener("blur", () => { document.title = "Don't Miss the Drive... | DRIVAYAN"; });
    window.addEventListener("focus", () => { document.title = docTitle; });

    // ============================================================
    // LIVE AUTO-UPDATING NEWS ENGINE — DRIVAYAN
    // ============================================================

    // Unsplash images mapped by category for visual variety
    const NEWS_IMAGES = {
      'EV': 'https://images.unsplash.com/photo-1620714223084-8fcacc2dbe4d?q=80&w=800&auto=format',
      'SUV': 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?q=80&w=800&auto=format',
      'REVIEW': 'https://images.unsplash.com/photo-1492144534655-ae79c964c9d7?q=80&w=800&auto=format',
      'RACE': 'https://images.unsplash.com/photo-1568605117036-5fe5e7bab0b7?q=80&w=800&auto=format',
      'LUXURY': 'https://images.unsplash.com/photo-1563720223185-11003d516935?q=80&w=800&auto=format',
      'CLASSIC': 'https://images.unsplash.com/photo-1504215680853-026ed2a45def?q=80&w=800&auto=format',
      'TECH': 'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?q=80&w=800&auto=format',
      'DEFAULT': 'https://images.unsplash.com/photo-1503376780353-7e6692767b70?q=80&w=800&auto=format',
    };

    function getNewsImage(category) {
      for (const [key, url] of Object.entries(NEWS_IMAGES)) {
        if (category && category.toUpperCase().includes(key)) return url;
      }
      return NEWS_IMAGES.DEFAULT;
    }

    function setNewsStatus(state) {
      const pulse = document.getElementById('news-pulse');
      const text = document.getElementById('news-status-text');
      const icon = document.getElementById('refresh-icon');
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
      el.textContent = `// UPDATED: ${now.toLocaleTimeString('en-IN', { hour: '2-digit', minute: '2-digit' })}`;
    }

    function renderFeaturedNews(articles) {
      if (!articles || articles.length < 1) return '';
      const main = articles[0];
      const sides = articles.slice(1, 4);

      const sideHTML = sides.map((a, i) => `
    <a href="${a.url || '#'}" class="live-side-card" target="_blank" rel="noopener">
      <span class="live-tag-small">${a.category || 'DISPATCH'}</span>
      <h4 style="font-family:'Playfair Display',serif;font-size:1.05rem;line-height:1.35;">${a.headline}</h4>
      ${a.summary ? `<p style="font-size:12px;color:var(--muted);margin-top:8px;line-height:1.5;">${a.summary.substring(0, 90)}${a.summary.length > 90 ? '…' : ''}</p>` : ''}
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
      <p style="font-size:12px;color:var(--muted);line-height:1.55;">${(a.summary || '').substring(0, 110)}${(a.summary || '').length > 110 ? '…' : ''}</p>
      <span class="news-read-more">READ MORE <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></span>
    </a>
  `).join('');

      row.style.display = 'block';
      gsap.from(grid.children, { opacity: 0, y: 20, duration: 0.8, stagger: 0.1, ease: 'power2.out' });
    }

    function updateTickerFromNews(articles) {
      if (!articles || !articles.length) return;
      const ticker = document.getElementById('newsTicker');
      if (!ticker) return;
      const all = [...articles, ...articles];
      ticker.innerHTML = all.map(a =>
        `<a href="${a.url || '#'}" class="news-item" target="_blank" rel="noopener"><span>[LIVE]</span> ${a.headline.toUpperCase()}</a>`
      ).join('');
    }

    async function fetchLiveNews() {
      setNewsStatus('loading');

      const skeleton = document.getElementById('news-skeleton');
      const liveContent = document.getElementById('news-live-content');
      const errorEl = document.getElementById('news-error');

      if (skeleton) skeleton.style.display = 'grid';
      if (liveContent) liveContent.style.display = 'none';
      if (errorEl) errorEl.style.display = 'none';

      const prompt = `You are the news editor for DRIVAYAN, India's premier automotive storytelling platform.

Generate 8 compelling, realistic Indian automotive news stories for ${new Date().toLocaleDateString('en-IN', { day: 'numeric', month: 'long', year: 'numeric' })}.

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
        const clean = raw.replace(/^```json\s*/i, '').replace(/```\s*$/, '').trim();
        const articles = JSON.parse(clean);

        if (!Array.isArray(articles) || articles.length === 0) throw new Error('Empty articles');

        // Render featured (first 4)
        if (liveContent) {
          liveContent.innerHTML = renderFeaturedNews(articles.slice(0, 4));
          liveContent.style.display = 'block';
        }
        if (skeleton) skeleton.style.display = 'none';

        // Animate featured in
        gsap.from('#news-live-content', { opacity: 0, y: 20, duration: 1, ease: 'power2.out' });

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
        if (errorEl) errorEl.style.display = 'block';
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




    // ═══════════════════════════════════════════════════════════════════════════
    // BLOG SYSTEM — DRIVAYAN WIRE
    // ═══════════════════════════════════════════════════════════════════════════

    // ── State ────────────────────────────────────────────────────────────────
    let blogPosts = JSON.parse(localStorage.getItem('drivayan_blog_posts') || '[]');
    let editingPostId = null;
    let selectedBlogCategory = 'EV';
    let currentBlogFilter = 'ALL';
    let blogFeaturedImageData = null;

    // Seed sample posts if none exist
    if (blogPosts.length === 0) {
      blogPosts = [
        {
          id: 'post_seed_1',
          title: '10,000 KM in the Mahindra BE 6: The Honest EV Truth',
          body: `When I picked up my Mahindra BE 6 from the dealership in Bangalore six months ago, I had exactly three concerns: range anxiety, charging infrastructure, and whether the triple-screen interior would age well.\n\nSix months and 10,000 kilometres later, here's the unfiltered verdict.\n\nThe range anxiety is real — but manageable. On the highway between Bangalore and Mysore, I averaged 340 km on a full charge. In city traffic? Closer to 400. The claimed 540 km is theoretical. But here's the thing — theoretical is irrelevant when real-world performance is good enough.\n\nCharging is where India still has work to do. I found just four DC fast chargers operational on the Bangalore-Pune highway. Two were occupied. One was out of order. The fourth worked perfectly and filled me to 80% in 38 minutes.\n\nThe interior has aged brilliantly. The Cineluxe seats still feel premium. The ambient lighting still makes passengers gasp. The triple screen still draws attention at fuel stations — yes, people at fuel stations stop to look.\n\nWould I buy it again? Without question. But I'd also buy a portable Level 2 charger and plan every long highway trip around charging stops.`,
          category: 'EV',
          author: 'Arjun Mehta',
          date: 'March 10, 2026',
          readTime: 3,
          wordCount: 210,
          image: null,
          draft: false
        },
        {
          id: 'post_seed_2',
          title: 'The Manual Gearbox Is Not Dead. It Is Chosen.',
          body: `Every obituary for the manual gearbox is written by someone who never drove a Thar through Spiti Valley at 4,500 metres.\n\nThe argument against manuals is economic. Automatics are faster, smoother, more fuel-efficient on paper. This is all true. It is also irrelevant.\n\nA manual gearbox is not a transmission. It is a conversation between driver and machine. Every gear change is a decision — downshift before the corner, hold third through the mountain hairpin, blip the throttle on the way down. An automatic takes that conversation away. It speaks for you.\n\nI drove from Manali to Kaza in a 6-speed manual Thar last October. The road was broken tarmac, loose shale, and frozen stream crossings. Every metre required thought. Every gear required intention. By the time I reached Kaza, I was exhausted in the best way — the exhaustion of having actually driven, not just arrived.\n\nElectrification will kill the manual eventually. Battery weight demands single-speed simplicity. But until then, every kilometre in a three-pedal car is a protest — quiet, joyful, entirely analogue.\n\nDrive manual while you still can. In twenty years, you will miss it the way your father misses carburettors.`,
          category: 'CULTURE',
          author: 'Rohan Sharma',
          date: 'March 5, 2026',
          readTime: 2,
          wordCount: 198,
          image: null,
          draft: false
        }
      ];
      localStorage.setItem('drivayan_blog_posts', JSON.stringify(blogPosts));
    }

    // ── Render blog grid ──────────────────────────────────────────────────────
    function renderBlogGrid(filter) {
      const grid = document.getElementById('blogGrid');
      if (!grid) return;

      const posts = blogPosts.filter(p => !p.draft && (filter === 'ALL' || p.category === filter));

      if (posts.length === 0) {
        grid.innerHTML = `
      <div class="blog-empty">
        <div class="blog-empty-icon">✎</div>
        <p>No posts in this category yet.</p>
        <button class="blog-write-cta" onclick="openBlogEditor()">WRITE THE FIRST POST</button>
      </div>`;
        return;
      }

      // First post is featured (full width)
      const featured = posts[0];
      const rest = posts.slice(1);
      const BLOG_IMGS = {
        'EV': 'https://images.unsplash.com/photo-1620714223084-8fcacc2dbe4d?auto=format&fit=crop&q=80&w=800',
        'REVIEW': 'https://images.unsplash.com/photo-1492144534655-ae79c964c9d7?auto=format&fit=crop&q=80&w=800',
        'ROAD TRIP': 'https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?auto=format&fit=crop&q=80&w=800',
        'CULTURE': 'https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&q=80&w=800',
        'TECH': 'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?auto=format&fit=crop&q=80&w=800',
        'OPINION': 'https://images.unsplash.com/photo-1504215680853-026ed2a45def?auto=format&fit=crop&q=80&w=800',
        'INDUSTRY': 'https://images.unsplash.com/photo-1568605117036-5fe5e7bab0b7?auto=format&fit=crop&q=80&w=800',
        'CLASSIC': 'https://images.unsplash.com/photo-1519641471654-76ce0107ad1b?auto=format&fit=crop&q=80&w=800',
        'DEFAULT': 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?auto=format&fit=crop&q=80&w=800',
      };
      function getImg(post) {
        return post.image || BLOG_IMGS[post.category] || BLOG_IMGS['DEFAULT'];
      }
      function getExcerpt(body) {
        return body.replace(/\n+/g, ' ').split(' ').slice(0, 35).join(' ') + '…';
      }

      function cardHTML(post, idx, fullWidth) {
        const actionBtns = `
      <button onclick="event.stopPropagation();editPost('${post.id}')"
        style="background:none;border:1px solid var(--border);color:var(--muted);padding:4px 10px;
               font-family:'JetBrains Mono',monospace;font-size:8px;cursor:pointer;transition:all 0.2s;"
        onmouseover="this.style.borderColor='var(--text)';this.style.color='var(--text)'"
        onmouseout="this.style.borderColor='var(--border)';this.style.color='var(--muted)'">EDIT</button>
      <button onclick="event.stopPropagation();deletePost('${post.id}')"
        style="background:none;border:1px solid rgba(255,80,80,0.3);color:rgba(255,80,80,0.6);
               padding:4px 10px;font-family:'JetBrains Mono',monospace;font-size:8px;cursor:pointer;
               transition:all 0.2s;"
        onmouseover="this.style.borderColor='#ff5050';this.style.color='#ff5050'"
        onmouseout="this.style.borderColor='rgba(255,80,80,0.3)';this.style.color='rgba(255,80,80,0.6)'">DELETE</button>
    `;
        return `
      <div class="blog-card ${fullWidth ? 'blog-card-featured' : ''}"
           onclick="openBlogReader('${post.id}')"
           style="${fullWidth ? 'grid-column:1/-1;display:grid;grid-template-columns:1.4fr 1fr;' : ''}">
        <div class="blog-card-img">
          <div class="blog-card-cat">${post.category}</div>
          <img src="${getImg(post)}" alt="${post.title}" loading="lazy">
        </div>
        <div style="display:flex;flex-direction:column;${fullWidth ? 'padding:40px 36px;' : ''}">
          <div class="blog-card-body" style="${fullWidth ? 'padding:0;flex:1;' : ''}">
            <div class="blog-card-meta">
              <span>${post.date}</span>
              <span>${post.readTime} MIN READ</span>
            </div>
            <div class="blog-card-title">${post.title}</div>
            <div class="blog-card-excerpt">${getExcerpt(post.body)}</div>
          </div>
          <div class="blog-card-footer">
            <span class="blog-card-author">// ${post.author}</span>
            <div style="display:flex;align-items:center;gap:8px;">
              ${actionBtns}
              <span class="blog-read-link">READ →</span>
            </div>
          </div>
        </div>
      </div>`;
      }

      grid.innerHTML = cardHTML(featured, 0, true) + rest.map((p, i) => cardHTML(p, i + 1, false)).join('');

      // Re-trigger GSAP for new cards
      if (typeof ScrollTrigger !== 'undefined') ScrollTrigger.refresh();
    }

    // ── Blog filter ───────────────────────────────────────────────────────────
    function filterBlogPosts(cat, btn) {
      currentBlogFilter = cat;
      document.querySelectorAll('#blogFilterBar .ai-tag').forEach(b => b.classList.remove('selected'));
      if (btn) btn.classList.add('selected');
      else {
        const matchBtn = document.querySelector(`#blogFilterBar [data-filter="${cat}"]`);
        if (matchBtn) matchBtn.classList.add('selected');
      }
      renderBlogGrid(cat);
    }

    // ── Editor open / close ───────────────────────────────────────────────────
    function openBlogEditor(postId) {
      const overlay = document.getElementById('blogEditorOverlay');
      overlay.classList.add('open');
      document.body.style.overflow = 'hidden';

      // Set date
      const dateInput = document.getElementById('blogDateInput');
      if (dateInput) dateInput.value = new Date().toLocaleDateString('en-IN', { day: 'numeric', month: 'long', year: 'numeric' });

      // If editing existing post
      if (postId) {
        editingPostId = postId;
        const post = blogPosts.find(p => p.id === postId);
        if (post) {
          document.getElementById('blogTitleInput').value = post.title;
          document.getElementById('blogBodyInput').value = post.body;
          document.getElementById('blogAuthorInput').value = post.author;
          // Set category
          selectedBlogCategory = post.category;
          document.querySelectorAll('#aiCategoryTags .ai-tag').forEach(t => {
            t.classList.toggle('selected', t.dataset.cat === post.category);
          });
          if (post.image) {
            blogFeaturedImageData = post.image;
            const zone = document.getElementById('imageDropZone');
            zone.classList.add('has-image');
            zone.innerHTML = `<img src="${post.image}" alt="Featured"><input type="file" id="imageFileInput" accept="image/*" onchange="handleImageUpload(event)">`;
          }
          updatePreview();
          updateWordCount();
        }
      } else {
        editingPostId = null;
        document.getElementById('blogTitleInput').value = '';
        document.getElementById('blogBodyInput').value = '';
        document.getElementById('blogAuthorInput').value = '';
        blogFeaturedImageData = null;
        document.getElementById('imageDropZone').classList.remove('has-image');
        document.getElementById('imageDropZone').innerHTML = `
      <span class="image-drop-label">CLICK TO UPLOAD</span>
      <span style="font-size:24px;opacity:0.3;">⬆</span>
      <input type="file" id="imageFileInput" accept="image/*" onchange="handleImageUpload(event)" style="position:absolute;inset:0;opacity:0;cursor:pointer;">`;
        updatePreview();
        updateWordCount();
      }

      // Animate in
      if (typeof gsap !== 'undefined') {
        gsap.from('.blog-editor-topbar', { y: -20, opacity: 0, duration: 0.5, ease: 'expo.out' });
        gsap.from('.editor-toolbar', { y: -10, opacity: 0, duration: 0.5, delay: 0.05, ease: 'expo.out' });
        gsap.from('.editor-ai-panel', { x: -20, opacity: 0, duration: 0.6, delay: 0.1, ease: 'expo.out' });
        gsap.from('.editor-canvas', { opacity: 0, duration: 0.6, delay: 0.15, ease: 'power2.out' });
        gsap.from('.editor-preview-panel', { x: 20, opacity: 0, duration: 0.6, delay: 0.1, ease: 'expo.out' });
      }
    }

    function closeBlogEditor() {
      document.getElementById('blogEditorOverlay').classList.remove('open');
      document.body.style.overflow = '';
      editingPostId = null;
    }

    // ── Category tags (editor) ────────────────────────────────────────────────
    document.addEventListener('click', e => {
      if (e.target.classList.contains('ai-tag') && e.target.closest('#aiCategoryTags')) {
        e.target.closest('#aiCategoryTags').querySelectorAll('.ai-tag').forEach(t => t.classList.remove('selected'));
        e.target.classList.add('selected');
        selectedBlogCategory = e.target.dataset.cat || 'EV';
        updatePreview();
      }
    });

    // ── Generate with AI ──────────────────────────────────────────────────────
    async function generateBlogWithAI() {
      const topic = document.getElementById('aiTopicInput').value.trim();
      const tone = document.getElementById('aiToneSelect').value;
      const length = document.getElementById('aiLengthSelect').value;
      const category = selectedBlogCategory;

      if (!topic) {
        showBlogToast('Enter a topic in the AI panel first.');
        document.getElementById('aiTopicInput').focus();
        return;
      }

      const wordTargets = { short: 400, medium: 800, long: 1400 };
      const wordTarget = wordTargets[length] || 800;

      const toneGuides = {
        editorial: 'Authoritative, journalistic, third-person. Like a feature in Autocar India or Overdrive.',
        personal: 'First-person ownership story. "I picked up my car…" Raw, honest, personal.',
        technical: 'Spec-heavy. Mention real numbers, engine codes, torque figures, suspension geometry.',
        opinion: 'Bold takes. Strong opinions. Conversational but punchy. No hedging.',
        narrative: 'Cinematic road writing. Evocative descriptions. Sensory detail. Like literary travel writing.'
      };

      const prompt = `You are a writer for DRIVAYAN, India's premier automotive storytelling platform. 
Your voice is literary, passionate, and deeply knowledgeable about Indian car culture.

Write a ${wordTarget}-word blog post about: "${topic}"

Category: ${category}
Tone: ${toneGuides[tone]}

Format your response as JSON with this exact structure:
{
  "title": "Compelling headline (max 12 words)",
  "body": "Full blog post body (${wordTarget} words). Use \\n\\n for paragraph breaks. You may use ## for H2 subheadings and ### for H3 subheadings."
}

Rules:
- Make it feel genuinely written, not AI-generated
- Reference real Indian roads, real car models, real places
- The body must be exactly the blog post text — no meta-commentary
- Respond ONLY with valid JSON, no markdown fences, no preamble`;

      // Show generating overlay
      const overlay = document.getElementById('generatingOverlay');
      const btn = document.getElementById('aiGenerateBtn');
      const dot = document.getElementById('editorStatusDot');
      const statusTxt = document.getElementById('editorStatusText');

      overlay.classList.add('show');
      btn.disabled = true;
      dot.className = 'editor-status-dot generating';
      statusTxt.textContent = 'GENERATING';

      // Step animation
      const steps = ['genStep1', 'genStep2', 'genStep3', 'genStep4'];
      let currentStep = 0;
      const stepInterval = setInterval(() => {
        if (currentStep > 0) document.getElementById(steps[currentStep - 1]).className = 'gen-step done';
        if (currentStep < steps.length) {
          document.getElementById(steps[currentStep]).className = 'gen-step current';
          currentStep++;
        }
      }, 800);

      try {
        const response = await fetch('https://api.anthropic.com/v1/messages', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            model: 'claude-sonnet-4-20250514',
            max_tokens: 2000,
            messages: [{ role: 'user', content: prompt }]
          })
        });

        if (!response.ok) throw new Error(`HTTP ${response.status}`);
        const data = await response.json();
        const raw = data.content?.map(b => b.text || '').join('').trim();
        const clean = raw.replace(/^```json\s*/i, '').replace(/```\s*$/, '').trim();
        const result = JSON.parse(clean);

        clearInterval(stepInterval);
        steps.forEach(s => document.getElementById(s).className = 'gen-step done');

        // Fill editor
        setTimeout(() => {
          document.getElementById('blogTitleInput').value = result.title || '';
          document.getElementById('blogBodyInput').value = result.body || '';
          autoResize(document.getElementById('blogTitleInput'));
          updatePreview();
          updateWordCount();
          overlay.classList.remove('show');
          btn.disabled = false;
          dot.className = 'editor-status-dot active';
          statusTxt.textContent = 'AI DRAFT READY';
          steps.forEach(s => document.getElementById(s).className = 'gen-step');
          showBlogToast('✦ AI draft generated — review and publish');
        }, 600);

      } catch (err) {
        clearInterval(stepInterval);
        overlay.classList.remove('show');
        btn.disabled = false;
        dot.className = 'editor-status-dot';
        statusTxt.textContent = 'ERROR';
        steps.forEach(s => document.getElementById(s).className = 'gen-step');
        showBlogToast('Generation failed — check connection and retry');
        console.error('Blog generation error:', err);
      }
    }

    // ── AI micro-tools ────────────────────────────────────────────────────────
    async function aiImproveTitle() {
      const currentTitle = document.getElementById('blogTitleInput').value.trim();
      if (!currentTitle) { showBlogToast('Write a title first'); return; }
      const dot = document.getElementById('editorStatusDot');
      dot.className = 'editor-status-dot generating';
      document.getElementById('editorStatusText').textContent = 'IMPROVING';
      try {
        const res = await fetch('https://api.anthropic.com/v1/messages', {
          method: 'POST', headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            model: 'claude-sonnet-4-20250514', max_tokens: 200,
            messages: [{ role: 'user', content: `Rewrite this headline for DRIVAYAN (Indian automotive blog) to be more compelling and punchy. Max 12 words. Respond with just the new headline, nothing else.\n\nCurrent: "${currentTitle}"` }]
          })
        });
        const d = await res.json();
        const improved = d.content?.map(b => b.text || '').join('').trim().replace(/^["']|["']$/g, '');
        document.getElementById('blogTitleInput').value = improved;
        updatePreview();
        dot.className = 'editor-status-dot active';
        document.getElementById('editorStatusText').textContent = 'TITLE IMPROVED';
        showBlogToast('✦ Title improved');
      } catch (e) {
        dot.className = 'editor-status-dot';
        document.getElementById('editorStatusText').textContent = 'ERROR';
      }
    }

    async function aiContinueWriting() {
      const body = document.getElementById('blogBodyInput').value.trim();
      const title = document.getElementById('blogTitleInput').value.trim();
      if (!body) { showBlogToast('Write something first'); return; }
      const dot = document.getElementById('editorStatusDot');
      dot.className = 'editor-status-dot generating';
      document.getElementById('editorStatusText').textContent = 'CONTINUING';
      try {
        const res = await fetch('https://api.anthropic.com/v1/messages', {
          method: 'POST', headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            model: 'claude-sonnet-4-20250514', max_tokens: 500,
            messages: [{ role: 'user', content: `Continue this DRIVAYAN blog post with 2 more paragraphs. Match the voice and style exactly. End naturally. Respond with just the continuation text.\n\nTitle: ${title}\n\nExisting text (last 400 chars):...${body.slice(-400)}` }]
          })
        });
        const d = await res.json();
        const continuation = d.content?.map(b => b.text || '').join('').trim();
        const ta = document.getElementById('blogBodyInput');
        ta.value = ta.value.trimEnd() + '\n\n' + continuation;
        updatePreview(); updateWordCount();
        dot.className = 'editor-status-dot active';
        document.getElementById('editorStatusText').textContent = 'CONTINUED';
        showBlogToast('✦ Writing continued');
      } catch (e) {
        dot.className = 'editor-status-dot';
        document.getElementById('editorStatusText').textContent = 'ERROR';
      }
    }

    async function aiWriteConclusion() {
      const body = document.getElementById('blogBodyInput').value.trim();
      const title = document.getElementById('blogTitleInput').value.trim();
      if (!body) { showBlogToast('Write something first'); return; }
      const dot = document.getElementById('editorStatusDot');
      dot.className = 'editor-status-dot generating';
      document.getElementById('editorStatusText').textContent = 'WRITING';
      try {
        const res = await fetch('https://api.anthropic.com/v1/messages', {
          method: 'POST', headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            model: 'claude-sonnet-4-20250514', max_tokens: 300,
            messages: [{ role: 'user', content: `Write a concluding paragraph for this DRIVAYAN blog post. Make it memorable and resonant. Just the conclusion paragraph, no heading.\n\nTitle: ${title}\n\nPost (summary): ${body.slice(0, 600)}...` }]
          })
        });
        const d = await res.json();
        const conclusion = d.content?.map(b => b.text || '').join('').trim();
        const ta = document.getElementById('blogBodyInput');
        ta.value = ta.value.trimEnd() + '\n\n' + conclusion;
        updatePreview(); updateWordCount();
        dot.className = 'editor-status-dot active';
        document.getElementById('editorStatusText').textContent = 'READY';
        showBlogToast('✦ Conclusion written');
      } catch (e) {
        dot.className = 'editor-status-dot';
        document.getElementById('editorStatusText').textContent = 'ERROR';
      }
    }

    // ── Quick prompts ─────────────────────────────────────────────────────────
    function loadQuickPrompt(btn) {
      document.getElementById('aiTopicInput').value = btn.textContent.trim();
      document.getElementById('aiTopicInput').focus();
    }

    // ── Formatting ────────────────────────────────────────────────────────────
    function formatText(type) {
      const ta = document.getElementById('blogBodyInput');
      const start = ta.selectionStart, end = ta.selectionEnd;
      const sel = ta.value.substring(start, end);
      const pre = ta.value.substring(0, start);
      const post = ta.value.substring(end);
      let insert = '';
      if (type === 'bold') insert = `**${sel || 'bold text'}**`;
      if (type === 'italic') insert = `*${sel || 'italic text'}*`;
      if (type === 'h2') insert = `\n\n## ${sel || 'Subheading'}\n\n`;
      if (type === 'h3') insert = `\n\n### ${sel || 'Section Title'}\n\n`;
      if (type === 'quote') insert = `\n\n> ${sel || 'A memorable quote or thought'}\n\n`;
      if (type === 'bullet') insert = `\n- ${sel || 'Point one'}\n- Point two\n- Point three\n`;
      ta.value = pre + insert + post;
      ta.focus();
      updatePreview(); updateWordCount();
    }

    function autoResize(el) {
      el.style.height = 'auto';
      el.style.height = el.scrollHeight + 'px';
    }

    // ── Word count / preview ─────────────────────────────────────────────────
    function updateWordCount() {
      const body = document.getElementById('blogBodyInput').value;
      const words = body.trim() ? body.trim().split(/\s+/).length : 0;
      const mins = Math.max(1, Math.ceil(words / 200));
      const wcBtn = document.getElementById('wordCountBtn');
      if (wcBtn) wcBtn.textContent = `${words.toLocaleString()} words`;
      const rt = document.getElementById('editorReadTime');
      if (rt) rt.textContent = `${mins} MIN READ`;
      const pw = document.getElementById('previewWords');
      const pr = document.getElementById('previewReadTime');
      if (pw) pw.textContent = words.toLocaleString();
      if (pr) pr.textContent = `${mins} MIN`;
    }

    function updatePreview() {
      const title = document.getElementById('blogTitleInput')?.value || '';
      const body = document.getElementById('blogBodyInput')?.value || '';
      const author = document.getElementById('blogAuthorInput')?.value || '';
      const date = document.getElementById('blogDateInput')?.value || '';
      const excerpt = body.replace(/\n+/g, ' ').split(' ').slice(0, 30).join(' ') + (body.length > 100 ? '…' : '');
      if (document.getElementById('previewTitle')) document.getElementById('previewTitle').textContent = title || 'Your headline will appear here';
      if (document.getElementById('previewExcerpt')) document.getElementById('previewExcerpt').textContent = excerpt || 'Your opening paragraph will show as the excerpt…';
      if (document.getElementById('previewCat')) document.getElementById('previewCat').textContent = selectedBlogCategory;
      if (document.getElementById('previewCatLabel')) document.getElementById('previewCatLabel').textContent = selectedBlogCategory;
      if (document.getElementById('previewAuthor')) document.getElementById('previewAuthor').textContent = author || '—';
      if (document.getElementById('previewDate')) document.getElementById('previewDate').textContent = date || '—';
    }

    // ── Image upload ──────────────────────────────────────────────────────────
    function handleImageUpload(e) {
      const file = e.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = ev => {
        blogFeaturedImageData = ev.target.result;
        const zone = document.getElementById('imageDropZone');
        zone.classList.add('has-image');
        zone.innerHTML = `<img src="${ev.target.result}" alt="Featured"><input type="file" id="imageFileInput" accept="image/*" onchange="handleImageUpload(event)" style="position:absolute;inset:0;opacity:0;cursor:pointer;">`;
        showBlogToast('Image uploaded');
      };
      reader.readAsDataURL(file);
    }

    // ── Save / Publish ────────────────────────────────────────────────────────
    function collectPostData(draft) {
      const title = document.getElementById('blogTitleInput').value.trim();
      const body = document.getElementById('blogBodyInput').value.trim();
      const author = document.getElementById('blogAuthorInput').value.trim() || 'Anonymous';
      const date = document.getElementById('blogDateInput').value;
      const words = body ? body.split(/\s+/).length : 0;
      const mins = Math.max(1, Math.ceil(words / 200));
      return {
        title, body, author, date, category: selectedBlogCategory,
        readTime: mins, wordCount: words, image: blogFeaturedImageData, draft
      };
    }

    function saveDraft() {
      const data = collectPostData(true);
      if (!data.title && !data.body) { showBlogToast('Nothing to save.'); return; }
      saveOrUpdatePost(data);
      showBlogToast('Draft saved');
    }

    function publishPost() {
      const data = collectPostData(false);
      if (!data.title) { showBlogToast('Add a title before publishing.'); return; }
      if (!data.body || data.body.split(/\s+/).length < 20) {
        showBlogToast('Write at least 20 words before publishing.'); return;
      }
      saveOrUpdatePost(data);
      closeBlogEditor();
      renderBlogGrid(currentBlogFilter);
      showBlogToast('✦ Post published to Drivayan Wire');
      setTimeout(() => document.getElementById('blog').scrollIntoView({ behavior: 'smooth' }), 300);
    }

    function saveOrUpdatePost(data) {
      if (editingPostId) {
        const idx = blogPosts.findIndex(p => p.id === editingPostId);
        if (idx >= 0) blogPosts[idx] = { ...blogPosts[idx], ...data };
        // Sync to backend
        fetch(`${API_BASE}/posts/${editingPostId}`, {
          method: 'PATCH', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(data)
        }).catch(() => { });
      } else {
        const newPost = { id: 'post_' + Date.now(), ...data };
        blogPosts.unshift(newPost);
        // Sync to backend
        fetch(`${API_BASE}/posts`, {
          method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(newPost)
        }).catch(() => { });
      }
      localStorage.setItem('drivayan_blog_posts', JSON.stringify(blogPosts));
    }

    function editPost(id) {
      openBlogEditor(id);
    }

    function deletePost(id) {
      if (!confirm('Delete this post?')) return;
      blogPosts = blogPosts.filter(p => p.id !== id);
      localStorage.setItem('drivayan_blog_posts', JSON.stringify(blogPosts));
      renderBlogGrid(currentBlogFilter);
      showBlogToast('Post deleted');
      // Sync to backend
      fetch(`${API_BASE}/posts/${id}`, { method: 'DELETE' }).catch(() => { });
    }

    // ── Blog reader ───────────────────────────────────────────────────────────
    function openBlogReader(id) {
      const post = blogPosts.find(p => p.id === id);
      if (!post) return;
      const BLOG_IMGS = {
        'EV': 'https://images.unsplash.com/photo-1620714223084-8fcacc2dbe4d?auto=format&fit=crop&q=80&w=1200',
        'REVIEW': 'https://images.unsplash.com/photo-1492144534655-ae79c964c9d7?auto=format&fit=crop&q=80&w=1200',
        'ROAD TRIP': 'https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?auto=format&fit=crop&q=80&w=1200',
        'CULTURE': 'https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&q=80&w=1200',
        'TECH': 'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?auto=format&fit=crop&q=80&w=1200',
        'OPINION': 'https://images.unsplash.com/photo-1504215680853-026ed2a45def?auto=format&fit=crop&q=80&w=1200',
        'INDUSTRY': 'https://images.unsplash.com/photo-1568605117036-5fe5e7bab0b7?auto=format&fit=crop&q=80&w=1200',
        'CLASSIC': 'https://images.unsplash.com/photo-1519641471654-76ce0107ad1b?auto=format&fit=crop&q=80&w=1200',
        'DEFAULT': 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?auto=format&fit=crop&q=80&w=1200',
      };

      document.getElementById('readerCat').textContent = post.category;
      document.getElementById('readerTitle').textContent = post.title;
      document.getElementById('readerMeta').innerHTML = `
    <span>BY ${(post.author || 'ANONYMOUS').toUpperCase()}</span>
    <span>${post.date}</span>
    <span>${post.readTime} MIN READ</span>
    <span>${post.wordCount} WORDS</span>`;
      const img = document.getElementById('readerFeaturedImg');
      img.src = post.image || BLOG_IMGS[post.category] || BLOG_IMGS['DEFAULT'];
      img.style.display = 'block';

      // Parse markdown-lite to HTML
      function parseBody(text) {
        return text
          .split(/\n\n/)
          .map(para => {
            if (para.startsWith('## ')) return `<h2>${para.slice(3)}</h2>`;
            if (para.startsWith('### ')) return `<h3>${para.slice(4)}</h3>`;
            if (para.startsWith('> ')) return `<blockquote>${para.slice(2)}</blockquote>`;
            if (para.trim().startsWith('- ')) {
              const items = para.split('\n').filter(l => l.startsWith('- ')).map(l => `<li>${l.slice(2)}</li>`).join('');
              return `<ul style="padding-left:20px;margin-bottom:16px;">${items}</ul>`;
            }
            const html = para
              .replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>')
              .replace(/\*(.+?)\*/g, '<em>$1</em>');
            return `<p>${html}</p>`;
          })
          .join('');
      }

      document.getElementById('readerBody').innerHTML = parseBody(post.body);
      document.getElementById('blogReaderOverlay').classList.add('open');
      document.body.style.overflow = 'hidden';
    }

    function closeBlogReader() {
      document.getElementById('blogReaderOverlay').classList.remove('open');
      document.body.style.overflow = '';
    }

    function handleReaderClick(e) {
      if (e.target === document.getElementById('blogReaderOverlay')) closeBlogReader();
    }

    // ── Toast ─────────────────────────────────────────────────────────────────
    function showBlogToast(msg) {
      const t = document.getElementById('blogToast');
      if (!t) return;
      t.textContent = msg;
      t.classList.add('show');
      setTimeout(() => t.classList.remove('show'), 2800);
    }

    // ── Init ──────────────────────────────────────────────────────────────────
    renderBlogGrid('ALL');

  </script>

</body>
