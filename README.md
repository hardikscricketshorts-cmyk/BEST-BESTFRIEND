<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You 💛</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">

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
.intro {
    font-size: 26px;
    opacity: 0.9;
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

/* Chat style */
.chat {
    background: rgba(255,255,255,0.1);
    padding: 15px;
    border-radius: 15px;
    max-width: 320px;
    margin-top: 20px;
}

/* Final */
.final {
    font-size: 24px;
    opacity: 0.95;
    animation: glow 3s infinite alternate;
}
@keyframes glow {
    from { text-shadow: 0 0 5px #fff; }
    to { text-shadow: 0 0 20px #fff; }
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

<audio id="music" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3">
</audio>

<!-- INTRO -->
<div class="page active" id="intro">
    <div class="intro">You already know what this is… 💛</div>
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
    <div class="chat">
        "Then also i'll ask 😝"<br><br>
        "What is today's date?"<br><br>
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
</div>

<script>
function start(){
    document.getElementById("music").play();
    next("passPage");
}

function next(id){
    document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

function checkPass(){
    if(document.getElementById("pass").value==="1103"){
        next("p2");
    } else alert("Wrong password 💔");
}

/* Typewriter FIXED */
function type(el,text){
    let i=0;
    el.style.display="block";
    let int=setInterval(()=>{
        if(i < text.length){
            el.innerHTML += text[i];
            i++;
        } else {
            clearInterval(int);
        }
    },25);
}

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
    el.innerHTML="";
    type(el,texts[n-1]);

    /* FIXED DELAY */
    if(n==1){
        let delay = texts[n-1].length * 25;
        setTimeout(()=>next("chatPage"), delay + 500);
    }
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
