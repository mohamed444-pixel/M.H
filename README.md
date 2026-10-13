<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Everything 🤍</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Cairo', sans-serif;
        }
        body {
            background-color: #fce4ec;
            color: #4a4a4a;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow-x: hidden;
        }
        .container {
            width: 100%;
            max-width: 420px;
            padding: 20px;
            text-align: center;
        }
        /* شاشة الباسورد */
        #lock-screen {
            background: #fff;
            padding: 30px 20px;
            border-radius: 30px;
            box-shadow: 0 10px 25px rgba(233, 30, 99, 0.1);
            position: relative;
        }
        .heart-icon {
            font-size: 50px;
            color: #e91e63;
            margin-bottom: 15px;
        }
        h2 {
            color: #d81b60;
            margin-bottom: 10px;
            font-size: 24px;
        }
        p {
            color: #888;
            margin-bottom: 20px;
            font-size: 14px;
        }
        input[type="password"] {
            width: 80%;
            padding: 12px;
            border: 2px solid #f8bbd0;
            border-radius: 20px;
            outline: none;
            text-align: center;
            font-size: 16px;
            margin-bottom: 15px;
            background: #fff0f5;
        }
        input[type="password"]:focus {
            border-color: #e91e63;
        }
        .btn {
            background: #e91e63;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 20px;
            font-size: 16px;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(233, 30, 99, 0.3);
            transition: 0.3s;
        }
        .btn:hover {
            background: #c2185b;
        }
        .error-msg {
            color: #e53935;
            margin-top: 10px;
            font-size: 13px;
            display: none;
        }

        /* صفحة المحتوى */
        #content-screen {
            display: none;
            text-align: center;
        }
        .message-box {
            background: white;
            padding: 20px;
            border-radius: 20px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            line-height: 1.8;
            font-size: 15px;
        }
        .counter-box {
            background: white;
            padding: 20px;
            border-radius: 20px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }
        .counter-grid {
            display: flex;
            justify-content: space-around;
            margin-top: 15px;
        }
        .time-block span {
            display: block;
            font-size: 20px;
            font-weight: bold;
            color: #e91e63;
        }
        .time-block label {
            font-size: 12px;
            color: #888;
        }
        .music-player {
            background: white;
            padding: 15px;
            border-radius: 50px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            margin-bottom: 20px;
        }
        .music-player audio {
            width: 100%;
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- شاشة الباسورد -->
        <div id="lock-screen">
            <div class="heart-icon">💖</div>
            <h2>جاهزة؟ 🥺</h2>
            <p>دُل اللي بينا هناا 💌</p>
            <input type="password" id="passInput" placeholder="Password">
            <br>
            <button class="btn" onclick="checkPassword()">Unlock 💕</button>
            <div id="errorMsg" class="error-msg">الباسورد غلط يا حب، جربي تاني!</div>
        </div>

        <!-- الشاشة الرئيسية بعد فتح القفل -->
        <div id="content-screen">
            <div class="music-player">
                <!-- حط رابط الأغنية بتاعتكم هنا -->
                <audio controls autoplay loop>
                    <source src="YOUR_SONG_LINK.mp3" type="audio/mp3">
                    المتصفح لا يدعم الصوت
                </audio>
            </div>

            <div class="message-box">
                <p>أنا عملت الهدية دي عشان عايز أقولك إني بحبك، بحب كلامنا سوا، هزارنا وكل حاجة بينا... بحب كلامك لما بتحبي كل حاجة فيكي مهما ما أصفك أنا بحبك قد إيه مش هخلص بس الي أعرفه إنك غالية عندي وأوي 🤍</p>
            </div>

            <div class="counter-box">
                <h3>سوا من 02-06-2026 💕</h3>
                <div class="counter-grid" id="counter">
                    <div class="time-block"><span id="days">0</span><label>يوم</label></div>
                    <div class="time-block"><span id="hours">0</span><label>ساعة</label></div>
                    <div class="time-block"><span id="minutes">0</span><label>دقيقة</label></div>
                    <div class="time-block"><span id="seconds">0</span><label>ثانية</label></div>
                </div>
            </div>

            <div class="message-box">
                <p style="color: #e91e63; font-weight: bold;">بحبك وربنا يخليكي ليا، إنتي أغلى حاجة عندي ❤️</p>
            </div>
        </div>
    </div>

    <script>
        // الباسورد اللي هي تحطه (ممكن تغيره زي ما تحب)
        const correctPassword = "love";

        function checkPassword() {
            const input = document.getElementById("passInput").value;
            const errorMsg = document.getElementById("errorMsg");
            
            if (input === correctPassword) {
                document.getElementById("lock-screen").style.display = "none";
                document.getElementById("content-screen").style.display = "block";
                startCounter();
            } else {
                errorMsg.style.display = "block";
            }
        }

        // حساب العداد تلقائياً من تاريخ 2 يونيو 2026
        function startCounter() {
            const startDate = new Date("2026-06-02T00:00:00");

            setInterval(() => {
                const now = new Date();
                const diff = now - startDate;

                const days = Math.floor(diff / (1000 * 60 * 60 * 24));
                const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
                const minutes = Math.floor((diff / 1000 / 60) % 60);
                const seconds = Math.floor((diff / 1000) % 60);

                document.getElementById("days").innerText = days;
                document.getElementById("hours").innerText = hours;
                document.getElementById("minutes").innerText = minutes;
                document.getElementById("seconds").innerText = seconds;
            }, 1000);
        }
    </script>
</body>
</html>
