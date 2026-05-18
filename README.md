# Who Does Your Browser Think You Are?

**[Try it live](https://chettobrey.github.io/psycho-profile/)**

An interactive demo that shows how ad networks profile you from passive browser signals, before you click anything. Runs entirely in your browser. No backend, no tracking, no accounts.

## What it does

1. Collects device signals (OS, browser, screen, GPU, CPU, RAM)
2. Fingerprints the browser (canvas, WebGL, audio context, fonts)
3. Geolocates the IP via `ipwho.is` (one anonymous request)
4. Detects behavioral patterns (time of day, mouse entropy, dwell time)
5. Infers demographics, psychographics, and interest categories
6. Simulates ad creatives that would be served to the inferred profile
7. Explains the reasoning and uncertainty behind every inference

## Privacy

- Nothing is stored. No cookies, no localStorage writes, no accounts.
- The only external call is a single GET to `https://ipwho.is/` for IP geolocation. That request carries your IP (obviously) but no other identifying information.
- No analytics, no telemetry, no third-party scripts.
- View source to verify.

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
