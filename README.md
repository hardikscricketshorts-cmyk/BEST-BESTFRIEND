<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>💖</title>

<link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    font-family: 'Pacifico', cursive;
    background: linear-gradient(135deg, #ff4da6, #8a00ff);
    overflow: hidden;
    color: yellow;
}

.page {
    display: none;
    height: 100vh;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    padding: 20px;
    animation: fade 1s;
}
.active { display: flex; }

@keyframes fade {
    from {opacity:0; transform: scale(0.8);}
    to {opacity:1; transform: scale(1);}
}

.intro {
    font-size: 28px;
    animation: glow 2s infinite alternate;
}
@keyframes glow {
    from { text-shadow: 0 0 10px pink; }
    to { text-shadow: 0 0 30px white; }
}

input, button {
    padding: 10px;
    border-radius: 20px;
    border: none;
    margin-top: 10px;
}

button {
    background: pink;
    cursor: pointer;
}

/* Gift */
.gift {
    width: 150px;
    height: 120px;
    background: red;
    position: relative;
    border-radius: 10px;
    cursor: pointer;
}

.lid {
    position: absolute;
    width: 100%;
    height: 40px;
    background: darkred;
    top: -40px;
    transition: 0.6s;
}

.ribbonV {
    width: 20px;
    height: 100%;
    background: gold;
    position: absolute;
    left: 65px;
}

.ribbonH {
    height: 20px;
    width: 100%;
    background: gold;
    position: absolute;
    top: 50px;
}

.open .lid {
    transform: translateY(-120px) rotate(-25deg);
}

.message {
    display: none;
    margin-top: 20px;
    max-width: 600px;
    text-shadow: 0 0 10px white;
}

.big {
    font-size: 26px;
}

/* Confetti */
.confetti {
    position: fixed;
    width: 8px;
    height: 8px;
    background: white;
    animation: fall 2s linear forwards;
}
@keyframes fall {
    to {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
    }
}
</style>
</head>

<body>

<audio id="music" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<audio id="voice">
<source src="voice.mp3">
</audio>

<!-- INTRO -->
<div class="page active" id="intro">
    <div class="intro">Sarvadnya 💛<br>You already know what this is…</div>
    <button onclick="start()">Start 💫</button>
</div>

<!-- PASSWORD -->
<div class="page" id="page1">
    <h2>Enter Password 💝</h2>
    <input type="password" id="pass">
    <button onclick="checkPass()">Enter</button>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
    <div class="gift" onclick="openGift(1)">
        <div class="lid"></div>
        <div class="ribbonV"></div>
        <div class="ribbonH"></div>
    </div>
    <div class="message" id="msg1"></div>
</div>

<!-- PAGE 3 -->
<div class="page" id="page3">
    <div class="gift" onclick="openGift(2)">
        <div class="lid"></div>
        <div class="ribbonV"></div>
        <div class="ribbonH"></div>
    </div>
    <div class="message" id="msg2"></div>
</div>

<!-- PAGE 4 -->
<div class="page" id="page4">
    <div class="gift" onclick="openGift(3)">
        <div class="lid"></div>
        <div class="ribbonV"></div>
        <div class="ribbonH"></div>
    </div>
    <div class="message big" id="msg3"></div>
    <button onclick="playVoice()">🎙️ Play Voice Note</button>
</div>

<script>
function start(){
    document.getElementById("music").play();
    nextPage("page1");
}

function nextPage(id){
    document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

function checkPass(){
    let p=document.getElementById("pass").value;
    if(p==="1103"){
        nextPage("page2");
    } else alert("Wrong password 💔");
}

/* FIXED TYPEWRITER */
function typeText(el, text, callback){
    let i=0;
    el.style.display="block";
    el.innerHTML="";

    let interval=setInterval(()=>{
        el.innerHTML += text.charAt(i);
        i++;
        if(i >= text.length){
            clearInterval(interval);
            if(callback) callback();
        }
    },25);
}

/* CONFETTI */
function explode(){
    for(let i=0;i<40;i++){
        let c=document.createElement("div");
        c.className="confetti";
        c.style.left=Math.random()*100+"vw";
        document.body.appendChild(c);
        setTimeout(()=>c.remove(),2000);
    }
}

/* FIXED FLOW */
function openGift(n){
    let messages=[
`Sarvadnya 🥹💝 

From the past one year, you've been more than just a best friend to me — you've been my comfort, my happiness, and someone I truly cherish.  
You're incredibly talented and intelligent, and honestly, one of the most amazing people I know.  
The way you understand me, support me, and just exist in my life means more than I can ever properly explain.  
You're not just my best friend, you're someone I hold very close to my heart.  
I promise to always stand by you, protect our bond, and value you no matter what.  
You mean a lot to me... more than words can say 😚🎀`,

`Sobt celebrate krayla milala nahi, tri a small wish🥹`,

`Im Sorry For Not Being Enough To What You Deserve🫶`
    ];

    let gift=document.querySelectorAll(".gift")[n-1];
    gift.classList.add("open");
    explode();

    let msg=document.getElementById("msg"+n);

    if(n===1){
        typeText(msg, messages[0], ()=>{
            setTimeout(()=>nextPage("page3"),1500);
        });
    }
    else if(n===2){
        typeText(msg, messages[1], ()=>{
            setTimeout(()=>nextPage("page4"),1500);
        });
    }
    else if(n===3){
        typeText(msg, messages[2]);
    }
}

function playVoice(){
    document.getElementById("voice").play();
}
</script>

</body>
</html>
