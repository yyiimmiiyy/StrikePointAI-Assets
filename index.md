# StrikePoint AI — Documentation Index

**Last Updated:** April 19, 2026

StrikePoint AI is an offline-capable AI fishing assistant built by Goodhope Technologies LLC.
Your catch logs, waypoints, photos, and AI conversations are stored exclusively on your
device. When you are online, approximate GPS coordinates are transmitted to public
environmental APIs (NOAA, USGS, EPA, Open-Meteo, GBIF, OpenStreetMap) solely to
retrieve local conditions — they are never retained or sold by Goodhope Technologies LLC.

---

## Legal Documents

| Document | Description |
|---|---|
| [Privacy Policy](privacy.md) | What data is processed, where it goes, and your rights |
| [Terms & Conditions](terms.md) | Service scope, free tier, Pro unlock, and liability |

---

## Technical Reference

| Document | Description |
|---|---|
| [Architecture Overview](architecture.md) | Service locator, database schema, threading model, and AI inference pipeline |
| [RAG Services API](rag_services_api.md) | All 21 data sources injected into the LLM context — endpoints, gating, and failure contracts |
| [PublicWaypointService](public_waypoint_service.md) | Offline hotspot atlas, telemetry station discovery, and spatial query design |
| [Security Reference](security.md) | Encryption, backup security model, HTTPS enforcement, and privacy controls |
| [fllama Fork Backup](fllama-fork-backup.md) | Patch list, file paths, and rebase procedure for the custom fllama fork |
| [Launch Submission Checklist](fishing-app-launch-submission-list.md) | App Store + Play Console submission checklist and go/no-go gates |

---

## Marketing & Branding

| Document | Description |
|---|---|
| [Marketing & Branding Guide](marketing.md) | Verified feature claims, key stats table, and messaging angles |

---

## Quick Facts

| | |
|---|---|
| **AI model** | Llama 3.2 1B — 100% on-device via fllama |
| **Database encryption** | AES-256 SQLCipher with hardware-backed key |
| **Data sources** | 21 total: 10 live environmental APIs + 11 on-device engines |
| **Fisheries database** | 1,470+ named North American fisheries (all 50 US states + all Canadian provinces) |
| **Free tier** | Full offline atlas + catch logger; 30 AI queries during the first week after install, then 7 per 7-day rolling window |
| **Pro unlock** | One-time $19.99 — unlimited AI + unlimited tackle storage |
| **Privacy analytics** | Firebase Analytics/Crashlytics — opt-out in Settings → Privacy |
| **Developer** | Goodhope Technologies LLC · support@goodhopetech.com |
