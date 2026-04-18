# aayna-birthday
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aayna🌷</title>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: #0d1117;
  color: white;
  overflow: hidden;
}

/* Center */
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* Card */
.card {
  background: rgba(255,255,255,0.05);
  backdrop-filter: blur(15px);
  border-radius: 25px;
  padding: 25px;
  width: 320px;
  text-align: center;
}

/* Input */
input {
  width: 90%;
  padding: 12px;
  margin: 10px 0;
  border-radius: 12px;
  border: none;
  background: #161b22;
  color: white;
}

/* Button */
button {
  padding: 12px;
  width: 100%;
  border-radius: 25px;
  border: none;
  background: #7ee787;
  font-weight: bold;
  cursor: pointer;
  margin-top: 10px;
}

/* Main Page */
#mainPage {
  display: none;
  text-align: center;
  padding-top: 40px;
}

/* Image */
img {
  width: 260px;
  height: 260px;
  border-radius: 20px;
  object-fit: cover;
  margin: 15px 0;
  transition: opacity 1s ease-in-out;
}

/* Falling flowers */
.flower {
  position: fixed;
  top: -50px;
  font-size: 20px;
  animation: fall linear infinite;
}

@keyframes fall {
  to {
    transform: translateY(110vh);
  }
}
</style>
</head>

<body>

<!-- LOCK -->
<div class="center" id="lockScreen">
  <div class="card">
    <h2>🌷 Aayna🌷’s Surprise 🌷</h2>
    <p>This page is locked 🔐</p>

    <input id="password" type="password" placeholder="Enter Password">
    <button onclick="checkPassword()">Unlock 🔓</button>

    <p id="error" style="color:red;"></p>
  </div>
</div>

<!-- MAIN -->
<div id="mainPage">
  <h1>🌷 Happy Birthday Aayna🌷 🌸</h1>

  <p>
  No matter how far we are,<br>
  you are always in my thoughts.<br><br>
  This is for you ✨
  </p>

  <img id="slider" src="">

  <button onclick="playMusic()">Play Music 🎵</button>
</div>

<audio id="music">
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<script>
function checkPassword() {
  let pass = document.getElementById("password").value;

  if(pass === "2007") {
    document.getElementById("lockScreen").style.display = "none";
    document.getElementById("mainPage").style.display = "block";
    startSlider();
    createFlowers();
  } else {
    document.getElementById("error").innerText = "Wrong password ❌";
  }
}

/* Images */
let images = [
  "https://i.supaimg.com/58868626-3668-41a2-b05c-e3b339049dc6/91238b02-2c37-4cac-a931-db98bbb3d856.jpg",
  "https://i.supaimg.com/58868626-3668-41a2-b05c-e3b339049dc6/bce34474-9364-4e08-8faa-440d32d74297.jpg",
  "https://i.supaimg.com/58868626-3668-41a2-b05c-e3b339049dc6/c4163189-1108-4ba7-95fc-284a39b74df0.jpg",
  "https://i.supaimg.com/58868626-3668-41a2-b05c-e3b339049dc6/e2ceca87-37c9-480b-9f61-03acc091878a.jpg",
  "https://i.supaimg.com/58868626-3668-41a2-b05c-e3b339049dc6/0db79d27-5231-4df4-92d8-c9f52fead23e.jpg"
];

let index = 0;

function startSlider() {
  let img = document.getElementById("slider");
  img.src = images[index];

  setInterval(() => {
    img.style.opacity = 0;

    setTimeout(() => {
      index = (index + 1) % images.length;
      img.src = images[index];
      img.style.opacity = 1;
    }, 500);

  }, 3000);
}

/* Music */
function playMusic() {
  document.getElementById("music").play();
}

/* Falling Flowers */
function createFlowers() {
  for(let i = 0; i < 20; i++) {
    let flower = document.createElement("div");
    flower.className = "flower";
    flower.innerHTML = "🌷";

    flower.style.left = Math.random() * 100 + "vw";
    flower.style.animationDuration = (3 + Math.random() * 5) + "s";

    document.body.appendChild(flower);
  }
}
</script>

</body>
</html>
