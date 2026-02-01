<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For My Loosuu 💖</title>

    <script src="https://cdn.tailwindcss.com"></script>

    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600;700&family=Quicksand:wght@400;600&display=swap" rel="stylesheet">

    <style>
        body {
            font-family: 'Quicksand', sans-serif;
            overflow: hidden;
            touch-action: manipulation;
        }

        .cursive { font-family: 'Dancing Script', cursive; }

        .bg-heart {
            position: absolute;
            top: -10%;
            font-size: 24px;
            color: rgba(255, 192, 203, 0.7);
            animation: floatDown linear infinite;
            pointer-events: none;
        }

        @keyframes floatDown {
            0% { transform: translateY(-10vh) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
        }

        .slide { display: none; animation: fadeIn 0.8s ease forwards; }
        .slide.active { display: flex; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .btn-pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(244,63,94,0.7); }
            70% { box-shadow: 0 0 0 20px rgba(244,63,94,0); }
            100% { box-shadow: 0 0 0 0 rgba(244,63,94,0); }
        }

        .glass-card {
            background: rgba(255,255,255,0.6);
            backdrop-filter: blur(10px);
            border-radius: 24px;
            box-shadow: 0 10px 40px rgba(255,105,135,0.25);
        }

        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            animation: confetti-fall 3s linear forwards;
            pointer-events: none;
        }

        @keyframes confetti-fall {
            0% { transform: translateY(-10vh) rotate(0deg); }
            100% { transform: translateY(110vh) rotate(720deg); }
        }
    </style>
</head>

<body class="bg-gradient-to-br from-rose-100 via-pink-100 to-rose-200 h-screen w-screen flex items-center justify-center relative p-4">

<div id="bg-container" class="absolute inset-0 overflow-hidden"></div>

<div id="main-card" class="glass-card w-full max-w-lg p-8 z-10 flex flex-col items-center justify-center min-h-[500px] text-center">

    <!-- Slide 0 -->
    <div class="slide active flex-col" id="slide-0">
        <div class="text-6xl mb-6 animate-bounce">💕</div>
        <h1 class="text-4xl text-rose-600 mb-4 cursive font-bold">
            Hey my Loosuu 💖
        </h1>
        <p class="text-lg text-gray-700 font-semibold">
            I made something special just for you.
        </p>
    </div>

    <!-- Slide 1 -->
    <div class="slide flex-col" id="slide-1">
        <div class="text-6xl mb-6">🌸</div>
        <h2 class="text-3xl text-rose-700 cursive">
            You make my world brighter every single day.
        </h2>
    </div>

    <!-- Slide 2 -->
    <div class="slide flex-col" id="slide-2">
        <div class="text-6xl mb-6 animate-pulse">❤️</div>
        <h2 class="text-3xl text-rose-800 cursive">
            You are my favorite thought, my safe place, my forever.
        </h2>
    </div>

    <!-- Slide 3 -->
    <div class="slide flex-col relative min-h-[250px]" id="slide-3">
        <div class="text-6xl mb-4">💘</div>
        <h1 class="text-5xl text-rose-600 mb-8 cursive font-bold">
            Will you be my Valentine?
        </h1>

        <div class="flex gap-6 relative">
            <button id="yesBtn" onclick="handleYes()" class="bg-rose-500 text-white font-bold py-3 px-10 rounded-full btn-pulse text-xl">
                YES 💖
            </button>
            <button id="noBtn" class="bg-gray-300 text-gray-600 font-bold py-3 px-8 rounded-full">
                NO 😅
            </button>
        </div>
    </div>

    <!-- Slide 4 -->
    <div class="slide flex-col" id="slide-4">
        <div class="text-7xl mb-4 animate-bounce">🌹</div>
        <h1 class="text-5xl text-rose-600 cursive font-bold">
            Happy Valentine’s Day 💕
        </h1>
        <p class="text-2xl text-rose-800 font-bold cursive mt-4">
            I choose you, Loosuu — always 💖
        </p>
    </div>

</div>

<script>
    let currentSlide = 0;
    let yesScale = 1;
    let noScale = 1;
    const slides = document.querySelectorAll('.slide');
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const bgContainer = document.getElementById('bg-container');

    // Floating hearts
    setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'bg-heart';
        heart.innerHTML = Math.random() > 0.5 ? '❤️' : '💗';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = Math.random() * 3 + 4 + 's';
        bgContainer.appendChild(heart);
        setTimeout(() => heart.remove(), 7000);
    }, 500);

    function nextSlide() {
        slides[currentSlide].classList.remove('active');
        currentSlide++;
        slides[currentSlide].classList.add('active');

        if (currentSlide === 3) initNoButton();
        if (currentSlide === 4) celebrate();
    }

    // Auto open animation
    window.onload = () => {
        const auto = setInterval(() => {
            if (currentSlide < 3) nextSlide();
            else clearInterval(auto);
        }, 2500);
    };

    function initNoButton() {
        noBtn.addEventListener('mouseover', moveNo);
        noBtn.addEventListener('click', moveNo);
    }

    function moveNo() {
        yesScale += 0.3;
        yesBtn.style.transform = `scale(${yesScale})`;

        noScale = Math.max(0.2, noScale - 0.15);
        noBtn.style.transform = `scale(${noScale})`;

        noBtn.style.position = 'absolute';
        noBtn.style.left = Math.random() * 200 + 'px';
        noBtn.style.top = Math.random() * 120 + 'px';
    }

    function handleYes() {
        nextSlide();
    }

    function celebrate() {
        const colors = ['#ff69b4','#ff1493','#ffffff'];
        for (let i = 0; i < 100; i++) {
            setTimeout(() => {
                const c = document.createElement('div');
                c.className = 'confetti';
                c.style.backgroundColor = colors[Math.floor(Math.random()*colors.length)];
                c.style.left = Math.random()*100 + 'vw';
                document.body.appendChild(c);
                setTimeout(() => c.remove(), 4000);
            }, i * 30);
        }
    }
</script>

</body>
</html>
