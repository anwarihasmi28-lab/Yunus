<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For You ❤️</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Dancing+Script:wght@400;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(-45deg, #ff9a9e 0%, #fecfef 25%, #fecfef 50%, #a8edea 75%, #fed6e3 100%);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            color: #4a4a4a;
            overflow-x: hidden;
            min-height: 100vh;
            cursor: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24'><path fill='%23ff69b4' d='M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z'/></svg>"), auto;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Floating Hearts */
        #heartsContainer {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .heart {
            position: absolute;
            color: rgba(255, 105, 180, 0.6);
            font-size: 18px;
            animation: float 8s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        /* Welcome Screen */
        #welcome {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            z-index: 100;
            animation: fadeIn 1s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        .welcome-text {
            font-family: 'Dancing Script', cursive;
            font-size: clamp(2.5rem, 10vw, 5rem);
            background: linear-gradient(45deg, #ff6b9d, #c44569);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 30px;
            text-shadow: 0 4px 20px rgba(255, 107, 157, 0.3);
        }

        .enter-btn {
            background: linear-gradient(45deg, #ff6b9d, #c44569);
            border: none;
            color: white;
            padding: 18px 50px;
            font-size: 1.2rem;
            font-weight: 500;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(255, 107, 157, 0.4);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .enter-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(255, 107, 157, 0.6);
        }

        /* Main Container */
        #main {
            display: none;
            min-height: 100vh;
            padding: 100px 20px 50px;
            max-width: 900px;
            margin: 0 auto;
        }

        /* Sections */
        .section {
            margin-bottom: 80px;
            opacity: 0;
            transform: translateY(40px);
            animation: slideInUp 0.8s ease forwards;
        }

        @keyframes slideInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section:nth-child(1) { animation-delay: 0.1s; }
        .section:nth-child(2) { animation-delay: 0.2s; }
        .section:nth-child(3) { animation-delay: 0.3s; }
        .section:nth-child(4) { animation-delay: 0.4s; }
        .section:nth-child(5) { animation-delay: 0.5s; }

        /* Headings */
        .section h2 {
            font-family: 'Dancing Script', cursive;
            font-size: clamp(2.5rem, 8vw, 4.5rem);
            background: linear-gradient(45deg, #ff6b9d, #c44569);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 25px;
            text-align: center;
        }

        /* Text Content */
        .content {
            font-size: 1.2rem;
            line-height: 1.8;
            text-align: center;
            max-width: 700px;
            margin: 0 auto 40px;
            color: #555;
        }

        .typing {
            overflow: hidden;
            border-right: 3px solid #ff6b9d;
            white-space: nowrap;
            animation: typing 3s steps(40) forwards, blink 0.75s infinite;
            margin: 0 auto 20px;
            font-size: 1.2rem;
            font-weight: 500;
        }

        @keyframes typing {
            from { width: 0; }
        }

        @keyframes blink {
            50% { border-color: transparent; }
        }

        /* Shayari */
        .shayari {
            background: rgba(255, 255, 255, 0.6);
            backdrop-filter: blur(15px);
            padding: 40px;
            border-radius: 25px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            font-size: 1.3rem;
            line-height: 2;
            text-align: center;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            margin: 40px auto;
            max-width: 800px;
        }

        .shayari-line {
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.6s ease forwards;
            margin-bottom: 15px;
        }

        .shayari-line:nth-child(1) { animation-delay: 0.2s; }
        .shayari-line:nth-child(2) { animation-delay: 0.4s; }
        .shayari-line:nth-child(3) { animation-delay: 0.6s; }
        .shayari-line:nth-child(4) { animation-delay: 0.8s; }

        /* Buttons */
        .love-btn {
            background: linear-gradient(45deg, #ff9a8b, #ff6b9d);
            border: none;
            color: white;
            padding: 16px 40px;
            font-size: 1.1rem;
            font-weight: 500;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 25px rgba(255, 154, 139, 0.4);
            display: inline-block;
            margin: 20px 10px;
        }

        .love-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 35px rgba(255, 154, 139, 0.6);
        }

        /* Popup */
        #popup {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            background: linear-gradient(45deg, #ff6b9d, #c44569);
            color: white;
            padding: 35px 50px;
            border-radius: 25px;
            font-size: 1.4rem;
            font-weight: 600;
            z-index: 1000;
            box-shadow: 0 20px 50px rgba(255, 107, 157, 0.4);
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            text-align: center;
        }

        #popup.show {
            transform: translate(-50%, -50%) scale(1);
        }

        /* Surprise */
        .surprise-text {
            font-family: 'Dancing Script', cursive;
            font-size: clamp(3rem, 12vw, 6rem);
            background: linear-gradient(45deg, #ffd700, #ffed4e);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 40px rgba(255, 215, 0, 0.5);
            animation: glowPulse 2s ease-in-out infinite alternate;
            margin-top: 30px;
        }

        @keyframes glowPulse {
            from { 
                text-shadow: 0 0 20px rgba(255, 215, 0, 0.5);
                transform: scale(1);
            }
            to { 
                text-shadow: 0 0 40px rgba(255, 215, 0, 0.8);
                transform: scale(1.05);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            #main { padding: 80px 15px 30px; }
            .content, .shayari { font-size: 1.1rem; }
            .shayari { padding: 25px; margin: 30px 10px; }
            #popup { padding: 25px 35px; font-size: 1.2rem; }
        }

        /* Hide scrollbar for smooth look */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: rgba(255,255,255,0.1);
        }

        ::-webkit-scrollbar-thumb {
            background: linear-gradient(45deg, #ff6b9d, #c44569);
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <!-- Floating Hearts -->
    <div id="heartsContainer"></div>

    <!-- Welcome Screen -->
    <div id="welcome">
        <div class="welcome-text">Hey ❤️</div>
        <p style="font-size: 1.5rem; margin-bottom: 40px; color: #666;">I made something special for you...</p>
        <button class="enter-btn" onclick="enterSite()">Enter 💌</button>
    </div>

    <!-- Main Content -->
    <div id="main">
        <!-- Miss You Section -->
        <div class="section">
            <h2 class="typing">I Miss You 💔</h2>
            <div class="content">
                Every morning I wake up reaching for you, but you're not there. 
                Your smile haunts my thoughts, your voice echoes in my quiet moments. 
                The coffee we used to share tastes different now, the songs we loved feel empty. 
                Even the stars seem dimmer without you looking at them with me. 
                I miss the way your hand fits perfectly in mine, the way your laughter fills every corner of my heart. 
                Come back soon... I'm counting every heartbeat until you're here again.
            </div>
        </div>

        <!-- Shayari Section -->
        <div class="section">
            <div class="shayari">
                <div class="shayari-line">Teri tasveer dekh kar muskura leta hu,</div>
                <div class="shayari-line">Tu paas nahi hai, phir bhi paas mehsoos karta hu,</div>
                <div class="shayari-line">Har lamha tera hi khayal rehta hai,</div>
                <div class="shayari-line">Sach kahu… Misbah, main tujhe har din aur zyada miss karta hu ❤️</div>
            </div>
        </div>

        <!-- Interactive Button -->
        <div class="section" style="text-align: center;">
            <button class="love-btn" onclick="showPopup()">Do you miss me? 🥺</button>
        </div>

        <!-- Final Message -->
        <div class="section">
            <div class="content" style="font-size: 1.4rem; font-weight: 500; color: #ff6b9d;">
                No matter how far we are… 
                <span style="background: linear-gradient(45deg, #ff6b9d, #c44569); -webkit-background-clip: text; -webkit-text-fill-color: transparent;">
                    you're always in my heart ❤️
                </span>
            </div>
        </div>

        <!-- Surprise -->
        <div class="section" style="text-align: center;">
            <button class="love-btn" onclick="showSurprise()">One last thing 🎁</button>
            <div id="surprise" class="surprise-text" style="display: none;">I love you ❤️</div>
        </div>
    </div>

    <!-- Popup -->
    <div id="popup">I knew it 😌❤️</div>

    <script>
        // Enter site function
        function enterSite() {
            document.getElementById('welcome').style.display = 'none';
            document.getElementById('main').style.display = 'block';
            document.body.style.overflow = 'auto';
            createHearts();
            // Optional music (uncomment if you add audio file)
            // document.getElementById('bgMusic').play().catch(() => {});
        }

        // Create floating hearts
        function createHearts() {
            const container = document.getElementById('heartsContainer');
            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.innerHTML = '💖';
                heart.style.left = Math.random() * 100 + '%';
                heart.style.animationDuration = (Math.random() * 3 + 4) + 's';
                heart.style.fontSize = (Math.random() * 10 + 15) + 'px';
                container.appendChild(heart);
                setTimeout(() => heart.remove(), 8000);
            }, 300);
        }

        // Popup
        function showPopup() {
            const popup = document.getElementById('popup');
            popup.classList.add('show');
            
            // Heart animation on popup
            for(let i = 0; i < 10; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.innerHTML = '💕';
                    heart.style.position = 'fixed';
                    heart.style.left = '50%';
                    heart.style.top = '50%';
                    heart.style.fontSize = '20px';
                    heart.style.pointerEvents = 'none';
                    heart.style.zIndex = '1001';
                    heart.style.animation = 'float 2s ease-out forwards';
                    document.body.appendChild(heart);
                    setTimeout(() => heart.remove(), 2000);
                }, i * 100);
            }
            
            setTimeout(() => {
                popup.classList.remove('show');
            }, 2000);
        }

        // Surprise
        function showSurprise() {
            const surprise = document.getElementById('surprise');
            surprise.style.display = 'block';
            
            // Celebration hearts
            for(let i = 0; i < 20; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.innerHTML = ['💖', '💕', '💗', '💝'][Math.floor(Math.random() * 4)];
                    heart.style.position = 'fixed';
                    heart.style.left = Math.random() * 100 + '%';
                    heart.style.top = '100%';
                    heart.style.fontSize = '25px';
                    heart.style.pointerEvents = 'none';
                    heart.style.zIndex = '1001';
                    heart.style.animation = 'float 3s ease-out forwards';
                    document.body.appendChild(heart);
                    setTimeout(() => heart.remove(), 3000);
                }, i * 80);
            }
        }

        // Smooth scrolling
        document.documentElement.style.scrollBehavior = 'smooth';

        // Preload animations
        window.addEventListener('load', () => {
            document.body.style.opacity = '1';
        });
    </script>

    <!-- Optional Background Music (add your own audio file) -->
    <!--
    <audio id="bgMusic" loop preload="auto">
        <source src="romantic-bg.mp3" type="audio/mpeg">
    </audio>
    -->
</body>
</html>
