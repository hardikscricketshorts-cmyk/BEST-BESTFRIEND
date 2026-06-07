<!DOCTYPE html><html>
<head>
<meta charset="UTF-8">
<title>Best Friends Day 💖</title><link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet"><style>
body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(135deg, #ff4ecd, #7b2cbf);
    color: #fff4a3;
    font-style: italic;
    font-weight: 600;
    overflow-x: hidden;
}

/* hearts */
.corner { position: fixed; font-size: 1.5rem; opacity: 0.7; }
.tl { top: 10px; left: 10px; }
.tr { top: 10px; right: 10px; }
.bl { bottom: 10px; left: 10px; }
.br { bottom: 10px; right: 10px; }

/* pages */
.page {
    display: none;
    min-height: 100vh;
    padding: 30px 20px;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
}
.active { display: flex; }

/* text */
.main-text { font-size: 1.4rem; }
.long-text { font-size: 0.85rem; line-height: 1.6; margin-top: 15px; }

/* buttons */
button {
    padding: 10px 20px;
    margin-top: 20px;
    border: none;
    border-radius: 20px;
    background: #ff66c4;
    color: #fff4a3;
    cursor: pointer;
}

/* options */
.option {
    margin: 8px;
    padding: 10px 15px;
    border-radius: 12px;
    background: rgba(255,255,255,0.15);
    display: inline-block;
    cursor: pointer;
}

/* gift box */
.gift-wrapper {
    position: relative;
    width: 120px;
    height: 120px;
    cursor: pointer;
    animation: bounce 1s infinite alternate;
}

@keyframes bounce {
    from {transform: translateY(0);}
    to {transform: translateY(-8px);}
}

.box-base {
    width: 120px;
    height: 80px;
    background: #ff66c4;
    border-radius: 8px;
    position: absolute;
    bottom: 0;
}

.box-lid {
    width: 120px;
    height: 40px;
    background: #ff99dd;
    position: absolute;
    top: 0;
    transform-origin: top;
    transition: 0.6s;
}

.ribbon-v, .ribbon-h { position: absolute; background: white; }
.ribbon-v { width: 10px; height: 100%; left: 50%; transform: translateX(-50%); }
.ribbon-h { height: 10px; width: 100%; top: 50%; transform: translateY(-50%); }

.open .box-lid { transform: rotateX(120deg); }

/* content */
.box-content {
    display: none;
    margin-top: 25px;
    background: rgba(255,255,255,0.1);
    padding: 15px;
    border-radius: 12px;
    max-height: 60vh;
    overflow-y: auto;
}

/* 🎬 CINEMATIC VIDEO */
.video-wrapper {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: black;
    justify-content: center;
    align-items: center;
    animation: fadeIn 1s ease forwards;
}

.video-wrapper video {
    width: 90%;
    max-height: 80%;
    border-radius: 12px;
    transform: scale(0.7);
    opacity: 0;
    animation: zoomIn 1.2s ease forwards;
    animation-delay: 0.5s;
}

@keyframes fadeIn {
    from {opacity: 0;}
    to {opacity: 1;}
}

@keyframes zoomIn {
    to {
        transform: scale(1);
        opacity: 1;
    }
}

/* confetti */
.confetti {
    position: fixed;
    width: 6px;
    height: 6px;
    top: 0;
    animation: fall linear forwards;
}
@keyframes fall {
    to {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
    }
}
</style></head><body><div class="corner tl">💖</div>
<div class="corner tr">💗</div>
<div class="corner bl">💝</div>
<div class="corner br">🎀</div><!-- PAGE 1 --><div class="page active" id="page1">
    <div class="main-text">You already know what this is.</div>
    <button onclick="nextPage(2)">Next ➡</button>
</div><!-- PAGE 2 --><div class="page" id="page2">
    <div class="main-text">Then also I'll ask 😝</div>
    <p>What is today's date?</p>
    <div class="option" onclick="wrong()">11th February</div>
    <div class="option" onclick="correct()">8th June</div>
    <div class="option" onclick="wrong()">15th August</div>
</div><!-- PAGE 3 --><div class="page" id="page3">
    <p class="main-text">
        Tho we're not here to celebrate in personal, i'll try to make it atleast simplest wish 💛
    </p>
    <button onclick="nextPage(4)">Next ➡</button>
</div><!-- PAGE 4 --><div class="page" id="page4">
    <p>Enter password</p>
    <input type="password" id="pass">
    <br>
    <button onclick="checkPass()">Enter</button>
    <p id="error"></p>
</div><!-- PAGE 5 (LETTER) --><div class="page" id="page5"><div id="giftBox" class="gift-wrapper" onclick="openGift()">
    <div class="box-lid"></div>
    <div class="box-base"></div>
    <div class="ribbon-v"></div>
    <div class="ribbon-h"></div>
</div><div id="content" class="box-content">
    <p>शब्दात व्यक्त नाही करू शकलो 🙏💗</p><div class="long-text">
    Sarvadnya 🥹💝<br><br>
    From the past one year...
    You mean a lot to me 😚🎀
</div>

<button onclick="nextPage(6)">Next ➡</button>

</div></div><!-- PAGE 6 (VIDEO BOX) --><div class="page" id="page6"><div id="videoGift" class="gift-wrapper" onclick="openVideoGift()">
    <div class="box-lid"></div>
    <div class="box-base"></div>
    <div class="ribbon-v"></div>
    <div class="ribbon-h"></div>
</div></div><!-- 🎬 CINEMATIC VIDEO SCREEN --><div id="videoScreen" class="video-wrapper">
    <video id="myVideo" controls>
        <source src="VID-20251019-WA0033.mp4" type="video/mp4">
    </video>
</div><script>
function nextPage(p){
    document.querySelectorAll(".page").forEach(el=>el.classList.remove("active"));
    document.getElementById("page"+p).classList.add("active");
}

function correct(){ nextPage(3); }
function wrong(){ alert("Wrong answer 😝"); }

function checkPass(){
    let pass=document.getElementById("pass").value;
    if(pass==="1103"){ nextPage(5); }
    else{ document.getElementById("error").innerText="Wrong password!"; }
}

function openGift(){
    let box=document.getElementById("giftBox");
    box.classList.add("open");

    setTimeout(()=>{
        document.getElementById("content").style.display="block";
    },400);
}

function openVideoGift(){
    let box=document.getElementById("videoGift");
    box.classList.add("open");

    setTimeout(()=>{
        document.getElementById("videoScreen").style.display="flex";
        document.getElementById("myVideo").play();
    },500);
}
</script></body>
</html>
