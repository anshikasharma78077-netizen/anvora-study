
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="ANVORA helps students learn smarter with study resources, quizzes and productivity tools.">
  <title>ANVORA | Learn Without Limits</title>
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f4f8ff;
      color: #102b52;
    }
    header {
      background: #102b52;
      color: white;
      padding: 22px 16px;
      text-align: center;
    }
    header h1 { margin: 0; letter-spacing: 3px; }
    header p { color: #c9d9f2; }
    nav {
      background: white;
      padding: 14px 8px;
      text-align: center;
      position: sticky;
      top: 0;
    }
    nav a {
      color: #2563eb;
      text-decoration: none;
      margin: 0 8px;
      font-size: 14px;
      font-weight: bold;
    }
    .hero {
      text-align: center;
      padding: 65px 20px;
      background: linear-gradient(135deg, #dbeafe, #ffffff);
    }
    .hero h2 { font-size: 36px; margin: 0 0 15px; }
    .hero p {
      line-height: 1.7;
      max-width: 480px;
      margin: 0 auto 24px;
    }
    .btn {
      display: inline-block;
      background: #2563eb;
      color: white;
      padding: 13px 22px;
      border-radius: 8px;
      text-decoration: none;
      border: 0;
      cursor: pointer;
      font-size: 15px;
    }
    section { padding: 35px 18px; text-align: center; }
    .cards {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(145px, 1fr));
      gap: 15px;
      max-width: 850px;
      margin: 25px auto;
    }
    .card {
      background: white;
      padding: 23px 14px;
      border-radius: 14px;
      box-shadow: 0 3px 14px #102b5210;
    }
    .card .emoji { font-size: 32px; }
    .card h3 { margin-bottom: 8px; }
    .card p { color: #52627a; font-size: 14px; line-height: 1.5; }
    #quiz-box, #planner-box {
      background: white;
      max-width: 500px;
      margin: 20px auto;
      padding: 24px;
      border-radius: 14px;
      text-align: left;
    }
    #quiz-box button.option {
      display: block;
      width: 100%;
      margin: 10px 0;
      padding: 12px;
      background: #eff6ff;
      border: 1px solid #bfdbfe;
      border-radius: 8px;
      text-align: left;
      cursor: pointer;
    }
    input {
      padding: 12px;
      width: 100%;
      margin: 8px 0 14px;
      border: 1px solid #bfdbfe;
      border-radius: 7px;
    }
    footer {
      background: #102b52;
      color: white;
      text-align: center;
      padding: 24px 12px;
      line-height: 1.7;
    }
    footer p { color: #c9d9f2; }
  </style>
</head>
<body>

<header>
  <h1>ANVORA</h1>
  <p>Learn Without Limits.</p>
</header>

<nav>
  <a href="#home">Home</a>
  <a href="#resources">Resources</a>
  <a href="#quiz">Quiz</a>
  <a href="#planner">Planner</a>
</nav>

<main>
  <div class="hero" id="home">
    <h2>Your Next Chapter Starts Here.</h2>
    <p>Learn smarter, prepare better and build a study routine
       that helps you reach your goals. Welcome to ANVORA!</p>
    <a class="btn" href="#resources">Explore Resources</a>
  </div>

  <section id="resources">
    <h2>Your Learning Space 📚</h2>
    <p>Simple tools to make every study session more useful.</p>
    <div class="cards">
      <div class="card">
        <div class="emoji">📖</div>
        <h3>Study Notes</h3>
        <p>Organize your learning and revision materials.</p>
      </div>
      <div class="card">
        <div class="emoji">🧠</div>
        <h3>Quick Quiz</h3>
        <p>Test what you know with an interactive quiz.</p>
      </div>
      <div class="card">
        <div class="emoji">🗓️</div>
        <h3>Study Planner</h3>
        <p>Set a daily goal and plan your next session.</p>
      </div>
      <div class="card">
        <div class="emoji">⏱️</div>
        <h3>Focus Timer</h3>
        <p>Concentrate for 25 minutes, then take a break.</p>
        <button class="btn" onclick="startTimer()">Start Focus</button>
        <p id="timer">25:00</p>
      </div>
    </div>
  </section>

  <section id="quiz">
    <h2>Quick Knowledge Check</h2>
    <div id="quiz-box">
      <p><strong>Which language structures a web page?</strong></p>
      <button class="option" onclick="answer(false)">A. Python</button>
      <button class="option" onclick="answer(true)">B. HTML</button>
      <button class="option" onclick="answer(false)">C. SQL</button>
      <p id="quiz-result" aria-live="polite"></p>
    </div>
  </section>

  <section id="planner">
    <h2>My Study Goal ✨</h2>
    <div id="planner-box">
      <label for="goal">What do you want to study today?</label>
      <input id="goal" placeholder="e.g. Operating Systems">
      <button class="btn" onclick="saveGoal()">Save My Goal</button>
      <p id="goal-result" aria-live="polite"></p>
    </div>
  </section>
</main>

<footer>
  <h2>ANVORA</h2>
  <p>Learn. Practice. Grow.</p>
  <p>Made for learners, everywhere. 💙</p>
  <small>© <span id="year"></span> ANVORA</small>
</footer>

<script>
  document.getElementById("year").textContent =
    new Date().getFullYear();

  function answer(correct) {
    document.getElementById("quiz-result").textContent =
      correct ? "Correct! HTML structures web pages. 🎉"
              : "Not quite! The correct answer is HTML.";
  }

  function saveGoal() {
    const goal = document.getElementById("goal").value.trim();
    document.getElementById("goal-result").textContent = goal
      ? "Today's goal: " + goal + ". You've got this! 💙"
      : "Please enter a study goal first.";
  }

  let seconds = 1500;
  let interval = null;

  function startTimer() {
    if (interval) return;
    interval = setInterval(function() {
      if (seconds <= 0) {
        clearInterval(interval);
        interval = null;
        document.getElementById("timer").textContent =
          "Session complete! Take a break.";
        return;
      }
      seconds--;
      const m = Math.floor(seconds / 60);
      const s = seconds % 60;
      document.getElementById("timer").textContent =
        String(m).padStart(2, "0") + ":" +
        String(s).padStart(2, "0");
    }, 1000);
  }
</script>

</body>
</html>
# anvora-study
