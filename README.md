<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TS137 — GitHub Profile README Preview</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
            mono: ['JetBrains Mono', 'monospace'],
          }
        }
      }
    }
  </script>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { background: #000; font-family: 'Inter', sans-serif; color: #e5e5e5; }

    /* Scrollbar */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: transparent; }
    ::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.1); border-radius: 3px; }

    /* Animations */
    @keyframes slideInUp {
      from { transform: translateY(30px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes pulse-slow {
      0%, 100% { opacity: 0.06; transform: scale(1); }
      50% { opacity: 0.1; transform: scale(1.1); }
    }
    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-8px); }
    }
    @keyframes shimmer {
      0% { transform: translateX(-100%); }
      100% { transform: translateX(100%); }
    }
    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0; }
    }
    @keyframes typing {
      from { width: 0; }
      to { width: 100%; }
    }

    .animate-in {
      animation: slideInUp 0.6s ease-out forwards;
      opacity: 0;
    }
    .delay-1 { animation-delay: 0.1s; }
    .delay-2 { animation-delay: 0.2s; }
    .delay-3 { animation-delay: 0.3s; }
    .delay-4 { animation-delay: 0.4s; }
    .delay-5 { animation-delay: 0.5s; }
    .delay-6 { animation-delay: 0.6s; }
    .delay-7 { animation-delay: 0.7s; }
    .delay-8 { animation-delay: 0.8s; }

    /* Glow orbs */
    .glow-orb {
      position: absolute;
      border-radius: 50%;
      filter: blur(120px);
      pointer-events: none;
      animation: pulse-slow 6s ease-in-out infinite;
    }

    /* GitHub-style README preview */
    .readme-preview {
      background: #0d1117;
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 12px;
      overflow: hidden;
    }
    .readme-preview .header-bar {
      background: #161b22;
      border-bottom: 1px solid rgba(255,255,255,0.08);
      padding: 12px 16px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .readme-preview .dot {
      width: 12px; height: 12px; border-radius: 50%;
    }
    .readme-preview .content {
      padding: 32px 40px;
      max-width: 900px;
      margin: 0 auto;
    }

    /* Typing effect in preview */
    .typing-text {
      display: inline-block;
      overflow: hidden;
      white-space: nowrap;
      border-right: 3px solid #818cf8;
      animation: typing 2.5s steps(20, end) forwards, blink 0.8s step-end infinite;
      width: 0;
    }
    .typing-text-2 {
      animation-delay: 2.8s;
    }

    /* Stat cards */
    .stat-card {
      background: #161b22;
      border: 1px solid rgba(255,255,255,0.06);
      border-radius: 8px;
      padding: 20px;
      transition: all 0.3s ease;
    }
    .stat-card:hover {
      border-color: rgba(129,140,248,0.3);
      box-shadow: 0 0 30px -8px rgba(129,140,248,0.15);
    }

    /* Skill badge */
    .skill-badge {
      background: #161b22;
      border: 1px solid rgba(255,255,255,0.06);
      border-radius: 8px;
      padding: 10px 14px;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: all 0.3s ease;
      font-size: 13px;
      color: #c9d1d9;
    }
    .skill-badge:hover {
      border-color: rgba(129,140,248,0.4);
      transform: translateY(-2px);
      box-shadow: 0 8px 24px -4px rgba(0,0,0,0.4);
    }
    .skill-badge img, .skill-badge i {
      width: 20px; height: 20px;
    }

    /* Code block */
    .code-block {
      background: #0d1117;
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 8px;
      overflow: hidden;
      font-family: 'JetBrains Mono', monospace;
      font-size: 13px;
      line-height: 1.7;
    }
    .code-block .code-header {
      background: #161b22;
      padding: 8px 16px;
      font-size: 12px;
      color: #8b949e;
      border-bottom: 1px solid rgba(255,255,255,0.06);
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .code-block pre {
      padding: 16px 20px;
      color: #c9d1d9;
      overflow-x: auto;
    }
    .code-keyword { color: #ff7b72; }
    .code-type { color: #79c0ff; }
    .code-string { color: #a5d6ff; }
    .code-comment { color: #8b949e; font-style: italic; }
    .code-func { color: #d2a8ff; }
    .code-include { color: #ffa657; }

    /* Social badge */
    .social-badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 12px;
      font-weight: 500;
      transition: all 0.3s ease;
      border: 1px solid rgba(255,255,255,0.08);
    }
    .social-badge:hover {
      transform: translateY(-1px);
      box-shadow: 0 4px 16px -4px rgba(0,0,0,0.5);
    }

    /* Section title */
    .section-title {
      font-size: 16px;
      font-weight: 600;
      color: #e5e5e5;
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 16px;
    }
    .section-title::after {
      content: '';
      flex: 1;
      height: 1px;
      background: linear-gradient(to right, rgba(129,140,248,0.3), transparent);
    }

    /* Source code container */
    .source-container {
      background: #0a0a0a;
      border: 1px solid rgba(255,255,255,0.06);
      border-radius: 12px;
      overflow: hidden;
    }
    .source-container .source-header {
      background: #111;
      border-bottom: 1px solid rgba(255,255,255,0.06);
      padding: 12px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .source-container pre {
      padding: 20px 24px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 12px;
      line-height: 1.8;
      color: #a3a3a3;
      overflow-x: auto;
      max-height: 500px;
      overflow-y: auto;
    }

    /* Copy button */
    .copy-btn {
      background: rgba(129,140,248,0.15);
      color: #818cf8;
      border: 1px solid rgba(129,140,248,0.3);
      padding: 6px 16px;
      border-radius: 6px;
      font-size: 12px;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      gap: 6px;
      font-family: 'Inter', sans-serif;
    }
    .copy-btn:hover {
      background: rgba(129,140,248,0.25);
      box-shadow: 0 0 20px -4px rgba(129,140,248,0.3);
    }
    .copy-btn.copied {
      background: rgba(34,197,94,0.15);
      color: #22c55e;
      border-color: rgba(34,197,94,0.3);
    }

    /* Wallpaper preview */
    .wallpaper-container {
      border-radius: 12px;
      overflow: hidden;
      border: 1px solid rgba(255,255,255,0.06);
      position: relative;
    }
    .wallpaper-container img {
      width: 100%;
      display: block;
      opacity: 0.85;
      transition: opacity 0.5s ease;
    }
    .wallpaper-container:hover img {
      opacity: 1;
    }
    .wallpaper-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      padding: 24px;
      background: linear-gradient(to top, rgba(0,0,0,0.7), transparent);
    }

    /* Grid pattern */
    .grid-pattern {
      background-image:
        linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
      background-size: 40px 40px;
    }

    /* Tab system */
    .tab-btn {
      padding: 8px 20px;
      border-radius: 6px;
      font-size: 13px;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.3s ease;
      border: 1px solid transparent;
      background: transparent;
      color: #737373;
      font-family: 'Inter', sans-serif;
    }
    .tab-btn.active {
      background: rgba(129,140,248,0.1);
      color: #818cf8;
      border-color: rgba(129,140,248,0.2);
    }
    .tab-btn:hover:not(.active) {
      color: #a3a3a3;
    }

    /* Toast notification */
    .toast {
      position: fixed;
      bottom: 32px;
      right: 32px;
      background: #161b22;
      border: 1px solid rgba(34,197,94,0.3);
      color: #22c55e;
      padding: 12px 20px;
      border-radius: 8px;
      font-size: 13px;
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 8px;
      transform: translateY(100px);
      opacity: 0;
      transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
      z-index: 100;
      box-shadow: 0 8px 32px -8px rgba(0,0,0,0.5);
    }
    .toast.show {
      transform: translateY(0);
      opacity: 1;
    }

    /* Streak fire */
    .streak-bar {
      height: 6px;
      border-radius: 3px;
      background: linear-gradient(to right, #ff6b6b, #ffa657, #e3b341, #3fb950);
    }

    /* Contribution grid */
    .contrib-cell {
      width: 10px; height: 10px;
      border-radius: 2px;
      transition: all 0.2s ease;
    }
    .contrib-cell:hover {
      transform: scale(1.5);
      outline: 1px solid rgba(129,140,248,0.5);
    }
  </style>
</head>
<body class="grid-pattern min-h-screen">

  <!-- Glow Orbs -->
  <div class="glow-orb" style="width:600px;height:600px;background:#6366f1;top:-200px;right:-200px;"></div>
  <div class="glow-orb" style="width:500px;height:500px;background:#a855f7;bottom:-200px;left:-200px;animation-delay:3s;"></div>

  <!-- Toast -->
  <div id="toast" class="toast">
    <i class="fas fa-check-circle"></i>
    <span>README 源码已复制到剪贴板</span>
  </div>

  <!-- Navigation -->
  <nav class="fixed top-0 left-0 right-0 z-50 backdrop-blur-md bg-black/60 border-b border-white/5">
    <div class="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
      <div class="flex items-center gap-3">
        <div class="w-8 h-8 rounded-lg bg-gradient-to-br from-indigo-500 to-purple-600 flex items-center justify-center text-white text-xs font-bold">T</div>
        <span class="font-medium text-sm text-neutral-300">TS137 / README.md</span>
      </div>
      <div class="flex items-center gap-2">
        <button id="tab-preview" class="tab-btn active" onclick="switchTab('preview')">
          <i class="fas fa-eye mr-1.5 text-xs"></i>预览
        </button>
        <button id="tab-source" class="tab-btn" onclick="switchTab('source')">
          <i class="fas fa-code mr-1.5 text-xs"></i>源码
        </button>
      </div>
    </div>
  </nav>

  <!-- Main Content -->
  <main class="max-w-5xl mx-auto px-6 pt-28 pb-24">

    <!-- Preview Section -->
    <div id="preview-section">

      <!-- Intro -->
      <div class="text-center mb-12 animate-in delay-1">
        <p class="text-xs font-medium tracking-widest text-indigo-400 uppercase mb-3">GitHub Profile README</p>
        <h1 class="text-3xl md:text-4xl font-semibold tracking-tight mb-4" style="background:linear-gradient(to bottom,#fff,rgba(255,255,255,0.9),rgba(255,255,255,0.5));-webkit-background-clip:text;-webkit-text-fill-color:transparent;">
          优化你的 GitHub 主页
        </h1>
        <p class="text-neutral-400 text-sm max-w-md mx-auto leading-relaxed">
          以下是你美化后的 README 预览效果，点击上方「源码」标签可复制完整 Markdown
        </p>
      </div>

      <!-- GitHub README Preview -->
      <div class="readme-preview animate-in delay-2 mb-8">
        <div class="header-bar">
          <div class="dot" style="background:#ff5f57;"></div>
          <div class="dot" style="background:#febc2e;"></div>
          <div class="dot" style="background:#28c840;"></div>
          <span class="text-xs text-neutral-500 ml-2 font-mono">README.md</span>
        </div>
        <div class="content">

          <!-- Banner SVG placeholder -->
          <div class="animate-in delay-2 mb-6 rounded-xl overflow-hidden" style="background:linear-gradient(135deg,#0d1117 0%,#161b22 30%,#1a1a3e 60%,#0d1117 100%);border:1px solid rgba(255,255,255,0.06);height:160px;position:relative;display:flex;align-items:center;justify-content:center;">
            <div style="position:absolute;inset:0;background:radial-gradient(circle at 30% 50%,rgba(99,102,241,0.15),transparent 50%),radial-gradient(circle at 70% 50%,rgba(168,85,247,0.1),transparent 50%);"></div>
            <div style="position:relative;text-align:center;">
              <div style="font-family:'Segoe Script',cursive;font-size:32px;color:#e5e5e5;font-weight:600;">TS137</div>
              <div style="font-size:11px;color:#737373;margin-top:4px;letter-spacing:2px;">MODERN C++ DEVELOPER</div>
            </div>
            <!-- Floating dots -->
            <div style="position:absolute;top:20%;left:15%;width:4px;height:4px;border-radius:50%;background:rgba(129,140,248,0.4);animation:float 3s ease-in-out infinite;"></div>
            <div style="position:absolute;top:60%;left:80%;width:3px;height:3px;border-radius:50%;background:rgba(168,85,247,0.4);animation:float 4s ease-in-out infinite 1s;"></div>
            <div style="position:absolute;top:30%;left:70%;width:5px;height:5px;border-radius:50%;background:rgba(99,102,241,0.3);animation:float 3.5s ease-in-out infinite 0.5s;"></div>
            <div style="position:absolute;top:70%;left:25%;width:3px;height:3px;border-radius:50%;background:rgba(34,211,238,0.3);animation:float 4.5s ease-in-out infinite 1.5s;"></div>
          </div>

          <!-- Typing Effect -->
          <div class="text-center mb-6" style="min-height:32px;">
            <span class="typing-text" style="color:#818cf8;font-family:'JetBrains Mono',monospace;font-size:18px;font-weight:600;">Hi 👋 I'm TS137</span>
            <span class="typing-text typing-text-2" style="color:#c9d1d9;font-family:'JetBrains Mono',monospace;font-size:18px;"> | Modern C++ Developer</span>
          </div>

          <!-- Social Badges -->
          <div class="flex flex-wrap items-center justify-center gap-2 mb-8">
            <a href="#" class="social-badge" style="background:rgba(0,161,214,0.1);color:#00A1D6;border-color:rgba(0,161,214,0.2);">
              <i class="fas fa-tv text-xs"></i> Bilibili
            </a>
            <a href="#" class="social-badge" style="background:rgba(129,140,248,0.1);color:#818cf8;border-color:rgba(129,140,248,0.2);">
              <i class="fab fa-github text-xs"></i> GitHub
            </a>
            <a href="#" class="social-badge" style="background:rgba(212,72,54,0.1);color:#D44836;border-color:rgba(212,72,54,0.2);">
              <i class="fas fa-envelope text-xs"></i> Email
            </a>
          </div>

          <!-- Stats Row -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
            <div class="stat-card">
              <div class="flex items-center gap-3 mb-4">
                <i class="fas fa-chart-bar text-indigo-400 text-sm"></i>
                <span class="text-xs font-medium text-neutral-400 uppercase tracking-wider">GitHub Stats</span>
              </div>
              <div class="space-y-3">
                <div class="flex justify-between items-center">
                  <span class="text-sm text-neutral-400">Total Stars</span>
                  <span class="text-sm font-semibold text-indigo-400 font-mono">128</span>
                </div>
                <div class="flex justify-between items-center">
                  <span class="text-sm text-neutral-400">Total Commits</span>
                  <span class="text-sm font-semibold text-purple-400 font-mono">1,024</span>
                </div>
                <div class="flex justify-between items-center">
                  <span class="text-sm text-neutral-400">Total PRs</span>
                  <span class="text-sm font-semibold text-cyan-400 font-mono">86</span>
                </div>
                <div class="flex justify-between items-center">
                  <span class="text-sm text-neutral-400">Total Issues</span>
                  <span class="text-sm font-semibold text-green-400 font-mono">42</span>
                </div>
                <div class="flex justify-between items-center">
                  <span class="text-sm text-neutral-400">Contributed to</span>
                  <span class="text-sm font-semibold text-yellow-400 font-mono">12 repos</span>
                </div>
              </div>
            </div>
            <div class="stat-card">
              <div class="flex items-center gap-3 mb-4">
                <i class="fas fa-language text-purple-400 text-sm"></i>
                <span class="text-xs font-medium text-neutral-400 uppercase tracking-wider">Top Languages</span>
              </div>
              <div class="space-y-3">
                <div>
                  <div class="flex justify-between mb-1">
                    <span class="text-sm text-neutral-300">C++</span>
                    <span class="text-xs text-neutral-500 font-mono">68.2%</span>
                  </div>
                  <div class="h-1.5 bg-white/5 rounded-full overflow-hidden">
                    <div class="h-full rounded-full" style="width:68.2%;background:linear-gradient(to right,#6366f1,#818cf8);"></div>
                  </div>
                </div>
                <div>
                  <div class="flex justify-between mb-1">
                    <span class="text-sm text-neutral-300">C</span>
                    <span class="text-xs text-neutral-500 font-mono">15.8%</span>
                  </div>
                  <div class="h-1.5 bg-white/5 rounded-full overflow-hidden">
                    <div class="h-full rounded-full" style="width:15.8%;background:linear-gradient(to right,#a855f7,#c084fc);"></div>
                  </div>
                </div>
                <div>
                  <div class="flex justify-between mb-1">
                    <span class="text-sm text-neutral-300">Python</span>
                    <span class="text-xs text-neutral-500 font-mono">9.4%</span>
                  </div>
                  <div class="h-1.5 bg-white/5 rounded-full overflow-hidden">
                    <div class="h-full rounded-full" style="width:9.4%;background:linear-gradient(to right,#22d3ee,#67e8f9);"></div>
                  </div>
                </div>
                <div>
                  <div class="flex justify-between mb-1">
                    <span class="text-sm text-neutral-300">CMake</span>
                    <span class="text-xs text-neutral-500 font-mono">4.2%</span>
                  </div>
                  <div class="h-1.5 bg-white/5 rounded-full overflow-hidden">
                    <div class="h-full rounded-full" style="width:4.2%;background:linear-gradient(to right,#f59e0b,#fbbf24);"></div>
                  </div>
                </div>
                <div>
                  <div class="flex justify-between mb-1">
                    <span class="text-sm text-neutral-300">Shell</span>
                    <span class="text-xs text-neutral-500 font-mono">2.4%</span>
                  </div>
                  <div class="h-1.5 bg-white/5 rounded-full overflow-hidden">
                    <div class="h-full rounded-full" style="width:2.4%;background:linear-gradient(to right,#22c55e,#4ade80);"></div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- Streak Stats -->
          <div class="stat-card mb-6">
            <div class="flex items-center justify-between mb-4">
              <div class="flex items-center gap-3">
                <i class="fas fa-fire text-orange-400 text-sm"></i>
                <span class="text-xs font-medium text-neutral-400 uppercase tracking-wider">Contribution Streak</span>
              </div>
              <div class="flex items-center gap-1.5">
                <span class="text-2xl font-bold text-orange-400 font-mono">47</span>
                <span class="text-xs text-neutral-500">days</span>
              </div>
            </div>
            <div class="streak-bar mb-3" style="width:85%;"></div>
            <div class="flex justify-between text-xs text-neutral-500">
              <span>Longest: 92 days</span>
              <span>Current: 47 days</span>
              <span>This year: 1,024 contributions</span>
            </div>
            <!-- Mini contribution grid -->
            <div class="mt-4 flex flex-wrap gap-[3px]" id="contrib-grid"></div>
          </div>

          <!-- Tech Stack -->
          <div class="mb-6">
            <div class="section-title">
              <i class="fas fa-wrench text-indigo-400 text-sm"></i> Tech Stack
            </div>
            <div class="flex flex-wrap gap-2">
              <div class="skill-badge"><i class="fab fa-cuttlefish" style="color:#00599C;"></i> C++</div>
              <div class="skill-badge"><i class="fas fa-copyright" style="color:#A8B9CC;"></i> C</div>
              <div class="skill-badge"><i class="fas fa-cogs" style="color:#064F8C;"></i> CMake</div>
              <div class="skill-badge"><i class="fab fa-python" style="color:#3776AB;"></i> Python</div>
              <div class="skill-badge"><i class="fab fa-linux" style="color:#FCC624;"></i> Linux</div>
              <div class="skill-badge"><i class="fab fa-git-alt" style="color:#F05032;"></i> Git</div>
              <div class="skill-badge"><i class="fab fa-github" style="color:#e5e5e5;"></i> GitHub</div>
              <div class="skill-badge"><i class="fas fa-code" style="color:#007ACC;"></i> VS Code</div>
              <div class="skill-badge"><i class="fas fa-terminal" style="color:#4EAA25;"></i> CLion</div>
              <div class="skill-badge"><i class="fas fa-cube" style="color:#8DD8F8;"></i> Visual Studio</div>
              <div class="skill-badge"><i class="fas fa-microchip" style="color:#a3a3a3;"></i> GDB</div>
              <div class="skill-badge"><i class="fas fa-docker" style="color:#2496ED;"></i> Docker</div>
            </div>
          </div>

          <!-- About Me (Code Style) -->
          <div class="mb-6">
            <div class="section-title">
              <i class="fas fa-user text-purple-400 text-sm"></i> About Me
            </div>
            <div class="code-block">
              <div class="code-header">
                <i class="fas fa-file-code text-xs"></i>
                <span>about.cpp</span>
              </div>
              <pre><span class="code-comment">// 👋 Welcome to my profile!</span>
<span class="code-keyword">class</span> <span class="code-type">TS137</span> {
<span class="code-keyword">private</span>:
    std::string focus    = <span class="code-string">"Modern C++ Development"</span>;
    std::string learning = <span class="code-string">"System Programming & Architecture"</span>;
    std::string hobby    = <span class="code-string">"Open Source Contribution"</span>;

<span class="code-keyword">public</span>:
    <span class="code-type">void</span> <span class="code-func">say_hi</span>() <span class="code-keyword">const</span> {
        std::cout &lt;&lt; <span class="code-string">"Thanks for visiting! ✨"</span> &lt;&lt; std::endl;
    }

    <span class="code-type">bool</span> <span class="code-func">is_coffee_ready</span>() {
        <span class="code-keyword">return</span> <span class="code-keyword">true</span>; <span class="code-comment">// Always :)</span>
    }
};</pre>
            </div>
          </div>

          <!-- Currently -->
          <div class="mb-6">
            <div class="section-title">
              <i class="fas fa-bolt text-yellow-400 text-sm"></i> Currently
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
              <div class="flex items-start gap-3 p-3 rounded-lg" style="background:rgba(99,102,241,0.05);border:1px solid rgba(99,102,241,0.1);">
                <span class="text-lg mt-0.5">🔍</span>
                <div>
                  <p class="text-sm text-neutral-200">Working on</p>
                  <p class="text-xs text-neutral-400 mt-0.5">高性能 C++ 框架 & 系统级工具</p>
                </div>
              </div>
              <div class="flex items-start gap-3 p-3 rounded-lg" style="background:rgba(168,85,247,0.05);border:1px solid rgba(168,85,247,0.1);">
                <span class="text-lg mt-0.5">🌱</span>
                <div>
                  <p class="text-sm text-neutral-200">Learning</p>
                  <p class="text-xs text-neutral-400 mt-0.5">C++23/26 新特性 & 模板元编程</p>
                </div>
              </div>
              <div class="flex items-start gap-3 p-3 rounded-lg" style="background:rgba(34,211,238,0.05);border:1px solid rgba(34,211,238,0.1);">
                <span class="text-lg mt-0.5">🤝</span>
                <div>
                  <p class="text-sm text-neutral-200">Collaborating on</p>
                  <p class="text-xs text-neutral-400 mt-0.5">开源项目 & 技术社区</p>
                </div>
              </div>
              <div class="flex items-start gap-3 p-3 rounded-lg" style="background:rgba(34,197,94,0.05);border:1px solid rgba(34,197,94,0.1);">
                <span class="text-lg mt-0.5">💬</span>
                <div>
                  <p class="text-sm text-neutral-200">Ask me about</p>
                  <p class="text-xs text-neutral-400 mt-0.5">C++、系统编程、性能优化</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Wallpaper -->
          <div class="mb-6">
            <div class="section-title">
              <i class="fas fa-image text-cyan-400 text-sm"></i> Wallpaper
            </div>
            <div class="wallpaper-container">
              <img src="https://picsum.photos/seed/ts137-wallpaper/900/400.jpg" alt="壁纸" style="aspect-ratio:16/7;object-fit:cover;">
              <div class="wallpaper-overlay">
                <p class="text-xs text-neutral-400">「代码是写给人看的，附带能在机器上运行」</p>
              </div>
            </div>
          </div>

          <!-- Footer -->
          <div class="text-center pt-4 border-t border-white/5">
            <p class="text-xs text-neutral-600">
              Built with <span style="color:#ff6b6b;">♥</span> by TS137 · Powered by GitHub
            </p>
          </div>

        </div>
      </div>

    </div>

    <!-- Source Section -->
    <div id="source-section" style="display:none;">
      <div class="text-center mb-8">
        <p class="text-xs font-medium tracking-widest text-indigo-400 uppercase mb-3">Markdown Source</p>
        <h2 class="text-2xl font-semibold tracking-tight text-neutral-200 mb-2">README.md 源码</h2>
        <p class="text-neutral-500 text-sm">复制以下内容粘贴到你的 GitHub README 文件中</p>
      </div>

      <div class="source-container">
        <div class="source-header">
          <div class="flex items-center gap-2">
            <i class="fab fa-markdown text-neutral-500"></i>
            <span class="text-xs text-neutral-400 font-mono">README.md</span>
          </div>
          <button class="copy-btn" id="copyBtn" onclick="copySource()">
            <i class="fas fa-copy text-xs"></i>
            <span>复制源码</span>
          </button>
        </div>
        <pre id="sourceCode"></pre>
      </div>

      <!-- Tips -->
      <div class="mt-6 p-4 rounded-lg" style="background:rgba(129,140,248,0.05);border:1px solid rgba(129,140,248,0.1);">
        <p class="text-xs font-medium text-indigo-400 mb-2"><i class="fas fa-lightbulb mr-1.5"></i>使用提示</p>
        <ul class="text-xs text-neutral-400 space-y-1.5">
          <li>• 将 <code class="px-1 py-0.5 rounded bg-white/5 text-neutral-300 font-mono">dark_mode.svg</code> 和 <code class="px-1 py-0.5 rounded bg-white/5 text-neutral-300 font-mono">light_mode.svg</code> 上传到仓库根目录</li>
          <li>• 将壁纸图片 <code class="px-1 py-0.5 rounded bg-white/5 text-neutral-300 font-mono">1.png</code> 上传到仓库根目录</li>
          <li>• 修改社交链接中的占位符为你真实的链接地址</li>
          <li>• Stats 卡片数据会自动从你的 GitHub 账号实时获取</li>
          <li>• C++ 代码片段中的内容可自由修改为你想展示的信息</li>
          <li>• <code class="px-1 py-0.5 rounded bg-white/5 text-neutral-300 font-mono">skillicons.dev</code> 支持更换图标，参考 <a href="https://skillicons.dev" target="_blank" class="text-indigo-400 hover:underline">skillicons.dev</a></li>
        </ul>
      </div>
    </div>

  </main>

  <script>
    // Markdown source
    const readmeSource = `<div align="center">

<!-- Banner (Dark/Light Mode) -->
<a href="https://github.com/TS137">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/TS137/TS137/main/dark_mode.svg">
    <img alt="TS137" src="https://raw.githubusercontent.com/TS137/TS137/main/light_mode.svg" width="100%">
  </picture>
</a>

<!-- Typing Animation -->
<a href="https://github.com/TS137">
  <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=600&size=22&center=true&vCenter=true&lines=Hi+%F0%9F%91%8B+I'm+TS137;Modern+C%2B%2B+Developer;Building+Something+Amazing..." alt="Typing SVG">
</a>

<br><br>

<!-- Social Badges -->
<a href="https://b23.tv/iEJTnPp">
  <img src="https://img.shields.io/badge/Bilibili-主页-00A1D6?style=for-the-badge&logo=bilibili&logoColor=white" alt="Bilibili">
</a>
&nbsp;
<a href="https://github.com/TS137">
  <img src="https://img.shields.io/badge/GitHub-TS137-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
</a>
&nbsp;
<a href="mailto:your-email@example.com">
  <img src="https://img.shields.io/badge/Email-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
</a>

</div>

<br>

<!-- Stats Cards -->
<div align="center">
  <a href="https://github.com/anuraghazra/github-readme-stats">
    <img width="49%" src="https://github-readme-stats.vercel.app/api?username=TS137&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=C9D1D9&icon_color=79C0FF&text_color=C9D1D9" alt="GitHub Stats">
  </a>
  <a href="https://github.com/anuraghazra/github-readme-stats">
    <img width="49%" src="https://github-readme-stats.vercel.app/api/top-langs/?username=TS137&layout=compact&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=C9D1D9&text_color=C9D1D9&langs_count=8" alt="Top Languages">
  </a>
</div>

<br>

<!-- Streak Stats -->
<div align="center">
  <a href="https://github.com/DenverCoder1/github-readme-streak-stats">
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=TS137&theme=tokyonight&hide_border=true&background=0D1117&stroke=30363D&ring=79C0FF&fire=FF6B6B&currStreakLabel=79C0FF" alt="GitHub Streak">
  </a>
</div>

<br>

<!-- Tech Stack -->
<div align="center">

### 🛠 Tech Stack

<img src="https://skillicons.dev/icons?i=cpp,c,cmake,python,linux,git,github,vscode,clion,visualstudio,docker&theme=dark" alt="Tech Stack">

</div>

<br>

<!-- About Me -->
<div align="center">

### 👤 About Me

\`\`\`cpp
// 👋 Welcome to my profile!
class TS137 {
private:
    std::string focus    = "Modern C++ Development";
    std::string learning = "System Programming & Architecture";
    std::string hobby    = "Open Source Contribution";

public:
    void say_hi() const {
        std::cout << "Thanks for visiting! ✨" << std::endl;
    }

    bool is_coffee_ready() {
        return true; // Always :)
    }
};
\`\`\`

</div>

<br>

<!-- Currently -->
<div align="center">

### ⚡ Currently

- 🔭 Working on 高性能 C++ 框架 & 系统级工具
- 🌱 Learning C++23/26 新特性 & 模板元编程
- 🤝 Collaborating on 开源项目 & 技术社区
- 💬 Ask me about C++、系统编程、性能优化

</div>

<br>

<!-- Wallpaper -->
<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/TS137/TS137/main/1.png">
    <img src="https://raw.githubusercontent.com/TS137/TS137/main/1.png" alt="壁纸" width="80%">
  </picture>
</div>

<br>

<div align="center">

Built with ♥ by TS137 · Powered by GitHub

</div>`;

    // Insert source code
    document.getElementById('sourceCode').textContent = readmeSource;

    // Tab switching
    function switchTab(tab) {
      const previewSection = document.getElementById('preview-section');
      const sourceSection = document.getElementById('source-section');
      const tabPreview = document.getElementById('tab-preview');
      const tabSource = document.getElementById('tab-source');

      if (tab === 'preview') {
        previewSection.style.display = 'block';
        sourceSection.style.display = 'none';
        tabPreview.classList.add('active');
        tabSource.classList.remove('active');
      } else {
        previewSection.style.display = 'none';
        sourceSection.style.display = 'block';
        tabSource.classList.add('active');
        tabPreview.classList.remove('active');
      }
    }

    // Copy source
    function copySource() {
      const btn = document.getElementById('copyBtn');
      const toast = document.getElementById('toast');

      navigator.clipboard.writeText(readmeSource).then(() => {
        btn.classList.add('copied');
        btn.innerHTML = '<i class="fas fa-check text-xs"></i><span>已复制</span>';
        toast.classList.add('show');

        setTimeout(() => {
          btn.classList.remove('copied');
          btn.innerHTML = '<i class="fas fa-copy text-xs"></i><span>复制源码</span>';
          toast.classList.remove('show');
        }, 2500);
      }).catch(() => {
        // Fallback
        const textarea = document.createElement('textarea');
        textarea.value = readmeSource;
        document.body.appendChild(textarea);
        textarea.select();
        document.execCommand('copy');
        document.body.removeChild(textarea);

        btn.classList.add('copied');
        btn.innerHTML = '<i class="fas fa-check text-xs"></i><span>已复制</span>';
        toast.classList.add('show');

        setTimeout(() => {
          btn.classList.remove('copied');
          btn.innerHTML = '<i class="fas fa-copy text-xs"></i><span>复制源码</span>';
          toast.classList.remove('show');
        }, 2500);
      });
    }

    // Generate contribution grid
    function generateContribGrid() {
      const grid = document.getElementById('contrib-grid');
      const colors = [
        'rgba(255,255,255,0.03)',
        'rgba(99,102,241,0.15)',
        'rgba(99,102,241,0.3)',
        'rgba(99,102,241,0.5)',
        'rgba(99,102,241,0.8)',
      ];
      const weights = [0.35, 0.25, 0.2, 0.12, 0.08]; // distribution

      for (let i = 0; i < 365; i++) {
        const cell = document.createElement('div');
        cell.className = 'contrib-cell';
        const rand = Math.random();
        let cumulative = 0;
        let colorIdx = 0;
        for (let j = 0; j < weights.length; j++) {
          cumulative += weights[j];
          if (rand <= cumulative) { colorIdx = j; break; }
        }
        // Make recent days more active
        if (i > 300) colorIdx = Math.min(colorIdx + 1, colors.length - 1);
        cell.style.backgroundColor = colors[colorIdx];
        grid.appendChild(cell);
      }
    }
    generateContribGrid();
  </script>

</body>
</html>
