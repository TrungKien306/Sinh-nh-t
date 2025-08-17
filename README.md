<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Chúc mừng sinh nhật Hiên!</title>
  <style>
    body {
      text-align: center;
      background: linear-gradient(135deg, #ffdde1, #ee9ca7);
      font-family: 'Arial', sans-serif;
      overflow: hidden;
    }
    h1 {
      font-size: 60px;
      color: #ff0066;
      margin-top: 100px;
      animation: pulse 1.5s infinite;
    }
    p {
      font-size: 25px;
      color: #333;
    }
    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
    .balloon {
      position: absolute;
      bottom: -150px;
      width: 80px;
      animation: floatUp 6s infinite;
    }
    @keyframes floatUp {
      from { transform: translateY(0); opacity: 1; }
      to { transform: translateY(-120vh); opacity: 0; }
    }
  </style>
</head>
<body>
  <h1>🎉 Chúc mừng sinh nhật Hiên! 🎂</h1>
  <p>Chúc Hiên luôn xinh đẹp, hạnh phúc và thành công! 🥳💖</p>
  
  <!-- Hình bong bóng -->
  <img src="https://i.imgur.com/2s9X2KQ.png" class="balloon" style="left: 10%; animation-delay: 0s;">
  <img src="https://i.imgur.com/2s9X2KQ.png" class="balloon" style="left: 40%; animation-delay: 2s;">
  <img src="https://i.imgur.com/2s9X2KQ.png" class="balloon" style="left: 70%; animation-delay: 4s;">
  
  <!-- Nhạc nền -->
  <audio autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>
</body>
</html>
