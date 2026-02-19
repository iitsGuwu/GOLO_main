# GOLO One-Pager

A single-page SvelteKit site with **horizontal scrolling** (scroll right-to-left), a **hero** with a spinning 3D cube and blueprint-style labels, plus filler **data** and **charts** sections.

## Run locally

```bash
npm install
npm run dev
```

Open [http://localhost:5173](http://localhost:5173). Use **scroll wheel** or **drag** horizontally to move between sections.

## Build

```bash
npm run build
npm run preview
```

## Stack

- SvelteKit
- Svelte 5
- Vite 5
- CSS (no chart libs; bar/line/donut are custom SVG/CSS)

## Push to GitHub

1. Create a new repository on GitHub named **GOLO_main** (no README, no .gitignore).
2. Then run:
   ```bash
   git remote set-url origin https://github.com/YOUR_USERNAME/GOLO_main.git
   git push -u origin main
   ```
   (Replace `YOUR_USERNAME` with your GitHub username. Remote is already set to `iitsGuwu` if that's you.)
