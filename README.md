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
    color: yellow;
    text-align: center;
}

/* Pages */
.page {
    display: none;
    height: 100vh;
    padding-top: 100px;
}

button, input {
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
    margin: auto;
    border-radius: 10px;
    cursor: pointer;
}

/* Message */
.message {
    margin-top: 20px;
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
}
</style>
</head>

<body>

<audio id="music" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<!-- INTRO -->
<div class="page" id="intro" style="display:block;">
    <h2>You already know what this is… 💖</h2>
    <button onclick="start()">Start</button>
</div>

<!-- PASSWORD -->
<div class="page" id="page1">
    <h2>Enter Password 💝</h2>
    <input type="password" id="pass">
    <br>
    <button onclick="checkPass()">Enter</button>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
    <div class="gift" onclick="openGift(1)"></div>
    <div class="message" id="msg1"></div>
</div>

<!-- PAGE 3 -->
<div class="page" id="page3">
    <div class="gift" onclick="openGift(2)"></div>
    <div class="message" id="msg2"></div>
</div>

<!-- PAGE 4 -->
<div class="page" id="page4">
    <div class="gift" onclick="openGift(3)"></div>
    <div class="message" id="msg3"></div>
</div>

<script>
function showPage(id){
    document.querySelectorAll(".page").forEach(p => p.style.display="none");
    document.getElementById(id).style.display="block";
}

function start(){
    document.getElementById("music").play();
    showPage("page1");
}

function checkPass(){
    if(document.getElementById("pass").value === "1103"){
        showPage("page2");
    } else {
        alert("Wrong password");
    }
}

/* Typewriter */
function typeText(el, text, callback){
    let i = 0;
    el.innerHTML = "";
    let int = setInterval(()=>{
        el.innerHTML += text[i];
        i++;
        if(i >= text.length){
            clearInterval(int);
            if(callback) callback();
        }
    }, 25);
}

/* Open Gift */
function openGift(n){
    let texts = [
`Sarvadnya 🥹💝 

From the past one year, you've been more than just a best friend to me — you've been my comfort, my happiness, and someone I truly cherish.  
You're incredibly talented and intelligent, and honestly, one of the most amazing people I know.  
The way you understand me means everything to me. 💖`,

`Sobt celebrate krayla milala nahi, tri a small wish🥹`,

`Im Sorry For Not Being Enough To What You Deserve🫶`
    ];

    let el = document.getElementById("msg"+n);

    typeText(el, texts[n-1], function(){
        if(n < 3){
            let btn = document.createElement("button");
            btn.innerText = "Next 💕";
            btn.onclick = function(){
                showPage("page"+(n+1));
            };
            el.appendChild(document.createElement("br"));
            el.appendChild(btn);
        }
    });
}
</script>

</body>
</html>
