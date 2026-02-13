<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Selamat Ulang Tahun Syifa Ushodry - 23 Tahun!</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: 'Arial', sans-serif;
            background: linear-gradient(to bottom, #87CEEB, #B0E0E6); /* Gradasi biru muda */
            color: #333;
            overflow-x: hidden;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .container {
            text-align: center;
            padding: 20px;
            max-width: 90%;
            width: 100%;
        }

        h1 {
            font-size: 2.5em;
            color: #4682B4;
            margin-bottom: 20px;
        }

        .bubble-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
        }

        .bubble {
            width: 50px;
            height: 50px;
            background: radial-gradient(circle, #ADD8E6, #87CEEB);
            border-radius: 50%;
            cursor: pointer;
            transition: transform 0.2s;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .bubble:hover {
            transform: scale(1.1);
        }

        .bubble.clicked {
            background: #4682B4;
            opacity: 0.5;
        }

        .quiz-container {
            display: none;
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            max-width: 500px;
            width: 100%;
        }

        .question {
            margin-bottom: 20px;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .option {
            background: #E0F6FF;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.2s;
        }

        .option:hover {
            background: #B0E0E6;
        }

        .poem-container {
            display: none;
            background: rgba(255, 255, 255, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            max-width: 600px;
            width: 100%;
            font-size: 1.2em;
            line-height: 1.6;
        }

        .poem-text {
            white-space: pre-line;
        }

        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background: #4682B4;
            animation: fall 3s linear infinite;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(360deg);
            }
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2em;
            }
            .bubble {
                width: 40px;
                height: 40px;
            }
            .poem-container {
                font-size: 1em;
            }
        }
    </style>
</head>
<body>
    <audio id="bg-music" autoplay loop>
        <source src="https://www.soundjay.com/misc/sounds/bell-ringing-05.wav" type="audio/wav"> <!-- Ganti dengan URL musik romantis/mellow yang sesuai, contoh: https://example.com/romantic-music.mp3 -->
        Browser Anda tidak mendukung elemen audio.
    </audio>

    <div class="container">
        <h1>Selamat Ulang Tahun Syifa Ushodry - 23 Tahun! 🎉</h1>
        
        <div id="bubble-section">
            <p>Klik 10 gelembung biru untuk masuk ke langkah berikutnya!</p>
            <div class="bubble-container">
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
                <div class="bubble" onclick="clickBubble(this)"></div>
            </div>
        </div>

        <div id="quiz-section" class="quiz-container">
            <h2>Kuis Interaktif: Kenangan Kita</h2>
            <div id="question-1" class="question">
                <p>Pertanyaan 1: Apa kenangan pertama kita bertemu?</p>
                <div class="options">
                    <div class="option" onclick="selectOption(1, 'A')">A. Di sekolah</div>
                    <div class="option" onclick="selectOption(1, 'B')">B. Di acara keluarga</div>
                    <div class="option" onclick="selectOption(1, 'C')">C. Melalui teman bersama</div>
                </div>
            </div>
            <div id="question-2" class="question" style="display: none;">
                <p>Pertanyaan 2: Apa makanan favorit kita makan bersama?</p>
                <div class="options">
                    <div class="option" onclick="selectOption(2, 'A')">A. Pizza</div>
                    <div class="option" onclick="selectOption(2, 'B')">B. Ice Cream</div>
                    <div class="option" onclick="selectOption(2, 'C')">C. Nasi Goreng</div>
                </div>
            </div>
            <div id="question-3" class="question" style="display: none;">
                <p>Pertanyaan 3: Apa aktivitas favorit kita lakukan bersama?</p>
                <div class="options">
                    <div class="option" onclick="selectOption(3, 'A')">A. Jalan-jalan</div>
                    <div class="option" onclick="selectOption(3, 'B')">B. Nonton film</div>
                    <div class="option" onclick="selectOption(3, 'C')">C. Ngobrol sampai malam</div>
                </div>
            </div>
        </div>

        <div id="poem-section" class="poem-container">
            <h2>Puisi untuk Syifa</h2>
            <div id="poem-text" class="poem-text"></div>
        </div>
    </div>

    <script>
        let bubbleClicks = 0;
        const totalBubbles = 10;
        let currentQuestion = 1;
        const totalQuestions = 3;

        function clickBubble(bubble) {
            if (!bubble.classList.contains('clicked')) {
                bubble.classList.add('clicked');
                bubbleClicks++;
                if (bubbleClicks === totalBubbles) {
                    document.getElementById('bubble-section').style.display = 'none';
                    document.getElementById('quiz-section').style.display = 'block';
                }
            }
        }

        function selectOption(questionNum, choice) {
            // Simulasi jawaban benar (sesuaikan dengan kenangan nyata jika perlu)
            const correctAnswers = {1: 'C', 2: 'B', 3: 'C'};
            if (choice === correctAnswers[questionNum]) {
                alert('Jawaban benar! 🎉');
            } else {
                alert('Coba lagi! 😊');
                return;
            }

            document.getElementById(`question-${questionNum}`).style.display = 'none';
            currentQuestion++;
            if (currentQuestion <= totalQuestions) {
                document.getElementById(`question-${currentQuestion}`).style.display = 'block';
            } else {
                document.getElementById('quiz-section').style.display = 'none';
                document.getElementById('poem-section').style.display = 'block';
                typePoem();
            }
        }

        const poem = `Barakallah fie umriiikk syifaaaa🥳🥳
Di usiamu yang kini menyentuh angka dua puluh tiga,
Aku duduk terdiam, mengingat betapa hebatnya perjalanan kita.
Tujuh tahun bukan waktu yang singkat untuk sekadar singgah,
Tapi bagimu, itu adalah waktu untuk tetap bertahan tanpa pernah menyerah.
Aku ingin berterima kasih, meski kata mungkin takkan pernah cukup.
Terima kasih sudah menjadi rumah saat duniaku terasa tertutup.
Terutama untuk caramu mengerti kondisiku yang seringkali terbatas,
Untuk setiap langkahmu menuju rumahku yang tak pernah kau hitung dengan ikhlas.
Aku tahu, mungkin ini terasa tidak adil bagimu,
Harus selalu kamu yang datang, harus selalu kamu yang menjemput temu.
Aku sering merasa terlalu banyak menuntut, sering merasa bersalah,
Tapi caramu tersenyum dan tetap hadir, membuat egoku luluh dan kalah.
Kau tak pernah protes mengapa aku tak bisa ke rumahmu,
Kau tak pernah mengeluh meski jarak dan izin orang tuaku menjadi belenggu.
Terima kasih, Sipa... karena sudah hadir dengan cara yang begitu sabar,
Menjadikan persahabatan ini tempat paling aman untukku bersandar.
Di usia 23 ini, doaku hanya satu untukmu:
Tetaplah menjadi Syifa yang tangguh, yang tawanya selalu menenangkan.
Aku bangga memilikimu, aku bahagia kita pernah bertemu.
Selamat Ulang Tahun, Sahabat Terbaikku. I Love You More Than Anything! 💙`;

        function typePoem() {
            const poemElement = document.getElementById('poem-text');
            let index = 0;
            const typingSpeed = 100; // ms per character

            function type() {
                if (index < poem.length) {
                    poemElement.textContent += poem.charAt(index);
                    index++;
                    setTimeout(type, typingSpeed);
                } else {
                    // Puisi selesai, tampilkan konfeti
                    showConfetti();
                }
            }
            type();
        }

        function showConfetti() {
            for (let i = 0; i < 100; i++) {
                const confetti = document.createElement('div');
                confetti.classList.add('confetti');
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.animationDelay = Math.random() * 3 + 's';
                document.body.appendChild(confetti);
                setTimeout(() => confetti.remove(), 3000);
            }
        }
    </script>
</body>
</html>
