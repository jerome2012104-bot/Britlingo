<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BritLingo – British English Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f8ff;
      margin: 0;
      padding: 20px;
      text-align: center;
    }

    h1 {
      color: #1e90ff;
    }

    .quiz-box {
      max-width: 500px;
      margin: 0 auto;
      background: #ffffff;
      border-radius: 12px;
      box-shadow: 0 0 12px rgba(0,0,0,0.1);
      padding: 20px;
    }

    .question {
      font-size: 20px;
      margin-bottom: 20px;
    }

    .option {
      display: block;
      margin: 10px 0;
      padding: 14px;
      background: #e0e0e0;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    .option:hover {
      background: #d0d0d0;
    }

    #result {
      font-weight: bold;
      margin-top: 20px;
    }

    #nextBtn {
      margin-top: 20px;
      padding: 12px 24px;
      font-size: 16px;
      background-color: #1e90ff;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }

    #nextBtn:hover {
      background-color: #187bcd;
    }

    @media (max-width: 600px) {
      .quiz-box {
        padding: 15px;
      }
      .option {
        font-size: 16px;
      }
    }
  </style>
</head>
<body>

  <h1>🇬🇧 BritLingo Quiz</h1>
  <p>Lerne britisches Englisch mit einem kurzen Multiple-Choice-Quiz!</p>

  <div class="quiz-box">
    <div id="question" class="question">Lade Frage...</div>
    <div id="options"></div>
    <div id="result"></div>
    <button id="nextBtn" onclick="nextQuestion()">Nächste Frage</button>
  </div>

  <script>
    const quiz = [
      {
        question: "What does 'loo' mean in British English?",
        options: ["Lunch", "Toilet", "Bus", "Money"],
        answer: "Toilet"
      },
      {
        question: "What is a 'biscuit' in the UK?",
        options: ["Cake", "Bread", "Cookie", "Cracker"],
        answer: "Cookie"
      },
      {
        question: "What does 'petrol' mean in British English?",
        options: ["Gasoline", "Water", "Oil", "Juice"],
        answer: "Gasoline"
      },
      {
        question: "What is the British word for 'truck'?",
        options: ["Wagon", "Van", "Lorry", "Train"],
        answer: "Lorry"
      },
      {
        question: "What is a 'boot' on a British car?",
        options: ["Engine", "Trunk", "Seat", "Tyre"],
        answer: "Trunk"
      }
    ];

    let current = 0;

    function loadQuestion() {
      const q = quiz[current];
      document.getElementById("question").textContent = q.question;
      const optionsDiv = document.getElementById("options");
      optionsDiv.innerHTML = "";
      document.getElementById("result").textContent = "";

      q.options.forEach(option => {
        const btn = document.createElement("div");
        btn.textContent = option;
        btn.className = "option";
        btn.onclick = () => checkAnswer(option);
        optionsDiv.appendChild(btn);
      });
    }

    function checkAnswer(selected) {
      const correct = quiz[current].answer;
      const result = document.getElementById("result");
      if (selected === correct) {
        result.textContent = "✅ Richtig!";
        result.style.color = "green";
      } else {
        result.textContent = `❌ Falsch! Richtige Antwort: ${correct}`;
        result.style.color = "red";
      }
    }

    function nextQuestion() {
      current++;
      if (current < quiz.length) {
        loadQuestion();
      } else {
        document.getElementById("question").textContent = "🎉 Du hast das Quiz beendet!";
        document.getElementById("options").innerHTML = "";
        document.getElementById("nextBtn").style.display = "none";
        document.getElementById("result").textContent = "";
      }
    }

    window.onload = loadQuestion;
  </script>

</body>
</html>
