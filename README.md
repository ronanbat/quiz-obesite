# quiz-obesite
[index.html.html](https://github.com/user-attachments/files/25232449/index.html.html)
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Quiz Sensibilisation Obésité</title>
<style>
  body { font-family: Arial, sans-serif; max-width: 800px; margin: 20px auto; background-color: #f9f9f9; }
  h1 { text-align: center; color: #2c3e50; }
  .quiz-container { background-color: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
  .question { margin-bottom: 20px; }
  .btn { display: block; margin: 5px 0; padding: 12px; width: 100%; font-size: 16px; cursor: pointer; border: none; border-radius: 5px; }
  .btn:hover { opacity: 0.9; }
  #score { text-align: center; font-size: 24px; color: #27ae60; margin-top: 20px; }
</style>
</head>
<body>

<h1>Quiz – Sensibilisation à l’obésité</h1>
<div class="quiz-container" id="quiz"></div>
<div id="score"></div>

<script>
const questions = [
  {q: "1. L’obésité est définie principalement par :", options:["Le tour de taille uniquement","L’indice de masse corporelle (IMC) ≥ 30 kg/m²","Le poids ressenti comme excessif","Le pourcentage de masse musculaire"], answer: 1},
  {q: "2. L’obésité est considérée aujourd’hui comme :", options:["Un manque de volonté","Une maladie chronique multifactorielle","Un problème uniquement esthétique","Une conséquence inévitable de l’âge"], answer: 1},
  {q: "3. Parmi ces facteurs, lequel peut contribuer à l’obésité ?", options:["La génétique","Le manque de sommeil","Le stress chronique","Toutes les réponses ci-dessus"], answer: 3},
  {q: "4. Parmi ces situations, laquelle peut favoriser une prise de poids à long terme ?", options:["Dormir moins de 5 heures par nuit","Sauter régulièrement le petit-déjeuner sans compensation","Être exposé à un stress chronique","Toutes les réponses ci-dessus"], answer: 3},
  {q: "5. L’obésité augmente le risque de :", options:["Diabète de type 2","Hypertension","Maladies cardiovasculaires","Toutes les réponses ci-dessus"], answer: 3},
  {q: "6. La stigmatisation des personnes en situation d’obésité peut :", options:["Améliorer leur motivation","Favoriser la perte de poids","Aggraver leur état de santé physique et mentale","Être sans conséquence"], answer: 2},
  {q: "7. Une perte de poids progressive est préférable car :", options:["Elle est plus durable dans le temps","Elle évite les carences","Elle limite l’effet “yo-yo”","Toutes les réponses ci-dessus"], answer: 3},
  {q: "8. La prise en charge de l’obésité repose principalement sur :", options:["Un régime strict rapide","Une approche globale (nutrition, activité, psychologique, médicale)","Des compléments alimentaires","La volonté seule"], answer: 1},
  {q: "9. L’activité physique recommandée pour un adulte est d’environ :", options:["30 minutes par semaine","30 minutes par jour","150 minutes par semaine","10 minutes par mois"], answer: 2},
  {q: "10. La chirurgie bariatrique est indiquée :", options:["Pour toute personne souhaitant maigrir","Uniquement pour des raisons esthétiques","Selon des critères médicaux précis","En première intention systématiquement"], answer: 2},
  {q: "11. Combien de personnes sont touchées par l'obésité dans le monde (estimation OMS) ?", options:["Environ 500 millions","Plus d’un milliard","Environ 2,5 milliards","Environ 100 millions"], answer: 1}
];

let currentQuestion = 0;
let score = 0;

const quizDiv = document.getElementById("quiz");
const scoreDiv = document.getElementById("score");

function showQuestion() {
  quizDiv.innerHTML = "";
  if(currentQuestion >= questions.length){
    quizDiv.innerHTML = "<h2>Quiz terminé !</h2>";
    scoreDiv.textContent = `Votre score : ${score} / ${questions.length}`;
    return;
  }

  const qObj = questions[currentQuestion];
  const qTitle = document.createElement("h3");
  qTitle.textContent = qObj.q;
  quizDiv.appendChild(qTitle);

  qObj.options.forEach((opt, i) => {
    const btn = document.createElement("button");
    btn.className = "btn";
    btn.textContent = opt;
    btn.onclick = () => selectAnswer(i);
    quizDiv.appendChild(btn);
  });
}

function selectAnswer(i){
  const buttons = document.querySelectorAll(".btn");
  const correct = questions[currentQuestion].answer;
  buttons.forEach((btn, idx) => {
    if(idx === correct) btn.style.backgroundColor = "green";
    if(idx === i && i !== correct) btn.style.backgroundColor = "red";
    btn.disabled = true;
  });
  if(i === correct) score++;
  setTimeout(() => {
    currentQuestion++;
    showQuestion();
  }, 1000); // passe à la question suivante après 1s
}

showQuestion();
</script>

</body>
</html>
