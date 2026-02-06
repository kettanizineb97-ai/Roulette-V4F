<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <title>Roue des mois – V4F</title>

  <style>
    * {
      box-sizing: border-box;
      font-family: Arial, Helvetica, sans-serif;
    }

    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #fdf2f8, #eef6ff);
      display: flex;
      align-items: center;
      justify-content: center;
      color: #111;
    }

    .container {
      text-align: center;
      max-width: 600px;
      width: 100%;
      padding: 40px 20px;
    }

    h1 {
      color: #ff6f91;
      margin-bottom: 10px;
    }

    .bm-name {
      font-size: 18px;
      margin-bottom: 20px;
    }

    .wheel-wrapper {
      position: relative;
      margin: 0 auto 30px;
      width: 260px;
      height: 260px;
    }

    .pointer {
      position: absolute;
      top: -12px;
      left: 50%;
      transform: translateX(-50%);
      width: 0;
      height: 0;
      border-left: 12px solid transparent;
      border-right: 12px solid transparent;
      border-bottom: 20px solid #ff6f91;
      z-index: 10;
    }

    canvas {
      border-radius: 50%;
      background: white;
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    }

    button {
      padding: 14px 26px;
      border-radius: 30px;
      border: none;
      background: linear-gradient(135deg, #ff6f91, #ff9671);
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    button:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }

    .result {
      display: none;
    }

    .month {
      font-weight: bold;
      color: #ff6f91;
    }
  </style>
</head>

<body>
  <div class="container">

    <!-- ÉCRAN ROUE -->
    <div id="wheelScreen">
      <h1>Tournez la roue et découvrez quel mois vous sera attribué 😜</h1>

      <div class="wheel-wrapper">
        <div class="pointer"></div>
        <canvas id="wheel" width="260" height="260"></canvas>
      </div>

      <button id="spinBtn">Tourner</button>
    </div>

    <!-- ÉCRAN RÉSULTAT -->
    <div id="resultScreen" class="result">
      <h1>🎉 Félicitations 🎉</h1>
      <div class="bm-name" id="bmName"></div>

      <p>
        👉 Tu auras des accès admin sur LinkedIn tout au long du mois de
        <span class="month" id="monthResult"></span>.
      </p>

      <p><strong>250 crédits</strong> te seront accordés au courant de ce mois.</p>

      <p>
        À toi d’envoyer les demandes de suivi de la page
        <strong>LinkedIn V4F</strong> à ton réseau.
      </p>

      <p>
        <strong>Merci à toi de donner un coup de boost à la visibilité de V4F !</strong>
      </p>
    </div>

  </div>

  <script>
    /* ATTRIBUTIONS FIXES (MASQUÉES) */
    const mapping = {
      "Fanny": "Février",
      "Anas": "Mars",
      "Clémence": "Avril",
      "Thomas": "Mai",
      "Tariq": "Juin"
    };

    const months = ["Février", "Mars", "Avril", "Mai", "Juin"];
    const colors = ["#ffc6d9", "#9be7c4", "#ffe066", "#cdb4ff", "#ffd6a5"];

    const canvas = document.getElementById("wheel");
    const ctx = canvas.getContext("2d");
    const spinBtn = document.getElementById("spinBtn");

    let angle = 0;

    const bmName = prompt("Entre ton prénom :");

    if (!mapping[bmName]) {
      alert("Prénom non reconnu.");
      location.reload();
    }

    function drawWheel() {
      const slice = (2 * Math.PI) / months.length;
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      months.forEach((month, i) => {
        ctx.beginPath();
        ctx.moveTo(130, 130);
        ctx.arc(130, 130, 130, slice * i, slice * (i + 1));
        ctx.fillStyle = colors[i];
        ctx.fill();

        ctx.save();
        ctx.translate(130, 130);
        ctx.rotate(slice * i + slice / 2);
        ctx.textAlign = "right";
        ctx.font = "16px Arial"; // +2px
        ctx.fillStyle = "#333";
        ctx.fillText(month, 105, 5); // rapproché du centre
        ctx.restore();
      });
    }

    drawWheel();

    spinBtn.addEventListener("click", () => {
      spinBtn.disabled = true;

      const targetMonth = mapping[bmName];
      const monthIndex = months.indexOf(targetMonth);
      const sliceDeg = 360 / months.length;

      const targetAngle =
        360 * 4 +
        (360 - (monthIndex * sliceDeg + sliceDeg / 2));

      let start = angle;
      let end = (targetAngle * Math.PI) / 180;
      let duration = 2000;
      let startTime = null;

      function animate(time) {
        if (!startTime) startTime = time;
        let progress = (time - startTime) / duration;

        if (progress < 1) {
          angle = start + (end - start) * progress;
          ctx.setTransform(1, 0, 0, 1, 0, 0);
          ctx.translate(130, 130);
          ctx.rotate(angle);
          ctx.translate(-130, -130);
          drawWheel();
          requestAnimationFrame(animate);
        } else {
          // Pause de 3 secondes avant l'écran résultat
          setTimeout(() => {
            showResult(targetMonth);
          }, 3000);
        }
      }

      requestAnimationFrame(animate);
    });

    function showResult(month) {
      document.getElementById("wheelScreen").style.display = "none";
      document.getElementById("resultScreen").style.display = "block";
      document.getElementById("monthResult").textContent = month;
      document.getElementById("bmName").textContent = bmName;
    }
  </script>
</body>
</html>
