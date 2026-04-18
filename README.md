<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Ayush Kumar · Full Stack MERN Dev</title>
  <!-- Google Fonts & Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Three.js Core + Addons for 3D hover canvas -->
  <script type="importmap">
    {
      "imports": {
        "three": "https://unpkg.com/three@0.128.0/build/three.module.js",
        "three/addons/": "https://unpkg.com/three@0.128.0/examples/jsm/"
      }
    }
  </script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0a0a1f;
      font-family: 'Inter', sans-serif;
      color: #eef5ff;
      line-height: 1.5;
      display: flex;
      justify-content: center;
      padding: 2rem 1rem;
    }

    /* main README card container */
    .readme-container {
      max-width: 1200px;
      width: 100%;
      background: rgba(10, 15, 30, 0.65);
      backdrop-filter: blur(2px);
      border-radius: 3rem;
      box-shadow: 0 25px 45px rgba(0, 240, 255, 0.15), 0 0 0 1px rgba(0, 240, 255, 0.2);
      overflow: hidden;
      padding: 2rem 2rem 2.5rem;
      transition: all 0.3s ease;
    }

    /* 3D canvas wrapper (floating background element) */
    #canvas-3d {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -2;
      pointer-events: none;
    }

    /* gradient overlay for readability */
    .gradient-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at 20% 30%, rgba(0, 20, 40, 0.7), rgba(5, 5, 20, 0.85));
      z-index: -1;
      pointer-events: none;
    }

    /* banner area with glass hover effect */
    .banner {
      text-align: center;
      margin-bottom: 2rem;
      transition: transform 0.4s cubic-bezier(0.2, 0.9, 0.4, 1.1);
    }
    .banner:hover {
      transform: scale(1.01);
    }
    .banner-img {
      width: 100%;
      max-height: 220px;
      object-fit: cover;
      border-radius: 2rem;
      box-shadow: 0 20px 35px -12px rgba(0, 212, 255, 0.4);
      transition: all 0.3s;
      border: 1px solid rgba(0, 240, 255, 0.3);
    }
    .banner-img:hover {
      box-shadow: 0 25px 45px -8px #00d4ff80;
    }

    h1 {
      font-size: 3.2rem;
      font-weight: 800;
      background: linear-gradient(135deg, #FFFFFF, #00F0FF, #6C63FF);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      margin: 1rem 0 0.5rem;
      letter-spacing: -0.02em;
    }

    .tagline {
      font-size: 1.3rem;
      font-weight: 500;
      color: #b9e6ff;
      border-bottom: 1px dashed #00f0ff40;
      display: inline-block;
      padding-bottom: 6px;
    }

    /* typing wrapper */
    .typing-wrapper {
      margin: 1.5rem 0 1rem;
    }

    /* 3D hover cards for sections */
    .card-3d {
      background: rgba(20, 25, 45, 0.55);
      backdrop-filter: blur(8px);
      border-radius: 2rem;
      padding: 1.5rem;
      margin-bottom: 2rem;
      transition: all 0.35s ease;
      border: 1px solid rgba(0, 212, 255, 0.2);
      box-shadow: 0 10px 25px -10px rgba(0,0,0,0.3);
    }
    .card-3d:hover {
      transform: translateY(-6px) rotateX(2deg);
      border-color: #00f0ffaa;
      box-shadow: 0 25px 40px -12px #00d4ff40;
      background: rgba(25, 32, 55, 0.75);
    }

    .section-title {
      font-size: 1.9rem;
      font-weight: 700;
      margin-bottom: 1.3rem;
      display: flex;
      align-items: center;
      gap: 12px;
      border-left: 5px solid #00F0FF;
      padding-left: 1.2rem;
    }
    .section-title i {
      color: #00F0FF;
      font-size: 1.8rem;
    }

    .tech-icons {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin-top: 0.5rem;
    }
    .tech-badge {
      background: #0f1428;
      padding: 0.5rem 1rem;
      border-radius: 40px;
      font-weight: 500;
      font-size: 0.9rem;
      transition: all 0.2s;
      border: 1px solid #2c3e66;
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }
    .tech-badge i, .tech-badge img {
      font-size: 1.1rem;
    }
    .tech-badge:hover {
      transform: scale(1.05);
      background: #00d4ff20;
      border-color: #00f0ff;
      color: white;
      box-shadow: 0 5px 12px rgba(0,212,255,0.2);
    }

    /* Projects grid */
    .projects-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1.8rem;
      margin-top: 1rem;
    }
    .project-card {
      flex: 1 1 280px;
      background: rgba(8, 12, 28, 0.7);
      border-radius: 1.6rem;
      padding: 1.4rem;
      transition: all 0.3s;
      border: 1px solid rgba(0,240,255,0.2);
      backdrop-filter: blur(4px);
    }
    .project-card:hover {
      transform: translateY(-8px) scale(1.01);
      border-color: #00f0ff;
      background: #0b112bd9;
      box-shadow: 0 20px 30px -12px #00a6ff30;
    }
    .project-title {
      font-size: 1.6rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .project-links {
      margin-top: 1rem;
      display: flex;
      gap: 1rem;
    }
    .btn-icon {
      background: none;
      border: 1px solid #00f0ff;
      padding: 0.4rem 1rem;
      border-radius: 30px;
      color: #00f0ff;
      font-size: 0.8rem;
      font-weight: 600;
      transition: 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      text-decoration: none;
    }
    .btn-icon:hover {
      background: #00f0ff;
      color: #0a0a1f;
      transform: scale(1.02);
    }

    /* stats row: minimal & elegant */
    .stats-row {
      display: flex;
      flex-wrap: wrap;
      gap: 1.5rem;
      justify-content: space-between;
      margin-bottom: 1rem;
    }
    .stat-badge {
      background: linear-gradient(145deg, #0f172a, #0a0f1e);
      padding: 1rem 1.5rem;
      border-radius: 2rem;
      text-align: center;
      flex: 1;
      min-width: 140px;
      transition: all 0.25s;
      border: 1px solid #1e2a4a;
    }
    .stat-badge:hover {
      transform: translateY(-4px);
      border-color: #00f0ff;
    }
    .stat-number {
      font-size: 2.2rem;
      font-weight: 800;
      color: #00F0FF;
    }

    .connect-icons {
      display: flex;
      justify-content: center;
      gap: 2rem;
      margin: 2rem 0 1rem;
    }
    .social-link {
      background: #0f1428;
      width: 55px;
      height: 55px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      font-size: 1.8rem;
      transition: 0.25s;
      color: #b9eaff;
      border: 1px solid #2a3c6e;
    }
    .social-link:hover {
      transform: scale(1.1) rotate(3deg);
      background: #00d4ff;
      color: #0a0a1f;
      border-color: white;
      box-shadow: 0 0 15px #00f0ff;
    }

    footer {
      text-align: center;
      margin-top: 2rem;
      font-size: 0.9rem;
      opacity: 0.8;
    }

    @media (max-width: 780px) {
      .readme-container {
        padding: 1.3rem;
      }
      h1 {
        font-size: 2.2rem;
      }
      .section-title {
        font-size: 1.5rem;
      }
    }
  </style>
</head>
<body>

  <!-- 3D Animated Canvas Background (floating particles + rotating torus) -->
  <canvas id="canvas-3d"></canvas>
  <div class="gradient-overlay"></div>

  <div class="readme-container">
    <!-- Banner with hover effect -->
    <div class="banner">
      <!-- Using an attractive gradient placeholder as banner (instead of external link) -->
      <div class="banner-img" style="background: linear-gradient(135deg, #001d2f, #0a1f3a, #00182c); display: flex; align-items: center; justify-content: center; height: 200px;">
        <div style="text-align: center;">
          <i class="fas fa-code" style="font-size: 4rem; color: #00f0ff; opacity: 0.8;"></i>
          <p style="font-size: 1.6rem; font-weight: 600; letter-spacing: 1px;">AYUSH KUMAR</p>
          <p style="font-size: 0.9rem;">Full Stack MERN · Real-Time Architect</p>
        </div>
      </div>
    </div>

    <h1 align="center">👋 Hi, I'm Ayush Kumar</h1>
    <div align="center" class="tagline">🚀 Full Stack Developer (MERN) | Real-Time Scalable Applications</div>

    <div align="center" class="typing-wrapper">
      <span id="dynamic-typing" style="font-size: 1.4rem; font-weight: 500; color: #b1f0ff;"></span>
    </div>

    <!-- About + mini stats row (clean professional) -->
    <div class="card-3d">
      <div class="section-title">
        <i class="fas fa-user-astronaut"></i> 
        <span>About Me</span>
      </div>
      <p style="font-size: 1.05rem; margin-bottom: 1.2rem;">💻 <strong>Full Stack MERN Developer</strong> with focus on scalable & real-time systems · ⚡ Solved <strong>200+ DSA problems</strong> in C++ · 🏗️ Built apps with <strong>JWT/OAuth, Stripe Payments, Concurrency Control & WebSockets</strong> · 🎯 Currently open to internships & full-time opportunities · 📍 B.Tech CSE (AI) | GL Bajaj Institute of Technology</p>
      
      <div class="stats-row">
        <div class="stat-badge"><div class="stat-number">200+</div><div>DSA Problems</div><i class="fas fa-code-branch"></i></div>
        <div class="stat-badge"><div class="stat-number">8+</div><div>Projects Shipped</div><i class="fas fa-rocket"></i></div>
        <div class="stat-badge"><div class="stat-number">500+</div><div>Concurrent Users</div><i class="fas fa-users"></i></div>
        <div class="stat-badge"><div class="stat-number">✨</div><div>Real-Time Apps</div><i class="fas fa-bolt"></i></div>
      </div>
    </div>

    <!-- Tech Stack (interactive badges) -->
    <div class="card-3d">
      <div class="section-title">
        <i class="fas fa-cogs"></i>
        <span>Tech Stack · Toolbox</span>
      </div>
      <div class="tech-icons">
        <span class="tech-badge"><i class="fab fa-html5"></i> HTML5</span>
        <span class="tech-badge"><i class="fab fa-css3-alt"></i> CSS3</span>
        <span class="tech-badge"><i class="fab fa-js"></i> JS/TS</span>
        <span class="tech-badge"><i class="fab fa-react"></i> React</span>
        <span class="tech-badge"><i class="fab fa-node-js"></i> Node.js</span>
        <span class="tech-badge"><i class="fas fa-database"></i> MongoDB</span>
        <span class="tech-badge"><i class="fab fa-aws"></i> Express</span>
        <span class="tech-badge"><i class="fab fa-git-alt"></i> Git/GitHub</span>
        <span class="tech-badge"><i class="fas fa-cloud"></i> Vercel</span>
        <span class="tech-badge"><i class="fab fa-stripe"></i> Stripe</span>
        <span class="tech-badge"><i class="fas fa-robot"></i> OpenAI/Gemini</span>
        <span class="tech-badge"><i class="fas fa-layer-group"></i> Tailwind</span>
        <span class="tech-badge"><i class="fas fa-bolt"></i> WebSockets</span>
      </div>
    </div>

    <!-- Featured Projects -->
    <div class="card-3d">
      <div class="section-title">
        <i class="fas fa-fire"></i>
        <span>🔥 Featured Projects</span>
      </div>
      <div class="projects-grid">
        <div class="project-card">
          <div class="project-title"><i class="fas fa-ticket-alt" style="color: #00f0ff;"></i> CineBook</div>
          <p style="margin: 0.5rem 0;">Movie ticket booking with real-time seat locking, Stripe payments, Clerk auth & TMDB.</p>
          <div class="project-links">
            <a href="#" class="btn-icon"><i class="fas fa-globe"></i> Demo</a>
            <a href="#" class="btn-icon"><i class="fab fa-github"></i> Code</a>
          </div>
        </div>
        <div class="project-card">
          <div class="project-title"><i class="fas fa-microphone-alt"></i> AI Virtual Assistant</div>
          <p>Voice + text AI chat using Gemini, persistent sessions, Web Speech API.</p>
          <div class="project-links">
            <a href="#" class="btn-icon"><i class="fas fa-globe"></i> Live</a>
            <a href="#" class="btn-icon"><i class="fab fa-github"></i> Repo</a>
          </div>
        </div>
        <div class="project-card">
          <div class="project-title"><i class="fas fa-tasks"></i> ProjectFlow</div>
          <p>Kanban board with timeline, drag & drop, virtual scrolling (500+ tasks) & Zustand.</p>
          <div class="project-links">
            <a href="#" class="btn-icon"><i class="fas fa-globe"></i> Demo</a>
            <a href="#" class="btn-icon"><i class="fab fa-github"></i> Code</a>
          </div>
        </div>
      </div>
    </div>

    <!-- Achievements / Skills Row with glowing hover -->
    <div class="card-3d">
      <div class="section-title">
        <i class="fas fa-trophy"></i>
        <span>Achievements & Impact</span>
      </div>
      <div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center;">
        <div class="tech-badge" style="background: #001e30;"><i class="fas fa-check-circle"></i> 200+ DSA (C++)</div>
        <div class="tech-badge" style="background: #001e30;"><i class="fas fa-check-circle"></i> Real-time seat booking sync</div>
        <div class="tech-badge" style="background: #001e30;"><i class="fas fa-check-circle"></i> Stripe webhooks integration</div>
        <div class="tech-badge" style="background: #001e30;"><i class="fas fa-check-circle"></i> Optimized 500+ concurrent users</div>
        <div class="tech-badge" style="background: #001e30;"><i class="fas fa-check-circle"></i> JWT/OAuth expert</div>
      </div>
    </div>

    <!-- Connect & Footer -->
    <div class="connect-icons">
      <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
      <a href="#" class="social-link"><i class="fas fa-envelope"></i></a>
      <a href="#" class="social-link"><i class="fab fa-github"></i></a>
      <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
    </div>

    <div align="center" style="margin-top: 10px;">
      <span style="background: #0a0f1e; padding: 0.4rem 1rem; border-radius: 40px; font-size: 0.85rem;"><i class="fas fa-eye"></i> Profile Views: <strong id="viewCount">1,284</strong> · </span>
      <span style="margin-left: 0.5rem;"><i class="fas fa-code"></i> Code. Build. Scale. Repeat.</span>
    </div>
    <footer>
      💡 Open for internships & full‑time roles — Let's build something extraordinary!
    </footer>
  </div>

  <script type="module">
    import * as THREE from 'three';
    import { OrbitControls } from 'three/addons/controls/OrbitControls.js';
    
    // --- setup 3D scene with animated particles and rotating torus knot (hover reactive but static auto)
    const canvas = document.getElementById('canvas-3d');
    const scene = new THREE.Scene();
    scene.background = null; // transparent
    const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
    camera.position.set(0, 2, 12);
    camera.lookAt(0, 0, 0);
    
    const renderer = new THREE.WebGLRenderer({ canvas, alpha: true });
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(window.devicePixelRatio);
    
    // lights
    const ambientLight = new THREE.AmbientLight(0x222222);
    scene.add(ambientLight);
    const pointLight = new THREE.PointLight(0x00aaff, 1, 30);
    pointLight.position.set(3, 5, 5);
    scene.add(pointLight);
    const backLight = new THREE.PointLight(0xff44cc, 0.5);
    backLight.position.set(-2, 1, -4);
    scene.add(backLight);
    
    // central torus knot with glow effect
    const geometry = new THREE.TorusKnotGeometry(1.2, 0.32, 180, 24, 3, 4);
    const material = new THREE.MeshStandardMaterial({ color: 0x00f0ff, emissive: 0x006688, roughness: 0.3, metalness: 0.7 });
    const knot = new THREE.Mesh(geometry, material);
    scene.add(knot);
    
    // floating particles (stars)
    const particlesCount = 1200;
    const particlesGeometry = new THREE.BufferGeometry();
    const posArray = new Float32Array(particlesCount * 3);
    for(let i = 0; i < particlesCount; i++) {
      posArray[i*3] = (Math.random() - 0.5) * 40;
      posArray[i*3+1] = (Math.random() - 0.5) * 20;
      posArray[i*3+2] = (Math.random() - 0.5) * 25 - 8;
    }
    particlesGeometry.setAttribute('position', new THREE.BufferAttribute(posArray, 3));
    const particlesMat = new THREE.PointsMaterial({ color: 0x88ddff, size: 0.08, transparent: true, opacity: 0.6 });
    const particlesMesh = new THREE.Points(particlesGeometry, particlesMat);
    scene.add(particlesMesh);
    
    // second smaller stars
    const starCount = 800;
    const starGeo = new THREE.BufferGeometry();
    const starPos = new Float32Array(starCount * 3);
    for(let i = 0; i < starCount; i++) {
      starPos[i*3] = (Math.random() - 0.5) * 80;
      starPos[i*3+1] = (Math.random() - 0.5) * 40;
      starPos[i*3+2] = (Math.random() - 0.5) * 40 - 20;
    }
    starGeo.setAttribute('position', new THREE.BufferAttribute(starPos, 3));
    const starMat = new THREE.PointsMaterial({ color: 0xffaa88, size: 0.05 });
    const starsField = new THREE.Points(starGeo, starMat);
    scene.add(starsField);
    
    // floating rings / aura
    const ringGeo = new THREE.TorusGeometry(1.5, 0.05, 64, 200);
    const ringMat = new THREE.MeshStandardMaterial({ color: 0x44ccff, emissive: 0x2266aa });
    const ring = new THREE.Mesh(ringGeo, ringMat);
    scene.add(ring);
    
    let time = 0;
    
    function animate() {
      requestAnimationFrame(animate);
      time += 0.008;
      knot.rotation.x = time * 0.5;
      knot.rotation.y = time * 0.7;
      ring.rotation.x = time * 0.3;
      ring.rotation.z = time * 0.2;
      particlesMesh.rotation.y = time * 0.05;
      starsField.rotation.x = time * 0.03;
      
      // gentle camera sway (subtle)
      camera.position.x += (0 - camera.position.x) * 0.02;
      camera.lookAt(0, 0.5, 0);
      renderer.render(scene, camera);
    }
    
    animate();
    
    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    });
    
    // optional: mousemove effect on knot (parallax-like)
    document.addEventListener('mousemove', (e) => {
      const x = (e.clientX / window.innerWidth) * 2 - 1;
      const y = (e.clientY / window.innerHeight) * 2 - 1;
      knot.rotation.y += (x * 0.02 - knot.rotation.y) * 0.05;
      knot.rotation.x += (y * 0.02 - knot.rotation.x) * 0.05;
    });
  </script>
  
  <script>
    // Typing effect (professional animated)
    const phrases = [
      "⚡ Building Production Grade Apps",
      "🎯 200+ DSA Problems Solved",
      "🔄 MERN + Next.js Expert",
      "💳 Real-Time Apps & Payments",
      "🚀 Open to Internships & Roles"
    ];
    let idx = 0;
    let charIdx = 0;
    let isDeleting = false;
    const typingSpan = document.getElementById('dynamic-typing');
    
    function typeEffect() {
      const current = phrases[idx];
      if (isDeleting) {
        typingSpan.textContent = current.substring(0, charIdx-1);
        charIdx--;
        if (charIdx === 0) {
          isDeleting = false;
          idx = (idx + 1) % phrases.length;
          setTimeout(typeEffect, 300);
          return;
        }
      } else {
        typingSpan.textContent = current.substring(0, charIdx+1);
        charIdx++;
        if (charIdx === current.length) {
          isDeleting = true;
          setTimeout(typeEffect, 1800);
          return;
        }
      }
      setTimeout(typeEffect, isDeleting ? 45 : 90);
    }
    typeEffect();
    
    // simple view counter simulation (just for aesthetics)
    let views = 1284;
    const viewEl = document.getElementById('viewCount');
    if(viewEl) {
      setInterval(() => {
        views += Math.floor(Math.random() * 3);
        viewEl.innerText = views.toLocaleString();
      }, 5000);
    }
    
    // make all demo links # behave smooth (prevent default but no actual link)
    document.querySelectorAll('.btn-icon, .social-link').forEach(link => {
      link.addEventListener('click', (e) => {
        if(link.getAttribute('href') === '#') {
          e.preventDefault();
          // gentle alert that these are placeholders for your real profile links
          if(link.classList.contains('social-link')) {
            console.log("Replace with actual social URL");
          }
        }
      });
    });
  </script>
</body>
</html>
