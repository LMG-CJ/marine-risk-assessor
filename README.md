# Marine Risk &amp; Premium Assessor

A lightweight, single-file desktop tool for **marine cargo-vessel risk triage and indicative premium** — built for a specialist Lloyd's marine broker workflow.

Type an IMO number, the vessel particulars auto-fill, and you get a transparent risk score, an indicative premium breakdown, and a live verification panel — in seconds rather than the usual manual lookup across multiple sources.

> **Demonstration prototype.** All premiums are **illustrative only** — produced by a transparent demonstration rating model, **not a quotation or contract of insurance**. The IMO auto-fill in this build runs against a small **demo dataset** (mock vessels), not a live registry. Reference lists (flag tiers, IACS, ICC, IMDG, JWC war-risk areas) are current as at the dates shown in-app and must be re-verified at point of quote. This build is a working prototype and is not an official Lilley Plummer Risks system.

## What it does

- **Dropdown risk checklist** across Vessel, Flag &amp; Class, Cargo, Trading/Route, Cover, and Loss History.
- **Live risk index (0–100) and band** (Preferred → Refer/Decline) with hard underwriting gates (sanctions, class suspended, IMDG Class 1/7).
- **Transparent indicative premium** — rate-on-value × verified factor multipliers, separate war-risk line, **UK IPT-exempt** (commercial marine), with a full breakdown.
- **IMO auto-fill** — type a 7-digit IMO to populate vessel particulars (demo dataset).
- **Live vessel intelligence panel** — real deep-links to MarineTraffic, VesselFinder, Equasis, Paris MoU, IACS, OpenSanctions / OFAC / FCDO; an interactive war-zone map; and a live FX conversion of the sum insured.
- **Saved portfolio** (browser-local) — re-open any vessel to amend it and watch the risk and premium move.
- **Print / export** a one-page indicative summary.

## Run it

It's a single self-contained file — just open `index.html` in any modern browser. No install, no build, works offline (only the map basemap tiles and live FX need a connection).

To serve locally instead:

```bash
npx serve .        # or: python3 -m http.server 8080
```

## Tech

- One `index.html`, vanilla JS, no framework, no build step.
- [Leaflet](https://leafletjs.com/) inlined for the offline-capable war-zone map.
- Keyless live calls only (FX via frankfurter.app); everything degrades gracefully offline.

## Live-data roadmap (not in this build)

To make the IMO auto-fill and sanctions screening genuinely live, the plan is one thin **Cloudflare Worker** proxy in front of:

- **Datalastic** — vessel particulars + position by IMO (~€199/mo).
- **OFAC / EU FSF / UK FCDO** sanctions lists (free, server-side).
- **Open-Meteo** marine weather (~$29/mo commercial).

The single `index.html` stays the entire front-end; a `DEMO_MODE` flag keeps this file working offline.

---

© Demonstration prototype. Rating model and pricing are illustrative.
