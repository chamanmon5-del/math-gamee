<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>بازی ریاضی - جمع و تفریق اعداد مخلوط</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #d9afd9 0%, #f8c8dc 100%);
            color: #333;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 900px;
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            overflow: hidden;
            position: relative;
        }
        
        .header {
            background: linear-gradient(90deg, #d9afd9, #c895d6);
            color: white;
            padding: 20px;
            text-align: center;
            position: relative;
        }
        
        .header h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }
        
        .header p {
            font-size: 1.2rem;
            margin-bottom: 5px;
        }
        
        .teacher-info {
            background: linear-gradient(90deg, #f8c8dc, #f5b0cb);
            padding: 12px;
            border-radius: 10px;
            margin: 10px 0;
            font-weight: bold;
            color: #2D3436;
            text-align: center;
            border: 2px solid #e6a0c0;
        }
        
        .game-info {
            display: flex;
            justify-content: space-between;
            padding: 15px 20px;
            background: linear-gradient(90deg, #f8f9fa, #e9ecef);
            border-bottom: 2px solid #dee2e6;
        }
        
        .coins-container {
            display: flex;
            align-items: center;
            gap: 3px;
        }
        
        .coin {
            width: 20px;
            height: 20px;
            background: #FFD700;
            border-radius: 50%;
            border: 2px solid #FFA500;
            box-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }
        
        .coin.empty {
            background: #E9ECEF;
            border-color: #6C757D;
        }
        
        .score {
            font-weight: bold;
            font-size: 1.2rem;
            color: #9b59b6;
            background: white;
            padding: 5px 15px;
            border-radius: 20px;
            border: 2px solid #9b59b6;
        }
        
        .controls {
            display: flex;
            gap: 10px;
        }
        
        .control-btn {
            background: white;
            border: 2px solid #9b59b6;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            font-size: 1.2rem;
            cursor: pointer;
            color: #9b59b6;
            transition: all 0.3s ease;
        }
        
        .control-btn:hover {
            background: #9b59b6;
            color: white;
        }
        
        .game-area {
            padding: 30px 20px;
            text-align: center;
            background: white;
        }
        
        .game-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: #2C3E50;
            background: linear-gradient(90deg, #9b59b6, #8e44ad);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .level-selection {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 30px 0;
        }
        
        .level-btn {
            padding: 20px 40px;
            border: none;
            border-radius: 50px;
            font-size: 1.3rem;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: bold;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        
        .level-1 {
            background: linear-gradient(90deg, #2ecc71, #27ae60);
            color: white;
        }
        
        .level-2 {
            background: linear-gradient(90deg, #e74c3c, #c0392b);
            color: white;
        }
        
        .level-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.3);
        }
        
        .problem-display {
            font-size: 2.2rem;
            margin-bottom: 25px;
            line-height: 1.6;
            background: linear-gradient(135deg, #F8F9FA, #E9ECEF);
            padding: 20px;
            border-radius: 15px;
            border-right: 5px solid #9b59b6;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            min-height: 120px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .answer-section {
            margin-bottom: 25px;
            padding: 20px;
            background: linear-gradient(135deg, #f0f8ff, #e6f7ff);
            border-radius: 15px;
            border: 2px dashed #9b59b6;
        }
        
        .answer-label {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: #9b59b6;
            font-weight: bold;
        }
        
        .answer-input {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            font-size: 2rem;
        }
        
        .mixed-number {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .fraction-input {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
        }
        
        .fraction-line {
            border-top: 2px solid #9b59b6;
            width: 60px;
            height: 2px;
            background: #9b59b6;
        }
        
        .input-box {
            width: 80px;
            height: 80px;
            text-align: center;
            font-size: 2rem;
            border: 3px solid #9b59b6;
            border-radius: 15px;
            background: #ffffff;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }
        
        .input-box:focus {
            border-color: #8e44ad;
            box-shadow: 0 0 0 3px rgba(158, 84, 173, 0.3);
            outline: none;
        }
        
        .input-label {
            font-size: 1rem;
            color: #7f8c8d;
            margin-top: 5px;
        }
        
        .keyboard {
            display: grid;
            grid-template-columns: repeat(6, 1fr);
            gap: 10px;
            margin-bottom: 25px;
            padding: 0 10px;
        }
        
        .key {
            background: linear-gradient(135deg, #9b59b6, #8e44ad);
            color: white;
            border: none;
            padding: 15px 5px;
            border-radius: 12px;
            font-size: 1.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            min-height: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .key:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.3);
            background: linear-gradient(135deg, #8e44ad, #7d3c98);
        }
        
        .key:active {
            transform: translateY(0);
        }
        
        .actions {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
        }
        
        .btn {
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: bold;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        
        .btn-primary {
            background: linear-gradient(90deg, #9b59b6, #8e44ad);
            color: white;
        }
        
        .btn-secondary {
            background: linear-gradient(90deg, #95a5a6, #7f8c8d);
            color: white;
        }
        
        .btn-success {
            background: linear-gradient(90deg, #2ecc71, #27ae60);
            color: white;
        }
        
        .btn-danger {
            background: linear-gradient(90deg, #e74c3c, #c0392b);
            color: white;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.3);
        }
        
        .hidden {
            display: none !important;
        }
        
        .result {
            text-align: center;
            padding: 40px 30px;
            background: white;
        }
        
        .result h2 {
            font-size: 2.2rem;
            margin-bottom: 20px;
            color: #2C3E50;
        }
        
        .result-score {
            font-size: 4rem;
            font-weight: bold;
            color: #9b59b6;
            margin: 20px 0;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
            background: linear-gradient(135deg, #9b59b6, #8e44ad);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .flowers {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 10;
            opacity: 0;
            transition: opacity 0.5s ease;
        }
        
        .flower {
            position: absolute;
            font-size: 2.5rem;
            animation: fall 3s linear forwards;
        }
        
        @keyframes fall {
            0% {
                transform: translateY(-100px) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }
        
        .progress {
            height: 12px;
            background: #E9ECEF;
            border-radius: 10px;
            margin-bottom: 25px;
            overflow: hidden;
            box-shadow: inset 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #d9afd9, #c895d6);
            width: 0%;
            transition: width 0.5s ease;
            border-radius: 10px;
        }
        
        .volume-control {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 10px;
            justify-content: center;
        }
        
        .volume-slider {
            width: 100px;
        }
        
        .end-game-btn {
            position: absolute;
            bottom: 20px;
            left: 20px;
            background: linear-gradient(90deg, #e74c3c, #c0392b);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 50px;
            font-size: 1rem;
            cursor: pointer;
            z-index: 1000;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        
        .instructions {
            font-size: 1.1rem;
            color: #5D6D7E;
            margin-bottom: 20px;
            line-height: 1.6;
            text-align: center;
        }
        
        .fraction-display {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 0 10px;
        }
        
        .fraction-number {
            font-size: 2rem;
        }
        
        .fraction-divider {
            width: 60px;
            height: 2px;
            background: #333;
            margin: 2px 0;
        }
        
        .level-info {
            font-size: 1.2rem;
            color: #7f8c8d;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- دکمه پایان بازی در پایین صفحه -->
        <button class="end-game-btn" id="global-end-game-btn">پایان بازی</button>
        
        <div class="header">
            <h1>بازی ریاضی - جمع و تفریق اعداد مخلوط</h1>
            <p>کلاس پنجم - تمرین جمع و تفریق اعداد مخلوط با مخرج برابر</p>
            <div class="teacher-info">
                شقایق - آموزگار: منیره راه چمنی
            </div>
        </div>
        
        <div class="game-info">
            <div class="coins-container" id="coins-container">
                <!-- سکه‌ها اینجا ایجاد می‌شوند -->
            </div>
            <div class="score" id="score">امتیاز: ۰</div>
            <div class="controls">
                <button class="control-btn" id="sound-toggle">🔊</button>
                <button class="control-btn" id="music-toggle">🎵</button>
            </div>
        </div>
        
        <div class="game-area">
            <!-- صفحه شروع -->
            <div id="start-screen">
                <h2 class="game-title">به بازی ریاضی خوش آمدید!</h2>
                <div class="instructions">
                    <p>در این بازی، شما باید جمع و تفریق اعداد مخلوط با مخرج برابر را حل کنید.</p>
                    <p>برای هر پاسخ صحیح ۱ امتیاز دریافت می‌کنید و برای هر پاسخ غلط ۱ امتیاز کسر می‌شود.</p>
                    <p class="level-info">سطح ۱: ۲۰ سوال | سطح ۲: ۲۰ سوال</p>
                </div>
                
                <div class="level-selection">
                    <button class="level-btn level-1" data-level="1">سطح ۱</button>
                    <button class="level-btn level-2" data-level="2">سطح ۲</button>
                </div>
                
                <div class="volume-control">
                    <span>صدای موسیقی:</span>
                    <input type="range" min="0" max="100" value="50" class="volume-slider" id="music-volume">
                    <span>صدای اثرها:</span>
                    <input type="range" min="0" max="100" value="70" class="volume-slider" id="sound-volume">
                </div>
            </div>
            
            <!-- صفحه بازی -->
            <div id="game-screen" class="hidden">
                <h2 class="game-title" id="level-title">سطح ۱</h2>
                
                <div class="progress">
                    <div class="progress-bar" id="progress-bar"></div>
                </div>
                
                <div class="problem-display" id="problem-display">
                    <!-- مسئله ریاضی اینجا نمایش داده می‌شود -->
                </div>
                
                <div class="answer-section">
                    <div class="answer-label">پاسخ خود را به صورت عدد مخلوط وارد کنید:</div>
                    <div class="answer-input">
                        <div class="mixed-number">
                            <div class="fraction-input">
                                <input type="number" class="input-box" id="whole-part" placeholder="۰" min="0">
                                <div class="input-label">عدد صحیح</div>
                            </div>
                            <span style="font-size: 2rem;">و</span>
                            <div class="fraction-input">
                                <input type="number" class="input-box" id="numerator" placeholder="۰" min="0">
                                <div class="fraction-line"></div>
                                <input type="number" class="input-box" id="denominator" placeholder="۰" min="1" readonly>
                                <div class="input-label">کسر</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="keyboard" id="keyboard">
                    <!-- کلیدهای اعداد اینجا ایجاد می‌شوند -->
                </div>
                
                <div class="actions">
                    <button class="btn btn-secondary" id="clear-btn">پاک کردن</button>
                    <button class="btn btn-success" id="submit-btn">بررسی پاسخ</button>
                    <button class="btn btn-danger" id="skip-btn">سوال بعدی</button>
                </div>
            </div>
            
            <!-- صفحه نتیجه -->
            <div id="result-screen" class="hidden">
                <div class="result">
                    <h2 id="result-title">تبریک! شما بازی را به پایان رساندید</h2>
                    <p style="font-size: 1.3rem; color: #5D6D7E;">امتیاز نهایی شما:</p>
                    <div class="result-score" id="final-score">۰</div>
                    <p style="font-size: 1.2rem; color: #5D6D7E;">تعداد سکه‌های کسب شده: <span id="final-coins" style="color: #FFD700; font-weight: bold;">۰</span></p>
                    
                    <div class="actions">
                        <button class="btn btn-primary" id="restart-btn">بازی مجدد</button>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- افکت گل‌باران -->
        <div class="flowers" id="flowers"></div>
    </div>

    <!-- موسیقی و صداها -->
    <audio id="background-music" loop>
        <source src="0bikalam download1music.ir (1).mp3" type="audio/mpeg">
    </audio>
    <audio id="key-sound">
        <source src="https://assets.mixkit.co/sfx/preview/mixkit-select-click-1109.mp3" type="audio/mpeg">
    </audio>
    <audio id="correct-sound">
        <source src="Crowd Laughs Cheering And Applauding 3.wav" type="audio/wav">
    </audio>
    <audio id="wrong-sound">
        <source src="Wrong Answer Sound Effect.mp3" type="audio/mpeg">
    </audio>

    <script>
        // متغیرهای بازی
        let currentLevel = 1;
        let currentProblem = 0;
        let score = 0;
        let coins = 0;
        let totalProblems = 20;
        let soundEnabled = true;
        let musicEnabled = true;
        let currentWhole1, currentNumerator1, currentDenominator;
        let currentWhole2, currentNumerator2;
        let operation; // '+' یا '-'
        let correctWhole, correctNumerator;

        // عناصر DOM
        const startScreen = document.getElementById('start-screen');
        const gameScreen = document.getElementById('game-screen');
        const resultScreen = document.getElementById('result-screen');
        const levelTitle = document.getElementById('level-title');
        const problemDisplay = document.getElementById('problem-display');
        const wholePartInput = document.getElementById('whole-part');
        const numeratorInput = document.getElementById('numerator');
        const denominatorInput = document.getElementById('denominator');
        const keyboard = document.getElementById('keyboard');
        const scoreElement = document.getElementById('score');
        const coinsContainer = document.getElementById('coins-container');
        const finalScoreElement = document.getElementById('final-score');
        const finalCoinsElement = document.getElementById('final-coins');
        const resultTitle = document.getElementById('result-title');
        const progressBar = document.getElementById('progress-bar');
        const clearBtn = document.getElementById('clear-btn');
        const submitBtn = document.getElementById('submit-btn');
        const skipBtn = document.getElementById('skip-btn');
        const restartBtn = document.getElementById('restart-btn');
        const soundToggle = document.getElementById('sound-toggle');
        const musicToggle = document.getElementById('music-toggle');
        const levelButtons = document.querySelectorAll('.level-btn');
        const globalEndGameBtn = document.getElementById('global-end-game-btn');
        const flowersElement = document.getElementById('flowers');
        const musicVolume = document.getElementById('music-volume');
        const soundVolume = document.getElementById('sound-volume');
        const backgroundMusic = document.getElementById('background-music');
        const keySound = document.getElementById('key-sound');
        const correctSound = document.getElementById('correct-sound');
        const wrongSound = document.getElementById('wrong-sound');

        // تنظیم صداها
        backgroundMusic.volume = 0.5;
        keySound.volume = 0.7;
        correctSound.volume = 0.7;
        wrongSound.volume = 0.7;

        // ایجاد سکه‌ها (10 تایی)
        function createCoins() {
            coinsContainer.innerHTML = '';
            for (let i = 0; i < 10; i++) {
                const coin = document.createElement('div');
                coin.className = i < coins ? 'coin' : 'coin empty';
                coinsContainer.appendChild(coin);
            }
        }

        // پخش صداها
        function playKeySound() {
            if (!soundEnabled) return;
            try {
                keySound.currentTime = 0;
                keySound.play().catch(e => console.log("پخش صدا مجاز نیست"));
            } catch (error) {
                console.log("خطا در پخش صدا:", error);
            }
        }

        function playCorrectSound() {
            if (!soundEnabled) return;
            try {
                correctSound.currentTime = 0;
                correctSound.play().catch(e => console.log("پخش صدا مجاز نیست"));
            } catch (error) {
                console.log("خطا در پخش صدا:", error);
            }
        }

        function playWrongSound() {
            if (!soundEnabled) return;
            try {
                wrongSound.currentTime = 0;
                wrongSound.play().catch(e => console.log("پخش صدا مجاز نیست"));
            } catch (error) {
                console.log("خطا در پخش صدا:", error);
            }
        }

        // کنترل موسیقی پس‌زمینه
        function toggleBackgroundMusic() {
            if (musicEnabled) {
                backgroundMusic.play().catch(e => console.log("اتوماتیک پلی مجاز نیست"));
            } else {
                backgroundMusic.pause();
            }
        }

        // ایجاد صفحه کلید اعداد
        function createKeyboard() {
            keyboard.innerHTML = '';
            const numbers = ['1', '2', '3', '4', '5', '6', '7', '8', '9', '0', 'پاک کردن', 'تایید'];
            
            numbers.forEach(number => {
                const key = document.createElement('button');
                key.className = 'key';
                key.textContent = number;
                
                if (number === 'پاک کردن') {
                    key.style.background = 'linear-gradient(135deg, #e74c3c, #c0392b)';
                    key.addEventListener('click', clearAnswer);
                } else if (number === 'تایید') {
                    key.style.background = 'linear-gradient(135deg, #2ecc71, #27ae60)';
                    key.addEventListener('click', checkAnswer);
                } else {
                    key.addEventListener('click', () => addNumber(number));
                }
                
                keyboard.appendChild(key);
            });
        }

        // اضافه کردن عدد به پاسخ
        function addNumber(number) {
            playKeySound();
            
            // پیدا کردن فیلد فعال
            let activeField;
            if (document.activeElement === wholePartInput) {
                activeField = wholePartInput;
            } else if (document.activeElement === numeratorInput) {
                activeField = numeratorInput;
            } else {
                // اگر هیچ فیلدی فعال نیست، از عدد صحیح شروع کنیم
                activeField = wholePartInput;
                wholePartInput.focus();
            }
            
            // اضافه کردن عدد به فیلد فعال
            if (activeField.value === '') {
                activeField.value = number;
            } else {
                activeField.value += number;
            }
        }

        // پاک کردن پاسخ
        function clearAnswer() {
            playKeySound();
            wholePartInput.value = '';
            numeratorInput.value = '';
            wholePartInput.focus();
        }

        // تولید مسئله تصادفی
        function generateProblem() {
            // انتخاب تصادفی عملیات (جمع یا تفریق)
            operation = Math.random() > 0.5 ? '+' : '-';
            
            // مخرج مشترک
            currentDenominator = Math.floor(Math.random() * 8) + 2; // مخرج 2 تا 9
            
            if (currentLevel === 1) {
                // سطح ۱: اعداد کوچکتر
                currentWhole1 = Math.floor(Math.random() * 3) + 1; // عدد صحیح 1 تا 3
                currentWhole2 = Math.floor(Math.random() * 3) + 1; // عدد صحیح 1 تا 3
                currentNumerator1 = Math.floor(Math.random() * (currentDenominator - 1)) + 1; // صورت کوچکتر از مخرج
                currentNumerator2 = Math.floor(Math.random() * (currentDenominator - 1)) + 1; // صورت کوچکتر از مخرج
            } else {
                // سطح ۲: اعداد بزرگتر
                currentWhole1 = Math.floor(Math.random() * 5) + 1; // عدد صحیح 1 تا 5
                currentWhole2 = Math.floor(Math.random() * 5) + 1; // عدد صحیح 1 تا 5
                currentNumerator1 = Math.floor(Math.random() * (currentDenominator - 1)) + 1; // صورت کوچکتر از مخرج
                currentNumerator2 = Math.floor(Math.random() * (currentDenominator - 1)) + 1; // صورت کوچکتر از مخرج
            }
            
            // برای تفریق، مطمئن شویم نتیجه منفی نمی‌شود
            if (operation === '-') {
                const total1 = currentWhole1 + currentNumerator1 / currentDenominator;
                const total2 = currentWhole2 + currentNumerator2 / currentDenominator;
                
                if (total1 < total2) {
                    // اگر عدد اول کوچکتر است، جای آنها را عوض کنیم
                    [currentWhole1, currentWhole2] = [currentWhole2, currentWhole1];
                    [currentNumerator1, currentNumerator2] = [currentNumerator2, currentNumerator1];
                }
            }
            
            // محاسبه پاسخ صحیح
            calculateCorrectAnswer();
            
            // نمایش مسئله
            displayProblem();
            
            // تنظیم مخرج در پاسخ
            denominatorInput.value = currentDenominator;
        }

        // محاسبه پاسخ صحیح
        function calculateCorrectAnswer() {
            // تبدیل به کسر نامناسب
            const improperNumerator1 = currentWhole1 * currentDenominator + currentNumerator1;
            const improperNumerator2 = currentWhole2 * currentDenominator + currentNumerator2;
            
            let resultNumerator;
            if (operation === '+') {
                resultNumerator = improperNumerator1 + improperNumerator2;
            } else {
                resultNumerator = improperNumerator1 - improperNumerator2;
            }
            
            // تبدیل به عدد مخلوط
            correctWhole = Math.floor(resultNumerator / currentDenominator);
            correctNumerator = resultNumerator % currentDenominator;
            
            // اگر صورت صفر شد
            if (correctNumerator === 0) {
                correctNumerator = 0;
            }
        }

        // نمایش مسئله
        function displayProblem() {
            const problemHTML = `
                <div style="display: flex; align-items: center; justify-content: center; gap: 20px; direction: ltr;">
                    <div style="display: flex; align-items: center; gap: 10px;">
                        <span>${currentWhole1}</span>
                        <div class="fraction-display">
                            <div class="fraction-number">${currentNumerator1}</div>
                            <div class="fraction-divider"></div>
                            <div class="fraction-number">${currentDenominator}</div>
                        </div>
                    </div>
                    <div style="font-size: 2rem;">${operation}</div>
                    <div style="display: flex; align-items: center; gap: 10px;">
                        <span>${currentWhole2}</span>
                        <div class="fraction-display">
                            <div class="fraction-number">${currentNumerator2}</div>
                            <div class="fraction-divider"></div>
                            <div class="fraction-number">${currentDenominator}</div>
                        </div>
                    </div>
                    <div style="font-size: 2rem;">=</div>
                    <div style="font-size: 2rem;">?</div>
                </div>
            `;
            
            problemDisplay.innerHTML = problemHTML;
        }

        // نمایش افکت گل‌باران
        function showFlowers() {
            flowersElement.style.opacity = '1';
            
            for (let i = 0; i < 15; i++) {
                const flower = document.createElement('div');
                flower.className = 'flower';
                flower.textContent = '🌸';
                flower.style.left = `${Math.random() * 100}%`;
                flower.style.animationDuration = `${1 + Math.random() * 2}s`;
                flowersElement.appendChild(flower);
                
                setTimeout(() => {
                    if (flower.parentNode) {
                        flower.remove();
                    }
                }, 3000);
            }
            
            setTimeout(() => {
                flowersElement.style.opacity = '0';
            }, 2000);
        }

        // بررسی پاسخ
        function checkAnswer() {
            const userWhole = parseInt(wholePartInput.value) || 0;
            const userNumerator = parseInt(numeratorInput.value) || 0;
            
            if (userWhole === correctWhole && userNumerator === correctNumerator) {
                // پاسخ صحیح
                score++;
                coins = Math.min(10, coins + 1);
                playCorrectSound();
                showFlowers();
                alert("آفرین! پاسخ شما صحیح است.");
                nextProblem();
            } else {
                // پاسخ غلط
                score = Math.max(0, score - 1);
                coins = Math.max(0, coins - 1);
                playWrongSound();
                alert(`پاسخ صحیح: ${correctWhole} و ${correctNumerator}/${currentDenominator}`);
                nextProblem();
            }
            
            updateScore();
            createCoins();
            updateProgressBar();
        }

        // رفتن به مسئله بعدی
        function nextProblem() {
            currentProblem++;
            if (currentProblem < totalProblems) {
                clearAnswer();
                generateProblem();
            } else {
                endGame();
            }
        }

        // به روزرسانی امتیاز
        function updateScore() {
            scoreElement.textContent = `امتیاز: ${score}`;
        }

        // به روزرسانی نوار پیشرفت
        function updateProgressBar() {
            const progress = ((currentProblem) / totalProblems) * 100;
            progressBar.style.width = `${progress}%`;
        }

        // پایان بازی
        function endGame() {
            gameScreen.classList.add('hidden');
            resultScreen.classList.remove('hidden');
            
            finalScoreElement.textContent = score;
            finalCoinsElement.textContent = coins;
            
            if (score >= 15) {
                resultTitle.textContent = "عالی! شما نتیجه فوق‌العاده‌ای کسب کردید!";
            } else if (score >= 10) {
                resultTitle.textContent = "خوب است! می‌توانید بهتر هم عمل کنید!";
            } else {
                resultTitle.textContent = "نیاز به تمرین بیشتر دارید. ناامید نشوید!";
            }
        }

        // رویدادها
        document.addEventListener('DOMContentLoaded', function() {
            console.log("بازی بارگذاری شد!");
            
            // ایجاد سکه‌ها و صفحه کلید
            createCoins();
            createKeyboard();
            
            // شروع موسیقی پس‌زمینه به محض بارگذاری صفحه
            setTimeout(() => {
                backgroundMusic.play().catch(e => console.log("پخش خودکار صدا مجاز نیست"));
            }, 500);
            
            // رویدادهای دکمه‌های سطح
            levelButtons.forEach(button => {
                button.addEventListener('click', function() {
                    currentLevel = parseInt(this.dataset.level);
                    startGame();
                });
            });
            
            clearBtn.addEventListener('click', clearAnswer);
            submitBtn.addEventListener('click', checkAnswer);
            skipBtn.addEventListener('click', nextProblem);
            restartBtn.addEventListener('click', restartGame);
            globalEndGameBtn.addEventListener('click', endGame);
            
            soundToggle.addEventListener('click', toggleSound);
            musicToggle.addEventListener('click', toggleMusic);
            
            // کنترل حجم صدا
            musicVolume.addEventListener('input', function() {
                backgroundMusic.volume = this.value / 100;
            });
            
            soundVolume.addEventListener('input', function() {
                keySound.volume = this.value / 100;
                correctSound.volume = this.value / 100;
                wrongSound.volume = this.value / 100;
            });
            
            // فوکوس اولیه روی عدد صحیح
            wholePartInput.focus();
        });

        // شروع بازی
        function startGame() {
            startScreen.classList.add('hidden');
            gameScreen.classList.remove('hidden');
            resultScreen.classList.add('hidden');
            
            currentProblem = 0;
            score = 0;
            coins = 0;
            
            levelTitle.textContent = `سطح ${currentLevel}`;
            totalProblems = 20; // ۲۰ سوال برای هر سطح
            
            updateScore();
            createCoins();
            generateProblem();
            updateProgressBar();
        }

        // کنترل صدا
        function toggleSound() {
            soundEnabled = !soundEnabled;
            soundToggle.textContent = soundEnabled ? '🔊' : '🔇';
        }

        function toggleMusic() {
            musicEnabled = !musicEnabled;
            musicToggle.textContent = musicEnabled ? '🎵' : '🔇';
            toggleBackgroundMusic();
        }

        // شروع مجدد بازی
        function restartGame() {
            resultScreen.classList.add('hidden');
            startScreen.classList.remove('hidden');
        }
    </script>
</body>
</html>
