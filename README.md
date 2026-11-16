<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Muhammad Nazwar — Beyond the Code, Into the Universe</title>

  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Google Fonts: Space Grotesk, Inter, and JetBrains Mono -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;600&family=Space+Grotesk:wght@500;600;700&display=swap" rel="stylesheet" />

  <!-- Font Awesome for crisp cosmic & tech icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />

  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            cosmos: {
              950: '#040611',
              900: '#070b1e',
              800: '#0d1433',
              700: '#16204d',
            },
            nebula: {
              cyan: '#38bdf8',
              violet: '#a855f7',
              indigo: '#6366f1',
              emerald: '#34d399',
            }
          },
          fontFamily: {
            display: ['"Space Grotesk"', 'sans-serif'],
            sans: ['"Inter"', 'sans-serif'],
            mono: ['"JetBrains Mono"', 'monospace'],
          },
          animation: {
            'spin-slow': 'spin 28s linear infinite',
            'spin-reverse-slow': 'spinReverse 36s linear infinite',
            'float': 'float 6s ease-in-out infinite',
            'pulse-glow': 'pulseGlow 4s ease-in-out infinite',
          },
          keyframes: {
            spinReverse: {
              '0%': { transform: 'rotate(360deg)' },
              '100%': { transform: 'rotate(0deg)' },
            },
            float: {
              '0%, 100%': { transform: 'translateY(0px)' },
              '50%': { transform: 'translateY(-12px)' },
            },
            pulseGlow: {
              '0%, 100%': { opacity: '0.45', transform: 'scale(1)' },
              '50%': { opacity: '0.8', transform: 'scale(1.06)' },
            }
          }
        }
      }
    };
  </script>

  <style>
    /* Deep Space Base & Scrollbar */
    body {
      background-color: #040611;
      color: #e2e8f0;
      overflow-x: hidden;
    }

    ::-webkit-scrollbar {
      width: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #040611;
    }
    ::-webkit-scrollbar-thumb {
      background: linear-gradient(180deg, #38bdf8, #a855f7);
      border-radius: 9999px;
    }

    /* Glassmorphism Space Cards */
    .space-card {
      background: linear-gradient(145deg, rgba(15, 23, 42, 0.72), rgba(7, 11, 30, 0.85));
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1px solid rgba(148, 163, 184, 0.14);
      box-shadow: 0 12px 40px -12px rgba(0, 0, 0, 0.65);
      transition: transform 0.35s cubic-bezier(0.22, 1, 0.36, 1), border-color 0.35s ease, box-shadow 0.35s ease;
    }

    .space-card:hover {
      border-color: rgba(56, 189, 248, 0.42);
      box-shadow: 0 20px 50px -12px rgba(56, 189, 248, 0.16), 0 0 24px rgba(168, 85, 247, 0.12);
      transform: translateY(-4px);
    }

    /* Subtle Cosmic Grid Overlay */
    .cosmic-grid {
      background-size: 48px 48px;
      background-image: 
        linear-gradient(to right, rgba(56, 189, 248, 0.04) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(168, 85, 247, 0.04) 1px, transparent 1px);
    }

    /* Text Gradient */
    .text-cosmic-gradient {
      background: linear-gradient(135deg, #f8fafc 0%, #38bdf8 48%, #c084fc 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    /* Scroll Reveal Animation */
    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.75s cubic-bezier(0.16, 1, 0.3, 1), transform 0.75s cubic-bezier(0.16, 1, 0.3, 1);
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* Glowing Orbit Ring */
    .orbit-ring {
      border: 1px dashed rgba(56, 189, 248, 0.28);
      border-radius: 9999px;
    }
  </style>
</head>
<body class="font-sans antialiased selection:bg-sky-400/30 selection:text-sky-200 relative">

  <!-- Interactive Animated Starfield & Shooting Stars Canvas -->
  <canvas id="starfield-canvas" class="fixed inset-0 w-full h-full pointer-events-none z-0"></canvas>

  <!-- Ambient Nebula Glow Blobs -->
  <div class="fixed inset-0 pointer-events-none z-0 overflow-hidden">
    <div class="absolute -top-40 -left-32 w-[28rem] h-[28rem] sm:w-[38rem] sm:h-[38rem] rounded-full bg-sky-500/10 blur-[130px] animate-pulse-glow"></div>
    <div class="absolute top-1/3 -right-40 w-[26rem] h-[26rem] sm:w-[36rem] sm:h-[36rem] rounded-full bg-purple-600/12 blur-[140px] animate-pulse-glow" style="animation-delay: 2s;"></div>
    <div class="absolute -bottom-48 left-1/4 w-[30rem] h-[30rem] rounded-full bg-indigo-600/10 blur-[140px]"></div>
    <div class="absolute inset-0 cosmic-grid"></div>
  </div>

  <!-- Top Navigation Bar -->
  <header class="sticky top-0 z-50 backdrop-blur-xl bg-[#040611]/75 border-b border-slate-800/70">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
      <!-- Brand / Callsign -->
      <a href="#hero" class="flex items-center gap-2.5 group">
        <span class="w-9 h-9 rounded-xl bg-gradient-to-br from-sky-400/20 to-purple-500/20 border border-sky-400/40 flex items-center justify-center text-sky-300 shadow-[0_0_15px_rgba(56,189,248,0.25)] group-hover:scale-105 transition-transform">
          <i class="fa-solid fa-meteor text-sm"></i>
        </span>
        <div>
          <span class="font-display font-bold text-slate-100 tracking-wide text-base sm:text-lg">NAZWAR<span class="text-sky-400">.DEV</span></span>
        </div>
      </a>

      <!-- Desktop Navigation -->
      <nav class="hidden md:flex items-center gap-1 lg:gap-2 text-sm font-medium text-slate-300">
        <a href="#about" class="px-3.5 py-2 rounded-xl hover:text-sky-300 hover:bg-slate-800/50 transition-colors">About</a>
        <a href="#tech" class="px-3.5 py-2 rounded-xl hover:text-sky-300 hover:bg-slate-800/50 transition-colors">Tech Universe</a>
        <a href="#missions" class="px-3.5 py-2 rounded-xl hover:text-sky-300 hover:bg-slate-800/50 transition-colors">Missions</a>
        <a href="#exploration" class="px-3.5 py-2 rounded-xl hover:text-sky-300 hover:bg-slate-800/50 transition-colors">Exploration</a>
        <a href="#contact" class="ml-2 px-4 py-2 rounded-xl bg-gradient-to-r from-sky-500/20 to-purple-500/20 border border-sky-400/40 text-sky-200 hover:border-sky-300 hover:shadow-[0_0_20px_rgba(56,189,248,0.3)] transition-all">
          Contact Station
        </a>
      </nav>

      <!-- Mobile Menu Button -->
      <button id="mobile-menu-btn" aria-label="Toggle Menu" class="md:hidden p-2.5 rounded-xl bg-slate-900/80 border border-slate-700/70 text-slate-200 hover:text-sky-300">
        <i class="fa-solid fa-bars text-lg"></i>
      </button>
    </div>

    <!-- Mobile Navigation Dropdown -->
    <div id="mobile-menu" class="hidden md:hidden border-t border-slate-800/80 bg-[#050816]/95 backdrop-blur-xl px-4 py-4 space-y-1.5">
      <a href="#about" class="mobile-link block px-4 py-2.5 rounded-xl text-slate-200 hover:bg-slate-800/60 hover:text-sky-300">🪐 About Me</a>
      <a href="#tech" class="mobile-link block px-4 py-2.5 rounded-xl text-slate-200 hover:bg-slate-800/60 hover:text-sky-300">🚀 Technology Universe</a>
      <a href="#missions" class="mobile-link block px-4 py-2.5 rounded-xl text-slate-200 hover:bg-slate-800/60 hover:text-sky-300">🛰️ Mission Archive</a>
      <a href="#exploration" class="mobile-link block px-4 py-2.5 rounded-xl text-slate-200 hover:bg-slate-800/60 hover:text-sky-300">🔭 Academic & Education</a>
      <a href="#contact" class="mobile-link block px-4 py-2.5 rounded-xl text-sky-300 font-medium bg-sky-500/10 border border-sky-400/30">📡 Contact Station</a>
    </div>
  </header>

  <!-- Main Content Container -->
  <main class="relative z-10 max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">

    <!-- 1. HERO SECTION -->
    <section id="hero" class="min-h-[88vh] py-14 sm:py-20 flex flex-col lg:flex-row items-center justify-between gap-12">
      <!-- Left Hero Copy -->
      <div class="w-full lg:w-3/5 text-center lg:text-left space-y-6">
        <!-- Status Telemetry Pill -->
        <div class="inline-flex items-center gap-2.5 px-4 py-1.5 rounded-full bg-slate-900/80 border border-sky-400/30 text-xs sm:text-sm font-mono text-sky-300 shadow-[0_0_20px_rgba(56,189,248,0.15)]">
          <span class="relative flex h-2.5 w-2.5">
            <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
            <span class="relative inline-flex rounded-full h-2.5 w-2.5 bg-emerald-400"></span>
          </span>
          <span>BANDUNG SECTOR · SEMESTER 5</span>
        </div>

        <!-- Name & Title -->
        <div class="space-y-3">
          <h1 class="font-display text-4xl sm:text-5xl lg:text-6xl font-bold tracking-tight leading-tight">
            <span class="text-slate-100 block text-lg sm:text-xl font-mono font-normal text-sky-300/90 mb-2">🌌 COMMANDER PROFILE</span>
            <span class="text-cosmic-gradient">Muhammad Nazwar</span>
          </h1>

          <p class="font-mono text-xs sm:text-sm md:text-base tracking-widest uppercase text-purple-300/95 font-medium pt-1">
            ✦ INFORMATICS STUDENT · SOFTWARE DEVELOPMENT ENTHUSIAST ✦
          </p>
        </div>

        <!-- Tagline -->
        <p class="text-slate-300 text-base sm:text-lg md:text-xl max-w-2xl mx-auto lg:mx-0 leading-relaxed font-light">
          “Exploring the universe of technology, one line of code at a time.”
        </p>

        <!-- Primary CTA Buttons -->
        <div class="pt-3 flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-4">
          <a href="#missions" class="w-full sm:w-auto px-7 py-3.5 rounded-2xl bg-gradient-to-r from-sky-500 to-indigo-600 hover:from-sky-400 hover:to-indigo-500 text-white font-semibold text-sm sm:text-base shadow-[0_0_30px_rgba(56,189,248,0.35)] hover:shadow-[0_0_40px_rgba(56,189,248,0.55)] transition-all flex items-center justify-center gap-2.5">
            <i class="fa-solid fa-rocket"></i>
            <span>Explore Mission Archive</span>
          </a>
          <a href="#contact" class="w-full sm:w-auto px-7 py-3.5 rounded-2xl bg-slate-900/75 hover:bg-slate-800/80 border border-slate-700 hover:border-purple-400/50 text-slate-200 font-medium text-sm sm:text-base transition-all flex items-center justify-center gap-2.5">
            <i class="fa-solid fa-satellite-dish text-purple-400"></i>
            <span>Contact Station</span>
          </a>
        </div>

        <!-- Quick Telemetry Highlights -->
        <div class="pt-6 grid grid-cols-3 gap-3 sm:gap-5 max-w-lg mx-auto lg:mx-0">
          <div class="space-card rounded-2xl p-3.5 text-center lg:text-left">
            <div class="text-xs font-mono text-slate-400">CURRENT GPA</div>
            <div class="font-display text-lg sm:text-xl font-bold text-sky-300 mt-0.5">3.65 <span class="text-xs text-slate-400 font-normal">/ 4.00</span></div>
          </div>
          <div class="space-card rounded-2xl p-3.5 text-center lg:text-left">
            <div class="text-xs font-mono text-slate-400">SEMESTER</div>
            <div class="font-display text-lg sm:text-xl font-bold text-purple-300 mt-0.5">5th <span class="text-xs text-slate-400 font-normal">S1 IF</span></div>
          </div>
          <div class="space-card rounded-2xl p-3.5 text-center lg:text-left">
            <div class="text-xs font-mono text-slate-400">CORE STACK</div>
            <div class="font-display text-lg sm:text-xl font-bold text-emerald-300 mt-0.5">4+ <span class="text-xs text-slate-400 font-normal">Langs</span></div>
          </div>
        </div>
      </div>

      <!-- Right Orbital Hologram Visual -->
      <div class="w-full lg:w-2/5 flex items-center justify-center">
        <div class="relative w-72 h-72 sm:w-80 sm:h-80 md:w-96 md:h-96 flex items-center justify-center animate-float">
          <!-- Outer Orbit Ring -->
          <div class="absolute inset-0 orbit-ring animate-spin-slow">
            <span class="absolute -top-2 left-1/2 -translate-x-1/2 w-4 h-4 rounded-full bg-sky-400 shadow-[0_0_16px_#38bdf8]"></span>
            <span class="absolute bottom-6 right-6 w-3 h-3 rounded-full bg-purple-400 shadow-[0_0_14px_#a855f7]"></span>
          </div>

          <!-- Middle Orbit Ring -->
          <div class="absolute inset-7 rounded-full border border-purple-500/25 animate-spin-reverse-slow">
            <span class="absolute top-1/2 -left-1.5 -translate-y-1/2 w-3 h-3 rounded-full bg-emerald-400 shadow-[0_0_12px_#34d399]"></span>
          </div>

          <!-- Inner Planet Core Card -->
          <div class="relative w-48 h-48 sm:w-56 sm:h-56 rounded-full bg-gradient-to-br from-sky-500/20 via-indigo-900/60 to-purple-600/25 border border-sky-300/30 backdrop-blur-xl shadow-[0_0_60px_rgba(56,189,248,0.25)] flex flex-col items-center justify-center text-center p-5">
            <div class="w-16 h-16 rounded-2xl bg-gradient-to-br from-sky-400/25 to-purple-500/25 border border-sky-300/40 flex items-center justify-center mb-3 shadow-inner">
              <i class="fa-solid fa-user-astronaut text-3xl text-sky-300"></i>
            </div>
            <div class="font-display font-bold text-base sm:text-lg text-white tracking-wide">M. NAZWAR</div>
            <div class="font-mono text-[11px] text-sky-300/90 mt-0.5">UNLA · INFORMATIKA</div>
            <div class="mt-2.5 px-2.5 py-0.5 rounded-full bg-slate-950/70 border border-slate-700/80 text-[10px] font-mono text-slate-300">
              ID: 2024–PRESENT
            </div>
          </div>

          <!-- Floating Orbiting Badges -->
          <div class="hidden sm:flex items-center gap-2 px-3 py-1.5 rounded-xl space-card text-xs font-mono text-sky-200 absolute -top-2 right-2">
            <i class="fa-brands fa-java text-sky-400"></i> Java & C#
          </div>
          <div class="hidden sm:flex items-center gap-2 px-3 py-1.5 rounded-xl space-card text-xs font-mono text-purple-200 absolute bottom-2 left-0">
            <i class="fa-brands fa-laravel text-rose-400"></i> Laravel & MySQL
          </div>
        </div>
      </div>
    </section>

    <!-- 2. ABOUT ME & PERSONAL INFORMATION -->
    <section id="about" class="py-16 sm:py-20 reveal">
      <div class="flex items-center gap-3 mb-8">
        <span class="w-10 h-10 rounded-xl bg-sky-500/15 border border-sky-400/30 flex items-center justify-center text-sky-300 text-lg">🪐</span>
        <div>
          <p class="font-mono text-xs uppercase tracking-widest text-sky-400">01 // TELEMETRY & BIO</p>
          <h2 class="font-display text-2xl sm:text-3xl font-bold text-white">About Me & Personal Information</h2>
        </div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 lg:gap-8">
        <!-- About Narrative Card -->
        <div class="lg:col-span-6 space-card rounded-3xl p-6 sm:p-8 flex flex-col justify-between">
          <div class="space-y-4">
            <div class="inline-flex items-center gap-2 text-xs font-mono text-purple-300 bg-purple-500/10 border border-purple-400/25 px-3 py-1 rounded-full">
              <i class="fa-solid fa-terminal"></i>
              <span>ASTRONAUT_LOG.MD</span>
            </div>

            <p class="text-slate-200 text-base sm:text-lg leading-relaxed">
              Hello! I'm <span class="text-sky-300 font-semibold">Muhammad Nazwar</span>, an Informatics student at <span class="text-white font-medium">Universitas Langlangbuana</span>, currently in my 5th semester.
            </p>

            <p class="text-slate-300 text-sm sm:text-base leading-relaxed">
              I have an interest in software development and information technology. Through academic projects, I have gained experience using <span class="text-sky-300 font-mono text-xs sm:text-sm">Java</span>, <span class="text-sky-300 font-mono text-xs sm:text-sm">PHP</span>, <span class="text-sky-300 font-mono text-xs sm:text-sm">C#</span>, and <span class="text-sky-300 font-mono text-xs sm:text-sm">C++</span>, along with <span class="text-purple-300 font-mono text-xs sm:text-sm">Laravel</span>, <span class="text-purple-300 font-mono text-xs sm:text-sm">MySQL</span>, and <span class="text-purple-300 font-mono text-xs sm:text-sm">SQLite</span>.
            </p>

            <p class="text-slate-300 text-sm sm:text-base leading-relaxed">
              I am familiar with developing CRUD systems and testing applications using Postman. I enjoy learning new things, improving my technical skills, and working both independently and as part of a team.
            </p>
          </div>

          <div class="mt-6 pt-5 border-t border-slate-800/80 flex flex-wrap items-center gap-3 text-xs font-mono text-slate-400">
            <span class="px-3 py-1.5 rounded-xl bg-slate-900/90 border border-slate-800 text-sky-300">#SoftwareDevelopment</span>
            <span class="px-3 py-1.5 rounded-xl bg-slate-900/90 border border-slate-800 text-purple-300">#CRUDSystems</span>
            <span class="px-3 py-1.5 rounded-xl bg-slate-900/90 border border-slate-800 text-emerald-300">#APITesting</span>
          </div>
        </div>

        <!-- Personal Information Telemetry Grid -->
        <div class="lg:col-span-6 space-card rounded-3xl p-6 sm:p-8">
          <div class="flex items-center justify-between mb-5">
            <div class="flex items-center gap-2.5">
              <span class="text-lg">🌠</span>
              <h3 class="font-display text-lg sm:text-xl font-bold text-white">Personal Information</h3>
            </div>
            <span class="text-xs font-mono text-emerald-400 bg-emerald-500/10 border border-emerald-400/30 px-2.5 py-1 rounded-lg">VERIFIED</span>
          </div>

          <div class="grid grid-cols-1 sm:grid-cols-2 gap-3.5">
            <!-- Name -->
            <div class="p-3.5 rounded-2xl bg-slate-950/60 border border-slate-800/90 hover:border-sky-400/30 transition-colors">
              <div class="text-[11px] font-mono uppercase tracking-wider text-slate-400">Name</div>
              <div class="text-sm sm:text-base font-semibold text-slate-100 mt-0.5">Muhammad Nazwar</div>
            </div>

            <!-- University -->
            <div class="p-3.5 rounded-2xl bg-slate-950/60 border border-slate-800/90 hover:border-sky-400/30 transition-colors">
              <div class="text-[11px] font-mono uppercase tracking-wider text-slate-400">University</div>
              <div class="text-sm sm:text-base font-semibold text-slate-100 mt-0.5">Universitas Langlangbuana</div>
            </div>

            <!-- Study Program -->
            <div class="p-3.5 rounded-2xl bg-slate-950/60 border border-slate-800/90 hover:border-sky-400/30 transition-colors">
              <div class="text-[11px] font-mono uppercase tracking-wider text-slate-400">Study Program</div>
              <div class="text-sm sm:text-base font-semibold text-sky-300 mt-0.5">S1 Informatika</div>
            </div>

            <!-- Semester & GPA -->
            <div class="p-3.5 rounded-2xl bg-slate-950/60 border border-slate-800/90 hover:border-sky-400/30 transition-colors">
              <div class="text-[11px] font-mono uppercase tracking-wider text-slate-400">Semester / GPA</div>
              <div class="text-sm sm:text-base font-semibold text-purple-300 mt-0.5">Semester 5 · 3.65 / 4.00</div>
            </div>

            <!-- Location -->
            <div class="p-3.5 rounded-2xl bg-slate-950/60 border border-slate-800/90 hover:border-sky-400/30 transition-colors sm:col-span-2">
              <div class="text-[11px] font-mono uppercase tracking-wider text-slate-400">Location</div>
              <div class="text-sm sm:text-base font-semibold text-slate-100 mt-0.5 flex items-center gap-2">
                <i class="fa-solid fa-location-dot text-rose-400 text-xs"></i>
                <span>Bandung, West Java, Indonesia</span>
              </div>
            </div>

            <!-- Interest -->
            <div class="p-3.5 rounded-2xl bg-slate-950/60 border border-slate-800/90 hover:border-sky-400/30 transition-colors sm:col-span-2">
              <div class="text-[11px] font-mono uppercase tracking-wider text-slate-400">Interest</div>
              <div class="text-sm sm:text-base font-semibold text-emerald-300 mt-0.5">Software Development & Information Technology</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 3. TECHNOLOGY UNIVERSE -->
    <section id="tech" class="py-16 sm:py-20 reveal">
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-6 mb-8">
        <div class="flex items-center gap-3">
          <span class="w-10 h-10 rounded-xl bg-purple-500/15 border border-purple-400/30 flex items-center justify-center text-purple-300 text-lg">🚀</span>
          <div>
            <p class="font-mono text-xs uppercase tracking-widest text-purple-400">02 // CONSTELLATION STACK</p>
            <h2 class="font-display text-2xl sm:text-3xl font-bold text-white">Technology Universe</h2>
          </div>
        </div>

        <!-- Interactive Constellation Filter Tabs -->
        <div class="flex flex-wrap gap-2" id="tech-filters">
          <button data-filter="all" class="tech-filter-btn active px-3.5 py-2 rounded-xl text-xs sm:text-sm font-medium bg-sky-500/20 text-sky-200 border border-sky-400/50 transition-all">
            All Systems
          </button>
          <button data-filter="languages" class="tech-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-medium bg-slate-900/80 text-slate-300 border border-slate-800 hover:border-slate-600 transition-all">
            💻 Languages
          </button>
          <button data-filter="framework" class="tech-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-medium bg-slate-900/80 text-slate-300 border border-slate-800 hover:border-slate-600 transition-all">
            ⚙️ Framework
          </button>
          <button data-filter="database" class="tech-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-medium bg-slate-900/80 text-slate-300 border border-slate-800 hover:border-slate-600 transition-all">
            🗄️ Database
          </button>
          <button data-filter="tools" class="tech-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-medium bg-slate-900/80 text-slate-300 border border-slate-800 hover:border-slate-600 transition-all">
            🛠️ Dev Tools
          </button>
        </div>
      </div>

      <!-- Constellation Cards Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6" id="tech-grid">
        <!-- Category 1: Programming Languages -->
        <div class="tech-card space-card rounded-3xl p-6 sm:p-7" data-category="languages">
          <div class="flex items-center justify-between mb-5">
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 rounded-xl bg-sky-500/15 border border-sky-400/30 flex items-center justify-center text-lg">💻</div>
              <div>
                <h3 class="font-display text-lg font-bold text-white">Programming Languages</h3>
                <p class="text-xs font-mono text-slate-400">Core Computational Orbit</p>
              </div>
            </div>
            <span class="text-xs font-mono text-sky-300 bg-sky-500/10 px-2.5 py-1 rounded-lg">4 Nodes</span>
          </div>

          <div class="grid grid-cols-2 gap-3">
            <div class="flex items-center gap-3 p-3 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-sky-400/40 transition-colors">
              <i class="fa-brands fa-java text-amber-400 text-lg w-5 text-center"></i>
              <span class="font-medium text-sm text-slate-100">Java</span>
            </div>
            <div class="flex items-center gap-3 p-3 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-sky-400/40 transition-colors">
              <i class="fa-brands fa-php text-indigo-400 text-lg w-5 text-center"></i>
              <span class="font-medium text-sm text-slate-100">PHP</span>
            </div>
            <div class="flex items-center gap-3 p-3 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-sky-400/40 transition-colors">
              <span class="font-mono font-bold text-purple-400 text-sm w-5 text-center">C#</span>
              <span class="font-medium text-sm text-slate-100">C#</span>
            </div>
            <div class="flex items-center gap-3 p-3 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-sky-400/40 transition-colors">
              <span class="font-mono font-bold text-sky-400 text-xs w-5 text-center">C++</span>
              <span class="font-medium text-sm text-slate-100">C++</span>
            </div>
          </div>
        </div>

        <!-- Category 2: Framework & Database Combined or Separate Cards -->
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-1 gap-6">
          <!-- Framework -->
          <div class="tech-card space-card rounded-3xl p-6 sm:p-7" data-category="framework">
            <div class="flex items-center justify-between mb-4">
              <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-rose-500/15 border border-rose-400/30 flex items-center justify-center text-lg">⚙️</div>
                <div>
                  <h3 class="font-display text-lg font-bold text-white">Framework</h3>
                  <p class="text-xs font-mono text-slate-400">Web Architecture Engine</p>
                </div>
              </div>
              <span class="text-xs font-mono text-rose-300 bg-rose-500/10 px-2.5 py-1 rounded-lg">1 Node</span>
            </div>

            <div class="flex items-center justify-between p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-rose-400/40 transition-colors">
              <div class="flex items-center gap-3">
                <i class="fa-brands fa-laravel text-rose-400 text-xl"></i>
                <span class="font-semibold text-sm sm:text-base text-slate-100">Laravel</span>
              </div>
              <span class="text-xs font-mono text-slate-400">PHP MVC Framework</span>
            </div>
          </div>

          <!-- Database -->
          <div class="tech-card space-card rounded-3xl p-6 sm:p-7" data-category="database">
            <div class="flex items-center justify-between mb-4">
              <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-emerald-500/15 border border-emerald-400/30 flex items-center justify-center text-lg">🗄️</div>
                <div>
                  <h3 class="font-display text-lg font-bold text-white">Database</h3>
                  <p class="text-xs font-mono text-slate-400">Relational Data Storage</p>
                </div>
              </div>
              <span class="text-xs font-mono text-emerald-300 bg-emerald-500/10 px-2.5 py-1 rounded-lg">2 Nodes</span>
            </div>

            <div class="grid grid-cols-2 gap-3">
              <div class="flex items-center gap-3 p-3 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-emerald-400/40 transition-colors">
                <i class="fa-solid fa-database text-sky-400 text-base"></i>
                <span class="font-medium text-sm text-slate-100">MySQL</span>
              </div>
              <div class="flex items-center gap-3 p-3 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-emerald-400/40 transition-colors">
                <i class="fa-solid fa-server text-emerald-400 text-base"></i>
                <span class="font-medium text-sm text-slate-100">SQLite</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Category 4: Development Tools (Full Width) -->
        <div class="tech-card md:col-span-2 space-card rounded-3xl p-6 sm:p-7" data-category="tools">
          <div class="flex items-center justify-between mb-5">
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 rounded-xl bg-purple-500/15 border border-purple-400/30 flex items-center justify-center text-lg">🛠️</div>
              <div>
                <h3 class="font-display text-lg font-bold text-white">Development Tools</h3>
                <p class="text-xs font-mono text-slate-400">IDEs, API Testing & Productivity Suite</p>
              </div>
            </div>
            <span class="text-xs font-mono text-purple-300 bg-purple-500/10 px-2.5 py-1 rounded-lg">6 Nodes</span>
          </div>

          <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-3">
            <div class="flex items-center gap-3 p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-sky-400/40 transition-colors">
              <i class="fa-solid fa-code text-sky-400 text-base w-5 text-center"></i>
              <span class="font-medium text-sm text-slate-100">Visual Studio Code</span>
            </div>
            <div class="flex items-center gap-3 p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-purple-400/40 transition-colors">
              <i class="fa-solid fa-laptop-code text-purple-400 text-base w-5 text-center"></i>
              <span class="font-medium text-sm text-slate-100">Visual Studio</span>
            </div>
            <div class="flex items-center gap-3 p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-orange-400/40 transition-colors">
              <i class="fa-solid fa-paper-plane text-orange-400 text-base w-5 text-center"></i>
              <span class="font-medium text-sm text-slate-100">Postman</span>
            </div>
            <div class="flex items-center gap-3 p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-emerald-400/40 transition-colors">
              <i class="fa-solid fa-file-excel text-emerald-400 text-base w-5 text-center"></i>
              <span class="font-medium text-sm text-slate-100">Microsoft Excel</span>
            </div>
            <div class="flex items-center gap-3 p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-blue-400/40 transition-colors">
              <i class="fa-solid fa-file-word text-blue-400 text-base w-5 text-center"></i>
              <span class="font-medium text-sm text-slate-100">Microsoft Word</span>
            </div>
            <div class="flex items-center gap-3 p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 hover:border-amber-400/40 transition-colors">
              <i class="fa-solid fa-file-powerpoint text-amber-400 text-base w-5 text-center"></i>
              <span class="font-medium text-sm text-slate-100">Microsoft PowerPoint</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 4. MISSION ARCHIVE -->
    <section id="missions" class="py-16 sm:py-20 reveal">
      <div class="flex items-center gap-3 mb-10">
        <span class="w-10 h-10 rounded-xl bg-sky-500/15 border border-sky-400/30 flex items-center justify-center text-sky-300 text-lg">🛰️</span>
        <div>
          <p class="font-mono text-xs uppercase tracking-widest text-sky-400">03 // FLIGHT LOGS & EXPERIENCE</p>
          <h2 class="font-display text-2xl sm:text-3xl font-bold text-white">Mission Archive</h2>
        </div>
      </div>

      <!-- Orbital Timeline -->
      <div class="relative pl-6 sm:pl-10 border-l-2 border-slate-800 space-y-8">
        <!-- Mission 2 (Latest Chronologically: Aug - Oct 2026, or keeping user's exact numbered order 1, 2, 3 with clear badges) -->
        
        <!-- Mission 01 -->
        <div class="relative space-card rounded-3xl p-6 sm:p-8">
          <!-- Timeline Node Dot -->
          <span class="absolute -left-[33px] sm:-left-[49px] top-8 w-4 h-4 rounded-full bg-sky-400 border-4 border-[#040611] shadow-[0_0_15px_#38bdf8]"></span>

          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 pb-4 border-b border-slate-800/80">
            <div>
              <div class="inline-flex items-center gap-2 text-xs font-mono text-sky-300 mb-1">
                <span>MISSION // 01</span>
                <span>•</span>
                <span>CONFERENCE OPERATIONS</span>
              </div>
              <h3 class="font-display text-xl sm:text-2xl font-bold text-white">
                International Conference on ICT for Smart Society (ICISS) 2025
              </h3>
            </div>
            <div class="flex flex-wrap sm:flex-col items-start sm:items-end gap-1.5 shrink-0">
              <span class="px-3 py-1 rounded-xl bg-sky-500/15 border border-sky-400/30 text-sky-300 font-semibold text-xs sm:text-sm">
                Assistant Moderator
              </span>
              <span class="font-mono text-xs text-slate-400">
                <i class="fa-regular fa-calendar mr-1 text-sky-400"></i>September 2025
              </span>
            </div>
          </div>

          <ul class="mt-5 space-y-2.5 text-slate-300 text-sm sm:text-base">
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-sky-400 mt-1 shrink-0"></i>
              <span>Assisted the moderator in managing presentation sessions.</span>
            </li>
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-sky-400 mt-1 shrink-0"></i>
              <span>Helped with timekeeping and activity summaries.</span>
            </li>
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-sky-400 mt-1 shrink-0"></i>
              <span>Recorded and documented materials presented by national and international speakers.</span>
            </li>
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-sky-400 mt-1 shrink-0"></i>
              <span>Prepared event documentation in the form of reports and conference archives.</span>
            </li>
          </ul>
        </div>

        <!-- Mission 02 -->
        <div class="relative space-card rounded-3xl p-6 sm:p-8">
          <!-- Timeline Node Dot -->
          <span class="absolute -left-[33px] sm:-left-[49px] top-8 w-4 h-4 rounded-full bg-purple-400 border-4 border-[#040611] shadow-[0_0_15px_#a855f7]"></span>

          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 pb-4 border-b border-slate-800/80">
            <div>
              <div class="inline-flex items-center gap-2 text-xs font-mono text-purple-300 mb-1">
                <span>MISSION // 02</span>
                <span>•</span>
                <span>FIELD DATA TELEMETRY</span>
              </div>
              <h3 class="font-display text-xl sm:text-2xl font-bold text-white">
                Livable City Index Kota Bandung 2026
              </h3>
            </div>
            <div class="flex flex-wrap sm:flex-col items-start sm:items-end gap-1.5 shrink-0">
              <span class="px-3 py-1 rounded-xl bg-purple-500/15 border border-purple-400/30 text-purple-300 font-semibold text-xs sm:text-sm">
                Surveyor
              </span>
              <span class="font-mono text-xs text-slate-400">
                <i class="fa-regular fa-calendar mr-1 text-purple-400"></i>August – October 2026
              </span>
            </div>
          </div>

          <ul class="mt-5 space-y-2.5 text-slate-300 text-sm sm:text-base">
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-purple-400 mt-1 shrink-0"></i>
              <span>Collected field data through surveys and direct interviews with respondents.</span>
            </li>
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-purple-400 mt-1 shrink-0"></i>
              <span>Coordinated with the survey team during data collection.</span>
            </li>
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-purple-400 mt-1 shrink-0"></i>
              <span>Followed established procedures and targets.</span>
            </li>
          </ul>
        </div>

        <!-- Mission 03 -->
        <div class="relative space-card rounded-3xl p-6 sm:p-8">
          <!-- Timeline Node Dot -->
          <span class="absolute -left-[33px] sm:-left-[49px] top-8 w-4 h-4 rounded-full bg-emerald-400 border-4 border-[#040611] shadow-[0_0_15px_#34d399]"></span>

          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 pb-4 border-b border-slate-800/80">
            <div>
              <div class="inline-flex items-center gap-2 text-xs font-mono text-emerald-300 mb-1">
                <span>MISSION // 03</span>
                <span>•</span>
                <span>IOT INNOVATION & ACCESSIBILITY</span>
              </div>
              <h3 class="font-display text-xl sm:text-2xl font-bold text-white">
                Program Kreativitas Mahasiswa – Karsa Cipta (PKM-KC) 2026
              </h3>
            </div>
            <div class="flex flex-wrap sm:flex-col items-start sm:items-end gap-1.5 shrink-0">
              <span class="px-3 py-1 rounded-xl bg-emerald-500/15 border border-emerald-400/30 text-emerald-300 font-semibold text-xs sm:text-sm">
                Team Member
              </span>
              <span class="font-mono text-xs text-slate-400">
                <i class="fa-regular fa-calendar mr-1 text-emerald-400"></i>April 2026
              </span>
            </div>
          </div>

          <ul class="mt-5 space-y-2.5 text-slate-300 text-sm sm:text-base">
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-emerald-400 mt-1 shrink-0"></i>
              <span>Participated in preparing a team proposal for an IoT-based smart trash bin.</span>
            </li>
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-emerald-400 mt-1 shrink-0"></i>
              <span>Developed the concept of automatic waste sorting using sensors.</span>
            </li>
            <li class="flex items-start gap-3">
              <i class="fa-solid fa-angle-right text-emerald-400 mt-1 shrink-0"></i>
              <span>Proposed voice guidance features to improve accessibility for people with disabilities.</span>
            </li>
          </ul>
        </div>
      </div>
    </section>

    <!-- 5. ACADEMIC EXPLORATION, EDUCATION & LANGUAGES -->
    <section id="exploration" class="py-16 sm:py-20 reveal">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 lg:gap-8">
        <!-- Academic Exploration (Left 7 cols) -->
        <div class="lg:col-span-7 space-card rounded-3xl p-6 sm:p-8 flex flex-col justify-between">
          <div>
            <div class="flex items-center gap-3 mb-4">
              <span class="w-10 h-10 rounded-xl bg-indigo-500/15 border border-indigo-400/30 flex items-center justify-center text-lg">🔭</span>
              <div>
                <p class="font-mono text-xs uppercase tracking-widest text-indigo-400">04 // RESEARCH & LABS</p>
                <h2 class="font-display text-xl sm:text-2xl font-bold text-white">Academic Exploration</h2>
              </div>
            </div>

            <p class="text-slate-400 text-sm sm:text-base mb-5">
              Areas explored through academic projects and learning:
            </p>

            <div class="space-y-3">
              <div class="flex items-center gap-3.5 p-3.5 rounded-2xl bg-slate-950/65 border border-slate-800/90 hover:border-sky-400/35 transition-colors">
                <span class="w-8 h-8 rounded-xl bg-sky-500/15 text-sky-300 flex items-center justify-center shrink-0">
                  <i class="fa-solid fa-cubes text-sm"></i>
                </span>
                <span class="text-slate-200 text-sm sm:text-base">Application development using Java, Laravel, and C#.</span>
              </div>

              <div class="flex items-center gap-3.5 p-3.5 rounded-2xl bg-slate-950/65 border border-slate-800/90 hover:border-purple-400/35 transition-colors">
                <span class="w-8 h-8 rounded-xl bg-purple-500/15 text-purple-300 flex items-center justify-center shrink-0">
                  <i class="fa-solid fa-layer-group text-sm"></i>
                </span>
                <span class="text-slate-200 text-sm sm:text-base">CRUD system development.</span>
              </div>

              <div class="flex items-center gap-3.5 p-3.5 rounded-2xl bg-slate-950/65 border border-slate-800/90 hover:border-emerald-400/35 transition-colors">
                <span class="w-8 h-8 rounded-xl bg-emerald-500/15 text-emerald-300 flex items-center justify-center shrink-0">
                  <i class="fa-solid fa-database text-sm"></i>
                </span>
                <span class="text-slate-200 text-sm sm:text-base">Database implementation using MySQL and SQLite.</span>
              </div>

              <div class="flex items-center gap-3.5 p-3.5 rounded-2xl bg-slate-950/65 border border-slate-800/90 hover:border-orange-400/35 transition-colors">
                <span class="w-8 h-8 rounded-xl bg-orange-500/15 text-orange-300 flex items-center justify-center shrink-0">
                  <i class="fa-solid fa-vial-circle-check text-sm"></i>
                </span>
                <span class="text-slate-200 text-sm sm:text-base">Application testing using Postman.</span>
              </div>

              <div class="flex items-center gap-3.5 p-3.5 rounded-2xl bg-slate-950/65 border border-slate-800/90 hover:border-cyan-400/35 transition-colors">
                <span class="w-8 h-8 rounded-xl bg-cyan-500/15 text-cyan-300 flex items-center justify-center shrink-0">
                  <i class="fa-solid fa-microchip text-sm"></i>
                </span>
                <span class="text-slate-200 text-sm sm:text-base">Concept design for IoT-based smart devices.</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Education & Languages (Right 5 cols) -->
        <div class="lg:col-span-5 flex flex-col gap-6">
          <!-- Education Card -->
          <div class="space-card rounded-3xl p-6 sm:p-8 flex-1">
            <div class="flex items-center gap-3 mb-5">
              <span class="w-10 h-10 rounded-xl bg-sky-500/15 border border-sky-400/30 flex items-center justify-center text-lg">🎓</span>
              <div>
                <p class="font-mono text-xs uppercase tracking-widest text-sky-400">ACADEMY</p>
                <h2 class="font-display text-xl sm:text-2xl font-bold text-white">Education</h2>
              </div>
            </div>

            <div class="p-4 rounded-2xl bg-slate-950/70 border border-slate-800/90 space-y-3">
              <div class="flex items-start justify-between gap-2">
                <h3 class="font-display text-lg font-bold text-white">Universitas Langlangbuana</h3>
                <span class="px-2.5 py-1 rounded-lg bg-sky-500/15 text-sky-300 font-mono text-xs shrink-0">2024 – Present</span>
              </div>

              <div class="space-y-1.5 text-sm text-slate-300">
                <div class="flex items-center justify-between">
                  <span class="text-slate-400">Program</span>
                  <span class="font-medium text-slate-100">S1 Informatika</span>
                </div>
                <div class="flex items-center justify-between">
                  <span class="text-slate-400">GPA</span>
                  <span class="font-mono font-semibold text-emerald-300">3.65 / 4.00</span>
                </div>
              </div>

              <!-- Visual GPA Orbit Bar -->
              <div class="pt-2">
                <div class="w-full h-2 rounded-full bg-slate-800 overflow-hidden">
                  <div class="h-full rounded-full bg-gradient-to-r from-sky-400 to-purple-500" style="width: 91.25%;"></div>
                </div>
              </div>
            </div>
          </div>

          <!-- Languages Card -->
          <div class="space-card rounded-3xl p-6 sm:p-8">
            <div class="flex items-center gap-3 mb-5">
              <span class="w-10 h-10 rounded-xl bg-purple-500/15 border border-purple-400/30 flex items-center justify-center text-lg">🌍</span>
              <div>
                <p class="font-mono text-xs uppercase tracking-widest text-purple-400">COMMUNICATIONS</p>
                <h2 class="font-display text-xl sm:text-2xl font-bold text-white">Languages</h2>
              </div>
            </div>

            <div class="space-y-3">
              <div class="p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 flex items-center justify-between">
                <div>
                  <div class="font-semibold text-slate-100 text-sm sm:text-base">Indonesian</div>
                  <div class="text-xs text-slate-400">Primary Language</div>
                </div>
                <span class="px-3 py-1 rounded-xl bg-emerald-500/15 border border-emerald-400/30 text-emerald-300 text-xs font-mono font-medium">
                  Native
                </span>
              </div>

              <div class="p-3.5 rounded-2xl bg-slate-950/70 border border-slate-800/90 flex items-center justify-between">
                <div>
                  <div class="font-semibold text-slate-100 text-sm sm:text-base">English</div>
                  <div class="text-xs text-slate-400">Reading and Writing</div>
                </div>
                <span class="px-3 py-1 rounded-xl bg-sky-500/15 border border-sky-400/30 text-sky-300 text-xs font-mono font-medium">
                  Active
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 6. CONTACT STATION -->
    <section id="contact" class="py-16 sm:py-20 reveal">
      <div class="space-card rounded-3xl p-8 sm:p-12 relative overflow-hidden border-sky-400/25">
        <!-- Decorative Radial Glow -->
        <div class="absolute -right-24 -bottom-24 w-72 h-72 rounded-full bg-sky-500/15 blur-3xl pointer-events-none"></div>
        <div class="absolute -left-24 -top-24 w-72 h-72 rounded-full bg-purple-500/15 blur-3xl pointer-events-none"></div>

        <div class="relative z-10 max-w-3xl mx-auto text-center space-y-6">
          <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-sky-500/10 border border-sky-400/30 text-sky-300 font-mono text-xs">
            <span>📡</span>
            <span>OPEN FREQUENCY // TRANSMISSION READY</span>
          </div>

          <h2 class="font-display text-3xl sm:text-4xl font-bold text-white">
            Contact Station
          </h2>

          <p class="text-slate-300 text-base sm:text-lg max-w-xl mx-auto">
            Feel free to connect with me! Whether it's about software development projects, academic collaborations, or tech discussions, my frequency is always open.
          </p>

          <!-- Contact Details Cards -->
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-2 text-left">
            <!-- Email Card with Copy & Mailto -->
            <div class="p-4 sm:p-5 rounded-2xl bg-slate-950/80 border border-slate-800 hover:border-sky-400/50 transition-all flex items-center justify-between gap-3">
              <div class="flex items-center gap-3.5 min-w-0">
                <div class="w-11 h-11 rounded-xl bg-sky-500/15 border border-sky-400/30 flex items-center justify-center text-sky-300 shrink-0">
                  <i class="fa-solid fa-envelope text-lg"></i>
                </div>
                <div class="min-w-0">
                  <div class="text-xs font-mono text-slate-400">EMAIL ADDRESS</div>
                  <a href="mailto:nazwaradp@gmail.com" class="text-sm sm:text-base font-semibold text-white hover:text-sky-300 transition-colors truncate block">
                    nazwaradp@gmail.com
                  </a>
                </div>
              </div>

              <button id="copy-email-btn" title="Copy Email" class="px-3 py-2 rounded-xl bg-slate-900 hover:bg-sky-500/20 border border-slate-700 hover:border-sky-400/50 text-slate-300 hover:text-sky-200 text-xs font-mono transition-all shrink-0 flex items-center gap-1.5">
                <i class="fa-regular fa-copy"></i>
                <span id="copy-email-text">Copy</span>
              </button>
            </div>

            <!-- Location Card -->
            <div class="p-4 sm:p-5 rounded-2xl bg-slate-950/80 border border-slate-800 hover:border-purple-400/50 transition-all flex items-center gap-3.5">
              <div class="w-11 h-11 rounded-xl bg-purple-500/15 border border-purple-400/30 flex items-center justify-center text-purple-300 shrink-0">
                <i class="fa-solid fa-earth-asia text-lg"></i>
              </div>
              <div>
                <div class="text-xs font-mono text-slate-400">BASE COORDINATES</div>
                <div class="text-sm sm:text-base font-semibold text-white">
                  Bandung, West Java, Indonesia
                </div>
              </div>
            </div>
          </div>

          <!-- Direct Action Button -->
          <div class="pt-2">
            <a href="mailto:nazwaradp@gmail.com" class="inline-flex items-center justify-center gap-2.5 px-8 py-3.5 rounded-2xl bg-gradient-to-r from-sky-500 to-purple-600 hover:from-sky-400 hover:to-purple-500 text-white font-semibold text-sm sm:text-base shadow-[0_0_25px_rgba(56,189,248,0.3)] hover:shadow-[0_0_35px_rgba(168,85,247,0.45)] transition-all">
              <i class="fa-solid fa-paper-plane"></i>
              <span>Send Transmission via Email</span>
            </a>
          </div>
        </div>
      </div>
    </section>

  </main>

  <!-- COSMIC FOOTER -->
  <footer class="relative z-10 border-t border-slate-800/80 bg-[#03050e]/90 backdrop-blur-lg mt-10">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-10 text-center space-y-3">
      <div class="font-display text-lg sm:text-xl font-bold text-cosmic-gradient">
        ✨ Beyond the Code, Into the Universe ✨
      </div>
      <p class="font-mono text-xs sm:text-sm text-slate-300 tracking-wide">
        Keep Learning · Keep Exploring · Keep Creating
      </p>
      <div class="text-xl pt-1 tracking-widest">
        🌌 🚀 🪐
      </div>
      <p class="text-xs text-slate-500 pt-3">
        © 2026 Muhammad Nazwar · S1 Informatika, Universitas Langlangbuana
      </p>
    </div>
  </footer>

  <!-- Custom Toast Notification (No alert() used) -->
  <div id="toast-notification" class="fixed bottom-6 right-6 z-50 translate-y-20 opacity-0 pointer-events-none transition-all duration-300 px-4 py-3 rounded-2xl bg-slate-900/95 border border-sky-400/50 text-sky-200 shadow-[0_10px_30px_rgba(0,0,0,0.6)] backdrop-blur-xl flex items-center gap-2.5 text-sm font-medium">
    <i class="fa-solid fa-circle-check text-emerald-400"></i>
    <span id="toast-message">Email copied to clipboard!</span>
  </div>

  <!-- Interactive Starfield & UI Logic -->
  <script>
    // 1. Animated Deep-Space Starfield & Shooting Stars Canvas
    (function initStarfield() {
      const canvas = document.getElementById('starfield-canvas');
      if (!canvas) return;
      const ctx = canvas.getContext('2d');

      let width = 0;
      let height = 0;
      let stars = [];
      let shootingStars = [];

      function resizeCanvas() {
        width = canvas.width = window.innerWidth;
        height = canvas.height = window.innerHeight;
        createStars();
      }

      function createStars() {
        const count = Math.min(Math.floor((width * height) / 6500), 260);
        stars = [];
        const colors = ['#ffffff', '#bae6fd', '#e9d5ff', '#7dd3fc', '#c4b5fd'];
        for (let i = 0; i < count; i++) {
          stars.push({
            x: Math.random() * width,
            y: Math.random() * height,
            radius: Math.random() * 1.6 + 0.3,
            alpha: Math.random() * 0.8 + 0.2,
            twinkleSpeed: (Math.random() * 0.02 + 0.005) * (Math.random() < 0.5 ? 1 : -1),
            driftY: Math.random() * 0.12 + 0.02,
            color: colors[Math.floor(Math.random() * colors.length)]
          });
        }
      }

      function spawnShootingStar() {
        if (shootingStars.length < 2 && Math.random() < 0.008) {
          shootingStars.push({
            x: Math.random() * width * 0.8,
            y: Math.random() * height * 0.4,
            length: Math.random() * 90 + 60,
            speed: Math.random() * 9 + 7,
            angle: Math.PI / 5,
            opacity: 1
          });
        }
      }

      function animate() {
        ctx.clearRect(0, 0, width, height);

        // Draw twinkling stars
        for (let i = 0; i < stars.length; i++) {
          const s = stars[i];
          s.alpha += s.twinkleSpeed;
          if (s.alpha > 1 || s.alpha < 0.15) {
            s.twinkleSpeed *= -1;
          }

          s.y -= s.driftY;
          if (s.y < 0) {
            s.y = height;
            s.x = Math.random() * width;
          }

          ctx.beginPath();
          ctx.arc(s.x, s.y, s.radius, 0, Math.PI * 2);
          ctx.fillStyle = s.color;
          ctx.globalAlpha = Math.max(0.1, Math.min(1, s.alpha));
          ctx.fill();
        }

        // Draw shooting stars
        spawnShootingStar();
        for (let i = shootingStars.length - 1; i >= 0; i--) {
          const ss = shootingStars[i];
          const endX = ss.x - Math.cos(ss.angle) * ss.length;
          const endY = ss.y - Math.sin(ss.angle) * ss.length;

          const grad = ctx.createLinearGradient(ss.x, ss.y, endX, endY);
          grad.addColorStop(0, `rgba(186, 230, 253, ${ss.opacity})`);
          grad.addColorStop(1, 'rgba(56, 189, 248, 0)');

          ctx.beginPath();
          ctx.moveTo(ss.x, ss.y);
          ctx.lineTo(endX, endY);
          ctx.strokeStyle = grad;
          ctx.lineWidth = 1.6;
          ctx.globalAlpha = ss.opacity;
          ctx.stroke();

          ss.x += Math.cos(ss.angle) * ss.speed;
          ss.y += Math.sin(ss.angle) * ss.speed;
          ss.opacity -= 0.015;

          if (ss.opacity <= 0 || ss.x > width + 100 || ss.y > height + 100) {
            shootingStars.splice(i, 1);
          }
        }

        ctx.globalAlpha = 1;
        requestAnimationFrame(animate);
      }

      window.addEventListener('resize', resizeCanvas);
      window.addEventListener('load', () => {
        resizeCanvas();
        animate();
      });
    })();

    // 2. Mobile Navigation Toggle
    const mobileMenuBtn = document.getElementById('mobile-menu-btn');
    const mobileMenu = document.getElementById('mobile-menu');
    const mobileLinks = document.querySelectorAll('.mobile-link');

    if (mobileMenuBtn && mobileMenu) {
      mobileMenuBtn.addEventListener('click', () => {
        mobileMenu.classList.toggle('hidden');
      });

      mobileLinks.forEach(link => {
        link.addEventListener('click', () => {
          mobileMenu.classList.add('hidden');
        });
      });
    }

    // 3. Technology Universe Filter Tabs
    const filterButtons = document.querySelectorAll('.tech-filter-btn');
    const techCards = document.querySelectorAll('.tech-card');

    filterButtons.forEach(btn => {
      btn.addEventListener('click', () => {
        const filter = btn.getAttribute('data-filter');

        // Update active tab styling
        filterButtons.forEach(b => {
          b.classList.remove('active', 'bg-sky-500/20', 'text-sky-200', 'border-sky-400/50');
          b.classList.add('bg-slate-900/80', 'text-slate-300', 'border-slate-800');
        });
        btn.classList.add('active', 'bg-sky-500/20', 'text-sky-200', 'border-sky-400/50');
        btn.classList.remove('bg-slate-900/80', 'text-slate-300', 'border-slate-800');

        // Filter cards smoothly
        techCards.forEach(card => {
          const category = card.getAttribute('data-category');
          if (filter === 'all' || category === filter) {
            card.style.display = '';
          } else {
            card.style.display = 'none';
          }
        });
      });
    });

    // 4. One-Click Email Copy with Toast Notification (using document.execCommand fallback)
    const copyEmailBtn = document.getElementById('copy-email-btn');
    const copyEmailText = document.getElementById('copy-email-text');
    const toast = document.getElementById('toast-notification');
    const toastMessage = document.getElementById('toast-message');
    let toastTimeout = null;

    function showToast(msg) {
      if (!toast || !toastMessage) return;
      toastMessage.textContent = msg;
      toast.classList.remove('translate-y-20', 'opacity-0');
      toast.classList.add('translate-y-0', 'opacity-100');

      clearTimeout(toastTimeout);
      toastTimeout = setTimeout(() => {
        toast.classList.add('translate-y-20', 'opacity-0');
        toast.classList.remove('translate-y-0', 'opacity-100');
      }, 2800);
    }

    if (copyEmailBtn) {
      copyEmailBtn.addEventListener('click', () => {
        const email = 'nazwaradp@gmail.com';
        const tempInput = document.createElement('textarea');
        tempInput.value = email;
        tempInput.style.position = 'fixed';
        tempInput.style.opacity = '0';
        document.body.appendChild(tempInput);
        tempInput.select();

        try {
          document.execCommand('copy');
          if (copyEmailText) copyEmailText.textContent = 'Copied!';
          showToast('Copied nazwaradp@gmail.com to clipboard!');
          setTimeout(() => {
            if (copyEmailText) copyEmailText.textContent = 'Copy';
          }, 2200);
        } catch (err) {
          showToast('Email: nazwaradp@gmail.com');
        } finally {
          document.body.removeChild(tempInput);
        }
      });
    }

    // 5. Scroll Reveal Observer
    const revealElements = document.querySelectorAll('.reveal');
    const revealObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
          revealObserver.unobserve(entry.target);
        }
      });
    }, { threshold: 0.1 });

    revealElements.forEach(el => revealObserver.observe(el));
  </script>
</body>
</html>
