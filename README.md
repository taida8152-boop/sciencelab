<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>ScienceLab Virtuel</title>

<style>
/* ===== BODY ===== */
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #0f172a, #1e3a8a);
    color: white;
}

/* ===== HEADER ===== */
header {
    background: rgba(0,0,0,0.5);
    padding: 20px;
    text-align: center;
    font-size: 28px;
    font-weight: bold;
    backdrop-filter: blur(10px);
}

/* ===== NAVBAR ===== */
nav {
    display: flex;
    justify-content: center;
    background: rgba(0,0,0,0.3);
    backdrop-filter: blur(10px);
}

nav button {
    background: none;
    border: none;
    color: white;
    padding: 15px 25px;
    cursor: pointer;
    transition: 0.3s;
    font-size: 16px;
}

nav button:hover {
    background: rgba(255,255,255,0.1);
    transform: scale(1.1);
}

/* ===== SECTIONS ===== */
.section {
    display: none;
    padding: 40px;
    text-align: center;
    animation: fade 0.5s ease;
}

.active {
    display: block;
}

/* ===== ANIMATION ===== */
@keyframes fade {
    from {opacity: 0; transform: translateY(20px);}
    to {opacity: 1; transform: translateY(0);}
}

/* ===== IFRAMES ===== */
iframe {
    margin-top: 20px;
    width: 90%;
    height: 500px;
    border-radius: 15px;
    box-shadow: 0 0 20px rgba(0,0,0,0.5);
    border: none;
}

/* ===== LABO ===== */
#laboZone {
    width: 200px;
    height: 200px;
    margin: auto;
    background: linear-gradient(135deg, blue, cyan);
    transition: 0.5s;
    border-radius: 20px;
    box-shadow: 0 0 20px rgba(0,0,0,0.5);
}

/* ===== BOUTONS LABO ===== */
button.action {
    margin: 10px;
    padding: 12px 20px;
    border: none;
    border-radius: 10px;
    background: linear-gradient(135deg, #3b82f6, #06b6d4);
    color: white;
    cursor: pointer;
    transition: 0.3s;
}

button.action:hover {
    transform: scale(1.1);
    box-shadow: 0 0 10px #3b82f6;
}
</style>
</head>

<body>

<header>🔬 ScienceLab Virtuel</header>

<nav>
    <button onclick="show('home')">Accueil</button>
    <button onclick="show('college')">Collège</button>
    <button onclick="show('lycee')">Lycée</button>
    <button onclick="show('labo')">Labo</button>
</nav>

<!-- ===== ACCUEIL ===== -->
<div id="home" class="section active">
    <h1>Bienvenue 👋</h1>
    <p>Fais des expériences scientifiques interactives du collège à la terminale.</p>
</div>

<!-- ===== COLLEGE ===== -->
<div id="college" class="section">
    <h2>Collège</h2>
    <p>États de la matière, énergie, électricité</p>
    <iframe src="https://phet.colorado.edu/sims/html/states-of-matter/latest/states-of-matter_en.html"></iframe>
</div>

<!-- ===== LYCEE ===== -->
<div id="lycee" class="section">
    <h2>Lycée</h2>
    <p>Réactions chimiques, ondes, circuits</p>
    <iframe src="https://phet.colorado.edu/sims/html/circuit-construction-kit-dc/latest/circuit-construction-kit-dc_en.html"></iframe>
</div>

<!-- ===== LABO INTERACTIF ===== -->
<div id="labo" class="section">
    <h2>🧪 Labo Virtuel</h2>

    <div id="laboZone"></div>

    <br>

    <button class="action" onclick="acide()">Ajouter Acide</button>
    <button class="action" onclick="base()">Ajouter Base</button>
    <button class="action" onclick="reset()">Reset</button>

    <p id="resultat">Aucune réaction</p>
</div>

<script>
/* ===== NAVIGATION ===== */
function show(id) {
    document.querySelectorAll('.section').forEach(sec => sec.classList.remove('active'));
    document.getElementById(id).classList.add('active');
}

/* ===== LABO ===== */
let a = 0;
let b = 0;

function acide() {
    a++;
    verifier();
}

function base() {
    b++;
    verifier();
}

function verifier() {
    if (a > 0 && b > 0) {
        document.getElementById("laboZone").style.background = "purple";
        document.getElementById("resultat").innerText = "Réaction chimique réussie !";
    }
}

function reset() {
    a = 0;
    b = 0;
    document.getElementById("laboZone").style.background = "linear-gradient(135deg, blue, cyan)";
    document.getElementById("resultat").innerText = "Aucune réaction";
}
</script>

</body>
</html>
