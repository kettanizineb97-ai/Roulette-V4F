<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <title>Roue des mois – V4F</title>

  <style>
    * { box-sizing: border-box; font-family: Arial, Helvetica, sans-serif; }

    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #fdf2f8, #eef6ff);
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .container { text-align: center; }

    h1 { color: #ff6f91; }

    .wheel-wrapper {
      position: relative;
      width: 260px;
      height: 260px;
      margin: 30px auto;
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
      box-shadow: 0 10px 30px rgba(0,0,0,0.15);
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

    .result { display: none; }
    .month { color: #ff6f91; font-weight: bold; }
  </style>
</head>

<body>
  <div class="container">

    <div id="wheelScreen">
      <h1>Tournez la roue et découvrez quel mois vous sera attribué 😜</h1>

      <div class="wheel-wrapper">
        <div class="pointer"></div>
        <canvas id="wheel" width="260" height="260"></canvas>
      </div>

      <button id="spinBtn">Tourner</button>
    </div>

    <div id="resultScreen" class="result">
      <h1>🎉 Félicitations 🎉</h1>
      <div id="bmName"></div>

      <p>👉 Tu auras des accès admin sur LinkedIn tout au long du mois de
        <span class="month" id="monthResult"></span>.
      </p>

      <p><strong>250 crédits</strong> te seront accordés au courant de ce mois.</p>

      <p>À toi d’envoyer les demandes de suivi de la page <strong>LinkedIn V4F</strong>.</p>

      <p><strong>Merci à toi de donner un coup de boost à la visibilité de V4F !</strong></p>
    </div>

  </div>

<script>
  /* ✅ Mapping verrouillé */
  const mapping = {
    Fanny: 0,     // Février
    Anas: 1,      // Mars
    Clémence: 2,  // Avril
    Thomas: 3,    // Mai
    Tariq: 4      // Juin
  };

  const months = ["Février", "Mars", "Avril", "Mai", "Juin"];
  const colors = ["#ffc6d9", "#9be7c4", "#ffe066", "#cdb4ff", "#ffd6a5"];

  const canvas = document.getElementById("wheel");
  const ctx = canvas.getContext("2d");
  const center = 130;
  const radius = 130;
  const slice = (2 * Math.PI) / months.length;

  let rotation = -Math.PI / 2; // 🔑 ALIGNEMENT INITIAL AVEC LE CURSEUR

  const bmName = prompt("Entre ton prénom :");

  if (!(bmName in mapping)) {
    alert("Prénom non reconnu.");
    location.reload();
  }

  function drawWheel(angle) {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    months.forEach((month, i) => {
      const start = angle + i * slice;
      const end = start + slice;

      ctx.beginPath();
      ctx.moveTo(center, center);
      ctx.arc(center, center, radius, start, end);
      ctx.fillStyle = colors[i];
      ctx.fill();

      ctx.save();
      ctx.translate(center, center);
      ctx.rotate(start + slice / 2);
      ctx.textAlign = "right";
      ctx.font = "16px Arial";
      ctx.fillStyle = "#333";
      ctx.fillText(month, radius - 25, 5);
      ctx.restore();
    });
  }

  drawWheel(rotation);

  document.getElementById("spinBtn").onclick = () => {
    const index = mapping[bmName];
    const target =
      -Math.PI / 2
      - index * slice
      + 3 * 2 * Math.PI;

    const start = rotation;
    const duration = 3000;
    let startTime = null;

    function animate(t) {
      if (!startTime) startTime = t;
      const p = Math.min((t - startTime) / duration, 1);
      rotation = start + (target - start) * p;
      drawWheel(rotation);

      if (p < 1) requestAnimationFrame(animate);
      else setTimeout(() => showResult(index), 5000);
    }

    requestAnimationFrame(animate);
  };

  function showResult(index) {
    document.getElementById("wheelScreen").style.display = "none";
    document.getElementById("resultScreen").style.display = "block";
    document.getElementById("monthResult").textContent = months[index];
    document.getElementById("bmName").textContent = bmName;
  }
</script>

</body>
</html>
