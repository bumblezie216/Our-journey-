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
    min-height: 100%;
    font-family: Georgia, "Times New Roman", serif;
    background: #020005;
    color: #fff;
    overflow-x: hidden;
}

body {
    min-height: 100vh;
}

/* =========================
   SPACE
========================= */

.space {
    position: fixed;
    inset: 0;
    overflow: hidden;
    pointer-events: none;
    z-index: -10;

    background:
        radial-gradient(
            circle at 50% 45%,
            rgba(100, 0, 60, .25),
            transparent 34%
        ),
        radial-gradient(
            circle at 10% 20%,
            rgba(100, 0, 55, .18),
            transparent 28%
        ),
        radial-gradient(
            circle at 90% 80%,
            rgba(60, 0, 85, .16),
            transparent 30%
        ),
        #020005;
}

.nebula {
    position: absolute;
    width: 70vw;
    height: 70vw;
    border-radius: 50%;
    filter: blur(90px);
    opacity: .25;
}

.nebula.one {
    background: #65002f;
    top: -30%;
    left: -25%;
}

.nebula.two {
    background: #35004d;
    right: -25%;
    bottom: -30%;
}

.nebula.three {
    background: #85003f;
    left: 40%;
    top: 35%;
    opacity: .08;
}

.bg-star {
    position: absolute;
    width: 2px;
    height: 2px;
    background: white;
    border-radius: 50%;
    animation: twinkle 3s infinite ease-in-out;
}

@keyframes twinkle {
    0%,100% {
        opacity: .2;
        transform: scale(.7);
    }

    50% {
        opacity: 1;
        transform: scale(1.5);
    }
}

/* =========================
   SHOOTING STARS
========================= */

.shooting-star {
    position: absolute;
    width: 130px;
    height: 2px;

    background:
        linear-gradient(
            90deg,
            transparent,
            rgba(255,255,255,.9)
        );

    transform: rotate(-35deg);
    opacity: 0;
    animation: shoot 7s linear infinite;
}

.shooting-star:nth-child(1) {
    top: 8%;
    left: 85%;
    animation-delay: 1s;
}

.shooting-star:nth-child(2) {
    top: 28%;
    left: 65%;
    animation-delay: 4s;
}

.shooting-star:nth-child(3) {
    top: 60%;
    left: 92%;
    animation-delay: 7s;
}

.shooting-star:nth-child(4) {
    top: 75%;
    left: 30%;
    animation-delay: 10s;
}

.shooting-star:nth-child(5) {
    top: 15%;
    left: 35%;
    animation-delay: 13s;
}

@keyframes shoot {
    0% {
        transform: translate(0,0) rotate(-35deg);
        opacity: 0;
    }

    8% {
        opacity: 1;
    }

    18% {
        transform: translate(-280px,190px) rotate(-35deg);
        opacity: 0;
    }

    100% {
        opacity: 0;
    }
}

/* =========================
   HEADER
========================= */

.header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 70px;

    z-index: 100;

    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 0 22px;

    background: rgba(2,0,5,.78);
    backdrop-filter: blur(12px);

    border-bottom:
        1px solid rgba(185,40,105,.35);
}

.logo {
    font-size: 16px;
    letter-spacing: 3px;
    color: #f7c9dc;
}

.star-counter {
    font-size: 15px;
    color: #ffe0ed;
}

.star-counter span {
    color: #ff83b7;
    font-weight: bold;
}

/* =========================
   GAME
========================= */

.game {
    min-height: 100vh;
    padding: 100px 20px 60px;

    display: flex;
    justify-content: center;
}

.screen {
    width: 100%;
    max-width: 1100px;
    display: none;

    animation: fadeIn .65s ease;
}

.screen.active {
    display: block;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(15px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* =========================
   PANELS
========================= */

.panel {
    background: rgba(11,0,13,.88);

    border:
        1px solid rgba(195,45,113,.38);

    border-radius: 25px;

    padding: 35px;

    box-shadow:
        0 0 60px rgba(110,0,60,.16),
        inset 0 0 30px rgba(255,255,255,.015);
}

h1 {
    font-size: clamp(35px,7vw,72px);
    line-height: 1;
    margin: 0 0 20px;
    color: #ffe7f0;
}

h2 {
    font-size: clamp(28px,5vw,45px);
    margin: 0 0 15px;
    color: #ffd8e8;
}

p {
    font-size: 18px;
    line-height: 1.8;
    color: #eadce4;
}

.small {
    font-size: 14px;
    color: #a998a3;
}

.eyebrow {
    text-transform: uppercase;
    letter-spacing: 4px;
    color: #e66b9f;
    font-size: 12px;
    margin-bottom: 12px;
}

/* =========================
   BUTTONS
========================= */

.choice-container {
    display: grid;
    gap: 13px;
    margin-top: 25px;
}

.choice {
    border:
        1px solid rgba(225,74,145,.45);

    background:
        rgba(75,0,42,.32);

    color: white;

    padding: 17px 20px;

    border-radius: 14px;

    cursor: pointer;

    text-align: left;

    font-size: 16px;

    transition: .25s;
}

.choice:hover {
    transform: translateX(7px);

    background:
        rgba(115,0,65,.48);

    border-color: #ec75a9;

    box-shadow:
        0 0 25px rgba(190,25,100,.18);
}

.primary {
    border: 0;

    background:
        linear-gradient(
            135deg,
            #7d164c,
            #bd3976
        );

    color: white;

    padding: 15px 25px;

    border-radius: 30px;

    cursor: pointer;

    font-size: 16px;

    margin-top: 20px;

    box-shadow:
        0 0 25px rgba(185,43,112,.22);

    transition: .25s;
}

.primary:hover {
    transform: scale(1.04);
}

/* =========================
   INTRO
========================= */

.intro {
    min-height: 70vh;

    display: flex;
    align-items: center;
    justify-content: center;

    text-align: center;
}

.intro .panel {
    max-width: 850px;
}

.big-heart {
    font-size: 60px;
    animation: heartbeat 2s infinite;
}

@keyframes heartbeat {
    0%,100% {
        transform: scale(1);
    }

    50% {
        transform: scale(1.12);
    }
}

/* =========================
   MEMORY
========================= */

.memory {
    padding: 22px;

    border-radius: 18px;

    background:
        rgba(82,0,47,.2);

    border:
        1px solid rgba(210,77,139,.25);

    margin: 20px 0;

    line-height: 1.7;
}

.memory strong {
    display: block;
    color: #ffafd0;
    margin-bottom: 8px;
}

/* =========================
   STORY ART
========================= */

.scene-art {
    min-height: 230px;

    border-radius: 20px;

    margin-bottom: 25px;

    display: flex;
    align-items: center;
    justify-content: center;

    position: relative;

    overflow: hidden;

    font-size: 80px;

    background:
        radial-gradient(
            circle at center,
            rgba(161,28,95,.25),
            transparent 45%
        ),
        #060008;

    border:
        1px solid rgba(220,80,144,.2);
}

/* =========================
   HIDDEN STARS
========================= */

.hidden-star {
    position: absolute;

    width: 30px;
    height: 30px;

    border: 0;

    padding: 0;

    background: transparent;

    color: white;

    font-size: 20px;

    line-height: 30px;

    cursor: pointer;

    z-index: 50;

    text-shadow:
        0 0 5px white,
        0 0 12px #ff72ad,
        0 0 25px #b40060;

    animation:
        starPulse 1.8s infinite ease-in-out;
}

.hidden-star:hover {
    transform: scale(1.5);
}

@keyframes starPulse {
    0%,100% {
        opacity: .45;
        transform: scale(.8);
    }

    50% {
        opacity: 1;
        transform: scale(1.15);
    }
}

.star-found {
    position: fixed;

    left: 50%;
    top: 50%;

    transform: translate(-50%,-50%);

    z-index: 999;

    background:
        rgba(24,0,18,.97);

    border:
        1px solid #d95b96;

    padding: 20px 30px;

    border-radius: 18px;

    box-shadow:
        0 0 50px rgba(218,62,133,.45);

    text-align: center;

    animation: found .35s ease;
}

@keyframes found {
    from {
        opacity: 0;
        transform:
            translate(-50%,-50%)
            scale(.7);
    }

    to {
        opacity: 1;
        transform:
            translate(-50%,-50%)
            scale(1);
    }
}

/* =========================
   GALAXY MAP
========================= */

.galaxy-map {
    position: relative;

    height: 650px;

    border-radius: 30px;

    overflow: hidden;

    border:
        1px solid rgba(210,48,119,.35);

    background:
        radial-gradient(
            circle at 50% 50%,
            rgba(128,0,68,.22),
            transparent 20%
        ),
        #030006;
}

.orbit {
    position: absolute;

    left: 50%;
    top: 50%;

    transform:
        translate(-50%,-50%);

    border:
        1px solid rgba(220,98,156,.14);

    border-radius: 50%;
}

.orbit.one {
    width: 180px;
    height: 180px;
}

.orbit.two {
    width: 310px;
    height: 310px;
}

.orbit.three {
    width: 450px;
    height: 450px;
}

.orbit.four {
    width: 590px;
    height: 590px;
}

.sun {
    position: absolute;

    left: 50%;
    top: 50%;

    width: 75px;
    height: 75px;

    transform:
        translate(-50%,-50%);

    border-radius: 50%;

    background:
        radial-gradient(
            circle,
            #ffd9ec,
            #9b1d5b 50%,
            #250014
        );

    box-shadow:
        0 0 45px rgba(213,55,125,.55);
}

.planet {
    position: absolute;

    width: 75px;
    height: 75px;

    border-radius: 50%;

    border:
        2px solid rgba(255,205,229,.35);

    cursor: pointer;

    display: flex;
    align-items: center;
    justify-content: center;

    color: white;

    font-size: 20px;

    text-align: center;

    transition: .3s;

    box-shadow:
        0 0 25px rgba(177,32,100,.3);
}

.planet:hover {
    transform: scale(1.15);

    box-shadow:
        0 0 40px rgba(240,98,158,.6);
}

.planet.visited {
    border-color: #f38db8;
}

.planet-label {
    position: absolute;

    bottom: -27px;

    left: 50%;

    transform:
        translateX(-50%);

    white-space: nowrap;

    color: #d9c4ce;

    font-size: 12px;
}

.p1 {
    left: 20%;
    top: 16%;
    background:
        radial-gradient(circle at 35% 30%,#c18bff,#4e145f);
}

.p2 {
    left: 48%;
    top: 10%;
    background:
        radial-gradient(circle at 35% 30%,#b87a46,#29120a);
}

.p3 {
    right: 15%;
    top: 26%;
    background:
        radial-gradient(circle at 35% 30%,#7592ff,#15215d);
}

.p4 {
    left: 12%;
    top: 46%;
    background:
        radial-gradient(circle at 35% 30%,#8a5bff,#24103d);
}

.p5 {
    right: 12%;
    top: 52%;
    background:
        radial-gradient(circle at 35% 30%,#6db8ff,#093a55);
}

.p6 {
    left: 28%;
    bottom: 9%;
    background:
        radial-gradient(circle at 35% 30%,#ff9cc5,#551331);
}

.p7 {
    right: 28%;
    bottom: 9%;
    background:
        radial-gradient(circle at 35% 30%,#ffbb73,#6d2711);
}

.p8 {
    left: 46%;
    bottom: 3%;
    background:
        radial-gradient(circle at 35% 30%,#9ed8ff,#183a61);
}

.p9 {
    left: 4%;
    top: 20%;
    background:
        radial-gradient(circle at 35% 30%,#d7a6ff,#36165e);
}

.p10 {
    right: 3%;
    top: 12%;
    background:
        radial-gradient(circle at 35% 30%,#ef88bd,#53112f);
}

.spaceship {
    position: absolute;

    width: 45px;
    height: 45px;

    display: flex;
    align-items: center;
    justify-content: center;

    font-size: 27px;

    transition:
        left 1s ease,
        top 1s ease;

    z-index: 20;
}

/* =========================
   LETTER
========================= */

.letter {
    max-width: 850px;

    margin: auto;

    background:
        linear-gradient(
            rgba(35,0,24,.92),
            rgba(15,0,12,.96)
        );

    border:
        1px solid rgba(217,87,144,.35);

    padding:
        clamp(25px,6vw,60px);

    border-radius: 25px;

    box-shadow:
        0 0 70px rgba(129,0,67,.2);
}

.letter p {
    font-size: 18px;
    line-height: 2;
}

.signature {
    margin-top: 35px;

    text-align: right;

    color: #ffafd0;

    font-size: 21px;
}

/* =========================
   CONSTELLATION
========================= */

.constellation {
    position: relative;

    height: 500px;

    margin-top: 25px;

    background:
        radial-gradient(
            circle,
            rgba(114,0,63,.2),
            transparent 45%
        ),
        #020005;

    border-radius: 25px;

    overflow: hidden;
}

.constellation-star {
    position: absolute;

    width: 12px;
    height: 12px;

    border-radius: 50%;

    background: white;

    box-shadow:
        0 0 15px #ff9bc6,
        0 0 30px #b30062;

    animation:
        constellationGlow 2s infinite ease-in-out;
}

@keyframes constellationGlow {
    0%,100% {
        opacity: .5;
    }

    50% {
        opacity: 1;
    }
}

.constellation-line {
    position: absolute;

    height: 1px;

    background:
        rgba(255,160,203,.4);

    transform-origin: left center;
}

/* =========================
   STAR REVEAL
========================= */

.star-reveal {
    text-align: center;

    padding: 50px 20px;
}

.real-star {
    font-size: 120px;

    margin: 25px;

    animation:
        realStar 3s infinite ease-in-out;
}

@keyframes realStar {
    0%,100% {
        transform: scale(1);

        filter:
            drop-shadow(0 0 10px white);
    }

    50% {
        transform: scale(1.15);

        filter:
            drop-shadow(0 0 40px #ff78b5);
    }
}

/* =========================
   MOBILE
========================= */

@media (max-width:700px) {

    .header {
        padding: 0 13px;
    }

    .logo {
        font-size: 11px;
        letter-spacing: 2px;
    }

    .panel {
        padding: 24px 18px;
    }

    .galaxy-map {
        height: 570px;
    }

    .planet {
        width: 62px;
        height: 62px;
        font-size: 16px;
    }

    .planet-label {
        font-size: 9px;
    }

    .scene-art {
        min-height: 180px;
    }

    p {
        font-size: 16px;
    }
}
</style>
</head>

<body>

<div class="space">

    <div class="nebula one"></div>
    <div class="nebula two"></div>
    <div class="nebula three"></div>

    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>

    <div id="backgroundStars"></div>

</div>

<header class="header">

    <div class="logo">
        LOLA'S LITTLE UNIVERSE
    </div>

    <div class="star-counter">
        ⭐ <span id="starCount">0</span> / 27
    </div>

</header>


<main class="game">

<!-- ======================================================
     INTRO
====================================================== -->

<section id="intro" class="screen active">

    <div class="intro">

        <div class="panel">

            <div class="big-heart">♡</div>

            <div class="eyebrow">
                A birthday story for Lola
            </div>

            <h1>
                Lola's Little Universe
            </h1>

            <p>
                Somewhere beyond the stars,
                there is a universe that has been waiting for you.
            </p>

            <p>
                But before you find it,
                there are places you have to visit,
                memories you have to uncover,
                choices you have to make...
                and 27 little stars hidden along the way.
            </p>

            <p class="small">
                Some stars are easy to find.<br>
                Some are hiding where you least expect them.
            </p>

            <button
                class="primary"
                onclick="startGame()"
            >
                Begin the journey ✦
            </button>

        </div>

    </div>

</section>


<!-- ======================================================
     PROLOGUE
====================================================== -->

<section id="prologue" class="screen">

    <div class="panel">

        <div
            class="scene-art"
            id="prologueArt"
        >

            <button
                class="hidden-star"
                style="left:12%;top:18%;"
                onclick="collectStar('s1',this)"
            >
                ✦
            </button>

            <button
                class="hidden-star"
                style="left:78%;top:25%;"
                onclick="collectStar('s2',this)"
            >
                ✦
            </button>

            <button
                class="hidden-star"
                style="left:45%;top:72%;"
                onclick="collectStar('s3',this)"
            >
                ✦
            </button>

            <div style="z-index:2;">
                🚀
            </div>

        </div>

        <div class="eyebrow">
            Prologue
        </div>

        <h2>
            The Beginning
        </h2>

        <p>
            Lola opens her eyes.
        </p>

        <p>
            There is no ceiling above her.
            No floor beneath her.
            Only an endless black sky filled with stars.
        </p>

        <p>
            Floating in front of her is a tiny spaceship.
        </p>

        <p>
            A message appears across its window:
        </p>

        <div class="memory">

            <strong>
                THERE IS A UNIVERSE WAITING FOR YOU.
            </strong>

            But first,
            you have to find your way to it.

        </div>

        <p>
            Three paths appear in front of her.
        </p>

        <div class="choice-container">

            <button
                class="choice"
                onclick="prologueChoice('ship')"
            >
                🚀 Take the spaceship
            </button>

            <button
                class="choice"
                onclick="prologueChoice('stars')"
            >
                ✦ Follow the stars
            </button>

            <button
                class="choice"
                onclick="prologueChoice('waves')"
            >
                🌊 Follow the sound of waves
            </button>

        </div>

    </div>

</section>


<!-- ======================================================
     MAP
====================================================== -->

<section id="map" class="screen">

    <div class="panel">

        <div class="eyebrow">
            The Galaxy
        </div>

        <h2>
            Choose where to go
        </h2>

        <p>
            Your spaceship waits in the centre of the galaxy.
            Every planet holds another part of the story.
        </p>

        <div class="galaxy-map">

            <div class="orbit one"></div>
            <div class="orbit two"></div>
            <div class="orbit three"></div>
            <div class="orbit four"></div>

            <div class="sun"></div>

            <div
                class="spaceship"
                id="spaceship"
                style="left:47%;top:45%;"
            >
                🚀
            </div>

            <div
                class="planet p1"
                onclick="visitPlanet('beginning')"
            >
                ✦
                <span class="planet-label">
                    The Beginning
                </span>
            </div>

            <div
                class="planet p2"
                onclick="visitPlanet('coffee')"
            >
                ☕
                <span class="planet-label">
                    Black Coffee
                </span>
            </div>

            <div
                class="planet p3"
                onclick="visitPlanet('hazel')"
            >
                👁
                <span class="planet-label">
                    Hazel
                </span>
            </div>

            <div
                class="planet p4"
                onclick="visitPlanet('storm')"
            >
                🌩
                <span class="planet-label">
                    The Storm
                </span>
            </div>

            <div
                class="planet p5"
                onclick="visitPlanet('ocean')"
            >
                🌊
                <span class="planet-label">
                    The Ocean
                </span>
            </div>

            <div
                class="planet p6"
                onclick="visitPlanet('colour')"
            >
                💙
                <span class="planet-label">
                    Two Moons
                </span>
            </div>

            <div
                class="planet p7"
                onclick="visitPlanet('gravity')"
            >
                ✦
                <span class="planet-label">
                    Gravity
                </span>
            </div>

            <div
                class="planet p8"
                onclick="visitPlanet('future')"
            >
                💍
                <span class="planet-label">
                    The Future
                </span>
            </div>

            <div
                class="planet p9"
                onclick="visitPlanet('sunset')"
            >
                🌅
                <span class="planet-label">
                    Sunset
                </span>
            </div>

            <div
                class="planet p10"
                onclick="visitPlanet('ouruniverse')"
            >
                ♡
                <span class="planet-label">
                    Our Universe
                </span>
            </div>

        </div>

        <p class="small">
            Explore everything. Look carefully.
            Some stars only appear in certain places.
        </p>

    </div>

</section>


<!-- ======================================================
     STORY
====================================================== -->

<section id="story" class="screen">

    <div class="panel story-card">

        <div id="storyContent"></div>

    </div>

</section>


<!-- ======================================================
     CONSTELLATION
====================================================== -->

<section id="constellationScreen" class="screen">

    <div class="panel">

        <div class="eyebrow">
            You found them all
        </div>

        <h2>
            Our Constellation
        </h2>

        <p>
            Twenty seven little stars.
            Twenty seven pieces of the journey.
        </p>

        <div
            class="constellation"
            id="constellation"
        ></div>

        <p style="text-align:center;">
            And somehow,
            every star led back to you.
        </p>

        <button
            class="primary"
            onclick="showFinalLetter()"
        >
            Find out what was waiting at the end ✦
        </button>

    </div>

</section>


<!-- ======================================================
     LETTER
====================================================== -->

<section id="letterScreen" class="screen">

    <div class="letter">

        <div class="eyebrow">
            The Final Letter
        </div>

        <h2>
            Home
        </h2>

        <p>
            Lola,
        </p>

        <p>
            If you've made it all the way here,
            then I suppose there's only one thing left for me to tell you.
        </p>

        <p>
            I am so incredibly proud of you.
        </p>

        <p>
            I'm proud of the person you are,
            the things you've survived,
            the things you've overcome,
            and the person you're continuing to become.
        </p>

        <p>
            I'm proud of the softness you've managed to keep
            in a world that hasn't always been soft with you.
        </p>

        <p>
            You never have to become someone else to deserve love.
            You are already enough.
        </p>

        <p>
            You are my favourite person.
            Not just one of my favourite people.
            <strong>My favourite.</strong>
        </p>

        <p>
            You are such a beautiful part of my life.
            You are everything to me and somehow...
            still so much more.
        </p>

        <p>
            I don't just want the huge moments with you.
            I want the ordinary ones.
        </p>

        <p>
            I want to dance with you in the kitchen for no reason.
            I want to sing with you until we're laughing too hard
            to finish the song.
            I want to paint beside you.
            I want to sit with you somewhere in the countryside
            and watch the sunset.
        </p>

        <p>
            I want the tree house we've talked about.
            I want green fields and open skies.
            Dark nights filled with stars.
            Slow mornings.
            Coffee.
            Messy hair.
            Bare feet.
            Your hand finding mine without either of us thinking about it.
        </p>

        <p>
            I want to marry you.
        </p>

        <p>
            I want the little house in the countryside.
            I want the tree house.
            I want slow mornings beside you.
            I want to wake up and know that somehow,
            after everything,
            I get to spend another day with you.
        </p>

        <p>
            I want to grow older with you.
            I want to be happy with you.
            I want to build a life that feels like ours.
        </p>

        <p>
            And I want to see the ocean with you.
            I want to watch your face when you finally experience
            something you've dreamed about.
        </p>

        <p>
            I want the photographs we haven't taken yet.
            The songs we haven't sung.
            The paintings we haven't made.
            The places we haven't found.
            The stories we haven't written.
        </p>

        <p>
            If I could ask the universe for anything,
            I'd ask for a life where I get to keep finding you in it.
        </p>

        <p>
            Because you're my favourite place to return to.
            My favourite voice.
            My favourite person to talk to.
            The thought I want at the end of the day.
            The future I want to imagine.
            And my favourite part of today.
        </p>

        <p>
            I love you on the easy days.
            I love you on the difficult ones.
            I love you on the days when you feel beautiful
            and on the days when you can't see what I see in you.
        </p>

        <p>
            Here's to 27.
        </p>

        <p>
            To the countryside.
            To the tree house.
            To paintings.
            To songs.
            To dancing.
            To the ocean.
            To stars.
            To stingrays.
            To quiet mornings.
            To ridiculous nights.
            And to the future we keep imagining.
        </p>

        <p>
            You and me.
            Still talking.
            Still laughing.
            Still dreaming.
            Still finding new reasons to love each other.
        </p>

        <p>
            Happy 27th birthday, my love.
        </p>

        <p>
            You are my favourite person.
            You are everything.
            And somehow,
            you are still so much more.
        </p>

        <p>
            If there are a million galaxies above us,
            I hope you know that I'd still look for you.
        </p>

        <p>
            I'd always find my way home to you.
        </p>

        <div class="signature">
            — Bree
        </div>

        <div style="text-align:center;">

            <button
                class="primary"
                onclick="showStarReveal()"
            >
                There's one more thing ✦
            </button>

        </div>

    </div>

</section>


<!-- ======================================================
     STAR REVEAL
====================================================== -->

<section id="starReveal" class="screen">

    <div class="panel star-reveal">

        <div class="eyebrow">
            A little piece of the universe
        </div>

        <h2>
            For Lola
        </h2>

        <div class="real-star">
            ⭐
        </div>

        <p>
            You already have a star.
        </p>

        <p>
            But I wanted you to have something else too.
        </p>

        <p>
            A little universe made entirely for you.
        </p>

        <p>
            Every planet.
            Every choice.
            Every hidden star.
            Every word.
        </p>

        <p>
            Because if I could give you the entire universe,
            I still think I'd choose to give you a little piece of it
            that reminds you of us.
        </p>

        <h2>
            Happy 27th Birthday, Lola. ♡
        </h2>

        <p class="small">
            And yes...
            the star you found at the end is yours.
        </p>

        <button
            class="primary"
            onclick="resetGame()"
        >
            Play again
        </button>

    </div>

</section>

</main>


<script>

/* ==========================================================
   GAME SAVE
========================================================== */

const SAVE_KEY = "lolaLittleUniverse_v3";

let state = {
    stars: [],
    visited: [],
    path: [],
    completed: false
};


/* ==========================================================
   LOAD / SAVE
========================================================== */

function loadGame() {

    try {

        const saved =
            JSON.parse(
                localStorage.getItem(SAVE_KEY)
            );

        if (saved) {

            state = {
                stars:
                    Array.isArray(saved.stars)
                        ? saved.stars
                        : [],

                visited:
                    Array.isArray(saved.visited)
                        ? saved.visited
                        : [],

                path:
                    Array.isArray(saved.path)
                        ? saved.path
                        : [],

                completed:
                    !!saved.completed
            };
        }

    } catch(e) {

        console.log(
            "Starting a fresh universe."
        );
    }

    updateStarCounter();
    updateVisitedPlanets();
}


function saveGame() {

    localStorage.setItem(
        SAVE_KEY,
        JSON.stringify(state)
    );
}


/* ==========================================================
   STAR COUNTER
========================================================== */

function updateStarCounter() {

    document.getElementById(
        "starCount"
    ).textContent =
        state.stars.length;
}


/* ==========================================================
   VISITED PLANETS
========================================================== */

function updateVisitedPlanets() {

    const planets =
        document.querySelectorAll(
            ".planet"
        );

    planets.forEach(
        planet => {
            planet.classList.remove(
                "visited"
            );
        }
    );

    const map = {
        beginning: ".p1",
        coffee: ".p2",
        hazel: ".p3",
        storm: ".p4",
        ocean: ".p5",
        colour: ".p6",
        gravity: ".p7",
        future: ".p8",
        sunset: ".p9",
        ouruniverse: ".p10"
    };

    state.visited.forEach(
        name => {

            const selector =
                map[name];

            if (selector) {

                const planet =
                    document.querySelector(
                        selector
                    );

                if (planet) {
                    planet.classList.add(
                        "visited"
                    );
                }
            }
        }
    );
}


/* ==========================================================
   SCREEN
========================================================== */

function showScreen(id) {

    document
        .querySelectorAll(".screen")
        .forEach(
            screen => {
                screen.classList.remove(
                    "active"
                );
            }
        );

    const target =
        document.getElementById(id);

    if (target) {

        target.classList.add(
            "active"
        );
    }

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}


/* ==========================================================
   START
========================================================== */

function startGame() {

    state.path = [];

    saveGame();

    showScreen(
        "prologue"
    );
}


/* ==========================================================
   PROLOGUE
========================================================== */

function prologueChoice(choice) {

    state.path.push(choice);

    saveGame();

    if (choice === "ship") {

        story(
            "The Spaceship",
            `
            <p>
                The spaceship hums quietly as Lola steps inside.
            </p>

            <p>
                The moment she touches the controls,
                the stars outside begin moving.
            </p>

            <p>
                A tiny message appears:
            </p>

            <div class="memory">
                <strong>
                    SOMEWHERE OUT THERE,
                    SOMEONE IS WAITING.
                </strong>
            </div>
            `,
            "🚀",
            [
                ["Fly towards the nearest planet", "map"],
                ["Follow the brightest star", "beginning"]
            ],
            []
        );

    } else if (choice === "stars") {

        story(
            "Following the Stars",
            `
            <p>
                Lola follows the stars.
            </p>

            <p>
                One by one, they form a path through the darkness.
            </p>

            <p>
                At the end of it sits a tiny spaceship,
                waiting for her.
            </p>

            <p>
                Somehow, it feels like it already knows her.
            </p>
            `,
            "✦",
            [
                ["Take the spaceship", "map"],
                ["Follow the path", "beginning"]
            ],
            []
        );

    } else {

        story(
            "Following the Waves",
            `
            <p>
                Lola follows the sound of waves through the darkness.
            </p>

            <p>
                Eventually she reaches a tiny blue planet
                where the ocean stretches endlessly beneath
                a sky full of stars.
            </p>
            `,
            "🌊",
            [
                ["Step onto the beach", "ocean"],
                ["Return to the spaceship", "map"]
            ],
            []
        );
    }
}


/* ==========================================================
   MAP
========================================================== */

function visitPlanet(planet) {

    if (
        !state.visited.includes(
            planet
        )
    ) {

        state.visited.push(
            planet
        );

        saveGame();
    }

    updateVisitedPlanets();

    moveSpaceship(planet);

    const content = {

        beginning: {

            title:
                "Before You",

            icon:
                "✦",

            text: `
                <p>
                    Before there was an us,
                    there was simply you.
                </p>

                <p>
                    Somewhere in the universe,
                    a girl with hazel eyes,
                    a love for black coffee,
                    and a dream of seeing the ocean
                    was living a life that had no idea
                    it was about to become part of someone else's universe.
                </p>

                <p>
                    Three doors appear.
                </p>
            `,

            choices: [
                [
                    "☕ Follow the smell of coffee",
                    "coffee"
                ],
                [
                    "🔭 Look through the observatory",
                    "hazel"
                ],
                [
                    "🌊 Follow the ocean",
                    "ocean"
                ]
            ],

            stars: [
                "s4"
            ]
        },


        coffee: {

            title:
                "The Black Coffee Planet",

            icon:
                "☕",

            text: `
                <p>
                    The entire planet smells like freshly brewed coffee.
                </p>

                <p>
                    At the centre sits a tiny café
                    beneath a sky filled with burgundy stars.
                </p>

                <p>
                    Someone has left a note on the table:
                </p>

                <div class="memory">
                    <strong>
                        BLACK COFFEE.
                    </strong>

                    The first clue is always hidden
                    in the little things.
                </div>

                <p>
                    Lola smiles.
                </p>
            `,

            choices: [
                [
                    "☕ Sit down with the coffee",
                    "coffee2"
                ],
                [
                    "✦ Search the café",
                    "coffee3"
                ],
                [
                    "🚀 Return to the galaxy",
                    "map"
                ]
            ],

            stars: [
                "s5",
                "s6"
            ]
        },


        hazel: {

            title:
                "The Hazel Nebula",

            icon:
                "👁",

            text: `
                <p>
                    The observatory opens into a nebula
                    filled with colours somewhere between
                    green, gold and brown.
                </p>

                <p>
                    Hazel.
                </p>

                <p>
                    A telescope points towards one particular star.
                </p>

                <p>
                    When Lola looks through it,
                    she sees a pair of eyes looking back at her.
                </p>
            `,

            choices: [
                [
                    "👁 Look closer",
                    "hazel2"
                ],
                [
                    "✦ Follow the star",
                    "hazel3"
                ],
                [
                    "🚀 Return to the galaxy",
                    "map"
                ]
            ],

            stars: [
                "s7",
                "s8"
            ]
        },


        storm: {

            title:
                "The Storm",

            icon:
                "🌩",

            text: `
                <p>
                    Dark clouds gather around the planet.
                </p>

                <p>
                    Thunder cracks across the sky.
                </p>

                <p>
                    Lola instinctively covers her face.
                </p>

                <p>
                    Somewhere through the storm,
                    a familiar voice says:
                </p>

                <div class="memory">
                    <strong>
                        “I'm here.”
                    </strong>

                    You don't have to face the storm alone.
                </div>
            `,

            choices: [
                [
                    "🌩 Face the storm",
                    "stormFace"
                ],
                [
                    "🚀 Fly through it",
                    "stormFly"
                ],
                [
                    "♡ Follow the voice",
                    "stormVoice"
                ],
                [
                    "🌙 Wait until it passes",
                    "stormWait"
                ]
            ],

            stars: [
                "s9",
                "s10"
            ]
        },


        ocean: {

            title:
                "The Ocean",

            icon:
                "🌊",

            text: `
                <p>
                    The spaceship lands beside an endless ocean.
                </p>

                <p>
                    Lola steps onto the sand.
                </p>

                <p>
                    The waves roll gently towards her.
                </p>

                <p>
                    And beneath the water,
                    something moves.
                </p>

                <p>
                    A stingray glides through the blue.
                </p>

                <p>
                    For a moment,
                    the whole universe becomes quiet.
                </p>
            `,

            choices: [
                [
                    "🌊 Walk into the water",
                    "oceanWalk"
                ],
                [
                    "🐟 Follow the stingray",
                    "stingray"
                ],
                [
                    "🌅 Sit and watch the waves",
                    "oceanSit"
                ],
                [
                    "🚀 Return to the galaxy",
                    "map"
                ]
            ],

            stars: [
                "s11",
                "s12",
                "s13"
            ]
        },


        colour: {

            title:
                "Two Moons",

            icon:
                "💙",

            text: `
                <p>
                    Two moons hang above the planet.
                </p>

                <p>
                    One is soft baby blue.
                    The other is deep burgundy.
                </p>

                <p>
                    Together,
                    they illuminate everything beneath them.
                </p>

                <p>
                    A message appears:
                </p>

                <div class="memory">
                    <strong>
                        TWO DIFFERENT COLOURS.
                    </strong>

                    Somehow they still look right beside each other.
                </div>
            `,

            choices: [
                [
                    "💙 Touch the blue moon",
                    "blueMoon"
                ],
                [
                    "🍷 Touch the burgundy moon",
                    "burgundyMoon"
                ],
                [
                    "♡ Stand between them",
                    "betweenMoons"
                ]
            ],

            stars: [
                "s14",
                "s15"
            ]
        },


        gravity: {

            title:
                "Gravity",

            icon:
                "✦",

            text: `
                <p>
                    On this planet,
                    gravity works differently.
                </p>

                <p>
                    Lola floats several feet above the ground.
                </p>

                <p>
                    A hand reaches up towards her.
                </p>

                <p>
                    “Come here, short girl.”
                </p>

                <p>
                    Apparently the universe has decided
                    that height differences are funny.
                </p>
            `,

            choices: [
                [
                    "😂 Laugh and take the hand",
                    "gravityLaugh"
                ],
                [
                    "🫶 Let yourself fall",
                    "gravityFall"
                ],
                [
                    "🚀 Float away dramatically",
                    "gravityAway"
                ]
            ],

            stars: [
                "s16",
                "s17"
            ]
        },


        sunset: {

            title:
                "The Sunset Planet",

            icon:
                "🌅",

            text: `
                <p>
                    The sky turns gold,
                    pink and burgundy.
                </p>

                <p>
                    It feels strangely familiar.
                </p>

                <p>
                    There are no clocks here.
                    No deadlines.
                    Nothing that needs fixing.
                </p>

                <p>
                    Just a sunset
                    and someone beside you.
                </p>
            `,

            choices: [
                [
                    "🎨 Paint the sunset",
                    "painting"
                ],
                [
                    "🎵 Sing together",
                    "singing"
                ],
                [
                    "💃 Dance beneath it",
                    "dancing"
                ],
                [
                    "🌅 Sit quietly and watch",
                    "sunsetQuiet"
                ]
            ],

            stars: [
                "s18"
            ]
        },


        future: {

            title:
                "The Future",

            icon:
                "💍",

            text: `
                <p>
                    The spaceship enters a completely different
                    part of the galaxy.
                </p>

                <p>
                    The stars disappear.
                </p>

                <p>
                    In their place is a little countryside house,
                    surrounded by green fields.
                </p>

                <p>
                    There is a tree house in the distance.
                </p>

                <p>
                    And somewhere inside the house,
                    two wedding rings sit beside each other.
                </p>
            `,

            choices: [
                [
                    "💍 Walk towards the wedding",
                    "wedding"
                ],
                [
                    "🌳 Go to the tree house",
                    "treehouse"
                ],
                [
                    "🌾 Explore the countryside",
                    "countryside"
                ],
                [
                    "🎨 Enter the future studio",
                    "studio"
                ]
            ],

            stars: [
                "s25"
            ]
        },


        ouruniverse: {

            title:
                "Our Universe",

            icon:
                "♡",

            text: `
                <p>
                    Every planet begins disappearing.
                </p>

                <p>
                    The coffee.
                    The storms.
                    The ocean.
                    The sunsets.
                    The countryside.
                </p>

                <p>
                    Everything folds into one enormous galaxy.
                </p>

                <p>
                    At its centre is a single word.
                </p>

                <h2 style="text-align:center;">
                    HOME.
                </h2>

                <p>
                    But something is still missing.
                </p>

                <p>
                    The stars.
                </p>
            `,

            choices: [
                [
                    "⭐ Gather the stars",
                    "constellationCheck"
                ]
            ],

            stars: []
        }

    };

    const data =
        content[planet];

    if (!data) return;

    story(
        data.title,
        data.text,
        data.icon,
        data.choices,
        data.stars
    );
}


/* ==========================================================
   SPACESHIP
========================================================== */

function moveSpaceship(planet) {

    const positions = {

        beginning: ["20%","16%"],
        coffee: ["48%","10%"],
        hazel: ["82%","26%"],
        storm: ["12%","46%"],
        ocean: ["82%","52%"],
        colour: ["28%","82%"],
        gravity: ["68%","82%"],
        future: ["46%","88%"],
        sunset: ["4%","20%"],
        ouruniverse: ["87%","12%"]

    };

    const pos =
        positions[planet];

    if (!pos) return;

    const ship =
        document.getElementById(
            "spaceship"
        );

    ship.style.left =
        pos[0];

    ship.style.top =
        pos[1];
}


/* ==========================================================
   STORY ENGINE
========================================================== */

function story(
    title,
    text,
    icon,
    choices,
    stars = []
) {

    let starsHTML = "";

    const positions = [

        ["10%","16%"],
        ["78%","21%"],
        ["58%","75%"],
        ["25%","67%"],
        ["89%","57%"]

    ];

    stars.forEach(
        (id,index) => {

            if (
                !state.stars.includes(
                    id
                )
            ) {

                const pos =
                    positions[
                        index %
                        positions.length
                    ];

                starsHTML += `

                    <button
                        class="hidden-star"
                        style="
                            left:${pos[0]};
                            top:${pos[1]};
                        "
                        onclick="
                            collectStar(
                                '${id}',
                                this
                            )
                        "
                        title="A hidden star"
                    >
                        ✦
                    </button>

                `;
            }
        }
    );


    const choicesHTML =
        choices
            .map(
                choice => {

                    return `

                        <button
                            class="choice"
                            onclick="
                                storyChoice(
                                    '${choice[1]}'
                                )
                            "
                        >
                            ${choice[0]}
                        </button>

                    `;
                }
            )
            .join("");


    document.getElementById(
        "storyContent"
    ).innerHTML = `

        <div class="scene-art">

            <div
                style="
                    position:relative;
                    z-index:2;
                "
            >
                ${icon}
            </div>

            ${starsHTML}

        </div>

        <div class="eyebrow">
            A place between the stars
        </div>

        <h2>
            ${title}
        </h2>

        ${text}

        <div class="choice-container">
            ${choicesHTML}
        </div>

        <div
            style="
                margin-top:25px;
                text-align:center;
            "
        >

            <button
                class="primary"
                onclick="
                    showScreen('map')
                "
            >
                🚀 Return to galaxy
            </button>

        </div>

    `;

    showScreen(
        "story"
    );
}


/* ==========================================================
   COLLECT STAR
========================================================== */

function collectStar(
    id,
    element
) {

    if (
        state.stars.includes(id)
    ) {
        return;
    }

    state.stars.push(id);

    element.classList.add(
        "collected"
    );

    updateStarCounter();

    saveGame();

    showFoundStar();
}


function showFoundStar() {

    const popup =
        document.createElement(
            "div"
        );

    popup.className =
        "star-found";

    popup.innerHTML = `

        <div
            style="
                font-size:35px;
            "
        >
            ⭐
        </div>

        <strong>
            Star found!
        </strong>

        <div
            style="
                margin-top:6px;
                color:#d9c4ce;
            "
        >
            ${state.stars.length} / 27
        </div>

    `;

    document.body.appendChild(
        popup
    );

    setTimeout(
        () => {
            popup.remove();
        },
        1500
    );
}


/* ==========================================================
   ROUTING
========================================================== */

function storyChoice(
    destination
) {

    switch(destination) {

        case "map":
            showScreen("map");
            break;

        case "beginning":
            visitPlanet("beginning");
            break;

        case "coffee":
            visitPlanet("coffee");
            break;

        case "hazel":
            visitPlanet("hazel");
            break;

        case "storm":
            visitPlanet("storm");
            break;

        case "ocean":
            visitPlanet("ocean");
            break;

        case "colour":
            visitPlanet("colour");
            break;

        case "gravity":
            visitPlanet("gravity");
            break;

        case "sunset":
            visitPlanet("sunset");
            break;

        case "future":
            visitPlanet("future");
            break;

        case "ouruniverse":
            visitPlanet("ouruniverse");
            break;

        case "coffee2":
            coffeeSecond();
            break;

        case "coffee3":
            coffeeSearch();
            break;

        case "hazel2":
            hazelClose();
            break;

        case "hazel3":
            hazelFollow();
            break;

        case "stormFace":
            stormFace();
            break;

        case "stormFly":
            stormFly();
            break;

        case "stormVoice":
            stormVoice();
            break;

        case "stormWait":
            stormWait();
            break;

        case "oceanWalk":
            oceanWalk();
            break;

        case "stingray":
            stingray();
            break;

        case "oceanSit":
            oceanSit();
            break;

        case "blueMoon":
            blueMoon();
            break;

        case "burgundyMoon":
            burgundyMoon();
            break;

        case "betweenMoons":
            betweenMoons();
            break;

        case "gravityLaugh":
            gravityLaugh();
            break;

        case "gravityFall":
            gravityFall();
            break;

        case "gravityAway":
            gravityAway();
            break;

        case "painting":
            painting();
            break;

        case "singing":
            singing();
            break;

        case "dancing":
            dancing();
            break;

        case "sunsetQuiet":
            sunsetQuiet();
            break;

        case "wedding":
            wedding();
            break;

        case "treehouse":
            treehouse();
            break;

        case "countryside":
            countryside();
            break;

        case "studio":
            studio();
            break;

        case "constellationCheck":
            constellationCheck();
            break;
    }
}


/* ==========================================================
   COFFEE
========================================================== */

function coffeeSecond() {

    story(
        "The Coffee",
        `
        <p>
            Lola takes a sip.
        </p>

        <p>
            Black coffee.
        </p>

        <p>
            The strange thing is that the universe suddenly
            feels a little less lonely.
        </p>

        <p>
            On the table is another note:
        </p>

        <div class="memory">
            <strong>
                Some people feel like home
                before you've even met them.
            </strong>
        </div>
        `,
        "☕",
        [
            [
                "✦ Keep the note",
                "coffee3"
            ],
            [
                "🚀 Return to the galaxy",
                "map"
            ]
        ],
        ["s5"]
    );
}


function coffeeSearch() {

    story(
        "Something Hidden",
        `
        <p>
            Lola searches beneath the tables,
            behind the counter,
            and finally underneath the coffee cup.
        </p>

        <p>
            There is a tiny drawing of a girl.
        </p>

        <p>
            Brown hair.
            Brown eyes.
            A ridiculous number of words written around her.
        </p>

        <p>
            One sentence is circled:
        </p>

        <div class="memory">
            <strong>
                “She writes because sometimes
                love is too big to simply say.”
            </strong>
        </div>
        `,
        "✍️",
        [
            [
                "✦ Keep reading",
                "hazel"
            ],
            [
                "🚀 Return to the galaxy",
                "map"
            ]
        ],
        ["s6"]
    );
}


/* ==========================================================
   HAZEL
========================================================== */

function hazelClose() {

    story(
        "Hazel",
        `
        <p>
            Lola looks closer.
        </p>

        <p>
            The eyes are hazel.
            Warm.
            Familiar.
        </p>

        <p>
            For some reason,
            Lola feels like she has been searching
            for those eyes her entire life.
        </p>
        `,
        "👁",
        [
            [
                "✦ Follow the light",
                "hazel3"
            ],
            [
                "🚀 Return to the galaxy",
                "map"
            ]
        ],
        ["s7"]
    );
}


function hazelFollow() {

    story(
        "The Girl Behind the Stars",
        `
        <p>
            Lola follows the star.
        </p>

        <p>
            It leads her to a small room filled with poems.
        </p>

        <p>
            Every wall has another sentence written across it.
        </p>

        <p>
            One keeps appearing:
        </p>

        <div class="memory">
            <strong>
                “I like cats, sunsets,
                and my girlfriend Lola.”
            </strong>
        </div>

        <p>
            Lola realises that someone has been
            writing a universe around her.
        </p>
        `,
        "♡",
        [
            [
                "♡ Keep going",
                "storm"
            ],
            [
                "🚀 Return to the galaxy",
                "map"
            ]
        ],
        ["s8"]
    );
}


/* ==========================================================
   STORM
========================================================== */

function stormFace() {

    story(
        "Facing the Storm",
        `
        <p>
            Lola takes a breath.
        </p>

        <p>
            Thunder shakes the planet.
        </p>

        <p>
            But she keeps walking.
        </p>

        <p>
            Another little light appears ahead.
        </p>

        <div class="memory">
            <strong>
                You are stronger than the storm.
            </strong>
        </div>
        `,
        "🌩",
        [
            [
                "✦ Follow the light",
                "map"
            ],
            [
                "♡ Listen to the voice",
                "stormVoice"
            ]
        ],
        ["s9"]
    );
}


function stormFly() {

    story(
        "Through the Storm",
        `
        <p>
            Lola grips the spaceship controls.
        </p>

        <p>
            Lightning flashes around her.
        </p>

        <p>
            Then a voice comes through the radio.
        </p>

        <div class="memory">
            <strong>
                “I'm here. Count with me.”
            </strong>
        </div>

        <p>
            One.
            Two.
            Three...
        </p>
        `,
        "🚀",
        [
            [
                "♡ Keep listening",
                "stormVoice"
            ],
            [
                "✦ Follow the stars",
                "map"
            ]
        ],
        ["s10"]
    );
}


function stormVoice() {

    story(
        "I'm Here",
        `
        <p>
            Lola follows the voice.
        </p>

        <p>
            The storm doesn't disappear.
        </p>

        <p>
            But somehow it doesn't feel
            quite as frightening anymore.
        </p>

        <p>
            Because sometimes you don't need
            someone to stop the storm.
        </p>

        <p>
            Sometimes you just need someone who stays.
        </p>
        `,
        "♡",
        [
            [
                "🌌 Continue",
                "map"
            ],
            [
                "🌊 Find the ocean",
                "ocean"
            ]
        ],
        ["s22"]
    );
}


function stormWait() {

    story(
        "After the Storm",
        `
        <p>
            Lola waits.
        </p>

        <p>
            Eventually the thunder becomes quieter.
        </p>

        <p>
            The clouds part.
        </p>

        <p>
            And there, behind them,
            is a path of stars.
        </p>
        `,
        "✦",
        [
            [
                "✦ Follow the stars",
                "map"
            ],
            [
                "🌊 Follow the waves",
                "ocean"
            ]
        ],
        []
    );
}


/* ==========================================================
   OCEAN
========================================================== */

function oceanWalk() {

    story(
        "The Water",
        `
        <p>
            Lola walks into the ocean.
        </p>

        <p>
            The water reaches her ankles,
            then her knees.
        </p>

        <p>
            The entire ocean glows beneath her.
        </p>

        <p>
            She finally understands why some dreams
            are worth waiting for.
        </p>
        `,
        "🌊",
        [
            [
                "🐟 Follow the stingray",
                "stingray"
            ],
            [
                "🌅 Sit beside the water",
                "oceanSit"
            ]
        ],
        ["s11"]
    );
}


function stingray() {

    story(
        "The Stingray",
        `
        <p>
            A stingray glides beneath the water.
        </p>

        <p>
            Lola follows it.
        </p>

        <p>
            It leads her to a tiny glowing star
            beneath the surface.
        </p>

        <p>
            She reaches down and catches it.
        </p>

        <div class="memory">
            <strong>
                Some things are worth diving for.
            </strong>
        </div>
        `,
        "🐟",
        [
            [
                "🌊 Return to shore",
                "map"
            ],
            [
                "✦ Keep exploring",
                "oceanSit"
            ]
        ],
        ["s12"]
    );
}


function oceanSit() {

    story(
        "The Dream",
        `
        <p>
            Lola sits beside the ocean.
        </p>

        <p>
            The waves are quiet.
        </p>

        <p>
            Somewhere far away,
            someone is imagining this exact moment.
        </p>

        <p>
            Seeing the ocean together.
        </p>

        <p>
            Finally.
        </p>
        `,
        "🌊",
        [
            [
                "🌅 Watch the sunset",
                "sunset"
            ],
            [
                "🚀 Return to the galaxy",
                "map"
            ]
        ],
        ["s13"]
    );
}


/* ==========================================================
   TWO MOONS
========================================================== */

function blueMoon() {

    story(
        "Baby Blue",
        `
        <p>
            Lola touches the blue moon.
        </p>

        <p>
            It glows softly beneath her hand.
        </p>

        <p>
            It feels gentle.
            Calm.
            Like something familiar.
        </p>
        `,
        "💙",
        [
            [
                "🍷 Find the other moon",
                "burgundyMoon"
            ],
            [
                "♡ Stay here a little longer",
                "betweenMoons"
            ]
        ],
        ["s14"]
    );
}


function burgundyMoon() {

    story(
        "Burgundy",
        `
        <p>
            The second moon glows burgundy.
        </p>

        <p>
            Somehow,
            the two colours belong together.
        </p>

        <p>
            Not because they are the same.
            Because they aren't.
        </p>
        `,
        "🍷",
        [
            [
                "💙 Return to the blue moon",
                "blueMoon"
            ],
            [
                "♡ Stand between them",
                "betweenMoons"
            ]
        ],
        ["s15"]
    );
}


function betweenMoons() {

    story(
        "Between Two Moons",
        `
        <p>
            Lola stands between baby blue and burgundy.
        </p>

        <p>
            Two colours.
            Two people.
            One universe.
        </p>

        <p>
            Maybe love was never about being identical.
        </p>

        <p>
            Maybe it was always about finding someone
            whose differences somehow make the world
            feel more complete.
        </p>
        `,
        "♡",
        [
            [
                "✦ Continue",
                "map"
            ],
            [
                "🚀 Return to the galaxy",
                "map"
            ]
        ],
        []
    );
}


/* ==========================================================
   GRAVITY
========================================================== */

function gravityLaugh() {

    story(
        "Gravity",
        `
        <p>
            Lola laughs.
        </p>

        <p>
            Apparently someone being 5'10
            and someone being around 5'1
            is enough for the universe
            to create its own gravitational joke.
        </p>

        <p>
            A hand reaches up again.
        </p>
        `,
        "😂",
        [
            [
                "🫶 Take the hand",
                "gravityFall"
            ],
            [
                "🚀 Float dramatically away",
                "gravityAway"
            ]
        ],
        ["s16"]
    );
}


function gravityFall() {

    story(
        "Come Here",
        `
        <p>
            Lola lets herself fall.
        </p>

        <p>
            Instead of hitting the ground,
            she lands safely in someone's arms.
        </p>

        <p>
            For once,
            gravity feels like something gentle.
        </p>
        `,
        "🫶",
        [
            [
                "♡ Stay there",
                "sunset"
            ],
            [
                "😂 Laugh about it",
                "gravityLaugh"
            ]
        ],
        ["s17"]
    );
}


function gravityAway() {

    story(
        "The Dramatic Escape",
        `
        <p>
            Lola floats away dramatically.
        </p>

        <p>
            Somewhere below her,
            someone yells:
        </p>

        <div class="memory">
            <strong>
                “COME BACK HERE.”
            </strong>
        </div>

        <p>
            Lola laughs.
        </p>
        `,
        "🚀",
        [
            [
                "😂 Go back",
                "gravityLaugh"
            ],
            [
                "🌅 Fly towards the sunset",
                "sunset"
            ]
        ],
        []
    );
}


/* ==========================================================
   SUNSET
========================================================== */

function painting() {

    story(
        "Painting Together",
        `
        <p>
            Lola picks up a paintbrush.
        </p>

        <p>
            The sunset becomes a canvas.
        </p>

        <p>
            Two people sit beside each other,
            getting paint everywhere except
            where it was supposed to go.
        </p>

        <p>
            Somehow,
            the painting turns out beautiful anyway.
        </p>
        `,
        "🎨",
        [
            [
                "🎵 Put on music",
                "singing"
            ],
            [
                "💃 Dance instead",
                "dancing"
            ]
        ],
        ["s19"]
    );
}


function singing() {

    story(
        "The Song",
        `
        <p>
            Someone starts singing.
        </p>

        <p>
            Lola joins in.
        </p>

        <p>
            Neither of them gets every note right.
        </p>

        <p>
            Eventually they're laughing too much
            to finish the song.
        </p>

        <p>
            And somehow that makes it perfect.
        </p>
        `,
        "🎵",
        [
            [
                "💃 Dance anyway",
                "dancing"
            ],
            [
                "🎨 Go back to painting",
                "painting"
            ]
        ],
        ["s20"]
    );
}


function dancing() {

    story(
        "Dancing",
        `
        <p>
            There is no music anymore.
        </p>

        <p>
            So they make their own.
        </p>

        <p>
            Two people dancing beneath a galaxy,
            barefoot on warm grass,
            laughing like nobody else exists.
        </p>
        `,
        "💃",
        [
            [
                "🌾 Keep dancing into the countryside",
                "countryside"
            ],
            [
                "🌅 Sit down together",
                "sunsetQuiet"
            ]
        ],
        ["s21"]
    );
}


function sunsetQuiet() {

    story(
        "Nothing At All",
        `
        <p>
            They sit together.
        </p>

        <p>
            No big adventure.
            No dramatic moment.
        </p>

        <p>
            Just being there.
        </p>

        <p>
            Sometimes that is enough.
        </p>
        `,
        "♡",
        [
            [
                "🌌 Continue",
                "map"
            ],
            [
                "💍 Look towards the future",
                "future"
            ]
        ],
        []
    );
}


/* ==========================================================
   FUTURE
========================================================== */

function wedding() {

    story(
        "The Wedding",
        `
        <p>
            The countryside is glowing
            beneath a warm afternoon sky.
        </p>

        <p>
            Lola walks towards the person waiting for her.
        </p>

        <p>
            There are flowers everywhere.
        </p>

        <p>
            And when Lola reaches the end of the path,
            one word echoes through the universe:
        </p>

        <h2 style="text-align:center;">
            WIFE.
        </h2>

        <p>
            Not a dream anymore.
            A future.
        </p>
        `,
        "💍",
        [
            [
                "💍 Say “I do”",
                "weddingVows"
            ],
            [
                "♡ Look at her and laugh",
                "weddingLaugh"
            ],
            [
                "🌸 Take in the moment",
                "weddingQuiet"
            ]
        ],
        ["s26"]
    );
}


function weddingVows() {

    story(
        "I Do",
        `
        <p>
            Lola says yes.
        </p>

        <p>
            And suddenly every little future
            they've ever imagined feels a little closer.
        </p>

        <p>
            The countryside house.
            The tree house.
            The mornings.
            The paintings.
            The songs.
            The ocean.
        </p>

        <p>
            A whole life.
        </p>
        `,
        "💍",
        [
            [
                "🌳 Go see the tree house",
                "treehouse"
            ],
            [
                "🌾 Walk through the countryside",
                "countryside"
            ]
        ],
        []
    );
}


function weddingLaugh() {

    story(
        "The Wedding Laugh",
        `
        <p>
            Instead of being perfectly serious,
            Lola laughs.
        </p>

        <p>
            And the person standing opposite her
            laughs too.
        </p>

        <p>
            Because even on the biggest day of their lives,
            they're still themselves.
        </p>
        `,
        "♡",
        [
            [
                "💍 Say yes",
                "weddingVows"
            ],
            [
                "🌳 Run towards the tree house",
                "treehouse"
            ]
        ],
        []
    );
}


function weddingQuiet() {

    story(
        "The Moment",
        `
        <p>
            Lola takes a breath.
        </p>

        <p>
            She looks around.
        </p>

        <p>
            And realises this is the kind of happiness
            she always hoped existed somewhere.
        </p>
        `,
        "🌸",
        [
            [
                "💍 Say yes",
                "weddingVows"
            ],
            [
                "🌾 Walk outside",
                "countryside"
            ]
        ],
        []
    );
}


/* ==========================================================
   TREE HOUSE
========================================================== */

function treehouse() {

    story(
        "The Tree House",
        `
        <p>
            Behind the little countryside house
            stands an enormous tree.
        </p>

        <p>
            Built into its branches is a tree house.
        </p>

        <p>
            It has blankets.
            Fairy lights.
            Books.
            Paintings.
            And a window overlooking the fields.
        </p>

        <p>
            This is the place where all
            the quiet evenings happen.
        </p>
        `,
        "🌳",
        [
            [
                "🌌 Look at the stars",
                "treeStars"
            ],
            [
                "🎨 Paint together",
                "treePaint"
            ],
            [
                "☕ Bring coffee upstairs",
                "treeCoffee"
            ]
        ],
        ["s27"]
    );
}


function treeStars() {

    story(
        "Under the Stars",
        `
        <p>
            Lola lies beneath the little roof
            of the tree house.
        </p>

        <p>
            Above her are thousands of stars.
        </p>

        <p>
            Beside her is the person she loves.
        </p>

        <p>
            Nothing needs to happen.
        </p>

        <p>
            They can simply grow old
            beneath the same sky.
        </p>
        `,
        "🌌",
        [
            [
                "🌾 Go back to the house",
                "countryside"
            ],
            [
                "💍 Think about the future",
                "future"
            ]
        ],
        ["s23"]
    );
}


function treePaint() {

    story(
        "Another Painting",
        `
        <p>
            They paint the countryside together.
        </p>

        <p>
            The first painting is terrible.
        </p>

        <p>
            The second one is somehow worse.
        </p>

        <p>
            They keep both anyway.
        </p>
        `,
        "🎨",
        [
            [
                "☕ Make coffee",
                "treeCoffee"
            ],
            [
                "🌾 Go outside",
                "countryside"
            ]
        ],
        []
    );
}


function treeCoffee() {

    story(
        "Morning Coffee",
        `
        <p>
            Two cups of coffee.
        </p>

        <p>
            One tree house.
        </p>

        <p>
            Morning sunlight through the leaves.
        </p>

        <p>
            And the quiet realisation
            that this is home.
        </p>
        `,
        "☕",
        [
            [
                "🌾 Walk through the fields",
                "countryside"
            ],
            [
                "🌌 Stay here all morning",
                "treeStars"
            ]
        ],
        []
    );
}


/* ==========================================================
   COUNTRYSIDE
========================================================== */

function countryside() {

    story(
        "The Countryside",
        `
        <p>
            Green fields stretch towards the horizon.
        </p>

        <p>
            The little house sits quietly in the middle of it all.
        </p>

        <p>
            There is no rush here.
        </p>

        <p>
            Just two people building a life together.
        </p>
        `,
        "🌾",
        [
            [
                "🌅 Watch the sunset",
                "countrySunset"
            ],
            [
                "🌳 Visit the tree house",
                "treehouse"
            ],
            [
                "🏠 Go inside your home",
                "marriedLife"
            ]
        ],
        ["s24"]
    );
}


function countrySunset() {

    story(
        "A Quiet Evening",
        `
        <p>
            The sun disappears behind the fields.
        </p>

        <p>
            Lola reaches for a hand beside her.
        </p>

        <p>
            Years from now,
            this will still be one of their favourite moments.
        </p>
        `,
        "🌅",
        [
            [
                "🏠 Go home",
                "marriedLife"
            ],
            [
                "🌳 Go to the tree house",
                "treehouse"
            ]
        ],
        []
    );
}


function marriedLife() {

    story(
        "Married Life",
        `
        <p>
            Morning.
        </p>

        <p>
            The house is quiet.
        </p>

        <p>
            Lola wakes beside the person she married.
        </p>

        <p>
            There is coffee waiting.
        </p>

        <p>
            Somewhere downstairs,
            music starts playing.
        </p>

        <p>
            Someone begins dancing
            while cooking breakfast.
        </p>

        <p>
            Lola laughs.
        </p>

        <p>
            This is not some enormous fairytale.
        </p>

        <p>
            It's better.
        </p>

        <p>
            It's ordinary.
            It's theirs.
        </p>
        `,
        "🏠",
        [
            [
                "💃 Dance in the kitchen",
                "marriedDance"
            ],
            [
                "🎨 Paint together",
                "marriedPaint"
            ],
            [
                "🎵 Sing together",
                "marriedSing"
            ],
            [
                "☕ Do absolutely nothing",
                "marriedNothing"
            ]
        ],
        []
    );
}


function marriedDance() {

    story(
        "Kitchen Dancing",
        `
        <p>
            Breakfast is forgotten.
        </p>

        <p>
            The music gets louder.
        </p>

        <p>
            Two people dance around the kitchen,
            laughing until they can barely stand.
        </p>
        `,
        "💃",
        [
            [
                "☕ Eventually make breakfast",
                "marriedLife"
            ],
            [
                "♡ Keep dancing",
                "marriedLife"
            ]
        ],
        []
    );
}


function marriedPaint() {

    story(
        "The Studio",
        `
        <p>
            Paint covers the table.
        </p>

        <p>
            There are unfinished canvases everywhere.
        </p>

        <p>
            Some are beautiful.
            Some are questionable.
        </p>

        <p>
            All of them belong to a life
            they built together.
        </p>
        `,
        "🎨",
        [
            [
                "♡ Look around the room",
                "studio"
            ],
            [
                "🏠 Go back home",
                "marriedLife"
            ]
        ],
        []
    );
}


function marriedSing() {

    story(
        "Singing",
        `
        <p>
            They sing badly.
        </p>

        <p>
            They know they sing badly.
        </p>

        <p>
            They don't care.
        </p>

        <p>
            Because happiness doesn't have to sound perfect.
        </p>
        `,
        "🎵",
        [
            [
                "💃 Dance too",
                "marriedDance"
            ],
            [
                "☕ Make coffee",
                "marriedLife"
            ]
        ],
        []
    );
}


function marriedNothing() {

    story(
        "Nothing",
        `
        <p>
            They stay on the sofa.
        </p>

        <p>
            No plans.
            No adventure.
            No reason to get up.
        </p>

        <p>
            Just each other.
        </p>

        <p>
            Sometimes a happy life is simply
            having someone you want to do nothing with.
        </p>
        `,
        "♡",
        [
            [
                "🌌 Look outside at the stars",
                "future"
            ],
            [
                "🏠 Stay home",
                "marriedLife"
            ]
        ],
        []
    );
}


/* ==========================================================
   FUTURE STUDIO
========================================================== */

function studio() {

    story(
        "The Future Studio",
        `
        <p>
            The studio is covered in memories.
        </p>

        <p>
            Paintings.
            Photographs.
            Little notes.
            Tickets from places you've visited.
        </p>

        <p>
            On the wall is a blank canvas.
        </p>

        <p>
            A message is written beneath it:
        </p>

        <div class="memory">
            <strong>
                THIS ONE IS FOR EVERYTHING
                WE HAVEN'T DONE YET.
            </strong>
        </div>
        `,
        "🎨",
        [
            [
                "🎨 Start painting",
                "studioPaint"
            ],
            [
                "♡ Leave it blank for now",
                "studioBlank"
            ],
            [
                "🏠 Go home",
                "marriedLife"
            ]
        ],
        []
    );
}


function studioPaint() {

    story(
        "The Unfinished Painting",
        `
        <p>
            Lola picks up a brush.
        </p>

        <p>
            The first colour is baby blue.
        </p>

        <p>
            The second is burgundy.
        </p>

        <p>
            Then gold.
            Then green.
            Then every colour they can find.
        </p>

        <p>
            Because the future isn't finished yet.
        </p>

        <p>
            There are still so many things left to create.
        </p>
        `,
        "🎨",
        [
            [
                "♡ Keep the painting unfinished",
                "studioBlank"
            ],
            [
                "🌌 Return to the galaxy",
                "map"
            ]
        ],
        []
    );
}


function studioBlank() {

    story(
        "Not Yet",
        `
        <p>
            Lola leaves the canvas blank.
        </p>

        <p>
            Not because there is nothing to say.
        </p>

        <p>
            Because there is still so much left to live.
        </p>

        <p>
            The best parts haven't happened yet.
        </p>
        `,
        "♡",
        [
            [
                "🌌 Return to the galaxy",
                "map"
            ],
            [
                "💍 Look towards the future",
                "future"
            ]
        ],
        []
    );
}


/* ==========================================================
   FINAL CONSTELLATION
========================================================== */

function constellationCheck() {

    updateStarCounter();

    if (
        state.stars.length < 27
    ) {

        story(
            "Not Yet",
            `
            <p>
                The universe waits.
            </p>

            <p>
                The constellation is incomplete.
            </p>

            <p>
                You have found
                <strong>
                    ${state.stars.length}
                </strong>
                out of 27 stars.
            </p>

            <p>
                There are still stars hiding somewhere
                in the galaxy.
            </p>

            <div class="memory">
                <strong>
                    Look carefully.
                </strong>

                Try revisiting planets.
                Some stars only appear in certain
                parts of the story.
            </div>
            `,
            "⭐",
            [
                [
                    "🚀 Return to the galaxy",
                    "map"
                ]
            ],
            []
        );

        return;
    }

    state.completed = true;

    saveGame();

    createConstellation();

    showScreen(
        "constellationScreen"
    );
}


/* ==========================================================
   CONSTELLATION
========================================================== */

function createConstellation() {

    const box =
        document.getElementById(
            "constellation"
        );

    box.innerHTML = "";

    const positions = [

        [8,25],
        [16,40],
        [25,18],
        [34,32],
        [43,12],
        [51,28],
        [59,16],
        [68,36],
        [78,21],
        [88,33],
        [13,60],
        [22,74],
        [32,57],
        [42,70],
        [52,52],
        [61,72],
        [70,56],
        [80,70],
        [90,55],
        [18,88],
        [31,84],
        [44,91],
        [56,84],
        [68,91],
        [79,82],
        [90,91],
        [50,43]

    ];

    positions.forEach(
        (position,index) => {

            const star =
                document.createElement(
                    "div"
                );

            star.className =
                "constellation-star";

            star.style.left =
                position[0] + "%";

            star.style.top =
                position[1] + "%";

            star.title =
                "Star " +
                (index + 1);

            box.appendChild(
                star
            );
        }
    );


    for (
        let i = 0;
        i < positions.length - 1;
        i++
    ) {

        const a =
            positions[i];

        const b =
            positions[i + 1];

        const x1 = a[0];
        const y1 = a[1];

        const x2 = b[0];
        const y2 = b[1];

        const dx =
            x2 - x1;

        const dy =
            y2 - y1;

        const length =
            Math.sqrt(
                dx * dx +
                dy * dy
            );

        const angle =
            Math.atan2(
                dy,
                dx
            ) *
            180 /
            Math.PI;

        const line =
            document.createElement(
                "div"
            );

        line.className =
            "constellation-line";

        line.style.left =
            x1 + "%";

        line.style.top =
            y1 + "%";

        line.style.width =
            length + "%";

        line.style.transform =
            `rotate(${angle}deg)`;

        box.appendChild(
            line
        );
    }
}


/* ==========================================================
   FINAL LETTER / REVEAL
========================================================== */

function showFinalLetter() {

    showScreen(
        "letterScreen"
    );
}


function showStarReveal() {

    showScreen(
        "starReveal"
    );
}


/* ==========================================================
   RESET
========================================================== */

function resetGame() {

    const confirmed =
        confirm(
            "Start the entire universe again? Your 27 collected stars will be reset."
        );

    if (!confirmed) {
        return;
    }

    localStorage.removeItem(
        SAVE_KEY
    );

    state = {

        stars: [],

        visited: [],

        path: [],

        completed: false

    };

    updateStarCounter();

    updateVisitedPlanets();

    showScreen(
        "intro"
    );
}


/* ==========================================================
   BACKGROUND STARS
========================================================== */

function createBackgroundStars() {

    const container =
        document.getElementById(
            "backgroundStars"
        );

    for (
        let i = 0;
        i < 180;
        i++
    ) {

        const star =
            document.createElement(
                "div"
            );

        star.className =
            "bg-star";

        star.style.left =
            Math.random() *
            100 +
            "%";

        star.style.top =
            Math.random() *
            100 +
            "%";

        star.style.animationDelay =
            Math.random() *
            4 +
            "s";

        star.style.opacity =
            .2 +
            Math.random() *
            .7;

        container.appendChild(
            star
        );
    }
}


/* ==========================================================
   INITIALISE
========================================================== */

createBackgroundStars();

loadGame();

</script>

</body>
</html>
