# ems_studio — Portfolio Website

> Solo. From spark to ship.

---

## What is this?

Personal portfolio for **ems_studio** (Maik), an independent maker based in Berlin.  
A single-page site showcasing AI-native apps, mobile products, web tools — and now, games.

Built with zero frameworks. Pure HTML, CSS, JS — shipped via Railway.

---

## Stack

| Layer | Tech |
|---|---|
| Frontend | Vanilla HTML · CSS · JS |
| Fonts | Bebas Neue · DM Mono · DM Sans |
| Hosting | Railway (static, `serve`) |
| Design | Dark grain aesthetic · custom cursor · scroll animations |

---

## Projects featured

| # | Name | Type |
|---|---|---|
| 001 | **Planty** | Mobile · AI Vision · Claude |
| 002 | **CiaoLead** | Web · SaaS · B2B |
| 003 | **Project Anchor** | Mobile · AI Agent · Wellness |
| 004 | **Jonny in the Jungle** | Game · Pixel Art · Pygame |

---

## Session log — 12.06.2025

Full build + deployment session. Starting from a raw HTML file, we shipped:

### 🚀 Railway deployment
- Added `package.json` with `serve` as static server
- Added `railway.json` with start command bound to `0.0.0.0:$PORT`
- Added `.gitignore` for `node_modules`
- Renamed `ems-studio-portfolio.html` → `index.html` so Railway serves the homepage correctly

### 🎮 Project 004 — Jonny in the Jungle
Added a new project entry with a full custom modal experience:

- **Urban Jungle modal** — opens on click of the project row, closes on X / backdrop click / Escape
- **Two tabs inside the modal:**
  - `In-Game Visuals` — 6 screenshots at original resolution, 4:3 layout, no cropping (`object-fit: contain`)
  - `Download & Play` — step-by-step install guide (Steam demo style), Windows-only badge, no Python required note
- **Download on itch.io** CTA button
- Screenshots sourced directly from [echo-maik-games.itch.io/jonny-in-the-jungle](https://echo-maik-games.itch.io/jonny-in-the-jungle) at original CDN resolution
- Engine tag corrected: Unity → **Pygame**

### ✦ Design upgrades
- Section count badge updated: `003 works` → `004 works`
- Cursor ring now **fills** on project row hover (professional, no emoji preview)
- Urban Jungle modal aesthetic: dark concrete palette, acid green (#6eff2a) accents, Bebas Neue titles, Space Mono body, zebra stripe borders
- Tab label: `Screenshots` → `In-Game Visuals`
- Old flat gallery section removed in favour of the modal

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
