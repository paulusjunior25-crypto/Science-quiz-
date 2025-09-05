# Science-quiz-<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Daily Science Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f9;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .container {
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      max-width: 500px;
      width: 100%;
      text-align: center;
    }
    h1 {
      color: #2c3e50;
    }
    button {
      margin-top: 10px;
      padding: 10px 15px;
      border: none;
      border-radius: 8px;
      background: #3498db;
      color: #fff;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background: #2980b9;
    }
    .option {
      display: block;
      margin: 8px 0;
      padding: 10px;
      background: #ecf0f1;
      border-radius: 8px;
      cursor: pointer;
    }
    .option:hover {
      background: #d0d7de;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Daily Science Quiz</h1>
    <div id="quiz"></div>
    <button id="startBtn">Start Quiz</button>
  </div>

  <script>
    const questions = [
      {
        question: "What planet is known as the Red Planet?",
        answers: ["Earth", "Mars", "Venus", "Jupiter"],
        correct: "Mars"
      },
      {
        question: "What is the chemical symbol for water?",
        answers: ["O2", "CO2", "H2O", "NaCl"],
        correct: "H2O"
      },
      {
        question: "How many bones are in the adult human body?",
        answers: ["106", "206", "306", "406"],
        correct: "206"
      }
    ];

    let currentQuestion = 0;
    let score = 0;

    const quizContainer = document.getElementById("quiz");
    const startBtn = document.getElementById("startBtn");

    function startQuiz() {
      startBtn.style.display = "none";
      showQuestion();
    }

    function showQuestion() {
      if (currentQuestion < questions.length) {
        let q = questions[currentQuestion];
        quizContainer.innerHTML = `<h3>${q.question}</h3>`;
        q.answers.forEach(answer => {
          const btn = document.createElement("div");
          btn.classList.add("option");
          btn.textContent = answer;
          btn.onclick = () => checkAnswer(answer);
          quizContainer.appendChild(btn);
        });
      } else {
        quizContainer.innerHTML = `<h2>You scored ${score} out of ${questions.length}</h2>`;
        startBtn.textContent = "Play Again";
        startBtn.style.display = "block";
        startBtn.onclick = restartQuiz;
      }
    }

    function checkAnswer(answer) {
      if (answer === questions[currentQuestion].correct) {
        score++;
      }
      currentQuestion++;
      showQuestion();
    }

    function restartQuiz() {
      currentQuestion = 0;
      score = 0;
      startQuiz();
    }

    startBtn.addEventListener("click", startQuiz);
  </script>
</body>
</html>
