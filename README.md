<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Ayush Kumar | Full Stack Developer Portfolio</title>
  <!-- Google Fonts & Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- AOS Library for scroll animations -->
  <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: #0a0a0f;
      color: #eef2ff;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }

    /* animated gradient background */
    .animated-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -2;
      background: radial-gradient(circle at 20% 30%, #0a0f1f, #03050b);
    }

    .animated-bg::before {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      top: -50%;
      left: -50%;
      background: conic-gradient(from 0deg, #ff4d8c, #7a2be0, #2b9eff, #ff4d8c);
      animation: rotateBg 20s linear infinite;
      opacity: 0.12;
      filter: blur(70px);
      z-index: -1;
    }

    @keyframes rotateBg {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* custom cursor glow */
    .cursor-glow {
      position: fixed;
      width: 400px;
      height: 400px;
      background: radial-gradient(circle, rgba(255,77,140,0.2) 0%, rgba(122,43,224,0) 70%);
      border-radius: 50%;
      pointer-events: none;
      transform: translate(-50%, -50%);
      z-index: 9999;
      transition: transform 0.05s linear;
    }

    /* container */
    .container {
      max-width: 1280px;
      margin: 0 auto;
      padding: 2rem 1.5rem;
      position: relative;
      z-index: 2;
    }

    /* banner section (hero) */
    .hero {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 2rem 0 3rem;
      border-radius: 48px;
      background: rgba(15, 20, 30, 0.55);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(255,255,255,0.08);
      box-shadow: 0 25px 40px -12px rgba(0,0,0,0.5);
      margin-bottom: 3rem;
    }

    .banner-img {
      width: 140px;
      height: 140px;
      border-radius: 50%;
      object-fit: cover;
      border: 3px solid #ff6ec7;
      box-shadow: 0 0 25px rgba(255,110,199,0.5);
      transition: transform 0.3s ease;
      margin-top: 1rem;
    }

    .banner-img:hover {
      transform: scale(1.03);
    }

    h1 {
      font-size: 3.8rem;
      font-weight: 800;
      background: linear-gradient(135deg, #FFFFFF, #ffb3d9, #c084fc);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      margin: 0.5rem 0 0.2rem;
      letter-spacing: -0.02em;
    }

    .typed-wrapper {
      height: 70px;
      margin: 0.5rem 0;
    }

    .subtitle {
      font-size: 1.6rem;
      font-weight: 500;
      color: #cbd5e6;
    }

    .social-links {
      display: flex;
      gap: 1.5rem;
      margin-top: 1.8rem;
      flex-wrap: wrap;
      justify-content: center;
    }

    .social-icon {
      background: rgba(255,255,255,0.05);
      padding: 0.8rem 1.8rem;
      border-radius: 60px;
      text-decoration: none;
      color: #f0f3fa;
      font-weight: 600;
      backdrop-filter: blur(4px);
      transition: all 0.25s;
      border: 1px solid rgba(255,110,199,0.3);
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      font-size: 1rem;
    }

    .social-icon i {
      font-size: 1.3rem;
      color: #ff6ec7;
    }

    .social-icon:hover {
      background: #ff6ec7;
      color: #0a0a0f;
      border-color: #ff6ec7;
      transform: translateY(-3px);
      box-shadow: 0 10px 20px -5px rgba(255,110,199,0.4);
    }

    .social-icon:hover i {
      color: #0a0a0f;
    }

    /* section cards */
    .section-card {
      background: rgba(12, 16, 28, 0.7);
      backdrop-filter: blur(12px);
      border-radius: 2rem;
      padding: 2rem 2rem;
      margin-bottom: 2.5rem;
      border: 1px solid rgba(255,255,255,0.08);
      transition: all 0.3s;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    }

    .section-title {
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 1.5rem;
      display: flex;
      align-items: center;
      gap: 12px;
      border-left: 4px solid #ff6ec7;
      padding-left: 1rem;
    }

    .section-title i {
      color: #ff6ec7;
      font-size: 1.8rem;
    }

    .tech-icons {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin-top: 1rem;
    }

    .tech-icons img {
      width: 55px;
      transition: transform 0.2s, filter 0.2s;
    }

    .tech-icons img:hover {
      transform: translateY(-8px);
      filter: drop-shadow(0 0 8px #ff6ec7);
    }

    /* projects grid */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 1.8rem;
      margin-top: 1rem;
    }

    .project-card {
      background: rgba(0,0,0,0.45);
      border-radius: 1.5rem;
      padding: 1.5rem;
      border: 1px solid rgba(255,110,199,0.2);
      transition: all 0.3s;
    }

    .project-card:hover {
      transform: translateY(-8px);
      border-color: #ff6ec7;
      box-shadow: 0 20px 25px -12px rgba(255,110,199,0.3);
      background: rgba(20, 25, 45, 0.8);
    }

    .project-title {
      font-size: 1.6rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .project-desc {
      color: #b9c3dd;
      margin: 0.8rem 0;
      line-height: 1.5;
    }

    .project-links {
      display: flex;
      gap: 1rem;
      margin-top: 1rem;
      flex-wrap: wrap;
    }

    .btn-link {
      background: none;
      border: 1px solid #ff6ec7;
      padding: 0.4rem 1rem;
      border-radius: 40px;
      color: #ffb3d9;
      text-decoration: none;
      font-size: 0.85rem;
      font-weight: 500;
      transition: 0.2s;
    }

    .btn-link:hover {
      background: #ff6ec7;
      color: #0a0a0f;
    }

    .achievements-list {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      list-style: none;
      margin-top: 0.5rem;
    }

    .achievements-list li {
      background: rgba(255,110,199,0.12);
      padding: 0.5rem 1rem;
      border-radius: 40px;
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 0.6rem;
    }

    .achievements-list li i {
      color: #ffb347;
    }

    hr {
      border-color: rgba(255,110,199,0.2);
      margin: 1rem 0;
    }

    footer {
      text-align: center;
      padding: 2rem 0 1rem;
      color: #8e9aaf;
      font-size: 0.9rem;
    }

    @media (max-width: 680px) {
      h1 {
        font-size: 2.4rem;
      }
      .subtitle {
        font-size: 1.2rem;
      }
      .section-card {
        padding: 1.5rem;
      }
    }
  </style>
</head>
<body>

<div class="animated-bg"></div>
<div class="cursor-glow" id="cursorGlow"></div>

<div class="container">
  <!-- HERO / BANNER SECTION (attractive) -->
  <div class="hero" data-aos="fade-up" data-aos-duration="800">
    <!-- you can replace with actual image, but I'll use a modern avatar placeholder with gradient -->
    <div style="position: relative;">
      <img src="https://ui-avatars.com/api/?background=FF6EC7&color=fff&rounded=true&size=140&bold=true&name=Ayush+Kumar" alt="Ayush Kumar" class="banner-img" />
      <div style="position: absolute; bottom: 5px; right: 5px; background: #0f0f1a; border-radius: 30px; padding: 4px 10px; font-size: 0.7rem; font-weight: bold; border:1px solid #ff6ec7;">✨ MERN</div>
    </div>
    <h1>Ayush Kumar</h1>
    <div class="typed-wrapper">
      <div class="subtitle" id="typedLine">🚀 Full Stack Developer | MERN Stack</div>
    </div>
    <div class="social-links">
      <a href="https://linkedin.com/in/ayush-kumar-35499a32b" target="_blank" class="social-icon"><i class="fab fa-linkedin-in"></i> LinkedIn</a>
      <a href="mailto:aksrivastav0825@gmail.com" class="social-icon"><i class="fas fa-envelope"></i> Email</a>
      <a href="https://github.com/Ayush8292006" target="_blank" class="social-icon"><i class="fab fa-github"></i> GitHub</a>
    </div>
  </div>

  <!-- About + Tech combined card -->
  <div class="section-card" data-aos="fade-right" data-aos-duration="700">
    <div class="section-title">
      <i class="fas fa-code"></i> 
      <span>About Me & Tech Arsenal</span>
    </div>
    <div style="display: flex; flex-wrap: wrap; gap: 2rem; justify-content: space-between;">
      <div style="flex: 1.5;">
        <p style="font-size: 1.05rem; line-height: 1.6; margin-bottom: 1rem;">💻 <strong>Full Stack Developer</strong> (React, Node.js, MongoDB)<br>
        ⚡ Built real-time & scalable applications · 🧠 Solved 200+ DSA problems (C++)<br>
        🚀 Focused on production-level projects · 🎯 Open to Internship opportunities</p>
        <div style="display: flex; gap: 0.8rem; flex-wrap: wrap; margin-top: 0.8rem;">
          <span style="background:#ff6ec720; padding:0.3rem 1rem; border-radius:30px;"><i class="fas fa-database"></i> MongoDB</span>
          <span style="background:#ff6ec720; padding:0.3rem 1rem; border-radius:30px;"><i class="fab fa-react"></i> React</span>
          <span style="background:#ff6ec720; padding:0.3rem 1rem; border-radius:30px;"><i class="fab fa-node-js"></i> Node.js</span>
          <span style="background:#ff6ec720; padding:0.3rem 1rem; border-radius:30px;"><i class="fas fa-cloud"></i> Stripe</span>
        </div>
      </div>
      <div style="flex: 2;">
        <div class="tech-icons">
          <img src="https://skillicons.dev/icons?i=html,css,js,react,nodejs,express,mongodb,cpp,python,git,github,vercel,tailwind" alt="tech stack" style="max-width:100%;">
        </div>
      </div>
    </div>
  </div>

  <!-- Featured Projects -->
  <div class="section-card" data-aos="fade-up" data-aos-duration="700">
    <div class="section-title">
      <i class="fas fa-rocket"></i>
      <span>🔥 Featured Projects</span>
    </div>
    <div class="projects-grid">
      <!-- CineBook -->
      <div class="project-card">
        <div class="project-title"><i class="fas fa-film" style="color:#ff6ec7;"></i> CineBook</div>
        <div class="project-desc">Real-time seat booking with locking system + Stripe payments + email tickets. Production ready full-stack MERN app.</div>
        <div class="project-links">
          <a href="https://cinebook-omega.vercel.app/" target="_blank" class="btn-link"><i class="fas fa-external-link-alt"></i> Live Demo</a>
          <a href="https://github.com/Ayush8292006/CineBook-TicketBooking" target="_blank" class="btn-link"><i class="fab fa-github"></i> Code</a>
        </div>
      </div>
      <!-- AI Assistant -->
      <div class="project-card">
        <div class="project-title"><i class="fas fa-microphone-alt" style="color:#ff6ec7;"></i> AI Assistant</div>
        <div class="project-desc">Voice + text AI assistant with authentication & chat history, powered by modern API integrations.</div>
        <div class="project-links">
          <a href="https://virtual-chatbot-sandy.vercel.app" target="_blank" class="btn-link"><i class="fas fa-external-link-alt"></i> Live Demo</a>
          <a href="https://github.com/Ayush8292006/Virtual-Chatbot" target="_blank" class="btn-link"><i class="fab fa-github"></i> Code</a>
        </div>
      </div>
      <!-- ProjectFlow -->
      <div class="project-card">
        <div class="project-title"><i class="fas fa-tasks" style="color:#ff6ec7;"></i> ProjectFlow</div>
        <div class="project-desc">Kanban board with drag & drop + optimized performance for 500+ tasks. Smooth UX and realtime updates.</div>
        <div class="project-links">
          <a href="https://kanban-timeline-website.vercel.app/" target="_blank" class="btn-link"><i class="fas fa-external-link-alt"></i> Live Demo</a>
          <a href="https://github.com/Ayush8292006/kanban-timeline-website" target="_blank" class="btn-link"><i class="fab fa-github"></i> Code</a>
        </div>
      </div>
    </div>
  </div>

  <!-- Achievements + Stats -->
  <div class="section-card" data-aos="zoom-in" data-aos-duration="600">
    <div class="section-title">
      <i class="fas fa-trophy"></i>
      <span>🏆 Achievements & Milestones</span>
    </div>
    <div style="display: flex; flex-wrap: wrap; gap: 1.5rem; justify-content: space-between;">
      <ul class="achievements-list" style="flex:1;">
        <li><i class="fas fa-brain"></i> Solved 200+ DSA problems (C++)</li>
        <li><i class="fas fa-chart-line"></i> Built real-time applications with WebSockets</li>
        <li><i class="fas fa-credit-card"></i> Implemented Stripe payment system</li>
        <li><i class="fas fa-tachometer-alt"></i> Optimized apps for 500+ concurrent users</li>
        <li><i class="fas fa-lock"></i> Strong in authentication (JWT, OAuth) & APIs</li>
      </ul>
      <div style="flex:0.5; text-align: center; background: rgba(255,110,199,0.1); border-radius: 30px; padding: 1rem;">
        <i class="fas fa-code-branch" style="font-size: 2rem; color:#ff6ec7;"></i>
        <p style="font-weight: bold; margin-top: 0.5rem;">20+ <br> Projects</p>
      </div>
    </div>
  </div>

  <!-- Connect & Quote -->
  <div class="section-card" data-aos="fade-left" data-aos-duration="600" style="text-align: center;">
    <div class="section-title" style="justify-content: center; border-left: none;">
      <i class="fas fa-globe"></i> <span>Let's Connect</span>
    </div>
    <div style="display: flex; justify-content: center; gap: 2rem; flex-wrap: wrap; margin: 1rem 0;">
      <a href="https://linkedin.com/in/ayush-kumar-35499a32b" target="_blank" style="background:#ff6ec722; padding: 0.7rem 2rem; border-radius: 60px; text-decoration: none; color: white; font-weight:600;"><i class="fab fa-linkedin"></i> LinkedIn</a>
      <a href="mailto:aksrivastav0825@gmail.com" style="background:#ff6ec722; padding: 0.7rem 2rem; border-radius: 60px; text-decoration: none; color: white; font-weight:600;"><i class="fas fa-envelope"></i> aksrivastav0825@gmail.com</a>
      <a href="https://github.com/Ayush8292006" target="_blank" style="background:#ff6ec722; padding: 0.7rem 2rem; border-radius: 60px; text-decoration: none; color: white; font-weight:600;"><i class="fab fa-github"></i> GitHub</a>
    </div>
    <hr>
    <p style="font-size: 1.3rem; font-weight: 500; letter-spacing: 1px;">⚡ "Code. Build. Scale."</p>
  </div>

  <footer>
    <i class="fas fa-crown" style="color:#ff6ec7;"></i> Ayush Kumar — Full Stack Developer | MERN expert — constantly building the future.
  </footer>
</div>

<!-- Scripts -->
<script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
  AOS.init({
    duration: 800,
    once: true,
    offset: 100,
  });

  // Dynamic typing animation for subtitle line (professional animated text)
  const typedElement = document.getElementById('typedLine');
  const phrases = [
    "🚀 Full Stack Developer | MERN Stack",
    "💻 React • Node.js • MongoDB",
    "⚡ Real-time Apps & Scalable Systems",
    "🎯 Open to Internships & Opportunities"
  ];
  let phraseIndex = 0;
  let charIndex = 0;
  let isDeleting = false;
  let currentText = '';

  function typeEffect() {
    const fullText = phrases[phraseIndex];
    if (isDeleting) {
      currentText = fullText.substring(0, charIndex - 1);
      charIndex--;
    } else {
      currentText = fullText.substring(0, charIndex + 1);
      charIndex++;
    }
    typedElement.textContent = currentText;

    if (!isDeleting && charIndex === fullText.length) {
      isDeleting = true;
      setTimeout(typeEffect, 2000);
      return;
    }
    if (isDeleting && charIndex === 0) {
      isDeleting = false;
      phraseIndex = (phraseIndex + 1) % phrases.length;
      setTimeout(typeEffect, 400);
      return;
    }
    const speed = isDeleting ? 60 : 100;
    setTimeout(typeEffect, speed);
  }

  typeEffect();

  // cursor glow effect
  const cursorGlow = document.getElementById('cursorGlow');
  document.addEventListener('mousemove', (e) => {
    cursorGlow.style.left = e.clientX + 'px';
    cursorGlow.style.top = e.clientY + 'px';
  });

  // add smooth scroll to anchors if any
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
      const target = document.querySelector(this.getAttribute('href'));
      if (target) {
        e.preventDefault();
        target.scrollIntoView({ behavior: 'smooth' });
      }
    });
  });
</script>
</body>
</html>
