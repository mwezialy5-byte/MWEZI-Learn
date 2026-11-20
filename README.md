# MWEZI-Learn
ICT and Technology Learning Platform[script.js](https://github.com/user-attachments/files/35139872/script.js)

const searchInput = document.getElementById('courseSearch');
const cards = [...document.querySelectorAll('.course-card')];
const noResults = document.getElementById('noResults');[index.html](https://github.com/user-attachments/files/35139879/index.html)
[style.css](https://github.com/user-attachments/files/35139877/style.css)

const dialog = document.getElementById('lessonDialog');
const dialogTitle = document.getElementById('dialogTitle');
const dialogContent = document.getElementById('dialogContent');

document.getElementById('year').textContent = new Date().getFullYear();

searchInput.addEventListener('input', () => {
  const term = searchInput.value.trim().toLowerCase();
  let visible = 0;
  cards.forEach(card => {
    const matches = (card.dataset.search + ' ' + card.innerText).toLowerCase().includes(term);
    card.hidden = !matches;
    if (matches) visible++;
  });
  noResults.hidden = visible !== 0;
});

const lessonText = {
  'Computer Basics': '<p>A computer is an electronic device that receives data, processes it, stores it, and produces information.</p><ul><li><b>Hardware:</b> physical parts, such as a keyboard, monitor, and mouse.</li><li><b>Software:</b> programs and instructions that tell the computer what to do.</li><li><b>Input:</b> data entered into a computer.</li><li><b>Output:</b> information produced by a computer.</li></ul>',
  'Using the Internet': '<p>The internet connects computers and devices around the world. A web browser helps you visit websites and find information.</p><p>Use reliable sources, be respectful online, and ask a trusted adult if something online makes you uncomfortable.</p>',
  'Introduction to Coding': '<p>Coding means writing instructions a computer can follow. A webpage commonly uses HTML for structure, CSS for design, and JavaScript for interactivity.</p><p>Try changing a heading in the <code>index.html</code> file and refresh your page to see what happens.</p>',
  'Digital Safety': '<p>Keep personal information private. Use unique passwords, log out on shared devices, check before opening unfamiliar links, and talk to a trusted adult about suspicious messages.</p>',
  'Technology Around Us': '<p>Technology includes tools and systems people use to solve problems. Examples include phones, computers, digital learning tools, medical equipment, and communication systems.</p>',
  'Quick ICT Quiz': '<p><b>Question:</b> Which part of a computer is commonly used to type letters?</p><div class="quiz-options"><button class="quiz-option">A. Monitor</button><button class="quiz-option">B. Keyboard</button><button class="quiz-option">C. Speaker</button></div><p id="quizFeedback" aria-live="polite"></p>'
};

document.querySelectorAll('.learn-button').forEach(button => {
  button.addEventListener('click', () => {
    const topic = button.dataset.topic;
    dialogTitle.textContent = topic;
    dialogContent.innerHTML = lessonText[topic] || '<p>Lesson coming soon. Keep exploring MWEZI Learn!</p>';
    dialog.showModal();
    const options = dialogContent.querySelectorAll('.quiz-option');
    options.forEach(option => option.addEventListener('click', () => {
      const feedback = dialogContent.querySelector('#quizFeedback');
      feedback.textContent = option.textContent.startsWith('B.') ? 'Correct! The keyboard is used to type.' : 'Not quite. Try again!';
      feedback.style.fontWeight = '700';
    }));
  });
});

document.getElementById('closeDialog').addEventListener('click', () => dialog.close());
dialog.addEventListener('click', event => {
  if (event.target === dialog) dialog.close();
});

@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Space+Grotesk:wght@500;600;700&display=swap');
:root{--navy:#10233f;--blue:#4169e1;--sky:#eaf2ff;--text:#24344c;--muted:#64748b;--bg:#f7f9fc;--white:#fff}
*{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;font-family:'DM Sans',sans-serif;color:var(--text);background:var(--bg);line-height:1.6}
.site-header{height:76px;display:flex;align-items:center;justify-content:space-between;padding:0 7%;background:#fff;border-bottom:1px solid #edf1f7;position:sticky;top:0;z-index:10}
.brand{font-family:'Space Grotesk',sans-serif;font-size:1.25rem;font-weight:700;color:var(--navy);text-decoration:none;display:flex;align-items:center;gap:8px}.brand-mark{width:32px;height:32px;border-radius:10px;background:var(--blue);color:white;display:grid;place-items:center}.brand-light{font-weight:500;color:var(--blue)}
nav{display:flex;gap:30px}nav a{font-size:.95rem;text-decoration:none;color:var(--text)}nav a:hover{color:var(--blue)}
.hero{padding:70px 7% 80px;min-height:450px;display:flex;align-items:center;justify-content:space-between;gap:40px;background:linear-gradient(120deg,#f7f9fc 45%,#edf3ff)}
.hero-content{max-width:580px}.eyebrow{font-size:.75rem;letter-spacing:2px;font-weight:700;color:var(--blue);margin:0 0 12px}
h1,h2,h3{font-family:'Space Grotesk',sans-serif;line-height:1.18;color:var(--navy)}h1{font-size:clamp(2.5rem,5vw,4.3rem);margin:0 0 20px}h1 span{color:var(--blue)}.hero-copy{font-size:1.08rem;max-width:530px;color:var(--muted);margin:0 0 28px}
.primary-button{display:inline-flex;align-items:center;gap:12px;background:var(--blue);color:white;padding:13px 20px;border-radius:12px;text-decoration:none;font-weight:700;box-shadow:0 8px 22px #4169e133}.primary-button:hover{background:#3156c7}
.hero-art{position:relative;width:320px;height:300px;flex:0 0 320px;display:grid;place-items:center}.orbit{position:absolute;border:1px dashed #a9bce8;border-radius:50%}.orbit-one{width:290px;height:290px}.orbit-two{width:215px;height:215px}.moon{width:145px;height:145px;border-radius:38px;background:linear-gradient(135deg,#5278ee,#7ea4ff);display:grid;place-items:center;color:#fff;font-family:'Space Grotesk';font-size:4.5rem;font-weight:700;box-shadow:0 25px 60px #4169e155;transform:rotate(-8deg)}.floating-card{position:absolute;background:#fff;padding:13px 17px;border-radius:14px;box-shadow:0 12px 35px #1a335015;font-weight:700}.floating-card span{margin-left:7px}.card-top{top:18px;right:0}.card-bottom{bottom:20px;left:0}
.section{padding:72px 7%}.section-heading{display:flex;align-items:end;justify-content:space-between;gap:25px;margin-bottom:28px}.section-heading h2{font-size:2rem;margin:0}.search-wrap{display:flex;align-items:center;gap:8px;border:1px solid #dfe6f1;background:#fff;border-radius:12px;padding:9px 12px;color:#7b8ba5}.search-wrap input{border:0;outline:0;font:inherit;width:190px;background:transparent}
.course-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}.course-card{background:#fff;border:1px solid #edf1f7;border-radius:18px;padding:23px;box-shadow:0 5px 20px #10233f05;transition:transform .2s,box-shadow .2s}.course-card:hover{transform:translateY(-4px);box-shadow:0 14px 35px #10233f0d}.course-icon{width:54px;height:54px;border-radius:16px;display:grid;place-items:center;font-size:1.5rem;margin-bottom:18px}.blue{background:#e7efff}.purple{background:#f0eaff}.orange{background:#fff0df}.green{background:#e4f7ed}.pink{background:#ffe9f1}.yellow{background:#fff6d9}.course-tag{font-size:.7rem;letter-spacing:1.3px;font-weight:700;color:var(--blue);margin:0 0 7px}.course-card h3{font-size:1.25rem;margin:0 0 10px}.course-card>p:not(.course-tag){color:var(--muted);font-size:.93rem;min-height:48px;margin:0 0 15px}.learn-button{border:0;background:transparent;color:var(--blue);font:inherit;font-weight:700;padding:0;cursor:pointer}.learn-button:hover{text-decoration:underline}.no-results{color:var(--muted);padding:20px}
.about-section{background:var(--navy);color:#d7e2f5;padding:58px 7%}.about-inner{display:grid;grid-template-columns:1fr 1fr;gap:50px;align-items:center}.about-section h2{color:white;font-size:2rem;margin:0}.about-section .eyebrow{color:#9db6ff}.about-inner>p{margin:0;color:#d1ddf0}
footer{padding:24px 7%;display:flex;justify-content:space-between;align-items:center;gap:20px;background:#fff}footer p{color:var(--muted);font-size:.85rem;margin:0}.footer-brand{font-size:1rem}
dialog{border:0;border-radius:20px;padding:30px;max-width:500px;width:calc(100% - 32px);box-shadow:0 25px 80px #10233f35;color:var(--text)}dialog::backdrop{background:#10233f88;backdrop-filter:blur(3px)}dialog h2{margin:0 0 15px}.dialog-close{float:right;border:0;background:#edf2fa;border-radius:50%;width:34px;height:34px;font-size:1.3rem;cursor:pointer}
@media(max-width:850px){.course-grid{grid-template-columns:repeat(2,1fr)}.hero-art{width:260px;flex-basis:260px}.orbit-one{width:250px;height:250px}.orbit-two{width:185px;height:185px}.about-inner{grid-template-columns:1fr;gap:20px}}
@media(max-width:600px){.site-header{padding:0 5%;height:68px}nav{gap:14px}nav a{font-size:.85rem}.hero{padding:55px 6%;text-align:center}.hero-art{display:none}.hero-copy{margin-left:auto;margin-right:auto}.section{padding:52px 6%}.section-heading{align-items:stretch;flex-direction:column}.search-wrap input{width:100%}.course-grid{grid-template-columns:1fr}.course-card>p:not(.course-tag){min-height:0}.about-section{padding:45px 6%}footer{padding:22px 6%;flex-direction:column;text-align:center}}

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MWEZI Learn | Learn ICT & Technology</title>
  <meta name="description" content="MWEZI Learn — a simple learning website for ICT, digital skills, and technology.">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header class="site-header">
    <a class="brand" href="#home" aria-label="MWEZI Learn home"><span class="brand-mark">M</span> MWEZI <span class="brand-light">Learn</span></a>
    <nav aria-label="Main navigation">
      <a href="#home">Home</a>
      <a href="#courses">Courses</a>
      <a href="#about">About</a>
    </nav>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="hero-content">
        <p class="eyebrow">LEARN • PRACTICE • GROW</p>
        <h1>Explore technology.<br><span>Build your future.</span></h1>
        <p class="hero-copy">Welcome to MWEZI Learn — a friendly place to discover ICT, digital skills, and the world of technology one lesson at a time.</p>
        <a class="primary-button" href="#courses">Explore lessons <span aria-hidden="true">→</span></a>
      </div>
      <div class="hero-art" aria-hidden="true">
        <div class="orbit orbit-one"></div><div class="orbit orbit-two"></div>
        <div class="moon">M</div>
        <div class="floating-card card-top">💡 <span>Ideas</span></div>
        <div class="floating-card card-bottom">💻 <span>Skills</span></div>
      </div>
    </section>

    <section class="section" id="courses">
      <div class="section-heading">
        <div><p class="eyebrow">START LEARNING</p><h2>Explore learning topics</h2></div>
        <label class="search-wrap"><span aria-hidden="true">⌕</span><input id="courseSearch" type="search" placeholder="Search lessons..." aria-label="Search lessons"></label>
      </div>
      <div class="course-grid" id="courseGrid">
        <article class="course-card" data-search="computer basics hardware software computer">
          <div class="course-icon blue">🖥️</div><p class="course-tag">ICT FUNDAMENTALS</p><h3>Computer Basics</h3><p>Learn what computers are, their parts, and how they work.</p><button class="learn-button" data-topic="Computer Basics">Learn more →</button>
        </article>
        <article class="course-card" data-search="internet web browsing online safety">
          <div class="course-icon purple">🌐</div><p class="course-tag">DIGITAL SKILLS</p><h3>Using the Internet</h3><p>Explore websites, search for information, and use the internet wisely.</p><button class="learn-button" data-topic="Using the Internet">Learn more →</button>
        </article>
        <article class="course-card" data-search="coding programming html css javascript">
          <div class="course-icon orange">⌨️</div><p class="course-tag">CREATE</p><h3>Introduction to Coding</h3><p>Discover how instructions help computers perform tasks.</p><button class="learn-button" data-topic="Introduction to Coding">Learn more →</button>
        </article>
        <article class="course-card" data-search="digital safety privacy passwords cyber security">
          <div class="course-icon green">🔐</div><p class="course-tag">STAY SAFE</p><h3>Digital Safety</h3><p>Understand privacy, strong passwords, and responsible online behavior.</p><button class="learn-button" data-topic="Digital Safety">Learn more →</button>
        </article>
        <article class="course-card" data-search="technology innovation devices">
          <div class="course-icon pink">🚀</div><p class="course-tag">DISCOVER</p><h3>Technology Around Us</h3><p>See how technology supports learning, communication, and daily life.</p><button class="learn-button" data-topic="Technology Around Us">Learn more →</button>
        </article>
        <article class="course-card" data-search="practice activities quiz">
          <div class="course-icon yellow">🧩</div><p class="course-tag">PRACTICE</p><h3>Quick ICT Quiz</h3><p>Test your knowledge with a short beginner-friendly question.</p><button class="learn-button" data-topic="Quick ICT Quiz">Start quiz →</button>
        </article>
      </div>
      <p class="no-results" id="noResults" hidden>No lessons found. Try a different search.</p>
    </section>

    <section class="about-section" id="about">
      <div class="about-inner"><div><p class="eyebrow">ABOUT MWEZI LEARN</p><h2>Knowledge is a light that keeps growing.</h2></div>
      <p>MWEZI Learn is a learning project designed to help learners explore ICT and technology through clear explanations, useful topics, and practice. Keep learning, keep asking questions, and keep creating.</p></div>
    </section>
  </main>

  <footer><a class="brand footer-brand" href="#home"><span class="brand-mark">M</span> MWEZI <span class="brand-light">Learn</span></a><p>© <span id="year"></span> MWEZI Learn · Learn something new today.</p></footer>

  <dialog id="lessonDialog">
    <button class="dialog-close" id="closeDialog" aria-label="Close">×</button>
    <p class="eyebrow">MWEZI LEARN</p><h2 id="dialogTitle">Lesson</h2><div id="dialogContent"></div>
  </dialog>
  <script src="script.js"></script>
</body>
</html>
