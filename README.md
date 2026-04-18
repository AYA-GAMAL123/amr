!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Happy Birthday Amory 🎉</title>
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">
    <style>
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body {
            margin: 0; padding: 0; height: 100vh;
            background: linear-gradient(180deg, #813054 0%, #d86d99 100%);
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            font-family: 'Great Vibes', cursive; overflow: hidden; color: #f8e4d8; text-align: center;
            position: relative;
        }
        .content { z-index: 10; width: 100%; }
        h1 { font-size: 3.5rem; margin: 0; }
        .name { font-size: 4.5rem; margin-bottom: 10px; display: block; }
        .cake-btn {
            background: none; border: none; font-size: 100px;
            cursor: pointer; outline: none; display: block; margin: 0 auto;
            transition: transform 0.3s;
        }
        .cake-btn:active { transform: scale(0.9); }
        .gift { font-size: 50px; animation: bounce 2s infinite; }
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-20px); }
        }
        .hint { font-family: sans-serif; font-size: 14px; margin-top: 20px; opacity: 0.8; }
        .heart {
            position: absolute; bottom: -50px;
            animation: floatUp 4s linear forwards; pointer-events: none; z-index: 5;
        }
        @keyframes floatUp {
            to { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body onclick="startExperience()">

    <div class="content">
        <h1>Happy Birthday</h1>
        <span class="name">Amory</span>
        
        <button class="cake-btn">🎂</button>
        
        <div class="gift">🎁</div>
        <p class="hint" id="hintText">✨ اضغط في أي مكان للمفاجأة ✨</p>
    </div>

    <audio id="birthdayAudio" loop playsinline>
        <source src="./_happybirthday .mp3" type="audio/mpeg">
    </audio>

    <script>
        let started = false;
        function startExperience() {
            if (started) return;
            
            const audio = document.getElementById('birthdayAudio');
            
            // محاولة تشغيل الصوت
            audio.play().then(() => {
                started = true;
                document.getElementById('hintText').style.opacity = "0";
                // بدأ ظهور القلوب
                setInterval(createHeart, 300);
            }).catch(error => {
                console.log("المنصفح محتاج لمسة كمان");
            });
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = ['❤️','💖','💗','✨'][Math.floor(Math.random()*4)];
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.fontSize = (Math.random() * 20 + 20) + 'px';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 4000);
        }
    </script>
</body>
</html>
