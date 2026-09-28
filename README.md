<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lola's Little Universe</title>

<style>
* {
    box-sizing: border-box;
}

html, body {
    margin: 0;
    padding: 0;
    width: 100%;
    min-height: 100%;
    font-family: Georgia, "Times New Roman", serif;
    background: #020b20;
    color: white;
    overflow-x: hidden;
}

body {
    min-height: 100vh;
}

button {
    font-family: inherit;
}

#game {
    min-height: 100vh;
    position: relative;
    overflow: hidden;
}

/* =========================
   BACKGROUND
========================= */

.space {
    position: fixed;
    inset: 0;
    z-index: 0;
    background:
        radial-gradient(circle at 20% 20%, rgba(95,160,255,.15), transparent 25%),
        radial-gradient(circle at 80% 70%, rgba(100,200,255,.12), transparent 25%),
        linear-gradient(180deg, #020817, #031a3a 55%, #020817);
}

.star-bg {
    position: fixed;
    width: 3px;
    height: 3px;
    border-radius: 50%;
    background: white;
    opacity: .7;
    animation: twinkle 3s infinite alternate;
    z-index: 1;
}

@keyframes twinkle {
    from { opacity: .15; transform: scale(.7); }
    to { opacity: 1; transform: scale(1.3); }
}

.stingray {
    position: fixed;
    font-size: 42px;
    opacity: .15;
    z-index: 2;
    animation: swim 20s linear infinite;
    pointer-events: none;
}

.stingray.one {
    top: 18%;
    left: -80px;
}

.stingray.two {
    top: 72%;
    right: -80px;
    animation-delay: 8s;
    transform: scaleX(-1);
}

@keyframes swim {
    0% {
        transform: translateX(0);
    }
    50% {
        transform: translateX(55vw) translateY(-40px);
    }
    100% {
        transform: translateX(115vw) translateY(20px);
    }
}

/* =========================
   HUD
========================= */

#hud {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    padding: 14px 18px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    z-index: 20;
    background: rgba(2,10,30,.55);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(255,255,255,.08);
}

.hud-title {
    font-size: 14px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: #bcdcff;
}

.star-counter {
    color: #fff1a8;
    font-size: 15px;
}

/* =========================
   SCREEN
========================= */

.screen {
    position: relative;
    z-index: 5;
    min-height: 100vh;
    padding: 90px 20px 50px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.panel {
    width: min(850px, 100%);
    background: rgba(4,21,50,.78);
    border: 1px solid rgba(150,210,255,.22);
    box-shadow: 0 25px 80px rgba(0,0,0,.45);
    border-radius: 28px;
    padding: 35px;
    backdrop-filter: blur(16px);
    animation: appear .7s ease;
}

@keyframes appear {
    from {
        opacity: 0;
        transform: translateY(20px) scale(.98);
    }
    to {
        opacity: 1;
        transform: translateY(0) scale(1);
    }
}

h1 {
    font-size: clamp(38px, 8vw, 75px);
    margin: 0 0 12px;
    text-align: center;
    color: #d9ecff;
    text-shadow: 0 0 25px rgba(120,190,255,.4);
}

h2 {
    font-size: clamp(27px, 5vw, 43px);
    text-align: center;
    color: #d8edff;
    margin-top: 0;
}

h3 {
    color: #b9dcff;
}

.subtitle {
    text-align: center;
    color: #b9cce5;
    font-size: 18px;
    line-height: 1.8;
}

.story {
    font-size: 18px;
    line-height: 1.9;
    color: #e4edf8;
}

.story p {
    margin: 0 0 18px;
}

.quote {
    margin: 25px 0;
    padding: 20px;
    border-left: 3px solid #9bd2ff;
    background: rgba(120,190,255,.06);
    color: #cfe8ff;
    font-style: italic;
}

/* =========================
   CHOICES
========================= */

.choices {
    display: grid;
    gap: 14px;
    margin-top: 30px;
}

.choice {
    width: 100%;
    padding: 17px 20px;
    border-radius: 16px;
    border: 1px solid rgba(160,210,255,.3);
    background: rgba(85,155,220,.10);
    color: white;
    font-size: 17px;
    cursor: pointer;
    transition: .25s;
    text-align: left;
}

.choice:hover {
    background: rgba(120,190,255,.22);
    transform: translateY(-2px);
    border-color: rgba(190,230,255,.7);
    box-shadow: 0 8px 30px rgba(70,160,255,.12);
}

.choice small {
    display: block;
    color: #9eb9d7;
    margin-top: 5px;
}

/* =========================
   BUTTON
========================= */

.continue {
    display: block;
    margin: 30px auto 0;
    padding: 14px 28px;
    border-radius: 30px;
    border: 1px solid #b5dcff;
    background: rgba(150,210,255,.12);
    color: white;
    cursor: pointer;
    font-size: 17px;
    transition: .25s;
}

.continue:hover {
    background: rgba(150,210,255,.25);
    transform: translateY(-2px);
}

/* =========================
   GAME MAP
========================= */

.map {
    position: relative;
    height: 560px;
    border-radius: 25px;
    overflow: hidden;
    background:
        radial-gradient(circle at center, rgba(255,220,100,.14), transparent 8%),
        radial-gradient(circle at 30% 40%, rgba(80,160,255,.09), transparent 30%),
        radial-gradient(circle at 75% 65%, rgba(160,100,255,.08), transparent 30%),
        #020918;
    border: 1px solid rgba(180,220,255,.15);
}

.sun {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background: radial-gradient(circle, #fff4bd, #ffcb62, #d87c2c);
    box-shadow: 0 0 55px rgba(255,205,100,.55);
}

.orbit {
    position: absolute;
    left: 50%;
    top: 50%;
    border: 1px solid rgba(180,220,255,.12);
    border-radius: 50%;
    transform: translate(-50%,-50%);
}

.o1 { width: 160px; height: 160px; }
.o2 { width: 270px; height: 270px; }
.o3 { width: 390px; height: 390px; }
.o4 { width: 510px; height: 510px; }

.planet {
    position: absolute;
    width: 70px;
    height: 70px;
    border-radius: 50%;
    border: 1px solid rgba(255,255,255,.3);
    cursor: pointer;
    color: white;
    font-size: 28px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: .3s;
    box-shadow: 0 0 25px rgba(100,190,255,.15);
}

.planet:hover {
    transform: scale(1.15);
    box-shadow: 0 0 35px rgba(150,220,255,.4);
}

.planet span {
    position: absolute;
    top: 76px;
    font-size: 12px;
    width: 120px;
    text-align: center;
    color: #bcd5ef;
}

.p-coffee {
    left: 18%;
    top: 20%;
    background: radial-gradient(circle at 30% 30%, #d8b38a, #684b35);
}

.p-storm {
    right: 17%;
    top: 18%;
    background: radial-gradient(circle at 30% 30%, #8da6c8, #202c53);
}

.p-gravity {
    left: 12%;
    bottom: 18%;
    background: radial-gradient(circle at 30% 30%, #efb8d8, #613b79);
}

.p-ocean {
    right: 13%;
    bottom: 20%;
    background: radial-gradient(circle at 30% 30%, #80e2ff, #1266a8);
}

.p-future {
    left: 50%;
    bottom: 7%;
    transform: translateX(-50%);
    background: radial-gradient(circle at 30% 30%, #d6b7ff, #54387d);
}

.p-future:hover {
    transform: translateX(-50%) scale(1.15);
}

.map-label {
    position: absolute;
    left: 50%;
    top: 16px;
    transform: translateX(-50%);
    text-align: center;
    color: #b9d9f8;
    letter-spacing: 3px;
    text-transform: uppercase;
    font-size: 12px;
}

/* =========================
   SPECIAL SCENES
========================= */

.big-symbol {
    text-align: center;
    font-size: 85px;
    margin: 10px 0 20px;
    filter: drop-shadow(0 0 20px rgba(150,210,255,.3));
}

.ocean-scene {
    min-height: 350px;
    border-radius: 22px;
    padding: 30px;
    background:
        radial-gradient(circle at 50% 20%, rgba(170,235,255,.3), transparent 20%),
        linear-gradient(180deg, rgba(50,160,220,.35), rgba(2,30,65,.8));
    position: relative;
    overflow: hidden;
}

.wave {
    position: absolute;
    left: -10%;
    width: 120%;
    height: 90px;
    border-radius: 50%;
    border-top: 3px solid rgba(190,240,255,.3);
    animation: wave 5s ease-in-out infinite alternate;
}

.wave.one { bottom: 30px; }
.wave.two { bottom: 75px; animation-delay: 1s; }
.wave.three { bottom: 120px; animation-delay: 2s; }

@keyframes wave {
    from { transform: translateX(-20px); }
    to { transform: translateX(20px); }
}

.stingray-big {
    font-size: 80px;
    text-align: center;
    animation: ray 5s ease-in-out infinite alternate;
}

@keyframes ray {
    from { transform: translateX(-25px) rotate(-4deg); }
    to { transform: translateX(25px) rotate(4deg); }
}

/* =========================
   STARS
========================= */

.hidden-star {
    position: absolute;
    color: #fff5a8;
    font-size: 28px;
    cursor: pointer;
    z-index: 10;
    text-shadow: 0 0 15px #fff;
    animation: starPulse 1.7s infinite alternate;
}

@keyframes starPulse {
    from { opacity: .45; transform: scale(.8); }
    to { opacity: 1; transform: scale(1.2); }
}

.constellation {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 12px;
    margin-top: 25px;
}

.collect-star {
    aspect-ratio: 1;
    border-radius: 50%;
    background: rgba(255,255,255,.05);
    border: 1px solid rgba(255,255,255,.12);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
}

.collect-star.found {
    color: #fff3a3;
    background: rgba(255,230,120,.12);
    box-shadow: 0 0 20px rgba(255,230,120,.25);
}

/* =========================
   WEDDING / FUTURE
========================= */

.wedding {
    text-align: center;
    padding: 20px;
}

.rings {
    font-size: 90px;
    animation: float 3s ease-in-out infinite;
}

@keyframes float {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-12px); }
}

.countryside {
    min-height: 350px;
    border-radius: 25px;
    position: relative;
    overflow: hidden;
    background:
        linear-gradient(180deg, #92c9ef 0%, #d9efff 42%, #7fb77d 43%, #315e39 100%);
}

.sunset {
    position: absolute;
    width: 85px;
    height: 85px;
    border-radius: 50%;
    background: #ffe3a0;
    right: 15%;
    top: 13%;
    box-shadow: 0 0 45px rgba(255,225,150,.6);
}

.house {
    position: absolute;
    bottom: 75px;
    left: 50%;
    transform: translateX(-50%);
    width: 160px;
    height: 110px;
    background: #d7b991;
    border-radius: 8px;
}

.house:before {
    content: "";
    position: absolute;
    left: -25px;
    top: -65px;
    width: 210px;
    height: 90px;
    background: #734c43;
    clip-path: polygon(50% 0,100% 100%,0 100%);
}

.treehouse {
    position: absolute;
    left: 12%;
    bottom: 85px;
    font-size: 70px;
}

.field {
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 110px;
    background: rgba(36,92,47,.65);
}

/* =========================
   FINAL
========================= */

.final {
    text-align: left;
}

.final h2 {
    text-align: center;
}

.final-letter {
    line-height: 2;
    font-size: 17px;
    color: #e4edf8;
}

.real-star {
    text-align: center;
    margin-top: 30px;
    padding: 35px 20px;
    border-radius: 25px;
    background: radial-gradient(circle, rgba(255,230,120,.15), rgba(255,230,120,.02));
    border: 1px solid rgba(255,230,120,.2);
}

.real-star .star {
    font-size: 110px;
    animation: starReveal 2s infinite alternate;
}

@keyframes starReveal {
    from {
        transform: scale(.9);
        filter: drop-shadow(0 0 10px #fff);
    }
    to {
        transform: scale(1.08);
        filter: drop-shadow(0 0 35px #fff);
    }
}

/* =========================
   MOBILE
========================= */

@media(max-width: 650px) {
    .panel {
        padding: 24px 18px;
        border-radius: 22px;
    }

    .map {
        height: 500px;
    }

    .planet {
        width: 58px;
        height: 58px;
        font-size: 23px;
    }

    .planet span {
        top: 62px;
        font-size: 10px;
    }

    .o4 {
        width: 450px;
        height: 450px;
    }

    .story {
        font-size: 16px;
    }

    .constellation {
        gap: 7px;
    }
}
</style>
</head>

<body>

<div id="game">

<div class="space"></div>

<div class="star-bg" style="left:8%;top:12%"></div>
<div class="star-bg" style="left:17%;top:42%"></div>
<div class="star-bg" style="left:29%;top:8%"></div>
<div class="star-bg" style="left:42%;top:27%"></div>
<div class="star-bg" style="left:53%;top:10%"></div>
<div class="star-bg" style="left:68%;top:32%"></div>
<div class="star-bg" style="left:81%;top:14%"></div>
<div class="star-bg" style="left:91%;top:47%"></div>
<div class="star-bg" style="left:11%;top:78%"></div>
<div class="star-bg" style="left:34%;top:88%"></div>
<div class="star-bg" style="left:58%;top:76%"></div>
<div class="star-bg" style="left:76%;top:88%"></div>

<div class="stingray one">𓆩𓆪</div>
<div class="stingray two">𓆩𓆪</div>

<div id="hud">
    <div class="hud-title">Lola's Little Universe</div>
    <div class="star-counter">⭐ <span id="starCount">0</span> / 27</div>
</div>

<div id="screen" class="screen"></div>

</div>

<script>

/* =========================================================
   GAME STATE
========================================================= */

const state = {
    stars: new Set(),
    choices: [],
    coffee: false,
    storm: false,
    ocean: false,
    stingray: false,
    future: false,
    weddingChoice: "",
    homeChoice: ""
};

/* =========================================================
   HELPERS
========================================================= */

const screen = document.getElementById("screen");
const starCount = document.getElementById("starCount");

function updateStars() {
    starCount.textContent = state.stars.size;
}

function addStar(id) {

    if (state.stars.has(id)) return;

    state.stars.add(id);
    updateStars();

    const el = document.createElement("div");
    el.className = "hidden-star";
    el.textContent = "⭐";
    el.style.left = Math.random() * 85 + 5 + "%";
    el.style.top = Math.random() * 75 + 10 + "%";

    el.onclick = () => {
        state.stars.add(id);
        el.remove();
        updateStars();
    };

    screen.appendChild(el);
}

function panel(content) {
    screen.innerHTML = `<div class="panel">${content}</div>`;
}

function choice(text, fn, description = "") {
    return `
        <button class="choice" onclick="${fn}">
            ${text}
            ${description ? `<small>${description}</small>` : ""}
        </button>
    `;
}

function remember(choiceName) {
    state.choices.push(choiceName);
}

/* =========================================================
   START
========================================================= */

function startGame() {

    panel(`
        <div class="big-symbol">🌌</div>

        <h1>Lola's Little Universe</h1>

        <p class="subtitle">
            A little adventure made for the girl who somehow became
            my favourite part of the universe.
        </p>

        <div class="story">
            <p>
                Somewhere beyond the stars, there is a universe that has
                been waiting for you.
            </p>

            <p>
                But before you can reach it, you have to find your way there.
            </p>

            <div class="quote">
                "There are billions of stars in the sky.
                Somehow, I still found you."
            </div>
        </div>

        <button class="continue" onclick="chapterOne()">
            Begin the journey ✨
        </button>
    `);
}

/* =========================================================
   CHAPTER 1
========================================================= */

function chapterOne() {

    panel(`
        <h2>Chapter One<br>The Beginning</h2>

        <div class="story">

            <p>
                Lola wakes somewhere unfamiliar.
            </p>

            <p>
                There is no ground beneath her feet.
                No ceiling above her.
                Only stars.
            </p>

            <p>
                Floating in front of her is a tiny spaceship.
                On the side, written in silver letters, are three words:
            </p>

            <div class="quote">
                FIND YOUR UNIVERSE.
            </div>

            <p>
                Beneath it are three glowing paths.
            </p>

        </div>

        <div class="choices">

            ${choice(
                "🚀 Take the spaceship",
                "openingShip()",
                "Maybe the stars are trying to lead somewhere."
            )}

            ${choice(
                "✨ Follow the stars",
                "openingStars()",
                "Somewhere, one star shines brighter than the rest."
            )}

            ${choice(
                "🌊 Follow the sound of waves",
                "openingOcean()",
                "You can hear the ocean even though there shouldn't be one."
            )}

        </div>
    `);
}

/* =========================================================
   OPENING BRANCHES
========================================================= */

function openingShip() {

    remember("spaceship");

    panel(`
        <div class="big-symbol">🚀</div>

        <h2>The Spaceship</h2>

        <div class="story">

            <p>
                Lola climbs inside.
            </p>

            <p>
                The spaceship is tiny, but somehow it feels warm.
            </p>

            <p>
                On the dashboard is a single button.
            </p>

            <p>
                It reads:
            </p>

            <div class="quote">
                "Wherever she is, go there."
            </div>

            <p>
                You don't know who "she" is yet.
            </p>

        </div>

        <button class="continue" onclick="beforeUs()">
            Press the button ✨
        </button>
    `);
}

function openingStars() {

    remember("stars");

    panel(`
        <div class="big-symbol">✨</div>

        <h2>The Stars</h2>

        <div class="story">

            <p>
                Lola follows the brightest star.
            </p>

            <p>
                As she gets closer, she notices something strange.
            </p>

            <p>
                The stars aren't random.
            </p>

            <p>
                They form a path.
            </p>

            <p>
                And at the end of it is a tiny blue light.
            </p>

            <div class="quote">
                "Keep going."
            </div>

        </div>

        <button class="continue" onclick="beforeUs()">
            Follow the blue light 💙
        </button>
    `);
}

function openingOcean() {

    remember("ocean");

    panel(`
        <div class="big-symbol">🌊</div>

        <h2>The Ocean</h2>

        <div class="story">

            <p>
                Lola follows the sound of waves.
            </p>

            <p>
                Somehow, there is an ocean floating in space.
            </p>

            <p>
                The water is impossibly blue.
            </p>

            <p>
                For a moment, everything is quiet.
            </p>

            <div class="quote">
                "Somewhere out there is someone who wants to see
                the ocean with you."
            </div>

        </div>

        <button class="continue" onclick="beforeUs()">
            Keep walking 🌊
        </button>
    `);
}

/* =========================================================
   CHAPTER 2
========================================================= */

function beforeUs() {

    panel(`
        <h2>Chapter Two<br>Before Us</h2>

        <div class="story">

            <p>
                The path continues.
            </p>

            <p>
                You haven't found the universe yet.
            </p>

            <p>
                Instead, you begin finding pieces of a story.
            </p>

            <p>
                A story about two people who haven't met yet.
            </p>

            <p>
                Somewhere ahead are three worlds.
            </p>

        </div>

        <div class="choices">

            ${choice(
                "☕ Enter the little coffee shop",
                "coffeeScene()",
                "It smells like black coffee."
            )}

            ${choice(
                "🌌 Enter the observatory",
                "observatoryScene()",
                "Something is written in the stars."
            )}

            ${choice(
                "🌊 Return to the ocean",
                "oceanMemory()",
                "You still hear the waves."
            )}

        </div>
    `);
}

/* =========================================================
   COFFEE
========================================================= */

function coffeeScene() {

    state.coffee = true;
    addStar("coffee");

    panel(`
        <div class="big-symbol">☕</div>

        <h2>The Coffee Shop</h2>

        <div class="story">

            <p>
                You open the door.
            </p>

            <p>
                There is one table.
                One chair.
                And a cup of black coffee waiting for someone.
            </p>

            <p>
                Beside it is a note.
            </p>

            <div class="quote">
                "For the girl who likes her coffee black."
            </div>

            <p>
                You smile.
            </p>

            <p>
                You still don't know who she is.
            </p>

        </div>

        <button class="continue" onclick="coffeeChoice()">
            Read the next note ☕
        </button>
    `);
}

function coffeeChoice() {

    panel(`
        <h2>A Little Clue</h2>

        <div class="story">

            <p>
                Beneath the coffee cup is another message.
            </p>

            <div class="quote">
                "She has hazel eyes."
            </div>

            <p>
                And suddenly, the universe feels a little smaller.
            </p>

        </div>

        <div class="choices">

            ${choice(
                "Keep searching",
                "beforeUs()",
                "There must be more."
            )}

            ${choice(
                "Follow the stars",
                "observatoryScene()",
                "Maybe they'll tell you who she is."
            )}

        </div>
    `);
}

/* =========================================================
   OBSERVATORY
========================================================= */

function observatoryScene() {

    addStar("observatory");

    panel(`
        <div class="big-symbol">🔭</div>

        <h2>The Observatory</h2>

        <div class="story">

            <p>
                The telescope points toward a tiny blue star.
            </p>

            <p>
                You look through it.
            </p>

            <p>
                Instead of seeing planets, you see memories.
            </p>

            <p>
                A girl laughing.
                A girl writing.
                A girl looking at the sunset.
            </p>

            <p>
                And then a final message appears.
            </p>

            <div class="quote">
                "She is waiting somewhere beyond the distance."
            </div>

        </div>

        <button class="continue" onclick="stormChapter()">
            Continue 🌩️
        </button>
    `);
}

/* =========================================================
   OCEAN MEMORY
========================================================= */

function oceanMemory() {

    state.ocean = true;

    panel(`
        <div class="ocean-scene">

            <div class="wave one"></div>
            <div class="wave two"></div>
            <div class="wave three"></div>

            <div class="story">
                <h2>The Blue World</h2>

                <p>
                    The ocean stretches endlessly.
                </p>

                <p>
                    You wonder what it would be like to stand beside
                    someone who had always dreamed of seeing it.
                </p>

                <div class="quote">
                    "One day, I want to see the ocean with you."
                </div>
            </div>

        </div>

        <button class="continue" onclick="stormChapter()">
            Leave the ocean 🌊
        </button>
    `);
}

/* =========================================================
   STORM
========================================================= */

function stormChapter() {

    panel(`
        <h2>Chapter Three<br>The Storm</h2>

        <div class="story">

            <p>
                The stars suddenly disappear.
            </p>

            <p>
                Clouds gather around the spaceship.
            </p>

            <p>
                Thunder shakes the sky.
            </p>

            <p>
                For a moment, everything feels frightening.
            </p>

            <p>
                Then you notice something.
            </p>

            <p>
                There is a little light beside you.
            </p>

        </div>

        <div class="choices">

            ${choice(
                "🌩️ Face the storm",
                "stormBrave()",
                "You don't run."
            )}

            ${choice(
                "🚀 Fly straight through it",
                "stormFly()",
                "Maybe the other side is closer than you think."
            )}

            ${choice(
                "⭐ Follow the little light",
                "stormLight()",
                "Something is waiting there."
            )}

            ${choice(
                "🫂 Search for someone",
                "stormSomeone()",
                "You shouldn't have to face a storm alone."
            )}

        </div>
    `);
}

function stormBrave() {
    state.storm = true;
    addStar("storm1");

    panel(`
        <div class="big-symbol">🌩️</div>
        <h2>You Stay</h2>

        <div class="story">
            <p>
                You stay until the storm passes.
            </p>

            <p>
                When the clouds disappear, there is a message written
                across the sky.
            </p>

            <div class="quote">
                "You are braver than you think."
            </div>
        </div>

        <button class="continue" onclick="girlChapter()">
            Continue 💙
        </button>
    `);
}

function stormFly() {

    state.storm = true;

    panel(`
        <div class="big-symbol">🚀</div>
        <h2>Through the Storm</h2>

        <div class="story">

            <p>
                You hold the controls tightly.
            </p>

            <p>
                Lightning flashes around you.
            </p>

            <p>
                And then suddenly...
            </p>

            <p>
                silence.
            </p>

            <p>
                The storm is behind you.
            </p>

            <div class="quote">
                "Sometimes the way forward is through."
            </div>

        </div>

        <button class="continue" onclick="girlChapter()">
            Continue ⭐
        </button>
    `);
}

function stormLight() {

    state.storm = true;

    panel(`
        <div class="big-symbol">✨</div>
        <h2>The Little Light</h2>

        <div class="story">

            <p>
                You follow it.
            </p>

            <p>
                The light gets brighter.
            </p>

            <p>
                And you hear a voice.
            </p>

            <div class="quote">
                "You don't have to be brave alone."
            </div>

        </div>

        <button class="continue" onclick="girlChapter()">
            Follow the voice 💙
        </button>
    `);
}

function stormSomeone() {

    state.storm = true;

    panel(`
        <div class="big-symbol">💙</div>
        <h2>Someone</h2>

        <div class="story">

            <p>
                You search through the darkness.
            </p>

            <p>
                You don't find anyone.
            </p>

            <p>
                But you find something else.
            </p>

            <p>
                A message.
            </p>

            <div class="quote">
                "Someone is looking for you too."
            </div>

        </div>

        <button class="continue" onclick="girlChapter()">
            Keep going ✨
        </button>
    `);
}

/* =========================================================
   GIRL
========================================================= */

function girlChapter() {

    addStar("girl");

    panel(`
        <h2>Chapter Four<br>The Girl Behind the Stars</h2>

        <div class="story">

            <p>
                For the first time, you see her.
            </p>

            <p>
                Not clearly.
                Not enough to touch.
            </p>

            <p>
                Just fragments.
            </p>

            <div class="quote">
                "She likes sunsets."
            </div>

            <div class="quote">
                "She writes when she doesn't know what else to say."
            </div>

            <div class="quote">
                "She has brown eyes."
            </div>

            <div class="quote">
                "And she keeps talking about a girl named Lola."
            </div>

            <p>
                You stop.
            </p>

            <p>
                So that's her name.
            </p>

        </div>

        <button class="continue" onclick="meetingChapter()">
            Find her 💙
        </button>
    `);
}

/* =========================================================
   FINDING EACH OTHER
========================================================= */

function meetingChapter() {

    panel(`
        <h2>Chapter Five<br>Finding Each Other</h2>

        <div class="story">

            <p>
                There are four doors ahead.
            </p>

            <p>
                Each one contains a piece of the story.
            </p>

        </div>

        <div class="choices">

            ${choice(
                "🍣 The Sushi Door",
                "sushiScene()",
                "One of you loves sushi. The other absolutely does not."
            )}

            ${choice(
                "💙 The Blue Door",
                "colourScene()",
                "Baby blue meets burgundy."
            )}

            ${choice(
                "👀 The Hazel Door",
                "hazelScene()",
                "Somewhere behind it are a pair of hazel eyes."
            )}

            ${choice(
                "📏 The Gravity Door",
                "gravityScene()",
                "Apparently height differences can affect the laws of physics."
            )}

        </div>
    `);
}

function sushiScene() {

    remember("sushi");
    addStar("sushi");

    panel(`
        <div class="big-symbol">🍣</div>

        <h2>The Sushi Planet</h2>

        <div class="story">

            <p>
                You arrive on a tiny planet covered in sushi.
            </p>

            <p>
                Lola looks delighted.
            </p>

            <p>
                Bree looks horrified.
            </p>

            <div class="quote">
                "Somehow, love survived this."
            </div>

            <p>
                The universe considers this a miracle.
            </p>

        </div>

        <button class="continue" onclick="meetingChoice()">
            Continue 😂
        </button>
    `);
}

function colourScene() {

    remember("colours");

    panel(`
        <div class="big-symbol">💙</div>

        <h2>Two Moons</h2>

        <div class="story">

            <p>
                Two moons hang above the planet.
            </p>

            <p>
                One is baby blue.
            </p>

            <p>
                One is burgundy.
            </p>

            <p>
                Different colours.
                Same sky.
            </p>

            <div class="quote">
                "Maybe love isn't about being the same.
                Maybe it's about finding someone whose differences
                make your world more beautiful."
            </div>

        </div>

        <button class="continue" onclick="meetingChoice()">
            Continue 💙
        </button>
    `);
}

function hazelScene() {

    remember("hazel");

    panel(`
        <div class="big-symbol">👁️</div>

        <h2>Hazel</h2>

        <div class="story">

            <p>
                The planet is completely dark.
            </p>

            <p>
                Then two hazel lights appear.
            </p>

            <p>
                You realise they aren't lights.
            </p>

            <p>
                They're eyes.
            </p>

            <div class="quote">
                "If the universe ever asks what colour home is,
                I'd say hazel."
            </div>

        </div>

        <button class="continue" onclick="meetingChoice()">
            Continue ✨
        </button>
    `);
}

function gravityScene() {

    remember("gravity");

    panel(`
        <div class="big-symbol">🪐</div>

        <h2>The Gravity Planet</h2>

        <div class="story">

            <p>
                Gravity behaves strangely here.
            </p>

            <p>
                The taller you are, the further you float.
            </p>

            <p>
                Lola barely moves.
            </p>

            <p>
                Bree immediately floats into the ceiling.
            </p>

            <div class="quote">
                "Apparently being 5'10 has finally become a problem."
            </div>

            <p>
                Lola laughs.
            </p>

            <p>
                Somehow, you think that might be your favourite sound.
            </p>

        </div>

        <button class="continue" onclick="meetingChoice()">
            Continue 😂
        </button>
    `);
}

function meetingChoice() {

    panel(`
        <h2>One Last Choice</h2>

        <div class="story">
            <p>
                You've found pieces of Lola.
            </p>

            <p>
                You've found pieces of Bree.
            </p>

            <p>
                But you still haven't found the universe they created together.
            </p>
        </div>

        <div class="choices">

            ${choice(
                "💙 Keep looking for Lola",
                "usChapter()"
            )}

            ${choice(
                "✨ Follow the stars",
                "usChapter()"
            )}

            ${choice(
                "🌊 Find the ocean",
                "oceanChapter()"
            )}

        </div>
    `);
}

/* =========================================================
   US
========================================================= */

function usChapter() {

    addStar("us");

    panel(`
        <h2>Chapter Six<br>Us</h2>

        <div class="story">

            <p>
                Eventually, the distance between two worlds becomes
                smaller.
            </p>

            <p>
                And somehow, you find her.
            </p>

            <p>
                Not in a galaxy.
            </p>

            <p>
                Not in a constellation.
            </p>

            <p>
                Just there.
            </p>

            <p>
                Lola.
            </p>

            <div class="quote">
                "I think I found you."
            </div>

            <p>
                And then the universe gives you four possibilities.
            </p>
        </div>

        <div class="choices">

            ${choice(
                "🌅 Watch the sunset together",
                "sunsetScene()"
            )}

            ${choice(
                "🎨 Paint together",
                "paintingScene()"
            )}

            ${choice(
                "🎶 Sing together",
                "singingScene()"
            )}

            ${choice(
                "💃 Dance together",
                "dancingScene()"
            )}

        </div>
    `);
}

function sunsetScene() {

    panel(`
        <div class="big-symbol">🌅</div>

        <h2>The Sunset</h2>

        <div class="story">

            <p>
                You sit beside each other and watch the sky change.
            </p>

            <p>
                Neither of you says much.
            </p>

            <p>
                You don't need to.
            </p>

            <div class="quote">
                "Some moments are beautiful simply because
                you get to experience them together."
            </div>

        </div>

        <button class="continue" onclick="usChapter()">
            Back to our little world 💙
        </button>
    `);
}

function paintingScene() {

    addStar("painting");

    panel(`
        <div class="big-symbol">🎨</div>

        <h2>The Painting</h2>

        <div class="story">

            <p>
                You paint beside each other.
            </p>

            <p>
                Neither painting makes much sense.
            </p>

            <p>
                Somehow, you both love them anyway.
            </p>

            <div class="quote">
                "We don't have to make something perfect
                for it to become ours."
            </div>

        </div>

        <button class="continue" onclick="usChapter()">
            Keep exploring 🎨
        </button>
    `);
}

function singingScene() {

    panel(`
        <div class="big-symbol">🎶</div>

        <h2>The Song</h2>

        <div class="story">

            <p>
                You sing together.
            </p>

            <p>
                Eventually one of you forgets the words.
            </p>

            <p>
                Then both of you start laughing.
            </p>

            <div class="quote">
                "Maybe this is what happiness sounds like."
            </div>

        </div>

        <button class="continue" onclick="usChapter()">
            Keep exploring 🎶
        </button>
    `);
}

function dancingScene() {

    addStar("dancing");

    panel(`
        <div class="big-symbol">💃</div>

        <h2>The Dance</h2>

        <div class="story">

            <p>
                There isn't even music playing.
            </p>

            <p>
                You dance anyway.
            </p>

            <p>
                Lola laughs.
            </p>

            <p>
                You pull her closer.
            </p>

            <div class="quote">
                "For a moment, there is no distance."
            </div>

        </div>

        <button class="continue" onclick="usChapter()">
            Keep exploring 💙
        </button>
    `);
}

/* =========================================================
   OCEAN
========================================================= */

function oceanChapter() {

    state.ocean = true;

    panel(`
        <div class="ocean-scene">

            <div class="wave one"></div>
            <div class="wave two"></div>
            <div class="wave three"></div>

            <div class="stingray-big">
                𓆩𓆪
            </div>

            <h2>The Ocean</h2>

            <div class="story">

                <p>
                    This is the place Lola always wanted to see.
                </p>

                <p>
                    The two of you stand at the edge of the water.
                </p>

                <p>
                    A stingray glides through the waves.
                </p>

                <p>
                    It looks almost like it is leading you somewhere.
                </p>

            </div>

        </div>

        <button class="continue" onclick="stingrayScene()">
            Follow the stingray 🐠
        </button>
    `);
}

function stingrayScene() {

    state.stingray = true;
    addStar("stingray");

    panel(`
        <div class="big-symbol">𓆩𓆪</div>

        <h2>The Stingray</h2>

        <div class="story">

            <p>
                The stingray disappears beneath the water.
            </p>

            <p>
                You look down.
            </p>

            <p>
                At the bottom of the ocean is a star.
            </p>

            <p>
                You pick it up.
            </p>

            <div class="quote">
                "Some things are worth searching for."
            </div>

            <p>
                You place the star inside your spaceship.
            </p>

        </div>

        <button class="continue" onclick="futureChapter()">
            Continue ⭐
        </button>
    `);
}

/* =========================================================
   FUTURE
========================================================= */

function futureChapter() {

    state.future = true;

    panel(`
        <h2>Chapter Seven<br>The Future</h2>

        <div class="story">

            <p>
                The spaceship begins travelling further than it ever has.
            </p>

            <p>
                Past the stars.
                Past the planets.
                Past everything you thought the universe could contain.
            </p>

            <p>
                And then you see something.
            </p>

            <div class="quote">
                "A life that hasn't happened yet."
            </div>

            <p>
                There are four doors.
            </p>

        </div>

        <div class="choices">

            ${choice(
                "💍 Open the Wedding Garden",
                "weddingScene()",
                "A future where you promise to choose each other."
            )}

            ${choice(
                "🌳 Find the Tree House",
                "treehouseScene()",
                "The little dream you've talked about."
            )}

            ${choice(
                "🏡 Explore the Countryside",
                "countrysideScene()",
                "Green fields, a little house and slow mornings."
            )}

            ${choice(
                "🎨 Find the Studio",
                "futureStudioScene()",
                "A place to paint together."
            )}

        </div>
    `);
}

/* =========================================================
   WEDDING
========================================================= */

function weddingScene() {

    state.weddingChoice = "wedding";
    addStar("wedding");

    panel(`
        <div class="wedding">

            <div class="rings">💍</div>

            <h2>The Wedding Garden</h2>

            <div class="story">

                <p>
                    Flowers surround you.
                </p>

                <p>
                    The sky is full of stars.
                </p>

                <p>
                    And there she is.
                </p>

                <p>
                    Lola.
                </p>

                <p>
                    You reach for her hand.
                </p>

                <div class="quote">
                    "My wife."
                </div>

                <p>
                    The words feel almost impossible to believe.
                </p>

                <p>
                    And somehow, they feel like the most natural words
                    in the world.
                </p>

            </div>

        </div>

        <button class="continue" onclick="weddingChoice()">
            Continue 💍
        </button>
    `);
}

function weddingChoice() {

    panel(`
        <h2>Your Wedding</h2>

        <div class="story">
            <p>
                What kind of wedding do you imagine?
            </p>
        </div>

        <div class="choices">

            ${choice(
                "🌌 Beneath the stars",
                "weddingEnding('stars')"
            )}

            ${choice(
                "🌿 In the countryside",
                "weddingEnding('country')"
            )}

            ${choice(
                "🌸 Surrounded by flowers",
                "weddingEnding('flowers')"
            )}

            ${choice(
                "💙 Just us",
                "weddingEnding('us')"
            )}

        </div>
    `);
}

function weddingEnding(type) {

    state.weddingChoice = type;

    let message = "";

    if (type === "stars") {
        message = "A quiet ceremony beneath a sky full of stars.";
    }

    if (type === "country") {
        message = "A little countryside wedding surrounded by green fields.";
    }

    if (type === "flowers") {
        message = "Flowers everywhere, soft music and two people choosing each other.";
    }

    if (type === "us") {
        message = "No matter where it happens, the important part is that it is you and me.";
    }

    panel(`
        <div class="big-symbol">💍</div>

        <h2>One Day</h2>

        <div class="story">

            <p>
                ${message}
            </p>

            <p>
                Whatever the day looks like, there is one thing that doesn't
                change.
            </p>

            <div class="quote">
                "I choose you."
            </div>

        </div>

        <button class="continue" onclick="futureChapter()">
            Continue through the future ✨
        </button>
    `);
}

/* =========================================================
   TREEHOUSE
========================================================= */

function treehouseScene() {

    addStar("treehouse");

    panel(`
        <div class="big-symbol">🌳</div>

        <h2>The Tree House</h2>

        <div class="story">

            <p>
                At the edge of the countryside is a huge old tree.
            </p>

            <p>
                And halfway up it is the tree house you've talked about.
            </p>

            <p>
                It isn't perfect.
            </p>

            <p>
                But it is yours.
            </p>

            <div class="quote">
                "Some dreams are small enough to build with your own hands."
            </div>

        </div>

        <button class="continue" onclick="futureChapter()">
            Keep exploring 🌳
        </button>
    `);
}

/* =========================================================
   COUNTRYSIDE
========================================================= */

function countrysideScene() {

    state.homeChoice = "countryside";

    panel(`
        <div class="countryside">

            <div class="sunset"></div>
            <div class="treehouse">🌳</div>
            <div class="house"></div>
            <div class="field"></div>

        </div>

        <h2>The Countryside</h2>

        <div class="story">

            <p>
                A little house sits among endless green fields.
            </p>

            <p>
                There is a garden outside.
            </p>

            <p>
                A tree house nearby.
            </p>

            <p>
                And a kitchen where you can dance together.
            </p>

            <p>
                This isn't some perfect fantasy.
            </p>

            <p>
                It's simply a life where you get to come home to each other.
            </p>

        </div>

        <button class="continue" onclick="marriedLifeScene()">
            See what life becomes 🏡
        </button>
    `);
}

function marriedLifeScene() {

    addStar("marriedlife");

    panel(`
        <div class="big-symbol">🏡</div>

        <h2>Our Ordinary Life</h2>

        <div class="story">

            <p>
                You wake up beside her.
            </p>

            <p>
                There is coffee in the kitchen.
            </p>

            <p>
                The windows look out over green fields.
            </p>

            <p>
                Sometimes you paint together.
            </p>

            <p>
                Sometimes you sing.
            </p>

            <p>
                Sometimes you dance around the kitchen.
            </p>

            <p>
                Sometimes you do absolutely nothing.
            </p>

            <p>
                And somehow, those are the happiest days.
            </p>

            <div class="quote">
                "Not because life is perfect.
                Because it's ours."
            </div>

        </div>

        <button class="continue" onclick="futureChoice()">
            Continue 💙
        </button>
    `);
}

function futureStudioScene() {

    panel(`
        <div class="big-symbol">🎨</div>

        <h2>The Little Studio</h2>

        <div class="story">

            <p>
                Two canvases sit beside each other.
            </p>

            <p>
                Yours.
                Hers.
            </p>

            <p>
                Paint covers the table.
            </p>

            <p>
                Music plays softly.
            </p>

            <p>
                You look over at Lola.
            </p>

            <div class="quote">
                "I think I could be happy here."
            </div>

        </div>

        <button class="continue" onclick="futureChapter()">
            Continue 🎨
        </button>
    `);
}

/* =========================================================
   FINAL FUTURE CHOICE
========================================================= */

function futureChoice() {

    panel(`
        <h2>The Life We Choose</h2>

        <div class="story">

            <p>
                The future asks you one final question.
            </p>

            <div class="quote">
                "What do you want most?"
            </div>

        </div>

        <div class="choices">

            ${choice(
                "💍 To marry her",
                "futureAnswer('marriage')"
            )}

            ${choice(
                "🏡 To build a home together",
                "futureAnswer('home')"
            )}

            ${choice(
                "🌳 To grow old together",
                "futureAnswer('forever')"
            )}

            ${choice(
                "💙 To simply be happy together",
                "futureAnswer('happy')"
            )}

        </div>
    `);
}

function futureAnswer(type) {

    panel(`
        <div class="big-symbol">💙</div>

        <h2>Maybe It's All Of Them</h2>

        <div class="story">

            <p>
                Maybe the answer was never just one thing.
            </p>

            <p>
                Maybe it's the wedding.
            </p>

            <p>
                The countryside.
            </p>

            <p>
                The tree house.
            </p>

            <p>
                The paintings.
            </p>

            <p>
                The songs.
            </p>

            <p>
                The dancing.
            </p>

            <p>
                The ordinary mornings.
            </p>

            <p>
                Growing older together.
            </p>

            <p>
                And being happy simply because you are together.
            </p>

            <div class="quote">
                "A future doesn't have to be perfect.
                It just has to be ours."
            </div>

        </div>

        <button class="continue" onclick="universeChapter()">
            Enter Our Universe 🌌
        </button>
    `);
}

/* =========================================================
   OUR UNIVERSE
========================================================= */

function universeChapter() {

    addStar("universe");

    panel(`
        <div class="big-symbol">🌌</div>

        <h2>Chapter Eight<br>Our Universe</h2>

        <div class="story">

            <p>
                The spaceship stops.
            </p>

            <p>
                There are no more planets to visit.
            </p>

            <p>
                No more doors.
            </p>

            <p>
                No more paths.
            </p>

            <p>
                You look around.
            </p>

            <p>
                And finally understand.
            </p>

            <div class="quote">
                "You weren't looking for a universe."
            </div>

            <div class="quote">
                "You were looking for home."
            </div>

            <p>
                Every star you've collected begins glowing.
            </p>

            <p>
                The planets disappear.
            </p>

            <p>
                Everything becomes one enormous galaxy.
            </p>

        </div>

        <button class="continue" onclick="galaxyReveal()">
            Watch the universe appear ✨
        </button>
    `);
}

/* =========================================================
   GALAXY REVEAL
========================================================= */

function galaxyReveal() {

    panel(`
        <div class="big-symbol">✨</div>

        <h2>27 Stars</h2>

        <div class="story">

            <p>
                Every little choice you made brought you here.
            </p>

            <p>
                Every memory.
                Every dream.
                Every tiny thing that makes you, you.
            </p>

            <p>
                And there are 27 stars waiting in the sky.
            </p>

        </div>

        <div class="constellation" id="constellation"></div>

        <button class="continue" onclick="finalLetter()">
            One final message 💙
        </button>
    `);

    const constellation = document.getElementById("constellation");

    for (let i = 1; i <= 27; i++) {

        const star = document.createElement("div");

        star.className =
            "collect-star " +
            (state.stars.size >= i ? "found" : "");

        star.textContent =
            state.stars.size >= i ? "⭐" : "·";

        constellation.appendChild(star);
    }
}

/* =========================================================
   FINAL LETTER
========================================================= */

function finalLetter() {

    panel(`
        <div class="final">

            <h2>For Lola</h2>

            <div class="final-letter">

                <p>
                    Lola,
                </p>

                <p>
                    If you've made it all the way here, then I suppose
                    there's only one thing left for me to tell you.
                </p>

                <p>
                    I am so incredibly proud of you.
                </p>

                <p>
                    More than I think I will ever know how to put into words.
                    I'm proud of the person you are, of the things you've
                    survived, of the things you've overcome, and of the person
                    you continue to become.
                </p>

                <p>
                    I'm proud of you for making it through the days that felt
                    impossible. I'm proud of the softness you've managed to
                    keep in a world that hasn't always been soft with you.
                </p>

                <p>
                    And more than anything, I hope you know that you never
                    have to become someone else to deserve love.
                </p>

                <p>
                    You are already enough.
                </p>

                <p>
                    You are my favourite person.
                </p>

                <p>
                    Not just one of my favourite people.
                    My favourite.
                </p>

                <p>
                    You have somehow become such a beautiful part of my life
                    that sometimes I don't know how I existed without you in it.
                    You are everything to me and somehow, at the same time,
                    you are still so much more than everything I could ever
                    put into a single word.
                </p>

                <p>
                    I don't just want the extraordinary moments with you.
                    I want the ordinary ones.
                </p>

                <p>
                    I want to dance with you in the kitchen for absolutely
                    no reason. I want to sing with you until we're laughing
                    because neither of us can remember the words.
                </p>

                <p>
                    I want to paint beside you, even if neither of us knows
                    what we're doing.
                </p>

                <p>
                    I want to sit somewhere quiet in the countryside with you
                    and watch the sun disappear.
                </p>

                <p>
                    I want that tree house we've talked about.
                </p>

                <p>
                    I want somewhere that feels like ours.
                </p>

                <p>
                    Somewhere surrounded by green fields and open skies,
                    where the nights are dark enough for us to see every star
                    above us.
                </p>

                <p>
                    I want to marry you.
                </p>

                <p>
                    I want the little house in the countryside.
                </p>

                <p>
                    I want the tree house and the green fields and the slow
                    mornings.
                </p>

                <p>
                    I want to wake up beside you and fall asleep knowing that
                    the person I love is right there.
                </p>

                <p>
                    I want us to grow older together and still find reasons
                    to laugh.
                </p>

                <p>
                    More than anything, I want a life where we are simply
                    happy together.
                </p>

                <p>
                    I want to see the ocean with you.
                </p>

                <p>
                    I want to stand beside you while the waves reach the shore
                    and finally watch you experience something you've dreamed
                    about.
                </p>

                <p>
                    I want photographs we haven't taken yet.
                    Songs we haven't sung yet.
                    Paintings we haven't made yet.
                    Places we haven't found yet.
                    Stories we haven't written yet.
                </p>

                <p>
                    I want all the little things we've imagined scattered
                    throughout our future.
                </p>

                <p>
                    And I want the things we haven't imagined yet, too.
                </p>

                <p>
                    Because that's the part that makes me happiest.
                </p>

                <p>
                    There is still so much life ahead of us that we haven't
                    even discovered.
                </p>

                <p>
                    So many sunsets.
                    So many nights beneath the stars.
                    So many ridiculous conversations.
                    So many moments where one of us will look at the other
                    and laugh because somehow this is our life.
                </p>

                <p>
                    And if I could ask the universe for anything, I wouldn't
                    ask for a perfect life.
                </p>

                <p>
                    I'd ask for a life where I get to keep finding you in it.
                </p>

                <p>
                    Because somewhere along the way, you became my favourite
                    place to return to.
                </p>

                <p>
                    My favourite voice.
                    My favourite person to talk to.
                    My favourite thought at the end of the day.
                    My favourite future to imagine.
                    And my favourite part of today.
                </p>

                <p>
                    I hope you never forget how loved you are.
                </p>

                <p>
                    Not only on your birthday.
                    Not only when everything is beautiful.
                    But on the ordinary days.
                    On the difficult days.
                    On the days when you don't feel particularly lovable.
                </p>

                <p>
                    Especially then.
                </p>

                <p>
                    I will still look at you and see you.
                    Not some perfect version of you.
                    Just you.
                </p>

                <p>
                    And I will still think you are extraordinary.
                </p>

                <p>
                    So here's to 27.
                </p>

                <p>
                    Here's to everything you've already survived.
                    Everything you've already become.
                    And everything you haven't become yet.
                </p>

                <p>
                    Here's to the countryside.
                    The tree house.
                    The paintings.
                    The songs.
                    The dancing.
                    The ocean.
                    The stars.
                    The stingrays.
                    The quiet mornings.
                    The ridiculous nights.
                    The future we keep imagining.
                    And every little thing in between.
                </p>

                <p>
                    I don't know exactly where life will take us.
                </p>

                <p>
                    But I know what I hope is waiting somewhere along the road.
                </p>

                <p>
                    You and me.
                </p>

                <p>
                    Still talking.
                    Still laughing.
                    Still dreaming.
                    Still finding new reasons to love each other.
                </p>

                <p>
                    And maybe one day, we'll look back at this little universe
                    and laugh at how small our dreams seemed compared to
                    everything we actually got to experience.
                </p>

                <p>
                    Until then, I'll keep dreaming with you.
                    I'll keep writing about you.
                    I'll keep loving you.
                </p>

                <p>
                    And I'll keep reminding you, whenever you forget,
                    just how proud I am of the person you are.
                </p>

                <p>
                    Happy 27th birthday, my love.
                </p>

                <p>
                    You are my favourite person.
                    You are everything.
                    And somehow, you are still so much more.
                </p>

                <p>
                    If there are a million galaxies above us,
                    I hope you know that I'd still look for you.
                </p>

                <p>
                    Because no matter how enormous the universe becomes,
                </p>

                <div class="quote">
                    I'd always find my way home to you.
                </div>

                <p>
                    — Bree
                </p>

            </div>

            <button class="continue" onclick="starReveal()">
                There's one last star ⭐
            </button>

        </div>
    `);
}

/* =========================================================
   REAL STAR REVEAL
========================================================= */

function starReveal() {

    panel(`
        <div class="real-star">

            <div class="star">⭐</div>

            <h2>Your Star</h2>

            <div class="story">

                <p>
                    You made it to the end.
                </p>

                <p>
                    And there is one star that was never meant to be
                    found inside this game.
                </p>

                <p>
                    Because this one exists outside of the screen.
                </p>

                <p>
                    I bought you a star.
                </p>

                <p>
                    A real little piece of the universe that gets to have
                    your name attached to it.
                </p>

                <div class="quote">
                    "Of all the stars in the sky,
                    somehow you became mine."
                </div>

                <p>
                    Happy 27th birthday, Lola.
                </p>

                <p>
                    Welcome to your universe.
                </p>

                <p>
                    And if you ever look up at the night sky,
                    remember that somewhere among all those lights,
                    there is one that belongs to you.
                </p>

                <p style="text-align:center;font-size:24px;">
                    💙🌌⭐
                </p>

            </div>

        </div>
    `);
}

/* =========================================================
   START
========================================================= */

startGame();

</script>

</body>
</html>
