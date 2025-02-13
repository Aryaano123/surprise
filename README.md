<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Surprise ❤️</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Sacramento&display=swap');

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            font-family: 'Sacramento', cursive;
            font-size: 30px;
            text-align: center;
            overflow: hidden;
            position: relative;
        }

        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: relative;
        }

        .box {
            width: 450px;
            height: 220px;
            background: white;
            color: #ff4d6d;
            font-size: 40px;
            font-weight: bold;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            cursor: pointer;
            transition: all 0.5s ease-in-out;
            opacity: 0;
            transform: scale(0.8);
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0.8);
        }

        .show {
            opacity: 1;
            transform: translate(-50%, -50%) scale(1);
        }

        .pink-box {
            background: #ff4d6d;
            color: white;
            flex-direction: column;
            display: none;
            padding: 20px;
        }

        .buttons {
            margin-top: 15px;
        }

        .btn {
            padding: 12px 25px;
            font-size: 20px;
            font-weight: bold;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            margin: 5px;
            transition: 0.3s;
            position: relative;
            overflow: hidden;
        }

        .btn:hover {
            background: #ff8fab;
            box-shadow: 0 0 10px rgba(255, 77, 109, 0.7);
        }

        .yes {
            background: #28a745;
            color: white;
        }

        .no {
            background: #dc3545;
            color: white;
        }

        .final-box {
            background: #ffdfba;
            color: #ff4d6d;
            display: none;
        }

        .music-btn {
            background: #ffdfba;
            color: #ff4d6d;
            font-size: 80px;
            border-radius: 15px;
            margin-top: 20px;
        }

        /* Love Quote */
        .quote {
            font-size: 28px;
            font-weight: bold;
            color: white;
            opacity: 0;
            animation: fadeIn 3s ease-in-out forwards;
            position: absolute;
            top: 15%;
            text-align: center;
        }

        @keyframes fadeIn {
            0% { opacity: 0; transform: translateY(-20px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        /* Floating Hearts */
        .heart {
            position: absolute;
            color: red;
            font-size: 25px;
            opacity: 0.8;
            animation: float 4s linear;
        }

        @keyframes float {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-150px); opacity: 0; }
        }

        /* Falling Hearts */
        .falling-heart {
            position: absolute;
            color: red;
            font-size: 25px;
            opacity: 0.8;
            animation: fallingHearts 5s linear;
        }

        @keyframes fallingHearts {
            0% { transform: translateY(-100px); opacity: 0; }
            100% { transform: translateY(100vh); opacity: 1; }
        }

    </style>
</head>
<body>

<div id="loveQuote" class="quote">
    "You are my pookie. 🎀❤️"
</div>

<div class="container">
    <div id="redBox" class="box show" onclick="showValentineBox()">Heyy Anna kutty 💌</div>

    <div id="pinkBox" class="box pink-box">
        Will you be my Valentine? 💖
        <div class="buttons">
            <button class="btn yes" onclick="showFinalBox()">Yes</button>
            <button class="btn no" onclick="addYesButtons()">No</button>
        </div>
    </div>

    <div id="finalBox" class="box final-box">
        Yaaayyyy! I love you ❤️
    </div>

    <button id="musicButton" class="btn music-btn">Click here</button>
</div>

<audio id="loveSong" src="song1.mp3"></audio>

<script>
    function showValentineBox() {
        document.getElementById("redBox").style.display = "none";
        document.getElementById("pinkBox").style.display = "flex";
        document.getElementById("pinkBox").classList.add("show");
    }

    function showFinalBox() {
        document.getElementById("pinkBox").style.display = "none";
        document.getElementById("finalBox").style.display = "flex";
        document.getElementById("finalBox").classList.add("show");
        createHearts();
    }

    function addYesButtons() {
        let noButton = document.querySelector(".no");
        let newButton = document.createElement("button");
        newButton.classList.add("btn", "yes");
        newButton.innerText = "Yes";
        newButton.onclick = showFinalBox;
        noButton.parentNode.insertBefore(newButton, noButton);
    }

    function createHearts() {
        for (let i = 100; i < 150; i++) {
            let heart = document.createElement("div");
            heart.innerHTML = "❤️";
            heart.classList.add("heart");
            heart.style.left = Math.random() * window.innerWidth + "px";
            heart.style.top = Math.random() * window.innerHeight + "px";
            heart.style.animation = "float 4s linear";
            document.body.appendChild(heart);
            setTimeout(() => { heart.remove(); }, 4000);
        }
    }

    function fallingHearts() {
        setInterval(() => {
            let heart = document.createElement("div");
            heart.innerHTML = "❤️";
            heart.classList.add("falling-heart");
            heart.style.left = Math.random() * window.innerWidth + "px";
            heart.style.animation = "fallingHearts 5s linear";
            document.body.appendChild(heart);
            setTimeout(() => { heart.remove(); }, 5000);
        }, 300);
    }

    document.getElementById("musicButton").addEventListener("click", function() {
        let song = document.getElementById("loveSong");
        song.currentTime = 30; // Start from 30 seconds
        song.play();
        this.style.display = "none"; // Hide button after clicking
    });

    fallingHearts();
</script>

</body>
</html>
