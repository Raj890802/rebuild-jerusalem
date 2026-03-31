<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Rebuild the Kingdom — Donate</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;800&family=Crimson+Pro:ital,wght@0,300;0,400;1,300;1,400&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --gold: #C9A84C;
    --gold-light: #E8C96A;
    --gold-dark: #8B6914;
    --crimson: #8B1A1A;
    --parchment: #F5EDD6;
    --parchment-dark: #EAD9B0;
    --stone: #2C2416;
    --stone-mid: #4A3B28;
    --ink: #1A1208;
  }

  body {
    font-family: 'Crimson Pro', Georgia, serif;
    background-color: #1A1208;
    color: var(--parchment);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* === BACKGROUND === */
  .bg-layer {
    position: fixed;
    inset: 0;
    z-index: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 0%, rgba(201,168,76,0.08) 0%, transparent 70%),
      radial-gradient(ellipse 60% 40% at 20% 100%, rgba(139,26,26,0.12) 0%, transparent 60%),
      #1A1208;
  }

  .cross-bg {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0.025;
    pointer-events: none;
    z-index: 0;
  }

  /* === LAYOUT === */
  .page {
    position: relative;
    z-index: 1;
    max-width: 680px;
    margin: 0 auto;
    padding: 3rem 1.5rem 4rem;
  }

  /* === HEADER === */
  .header {
    text-align: center;
    margin-bottom: 3rem;
    animation: fadeDown 0.9s ease both;
  }

  .cross-emblem {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 1.5rem;
  }

  .divider-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, transparent, var(--gold-dark), transparent);
    max-width: 80px;
  }

  .cross-symbol {
    font-size: 32px;
    color: var(--gold);
    margin: 0 16px;
    text-shadow: 0 0 20px rgba(201,168,76,0.4);
    letter-spacing: 0;
  }

  h1 {
    font-family: 'Cinzel', serif;
    font-size: clamp(22px, 5vw, 36px);
    font-weight: 800;
    color: var(--gold-light);
    letter-spacing: 0.04em;
    line-height: 1.2;
    margin-bottom: 0.5rem;
    text-shadow: 0 2px 12px rgba(201,168,76,0.25);
  }

  .subtitle-latin {
    font-family: 'Cinzel', serif;
    font-size: 11px;
    font-weight: 400;
    color: var(--gold-dark);
    letter-spacing: 0.25em;
    text-transform: uppercase;
    margin-bottom: 1.25rem;
  }

  .header-desc {
    font-size: 17px;
    font-weight: 300;
    color: var(--parchment-dark);
    line-height: 1.75;
    font-style: italic;
    max-width: 480px;
    margin: 0 auto;
  }

  /* === CARD === */
  .card {
    background: rgba(245,237,214,0.05);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 4px;
    padding: 2rem;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.9s ease both;
  }

  .card-title {
    font-family: 'Cinzel', serif;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.2em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 1.25rem;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .card-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: rgba(201,168,76,0.2);
  }

  /* === AMOUNTS === */
  .amount-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-bottom: 1.25rem;
  }

  .amount-btn {
    padding: 14px 8px;
    background: transparent;
    border: 1px solid rgba(201,168,76,0.25);
    border-radius: 3px;
    color: var(--parchment);
    font-family: 'Cinzel', serif;
    font-size: 15px;
    cursor: pointer;
    transition: all 0.2s ease;
    text-align: center;
  }

  .amount-btn:hover {
    border-color: var(--gold);
    color: var(--gold-light);
    background: rgba(201,168,76,0.06);
  }

  .amount-btn.selected {
    border-color: var(--gold);
    border-width: 2px;
    color: var(--gold-light);
    background: rgba(201,168,76,0.1);
  }

  .amount-btn .label {
    display: block;
    font-size: 9px;
    font-family: 'Crimson Pro', serif;
    color: rgba(201,168,76,0.55);
    letter-spacing: 0.1em;
    margin-top: 3px;
    font-style: italic;
    text-transform: none;
  }

  /* === CUSTOM INPUT === */
  .input-wrap {
    position: relative;
    margin-bottom: 1rem;
  }

  .input-prefix {
    position: absolute;
    left: 14px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--gold-dark);
    font-family: 'Cinzel', serif;
    font-size: 15px;
    pointer-events: none;
  }

  input[type="number"], textarea {
    width: 100%;
    background: rgba(245,237,214,0.04);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 3px;
    padding: 13px 14px 13px 30px;
    color: var(--parchment);
    font-family: 'Crimson Pro', serif;
    font-size: 16px;
    outline: none;
    transition: border-color 0.2s;
    -moz-appearance: textfield;
  }

  input[type="number"]::-webkit-inner-spin-button { -webkit-appearance: none; }

  input[type="number"]:focus, textarea:focus {
    border-color: var(--gold);
  }

  textarea {
    padding: 12px 14px;
    resize: none;
    height: 80px;
    font-style: italic;
    font-size: 15px;
  }

  textarea::placeholder, input::placeholder {
    color: rgba(245,237,214,0.25);
    font-style: italic;
  }

  /* === IMPACT === */
  .impact-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-top: 0.5rem;
  }

  .impact-item {
    text-align: center;
    padding: 14px 8px;
    background: rgba(201,168,76,0.04);
    border: 1px solid rgba(201,168,76,0.12);
    border-radius: 3px;
  }

  .impact-amount {
    font-family: 'Cinzel', serif;
    font-size: 16px;
    color: var(--gold);
    display: block;
    margin-bottom: 4px;
  }

  .impact-desc {
    font-size: 12px;
    color: rgba(245,237,214,0.5);
    font-style: italic;
    line-height: 1.4;
  }

  /* === DONATE BUTTON === */
  .donate-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    width: 100%;
    padding: 18px 24px;
    background: linear-gradient(135deg, #C9A84C 0%, #E8C96A 45%, #C9A84C 100%);
    border: none;
    border-radius: 3px;
    color: var(--ink);
    font-family: 'Cinzel', serif;
    font-size: 15px;
    font-weight: 600;
    letter-spacing: 0.08em;
    cursor: pointer;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.12s;
    margin-bottom: 1rem;
    animation: fadeUp 0.9s 0.3s ease both;
  }

  .donate-btn:hover { opacity: 0.9; }
  .donate-btn:active { transform: scale(0.985); }

  .shield-icon { display: inline-block; }

  .secure-row {
    text-align: center;
    font-size: 12px;
    color: rgba(245,237,214,0.3);
    font-style: italic;
    margin-bottom: 2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 6px;
    animation: fadeUp 0.9s 0.4s ease both;
  }

  /* === FOOTER === */
  .footer-verse {
    text-align: center;
    border-top: 1px solid rgba(201,168,76,0.12);
    padding-top: 2rem;
    animation: fadeUp 0.9s 0.5s ease both;
  }

  .verse-text {
    font-size: 16px;
    font-style: italic;
    color: rgba(245,237,214,0.5);
    line-height: 1.7;
    max-width: 400px;
    margin: 0 auto 0.5rem;
  }

  .verse-ref {
    font-family: 'Cinzel', serif;
    font-size: 11px;
    letter-spacing: 0.15em;
    color: var(--gold-dark);
  }

  /* === ANIMATIONS === */
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(16px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .card:nth-child(1) { animation-delay: 0.1s; }
  .card:nth-child(2) { animation-delay: 0.2s; }

  @media (max-width: 480px) {
    .amount-grid { grid-template-columns: repeat(2, 1fr); }
    .impact-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="bg-layer"></div>

<!-- Large cross watermark -->
<svg class="cross-bg" width="400" height="500" viewBox="0 0 400 500" fill="none" xmlns="http://www.w3.org/2000/svg">
  <rect x="160" y="0" width="80" height="500" fill="#C9A84C"/>
  <rect x="0" y="150" width="400" height="80" fill="#C9A84C"/>
</svg>

<div class="page">

  <!-- HEADER -->
  <div class="header">
    <div class="cross-emblem">
      <div class="divider-line"></div>
      <span class="cross-symbol">✝</span>
      <div class="divider-line"></div>
    </div>
    <p class="subtitle-latin">Pro Gloria Dei · Jerusalem</p>
    <h1>Rebuild the Kingdom<br>of Christ in Jerusalem</h1>
    <p style="margin-top:1rem;" class="header-desc">
      A sacred mission to restore the holy city — stone by stone, soul by soul.
      Your offering joins centuries of faith.
    </p>
  </div>

  <!-- AMOUNT SELECTION -->
  <div class="card">
    <div class="card-title">Choose your offering</div>

    <div class="amount-grid">
      <button class="amount-btn" onclick="selectAmount(this,'10')">
        $10<span class="label">a small stone</span>
      </button>
      <button class="amount-btn" onclick="selectAmount(this,'25')">
        $25<span class="label">a lamp lit</span>
      </button>
      <button class="amount-btn selected" onclick="selectAmount(this,'50')">
        $50<span class="label">a foundation</span>
      </button>
      <button class="amount-btn" onclick="selectAmount(this,'100')">
        $100<span class="label">a pillar raised</span>
      </button>
      <button class="amount-btn" onclick="selectAmount(this,'250')">
        $250<span class="label">a wall restored</span>
      </button>
      <button class="amount-btn" onclick="selectAmount(this,'')">
        Custom<span class="label">your heart</span>
      </button>
    </div>

    <div class="input-wrap">
      <span class="input-prefix">$</span>
      <input type="number" id="amountInput" value="50" min="1" placeholder="Enter amount" oninput="syncCustom(this)"/>
    </div>

    <div style="margin-bottom:0;">
      <div class="card-title" style="margin-bottom:0.75rem;">Leave a prayer or message</div>
      <textarea id="msgInput" placeholder="Write your prayer or dedication..."></textarea>
    </div>
  </div>

  <!-- IMPACT -->
  <div class="card">
    <div class="card-title">Your impact</div>
    <div class="impact-grid">
      <div class="impact-item">
        <span class="impact-amount">$25</span>
        <span class="impact-desc">Provides sacred texts & scriptures</span>
      </div>
      <div class="impact-item">
        <span class="impact-amount">$100</span>
        <span class="impact-desc">Restores a section of holy stonework</span>
      </div>
      <div class="impact-item">
        <span class="impact-amount">$500</span>
        <span class="impact-desc">Funds a chapel restoration phase</span>
      </div>
    </div>
  </div>

  <!-- DONATE BUTTON -->
  <a id="donateLink" href="https://www.paypal.me/RajMehra32/50" target="_blank" class="donate-btn" onclick="updateLink()">
    ✝ &nbsp; Make Your Sacred Offering
  </a>

  <p class="secure-row">
    <svg width="12" height="13" viewBox="0 0 24 24" fill="none"><rect x="3" y="11" width="18" height="11" rx="2" stroke="currentColor" stroke-width="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4" stroke="currentColor" stroke-width="2"/></svg>
    Encrypted &amp; secure · All offerings are received in good faith
  </p>

  <!-- FOOTER VERSE -->
  <div class="footer-verse">
    <p class="verse-text">"And they shall rebuild the ancient ruins; they shall raise up the former devastations."</p>
    <p class="verse-ref">Isaiah 61:4</p>
  </div>

</div>

<script>
  let selectedAmount = '50';

  function selectAmount(btn, val) {
    document.querySelectorAll('.amount-btn').forEach(b => b.classList.remove('selected'));
    btn.classList.add('selected');
    selectedAmount = val;
    const inp = document.getElementById('amountInput');
    if (val) { inp.value = val; }
    else { inp.value = ''; inp.focus(); }
    updateLink();
  }

  function syncCustom(inp) {
    selectedAmount = inp.value;
    document.querySelectorAll('.amount-btn').forEach(b => b.classList.remove('selected'));
    updateLink();
  }

  function updateLink() {
    const amt = document.getElementById('amountInput').value || selectedAmount;
    const link = document.getElementById('donateLink');
    link.href = (amt && parseFloat(amt) > 0)
      ? `https://www.paypal.me/RajMehra32/${amt}`
      : 'https://www.paypal.me/RajMehra32';
  }
</script>
</b<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Rebuild the Kingdom — Donate</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;800&family=Crimson+Pro:ital,wght@0,300;0,400;1,300;1,400&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --gold: #C9A84C;
    --gold-light: #E8C96A;
    --gold-dark: #8B6914;
    --crimson: #8B1A1A;
    --parchment: #F5EDD6;
    --parchment-dark: #EAD9B0;
    --stone: #2C2416;
    --stone-mid: #4A3B28;
    --ink: #1A1208;
  }

  body {
    font-family: 'Crimson Pro', Georgia, serif;
    background-color: #1A1208;
    color: var(--parchment);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* === BACKGROUND === */
  .bg-layer {
    position: fixed;
    inset: 0;
    z-index: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 0%, rgba(201,168,76,0.08) 0%, transparent 70%),
      radial-gradient(ellipse 60% 40% at 20% 100%, rgba(139,26,26,0.12) 0%, transparent 60%),
      #1A1208;
  }

  .cross-bg {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0.025;
    pointer-events: none;
    z-index: 0;
  }

  /* === LAYOUT === */
  .page {
    position: relative;
    z-index: 1;
    max-width: 680px;
    margin: 0 auto;
    padding: 3rem 1.5rem 4rem;
  }

  /* === HEADER === */
  .header {
    text-align: center;
    margin-bottom: 3rem;
    animation: fadeDown 0.9s ease both;
  }

  .cross-emblem {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 1.5rem;
  }

  .divider-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, transparent, var(--gold-dark), transparent);
    max-width: 80px;
  }

  .cross-symbol {
    font-size: 32px;
    color: var(--gold);
    margin: 0 16px;
    text-shadow: 0 0 20px rgba(201,168,76,0.4);
    letter-spacing: 0;
  }

  h1 {
    font-family: 'Cinzel', serif;
    font-size: clamp(22px, 5vw, 36px);
    font-weight: 800;
    color: var(--gold-light);
    letter-spacing: 0.04em;
    line-height: 1.2;
    margin-bottom: 0.5rem;
    text-shadow: 0 2px 12px rgba(201,168,76,0.25);
  }

  .subtitle-latin {
    font-family: 'Cinzel', serif;
    font-size: 11px;
    font-weight: 400;
    color: var(--gold-dark);
    letter-spacing: 0.25em;
    text-transform: uppercase;
    margin-bottom: 1.25rem;
  }

  .header-desc {
    font-size: 17px;
    font-weight: 300;
    color: var(--parchment-dark);
    line-height: 1.75;
    font-style: italic;
    max-width: 480px;
    margin: 0 auto;
  }

  /* === CARD === */
  .card {
    background: rgba(245,237,214,0.05);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 4px;
    padding: 2rem;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.9s ease both;
  }

  .card-title {
    font-family: 'Cinzel', serif;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.2em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 1.25rem;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .card-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: rgba(201,168,76,0.2);
  }

  /* === AMOUNTS === */
  .amount-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-bottom: 1.25rem;
  }

  .amount-btn {
    padding: 14px 8px;
    background: transparent;
    border: 1px solid rgba(201,168,76,0.25);
    border-radius: 3px;
    color: var(--parchment);
    font-family: 'Cinzel', serif;
    font-size: 15px;
    cursor: pointer;
    transition: all 0.2s ease;
    text-align: center;
  }

  .amount-btn:hover {
    border-color: var(--gold);
    color: var(--gold-light);
    background: rgba(201,168,76,0.06);
  }

  .amount-btn.selected {
    border-color: var(--gold);
    border-width: 2px;
    color: var(--gold-light);
    background: rgba(201,168,76,0.1);
  }

  .amount-btn .label {
    display: block;
    font-size: 9px;
    font-family: 'Crimson Pro', serif;
    color: rgba(201,168,76,0.55);
    letter-spacing: 0.1em;
    margin-top: 3px;
    font-style: italic;
    text-transform: none;
  }

  /* === CUSTOM INPUT === */
  .input-wrap {
    position: relative;
    margin-bottom: 1rem;
  }

  .input-prefix {
    position: absolute;
    left: 14px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--gold-dark);
    font-family: 'Cinzel', serif;
    font-size: 15px;
    pointer-events: none;
  }

  input[type="number"], textarea {
    width: 100%;
    background: rgba(245,237,214,0.04);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 3px;
    padding: 13px 14px 13px 30px;
    color: var(--parchment);
    font-family: 'Crimson Pro', serif;
    font-size: 16px;
    outline: none;
    transition: border-color 0.2s;
    -moz-appearance: textfield;
  }

  input[type="number"]::-webkit-inner-spin-button { -webkit-appearance: none; }

  input[type="number"]:focus, textarea:focus {
    border-color: var(--gold);
  }

  textarea {
    padding: 12px 14px;
    resize: none;
    height: 80px;
    font-style: italic;
    font-size: 15px;
  }

  textarea::placeholder, input::placeholder {
    color: rgba(245,237,214,0.25);
    font-style: italic;
  }

  /* === IMPACT === */
  .impact-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-top: 0.5rem;
  }

  .impact-item {
    text-align: center;
    padding: 14px 8px;
    background: rgba(201,168,76,0.04);
    border: 1px solid rgba(201,168,76,0.12);
    border-radius: 3px;
  }

  .impact-amount {
    font-family: 'Cinzel', serif;
    font-size: 16px;
    color: var(--gold);
    display: block;
    margin-bottom: 4px;
  }

  .impact-desc {
    font-size: 12px;
    color: rgba(245,237,214,0.5);
    font-style: italic;
    line-height: 1.4;
  }

  /* === DONATE BUTTON === */
  .donate-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    width: 100%;
    padding: 18px 24px;
    background: linear-gradient(135deg, #C9A84C 0%, #E8C96A 45%, #C9A84C 100%);
    border: none;
    border-radius: 3px;
    color: var(--ink);
    font-family: 'Cinzel', serif;
    font-size: 15px;
    font-weight: 600;
    letter-spacing: 0.08em;
    cursor: pointer;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.12s;
    margin-bottom: 1rem;
    animation: fadeUp 0.9s 0.3s ease both;
  }

  .donate-btn:hover { opacity: 0.9; }
  .donate-btn:active { transform: scale(0.985); }

  .shield-icon { display: inline-block; }

  .secure-row {
    text-align: center;
    font-size: 12px;
    color: rgba(245,237,214,0.3);
    font-style: italic;
    margin-bottom: 2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 6px;
    animation: fadeUp 0.9s 0.4s ease both;
  }

  /* === FOOTER === */
  .footer-verse {
    text-align: center;
    border-top: 1px solid rgba(201,168,76,0.12);
    padding-top: 2rem;
    animation: fadeUp 0.9s 0.5s ease both;
  }

  .verse-text {
    font-size: 16px;
    font-style: italic;
    color: rgba(245,237,214,0.5);
    line-height: 1.7;
    max-width: 400px;
    margin: 0 auto 0.5rem;
  }

  .verse-ref {
    font-family: 'Cinzel', serif;
    font-size: 11px;
    letter-spacing: 0.15em;
    color: var(--gold-dark);
  }

  /* === ANIMATIONS === */
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(16px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .card:nth-child(1) { animation-delay: 0.1s; }
  .card:nth-child(2) { animation-delay: 0.2s; }

  @media (max-width: 480px) {
    .amount-grid { grid-template-columns: repeat(2, 1fr); }
    .impact-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="bg-layer"></div>

<!-- Large cross watermark -->
<svg class="cross-bg" width="400" height="500" viewBox="0 0 400 500" fill="none" xmlns="http://www.w3.org/2000/svg">
  <rect x="160" y="0" width="80" height="500" fill="#C9A84C"/>
  <rect x="0" y="150" width="400" height="80" fill="#C9A84C"/>
</svg>

<div class="page">

  <!-- HEADER -->
  <div class="header">
    <div class="cross-emblem">
      <div class="divider-line"></div>
      <span class="cross-symbol">✝</span>
      <div class="divider-line"></div>
    </div>
    <p class="subtitle-latin">Pro Gloria Dei · Jerusalem</p>
    <h1>Rebuild the Kingdom<br>of Christ in Jerusalem</h1>
    <p style="margin-top:1rem;" class="header-desc">
      A sacred mission to restore the holy city — stone by stone, soul by soul.
      Your offering joins centuries of faith.
    </p>
  </div>

  <!-- AMOUNT SELECTION -->
  <div class="card">
    <div class="card-title">Choose your offering</div>

    <div class="amount-grid">
      <button class="amount-btn" onclick="selectAmount(this,'10')">
        $10<span class="label">a small stone</span>
      </button>
      <button class="amount-btn" onclick="selectAmount(this,'25')">
        $25<span class="label">a lamp lit</span>
      </button>
      <button class="amount-btn selected" onclick="selectAmount(this,'50')">
        $50<span class="label">a foundation</span>
      </button>
      <button class="amount-btn" onclick="selectAmount(this,'100')">
        $100<span class="label">a pillar raised</span>
      </button>
      <button class="amount-btn" onclick="selectAmount(this,'250')">
        $250<span class="label">a wall restored</span>
      </button>
      <button class="amount-btn" onclick="selectAmount(this,'')">
        Custom<span class="label">your heart</span>
      </button>
    </div>

    <div class="input-wrap">
      <span class="input-prefix">$</span>
      <input type="number" id="amountInput" value="50" min="1" placeholder="Enter amount" oninput="syncCustom(this)"/>
    </div>

    <div style="margin-bottom:0;">
      <div class="card-title" style="margin-bottom:0.75rem;">Leave a prayer or message</div>
      <textarea id="msgInput" placeholder="Write your prayer or dedication..."></textarea>
    </div>
  </div>

  <!-- IMPACT -->
  <div class="card">
    <div class="card-title">Your impact</div>
    <div class="impact-grid">
      <div class="impact-item">
        <span class="impact-amount">$25</span>
        <span class="impact-desc">Provides sacred texts & scriptures</span>
      </div>
      <div class="impact-item">
        <span class="impact-amount">$100</span>
        <span class="impact-desc">Restores a section of holy stonework</span>
      </div>
      <div class="impact-item">
        <span class="impact-amount">$500</span>
        <span class="impact-desc">Funds a chapel restoration phase</span>
      </div>
    </div>
  </div>

  <!-- DONATE BUTTON -->
  <a id="donateLink" href="https://www.paypal.me/RajMehra32/50" target="_blank" class="donate-btn" onclick="updateLink()">
    ✝ &nbsp; Make Your Sacred Offering
  </a>

  <p class="secure-row">
    <svg width="12" height="13" viewBox="0 0 24 24" fill="none"><rect x="3" y="11" width="18" height="11" rx="2" stroke="currentColor" stroke-width="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4" stroke="currentColor" stroke-width="2"/></svg>
    Encrypted &amp; secure · All offerings are received in good faith
  </p>

  <!-- FOOTER VERSE -->
  <div class="footer-verse">go
    <p class="verse-text">"And they shall rebuild the ancient ruins; they shall raise up the former devastations."</p>
    <p class="verse-ref">Isaiah 61:4</p>
  </div>

</div>

<script>
  let selectedAmount = '50';

  function selectAmount(btn, val) {
    document.querySelectorAll('.amount-btn').forEach(b => b.classList.remove('selected'));
    btn.classList.add('selected');
    selectedAmount = val;
    const inp = document.getElementById('amountInput');
    if (val) { inp.value = val; }
    else { inp.value = ''; inp.focus(); }
    updateLink();
  }

  function syncCustom(inp) {
    selectedAmount = inp.value;
    document.querySelectorAll('.amount-btn').forEach(b => b.classList.remove('selected'));
    updateLink();
  }

  function updateLink() {
    const amt = document.getElementById('amountInput').value || selectedAmount;
    const link = document.getElementById('donateLink');
    link.href = (amt && parseFloat(amt) > 0)
      ? `https://www.paypal.me/RajMehra32/${amt}`
      : 'https://www.paypal.me/RajMehra32';
  }
</script>
</body>
</html>
