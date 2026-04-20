# Privacy Policy — StrikePoint AI

**Last Updated:** April 19, 2026
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
AI inference (Llama 3.2) runs entirely on your device's CPU/RAM — your queries are never
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
| Biodiversity occurrences | Yes | Sent to GBIF API as a bounding box |
| Nearby water bodies | Yes | Sent to OpenStreetMap Overpass API |
| Reverse geocoding | Yes | Sent to Nominatim API to resolve water body name |
| Offline marine conditions | Yes | Sent to Open-Meteo Marine API |
| River flow (USGS/ECCC) | No | Queried by station ID only — coordinates not transmitted¹ |
| NOAA tides (US coasts) | No | Queried by station ID only — coordinates not transmitted¹ |
| CHS tides (Canadian coasts) | No | Queried by CHS station code only — coordinates not transmitted¹ |
| Waypoints and catch logs | No | Stored locally only, never transmitted |

¹ Station IDs are discovered on-device from the pre-bundled public hotspot atlas
(52,929 rows of government-sourced gauge/tidal stations). No coordinates are sent to
USGS, NOAA, ECCC, or CHS for that discovery step.

When coordinates are transmitted to third-party APIs, they are used only to return
environmental data for your current session. Goodhope Technologies LLC does not retain, sell, or
share these coordinates. The third-party services (Open-Meteo, EPA, GBIF, OpenStreetMap,
Nominatim) have their own privacy policies governing momentary request processing.

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
(Open-Meteo, USGS, EPA WQX, OpenStreetMap, GBIF, Environment Canada, Nominatim). Your
approximate GPS coordinates may be included in these requests as described in Section 2.
GBIF biodiversity occurrence data is licensed under CC-BY and is attributed accordingly
within the app.

### Firebase Analytics
We use **Google Firebase Analytics** to track aggregate, anonymous app-level events:
`purchase_success`, `paywall_view`, and `app_open`. These events do not include your GPS
coordinates, catch data, photos, or any personally identifiable information.

You can disable analytics collection at any time under **Settings → Privacy → Usage
Analytics**. When disabled, no events are buffered or transmitted — the setting takes
effect immediately and persists across app restarts.

### Firebase Crashlytics
We use **Google Firebase Crashlytics** to collect anonymous crash reports when the app
encounters an unexpected error. Reports contain a stack trace, device model, OS version,
and app version. They do not contain your catch data, GPS coordinates, photos, or any
personally identifiable information.

You can disable crash reporting at any time under **Settings → Privacy → Crash Reporting**.
When disabled, no crash data is uploaded. The setting takes effect immediately and
persists across app restarts.

Both Firebase services are subject to [Google's Privacy Policy](https://policies.google.com/privacy).

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
- **Disable analytics:** Settings → Privacy → Usage Analytics (off = zero data collected).
- **Disable crash reporting:** Settings → Privacy → Crash Reporting (off = zero data
  uploaded).
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
