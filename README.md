<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Giga.pub Telegram Mini App</title>

  <!-- Telegram SDK -->
  <script src="https://telegram.org/js/telegram-web-app.js"></script>

  <!-- ✅ Giga.pub Script -->
  <script src="https://ad.gigapub.tech/script?id=1263" defer></script>

  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      padding: 40px;
      background: #f2f2f2;
    }

    button {
      background-color: #0088cc;
      color: white;
      padding: 14px 28px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 30px;
    }

    button:hover {
      background-color: #006fa1;
    }
  </style>
</head>
<body>
  <h2>🎬 Watch & Earn</h2>
  <p id="status">Loading Telegram user...</p>

  <button onclick="showAd()">🎥 Watch Ad</button>

  <script>
    // ✅ Telegram init
    const tg = window.Telegram.WebApp;
    tg.ready();
    tg.expand();

    const user = tg.initDataUnsafe?.user;
    document.getElementById("status").innerText = user
      ? `Hello, ${user.first_name}!`
      : 'Welcome, Guest!';

    // ✅ Giga Ad show logic
    function showAd() {
      if (typeof window.showGiga === 'function') {
        window.showGiga()
          .then(() => {
            alert('✅ Ad watched! Reward granted.');
          })
          .catch((err) => {
            console.error('Ad error:', err);
            alert('❌ Failed to load ad.');
          });
      } else {
        alert('⚠️ Ad system not loaded yet.');
      }
    }
  </script>
</body>
</html>
