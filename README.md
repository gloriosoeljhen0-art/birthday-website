<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>happy birthday baby 💕</title>

<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">

<style>
/* =========================
   GLOBAL STYLES
========================= */
*{margin:0;padding:0;box-sizing:border-box;}
body{
  font-family: Inter, sans-serif;
  background:#0b0b10;
  color:#fff;
  overflow-x:hidden;
}

/* Loading Screen */
#loader{
  position:fixed;
  inset:0;
  background:#0b0b10;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  z-index:9999;
}
.loader-text{
  font-family:'Playfair Display', serif;
  font-size:22px;
  margin-top:15px;
  opacity:0.8;
}

/* Hero */
.hero{
  height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  text-align:center;
  flex-direction:column;
  background: radial-gradient(circle at top,#1b1b2a,#0b0b10);
  position:relative;
  overflow:hidden;
}
.hero h1{
  font-family:'Playfair Display', serif;
  font-size:3rem;
}
.hero p{
  opacity:0.7;
  margin-top:10px;
}

/* Floating hearts */
.heart{
  position:absolute;
  color:pink;
  animation:floatUp 6s linear infinite;
}
@keyframes floatUp{
  0%{transform:translateY(100vh) scale(0.5);opacity:0;}
  30%{opacity:1;}
  100%{transform:translateY(-10vh) scale(1.2);opacity:0;}
}

/* Sections */
section{
  padding:80px 20px;
  max-width:1000px;
  margin:auto;
}

/* Glass cards */
.card{
  background:rgba(255,255,255,0.06);
  backdrop-filter: blur(10px);
  border:1px solid rgba(255,255,255,0.1);
  border-radius:20px;
  padding:20px;
}

/* Gallery */
.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
  gap:10px;
}
.gallery img{
  width:100%;
  border-radius:15px;
  cursor:pointer;
  transition:0.3s;
}
.gallery img:hover{transform:scale(1.05);}

/* Lightbox */
#lightbox{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.9);
  display:none;
  justify-content:center;
  align-items:center;
}
#lightbox img{
  max-width:90%;
  max-height:80%;
  border-radius:10px;
}

/* Timeline */
.timeline{
  border-left:2px solid rgba(255,255,255,0.2);
  margin-left:20px;
}
.event{
  margin:20px;
  padding-left:20px;
}

/* Cake */
.cake-container{
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
}
.cake{
  width:200px;
  height:120px;
  background:pink;
  border-radius:10px;
  position:relative;
}
.candle{
  width:10px;
  height:40px;
  background:gold;
  position:absolute;
  top:-40px;
  left:50%;
  transform:translateX(-50%);
}
.flame{
  width:15px;
  height:15px;
  background:orange;
  border-radius:50%;
  position:absolute;
  top:-55px;
  left:50%;
  transform:translateX(-50%);
  animation: flicker 0.3s infinite;
}
@keyframes flicker{
  0%{transform:translateX(-50%) scale(1);}
  50%{transform:translateX(-50%) scale(1.2);}
  100%{transform:translateX(-50%) scale(1);}
}

/* Button */
button{
  padding:10px 20px;
  border:none;
  border-radius:10px;
  background:#ff4d8d;
  color:white;
  cursor:pointer;
  margin-top:10px;
}

/* Music control */
.music{
  position:fixed;
  bottom:20px;
  right:20px;
}
</style>
</head>

<body>

<!-- LOADER -->
<div id="loader">
  <h1>Loading Memories...</h1>
  <div class="loader-text">for my baby 💕</div>
</div>

<!-- HERO -->
<div class="hero">
  <h1>happy 19th birthday, baby 💕</h1>
  <p>Made with love by Elie</p>
</div>

<!-- LETTER -->
<section>
  <div class="card">
    <h2 style="font-family:'Playfair Display';">A Letter for You</h2>
    <p>
      Hi Juvy,  
      I made this website because I can't be there physically, but I want you to feel how important you are to me.  
      Every memory, every laugh, every moment — I kept it here. 💖
    </p>
  </div>
</section>

<!-- GALLERY -->
<section>
  <h2 style="text-align:center;margin-bottom:20px;">Our Memories</h2>
  <div class="gallery">
    <img src="https://placekitten.com/300/300" onclick="openImg(this.src)">
    <img src="https://placekitten.com/301/300" onclick="openImg(this.src)">
    <img src="https://placekitten.com/302/300" onclick="openImg(this.src)">
    <img src="https://placekitten.com/303/300" onclick="openImg(this.src)">
  </div>
</section>

<!-- CAKE -->
<section>
  <div class="cake-container">
    <h2 style="margin-bottom:20px;">Make a Wish 🎂</h2>

    <div class="cake">
      <div class="candle"></div>
      <div class="flame" id="flame"></div>
    </div>

    <button onclick="startMic()">🎤 Blow the Candle</button>
    <p id="status"></p>
  </div>
</section>

<!-- LIGHTBOX -->
<div id="lightbox" onclick="this.style.display='none'">
  <img id="lightbox-img">
</div>

<!-- MUSIC -->
<div class="music">
  <button onclick="toggleMusic()">🎵 Music</button>
  <audio id="bgm" loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_d5a9f0.mp3?filename=soft-piano-ambient-112191.mp3">
  </audio>
</div>

<script>
/* =========================
   LOADER
========================= */
window.onload = () => {
  setTimeout(()=> document.getElementById("loader").style.display="none", 1500);
};

/* =========================
   FLOATING HEARTS
========================= */
setInterval(()=>{
  let heart = document.createElement("div");
  heart.classList.add("heart");
  heart.innerHTML = "💕";
  heart.style.left = Math.random()*100+"vw";
  heart.style.fontSize = Math.random()*20+10+"px";
  document.body.appendChild(heart);
  setTimeout(()=>heart.remove(),6000);
},500);

/* =========================
   LIGHTBOX
========================= */
function openImg(src){
  document.getElementById("lightbox").style.display="flex";
  document.getElementById("lightbox-img").src = src;
}

/* =========================
   MUSIC
========================= */
function toggleMusic(){
  let music = document.getElementById("bgm");
  if(music.paused) music.play();
  else music.pause();
}

/* =========================
   MIC BLOW CANDLE
========================= */
let audioContext, analyser, micStream;

async function startMic(){
  document.getElementById("status").innerText = "Listening... blow into mic 💨";

  audioContext = new (window.AudioContext || window.webkitAudioContext)();
  micStream = await navigator.mediaDevices.getUserMedia({ audio:true });

  let source = audioContext.createMediaStreamSource(micStream);
  analyser = audioContext.createAnalyser();
  source.connect(analyser);

  analyser.fftSize = 512;
  let data = new Uint8Array(analyser.frequencyBinCount);

  function detectBlow(){
    analyser.getByteFrequencyData(data);
    let volume = data.reduce((a,b)=>a+b)/data.length;

    if(volume > 25){
      document.getElementById("flame").style.display="none";
      document.getElementById("status").innerText = "🎉 Candle blown! Make a wish 💖";
      micStream.getTracks().forEach(t=>t.stop());
      return;
    }
    requestAnimationFrame(detectBlow);
  }
  detectBlow();
}
</script>

</body>
</html>