# ems_studio — Portfolio Website

> Solo. From spark to ship.

---

## What is this?

Personal portfolio for **ems_studio** (Maik), an independent maker based in Berlin.  
A single-page site showcasing AI-native apps, mobile products, web tools — and games.

Built with zero frameworks. Pure HTML, CSS, JS — shipped via Railway.

---

## Stack

| Layer | Tech |
|---|---|
| Frontend | Vanilla HTML · CSS · JS |
| Fonts | Bebas Neue · DM Mono · DM Sans |
| Hosting | Railway (static, `serve`) |
| Design | Dark grain aesthetic · custom cursor · modal system |

---

## Projects featured

| # | Name | Type | Modal |
|---|---|---|---|
| 001 | **Planta Sano** | Mobile · AI Vision · Claude | Garden Tech — phone mockup + video + carousel |
| 002 | **CiaoLead** | Web · SaaS · B2B | — |
| 003 | **Project Anchor** | Mobile · AI Agent · Wellness | — |
| 004 | **Jonny in the Jungle** | Game · Pixel Art · Pygame | Urban Jungle — screenshots + download guide |

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

## Asset files (repo root)

| File | Size | Used in |
|---|---|---|
| `planta-sano-demo.mp4` | ~900KB | Planta Sano modal — phone video loop |
| `planta-sano-notebook.png` | ~145KB | Planta Sano carousel |
| `planta-sano-diary.png` | ~160KB | Planta Sano carousel |
| `planta-sano-progress.png` | ~51KB | Planta Sano carousel |
| `planta-sano-care.png` | ~127KB | Planta Sano carousel |

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

<sub>ems_studio · Berlin · 2026</sub>
