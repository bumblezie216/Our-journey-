<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Lola's Little Universe</title>

<style>
/* =========================================================
   LOLA'S LITTLE UNIVERSE
   Interactive birthday adventure
   ========================================================= */

* {
    box-sizing: border-box;
}

html,
body {
    margin: 0;
    padding: 0;
    width: 100%;
    min-height: 100%;
    font-family: Georgia, "Times New Roman", serif;
    background: #030205;
    color: #fff;
    overflow-x: hidden;
}

body {
    min-height: 100vh;
}

/* ---------------------------------------------------------
   GALAXY BACKGROUND
   --------------------------------------------------------- */

#space {
    position: fixed;
    inset: 0;
    z-index: 0;
    overflow: hidden;
    background:
        radial-gradient(circle at 20% 20%, rgba(105, 0, 40, .22), transparent 28%),
        radial-gradient(circle at 80% 70%, rgba(80, 0, 35, .20), transparent 30%),
        radial-gradient(circle at 50% 50%, rgba(120, 0, 55, .10), transparent 45%),
        #020204;
}

.nebula {
    position: absolute;
    width: 55vw;
    height: 55vw;
    border-radius: 50%;
    filter: blur(70px);
    opacity: .18;
    pointer-events: none;
}

.nebula.one {
    background: #75002d;
    left: -20vw;
    top: 10vh;
}

.nebula.two {
    background: #42001d;
    right: -20vw;
    bottom: 0;
}

.star-bg {
    position: absolute;
    width: 2px;
    height: 2px;
    border-radius: 50%;
    background: white;
    opacity: .75;
    animation: twinkle 3s infinite ease-in-out;
}

@keyframes twinkle {
    0%, 100% { opacity: .25; transform: scale(.8); }
    50% { opacity: 1; transform: scale(1.5); }
}

/* ---------------------------------------------------------
   SHOOTING STARS
   --------------------------------------------------------- */

.shooting-star {
    position: absolute;
    width: 120px;
    height: 2px;
    background: linear-gradient(
        90deg,
        rgba(255,255,255,0),
        rgba(255,255,255,.95)
    );
    transform: rotate(-35deg);
    opacity: 0;
    pointer-events: none;
    animation: shoot 4s linear infinite;
}

.shooting-star::after {
    content: "";
    position: absolute;
    right: 0;
    top: -2px;
    width: 6px;
    height: 6px;
    background: white;
    border-radius: 50%;
    box-shadow: 0 0 10px white, 0 0 20px #b0004d;
}

.shooting-star:nth-child(4) {
    animation-delay: 1.5s;
    left: 20%;
    top: 5%;
}

.shooting-star:nth-child(5) {
    animation-delay: 3s;
    left: 65%;
    top: 15%;
}

.shooting-star:nth-child(6) {
    animation-delay: .5s;
    left: 80%;
    top: 45%;
}

.shooting-star:nth-child(7) {
    animation-delay: 2.2s;
    left: 40%;
    top: 60%;
}

@keyframes shoot {
    0% {
        opacity: 0;
        transform: translate(0,0) rotate(-35deg);
    }

    10% {
        opacity: 1;
    }

    35% {
        opacity: 0;
        transform: translate(-420px,420px) rotate(-35deg);
    }

    100% {
        opacity: 0;
    }
}

/* ---------------------------------------------------------
   GAME UI
   --------------------------------------------------------- */

#game {
    position: relative;
    z-index: 2;
    min-height: 100vh;
}

header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 65px;
    z-index: 20;

    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 0 18px;

    background: rgba(3,0,3,.82);
    border-bottom: 1px solid rgba(170,0,70,.45);
    backdrop-filter: blur(12px);
}

.logo {
    font-size: 15px;
    letter-spacing: 2px;
    color: #ffb3cf;
}

.progress {
    font-size: 13px;
    color: #e7c3d0;
}

.progress span {
    color: #ff6fa7;
    font-weight: bold;
}

#screen {
    min-height: 100vh;
    padding: 95px 18px 50px;
    display: flex;
    justify-content: center;
    align-items: flex-start;
}

.panel {
    width: min(900px, 100%);
    background:
        linear-gradient(
            145deg,
            rgba(60,0,28,.82),
            rgba(8,4,9,.91)
        );

    border: 1px solid rgba(180,0,75,.48);
    box-shadow:
        0 0 50px rgba(100,0,45,.25),
        inset 0 0 40px rgba(100,0,45,.08);

    border-radius: 24px;
    padding: 30px 22px;
    animation: appear .7s ease;
}

@keyframes appear {
    from {
        opacity: 0;
        transform: translateY(18px) scale(.98);
    }

    to {
        opacity: 1;
        transform: translateY(0) scale(1);
    }
}

h1,
h2,
h3 {
    text-align: center;
}

h1 {
    font-size: clamp(34px, 8vw, 68px);
    margin: 10px 0;
    color: #fff0f6;
    text-shadow: 0 0 25px rgba(220,0,90,.55);
}

h2 {
    font-size: clamp(25px, 5vw, 42px);
    color: #ffd4e4;
}

h3 {
    color: #ff83b2;
}

.subtitle {
    text-align: center;
    color: #d9b7c5;
    line-height: 1.8;
    font-size: 17px;
    max-width: 680px;
    margin: 18px auto;
}

.quote {
    text-align: center;
    color: #ffb6d0;
    font-style: italic;
    font-size: 20px;
    line-height: 1.7;
    margin: 30px auto;
    max-width: 650px;
}

button {
    display: block;
    width: min(620px, 100%);
    margin: 12px auto;

    padding: 15px 20px;

    border-radius: 15px;
    border: 1px solid rgba(255,110,165,.45);

    background:
        linear-gradient(
            135deg,
            rgba(110,0,48,.85),
            rgba(45,0,22,.9)
        );

    color: white;
    font-family: inherit;
    font-size: 16px;

    cursor: pointer;

    transition:
        transform .2s ease,
        box-shadow .2s ease,
        background .2s ease;
}

button:hover {
    transform: translateY(-3px);
    box-shadow:
        0 8px 25px rgba(160,0,75,.3),
        0 0 20px rgba(200,0,90,.15);

    background:
        linear-gradient(
            135deg,
            rgba(145,0,62,.9),
            rgba(65,0,30,.95)
        );
}

button:active {
    transform: scale(.97);
}

.small-button {
    width: auto;
    display: inline-block;
    margin: 8px;
    padding: 11px 17px;
}

/* ---------------------------------------------------------
   GALAXY MAP
   --------------------------------------------------------- */

.map {
    position: relative;
    width: 100%;
    min-height: 620px;
    overflow: hidden;
    border-radius: 22px;

    background:
        radial-gradient(circle at 50% 50%, rgba(140,0,65,.16), transparent 28%),
        radial-gradient(circle at 30% 70%, rgba(80,0,40,.12), transparent 25%),
        #030205;

    border: 1px solid rgba(170,0,70,.35);
}

.map-title {
    position: absolute;
    z-index: 5;
    top: 20px;
    left: 0;
    right: 0;
    text-align: center;
}

.map-title h2 {
    margin: 0;
}

.map-title p {
    color: #bda2ad;
    font-size: 13px;
}

.sun {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);

    width: 95px;
    height: 95px;
    border-radius: 50%;

    background:
        radial-gradient(circle at 35% 30%, #fff1c9, #d29b32 45%, #8d4315);

    box-shadow:
        0 0 25px #d58c2e,
        0 0 70px rgba(180,90,20,.45);

    display: flex;
    align-items: center;
    justify-content: center;

    font-size: 12px;
    color: #210d00;
    font-weight: bold;
}

.planet {
    position: absolute;

    border-radius: 50%;

    display: flex;
    align-items: center;
    justify-content: center;

    cursor: pointer;

    border: 2px solid rgba(255,255,255,.2);

    color: white;
    font-size: 11px;
    text-align: center;

    box-shadow:
        0 0 18px rgba(170,0,70,.35);

    transition:
        transform .25s ease,
        filter .25s ease,
        box-shadow .25s ease;
}

.planet:hover {
    transform: scale(1.15);
    filter: brightness(1.25);
    box-shadow:
        0 0 25px rgba(255,70,140,.55),
        0 0 50px rgba(160,0,75,.3);
}

.planet.locked {
    filter: grayscale(1);
    opacity: .35;
    cursor: not-allowed;
}

.planet.done {
    box-shadow:
        0 0 22px rgba(255,120,170,.7),
        0 0 50px rgba(180,0,80,.35);
}

.p1 {
    width: 68px;
    height: 68px;
    left: 8%;
    top: 18%;
    background: radial-gradient(circle at 35% 30%, #8a552c, #32170e);
}

.p2 {
    width: 78px;
    height: 78px;
    left: 22%;
    top: 63%;
    background: radial-gradient(circle at 35% 30%, #563c91, #17102d);
}

.p3 {
    width: 74px;
    height: 74px;
    left: 35%;
    top: 17%;
    background: radial-gradient(circle at 35% 30%, #315d89, #0b1728);
}

.p4 {
    width: 88px;
    height: 88px;
    right: 27%;
    top: 65%;
    background: radial-gradient(circle at 35% 30%, #a71e52, #360617);
}

.p5 {
    width: 72px;
    height: 72px;
    right: 8%;
    top: 20%;
    background: radial-gradient(circle at 35% 30%, #5b7d9a, #14202c);
}

.p6 {
    width: 84px;
    height: 84px;
    right: 12%;
    top: 62%;
    background: radial-gradient(circle at 35% 30%, #c9b09a, #5c3928);
}

.p7 {
    width: 64px;
    height: 64px;
    left: 48%;
    top: 8%;
    background: radial-gradient(circle at 35% 30%, #7c4f96, #28102f);
}

.p8 {
    width: 80px;
    height: 80px;
    left: 7%;
    top: 80%;
    background: radial-gradient(circle at 35% 30%, #4c9168, #112c1b);
}

.p9 {
    width: 78px;
    height: 78px;
    right: 45%;
    top: 82%;
    background: radial-gradient(circle at 35% 30%, #b789bd, #3b183f);
}

.p10 {
    width: 85px;
    height: 85px;
    right: 3%;
    top: 42%;
    background: radial-gradient(circle at 35% 30%, #b07d4e, #392010);
}

/* ---------------------------------------------------------
   SPACESHIP
   --------------------------------------------------------- */

.ship {
    position: absolute;
    z-index: 4;

    width: 46px;
    height: 28px;

    background: linear-gradient(135deg, #fff, #c8c8d4);
    border-radius: 50% 60% 60% 30%;

    box-shadow:
        0 0 10px white,
        0 0 25px rgba(255,255,255,.5);

    transition:
        left 1s ease,
        top 1s ease;
}

.ship::before {
    content: "";
    position: absolute;
    width: 14px;
    height: 14px;
    left: 15px;
    top: 6px;
    border-radius: 50%;
    background: #8d0d43;
}

.ship::after {
    content: "";
    position: absolute;
    right: -18px;
    top: 10px;
    width: 20px;
    height: 7px;
    background: linear-gradient(90deg, #ff7eae, transparent);
    border-radius: 50%;
}

/* ---------------------------------------------------------
   HIDDEN STARS
   --------------------------------------------------------- */

.hidden-star {
    position: absolute;
    z-index: 10;

    width: 22px;
    height: 22px;

    display: flex;
    align-items: center;
    justify-content: center;

    color: #fff;
    font-size: 17px;

    cursor: pointer;

    animation:
        hiddenTwinkle 1.8s infinite ease-in-out;

    filter:
        drop-shadow(0 0 5px white)
        drop-shadow(0 0 10px #ff3d87);
}

.hidden-star:hover {
    transform: scale(1.4);
}

@keyframes hiddenTwinkle {
    0%, 100% {
        opacity: .35;
        transform: scale(.85);
    }

    50% {
        opacity: 1;
        transform: scale(1.15);
    }
}

.star-collected {
    animation: collectStar .7s ease forwards;
}

@keyframes collectStar {
    0% {
        transform: scale(1);
        opacity: 1;
    }

    50% {
        transform: scale(2);
        opacity: 1;
    }

    100% {
        transform: scale(0);
        opacity: 0;
    }
}

/* ---------------------------------------------------------
   STORY SCENES
   --------------------------------------------------------- */

.scene {
    position: relative;
    min-height: 430px;
    overflow: hidden;
    border-radius: 20px;
    padding: 25px;

    background:
        radial-gradient(circle at 50% 30%, rgba(160,0,75,.18), transparent 35%),
        #050306;

    border: 1px solid rgba(160,0,70,.3);
}

.scene p {
    color: #dfc8d1;
    line-height: 1.8;
    font-size: 17px;
}

.memory {
    text-align: center;
    padding: 25px;
    margin: 20px 0;

    border-left: 2px solid #a6004a;

    background: rgba(100,0,45,.10);
    color: #ffc9dc;
    font-style: italic;
    line-height: 1.8;
}

/* ---------------------------------------------------------
   OCEAN
   --------------------------------------------------------- */

.ocean {
    position: relative;
    height: 430px;
    overflow: hidden;
    border-radius: 20px;

    background:
        linear-gradient(
            to bottom,
            #07030a 0%,
            #180719 35%,
            #21092a 60%,
            #050b18 100%
        );
}

.moon {
    position: absolute;
    width: 85px;
    height: 85px;
    border-radius: 50%;
    right: 12%;
    top: 10%;

    background: #fff5fa;
    box-shadow: 0 0 35px rgba(255,255,255,.55);
}

.wave {
    position: absolute;
    left: -10%;
    bottom: -40px;
    width: 120%;
    height: 160px;

    background:
        radial-gradient(
            ellipse at 50% 0%,
            #3b0e46,
            #0a1025 70%
        );

    border-radius: 50% 50% 0 0;
}

.stingray {
    position: absolute;
    font-size: 45px;
    animation: swim 9s linear infinite;
}

@keyframes swim {
    from {
        left: -100px;
        transform: translateY(0) rotate(-5deg);
    }

    50% {
        transform: translateY(-30px) rotate(5deg);
    }

    to {
        left: calc(100% + 100px);
        transform: translateY(10px) rotate(-4deg);
    }
}

/* ---------------------------------------------------------
   WEDDING
   --------------------------------------------------------- */

.wedding {
    position: relative;
    min-height: 430px;
    overflow: hidden;
    border-radius: 20px;

    background:
        radial-gradient(
            circle at 50% 35%,
            rgba(255,180,210,.16),
            transparent 25%
        ),
        linear-gradient(
            180deg,
            #1d0714,
            #050306
        );
}

.petals {
    position: absolute;
    inset: 0;
    overflow: hidden;
}

.petal {
    position: absolute;
    top: -30px;
    width: 10px;
    height: 15px;
    border-radius: 70% 30% 70% 30%;
    background: #d67a9a;
    opacity: .7;
    animation: fall 7s linear infinite;
}

@keyframes fall {
    to {
        transform:
            translateY(500px)
            rotate(360deg);
        opacity: 0;
    }
}

/* ---------------------------------------------------------
   COUNTRYSIDE
   --------------------------------------------------------- */

.countryside {
    position: relative;
    min-height: 430px;
    overflow: hidden;
    border-radius: 20px;

    background:
        linear-gradient(
            #160711 0%,
            #3c1726 48%,
            #193c27 49%,
            #07190e 100%
        );
}

.sunset {
    position: absolute;
    width: 100px;
    height: 100px;
    border-radius: 50%;
    top: 60px;
    left: 15%;
    background: #ffb08c;
    box-shadow: 0 0 50px #ff8a7b;
}

.house {
    position: absolute;
    bottom: 90px;
    left: 50%;
    transform: translateX(-50%);
    width: 150px;
    height: 100px;
    background: #513026;
    border: 2px solid #8e5d4b;
}

.house::before {
    content: "";
    position: absolute;
    top: -65px;
    left: -20px;
    border-left: 95px solid transparent;
    border-right: 95px solid transparent;
    border-bottom: 70px solid #2a0c19;
}

.tree {
    position: absolute;
    bottom: 80px;
    right: 10%;
    font-size: 100px;
}

/* ---------------------------------------------------------
   FINAL LETTER
   --------------------------------------------------------- */

.letter {
    max-height: 65vh;
    overflow-y: auto;

    padding: 25px;

    background: rgba(255,255,255,.025);
    border: 1px solid rgba(255,100,160,.18);
    border-radius: 18px;

    line-height: 1.9;
    color: #ead5dd;
    font-size: 17px;
}

.letter p {
    margin: 0 0 20px;
}

.signature {
    text-align: right;
    color: #ff8db8;
    font-size: 22px;
    font-style: italic;
}

/* ---------------------------------------------------------
   CONSTELLATION
   --------------------------------------------------------- */

.constellation {
    position: relative;
    width: 100%;
    max-width: 650px;
    height: 430px;
    margin: auto;

    background:
        radial-gradient(circle, rgba(160,0,70,.14), transparent 50%),
        #020204;

    border-radius: 20px;
    border: 1px solid rgba(180,0,75,.35);
}

.constellation-star {
    position: absolute;
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: white;

    box-shadow:
        0 0 8px white,
        0 0 18px #ff4d91;
}

.constellation-line {
    position: absolute;
    height: 1px;
    background: rgba(255,160,195,.4);
    transform-origin: left center;
}

/* ---------------------------------------------------------
   RESPONSIVE
   --------------------------------------------------------- */

@media (max-width: 650px) {

    header {
        height: 58px;
    }

    .logo {
        font-size: 12px;
    }

    .progress {
        font-size: 11px;
    }

    #screen {
        padding: 80px 10px 30px;
    }

    .panel {
        padding: 22px 14px;
        border-radius: 18px;
    }

    .map {
        min-height: 600px;
    }

    .planet {
        transform: scale(.85);
    }

    .planet:hover {
        transform: scale(.95);
    }

    .letter {
        font-size: 16px;
    }
}
</style>
</head>

<body>

<div id="space">
    <div class="nebula one"></div>
    <div class="nebula two"></div>

    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
</div>

<div id="game">

<header>
    <div class="logo">LOLA'S LITTLE UNIVERSE ✦</div>

    <div class="progress">
        Stars:
        <span id="starCount">0</span>/27
    </div>
</header>

<main id="screen"></main>

</div>

<script>

/* =========================================================
   GAME STATE
   ========================================================= */

const state = {

    stars: JSON.parse(localStorage.getItem("lolaStars") || "[]"),

    unlocked: JSON.parse(
        localStorage.getItem("lolaPlanets") ||
        JSON.stringify([
            "beginning",
            "coffee",
            "observatory"
        ])
    ),

    completed: JSON.parse(
        localStorage.getItem("lolaCompleted") || "[]"
    ),

    choices: {},

    currentPlanet: null
};

const screen = document.getElementById("screen");
const starCount = document.getElementById("starCount");

function saveGame() {

    localStorage.setItem(
        "lolaStars",
        JSON.stringify(state.stars)
    );

    localStorage.setItem(
        "lolaPlanets",
        JSON.stringify(state.unlocked)
    );

    localStorage.setItem(
        "lolaCompleted",
        JSON.stringify(state.completed)
    );
}

function updateHUD() {

    starCount.textContent = state.stars.length;
}

function hasStar(id) {

    return state.stars.includes(id);
}

function collectStar(id, element) {

    if (hasStar(id)) return;

    state.stars.push(id);

    saveGame();
    updateHUD();

    if (element) {

        element.classList.add("star-collected");

        setTimeout(() => {
            element.remove();
        }, 700);
    }
}

function unlock(id) {

    if (!state.unlocked.includes(id)) {

        state.unlocked.push(id);
        saveGame();
    }
}

function complete(id) {

    if (!state.completed.includes(id)) {

        state.completed.push(id);
        saveGame();
    }
}

function isComplete(id) {

    return state.completed.includes(id);
}

updateHUD();


/* =========================================================
   HELPERS
   ========================================================= */

function panel(html) {

    screen.innerHTML = `
        <div class="panel">
            ${html}
        </div>
    `;
}

function button(text, action, disabled = false) {

    return `
        <button
            ${disabled ? "disabled" : ""}
            onclick="${action}"
        >
            ${text}
        </button>
    `;
}

function star(id, x, y) {

    if (hasStar(id)) return "";

    return `
        <div
            class="hidden-star"
            style="left:${x}%;top:${y}%"
            onclick="collectStar('${id}', this)"
            title="A hidden star"
        >
            ✦
        </div>
    `;
}

function transition(fn) {

    screen.style.opacity = "0";

    setTimeout(() => {

        fn();

        screen.style.opacity = "1";

    }, 250);
}


/* =========================================================
   INTRO
   ========================================================= */

function startGame() {

    panel(`
        <h1>Lola's Little Universe</h1>

        <p class="subtitle">
            Somewhere between the stars, the ocean and all
            the little pieces of a life that haven't happened yet,
            there is a universe waiting for you.
        </p>

        <div class="quote">
            "There are billions of stars in the sky.<br>
            Somehow, I still found you."
        </div>

        ${button(
            "✦ Begin the adventure",
            "transition(prologue)"
        )}

        ${button(
            "↩ Continue my journey",
            "transition(galaxyMap)"
        )}

        <p style="
            text-align:center;
            color:#98727f;
            font-size:13px;
            margin-top:25px;
        ">
            Your collected stars are saved automatically.
        </p>
    `);
}


/* =========================================================
   PROLOGUE
   ========================================================= */

function prologue() {

    panel(`
        <h2>Prologue — The Beginning</h2>

        <div class="scene">

            ${star("s1", 12, 18)}

            <p>
                Lola opens her eyes.
            </p>

            <p>
                There is no ceiling above her.
                No walls.
                No floor she recognises.
            </p>

            <p>
                Only an enormous black sky filled with stars.
            </p>

            <p>
                A tiny spaceship rests beside her.
                Its little window glows burgundy.
            </p>

            <div class="memory">
                On the screen inside it, three words are waiting:
                <br><br>
                <strong>Find your universe.</strong>
            </div>

            <p>
                Three paths appear in the distance.
            </p>

        </div>

        ${button(
            "🚀 Take the spaceship",
            "transition(openingShip)"
        )}

        ${button(
            "✨ Follow the stars",
            "transition(openingStars)"
        )}

        ${button(
            "🌊 Follow the sound of waves",
            "transition(openingOcean)"
        )}
    `);
}

function openingShip() {

    unlock("storm");

    panel(`
        <h2>The Little Spaceship</h2>

        <div class="scene">

            ${star("s2", 80, 17)}

            <p>
                Lola climbs into the spaceship.
            </p>

            <p>
                It feels strangely familiar, even though
                she has never seen it before.
            </p>

            <p>
                On the dashboard is a tiny handwritten note.
            </p>

            <div class="memory">
                "If you ever get lost,
                follow the person who makes the universe
                feel a little less frightening."
            </div>

        </div>

        ${button(
            "Continue",
            "transition(galaxyMap)"
        )}
    `);
}

function openingStars() {

    unlock("hazel");

    panel(`
        <h2>Follow the Stars</h2>

        <div class="scene">

            ${star("s3", 68, 22)}

            <p>
                Lola follows the brightest stars.
            </p>

            <p>
                The farther she walks, the more the stars
                begin to resemble tiny memories.
            </p>

            <div class="memory">
                A voice.<br>
                A laugh.<br>
                Someone talking about the future.<br>
                Someone who writes when feelings become
                too big for ordinary words.
            </div>

            <p>
                Somewhere ahead, there is a girl she hasn't met
                in this strange little universe yet.
            </p>

        </div>

        ${button(
            "Continue",
            "transition(galaxyMap)"
        )}
    `);
}

function openingOcean() {

    unlock("ocean");

    panel(`
        <h2>The Sound of the Ocean</h2>

        <div class="ocean">

            ${star("s4", 23, 25)}

            <div class="moon"></div>

            <div class="wave"></div>

            <div class="stingray"
                 style="top:58%;animation-delay:-2s">
                🐟
            </div>

            <div class="stingray"
                 style="top:72%;animation-delay:-6s;font-size:30px">
                🐟
            </div>

        </div>

        <p class="quote">
            "She wants to see the ocean someday."
        </p>

        ${button(
            "Enter the galaxy",
            "transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   GALAXY MAP
   ========================================================= */

function galaxyMap() {

    const planets = [

        ["beginning", "Beginning", "p1"],
        ["coffee", "Coffee", "p2"],
        ["observatory", "Stars", "p3"],
        ["storm", "Storm", "p4"],
        ["hazel", "Hazel", "p5"],
        ["colour", "Colours", "p6"],
        ["gravity", "Gravity", "p7"],
        ["ocean", "Ocean", "p8"],
        ["sunset", "Sunset", "p9"],
        ["future", "Future", "p10"]
    ];

    let planetHTML = "";

    planets.forEach(([id, name, cls]) => {

        const locked = !state.unlocked.includes(id);
        const done = isComplete(id);

        planetHTML += `
            <div
                class="planet ${cls}
                ${locked ? "locked" : ""}
                ${done ? "done" : ""}"
                onclick="${
                    locked
                    ? `lockedMessage('${name}')`
                    : `travel('${id}')`
                }"
            >
                ${done ? "✓ " : ""}${name}
            </div>
        `;
    });

    let shipPosition = {
        left: "47%",
        top: "49%"
    };

    if (state.currentPlanet === "coffee")
        shipPosition = {left:"23%",top:"66%"};

    if (state.currentPlanet === "ocean")
        shipPosition = {left:"8%",top:"82%"};

    if (state.currentPlanet === "future")
        shipPosition = {left:"5%",top:"44%"};

    panel(`

        <h2>🌌 The Galaxy</h2>

        <p class="subtitle">
            Your spaceship is waiting.
            Choose a planet to explore.
        </p>

        <div class="map">

            <div class="map-title">
                <p>
                    Explore the planets. Find the hidden stars.
                </p>
            </div>

            <div class="sun">OUR<br>UNIVERSE</div>

            <div
                class="ship"
                style="
                    left:${shipPosition.left};
                    top:${shipPosition.top};
                "
            ></div>

            ${planetHTML}

        </div>

        <p class="subtitle">
            ✦ ${state.stars.length}/27 stars found
        </p>

        ${
            state.stars.length >= 27
            ? button(
                "🌌 Enter Our Universe",
                "transition(universeChapter)"
            )
            : ""
        }

    `);
}

function lockedMessage(name) {

    alert(
        `${name} is still hidden.\n\n`
        + `Explore the other planets first.`
    );
}

function travel(id) {

    state.currentPlanet = id;

    transition(() => {

        switch(id) {

            case "beginning":
                beginningPlanet();
                break;

            case "coffee":
                coffeePlanet();
                break;

            case "observatory":
                observatoryPlanet();
                break;

            case "storm":
                stormPlanet();
                break;

            case "hazel":
                hazelPlanet();
                break;

            case "colour":
                colourPlanet();
                break;

            case "gravity":
                gravityPlanet();
                break;

            case "ocean":
                oceanPlanet();
                break;

            case "sunset":
                sunsetPlanet();
                break;

            case "future":
                futurePlanet();
                break;

            default:
                galaxyMap();
        }

    });
}


/* =========================================================
   PLANET 1 — BEGINNING
   ========================================================= */

function beginningPlanet() {

    panel(`
        <h2>Planet I — The Beginning</h2>

        <div class="scene">

            ${star("s5", 18, 70)}

            <p>
                The first planet is quiet.
            </p>

            <p>
                There are no grand monuments here.
                No impossible cities.
                No great mysteries.
            </p>

            <p>
                Just the beginning.
            </p>

            <div class="memory">
                Every love story begins somewhere.
                Sometimes it begins with a conversation.
                Sometimes a laugh.
                Sometimes with two people
                who don't realise yet how important
                they are going to become to each other.
            </div>

        </div>

        ${button(
            "Leave the planet",
            "unlock('coffee'); transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 2 — COFFEE
   ========================================================= */

function coffeePlanet() {

    panel(`
        <h2>Planet II — Black Coffee</h2>

        <div class="scene">

            ${star("s6", 77, 20)}
            ${star("s7", 34, 77)}

            <p>
                Lola lands somewhere that smells like coffee.
            </p>

            <p>
                There is one tiny café floating in the middle
                of the galaxy.
            </p>

            <div class="memory">
                Black coffee.
                No sugar.
                Somehow exactly right.
            </div>

            <p>
                A cup sits on the table with a message beneath it:
            </p>

            <div class="quote">
                "Someone out there knows your favourite things."
            </div>

        </div>

        ${button(
            "☕ Sit and drink the coffee",
            "coffeeChoice('coffee')"
        )}

        ${button(
            "🔭 Look through the window",
            "coffeeChoice('window')"
        )}

        ${button(
            "🚀 Return to the galaxy",
            "transition(galaxyMap)"
        )}
    `);
}

function coffeeChoice(choice) {

    state.choices.coffee = choice;

    let text = choice === "coffee"
        ? `
            You sit quietly with the coffee.
            <br><br>
            It tastes like comfort.
            Like one of those ordinary moments
            you would want to share with someone you love.
        `
        : `
            You look through the window.
            <br><br>
            Far away, a tiny blue planet shines.
            You don't know it yet, but you'll eventually
            find something important there.
        `;

    unlock("observatory");

    panel(`
        <h2>The Little Things</h2>

        <div class="memory">
            ${text}
        </div>

        ${button(
            "Continue",
            "transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 3 — OBSERVATORY
   ========================================================= */

function observatoryPlanet() {

    panel(`
        <h2>Planet III — The Observatory</h2>

        <div class="scene">

            ${star("s8", 25, 22)}
            ${star("s9", 74, 68)}

            <p>
                The next planet is covered in observatories.
            </p>

            <p>
                Every telescope points towards the same
                distant galaxy.
            </p>

            <p>
                When Lola looks through one,
                she sees fragments of a story.
            </p>

            <div class="memory">
                She likes sunsets.<br>
                She writes poetry.<br>
                She talks about a tree house.<br>
                She wants a life in the countryside.<br>
                And somewhere in all of it,
                she keeps saying one name.
            </div>

            <p class="quote">
                Lola.
            </p>

        </div>

        ${button(
            "Look closer",
            "transition(girlBehindStars)"
        )}

        ${button(
            "Return to the galaxy",
            "transition(galaxyMap)"
        )}
    `);
}

function girlBehindStars() {

    unlock("storm");
    unlock("hazel");

    panel(`
        <h2>The Girl Behind the Stars</h2>

        <div class="scene">

            ${star("s10", 54, 18)}

            <p>
                The telescope focuses.
            </p>

            <p>
                For the first time, Lola sees her.
            </p>

            <div class="memory">
                Brown eyes.<br>
                Brown hair.<br>
                Two tattoo sleeves.<br>
                A love for sunsets.<br>
                A ridiculous amount of poetry.
            </div>

            <p>
                The girl smiles at something on her screen.
            </p>

            <p>
                And Lola somehow knows:
            </p>

            <div class="quote">
                "This is Bree."
            </div>

        </div>

        ${button(
            "Find out what happens next",
            "transition(stormPlanet)"
        )}

        ${button(
            "Return to the galaxy",
            "transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 4 — STORM
   ========================================================= */

function stormPlanet() {

    panel(`
        <h2>Planet IV — The Storm</h2>

        <div class="scene">

            ${star("s11", 83, 17)}
            ${star("s12", 21, 58)}

            <p>
                Suddenly, thunder cracks across the sky.
            </p>

            <p>
                The spaceship shakes.
            </p>

            <p>
                The stars disappear behind dark clouds.
            </p>

            <div class="memory">
                Someone is frightened by storms.
                She covers her face.
                She counts to ten.
                And somewhere far away,
                another girl stays on the phone with her.
            </div>

        </div>

        ${button(
            "❤️ Stay with her",
            "stormChoice('stay')"
        )}

        ${button(
            "⚡ Fly through the storm",
            "stormChoice('fly')"
        )}

        ${button(
            "✨ Follow the little light",
            "stormChoice('light')"
        )}
    `);
}

function stormChoice(choice) {

    state.choices.storm = choice;

    let outcome = {

        stay: `
            You don't try to make the storm disappear.
            You simply stay.
            <br><br>
            Sometimes love isn't fixing the thunder.
            Sometimes it's making sure someone doesn't
            have to face it alone.
        `,

        fly: `
            You grip the controls and fly forward.
            <br><br>
            The storm roars around you,
            but eventually the clouds break.
            <br><br>
            On the other side is a sky full of stars.
        `,

        light: `
            You follow a tiny burgundy light.
            <br><br>
            It leads you safely through the storm.
            <br><br>
            Beneath it is a message:
            <br><br>
            <strong>
            "You don't have to be brave all by yourself."
            </strong>
        `
    }[choice];

    unlock("hazel");
    unlock("gravity");

    panel(`
        <h2>After the Storm</h2>

        <div class="memory">
            ${outcome}
        </div>

        ${button(
            "Continue",
            "transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 5 — HAZEL EYES
   ========================================================= */

function hazelPlanet() {

    panel(`
        <h2>Planet V — Hazel</h2>

        <div class="scene">

            ${star("s13", 15, 20)}
            ${star("s14", 80, 74)}

            <p>
                The planet changes colour every time
                Lola looks around.
            </p>

            <p>
                Gold.
                Green.
                Brown.
                Amber.
            </p>

            <p>
                The colours move like sunlight through trees.
            </p>

            <div class="quote">
                Hazel eyes.
            </div>

            <p>
                A tiny note appears:
            </p>

            <div class="memory">
                "Some people have eyes.
                Some people have little galaxies in them."
            </div>

        </div>

        ${button(
            "Keep exploring",
            "unlock('colour'); transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 6 — COLOURS
   ========================================================= */

function colourPlanet() {

    panel(`
        <h2>Planet VI — Two Colours</h2>

        <div class="scene">

            ${star("s15", 72, 20)}
            ${star("s16", 28, 72)}

            <p>
                Two moons appear above the planet.
            </p>

            <div class="quote">
                Baby blue.<br>
                Burgundy.
            </div>

            <p>
                One belongs to Lola.
                One belongs to Bree.
            </p>

            <p>
                They orbit each other without ever
                needing to become the same colour.
            </p>

            <div class="memory">
                Different colours.
                Different worlds.
                Somehow still part of the same sky.
            </div>

        </div>

        ${button(
            "Continue",
            "unlock('gravity'); transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 7 — GRAVITY
   ========================================================= */

function gravityPlanet() {

    panel(`
        <h2>Planet VII — Gravity</h2>

        <div class="scene">

            ${star("s17", 18, 18)}
            ${star("s18", 83, 77)}

            <p>
                Gravity behaves strangely here.
            </p>

            <p>
                Everything floats.
            </p>

            <p>
                Including two people who clearly
                have a very different opinion
                about how tall they are.
            </p>

            <div class="memory">
                5'10.<br>
                5'1-ish.<br><br>
                One extremely short girlfriend.
                One extremely tall girlfriend.
                One universe.
            </div>

            <p class="quote">
                "At least you'll always have someone
                to reach the top shelf."
            </p>

        </div>

        ${button(
            "Continue",
            "unlock('ocean'); transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 8 — OCEAN
   ========================================================= */

function oceanPlanet() {

    panel(`
        <h2>Planet VIII — The Ocean</h2>

        <div class="ocean">

            ${star("s19", 18, 30)}
            ${star("s20", 67, 52)}
            ${star("s21", 87, 75)}

            <div class="moon"></div>

            <div class="wave"></div>

            <div class="stingray"
                 style="top:55%;animation-delay:-1s">
                🐟
            </div>

            <div class="stingray"
                 style="top:68%;animation-delay:-5s;font-size:34px">
                🐟
            </div>

            <div class="stingray"
                 style="top:45%;animation-delay:-8s;font-size:27px">
                🐟
            </div>

        </div>

        <p class="quote">
            "One day, I want to see the ocean with you."
        </p>

        ${button(
            "🌊 Step into the water",
            "transition(oceanMemory)"
        )}

        ${button(
            "🐟 Follow the stingrays",
            "transition(stingrayMemory)"
        )}
    `);
}

function oceanMemory() {

    unlock("sunset");

    panel(`
        <h2>The Ocean You Haven't Seen Yet</h2>

        <div class="memory">

            I imagine standing beside you
            while you see the ocean for the first time.

            <br><br>

            I imagine looking at your face
            instead of the waves.

            <br><br>

            Because somehow,
            I think watching you experience
            something you've dreamed about
            would become one of my favourite memories too.

        </div>

        ${button(
            "Continue",
            "transition(galaxyMap)"
        )}
    `);
}

function stingrayMemory() {

    unlock("sunset");

    panel(`
        <h2>The Stingrays</h2>

        <div class="scene">

            ${star("s22", 50, 20)}

            <div class="stingray"
                 style="top:50%;animation-duration:6s">
                🐟
            </div>

            <p>
                A stingray swims past the spaceship.
            </p>

            <p>
                Then another.
            </p>

            <p>
                Then another.
            </p>

            <div class="quote">
                Apparently the universe decided
                stingrays belong in your love story.
            </div>

            <p>
                One of them pauses.
            </p>

            <p>
                It has a tiny star above its head.
            </p>

        </div>

        ${button(
            "Follow the stingray",
            "transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 9 — SUNSET
   ========================================================= */

function sunsetPlanet() {

    panel(`
        <h2>Planet IX — Sunset</h2>

        <div class="scene">

            ${star("s23", 20, 23)}
            ${star("s24", 78, 72)}

            <p>
                The entire planet is covered in sunset.
            </p>

            <p>
                Burgundy skies.
                Pink clouds.
                Golden light.
            </p>

            <div class="memory">
                This is where you realise
                that you don't only want the huge moments.
            </div>

            <p>
                You want the little ones.
            </p>

            <p>
                Dancing in the kitchen.
                Singing badly.
                Painting beside each other.
                Sitting somewhere quiet.
                Talking until midnight.
            </p>

        </div>

        ${button(
            "💃 Dance",
            "sunsetChoice('dance')"
        )}

        ${button(
            "🎨 Paint",
            "sunsetChoice('paint')"
        )}

        ${button(
            "🎵 Sing",
            "sunsetChoice('sing')"
        )}

        ${button(
            "🌳 Dream about the future",
            "sunsetChoice('future')"
        )}
    `);
}

function sunsetChoice(choice) {

    state.choices.sunset = choice;

    const stories = {

        dance: `
            You put on music.
            <br><br>
            Neither of you knows the right steps.
            <br><br>
            You dance anyway.
        `,

        paint: `
            Two canvases appear.
            <br><br>
            Neither painting looks anything like
            what you planned.
            <br><br>
            You both laugh.
        `,

        sing: `
            You sing together.
            <br><br>
            One of you forgets the words.
            The other makes up completely new ones.
            <br><br>
            Somehow it becomes your favourite song.
        `,

        future: `
            You sit beneath the sunset
            and talk about the life you want.
            <br><br>
            A countryside house.
            A tree house.
            A quiet life.
            <br><br>
            And each other.
        `
    };

    unlock("future");

    panel(`
        <h2>A Little Piece of Us</h2>

        <div class="memory">
            ${stories[choice]}
        </div>

        ${button(
            "Continue",
            "transition(galaxyMap)"
        )}
    `);
}


/* =========================================================
   PLANET 10 — FUTURE
   ========================================================= */

function futurePlanet() {

    panel(`
        <h2>Planet X — The Future</h2>

        <div class="scene">

            ${star("s25", 15, 25)}
            ${star("s26", 80, 20)}
            ${star("s27", 74, 77)}

            <p>
                The final planet doesn't show the future
                as one single moment.
            </p>

            <p>
                Instead, it shows possibilities.
            </p>

            <div class="memory">
                A wedding.<br>
                A little house in the countryside.<br>
                A tree house.<br>
                Paintings on the walls.<br>
                Music in the kitchen.<br>
                Two people growing older together.
            </div>

            <p>
                Lola sees a garden.
            </p>

            <p>
                Someone is waiting there.
            </p>

        </div>

        ${button(
            "💍 Walk towards the wedding",
            "transition(weddingScene)"
        )}

        ${button(
            "🌳 Find the tree house",
            "transition(treehouseScene)"
        )}

        ${button(
            "🏡 Explore the countryside",
            "transition(countrysideScene)"
        )}

        ${button(
            "🎨 See the life you've built",
            "transition(marriedLifeScene)"
        )}
    `);
}


/* =========================================================
   WEDDING
   ========================================================= */

function weddingScene() {

    panel(`
        <h2>💍 The Wedding</h2>

        <div class="wedding">

            ${star("s25", 20, 20)}

            <div class="petals">
                <div class="petal" style="left:10%;animation-delay:0s"></div>
                <div class="petal" style="left:25%;animation-delay:2s"></div>
                <div class="petal" style="left:50%;animation-delay:1s"></div>
                <div class="petal" style="left:70%;animation-delay:3s"></div>
                <div class="petal" style="left:85%;animation-delay:1.5s"></div>
            </div>

            <div style="
                position:absolute;
                inset:0;
                display:flex;
                align-items:center;
                justify-content:center;
                flex-direction:column;
                text-align:center;
                padding:20px;
            ">

                <div style="font-size:70px">💐</div>

                <h2 style="margin:10px">
                    One day.
                </h2>

                <p>
                    Lola stands beneath a sky full of stars.
                </p>

                <p>
                    And the person waiting for her
                    reaches out her hand.
                </p>

            </div>

        </div>

        ${button(
            "Take her hand",
            "weddingChoice('hand')"
        )}

        ${button(
            "Look at her and laugh",
            "weddingChoice('laugh')"
        )}

        ${button(
            "Tell her you love her",
            "weddingChoice('love')"
        )}
    `);
}

function weddingChoice(choice) {

    state.choices.wedding = choice;

    const endings = {

        hand: `
            You take her hand.
            <br><br>
            Everything else disappears.
            <br><br>
            There is only the person beside you
            and the life waiting ahead.
        `,

        laugh: `
            You look at her.
            <br><br>
            And both of you start laughing.
            <br><br>
            Not because anything went wrong.
            <br><br>
            Because somehow,
            after everything,
            you're actually here.
        `,

        love: `
            You tell her you love her.
            <br><br>
            The words feel familiar,
            but somehow they're still not enough.
            <br><br>
            So you say them again.
        `
    };

    unlock("future");

    panel(`
        <h2>And Then...</h2>

        <div class="memory">
            ${endings[choice]}
        </div>

        ${button(
            "Continue into the future",
            "transition(countrysideScene)"
        )}
    `);
}


/* =========================================================
   TREE HOUSE
   ========================================================= */

function treehouseScene() {

    panel(`
        <h2>🌳 The Tree House</h2>

        <div class="countryside">

            ${star("s26", 80, 18)}

            <div class="sunset"></div>

            <div class="house"></div>

            <div class="tree">
                🌳
            </div>

        </div>

        <div class="memory">

            There is a little tree house
            somewhere beyond the fields.

            <br><br>

            It isn't perfect.

            <br><br>

            That's what makes it yours.

            <br><br>

            A place to sit.
            A place to talk.
            A place to watch the stars.

        </div>

        ${button(
            "Climb inside",
            "treehouseInside()"
        )}
    `);
}

function treehouseInside() {

    panel(`
        <h2>Our Little Place</h2>

        <div class="memory">

            You sit beside each other
            beneath a blanket.

            <br><br>

            You talk about everything
            and absolutely nothing.

            <br><br>

            Eventually,
            the conversation becomes quiet.

            <br><br>

            You look outside.

            <br><br>

            The stars are everywhere.

        </div>

        ${button(
            "Continue",
            "transition(countrysideScene)"
        )}
    `);
}


/* =========================================================
   COUNTRYSIDE
   ========================================================= */

function countrysideScene() {

    panel(`
        <h2>🏡 The Countryside</h2>

        <div class="countryside">

            ${star("s27", 18, 18)}

            <div class="sunset"></div>

            <div class="house"></div>

            <div class="tree">
                🌳
            </div>

        </div>

        <div class="memory">

            A little house surrounded by green fields.

            <br><br>

            No huge city.
            No rushing around.

            <br><br>

            Just home.

            <br><br>

            You wake up together.
            You drink coffee.
            You argue about who gets the blanket.
            You cook.
            You paint.
            You sing.
            You dance.

            <br><br>

            And sometimes,
            you do absolutely nothing.

        </div>

        ${button(
            "🌅 Watch the sunset together",
            "futureChoice('sunset')"
        )}

        ${button(
            "☕ Have a quiet morning",
            "futureChoice('morning')"
        )}

        ${button(
            "❤️ Stay together forever",
            "futureChoice('forever')"
        )}
    `);
}

function marriedLifeScene() {

    panel(`
        <h2>❤️ Married Life</h2>

        <div class="scene">

            <p>
                Years have passed.
            </p>

            <p>
                The house still smells like coffee.
            </p>

            <p>
                There are paintings on the walls.
            </p>

            <p>
                Music still plays in the kitchen.
            </p>

            <p>
                The tree house is still standing.
            </p>

            <div class="memory">
                You grew older together.
                <br><br>
                Not because every day was perfect.
                <br><br>
                But because you kept choosing
                to build a life together.
            </div>

        </div>

        ${button(
            "Keep dreaming",
            "transition(countrysideScene)"
        )}
    `);
}


/* =========================================================
   FUTURE CHOICE
   ========================================================= */

function futureChoice(choice) {

    state.choices.future = choice;
    complete("future");

    let text = {

        sunset: `
            You stand outside together
            and watch the sky turn pink.
            <br><br>
            Lola rests her head against you.
            <br><br>
            Neither of you says anything.
            <br><br>
            You don't need to.
        `,

        morning: `
            Morning comes slowly.
            <br><br>
            There is coffee.
            Messy hair.
            Bare feet.
            <br><br>
            And the quiet happiness
            of waking up beside the person you love.
        `,

        forever: `
            You look at her.
            <br><br>
            You know exactly what you want.
            <br><br>
            To marry her.
            <br>
            To build a home with her.
            <br>
            To grow old with her.
            <br>
            To be happy together.
        `
    }[choice];

    panel(`
        <h2>The Life We Imagine</h2>

        <div class="memory">
            ${text}
        </div>

        ${button(
            "🌌 Return to the galaxy",
            "transition(galaxyMap)"
        )}

        ${
            state.stars.length >= 27
            ? button(
                "✨ Enter Our Universe",
                "transition(universeChapter)"
            )
            : ""
        }
    `);
}


/* =========================================================
   OUR UNIVERSE
   ========================================================= */

function universeChapter() {

    if (state.stars.length < 27) {

        panel(`
            <h2>Not Yet...</h2>

            <div class="memory">
                There are still hidden stars somewhere
                in the galaxy.
                <br><br>
                You have found ${state.stars.length}/27.
                <br><br>
                Keep exploring.
            </div>

            ${button(
                "Return to the galaxy",
                "transition(galaxyMap)"
            )}
        `);

        return;
    }

    complete("universe");

    panel(`
        <h2>🌌 Our Universe</h2>

        <p class="subtitle">
            You found all 27 stars.
        </p>

        <div class="constellation" id="constellation"></div>

        <div class="memory">

            The planets begin to disappear.

            <br><br>

            The ocean.
            The storms.
            The sunsets.
            The coffee.
            The countryside.
            The wedding.

            <br><br>

            They all become one sky.

            <br><br>

            Because every little place
            was always leading here.

        </div>

        ${button(
            "Read the final letter",
            "transition(finalLetter)"
        )}
    `);

    createConstellation();
}


/* =========================================================
   CONSTELLATION
   ========================================================= */

function createConstellation() {

    const box = document.getElementById("constellation");

    if (!box) return;

    const points = [];

    for (let i = 0; i < 27; i++) {

        const angle = (i / 27) * Math.PI * 2;

        const radius =
            100 +
            Math.sin(i * 2.7) * 55;

        const x =
            50 +
            Math.cos(angle) * radius / 6.5;

        const y =
            50 +
            Math.sin(angle) * radius / 3.7;

        points.push({x, y});

        box.innerHTML += `
            <div
                class="constellation-star"
                style="
                    left:${x}%;
                    top:${y}%;
                "
            ></div>
        `;
    }

    for (let i = 0; i < points.length - 1; i++) {

        const a = points[i];
        const b = points[i + 1];

        const dx = b.x - a.x;
        const dy = b.y - a.y;

        const length = Math.sqrt(dx*dx + dy*dy);

        const angle =
            Math.atan2(dy, dx) * 180 / Math.PI;

        box.innerHTML += `
            <div
                class="constellation-line"
                style="
                    left:${a.x}%;
                    top:${a.y}%;
                    width:${length}%;
                    transform:rotate(${angle}deg);
                "
            ></div>
        `;
    }
}


/* =========================================================
   FINAL LETTER
   ========================================================= */

function finalLetter() {

    panel(`
        <h2>For Lola ❤️</h2>

        <div class="letter">

            <p>
                Lola,
            </p>

            <p>
                If you've made it all the way here,
                then I suppose there's only one thing
                left for me to tell you.
            </p>

            <p>
                I am so incredibly proud of you.
            </p>

            <p>
                More than I think I will ever know
                how to put into words.
            </p>

            <p>
                I'm proud of the person you are,
                of the things you've survived,
                of the things you've overcome,
                and of the person you continue to become.
            </p>

            <p>
                I'm proud of you for making it through
                the days that felt impossible.
                I'm proud of the softness you've managed
                to keep in a world that hasn't always
                been soft with you.
            </p>

            <p>
                And more than anything,
                I hope you know that you never have
                to become someone else to deserve love.
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
                You have somehow become such a beautiful
                part of my life that sometimes I don't know
                how I existed without you in it.
                You are everything to me and somehow,
                at the same time, you are still so much more
                than everything I could ever put into a single word.
            </p>

            <p>
                I don't just want the extraordinary moments
                with you.
            </p>

            <p>
                I want the ordinary ones.
            </p>

            <p>
                I want to dance with you in the kitchen
                for absolutely no reason.
                I want to sing with you until we're laughing
                because neither of us can remember the words.
                I want to paint beside you,
                even if neither of us knows what we're doing.
                I want to sit somewhere quiet in the countryside
                with you and watch the sun disappear.
            </p>

            <p>
                I want that tree house we've talked about.
            </p>

            <p>
                I want somewhere that feels like ours.
            </p>

            <p>
                Somewhere surrounded by green fields
                and open skies, where the nights are dark enough
                for us to see every star above us.
                Somewhere we can sit together and talk
                until we realise we've been talking for hours.
            </p>

            <p>
                I want slow mornings.
            </p>

            <p>
                Coffee.
            </p>

            <p>
                Messy hair.
            </p>

            <p>
                Bare feet.
            </p>

            <p>
                Your hand finding mine without either of us
                thinking about it.
            </p>

            <p>
                I want to marry you.
            </p>

            <p>
                I want the little house in the countryside.
                I want the tree house and the green fields
                and the slow mornings.
                I want to wake up beside you and fall asleep
                knowing that the person I love is right there.
            </p>

            <p>
                I want us to grow older together
                and still find reasons to laugh.
            </p>

            <p>
                More than anything,
                I want a life where we are simply
                happy together.
            </p>

            <p>
                I want the kind of life where nothing
                particularly remarkable happens and yet,
                somehow, I still go to sleep thinking,
                "I got to spend another day with her."
            </p>

            <p>
                I want to see the ocean with you.
            </p>

            <p>
                I want to stand beside you while the waves
                reach the shore and finally watch you experience
                something you've dreamed about.
            </p>

            <p>
                I want photographs we haven't taken yet.
            </p>

            <p>
                Songs we haven't sung yet.
            </p>

            <p>
                Paintings we haven't made yet.
            </p>

            <p>
                Places we haven't found yet.
            </p>

            <p>
                Stories we haven't written yet.
            </p>

            <p>
                I want all the little things we've imagined
                scattered throughout our future.
            </p>

            <p>
                And I want the things we haven't imagined yet,
                too.
            </p>

            <p>
                Because that's the part that makes me happiest.
            </p>

            <p>
                There is still so much life ahead of us
                that we haven't even discovered.
            </p>

            <p>
                So many sunsets.
                So many nights beneath the stars.
                So many ridiculous conversations.
                So many moments where one of us will look
                at the other and laugh because somehow
                this is our life.
            </p>

            <p>
                And if I could ask the universe for anything,
                I wouldn't ask for a perfect life.
            </p>

            <p>
                I'd ask for a life where I get to keep
                finding you in it.
            </p>

            <p>
                Because somewhere along the way,
                you became my favourite place to return to.
            </p>

            <p>
                My favourite voice.
            </p>

            <p>
                My favourite person to talk to.
            </p>

            <p>
                My favourite thought at the end of the day.
            </p>

            <p>
                My favourite future to imagine.
            </p>

            <p>
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
                But I know what I hope is waiting somewhere
                along the road.
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
                And maybe one day, we'll look back at this
                little universe and laugh at how small
                our dreams seemed compared to everything
                we actually got to experience.
            </p>

            <p>
                Until then, I'll keep dreaming with you.
                I'll keep writing about you.
                I'll keep loving you.
                And I'll keep reminding you,
                whenever you forget,
                just how proud I am of the person you are.
            </p>

            <p>
                Happy 27th birthday, my love.
            </p>

            <p>
                You are my favourite person.
            </p>

            <p>
                You are everything.
            </p>

            <p>
                And somehow, you are still so much more.
            </p>

            <p>
                If there are a million galaxies above us,
                I hope you know that I'd still look for you.
            </p>

            <p>
                Because no matter how enormous the universe becomes,
                I'd always find my way home to you.
            </p>

            <p class="signature">
                — Bree ❤️
            </p>

        </div>

        ${button(
            "⭐ There's one last thing...",
            "transition(starReveal)"
        )}
    `);
}


/* =========================================================
   REAL STAR REVEAL
   ========================================================= */

function starReveal() {

    panel(`
        <h2>⭐ Your Star</h2>

        <div class="scene">

            <div style="
                text-align:center;
                padding:40px 10px;
            ">

                <div style="
                    font-size:110px;
                    animation:hiddenTwinkle 2s infinite;
                ">
                    ✦
                </div>

                <h2>
                    Somewhere in the real universe,
                    there is a star with your name on it.
                </h2>

                <p>
                    I wanted you to have something
                    that wasn't only inside this little game.
                </p>

                <p>
                    Something that exists beyond the screen.
                </p>

                <div class="quote">
                    "Of all the stars in every sky,
                    somehow I still found my way to you."
                </div>

            </div>

        </div>

        ${button(
            "🌌 Play again",
            "transition(startGame)"
        )}

        <p style="
            text-align:center;
            color:#76505e;
            font-size:12px;
        ">
            Happy 27th birthday, Lola ❤️
        </p>
    `);
}


/* =========================================================
   START
   ========================================================= */

startGame();

</script>

</body>
</html>
