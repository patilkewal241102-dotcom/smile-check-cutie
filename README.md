<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>For Jenso 💖</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #fff5f8;
      padding: 50px;
      overflow: hidden;
      margin: 0;
    }

    h1 {
      font-size: 2.4rem;
      margin-bottom: 25px;
      min-height: 70px;
      position: relative;
      z-index: 2;
    }

    #message {
      font-size: 1.4rem;
      margin: 25px auto;
      max-width: 650px;
      line-height: 1.7;
      white-space: pre-line;
      min-height: 90px;
      position: relative;
      z-index: 2;
    }

   /* ✅ FIXED GIF SIZE */ 
    img {
      margin-top: 20px;
      width: 280px;
      height: 220px;
      object-fit: contain;
      border-radius: 20px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.2);
      display: none;
       /* ✅ ADD THESE */
      margin-left: auto;
      margin-right: auto;
      position: relative;
      z-index: 2;
      background: white;
      padding: 8px;
    }

    button {
      padding: 12px 28px;
      font-size: 1rem;
      border: none;
      border-radius: 25px;
      background: #ff4d6d;
      color: white;
      cursor: pointer;
      margin-top: 25px;
      animation: floaty 1.6s ease-in-out infinite;
      position: relative;
      z-index: 2;
    }

    #contentBox {
      max-width: 700px;
      margin: 0 auto;
      padding: 25px;
      border-radius: 25px;
      background: rgba(255, 255, 255, 0.7);
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    }


    @keyframes floaty {
      0%   { transform: translateY(0px); }
      50%  { transform: translateY(-6px); }
      100% { transform: translateY(0px); }
    }

    /* 👀 Shake animation */
    .shake {
      display: inline-block;
      animation: shake 0.3s infinite;
    }

    @keyframes shake {
      0% { transform: translate(0, 0); }
      25% { transform: translate(2px, -2px); }
      50% { transform: translate(-2px, 2px); }
      75% { transform: translate(2px, 2px); }
      100% { transform: translate(0, 0); }
    }

    /* 💗 Floating Hearts */
    .heart {
      position: absolute;
      font-size: 22px;
      animation: floatUp 4s linear infinite;
      opacity: 0.8;
      z-index: 1;
    }

    @keyframes floatUp {
      0% { transform: translateY(0); opacity: 0.9; }
      100% { transform: translateY(-700px); opacity: 0; }
    }

    #finalSection {
      display: none;
      margin-top: 35px;
      position: relative;
      z-index: 2;
    }

    #noReply {
      margin-top: 20px;
      font-size: 1.2rem;
      min-height: 40px;
    }
  </style>
</head>

<body>

  <h1 id="title"></h1>
  <div id="contentBox">
  <div id="message"></div>
  <img id="photo" src="" alt="gif"/>
  </div>


  <button id="nextBtn" onclick="nextLine()">Next ➝</button>

  <!-- Final Yes/No Section -->
  <div id="finalSection">
    <div style="font-size:1.4rem; margin-bottom:20px;">
      Be honest… You smiled a little, didn’t you? 👀
    </div>

    <button onclick="yesClicked()">Yes 🤍</button>
    <button id="noBtn" onclick="noClicked()">No 🙄</button>

    <div id="noReply"></div>
  </div>

  <script>
    /* --- INTRO TYPING --- */
    const introText = "heyyyyyyyyyyyyyyyyy ";
    let introIndex = 0;
    let introDone = false;

    function typeIntro() {
      if (introIndex < introText.length) {
        document.getElementById("title").innerText += introText[introIndex];
        introIndex++;
        setTimeout(typeIntro, 120);
      } else {
        document.getElementById("title").innerHTML +=
          `<span class="shake">👀</span>`;
        document.getElementById("message").innerText =
          "Click next 😌";
        introDone = true;
      }
    }
    typeIntro();

    /* --- STORY STAGES --- */
    let stage = 0; // 0=intro, 1=valentine card, 2=story

    /* --- STORY LINES --- */
    const lines = [
      { text: "This isn’t a big question.", img: "gif0.gif" },
      { text: "Just a small message from me…", img: "gif00.gif" },
      { text: "I’m really grateful that you’re in my life.", img: "gif1.gif" },
      { text: "I just wanted to remind you that you’re a very special person to me.", img: "gif1.gif" },
      { text: "And you genuinely matter to me more than you probably realize,\nyou ungrateful potato😚", img: "gif3.gif" },
      { text: "No pressure, no expectations —\njust appreciation, warmth, and a lot of care 🌹", img: "gif4.gif" },
      { text: "found my favorite person 🤍", img: "collage.jpg" }
    ];

    let index = 0;

    /* --- PRELOAD GIFS FOR INSTANT SWITCHING --- */
const preloadImages = [
  "gif0.gif",
  "gif00.gif",
  "gif1.gif",
  "gif3.gif",
  "gif4.gif",
  "collage.jpg"
];

preloadImages.forEach(src => {
  const img = new Image();
  img.src = src;
});


    /* --- HEARTS --- */
    function startHearts() {
      for (let i = 0; i < 18; i++) {
        let heart = document.createElement("div");
        heart.className = "heart";
        heart.innerHTML = "💗";
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.top = (Math.random() * 400 + 200) + "px";
        heart.style.animationDuration = (3 + Math.random() * 2) + "s";
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 5000);
      }
    }

    /* --- NEXT BUTTON --- */
    function nextLine() {
      if (!introDone) return;

      // Valentine Title Card Screen
      if (stage === 0) {
        document.getElementById("title").innerText =
          "💖 Happy Valentine’s Day, Jenso";
        document.getElementById("message").innerText = "";
        startHearts();
        stage = 1;
        return;
      }

      // Hide title and start story
      if (stage === 1) {
        document.getElementById("title").style.display = "none";
        stage = 2;
      }

      // Show Story
      if (index < lines.length) {
        document.getElementById("message").innerText =
          lines[index].text;

        const photo = document.getElementById("photo");

        if (lines[index].img !== "") {
          // Hide old GIF instantly
          photo.style.display = "none";

          // Show new GIF only when loaded
          photo.onload = () => {
          photo.style.display = "block";
          };

photo.src = lines[index].img;

        }

        index++;
      }

      // End → Final Section
      else {
        document.getElementById("message").style.display = "none";
        document.getElementById("photo").style.display = "none";
        document.getElementById("nextBtn").style.display = "none";

        document.getElementById("finalSection").style.display = "block";
      }
    }

    /* --- FINAL YES/NO --- */
    let noCount = 0;
    let escapeMode = false;

    const noBtn = document.getElementById("noBtn");

    // Hover runaway after escapeMode is true
    noBtn.addEventListener("mouseover", () => {
      if (!escapeMode) return;

      const x = Math.random() * (window.innerWidth - 140);
      const y = Math.random() * (window.innerHeight - 80);

      noBtn.style.position = "absolute";
      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
    });

    function yesClicked() {
      document.getElementById("noReply").innerText =
        "Hehe… that’s all I wanted 😌🤍\njust a little smile.";
    }

    function noClicked() {
      noCount++;

      const reply = document.getElementById("noReply");

      if (noCount === 1) {
        reply.innerText = "I bet you’re smiling right now 😙";
      }
      else if (noCount === 2) {
        reply.innerText = "you liarrrrrrrrrr 🥺";
      }
      else if (noCount === 3) {
        reply.innerText = "c’monnnnnnnnn😩";
      }
      else {
        reply.innerText = "nope 😈 you’re not clicking No anymore.";
        escapeMode = true;
      }
    }
  </script>

</body>
</html>
