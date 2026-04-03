# DUMMY-S-BD-CARD
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>21st Birthday Surprise</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Quicksand', sans-serif;
            background-color: #D2B48C;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
            padding: 20px;
        }

        .stage-container {
            position: relative;
            width: 100%;
            max-width: 1000px;
            opacity: 0;
            transition: opacity 1s ease-in-out;
        }

        .stage-container.active {
            opacity: 1;
        }

        /* Stage 1: Balloon Pop Intro */
        #stage1 {
            height: 600px;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
            padding: 40px;
        }

        .doodle-cat {
            width: 80px;
            height: 80px;
            position: absolute;
        }

        svg.cat-svg {
            width: 100%;
            height: 100%;
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.1));
        }

        .balloon {
            width: 50px;
            height: 70px;
            border-radius: 50% 50% 50% 0;
            cursor: pointer;
            animation: float 3s ease-in-out infinite;
            transform-origin: center bottom;
            position: absolute;
            box-shadow: inset -2px -2px 4px rgba(0,0,0,0.1);
            transition: all 0.2s ease;
        }

        .balloon:hover {
            transform: scale(1.05);
        }

        .balloon.pop-animation {
            animation: popScale 0.4s ease-out;
        }

        .balloon-string {
            position: absolute;
            width: 2px;
            height: 40px;
            background-color: rgba(0,0,0,0.3);
            bottom: -40px;
            left: 50%;
            transform: translateX(-1px);
        }

        .balloon-pink { background-color: #FFB3D9; }
        .balloon-blue { background-color: #B3D9FF; }
        .balloon-mint { background-color: #B3FFD9; }
        .balloon-lemon { background-color: #FFFAB3; }

        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-30px) rotate(2deg); }
        }

        @keyframes popScale {
            0% { transform: scale(1); }
            100% { transform: scale(0); opacity: 0; }
        }

        /* Stage 2: Birthday Cake */
        #stage2 {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 30px;
            min-height: 500px;
        }

        .cake-container {
            position: relative;
            display: flex;
            justify-content: center;
            align-items: flex-end;
            height: 300px;
        }

        .cake {
            width: 200px;
            height: 120px;
            background: linear-gradient(180deg, #F5F5F0 0%, #E8E8E0 100%);
            border-radius: 10px;
            border: 2px solid #C0C0B0;
            position: relative;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .cake::before {
            content: '';
            position: absolute;
            top: -15px;
            left: 0;
            right: 0;
            height: 20px;
            background: linear-gradient(180deg, #FFD1DC 0%, #FFC0CB 100%);
            border-radius: 10px 10px 0 0;
        }

        .cake::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 10%;
            width: 80%;
            height: 15px;
            background: linear-gradient(180deg, #FFC0CB 0%, #FFB3D9 100%);
            border-radius: 50%;
        }

        .berries {
            position: absolute;
            top: 20px;
            left: 20px;
            right: 20px;
            bottom: 20px;
            display: flex;
            justify-content: space-around;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        .berry {
            width: 12px;
            height: 12px;
            background-color: #4A90E2;
            border-radius: 50%;
            box-shadow: inset -1px -1px 2px rgba(0,0,0,0.2);
        }

        .candles {
            position: absolute;
            top: -40px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
        }

        .candle {
            width: 6px;
            height: 40px;
            background-color: #FFE4B5;
            border-radius: 3px;
            position: relative;
        }

        .flame {
            position: absolute;
            top: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 8px;
            height: 20px;
            background: linear-gradient(180deg, #FFA500 0%, #FFD700 100%);
            border-radius: 50% 50% 50% 0;
            animation: flicker 0.6s ease-in-out infinite;
        }

        @keyframes flicker {
            0%, 100% { transform: translateX(-50%) scaleY(1); }
            50% { transform: translateX(-50%) scaleY(1.1); opacity: 0.8; }
        }

        .cake-text {
            font-size: 24px;
            color: #6B4423;
            text-align: center;
            font-weight: 600;
        }

        .blow-button {
            padding: 12px 30px;
            font-size: 18px;
            font-family: 'Quicksand', sans-serif;
            font-weight: 600;
            background-color: #FFB3D9;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(255, 179, 217, 0.4);
            transition: all 0.3s ease;
            opacity: 0;
            animation: fadeIn 0.5s ease-out 1s forwards;
        }

        .blow-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 179, 217, 0.6);
        }

        .blow-button:active {
            transform: translateY(0);
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Stage 3: Quiz */
        #stage3 {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 600px;
            padding: 40px 20px;
        }

        .quiz-box {
            background-color: #E8DFF5;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.15);
            max-width: 500px;
            width: 100%;
        }

        .quiz-question {
            font-size: 24px;
            font-weight: 600;
            color: #6B4423;
            margin-bottom: 30px;
            text-align: center;
        }

        .quiz-options {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .quiz-option {
            padding: 15px 20px;
            background-color: white;
            border: 2px solid #D8C9E8;
            border-radius: 12px;
            font-size: 16px;
            font-family: 'Quicksand', sans-serif;
            cursor: pointer;
            transition: all 0.3s ease;
            color: #6B4423;
            font-weight: 500;
        }

        .quiz-option:hover {
            background-color: #F5F0FA;
            border-color: #C0A8D8;
            transform: translateX(5px);
        }

        .quiz-option.correct {
            background-color: #C8E6C9;
            border-color: #81C784;
        }

        .quiz-option.incorrect {
            background-color: #FFCDD2;
            border-color: #E57373;
            animation: shake 0.3s ease;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }

        .quiz-feedback {
            margin-top: 20px;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            font-weight: 600;
            font-style: italic;
            min-height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .feedback-correct {
            background-color: #C8E6C9;
            color: #2E7D32;
        }

        .feedback-incorrect {
            background-color: #FFCDD2;
            color: #C62828;
        }

        /* Stage 4: Letter & Gift */
        #stage4 {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 30px;
            min-height: 700px;
            padding: 40px 20px;
        }

        .letter-box {
            background-color: #FFD1DC;
            border-radius: 15px;
            padding: 30px;
            max-width: 600px;
            width: 100%;
            box-shadow: 0 10px 40px rgba(0,0,0,0.15);
            max-height: 400px;
            overflow-y: auto;
            font-size: 16px;
            line-height: 1.8;
            color: #6B4423;
        }

        .letter-box::-webkit-scrollbar {
            width: 8px;
        }

        .letter-box::-webkit-scrollbar-track {
            background: transparent;
        }

        .letter-box::-webkit-scrollbar-thumb {
            background: #FFB3D9;
            border-radius: 4px;
        }

        .bouquet-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        .lily-svg {
            width: 150px;
            height: 150px;
            filter: drop-shadow(0 5px 15px rgba(0,0,0,0.1));
        }

        .accept-bouquet-button,
        .accept-cat-button {
            padding: 12px 30px;
            font-size: 18px;
            font-family: 'Quicksand', sans-serif;
            font-weight: 600;
            background-color: #FFB3D9;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(255, 179, 217, 0.4);
            transition: all 0.3s ease;
        }

        .accept-bouquet-button:hover,
        .accept-cat-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 179, 217, 0.6);
        }

        .cat-with-bow {
            width: 120px;
            height: 120px;
            cursor: pointer;
            animation: bounce 0.6s ease-in-out;
            filter: drop-shadow(0 5px 15px rgba(0,0,0,0.1));
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        .accept-cat-button {
            margin-top: 20px;
            opacity: 0;
            animation: fadeIn 0.5s ease-out 2s forwards;
        }

        /* Navigation Button */
        .next-button {
            padding: 12px 30px;
            font-size: 18px;
            font-family: 'Quicksand', sans-serif;
            font-weight: 600;
            background-color: #FFB3D9;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(255, 179, 217, 0.4);
            transition: all 0.3s ease;
            margin-top: 20px;
        }

        .next-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 179, 217, 0.6);
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <!-- Stage 1: Balloon Pop Intro -->
    <div id="stage1" class="stage-container">
        <svg class="cat-svg doodle-cat" style="top: 50px; left: 10%;" viewBox="0 0 100 100">
            <circle cx="50" cy="50" r="40" fill="none" stroke="black" stroke-width="2"/>
            <circle cx="35" cy="40" r="8" fill="none" stroke="black" stroke-width="2"/>
            <circle cx="65" cy="40" r="8" fill="none" stroke="black" stroke-width="2"/>
            <circle cx="32" cy="38" r="3" fill="black"/>
            <circle cx="62" cy="38" r="3" fill="black"/>
            <circle cx="30" cy="55" r="4" fill="#FFB3D9"/>
            <circle cx="70" cy="55" r="4" fill="#FFB3D9"/>
            <path d="M 50 55 Q 50 65 45 70" fill="none" stroke="black" stroke-width="2" stroke-linecap="round"/>
            <path d="M 25 30 L 20 15 L 25 25" fill="none" stroke="black" stroke-width="2"/>
            <path d="M 75 30 L 80 15 L 75 25" fill="none" stroke="black" stroke-width="2"/>
        </svg>
        <svg class="cat-svg doodle-cat" style="top: 200px; right: 15%;" viewBox="0 0 100 100">
            <circle cx="50" cy="50" r="40" fill="none" stroke="black" stroke-width="2"/>
            <circle cx="35" cy="40" r="8" fill="none" stroke="black" stroke-width="2"/>
            <circle cx="65" cy="40" r="8" fill="none" stroke="black" stroke-width="2"/>
            <circle cx="32" cy="38" r="3" fill="black"/>
            <circle cx="62" cy="38" r="3" fill="black"/>
            <circle cx="30" cy="55" r="4" fill="#FFB3D9"/>
            <circle cx="70" cy="55" r="4" fill="#FFB3D9"/>
            <path d="M 50 55 Q 50 65 45 70" fill="none" stroke="black" stroke-width="2" stroke-linecap="round"/>
            <path d="M 25 30 L 20 15 L 25 25" fill="none" stroke="black" stroke-width="2"/>
            <path d="M 75 30 L 80 15 L 75 25" fill="none" stroke="black" stroke-width="2"/>
        </svg>
    </div>

    <!-- Stage 2: Birthday Cake -->
    <div id="stage2" class="stage-container hidden">
        <div class="cake-container">
            <div class="cake">
                <div class="candles">
                    <div class="candle"><div class="flame"></div></div>
                    <div class="candle"><div class="flame"></div></div>
                    <div class="candle"><div class="flame"></div></div>
                    <div class="candle"><div class="flame"></div></div>
                    <div class="candle"><div class="flame"></div></div>
                </div>
                <div class="berries">
                    <div class="berry"></div>
                    <div class="berry"></div>
                    <div class="berry"></div>
                    <div class="berry"></div>
                    <div class="berry"></div>
                </div>
            </div>
        </div>
        <p class="cake-text">Make a wish and blow out your candles!</p>
        <button class="blow-button">BLOW</button>
    </div>

    <!-- Stage 3: Quiz -->
    <div id="stage3" class="stage-container hidden">
        <div class="quiz-box">
            <div class="quiz-question" id="quizQuestion"></div>
            <div class="quiz-options" id="quizOptions"></div>
            <div class="quiz-feedback" id="quizFeedback"></div>
        </div>
    </div>

    <!-- Stage 4: Letter & Gift -->
    <div id="stage4" class="stage-container hidden">
        <div class="letter-box">
            <p>Tysm for existing honestly! Even though u r a total noobra n u r officially turning into a 21-year-old UNC today, u r still the realest bestie. It's actually wild that u r this old now but akal tabhi nahi aaye ge. Like it's actually a talent at this pt BUAHAHHAHAHA 💀</p>
            <br>
            <p>Seriously though, thx for being such a real fren. Whether we're messing around on DC or just talking rubbish, u r the 1 person who always keeps the energy 10/10. I hope this year brings u all the happiness n maybe a few brain cells if u r lucky!</p>
            <br>
            <p>N free nahi hona samjhe na? Just because u r an adult now doesn't mean u r not still a khambu. Also why tf r u smiling? Stop it, it's embarrassing! Hope ur day is legendary u ancient old man. Love ya always SJHJSAJJJJJ 🎈</p>
        </div>
        <div class="bouquet-container hidden" id="bouquetContainer">
            <svg class="lily-svg" viewBox="0 0 200 200">
                <!-- Yellow lilies -->
                <g id="yellowLily1">
                    <line x1="100" y1="180" x2="100" y2="80" stroke="#228B22" stroke-width="2"/>
                    <ellipse cx="90" cy="70" rx="8" ry="20" fill="#FFD700" transform="rotate(-30 90 70)"/>
                    <ellipse cx="110" cy="70" rx="8" ry="20" fill="#FFD700" transform="rotate(30 110 70)"/>
                    <ellipse cx="100" cy="50" rx="8" ry="20" fill="#FFD700"/>
                </g>
                <g id="yellowLily2" transform="translate(-40, 0)">
                    <line x1="100" y1="180" x2="100" y2="80" stroke="#228B22" stroke-width="2"/>
                    <ellipse cx="90" cy="70" rx="8" ry="20" fill="#FFD700" transform="rotate(-30 90 70)"/>
                    <ellipse cx="110" cy="70" rx="8" ry="20" fill="#FFD700" transform="rotate(30 110 70)"/>
                    <ellipse cx="100" cy="50" rx="8" ry="20" fill="#FFD700"/>
                </g>
                <!-- Red lilies -->
                <g id="redLily1" transform="translate(40, 0)">
                    <line x1="100" y1="180" x2="100" y2="80" stroke="#228B22" stroke-width="2"/>
                    <ellipse cx="90" cy="70" rx="8" ry="20" fill="#DC143C" transform="rotate(-30 90 70)"/>
                    <ellipse cx="110" cy="70" rx="8" ry="20" fill="#DC143C" transform="rotate(30 110 70)"/>
                    <ellipse cx="100" cy="50" rx="8" ry="20" fill="#DC143C"/>
                </g>
                <g id="redLily2" transform="translate(80, 0)">
                    <line x1="100" y1="180" x2="100" y2="80" stroke="#228B22" stroke-width="2"/>
                    <ellipse cx="90" cy="70" rx="8" ry="20" fill="#DC143C" transform="rotate(-30 90 70)"/>
                    <ellipse cx="110" cy="70" rx="8" ry="20" fill="#DC143C" transform="rotate(30 110 70)"/>
                    <ellipse cx="100" cy="50" rx="8" ry="20" fill="#DC143C"/>
                </g>
            </svg>
            <button class="accept-bouquet-button">Accept Bouquet</button>
        </div>
        <div id="catContainer" class="hidden">
            <svg class="cat-with-bow" viewBox="0 0 100 100">
                <circle cx="50" cy="50" r="40" fill="none" stroke="black" stroke-width="2"/>
                <circle cx="35" cy="40" r="8" fill="none" stroke="black" stroke-width="2"/>
                <circle cx="65" cy="40" r="8" fill="none" stroke="black" stroke-width="2"/>
                <circle cx="32" cy="38" r="3" fill="black"/>
                <circle cx="62" cy="38" r="3" fill="black"/>
                <circle cx="30" cy="55" r="4" fill="#FFB3D9"/>
                <circle cx="70" cy="55" r="4" fill="#FFB3D9"/>
                <path d="M 50 55 Q 50 65 45 70" fill="none" stroke="black" stroke-width="2" stroke-linecap="round"/>
                <path d="M 25 30 L 20 15 L 25 25" fill="none" stroke="black" stroke-width="2"/>
                <path d="M 75 30 L 80 15 L 75 25" fill="none" stroke="black" stroke-width="2"/>
                <!-- Pink Bow -->
                <circle cx="50" cy="28" r="6" fill="#FFB3D9"/>
                <circle cx="42" cy="30" r="5" fill="#FFB3D9"/>
                <circle cx="58" cy="30" r="5" fill="#FFB3D9"/>
            </svg>
            <button class="accept-cat-button">ACCEPT CAT</button>
        </div>
    </div>

    <script>
        // State Machine
        class BirthdayExperience {
            constructor() {
                this.currentStage = 1;
                this.balloons = [];
                this.quizIndex = 0;
                this.quizData = [
                    {
                        question: "When did we first talk?",
                        options: ["30 Jan 26", "21 Dec 25", "27 Feb 26", "28 Jan 26"],
                        correct: 0,
                        correctFeedback: "Awww",
                        incorrectFeedback: "Itna bhi nahi pata, noobra? Choose again, huh!"
                    },
                    {
                        question: "Who's your bestie?",
                        options: ["Mahnoor", "Mahnoor", "Mahnoor", "Anshi"],
                        correct: 0,
                        correctFeedback: "",
                        incorrectFeedback: "Chalo ji, dosti khatam!"
                    },
                    {
                        question: "What do I hate about you most?",
                        options: ["Everything", "Nothing", "Your other besties", "Your dumbass talks"],
                        correct: 2,
                        correctFeedback: "Wow, you know me very well.",
                        incorrectFeedback: ""
                    }
                ];
                this.init();
            }

            init() {
                this.showStage1();
            }

            showStage1() {
                this.hideAllStages();
                document.getElementById('stage1').classList.add('active');
                this.createBalloons();
            }

            createBalloons() {
                const stage1 = document.getElementById('stage1');
                const balloonColors = ['balloon-pink', 'balloon-blue', 'balloon-mint', 'balloon-lemon'];
                this.balloons = [];

                balloonColors.forEach((color, index) => {
                    const balloon = document.createElement('div');
                    balloon.className = `balloon ${color}`;
                    balloon.style.left = (20 + index * 20) + '%';
                    balloon.style.top = (100 - index * 15) + 'px';
                    balloon.style.animationDelay = (index * 0.3) + 's';
                    balloon.style.zIndex = index;

                    const string = document.createElement('div');
                    string.className = 'balloon-string';
                    balloon.appendChild(string);

                    balloon.addEventListener('click', () => this.popBalloon(balloon));
                    stage1.appendChild(balloon);
                    this.balloons.push(balloon);
                });
            }

            popBalloon(balloon) {
                balloon.classList.add('pop-animation');
                this.playSound('pop');
                setTimeout(() => {
                    balloon.remove();
                    this.balloons = this.balloons.filter(b => b !== balloon);
                    if (this.balloons.length === 0) {
                        setTimeout(() => this.showStage2(), 2000);
                    }
                }, 400);
            }

            showStage2() {
                this.hideAllStages();
                document.getElementById('stage2').classList.add('active');
                const blowButton = document.querySelector('.blow-button');
                blowButton.addEventListener('click', () => this.blowCandles());
            }

            blowCandles() {
                const flames = document.querySelectorAll('.flame');
                flames.forEach(flame => {
                    flame.style.display = 'none';
                });
                const blowButton = document.querySelector('.blow-button');
                blowButton.textContent = 'SUCCESS!';
                blowButton.disabled = true;
                setTimeout(() => this.showStage3(), 1500);
            }

            showStage3() {
                this.hideAllStages();
                this.quizIndex = 0;
                document.getElementById('stage3').classList.add('active');
                this.displayQuizQuestion();
            }

            displayQuizQuestion() {
                const quiz = this.quizData[this.quizIndex];
                document.getElementById('quizQuestion').textContent = quiz.question;
                const quizOptions = document.getElementById('quizOptions');
                quizOptions.innerHTML = '';
                const feedbackDiv = document.getElementById('quizFeedback');
                feedbackDiv.innerHTML = '';

                quiz.options.forEach((option, index) => {
                    const button = document.createElement('button');
                    button.className = 'quiz-option';
                    button.textContent = option;
                    button.addEventListener('click', () => this.handleQuizAnswer(index));
                    quizOptions.appendChild(button);
                });
            }

            handleQuizAnswer(selectedIndex) {
                const quiz = this.quizData[this.quizIndex];
                const feedbackDiv = document.getElementById('quizFeedback');
                const options = document.querySelectorAll('.quiz-option');

                if (selectedIndex === quiz.correct) {
                    options[selectedIndex].classList.add('correct');
                    feedbackDiv.className = 'quiz-feedback feedback-correct';
                    feedbackDiv.textContent = quiz.correctFeedback;
                    setTimeout(() => {
                        this.quizIndex++;
                        if (this.quizIndex < this.quizData.length) {
                            this.displayQuizQuestion();
                        } else {
                            setTimeout(() => this.showStage4(), 1000);
                        }
                    }, 1500);
                } else {
                    options[selectedIndex].classList.add('incorrect');
                    feedbackDiv.className = 'quiz-feedback feedback-incorrect';
                    feedbackDiv.textContent = quiz.incorrectFeedback;
                }
            }

            showStage4() {
                this.hideAllStages();
                document.getElementById('stage4').classList.add('active');
                const nextButton = document.createElement('button');
                nextButton.className = 'next-button';
                nextButton.textContent = 'NEXT';
                nextButton.addEventListener('click', () => this.showBouquet());
                document.getElementById('stage4').appendChild(nextButton);
            }

            showBouquet() {
                document.querySelector('.next-button').remove();
                document.getElementById('bouquetContainer').classList.remove('hidden');
                const acceptBouquetButton = document.querySelector('.accept-bouquet-button');
                acceptBouquetButton.addEventListener('click', () => this.showCat());
            }

            showCat() {
                document.getElementById('bouquetContainer').classList.add('hidden');
                document.getElementById('catContainer').classList.remove('hidden');
                const cat = document.querySelector('.cat-with-bow');
                cat.addEventListener('click', () => this.catClick());
            }

            catClick() {
                this.playSound('meow');
                const cat = document.querySelector('.cat-with-bow');
                cat.style.animation = 'none';
                setTimeout(() => {
                    cat.style.animation = 'bounce 0.6s ease-in-out';
                }, 10);
            }

            hideAllStages() {
                const stages = document.querySelectorAll('.stage-container');
                stages.forEach(stage => stage.classList.remove('active'));
            }

            playSound(soundName) {
                // Create audio context for sound effects
                const audioContext = new (window.AudioContext || window.webkitAudioContext)();
                
                if (soundName === 'pop') {
                    this.playPopSound(audioContext);
                } else if (soundName === 'meow') {
                    this.playMeowSound(audioContext);
                }
            }

            playPopSound(audioContext) {
                const now = audioContext.currentTime;
                const osc = audioContext.createOscillator();
                const gain = audioContext.createGain();
                
                osc.connect(gain);
                gain.connect(audioContext.destination);
                
                osc.frequency.setValueAtTime(800, now);
                osc.frequency.exponentialRampToValueAtTime(100, now + 0.1);
                
                gain.gain.setValueAtTime(0.3, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.1);
                
                osc.start(now);
                osc.stop(now + 0.1);
            }

            playMeowSound(audioContext) {
                const now = audioContext.currentTime;
                const osc = audioContext.createOscillator();
                const gain = audioContext.createGain();
                
                osc.connect(gain);
                gain.connect(audioContext.destination);
                
                osc.frequency.setValueAtTime(400, now);
                osc.frequency.exponentialRampToValueAtTime(200, now + 0.3);
                
                gain.gain.setValueAtTime(0.2, now);
                gain.gain.exponentialRampToValueAtTime(0, now + 0.3);
                
                osc.start(now);
                osc.stop(now + 0.3);
            }
        }

        // Initialize when page loads
        window.addEventListener('load', () => {
            new BirthdayExperience();
        });
    </script>
</body>
</html>
