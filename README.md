<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Surprise!</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@400;600;700&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Hind Siliguri', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background: linear-gradient(135deg, #1f1235, #321e54, #4a2160, #2b1040);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            color: white;
        }

        .app-container {
            width: 100%;
            max-width: 420px;
            height: 100vh;
            max-height: 880px;
            padding: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }

        .bg-decorations {
            position: fixed;
            inset: 0;
            overflow: hidden;
            pointer-events: none;
        }

        .floating-item {
            position: absolute;
            font-size: 1.5rem;
            opacity: .6;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%,100% {
                transform: translateY(0) rotate(0);
            }
            50% {
                transform: translateY(-20px) rotate(10deg);
            }
        }

        .card {
            width: 100%;
            min-height: 480px;
            padding: 35px 25px;
            border-radius: 28px;
            background: rgba(255,255,255,.08);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255,255,255,.15);
            box-shadow:
                0 20px 50px rgba(0,0,0,.4),
                inset 0 0 15px rgba(255,255,255,.05);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            z-index: 10;
        }

        .screen {
            display: none;
            width: 100%;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            opacity: 0;
            transform: translateY(20px) scale(.95);
        }

        .screen.active {
            display: flex;
            animation: appear .5s ease forwards;
        }

        @keyframes appear {
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        h1 {
            color: #ffd166;
            font-size: 1.8rem;
            line-height: 1.3;
            margin-bottom: 15px;
            text-shadow: 0 0 12px rgba(255,209,102,.4);
        }

        .primary-text {
            font-size: 1.2rem;
            line-height: 1.6;
            color: #f1f1f1;
            margin-bottom: 15px;
        }

        .sub-text {
            font-size: 1rem;
            color: #d1c4e9;
            margin-bottom: 25px;
        }

        .final-note {
            font-size: .95rem;
            color: #ffb74d;
            margin-top: 15px;
            font-style: italic;
        }

        .gift-icon {
            font-size: 5rem;
            margin-bottom: 20px;
            animation: bounce 2s infinite;
        }

        .emoji-group {
            font-size: 2.2rem;
            margin: 15px 0;
            letter-spacing: 5px;
            animation: pulse 1.5s infinite alternate;
        }

        @keyframes bounce {
            0%,20%,50%,80%,100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-18px);
            }
            60% {
                transform: translateY(-8px);
            }
        }

        @keyframes pulse {
            from {
                transform: scale(1);
            }
            to {
                transform: scale(1.1);
            }
        }

        .btn {
            border: none;
            outline: none;
            cursor: pointer;
            margin-top: 10px;
            padding: 14px 32px;
            border-radius: 50px;
            color: white;
            background: linear-gradient(135deg,#ff4081,#ff80ab);
            font-size: 1.1rem;
            font-weight: 600;
            box-shadow: 0 8px 20px rgba(255,64,129,.4);
            transition: .3s;
        }

        .btn:active {
            transform: scale(.96);
        }

        #confetti-canvas {
            position: fixed;
            inset: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            z-index: 100;
        }
    </style>
</head>

<body>

<canvas id="confetti-canvas"></canvas>

<div class="bg-decorations" id="bgDecor"></div>

<div class="app-container">
    <div class="card">

        <!-- SCREEN 1 -->
        <div class="screen active" id="screen1">
            <div class="gift-icon">🎁</div>

            <p class="primary-text">
                এই Botli, তোর জন্য একটা জিনিস আছে... 👀
            </p>

            <p class="sub-text">
                একটু ধৈর্য ধরে শেষ পর্যন্ত দেখিস।
            </p>

            <button class="btn" onclick="nextScreen(2)">
                খুল তো 😌
            </button>
        </div>

        <!-- SCREEN 2 -->
        <div class="screen" id="screen2">
            <div class="emoji-group">😌✨</div>

            <p class="primary-text">
                Sokal, আজকে বেশি ভাব নেওয়ার দরকার নেই 😌<br>
                তোর জন্য এত কষ্ট করে কিছু বানানো হয়েছে,<br>
                তাই চুপচাপ দেখে যা। 😂
            </p>

            <button class="btn" onclick="nextScreen(3)">
                আচ্ছা, পরেরটা দেখ
            </button>
        </div>

        <!-- SCREEN 3 -->
        <div class="screen" id="screen3">

            <p class="primary-text">
                Botli, বয়স বাড়তেছে ঠিকই,<br>
                কিন্তু বুদ্ধি যে সেই হারে বাড়তেছে—<br>
                তার কোনো প্রমাণ এখনো পাওয়া যায়নি। 😂
            </p>

            <div class="emoji-group">
                😂 🤦‍♂️ 🎉
            </div>

            <button class="btn" onclick="nextScreen(4)">
                আরও আছে 👀
            </button>
        </div>

        <!-- SCREEN 4 -->
        <div class="screen" id="screen4">

            <h1>
                Happy Birthday, Botli! 🎂🎉
            </h1>

            <p class="primary-text">
                জীবনের নতুন বছরটা যেন তোর জন্য<br>
                অনেক হাসি, ভালো সময় আর সুন্দর স্মৃতি নিয়ে আসে।<br>
                সবসময় ভালো থাকিস, নিজের মতো থাকিস,<br>
                আর হ্যাঁ—আজকে একটু কম পাগলামি করিস। 😂
            </p>

            <button class="btn" onclick="nextScreen(5)">
                শেষটা দেখ
            </button>
        </div>

        <!-- SCREEN 5 -->
        <div class="screen" id="screen5">

            <p class="primary-text">
                Botli, বেশি কিছু বলব না。<br>
                শুধু বলি—ভালো থাকিস, হাসিখুশি থাকিস,<br>
                আর তোর এই পাগলামিগুলো যেন এমনই থাকে। 😌😂
                <br><br>
                আজকের দিনটা ভালোভাবে enjoy কর। 🎉
            </p>

            <p class="final-note">
                আচ্ছা, এবার যা—অনেক হয়ে গেছে। 😂
            </p>

        </div>

    </div>
</div>

<script>

const decorItems = [
    '⭐','✨','🎁','🎈','⚡','🎉','🌟'
];

const bgContainer = document.getElementById('bgDecor');

for(let i = 0; i < 15; i++){

    const item = document.createElement('div');

    item.className = 'floating-item';

    item.innerText =
        decorItems[Math.floor(Math.random() * decorItems.length)];

    item.style.left = Math.random() * 100 + '%';
    item.style.top = Math.random() * 100 + '%';

    item.style.animationDelay =
        Math.random() * 5 + 's';

    item.style.animationDuration =
        (Math.random() * 4 + 4) + 's';

    bgContainer.appendChild(item);
}


function nextScreen(screenNum){

    const current =
        document.querySelector('.screen.active');

    if(current){
        current.classList.remove('active');
    }

    setTimeout(() => {

        const target =
            document.getElementById('screen' + screenNum);

        if(target){
            target.classList.add('active');
        }

        if(screenNum === 4){
            startConfetti();
        }

    },300);
}


/* CONFETTI */

const canvas =
    document.getElementById('confetti-canvas');

const ctx =
    canvas.getContext('2d');

let particles = [];
let animationFrame;


function resizeCanvas(){

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

}

window.addEventListener(
    'resize',
    resizeCanvas
);

resizeCanvas();


function createConfettiParticle(){

    const colors = [
        '#ff4081',
        '#ffd166',
        '#06d6a0',
        '#118ab2',
        '#ff80ab',
        '#b388ff'
    ];

    return {

        x: Math.random() * canvas.width,

        y:
            Math.random() * canvas.height
            - canvas.height,

        size:
            Math.random() * 8 + 4,

        color:
            colors[
                Math.floor(
                    Math.random() * colors.length
                )
            ],

        speedY:
            Math.random() * 3 + 2,

        speedX:
            Math.random() * 2 - 1,

        spin:
            Math.random() * 360,

        spinSpeed:
            Math.random() * 10 - 5
    };
}


function startConfetti(){

    cancelAnimationFrame(animationFrame);

    particles = [];

    for(let i = 0; i < 100; i++){

        particles.push(
            createConfettiParticle()
        );

    }

    animateConfetti();
}


function animateConfetti(){

    ctx.clearRect(
        0,
        0,
        canvas.width,
        canvas.height
    );

    let activeParticles = false;

    particles.forEach(p => {

        p.y += p.speedY;
        p.x += p.speedX;
        p.spin += p.spinSpeed;

        ctx.save();

        ctx.translate(p.x,p.y);

        ctx.rotate(
            p.spin * Math.PI / 180
        );

        ctx.fillStyle = p.color;

        ctx.fillRect(
            -p.size / 2,
            -p.size / 2,
            p.size,
            p.size
        );

        ctx.restore();

        if(p.y < canvas.height){
            activeParticles = true;
        }

    });

    if(activeParticles){

        animationFrame =
            requestAnimationFrame(
                animateConfetti
            );

    }else{

        ctx.clearRect(
            0,
            0,
            canvas.width,
            canvas.height
        );

    }
}

</script>

</body>
</html>
