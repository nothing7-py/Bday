
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday!</title>
<style>
body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    font-family: 'Arial', sans-serif;
}

.message-container {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: #fff;
    padding: 20px;
    box-sizing: border-box;
    transition: background 0.5s ease;
    position: relative;
}

.naughty {
    background: linear-gradient(to bottom right, #ff9ec7, #ffccf0);
    color: #fff;
}

.clean {
    background: linear-gradient(to bottom right, #a1c4fd, #c2e9fb);
    color: #333;
}

h1 {
    font-size: 3em;
    margin-bottom: 20px;
    z-index: 2;
    position: relative;
}

p {
    font-size: 1.5em;
    max-width: 600px;
    z-index: 2;
    position: relative;
}

button {
    margin-top: 30px;
    padding: 10px 20px;
    font-size: 1em;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: 0.3s;
    z-index: 2;
    position: relative;
}

button:hover {
    transform: scale(1.1);
}

/* Floating hearts */
.heart {
    position: absolute;
    font-size: 1.2em;
    animation: float 8s linear infinite;
    opacity: 0.8;
}

@keyframes float {
    0% { transform: translateY(100vh) scale(0.5); opacity: 0.7; }
    50% { opacity: 1; }
    100% { transform: translateY(-50vh) scale(1); opacity: 0; }
}

/* Petals animation */
.petals {
    position: absolute;
    top: -50px;
    font-size: 1.5em;
    animation: fall 10s linear infinite;
    opacity: 0.8;
}

@keyframes fall {
    0% { transform: translateY(0) rotate(0deg); opacity: 0.8; }
    100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
}

/* Sparkles animation */
.sparkle {
    position: absolute;
    top: -20px;
    font-size: 1.5em;
    animation: sparkleMove 5s linear infinite;
    opacity: 0.7;
}

@keyframes sparkleMove {
    0% { transform: translateY(0) scale(0.5); opacity: 0.7; }
    50% { opacity: 1; }
    100% { transform: translateY(100vh) scale(1); opacity: 0; }
}
</style>
</head>
<body>

<div id="naughtyMsg" class="message-container naughty">
    <h1>Happy Birthday, Cutie! 😏</h1>
    <p>Wishing you a day full of fun, naughty surprises, and a little Japanese charm to keep you blushing! 💖</p>
    <button onclick="switchMessage()">See the sweet side too!</button>
    <iframe id="naughtyBGM" src="https://www.youtube.com/embed/DnHkSmJv6xg?autoplay=1&loop=1&playlist=DnHkSmJv6xg" allow="autoplay"></iframe>
</div>

<div id="cleanMsg" class="message-container clean">
    <h1>Happy Birthday, Friend! 🎉</h1>
    <p>Thank you for being such an amazing friend! May your year ahead be full of laughter, joy, and all things wonderful. 🥰</p>
    <button onclick="switchMessage()">Back to the naughty side 😏</button>
    <iframe id="cleanBGM" src="https://www.youtube.com/embed/2XPNQDBi5cs?autoplay=1&loop=1&playlist=2XPNQDBi5cs" allow="autoplay"></iframe>
</div>

<script>
const naughty = document.getElementById('naughtyMsg');
const clean = document.getElementById('cleanMsg');
const naughtyBGM = document.getElementById('naughtyBGM');
const cleanBGM = document.getElementById('cleanBGM');

clean.style.display = 'none';
naughtyBGM.style.display = 'block';
cleanBGM.style.display = 'none';

function switchMessage() {
    if (naughty.style.display === 'block') {
        naughty.style.display = 'none';
        clean.style.display = 'flex';
        naughtyBGM.style.display = 'none';
        cleanBGM.style.display = 'block';
    } else {
        naughty.style.display = 'flex';
        clean.style.display = 'none';
        naughtyBGM.style.display = 'block';
        cleanBGM.style.display = 'none';
    }
}

// Floating hearts
function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.innerHTML = '💖';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = (5 + Math.random() * 5) + 's';
    heart.style.color = (naughty.style.display === 'block') ? '#ff69b4' : '#f0e68c';
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 8000);
}

// Cherry blossoms petals
function createPetal() {
    if(naughty.style.display === 'block') {
        const petal = document.createElement('div');
        petal.classList.add('petals');
        petal.innerHTML = '🌸';
        petal.style.left = Math.random() * 100 + 'vw';
        petal.style.fontSize = (12 + Math.random()*18) + 'px';
        document.body.appendChild(petal);
        setTimeout(() => petal.remove(), 10000);
    }
}

// Sparkles
function createSparkle() {
    if(clean.style.display === 'flex') {
        const sparkle = document.createElement('div');
        sparkle.classList.add('sparkle');
        sparkle.innerHTML = '✨';
        sparkle.style.left = Math.random() * 100 + 'vw';
        sparkle.style.fontSize = (12 + Math.random()*18) + 'px';
        document.body.appendChild(sparkle);
        setTimeout(() => sparkle.remove(), 5000);
    }
}

setInterval(() => { createHeart(); createPetal(); createSparkle(); }, 500);
</script>

</body>
</html>