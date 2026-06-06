
<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<title>Best Friends Day 💜</title><link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;600&display=swap" rel="stylesheet"><style>
body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(135deg, #2b1055, #7597de);
    color: white;
}

/* Pages */
.page {
    display: none;
    min-height: 100vh;
    padding: 40px 20px;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    animation: fade 0.6s ease;
}
.active { display: flex; }

@keyframes fade {
    from {opacity: 0; transform: translateY(20px);}
    to {opacity: 1; transform: translateY(0);}
}

/* Text */
.main-text {
    font-size: 1.5rem;
    font-weight: 500;
}

/* Paragraph */
.long-text {
    font-size: 0.85rem;
    line-height: 1.6;
    margin-top: 15px;
}

/* Buttons */
button {
    padding: 10px 22px;
    margin-top: 20px;
    font-size: 0.9rem;
    border: none;
    border-radius: 20px;
    background: #9d4edd;
    color: white;
    cursor: pointer;
}
button:hover {
    transform: scale(1.08);
    background: #7b2cbf;
}

/* Options */
.option {
    margin: 8px;
    padding: 10px 18px;
    border-radius: 12px;
    background: rgba(255,255,255,0.1);
    display: inline-block;
    cursor: pointer;
}
.option:hover {
    background: rgba(255,255,255,0.25);
}

/* Input */
input {
    padding: 10px;
    border-radius: 10px;
    border: none;
}

/* Gift */
.gift-box {
    font-size: 3.2rem;
    cursor: pointer;
    animation: glow 1.5s infinite alternate;
}

@keyframes glow {
    from {text-shadow: 0 0 10px #fff;}
    to {text-shadow: 0 0 25px #ff9eff;}
}

.tap-text {
    font-size: 0.8rem;
    opacity: 0.7;
}

/* Box */
.box {
    display: none;
    max-width: 95%;
    max-height: 60vh;
    overflow-y: auto;
    padding: 15px;
    border-radius: 15px;
    background: rgba(255,255,255,0.08);
    animation: pop 0.5s ease;
}

@keyframes pop {
    from {transform: scale(0.7); opacity: 0;}
    to {transform: scale(1); opacity: 1;}
}

/* Confetti */
.confetti {
    position: fixed;
    width: 8px;
    height: 8px;
    background: white;
    top: 0;
    animation: fall 2s linear forwards;
}

@keyframes fall {
    to {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
    }
}
</style></head><body><!-- MUSIC --><audio id="music" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8e5c3a6e3.mp3?filename=soft-piano-ambient-110624.mp3"></audio>

<!-- PAGE 1 --><div class="page active" id="page1">
    <div class="main-text">You already know what this is.</div>
    <button onclick="nextPage(2)">Next ➡</button>
</div><!-- PAGE 2 --><div class="page" id="page2">
    <div class="main-text">Then also I'll ask 😝</div>
    <p>What is today's date?</p>
    <div>
        <div class="option" onclick="wrong()">11th February</div>
        <div class="option" onclick="correct()">8th June</div>
        <div class="option" onclick="wrong()">15th August</div>
    </div>
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
    <p id="error" style="color:#ffb3c6;"></p>
</div><!-- PAGE 5 --><div class="page" id="page5">
    <div class="gift-box" onclick="openGift()">
        🎁
        <div class="tap-text">Tap to open</div>
    </div><div id="giftContent" class="box">
    <div>शब्दात व्यक्त नाही करू शकलो 💛</div>

    <div class="long-text">
        Sarvadnya 💛<br><br>
        From the past one year, you've been more than just a best friend to me — you've been my comfort, my happiness, and someone I truly cherish.  
        You're incredibly talented and intelligent, and honestly, one of the most amazing people I know.  
        The way you understand me, support me, and just exist in my life means more than I can ever properly explain.  
        You're not just my best friend, you're someone I hold very close to my heart.  
        I promise to always stand by you, protect our bond, and value you no matter what.  
        You mean a lot to me... more than words can say 💛
    </div>
</div>

</div><script>
function nextPage(page) {
    document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
    document.getElementById("page" + page).classList.add("active");
}

function correct() {
    nextPage(3);
}

function wrong() {
    alert("Wrong answer 😝 Try again!");
}

function checkPass() {
    let pass = document.getElementById("pass").value;
    if(pass === "1103") {
        nextPage(5);
    } else {
        document.getElementById("error").innerText = "Wrong password!";
    }
}

function openGift() {
    document.querySelector(".gift-box").style.display = "none";
    document.getElementById("giftContent").style.display = "block";

    // play music
    document.getElementById("music").play();

    // confetti
    for(let i=0; i<60; i++){
        let conf = document.createElement("div");
        conf.classList.add("confetti");
        conf.style.left = Math.random()*100 + "vw";
        conf.style.background = "hsl(" + Math.random()*360 + ",100%,70%)";
        conf.style.animationDuration = (1.5 + Math.random()) + "s";
        document.body.appendChild(conf);

        setTimeout(() => conf.remove(), 2000);
    }
}
</script></body>
</html>
