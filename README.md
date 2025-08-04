<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Telegram Mini App with Giga.pub Ads</title>

  <!-- ✅ Telegram SDK -->
  <script src="https://telegram.org/js/telegram-web-app.js"></script>

  <!-- ✅ Your Giga.pub Ad Script (ID 1263) -->
  <script src="https://ad.gigapub.tech/script?id=1263"></script>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f2f5;
      padding: 20px;
      text-align: center;
    }

    button {
      background-color: #0088cc;
      color: white;
      border: none;
      padding: 14px 24px;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 30px;
    }

    button:hover {
      background-color: #0070aa;
    }
  </style>
</head>
<body>
  <h2>🚀 Telegram Mini App</h2>
  <p id="welcome">Loading...</p>

  <!-- ✅ Button to show ad -->
  <button onclick="showRewardedAd()">🎥 Watch Ad & Earn</button>

  <script>
    // Telegram init
    const tg = window.Telegram.WebApp;
    tg.ready();
    tg.expand();

    const user = tg.initDataUnsafe?.user;
    document.getElementById("welcome").innerText =
      user ? `Welcome, ${user.first_name}!` : "Welcome, guest!";

    // ✅ Show Ad using Giga script
    function showRewardedAd() {
      if (typeof Giga !== 'undefined') {
        Giga.showAd({
          type: "rewarded",
          onComplete: () => {
            alert("✅ You've earned 10 points!");
          },
          onError: (err) => {
            alert("❌ Ad failed to load.");
            console.error(err);
          }
        });
      } else {
        alert("⚠️ Giga script not loaded!");
      }
    }
  </script>
</body>
</html>
