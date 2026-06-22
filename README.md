# Running Coach App

A personal training plan app — 24-week running + strength program, workout guides
(Strength A/B, Mobility, Pre/Post-Run stretching), nutrition reference, and gear list.
Built as an installable PWA (Progressive Web App).

## What's in here

- `index.html` — the whole app (single file, no build step)
- `manifest.json` — PWA manifest (name, icons, theme color)
- `sw.js` — service worker (enables offline support + "Add to Home Screen")
- `icon-*.png`, `favicon-*.png` — app icons in required sizes
- `netlify.toml` — Netlify deploy config + cache headers

## Deploying to Netlify

### Option A: Connect this GitHub repo (recommended — auto-deploys on every push)

1. Push this folder to a new GitHub repo named `running-coach-app`.
2. Go to [app.netlify.com](https://app.netlify.com) → **Add new site** → **Import an existing project**.
3. Choose **GitHub**, authorize if prompted, and select the `running-coach-app` repo.
4. Build settings: leave **build command** blank, set **publish directory** to `.` (it should auto-detect from `netlify.toml`).
5. Click **Deploy**. You'll get a URL like `https://random-name-123.netlify.app`.
6. Optional: in Site settings → Domain management, you can change the subdomain to something like `philliplahue-run-coach.netlify.app`, or attach a custom domain you own.

After this, every time you (or I, on your behalf) push a change to the GitHub repo, Netlify automatically rebuilds and redeploys — no manual steps.

### Option B: Drag-and-drop (quick, but no auto-redeploy)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop).
2. Drag this entire folder onto the page.
3. Done — you get a live URL immediately. To update later, drag the folder again.

## Installing on your iPhone (turns it into an app icon)

1. Open the deployed Netlify URL in **Safari** on your iPhone (must be Safari, not Chrome).
2. Tap the **Share** icon (square with an arrow pointing up).
3. Scroll down and tap **Add to Home Screen**.
4. Tap **Add**.

You'll now have an app icon on your home screen. Tapping it opens the app full-screen,
with no Safari address bar — and it'll work offline after the first load, since the
service worker caches everything locally.

## Making future edits

Since this is one HTML file, most changes (adding workouts, tweaking the calendar,
adjusting styles) just mean editing `index.html` directly and pushing to GitHub.
Netlify picks up the change and redeploys automatically within about 30–60 seconds.

If you ever change the visual design significantly, bump the `CACHE_NAME` version
string at the top of `sw.js` (e.g. `run-coach-v1` → `run-coach-v2`) so the service
worker knows to fetch fresh files instead of serving the old cached version.
