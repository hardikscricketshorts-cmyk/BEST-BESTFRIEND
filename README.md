<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>💖</title>

<style>
body {
    margin: 0;
    font-family: cursive;
    background: linear-gradient(135deg, #ff4da6, #8a00ff);
    color: yellow;
    text-align: center;
}

.page {
    display: none;
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

.gift {
    width: 150px;
    height: 120px;
    background: red;
    margin: auto;
    border-radius: 10px;
    cursor: pointer;
}

.message {
    margin-top: 20px;
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
}

/* hidden buttons */
.nextBtn {
    display: none;
}
</style>
</head>

<body>

<div id="intro" class="page" style="display:block;">
    <h2>You already know what this is 💖</h2>
    <button onclick="showPage('page1')">Start</button>
</div>

<div id="page1" class="page">
    <h2>Enter Password 💝</h2>
    <input type="password" id="pass">
    <br>
    <button onclick="checkPass()">Enter</button>
</div>

<div id="page2" class="page">
    <div class="gift" onclick="openGift(1)"></div>
    <div class="message" id="msg1"></div>
    <button class="nextBtn" id="next1" onclick="showPage('page3')">Next 💕</button>
</div>

<div id="page3" class="page">
    <div class="gift" onclick="openGift(2)"></div>
    <div class="message" id="msg2"></div>
    <button class="nextBtn" id="next2" onclick="showPage('page4')">Next 💕</button>
</div>

<div id="page4" class="page">
    <div class="gift" onclick="openGift(3)"></div>
    <div class="message" id="msg3"></div>
</div>

<script>
function showPage(id){
    document.querySelectorAll(".page").forEach(p => p.style.display="none");
    document.getElementById(id).style.display="block";
}

function checkPass(){
    if(document.getElementById("pass").value === "1103"){
        showPage("page2");
    } else {
        alert("Wrong password");
    }
}

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

function openGift(n){
    let texts = [
`Sarvadnya 🥹💝 

From the past one year, you've been more than just a best friend to me — you've been my comfort, my happiness, and someone I truly cherish.  
You're incredibly talented and intelligent, and honestly, one of the most amazing people I know.  
The way you understand me means everything to me 💖`,

`Sobt celebrate krayla milala nahi, tri a small wish🥹`,

`Im Sorry For Not Being Enough To What You Deserve🫶`
    ];

    let el = document.getElementById("msg"+n);

    typeText(el, texts[n-1], function(){
        if(n === 1){
            document.getElementById("next1").style.display = "inline-block";
        }
        if(n === 2){
            document.getElementById("next2").style.display = "inline-block";
        }
    });
}
</script>

</body>
</html>
