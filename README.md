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

/* Pages */
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

/* Intro */
.intro {
    font-size: 28px;
    animation: glow 2s infinite alternate;
}
@keyframes glow {
    from { text-shadow: 0 0 10px pink; }
    to { text-shadow: 0 0 30px white; }
}

/* Input */
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

/* Shake on wrong password */
.shake {
    animation: shake 0.3s;
}
@keyframes shake {
    0%{transform:translateX(0)}
    25%{transform:translateX(-5px)}
    50%{transform:translateX(5px)}
    75%{transform:translateX(-5px)}
    100%{transform:translateX(0)}
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

/* Message */
.message {
    display: none;
    margin-top: 20px;
    max-width: 600px;
    text-shadow: 0 0 10px white;
}

/* Final emotional */
.big {
    font-size: 26px;
    animation: pulse 2s infinite;
}
@keyframes pulse {
    0%{transform:scale(1)}
    50%{transform:scale(1.05)}
    100%{transform:scale(1)}
}

/* Hearts + bubbles */
.float {
    position: absolute;
    bottom: -50px;
    font-size: 20px;
    animation: rise 10s linear infinite;
}
@keyframes rise {
    to { transform: translateY(-120vh); opacity:0;}
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

/* Sparkle cursor */
.sparkle {
    position: fixed;
    width: 6px;
    height: 6px;
    background: white;
    border-radius: 50%;
    pointer-events: none;
    animation: fadeOut 1s forwards;
}
@keyframes fadeOut {
    to {opacity:0; transform: scale(2);}
}
</style>
</head>

<body>

<audio id="music" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<div class="page active" id="intro">
    <div class="intro">You already know what this is… 💖</div>
    <button onclick="start()">Start 💫</button>
</div>

<div class="page" id="page1">
    <h2>Enter Password 💝</h2>
    <input type="password" id="pass">
    <button onclick="checkPass()">Enter</button>
</div>

<div class="page" id="page2">
    <div class="gift" onclick="openGift(1)">
        <div class="lid"></div>
        <div class="ribbonV"></div>
        <div class="ribbonH"></div>
    </div>
    <div class="message" id="msg1"></div>
</div>

<div class="page" id="page3">
    <div class="gift" onclick="openGift(2)">
        <div class="lid"></div>
        <div class="ribbonV"></div>
        <div class="ribbonH"></div>
    </div>
    <div class="message" id="msg2"></div>
</div>

<div class="page" id="page4">
    <div class="gift" onclick="openGift(3)">
        <div class="lid"></div>
        <div class="ribbonV"></div>
        <div class="ribbonH"></div>
    </div>
    <div class="message big" id="msg3"></div>
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
    let p=document.getElementById("pass");
    if(p.value==="1103"){
        nextPage("page2");
    } else {
        p.classList.add("shake");
        setTimeout(()=>p.classList.remove("shake"),300);
    }
}

/* UPDATED Typewriter with callback */
function typeText(el,text,callback,speed=25){
    let i=0;
    el.style.display="block";
    let int=setInterval(()=>{
        el.innerHTML+=text[i];
        i++;
        if(i>=text.length){
            clearInterval(int);
            if(callback) callback();  // 👈 triggers after typing
        }
    },speed);
}

function explode(){
    for(let i=0;i<40;i++){
        let c=document.createElement("div");
        c.className="confetti";
        c.style.left=Math.random()*100+"vw";
        c.style.background=`hsl(${Math.random()*360},100%,70%)`;
        document.body.appendChild(c);
        setTimeout(()=>c.remove(),2000);
    }
}

function openGift(n){
    let gift=document.querySelectorAll(".gift")[n-1];
    gift.classList.add("open");
    gift.style.pointerEvents="none"; // fix

    explode();

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

    let el=document.getElementById("msg"+n);
    el.innerHTML="";

    typeText(el,texts[n-1], ()=>{
        if(n<3){
            let btn=document.createElement("button");
            btn.innerText="Next 💕";
            btn.onclick=()=>nextPage("page"+(n+1));
            el.appendChild(document.createElement("br"));
            el.appendChild(btn);
        }
    });
}

setInterval(()=>{
    let f=document.createElement("div");
    f.className="float";
    f.innerText=["💖","💗","💝","🎀"][Math.floor(Math.random()*4)];
    f.style.left=Math.random()*100+"vw";
    document.body.appendChild(f);
    setTimeout(()=>f.remove(),10000);
},500);

document.addEventListener("mousemove",e=>{
    let s=document.createElement("div");
    s.className="sparkle";
    s.style.left=e.clientX+"px";
    s.style.top=e.clientY+"px";
    document.body.appendChild(s);
    setTimeout(()=>s.remove(),1000);
});
</script>

</body>
</html>
