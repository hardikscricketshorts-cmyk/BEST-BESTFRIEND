<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Best Friends Day 💛</title>

<style>
body {
    margin: 0;
    font-family: 'Comic Sans MS', cursive;
    background: linear-gradient(135deg, #fff7cc, #ffe4ec);
    overflow: hidden;
}

/* Pages */
.page {
    display: none;
    height: 100vh;
    width: 100%;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    animation: fade 0.8s ease;
}

.active {
    display: flex;
}

@keyframes fade {
    from {opacity: 0; transform: scale(0.95);}
    to {opacity: 1; transform: scale(1);}
}

/* Center text */
.main-text {
    font-size: 2.5rem;
    font-weight: bold;
}

/* Buttons */
button {
    padding: 12px 25px;
    margin-top: 20px;
    font-size: 1rem;
    border: none;
    border-radius: 20px;
    background: #ff9eb5;
    color: white;
    cursor: pointer;
    transition: 0.3s;
}

button:hover {
    transform: scale(1.1);
    background: #ff6f91;
}

/* Options */
.option {
    margin: 10px;
    cursor: pointer;
    padding: 10px 20px;
    border-radius: 15px;
    background: white;
    display: inline-block;
}

.option:hover {
    background: #ffd6e0;
}

/* Input */
input {
    padding: 10px;
    border-radius: 10px;
    border: 1px solid #ccc;
}

/* Flowers (simple decorative corners) */
.corner {
    position: absolute;
    width: 120px;
    opacity: 0.6;
}

.top-left { top: 0; left: 0; }
.top-right { top: 0; right: 0; transform: rotate(90deg); }
.bottom-left { bottom: 0; left: 0; transform: rotate(-90deg); }
.bottom-right { bottom: 0; right: 0; transform: rotate(180deg); }

/* Pop animation */
.pop {
    animation: pop 0.4s ease;
}

@keyframes pop {
    0% {transform: scale(0.7);}
    100% {transform: scale(1);}
}
</style>
</head>

<body>

<!-- Flower Decorations -->
<img src="https://png.pngtree.com/png-clipart/20210311/original/pngtree-watercolor-flower-png-image_6001557.png" class="corner top-left">
<img src="https://png.pngtree.com/png-clipart/20210311/original/pngtree-watercolor-flower-png-image_6001557.png" class="corner top-right">
<img src="https://png.pngtree.com/png-clipart/20210311/original/pngtree-watercolor-flower-png-image_6001557.png" class="corner bottom-left">
<img src="https://png.pngtree.com/png-clipart/20210311/original/pngtree-watercolor-flower-png-image_6001557.png" class="corner bottom-right">

<!-- PAGE 1 -->
<div class="page active" id="page1">
    <div class="main-text">You already know what this is.</div>
    <button onclick="nextPage(2)">Next ➡</button>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
    <div class="main-text">Then also i'll ask 😝</div>
    <button onclick="showQuestion()">Okk</button>

    <div id="question" style="display:none;">
        <p class="pop">What is today's date?</p>

        <div class="option" onclick="wrong()">11th February</div>
        <div class="option" onclick="correct()">8th June</div>
        <div class="option" onclick="wrong()">15th August</div>
    </div>
</div>

<!-- PAGE 3 -->
<div class="page" id="page3">
    <p class="main-text">
        Tho we're not here to celebrate in personal, i'll try to make it atleast simplest wish 💛
    </p>
    <button onclick="nextPage(4)">Next ➡</button>
</div>

<!-- PAGE 4 -->
<div class="page" id="page4">
    <p>Tell the password</p>
    <input type="password" id="pass">
    <br>
    <button onclick="checkPass()">Enter</button>
    <p id="error" style="color:red;"></p>
</div>

<!-- PAGE 5 -->
<div class="page" id="page5">
    <p class="main-text pop">
        Sarvadnya 💛<br><br>
        From the past one year, you've been more than just a best friend to me — you've been my comfort, my happiness, and someone I truly cherish.  
        You're incredibly talented and intelligent, and honestly, one of the most amazing people I know.  
        The way you understand me, support me, and just exist in my life means more than I can ever properly explain.  
        You're not just my best friend, you're someone I hold very close to my heart.  
        I promise to always stand by you, protect our bond, and value you no matter what.  
        You mean a lot to me... more than words can say 💛
    </p>
</div>

<script>
function nextPage(page) {
    document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
    document.getElementById("page" + page).classList.add("active");
}

function showQuestion() {
    document.getElementById("question").style.display = "block";
}

function correct() {
    nextPage(3);
}

function wrong() {
    alert("Wrong answer 😝 try again!");
}

function checkPass() {
    let pass = document.getElementById("pass").value;
    if(pass === "1103") {
        nextPage(5);
    } else {
        document.getElementById("error").innerText = "Wrong password!";
    }
}
</script>

</body>
</html>
