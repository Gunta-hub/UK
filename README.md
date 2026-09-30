
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Typically British? | Interactive English</title>
<style>
:root {
  --navy: #17345b;
  --red: #c83b4b;
  --cream: #fffaf0;
  --ink: #1e293b;
  --muted: #64748b;
  --green: #26734d;
  --gold: #f4c95d;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  background: linear-gradient(135deg, #f4f0e7, #e9eef5);
  color: var(--ink);
  font: 16px/1.55 system-ui, -apple-system, Segoe UI, sans-serif;
}

header {
  background: var(--navy);
  color: white;
  padding: 30px 20px 26px;
  text-align: center;
  border-bottom: 6px solid var(--red);
}

header .flag { font-size: 28px; }

h1 {
  font-size: clamp(1.8rem, 5vw, 3rem);
  margin: 4px 0 2px;
}

header p { margin: 0; color: #e0e8f4; }

main {
  max-width: 1000px;
  margin: 28px auto;
  padding: 0 16px 40px;
}

.intro {
  background: white;
  border-radius: 18px;
  padding: 18px 22px;
  box-shadow: 0 8px 25px #18345b12;
  margin-bottom: 20px;
}

.tabs {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin: 20px 0;
}

.tab {
  border: 2px solid var(--navy);
  background: white;
  color: var(--navy);
  font-weight: 700;
  padding: 11px 18px;
  border-radius: 999px;
  cursor: pointer;
}

.tab[aria-selected="true"] {
  background: var(--navy);
  color: white;
}

.panel {
  background: white;
  border-radius: 20px;
  padding: clamp(18px, 4vw, 30px);
  box-shadow: 0 12px 30px #18345b16;
}

.hidden { display: none !important; }

.eyebrow {
  color: var(--red);
  font-size: .78rem;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: .12em;
}

h2 {
  margin: 4px 0 8px;
  color: var(--navy);
  font-size: 1.55rem;
}

.progress-wrap {
  height: 9px;
  background: #e7ebf0;
  border-radius: 99px;
  overflow: hidden;
  margin: 15px 0 20px;
}

.progress {
  height: 100%;
  width: 0;
  background: linear-gradient(90deg, var(--red), #e69a62);
  transition: width .25s;
}

.question {
  font-size: 1.2rem;
  font-weight: 750;
  margin: 18px 0;
}

.options {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 10px;
}

.option {
  border: 2px solid #d9e0e9;
  background: white;
  border-radius: 12px;
  padding: 13px;
  text-align: left;
  cursor: pointer;
  font: inherit;
  transition: .15s;
}

.option:hover:not(:disabled) {
  border-color: var(--navy);
  transform: translateY(-1px);
}

.option:focus-visible,
.tab:focus-visible,
.btn:focus-visible,
.drop:focus-visible {
  outline: 3px solid var(--gold);
  outline-offset: 2px;
}

.option.correct {
  border-color: #3c9868;
  background: #eaf7ef;
}

.option.wrong {
  border-color: #d65a65;
  background: #fff0f1;
}

.option:disabled { cursor: default; }

.feedback {
  min-height: 48px;
  margin: 14px 0 4px;
  font-weight: 650;
}

.feedback.good { color: var(--green); }
.feedback.bad { color: #b42332; }

.controls {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  align-items: center;
  margin-top: 16px;
}

.btn {
  border: 0;
  background: var(--navy);
  color: white;
  padding: 11px 18px;
  border-radius: 10px;
  font-weight: 750;
  cursor: pointer;
}

.btn.secondary {
  background: #e8edf4;
  color: var(--navy);
}

.btn:disabled {
  opacity: .45;
  cursor: not-allowed;
}

.score {
  margin-left: auto;
  color: var(--muted);
  font-weight: 700;
}

.match-grid {
  display: grid;
  grid-template-columns: 1fr 1.15fr;
  gap: 18px;
  margin-top: 18px;
}

.match-col h3 {
  font-size: .95rem;
  color: var(--muted);
  margin: 0 0 8px;
}

.term {
  padding: 11px 12px;
  margin: 8px 0;
  background: #edf2f8;
  border: 1px solid #d8e1ed;
  border-radius: 10px;
  font-weight: 750;
  cursor: grab;
  user-select: none;
}

.term.selected {
  outline: 3px solid var(--gold);
  background: #fff8dd;
}

.term.used {
  opacity: .45;
  cursor: default;
}

.drop {
  min-height: 48px;
  padding: 9px 11px;
  margin: 8px 0;
  border: 2px dashed #c5cfdb;
  border-radius: 10px;
  background: #fcfdff;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  cursor: pointer;
}

.drop.over {
  border-color: var(--red);
  background: #fff4f4;
}

.drop.filled {
  border-style: solid;
  border-color: #a8b6c9;
}

.drop.correct {
  border-color: #3c9868;
  background: #eaf7ef;
}

.drop.wrong {
  border-color: #d65a65;
  background: #fff0f1;
}

.drop .definition { font-size: .94rem; }

.drop .answer {
  font-size: .83rem;
  color: var(--navy);
  font-weight: 800;
  white-space: nowrap;
}

.hint {
  font-size: .9rem;
  color: var(--muted);
}

.result {
  background: #f1f6fb;
  border-radius: 14px;
  padding: 18px;
}

footer {
  text-align: center;
  color: var(--muted);
  font-size: .85rem;
  padding: 0 16px 28px;
}

@media (max-width: 620px) {
  .match-grid { grid-template-columns: 1fr; }
  .score { margin-left: 0; width: 100%; }
  .panel { padding: 18px; }
}
</style>
</head>

<body>

<header>
  <div class="flag" aria-hidden="true">🇬🇧</div>
  <h1>Typically British?</h1>
  <p>A British Way of Life · Interactive English</p>
</header>

<main>
  <section class="intro">
    <strong>Ready to explore?</strong>
    Test what you remember from the text,
    then match important words and ideas.
    Read each question carefully and use the
    feedback to learn.
  </section>

  <nav class="tabs" aria-label="Choose an activity">
    <button class="tab" id="tabQuiz"
      aria-selected="true" aria-controls="quiz">
      1 · Knowledge quiz
    </button>
    <button class="tab" id="tabMatch"
      aria-selected="false" aria-controls="match">
      2 · Match the concepts
    </button>
  </nav>

  <!-- TASK 1: QUIZ -->
  <section class="panel" id="quiz">
    <div class="eyebrow">Task 1 · Multiple choice</div>
    <h2>How much do you know?</h2>
    <p class="hint">
      Choose one answer for each question.
      You’ll get instant feedback.
    </p>

    <div class="progress-wrap" aria-label="Quiz progress">
      <div class="progress" id="quizProgress"></div>
    </div>

    <div id="quizArea" aria-live="polite"></div>
  </section>

  <!-- TASK 2: MATCHING -->
  <section class="panel hidden" id="match">
    <div class="eyebrow">Task 2 · Vocabulary and ideas</div>
    <h2>Match the concepts</h2>
    <p class="hint">
      Drag a term onto its definition, or tap a term
      and then tap a definition. Match all six.
    </p>

    <div class="match-grid">
      <div class="match-col">
        <h3>TERMS</h3>
        <div id="terms"></div>
      </div>

      <div class="match-col">
        <h3>DEFINITIONS</h3>
        <div id="drops"></div>
      </div>
    </div>

    <div class="controls">
      <button class="btn" id="checkMatch">
        Check answers
      </button>
      <button class="btn secondary" id="resetMatch">
        Start again
      </button>
      <span class="score" id="matchScore"
        aria-live="polite"></span>
    </div>

    <div id="matchFeedback" class="feedback"
      aria-live="polite"></div>
  </section>
</main>

<footer>
  Learning activity based on
  “Typically British? A British Way of Life”
  · You can replay both tasks.
</footer>

<script>
// ========================================
// TASK 1: MULTIPLE-CHOICE QUIZ
// ========================================

const questions = [
  {
    q: "Which countries make up Great Britain?",
    a: [
      "England, Scotland and Wales",
      "England and Northern Ireland",
      "Scotland, Wales and the Republic of Ireland"
    ],
    c: 0,
    e: "Great Britain consists of England, Scotland and Wales. Northern Ireland is part of the UK, but not Great Britain."
  },
  {
    q: "Which countries together form the United Kingdom?",
    a: [
      "Great Britain and the Republic of Ireland",
      "Great Britain and Northern Ireland",
      "England, Wales and the Republic of Ireland"
    ],
    c: 1,
    e: "The UK consists of England, Scotland, Wales and Northern Ireland."
  },
  {
    q: "According to the text, are people from the UK’s countries all alike?",
    a: [
      "Yes, they share exactly the same culture",
      "No, cultures and customs can differ",
      "Only their food is different"
    ],
    c: 1,
    e: "The text explains that the countries have their own cultures and can differ in humour, food and customs."
  },
  {
    q: "Why might football be changing as a working-class sport?",
    a: [
      "There are fewer football teams",
      "Ticket prices are high and media has a bigger role",
      "Football is no longer popular"
    ],
    c: 1,
    e: "The text mentions high ticket prices and the growing influence of the media."
  },
  {
    q: "What is the word “pub” short for?",
    a: [
      "Public house",
      "People’s union building",
      "Popular British"
    ],
    c: 0,
    e: "Pub is short for “public house”."
  },
  {
    q: "According to the text, what is a pub primarily?",
    a: [
      "A place only to watch football",
      "A social centre where people meet and talk",
      "A school for adults"
    ],
    c: 1,
    e: "The text describes pubs primarily as social centres for meeting and discussing different subjects."
  },
  {
    q: "Which set names the three traditional social classes in Britain?",
    a: [
      "Royal, urban and rural",
      "Upper, middle and working",
      "Rich, famous and local"
    ],
    c: 1,
    e: "The three traditional classes named are upper, middle and working class. The text also mentions an underclass."
  },
  {
    q: "Which is NOT one of the four criteria for being described as posh in the text?",
    a: [
      "Money and family background",
      "Schooling",
      "Favourite football team"
    ],
    c: 2,
    e: "The four criteria are money, schooling, appearance and voice/accent."
  },
  {
    q: "Which feature does the text say may reveal social background most clearly?",
    a: [
      "Voice or accent",
      "Favourite food",
      "Height"
    ],
    c: 0,
    e: "The text suggests that voice and accent may reveal social background particularly clearly."
  }
];

let qi = 0;
let score = 0;
let answered = false;

const quizArea = document.getElementById("quizArea");

function renderQuestion() {
  answered = false;

  document.getElementById("quizProgress").style.width =
    (qi / questions.length * 100) + "%";

  if (qi >= questions.length) {
    document.getElementById("quizProgress").style.width = "100%";

    quizArea.innerHTML = `
      <div class="result">
        <h2>Quiz complete!</h2>
        <p>You scored
          <strong>${score} out of ${questions.length}</strong>.
        </p>
        <p>
          ${
            score === questions.length
              ? "Excellent work — you remembered every answer!"
              : score >= 6
              ? "Well done! Review the explanations and try again to improve your score."
              : "Good effort. Read the feedback and have another go."
          }
        </p>
        <button class="btn" id="retryQuiz">
          Try the quiz again
        </button>
      </div>
    `;

    document.getElementById("retryQuiz").onclick = () => {
      qi = 0;
      score = 0;
      renderQuestion();
    };
    return;
  }

  const q = questions[qi];

  quizArea.innerHTML = `
    <div class="question">
      ${qi + 1}. ${q.q}
    </div>

    <div class="options">
      ${q.a.map((a, i) => `
        <button class="option" data-i="${i}">
          ${String.fromCharCode(65 + i)}. ${a}
        </button>
      `).join("")}
    </div>

    <div class="feedback" id="qFeedback"
      aria-live="polite"></div>

    <div class="controls">
      <button class="btn" id="nextQ" disabled>
        ${qi === questions.length - 1
          ? "See result"
          : "Next question →"}
      </button>
      <span class="score">
        Question ${qi + 1} of ${questions.length}
        · Score: ${score}
      </span>
    </div>
  `;

  quizArea.querySelectorAll(".option").forEach(button => {
    button.onclick = () => {
      if (answered) return;
      answered = true;

      const chosen = Number(button.dataset.i);

      quizArea.querySelectorAll(".option").forEach((el, i) => {
        el.disabled = true;

        if (i === q.c) {
          el.classList.add("correct");
        }

        if (i === chosen && chosen !== q.c) {
          el.classList.add("wrong");
        }
      });

      const feedback = document.getElementById("qFeedback");

      if (chosen === q.c) {
        score++;
        feedback.className = "feedback good";
        feedback.textContent = "Correct! " + q.e;
      } else {
        feedback.className = "feedback bad";
        feedback.textContent = "Not quite. " + q.e;
      }

      document.getElementById("nextQ").disabled = false;

      quizArea.querySelector(".score").textContent =
        `Question ${qi + 1} of ${questions.length} · Score: ${score}`;
    };
  });

  document.getElementById("nextQ").onclick = () => {
    qi++;
    renderQuestion();
  };
}

renderQuestion();


// ========================================
// TASK 2: MATCHING
// ========================================

const pairs = [
  [
    "Old money",
    "Wealth passed down through a family over a long period."
  ],
  [
    "Public school",
    "In the text, a fee-paying school that families pay to attend."
  ],
  [
    "Accent",
    "A way of pronouncing words that can give clues about where someone is from."
  ],
  [
    "Understatement",
    "A way of expressing something as less important or serious than it may be."
  ],
  [
    "Posh",
    "An informal word associated in the text with upper-class status."
  ],
  [
    "Underclass",
    "A term the text uses for the poorest group in society."
  ]
];

let selected = null;
let placements = {};

const termsEl = document.getElementById("terms");
const dropsEl = document.getElementById("drops");

function shuffle(array) {
  return [...array].sort(() => Math.random() - 0.5);
}

let termOrder = shuffle(pairs.map((p, i) => i));
let dropOrder = shuffle(pairs.map((p, i) => i));

function renderMatch() {
  termsEl.innerHTML = "";
  dropsEl.innerHTML = "";
  selected = null;
  placements = {};

  // Create draggable terms.
  termOrder.forEach(i => {
    const el = document.createElement("div");

    el.className = "term";
    el.textContent = pairs[i][0];
    el.draggable = true;
    el.dataset.id = i;
    el.tabIndex = 0;
    el.setAttribute("role", "button");
    el.setAttribute("aria-label", "Term: " + pairs[i][0]);

    el.addEventListener("dragstart", e => {
      e.dataTransfer.setData("text/plain", String(i));
    });

    el.addEventListener("click", () => {
      if (el.classList.contains("used")) return;

      termsEl.querySelectorAll(".term").forEach(x => {
        x.classList.remove("selected");
      });

      selected = i;
      el.classList.add("selected");
    });

    el.addEventListener("keydown", e => {
      if (e.key === "Enter" || e.key === " ") {
        e.preventDefault();
        el.click();
      }
    });

    termsEl.appendChild(el);
  });

  // Create definition drop zones.
  dropOrder.forEach(i => {
    const el = document.createElement("div");

    el.className = "drop";
    el.dataset.id = i;
    el.tabIndex = 0;
    el.setAttribute("role", "button");
    el.setAttribute(
      "aria-label",
      "Definition: " + pairs[i][1]
    );

    el.innerHTML = `
      <span class="definition">${pairs[i][1]}</span>
      <span class="answer" aria-live="polite">＋</span>
    `;

    el.addEventListener("dragover", e => {
      e.preventDefault();
      el.classList.add("over");
    });

    el.addEventListener("dragleave", () => {
      el.classList.remove("over");
    });

    el.addEventListener("drop", e => {
      e.preventDefault();
      el.classList.remove("over");

      const term = Number(
        e.dataTransfer.getData("text/plain")
      );

      place(term, i);
    });

    el.addEventListener("click", () => {
      if (selected !== null) {
        place(selected, i);
      }
    });

    el.addEventListener("keydown", e => {
      if (
        (e.key === "Enter" || e.key === " ") &&
        selected !== null
      ) {
        e.preventDefault();
        place(selected, i);
      }
    });

    dropsEl.appendChild(el);
  });

  document.getElementById("matchScore").textContent = "";
  document.getElementById("matchFeedback").textContent = "";
}

// Place a term in a definition.
function place(term, slot) {
  if (placements[term] === slot) return;

  // Remove any term already in this slot.
  Object.keys(placements).forEach(k => {
    if (placements[k] === slot) {
      delete placements[k];
    }
  });

  // Remove this term from its previous slot.
  delete placements[term];
  placements[term] = slot;

  const slotEl = [...dropsEl.children].find(
    x => Number(x.dataset.id) === slot
  );

  slotEl.classList.remove("correct", "wrong");
  slotEl.classList.add("filled");
  slotEl.querySelector(".answer").textContent = pairs[term][0];

  termsEl.querySelectorAll(".term").forEach(x => {
    x.classList.toggle("used", Number(x.dataset.id) === term);
    x.classList.remove("selected");
  });

  selected = null;
  document.getElementById("matchFeedback").textContent = "";
}

// Check the matching answers.
document.getElementById("checkMatch").onclick = () => {
  let correct = 0;

  [...dropsEl.children].forEach(el => {
    const slot = Number(el.dataset.id);

    const term = Object.keys(placements).find(
      k => placements[k] === slot
    );

    el.classList.remove("correct", "wrong");

    if (term !== undefined && Number(term) === slot) {
      correct++;
      el.classList.add("correct");
    } else {
      el.classList.add("wrong");
    }
  });

  document.getElementById("matchScore").textContent =
    `${correct} / ${pairs.length} correct`;

  const feedback = document.getElementById("matchFeedback");

  feedback.className =
    "feedback " + (correct === pairs.length ? "good" : "bad");

  feedback.textContent =
    correct === pairs.length
      ? "Perfect match! You got them all."
      : `You matched ${correct} of ${pairs.length}. Correct matches are highlighted in green. You can move terms and check again.`;
};

// Restart matching activity.
document.getElementById("resetMatch").onclick = () => {
  termOrder = shuffle(pairs.map((p, i) => i));
  dropOrder = shuffle(pairs.map((p, i) => i));
  renderMatch();
};

renderMatch();


// ========================================
// NAVIGATION BETWEEN TASKS
// ========================================

const tabQuiz = document.getElementById("tabQuiz");
const tabMatch = document.getElementById("tabMatch");

function switchTab(which) {
  const quiz = which === "quiz";

  document.getElementById("quiz")
    .classList.toggle("hidden", !quiz);

  document.getElementById("match")
    .classList.toggle("hidden", quiz);

  tabQuiz.setAttribute("aria-selected", String(quiz));
  tabMatch.setAttribute("aria-selected", String(!quiz));
}

tabQuiz.onclick = () => switchTab("quiz");
tabMatch.onclick = () => switchTab("match");
</script>
</body>
</html>
