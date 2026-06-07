
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Fira+Code:wght@400;500&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --surface2: #16161f;
    --border: rgba(255,255,255,0.07);
    --border2: rgba(255,255,255,0.12);
    --accent: #7c5cfc;
    --accent2: #fc5caf;
    --accent3: #5cfcce;
    --text: #e8e8f0;
    --muted: #7070a0;
    --glow: rgba(124,92,252,0.15);
  }

  body {
    font-family: 'Space Grotesk', sans-serif;
    background: var(--bg);
    color: var(--text);
    padding: 0;
    margin: 0;
    min-height: 100vh;
    overflow-x: hidden;
  }

  .readme-wrap {
    max-width: 780px;
    margin: 0 auto;
    padding: 2rem 1.5rem 3rem;
    position: relative;
  }

  /* Animated grid background */
  .grid-bg {
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(124,92,252,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(124,92,252,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    z-index: 0;
    animation: gridPulse 8s ease-in-out infinite;
  }

  @keyframes gridPulse {
    0%, 100% { opacity: 0.5; }
    50% { opacity: 1; }
  }

  /* Floating orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    z-index: 0;
    pointer-events: none;
    animation: orbFloat 12s ease-in-out infinite;
  }
  .orb-1 { width: 300px; height: 300px; background: rgba(124,92,252,0.12); top: -100px; left: -100px; }
  .orb-2 { width: 250px; height: 250px; background: rgba(252,92,175,0.1); top: 50%; right: -80px; animation-delay: -4s; }
  .orb-3 { width: 200px; height: 200px; background: rgba(92,252,206,0.08); bottom: 100px; left: 20%; animation-delay: -8s; }

  @keyframes orbFloat {
    0%, 100% { transform: translateY(0) scale(1); }
    50% { transform: translateY(-30px) scale(1.05); }
  }

  .content { position: relative; z-index: 1; }

  /* ===== HERO SECTION ===== */
  .hero {
    border: 1px solid var(--border2);
    border-radius: 20px;
    background: linear-gradient(135deg, var(--surface) 0%, rgba(124,92,252,0.05) 100%);
    padding: 2.5rem;
    margin-bottom: 1.5rem;
    position: relative;
    overflow: hidden;
    animation: fadeSlideUp 0.6s ease both;
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: -1px;
    border-radius: 20px;
    padding: 1px;
    background: linear-gradient(135deg, rgba(124,92,252,0.5), rgba(252,92,175,0.3), transparent 60%);
    -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor;
    mask-composite: exclude;
    pointer-events: none;
  }

  .hero-inner {
    display: flex;
    align-items: center;
    gap: 2rem;
    flex-wrap: wrap;
  }

  .avatar-ring {
    position: relative;
    flex-shrink: 0;
  }

  .avatar {
    width: 90px;
    height: 90px;
    border-radius: 50%;
    background: linear-gradient(135deg, #7c5cfc, #fc5caf);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    font-weight: 700;
    color: #fff;
    position: relative;
    z-index: 1;
    letter-spacing: -1px;
    animation: avatarPulse 3s ease-in-out infinite;
  }

  @keyframes avatarPulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(124,92,252,0.4); }
    50% { box-shadow: 0 0 0 12px rgba(124,92,252,0); }
  }

  .avatar-ring::before {
    content: '';
    position: absolute;
    inset: -4px;
    border-radius: 50%;
    background: conic-gradient(from 0deg, #7c5cfc, #fc5caf, #5cfcce, #7c5cfc);
    animation: spin 4s linear infinite;
    z-index: 0;
  }

  .avatar-ring::after {
    content: '';
    position: absolute;
    inset: -2px;
    border-radius: 50%;
    background: var(--bg);
    z-index: 0;
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  .hero-text { flex: 1; min-width: 200px; }

  .greeting {
    font-size: 0.75rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    font-weight: 500;
    margin-bottom: 0.4rem;
    animation: fadeSlideUp 0.6s 0.1s ease both;
  }

  .hero-name {
    font-size: 2rem;
    font-weight: 700;
    line-height: 1.1;
    margin-bottom: 0.5rem;
    animation: fadeSlideUp 0.6s 0.15s ease both;
  }

  .hero-name .highlight {
    background: linear-gradient(135deg, #7c5cfc, #fc5caf);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-title {
    font-size: 0.95rem;
    color: var(--muted);
    display: flex;
    align-items: center;
    gap: 0.5rem;
    flex-wrap: wrap;
    animation: fadeSlideUp 0.6s 0.2s ease both;
  }

  .badge-pill {
    font-size: 0.7rem;
    padding: 3px 10px;
    border-radius: 20px;
    font-weight: 600;
    letter-spacing: 0.05em;
  }

  .badge-aspnet { background: rgba(81,43,212,0.25); color: #a78bfa; border: 1px solid rgba(81,43,212,0.4); }
  .badge-laravel { background: rgba(255,45,32,0.18); color: #fb7185; border: 1px solid rgba(255,45,32,0.3); }

  .hero-taglines {
    margin-top: 1.2rem;
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    animation: fadeSlideUp 0.6s 0.25s ease both;
  }

  .tagline {
    font-size: 0.88rem;
    color: var(--muted);
    display: flex;
    align-items: center;
    gap: 0.6rem;
  }

  .tagline-icon {
    width: 20px;
    height: 20px;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.7rem;
    flex-shrink: 0;
  }

  .ti-purp { background: rgba(124,92,252,0.2); }
  .ti-pink { background: rgba(252,92,175,0.2); }
  .ti-teal { background: rgba(92,252,206,0.2); }

  /* ===== SECTION CARD ===== */
  .section-card {
    border: 1px solid var(--border);
    border-radius: 16px;
    background: var(--surface);
    margin-bottom: 1.5rem;
    overflow: hidden;
    animation: fadeSlideUp 0.6s ease both;
  }

  .section-card:nth-child(2) { animation-delay: 0.1s; }
  .section-card:nth-child(3) { animation-delay: 0.2s; }
  .section-card:nth-child(4) { animation-delay: 0.3s; }

  .section-header {
    padding: 1.2rem 1.5rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 0.7rem;
    background: rgba(255,255,255,0.02);
  }

  .section-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    animation: dotBlink 2s ease-in-out infinite;
  }

  @keyframes dotBlink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }

  .section-title {
    font-size: 0.8rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .section-body { padding: 1.5rem; }

  /* ===== TECH GRID ===== */
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
    gap: 0.75rem;
  }

  .tech-chip {
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 0.65rem 0.9rem;
    display: flex;
    align-items: center;
    gap: 0.55rem;
    font-size: 0.82rem;
    font-weight: 500;
    color: var(--text);
    background: var(--surface2);
    cursor: default;
    transition: all 0.25s ease;
    position: relative;
    overflow: hidden;
  }

  .tech-chip::before {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity 0.25s ease;
  }

  .tech-chip:hover {
    border-color: var(--border2);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
  }

  .tech-chip:hover::before { opacity: 1; }

  .chip-icon {
    width: 22px;
    height: 22px;
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.65rem;
    font-weight: 700;
    flex-shrink: 0;
  }

  .ci-net { background: rgba(81,43,212,0.3); color: #a78bfa; }
  .ci-cs { background: rgba(35,145,32,0.25); color: #4ade80; }
  .ci-ef { background: rgba(81,43,212,0.2); color: #818cf8; }
  .ci-redis { background: rgba(220,56,45,0.25); color: #f87171; }
  .ci-sw { background: rgba(133,234,45,0.2); color: #a3e635; }
  .ci-lara { background: rgba(255,45,32,0.2); color: #fb7185; }
  .ci-react { background: rgba(32,35,42,0.5); color: #38bdf8; }
  .ci-redux { background: rgba(118,74,188,0.25); color: #c084fc; }
  .ci-mysql { background: rgba(0,59,87,0.4); color: #38bdf8; }
  .ci-sql { background: rgba(204,41,39,0.2); color: #f87171; }
  .ci-next { background: rgba(255,255,255,0.08); color: #e2e8f0; }
  .ci-api { background: rgba(10,126,164,0.25); color: #38bdf8; }

  .tech-chip:hover .chip-icon { transform: scale(1.1); }

  /* ===== SKILLS ===== */
  .skills-list {
    display: flex;
    flex-direction: column;
    gap: 0.65rem;
  }

  .skill-item {
    display: flex;
    align-items: flex-start;
    gap: 0.75rem;
    padding: 0.75rem 1rem;
    border-radius: 10px;
    background: var(--surface2);
    border: 1px solid var(--border);
    font-size: 0.87rem;
    transition: all 0.2s ease;
    cursor: default;
  }

  .skill-item:hover {
    border-color: rgba(124,92,252,0.3);
    background: rgba(124,92,252,0.05);
    transform: translateX(4px);
  }

  .skill-bullet {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--accent3));
    margin-top: 6px;
    flex-shrink: 0;
  }

  /* ===== CONTACT ===== */
  .contact-links {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .contact-link {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    padding: 0.75rem 1.25rem;
    border-radius: 12px;
    border: 1px solid var(--border2);
    background: var(--surface2);
    text-decoration: none;
    color: var(--text);
    font-size: 0.875rem;
    font-weight: 500;
    transition: all 0.25s ease;
    flex: 1;
    min-width: 140px;
    justify-content: center;
    cursor: pointer;
  }

  .contact-link.gh { border-color: rgba(255,255,255,0.15); }
  .contact-link.li { border-color: rgba(0,119,181,0.35); }

  .contact-link:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 32px rgba(0,0,0,0.4);
  }

  .contact-link.gh:hover { background: rgba(255,255,255,0.06); border-color: rgba(255,255,255,0.25); }
  .contact-link.li:hover { background: rgba(0,119,181,0.12); border-color: rgba(0,119,181,0.5); }

  .link-icon {
    width: 28px;
    height: 28px;
    border-radius: 7px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.85rem;
  }

  .link-icon.gh { background: rgba(255,255,255,0.08); }
  .link-icon.li { background: rgba(0,119,181,0.2); color: #38bdf8; }

  /* ===== STATS ROW ===== */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0.75rem;
    margin-bottom: 1.5rem;
    animation: fadeSlideUp 0.6s 0.05s ease both;
  }

  .stat-card {
    border: 1px solid var(--border);
    border-radius: 14px;
    background: var(--surface);
    padding: 1.2rem 1rem;
    text-align: center;
    position: relative;
    overflow: hidden;
    cursor: default;
    transition: all 0.25s ease;
  }

  .stat-card::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 2px;
  }

  .stat-card.s1::after { background: linear-gradient(90deg, var(--accent), transparent); }
  .stat-card.s2::after { background: linear-gradient(90deg, var(--accent2), transparent); }
  .stat-card.s3::after { background: linear-gradient(90deg, var(--accent3), transparent); }

  .stat-card:hover { transform: translateY(-3px); border-color: var(--border2); }

  .stat-num {
    font-size: 1.8rem;
    font-weight: 700;
    line-height: 1;
    margin-bottom: 0.3rem;
  }

  .stat-card.s1 .stat-num { background: linear-gradient(135deg, var(--accent), #a78bfa); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .stat-card.s2 .stat-num { background: linear-gradient(135deg, var(--accent2), #fb923c); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .stat-card.s3 .stat-num { background: linear-gradient(135deg, var(--accent3), #34d399); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }

  .stat-label { font-size: 0.72rem; color: var(--muted); font-weight: 500; letter-spacing: 0.05em; }

  /* ===== COPY BUTTON ===== */
  .copy-btn-wrap {
    text-align: center;
    margin-top: 2rem;
  }

  .copy-btn {
    display: inline-flex;
    align-items: center;
    gap: 0.6rem;
    padding: 0.75rem 1.75rem;
    border-radius: 12px;
    border: 1px solid rgba(124,92,252,0.4);
    background: rgba(124,92,252,0.1);
    color: #a78bfa;
    font-family: 'Space Grotesk', sans-serif;
    font-size: 0.875rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.25s ease;
    letter-spacing: 0.03em;
  }

  .copy-btn:hover {
    background: rgba(124,92,252,0.2);
    border-color: rgba(124,92,252,0.6);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(124,92,252,0.2);
  }

  .copy-btn:active { transform: scale(0.97); }

  /* ===== ANIMATIONS ===== */
  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes shimmer {
    0% { background-position: -200% center; }
    100% { background-position: 200% center; }
  }

  /* terminal line */
  .terminal-line {
    font-family: 'Fira Code', monospace;
    font-size: 0.78rem;
    color: var(--accent3);
    background: rgba(92,252,206,0.06);
    border: 1px solid rgba(92,252,206,0.15);
    border-radius: 8px;
    padding: 0.5rem 1rem;
    margin-top: 1rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .term-prompt { color: var(--accent2); }
  .term-cursor {
    display: inline-block;
    width: 2px;
    height: 13px;
    background: var(--accent3);
    margin-left: 2px;
    animation: blink 1s step-end infinite;
    vertical-align: middle;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border2), transparent);
    margin: 0.25rem 0;
  }

  /* Responsive */
  @media (max-width: 520px) {
    .hero-inner { flex-direction: column; align-items: flex-start; }
    .stats-row { grid-template-columns: 1fr 1fr; }
    .stats-row .stat-card:last-child { grid-column: span 2; }
    .tech-grid { grid-template-columns: repeat(auto-fill, minmax(110px, 1fr)); }
  }
</style>

<div class="grid-bg"></div>
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<div class="readme-wrap">
  <div class="content">

    <!-- HERO -->
    <div class="hero">
      <div class="hero-inner">
        <div class="avatar-ring">
          <div class="avatar">JM</div>
        </div>
        <div class="hero-text">
          <div class="greeting">👋 Welcome to my profile</div>
          <div class="hero-name">
            Jassim <span class="highlight">Mohammed</span>
          </div>
          <div class="hero-title">
            Backend Developer
            <span class="badge-pill badge-aspnet">ASP.NET Core</span>
            <span class="badge-pill badge-laravel">Laravel</span>
          </div>
          <div class="hero-taglines">
            <div class="tagline">
              <div class="tagline-icon ti-purp">🚀</div>
              أبني تطبيقات سريعة، آمنة، وقابلة للتوسع
            </div>
            <div class="tagline">
              <div class="tagline-icon ti-teal">🎯</div>
              أسعى للعمل على مشاريع عالمية المستوى
            </div>
          </div>
          <div class="terminal-line">
            <span class="term-prompt">~/jasbx222 $</span>
            <span>git commit -m "Building the future, one API at a time"</span>
            <span class="term-cursor"></span>
          </div>
        </div>
      </div>
    </div>

    <!-- STATS -->
    <div class="stats-row">
      <div class="stat-card s1">
        <div class="stat-num">2+</div>
        <div class="stat-label">Frameworks</div>
      </div>
      <div class="stat-card s2">
        <div class="stat-num">12+</div>
        <div class="stat-label">Technologies</div>
      </div>
      <div class="stat-card s3">
        <div class="stat-num">∞</div>
        <div class="stat-label">Passion</div>
      </div>
    </div>

    <!-- TECH STACK -->
    <div class="section-card">
      <div class="section-header">
        <div class="section-dot"></div>
        <div class="section-title">🛠 Tech Stack</div>
      </div>
      <div class="section-body">
        <div class="tech-grid">
          <div class="tech-chip"><div class="chip-icon ci-net">.NET</div>ASP.NET Core</div>
          <div class="tech-chip"><div class="chip-icon ci-cs">C#</div>C Sharp</div>
          <div class="tech-chip"><div class="chip-icon ci-ef">EF</div>EF Core</div>
          <div class="tech-chip"><div class="chip-icon ci-redis">R</div>Redis</div>
          <div class="tech-chip"><div class="chip-icon ci-sw">SW</div>Swagger</div>
          <div class="tech-chip"><div class="chip-icon ci-lara">L</div>Laravel</div>
          <div class="tech-chip"><div class="chip-icon ci-react">⚛</div>React</div>
          <div class="tech-chip"><div class="chip-icon ci-redux">Rx</div>Redux</div>
          <div class="tech-chip"><div class="chip-icon ci-mysql">MY</div>MySQL</div>
          <div class="tech-chip"><div class="chip-icon ci-sql">SQL</div>SQL Server</div>
          <div class="tech-chip"><div class="chip-icon ci-next">N</div>Next.js</div>
          <div class="tech-chip"><div class="chip-icon ci-api">API</div>REST API</div>
        </div>
      </div>
    </div>

    <!-- SKILLS -->
    <div class="section-card">
      <div class="section-header">
        <div class="section-dot"></div>
        <div class="section-title">🧠 Core Skills</div>
      </div>
      <div class="section-body">
        <div class="skills-list">
          <div class="skill-item"><div class="skill-bullet"></div>Building RESTful APIs with ASP.NET Core & Laravel</div>
          <div class="skill-item"><div class="skill-bullet"></div>Entity Framework Core — Code First & Database First</div>
          <div class="skill-item"><div class="skill-bullet"></div>Redis Caching & Cache Invalidation strategies</div>
          <div class="skill-item"><div class="skill-bullet"></div>Swagger / OpenAPI Documentation</div>
          <div class="skill-item"><div class="skill-bullet"></div>Dependency Injection & Repository Pattern</div>
          <div class="skill-item"><div class="skill-bullet"></div>Authentication & Authorization with JWT</div>
          <div class="skill-item"><div class="skill-bullet"></div>SQL Server & MySQL Database Design</div>
          <div class="skill-item"><div class="skill-bullet"></div>State Management with Redux Toolkit</div>
          <div class="skill-item"><div class="skill-bullet"></div>Data Fetching with React Query</div>
        </div>
      </div>
    </div>

    <!-- CONTACT -->
    <div class="section-card">
      <div class="section-header">
        <div class="section-dot"></div>
        <div class="section-title">📫 Connect with Me</div>
      </div>
      <div class="section-body">
        <div class="contact-links">
          <div class="contact-link gh" onclick="openLink('https://github.com/jasbx222')">
            <div class="link-icon gh">⬡</div>
            <div>
              <div style="font-size:0.78rem;color:var(--muted);font-weight:400;">GitHub</div>
              <div>jasbx222</div>
            </div>
          </div>
          <div class="contact-link li" onclick="openLink('https://www.linkedin.com/in/jassim-mohamed-253a98295')">
            <div class="link-icon li">in</div>
            <div>
              <div style="font-size:0.78rem;color:var(--muted);font-weight:400;">LinkedIn</div>
              <div>Jassim Mohammed</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- COPY BUTTON -->
    <div class="copy-btn-wrap">
      <button class="copy-btn" onclick="copyMarkdown()">
        📋 Copy README Markdown
      </button>
    </div>

  </div>
</div>

<script>
const README_CONTENT = `# Hi, I'm Jassim Mohammed 👋

<div align="center">

![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=7C5CFC&center=true&vCenter=true&width=500&lines=Backend+Developer;ASP.NET+Core+%7C+Laravel;Building+Scalable+APIs;Clean+Code+%7C+Best+Practices)

</div>

---

\`\`\`typescript
const jassim = {
  role: "Backend Developer",
  specialization: ["ASP.NET Core", "Laravel"],
  passion: "Building fast, secure & scalable applications",
  goal: "Working on world-class projects",
  currentlyLearning: "Advanced System Design & Cloud Architecture"
};
\`\`\`

---

## 🛠 Tech Stack

### Backend
![ASP.NET Core](https://img.shields.io/badge/ASP.NET_Core-512BD4?style=for-the-badge&logo=.net&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white)
![Entity Framework Core](https://img.shields.io/badge/EF_Core-512BD4?style=for-the-badge&logo=.net&logoColor=white)
![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)
![REST API](https://img.shields.io/badge/REST_API-0A7EA4?style=for-the-badge&logoColor=white)

### Frontend
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![Redux](https://img.shields.io/badge/Redux-764ABC?style=for-the-badge&logo=redux&logoColor=white)

### Databases
![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-003B57?style=for-the-badge&logo=mysql&logoColor=white)

---

## 🧠 Core Skills

- ⚡ Building RESTful APIs with ASP.NET Core & Laravel
- ⚡ Entity Framework Core (Code First & Database First)
- ⚡ Redis Caching & Cache Invalidation strategies
- ⚡ Swagger / OpenAPI Documentation
- ⚡ Dependency Injection & Repository Pattern
- ⚡ Authentication & Authorization (JWT)
- ⚡ SQL Server & MySQL Database Design
- ⚡ State Management using Redux Toolkit
- ⚡ Data Fetching with React Query

---

## 📊 GitHub Stats

<div align="center">

![Jassim's GitHub Stats](https://github-readme-stats.vercel.app/api?username=jasbx222&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0a0a0f&title_color=7c5cfc&icon_color=fc5caf&text_color=e8e8f0)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=jasbx222&layout=compact&theme=tokyonight&hide_border=true&bg_color=0a0a0f&title_color=7c5cfc&text_color=e8e8f0)

</div>

---

## 📫 Contact Me

<div align="center">

[![GitHub](https://img.shields.io/badge/GitHub-jasbx222-181717?style=for-the-badge&logo=github)](https://github.com/jasbx222)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Jassim_Mohammed-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/jassim-mohamed-253a98295)

</div>

---

<div align="center">

*"Building the future, one API at a time"* 🚀

</div>`;

function copyMarkdown() {
  navigator.clipboard.writeText(README_CONTENT).then(() => {
    const btn = document.querySelector('.copy-btn');
    btn.textContent = '✅ Copied!';
    btn.style.background = 'rgba(92,252,206,0.15)';
    btn.style.borderColor = 'rgba(92,252,206,0.5)';
    btn.style.color = '#5cfcce';
    setTimeout(() => {
      btn.innerHTML = '📋 Copy README Markdown';
      btn.style.background = '';
      btn.style.borderColor = '';
      btn.style.color = '';
    }, 2500);
  });
}
</script>
