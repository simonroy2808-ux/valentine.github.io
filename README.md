<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Amelia, Will You Be My Valentine? ❤️</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow-x: hidden;
    }

    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 20px;
      max-width: 360px;
      width: 100%;
      padding: 20px;
    }

    .photos {
      display: flex;
      gap: 10px;
      overflow-x: auto;
      scroll-snap-type: x mandatory;
    }

    .photos img {
      width: 220px;
      height: 280px;
      object-fit: cover;
      border-radius: 18px;
      scroll-snap-align: center;
      box-shadow: 0 10px 25px rgba(0,0,0,0.25);
    }

    .card {
      background: #fff;
      padding: 30px 25px;
      border-radius: 22px;
      text-align: center;
      width: 100%;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
    }

    h1 {
      color: #ff4d6d;
      margin-bottom: 10px;
    }

    p {
      color: #555;
      margin-bottom: 25px;
    }

    .buttons {
      display: flex;
      gap: 12px;
    }

    button {
      flex: 1;
      padding: 12px 0;
      border: none;
      border-radius: 30px;
      font-size: 16px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    #yesBtn {
      background: #ff4d6d;
      color: #fff;
    }

    #yesBtn:hover {
      background: #e63e5c;
    }

    #noBtn {
      background: #f1f1f1;
      color: #333;
    }

    .success {
      display: none;
    }

    .success h2 {
      color: #ff4d6d;
    }

    .hearts {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      overflow: hidden;
    }

    .heart {
      position: absolute;
      font-size: 22px;
      animation: floatUp 6s linear infinite;
    }

    @keyframes floatUp {
      from {
        transform: translateY(100vh) scale(1);
        opacity: 1;
      }
      to {
        transform: translateY(-10vh) scale(1.5);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

<div class="container">

  <div class="photos">
    <img src="photo1.jpg" alt="Simon" />
    <img src="photo2.jpg" alt="Amelia" />
    <img src="photo3.jpg" alt="Simon & Amelia" />
  </div>

  <div class="card" id="card">
    <h1>Amelia 💖</h1>
    <p>Will you be my Valentine?<br/>Love, Big Sal</p>

    <div class="buttons">
      <button id="yesBtn">Yes 💘</button>
      <button id="noBtn">No 🙈</button>
    </div>
  </div>

  <div class="card success" id="success">
    <h2>Yay! 💕</h2>
    <p>I can't wait to spend Valentine's Day with you, Amelia 🥰<br/>Love, Big Sal</p>
  </div>

</div>

<div class="hearts" id="hearts"></div>

<audio id="bgMusic" src="kiss-from-a-rose.mp3" preload="auto"></audio>

<script>
  const noBtn = document.getElementById('noBtn');
  const yesBtn = document.getElementById('yesBtn');
  const card = document.getElementById('card');
  const success = document.getElementById('success');
  const heartsContainer = document.getElementById('hearts');
  const music = document.getElementById('bgMusic');

  noBtn.addEventListener('mouseover', () => {
    const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
    const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
    noBtn.style.position = 'fixed';
    noBtn.style.left = `${x}px`;
    noBtn.style.top = `${y}px`;
  });

  yesBtn.addEventListener('click', () => {
    card.style.display = 'none';
    success.style.display = 'block';
    music.play();
    startHearts();
  });

  function startHearts() {
    setInterval(() => {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.textContent = '❤️';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = Math.random() * 3 + 4 + 's';
      heartsContainer.appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }, 300);
  }
</script>

</body>
</html>
