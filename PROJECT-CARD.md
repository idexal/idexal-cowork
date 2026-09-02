# PROJECT CARD — idexal-CoWork (Idexa CoWork)

**Type:** Code (production) · **Version:** 0.5.52 · **Stack:** Electron + React + Monaco + Tailwind CSS, Playwright browser automation, npm
**Identity:** ✅ Already Idexa-branded (`idexal-cowork`, private:false) — free, open-source AI super app / agentic OS (MIT, BYOK, no subscription)

## ⚠️ REPO INTEGRITY WARNING (2026-09-02)
This local copy is **INCOMPLETE**: `src/` and `scripts/` folders are **missing** (verified: `npm run setup` fails on `scripts/setup.mjs`; the `npm run build` chain cannot run).
Present & healthy: `package.json` (v0.5.52), `tsconfig*.json`, `vite.config`, `node_modules`, `dist/` (previous FULL build), `connectors/`, `deploy/`, `docs/`, `native/`, `mobile/`, `bin/`, `build/`, `assets/`, `data/`.
**Action needed:** re-copy the FULL repo from the source machine (`C:\Users\LahbabiCode\Desktop\idexla\idexal-CoWork`) — especially `src/` + `scripts/` — then re-run `npm install && npm run setup && npm run build && npm run package`.

## How it runs TODAY (workaround — verified working path)
The previous build inside `dist/` is complete (`main: dist/electron/electron/main.js`, `dist/renderer/index.html` present, 225 renderer files):
```powershell
# detached helper (log: Scripts/_build-logs/cowork-app.log):
Start-Process powershell -WindowStyle Hidden -ArgumentList '-NoProfile','-ExecutionPolicy','Bypass','-File','c:\Users\idexal\Desktop\idexal\Scripts\_build\run-cowork-app.ps1'
# manual equivalent:
cd c:\Users\idexal\Desktop\idexal\idexal-CoWork ; npx electron .
```

## Original pipeline (after source re-sync)
```powershell
npm install && npm run setup && npm run build && npm run package   # → dist\*.exe (NSIS)
```
Key scripts: `setup` → `node scripts/setup.mjs` · `package` → `build:with-numbat` + `scripts/run_electron_builder.mjs` · `dev` → `scripts/dev_with_logs.mjs` · tests: `npm run test` (vitest, 4,900+)

## Docker (alternative)
`docker-compose up --build` → port **18789** (deploy/ is present)

## Facts
- Contact cowork@idexal.com · Site cowork.idexa.com · Repo github.com/idexal/idexal-cowork
- Windows packaging needs VS Build Tools + Python 3 (Python 3.14 present)
