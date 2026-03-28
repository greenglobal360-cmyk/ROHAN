<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Rohan ❤️ Purva</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
    text-align: center;
    font-family: Arial, sans-serif;
    background: #ffe6f0;
    overflow: hidden;
}

h1 {
    margin-top: 100px;
    color: #ff3366;
}

/* Buttons */
.btn {
    padding: 12px 25px;
    font-size: 18px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    margin: 20px;
    position: absolute;
}

#yes {
    background-color: #ff4d6d;
    color: white;
    left: 40%;
    top: 50%;
}

#no {
    background-color: #666;
    color: white;
    left: 55%;
    top: 50%;
}

/* Floating hearts */
.heart {
    position: absolute;
    color: red;
    animation: floatUp 5s linear infinite;
}

@keyframes floatUp {
    0% { transform: translateY(100vh); opacity: 1; }
    100% { transform: translateY(-10vh); opacity: 0; }
}

/* Dance animation */
@keyframes dance {
    0% { transform: rotate(0deg) scale(1); }
    25% { transform: rotate(5deg) scale(1.1); }
    50% { transform: rotate(-5deg) scale(1.1); }
    75% { transform: rotate(5deg) scale(1.1); }
    100% { transform: rotate(0deg) scale(1); }
}

.dance {
    animation: dance 0.5s infinite;
}
</style>
</head>

<body>

<h1 id="question">Rohan ❤️ Purva<br>Will you be my Valentine? 💖</h1>

<button id="yes" class="btn">Yes 💖</button>
<button id="no" class="btn">No 😢</button>

<script>
const noBtn = document.getElementById("no");
const yesBtn = document.getElementById("yes");
const question = document.getElementById("question");

let messages = [
    "Are you sure? 😢",
    "Really sure? 🥺",
    "Think again 💔",
    "Please say yes ❤️",
    "Don't break my heart 💕",
    "Last chance 😭",
    "I'm sad now 😞",
    "You can't say no 😜"
];

let index = 0;

// Move button
function moveButton() {
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 50);

    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";

    // Change message
    question.innerHTML = "Rohan ❤️ Purva<br>" + messages[index % messages.length];
    index++;

    // Shrink button
    let size = parseFloat(window.getComputedStyle(noBtn).fontSize);
    if (size > 10) {
        noBtn.style.fontSize = (size - 2) + "px";
    }
}

// Desktop
noBtn.addEventListener("mouseover", moveButton);

// Mobile
noBtn.addEventListener("touchstart", function(e) {
    e.preventDefault();
    moveButton();
});

// Floating hearts
function createHeart() {
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "❤️";

    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (Math.random() * 20 + 15) + "px";

    document.body.appendChild(heart);

    setTimeout(() => heart.remove(), 5000);
}

setInterval(createHeart, 300);

// YES click
yesBtn.addEventListener("click", () => {
    document.body.innerHTML = `
        <h1 class="dance" style="color:#ff3366; margin-top:150px;">
        💃❤️ Rohan Loves Purva ❤️💃<br><br>
        🎉 You said YES 🎉
        </h1>
    `;

    for (let i = 0; i < 50; i++) {
        setTimeout(createHeart, i * 100);
    }
});
</script>

</body>
</html>
