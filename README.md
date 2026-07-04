# Echo Maik Studio (EMS) — Portfolio Website

> Echoes of a maker. Vibe coding all the way.

---

## What is this?

Personal portfolio for **Echo Maik Studio (EMS)** — Maik, an independent maker based in Berlin.  
A single-page site showcasing AI-native apps, mobile products, web tools — and games.

Built with zero frameworks. Pure HTML, CSS, JS — shipped via Railway.

**Brand:** the wordmark is **echo_maik_studio** (with the **"ai"** in *maik* in accent green `#4ade80` as an easter egg); **EMS** is used standalone. Target domain `echomaik.studio` (not yet purchased) · `echomaikstudio@gmail.com` · Instagram [@echomaikstudio](https://instagram.com/echomaikstudio).

---

## Stack

| Layer | Tech |
|---|---|
| Frontend | Vanilla HTML · CSS · JS |
| Fonts | UI: Bebas Neue · DM Mono · DM Sans — Diary: Caveat · Space Mono · Plus Jakarta Sans — Dream CV: Share Tech Mono · Rajdhani |
| Hosting | Railway (static, `serve`) |
| Design | Dark grain aesthetic · custom cursor · modal system · animated SVG graffiti hero · 3D flipbook |

---

## Projects featured

| # | Name | Type | Modal |
|---|---|---|---|
| 001 | **Planta Sano** | Mobile · AI Vision · Claude | Garden Tech — phone mockup + video + screenshot slider |
| 002 | **CiaoLead** | Web · SaaS · B2B | — |
| 003 | **Project Anchor** | N8N · React Native · ElevenLabs | Annie's Diary — 3D flipbook (5 leaves · page-flip · ← →) |
| 004 | **Jonny in the Jungle** | Game · Pixel Art · Pygame | Urban Jungle — screenshots + download guide |
| 005 | **Dream-CV** | Web · AI · Claude · Live | Dream CV — live "tailoring" reel: JD keywords light up → redacted CV builds → match-score gauge |

> Row titles are uniform grey `#c8c8c8` (lighten to off-white on hover); tags are all acid green `#6eff2a`. Each project's own colour lives inside its modal.

---

## Session log — 12.06.2026

Full build + deployment session. Starting from a raw HTML file, shipped in one day:

### 🚀 Railway deployment
- Added `package.json` with `serve` as static server
- Added `railway.json` with start command bound to `0.0.0.0:$PORT`
- Added `.gitignore` for `node_modules`
- Renamed `ems-studio-portfolio.html` → `index.html` so Railway serves the homepage correctly

### 🎮 Project 004 — Jonny in the Jungle
- **Urban Jungle modal** — opens on row click, closes on X / backdrop / Escape
- Two tabs: `In-Game Visuals` (6 screenshots, 4:3 no-crop, original CDN resolution) and `Download & Play` (Steam-style install guide, Windows-only badge)
- Engine tag corrected: Unity → **Pygame**
- Screenshots sourced from itch.io at original resolution

### 🌿 Project 001 — Planta Sano (formerly Planty)
- Renamed Planty → **Planta Sano** across the entire page
- **Garden Tech modal** — narrow phone-shaped layout (max 420px), green `#4ade80` accent, solid top stripe
- CSS phone frame with `<video autoplay loop muted playsinline>` at exact 9:16 ratio
- Horizontal scroll-snap carousel of 4 app screenshots (no lazy loading — loaded eagerly for instant display inside hidden modal)
- Video triggered via `video.play()` on modal open (browser blocks autoplay on hidden elements)
- Feature grid 2×2 with green accents
- Muted App Store / Google Play "Coming Soon" badge pills
- **Lightbox** — click any carousel image to zoom full-screen, close with X / backdrop / Escape

### ✦ Design upgrades
- Section count: `003 works` → `004 works`
- Cursor ring **fills** on project row hover (replaces emoji preview)
- Each project modal has a distinct visual language (Urban Jungle vs Garden Tech)
- Tab label: `Screenshots` → `In-Game Visuals`

---

## Session log — 17.06.2026

Polish pass on the Planta Sano modal + full mobile responsiveness.

### 🖼️ Planta Sano screenshot slider
- Replaced the flat carousel with a **second phone frame** holding the 4 app screenshots in a swipeable slider
- Design nav controls: circular `←` / `→` buttons (disabled at start/end) + clickable dot indicators
- Slider track uses a CSS `translateX` transition; lightbox still available on image click
- Bumped phone frame to **300px** and modal to **520px** on desktop so screenshots read sharply
- Screenshots shown with `object-fit: contain` + centered — full screen visible, no cropping (applied on **all** viewports)

### 📱 Mobile responsiveness (`@media max-width: 768px`)
The site previously had **no** mobile breakpoint — all layouts were desktop-fixed. Added a single mobile block (desktop styles untouched):
- **Nav** — hides the "Available for work" status badge, tightens padding/links (was overflowing)
- **Custom cursor** — disabled on touch (it was floating stuck at `0,0`), default cursors restored
- **Hero** — hides the 380px decorative phone (overflowed), rescales title, drops the vertical "Scroll" label
- **Counter row** — `4 cols → 2×2` grid with corrected borders
- **Project rows** — the fixed `80px/1fr/200px/160px` grid (~536px min) restructured into a stacked `grid-template-areas` layout
- **About** — two columns stacked to one; right border → bottom border
- **Footer** — logo + copyright stacked vertically

---

## Session log — 21.06.2026

Two features in one day: the Project Anchor diary modal and an animated graffiti hero.

### ⚓ Project 003 — Project Anchor (Annie's Diary)
- **Flipbook diary modal** — opens on row click, closes on X / backdrop / Escape (same pattern as the other modals)
- A real 3D page-flip "book": 5 leaves, each with a front + back face, driven by `perspective` + `transform-style: preserve-3d` + `backface-visibility`
- Flip with the prev / next buttons **or** the `←` `→` arrow keys — the key listener is scoped to the open modal only, so it never hijacks the rest of the page
- Resets to page 1 every time it opens
- Distinct warm palette (cream pages on green `#5AA17E` covers) — kept isolated from the dark site theme by shadowing `--accent` on the modal
- Fonts added: **Caveat · Space Mono · Plus Jakarta Sans**
- Mobile: the wide two-page spread scales down (JS-computed `--pa-scale`) so the whole book fits the phone, controls stay tappable below

### 🎨 Hero — animated "EMS" graffiti
- Replaced the faint ghost "EMS" text with an animated **smoked-brick graffiti** (smoke drift + gleam, CSS animations inside the SVG)
- Sits on the right, bleeds off the right edge; left-edge `mask-image` fade keeps the headline + subtitle clean
- Removed the decorative robot SVG — the graffiti owns the right side
- **Interactive spray-paint** — a spray can draws "EMS" left→right on a loop (clip-path width reveal synced to the can), then restarts from zero
- Runs **only when the user is "in front of the site"**: hero on-screen (`IntersectionObserver`) **and** tab visible (Page Visibility API). Off-screen / hidden tab → static full EMS, no motion. Respects `prefers-reduced-motion`
- Inlined the SVG into `index.html` so the draw can be JS-driven (an `<img>` can't be)
- Mobile: EMS becomes a full-width **banner above** the "Vibe Coding" headline

---

## Session log — 22.06.2026

Row 003 recolor + a mobile-only diary fix.

### ⚓ Project 003 — row recolor
- Homepage row 003: the **Project Anchor** name tinted dusty terracotta-rose (`#d99c84`)
- Tags swapped `Mobile / AI Agent / Wellness` → **N8N · React Native · ElevenLabs**, colored green like the other projects
- The diary/modal palette was left untouched

### 🩹 Diary — mobile 3D face bleed-through fix
On iOS Safari the flipbook's front and back faces rendered coplanar, so text appeared mirrored / doubled. Fixed (scoped to `@media max-width: 768px`, desktop untouched):
- Added `-webkit-` prefixes for `transform-style: preserve-3d` and `backface-visibility: hidden` (iOS Safari needs them)
- Depth-separated the faces so the opaque front always occludes the back: front `translateZ(30px)`, back `rotateY(180deg) translateZ(30px)`
- Set the modal's open state to `transform: none` so the wrapper no longer flattens the 3D context
- Kept `perspective` + `preserve-3d` alive at every breakpoint

---

## Session log — 04.07.2026

Rebrand to **Echo Maik Studio** + a unified project-row colour system.

### 🏷️ Rebrand — ems_studio → Echo Maik Studio
- Wordmark `echo_maik_studio` in the nav + footer, with the **"ai"** in *maik* highlighted green `#4ade80` (easter egg); `EMS` used standalone in the eyebrow, About and footer
- Hero headline `Vibe / Coding.` → **`Echoes / of a maker`** (Bebas Neue, solid + outline) — reduced the title clamp (`60 / 8.2vw / 106px`) so it no longer clashes with the EMS graffiti
- Subtitle now carries the **"vibe coding"** line; hero eyebrow → `EMS · Est. 2024 · Berlin, DE`
- Contact: email → `echomaikstudio@gmail.com`; removed the X link, added **Instagram** `@echomaikstudio`
- `<title>` → `Echo Maik Studio — Maik`; About · Studio value → `EMS`
- Graffiti: removed the `UNDERGROUND` tag (artwork, smoke, `ems · berlin` tag + animation untouched)

### 🎨 Project rows — unified colours
- All four project titles render **uniform grey `#c8c8c8`**, lightening to off-white on hover (dropped the per-project inline title colours + the `--game` title rules — supersedes the terracotta `003` name)
- All tags now **acid green `#6eff2a`** with a green border, on every project
- Per-project colour stays inside each project's modal (diary terracotta, Garden Tech green, Urban Jungle acid green)

### 🧬 Project 005 — Dream CV
- New **005 "Dream-CV"** row (built with my `project-row` classes) opening a self-contained **live-app modal**, lifted **verbatim** from a Claude Design export — its own neon-green micro-aesthetic (Share Tech Mono + Rajdhani, film grain, glow)
- **"Tailoring" reel** on open: the job description types in → keywords light up → a data spine pulses → the redacted CV builds section by section → matched skills glow → a match-score gauge + factor bars animate in. The role chips (Product Designer / Growth Lead / Frontend Engineer) re-run it
- The CV is an abstract **"redacted"** document (blurred bars, never real data) — no screenshots
- Opens on row click, closes on ✕ / backdrop / Escape, locks body scroll; only change to the lift was `z-index 900 → 1000` to match the other modals; `≤600px` collapses to a single column
- "Try it live" → the real app on Railway. The design reference `_dream-cv-modal.html` is **git-ignored** — never deployed

---

## Asset files (repo root)

| File | Size | Used in |
|---|---|---|
| `planta-sano-demo.mp4` | ~900KB | Planta Sano modal — phone video loop |
| `planta-sano-notebook.png` | ~145KB | Planta Sano slider |
| `planta-sano-diary.png` | ~160KB | Planta Sano slider |
| `planta-sano-progress.png` | ~51KB | Planta Sano slider |
| `planta-sano-care.png` | ~127KB | Planta Sano slider |
| `project-anchor-avatar.png` | ~165KB | Project Anchor diary — cover + journal avatar |
| `project-anchor-chat.png` | ~505KB | Project Anchor diary — chat / about screens |
| `project-anchor-voice.png` | ~532KB | Project Anchor diary — voice screen |
| `ems-hero-graffiti.svg` | ~4KB | Original hero graffiti source (now inlined into `index.html`) |

---

## Local dev

```bash
npm install
npm start
# → http://localhost:3000
```

---

## Deployment

Push to `main` → Railway auto-redeploys.  
No build step. No bundler. Just `serve .`

---

<sub>Echo Maik Studio · EMS · Berlin · 2026</sub>
