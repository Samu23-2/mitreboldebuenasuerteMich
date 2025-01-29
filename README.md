<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>San Valentín</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      text-align: center;
      background: linear-gradient(135deg, #ff7eb9, #ff758c);
      color: white;
      margin: 0;
      padding: 0;
      overflow: hidden;
    }
    h1 {
      margin-top: 50px;
      font-size: 3em;
    }
    .container {
      position: relative;
      margin-top: 20px;
    }
    .button {
      padding: 15px 30px;
      font-size: 1.5em;
      margin: 10px;
      cursor: pointer;
      border: none;
      border-radius: 10px;
      color: white;
      background-color: #ff4d4d;
      transition: background-color 0.3s;
    }
    .button:hover {
      background-color: #ff1a1a;
    }
    #noButton {
      position: absolute;
    }
    .fireworks {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      pointer-events: none;
      overflow: hidden;
    }
    .firework {
      position: absolute;
      width: 10px;
      height: 10px;
      background: yellow;
      border-radius: 50%;
      animation: explode 1s ease-out;
    }
    @keyframes explode {
      0% {
        transform: scale(1);
        opacity: 1;
      }
      100% {
        transform: scale(10);
        opacity: 0;
      }
    }
    .emoji {
      position: absolute;
      font-size: 2em;
      animation: float 5s ease-in-out infinite;
    }
    @keyframes float {
      0%, 100% {
        transform: translateY(0);
      }
      50% {
        transform: translateY(-20px);
      }
    }
  </style>
</head>
<body>
  <h1>¿Quieres ser mi San Valentín?</h1>
  <div class="container">
    <button class="button" id="yesButton">SÍ</button>
    <button class="button" id="noButton">NO</button>
  </div>
  <div class="fireworks" id="fireworks"></div>

  <script>
    const noButton = document.getElementById('noButton');
    const yesButton = document.getElementById('yesButton');
    const fireworksContainer = document.getElementById('fireworks');

    noButton.addEventListener('mouseover', () => {
      const x = Math.random() * (window.innerWidth - noButton.offsetWidth);
      const y = Math.random() * (window.innerHeight - noButton.offsetHeight);
      noButton.style.left = `${x}px`;
      noButton.style.top = `${y}px`;
    });

    yesButton.addEventListener('click', () => {
      // Mostrar emojis y fuegos artificiales
      for (let i = 0; i < 100; i++) {
        const emoji = document.createElement('div');
        emoji.classList.add('emoji');
        emoji.innerText = ['❤️', '🎉', '🎊', '💖', '🥳'][Math.floor(Math.random() * 5)];
        emoji.style.left = `${Math.random() * window.innerWidth}px`;
        emoji.style.top = `${Math.random() * window.innerHeight}px`;
        document.body.appendChild(emoji);
      }

      for (let i = 0; i < 50; i++) {
        const firework = document.createElement('div');
        firework.classList.add('firework');
        firework.style.left = `${Math.random() * window.innerWidth}px`;
        firework.style.top = `${Math.random() * window.innerHeight}px`;
        fireworksContainer.appendChild(firework);
        setTimeout(() => {
          firework.remove();
        }, 1000);
      }

      // Cambiar el texto del botón SÍ
      yesButton.innerText = '¡SABÍA QUE DIRÍAS QUE SÍ! ❤️';
      yesButton.disabled = true;
      noButton.style.display = 'none';
    });
  </script>
</body>
</html>
