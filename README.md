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
      overflow: hidden;
      background: black;
      color: #0f0;
      font-family: 'Courier New', monospace;
    }
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1;
    }
    .glow {
      text-shadow: 0 0 5px #0f0, 0 0 10px #0f0, 0 0 20px #0f0;
    }
  </style>
</head>
<body class="flex flex-col justify-center items-center h-screen text-center">

  <!-- Hero Section -->
  <section>
    <h1 class="text-6xl font-bold mb-4 glow">TOMAZO</h1>
    <p class="text-xl text-green-400 max-w-xl mx-auto glow">
      Tomas Atanasov • Cyber Specialist • Software Engineer
    </p>
    <a href="#about" class="mt-8 inline-block px-6 py-3 rounded bg-green-700/30 border border-green-400 text-green-300 hover:bg-green-700/60 transition glow">
      Access Profile ↓
    </a>
  </section>

  <!-- About Section -->
  <section id="about" class="p-12 mt-20 bg-black/80 rounded-2xl border border-green-400 max-w-3xl mx-auto glow">
    <h2 class="text-3xl mb-4">About Me</h2>
    <p>
      Passionate about building immersive experiences in software and game development. 
      Blending creativity, cyber aesthetics, and next-gen technologies. 
      Student of Blackpool & the Fylde College (ID: 30221022).
    </p>
  </section>

  <!-- Contact -->
  <footer class="text-center py-6 text-green-500 glow">
    <p>© 2025 Tomas Atanasov | <a href="mailto:xemenone@hotmail.com" class="underline">Contact</a></p>
  </footer>

  <!-- Matrix Rain Background -->
  <canvas id="matrix"></canvas>
  <script>
    const canvas = document.getElementById("matrix");
    const ctx = canvas.getContext("2d");

    canvas.height = window.innerHeight;
    canvas.width = window.innerWidth;

    // Pool of symbols
    const symbols = [
      "ア","カ","サ","タ","ナ","ハ","マ","ヤ","ラ","ワ",
      "0","1","2","3","4","5","6","7","8","9",
      "TOMAZO","Tomas Atanasov","30221022","Blackpool & the Fylde College"
    ];

    const fontSize = 16;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {
      ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.fillStyle = "#0F0";
      ctx.font = fontSize + "px monospace";

      for (let i = 0; i < drops.length; i++) {
        const text = symbols[Math.floor(Math.random() * symbols.length)];
        ctx.fillText(text, i * fontSize, drops[i] * fontSize);

        if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
          drops[i] = 0;
        }
        drops[i]++;
      }
    }

    setInterval(draw, 33);

    window.addEventListener("resize", () => {
      canvas.height = window.innerHeight;
      canvas.width = window.innerWidth;
    });
  </script>
</body>
</html>
