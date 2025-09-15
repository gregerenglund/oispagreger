# Auto detect text files and perform LF normalization
* text=auto
oispa-nuuskaa/
│
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
├── images/
│   └── (game / UI / other pictures you want to include)
└── backgrounds/
    └── (https://ibb.co/kVbx9B76)

<!DOCTYPE html>
<html lang="fi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Oispa Nuuskaa</title>
  <link rel="stylesheet" href="css/styles.css">
</head>
<body>

  <div id="background-overlay"></div>

  <div class="container">

    <header>
      <h1>OISPA NUUSKAA!</h1>
    </header>

    <div class="message" id="score-message">
      <!-- Dynamically set score message -->
      0
    </div>

    <div class="instructions">
      <p>Yhdistä nuuskapurkit ja pyri saavuttamaan pelin paras siberian nuuska! Varo, ettei tila täytty pelilaudalla. Jos nuuskaa on liikaa, voit siirtyä katkohoidolle, mutta se maksaa 1000 pistettä.</p>
    </div>

    <div class="controls">
      <button id="continue-btn">Jatka peliä</button>
      <button id="retry-btn">Yritä uudestaan</button>
      <button id="katko-btn">Katkohoito</button>
    </div>

    <section class="top-scores">
      <h2>Top 10 Nuuska Mestarit</h2>
      <ol id="highscores-list">
        <!-- JS will populate -->
      </ol>
    </section>

    <footer>
      <p>Oispa Nuuskaa — kaikki oikeudet pidätetään</p>
    </footer>

  </div> <!-- .container -->

  <script src="js/script.js"></script>
</body>
</html>
/* Reset basics */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
  font-family: Arial, sans-serif;
  color: #fff;
  overflow-x: hidden;
}

body {
  position: relative;
  background: #000; /* fallback */
}

#background-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center center;
  z-index: -1;
  /* default background, replace by JS or CSS */
  background-image: url('../backgrounds/default-bg.jpg');
  opacity: 0.6; /* adjust to make text readable over */
}

.container {
  position: relative;
  max-width: 800px;
  margin: auto;
  padding: 20px;
  text-align: center;
}

header h1 {
  font-size: 3rem;
  margin-bottom: 20px;
}

.message {
  font-size: 2rem;
  margin-bottom: 20px;
}

.instructions {
  margin: 20px 0;
  font-size: 1.2rem;
}

.controls {
  margin: 20px 0;
}

.controls button {
  margin: 0 10px;
  padding: 10px 20px;
  font-size: 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  background-color: rgba(0,0,0,0.7);
  color: #fff;
  transition: background-color 0.3s;
}

.controls button:hover {
  background-color: rgba(255,255,255,0.2);
}

.top-scores {
  margin: 30px 0;
}

.top-scores h2 {
  margin-bottom: 10px;
  font-size: 1.8rem;
}

.top-scores ol {
  list-style: none;
  padding-left: 0;
}

.top-scores li {
  margin: 5px 0;
  font-size: 1.1rem;
}

footer {
  margin-top: 40px;
  font-size: 0.9rem;
}
// Example data for high scores
const defaultScores = [
  { name: "Pelaaja1", score: 5000 },
  { name: "Pelaaja2", score: 4000 },
  { name: "Pelaaja3", score: 3500 },
  { name: "Pelaaja4", score: 3000 },
  { name: "Pelaaja5", score: 2500 },
  { name: "Pelaaja6", score: 2000 },
  { name: "Pelaaja7", score: 1500 },
  { name: "Pelaaja8", score: 1000 },
  { name: "Pelaaja9", score: 500 },
  { name: "Pelaaja10", score: 100 }
];

// Settings / Customization
const settings = {
  backgroundImagePath: 'backgrounds/default-bg.jpg',
  backgroundOpacity: 0.6,
  messageText: '0'
};

// Load initial data
document.addEventListener('DOMContentLoaded', () => {
  // Set background
  const bg = document.getElementById('background-overlay');
  if (settings.backgroundImagePath) {
    bg.style.backgroundImage = `url('../${settings.backgroundImagePath}')`;
  }
  bg.style.opacity = settings.backgroundOpacity;

  // Set message
  const msg = document.getElementById('score-message');
  msg.textContent = settings.messageText;

  // Populate high scores
  const ol = document.getElementById('highscores-list');
  defaultScores.forEach((item, idx) => {
    const li = document.createElement('li');
    li.textContent = `${idx + 1}. ${item.name} — ${item.score}`;
    ol.appendChild(li);
  });

  // Add button behavior (placeholders)
  document.getElementById('continue-btn').addEventListener('click', () => {
    alert('Jatka peliä functionality not implemented yet.');
  });
  document.getElementById('retry-btn').addEventListener('click', () => {
    alert('Yritä uudestaan!');
  });
  document.getElementById('katko-btn').addEventListener('click', () => {
    alert('Katkohoito — maksaa 1000 pistettä.');
  });
});
