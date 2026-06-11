<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>สนุกกับมาตราตัวสะกด ป.3</title>
    <!-- ใช้ฟอนต์น่ารักๆ สำหรับเด็ก -->
    <link href="https://fonts.googleapis.com/css2?family=Mali:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        /* กำหนดธีมสีสันสดใสสำหรับเด็ก */
        :root {
            --primary-color: #FF7B89;
            --secondary-color: #8CC2D3;
            --accent-yellow: #FFD25A;
            --accent-green: #97C1A9;
            --bg-color: #FDF6F0;
            --text-dark: #4A4A4A;
            
            /* สีประจำ 9 มาตรา */
            --c-koka: #FF9AA2;
            --c-kok: #FFB7B2;
            --c-kod: #FFDAC1;
            --c-kob: #E2F0CB;
            --c-kon: #B5EAD7;
            --c-kong: #C7CEEA;
            --c-kom: #FAD02E;
            --c-koei: #F28D35;
            --c-keaw: #D988B9;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Mali', cursive, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-dark);
            line-height: 1.6;
            scroll-behavior: smooth;
        }

        /* เมนูนำทาง (Navbar) */
        nav {
            background-color: var(--secondary-color);
            padding: 15px;
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        nav a {
            color: white;
            text-decoration: none;
            font-weight: 700;
            font-size: 1.1rem;
            padding: 8px 16px;
            border-radius: 20px;
            background-color: rgba(255,255,255,0.2);
            transition: 0.3s;
        }

        nav a:hover {
            background-color: var(--accent-yellow);
            color: var(--text-dark);
            transform: translateY(-2px);
        }

        /* เพิ่ม CSS สำหรับเมนู Dropdown 9 มาตรา */
        .dropdown {
            position: relative;
            display: inline-block;
        }

        .dropdown-content {
            display: none;
            position: absolute;
            background-color: white;
            min-width: 180px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            z-index: 1000;
            border-radius: 15px;
            top: 110%;
            left: 50%;
            transform: translateX(-50%);
            padding: 10px 0;
            flex-direction: column;
            gap: 5px;
        }

        .dropdown:hover .dropdown-content {
            display: flex;
        }

        .dropdown-content a {
            background-color: transparent;
            color: var(--text-dark);
            padding: 10px 20px;
            border-radius: 10px;
            margin: 0 10px;
            text-align: left;
            transition: 0.2s;
            font-size: 1rem;
        }

        .dropdown-content a:hover {
            background-color: var(--accent-yellow);
            color: var(--text-dark);
            transform: scale(1.02);
        }

        /* ส่วนหัวเว็บไซต์ (Hero Section) */
        header {
            text-align: center;
            padding: 50px 20px;
            background: linear-gradient(135deg, var(--primary-color), #FF9EAB);
            color: white;
        }

        header h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .cartoon {
            font-size: 3rem;
            display: inline-block;
            animation: bounce 2s infinite;
            margin: 0 10px;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        /* ส่วนเนื้อหา */
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 30px 20px;
        }

        .section-box {
            background: white;
            border-radius: 25px;
            padding: 30px;
            margin-bottom: 40px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.05);
            border: 4px dashed var(--secondary-color);
            text-align: center;
        }

        .section-box h2 {
            font-size: 2rem;
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        /* แถบเมนูย่อยสำหรับเลือกมาตรา */
        .matra-tabs-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
            background: white;
            padding: 15px;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            border: 4px dashed var(--secondary-color);
        }

        .matra-tab-btn {
            padding: 10px 20px;
            border-radius: 15px;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            border: 2px solid #eee;
            background: #f9f9f9;
            color: var(--text-dark);
            transition: all 0.3s ease;
            font-family: 'Mali', cursive;
        }

        .matra-tab-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.15);
        }

        .matra-section {
            display: none;
            animation: fadeIn 0.4s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* การ์ดคำศัพท์ */
        .word-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .word-card {
            background-color: #f9f9f9;
            border-radius: 15px;
            padding: 20px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 10px;
            font-size: 1.8rem;
            font-weight: 700;
            border: 2px solid #eee;
            transition: 0.2s;
        }

        .word-card:hover {
            transform: scale(1.05);
            border-color: var(--accent-yellow);
            box-shadow: 0 5px 15px rgba(255, 210, 90, 0.3);
        }

        .word-image {
            font-size: 4rem;
            background: white;
            width: 100px;
            height: 100px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.08);
            margin-bottom: 5px;
        }

        /* ปุ่มกดเสียง */
        .play-sound-btn {
            background-color: var(--accent-yellow);
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            font-size: 1.5rem;
            cursor: pointer;
            box-shadow: 0 4px 0 #E5B83B;
            transition: 0.1s;
        }

        .play-sound-btn:active {
            transform: translateY(4px);
            box-shadow: 0 0 0 #E5B83B;
        }

        /* ส่วนของเกม (นักล่าคำศัพท์ รูปภาพ) */
        #game-section {
            background-color: var(--accent-green);
            border-color: #7BB092;
            color: white;
        }

        .game-card {
            background: white;
            color: var(--text-dark);
            border-radius: 20px;
            padding: 30px;
            margin-top: 20px;
        }

        .choice-btn {
            display: block;
            width: 100%;
            background-color: var(--bg-color);
            border: 2px solid var(--secondary-color);
            padding: 15px;
            font-size: 1.5rem;
            font-weight: bold;
            border-radius: 15px;
            margin-bottom: 10px;
            cursor: pointer;
            transition: 0.2s;
            font-family: 'Mali', cursive;
        }

        .choice-btn:hover:not(:disabled) {
            background-color: var(--secondary-color);
            color: white;
        }

        .game-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; font-size: 1.5rem; font-weight: bold; }
        .lives-box { color: #ff4757; letter-spacing: 3px; font-size: 1.8rem; }
        .score-box { color: #2ed573; background: #f1f2f6; padding: 5px 15px; border-radius: 20px; display: flex; align-items: center; gap: 10px;}
        .combo-text { color: #ff9f43; font-size: 1.2rem; font-weight: bold; animation: popIn 0.3s ease-out; display: none; }
        
        .game-target-box { background: linear-gradient(135deg, #1A535C, #4ECDC4); color: white; border-radius: 20px; padding: 30px 20px; font-size: 2rem; box-shadow: 0 10px 20px rgba(0,0,0,0.1); text-align: center; margin-bottom: 25px; border: 4px solid var(--accent-yellow); position: relative; }
        .game-target-title { font-size: 1.2rem; color: var(--accent-yellow); margin-bottom: 5px; font-weight: bold;}
        .game-target-matra { font-size: 3rem; font-weight: bold; text-shadow: 2px 2px 0 #1A535C; animation: popIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
        
        .image-choices-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
        @media (max-width: 600px) { .image-choices-grid { grid-template-columns: 1fr 1fr; gap: 10px; } .game-target-matra {font-size: 2.2rem;} }
        
        .image-choice-btn { background: white; border: 4px solid #e0e0e0; border-radius: 25px; padding: 25px 10px; cursor: pointer; transition: 0.2s; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 15px; box-shadow: 0 6px 0 #d1d1d1; width: 100%; font-family: 'Mali', cursive;}
        .image-choice-btn:hover:not(:disabled) { transform: translateY(-5px); border-color: var(--secondary-color); box-shadow: 0 10px 0 var(--secondary-color); }
        .image-choice-btn:active:not(:disabled) { transform: translateY(5px); box-shadow: 0 0 0 transparent; }
        .image-choice-btn:disabled { opacity: 0.9; cursor: not-allowed; transform: none; box-shadow: 0 6px 0 #d1d1d1; }
        
        .image-choice-emoji { font-size: 5rem; margin-bottom: 5px; filter: drop-shadow(0 4px 6px rgba(0,0,0,0.1)); }
        .image-choice-word { font-size: 1.8rem; font-weight: bold; color: var(--text-dark); background: #f4f4f4; padding: 5px 20px; border-radius: 15px; width: 90%; text-align: center; }
        
        .btn-correct { background-color: #d4edda !important; border-color: #28a745 !important; box-shadow: 0 6px 0 #1e7e34 !important; }
        .btn-correct .image-choice-word { background: #28a745; color: white; }
        
        .btn-wrong { background-color: #f8d7da !important; border-color: #dc3545 !important; box-shadow: 0 6px 0 #bd2130 !important; }
        .btn-wrong .image-choice-word { background: #dc3545; color: white; text-decoration: line-through;}
        
        @keyframes popIn { 0% { transform: scale(0); } 100% { transform: scale(1); } }
        @keyframes shake { 0%, 100% { transform: translateX(0); } 25% { transform: translateX(-10px); } 75% { transform: translateX(10px); } }
        .shake-anim { animation: shake 0.4s ease-in-out; }

        /* CSS บทเรียน */
        .theory-content { display: flex; flex-direction: column; gap: 20px; text-align: left; }
        .theory-card { background: white; border-radius: 20px; padding: 25px; box-shadow: 0 8px 15px rgba(0,0,0,0.05); border: 3px dashed var(--secondary-color); }
        .matra-list-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 15px; margin-top: 15px; }
        .matra-item { background: #fdfdfd; padding: 15px 20px; border-radius: 15px; border-left: 6px solid var(--primary-color); box-shadow: 0 4px 6px rgba(0,0,0,0.02); display: flex; align-items: center; font-size: 1.2rem; transition: 0.2s; }
        .matra-item:hover { transform: translateX(5px); box-shadow: 0 4px 8px rgba(0,0,0,0.05); }
        .type-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 15px; }
        .type-box { border-radius: 15px; padding: 20px; }
        .type-box ul { font-size: 1.2rem; line-height: 1.6; }
        .type-box li { margin-bottom: 5px; }
        @media (max-width: 600px) { .type-grid { grid-template-columns: 1fr; } }

        /* Footer */
        footer {
            text-align: center;
            padding: 20px;
            background-color: var(--text-dark);
            color: white;
            margin-top: 20px;
        }

        /* Responsive Design (อัปเดตให้รองรับมือถือได้สมบูรณ์แบบ) */
        @media (max-width: 600px) {
            header h1 { font-size: 2rem; }
            header { padding: 30px 10px; }
            .word-card { font-size: 1.4rem; padding: 15px; }
            .word-image { width: 80px; height: 80px; font-size: 3rem; }
            .play-sound-btn { width: 45px; height: 45px; font-size: 1.2rem; }
            .choice-btn { font-size: 1.2rem; padding: 12px; }
            .matra-tab-btn { padding: 8px 12px; font-size: 1rem; }
            .word-grid { grid-template-columns: repeat(auto-fit, minmax(130px, 1fr)); gap: 10px; }
            .image-choice-btn { padding: 15px 5px; }
            .image-choice-emoji { font-size: 3.5rem; }
            .image-choice-word { font-size: 1.3rem; padding: 5px 10px; }
            .matra-list-grid { grid-template-columns: 1fr; }
            nav { padding: 10px; gap: 5px; }
            nav a { font-size: 1rem; padding: 6px 12px; }
            .dropdown-content { min-width: 150px; }
        }
    </style>
</head>
<body>

    <!-- เมนู -->
    <nav>
        <a href="#home">🏠 หน้าแรก</a>
        <a href="#theory">📚 บทเรียน</a>
        
        <!-- เปลี่ยนปุ่ม 9 มาตรา เป็นแบบ Dropdown -->
        <div class="dropdown">
            <a href="javascript:void(0)" class="dropbtn">🔤 ๙ มาตรา ▾</a>
            <div class="dropdown-content">
                <a href="#matra-tabs" onclick="openMatraTab('koka', 'var(--c-koka)')">🐔 แม่ ก กา</a>
                <a href="#matra-tabs" onclick="openMatraTab('kok', 'var(--c-kok)')">🐦 แม่ กก</a>
                <a href="#matra-tabs" onclick="openMatraTab('kod', 'var(--c-kod)')">🐜 แม่ กด</a>
                <a href="#matra-tabs" onclick="openMatraTab('kob', 'var(--c-kob)')">🐸 แม่ กบ</a>
                <a href="#matra-tabs" onclick="openMatraTab('kon', 'var(--c-kon)')">🥄 แม่ กน</a>
                <a href="#matra-tabs" onclick="openMatraTab('kong', 'var(--c-kong)')">🐘 แม่ กง</a>
                <a href="#matra-tabs" onclick="openMatraTab('kom', 'var(--c-kom)')">🍊 แม่ กม</a>
                <a href="#matra-tabs" onclick="openMatraTab('koei', 'var(--c-koei)')">🍌 แม่ เกย</a>
                <a href="#matra-tabs" onclick="openMatraTab('keaw', 'var(--c-keaw)')">🐱 แม่ เกอว</a>
            </div>
        </div>

        <a href="#game-section">🎮 เล่นเกม</a>
    </nav>

    <!-- หน้าแรก -->
    <header id="home">
        <div class="cartoon">🦁</div>
        <div class="cartoon">🐰</div>
        <div class="cartoon">🐼</div>
        <h1>มาตราตัวสะกดไทย ป.3</h1>
        <p style="font-size: 1.2rem;">เรียนรู้คำศัพท์สนุกๆ พร้อมเกมตอบคำถาม 🌟</p>
    </header>

    <main class="container">
        
        <!-- เนื้อหาทฤษฎีเพิ่มเติม -->
        <section id="theory" class="section-box" style="border-color: var(--secondary-color); background-color: #f4fbff;">
            <h2 style="color: var(--secondary-color); text-align: center; margin-bottom: 25px;">📚 บทเรียน: มาตราตัวสะกด</h2>
            <div class="theory-content">
                
                <div class="theory-card" style="border-color: #FF7B89;">
                    <h3 style="color: #FF7B89; margin-bottom: 10px; font-size: 1.5rem;">✨ ความหมาย</h3>
                    <p style="font-size: 1.2rem; color: var(--text-dark); line-height: 1.8;">
                        <strong>มาตราตัวสะกด</strong> คือ พยัญชนะที่ผสมอยู่ข้างหลังคำหรือพยางค์ในแม่ ก กา ทำให้แม่ ก กา มีตัวสะกด มีทั้งหมด <strong>๘ แม่</strong> (ถ้ารวมแม่ ก กา ที่ไม่มีตัวสะกดด้วย จะเป็น <strong>๙ มาตรา</strong> จ้า)
                    </p>
                </div>

                <div class="theory-card" style="border-color: var(--accent-yellow);">
                    <h3 style="color: #e5a900; margin-bottom: 5px; font-size: 1.5rem;">📌 พยัญชนะตัวสะกดทั้ง ๙ มาตรา</h3>
                    <div class="matra-list-grid">
                        <div class="matra-item" style="border-color: var(--c-koka);"><span>🐔 <strong>แม่ ก กา</strong> - คำที่ไม่มีตัวสะกด</span></div>
                        <div class="matra-item" style="border-color: var(--c-kok);"><span>🐦 <strong>แม่ กก</strong> - สะกดด้วย ก ข ค ฆ</span></div>
                        <div class="matra-item" style="border-color: var(--c-kod);"><span>🐜 <strong>แม่ กด</strong> - สะกดด้วย จ ด ต ถ ท ธ ฎ ฏ ฑ ฒ ช ซ ศ ษ ส</span></div>
                        <div class="matra-item" style="border-color: var(--c-kob);"><span>🐸 <strong>แม่ กบ</strong> - สะกดด้วย บ ป พ ภ ฟ</span></div>
                        <div class="matra-item" style="border-color: var(--c-kon);"><span>🥄 <strong>แม่ กน</strong> - สะกดด้วย น ณ ญ ร ล ฬ</span></div>
                        <div class="matra-item" style="border-color: var(--c-kong);"><span>🐘 <strong>แม่ กง</strong> - สะกดด้วย ง</span></div>
                        <div class="matra-item" style="border-color: var(--c-kom);"><span>🍊 <strong>แม่ กม</strong> - สะกดด้วย ม</span></div>
                        <div class="matra-item" style="border-color: var(--c-koei);"><span>🍌 <strong>แม่ เกย</strong> - สะกดด้วย ย</span></div>
                        <div class="matra-item" style="border-color: var(--c-keaw);"><span>🐱 <strong>แม่ เกอว</strong> - สะกดด้วย ว</span></div>
                    </div>
                </div>

                <div class="theory-card" style="border-color: #97C1A9;">
                    <h3 style="color: #5d9878; margin-bottom: 5px; font-size: 1.5rem;">✌️ ประเภทของมาตราตัวสะกด</h3>
                    <div class="type-grid">
                        <div class="type-box" style="background: #eef2ff; border: 3px solid #b5c0ff;">
                            <h4 style="color: #4a6ee0; margin-bottom: 10px; font-size: 1.3rem;">⭐ ๑. ตรงตามมาตรา</h4>
                            <p style="font-size: 1rem; color: #666; margin-bottom: 10px;">(มีตัวสะกดเพียงตัวเดียว)</p>
                            <ul style="margin-left: 25px; color: var(--text-dark);">
                                <li>🐘 <strong>แม่กง</strong> (ง)</li>
                                <li>🍊 <strong>แม่กม</strong> (ม)</li>
                                <li>🍌 <strong>แม่เกย</strong> (ย)</li>
                                <li>🐱 <strong>แม่เกอว</strong> (ว)</li>
                            </ul>
                        </div>
                        <div class="type-box" style="background: #fff0f5; border: 3px solid #ffb5c6;">
                            <h4 style="color: #e04a73; margin-bottom: 10px; font-size: 1.3rem;">🌟 ๒. ไม่ตรงตามมาตรา</h4>
                            <p style="font-size: 1rem; color: #666; margin-bottom: 10px;">(มีตัวสะกดหลายตัว แต่ออกเสียงเหมือนกัน)</p>
                            <ul style="margin-left: 25px; color: var(--text-dark);">
                                <li>🐦 <strong>แม่กก</strong></li>
                                <li>🐜 <strong>แม่กด</strong></li>
                                <li>🐸 <strong>แม่กบ</strong></li>
                                <li>🥄 <strong>แม่กน</strong></li>
                            </ul>
                        </div>
                    </div>
                </div>

                <div style="text-align: center; font-size: 1.5rem; color: var(--accent-yellow); font-weight: bold; background: var(--text-dark); padding: 15px; border-radius: 15px; box-shadow: 0 4px 0 #222;">
                    💡 ช่วยจำ: "มาตราตัวสะกด ๙ มาตรา"
                </div>
            </div>
        </section>

        <!-- แถบเมนูย่อยเลือกมาตรา -->
        <div id="matra-tabs" class="matra-tabs-container"></div>
        <!-- คอนเทนเนอร์สำหรับใส่เนื้อหาแต่ละมาตรา -->
        <div id="matra-container"></div>

        <!-- ส่วนของเกม -->
        <section id="game-section" class="section-box" style="background-color: var(--accent-green); border-color: #7BB092; color: white;">
            <h2 style="color: white; text-shadow: 1px 1px 2px rgba(0,0,0,0.2);">🎮 เกม: นักล่าคำศัพท์มาตราตัวสะกด</h2>
            <p style="font-size: 1.2rem;">ค้นหารูปภาพและคำศัพท์ให้ตรงกับมาตราที่กำหนด (มีหัวใจ 3 ดวงนะ!) 💖</p>
            
            <!-- หน้าเริ่มเกม -->
            <div id="game-start-screen" class="game-card" style="margin-top: 20px; text-align: center;">
                <div style="font-size: 5rem; margin-bottom: 20px;">🕵️‍♂️🔍</div>
                <button class="choice-btn" onclick="startGame()" style="width: 100%; background-color: var(--accent-yellow); box-shadow: 0 5px 0 #E5B83B;">▶️ เริ่มเกมนักล่าคำศัพท์!</button>
            </div>

            <!-- หน้าเล่นเกม -->
            <div id="game-play-screen" style="display: none; margin-top: 20px;">
                <div class="game-header">
                    <div class="score-box">
                        ⭐ <span id="game-score">0</span>
                        <div id="combo-display" class="combo-text">Combo x2! 🔥</div>
                    </div>
                    <div class="lives-box" id="game-lives">❤️❤️❤️</div>
                </div>
                
                <div class="game-target-box" id="question-box">
                    <div class="game-target-title">ค้นหาคำศัพท์ที่อยู่ใน...</div>
                    <div id="game-target-matra" class="game-target-matra">แม่ กก</div>
                </div>
                
                <div class="image-choices-grid" id="choices-container">
                    <!-- ปุ่มตัวเลือกรูปภาพจะถูกสร้างด้วย JS -->
                </div>
            </div>

            <!-- หน้าจบเกม -->
            <div id="game-over-screen" class="game-card" style="display: none; margin-top: 20px; text-align: center;">
                <div id="game-over-emoji" style="font-size: 5rem;">🏆</div>
                <h3 id="game-over-title" style="font-size: 2rem; color: var(--primary-color);">จบเกม!</h3>
                <p id="game-over-score" style="font-size: 1.5rem; margin: 15px 0; color: #444;"></p>
                <button class="choice-btn" onclick="startGame()" style="width: 100%; background-color: var(--secondary-color); color: white; box-shadow: 0 5px 0 #63A8BD;">🔄 เล่นอีกครั้ง</button>
            </div>
        </section>

    </main>

    <footer>
        <p>จัดทำเพื่อการศึกษา - มาตราตัวสะกดไทย ป.3</p>
    </footer>

    <!-- JavaScript -->
    <script>
        // ข้อมูลคำศัพท์ 9 มาตรา (มาตราละ 20 คำ)
        const matraData = [
            {
                id: "koka", title: "🐔 ๑. แม่ ก กา", desc: "คำที่ <strong>ไม่มี</strong> ตัวสะกด", color: "var(--c-koka)",
                words: [
                    {w:"ปลา", i:"🐟"}, {w:"หมู", i:"🐷"}, {w:"เก้าอี้", i:"🪑"}, {w:"ไก่", i:"🐔"}, {w:"เต่า", i:"🐢"},
                    {w:"ม้า", i:"🐴"}, {w:"หมี", i:"🐻"}, {w:"หมา", i:"🐶"}, {w:"ทะเล", i:"🌊"}, {w:"ภูเขา", i:"⛰️"},
                    {w:"ปู", i:"🦀"}, {w:"งู", i:"🐍"}, {w:"ตู้", i:"🗄️"}, {w:"ตา", i:"👁️"}, {w:"หู", i:"👂"},
                    {w:"ใบไม้", i:"🍃"}, {w:"เสื้อ", i:"👕"}, {w:"กระเป๋า", i:"🎒"}, {w:"เรือ", i:"⛵"}, {w:"นาฬิกา", i:"⌚"}
                ]
            },
            {
                id: "kok", title: "🐦 ๒. แม่ กก", desc: "คำที่มี <strong>ก, ข, ค, ฆ</strong> เป็นตัวสะกด", color: "var(--c-kok)",
                words: [
                    {w:"นก", i:"🐦"}, {w:"สุนัข", i:"🐕"}, {w:"เมฆ", i:"☁️"}, {w:"หมวก", i:"🧢"}, {w:"ตุ๊กตา", i:"🧸"},
                    {w:"ผัก", i:"🥬"}, {w:"พริก", i:"🌶️"}, {w:"กระจก", i:"🪞"}, {w:"เชือก", i:"🪢"}, {w:"เค้ก", i:"🍰"},
                    {w:"ปาก", i:"👄"}, {w:"ดอกไม้", i:"🌸"}, {w:"เลข", i:"🔢"}, {w:"โรค", i:"🦠"}, {w:"หมึก", i:"🦑"},
                    {w:"โลก", i:"🌍"}, {w:"คางคก", i:"🐸"}, {w:"จมูก", i:"👃"}, {w:"ปีก", i:"🪽"}, {w:"เด็ก", i:"👦"}
                ]
            },
            {
                id: "kod", title: "🐜 ๓. แม่ กด", desc: "คำที่มี <strong>ด, จ, ช, ซ, ฎ, ฏ, ฐ, ฑ, ฒ, ต, ถ, ท, ธ, ศ, ษ, ส</strong> สะกด", color: "var(--c-kod)",
                words: [
                    {w:"มด", i:"🐜"}, {w:"ตำรวจ", i:"👮"}, {w:"รถ", i:"🚗"}, {w:"สมุด", i:"📓"}, {w:"ไม้บรรทัด", i:"📏"},
                    {w:"กระดาษ", i:"📄"}, {w:"โทรทัศน์", i:"📺"}, {w:"แครอท", i:"🥕"}, {w:"อูฐ", i:"🐪"}, {w:"สับปะรด", i:"🍍"},
                    {w:"เพชร", i:"💎"}, {w:"ขวด", i:"🍾"}, {w:"มงกุฎ", i:"👑"}, {w:"เห็ด", i:"🍄"}, {w:"เป็ด", i:"🦆"},
                    {w:"วัด", i:"⛩️"}, {w:"ไม้กวาด", i:"🧹"}, {w:"เสื้อเชิ้ต", i:"👔"}, {w:"แรด", i:"🦏"}, {w:"อิฐ", i:"🧱"}
                ]
            },
            {
                id: "kob", title: "🐸 ๔. แม่ กบ", desc: "คำที่มี <strong>บ, ป, พ, ฟ, ภ</strong> เป็นตัวสะกด", color: "var(--c-kob)",
                words: [
                    {w:"กบ", i:"🐸"}, {w:"รูปภาพ", i:"🖼️"}, {w:"ยีราฟ", i:"🦒"}, {w:"โทรศัพท์", i:"📱"}, {w:"ตะเกียบ", i:"🥢"},
                    {w:"ทัพพี", i:"🥄"}, {w:"ธูป", i:"🕯️"}, {w:"ยางลบ", i:"🧽"}, {w:"ดาบ", i:"🗡️"}, {w:"เล็บ", i:"💅"},
                    {w:"ซุป", i:"🍲"}, {w:"แมลงสาบ", i:"🪳"}, {w:"หีบ", i:"🧰"}, {w:"จอบ", i:"⛏️"}, {w:"ข้าวเกรียบ", i:"🍘"},
                    {w:"กรอบรูป", i:"🖼️"}, {w:"ทะเลสาบ", i:"🏞️"}, {w:"ตลับ", i:"💄"}, {w:"ไม้หนีบ", i:"📎"}, {w:"แฟ้มพับ", i:"📁"}
                ]
            },
            {
                id: "kon", title: "🥄 ๕. แม่ กน", desc: "คำที่มี <strong>น, ณ, ญ, ร, ล, ฬ</strong> เป็นตัวสะกด", color: "var(--c-kon)",
                words: [
                    {w:"ช้อน", i:"🥄"}, {w:"ฟุตบอล", i:"⚽"}, {w:"เหรียญ", i:"🪙"}, {w:"พยาบาล", i:"👩‍⚕️"}, {w:"ทหาร", i:"🪖"},
                    {w:"ผลไม้", i:"🍎"}, {w:"ของขวัญ", i:"🎁"}, {w:"ปฏิทิน", i:"📅"}, {w:"บันได", i:"🪜"}, {w:"แว่นตา", i:"👓"},
                    {w:"บ้าน", i:"🏠"}, {w:"จาน", i:"🍽️"}, {w:"โจร", i:"🥷"}, {w:"วาฬ", i:"🐳"}, {w:"น้ำตาล", i:"🧂"},
                    {w:"หมอน", i:"🛌"}, {w:"แหวน", i:"💍"}, {w:"กรรไกร", i:"✂️"}, {w:"ฟัน", i:"🦷"}, {w:"ถนน", i:"🛣️"}
                ]
            },
            {
                id: "kong", title: "🐘 ๖. แม่ กง", desc: "คำที่มี <strong>ง</strong> เป็นตัวสะกด", color: "var(--c-kong)",
                words: [
                    {w:"ช้าง", i:"🐘"}, {w:"ลิง", i:"🐒"}, {w:"กางเกง", i:"👖"}, {w:"เตียง", i:"🛏️"}, {w:"แมลง", i:"🐞"},
                    {w:"กลอง", i:"🥁"}, {w:"ธง", i:"🇹🇭"}, {w:"ยาง", i:"🛞"}, {w:"แตงโม", i:"🍉"}, {w:"กุ้ง", i:"🦐"},
                    {w:"รุ้ง", i:"🌈"}, {w:"ถุง", i:"🛍️"}, {w:"ยุง", i:"🦟"}, {w:"กระโปรง", i:"👗"}, {w:"มะม่วง", i:"🥭"},
                    {w:"กล่อง", i:"📦"}, {w:"ทอง", i:"🥇"}, {w:"แปรง", i:"🪥"}, {w:"รองเท้า", i:"👟"}, {w:"กระถาง", i:"🪴"}
                ]
            },
            {
                id: "kom", title: "🍊 ๗. แม่ กม", desc: "คำที่มี <strong>ม</strong> เป็นตัวสะกด", color: "var(--c-kom)",
                words: [
                    {w:"ส้ม", i:"🍊"}, {w:"ร่ม", i:"☂️"}, {w:"ฉลาม", i:"🦈"}, {w:"นม", i:"🥛"}, {w:"ไอศกรีม", i:"🍦"},
                    {w:"โคมไฟ", i:"💡"}, {w:"เข็ม", i:"🪡"}, {w:"หัวหอม", i:"🧅"}, {w:"แยม", i:"🍯"}, {w:"พัดลม", i:"🌬️"},
                    {w:"ผม", i:"💇"}, {w:"มะขาม", i:"🤎"}, {w:"ชาม", i:"🍜"}, {w:"ซ่อม", i:"🛠️"}, {w:"ยิ้ม", i:"😊"},
                    {w:"กระเทียม", i:"🧄"}, {w:"ชมพู่", i:"💗"}, {w:"ทับทิม", i:"❤️"}, {w:"สนาม", i:"🏟️"}, {w:"เต็นท์โดม", i:"⛺"}
                ]
            },
            {
                id: "koei", title: "🍌 ๘. แม่ เกย", desc: "คำที่มี <strong>ย</strong> เป็นตัวสะกด", color: "var(--c-koei)",
                words: [
                    {w:"กล้วย", i:"🍌"}, {w:"ไฟฉาย", i:"🔦"}, {w:"หอย", i:"🐚"}, {w:"ควาย", i:"🐃"}, {w:"กระต่าย", i:"🐰"},
                    {w:"เลื่อย", i:"🪚"}, {w:"เนย", i:"🧈"}, {w:"ถ้วย", i:"🍵"}, {w:"สร้อย", i:"📿"}, {w:"ป้าย", i:"🛑"},
                    {w:"มวย", i:"🥊"}, {w:"หิ่งห้อย", i:"✨"}, {w:"นักมวย", i:"🥊"}, {w:"ยาย", i:"👵"}, {w:"สวย", i:"💅"},
                    {w:"รวย", i:"💰"}, {w:"หอยทาก", i:"🐌"}, {w:"อร่อย", i:"😋"}, {w:"ป่วย", i:"🤒"}, {w:"ผู้ชาย", i:"👨"}
                ]
            },
            {
                id: "keaw", title: "🐱 ๙. แม่ เกอว", desc: "คำที่มี <strong>ว</strong> เป็นตัวสะกด", color: "var(--c-keaw)",
                words: [
                    {w:"แมว", i:"🐱"}, {w:"แก้ว", i:"🥛"}, {w:"ดาว", i:"⭐"}, {w:"มะพร้าว", i:"🥥"}, {w:"คอมพิวเตอร์", i:"💻"},
                    {w:"นิ้ว", i:"👆"}, {w:"ว่าว", i:"🪁"}, {w:"ข้าว", i:"🍚"}, {w:"มะนาว", i:"🍋"}, {w:"ค้างคาว", i:"🦇"},
                    {w:"เคียว", i:"🌾"}, {w:"หิว", i:"🤤"}, {w:"ข่าว", i:"📰"}, {w:"สาว", i:"👩"}, {w:"ไข่ดาว", i:"🍳"},
                    {w:"สิว", i:"🔴"}, {w:"คิ้ว", i:"🤨"}, {w:"เหยี่ยว", i:"🦅"}, {w:"นิ้วโป้ง", i:"👍"}, {w:"นิ้วก้อย", i:"🤙"}
                ]
            }
        ];

        // ==========================================
        // 1. สร้าง UI: แถบเมนูย่อย (Tabs) และเนื้อหาคำศัพท์
        // ==========================================
        const tabsContainer = document.getElementById('matra-tabs');
        const container = document.getElementById('matra-container');
        let tabsHTML = '';
        let htmlContent = '';

        matraData.forEach((matra, index) => {
            const isActive = index === 0 ? 'active' : '';
            const displayStyle = index === 0 ? 'block' : 'none';
            const activeBg = index === 0 ? `background-color: ${matra.color}; color: white; border-color: ${matra.color};` : '';
            
            const shortName = matra.title.split('. ')[1];
            const icon = matra.title.split(' ')[0];

            tabsHTML += `<button class="matra-tab-btn ${isActive}" id="tab-${matra.id}" onclick="openMatraTab('${matra.id}', '${matra.color}')" style="${activeBg}">${icon} ${shortName}</button>`;

            htmlContent += `
                <section id="sec-${matra.id}" class="section-box matra-section ${isActive}" style="border-color: ${matra.color}; display: ${displayStyle};">
                    <h2 style="color: ${matra.color};">${matra.title}</h2>
                    <p style="font-size: 1.2rem; margin-bottom: 20px;">${matra.desc}</p>
                    <div class="word-grid">
            `;
            matra.words.forEach(word => {
                htmlContent += `
                        <div class="word-card">
                            <div class="word-image">${word.i}</div>
                            <span>${word.w}</span>
                            <button class="play-sound-btn" onclick="speakThaiSlowly('${word.w}')" aria-label="ฟังเสียงคำว่า ${word.w}">🔊</button>
                        </div>
                `;
            });
            
            htmlContent += `
                    </div>
                </section>
            `;
        });
        
        tabsContainer.innerHTML = tabsHTML;
        container.innerHTML = htmlContent;

        // ฟังก์ชันสลับหน้าต่างมาตรา
        window.openMatraTab = function(matraId, color) {
            document.querySelectorAll('.matra-section').forEach(sec => {
                sec.style.display = 'none';
                sec.classList.remove('active');
            });
            document.querySelectorAll('.matra-tab-btn').forEach(tab => {
                tab.style.backgroundColor = '#f9f9f9';
                tab.style.color = 'var(--text-dark)';
                tab.style.borderColor = '#eee';
                tab.classList.remove('active');
            });

            const activeSec = document.getElementById('sec-' + matraId);
            activeSec.style.display = 'block';
            activeSec.classList.add('active');

            const activeTab = document.getElementById('tab-' + matraId);
            activeTab.style.backgroundColor = color;
            activeTab.style.color = 'white';
            activeTab.style.borderColor = color;
            activeTab.classList.add('active');
        };

        // ==========================================
        // 2. ระบบเสียง (Web Speech API)
        // ==========================================
        // เพิ่มระบบปลดล็อกเสียงสำหรับโทรศัพท์มือถือ
        let speechUnlocked = false;
        function unlockSpeech() {
            if (!speechUnlocked && 'speechSynthesis' in window) {
                // สร้างเสียงว่างเปล่าเพื่อกระตุ้นให้ระบบเสียงของมือถือตื่นตัว
                const utterance = new SpeechSynthesisUtterance('');
                window.speechSynthesis.speak(utterance);
                speechUnlocked = true;
                // เมื่อปลดล็อกแล้ว ให้เอาตัวดักจับออก
                document.removeEventListener('touchstart', unlockSpeech);
                document.removeEventListener('click', unlockSpeech);
            }
        }
        // ดักจับการแตะหน้าจอครั้งแรกเพื่อปลดล็อกเสียง
        document.addEventListener('touchstart', unlockSpeech);
        document.addEventListener('click', unlockSpeech);

        function speakThaiSlowly(text) {
            if ('speechSynthesis' in window) {
                window.speechSynthesis.cancel();
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = 'th-TH'; 
                // ปรับความเร็วขึ้นมานิดหน่อย (มือถือบางรุ่นจะไม่อ่านถ้าตั้งค่าต่ำกว่า 0.5)
                utterance.rate = 0.6;    
                utterance.pitch = 1.1;

                // พยายามเลือกเสียงภาษาไทยที่ติดตั้งอยู่ในเครื่องให้แม่นยำขึ้น
                const voices = window.speechSynthesis.getVoices();
                const thaiVoice = voices.find(v => v.lang.includes('th') || v.lang.includes('TH'));
                if (thaiVoice) {
                    utterance.voice = thaiVoice;
                }

                window.speechSynthesis.speak(utterance);
            }
        }

        function playFeedbackSound(isCorrect) {
            if ('speechSynthesis' in window) {
                window.speechSynthesis.cancel();
                const feedbackText = isCorrect ? "ถูกต้องครับ!" : "ผิดครับ ลองใหม่นะ";
                const utterance = new SpeechSynthesisUtterance(feedbackText);
                utterance.lang = 'th-TH';
                utterance.rate = 0.7; // ปรับให้เสียงเกมเร็วขึ้นนิดหน่อย
                
                const voices = window.speechSynthesis.getVoices();
                const thaiVoice = voices.find(v => v.lang.includes('th') || v.lang.includes('TH'));
                if (thaiVoice) {
                    utterance.voice = thaiVoice;
                }

                window.speechSynthesis.speak(utterance);
            }
        }

        // ==========================================
        // 3. ระบบเกม "นักล่าคำศัพท์" (หารูปภาพ 4 ตัวเลือก, 3 หัวใจ)
        // ==========================================
        let gameScore = 0;
        let gameLives = 3; 
        let gameCombo = 0; 
        let currentTargetMatra = "";
        let currentCorrectWordObj = null;

        function startGame() {
            gameScore = 0;
            gameLives = 3;
            gameCombo = 0;
            updateGameHeader();
            
            document.getElementById('game-start-screen').style.display = 'none';
            document.getElementById('game-over-screen').style.display = 'none';
            document.getElementById('game-play-screen').style.display = 'block';
            
            loadNextQuestion();
            speakThaiSlowly("เริ่มเกมนักล่าคำศัพท์");
        }

        function loadNextQuestion() {
            const randomMatraIndex = Math.floor(Math.random() * matraData.length);
            const targetMatra = matraData[randomMatraIndex];
            currentTargetMatra = targetMatra.title.split('. ')[1]; 
            
            const matraEl = document.getElementById('game-target-matra');
            matraEl.innerText = currentTargetMatra;
            matraEl.classList.remove('game-target-matra');
            void matraEl.offsetWidth; 
            matraEl.classList.add('game-target-matra');
            
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(`ค้นหาคำที่อยู่ใน ${currentTargetMatra}`);
                utterance.lang = 'th-TH'; utterance.rate = 0.6;
                window.speechSynthesis.speak(utterance);
            }

            const correctWordIndex = Math.floor(Math.random() * targetMatra.words.length);
            currentCorrectWordObj = targetMatra.words[correctWordIndex];
            
            let wrongWords = [];
            while(wrongWords.length < 3) {
                let rMatraIdx = Math.floor(Math.random() * matraData.length);
                if(rMatraIdx !== randomMatraIndex) {
                    let rWordIdx = Math.floor(Math.random() * matraData[rMatraIdx].words.length);
                    let wWord = matraData[rMatraIdx].words[rWordIdx];
                    if(!wrongWords.find(w => w.w === wWord.w)) {
                        wrongWords.push(wWord);
                    }
                }
            }

            let choices = [currentCorrectWordObj, ...wrongWords];
            choices.sort(() => Math.random() - 0.5);

            const choicesContainer = document.getElementById('choices-container');
            let buttonsHTML = '';
            choices.forEach(choiceObj => {
                const isCorrect = (choiceObj.w === currentCorrectWordObj.w);
                buttonsHTML += `
                    <button class="image-choice-btn" data-correct="${isCorrect}" onclick="checkGameAnswer(this)">
                        <div class="image-choice-emoji">${choiceObj.i}</div>
                        <div class="image-choice-word">${choiceObj.w}</div>
                    </button>
                `;
            });
            choicesContainer.innerHTML = buttonsHTML;
        }

        function checkGameAnswer(buttonElement) {
            const buttons = document.querySelectorAll('#choices-container .image-choice-btn');
            buttons.forEach(btn => btn.disabled = true); 

            const isCorrect = buttonElement.getAttribute('data-correct') === 'true';

            if (isCorrect) {
                gameCombo++;
                let bonusPoints = (gameCombo > 1) ? (gameCombo * 5) : 0; 
                gameScore += (10 + bonusPoints);
                
                updateGameHeader(bonusPoints);
                buttonElement.classList.add('btn-correct');
                playFeedbackSound(true);
                
                setTimeout(() => {
                    loadNextQuestion();
                }, 1500);

            } else {
                gameLives--;
                gameCombo = 0;
                updateGameHeader();
                
                buttonElement.classList.add('btn-wrong');
                document.getElementById('question-box').classList.add('shake-anim');
                playFeedbackSound(false);

                buttons.forEach(btn => {
                    if (btn.getAttribute('data-correct') === 'true') {
                        btn.classList.add('btn-correct');
                    }
                });

                setTimeout(() => {
                    document.getElementById('question-box').classList.remove('shake-anim');
                    if (gameLives > 0) {
                        loadNextQuestion();
                    } else {
                        endGame();
                    }
                }, 2000);
            }
        }

        function updateGameHeader(bonus = 0) {
            document.getElementById('game-score').innerText = gameScore;
            
            let hearts = '';
            for(let i=0; i<3; i++) {
                hearts += (i < gameLives) ? '❤️' : '🖤';
            }
            document.getElementById('game-lives').innerText = hearts;

            const comboEl = document.getElementById('combo-display');
            if(gameCombo > 1) {
                comboEl.innerText = `Combo x${gameCombo} (+${bonus}) 🔥`;
                comboEl.style.display = 'block';
                comboEl.style.animation = 'none';
                void comboEl.offsetWidth;
                comboEl.style.animation = 'popIn 0.3s ease-out';
            } else {
                comboEl.style.display = 'none';
            }
        }

        function endGame() {
            document.getElementById('game-play-screen').style.display = 'none';
            document.getElementById('game-over-screen').style.display = 'block';
            
            document.getElementById('game-over-score').innerHTML = `เก่งมากๆ น้องๆ ทำคะแนนได้<br><strong style="font-size: 4rem; color: #ff4757;">${gameScore}</strong><br>คะแนน`;
            
            if (gameScore >= 100) {
                document.getElementById('game-over-emoji').innerText = '🎉';
                document.getElementById('game-over-title').innerText = 'สุดยอดนักล่าคำศัพท์!';
                speakThaiSlowly(`สุดยอด น้องๆ ได้ ${gameScore} คะแนน`);
            } else {
                document.getElementById('game-over-emoji').innerText = '💪';
                document.getElementById('game-over-title').innerText = 'พยายามได้ดีมาก!';
                speakThaiSlowly(`จบเกม น้องๆ ได้ ${gameScore} คะแนน ลองเล่นอีกครั้งนะ`);
            }
        }
    </script>
</body>
</html>
