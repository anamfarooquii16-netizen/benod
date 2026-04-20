# benod
vdugdb 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEVORA — Crafted in Leather. Defined by Style.</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Jost:wght@200;300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --cream: #F5F0E8;
    --beige: #E8DFD0;
    --sand: #D4C4A8;
    --warm-tan: #B8956A;
    --rich-brown: #6B4C2A;
    --dark-brown: #3A2718;
    --near-black: #1A1410;
    --text-light: #8C7A65;
    --text-mid: #5C4A35;
    --white: #FDFAF5;
    --overlay: rgba(26, 20, 16, 0.45);
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Jost', sans-serif;
    background: var(--cream);
    color: var(--near-black);
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom Cursor */
  .cursor {
    width: 10px; height: 10px;
    background: var(--warm-tan);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none; z-index: 9999;
    transition: transform 0.15s ease;
    transform: translate(-50%, -50%);
  }
  .cursor-ring {
    width: 34px; height: 34px;
    border: 1px solid var(--warm-tan);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none; z-index: 9998;
    transition: transform 0.35s ease, width 0.3s, height 0.3s, opacity 0.3s;
    transform: translate(-50%, -50%);
    opacity: 0.7;
  }
  body:hover .cursor-ring { opacity: 1; }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--cream); }
  ::-webkit-scrollbar-thumb { background: var(--warm-tan); border-radius: 2px; }

  /* ── NAVBAR ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 60px;
    height: 80px;
    background: rgba(245, 240, 232, 0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(184, 149, 106, 0.15);
    transition: background 0.4s, box-shadow 0.4s;
  }
  nav.scrolled {
    background: rgba(245, 240, 232, 0.98);
    box-shadow: 0 2px 40px rgba(58, 39, 24, 0.08);
  }

  .nav-logo {
    font-family: 'Cormorant Garamond', serif;
    font-size: 26px; font-weight: 300; letter-spacing: 0.22em;
    color: var(--dark-brown); text-decoration: none;
    text-transform: uppercase;
  }
  .nav-logo span { color: var(--warm-tan); }

  .nav-menu {
    display: flex; gap: 36px; list-style: none;
    position: absolute; left: 50%; transform: translateX(-50%);
  }
  .nav-menu a {
    font-size: 11px; letter-spacing: 0.18em; text-transform: uppercase;
    color: var(--text-mid); text-decoration: none; font-weight: 400;
    position: relative; padding-bottom: 3px;
    transition: color 0.3s;
  }
  .nav-menu a::after {
    content: ''; position: absolute; bottom: 0; left: 0;
    width: 0; height: 1px; background: var(--warm-tan);
    transition: width 0.35s ease;
  }
  .nav-menu a:hover { color: var(--dark-brown); }
  .nav-menu a:hover::after { width: 100%; }

  .nav-right { display: flex; align-items: center; gap: 20px; }
  .nav-icon {
    background: none; border: none; cursor: none;
    color: var(--text-mid); font-size: 18px;
    transition: color 0.3s;
  }
  .nav-icon:hover { color: var(--warm-tan); }

  /* ── HERO ── */
  .hero {
    height: 100vh; position: relative;
    display: flex; align-items: center; justify-content: center;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute; inset: 0;
    background:
      linear-gradient(160deg, rgba(58,39,24,0.55) 0%, rgba(26,20,16,0.3) 50%, rgba(107,76,42,0.4) 100%),
      url('https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=1800&q=80') center/cover no-repeat;
    transform: scale(1.05);
    transition: transform 8s ease;
  }
  .hero:hover .hero-bg { transform: scale(1.0); }

  /* Grain overlay */
  .hero::before {
    content: ''; position: absolute; inset: 0; z-index: 1;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    opacity: 0.4; pointer-events: none;
  }

  .hero-content {
    position: relative; z-index: 2;
    text-align: center; color: var(--white);
    max-width: 800px; padding: 0 30px;
    animation: heroFadeIn 1.4s ease forwards;
  }

  @keyframes heroFadeIn {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .hero-eyebrow {
    font-size: 10px; letter-spacing: 0.35em; text-transform: uppercase;
    color: var(--sand); margin-bottom: 24px;
    font-weight: 300;
    animation: heroFadeIn 1s 0.2s both ease;
  }

  .hero-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(48px, 7vw, 88px);
    font-weight: 300; line-height: 1.1;
    letter-spacing: 0.03em;
    margin-bottom: 28px;
    animation: heroFadeIn 1s 0.4s both ease;
  }
  .hero-title em { font-style: italic; color: var(--sand); }

  .hero-sub {
    font-size: 13px; letter-spacing: 0.08em; font-weight: 300;
    color: rgba(253,250,245,0.75); margin-bottom: 52px;
    line-height: 1.9;
    animation: heroFadeIn 1s 0.6s both ease;
  }

  .btn-primary {
    display: inline-block;
    padding: 16px 52px;
    border: 1px solid rgba(253,250,245,0.6);
    color: var(--white); text-decoration: none;
    font-size: 10px; letter-spacing: 0.25em; text-transform: uppercase;
    font-weight: 400; font-family: 'Jost', sans-serif;
    transition: background 0.4s, border-color 0.4s, color 0.4s;
    cursor: none;
    animation: heroFadeIn 1s 0.8s both ease;
    position: relative; overflow: hidden;
  }
  .btn-primary::before {
    content: ''; position: absolute; inset: 0;
    background: var(--warm-tan);
    transform: translateX(-101%);
    transition: transform 0.45s cubic-bezier(0.4,0,0.2,1);
  }
  .btn-primary:hover::before { transform: translateX(0); }
  .btn-primary:hover { border-color: var(--warm-tan); }
  .btn-primary span { position: relative; z-index: 1; }

  .hero-scroll {
    position: absolute; bottom: 40px; left: 50%; transform: translateX(-50%);
    z-index: 2; display: flex; flex-direction: column; align-items: center; gap: 10px;
    color: rgba(253,250,245,0.5); font-size: 9px; letter-spacing: 0.25em; text-transform: uppercase;
    animation: heroFadeIn 1s 1.2s both ease;
  }
  .scroll-line {
    width: 1px; height: 50px; background: rgba(253,250,245,0.3);
    position: relative; overflow: hidden;
  }
  .scroll-line::after {
    content: ''; position: absolute; top: -100%; left: 0;
    width: 100%; height: 100%; background: var(--warm-tan);
    animation: scrollDrop 1.8s ease infinite;
  }
  @keyframes scrollDrop {
    0% { top: -100%; }
    100% { top: 200%; }
  }

  /* ── SECTION COMMON ── */
  section { padding: 120px 80px; }

  .section-label {
    font-size: 9px; letter-spacing: 0.35em; text-transform: uppercase;
    color: var(--warm-tan); margin-bottom: 20px; font-weight: 400;
  }

  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(36px, 5vw, 60px);
    font-weight: 300; line-height: 1.15;
    color: var(--dark-brown); letter-spacing: 0.02em;
  }
  .section-title em { font-style: italic; color: var(--warm-tan); }

  /* ── ABOUT ── */
  .about {
    background: var(--near-black);
    display: grid; grid-template-columns: 1fr 1fr; gap: 100px;
    align-items: center;
  }

  .about-image-wrap {
    position: relative; height: 580px;
  }
  .about-img {
    width: 100%; height: 100%;
    object-fit: cover;
    filter: brightness(0.9) sepia(0.15);
  }
  .about-accent {
    position: absolute; top: -20px; left: -20px;
    width: 140px; height: 140px;
    border: 1px solid rgba(184,149,106,0.3);
    pointer-events: none;
  }
  .about-accent2 {
    position: absolute; bottom: -20px; right: -20px;
    width: 100px; height: 100px;
    border: 1px solid rgba(184,149,106,0.2);
    pointer-events: none;
  }

  .about-text .section-label { color: var(--warm-tan); }
  .about-text .section-title { color: var(--beige); }

  .about-body {
    margin-top: 30px;
    font-size: 14px; line-height: 2.1; font-weight: 300;
    color: rgba(232, 223, 208, 0.65);
    letter-spacing: 0.04em;
  }

  .about-stat-row {
    display: flex; gap: 50px; margin-top: 56px;
    padding-top: 40px; border-top: 1px solid rgba(184,149,106,0.2);
  }
  .stat-item {}
  .stat-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 44px; font-weight: 300; color: var(--warm-tan);
    line-height: 1;
  }
  .stat-label {
    font-size: 10px; letter-spacing: 0.18em; text-transform: uppercase;
    color: rgba(232,223,208,0.45); margin-top: 8px; font-weight: 300;
  }

  /* ── COLLECTIONS ── */
  .collections { background: var(--white); }
  .collections-header { text-align: center; margin-bottom: 70px; }
  .collections-header .section-title { margin-top: 16px; }

  .collections-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto auto;
    gap: 20px;
  }
  .coll-card {
    position: relative; overflow: hidden; cursor: none;
    aspect-ratio: 3/4;
  }
  .coll-card:first-child { grid-column: 1; grid-row: 1 / 3; aspect-ratio: auto; }
  .coll-card:nth-child(2),
  .coll-card:nth-child(3) { grid-column: 2; }
  .coll-card:nth-child(4),
  .coll-card:nth-child(5) { grid-column: 3; }

  .coll-card img {
    width: 100%; height: 100%; object-fit: cover;
    transition: transform 0.8s cubic-bezier(0.4,0,0.2,1), filter 0.5s;
    filter: brightness(0.85) sepia(0.1);
  }
  .coll-card:hover img {
    transform: scale(1.06);
    filter: brightness(0.75) sepia(0.2);
  }

  .coll-overlay {
    position: absolute; inset: 0;
    background: linear-gradient(to top, rgba(26,20,16,0.75) 0%, transparent 60%);
    display: flex; flex-direction: column; justify-content: flex-end;
    padding: 32px;
    transition: background 0.4s;
  }
  .coll-card:hover .coll-overlay {
    background: linear-gradient(to top, rgba(26,20,16,0.85) 0%, rgba(26,20,16,0.2) 100%);
  }

  .coll-category {
    font-size: 9px; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--warm-tan); margin-bottom: 8px; font-weight: 400;
  }
  .coll-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 28px; font-weight: 300;
    color: var(--white); line-height: 1.2;
  }
  .coll-arrow {
    margin-top: 16px;
    width: 36px; height: 1px; background: var(--warm-tan);
    position: relative;
    transform: scaleX(0); transform-origin: left;
    transition: transform 0.4s 0.1s ease;
  }
  .coll-arrow::after {
    content: ''; position: absolute; right: 0; top: -3px;
    border: 3px solid transparent;
    border-left: 5px solid var(--warm-tan);
  }
  .coll-card:hover .coll-arrow { transform: scaleX(1); }

  /* ── SLIDER ── */
  .slider-section { background: var(--near-black); padding: 100px 0; }
  .slider-header { text-align: center; margin-bottom: 60px; padding: 0 80px; }
  .slider-header .section-title { color: var(--beige); }

  .slider-wrapper { position: relative; overflow: hidden; }
  .slider-track {
    display: flex; gap: 24px;
    padding: 0 80px;
    transition: transform 0.6s cubic-bezier(0.4,0,0.2,1);
  }

  .slide {
    flex: 0 0 calc(33.333% - 16px);
    position: relative; overflow: hidden;
    height: 500px; cursor: none;
  }
  .slide img {
    width: 100%; height: 100%; object-fit: cover;
    transition: transform 0.7s ease, filter 0.5s;
    filter: brightness(0.9) sepia(0.1);
  }
  .slide:hover img { transform: scale(1.04); filter: brightness(0.8) sepia(0.2); }

  .slide-label {
    position: absolute; bottom: 0; left: 0; right: 0;
    padding: 24px 28px;
    background: linear-gradient(to top, rgba(26,20,16,0.8) 0%, transparent 100%);
  }
  .slide-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 22px; font-weight: 300; color: var(--white);
  }
  .slide-tag {
    font-size: 9px; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--warm-tan); margin-top: 4px;
  }

  .slider-controls {
    display: flex; justify-content: center; gap: 16px; margin-top: 48px;
    padding: 0 80px;
  }
  .slider-btn {
    width: 52px; height: 52px;
    border: 1px solid rgba(184,149,106,0.4);
    background: transparent; cursor: none;
    color: var(--warm-tan); font-size: 18px;
    transition: background 0.3s, border-color 0.3s;
    display: flex; align-items: center; justify-content: center;
  }
  .slider-btn:hover { background: var(--warm-tan); color: var(--white); border-color: var(--warm-tan); }

  .slider-dots {
    display: flex; gap: 8px; align-items: center;
    margin-top: 28px; justify-content: center;
  }
  .dot {
    width: 24px; height: 1px; background: rgba(184,149,106,0.3);
    transition: background 0.3s, width 0.3s; cursor: none;
  }
  .dot.active { background: var(--warm-tan); width: 40px; }

  /* ── WHY US ── */
  .why { background: var(--cream); }
  .why-header { text-align: center; margin-bottom: 80px; }

  .why-grid {
    display: grid; grid-template-columns: repeat(4, 1fr); gap: 2px;
  }
  .why-card {
    background: var(--white); padding: 52px 36px;
    position: relative; overflow: hidden;
    transition: background 0.4s;
    cursor: default;
  }
  .why-card::before {
    content: ''; position: absolute; bottom: 0; left: 0;
    width: 100%; height: 3px;
    background: var(--warm-tan);
    transform: scaleX(0); transform-origin: left;
    transition: transform 0.4s ease;
  }
  .why-card:hover::before { transform: scaleX(1); }
  .why-card:hover { background: var(--beige); }

  .why-icon {
    font-size: 28px; margin-bottom: 28px;
    display: block; color: var(--warm-tan);
  }
  .why-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 22px; font-weight: 400; color: var(--dark-brown);
    margin-bottom: 16px; line-height: 1.3;
  }
  .why-desc {
    font-size: 13px; line-height: 1.9; font-weight: 300;
    color: var(--text-light); letter-spacing: 0.03em;
  }
  .why-num {
    position: absolute; top: 28px; right: 28px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 48px; font-weight: 300;
    color: rgba(184,149,106,0.12); line-height: 1;
  }

  /* ── VISION ── */
  .vision {
    background: var(--dark-brown);
    text-align: center; padding: 140px 80px;
    position: relative; overflow: hidden;
  }
  .vision::before {
    content: '"'; position: absolute;
    font-family: 'Cormorant Garamond', serif;
    font-size: 600px; font-weight: 300; line-height: 1;
    color: rgba(184,149,106,0.05);
    top: -100px; left: 50%; transform: translateX(-50%);
    pointer-events: none;
  }

  .vision-label { color: var(--warm-tan); margin-bottom: 30px; }

  .vision-quote {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(28px, 4vw, 52px);
    font-weight: 300; line-height: 1.5;
    color: var(--beige); letter-spacing: 0.03em;
    max-width: 860px; margin: 0 auto 40px;
    position: relative; z-index: 1;
  }
  .vision-quote em { font-style: italic; color: var(--warm-tan); }

  .vision-line {
    width: 60px; height: 1px; background: var(--warm-tan);
    margin: 0 auto;
  }

  /* ── FOOTER ── */
  footer {
    background: var(--near-black);
    padding: 80px 80px 40px;
    color: rgba(232,223,208,0.5);
  }

  .footer-top {
    display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 60px; margin-bottom: 60px;
    padding-bottom: 60px;
    border-bottom: 1px solid rgba(184,149,106,0.15);
  }

  .footer-brand .nav-logo { color: var(--beige); display: block; margin-bottom: 20px; }
  .footer-tagline {
    font-size: 12px; line-height: 2; font-weight: 300;
    color: rgba(232,223,208,0.45); letter-spacing: 0.05em;
    max-width: 280px;
  }

  .footer-social-label {
    font-size: 9px; letter-spacing: 0.22em; text-transform: uppercase;
    color: var(--warm-tan); margin-top: 28px; margin-bottom: 14px; font-weight: 400;
  }
  .footer-social {
    display: flex; flex-wrap: wrap; gap: 10px;
    max-width: 320px;
  }
  .social-link {
    width: 36px; height: 36px;
    border: 1px solid rgba(184,149,106,0.3);
    display: flex; align-items: center; justify-content: center;
    color: rgba(232,223,208,0.5); text-decoration: none; font-size: 14px;
    transition: background 0.3s, border-color 0.3s, color 0.3s, transform 0.2s;
    cursor: none;
    position: relative;
  }
  .social-link:hover {
    background: var(--warm-tan); border-color: var(--warm-tan);
    color: var(--white); transform: translateY(-2px);
  }
  .social-link::after {
    content: attr(title);
    position: absolute; bottom: calc(100% + 8px); left: 50%; transform: translateX(-50%);
    background: rgba(26,20,16,0.9); color: var(--beige);
    font-size: 9px; letter-spacing: 0.1em; padding: 4px 8px; white-space: nowrap;
    opacity: 0; pointer-events: none; transition: opacity 0.2s;
  }
  .social-link:hover::after { opacity: 1; }
  .footer-presented {
    text-align: center; padding: 30px 0 20px;
    border-top: 1px solid rgba(184,149,106,0.12);
    margin-bottom: 10px;
  }
  .presented-text {
    font-size: 11px; letter-spacing: 0.25em; text-transform: uppercase;
    color: rgba(232,223,208,0.3); font-weight: 300;
  }
  .presented-text em {
    font-style: normal; color: var(--warm-tan); letter-spacing: 0.3em;
    font-family: 'Cormorant Garamond', serif; font-size: 13px; font-weight: 400;
  }

  .footer-col h4 {
    font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--beige); margin-bottom: 24px; font-weight: 400;
  }
  .footer-links { list-style: none; display: flex; flex-direction: column; gap: 14px; }
  .footer-links a {
    font-size: 12px; color: rgba(232,223,208,0.45); text-decoration: none;
    font-weight: 300; letter-spacing: 0.06em;
    transition: color 0.3s; cursor: none;
  }
  .footer-links a:hover { color: var(--warm-tan); }

  .contact-item { display: flex; flex-direction: column; gap: 4px; margin-bottom: 16px; }
  .contact-label { font-size: 9px; letter-spacing: 0.2em; text-transform: uppercase; color: var(--warm-tan); }
  .contact-val { font-size: 12px; color: rgba(232,223,208,0.45); font-weight: 300; }

  .footer-bottom {
    display: flex; justify-content: space-between; align-items: center;
    font-size: 10px; letter-spacing: 0.12em; color: rgba(232,223,208,0.25);
  }

  /* ── ANIMATIONS ── */
  .reveal {
    opacity: 0; transform: translateY(40px);
    transition: opacity 0.9s ease, transform 0.9s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-delay-1 { transition-delay: 0.15s; }
  .reveal-delay-2 { transition-delay: 0.3s; }
  .reveal-delay-3 { transition-delay: 0.45s; }
  .reveal-delay-4 { transition-delay: 0.6s; }

  /* ── RESPONSIVE ── */
  @media (max-width: 1100px) {
    .about { grid-template-columns: 1fr; gap: 60px; }
    .about-image-wrap { height: 400px; }
    .collections-grid { grid-template-columns: 1fr 1fr; }
    .coll-card:first-child { grid-column: 1 / 3; grid-row: 1; aspect-ratio: 16/7; }
    .coll-card:nth-child(2), .coll-card:nth-child(3) { grid-column: auto; }
    .coll-card:nth-child(4), .coll-card:nth-child(5) { grid-column: auto; }
    .why-grid { grid-template-columns: 1fr 1fr; }
    .footer-top { grid-template-columns: 1fr 1fr; gap: 40px; }
  }

  @media (max-width: 768px) {
    nav { padding: 0 24px; }
    .nav-menu { display: none; }
    section { padding: 80px 24px; }
    .collections-grid { grid-template-columns: 1fr; }
    .coll-card:first-child { grid-column: 1; grid-row: auto; aspect-ratio: 3/4; }
    .slide { flex: 0 0 85%; }
    .slider-track { padding: 0 24px; }
    .slider-controls, .slider-header { padding: 0 24px; }
    .why-grid { grid-template-columns: 1fr; }
    .footer-top { grid-template-columns: 1fr; }
    footer { padding: 60px 24px 30px; }
    .footer-bottom { flex-direction: column; gap: 12px; text-align: center; }
    .vision { padding: 100px 24px; }
    .about { padding: 80px 24px; }
    .hamburger { display: flex; }
  }

  .hamburger {
    display: none; flex-direction: column; gap: 5px;
    background: none; border: none; cursor: none;
  }
  .hamburger span {
    width: 22px; height: 1px; background: var(--dark-brown);
    display: block; transition: all 0.3s;
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- ── NAVBAR ── -->
<nav id="navbar">
  <a href="#" class="nav-logo">NEV<span>O</span>RA</a>
  <ul class="nav-menu">
    <li><a href="#">Home</a></li>
    <li><a href="#">Jackets</a></li>
    <li><a href="#">Bags</a></li>
    <li><a href="#">Wallets</a></li>
    <li><a href="#">Belts</a></li>
    <li><a href="#">Gift Sets</a></li>
    <li><a href="#">Accessories</a></li>
    <li><a href="#">Collection</a></li>
  </ul>
  <div class="nav-right">
    <button class="nav-icon" aria-label="Search">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="11" cy="11" r="7"/><path d="M21 21l-4.35-4.35"/></svg>
    </button>
    <button class="hamburger" aria-label="Menu">
      <span></span><span></span><span></span>
    </button>
  </div>
</nav>

<!-- ── HERO ── -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-content">
    <p class="hero-eyebrow">Est. 2024 — Premium Leather Goods</p>
    <h1 class="hero-title">Crafted in Leather.<br><em>Defined by Style.</em></h1>
    <p class="hero-sub">Discover timeless leather pieces designed to elevate your everyday style.</p>
    <a href="#collections" class="btn-primary"><span>Explore Collection</span></a>
  </div>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    <span>Scroll</span>
  </div>
</section>

<!-- ── ABOUT ── -->
<section class="about" id="about">
  <div class="about-image-wrap reveal">
    <img class="about-img" src="https://images.unsplash.com/photo-1553062407-98eeb64c6a62?w=900&q=80" alt="Leather craftsmanship">
    <div class="about-accent"></div>
    <div class="about-accent2"></div>
  </div>
  <div class="about-text">
    <p class="section-label reveal">Our Story</p>
    <h2 class="section-title reveal reveal-delay-1">Where Craft<br>Meets <em>Elegance</em></h2>
    <p class="about-body reveal reveal-delay-2">
      We create timeless leather products designed for individuals who value quality, elegance, and modern style. Each piece reflects craftsmanship, durability, and aesthetic excellence — born from a passion for the art of leatherwork and a dedication to enduring beauty.
    </p>
    <div class="about-stat-row reveal reveal-delay-3">
      <div class="stat-item">
        <div class="stat-num">12+</div>
        <div class="stat-label">Years of Craft</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">40K</div>
        <div class="stat-label">Happy Clients</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">100%</div>
        <div class="stat-label">Genuine Leather</div>
      </div>
    </div>
  </div>
</section>

<!-- ── COLLECTIONS ── -->
<section class="collections" id="collections">
  <div class="collections-header">
    <p class="section-label reveal">Curated for You</p>
    <h2 class="section-title reveal reveal-delay-1">Our <em>Collections</em></h2>
  </div>
  <div class="collections-grid">
    <div class="coll-card reveal">
      <img src="https://images.unsplash.com/photo-1551028719-00167b16eac5?w=900&q=80" alt="Leather Jackets">
      <div class="coll-overlay">
        <span class="coll-category">Statement Piece</span>
        <div class="coll-name">Leather Jackets</div>
        <div class="coll-arrow"></div>
      </div>
    </div>
    <div class="coll-card reveal reveal-delay-1">
      <img src="https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=700&q=80" alt="Leather Bags">
      <div class="coll-overlay">
        <span class="coll-category">Signature</span>
        <div class="coll-name">Leather Bags</div>
        <div class="coll-arrow"></div>
      </div>
    </div>
    <div class="coll-card reveal reveal-delay-2">
      <img src="https://images.unsplash.com/photo-1627123424574-724758594e93?w=700&q=80" alt="Wallets">
      <div class="coll-overlay">
        <span class="coll-category">Everyday Essential</span>
        <div class="coll-name">Wallets</div>
        <div class="coll-arrow"></div>
      </div>
    </div>
    <div class="coll-card reveal reveal-delay-1">
      <img src="https://images.unsplash.com/photo-1624222247344-550fb60583dc?w=700&q=80" alt="Belts">
      <div class="coll-overlay">
        <span class="coll-category">Refined Detail</span>
        <div class="coll-name">Belts</div>
        <div class="coll-arrow"></div>
      </div>
    </div>
    <div class="coll-card reveal reveal-delay-2">
      <img src="https://images.unsplash.com/photo-1600721391776-b5cd0e0048f9?w=700&q=80" alt="Accessories">
      <div class="coll-overlay">
        <span class="coll-category">The Final Touch</span>
        <div class="coll-name">Accessories</div>
        <div class="coll-arrow"></div>
      </div>
    </div>
  </div>
</section>

<!-- ── SLIDER ── -->
<section class="slider-section">
  <div class="slider-header">
    <p class="section-label reveal">Featured</p>
    <h2 class="section-title reveal reveal-delay-1">Leather <em>Bags</em> Edit</h2>
  </div>
  <div class="slider-wrapper">
    <div class="slider-track" id="sliderTrack">
      <div class="slide">
        <img src="https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=800&q=80" alt="Tote Bag">
        <div class="slide-label">
          <div class="slide-name">The Nevora Tote</div>
          <div class="slide-tag">Full-Grain Leather</div>
        </div>
      </div>
      <div class="slide">
        <img src="https://images.unsplash.com/photo-1584917865442-de89df76afd3?w=800&q=80" alt="Crossbody Bag">
        <div class="slide-label">
          <div class="slide-name">Crossbody Classic</div>
          <div class="slide-tag">Pebbled Leather</div>
        </div>
      </div>
      <div class="slide">
        <img src="https://images.unsplash.com/photo-1553062407-98eeb64c6a62?w=800&q=80" alt="Shoulder Bag">
        <div class="slide-label">
          <div class="slide-name">Structured Shoulder</div>
          <div class="slide-tag">Vegetable Tanned</div>
        </div>
      </div>
      <div class="slide">
        <img src="https://images.unsplash.com/photo-1566150905458-1bf1fc113f0d?w=800&q=80" alt="Backpack">
        <div class="slide-label">
          <div class="slide-name">Heritage Backpack</div>
          <div class="slide-tag">Waxed Leather</div>
        </div>
      </div>
      <div class="slide">
        <img src="https://images.unsplash.com/photo-1590874103328-eac38a683ce7?w=800&q=80" alt="Clutch">
        <div class="slide-label">
          <div class="slide-name">Evening Clutch</div>
          <div class="slide-tag">Nappa Leather</div>
        </div>
      </div>
    </div>
  </div>
  <div class="slider-controls">
    <button class="slider-btn" id="prevBtn" aria-label="Previous">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M15 18l-6-6 6-6"/></svg>
    </button>
    <button class="slider-btn" id="nextBtn" aria-label="Next">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M9 18l6-6-6-6"/></svg>
    </button>
  </div>
  <div class="slider-dots" id="sliderDots"></div>
</section>

<!-- ── WHY US ── -->
<section class="why">
  <div class="why-header">
    <p class="section-label reveal">Our Promise</p>
    <h2 class="section-title reveal reveal-delay-1">Why Choose <em>Nevora</em></h2>
  </div>
  <div class="why-grid">
    <div class="why-card reveal">
      <span class="why-num">01</span>
      <span class="why-icon">◈</span>
      <h3 class="why-title">Premium Quality Leather</h3>
      <p class="why-desc">Sourced from the world's finest tanneries, every hide is selected for its texture, grain, and longevity.</p>
    </div>
    <div class="why-card reveal reveal-delay-1">
      <span class="why-num">02</span>
      <span class="why-icon">◉</span>
      <h3 class="why-title">Minimal & Modern Design</h3>
      <p class="why-desc">Clean silhouettes and understated elegance — our designs are built to transcend trends and endure seasons.</p>
    </div>
    <div class="why-card reveal reveal-delay-2">
      <span class="why-num">03</span>
      <span class="why-icon">◈</span>
      <h3 class="why-title">Durable Craftsmanship</h3>
      <p class="why-desc">Hand-stitched and carefully constructed, our pieces are made to grow more beautiful with time and use.</p>
    </div>
    <div class="why-card reveal reveal-delay-3">
      <span class="why-num">04</span>
      <span class="why-icon">◎</span>
      <h3 class="why-title">Attention to Detail</h3>
      <p class="why-desc">From edge finishing to hardware selection — every element is considered, refined, and perfectly executed.</p>
    </div>
  </div>
</section>

<!-- ── VISION ── -->
<section class="vision">
  <p class="section-label vision-label reveal">Brand Vision</p>
  <blockquote class="vision-quote reveal reveal-delay-1">
    "To become a globally recognized lifestyle brand known for <em>innovative, sustainable,</em> and emotionally engaging leather products."
  </blockquote>
  <div class="vision-line reveal reveal-delay-2"></div>
</section>

<!-- ── FOOTER ── -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <a href="#" class="nav-logo">NEV<span style="color:var(--warm-tan)">O</span>RA</a>
      <p class="footer-tagline">Crafted with intention. Worn with purpose. Timeless leather for the discerning individual.</p>
      <div class="footer-social-label">Follow Us</div>
      <div class="footer-social">
        <a href="https://www.facebook.com/profile.php?id=61575481410849" target="_blank" class="social-link" aria-label="Facebook" title="Facebook">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M18 2h-3a5 5 0 00-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 011-1h3z"/></svg>
        </a>
        <a href="https://www.youtube.com/@AnamFarooquii" target="_blank" class="social-link" aria-label="YouTube" title="YouTube">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M22.54 6.42a2.78 2.78 0 00-1.95-1.96C18.88 4 12 4 12 4s-6.88 0-8.59.46A2.78 2.78 0 001.46 6.42 29 29 0 001 12a29 29 0 00.46 5.58 2.78 2.78 0 001.95 1.96C5.12 20 12 20 12 20s6.88 0 8.59-.46a2.78 2.78 0 001.95-1.96A29 29 0 0023 12a29 29 0 00-.46-5.58z"/><polygon points="9.75 15.02 15.5 12 9.75 8.98 9.75 15.02" stroke="currentColor" stroke-width="1.5"/></svg>
        </a>
        <a href="https://www.instagram.com/anamfarooquii16/" target="_blank" class="social-link" aria-label="Instagram" title="Instagram">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor" stroke="none"/></svg>
        </a>
        <a href="https://www.tiktok.com/@anamfarooquii" target="_blank" class="social-link" aria-label="TikTok" title="TikTok">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M9 12a4 4 0 1 0 4 4V4a5 5 0 0 0 5 5"/></svg>
        </a>
        <a href="https://www.threads.com/@anamfarooquii16" target="_blank" class="social-link" aria-label="Threads" title="Threads">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 4c1.5 0 2.7.5 3.6 1.4.9.9 1.4 2.1 1.4 3.6 0 1.2-.3 2.2-.9 3-.5.7-1.3 1.2-2.2 1.4.1.4.1.8.1 1.1 0 1.1-.9 2-2 2s-2-.9-2-2c0-.3 0-.6.1-.9-1.5-.3-2.6-1.5-2.6-3.1 0-1.7 1.4-3.1 3.1-3.1.4 0 .8.1 1.1.2-.1-.3-.1-.6-.1-.9 0-1.7 1.4-3 3.1-3"/></svg>
        </a>
        <a href="https://x.com/AnamFarooquii16" target="_blank" class="social-link" aria-label="X / Twitter" title="X">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.748l7.73-8.835L1.254 2.25H8.08l4.261 5.635zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        </a>
        <a href="https://www.pinterest.com/anamfarooquii/" target="_blank" class="social-link" aria-label="Pinterest" title="Pinterest">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2C6.48 2 2 6.48 2 12c0 4.24 2.65 7.86 6.39 9.29-.09-.78-.17-1.98.04-2.83.18-.77 1.22-5.16 1.22-5.16s-.31-.62-.31-1.54c0-1.45.84-2.53 1.88-2.53.89 0 1.32.67 1.32 1.47 0 .9-.57 2.24-.87 3.48-.25 1.04.52 1.88 1.54 1.88 1.85 0 3.1-2.37 3.1-5.17 0-2.14-1.45-3.63-3.52-3.63-2.4 0-3.8 1.8-3.8 3.65 0 .72.28 1.5.62 1.92.07.08.08.16.06.24l-.23.94c-.04.15-.13.18-.29.11-1.08-.5-1.75-2.09-1.75-3.36 0-2.73 1.99-5.24 5.73-5.24 3.01 0 5.34 2.14 5.34 5.01 0 2.99-1.89 5.39-4.5 5.39-.88 0-1.7-.46-1.99-1l-.54 2.02c-.19.75-.71 1.68-1.06 2.25.8.25 1.64.38 2.51.38 5.52 0 10-4.48 10-10S17.52 2 12 2z"/></svg>
        </a>
        <a href="https://www.linkedin.com/in/anam-farooquii-a8140a3bb/" target="_blank" class="social-link" aria-label="LinkedIn" title="LinkedIn">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        </a>
        <a href="https://t.me/anamfarooquii" target="_blank" class="social-link" aria-label="Telegram" title="Telegram">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M21.198 2.433a2.242 2.242 0 00-1.022.215l-16.5 7.5a2.25 2.25 0 00.126 4.17l3.528 1.17 1.544 5.144a1.5 1.5 0 002.569.534l2.06-2.31 4.018 2.96a2.25 2.25 0 003.426-1.536l2.25-15a2.25 2.25 0 00-2.999-2.847z"/></svg>
        </a>
        <a href="https://discord.com/channels/@me" target="_blank" class="social-link" aria-label="Discord" title="Discord">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20.317 4.37a19.791 19.791 0 00-4.885-1.515.074.074 0 00-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 00-5.487 0 12.64 12.64 0 00-.617-1.25.077.077 0 00-.079-.037A19.736 19.736 0 003.677 4.37a.07.07 0 00-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 00.031.057 19.9 19.9 0 005.993 3.03.078.078 0 00.084-.028c.462-.63.874-1.295 1.226-1.994a.076.076 0 00-.041-.106 13.107 13.107 0 01-1.872-.892.077.077 0 01-.008-.128 10.2 10.2 0 00.372-.292.074.074 0 01.077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 01.078.01c.12.098.246.198.373.292a.077.077 0 01-.006.127 12.299 12.299 0 01-1.873.892.077.077 0 00-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 00.084.028 19.839 19.839 0 006.002-3.03.077.077 0 00.032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 00-.031-.03z"/></svg>
        </a>
        <a href="https://www.snapchat.com/add/anamfarooquii?share_id=n2KgYsnHz6o&locale=en-US" target="_blank" class="social-link" aria-label="Snapchat" title="Snapchat">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2C8 2 5 5 5 9v1c-.5.1-1 .3-1.5.7-.3.3-.5.7-.5 1.1 0 .6.4 1.1 1 1.3-.5.7-.9 1.5-1 2.4-.1.6.3 1.1.8 1.3l.2.1c.5.2 1.1.4 1.6.5.3.5.7.9 1.2 1.1.7.3 1.4.4 2.1.4.3.4.7.7 1.1.7s.8-.3 1.1-.7c.7 0 1.4-.1 2.1-.4.5-.2.9-.6 1.2-1.1.5-.1 1.1-.3 1.6-.5l.2-.1c.5-.2.9-.7.8-1.3-.1-.9-.5-1.7-1-2.4.6-.2 1-.7 1-1.3 0-.4-.2-.8-.5-1.1-.5-.4-1-.6-1.5-.7V9c0-4-3-7-7-7z"/></svg>
        </a>
      </div>
    </div>

    <div class="footer-col">
      <h4>Collections</h4>
      <ul class="footer-links">
        <li><a href="#">Leather Jackets</a></li>
        <li><a href="#">Leather Bags</a></li>
        <li><a href="#">Wallets</a></li>
        <li><a href="#">Belts</a></li>
        <li><a href="#">Gift Sets</a></li>
        <li><a href="#">Accessories</a></li>
      </ul>
    </div>

    <div class="footer-col">
      <h4>Company</h4>
      <ul class="footer-links">
        <li><a href="#">Our Story</a></li>
        <li><a href="#">Craftsmanship</a></li>
        <li><a href="#">Sustainability</a></li>
        <li><a href="#">Careers</a></li>
        <li><a href="#">Press</a></li>
      </ul>
    </div>

    <div class="footer-col">
      <h4>Contact</h4>
      <div class="contact-item">
        <span class="contact-label">Email</span>
        <span class="contact-val"><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="49212c25252609272c3f263b28672a2624">[email&#160;protected]</a></span>
      </div>
      <div class="contact-item">
        <span class="contact-label">Phone</span>
        <span class="contact-val">+1 (800) 638-6720</span>
      </div>
      <div class="contact-item">
        <span class="contact-label">Studio</span>
        <span class="contact-val">New York, NY 10001</span>
      </div>
    </div>
  </div>

  <div class="footer-presented">
    <span class="presented-text">Presented by <em>AnaEVORA</em></span>
  </div>
  <div class="footer-bottom">
    <span>© 2024 Nevora. All rights reserved.</span>
    <span>Privacy Policy &nbsp;·&nbsp; Terms of Service &nbsp;·&nbsp; Care Guide</span>
  </div>
</footer>

<script data-cfasync="false" src="/cdn-cgi/scripts/5c5dd728/cloudflare-static/email-decode.min.js"></script><script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const cursorRing = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animCursor() {
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    cursorRing.style.left = rx + 'px'; cursorRing.style.top = ry + 'px';
    requestAnimationFrame(animCursor);
  }
  animCursor();
  document.querySelectorAll('a, button, .coll-card, .slide').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursorRing.style.width = '52px'; cursorRing.style.height = '52px';
      cursorRing.style.borderColor = 'var(--warm-tan)';
    });
    el.addEventListener('mouseleave', () => {
      cursorRing.style.width = '34px'; cursorRing.style.height = '34px';
    });
  });

  // Navbar scroll
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 60);
  });

  // Reveal animations
  const reveals = document.querySelectorAll('.reveal');
  const revealObs = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
  }, { threshold: 0.15 });
  reveals.forEach(el => revealObs.observe(el));

  // Slider
  const track = document.getElementById('sliderTrack');
  const slides = track.querySelectorAll('.slide');
  const dotsContainer = document.getElementById('sliderDots');
  let current = 0;
  const visibleCount = window.innerWidth < 768 ? 1 : 3;

  slides.forEach((_, i) => {
    const dot = document.createElement('div');
    dot.classList.add('dot');
    if (i === 0) dot.classList.add('active');
    dot.addEventListener('click', () => goTo(i));
    dotsContainer.appendChild(dot);
  });

  function goTo(n) {
    const total = slides.length;
    current = ((n % total) + total) % total;
    const slideWidth = slides[0].offsetWidth + 24;
    track.style.transform = `translateX(-${current * slideWidth}px)`;
    document.querySelectorAll('.dot').forEach((d, i) => d.classList.toggle('active', i === current));
  }

  document.getElementById('prevBtn').addEventListener('click', () => goTo(current - 1));
  document.getElementById('nextBtn').addEventListener('click', () => goTo(current + 1));

  // Auto-slide
  let autoSlide = setInterval(() => goTo(current + 1), 4000);
  track.addEventListener('mouse
