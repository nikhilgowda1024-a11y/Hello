# Hello
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Valentine 💖</title>

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@400;600&display=swap" rel="stylesheet">

<style>
  * {
    box-sizing: border-box;
    user-select: none;
  }

  body {
    margin: 0;
    height: 100vh;
    overflow: hidden;
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(-45deg, #ff4ecd, #6a5cff, #00c6ff, #00f5a0);
    background-size: 400% 400%;
    animation: bgDance 12s ease infinite;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  @keyframes bgDance {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  .container {
    text-align: center;
    color: white;
    z-index: 10;
  }

  h1 {
    font-family: 'Pacifico', cursive;
    font-size: 3.4rem;
    margin-bottom: 40px;
    text-shadow: 0 8px 25px rgba(0,0,0,0.35);
  }

  .buttons {
    position: relative;
    width: 420px;
    height: 240px;
    margin: auto;
  }

  button {
    position: absolute;
    border: none;
    border-radius: 50px;
    padding: 16px 38px;
    font-size: 1.3rem;
    cursor: pointer;
    box-shadow: 0 12px 30px rgba(0,0,0,0.3);
    transition: transform 0.3s ease, opacity 0.3s ease;
  }

  #yes {
    background: linear-gradient(135deg, #00ff99, #00c6ff);
    color: #003;
    left: 50%;
    top: 40px;
    transform: translateX(-50%);
    z-index: 2;
  }

  #no {
    background: linear-gradient(135deg, #ff416c, #ff4b2b);
    color: white;
    left: 50%;
    top: 130px;
    transform: translateX(-50%);
    pointer-events: none;
  }

  .yay {
    display: none;
    font-family: 'Pacifico', cursive;
    font-size: 4.8rem;
    margin-top: 25px;
    animation: pop 0.8s ease forwards;
  }

  .gif {
    display: none;
    margin-top: 20px;
  }

  @keyframes pop {
    0% { transform: scale(0); opacity: 0; }
    100% { transform: scale(1); opacity: 1; }
  }

  /* Floating Hearts */
  .heart {
    position: absolute;
    bottom: -50px;
    font-size: 22px;
    animation: floatUp linear infinite;
    pointer-events: none;
    opacity: 0.9;
  }

  @keyframes floatUp {
    from {
      transform: translateY(0) scale(1);
      opacity: 1;
    }
    to {
      transform: translateY(-120vh) scale(1.6);
      opacity: 0;
    }
  }

  /* Confetti */
  .confetti {
    position: absolute;
    width: 10px;
    height: 10px;
    animation: fall 4s linear infinite;
  }

  @keyframes fall {
    0% { transform: translateY(-10vh) rotate(0deg); }
    100% { transform: translateY(110vh) rotate(360deg); }
  }
</style>
</head>

<body>

<div class="container">
  <h1>Priya, will you be my Valentine? 💖</h1>

  <div class="buttons">
    <button id="yes">YES 💘</button>
    <button id="no">NO 😏</button>
  </div>

  <div class="yay">YAY 🎉🥰</div>

  <div class="gif">
    <img src="https://media.giphy.com/media/26ufdipQqU2lhNA4g/giphy.gif" width="260">
  </div>
</div>

<script>
  const noBtn = document.getElementById("no");
  const yesBtn = document.getElementById("yes");
  const yay = document.querySelector(".yay");
  const gif = document.querySelector(".gif");

  let yesScale = 1;
  let noOpacity = 1;

  // NO button dances forever
  function danceNo() {
    const x = Math.random() * (window.innerWidth - 150);
    const y = Math.random() * (window.innerHeight - 150);
    const r = Math.random() * 360;

    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
    noBtn.style.transform = `rotate(${r}deg)`;
  }

  setInterval(danceNo, 500);

  document.addEventListener("mousemove", () => {
    yesScale += 0.005;
    yesBtn.style.transform = `translateX(-50%) scale(${yesScale})`;

    noOpacity -= 0.003;
    noBtn.style.opacity = noOpacity;
    if (noOpacity <= 0) noBtn.style.display = "none";
  });

  yesBtn.addEventListener("click", () => {
    noBtn.style.display = "none";
    yesBtn.style.display = "none";
    yay.style.display = "block";
    gif.style.display = "block";
    startConfetti();
  });

  // Floating hearts
  function createHeart() {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = ["💖","💘","💝","💕"][Math.floor(Math.random()*4)];
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = Math.random() * 18 + 18 + "px";
    heart.style.animationDuration = Math.random() * 3 + 4 + "s";
    document.body.appendChild(heart);

    setTimeout(() => heart.remove(), 7000);
  }

  setInterval(createHeart, 250);

  // Confetti explosion
  function startConfetti() {
    for (let i = 0; i < 80; i++) {
      const c = document.createElement("div");
      c.className = "confetti";
      c.style.left = Math.random() * 100 + "vw";
      c.style.backgroundColor = `hsl(${Math.random()*360},100%,50%)`;
      c.style.animationDuration = Math.random() * 2 + 3 + "s";
      document.body.appendChild(c);

      setTimeout(() => c.remove(), 5000);
    }
  }
</script>

</body>
</html>
