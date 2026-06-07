<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You 💛</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(135deg, #ff7eb3, #8e44ad);
    color: #ffe66d;
    overflow: hidden;
}

/* Pages */
.page {
    display: none;
    height: 100vh;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    padding: 20px;
    animation: fade 0.8s ease;
}
.active { display: flex; }

@keyframes fade {
    from {opacity:0; transform: translateY(20px);}
    to {opacity:1; transform: translateY(0);}
}

/* Intro */
.name {
    font-size: 32px;
    font-weight: 600;
    animation: glow 2s infinite alternate;
}
@keyframes glow {
    from { text-shadow: 0 0 10px pink; }
    to { text-shadow: 0 0 25px white; }
}

/* Input */
input, button {
    padding: 10px;
    border-radius: 25px;
    border: none;
    margin-top: 12px;
}

button {
    background: #ffd6e0;
    cursor: pointer;
}

/* Gift */
.gift {
    width: 140px;
    height: 100px;
    background: #ff4d6d;
    border-radius: 10px;
    position: relative;
    cursor: pointer;
}

.lid {
    position: absolute;
    width: 100%;
    height: 35px;
    background: #c9184a;
    top: -35px;
    transition: 0.6s ease;
}

.ribbon {
    position: absolute;
    background: gold;
}
.ribbon.v { width: 18px; height: 100%; left: 60px; }
.ribbon.h { height: 18px; width: 100%; top: 40px; }

.open .lid {
    transform: translateY(-90px) rotate(-15deg);
}

/* Message */
.message {
    display: none;
    max-width: 600px;
    margin-top: 20px;
    line-height: 1.6;
}

/* Final */
.final {
    font-size: 24px;
    animation: glow 3s infinite alternate;
}

/* Particles */
.particle {
    position: absolute;
    width: 6px;
    height: 6px;
    background: white;
    opacity: 0.5;
    border-radius: 50%;
    animation: float 8s linear infinite;
}
@keyframes float {
    to { transform: translateY(-120vh); opacity: 0;}
}
</style>
</head>

<body>

<audio id="bgmusic" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3">
</audio>

<audio id="voice">
<source src="voice.mp3" type="audio/mp3">
</audio>

<!-- INTRO -->
<div class="page active" id="intro">
    <div class="name">Sarvadnya 💛</div>
    <div>You already know what this is…</div>
    <button onclick="start()">Continue</button>
</div>

<!-- PASSWORD -->
<div class="page" id="passPage">
    <h3>Enter Password</h3>
    <input type="password" id="pass">
    <button onclick="checkPass()">Enter</button>
</div>

<!-- GIFT 1 -->
<div class="page" id="p2">
    <div class="gift" onclick="openGift(1)">
        <div class="lid"></div>
        <div class="ribbon v"></div>
        <div class="ribbon h"></div>
    </div>
    <div class="message" id="m1"></div>
</div>

<!-- CHAT PAGE -->
<div class="page" id="chatPage">
    <div>
        “Then also i'll ask 😝”<br><br>
        “What is today's date?”<br><br>
        👉 Best Friends Day 💛
    </div>
    <button onclick="next('p3')">Next</button>
</div>

<!-- GIFT 2 -->
<div class="page" id="p3">
    <div class="gift" onclick="openGift(2)">
        <div class="lid"></div>
        <div class="ribbon v"></div>
        <div class="ribbon h"></div>
    </div>
    <div class="message" id="m2"></div>
</div>

<!-- FINAL -->
<div class="page" id="finalPage">
    <div class="gift" onclick="openGift(3)">
        <div class="lid"></div>
        <div class="ribbon v"></div>
        <div class="ribbon h"></div>
    </div>
    <div class="message final" id="m3"></div>

    <button onclick="playVoice()">🎙️ Play Voice Note</button>
</div>

<script>
function start(){
    document.getElementById("bgmusic").play();
    next("passPage");
}

/* ✅ FIXED NEXT FUNCTION */
function next(id){
    let pages = document.querySelectorAll(".page");

    pages.forEach(p => {
        p.classList.remove("active");
        p.style.display = "none";
    });

    let nextPage = document.getElementById(id);

    if(nextPage){
        nextPage.style.display = "flex";
        setTimeout(()=>{
            nextPage.classList.add("active");
        }, 10);
    }
}

function checkPass(){
    if(document.getElementById("pass").value==="1103"){
        next("p2");
    } else alert("Wrong password 💔");
}

/* TYPEWRITER */
function type(el,text,callback){
    let i=0;
    el.style.display="block";
    el.innerHTML="";

    let int=setInterval(()=>{
        el.innerHTML += text.charAt(i);
        i++;
        if(i >= text.length){
            clearInterval(int);
            if(callback) callback();
        }
    },25);
}

/* FLOW */
function openGift(n){
    let texts=[
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

    let el=document.getElementById("m"+n);

    if(n === 1){
        type(el, texts[0], () => {
            setTimeout(()=> next("chatPage"), 1500);
        });
    }
    else if(n === 2){
        type(el, texts[1], () => {
            setTimeout(()=> next("finalPage"), 1500);
        });
    }
    else if(n === 3){
        type(el, texts[2]);
    }
}

function playVoice(){
    document.getElementById("voice").play();
}

/* Particles */
setInterval(()=>{
    let p=document.createElement("div");
    p.className="particle";
    p.style.left=Math.random()*100+"vw";
    document.body.appendChild(p);
    setTimeout(()=>p.remove(),8000);
},400);
</script>

</body>
</html>
