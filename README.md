<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Faiza, Will You Be My Valentine? 💖</title>
  <style>
    :root{
      --bg1:#ffdde1;
      --bg2:#ee9ca7;
      --card:rgba(255,255,255,.78);
      --text:#222;
      --shadow:0 20px 70px rgba(0,0,0,.18);
      --hot:#ff2f77;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;
      min-height:100vh;
      display:grid;
      place-items:center;
      padding:24px;
      background:linear-gradient(135deg,var(--bg1),var(--bg2));
      overflow:hidden;
    }
    .hearts{
      position:fixed; inset:0;
      pointer-events:none;
      opacity:.22;
      font-size:28px;
      filter: blur(.1px);
      animation: float 8s linear infinite;
      white-space:nowrap;
    }
    .hearts:nth-child(2){opacity:.16; font-size:34px; animation-duration:11s}
    .hearts:nth-child(3){opacity:.12; font-size:40px; animation-duration:14s}
    @keyframes float{
      from{transform:translateX(-10%) translateY(0)}
      to{transform:translateX(10%) translateY(-25%)}
    }

    .card{
      width:min(560px,100%);
      background:var(--card);
      backdrop-filter: blur(12px);
      border:1px solid rgba(255,255,255,.6);
      border-radius:26px;
      box-shadow:var(--shadow);
      padding:28px 22px;
      text-align:center;
      position:relative;
      overflow:hidden;
    }
    .badge{
      display:inline-flex;
      gap:8px;
      align-items:center;
      padding:10px 14px;
      border-radius:999px;
      background:rgba(255,255,255,.75);
      font-weight:800;
      letter-spacing:.2px;
    }
    h1{
      margin:14px 0 8px;
      font-size:2.1rem;
      color:var(--text);
      line-height:1.15;
    }
    .sub{
      margin:0 0 18px;
      color:rgba(0,0,0,.65);
      font-size:1.05rem;
    }

    .stage{
      position:relative;
      margin-top:10px;
      height:120px;
    }
    .buttons{
      display:flex;
      gap:14px;
      justify-content:center;
      flex-wrap:wrap;
      margin:0;
      position:relative;
      z-index:2;
    }
    .btn{
      border:0;
      padding:14px 22px;
      border-radius:16px;
      font-size:1.05rem;
      cursor:pointer;
      transition:transform .15s ease, box-shadow .15s ease;
      box-shadow:0 12px 22px rgba(0,0,0,.14);
      user-select:none;
      touch-action:manipulation;
    }
    .btn:hover{transform:translateY(-2px); box-shadow:0 16px 26px rgba(0,0,0,.18)}
    .yes{background:var(--hot); color:#fff;}
    .no{background:rgba(255,255,255,.92); color:#333; position:absolute; left:50%; top:54%; transform:translate(-50%,-50%);}

    .hint{
      margin-top:8px;
      font-size:.98rem;
      opacity:.75;
    }

    .result{
      margin-top:18px;
      padding:18px 14px;
      border-radius:18px;
      background:rgba(255,255,255,.8);
      border:1px solid rgba(255,255,255,.65);
      animation: pop .35s ease forwards;
    }
    .hidden{display:none}
    @keyframes pop{from{transform:scale(.98); opacity:0} to{transform:scale(1); opacity:1}}

    .big{
      font-size:1.6rem;
      font-weight:900;
      margin-bottom:8px;
    }
    .tiny{
      opacity:.78;
      margin-top:10px;
      font-size:.95rem;
      font-weight:700;
    }
    .footer{margin-top:16px; font-size:.95rem; opacity:.7}

    /* Confetti */
    .confetti{
      position:fixed;
      inset:0;
      pointer-events:none;
      overflow:hidden;
      display:none;
    }
    .confetti.show{display:block;}
    .piece{
      position:absolute;
      top:-10px;
      width:10px;
      height:14px;
      opacity:.95;
      transform:rotate(0deg);
      animation: fall 1.6s linear forwards;
    }
    @keyframes fall{
      to{transform:translateY(110vh) rotate(720deg); opacity:1}
    }
  </style>
</head>

<body>
  <div class="hearts">💗 💖 💘 💝 💞 💓 💕 💗 💖 💘 💝 💞 💓 💕</div>
  <div class="hearts">💖 💘 💝 💞 💓 💕 💖 💘 💝 💞 💓 💕</div>
  <div class="hearts">💘 💝 💞 💓 💕 💘 💝 💞 💓 💕</div>

  <div class="confetti" id="confetti"></div>

  <div class="card" id="card">
    <div class="badge">💌 For Faiza 💌 <span>✨</span></div>

    <h1>Faiza… will you be my Valentine? 💖</h1>
    <p class="sub">From Sikander 💘</p>

    <div class="stage" id="stage">
      <div class="buttons">
        <button id="yesBtn" class="btn yes">Yes 😍</button>
      </div>

      <button id="noBtn" class="btn no">No 😅</button>
    </div>

    <div class="hint" id="hint">P.S. Try pressing “No” 🙈</div>

    <div id="result" class="result hidden">
      <div class="big">YAY, FAIZA!! 🎉💘</div>
      <p>
        You’re my favorite person, always. 🥹❤️<br/>
        Valentine’s is officially ours — dinner 🍽️ + dessert 🍰 + a surprise 🎁
      </p>
      <p class="tiny">Love you — Sikander 🫶</p>
    </div>

    <div class="footer">Made with love ✨💗</div>
  </div>

  <script>
    const yesBtn = document.getElementById("yesBtn");
    const noBtn = document.getElementById("noBtn");
    const result = document.getElementById("result");
    const stage = document.getElementById("stage");
    const hint = document.getElementById("hint");
    const confetti = document.getElementById("confetti");

    const noTexts = [
      "No 😅",
      "Wait… No? 🥺",
      "Are you sure? 😭",
      "Pleaseee? 🙏🥹",
      "Faiza… 😳",
      "Okay fine… YES? 😇"
    ];
    let noCount = 0;

    yesBtn.addEventListener("click", () => {
      result.classList.remove("hidden");
      hint.textContent = "Best answer ever 😍💖";
      yesBtn.disabled = true;
      noBtn.disabled = true;
      yesBtn.textContent = "Yes 😍 (locked in!)";
      launchConfetti();
    });

    // Move the NO button on hover/tap
    noBtn.addEventListener("mouseenter", moveNo);
    noBtn.addEventListener("click", (e) => {
      e.preventDefault();
      moveNo(true);
    });

    function moveNo(onClick=false){
      const rect = stage.getBoundingClientRect();
      const btn = noBtn.getBoundingClientRect();

      const pad = 10;
      const maxX = rect.width - btn.width - pad * 2;
      const maxY = rect.height - btn.height - pad * 2;

      const x = pad + Math.random() * maxX;
      const y = pad + Math.random() * maxY;

      noBtn.style.left = `${x}px`;
      noBtn.style.top  = `${y}px`;
      noBtn.style.transform = "translate(0,0)";

      // Change text a bit each time
      noCount++;
      noBtn.textContent = noTexts[Math.min(noCount, noTexts.length-1)];

      if (onClick && noCount >= 3) {
        hint.textContent = "No is not an option today 😄💘";
      }
    }

    function launchConfetti(){
      confetti.innerHTML = "";
      confetti.classList.add("show");
      const colors = ["#ff2f77","#ffcc00","#7c3aed","#22c55e","#06b6d4","#fb7185"];

      for(let i=0;i<120;i++){
        const p = document.createElement("div");
        p.className = "piece";
        p.style.left = Math.random()*100 + "vw";
        p.style.background = colors[Math.floor(Math.random()*colors.length)];
        p.style.animationDelay = (Math.random()*0.6) + "s";
        p.style.width = (6 + Math.random()*8) + "px";
        p.style.height = (8 + Math.random()*10) + "px";
        p.style.borderRadius = (Math.random() > 0.6) ? "999px" : "2px";
        confetti.appendChild(p);
      }

      setTimeout(() => confetti.classList.remove("show"), 2200);
    }
  </script>
</body>
</html>
