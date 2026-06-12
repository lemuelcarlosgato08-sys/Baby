<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Para a Mara 🌹</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600;700&display=swap" rel="stylesheet">
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    min-height: 100vh;
    background: #fff0f0;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: sans-serif;
    overflow: hidden;
  }
  .petals-bg { position: fixed; inset: 0; pointer-events: none; z-index: 0; }
  .petal {
    position: absolute;
    width: 10px; height: 14px;
    border-radius: 50% 0 50% 0;
    opacity: 0;
    animation: fall linear infinite;
  }
  @keyframes fall {
    0%   { transform: translateY(-20px) rotate(0deg); opacity: 0.7; }
    100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
  }
  .card {
    position: relative; z-index: 2;
    background: #fff;
    border: 1px solid #f7c1c1;
    border-radius: 24px;
    padding: 2.5rem 2rem 2rem;
    max-width: 420px; width: 90%;
    text-align: center;
  }
  .hearts-row { font-size: 28px; margin-bottom: 1rem; letter-spacing: 6px; }
  .to-name {
    font-family: 'Dancing Script', cursive;
    font-size: 42px; font-weight: 700;
    color: #A32D2D; margin-bottom: 0.25rem;
  }
  .subtitle {
    font-size: 12px; color: #888;
    margin-bottom: 1.5rem;
    letter-spacing: 2px; text-transform: uppercase;
  }
  .divider { width: 60px; height: 1px; background: #E24B4A; margin: 0 auto 1.5rem; opacity: 0.4; }
  .message {
    font-family: 'Dancing Script', cursive;
    font-size: 21px; color: #333; line-height: 1.8; margin-bottom: 1.5rem;
  }
  .rose {
    font-size: 52px; display: block;
    margin: 0.5rem auto 1rem;
    animation: pulse 2s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.12); }
  }
  .signed { font-size: 13px; color: #888; letter-spacing: 1px; }
  .btn {
    margin-top: 1.5rem;
    background: #E24B4A; color: #fff;
    border: none; border-radius: 50px;
    padding: 10px 28px; font-size: 14px;
    cursor: pointer; transition: transform 0.15s, opacity 0.15s;
  }
  .btn:hover { opacity: 0.88; transform: scale(1.03); }
  .confetti-burst { position: fixed; inset: 0; pointer-events: none; z-index: 10; }
  .conf { position: absolute; width: 8px; height: 8px; border-radius: 2px; opacity: 0; }
</style>
</head>
<body>
<div class="petals-bg" id="petals"></div>
<div class="card">
  <div class="hearts-row">🤍 ❤️ 🤍</div>
  <div class="to-name">Mara</div>
  <div class="subtitle">Feliz Dia dos Namorados</div>
  <div class="divider"></div>
  <span class="rose">🌹</span>
  <p class="message" id="msg">
    Você é a pessoa que faz<br>
    meu coração acelerar<br>
    só de pensar no seu sorriso.<br><br>
    Hoje e sempre, é você.
  </p>
  <div class="divider"></div>
  <p class="signed">Com todo o meu amor ❤️</p>
  <button class="btn" onclick="boom()">Toca aqui, Mara 🌹</button>
</div>
<div class="confetti-burst" id="burst"></div>
<script>
  const petalColors = ['#F09595','#F7C1C1','#FCEBEB','#F4C0D1','#ED93B1','#FAC775'];
  const container = document.getElementById('petals');
  for (let i = 0; i < 22; i++) {
    const p = document.createElement('div');
    p.className = 'petal';
    p.style.left = Math.random() * 100 + '%';
    p.style.top = Math.random() * 100 + '%';
    p.style.background = petalColors[Math.floor(Math.random() * petalColors.length)];
    p.style.animationDuration = (4 + Math.random() * 6) + 's';
    p.style.animationDelay = (Math.random() * 6) + 's';
    container.appendChild(p);
  }
  const messages = [
    "Você é a razão do<br>meu maior sorriso<br>cada manhã.<br><br>Te amo demais.",
    "Com você, até os<br>dias comuns se tornam<br>a melhor memória.<br><br>Feliz Dia dos Namorados!",
    "Você é a pessoa que faz<br>meu coração acelerar<br>só de pensar no seu sorriso.<br><br>Hoje e sempre, é você.",
    "Você é a minha parte<br>favorita de todos<br>os meus dias.<br><br>Sempre você. ❤️"
  ];
  let msgIdx = 0;
  function boom() {
    msgIdx = (msgIdx + 1) % messages.length;
    const msg = document.getElementById('msg');
    msg.style.transition = 'opacity 0.3s';
    msg.style.opacity = '0';
    setTimeout(() => { msg.innerHTML = messages[msgIdx]; msg.style.opacity = '1'; }, 320);
    const burst = document.getElementById('burst');
    burst.innerHTML = '';
    const confColors = ['#E24B4A','#F09595','#FAC775','#ED93B1','#378ADD','#5DCAA5'];
    for (let i = 0; i < 30; i++) {
      const c = document.createElement('div');
      c.className = 'conf';
      c.style.background = confColors[i % confColors.length];
      c.style.left = (30 + Math.random() * 40) + '%';
      c.style.top = (30 + Math.random() * 30) + '%';
      c.style.borderRadius = Math.random() > 0.5 ? '50%' : '2px';
      const angle = Math.random() * 360;
      const dist = 60 + Math.random() * 120;
      burst.appendChild(c);
      requestAnimationFrame(() => {
        c.style.opacity = '1';
        c.style.transition = 'transform 0.7s ease-out, opacity 0.7s ease-out';
        c.style.transform = `translate(${Math.cos(angle*Math.PI/180)*dist}px, ${Math.sin(angle*Math.PI/180)*dist}px) rotate(${angle}deg)`;
        setTimeout(() => { c.style.opacity = '0'; }, 400);
      });
    }
  }
</script>
</body>
</html>
