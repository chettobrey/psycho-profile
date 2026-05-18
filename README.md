# Who Does Your Browser Think You Are?

An interactive single-page demo that shows how ad networks profile users from passive browser signals. Runs entirely in the browser. No backend. No tracking.

## What it does

1. Collects device signals (OS, browser, screen, GPU, CPU, RAM)
2. Fingerprints the browser (canvas, WebGL, audio context, fonts)
3. Geolocates the IP via `ipwho.is` (one anonymous request)
4. Detects behavioral patterns (time of day, mouse entropy, dwell time)
5. Infers demographics, psychographics, and interest categories
6. Simulates ad creatives that would be served to the inferred profile
7. Explains the reasoning and uncertainty behind every inference

## Privacy guarantees

- Nothing is stored. No cookies, no localStorage writes, no accounts.
- The only external call is a single GET to `https://ipwho.is/` for IP geolocation. That request carries your IP (obviously) but no other identifying information.
- No analytics, no telemetry, no third-party scripts.

## Running locally on a Mac

**Option 1: Just open the file (easiest)**

Double-click `index.html` in Finder, or from Terminal:

```bash
open index.html
```

That's it. No install, no server, no build step. It opens in your default browser directly from the filesystem. All the fingerprinting APIs and the IP geolocation request work fine from a `file://` URL.

**Option 2: Serve it (if you want a real URL)**

If you'd rather hit `http://localhost:8080` instead of a `file://` path:

```bash
# Python (already on every Mac)
python3 -m http.server 8080

# Then open http://localhost:8080 in your browser
```

Or if you have Node installed:

```bash
npx serve .
```

Either way, run the command from the `psycho-profile/` directory.

## Deploying

Drop `index.html` on any static host: Vercel, Netlify, GitHub Pages, S3, Cloudflare Pages. No build step.

## What's collected

| Category | Signals |
|---|---|
| Device | UA string, OS, browser, screen resolution, DPR, viewport, touch points, CPU cores, RAM, platform |
| Network | IP, city, region, ISP, ASN, timezone (browser + IP), referrer, languages, connection type |
| Fingerprinting | Canvas hash, WebGL GPU renderer/vendor, audio context hash, installed fonts (20 tested) |
| Behavioral | Time of day, dwell before scan, mouse movement count and entropy, scroll events, click count |

## Limitations and intentional honesty

Every inference section includes a "How wrong might this be?" note. The goal is to show how thin the signal chain is, not to build a reliable profiler. Real ad networks aggregate these signals across millions of sessions and cross-reference with purchase data, browsing history, and data broker files. This demo has none of that.

The Big Five psychographic guesses are labeled as parlor tricks because they are.
