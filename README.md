<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>ウイルス警告！？ドッキリ</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background-image: url('IMG_0222.webp');
      background-size: cover;
      background-position: center;
    }
    .popup {
      position: absolute;
      background-color: white;
      border: 2px solid red;
      padding: 10px;
      font-weight: bold;
      box-shadow: 0 0 10px rgba(255,0,0,0.7);
      z-index: 1000;
    }
    .start-button {
      position: absolute;
      top: 40%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 20px 40px;
      font-size: 18px;
      background-color: crimson;
      color: white;
      border: none;
      border-radius: 10px;
      box-shadow: 0 0 10px crimson;
      z-index: 2000;
    }
  </style>
</head>
<body>
  <button class="start-button" onclick="startPrank()">スタート</button>

  <audio id="alertSound" loop>
    <source src="https://www.soundjay.com/button/beep-10.mp3" type="audio/mpeg">
  </audio>

  <script>
    function createPopup() {
      const popup = document.createElement('div');
      popup.classList.add('popup');
      popup.style.left = Math.random() * window.innerWidth + 'px';
      popup.style.top = Math.random() * window.innerHeight + 'px';
      popup.innerHTML = '⚠️ ウイルスを検出しました！';
      document.body.appendChild(popup);
    }

    function startPrank() {
      document.querySelector('.start-button').style.display = 'none';

      const sound = document.getElementById('alertSound');
      sound.play();

      setInterval(() => {
        for (let i = 0; i < 10; i++) {
          createPopup();
        }
      }, 1000);
    }
  </script>
</body>
</html>

