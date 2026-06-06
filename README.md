<!DOCTYPE html><html lang="en">
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

/* Hearts */
.corner {
    position: fixed;
    font-size: 1.5rem;
    opacity: 0.7;
}
.tl { top: 10px; left: 10px; }
.tr { top: 10px; right: 10px; }
.bl { bottom: 10px; left: 10px; }
.br { bottom: 10px; right: 10px; }

/* Pages */
.page {
    display: none;
    min-height: 100vh;
    padding: 30px 20px;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    animation: fade 0.5s ease;
}
.active { display: flex; }

@keyframes fade {
    from {opacity: 0; transform: scale(0.95);}
    to {opacity: 1; transform: scale(1);}
}

/* Text */
.main-text {
    font-size: 1.4rem;
    animation: pop 0.5s ease;
}

.long-text {
    font-size: 0.85rem;
    line-height: 1.6;
    margin-top: 15px;
}

/* Buttons */
button {
    padding: 10px 20px;
    margin-top: 20px;
    border: none;
    border-radius: 20px;
    background: #ff66c4;
    color: #fff4a3;
    cursor: pointer;
    transition: 0.3s;
}
button:hover {
    transform: scale(1.1);
}

/* Options */
.option {
    margin: 8px;
    padding: 10px 15px;
    border-radius: 12px;
    background: rgba(255,255,255,0.15);
    display: inline-block;
    cursor: pointer;
    transition: 0.3s;
}
.option:hover {
    transform: scale(1.08);
}

/* Input */
input {
    padding: 10px;
    border-radius: 10px;
    border: none;
}

/* Pop animation */
@keyframes pop {
    from {transform: scale(0.8);}
    to {transform: scale(1);}
}

/* Gift box */
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

.ribbon-v, .ribbon-h {
    position: absolute;
    background: white;
}
.ribbon-v {
    width: 10px;
    height: 100%;
    left: 50%;
    transform: translateX(-50%);
}
.ribbon-h {
    height: 10px;
    width: 100%;
    top: 50%;
    transform: translateY(-50%);
}

.open .box-lid {
    transform: rotateX(120deg);
}

/* Content box */
.box-content {
    display: none;
    margin-top: 25px;
    background: rgba(255,255,255,0.1);
    padding: 15px;
    border-radius: 12px;
    max-height: 60vh;
    overflow-y: auto;
}

/* Confetti */
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
</style></head><body><!-- hearts --><div class="corner tl">💖</div>
<div class="corner tr">💗</div>
<div class="corner bl">💝</div>
<div class="corner br">🎀</div><audio id="music">
<source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8e5c3a6e3.mp3">
</audio><!-- PAGE 1 --><div class="page active" id="page1">
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
    <p id="error" style="color:#ffd6ec;"></p>
</div><!-- PAGE 5 --><div class="page" id="page5"><div id="giftBox" class="gift-wrapper" onclick="openGift()">
    <div class="box-lid"></div>
    <div class="box-base"></div>
    <div class="ribbon-v"></div>
    <div class="ribbon-h"></div>
</div>

<div id="content" class="box-content">
    <p>शब्दात व्यक्त नाही करू शकलो 🙏💗</p>

    <div class="long-text">
        Sarvadnya 🥹💝<br><br>
        From the past one year, you've been more than just a best friend to me — you've been my comfort, my happiness, and someone I truly cherish.  
        You're incredibly talented and intelligent, and honestly, one of the most amazing people I know.  
        The way you understand me, support me, and just exist in my life means more than I can ever properly explain.  
        You're not just my best friend, you're someone I hold very close to my heart.  
        I promise to always stand by you, protect our bond, and value you no matter what.  
        You mean a lot to me... more than words can say 😚🎀
    </div>
</div>

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

    document.getElementById("music").play().catch(()=>{});

    for(let i=0;i<50;i++){
        let c=document.createElement("div");
        c.className="confetti";
        c.style.left=Math.random()*100+"vw";
        c.style.background="hsl("+Math.random()*360+",100%,70%)";
        c.style.animationDuration=(1+Math.random())+"s";
        document.body.appendChild(c);
        setTimeout(()=>c.remove(),1500);
    }
}
</script></body>
</html>
