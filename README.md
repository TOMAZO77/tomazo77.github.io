<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tomas Atanasov | Cyber Specialist</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      margin: 0;
      background: black;
      font-family: 'Courier New', monospace;
      color: white;
      scroll-behavior: smooth; /* sleek scrolling */
    }
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1;
    }
    .glass {
      background: rgba(0, 0, 0, 0.55);
      backdrop-filter: blur(8px);
      border: 1px solid rgba(255, 0, 0, 0.3);
      border-radius: 14px;
      padding: 2rem;
      margin: 5rem auto;
      max-width: 800px;
      box-shadow: 0 0 25px rgba(255, 0, 0, 0.3);
    }
    .glow {
      text-shadow: 0 0 12px #a00, 0 0 24px #d00, 0 0 40px #f00;
    }
  </style>
</head>
<body>

  <!-- Hero Section -->
  <section class="glass text-center">
    <h1 class="text-6xl font-bold mb-4 glow text-red-500">TOMAZO</h1>
    <p class="text-xl text-red-300 glow">
      Cyber Specialist • Software Engineer • Next-gen Developer
    </p>
    <a href="#about" class="mt-8 inline-block px-6 py-3 rounded bg-red-700/30 border border-red-500 text-red-200 hover:bg-red-700/60 transition glow">
      Enter System ↓
    </a>
  </section>

  <!-- About Section -->
  <section id="about" class="glass text-center text-red-200">
    <h2 class="text-3xl mb-4 glow">About Me</h2>
    <p>
      Passionate about building immersive experiences in software and game development. 
      Blending creativity, cyber aesthetics, and next-gen technologies. <br><br>
      Student of <span class="glow">Blackpool & the Fylde College</span> <br>
      ID: <span class="glow">30221022</span>.
    </p>
  </section>

  <!-- Extra Scroll Section -->
  <section class="glass text-center text-red-200">
    <h2 class="text-3xl mb-4 glow">Projects</h2>
    <p>
      Exploring advanced systems, futuristic UI design, and powerful interactive experiences. 
      My goal is to fuse art and code into immersive realities.
    </p>
  </section>

  <!-- Contact -->
  <footer class="glass text-center text-red-300">
    <p>© 2025 Tomas Atanasov | 
      <a href="mailto:tomas-atanasov@hotmail.com" class="underline glow">Contact Me</a>
    </p>
  </footer>

  <!-- Matrix Rain Background -->
  <canvas id="matrix"></canvas>
  <script>
    const canvas = document.getElementById("matrix");
    const ctx = canvas.getContext("2d");

    canvas.height = window.innerHeight;
    canvas.width = window.innerWidth;

    const normalSymbols = ["ア","カ","サ","タ","ナ","ハ","マ","ヤ","ラ","ワ","0","1","2","3","4","5","6","7","8","9"];
    const specialSymbols = ["TOMAZO","Tomas Atanasov","30221022","Blackpool & the Fylde College"];
    const fontSize = 16;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    let pulse = 0;
    let direction = 1;

    function draw() {
      ctx.fillStyle = "rgba(0, 0, 0, 0.08)";
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.font = fontSize + "px monospace";

      pulse += direction * 0.05;
      if (pulse >= 1 || pulse <= 0) direction *= -1;

      for (let i = 0; i < drops.length; i++) {
        let text;
        // Occasionally insert a special symbol at random
        if (Math.random() < 0.002) {
          text = specialSymbols[Math.floor(Math.random() * specialSymbols.length)];
          const r = Math.floor(150 + pulse * 105); // dark red pulsing
          const g = Math.floor(20 + pulse * 30);
          const b = Math.floor(20 + pulse * 30);
          ctx.fillStyle = `rgb(${r},${g},${b})`;
          ctx.shadowBlur = 20;
          ctx.shadowColor = `rgba(${r},${g},${b},0.9)`;
          // Place it in a random X,Y instead of fixed column
          ctx.fillText(te
