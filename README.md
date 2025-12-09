```markdown
# Frontend (Vite)  Build & Dev

This folder contains a minimal Vite configuration and placeholder frontend entry files used by the Laravel app. The README documents how to run the frontend build and development workflow locally on Windows (PowerShell).

Prerequisites
- Node.js (LTS) installed and `npm` available. On Windows the Node installer adds `node` and `npm` to `C:\Program Files\nodejs`.
- PHP (for running the Laravel app) if you want to load pages that consume the Vite-built assets.

Install dependencies
```powershell
cd 'c:\Users\eburr\Downloads\CoinCentral Digital Banking Pro\codecanyon-33575024-viserbank-digital-banking-system\Files\core'
npm install
```

Production build
```powershell
& 'C:\Program Files\nodejs\node.exe' node_modules/vite/bin/vite.js build
# or equivalently
npm run build
```

Development (HMR)
```powershell
& 'C:\Program Files\nodejs\node.exe' node_modules/vite/bin/vite.js --host
# In a separate terminal (to serve Laravel pages):
php artisan serve
# Open your app pages in the browser; Vite will serve assets from http://localhost:5173/
```

Notes
- `vite.config.js` in this folder uses `laravel-vite-plugin` and registers the inputs
  `resources/js/app.js` and `resources/css/app.css` so the plugin can build assets.
- `laravel-vite-plugin@1.3.0` currently lists peer dependency `vite@^5 || ^6`. Vite was
  upgraded to v7 in this branch to address a security advisory; the plugin currently
  works in our tests but monitor for compatibility issues and update the plugin if
  a compatible release is available.

---

This PR
- Adds Vite config and minimal frontend entry files, enabling Vite build and dev workflows.
- PR: https://github.com/Starr2-lab/studious-octo-memory/pull/1

How I tested
- Installed dependencies: `npm install` in `Files/core`.
- Production build: `node node_modules/vite/bin/vite.js build`  `public/build` produced.
- Dev server: `node node_modules/vite/bin/vite.js --host`  HMR served at `http://localhost:5173/` and assets reloaded on file change.

Changelog
- Added: `vite.config.js`, `resources/js/app.js`, `resources/css/app.css`, `Files/core/README.md` (this file).

If you want additional details (CI notes, required status checks, or example HTML templates to include the Vite tags), tell me and I will add them.

```
