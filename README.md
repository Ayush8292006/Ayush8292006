<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Ayush Kumar · MERN Stack · GitHub Profile</title>
  <!-- Google Fonts + Font Awesome 6 -->
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- AOS CSS -->
  <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background: #0d0f14;
      color: #eef2ff;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }

    /* dynamic gradient orb background */
    .bg-orb {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -2;
      background: radial-gradient(circle at 30% 10%, #0a0c15, #010101);
    }

    .bg-orb::after {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at 70% 80%, rgba(255, 80, 140, 0.15), transparent 60%);
      pointer-events: none;
    }

    .noise {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: -1;
      opacity: 0.3;
    }

    /* main container with max-width like github readme but modern */
    .github-container {
      max-width: 1280px;
      margin: 2rem auto;
      padding: 0 1.8rem;
      position: relative;
      z-index: 2;
    }

    /* animated banner card (profile header) */
    .banner-card {
      background: rgba(18, 22, 35, 0.7);
      backdrop-filter: blur(16px);
      border-radius: 2.5rem;
      padding: 2rem 2rem 2rem 2rem;
      margin-bottom: 2rem;
      border: 1px solid rgba(255, 110, 199, 0.25);
      box-shadow: 0 25px 35px -18px rgba(0, 0, 0, 0.6);
      transition: transform 0.2s ease, box-shadow 0.2s;
      text-align: center;
    }

    .banner-card:hover {
      border-color: rgba(255, 110, 199, 0.6);
      box-shadow: 0 30px 40px -18px rgba(255, 110, 199, 0.25);
    }

    .avatar-wrapper {
      display: inline-block;
      position: relative;
    }

    .avatar {
      width: 130px;
      height: 130px;
      border-radius: 50%;
      background: linear-gradient(145deg, #ff6ec7, #c147e9);
      padding: 3px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 1rem;
    }

    .avatar img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 50%;
      background: #0f111a;
    }

    .glow-text {
      font-size: 3rem;
      font-weight: 800;
      background: linear-gradient(120deg, #FFFFFF, #ffb8da, #d9a7ff);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      letter-spacing: -0.02em;
    }

    .typing-area {
      min-height: 80px;
      font-size: 1.5rem;
      font-weight: 500;
      color: #cbd5ff;
      margin: 0.7rem 0;
    }

    .badge-group {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 0.8rem;
      margin-top: 1.2rem;
    }

    .badge {
      background: rgba(255, 110, 199, 0.12);
      padding: 0.4rem 1.2rem;
      border-radius: 60px;
      font-size: 0.85rem;
      font-weight: 500;
      backdrop-filter: blur(4px);
      border: 1px solid rgba(255, 110, 199, 0.3);
    }

    .badge i {
      margin-right: 6px;
      color: #ff9fcf;
    }

    /* social row */
    .social-row {
      display: flex;
      justify-content: center;
      gap: 1.8rem;
      margin: 1.5rem 0 0.5rem;
    }

    .social-btn {
      background: rgba(30, 34, 48, 0.8);
      padding: 0.6rem 1.5rem;
      border-radius: 40px;
      text-decoration: none;
      color: #f0f3ff;
      font-weight: 600;
      transition: 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      border: 1px solid rgba(255, 255, 255, 0.08);
    }

    .social-btn i {
      font-size: 1.2rem;
      color: #ff6ec7;
    }

    .social-btn:hover {
      background: #ff6ec7;
      color: #0b0e16;
      transform: translateY(-3px);
      border-color: #ff6ec7;
    }

    .social-btn:hover i {
      color: #0b0e16;
    }

    /* card style for sections (GitHub like but premium) */
    .repo-card {
      background: rgba(12, 16, 26, 0.65);
      backdrop-filter: blur(12px);
      border-radius: 1.8rem;
      padding: 1.6rem 2rem;
      margin-bottom: 2rem;
      border: 1px solid rgba(255, 255, 255, 0.05);
      transition: all 0.2s;
    }

    .section-header {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 1.5rem;
      font-size: 1.7rem;
      font-weight: 700;
      border-left: 4px solid #ff6ec7;
      padding-left: 1rem;
    }

    .section-header i {
      color: #ff6ec7;
      font-size: 1.6rem;
    }

    .tech-stack {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin: 1rem 0;
    }

    .tech-icon {
      background: #181e2c;
      border-radius: 16px;
      padding: 8px 12px;
      transition: all 0.2s;
    }

    .tech-icon img {
      width: 48px;
      filter: drop-shadow(0 0 3px rgba(255,110,199,0.4));
    }

    .tech-icon:hover {
      transform: translateY(-5px);
    }

    /* projects grid */
    .project-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(310px, 1fr));
      gap: 1.5rem;
      margin-top: 0.5rem;
    }

    .project-item {
      background: rgba(0, 0, 0, 0.45);
      border-radius: 1.5rem;
      padding: 1.3rem 1.5rem;
      border: 1px solid rgba(255, 110, 199, 0.2);
      transition: all 0.25s;
    }

    .project-item:hover {
      border-color: #ff6ec7;
      transform: translateY(-5px);
      background: rgba(20, 25, 45, 0.8);
    }

    .project-name {
      font-size: 1.4rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .project-desc {
      color: #b4c0e0;
      margin: 12px 0;
      line-height: 1.45;
    }

    .project-links a {
      display: inline-block;
      margin-right: 1rem;
      margin-top: 0.5rem;
      font-size: 0.85rem;
      background: rgba(255,110,199,0.1);
      padding: 0.3rem 1rem;
      border-radius: 30px;
      text-decoration: none;
      color: #ffc0e0;
      transition: 0.2s;
    }

    .project-links a:hover {
      background: #ff6ec7;
      color: #0a0c16;
    }

    .achievement-list {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      list-style: none;
    }

    .achievement-list li {
      background: rgba(255, 110, 199, 0.08);
      padding: 0.55rem 1.3rem;
      border-radius: 50px;
      font-weight: 500;
      font-size: 0.9rem;
    }

    .repo-stats {
      display: flex;
      gap: 1rem;
      margin-top: 1rem;
      color: #9aa4bf;
      font-size: 0.8rem;
    }

    footer {
      text-align: center;
      padding: 2rem 0 1rem;
      font-size: 0.85rem;
      opacity: 0.7;
    }

    @media (max-width: 700px) {
      .github-container {
        padding: 0 1rem;
      }
      .glow-text {
        font-size: 2rem;
      }
      .typing-area {
        font-size: 1rem;
      }
    }
  </style>
</head>
<body>
<div class="bg-orb"></div>
<div class="noise"></div>

<div class="github-container">
  <!-- MAIN BANNER (REPOSITORY FRONT PAGE) -->
  <div class="banner-card" data-aos="fade-up" data-aos-duration="900">
    <div class="avatar-wrapper">
      <div class="avatar">
        <!-- professional avatar with initials but looks clean -->
        <img src="https://ui-avatars.com/api/?background=1a1e2c&color=ff6ec7&rounded=true&size=120&bold=true&fontsize=0.55&name=Ayush+Kumar" alt="Ayush Kumar">
      </div>
    </div>
    <h1 class="glow-text">Ayush Kumar</h1>
    <div class="typing-area" id="dynamicRole"></div>
    <div class="badge-group">
      <span class="badge"><i class="fab fa-react"></i> React.js</span>
      <span class="badge"><i class="fab fa-node-js"></i> Node.js</span>
      <span class="badge"><i class="fas fa-database"></i> MongoDB</span>
      <span class="badge"><i class="fas fa-code-branch"></i> Express</span>
      <span class="badge"><i class="fas fa-cloud"></i> MERN Expert</span>
    </div>
    <div class="social-row">
      <a href="https://linkedin.com/in/ayush-kumar-35499a32b" target="_blank" class="social-btn"><i class="fab fa-linkedin-in"></i> LinkedIn</a>
      <a href="mailto:aksrivastav0825@gmail.com" class="social-btn"><i class="fas fa-envelope"></i> Email</a>
      <a href="https://github.com/Ayush8292006" target="_blank" class="social-btn"><i class="fab fa-github"></i> GitHub</a>
    </div>
  </div>

  <!-- ABOUT + TECH STACK (like a README intro) -->
  <div class="repo-card" data-aos="fade-right" data-aos-duration="700">
    <div class="section-header">
      <i class="fas fa-user-astronaut"></i>
      <span>About me</span>
    </div>
    <p style="font-size: 1.05rem; line-height: 1.6; margin-bottom: 1rem;">💻 Full Stack Developer specializing in <strong>MERN stack</strong> with a passion for building real-time, scalable web apps. Solved <strong>200+ DSA problems</strong> (C++) and love crafting production-grade solutions. 🚀 Open to internships & collaborations.</p>
    <div class="tech-stack">
      <!-- using skill icons with professional look -->
      <div class="tech-icon"><img src="https://skillicons.dev/icons?i=js" alt="JS"></div>
      <div class="tech-icon"><img src="https://skillicons.dev/icons?i=react" alt="React"></div>
      <div class="tech-icon"><img src="https://skillicons.dev/icons?i=nodejs" alt="Node"></div>
      <div class="tech-icon"><img src="https://skillicons.dev/icons?i=express" alt="Express"></div>
      <div class="tech-icon"><img src="https://skillicons.dev/icons?i=mongodb" alt="MongoDB"></div>
      <div class="tech-icon"><img src="https://skillicons.dev/icons?i=tailwind" alt="Tailwind"></div>
      <div class="tech-icon"><img src="https://skillicons.dev/icons?i=git" alt="Git"></div>
      <div class="tech-icon"><img src="https://skillicons.dev/icons?i=cpp" alt="C++"></div>
    </div>
  </div>

  <!-- FEATURED PROJECTS (SHOWCASING PINNED REPOS) -->
  <div class="repo-card" data-aos="fade-up" data-aos-duration="800">
    <div class="section-header">
      <i class="fas fa-star-of-life"></i>
      <span>📌 Pinned Projects · Real-world Impact</span>
    </div>
    <div class="project-grid">
      <!-- CineBook -->
      <div class="project-item">
        <div class="project-name"><i class="fas fa-ticket-alt" style="color:#ff6ec7;"></i> CineBook</div>
        <div class="project-desc">Real-time seat booking with locking system, Stripe payments, and email tickets. High concurrency handling.</div>
        <div class="project-links">
          <a href="https://cinebook-omega.vercel.app/" target="_blank"><i class="fas fa-globe"></i> Live</a>
          <a href="https://github.com/Ayush8292006/CineBook-TicketBooking" target="_blank"><i class="fab fa-github"></i> Repository</a>
        </div>
        <div class="repo-stats"><span><i class="fas fa-code-branch"></i> MERN + Stripe</span> <span><i class="fas fa-users"></i> Real-time</span></div>
      </div>
      <!-- AI Assistant -->
      <div class="project-item">
        <div class="project-name"><i class="fas fa-microphone-alt" style="color:#ff6ec7;"></i> AI Assistant</div>
        <div class="project-desc">Voice & text AI assistant with JWT authentication, chat history, and sleek UI.</div>
        <div class="project-links">
          <a href="https://virtual-chatbot-sandy.vercel.app" target="_blank"><i class="fas fa-globe"></i> Live</a>
          <a href="https://github.com/Ayush8292006/Virtual-Chatbot" target="_blank"><i class="fab fa-github"></i> Repository</a>
        </div>
        <div class="repo-stats"><span><i class="fas fa-robot"></i> OpenAI like</span> <span><i class="fas fa-database"></i> MongoDB</span></div>
      </div>
      <!-- ProjectFlow Kanban -->
      <div class="project-item">
        <div class="project-name"><i class="fas fa-tasks" style="color:#ff6ec7;"></i> ProjectFlow</div>
        <div class="project-desc">Kanban board with drag & drop, optimized for 500+ tasks, smooth drag-and-drop experience.</div>
        <div class="project-links">
          <a href="https://kanban-timeline-website.vercel.app/" target="_blank"><i class="fas fa-globe"></i> Live</a>
          <a href="https://github.com/Ayush8292006/kanban-timeline-website" target="_blank"><i class="fab fa-github"></i> Repository</a>
        </div>
        <div class="repo-stats"><span><i class="fas fa-chart-line"></i> Performance</span> <span><i class="fas fa-drag-drop"></i> DnD</span></div>
      </div>
    </div>
  </div>

  <!-- ACHIEVEMENTS & SKILL HIGHLIGHTS -->
  <div class="repo-card" data-aos="zoom-in" data-aos-duration="700">
    <div class="section-header">
      <i class="fas fa-medal"></i>
      <span>🏅 Achievements & Developer Milestones</span>
    </div>
    <ul class="achievement-list">
      <li><i class="fas fa-check-circle" style="color:#ff9fcf;"></i> 200+ DSA problems (C++)</li>
      <li><i class="fas fa-bolt"></i> Real-time apps with socket.io & concurrency</li>
      <li><i class="fas fa-credit-card"></i> Integrated Stripe payment gateway</li>
      <li><i class="fas fa-chart-simple"></i> Optimized apps for 500+ users/tasks</li>
      <li><i class="fas fa-shield-alt"></i> JWT, OAuth, authentication expert</li>
      <li><i class="fas fa-rocket"></i> Deployed full-stack apps on Vercel + Render</li>
    </ul>
    <div style="margin-top: 1.2rem; background: rgba(255,110,199,0.1); border-radius: 28px; padding: 0.8rem 1rem; text-align: center;">
      <i class="fas fa-code"></i> "Building scalable apps that solve real-world problems — always exploring new tech."
    </div>
  </div>

  <!-- GITHUB STATS & OPEN FOR INTERNSHIP BANNER -->
  <div class="repo-card" data-aos="fade-left" data-aos-duration="700" style="text-align: center;">
    <div class="section-header" style="justify-content: center; border-left: none;">
      <i class="fas fa-hand-peace"></i>
      <span>🤝 Open for Opportunities</span>
    </div>
    <p style="margin-bottom: 1rem;">I'm actively looking for <strong>internships / full‑time roles</strong> as a Full Stack Developer (MERN). Let's collaborate and build something impactful.</p>
    <div style="display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;">
      <span class="badge" style="background:#ff6ec7; color:#0a0c16;"><i class="fas fa-envelope-open-text"></i> aksrivastav0825@gmail.com</span>
      <span class="badge"><i class="fab fa-github"></i> @Ayush8292006</span>
    </div>
    <hr style="margin: 1.2rem 0; border-color: #ff6ec730;">
    <div style="display: flex; justify-content: center; gap: 1.2rem; font-size: 0.9rem;">
      <span><i class="fas fa-map-marker-alt"></i> Remote / India</span>
      <span><i class="fas fa-clock"></i> Immediate joiner</span>
    </div>
  </div>
  
  <footer>
    <i class="fas fa-code"></i> with ⚡ by Ayush Kumar — MERN Full Stack Developer — “Code. Build. Scale.”
  </footer>
</div>

<script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
  AOS.init({ duration: 700, once: true, offset: 20 });

  // professional typing animation for dynamic role line
  const roles = [
    "🚀 Full Stack Developer | MERN Stack",
    "💻 Building real-time web apps",
    "⚡ 200+ DSA problems (C++)",
    "🎯 Open for Internships"
  ];
  let roleIndex = 0;
  let charPos = 0;
  let isDeletingFlag = false;
  let currentRoleSpan = document.getElementById("dynamicRole");

  function animateTyping() {
    const full = roles[roleIndex];
    if (isDeletingFlag) {
      currentRoleSpan.textContent = full.substring(0, charPos - 1);
      charPos--;
    } else {
      currentRoleSpan.textContent = full.substring(0, charPos + 1);
      charPos++;
    }

    if (!isDeletingFlag && charPos === full.length) {
      isDeletingFlag = true;
      setTimeout(animateTyping, 1800);
      return;
    }
    if (isDeletingFlag && charPos === 0) {
      isDeletingFlag = false;
      roleIndex = (roleIndex + 1) % roles.length;
      setTimeout(animateTyping, 400);
      return;
    }
    const speed = isDeletingFlag ? 50 : 90;
    setTimeout(animateTyping, speed);
  }
  animateTyping();

  // add glow on card hover effect (extra micro-interaction)
  const cards = document.querySelectorAll('.repo-card, .banner-card');
  cards.forEach(card => {
    card.addEventListener('mouseenter', () => {
      card.style.transition = 'all 0.25s ease';
    });
  });
</script>
</body>
</html>
