<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cookie Clicker 101</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: #222;
      color: #fff;
      font-family: monospace;
      text-align: center;
      height: 100vh;
      overflow: hidden;
    }
    h1 {
      margin-top: 20px;
      font-size: 24px;
    }
    #cookie {
      font-size: 100px;
      cursor: pointer;
      margin: 30px 0;
      user-select: none;
    }
    #stats {
      font-size: 18px;
    }
    #upgrade {
      margin-top: 20px;
      padding: 10px 20px;
      background: #444;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-family: monospace;
    }
    #upgrade:disabled {
      background: #333;
      color: #888;
      cursor: default;
    }
  </style>
</head>
<body>
  <h1>Cookie Clicker 101</h1>
  <div id="cookie">🍪</div>
  <div id="stats">
    Cookies: <span id="count">0</span><br>
    Cookies per click: <span id="cpc">1</span>
  </div>
  <button id="upgrade" disabled>Upgrade Click (Cost: 50)</button>

  <script>
    let cookies = 0;
    let cookiesPerClick = 1;
    let upgradeCost = 50;

    const cookie = document.getElementById("cookie");
    const countSpan = document.getElementById("count");
    const cpcSpan = document.getElementById("cpc");
    const upgradeBtn = document.getElementById("upgrade");

    cookie.onclick = () => {
      cookies += cookiesPerClick;
      update();
    };

    upgradeBtn.onclick = () => {
      if (cookies >= upgradeCost) {
        cookies -= upgradeCost;
        cookiesPerClick++;
        upgradeCost = Math.floor(upgradeCost * 1.5);
        update();
      }
    };

    function update() {
      countSpan.textContent = cookies;
      cpcSpan.textContent = cookiesPerClick;
      upgradeBtn.textContent = `Upgrade Click (Cost: ${upgradeCost})`;
      upgradeBtn.disabled = cookies < upgradeCost;
    }
  </script>
</body>
</html>

