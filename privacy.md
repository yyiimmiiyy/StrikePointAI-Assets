# Privacy Policy — StrikePoint AI

**Last Updated:** April 8, 2026
**Developer:** YYIIMMIIYY LLC

## Overview

At YYIIMMIIYY LLC, we built StrikePoint AI to be a premium, off-grid survival technology. Because you may rely on it in remote locations, privacy and data sovereignty are foundational to the application. This Privacy Policy outlines our data practices for the StrikePoint AI mobile application.

## 1. Local Data Storage & AI Processing

StrikePoint AI is designed to keep your personal data under your control. While the application connects to the internet to fetch real-time environmental data, we **do not** collect, transmit, or store your personal data, catch logs, waypoints, photos, or forecasting queries on any external servers owned by YYIIMMIIYY LLC. The LLM (AI) inference runs 100% offline on your device's hardware.

All of your data is stored locally on your device within a secured, encrypted SQLite database. 

## 2. Location Data (GPS)

To provide precise Solunar forecasts, atmospheric pressure aggregation, and waypoint logging, StrikePoint AI requires access to your device's GPS and location services.
* **Local Processing:** Your exact GPS coordinates are used exclusively on your device to execute local heuristics.
* **No External Tracking:** We never transmit your location data to our servers, nor do we sell or share it with third parties.

## 3. Social Sharing & Media Export

StrikePoint AI includes a feature to generate and share "Trophy Cards" of your log entries.
* **Location Redaction:** When exporting a Trophy Card image, the rendering engine explicitly strips your exact coordinates and the water body name. The exported image will not contain embedded GPS EXIF data or textual location data, mathematically guaranteeing your spots remain secret.
* **OS Distribution:** The rendered image is passed directly to your device's native sharing sheet. You maintain full control over which apps or contacts receive the image.

## 4. Data Backups & Encryption

If you choose to export your data using StrikePoint AI's Backup & Restore feature, the app generates an AES-256 encrypted `.spai` archive. 
* The password you set is never transmitted to us.
* The backup file remains on your device or wherever you manually choose to share it (e.g., iCloud Drive, local storage, email). We cannot recover your data if you lose your password.

## 5. Third-Party Services 

While YYIIMMIIYY LLC does not collect your data, the app relies on specific third-party infrastructure to function:

### Environmental Data Aggregation
When you have internet access, StrikePoint AI fetches real-time environmental data from various public and third-party APIs (including Open-Meteo, USGS, EPA, OpenStreetMap, GBIF, and Environment Canada WaterOffice). Your IP address and request coordinates may be processed momentarily by their respective servers strictly to return the contextual data necessary for your forecast. GBIF biodiversity occurrence data is licensed under CC-BY and is attributed accordingly.

### Firebase Analytics & Conversion Tracking
While we do not track your fishing data, we do use **Google Firebase Analytics** strictly to track aggregate app installations and purchase conversions for the "Pro" lifetime unlock. The data sent to Firebase is strictly limited to conversion events (e.g., `purchase_success`, `paywall_view`) and does not include any geographical tracking, PII (Personally Identifiable Information), or usage telemetry inside the core application. See [Google's Privacy Policy](https://policies.google.com/privacy).

### Firebase Crashlytics
We use **Google Firebase Crashlytics** to automatically collect anonymous crash reports when the app encounters an unexpected error. Crash reports contain a stack trace, device model, OS version, and app version. They do not contain your catch data, GPS coordinates, photos, or any personally identifiable information. Crash reporting helps us fix bugs quickly and improve app stability. You can opt out by disabling analytics in your device settings. See [Google's Privacy Policy](https://policies.google.com/privacy).

### App Stores (Apple & Google)
Payments are processed entirely through the Apple App Store or Google Play Store. Payment information (such as credit card details) is never shared with us. Crash reports and anonymous usage telemetry may be collected natively by Apple or Google depending on your OS-level diagnostic settings.

## 6. Children's Privacy

StrikePoint AI is designed for a general audience. We do not knowingly collect personal information from children under the age of 13.

## 7. Your Rights & Data Deletion

Because you control 100% of your data:
* You can delete all your records instantly by navigating to the App Settings and purging your local cache.
* You can permanently destroy all application data by simply uninstalling StrikePoint AI from your device.

## 8. Changes to This Policy

We may update this privacy policy from time to time as we introduce new features. Changes will be reflected by updating the "Last Updated" date above.

## 9. Contact

For questions or concerns about this privacy policy, please contact:
**Email:** support@yyiimmiiyy.com
