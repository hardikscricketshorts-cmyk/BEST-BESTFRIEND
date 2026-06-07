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
}
.active { display: flex; }

input, button {
    padding: 10px;
    border-radius: 20px;
    border: none;
    margin-top: 10px;
}

button {
    background: pink;
    cursor: pointer;
    position: relative;
    z-index: 9999; /* 🔥 FORCE TOP */
}

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
}
</style>
</head>

<body>

<audio id="music" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<div class="page active" id="intro">
    <div>You already know what this is… 💖</div>
    <button onclick="start()">Start</button>
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
    <div id="btn1"></div> <!-- 🔥 button container -->
</div>

<div class="page" id="page3">
    <div class="gift" onclick="openGift(2)">
        <div class="lid"></div>
        <div class="ribbonV"></div>
        <div class="ribbonH"></div>
    </div>
    <div class="message" id="msg2"></div>
    <div id="btn2"></div>
</div>

<div class="page" id="page4">
    <div class="gift" onclick="openGift(3)">
        <div class="lid"></div>
        <div class="ribbonV"></div>
        <div class="ribbonH"></div>
    </div>
    <div class="message" id="msg3"></div>
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
    if(document.getElementById("pass").value==="1103"){
        nextPage("page2");
    }
}

function typeText(el,text,callback){
    let i=0;
    el.style.display="block";
    let int=setInterval(()=>{
        el.innerHTML+=text[i];
        i++;
        if(i>=text.length){
            clearInterval(int);
            if(callback) callback();
        }
    },25);
}

function openGift(n){
    let gift=document.querySelectorAll(".gift")[n-1];
    gift.classList.add("open");
    gift.style.pointerEvents="none";

    let texts=[
`Sarvadnya 🥹💝 ... (same text)`,

`Sobt celebrate krayla milala nahi, tri a small wish🥹`,

`Im Sorry For Not Being Enough To What You Deserve🫶`
    ];

    let el=document.getElementById("msg"+n);
    el.innerHTML="";

    typeText(el,texts[n-1], function(){
        if(n<3){
            let btn=document.createElement("button");
            btn.innerText="Next 💕";
            btn.onclick=function(){
                nextPage("page"+(n+1));
            };

            document.getElementById("btn"+n).appendChild(btn); // 🔥 OUTSIDE message
        }
    });
}
</script>

</body>
</html>
