
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TOMAZO | Cyber Matrix</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      margin: 0;
      background: black;
      font-family: 'Courier New', monospace;
      color: white;
      scroll-behavior: smooth;
      overflow-x: hidden;
    }
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1;
    }
    .glass {
      background: rgba(0, 0, 0, 0.6);
      backdrop-filter: blur(8px);
      border-radius: 12px;
      padding: 2rem;
      margin: 6rem auto;
      max-width: 850px;
      box-shadow: 0 0 20px rgba(0, 255, 0, 0.25);
      transform: scale(0.95);
      transition: all 0.6s ease-in-out;
    }
    .glass:hover {
      transform: scale(1) translateY(-5px);
      box-shadow: 0 0 30px rgba(0, 255, 0, 0.5);
    }
    .glow {
      text-shadow: 0 0 10px #0f0, 0 0 20px #0f0;
    }
    .red-glow {
      text-shadow: 0 0 10px #900, 0 0 20px #d00, 0 0 40px #f00;
    }
    section {
      min-height: 90vh;
    }
  </style>
</head>
<body>

  <!-- Hero Section -->
  <section class="glass text-center">
    <h1 class="text-6xl font-bold mb-4 glow text-green-400">TOMAZO</h1>
    <p class="text-xl text-green-300 glow">
      Cyber Specialist • Software Engineer • Next-gen Developer
    </p>
    <a href="#about" class="mt-8 inline-block px-6 py-3 rounded bg-green-700/20 border border-green-500 text-green-200 hover:bg-green-700/40 transition glow">
      Enter System ↓
    </a>
  </section>

  <!-- About Section -->
  <section id="about" class="glass text-center text-green-200">
    <h2 class="text-3xl mb-4 glow">About Me</h2>
    <p>
      Passionate about creating futuristic technology and immersive experiences. <br><br>
      Student at <span class="red-glow">Blackpool & the Fylde College</span> <br>
      ID: <span class="red-glow">30221022</span>.
    </p>
  </section>

  <!-- Projects -->
  <section class="glass text-center text-green-200">
    <h2 class="text-3xl mb-4 glow">Projects</h2>
    <p>
      Exploring software, games, and next-gen systems that push the limits of imagination.  
      My code is art, my art is code.  
    </p>
  </section>

  <!-- Footer pinned at bottom -->
  <footer class="text-green-300">
    <p>© 2025 Tomas Atanasov | 
      <a href="mailto:tomas-atanasov@hotmail.com">Contact Me</a>
    </p>
  </footer>

  <!-- Matrix Rain Background -->
  <canvas id="matrix"></canvas>
  <script>
    const canvas = document.getElementById("matrix");
    const ctx = canvas.getContext("2d");

    canvas.height = window.innerHeight;
    canvas.width = window.innerWidth;

    const normalSymbols = "アカサタナハマヤラワ0123456789".split("");
    const specialSymbols = ["TOMAZO", "Tomas Atanasov", "30221022", "Blackpool & the Fylde College"];
    const fontSize = 16;
    const columns = Math.floor(canvas.width / fontSize);
    const drops = Array(columns).fill(1);

    function draw() {
      ctx.fillStyle = "rgba(0, 0, 0, 0.08)";
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.font = fontSize + "px monospace";

      for (let i = 0; i < drops.length; i++) {
        let x = i * fontSize;
        let y = drops[i] * fontSize;

        // Random chance to insert special string instead of a single character
        if (Math.random() < 0.0015) {
          const text = specialSymbols[Math.floor(Math.random() * specialSymbols.length)];
          ctx.fillStyle = "rgb(180,0,0)";
          ctx.shadowBlur = 15;
          ctx.shadowColor = "rgba(255,0,0,0.8)";
          ctx.fillText(text, x, y);
        } else {
          const text = normalSymbols[Math.floor(Math.random() * normalSymbols.length)];
          ctx.fillStyle = "rgb(0,180,0)";
          ctx.shadowBlur = 0;
          ctx.fillText(text, x, y);
        }

        // reset drop to top randomly
        if (y > canvas.height && Math.random() > 0.975) {
          drops[i] = 0;
        }
        drops[i] += 1; // falling speed
      }
    }

    setInterval(draw, 40); // smooth movie-like frame rate

    window.addEventListener("resize", () => {
      canvas.height = window.innerHeight;
      canvas.width = window.innerWidth;
    });
  </script>
</body>
</html>
