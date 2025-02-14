<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Для моей любимой</title>
    <style>
        body {
            background: linear-gradient(to right, #ff758c, #ff7eb3);
            font-family: 'Georgia', serif;
            text-align: center;
            padding: 20px;
            color: #fff;
            overflow-y: auto;
            height: 100vh;
            margin: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
        }
        .container {
            max-width: 800px;
            width: 90%;
            margin-top: 20px;
            background: rgba(255, 255, 255, 0.3);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
            position: relative;
        }
        h1 {
            color: #fff;
            font-size: 36px;
        }
        .letter {
            background: rgba(255, 255, 255, 0.9);
            color: #333;
            padding: 20px;
            border-radius: 15px;
            font-size: 22px;
            font-weight: bold;
            text-align: left;
            margin-top: 20px;
            max-height: 400px;
            overflow-y: auto;
        }
        .controls {
            margin-top: 20px;
        }
        button {
            background: #ff3f6c;
            color: white;
            border: none;
            padding: 12px 25px;
            margin: 10px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            transition: background 0.3s;
        }
        button:hover {
            background: #e62e5d;
        }
        .gallery {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
            margin-top: 20px;
        }
        .gallery img {
            width: 120px;
            height: 120px;
            border-radius: 15px;
            object-fit: cover;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Для моей любимой</h1>
        <div class="letter">
            <p>Моей самой любимой</p>
            <p>Жаным,</p>
            <p>Я до сих пор помню тот день, когда встретил тебя. Мы вышли за водой, и тогда… твоя улыбка, твой взгляд сразу убили меня. С того момента я не мог перестать думать о тебе. Я ждал, надеялся снова увидеть тебя, узнать хоть что-то, чтобы понять — встретимся ли мы снова?</p>
            <p>Но ты изменила меня. Да, я всё ещё ленивый, могу забывать простые вещи… но я никогда не забуду твой влюблённый взгляд, твой голос, твои слова. Я помню твой запах, твои мягкие волосы, то, какая ты заботливая. Да какая разница, что у тебя трудный характер? Для меня это неважно. Наоборот, именно это притягивает меня к тебе ещё сильнее.</p>
            <p>Ты не простая. Ты особенная.</p>
            <p>Ты настолько красивая, что я просто замираю от счастья. Я не могу жить без твоих поцелуев, без твоих объятий. Когда ты не пишешь мне, будто дыхание сбивается, будто жизнь становится сложнее, а дышать труднее.</p>
            <p>Я хочу, чтобы у нас всё получилось. Я хочу видеть тебя каждое утро рядом со мной в постели… уже не просто как любимую девушку, а как жену. Я не знаю… мне кажется, ты создана для меня. Я не могу представить рядом другую женщину, кроме тебя.</p>
            <p>Ты спасла меня. И я благодарен за это.</p>
            <p>Да, я ещё многому учусь. Я не меняюсь, я улучшаюсь рядом с тобой. Потому что рядом с тобой я становлюсь в миллион раз лучше. Но знаешь, мне всё равно, каким видят меня другие. Самое главное — ты видишь во мне своего человека. А я вижу, что ты — моя.</p>
            <p>Я люблю тебя (М)</p>
        </div>
        <div class="controls">
            <input type="file" id="music-upload" accept="audio/*" multiple>
            <button onclick="playMusic()">Играть</button>
            <button onclick="stopMusic()">Стоп</button>
        </div>
        <audio id="background-music" loop></audio>
        <h2>ФОТКИ МОЕЙ БОПАШКИ ЛЮБЛЮ ТЕБЯ ЖАНЫМ</h2>
        <input type="file" id="photo-upload" accept="image/*" multiple onchange="loadPhotos(event)">
        <div class="gallery" id="photo-gallery"></div>
    </div>
    <script>
        let musicFiles = [];
        let currentTrack = 0;
        const audioPlayer = document.getElementById("background-music");
        const musicUpload = document.getElementById("music-upload");
        
        function playMusic() {
            if (musicFiles.length > 0) {
                audioPlayer.src = URL.createObjectURL(musicFiles[currentTrack]);
                audioPlayer.play();
                audioPlayer.onended = function() {
                    currentTrack = (currentTrack + 1) % musicFiles.length;
                    playMusic();
                };
            }
        }
        
        function stopMusic() {
            audioPlayer.pause();
            audioPlayer.currentTime = 0;
        }
        
        musicUpload.addEventListener("change", function(event) {
            musicFiles = Array.from(event.target.files);
            if (musicFiles.length > 0) {
                playMusic();
            }
        });
        
        function loadPhotos(event) {
            const gallery = document.getElementById("photo-gallery");
            const files = event.target.files;
            for (let i = 0; i < files.length; i++) {
                const img = document.createElement("img");
                img.src = URL.createObjectURL(files[i]);
                gallery.appendChild(img);
            }
        }
    </script>
</body>
</html>
