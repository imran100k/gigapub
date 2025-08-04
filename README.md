<!DOCTYPE html>
<html lang="en">
<head>
  
<script src="https://ad.gigapub.tech/script?id=1263"></script>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Telegram Mini App with Giga.pub Ads</title>

  <!-- Telegram WebApp SDK -->
  <script src="https://telegram.org/js/telegram-web-app.js"></script>

  <!-- Giga.pub SDK -->
  <script src="https://sdk.giga.pub/webapp.js"></script>

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
      padding: 12px 24px;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h2>🚀 Telegram Mini App</h2>
  <p id="welcome">Loading...</p>

  <button onclick="showRewardedAd()">🎥 Watch Ad to Earn</button>

  <script>
    // Initialize Telegram
    const tg = window.Telegram.WebApp;
    tg.ready();  // Required by Telegram
    tg.expand();

    const user = tg.initDataUnsafe.user;
    if (user) {
      document.getElementById("welcome").innerText = `Welcome, ${user.first_name || 'User'}!`;
    } else {
      document.getElementById("welcome").innerText = "Welcome, Guest!";
    }

    // Show Rewarded Ad
    function showRewardedAd() {
      if (typeof Giga !== 'undefined') {
        Giga.showAd({
          type: "rewarded",
          onComplete: () => {
            alert("✅ Thanks! You've earned points.");
          },
          onError: (err) => {
            console.error("Ad Error:", err);
            alert("❌ Ad failed to load.");
          }
        });
      } else {
        alert("⚠️ Giga.pub SDK not loaded!");
      }
    }
  </script>
</body>
</html>
