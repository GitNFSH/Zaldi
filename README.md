<!doctype html>

<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Zain — Portfolio</title>
  <!-- Tailwind Play CDN for quick prototyping -->
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    /* Background grid */
    body {
      background: linear-gradient(180deg, #05233a 0%, #04243b 100%);
    }.grid-bg::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
  background-size: 40px 40px, 40px 40px;
  pointer-events: none;
  z-index: 0;
}

/* neon effect */
.neon {
  text-shadow: 0 2px 0 rgba(0,0,0,0.6),
               0 0 8px rgba(56, 211, 255, 0.25),
               0 0 18px rgba(56, 211, 255, 0.18),
               0 0 36px rgba(56, 211, 255, 0.12);
}

/* translucent pill buttons */
.pill {
  background: rgba(255,255,255,0.03);
  backdrop-filter: blur(4px);
  border: 1px solid rgba(255,255,255,0.06);
}

/* play button */
.play-btn {
  width: 140px;
  height: 140px;
  border-radius: 50%;
  background: rgba(255,255,255,0.03);
  display:flex;
  align-items:center;
  justify-content:center;
  border: 1px solid rgba(255,255,255,0.06);
  cursor: pointer;
}

/* hanging card */
.hanging-card {
  width: 260px;
  transform: rotate(-10deg);
  box-shadow: 0 30px 60px rgba(2,6,23,0.6);
  border-radius: 12px;
  overflow: hidden;
  border: 1px solid rgba(255,255,255,0.06);
  background: linear-gradient(180deg,#0b3a52,#083147);
}

@media (max-width: 900px) {
  .hanging-card { display: none; }
}

  </style>
</head>
<body class="min-h-screen text-slate-200 relative overflow-hidden">
  <div class="grid-bg absolute inset-0" aria-hidden></div>  <!-- Top Navigation -->  <header class="relative z-20">
    <nav class="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 rounded bg-cyan-500 flex items-center justify-center font-bold">Z</div>
        <div class="hidden sm:block">
          <div class="text-sm font-semibold">Zain Ahmad Fahrezi</div>
          <div class="text-xs text-slate-400">Front End Developer</div>
        </div>
      </div>
      <ul class="flex items-center gap-6 text-sm">
        <li class="hover:text-white cursor-pointer">Home</li>
        <li class="hover:text-white cursor-pointer">About</li>
        <li class="hover:text-white cursor-pointer">Project</li>
        <li class="hover:text-white cursor-pointer">Contact</li>
      </ul>
    </nav>
  </header>  <!-- Hero -->  <main class="relative z-10">
    <section class="max-w-6xl mx-auto px-6 py-20 grid grid-cols-12 gap-8 items-center">
      <!-- Left: text -->
      <div class="col-span-12 lg:col-span-7">
        <div class="inline-flex items-center gap-3 mb-6">
          <span class="pill px-3 py-1 rounded-full text-xs">✨ Innovation For The Future</span>
        </div><h1 class="text-5xl md:text-6xl lg:text-7xl font-extrabold neon leading-tight text-cyan-300">WELCOME TO MY<br/>PORTFOLIO</h1>
    <h2 class="mt-4 text-2xl text-slate-300 font-medium">Front End Developer</h2>

    <p class="mt-6 text-slate-400 max-w-xl">I craft responsive and visually engaging websites using React, Tailwind CSS, and modern web technologies. Focus on performance and delightful UI.</p>

    <div class="mt-6 flex gap-3 flex-wrap">
      <button class="pill px-4 py-2 rounded-full text-sm">React</button>
      <button class="pill px-4 py-2 rounded-full text-sm">Javascript</button>
      <button class="pill px-4 py-2 rounded-full text-sm">Node.js</button>
      <button class="pill px-4 py-2 rounded-full text-sm">Tailwind</button>
    </div>

    <div class="mt-6 flex items-center gap-4">
      <!-- social icons -->
      <a aria-label="Github" href="#" class="p-2 rounded-full pill inline-flex"><svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" viewBox="0 0 24 24" fill="currentColor"><path d="M12 .5C5.65.5.5 5.65.5 12c0 5.09 3.29 9.41 7.86 10.94.58.11.79-.25.79-.56 0-.28-.01-1.02-.02-2-3.2.7-3.88-1.54-3.88-1.54-.53-1.34-1.3-1.7-1.3-1.7-1.07-.73.08-.72.08-.72 1.18.08 1.8 1.22 1.8 1.22 1.05 1.8 2.76 1.28 3.43.98.11-.76.41-1.28.75-1.57-2.56-.29-5.26-1.28-5.26-5.7 0-1.26.45-2.28 1.19-3.09-.12-.29-.52-1.47.11-3.06 0 0 .97-.31 3.18 1.18.92-.26 1.92-.39 2.91-.39s1.99.13 2.91.39c2.21-1.5 3.18-1.18 3.18-1.18.63 1.59.23 2.77.11 3.06.74.81 1.19 1.83 1.19 3.09 0 4.43-2.71 5.4-5.29 5.69.42.36.8 1.07.8 2.16 0 1.56-.01 2.82-.01 3.21 0 .31.21.68.8.56C20.71 21.41 24 17.09 24 12c0-6.35-5.15-11.5-12-11.5z"/></svg></a>
      <a aria-label="Instagram" href="#" class="p-2 rounded-full pill inline-flex"><svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" viewBox="0 0 24 24" fill="currentColor"><path d="M7 2C4.79 2 3 3.79 3 6v12c0 2.21 1.79 4 4 4h10c2.21 0 4-1.79 4-4V6c0-2.21-1.79-4-4-4H7zm5 5.5A4.5 4.5 0 1 1 7.5 12 4.5 4.5 0 0 1 12 7.5zm4.8-.25a1.05 1.05 0 1 1 0 2.1 1.05 1.05 0 0 1 0-2.1z"/></svg></a>
      <a aria-label="LinkedIn" href="#" class="p-2 rounded-full pill inline-flex"><svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" viewBox="0 0 24 24" fill="currentColor"><path d="M4.98 3.5C4.98 4.88 3.9 6 2.5 6S0 4.88 0 3.5 1.08 1 2.5 1 4.98 2.12 4.98 3.5zM.5 8.5h4V24h-4zM8.5 8.5h3.84v2.14h.05c.54-1.02 1.86-2.14 3.83-2.14 4.1 0 4.86 2.7 4.86 6.21V24h-4V14.9c0-2.17-.04-4.96-3.02-4.96-3.02 0-3.49 2.36-3.49 4.78V24h-4z"/></svg></a>
    </div>
  </div>

  <!-- Center: play button (overlay) -->
  <div class="col-span-12 lg:col-span-1 flex justify-center lg:justify-start z-20">
    <div class="play-btn" onclick="openDemo()" title="Play Demo">
      <svg width="48" height="48" viewBox="0 0 24 24" fill="rgba(255,255,255,0.12)" xmlns="http://www.w3.org/2000/svg"><path d="M8 5v14l11-7z"/></svg>
    </div>
  </div>

  <!-- Right: hanging badge/card -->
  <div class="col-span-12 lg:col-span-4 relative flex justify-center lg:justify-end">
    <div class="hanging-card relative">
      <img src="https://via.placeholder.com/260x380.png?text=ZAIN+AHMAD" alt="badge" class="w-full h-auto block" />
      <div class="p-3 text-sm text-slate-200">
        <div class="font-bold">ZAIN AHMAD F</div>
        <div class="text-xs text-slate-400">Front End Developer</div>
      </div>
    </div>
  </div>
</section>

  </main>  <script>
    function openDemo(){
      // contoh aksi: buka modal atau link video
      alert('Play demo - ganti dengan modal video atau link YouTube.');
    }
  </script></body>
</html>
