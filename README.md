<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday, Yash Sir 🎂</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy: #080E1F;
    --navy2: #0D1629;
    --cyan: #4FD1C5;
    --cyan-dim: #2A7A74;
    --silver: #C8D6E5;
    --white: #F0F6FF;
    --gold: #E2B96A;
    --gold-dim: #7A5C20;
    --muted: #5A6A80;
  }

  html, body {
    min-height: 100%;
    background: var(--navy);
    font-family: 'Inter', sans-serif;
    overflow-x: hidden;
    color: var(--white);
  }

  canvas#particles { position: fixed; inset: 0; pointer-events: none; z-index: 0; }
  canvas#confetti-canvas { position: fixed; inset: 0; pointer-events: none; z-index: 999; }
  canvas#fireworks-canvas { position: fixed; inset: 0; pointer-events: none; z-index: 998; }

  /* BALLOONS */
  .balloon-container { position: fixed; inset: 0; pointer-events: none; z-index: 2; overflow: hidden; }
  .balloon {
    position: absolute;
    bottom: -120px;
    font-size: 40px;
    animation: floatUp linear infinite;
    opacity: 0;
    filter: drop-shadow(0 4px 12px rgba(0,0,0,0.4));
    cursor: default;
    pointer-events: all;
  }
  .balloon:hover { animation-play-state: paused; transform: scale(1.3) rotate(10deg); filter: drop-shadow(0 0 18px rgba(79,209,197,0.7)); }
  @keyframes floatUp {
    0%   { opacity: 0; transform: translateX(0) rotate(-5deg); bottom: -120px; }
    5%   { opacity: 1; }
    50%  { transform: translateX(30px) rotate(5deg); }
    100% { opacity: 0; bottom: 110%; transform: translateX(-20px) rotate(-8deg); }
  }

  /* GATE */
  #gate {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 2.5rem 1.5rem;
    text-align: center;
    position: relative;
    z-index: 10;
  }

  .badge {
    display: inline-block;
    font-size: 10.5px;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--cyan);
    border: 1px solid var(--cyan-dim);
    padding: 5px 18px;
    border-radius: 999px;
    margin-bottom: 2.8rem;
    opacity: 0;
    animation: riseIn 0.9s ease 0.4s forwards;
  }

  .gate-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(30px, 9vw, 52px);
    font-weight: 700;
    color: var(--white);
    line-height: 1.2;
    margin-bottom: 1.2rem;
    opacity: 0;
    animation: riseIn 0.9s ease 0.7s forwards;
  }
  .gate-title span { color: var(--gold); font-style: italic; }

  .gate-body {
    font-size: 14.5px;
    color: var(--muted);
    line-height: 2;
    max-width: 300px;
    margin-bottom: 2.8rem;
    opacity: 0;
    animation: riseIn 0.9s ease 1s forwards;
  }
  .gate-body strong { color: var(--silver); font-weight: 500; }

  .ring-wrap {
    width: 110px; height: 110px;
    display: flex; align-items: center; justify-content: center;
    position: relative;
    margin: 0 auto 2.2rem;
    opacity: 0;
    animation: riseIn 0.9s ease 1.2s forwards;
  }
  .ring-svg { position: absolute; width: 110px; height: 110px; }
  .ring-progress {
    stroke-dasharray: 314;
    stroke-dashoffset: 314;
    transform-origin: center;
    transform: rotate(-90deg);
    animation: ringFill 3s ease 2s forwards;
  }
  @keyframes ringFill { to { stroke-dashoffset: 0; } }
  #cdown {
    font-family: 'Cormorant Garamond', serif;
    font-size: 52px;
    font-weight: 700;
    color: var(--gold);
    line-height: 1;
    transition: all 0.2s cubic-bezier(.34,1.56,.64,1);
    position: relative;
    z-index: 2;
  }

  #enter-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: transparent;
    color: var(--white);
    border: 1.5px solid var(--cyan);
    border-radius: 999px;
    padding: 0.9rem 2.4rem;
    font-family: 'Inter', sans-serif;
    font-size: 15px;
    font-weight: 500;
    cursor: pointer;
    letter-spacing: 0.04em;
    opacity: 0;
    animation: riseIn 0.9s ease 1.5s forwards, pulse-border 2.5s ease 2.5s infinite;
    transition: background 0.2s, transform 0.15s;
  }
  #enter-btn:active { transform: scale(0.96); }
  #enter-btn:hover { background: rgba(79,209,197,0.08); }
  @keyframes pulse-border {
    0%,100% { box-shadow: 0 0 0 0 rgba(79,209,197,0); }
    50% { box-shadow: 0 0 0 8px rgba(79,209,197,0.2); }
  }

  @keyframes riseIn {
    from { opacity: 0; transform: translateY(18px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* MAIN */
  #main { display: none; position: relative; z-index: 1; padding: 0 0 5rem; }

  /* HERO */
  .hero {
    min-height: 60vh;
    background: linear-gradient(180deg, var(--navy2) 0%, var(--navy) 100%);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 4rem 1.5rem 3rem;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    width: 420px; height: 420px;
    background: radial-gradient(circle, rgba(79,209,197,0.09) 0%, transparent 70%);
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    pointer-events: none;
    animation: pulse-glow 4s ease-in-out infinite;
  }
  @keyframes pulse-glow {
    0%,100% { transform: translate(-50%,-50%) scale(1); opacity: 1; }
    50% { transform: translate(-50%,-50%) scale(1.15); opacity: 0.6; }
  }

  .hero-tag {
    font-size: 10px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--cyan);
    margin-bottom: 1.4rem;
  }

  .hero-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(38px, 11vw, 66px);
    font-weight: 700;
    color: var(--white);
    line-height: 1.1;
    margin-bottom: 0.6rem;
  }
  .hero-title span { color: var(--gold); font-style: italic; }

  .hero-sub {
    font-family: 'Cormorant Garamond', serif;
    font-size: 18px;
    font-style: italic;
    color: var(--silver);
    margin-top: 0.4rem;
  }

  /* TWIST QUOTE — hero quotes with dramatic styling */
  .twist-quote {
    margin-top: 2.5rem;
    max-width: 340px;
    text-align: center;
    position: relative;
  }
  .twist-quote .tq-line {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(17px, 5vw, 22px);
    font-weight: 600;
    font-style: italic;
    color: var(--gold);
    line-height: 1.55;
    display: block;
    opacity: 0;
    transform: translateY(14px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .twist-quote .tq-line.show { opacity: 1; transform: translateY(0); }
  .twist-quote .tq-sep {
    display: block;
    width: 40px; height: 1px;
    background: rgba(226,185,106,0.4);
    margin: 0.85rem auto;
    opacity: 0;
    transition: opacity 0.7s ease 0.3s;
  }
  .twist-quote .tq-sep.show { opacity: 1; }
  .twist-quote .tq-sub {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--cyan);
    opacity: 0;
    transition: opacity 0.7s ease 0.5s;
  }
  .twist-quote .tq-sub.show { opacity: 1; }

  /* typewriter */
  .typewriter-wrap {
    margin-top: 2.8rem;
    background: rgba(79,209,197,0.05);
    border: 1px solid rgba(79,209,197,0.18);
    border-radius: 12px;
    padding: 1.1rem 1.5rem;
    max-width: 320px;
  }
  .typewriter-label {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--cyan-dim);
    margin-bottom: 0.5rem;
  }
  #typewriter-text {
    font-family: 'Cormorant Garamond', serif;
    font-size: 16px;
    font-style: italic;
    color: var(--cyan);
    line-height: 1.7;
    min-height: 50px;
  }
  .cursor {
    display: inline-block;
    width: 2px; height: 1em;
    background: var(--cyan);
    margin-left: 2px;
    vertical-align: text-bottom;
    animation: blink 0.75s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* DIVIDER */
  .divider {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 0 1.5rem;
    margin: 2.5rem 0;
  }
  .divider-line { flex: 1; height: 1px; background: rgba(79,209,197,0.12); }
  .divider-icon { color: var(--gold); font-size: 18px; flex-shrink: 0; }

  /* CARDS */
  .section { padding: 0 1.2rem; }
  .card {
    background: rgba(13,22,41,0.9);
    border: 1px solid rgba(79,209,197,0.1);
    border-radius: 18px;
    padding: 1.8rem 1.5rem;
    margin-bottom: 1.2rem;
    position: relative;
    overflow: hidden;
  }
  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 100%;
    background: linear-gradient(180deg, var(--cyan), var(--gold));
    border-radius: 3px 0 0 3px;
  }
  .card-num {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--cyan);
    margin-bottom: 0.7rem;
    opacity: 0.7;
  }
  .card p {
    font-size: 14.5px;
    color: var(--silver);
    line-height: 1.9;
    margin-bottom: 0.85rem;
  }
  .card p:last-child { margin-bottom: 0; }
  .card em { color: var(--cyan); font-style: normal; font-weight: 500; }
  .card strong { color: var(--white); font-weight: 500; }

  .pull-quote {
    font-family: 'Cormorant Garamond', serif;
    font-size: 18px;
    font-style: italic;
    font-weight: 600;
    color: var(--gold);
    line-height: 1.55;
    text-align: center;
    padding: 1.1rem 0.5rem;
    border-top: 1px solid rgba(226,185,106,0.15);
    border-bottom: 1px solid rgba(226,185,106,0.15);
    margin: 1rem 0;
  }

  /* SIGNATURE QUOTE BLOCKS */
  .sig-quote {
    margin: 0 1.2rem 1.2rem;
    background: linear-gradient(135deg, rgba(226,185,106,0.07) 0%, rgba(79,209,197,0.05) 100%);
    border: 1px solid rgba(226,185,106,0.25);
    border-radius: 18px;
    padding: 2.2rem 1.8rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .sig-quote::after {
    content: '"';
    font-family: 'Cormorant Garamond', serif;
    font-size: 120px;
    color: rgba(226,185,106,0.06);
    position: absolute;
    top: -10px; left: 10px;
    line-height: 1;
    pointer-events: none;
  }
  .sig-quote .sq-num {
    font-size: 10px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1rem;
    opacity: 0.7;
  }
  .sig-quote .sq-text {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(18px, 5.5vw, 24px);
    font-weight: 700;
    font-style: italic;
    color: var(--white);
    line-height: 1.45;
    margin-bottom: 0.7rem;
  }
  .sig-quote .sq-text span { color: var(--gold); }
  .sig-quote .sq-sub {
    font-size: 12.5px;
    color: var(--muted);
    line-height: 1.7;
  }

  /* LEGACY BANNER */
  .legacy-banner {
    margin: 0 1.2rem 1.2rem;
    background: linear-gradient(135deg, rgba(79,209,197,0.08), rgba(226,185,106,0.06));
    border: 1px solid rgba(226,185,106,0.2);
    border-radius: 18px;
    padding: 2rem 1.5rem;
    text-align: center;
  }
  .legacy-banner .lbl {
    font-size: 10.5px;
    letter-spacing: 0.24em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.8rem;
  }
  .legacy-banner .big {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(22px, 6vw, 30px);
    font-weight: 700;
    color: var(--white);
    line-height: 1.3;
  }
  .legacy-banner .big span { color: var(--cyan); font-style: italic; }

  /* WISH BLOCK */
  .wish-block {
    margin: 0 1.2rem 1.2rem;
    text-align: center;
    background: rgba(13,22,41,0.85);
    border: 1px solid rgba(79,209,197,0.1);
    border-radius: 18px;
    padding: 2rem 1.5rem;
  }
  .wish-block p { font-size: 14.5px; color: var(--silver); line-height: 1.9; margin-bottom: 0.7rem; }
  .wish-block p:last-child { margin-bottom: 0; }
  .wish-block strong { color: var(--white); font-weight: 500; }

  /* SIGN OFF */
  .sign-off { text-align: center; padding: 2rem 1.5rem 1rem; }
  .sign-off p { font-size: 13.5px; color: var(--muted); line-height: 1.8; }
  .sign-off .name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 22px;
    font-weight: 700;
    font-style: italic;
    color: var(--white);
    margin-top: 0.5rem;
  }
  .footer-icons { text-align: center; font-size: 26px; letter-spacing: 10px; margin-top: 2rem; }

  /* reveal */
  .rv { opacity: 0; transform: translateY(22px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .rv.on { opacity: 1; transform: translateY(0); }

  /* cracker burst particle */
  .burst-dot {
    position: fixed;
    width: 8px; height: 8px;
    border-radius: 50%;
    pointer-events: none;
    z-index: 997;
    animation: burst-fly 1.2s ease-out forwards;
  }
  @keyframes burst-fly {
    0%   { opacity: 1; transform: translate(0,0) scale(1); }
    100% { opacity: 0; transform: translate(var(--bx), var(--by)) scale(0.3); }
  }
</style>
</head>
<body>

<canvas id="particles"></canvas>
<canvas id="fireworks-canvas"></canvas>
<canvas id="confetti-canvas"></canvas>
<div class="balloon-container" id="balloonBox"></div>

<!-- GATE SCREEN -->
<div id="gate">
  <div class="badge">✦ From Your Entire Team — With Love ✦</div>
  <h1 class="gate-title">Before you<br>read <span>this...</span></h1>
  <p class="gate-body">
    This isn't from one person.<br>
    <strong>This is from all of us — your team.</strong><br>
    Every word here carries every one of us.<br><br>
    Please take a moment. 🙏
  </p>

  <div class="ring-wrap">
    <svg class="ring-svg" viewBox="0 0 110 110">
      <circle cx="55" cy="55" r="50" fill="none" stroke="rgba(79,209,197,0.1)" stroke-width="2"/>
      <circle cx="55" cy="55" r="50" class="ring-progress" fill="none" stroke="url(#ringGrad)" stroke-width="2" stroke-linecap="round"/>
      <defs>
        <linearGradient id="ringGrad" x1="0" y1="0" x2="1" y2="1">
          <stop offset="0%" stop-color="#4FD1C5"/>
          <stop offset="100%" stop-color="#E2B96A"/>
        </linearGradient>
      </defs>
    </svg>
    <span id="cdown">3</span>
  </div>

  <button id="enter-btn" onclick="beginCountdown()">
    🎂 Open the Message 🎂
  </button>
</div>

<!-- MAIN SCREEN -->
<div id="main">
  <!-- HERO -->
  <div class="hero rv">
    <p class="hero-tag">✦ From All of Us — Your Entire Team ✦</p>
    <h1 class="hero-title">Happy Birthday,<br><span>Yash Sir.</span></h1>
    <p class="hero-sub">🎂 The mentor. The vision. The legacy. 🌟</p>

    <div class="typewriter-wrap">
      <p class="typewriter-label">✦ Straight from our hearts</p>
      <div id="typewriter-text"><span class="cursor"></span></div>
    </div>
  </div>

  <!-- SIGNATURE QUOTE 1 -->
  <div class="divider rv">
    <div class="divider-line"></div><div class="divider-icon">✦</div><div class="divider-line"></div>
  </div>

  <div class="sig-quote rv">
    <p class="sq-num">✦ I — What We Know About You ✦</p>
    <p class="sq-text">
      Some people <span>teach lessons.</span><br>
      Rare people <span>leave a legacy.</span><br>
      Thank you for being one of them.
    </p>
    <p class="sq-sub">🙏 — From your entire team, with gratitude 🌷</p>
  </div>

  <!-- SECTION 1 -->
  <div class="section">
    <div class="card rv">
      <p class="card-num">01 — The Kind of Leader You Are</p>
      <p>
        There are people who manage teams.<br>
        And then there are people who <em>quietly raise the ceiling</em> for everyone around them — not by demanding more, but by <strong>showing what more actually looks like.</strong>
      </p>
      <div class="pull-quote">
        "You didn't just give us direction.<br>You gave all of us a reason to aim higher."
      </div>
      <p>
        Sir, you belong to the second kind. The rare kind.<br>
        And we — all of us on this team — are lucky to work beside you.
      </p>
    </div>

    <div class="card rv">
      <p class="card-num">02 — What a True Mentor Does</p>
      <p>
        Most people teach you <em>what to do.</em><br>
        A true mentor teaches you <strong>who to become.</strong>
      </p>
      <p>
        Without ever saying it out loud, you've shown each one of us:<br>
        how to handle pressure with grace,<br>
        how to lead without losing warmth,<br>
        and how to carry responsibility<br>
        like it's a <em>privilege — not a burden.</em>
      </p>
      <p>
        That kind of mentorship doesn't live in meetings.<br>
        It lives in all of us. <strong>Every single day.</strong>
      </p>
    </div>
  </div>

  <!-- LEGACY BANNER -->
  <div class="legacy-banner rv">
    <p class="lbl">✦ The Truth About You ✦</p>
    <p class="big">Not every career has a<br><span>Yash Sir moment.</span><br>Ours does. And we know<br>how lucky that makes us.</p>
  </div>

  <!-- SIGNATURE QUOTE 2 -->
  <div class="divider rv">
    <div class="divider-line"></div><div class="divider-icon">🎂</div><div class="divider-line"></div>
  </div>

  <div class="sig-quote rv">
    <p class="sq-num">✦ II — What Changed For All of Us ✦</p>
    <p class="sq-text">
      Not every mentor<br>changes a career.<br>
      Some change <span>the way we see ourselves.</span>
    </p>
    <p class="sq-sub">
      You did both, Sir.<br>
      <strong>Happy Birthday. 🎂✨</strong>
    </p>
  </div>

  <!-- SECTION 2 -->
  <div class="section">
    <div class="card rv">
      <p class="card-num">03 — The Small Things We Notice</p>
      <p>
        It's not always the big decisions that define a leader.<br>
        It's the small things —
      </p>
      <p>
        The way you <em>listen when someone's struggling.</em><br>
        The way you correct without crushing.<br>
        The way you push someone forward<br>
        and make them feel like they chose to walk themselves.
      </p>
      <p>
        <strong>That's not management. That's artistry.</strong>
      </p>
    </div>

    <div class="card rv">
      <p class="card-num">04 — A Message We Couldn't Just Type</p>
      <p>
        We could have sent a text.<br>
        But you've never given us anything less than your best —
      </p>
      <p>
        <em>so neither will we.</em>
      </p>
      <p>
        Years from now, when we're leading our own teams,<br>
        building our own paths,<br>
        we will remember the voice in our heads<br>
        that says: <strong><em>"Do it right. Do it with care."</em></strong>
      </p>
      <p>
        Sir — that voice will sound a lot like yours.
      </p>
    </div>
  </div>

  <!-- WISH BLOCK -->
  <div class="wish-block rv">
    <p>🎂 On this birthday, we wish you</p>
    <p>
      <strong>Health that matches your ambition.</strong><br>
      <strong>Joy that matches your generosity.</strong><br>
      <strong>Success that finally matches what you deserve.</strong>
    </p>
    <p style="margin-top:1rem; font-size:13px; color: var(--muted);">
      Because someone who pours this much into others<br>
      deserves the world pouring back. 🌏✨
    </p>
  </div>

  <!-- SIGN OFF -->
  <div class="sign-off rv">
    <p>
      From your team,<br>
      who watches you lead — and quietly learns.<br>
      Who works beside you — and quietly grows.
    </p>
    <p class="name">🌟 Happy Birthday, Sir. 🎂</p>
    <p style="margin-top:0.4rem; font-size:12px; color: var(--muted);">With respect, admiration & gratitude — from all of us.</p>
  </div>

  <div class="footer-icons rv">🎂 ✨ 🌟 🎈 🎉</div>
</div>

<script>
// ── PARTICLES ──
const pc = document.getElementById('particles');
const px = pc.getContext('2d');
pc.width = innerWidth; pc.height = innerHeight;
window.addEventListener('resize', () => { pc.width = innerWidth; pc.height = innerHeight; });
const dots = Array.from({length: 50}, () => ({
  x: Math.random() * pc.width, y: Math.random() * pc.height,
  r: 0.8 + Math.random() * 1.8, op: 0.1 + Math.random() * 0.35,
  sp: 0.15 + Math.random() * 0.3, dir: Math.random() * Math.PI * 2
}));
function drawParticles() {
  px.clearRect(0, 0, pc.width, pc.height);
  for (const d of dots) {
    d.x += Math.cos(d.dir) * d.sp; d.y += Math.sin(d.dir) * d.sp;
    if (d.x < -5) d.x = pc.width + 5; if (d.x > pc.width + 5) d.x = -5;
    if (d.y < -5) d.y = pc.height + 5; if (d.y > pc.height + 5) d.y = -5;
    px.beginPath(); px.arc(d.x, d.y, d.r, 0, Math.PI * 2);
    px.fillStyle = `rgba(79,209,197,${d.op})`; px.fill();
  }
  requestAnimationFrame(drawParticles);
}
drawParticles();

// ── CONFETTI ──
const cc = document.getElementById('confetti-canvas');
const cx = cc.getContext('2d');
cc.width = innerWidth; cc.height = innerHeight;
window.addEventListener('resize', () => { cc.width = innerWidth; cc.height = innerHeight; });
let flakes = [], confRunning = false;
const cols = ['#4FD1C5','#E2B96A','#C8D6E5','#A78BFA','#F472B6','#34D399','#60A5FA','#FCD34D','#FB7185','#f97316'];

function spawnConf(n) {
  for (let i = 0; i < n; i++) {
    flakes.push({
      x: Math.random() * cc.width, y: -10 - Math.random() * 100,
      w: 6 + Math.random() * 10, h: 4 + Math.random() * 6,
      color: cols[Math.floor(Math.random() * cols.length)],
      rot: Math.random() * Math.PI * 2,
      vx: (Math.random() - 0.5) * 5, vy: 2 + Math.random() * 4,
      vr: (Math.random() - 0.5) * 0.18,
      wob: Math.random() * Math.PI * 2, wsp: 0.04 + Math.random() * 0.08,
      shape: Math.random() > 0.4 ? 'rect' : 'circle'
    });
  }
}
function animConf() {
  cx.clearRect(0, 0, cc.width, cc.height);
  flakes = flakes.filter(f => f.y < cc.height + 20);
  for (const f of flakes) {
    f.wob += f.wsp; f.x += f.vx + Math.sin(f.wob) * 1.2; f.y += f.vy; f.rot += f.vr;
    cx.save(); cx.translate(f.x, f.y); cx.rotate(f.rot);
    cx.fillStyle = f.color; cx.globalAlpha = 0.9;
    if (f.shape === 'rect') cx.fillRect(-f.w/2, -f.h/2, f.w, f.h);
    else { cx.beginPath(); cx.arc(0,0,f.w/2,0,Math.PI*2); cx.fill(); }
    cx.restore();
  }
  if (confRunning || flakes.length > 0) requestAnimationFrame(animConf);
  else cx.clearRect(0,0,cc.width,cc.height);
}
function fireConfetti() {
  confRunning = true;
  for (let i = 0; i < 10; i++) setTimeout(() => spawnConf(32), i * 160);
  setTimeout(() => confRunning = false, 6000);
  animConf();
}

// ── FIREWORKS ──
const fw = document.getElementById('fireworks-canvas');
const fwx = fw.getContext('2d');
fw.width = innerWidth; fw.height = innerHeight;
window.addEventListener('resize', () => { fw.width = innerWidth; fw.height = innerHeight; });
let rockets = [], fwRunning = false;
const fwCols = ['#FFD700','#FF6B6B','#4FD1C5','#A78BFA','#F472B6','#34D399','#FB923C','#FCD34D','#60A5FA','#E2B96A'];

function launchRocket() {
  const x = 60 + Math.random() * (fw.width - 120);
  const targetY = 80 + Math.random() * (fw.height * 0.4);
  rockets.push({
    x, y: fw.height, tx: x + (Math.random()-0.5)*80, ty: targetY,
    speed: 8 + Math.random() * 6,
    color: fwCols[Math.floor(Math.random() * fwCols.length)],
    trail: [], exploded: false, particles: [], life: 0
  });
}
function animFw() {
  fwx.fillStyle = 'rgba(8,14,31,0.18)';
  fwx.fillRect(0, 0, fw.width, fw.height);
  rockets = rockets.filter(r => r.life < 120);
  for (const r of rockets) {
    r.life++;
    if (!r.exploded) {
      const dx = r.tx - r.x, dy = r.ty - r.y;
      const dist = Math.sqrt(dx*dx + dy*dy);
      if (dist < r.speed) {
        r.exploded = true;
        // burst particles
        for (let i = 0; i < 60; i++) {
          const angle = (i / 60) * Math.PI * 2;
          const spd = 2 + Math.random() * 5;
          r.particles.push({
            x: r.x, y: r.y,
            vx: Math.cos(angle) * spd, vy: Math.sin(angle) * spd,
            color: Math.random() > 0.5 ? r.color : fwCols[Math.floor(Math.random()*fwCols.length)],
            life: 1, decay: 0.012 + Math.random() * 0.016,
            size: 1.5 + Math.random() * 2.5
          });
        }
      } else {
        const nx = dx/dist * r.speed, ny = dy/dist * r.speed;
        r.trail.push({x: r.x, y: r.y});
        if (r.trail.length > 10) r.trail.shift();
        r.x += nx; r.y += ny;
        for (let i = 0; i < r.trail.length; i++) {
          fwx.beginPath();
          fwx.arc(r.trail[i].x, r.trail[i].y, 1.5 * (i/r.trail.length), 0, Math.PI*2);
          fwx.fillStyle = `rgba(255,220,100,${i/r.trail.length * 0.7})`;
          fwx.fill();
        }
        fwx.beginPath(); fwx.arc(r.x, r.y, 2.5, 0, Math.PI*2);
        fwx.fillStyle = '#FFF'; fwx.fill();
      }
    } else {
      for (const p of r.particles) {
        p.x += p.vx; p.y += p.vy + 0.06;
        p.vx *= 0.97; p.vy *= 0.97;
        p.life -= p.decay;
        if (p.life > 0) {
          fwx.beginPath(); fwx.arc(p.x, p.y, p.size * p.life, 0, Math.PI*2);
          fwx.fillStyle = p.color; fwx.globalAlpha = p.life;
          fwx.fill(); fwx.globalAlpha = 1;
        }
      }
      r.particles = r.particles.filter(p => p.life > 0);
    }
  }
  if (fwRunning || rockets.some(r => r.life < 120)) requestAnimationFrame(animFw);
  else { fwx.clearRect(0,0,fw.width,fw.height); }
}

function startFireworks(duration) {
  fwRunning = true;
  animFw();
  let elapsed = 0;
  const interval = setInterval(() => {
    launchRocket();
    if (Math.random() > 0.5) launchRocket();
    elapsed += 400;
    if (elapsed >= duration) { clearInterval(interval); fwRunning = false; }
  }, 400);
}

// ── BALLOONS ──
const BALLOONS = ['🎈','🎈','🎈','🎈','🎈','🎉','🎊','🎁','🌟','✨'];
const BOX = document.getElementById('balloonBox');
let balloonTimer = null;
function spawnBalloon() {
  const el = document.createElement('div');
  el.className = 'balloon';
  el.textContent = BALLOONS[Math.floor(Math.random() * BALLOONS.length)];
  el.style.left = (5 + Math.random() * 90) + 'vw';
  const dur = 7 + Math.random() * 8;
  const delay = Math.random() * 2;
  el.style.animationDuration = dur + 's';
  el.style.animationDelay = delay + 's';
  el.style.fontSize = (32 + Math.random() * 24) + 'px';
  BOX.appendChild(el);
  el.addEventListener('click', () => { el.textContent = '💥'; setTimeout(() => el.remove(), 300); });
  setTimeout(() => el.remove(), (dur + delay + 0.5) * 1000);
}
function startBalloons() {
  // initial burst
  for (let i = 0; i < 15; i++) setTimeout(spawnBalloon, i * 180);
  // continuous drip
  balloonTimer = setInterval(spawnBalloon, 900);
}

// ── COUNTDOWN GATE ──
let counting = false;
function beginCountdown() {
  if (counting) return;
  counting = true;
  document.getElementById('enter-btn').disabled = true;
  const el = document.getElementById('cdown');
  const tick = n => {
    el.style.transform = 'scale(1.6)';
    el.textContent = n === 0 ? '🎉' : n;
    setTimeout(() => { el.style.transform = 'scale(0.85)'; el.style.opacity = '0.5'; }, 480);
    if (n > 0) setTimeout(() => { el.style.opacity = '1'; tick(n - 1); }, 820);
    else setTimeout(openMain, 700);
  };
  tick(3);
}

function openMain() {
  document.getElementById('gate').style.display = 'none';
  const main = document.getElementById('main');
  main.style.display = 'block';

  // Big celebrations
  fireConfetti();
  setTimeout(fireConfetti, 1200);
  setTimeout(fireConfetti, 2800);
  setTimeout(fireConfetti, 5000);

  startFireworks(10000);
  startBalloons();

  // Reveal cards
  const els = main.querySelectorAll('.rv');
  els.forEach((el, i) => {
    setTimeout(() => el.classList.add('on'), 200 + i * 220);
  });

  // Typewriter after hero
  setTimeout(startTypewriter, 900);

  // Twist quote reveal
  setTimeout(() => {
    document.querySelectorAll('.tq-line, .tq-sep, .tq-sub').forEach((el, i) => {
      setTimeout(() => el.classList.add('show'), i * 400);
    });
  }, 1800);
}

// ── TYPEWRITER ──
const messages = [
  "Some people teach lessons.\nRare people leave a legacy.\nThank you, Sir — for being one of them. 🙏",
  "Not every mentor changes a career.\nSome change the way we see ourselves.\nYou did both. 🎂✨",
  "This message is from all of us.\nEvery single person on your team.\nHappy Birthday, Sir. 🌟"
];
let mIdx = 0, cIdx = 0, typing = true;
function startTypewriter() {
  const el = document.getElementById('typewriter-text');
  el.innerHTML = '<span class="cursor"></span>';
  typeChar(el);
}
function typeChar(el) {
  const msg = messages[mIdx];
  if (typing) {
    if (cIdx < msg.length) {
      const char = msg[cIdx];
      const plain = el.innerText.replace('|','');
      el.innerHTML = (plain + (char === '\n' ? '\n' : char)).replace(/\n/g,'<br>') + '<span class="cursor"></span>';
      cIdx++;
      setTimeout(() => typeChar(el), char === '\n' ? 300 : 44 + Math.random() * 28);
    } else {
      typing = false;
      setTimeout(() => { typing = false; eraseChar(el); }, 3200);
    }
  }
}
function eraseChar(el) {
  const plain = el.innerText;
  if (plain.length > 0) {
    el.innerHTML = plain.slice(0,-1).replace(/\n/g,'<br>') + '<span class="cursor"></span>';
    setTimeout(() => eraseChar(el), 20);
  } else {
    mIdx = (mIdx + 1) % messages.length; cIdx = 0; typing = true;
    setTimeout(() => typeChar(el), 500);
  }
}

// Periodic extra bursts as user scrolls
window.addEventListener('scroll', () => {
  if (Math.random() < 0.04) spawnBalloon();
}, { passive: true });
</script>
</body>
</html>
