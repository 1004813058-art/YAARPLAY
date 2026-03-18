<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>פלייליסט כיתת יער</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Assistant:wght@300;400;700&family=Suez+One&display=swap');

        :root {
            --bg-color: #f4f1ea; /* נייר ממוחזר עדין */
            --primary-color: #6d4c41; /* חום עץ */
            --accent-color: #78909c; /* כחול-אפור מכני */
            --text-color: #4e342e;
            --leaf-color: #a5d6a7;
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Assistant', sans-serif;
            background-color: var(--bg-color);
            background-image: url('data:image/svg+xml,%3Csvg width="20" height="20" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"%3E%3Cg fill="%23dcd6c8" fill-opacity="0.4" fill-rule="evenodd"%3E%3Ccircle cx="3" cy="3" r="1"/%3E%3Ccircle cx="13" cy="13" r="1"/%3E%3C/g%3E%3C/svg%3E'); /* טקסטורה עדינה */
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            color: var(--text-color);
            overflow-x: hidden;
            position: relative;
        }

        /* עלים אבסטרקטיים ברקע */
        .leaf-bg {
            position: absolute;
            width: 150px;
            height: 150px;
            background-color: var(--leaf-color);
            border-radius: 0 100% 0 100%;
            opacity: 0.1;
            z-index: -1;
        }

        .container {
            max-width: 650px;
            width: 90%;
            margin-top: 40px;
            margin-bottom: 40px;
            background: #ffffff;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(109, 76, 65, 0.1);
            border: 2px solid #e0e0e0;
            position: relative;
        }

        /* כותרת מיוחדת לכיתת יער */
        .header-area {
            text-align: center;
            margin-bottom: 30px;
            border-bottom: 2px solid var(--leaf-color);
            padding-bottom: 15px;
        }

        h1 {
            font-family: 'Suez One', serif;
            color: var(--primary-color);
            margin: 0;
            font-size: 2.8rem;
            letter-spacing: -1px;
        }

        .subtitle {
            font-size: 1.2rem;
            color: #8d6e63;
            font-weight: 300;
            margin-top: 5px;
        }

        /* --- נגן הסלילים (Reel-to-Reel) הוינטג' --- */
        .tape-player {
            width: 100%;
            height: 120px;
            background-color: #424242; /* צבע מכשיר ישן */
            border-radius: 10px;
            margin-bottom: 30px;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            box-shadow: inset 0 0 15px rgba(0,0,0,0.5);
            border: 4px solid #5d4037;
            overflow: hidden;
        }

        .reel {
            width: 80px;
            height: 80px;
            background: repeating-conic-gradient(#555 0% 15deg, #333 15deg 30deg);
            border-radius: 50%;
            border: 3px solid #9e9e9e;
            position: relative;
            margin: 0 40px;
            transition: transform 0.1s linear;
        }

        .reel-center {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 15px;
            height: 15px;
            background-color: #bdbdbd;
            border-radius: 50%;
        }

        /* סרט מגנטי ביניהם */
        .tape-line {
            position: absolute;
            width: 160px;
            height: 5px;
            background-color: #212121;
            top: 57px;
            left: calc(50% - 80px);
            z-index: 1;
        }

        /* כאשר הנגן "מנגן" */
        .tape-player.playing .reel {
            animation: rotateReel 4s linear infinite;
        }

        @keyframes rotateReel {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* --- אזור הקלט --- */
        .input-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .input-group input {
            width: 100%;
            padding: 15px;
            border: 1px solid #d7ccc8;
            border-radius: 12px;
            font-size: 1.1rem;
            color: var(--text-color);
            background-color: #fafafa;
            transition: all 0.3s ease;
            box-sizing: border-box; /* חשוב לריווח */
        }

        .input-group input:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 10px rgba(109, 76, 65, 0.1);
        }

        button {
            width: 100%;
            padding: 18px;
            background-color: var(--primary-color);
            color: #fff;
            border: none;
            border-radius: 50px; /* כפתור עגול יותר */
            cursor: pointer;
            font-size: 1.3rem;
            font-weight: 700;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(109, 76, 65, 0.2);
            font-family: 'Assistant', sans-serif;
        }

        button:hover {
            background-color: #5d4037;
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(109, 76, 65, 0.3);
        }

        /* --- אזור הפלייליסט --- */
        .playlist-display {
            margin-top: 40px;
            width: 100%;
            border-top: 1px dashed #d7ccc8;
            padding-top: 20px;
        }

        .song-item {
            background: #fff;
            margin: 15px 0;
            padding: 20px;
            border-radius: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            animation: songIn 0.6s ease-out;
            border: 1px solid #eee;
            box-shadow: 0 2px 5px rgba(0,0,0,0.02);
        }

        @keyframes songIn {
            0% { opacity: 0; transform: scale(0.9) translateY(20px); }
            100% { opacity: 1; transform: scale(1) translateY(0); }
        }

        .song-info {
            display: flex;
            flex-direction: column;
        }

        .song-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--primary-color);
        }

        .student-name {
            font-size: 1rem;
            color: #8d6e63;
            margin-top: 3px;
        }

        .music-symbol {
            font-size: 1.8rem;
            color: var(--leaf-color);
        }

    </style>
</head>
<body>

    <div class="leaf-bg" style="top: 10px; left: 10px; transform: rotate(15deg);"></div>
    <div class="leaf-bg" style="bottom: 10px; right: 10px; transform: rotate(-30deg);"></div>

    <div class="container">
        <div class="header-area">
            <h1>ניגון יער</h1>
            <div class="subtitle">הפלייליסט המשותף של כיתת יער</div>
        </div>

        <div class="tape-player" id="tapePlayer">
            <div class="reel" id="reel1">
                <div class="reel-center"></div>
            </div>
            <div class="tape-line"></div>
            <div class="reel" id="reel2">
                <div class="reel-center"></div>
            </div>
        </div>
        
        <div class="input-form">
            <div class="input-group">
                <input type="text" id="studentName" placeholder="השם שלי (למשל: נעם)...">
            </div>
            <div class="input-group">
                <input type="text" id="songTitle" placeholder="שם השיר והאמן שאני אוהב/ת...">
            </div>
            
            <button onclick="addSong()">הוספה לפלייליסט</button>
        </div>

        <div class="playlist-display" id="playlist">
            </div>
    </div>

    <audio id="clickSound" src="https://www.soundjay.com/buttons/button-16.mp3" preload="auto"></audio>

    <script>
        function addSong() {
            const name = document.getElementById('studentName').value;
            const song = document.getElementById('songTitle').value;
            const playlist = document.getElementById('playlist');
            const player = document.getElementById('tapePlayer');
            const clickSound = document.getElementById('clickSound');

            if (name === '' || song === '') {
                alert('אנא כתבו את השם שלכם ואת שם השיר');
                return;
            }

            // נגן צליל קליק
            clickSound.play();

            // הפעל אנימציה בנגן
            player.classList.add('playing');
            
            // צור את אלמנט השיר
            const item = document.createElement('div');
            item.className = 'song-item';
            item.innerHTML = `
                <div class="song-info">
                    <span class="song-title">${song}</span>
                    <span class="student-name">הבחירה של ${name}</span>
                </div>
                <span class="music-symbol">🎶</span>
            `;

            // הוסף לרשימה (בראש הרשימה)
            playlist.prepend(item);

            // ניקוי שדות
            document.getElementById('studentName').value = '';
            document.getElementById('songTitle').value = '';

            // הפסק אנימציה אחרי 5 שניות
            setTimeout(() => {
                player.classList.remove('playing');
            }, 5000);
        }
    </script>
</body>
</html>
