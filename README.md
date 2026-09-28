<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>The Places Between Us</title>

<style>

/* =========================================================
   CORE
========================================================= */

*{
    box-sizing:border-box;
}

html,
body{
    margin:0;
    padding:0;
    width:100%;
    min-height:100%;
    background:#020817;
    color:#fff;
    font-family:Georgia,"Times New Roman",serif;
    overflow-x:hidden;
}

body{
    min-height:100vh;
}

button{
    font-family:inherit;
}


/* =========================================================
   SPACE
========================================================= */

#space{
    position:fixed;
    inset:0;
    z-index:-10;

    background:
        radial-gradient(
            circle at 50% 35%,
            rgba(45,95,150,.55),
            rgba(5,22,48,.8) 35%,
            #020817 75%
        );
}

#stars{
    position:fixed;
    inset:0;
    z-index:-8;
    pointer-events:none;
}

.star{
    position:absolute;
    width:2px;
    height:2px;
    border-radius:50%;
    background:white;
    opacity:.65;
    animation:twinkle 3s ease-in-out infinite;
}

.star:nth-child(4n){
    width:3px;
    height:3px;
}

@keyframes twinkle{

    0%,100%{
        opacity:.3;
    }

    50%{
        opacity:1;
    }

}


/* =========================================================
   FLOATING STINGRAYS
========================================================= */

.stingray{
    position:fixed;
    z-index:-3;
    font-size:42px;
    opacity:.18;
    pointer-events:none;

    animation:
        swimAcross 18s linear infinite;
}

.stingray.two{
    animation-delay:7s;
    animation-duration:23s;
    font-size:30px;
}

@keyframes swimAcross{

    0%{
        left:-10%;
        top:75%;
        transform:rotate(5deg);
    }

    50%{
        left:50%;
        top:65%;
        transform:rotate(-8deg);
    }

    100%{
        left:110%;
        top:75%;
        transform:rotate(6deg);
    }

}


/* =========================================================
   APP
========================================================= */

#app{
    width:100%;
    min-height:100vh;
}


/* =========================================================
   SCREENS
========================================================= */

.screen{
    min-height:100vh;
    width:100%;

    display:none;

    justify-content:center;
    align-items:center;

    padding:
        80px
        20px
        50px;

    animation:fadeIn .7s ease;
}

.screen.active{
    display:flex;
}

@keyframes fadeIn{

    from{
        opacity:0;
        transform:translateY(12px);
    }

    to{
        opacity:1;
        transform:translateY(0);
    }

}


/* =========================================================
   CARD
========================================================= */

.card{
    width:min(1000px,100%);

    padding:
        clamp(25px,5vw,60px);

    border-radius:32px;

    background:
        linear-gradient(
            145deg,
            rgba(10,35,70,.88),
            rgba(4,15,32,.9)
        );

    border:
        1px solid
        rgba(170,220,255,.25);

    box-shadow:
        0 30px 100px rgba(0,0,0,.55),
        inset 0 0 70px rgba(130,200,255,.035);

    backdrop-filter:blur(15px);

    text-align:center;
}


/* =========================================================
   TYPOGRAPHY
========================================================= */

.eyebrow{
    color:#a9ddff;
    letter-spacing:4px;
    text-transform:uppercase;
    font-size:.75rem;
}

h1{
    font-size:
        clamp(3rem,9vw,7rem);

    line-height:.9;

    margin:
        25px 0;

    text-shadow:
        0 0 40px
        rgba(150,220,255,.45);
}

h2{
    font-size:
        clamp(2rem,6vw,4rem);

    margin:
        10px 0 20px;
}

h3{
    color:#a9ddff;
}

p{
    max-width:720px;
    margin:
        16px auto;

    font-size:
        clamp(1rem,2.5vw,1.2rem);

    line-height:1.8;

    color:#eaf6ff;
}

.muted{
    color:#a8c6dc;
    font-size:.95rem;
}


/* =========================================================
   BUTTONS
========================================================= */

.button-row{
    display:flex;
    flex-wrap:wrap;
    justify-content:center;
    gap:12px;
    margin-top:30px;
}

.btn{
    padding:
        14px 22px;

    border-radius:999px;

    border:
        1px solid
        rgba(170,220,255,.35);

    background:
        rgba(130,200,255,.09);

    color:white;

    cursor:pointer;

    transition:
        transform .2s,
        background .2s,
        box-shadow .2s;
}

.btn:hover{
    transform:translateY(-3px);

    background:
        rgba(150,215,255,.18);

    box-shadow:
        0 0 25px
        rgba(150,215,255,.18);
}

.btn.primary{
    background:
        linear-gradient(
            135deg,
            #b8e7ff,
            #6d9dd0
        );

    color:#06152b;

    border:none;

    font-weight:bold;
}

.btn.burgundy{
    background:
        rgba(111,39,73,.65);

    border-color:
        rgba(255,190,220,.3);
}


/* =========================================================
   HUD
========================================================= */

#hud{
    position:fixed;
    top:14px;
    left:50%;

    transform:translateX(-50%);

    width:
        min(1050px,calc(100% - 24px));

    display:none;

    justify-content:space-between;
    gap:10px;

    z-index:100;
}

.hud-item{
    padding:
        8px 14px;

    border-radius:999px;

    background:
        rgba(2,12,27,.8);

    border:
        1px solid
        rgba(160,220,255,.22);

    backdrop-filter:blur(10px);

    color:#b9d9ee;

    font-size:.78rem;
}


/* =========================================================
   GALAXY MAP
========================================================= */

.galaxy{
    position:relative;

    width:100%;
    max-width:900px;

    height:
        min(600px,72vh);

    min-height:480px;

    margin:
        30px auto;

    overflow:hidden;

    border-radius:30px;

    background:
        radial-gradient(
            circle at center,
            rgba(55,100,160,.15),
            transparent 65%
        );

    border:
        1px solid
        rgba(150,220,255,.12);
}


/* orbit lines */

.orbit{
    position:absolute;

    left:50%;
    top:50%;

    transform:
        translate(-50%,-50%);

    border:
        1px solid
        rgba(150,210,255,.12);

    border-radius:50%;
}

.orbit.one{
    width:230px;
    height:130px;
}

.orbit.two{
    width:430px;
    height:250px;
}

.orbit.three{
    width:650px;
    height:380px;
}

.orbit.four{
    width:850px;
    height:500px;
}


/* sun */

.sun{
    position:absolute;

    left:50%;
    top:50%;

    transform:
        translate(-50%,-50%);

    width:85px;
    height:85px;

    border-radius:50%;

    background:
        radial-gradient(
            circle,
            #fff,
            #a9ddff 45%,
            #4774a7 75%,
            transparent
        );

    box-shadow:
        0 0 50px
        rgba(150,220,255,.7);
}


/* planets */

.planet{
    position:absolute;

    width:105px;
    height:105px;

    border-radius:50%;

    display:flex;

    align-items:center;
    justify-content:center;

    text-align:center;

    cursor:pointer;

    border:
        1px solid
        rgba(190,230,255,.35);

    transition:
        transform .25s,
        box-shadow .25s;

    box-shadow:
        0 0 30px
        rgba(80,160,220,.18);
}

.planet:hover{
    transform:scale(1.12);

    box-shadow:
        0 0 45px
        rgba(150,220,255,.35);
}

.planet small{
    display:block;
    font-size:.75rem;
    padding:10px;
}

.planet.visited{
    box-shadow:
        0 0 40px
        rgba(170,220,255,.4);
}

.p1{
    left:8%;
    top:16%;

    background:
        radial-gradient(
            circle at 35% 30%,
            #dff6ff,
            #759cc4 40%,
            #203b61 75%
        );
}

.p2{
    right:10%;
    top:12%;

    background:
        radial-gradient(
            circle at 35% 30%,
            #dbc4d0,
            #6f2749 45%,
            #241124 80%
        );
}

.p3{
    left:20%;
    bottom:12%;

    background:
        radial-gradient(
            circle at 35% 30%,
            #d2ecff,
            #527ea9 42%,
            #122b4b 78%
        );
}

.p4{
    right:22%;
    bottom:9%;

    background:
        radial-gradient(
            circle at 35% 30%,
            #f1ddff,
            #7b6ba9 42%,
            #251d48 80%
        );
}

.p5{
    left:50%;
    top:8%;

    transform:translateX(-50%);

    background:
        radial-gradient(
            circle at 35% 30%,
            #fff1c9,
            #b5894c 40%,
            #382614 80%
        );
}

.p5:hover{
    transform:
        translateX(-50%)
        scale(1.12);
}


/* =========================================================
   MAP MESSAGE
========================================================= */

.map-message{
    min-height:70px;
    display:flex;
    align-items:center;
    justify-content:center;
}


/* =========================================================
   CHOICE CARDS
========================================================= */

.choices{
    display:grid;

    grid-template-columns:
        repeat(auto-fit,minmax(210px,1fr));

    gap:14px;

    margin-top:28px;
}

.choice{
    padding:20px;

    border-radius:20px;

    background:
        rgba(4,17,35,.65);

    border:
        1px solid
        rgba(150,220,255,.18);

    color:white;

    text-align:left;

    cursor:pointer;

    transition:.2s;
}

.choice:hover{
    transform:translateY(-3px);

    border-color:
        rgba(170,225,255,.5);

    background:
        rgba(100,170,220,.13);
}

.choice-title{
    color:#a9ddff;

    font-size:1.05rem;

    margin-bottom:7px;
}

.choice-description{
    color:#a9c7db;

    font-size:.9rem;

    line-height:1.5;
}


/* =========================================================
   SCENE
========================================================= */

.scene-icon{
    font-size:5rem;

    margin-bottom:5px;

    filter:
        drop-shadow(
            0 0 25px
            rgba(170,220,255,.4)
        );
}

.scene-text{
    max-width:720px;
    margin:auto;
}


/* =========================================================
   OCEAN
========================================================= */

.ocean{
    position:relative;

    height:300px;

    margin:
        30px auto;

    border-radius:25px;

    overflow:hidden;

    background:
        linear-gradient(
            #8bd3ff 0%,
            #3f91bd 42%,
            #0c4262 100%
        );
}

.moon{
    position:absolute;

    width:75px;
    height:75px;

    border-radius:50%;

    background:#e9f8ff;

    right:12%;
    top:12%;

    box-shadow:
        0 0 40px
        rgba(220,245,255,.8);
}

.wave{
    position:absolute;

    bottom:-10px;

    width:200%;

    height:100px;

    background:
        rgba(255,255,255,.14);

    border-radius:50% 50% 0 0;

    animation:wave 6s ease-in-out infinite;
}

@keyframes wave{

    50%{
        transform:translateX(-4%);
    }

}

.ocean-ray{
    position:absolute;

    font-size:60px;

    left:-100px;
    top:48%;

    animation:
        oceanRay 9s linear infinite;
}

@keyframes oceanRay{

    0%{
        left:-100px;
        transform:rotate(8deg);
    }

    100%{
        left:110%;
        transform:rotate(-8deg);
    }

}


/* =========================================================
   TREEHOUSE
========================================================= */

.treehouse{
    position:relative;

    height:320px;

    margin:30px auto;

    border-radius:25px;

    overflow:hidden;

    background:
        linear-gradient(
            #91caff,
            #d8edff 55%,
            #739c5c 56%,
            #365b32
        );
}

.tree{
    position:absolute;

    bottom:0;
    left:12%;

    font-size:220px;

    line-height:.7;
}

.house{
    position:absolute;

    left:50%;
    top:32%;

    transform:translateX(-50%);

    font-size:100px;

    filter:
        drop-shadow(
            0 15px 20px
            rgba(0,0,0,.3)
        );
}


/* =========================================================
   LETTER
========================================================= */

.letter{
    text-align:left;

    max-height:60vh;

    overflow:auto;

    padding:30px;

    border-radius:22px;

    background:
        rgba(255,255,255,.055);

    border:
        1px solid
        rgba(255,255,255,.12);
}

.letter p{
    font-size:1.05rem;
}

.signature{
    text-align:right;

    color:#a9ddff;
}


/* =========================================================
   STAR COLLECTION
========================================================= */

.star-board{
    display:grid;

    grid-template-columns:
        repeat(9,1fr);

    gap:9px;

    max-width:600px;

    margin:
        30px auto;
}

.collect-star{
    width:100%;
    aspect-ratio:1;

    border-radius:50%;

    border:0;

    background:
        rgba(255,255,255,.025);

    color:
        rgba(255,255,255,.18);

    font-size:1.3rem;

    cursor:pointer;

    transition:.2s;
}

.collect-star:hover{
    transform:scale(1.15);
}

.collect-star.found{
    color:#a9ddff;

    background:
        rgba(160,220,255,.1);

    text-shadow:
        0 0 15px
        #a9ddff;
}


/* =========================================================
   FINAL STAR
========================================================= */

.final-star{
    font-size:7rem;

    animation:
        starPulse 2s ease-in-out infinite;

    filter:
        drop-shadow(
            0 0 35px
            rgba(180,230,255,.9)
        );
}

@keyframes starPulse{

    50%{
        transform:scale(1.13);
    }

}


/* =========================================================
   PROGRESS
========================================================= */

.progress{
    width:100%;
    max-width:600px;

    height:5px;

    background:
        rgba(255,255,255,.08);

    border-radius:999px;

    margin:
        20px auto;
}

.progress-fill{
    height:100%;

    width:0%;

    border-radius:999px;

    background:
        linear-gradient(
            90deg,
            #a9ddff,
            #d7efff
        );

    transition:
        width .5s ease;
}


/* =========================================================
   MOBILE
========================================================= */

@media(max-width:600px){

    .screen{
        padding:
            75px
            12px
            30px;
    }

    .card{
        border-radius:22px;
        padding:24px 18px;
    }

    .galaxy{
        min-height:500px;
        height:65vh;
    }

    .planet{
        width:82px;
        height:82px;
    }

    .sun{
        width:65px;
        height:65px;
    }

    .orbit.one{
        width:180px;
        height:110px;
    }

    .orbit.two{
        width:330px;
        height:210px;
    }

    .orbit.three{
        width:500px;
        height:330px;
    }

    .orbit.four{
        width:650px;
        height:450px;
    }

    .star-board{
        grid-template-columns:
            repeat(7,1fr);
    }

}


/* =========================================================
   ACCESSIBILITY
========================================================= */

button:focus-visible{
    outline:
        2px solid #a9ddff;

    outline-offset:3px;
}

</style>
</head>


<body>


<!-- =======================================================
     BACKGROUND
======================================================= -->

<div id="space"></div>

<div id="stars"></div>

<div class="stingray">
    🪽
</div>

<div class="stingray two">
    🪽
</div>


<!-- =======================================================
     HUD
======================================================= -->

<div id="hud">

    <div class="hud-item" id="chapterHud">
        Chapter 1
    </div>

    <div class="hud-item">
        ⭐
        <span id="starCount">0</span>/27
    </div>

</div>


<!-- =======================================================
     APP
======================================================= -->

<div id="app"></div>


<script>

/* =========================================================
   GAME STATE
========================================================= */

const game = {

    chapter:0,

    visited:new Set(),

    stars:new Set(),

    choices:{

        firstStep:null,

        storm:null,

        future:null,

        ocean:null

    },

    messages:[],

    unlockedFinal:false

};


/* =========================================================
   STAR MESSAGES
========================================================= */

const starMessages = [

    "I love the way you make ordinary conversations feel important.",

    "Your hazel eyes are one of my favourite places.",

    "I love the little things that make you you.",

    "You deserve softness.",

    "You make distance feel smaller.",

    "I love imagining our future.",

    "I want to dance with you.",

    "I want to sing with you.",

    "I want to paint with you.",

    "I want to see the ocean with you.",

    "I want our tree house.",

    "I want the countryside with you.",

    "I love your voice.",

    "I love the calm you bring.",

    "I love learning every little thing about you.",

    "I am incredibly proud of you.",

    "You are my favourite person.",

    "You are loved on the ordinary days too.",

    "Baby blue belongs in our sky.",

    "There are still so many stories for us to write.",

    "I would find you across galaxies.",

    "You feel like home.",

    "You are everything and somehow still more.",

    "There are still so many mornings ahead.",

    "There are still so many sunsets.",

    "There are still so many songs.",

    "Happy 27th birthday, my love."

];


/* =========================================================
   CREATE BACKGROUND STARS
========================================================= */

function createStars(){

    const container =
        document.getElementById("stars");

    for(let i=0;i<180;i++){

        const star =
            document.createElement("div");

        star.className="star";

        star.style.left =
            Math.random()*100+"%";

        star.style.top =
            Math.random()*100+"%";

        star.style.animationDelay =
            Math.random()*4+"s";

        container.appendChild(star);

    }

}


/* =========================================================
   HUD
========================================================= */

function showHud(){

    document.getElementById("hud")
        .style.display="flex";

    updateHud();

}


function updateHud(){

    document.getElementById("starCount")
        .textContent =
        game.stars.size;

    document.getElementById("chapterHud")
        .textContent =
        "Chapter "+(game.chapter+1);

}


/* =========================================================
   SCREEN HELPER
========================================================= */

function screen(content){

    document.getElementById("app")
        .innerHTML = `

        <section class="screen active">

            <div class="card">

                ${content}

            </div>

        </section>

    `;

    window.scrollTo({
        top:0,
        behavior:"smooth"
    });

}


/* =========================================================
   START
========================================================= */

function startGame(){

    game.chapter=0;

    game.visited.clear();

    game.stars.clear();

    game.choices={
        firstStep:null,
        storm:null,
        future:null,
        ocean:null
    };

    showHud();

    intro();

}


/* =========================================================
   INTRO
========================================================= */

function intro(){

    screen(`

        <div class="eyebrow">
            A birthday story for Lola
        </div>

        <h1>
            The Places<br>
            Between Us
        </h1>

        <p>
            There are billions of stars in the sky.
        </p>

        <p>
            Somewhere amongst all of them,
            two people found each other.
        </p>

        <p class="muted">
            This is the story of how two separate
            worlds became one little universe.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="beforeYou()"
            >
                Begin the story ✨
            </button>

        </div>

    `);

}


/* =========================================================
   CHAPTER 1
========================================================= */

function beforeYou(){

    game.chapter=0;

    updateHud();

    screen(`

        <div class="scene-icon">
            🌑
        </div>

        <div class="eyebrow">
            Chapter One
        </div>

        <h2>
            Before You
        </h2>

        <div class="scene-text">

            <p>
                Before there was an us,
                there were two separate worlds.
            </p>

            <p>
                Two lives moving through completely
                different skies, neither knowing that
                somewhere in the distance there was
                someone who would eventually become
                home.
            </p>

            <p>
                Then one day, there was a light.
            </p>

        </div>

        <div class="choices">

            <button
                class="choice"
                onclick="chooseBeginning('light')"
            >

                <div class="choice-title">
                    ✨ Follow the light
                </div>

                <div class="choice-description">
                    Maybe some lights are meant
                    to be followed.
                </div>

            </button>


            <button
                class="choice"
                onclick="chooseBeginning('curious')"
            >

                <div class="choice-title">
                    🌙 Stay curious
                </div>

                <div class="choice-description">
                    Take another look at the
                    little light in the distance.
                </div>

            </button>


            <button
                class="choice"
                onclick="chooseBeginning('step')"
            >

                <div class="choice-title">
                    🚀 Take the first step
                </div>

                <div class="choice-description">
                    Sometimes the biggest stories
                    start with something very small.
                </div>

            </button>

        </div>

    `);

}


function chooseBeginning(choice){

    game.choices.firstStep=choice;

    findingEachOther();

}


/* =========================================================
   CHAPTER 2
========================================================= */

function findingEachOther(){

    game.chapter=1;

    updateHud();

    screen(`

        <div class="scene-icon">
            ✨
        </div>

        <div class="eyebrow">
            Chapter Two
        </div>

        <h2>
            Finding Each Other
        </h2>

        <p>
            Maybe love does not always arrive loudly.
        </p>

        <p>
            Sometimes it begins with a conversation.
            A voice.
            A little curiosity.
            A reason to stay up a little longer.
        </p>

        <p>
            And then suddenly, without either person
            quite realising when it happened...
        </p>

        <h3>
            someone matters.
        </h3>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="becomingUs()"
            >
                Keep going 💙
            </button>

        </div>

    `);

}


/* =========================================================
   CHAPTER 3
========================================================= */

function becomingUs(){

    game.chapter=2;

    updateHud();

    screen(`

        <div class="scene-icon">
            💙
        </div>

        <div class="eyebrow">
            Chapter Three
        </div>

        <h2>
            Becoming Us
        </h2>

        <p>
            Somewhere between the conversations,
            the laughter, the late nights,
            the little moments and all the things
            we started learning about each other...
        </p>

        <p>
            two separate worlds became connected.
        </p>

        <p>
            It stopped being just you.
        </p>

        <p>
            It stopped being just me.
        </p>

        <h3>
            It became us.
        </h3>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="openGalaxy()"
            >
                Enter our universe 🚀
            </button>

        </div>

    `);

}


/* =========================================================
   GALAXY MAP
========================================================= */

function openGalaxy(){

    game.chapter=3;

    updateHud();

    screen(`

        <div class="eyebrow">
            Chapter Four
        </div>

        <h2>
            Our Little Universe
        </h2>

        <p>
            Your spaceship has arrived.
        </p>

        <p class="muted">
            Explore the worlds around you.
            Some of them contain memories.
            Some contain dreams.
            Some contain stars.
        </p>

        <div class="galaxy">

            <div class="orbit one"></div>
            <div class="orbit two"></div>
            <div class="orbit three"></div>
            <div class="orbit four"></div>

            <div class="sun">
                ✨
            </div>


            <div
                class="planet p1"
                onclick="coffeePlanet()"
            >
                <small>
                    ☕<br>
                    Little Things
                </small>
            </div>


            <div
                class="planet p2"
                onclick="stormPlanet()"
            >
                <small>
                    🌩️<br>
                    The Storm
                </small>
            </div>


            <div
                class="planet p3"
                onclick="oceanPlanet()"
            >
                <small>
                    🌊<br>
                    The Ocean
                </small>
            </div>


            <div
                class="planet p4"
                onclick="futurePlanet()"
            >
                <small>
                    🌳<br>
                    The Future
                </small>
            </div>


            <div
                class="planet p5"
                onclick="gravityPlanet()"
            >
                <small>
                    📏<br>
                    Gravity
                </small>
            </div>

        </div>

        <div class="map-message">

            <p class="muted">
                Click a planet to explore it.
            </p>

        </div>

        <div class="button-row">

            <button
                class="btn"
                onclick="constellation()"
            >
                ⭐ View stars
            </button>

        </div>

    `);

}


/* =========================================================
   COFFEE PLANET
========================================================= */

function coffeePlanet(){

    game.visited.add("coffee");

    screen(`

        <div class="scene-icon">
            ☕
        </div>

        <div class="eyebrow">
            Little Things
        </div>

        <h2>
            The Black Coffee Planet
        </h2>

        <p>
            You land somewhere warm and quiet.
        </p>

        <p>
            There is coffee waiting.
        </p>

        <p>
            Black, of course.
        </p>

        <p>
            Because somewhere along the way,
            learning that tiny detail about Lola
            became something worth remembering.
        </p>

        <p>
            That's the thing about loving someone.
            You start collecting the little things.
        </p>

        <p>
            Their favourite colour.
            Their favourite drink.
            Their little habits.
            The things that make them laugh.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="openGalaxy()"
            >
                Return to the universe
            </button>

        </div>

    `);

}


/* =========================================================
   STORM PLANET
========================================================= */

function stormPlanet(){

    game.visited.add("storm");

    game.chapter=4;

    updateHud();

    screen(`

        <div class="scene-icon">
            🌩️
        </div>

        <div class="eyebrow">
            The Storm
        </div>

        <h2>
            When the Sky Gets Loud
        </h2>

        <p>
            The sky suddenly becomes dark.
        </p>

        <p>
            Thunder rolls across the planet.
        </p>

        <p>
            You know she doesn't like storms.
        </p>

        <p>
            So you have a choice.
        </p>

        <div class="choices">

            <button
                class="choice"
                onclick="stormChoice('count')"
            >

                <div class="choice-title">
                    🌙 Count to ten with her
                </div>

                <div class="choice-description">
                    Stay with her through every
                    second of the storm.
                </div>

            </button>


            <button
                class="choice"
                onclick="stormChoice('voice')"
            >

                <div class="choice-title">
                    💙 Let her hear your voice
                </div>

                <div class="choice-description">
                    Remind her that distance does
                    not mean she is alone.
                </div>

            </button>

        </div>

    `);

}


function stormChoice(choice){

    game.choices.storm=choice;

    screen(`

        <div class="scene-icon">
            💙
        </div>

        <h2>
            The storm passes.
        </h2>

        <p>
            Maybe you can't control the thunder.
        </p>

        <p>
            Maybe you can't make the distance
            disappear instantly.
        </p>

        <p>
            But you can stay.
        </p>

        <p>
            And sometimes,
            staying is its own kind of love.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="openGalaxy()"
            >
                Continue
            </button>

        </div>

    `);

}


/* =========================================================
   GRAVITY
========================================================= */

function gravityPlanet(){

    game.visited.add("gravity");

    screen(`

        <div class="scene-icon">
            📏
        </div>

        <div class="eyebrow">
            The Gravity Planet
        </div>

        <h2>
            The Laws of Gravity
        </h2>

        <p>
            According to very serious scientific
            calculations...
        </p>

        <p>
            One of you is around 5'10.
        </p>

        <p>
            The other is around 5'1.
        </p>

        <p>
            Which means the universe has apparently
            decided that your height difference
            should be adorable.
        </p>

        <p>
            But somehow the distance between your
            heights has never mattered nearly as much
            as the distance between your hearts.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="twoMoons()"
            >
                Continue 💙
            </button>

        </div>

    `);

}


/* =========================================================
   TWO MOONS
========================================================= */

function twoMoons(){

    game.visited.add("moons");

    screen(`

        <div class="scene-icon">
            🌙
        </div>

        <h2>
            Two Moons
        </h2>

        <p>
            The universe turns blue.
        </p>

        <p>
            One moon is baby blue.
        </p>

        <p>
            The other is burgundy.
        </p>

        <p>
            Two different colours.
            Two different worlds.
            Somehow sharing the same sky.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="openGalaxy()"
            >
                Back to the universe
            </button>

        </div>

    `);

}


/* =========================================================
   OCEAN PLANET
========================================================= */

function oceanPlanet(){

    game.visited.add("ocean");

    game.chapter=5;

    updateHud();

    screen(`

        <div class="scene-icon">
            🌊
        </div>

        <div class="eyebrow">
            A Future Moment
        </div>

        <h2>
            The Ocean
        </h2>

        <p>
            You step onto a shore.
        </p>

        <p>
            The waves stretch endlessly ahead.
        </p>

        <div class="ocean">

            <div class="moon"></div>

            <div class="ocean-ray">
                🪽
            </div>

            <div class="wave"></div>

        </div>

        <p>
            One day, I want to stand beside you
            while you finally see the ocean.
        </p>

        <p>
            Not through a screen.
            Not through a photograph.
            Not through someone else's story.
        </p>

        <p>
            Just you.
            Me.
            The waves.
        </p>

        <div class="choices">

            <button
                class="choice"
                onclick="oceanChoice('watch')"
            >

                <div class="choice-title">
                    🪽 Watch the stingray
                </div>

                <div class="choice-description">
                    Something small moves beneath
                    the blue water.
                </div>

            </button>


            <button
                class="choice"
                onclick="oceanChoice('future')"
            >

                <div class="choice-title">
                    🌊 Imagine the future
                </div>

                <div class="choice-description">
                    Imagine what it will feel like
                    when this isn't just a dream.
                </div>

            </button>

        </div>

    `);

}


function oceanChoice(choice){

    game.choices.ocean=choice;

    if(choice==="watch"){

        screen(`

            <div class="scene-icon">
                🪽
            </div>

            <h2>
                A Stingray
            </h2>

            <p>
                A stingray glides quietly beneath
                the surface.
            </p>

            <p>
                You watch it disappear into the blue.
            </p>

            <p>
                You smile.
            </p>

            <div class="button-row">

                <button
                    class="btn primary"
                    onclick="openGalaxy()"
                >
                    Continue
                </button>

            </div>

        `);

    }else{

        screen(`

            <div class="scene-icon">
                🌅
            </div>

            <h2>
                Not Yet.
            </h2>

            <p>
                Not yet doesn't mean never.
            </p>

            <p>
                Some dreams simply need a little
                more time before they become memories.
            </p>

            <p>
                And maybe one day, you'll stand there
                together and realise you actually made
                it to the place you used to only imagine.
            </p>

            <div class="button-row">

                <button
                    class="btn primary"
                    onclick="openGalaxy()"
                >
                    Continue
                </button>

            </div>

        `);

    }

}


/* =========================================================
   FUTURE PLANET
========================================================= */

function futurePlanet(){

    game.visited.add("future");

    game.chapter=6;

    updateHud();

    screen(`

        <div class="eyebrow">
            The Future
        </div>

        <h2>
            The Things We Haven't Done Yet
        </h2>

        <p>
            Some planets contain memories.
        </p>

        <p>
            This one contains things that haven't
            happened yet.
        </p>

        <div class="choices">

            <button
                class="choice"
                onclick="treehouse()"
            >

                <div class="choice-title">
                    🌳 The Tree House
                </div>

                <div class="choice-description">
                    Somewhere in the countryside,
                    above the green fields.
                </div>

            </button>


            <button
                class="choice"
                onclick="artScene()"
            >

                <div class="choice-title">
                    🎨 The Paintings
                </div>

                <div class="choice-description">
                    Paint together, even if neither
                    of you knows what you're doing.
                </div>

            </button>


            <button
                class="choice"
                onclick="musicScene()"
            >

                <div class="choice-title">
                    🎶 The Music
                </div>

                <div class="choice-description">
                    Sing until you forget the words.
                </div>

            </button>


            <button
                class="choice"
                onclick="danceScene()"
            >

                <div class="choice-title">
                    💃 The Dancing
                </div>

                <div class="choice-description">
                    Dance in the kitchen for no reason.
                </div>

            </button>

        </div>

    `);

}


/* =========================================================
   TREEHOUSE
========================================================= */

function treehouse(){

    screen(`

        <div class="eyebrow">
            Somewhere in the future
        </div>

        <h2>
            The Tree House
        </h2>

        <div class="treehouse">

            <div class="tree">
                🌳
            </div>

            <div class="house">
                🏡
            </div>

        </div>

        <p>
            Somewhere surrounded by green fields
            and open skies.
        </p>

        <p>
            A little tree house that belongs to us.
        </p>

        <p>
            Somewhere we can sit together,
            talk for hours, watch the stars
            and forget what time it is.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="openGalaxy()"
            >
                Keep dreaming
            </button>

        </div>

    `);

}


/* =========================================================
   ART
========================================================= */

function artScene(){

    screen(`

        <div class="scene-icon">
            🎨
        </div>

        <h2>
            Paint With Me
        </h2>

        <p>
            Maybe neither of us knows what we're doing.
        </p>

        <p>
            Maybe the painting turns out terrible.
        </p>

        <p>
            Maybe we laugh so hard we can't finish it.
        </p>

        <p>
            I think I'd still want that painting.
        </p>

        <p>
            Because it would be ours.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="openGalaxy()"
            >
                Continue
            </button>

        </div>

    `);

}


/* =========================================================
   MUSIC
========================================================= */

function musicScene(){

    screen(`

        <div class="scene-icon">
            🎶
        </div>

        <h2>
            Sing With Me
        </h2>

        <p>
            We don't need perfect voices.
        </p>

        <p>
            We don't even need to remember
            the words.
        </p>

        <p>
            I just want to hear you laughing
            when we completely ruin the song.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="openGalaxy()"
            >
                Continue
            </button>

        </div>

    `);

}


/* =========================================================
   DANCE
========================================================= */

function danceScene(){

    screen(`

        <div class="scene-icon">
            💃
        </div>

        <h2>
            Dance With Me
        </h2>

        <p>
            One day I want to put music on
            in the kitchen.
        </p>

        <p>
            I want to take your hand.
        </p>

        <p>
            And dance with you for absolutely
            no reason.
        </p>

        <p>
            Just because we can.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="openGalaxy()"
            >
                Continue
            </button>

        </div>

    `);

}


/* =========================================================
   CONSTELLATION
========================================================= */

function constellation(){

    let html="";

    for(let i=0;i<27;i++){

        const found =
            game.stars.has(i);

        html += `

            <button
                class="
                    collect-star
                    ${found ? "found" : ""}
                "
                onclick="
                    ${
                        found
                        ? `showStar(${i})`
                        : `collectStar(${i})`
                    }
                "
            >
                ${found ? "⭐" : "·"}
            </button>

        `;

    }


    screen(`

        <div class="scene-icon">
            🌌
        </div>

        <div class="eyebrow">
            Your Constellation
        </div>

        <h2>
            27 Stars
        </h2>

        <p>
            There are 27 stars hidden throughout
            the universe.
        </p>

        <p class="muted">
            Find every one to unlock the final
            constellation.
        </p>

        <div class="progress">

            <div
                class="progress-fill"
                style="
                    width:
                    ${(game.stars.size/27)*100}%
                "
            ></div>

        </div>

        <div class="star-board">
            ${html}
        </div>

        <p>
            ⭐
            ${game.stars.size}
            / 27 found
        </p>

        ${
            game.stars.size===27
            ? `
                <div class="button-row">

                    <button
                        class="btn primary"
                        onclick="constellationComplete()"
                    >
                        Unlock the constellation ✨
                    </button>

                </div>
            `
            : `
                <p class="muted">
                    Keep exploring the planets.
                </p>
            `
        }

        <div class="button-row">

            <button
                class="btn"
                onclick="openGalaxy()"
            >
                Return to galaxy
            </button>

        </div>

    `);

}


/* =========================================================
   COLLECT STAR
========================================================= */

function collectStar(id){

    game.stars.add(id);

    updateHud();

    showStar(id);

}


/* =========================================================
   STAR MESSAGE
========================================================= */

function showStar(id){

    screen(`

        <div class="scene-icon">
            ⭐
        </div>

        <h2>
            Star ${id+1}
        </h2>

        <p>
            ${starMessages[id]}
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="constellation()"
            >
                Back to constellation
            </button>

        </div>

    `);

}


/* =========================================================
   COMPLETE CONSTELLATION
========================================================= */

function constellationComplete(){

    game.unlockedFinal=true;

    screen(`

        <div class="scene-icon">
            🌌
        </div>

        <h2>
            You Found Them All.
        </h2>

        <p>
            27 stars.
        </p>

        <p>
            27 little pieces of this universe.
        </p>

        <p>
            But there is something you haven't
            found yet.
        </p>

        <p>
            The most important place in the entire
            universe isn't on the map.
        </p>

        <h3>
            It's Home.
        </h3>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="homeChapter()"
            >
                Find Home 🏡
            </button>

        </div>

    `);

}


/* =========================================================
   HOME
========================================================= */

function homeChapter(){

    game.chapter=7;

    updateHud();

    screen(`

        <div class="scene-icon">
            🏡
        </div>

        <div class="eyebrow">
            The Final Chapter
        </div>

        <h2>
            Home
        </h2>

        <p>
            Maybe home was never a place.
        </p>

        <p>
            Maybe it was the person you could
            tell everything to.
        </p>

        <p>
            The person whose voice could make
            the distance feel smaller.
        </p>

        <p>
            The person you wanted beside you
            for the extraordinary moments
            and the completely ordinary ones.
        </p>

        <p>
            Somewhere along the way,
            you became my favourite place
            to return to.
        </p>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="finalLetter()"
            >
                Open the final letter 💌
            </button>

        </div>

    `);

}


/* =========================================================
   FINAL LETTER
========================================================= */

function finalLetter(){

    screen(`

        <div class="eyebrow">
            For Lola
        </div>

        <h2>
            The Letter At The End Of The Universe
        </h2>

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
                <strong>
                    I am so incredibly proud of you.
                </strong>
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
                I'm proud of you for making it through
                the days that felt impossible.
                I'm proud of the softness you've managed
                to keep in a world that hasn't always
                been soft with you.
            </p>

            <p>
                And more than anything, I hope you know
                that you never have to become someone else
                to deserve love.
            </p>

            <p>
                <strong>
                    You are already enough.
                </strong>
            </p>

            <p>
                You are my favourite person.
            </p>

            <p>
                Not just one of my favourite people.
            </p>

            <p>
                <strong>
                    My favourite.
                </strong>
            </p>

            <p>
                You have somehow become such a beautiful
                part of my life that sometimes I don't know
                how I existed without you in it.
                You are everything to me and somehow,
                at the same time, you are still so much more
                than everything I could ever put into
                a single word.
            </p>

            <p>
                I don't just want the extraordinary moments
                with you.
                I want the ordinary ones.
            </p>

            <p>
                I want to dance with you in the kitchen
                for absolutely no reason.
                I want to sing with you until we're laughing
                because neither of us can remember the words.
                I want to paint beside you, even if neither
                of us knows what we're doing.
                I want to sit somewhere quiet in the countryside
                with you and watch the sun disappear.
            </p>

            <p>
                I want that tree house we've talked about.
            </p>

            <p>
                I want somewhere that feels like ours.
                Somewhere surrounded by green fields
                and open skies, where the nights are dark
                enough for us to see every star above us.
                Somewhere we can sit together and talk
                until we realise we've been talking for hours.
            </p>

            <p>
                I want slow mornings.
                Coffee.
                Messy hair.
                Bare feet.
                Your hand finding mine without either
                of us thinking about it.
            </p>

            <p>
                I want the kind of life where nothing
                particularly remarkable happens and yet,
                somehow, I still go to sleep thinking,
                “I got to spend another day with her.”
            </p>

            <p>
                I want to see the ocean with you.
                I want to stand beside you while the waves
                reach the shore and finally watch you
                experience something you've dreamed about.
            </p>

            <p>
                I want photographs we haven't taken yet.
                Songs we haven't sung yet.
                Paintings we haven't made yet.
                Places we haven't found yet.
                Stories we haven't written yet.
            </p>

            <p>
                I want all the little things we've imagined
                scattered throughout our future.
                And I want the things we haven't imagined yet,
                too.
            </p>

            <p>
                Because that's the part that makes me happiest.
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
                I'd ask for a life where I get to keep
                finding you in it.
            </p>

            <p>
                Because somewhere along the way,
                you became my favourite place to return to.
                My favourite voice.
                My favourite person to talk to.
                My favourite thought at the end of the day.
                My favourite future to imagine.
                And my favourite part of today.
            </p>

            <p>
                I hope you never forget how loved you are.
                Not only on your birthday.
                Not only when everything is beautiful.
                But on the ordinary days.
                On the difficult days.
                On the days when you don't feel particularly
                lovable.
                Especially then.
            </p>

            <p>
                I will still look at you and see you.
                Not some perfect version of you.
                Just you.
                And I will still think you are extraordinary.
            </p>

            <p>
                So here's to 27.
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
                But I know what I hope is waiting
                somewhere along the road.
            </p>

            <p>
                <strong>
                    You and me.
                </strong>
            </p>

            <p>
                Still talking.
                Still laughing.
                Still dreaming.
                Still finding new reasons
                to love each other.
            </p>

            <p>
                And maybe one day, we'll look back at
                this little universe and laugh at how small
                our dreams seemed compared to everything
                we actually got to experience.
            </p>

            <p>
                Until then, I'll keep dreaming with you.
                I'll keep writing about you.
                I'll keep loving you.
                And I'll keep reminding you, whenever
                you forget, just how proud I am
                of the person you are.
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
                Because no matter how enormous the universe
                becomes, I'd always find my way home to you.
            </p>

            <p class="signature">
                — Bree
            </p>

        </div>

        <div class="button-row">

            <button
                class="btn primary"
                onclick="finalReveal()"
            >
                One last star ⭐
            </button>

        </div>

    `);

}


/* =========================================================
   FINAL REVEAL
========================================================= */

function finalReveal(){

    screen(`

        <div class="final-star">
            ⭐
        </div>

        <div class="eyebrow">
            The Final Reveal
        </div>

        <h2>
            This One Is Yours.
        </h2>

        <p>
            You found 27 stars.
        </p>

        <p>
            You travelled through our little universe.
        </p>

        <p>
            You found the memories.
            You found the dreams.
            You found the future.
        </p>

        <p>
            But this star isn't part of the game.
        </p>

        <p>
            <strong>
                It's real.
            </strong>
        </p>

        <p>
            I bought a star for you.
        </p>

        <p>
            A little piece of the universe
            with your name on it.
        </p>

        <h3>
            Happy 27th birthday, my love. 💙
        </h3>

        <p>
            From my little universe to yours,
            I love you.
        </p>

        <div class="button-row">

            <button
                class="btn burgundy"
                onclick="restartGame()"
            >
                Play our story again
            </button>

        </div>

    `);

}


/* =========================================================
   RESTART
========================================================= */

function restartGame(){

    startGame();

}


/* =========================================================
   INITIALISE
========================================================= */

createStars();

document.getElementById("hud")
    .style.display="none";


/* =========================================================
   OPENING
========================================================= */

screen(`

    <div class="eyebrow">
        A little universe made for Lola
    </div>

    <h1>
        The Places<br>
        Between Us
    </h1>

    <p>
        There are billions of stars in the sky.
    </p>

    <p>
        But somehow, I found my favourite person
        somewhere between all of them.
    </p>

    <p class="muted">
        A tiny interactive love story for Lola's
        27th birthday.
    </p>

    <div class="button-row">

        <button
            class="btn primary"
            onclick="startGame()"
        >
            Begin ✨
        </button>

    </div>

`);

</script>

</body>
</html>
