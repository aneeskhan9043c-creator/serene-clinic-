# Serene Dental Website - Final Source Code

Here is the complete source code for your newly optimized Serene Dental website. You can easily copy this complete `index.html` into your deployment setup.

```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Serene Dental — Premium Dental Care</title>
  <meta name="description" content="Expert dental care combining cutting-edge technology with a gentle human touch. Trusted by 10,000+ patients." />
  <meta name="theme-color" content="#006497">
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet" />
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            heading: ['"Plus Jakarta Sans"', 'sans-serif'],
            body: ['"Inter"', 'sans-serif'],
          },
          colors: {
            primary: '#1A6BCC',
            'primary-dark': '#145AAD',
            navy: '#0a1628',
            'navy-footer': '#0a0f1e',
            'soft-blue': '#EFF6FF',
            'text-dark': '#0f172a',
            'text-muted': '#64748b',
          },
        },
      },
    };
  </script>
  <style>
    *, *::before, *::after { box-sizing: border-box; }
    body { font-family: 'Inter', sans-serif; margin: 0; background: #fff; color: #0f172a; }

    /* ─── Navbar blur on scroll ─── */
    .navbar-scrolled { background: rgba(255,255,255,0.82) !important; backdrop-filter: blur(16px); box-shadow: 0 1px 24px rgba(0,0,0,0.06); }

    /* ─── NotchNav active indicator ─── */
    .nav-indicator { position: absolute; bottom: -6px; left: 50%; transform: translateX(-50%); width: 0; height: 3px; background: #1A6BCC; border-radius: 999px; transition: width 0.35s cubic-bezier(.4,0,.2,1); }
    .nav-link:hover .nav-indicator,
    .nav-link.active .nav-indicator { width: 60%; }

    /* ─── Hero text gradient ─── */
    .hero-gradient-text {
      background: linear-gradient(135deg, #0a1628 0%, #1A6BCC 100%);
      -webkit-background-clip: text; -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    /* ─── Service card ─── */
    .service-card { position: relative; overflow: hidden; border-radius: 1.5rem; min-height: 400px; }
    .service-card img { transition: transform 0.6s ease; }
    .service-card:hover img { transform: scale(1.08); }
    .service-card:hover { box-shadow: 0 20px 60px rgba(26,107,204,0.18); }
    .service-card .learn-arrow { transition: transform 0.3s ease; }
    .service-card:hover .learn-arrow { transform: translateX(6px); }

    /* ─── Gallery hover ─── */
    .gallery-img { transition: transform 0.45s ease, box-shadow 0.45s ease; }
    .gallery-img:hover { transform: scale(1.03); box-shadow: 0 16px 48px rgba(0,0,0,0.12); }

    /* ─── Footer aurora pulse ─── */
    @keyframes auroraPulse {
      0%, 100% { opacity: 0.25; transform: scale(1); }
      50% { opacity: 0.45; transform: scale(1.15); }
    }
    .aurora-glow {
      position: absolute; top: 50%; left: 50%; transform: translate(-50%,-50%);
      width: 700px; height: 700px; border-radius: 50%;
      background: radial-gradient(circle, rgba(26,107,204,0.35) 0%, rgba(20,90,173,0.12) 40%, transparent 70%);
      animation: auroraPulse 6s ease-in-out infinite; pointer-events: none; z-index: 0;
    }

    /* ─── Footer grid lines ─── */
    .grid-lines {
      position: absolute; inset: 0; z-index: 0; pointer-events: none; opacity: 0.03;
      background-image:
        linear-gradient(rgba(255,255,255,0.5) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.5) 1px, transparent 1px);
      background-size: 60px 60px;
    }

    /* ─── Marquee ─── */
    @keyframes marqueeScroll { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }
    .marquee-track { display: flex; width: max-content; animation: marqueeScroll 20s linear infinite; }

    /* ─── Heart pulse ─── */
    @keyframes heartPulse { 0%,100% { transform: scale(1); } 50% { transform: scale(1.25); } }
    .heart-pulse { display: inline-block; animation: heartPulse 1.2s ease-in-out infinite; color: #ef4444; }

    /* ─── Glass pill buttons ─── */
    .glass-pill {
      background: rgba(255,255,255,0.08); border: 1px solid rgba(255,255,255,0.18);
      backdrop-filter: blur(12px); transition: all 0.4s ease;
    }
    .glass-pill:hover {
      background: rgba(255,255,255,0.16); border-color: rgba(255,255,255,0.4);
      transform: translateY(-4px); box-shadow: 0 8px 32px rgba(26,107,204,0.2);
    }

    /* ─── Fade-in animation ─── */
    .fade-up { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .fade-up.visible { opacity: 1; transform: translateY(0); }

    /* ─── Mobile menu ─── */
    .mobile-menu { max-height: 0; overflow: hidden; transition: max-height 0.4s ease; }
    .mobile-menu.open { max-height: 400px; }

    /* ─── Back to top ─── */
    .back-to-top { transition: all 0.35s ease; }
    .back-to-top:hover { transform: translateY(-6px); box-shadow: 0 8px 24px rgba(26,107,204,0.3); }

    /* === BASE ANIMATION STATES === */
    .reveal-up {
      opacity: 0;
      transform: translateY(60px);
      transition: opacity 0.7s cubic-bezier(0.22, 1, 0.36, 1),
                  transform 0.7s cubic-bezier(0.22, 1, 0.36, 1);
    }
    .reveal-up.visible { opacity: 1; transform: translateY(0); }

    .reveal-left {
      opacity: 0;
      transform: translateX(-60px);
      transition: opacity 0.8s cubic-bezier(0.22, 1, 0.36, 1),
                  transform 0.8s cubic-bezier(0.22, 1, 0.36, 1);
    }
    .reveal-left.visible { opacity: 1; transform: translateX(0); }

    .reveal-right {
      opacity: 0;
      transform: translateX(60px);
      transition: opacity 0.8s cubic-bezier(0.22, 1, 0.36, 1),
                  transform 0.8s cubic-bezier(0.22, 1, 0.36, 1);
    }
    .reveal-right.visible { opacity: 1; transform: translateX(0); }

    .reveal-scale {
      opacity: 0;
      transform: scale(0.88);
      transition: opacity 0.7s cubic-bezier(0.22, 1, 0.36, 1),
                  transform 0.7s cubic-bezier(0.22, 1, 0.36, 1);
    }
    .reveal-scale.visible { opacity: 1; transform: scale(1); }

    .reveal-blur {
      opacity: 0;
      filter: blur(12px);
      transform: translateY(30px);
      transition: opacity 0.9s ease,
                  filter 0.9s ease,
                  transform 0.9s cubic-bezier(0.22, 1, 0.36, 1);
    }
    .reveal-blur.visible { opacity: 1; filter: blur(0px); transform: translateY(0); }

    .delay-100 { transition-delay: 0.1s; }
    .delay-200 { transition-delay: 0.2s; }
    .delay-300 { transition-delay: 0.3s; }
    .delay-400 { transition-delay: 0.4s; }
    .delay-500 { transition-delay: 0.5s; }
    .delay-600 { transition-delay: 0.6s; }

    .img-zoom { overflow: hidden; border-radius: inherit; }
    .img-zoom img { transition: transform 0.6s cubic-bezier(0.22, 1, 0.36, 1); will-change: transform; }
    .img-zoom:hover img { transform: scale(1.07); }

    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-6px); }
    }
    .float-anim { animation: float 3s ease-in-out infinite; }

    @keyframes shimmer {
      0% { background-position: -200% center; }
      100% { background-position: 200% center; }
    }
    .shimmer-text {
      background: linear-gradient(90deg, #006497 0%, #79bff8 50%, #006497 100%);
      background-size: 200% auto;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      animation: shimmer 3s linear infinite;
    }

    .count-up { display: inline-block; transition: all 0.3s ease; }
    
    .nav-scrolled {
      padding-top: 0.5rem !important;
      padding-bottom: 0.5rem !important;
      transition: all 0.3s ease;
    }

    .service-card { transition: transform 0.4s cubic-bezier(0.22, 1, 0.36, 1), box-shadow 0.4s ease; }
    .service-card:hover { transform: translateY(-8px); box-shadow: 0 20px 40px rgba(0, 100, 151, 0.15); }

    @keyframes pulse-ring {
      0% { box-shadow: 0 0 0 0 rgba(0, 100, 151, 0.4); }
      70% { box-shadow: 0 0 0 12px rgba(0, 100, 151, 0); }
      100% { box-shadow: 0 0 0 0 rgba(0, 100, 151, 0); }
    }
    .pulse-btn { animation: pulse-ring 2s ease-out infinite; }

    .hero-parallax { transition: transform 0.1s linear; will-change: transform; }

    .service-card, .img-zoom img, .reveal-up, .reveal-scale, .reveal-blur, .reveal-left, .reveal-right { will-change: transform, opacity; }
    html { scroll-behavior: smooth; }
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after {
        animation-duration: 0.01ms !important;
        transition-duration: 0.01ms !important;
      }
    }
    
    * {
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
    }
    img { display: block; max-width: 100%; height: auto; }
    .service-card > img { height: 100%; max-width: none; width: 100%; }
    body { overflow-x: hidden; -webkit-overflow-scrolling: touch; }
    a, button { transition: all 0.25s ease; }
  </style>
</head>
<body>

<!-- ═══════════════════════════════════════════════════════════════════════
     SECTION 1 — NAVBAR
     ═══════════════════════════════════════════════════════════════════ -->
<nav id="navbar" class="fixed top-0 left-0 w-full z-50 transition-all duration-500" style="background:transparent;">
  <div class="max-w-7xl mx-auto px-5 lg:px-8 flex items-center justify-between h-[72px]">
    <!-- Logo -->
    <a href="#" class="flex items-center gap-2 font-heading font-extrabold text-lg md:text-xl text-text-dark select-none">
      <svg class="w-8 h-8 text-primary" viewBox="0 0 32 32" fill="none"><path d="M16 2C12.5 2 10 5 10 9c0 3 1.5 5 3 6.5-2 1-5 3.5-5 7.5 0 4 3.5 7 8 7s8-3 8-7c0-4-3-6.5-5-7.5 1.5-1.5 3-3.5 3-6.5 0-4-2.5-7-6-7z" fill="currentColor" opacity="0.9"/><path d="M16 4c-2.5 0-4 2.2-4 5s1.2 4.2 3 5.5c.5.4 1 .5 1 .5s.5-.1 1-.5c1.8-1.3 3-2.7 3-5.5S18.5 4 16 4z" fill="#fff" opacity="0.35"/></svg>
      <span>Serene Dental</span>
    </a>
    <!-- Desktop nav -->
    <div class="hidden md:flex items-center gap-8">
      <a href="#services" class="nav-link relative font-heading font-medium text-sm text-text-dark hover:text-primary transition-colors">Services<span class="nav-indicator"></span></a>
      <a href="#gallery"  class="nav-link relative font-heading font-medium text-sm text-text-dark hover:text-primary transition-colors">Gallery<span class="nav-indicator"></span></a>
      <a href="#about"    class="nav-link relative font-heading font-medium text-sm text-text-dark hover:text-primary transition-colors">About Us<span class="nav-indicator"></span></a>
      <a href="#testimonials" class="nav-link relative font-heading font-medium text-sm text-text-dark hover:text-primary transition-colors">Patient Care<span class="nav-indicator"></span></a>
    </div>
    <!-- CTA -->
    <a href="#footer-cta" class="pulse-btn hidden md:inline-flex items-center gap-2 bg-primary hover:bg-primary-dark text-white font-heading font-semibold text-sm px-6 py-2.5 rounded-full transition-all duration-300 hover:shadow-lg hover:shadow-primary/25 hover:-translate-y-0.5">
      Book Appointment
    </a>
    <!-- Hamburger -->
    <button id="hamburger-btn" class="md:hidden flex flex-col justify-center items-center p-2 z-50 text-text-dark" aria-label="Menu">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
      </svg>
    </button>
  </div>
  <!-- Mobile menu -->
  <div id="mobile-menu" class="hidden md:hidden absolute top-[76px] left-1/2 -translate-x-1/2 w-[92%] bg-white rounded-2xl shadow-xl p-5 border border-gray-100/50">
    <div class="flex flex-col gap-4">
      <a href="#services" class="font-heading font-medium text-text-dark block" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Services</a>
      <a href="#gallery" class="font-heading font-medium text-text-dark block" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Gallery</a>
      <a href="#about" class="font-heading font-medium text-text-dark block" onclick="document.getElementById('mobile-menu').classList.add('hidden')">About Us</a>
      <a href="#testimonials" class="font-heading font-medium text-text-dark block" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Patient Care</a>
      <a href="#footer-cta" class="bg-primary text-white text-center font-heading font-semibold w-full py-3 rounded-full mt-2 block" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Book Appointment</a>
    </div>
  </div>
</nav>

<!-- ═══════════════════════════════════════════════════════════════════════
     SECTION 2 — HERO
     ═══════════════════════════════════════════════════════════════════ -->
<section id="hero" class="relative w-full min-h-screen flex flex-col items-center justify-center overflow-hidden">
  <!-- Background Video -->
  <video id="heroVideo" autoplay loop muted playsinline crossorigin="anonymous" class="absolute inset-0 w-full h-full object-cover z-0" poster="">
    <source src="https://ik.imagekit.io/lrigu76hy/tailark/dna-video.mp4?updatedAt=1745736251477" type="video/mp4" />
  </video>
  <!-- White gradient overlay -->
  <div class="absolute inset-0 z-[1]" style="background: linear-gradient(180deg, rgba(255,255,255,0.65) 0%, rgba(239,246,255,0.60) 50%, rgba(255,255,255,0.85) 100%);"></div>

  <!-- Hero Content -->
  <div class="relative z-10 text-center max-w-4xl mx-auto p-6 md:p-12 pt-28 md:pt-32 flex flex-col items-center">
    <!-- Trust badge -->
    <div class="reveal-blur inline-flex items-center gap-2 bg-white/70 backdrop-blur-md border border-primary/10 rounded-full px-5 py-2 text-sm font-medium text-primary mb-8 shadow-sm">
      ⭐ Trusted by 10,000+ Patients
    </div>

    <!-- H1 -->
    <h1 class="reveal-up delay-100 font-heading font-[900] leading-[1.08] mb-6 hero-gradient-text text-3xl md:text-5xl lg:text-7xl">
      Your Smile Is Our<br/>Greatest Achievement
    </h1>

    <!-- Subheading -->
    <p class="reveal-up delay-200 text-text-muted text-lg md:text-xl max-w-2xl mx-auto mb-10 leading-relaxed">
      Expert dental care combining cutting-edge technology with a gentle human touch. We treat patients like family.
    </p>

    <!-- CTAs -->
    <div class="reveal-up delay-300 flex flex-col md:flex-row items-center justify-center gap-4 mb-10 w-full">
      <a href="#footer-cta" class="w-full md:w-auto inline-flex items-center justify-center gap-2 bg-primary hover:bg-primary-dark text-white font-heading font-bold text-base px-8 py-4 rounded-full transition-all duration-400 hover:shadow-xl hover:shadow-primary/30 hover:-translate-y-1">
        Book Appointment →
      </a>
      <a href="#services" class="w-full md:w-auto inline-flex items-center justify-center gap-2 border-2 border-primary text-primary hover:bg-primary hover:text-white font-heading font-bold text-base px-8 py-4 rounded-full transition-all duration-400">
        Explore Services
      </a>
    </div>

    <!-- Trust stats -->
    <div class="trust-stats reveal-up delay-400 flex flex-col sm:flex-row flex-wrap justify-center items-center gap-4 md:gap-10 text-sm text-text-muted font-medium w-full">
      <span>✓ <span data-count="15" data-suffix="+">15+</span> Years Experience</span>
      <span class="hidden sm:inline text-gray-300">|</span>
      <span>✓ <span data-count="98" data-suffix="%">98%</span> Patient Satisfaction</span>
      <span class="hidden sm:inline text-gray-300">|</span>
      <span>✓ <span data-count="0" data-suffix="">0</span> Pain Policy</span>
    </div>
  </div>

  <!-- Hero bottom image strip -->
  <div class="relative z-10 w-full max-w-5xl mx-auto px-6 md:px-5 pb-12 mt-4">
    <div class="reveal-scale delay-200 rounded-[2rem] overflow-hidden shadow-2xl shadow-primary/10">
      <img src="public/hero-dentist.jpg" alt="Dentist with patient" class="hero-parallax w-full h-auto object-cover" style="max-height: 420px;" loading="eager" fetchpriority="high" />
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════
     SECTION 3 — SERVICES
     ═══════════════════════════════════════════════════════════════════ -->
<section id="services" class="py-24 md:py-32 bg-white">
  <div class="max-w-7xl mx-auto px-5 lg:px-8">
    <!-- Section header -->
    <div class="text-center mb-16">
      <span class="shimmer-text reveal-up inline-block text-primary font-heading font-bold text-xs tracking-[0.2em] uppercase mb-3">Our Expertise</span>
      <h2 class="reveal-up delay-100 font-heading font-extrabold text-text-dark mb-4 text-3xl md:text-5xl">World-Class Dental Services</h2>
      <p class="reveal-up delay-200 text-text-muted max-w-2xl mx-auto text-base md:text-lg leading-relaxed">
        Every treatment is designed around your comfort, your schedule, and your confidence. We don't just fix teeth — we transform lives one smile at a time.
      </p>
    </div>

    <!-- Grid Cards -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8">

      <!-- Card 1 — Teeth Whitening -->
      <div class="service-card reveal-up delay-100 group cursor-pointer transition-all duration-500">
        <img src="https://images.unsplash.com/photo-1606811841689-23dfddce3e95?w=800&auto=format&fit=crop&q=80" alt="Teeth Whitening" class="absolute inset-0 w-full h-full object-cover" loading="lazy" decoding="async" />
        <div class="absolute inset-0" style="background: linear-gradient(to top, hsla(210,70%,25%,0.92) 0%, hsla(210,70%,25%,0.45) 50%, transparent 100%);"></div>
        <div class="relative z-10 flex flex-col justify-end h-full p-6 md:p-8 text-white">
          <div class="float-anim" style="animation-delay: 0s;">
            <h3 class="font-heading font-extrabold text-2xl mb-2">Teeth Whitening</h3>
            <p class="text-white/80 text-sm leading-relaxed mb-5 max-w-sm">Professional-grade whitening that lifts years of staining in a single session. See results before you leave.</p>
            <span class="inline-flex items-center gap-2 bg-white/15 backdrop-blur-md border border-white/20 rounded-full px-5 py-2.5 text-sm font-semibold w-max transition-all duration-300 group-hover:bg-white/25">
              Learn More <span class="learn-arrow">→</span>
            </span>
          </div>
        </div>
      </div>

      <!-- Card 2 — Dental Implants -->
      <div class="service-card reveal-up delay-200 group cursor-pointer transition-all duration-500">
        <img src="https://images.unsplash.com/photo-1609840114035-3c981b782dfe?w=800&auto=format&fit=crop&q=80" alt="Dental Implants" class="absolute inset-0 w-full h-full object-cover" loading="lazy" decoding="async" />
        <div class="absolute inset-0" style="background: linear-gradient(to top, hsla(175,60%,22%,0.92) 0%, hsla(175,60%,22%,0.45) 50%, transparent 100%);"></div>
        <div class="relative z-10 flex flex-col justify-end h-full p-6 md:p-8 text-white">
          <div class="float-anim" style="animation-delay: 0.2s;">
            <h3 class="font-heading font-extrabold text-2xl mb-2">Dental Implants</h3>
            <p class="text-white/80 text-sm leading-relaxed mb-5 max-w-sm">Permanent, natural-looking teeth replacements using titanium implants that last a lifetime.</p>
            <span class="inline-flex items-center gap-2 bg-white/15 backdrop-blur-md border border-white/20 rounded-full px-5 py-2.5 text-sm font-semibold w-max transition-all duration-300 group-hover:bg-white/25">
              Learn More <span class="learn-arrow">→</span>
            </span>
          </div>
        </div>
      </div>

      <!-- Card 3 — Braces & Aligners -->
      <div class="service-card reveal-up delay-300 group cursor-pointer transition-all duration-500">
        <img src="public/braces.jpg" alt="Braces and Aligners" class="absolute inset-0 w-full h-full object-cover" loading="lazy" decoding="async" />
        <div class="absolute inset-0" style="background: linear-gradient(to top, hsla(245,55%,30%,0.92) 0%, hsla(245,55%,30%,0.45) 50%, transparent 100%);"></div>
        <div class="relative z-10 flex flex-col justify-end h-full p-6 md:p-8 text-white">
          <div class="float-anim" style="animation-delay: 0.4s;">
            <h3 class="font-heading font-extrabold text-2xl mb-2">Braces & Aligners</h3>
            <p class="text-white/80 text-sm leading-relaxed mb-5 max-w-sm">Invisible aligners and modern braces for teens and adults. Straighten with confidence, not self-consciousness.</p>
            <span class="inline-flex items-center gap-2 bg-white/15 backdrop-blur-md border border-white/20 rounded-full px-5 py-2.5 text-sm font-semibold w-max transition-all duration-300 group-hover:bg-white/25">
              Learn More <span class="learn-arrow">→</span>
            </span>
          </div>
        </div>
      </div>

      <!-- Card 4 — Pediatric Dentistry -->
      <div class="service-card reveal-up delay-400 group cursor-pointer transition-all duration-500">
        <img src="public/pediatric.jpg" alt="Pediatric Dentistry" class="absolute inset-0 w-full h-full object-cover" loading="lazy" decoding="async" />
        <div class="absolute inset-0" style="background: linear-gradient(to top, hsla(150,50%,22%,0.92) 0%, hsla(150,50%,22%,0.45) 50%, transparent 100%);"></div>
        <div class="relative z-10 flex flex-col justify-end h-full p-6 md:p-8 text-white">
          <div class="float-anim" style="animation-delay: 0.6s;">
            <h3 class="font-heading font-extrabold text-2xl mb-2">Pediatric Dentistry</h3>
            <p class="text-white/80 text-sm leading-relaxed mb-5 max-w-sm">Gentle, fun, fear-free dental visits for children. Building healthy habits that last a lifetime.</p>
            <span class="inline-flex items-center gap-2 bg-white/15 backdrop-blur-md border border-white/20 rounded-full px-5 py-2.5 text-sm font-semibold w-max transition-all duration-300 group-hover:bg-white/25">
              Learn More <span class="learn-arrow">→</span>
            </span>
          </div>
        </div>
      </div>

      <!-- Card 5 — Cosmetic Dentistry -->
      <div class="service-card reveal-up delay-500 group cursor-pointer transition-all duration-500">
        <img src="public/cosmetic.png" alt="Cosmetic Dentistry" class="absolute inset-0 w-full h-full object-cover" loading="lazy" decoding="async" />
        <div class="absolute inset-0" style="background: linear-gradient(to top, hsla(200,50%,22%,0.92) 0%, hsla(200,50%,22%,0.45) 50%, transparent 100%);"></div>
        <div class="relative z-10 flex flex-col justify-end h-full p-6 md:p-8 text-white">
          <div class="float-anim" style="animation-delay: 0.8s;">
            <h3 class="font-heading font-extrabold text-2xl mb-2">Cosmetic Dentistry</h3>
            <p class="text-white/80 text-sm leading-relaxed mb-5 max-w-sm">From porcelain veneers to simple bonding, we redesign your smile to look completely natural and flawless.</p>
            <span class="inline-flex items-center gap-2 bg-white/15 backdrop-blur-md border border-white/20 rounded-full px-5 py-2.5 text-sm font-semibold w-max transition-all duration-300 group-hover:bg-white/25">
              Learn More <span class="learn-arrow">→</span>
            </span>
          </div>
        </div>
      </div>

      <!-- Card 6 — Endodontics -->
      <div class="service-card reveal-up delay-600 group cursor-pointer transition-all duration-500">
        <img src="public/endodontics.png" alt="Root Canals" class="absolute inset-0 w-full h-full object-cover" loading="lazy" decoding="async" />
        <div class="absolute inset-0" style="background: linear-gradient(to top, hsla(30,50%,22%,0.92) 0%, hsla(30,50%,22%,0.45) 50%, transparent 100%);"></div>
        <div class="relative z-10 flex flex-col justify-end h-full p-6 md:p-8 text-white">
          <div class="float-anim" style="animation-delay: 1.0s;">
            <h3 class="font-heading font-extrabold text-2xl mb-2">Endodontics</h3>
            <p class="text-white/80 text-sm leading-relaxed mb-5 max-w-sm">Painless root canal therapy designed to save your natural tooth and instantly relieve severe toothaches.</p>
            <span class="inline-flex items-center gap-2 bg-white/15 backdrop-blur-md border border-white/20 rounded-full px-5 py-2.5 text-sm font-semibold w-max transition-all duration-300 group-hover:bg-white/25">
              Learn More <span class="learn-arrow">→</span>
            </span>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════
     SECTION 4 — DOCTOR INTRO
     ═══════════════════════════════════════════════════════════════════ -->
<section id="about" class="py-24 md:py-32 bg-soft-blue">
  <div class="max-w-7xl mx-auto px-5 lg:px-8">
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-20 items-center">
      <!-- Image -->
      <div class="relative reveal-up delay-100">
        <img src="https://images.unsplash.com/photo-1622253692010-333f2da6031d?w=800&auto=format&fit=crop&q=80" alt="Dr. Sarah Ahmed, DDS" class="w-full rounded-3xl shadow-xl object-cover" style="max-height: 600px;" loading="lazy" decoding="async" />
        <!-- Floating badge -->
        <div class="absolute top-6 right-6 bg-white/90 backdrop-blur-md rounded-2xl px-5 py-3 shadow-lg">
          <span class="block text-primary font-heading font-extrabold text-2xl leading-none">15+</span>
          <span class="text-text-muted text-xs font-medium">Years Experience</span>
        </div>
      </div>

      <!-- Text -->
      <div class="reveal-up delay-200">
        <span class="inline-block text-primary font-heading font-bold text-xs tracking-[0.2em] uppercase mb-3 text-left">Meet Your Doctor</span>
        <h2 class="font-heading font-extrabold text-text-dark mb-2" style="font-size: clamp(1.8rem, 3.5vw, 2.8rem);">Dr. Sarah Ahmed, DDS</h2>
        <p class="text-primary font-heading font-semibold text-base mb-6">Chief Dental Surgeon & Founder</p>
        <p class="text-text-muted text-base leading-relaxed mb-4">
          Dr. Ahmed completed her dental training at Johns Hopkins School of Medicine and has spent over 15 years transforming smiles across Pakistan. Her philosophy is simple: every patient deserves pain-free, dignified, and world-class dental care.
        </p>
        <p class="text-text-muted text-base leading-relaxed mb-8">
          She specializes in cosmetic dentistry, full-mouth rehabilitation, and pediatric care — and she still personally oversees every treatment plan.
        </p>

        <!-- Achievement badges -->
        <div class="flex flex-wrap gap-3 mb-10">
          <span class="inline-flex items-center gap-2 bg-white rounded-full px-4 py-2 text-sm font-medium text-text-dark shadow-sm border border-gray-100">🎓 Johns Hopkins DDS</span>
          <span class="inline-flex items-center gap-2 bg-white rounded-full px-4 py-2 text-sm font-medium text-text-dark shadow-sm border border-gray-100">🏆 Best Dentist 2023</span>
          <span class="inline-flex items-center gap-2 bg-white rounded-full px-4 py-2 text-sm font-medium text-text-dark shadow-sm border border-gray-100">💉 10,000+ Procedures</span>
        </div>

        <a href="#footer-cta" class="inline-flex items-center gap-2 bg-primary hover:bg-primary-dark text-white font-heading font-bold text-base px-8 py-4 rounded-full transition-all duration-400 hover:shadow-xl hover:shadow-primary/30 hover:-translate-y-1">
          Book with Dr. Ahmed →
        </a>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════
     SECTION 5 — GALLERY
     ═══════════════════════════════════════════════════════════════════ -->
<section id="gallery" class="py-24 md:py-32 bg-white">
  <div class="max-w-7xl mx-auto px-5 lg:px-8">
    <div class="text-center mb-16">
      <span class="shimmer-text reveal-up inline-block text-primary font-heading font-bold text-xs tracking-[0.2em] uppercase mb-3">Our Environment</span>
      <h2 class="reveal-up delay-100 font-heading font-extrabold text-text-dark" style="font-size: clamp(2rem, 4vw, 3rem);">Clinic Gallery</h2>
    </div>

    <!-- Masonry-ish grid -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5 lg:auto-rows-[280px]">
      <!-- Image 1 — Tall -->
      <div class="reveal-scale img-zoom delay-100 sm:row-span-2 rounded-[1.5rem] overflow-hidden shadow-lg">
        <img src="https://images.unsplash.com/photo-1629909613654-28e377c37b09?w=800&auto=format&fit=crop&q=80" alt="Modern waiting room" class="gallery-img aspect-[4/3] sm:aspect-[4/5] w-full h-full object-cover cursor-pointer" loading="lazy" decoding="async" />
      </div>
      <!-- Image 2 — Square -->
      <div class="reveal-scale img-zoom delay-200 rounded-[1.5rem] overflow-hidden shadow-lg">
        <img src="https://images.unsplash.com/photo-1598256989800-fe5f95da9787?w=800&auto=format&fit=crop&q=80" alt="Dentist working on patient" class="gallery-img aspect-[4/3] sm:aspect-[4/5] w-full h-full object-cover cursor-pointer" loading="lazy" decoding="async" />
      </div>
      <!-- Image 3 — Square -->
      <div class="reveal-scale img-zoom delay-300 rounded-[1.5rem] overflow-hidden shadow-lg">
        <img src="https://images.unsplash.com/photo-1607990281513-2c110a25bd8c?w=800&auto=format&fit=crop&q=80" alt="Doctor patient interaction" class="gallery-img aspect-[4/3] sm:aspect-[4/5] w-full h-full object-cover cursor-pointer" loading="lazy" decoding="async" />
      </div>
      <!-- Image 4 — Wide -->
      <div class="reveal-scale img-zoom delay-400 sm:col-span-2 rounded-[1.5rem] overflow-hidden shadow-lg">
        <img src="https://images.unsplash.com/photo-1584515933487-779824d29309?w=800&auto=format&fit=crop&q=80" alt="Modern clinic equipment" class="gallery-img aspect-[4/3] sm:aspect-[4/5] w-full h-full object-cover cursor-pointer" loading="lazy" decoding="async" />
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════
     SECTION 6 — TESTIMONIALS
     ═══════════════════════════════════════════════════════════════════ -->
<section id="testimonials" class="py-24 md:py-32 bg-soft-blue">
  <div class="max-w-7xl mx-auto px-5 lg:px-8">
    <div class="text-center mb-16 reveal-up">
      <h2 class="font-heading font-extrabold text-text-dark" style="font-size: clamp(2rem, 4vw, 3rem);">What Our Patients Say</h2>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 lg:gap-8">
      <!-- Card 1 -->
      <div class="reveal-up delay-100 bg-white rounded-3xl p-8 shadow-sm border border-gray-50 transition-all duration-400 hover:shadow-lg hover:-translate-y-1">
        <div class="text-amber-400 text-lg mb-4">⭐⭐⭐⭐⭐</div>
        <p class="text-text-dark text-base leading-relaxed mb-6 italic">"I was terrified of dentists my whole life. Dr. Ahmed changed that completely. Zero pain, maximum results."</p>
        <div class="flex items-center gap-3">
          <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center font-heading font-bold text-primary">F</div>
          <div>
            <p class="font-heading font-semibold text-sm text-text-dark">Fatima K.</p>
            <p class="text-text-muted text-xs">Karachi</p>
          </div>
        </div>
      </div>

      <!-- Card 2 -->
      <div class="reveal-up delay-200 bg-white rounded-3xl p-8 shadow-sm border border-gray-50 transition-all duration-400 hover:shadow-lg hover:-translate-y-1">
        <div class="text-amber-400 text-lg mb-4">⭐⭐⭐⭐⭐</div>
        <p class="text-text-dark text-base leading-relaxed mb-6 italic">"The implants look and feel completely natural. I can't believe this is my smile now. Worth every rupee."</p>
        <div class="flex items-center gap-3">
          <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center font-heading font-bold text-primary">A</div>
          <div>
            <p class="font-heading font-semibold text-sm text-text-dark">Ahmed R.</p>
            <p class="text-text-muted text-xs">Lahore</p>
          </div>
        </div>
      </div>

      <!-- Card 3 -->
      <div class="reveal-up delay-300 bg-white rounded-3xl p-8 shadow-sm border border-gray-50 transition-all duration-400 hover:shadow-lg hover:-translate-y-1">
        <div class="text-amber-400 text-lg mb-4">⭐⭐⭐⭐⭐</div>
        <p class="text-text-dark text-base leading-relaxed mb-6 italic">"Brought my kids here and they actually ASKED to come back. That says everything."</p>
        <div class="flex items-center gap-3">
          <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center font-heading font-bold text-primary">M</div>
          <div>
            <p class="font-heading font-semibold text-sm text-text-dark">Mariam S.</p>
            <p class="text-text-muted text-xs">Islamabad</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════
     SECTION 7 — CINEMATIC FOOTER
     ═══════════════════════════════════════════════════════════════════ -->
<footer id="footer-cta" class="relative min-h-screen bg-navy-footer text-white overflow-hidden">

  <!-- Aurora glow -->
  <div class="aurora-glow"></div>
  <!-- Grid lines -->
  <div class="grid-lines"></div>
  <!-- Giant background text -->
  <div class="absolute inset-0 flex items-center justify-center pointer-events-none select-none z-0" aria-hidden="true">
    <span class="font-heading font-[900] text-white whitespace-nowrap" style="font-size: 20vw; opacity: 0.04;">SERENE</span>
  </div>

  <!-- Marquee strip -->
  <div class="relative z-10 border-t border-b border-white/10 py-4 overflow-hidden" style="transform: rotate(-1.5deg); margin: 0 -2rem;">
    <div class="marquee-track">
      <span class="text-white/70 text-xs font-heading font-semibold uppercase tracking-[0.3em] whitespace-nowrap px-6">Trusted Care ✦ Pain-Free Guarantee ✦ Modern Equipment ✦ Family-Friendly ✦ Book Today ✦ </span>
      <span class="text-white/70 text-xs font-heading font-semibold uppercase tracking-[0.3em] whitespace-nowrap px-6">Trusted Care ✦ Pain-Free Guarantee ✦ Modern Equipment ✦ Family-Friendly ✦ Book Today ✦ </span>
      <span class="text-white/70 text-xs font-heading font-semibold uppercase tracking-[0.3em] whitespace-nowrap px-6">Trusted Care ✦ Pain-Free Guarantee ✦ Modern Equipment ✦ Family-Friendly ✦ Book Today ✦ </span>
      <span class="text-white/70 text-xs font-heading font-semibold uppercase tracking-[0.3em] whitespace-nowrap px-6">Trusted Care ✦ Pain-Free Guarantee ✦ Modern Equipment ✦ Family-Friendly ✦ Book Today ✦ </span>
    </div>
  </div>

  <!-- Center CTA -->
  <div class="relative z-10 flex flex-col items-center justify-center text-center px-5 py-28 md:py-36">
    <h2 class="font-heading font-[900] mb-10 leading-[1.05]" style="font-size: clamp(2.5rem, 7vw, 5.5rem); background: linear-gradient(180deg, #ffffff 30%, #7dc4ff 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">
      Ready For Your<br/>Best Smile?
    </h2>
    <div class="flex flex-wrap justify-center gap-5">
      <a href="tel:+923001234567" class="glass-pill inline-flex items-center gap-3 rounded-full px-8 py-4 text-white font-heading font-bold text-base">
        📞 Call Us Now
      </a>
      <a href="#" class="glass-pill inline-flex items-center gap-3 rounded-full px-8 py-4 text-white font-heading font-bold text-base">
        📅 Book Online
      </a>
    </div>
  </div>

  <!-- Footer bottom columns -->
  <div class="relative z-10 border-t border-white/10 pt-16 pb-8">
    <div class="max-w-7xl mx-auto px-5 lg:px-8">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 md:gap-12 mb-12">
        <!-- Col 1 — Logo -->
        <div class="reveal-left">
          <div class="flex items-center gap-2 mb-4">
            <svg class="w-7 h-7 text-primary" viewBox="0 0 32 32" fill="none"><path d="M16 2C12.5 2 10 5 10 9c0 3 1.5 5 3 6.5-2 1-5 3.5-5 7.5 0 4 3.5 7 8 7s8-3 8-7c0-4-3-6.5-5-7.5 1.5-1.5 3-3.5 3-6.5 0-4-2.5-7-6-7z" fill="currentColor"/></svg>
            <span class="font-heading font-extrabold text-lg">Serene Dental</span>
          </div>
          <p class="text-white/50 text-sm leading-relaxed">Premium dental care for the whole family. Your comfort, confidence, and health come first.</p>
        </div>
        <!-- Col 2 — Quick Links -->
        <div class="reveal-up delay-100">
          <h4 class="font-heading font-bold text-sm uppercase tracking-wider mb-5 text-white/80">Quick Links</h4>
          <ul class="space-y-3">
            <li><a href="#services" class="text-white/50 hover:text-primary text-sm transition-colors duration-300">Services</a></li>
            <li><a href="#about" class="text-white/50 hover:text-primary text-sm transition-colors duration-300">About Us</a></li>
            <li><a href="#gallery" class="text-white/50 hover:text-primary text-sm transition-colors duration-300">Gallery</a></li>
            <li><a href="#testimonials" class="text-white/50 hover:text-primary text-sm transition-colors duration-300">Testimonials</a></li>
          </ul>
        </div>
        <!-- Col 3 — Contact -->
        <div class="reveal-up delay-200">
          <h4 class="font-heading font-bold text-sm uppercase tracking-wider mb-5 text-white/80">Contact</h4>
          <ul class="space-y-3 text-sm text-white/50">
            <li>📍 123 Healthcare Avenue, Karachi</li>
            <li>📞 +92 300 123 4567</li>
            <li>📧 info@serenedental.pk</li>
            <li>🕐 Mon-Sat: 9AM – 8PM</li>
          </ul>
        </div>
        <!-- Col 4 — Social -->
        <div class="reveal-up delay-300">
          <h4 class="font-heading font-bold text-sm uppercase tracking-wider mb-5 text-white/80">Follow Us</h4>
          <div class="flex gap-3">
            <!-- Facebook -->
            <a href="#" class="glass-pill w-11 h-11 rounded-full flex items-center justify-center text-white/70 hover:text-white" aria-label="Facebook">
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>
            </a>
            <!-- Instagram -->
            <a href="#" class="glass-pill w-11 h-11 rounded-full flex items-center justify-center text-white/70 hover:text-white" aria-label="Instagram">
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
            </a>
            <!-- WhatsApp -->
            <a href="https://wa.me/923001234567" class="glass-pill w-11 h-11 rounded-full flex items-center justify-center text-white/70 hover:text-white" aria-label="WhatsApp">
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
            </a>
          </div>
        </div>
      </div>

      <!-- Bottom bar -->
      <div class="border-t border-white/10 pt-6 pb-safe flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-white/40">
        <p>© 2025 Serene Dental Care. All rights reserved.</p>
        <p>Crafted with <span class="heart-pulse">❤</span> by Your Agency</p>
        <div class="flex gap-5">
          <a href="#" class="hover:text-white transition-colors duration-300">Privacy Policy</a>
          <a href="#" class="hover:text-white transition-colors duration-300">Terms of Use</a>
        </div>
      </div>
    </div>
  </div>

  <!-- Back to top -->
  <a href="#hero" class="back-to-top fixed bottom-6 right-6 z-50 w-12 h-12 rounded-full bg-primary/80 backdrop-blur-md text-white flex items-center justify-center shadow-lg text-xl font-bold" aria-label="Back to top">↑</a>
</footer>

<!-- ═══════════════════════════════════════════════════════════════════════
     JAVASCRIPT
     ═══════════════════════════════════════════════════════════════════ -->
<script>
// === INTERSECTION OBSERVER FOR SCROLL ANIMATIONS ===
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
}, {
  threshold: 0.12,
  rootMargin: '0px 0px -40px 0px'
});

// Observe all animatable elements
document.querySelectorAll(
  '.reveal-up, .reveal-left, .reveal-right, .reveal-scale, .reveal-blur'
).forEach(el => observer.observe(el));

// === NAVBAR SCROLL EFFECT ===
const nav = document.querySelector('nav');
window.addEventListener('scroll', () => {
  if (window.scrollY > 50) {
    nav.classList.add('nav-scrolled');
    nav.style.background = 'rgba(255,255,255,0.92)';
  } else {
    nav.classList.remove('nav-scrolled');
    nav.style.background = 'transparent';
  }
}, { passive: true });

// === MOBILE HAMBURGER MENU ===
const hamburger = document.getElementById('hamburger-btn');
const mobileMenu = document.getElementById('mobile-menu');
if (hamburger && mobileMenu) {
  hamburger.addEventListener('click', () => {
    const isOpen = mobileMenu.classList.contains('hidden');
    mobileMenu.classList.toggle('hidden', !isOpen);
    hamburger.innerHTML = isOpen
      ? `<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
           <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
         </svg>`
      : `<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
           <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
         </svg>`;
  });
}

// === HERO PARALLAX ON SCROLL ===
const heroImg = document.querySelector('.hero-parallax');
if (heroImg) {
  window.addEventListener('scroll', () => {
    const scrolled = window.scrollY;
    if (scrolled < 700) {
      heroImg.style.transform = `translateY(${scrolled * 0.15}px)`;
    }
  }, { passive: true });
}

// === SMOOTH COUNTER ANIMATION for trust stats ===
function animateCounter(el, target, duration = 1800) {
  let start = 0;
  const step = timestamp => {
    if (!start) start = timestamp;
    const progress = Math.min((timestamp - start) / duration, 1);
    const eased = 1 - Math.pow(1 - progress, 3);
    el.textContent = Math.floor(eased * target) + (el.dataset.suffix || '');
    if (progress < 1) requestAnimationFrame(step);
  };
  requestAnimationFrame(step);
}

// Trigger counter when stats come into view
const statsObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.querySelectorAll('[data-count]').forEach(counter => {
        animateCounter(counter, parseInt(counter.dataset.count));
      });
      statsObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.5 });

const statsSection = document.querySelector('.trust-stats');
if (statsSection) statsObserver.observe(statsSection);

// Active nav link tracking
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-link');
window.addEventListener('scroll', () => {
  let current = '';
  sections.forEach(s => { if (window.scrollY >= s.offsetTop - 200) current = s.getAttribute('id'); });
  navLinks.forEach(l => {
    l.classList.remove('active');
    if (l.getAttribute('href') === '#' + current) l.classList.add('active');
  });
});

// Force video autoplay if blocked
const heroVideo = document.getElementById('heroVideo');
if (heroVideo) {
  heroVideo.play().catch(() => {
    document.addEventListener('click', () => heroVideo.play(), { once: true });
    document.addEventListener('scroll', () => heroVideo.play(), { once: true });
  });
}
</script>

</body>
</html>
```
