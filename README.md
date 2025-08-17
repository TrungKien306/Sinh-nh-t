<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Chúc mừng sinh nhật Hiên!</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      font-family: 'Arial', sans-serif;
      background: linear-gradient(135deg, #ffdde1, #ee9ca7);
      height: 100vh;
      text-align: center;
      color: white;
    }

    h1 {
      margin-top: 80px;
      font-size: 65px;
      color: #ffeb3b;
      text-shadow: 0 0 20px #ff4081, 0 0 30px #ff4081;
      animation: glow 2s infinite alternate;
      z-index: 10;
      position: relative;
    }

    p {
      font-size: 28px;
      margin-top: 20px;
      color: #fff;
      text-shadow: 0 0 10px #000;
      position: relative;
      z-index: 10;
    }

    @keyframes glow {
      from { text-shadow: 0 0 20px #ff4081, 0 0 30px #ff4081; }
      to { text-shadow: 0 0 30px #00e676, 0 0 40px #00e676; }
    }

    .cake {
      width: 220px;
      margin-top: 30px;
      animation: bounce 2s infinite;
      z-index: 10;
      position: relative;
    }

    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-20px); }
    }

    /* Bong bóng */
    .balloon {
      position: absolute;
      bottom: -150px;
      width: 80px;
      animation: floatUp 10s infinite;
      opacity: 0.8;
    }

    @keyframes floatUp {
      from { transform: translateY(0); opacity: 1; }
      to { transform: translateY(-120vh); opacity: 0; }
    }

    /* Canvas pháo hoa */
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }
  </style>
</head>
<body>
  <h1>🎉 Chúc mừng sinh nhật Hiên! 🎂</h1>
  <p>Chúc Hiên luôn xinh đẹp 🌸, hạnh phúc 💖 và thành công 🌟!</p>
  
  <img src="https://pngimg.com/uploads/birthday_cake/birthday_cake_PNG107366.png" class="cake">

  <!-- Bong bóng -->
  <img src="https://pngimg.com/uploads/balloon/balloon_PNG4969.png" class="balloon" style="left: 10%; animation-delay: 0s;">
  <img src="https://pngimg.com/uploads/balloon/balloon_PNG4974.png" class="balloon" style="left: 30%; animation-delay: 3s;">
  <img src="https://pngimg.com/uploads/balloon/balloon_PNG4981.png" class="balloon" style="left: 60%; animation-delay: 6s;">
  <img src="https://pngimg.com/uploads/balloon/balloon_PNG4969.png" class="balloon" style="left: 80%; animation-delay: 9s;">

  <!-- Canvas pháo hoa -->
  <canvas id="fireworks"></canvas>

  <!-- Nhạc nền -->
  <audio autoplay loop>
    <source src="https://www.bensound.com/bensound-music/bensound-celebration.mp3" type="audio/mpeg">
  </audio>

  <script>
    const canvas = document.getElementById("fireworks");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    class Firework {
      constructor(x, y, color) {
        this.x = x;
        this.y = y;
        this.color = color;
        this.particles = [];
        for (let i = 0; i < 80; i++) {
          const angle = Math.random() * 2 * Math.PI;
          const speed = Math.random() * 5 + 2;
          this.particles.push({
            x: this.x,
            y: this.y,
            vx: Math.cos(angle) * speed,
            vy: Math.sin(angle) * speed,
            alpha: 1
          });
        }
      }
      update() {
        this.particles.forEach(p => {
          p.x += p.vx;
          p.y += p.vy;
          p.vy += 0.05;
          p.alpha -= 0.01;
        });
        this.particles = this.particles.filter(p => p.alpha > 0);
      }
      draw(ctx) {
        this.particles.forEach(p => {
          ctx.globalAlpha = p.alpha;
          ctx.fillStyle = this.color;
          ctx.beginPath();
          ctx.arc(p.x, p.y, 3, 0, 2 * Math.PI);
          ctx.fill();
        });
      }
    }

    let fireworks = [];
    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      if (Math.random() < 0.05) {
        fireworks.push(new Firework(
          Math.random() * canvas.width,
          Math.random() * canvas.height / 2,
          `hsl(${Math.random() * 360}, 100%, 60%)`
        ));
      }
      fireworks.forEach(f => {
        f.update();
        f.draw(ctx);
      });
      fireworks = fireworks.filter(f => f.particles.length > 0);
      requestAnimationFrame(animate);
    }
    animate();

    window.addEventListener("resize", () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });
  </script>
</body>
</html>
