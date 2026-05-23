# Privacy Policy — StrikePoint AI

**Last Updated:** May 23, 2026
**Developer:** Goodhope Technologies LLC

---

## Overview

StrikePoint AI is designed from the ground up for anglers who take their privacy seriously.
Your catch logs, waypoints, photos, and AI conversations are stored exclusively on your
device — they never touch Goodhope Technologies LLC servers. This policy explains precisely what data
is processed, where it goes, and what control you have over it.

---

## 1. Your Fishing Data — Stays on Your Device

Goodhope Technologies LLC does not collect, transmit, or store your personal fishing data on any
external servers. This includes:

- Catch logs (species, weight, location, photos)
- GPS waypoints and secret fishing spots
- AI chat conversations
- Digital tackle inventory
- Audio recordings from voice input

All of this data lives in an AES-256 encrypted SQLite database on your device. The
AI inference (Gemma 4) runs entirely on your device's CPU/RAM — your queries are never
sent to a cloud service for processing.

---

## 2. Location Data (GPS)

StrikePoint AI requires access to your device's GPS to provide accurate solunar forecasts,
environmental data aggregation, and waypoint logging.

**What we do with your coordinates:**

| Purpose | Transmitted externally? | Details |
|---|---|---|
| Solunar calculations | No | Pure offline math on-device |
| Weather forecast | Yes | Sent to Open-Meteo API to return your local forecast |
| EPA water quality | Yes | Sent to EPA WQX API to find nearest monitoring station |
| Air quality index | Yes | Sent to Open-Meteo AQI API |
| Biodiversity occurrences (per-water species lookup) | Yes | When on Wi-Fi only, sends a small bounding box around a tapped water to public-domain biodiversity APIs (GBIF, optionally iNaturalist) to enrich species data. Capped at 30 lookups per app session and 24-hour TTL — repeat lookups reuse the local cache. No account, no tracking, no PII attached. |
| Nearby water bodies | Yes | Sent to USGS National Hydrography Dataset WFS (US, public-domain federal) and NRCan National Hydro Network WFS (Canada, OGL) — OpenStreetMap Overpass was removed in v3.46. |
| Reverse geocoding | Yes | Sent to USGS NHD (US) / NRCan NHN (Canada) to resolve the closest named water body — same public-domain federal endpoints as the nearby water bodies lookup. No OSM, no Nominatim, no GeoNames. |
| Offline marine conditions | Yes | Sent to Open-Meteo Marine API |
| River flow (USGS/ECCC) | No | Queried by station ID only — coordinates not transmitted¹ |
| NOAA tides (US coasts) | No | Queried by station ID only — coordinates not transmitted¹ |
| CHS tides (Canadian coasts) | No | Queried by CHS station code only — coordinates not transmitted¹ |
| WMS Bathymetry Caching | Yes | When caching maps offline, geographic bounding boxes (BBOX) are sent to NOAA (US) or CHS NONNA (Canada) servers to fetch depth contours |
| Waypoints and catch logs | No | Stored locally only, never transmitted |
| Background atlas self-healing (GBIF) | Yes | When on Wi-Fi, `DataFreshnessService` sends activity centroids (50m-deduplicated, approximate — not exact catch coordinates) to the GBIF API to refresh nearby species occurrence data. These centroids are derived from your movement patterns, not your specific fishing spots. They are never linked to your identity because there is no user account |
| Map-driven species pre-cache (GBIF) | Yes | **Off by default.** When you opt in via Settings → "Pre-cache species when panning the map", the app sends the visible water-body bounding box to GBIF on Wi-Fi only to enrich species data for waters you scrolled past. Rate-limited to 5 water bodies per minute. Persisted under the local `map_species_pre_cache_enabled` flag; toggle off at any time to stop these requests |

¹ Station IDs are discovered on-device from the pre-bundled public hotspot atlas
(31,379 rows of government-sourced gauge/tidal/access-point data, including 14,094
USGS gauges, 156 ECCC gauges, and 9 CHS tidal stations among other access types). No
coordinates are sent to USGS, NOAA, ECCC, or CHS for that discovery step.

When coordinates are transmitted to third-party APIs, they are used only to return
environmental data for your current session. Goodhope Technologies LLC does not retain, sell, or
share these coordinates. The third-party services (Open-Meteo, EPA, GBIF, iNaturalist,
USGS NHD, NRCan NHN, NOAA, Environment Canada, USACE) have their own privacy policies
governing momentary request processing.

---

## 2a. On-Device Fish ID (Vision Service)

When you capture a photo through the in-app **Fish ID camera**, the entire image-analysis
pipeline runs on your device:

- The photo is compressed and centre-cropped to a 4:5 portrait format **on-device** in a
  background isolate.
- If the optional fish-classifier model is bundled with your build, species classification
  runs locally via TensorFlow Lite. The image is resized to 224×224, the inference runs
  inside a sandboxed isolate, and the result (top species + confidence) is returned to the
  UI without any network call.
- **Photos and inference results are never uploaded.** Goodhope Technologies LLC has no servers that
  receive catch images.
- Temporary compressed working files are deleted after inference; the original capture is
  retained only if you choose to attach it to a logged catch.

When the classifier is not bundled (the default for open-source builds), the camera screen
honestly reports "On-device Fish ID model not bundled" and lets you log the catch manually.
We do not silently fall back to a cloud service.

---

## 3. Social Sharing & Trophy Cards

StrikePoint AI includes a "Trophy Card" feature to share catch images.

- **Location redaction:** The rendering engine strips exact GPS coordinates and precise
  water body names from exported images. Exported images contain no embedded EXIF GPS data.
- **You control distribution:** The rendered image is passed to your device's native sharing
  sheet. You choose which apps or contacts receive it.

---

## 4. Data Backups & Encryption

The Backup & Restore feature exports an AES-256-CBC encrypted `.spai` archive.

- Your password is never transmitted to us and cannot be recovered.
- The archive includes your encrypted database and the database encryption key. The entire
  archive (key included) is sealed inside an AES-256-CBC envelope whose key is derived from
  your backup password via PBKDF2-HMAC-SHA256 (100,000 iterations). The archive is also
  HMAC-SHA256 authenticated. Without your backup password, neither the database key nor the
  database itself can be recovered. See [Security Reference §2](security.md) for the full
  binary format.
- **Store your backup password in a secure password manager.** If lost, the archive
  cannot be decrypted and your data cannot be restored from it.
- The backup file stays on your device or wherever you manually choose to save it
  (iCloud Drive, Google Drive, local storage). Goodhope Technologies LLC never receives it.

---

## 5. Free-Tier Usage Quota

Free-tier users receive **30 AI queries during the first 7 days after install**, then
**7 queries per rolling 7-day window** thereafter. This counter is stored on your device
in hardware-backed encrypted storage (`FlutterSecureStorage`) — it is never transmitted
to our servers. Purchasing the Pro lifetime unlock removes this limit permanently.

---

## 6. Third-Party Services

### Environmental Data APIs
When you are online, StrikePoint AI fetches real-time environmental data from public APIs
(Open-Meteo, USGS NHD, NRCan NHN, EPA WQX, GBIF, iNaturalist, Environment Canada, NOAA, USACE). Your
approximate GPS coordinates may be included in these requests as described in Section 2.
GBIF biodiversity occurrence data is licensed under CC-BY and is attributed accordingly
within the app.

### Analytics & Crash Reporting — REMOVED
**As of v3.46.5 (2026-05-02), StrikePoint AI sends no usage analytics and no crash
reports off-device.** The previous Firebase Analytics + Firebase Crashlytics integrations
were removed entirely. There is no third-party analytics service, no anonymous event
collection, and no remote crash reporting. All errors are logged to the local device-only
logger (which redacts PII including GPS coordinates, SQLCipher keys, and auth tokens
before writing) and never transmitted.

The corresponding **Settings → Privacy** toggles were also removed because there is
nothing left to opt out of. The single source of truth for what does/doesn't leave the
device is this document.

### App Stores (Apple & Google)
Payments are processed entirely through the Apple App Store or Google Play Store. Payment
information is never shared with us. Crash reports and anonymous usage telemetry may be
collected natively by Apple or Google depending on your OS-level diagnostic settings.

---

## 7. Children's Privacy

StrikePoint AI is designed for a general audience. We do not knowingly collect personal
information from children under the age of 13.

---

## 8. Your Rights & Data Deletion

Because you control 100% of your fishing data:

- **Delete records:** Navigate to Settings → Data & Diagnostics → Clear AI Chat History to
  remove AI conversations. Uninstalling the app permanently destroys all locally stored data.
- **Analytics + crash reporting:** Removed entirely as of v3.46.5 — nothing to opt out of.
- **Export your data:** Use Backup & Restore to create an encrypted portable archive before
  switching devices.

---

## 9. Changes to This Policy

We may update this policy as we introduce new features. Changes will be reflected by
updating the "Last Updated" date above. Significant changes will be communicated via an
in-app notice.

---

## 10. Contact

For questions or concerns about this privacy policy, please contact:
**Email:** support@goodhopetech.com
