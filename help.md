---
layout: default
title: Help & Support
---

# StrikePoint AI Technical User Guide

Welcome to StrikePoint AI. This is a tactical, offline-first fishing intelligence platform powered by an on-device Gemma 4 AI engine, a massive 28-source environmental data pipeline, and 9 core intelligence pillars.

This guide covers the advanced features, how to use them, and how they function when you leave cell service behind.

---

## 🎙️ Global Hands-Free Voice Mode
StrikePoint AI features a fully native Voice-to-AI interaction loop, completely bypassing the keyboard.

**How to use:**
1. Tap the **Microphone** icon in the AI Chat.
2. Speak your query naturally. The AI uses **multimodal phonetic mapping** (ensuring words like "bass" are processed in a fishing context, not as an audio term).
3. The system employs **silence-based auto-stop**—simply stop talking, and the native 16kHz WAV streaming will instantly package and route your audio to the Gemma 4 E2B engine.

---

## 🗺️ Offline Maps & Bathymetry
StrikePoint AI allows you to cache massive blocks of map data directly to your device so you can navigate and locate structure without cell service.

**How to download maps:**
1. Tap the **Download Icon** on the Map Screen.
2. The app will present a bounding box. Pan and zoom to select your expedition area.
3. If you have the **Bathymetry Layer** enabled (the topography icon), the app will *natively* download official NOAA (US) or CHS NONNA (Canada) WMS depth contour tiles alongside the standard map tiles.
4. Tap **Download**. Ensure you are on Wi-Fi (unless you have explicitly enabled Cellular Downloads in Trip Mode settings).

Your maps, including deep-water bathymetry, are now available 100% offline.

---

## 🏕️ Trip Mode
Trip Mode is a specialized lifecycle state designed for active expeditions. **It is separate from downloading maps.**

**What Trip Mode does:**
- **Quiet Mode Integration:** By default, Trip Mode silences non-essential push notifications so your phone isn't buzzing while you're fighting a fish.
- **Geographic Re-alignment:** If you travel long distances while the app is in the background, returning to the app in Trip Mode will dynamically force the Solunar Math engine to recalculate your major and minor feeding windows based on your new coordinates.
- **Cellular Overrides:** Allows you to configure whether the app is permitted to use cellular data for map downloads or API calls while active.

*Toggle Trip Mode using the tent icon on the map screen.*

---

## 📸 On-Device Vision (775-Class Fish ID)
Our custom Vision AI runs entirely on your phone's processor. Using a highly optimized **BEiTv2 TFLite** model, it can identify **775 unique species** of fish in milliseconds.

**How to log a catch:**
1. Tap the **Camera** button in the main navigation.
2. Take a photo of your catch. The AI will immediately analyze the frame entirely offline.
3. If the AI is highly confident (≥ 60% cosine similarity), it will automatically categorize the species and open the catch review sheet.
4. The Catch Logger instantly snapshots the current weather, NOAA MODIS water clarity, and solunar phase, saving the full environmental context to your local SQLCipher database.

---

## 🤖 The Tactical AI Engine (Gemma 4)
StrikePoint AI does not use the cloud to process your questions. We run Google's **Gemma 4 E2B** model directly on your device via the `flutter_gemma` LiteRT engine. 

Before the AI answers you, our Data Engine pulls from 28 unique sources.

**Core AI Features:**
- **USGS NHD & NRCan NHN Hydrology Classifier:** The AI reads raw public-domain ArcGIS geometry from federal and provincial hydrography networks to know exactly what type of water you are on. It will never tell you to fish for saltwater pelagics in an inland pond.
- **NOAA MODIS Water Clarity:** Integrates federal ERDDAP APIs to fetch real-time chlorophyll-a concentrations, replacing basic rain heuristics with actual satellite truth.
- **8-Layer Guard Chain:** Absolute safety. A relentless chain of stream validators ensures the AI refuses to give illegal or unregulated creel limit advice.
- **Hardware-Adaptive Intelligence:** StrikePoint automatically profiles your device's RAM, seamlessly swapping massive 1B+ parameter models in and out of memory to prevent Out-Of-Memory (OOM) crashes on older hardware.

---

## 🎣 Digital Tackle Box & Matrix
The Tackle Box is not just a list of your gear—it is an active intelligence matrix.

1. Add your lures, specifying their weight, color, and profile.
2. When you ask the AI for advice, it runs an **Optimal Tackle Matrix**.
3. It analyzes the live cloud cover, water turbidity, and depth. It then runs a **Cosine Similarity** search against your physical tackle inventory to tell you exactly which lure *that you own* is the mathematical best choice for current conditions. If you don't own the right lure, it will recommend what you should acquire.

---

## 💾 Military-Grade Offline Portability (.spai Backups)
Your waypoints and catches are strictly yours. StrikePoint provides true offline data portability without forcing you onto a cloud provider.

**How to migrate devices off-grid:**
1. Go to Settings > **Backup & Export**.
2. Create a secure password.
3. The app packages your SQLCipher database and images into a `.spai` archive, protected by **AES-256-CBC, 100k PBKDF2 iterations, and an HMAC-SHA256 integrity tag**.
4. Transfer this single encrypted file to your new device via AirDrop, Bluetooth, or USB and import it instantly.

---

## 💳 Pricing & Subscriptions
We hate subscriptions. You own your tools.

- **Free Tier:** Log unlimited catches, save unlimited waypoints, and use the offline map. You get 30 free AI queries during your first week, and 7 free queries every week after that.
- **Pro Unlock ($19.99):** A one-time purchase unlocks unlimited Gemma 4 AI interactions, unlimited tackle box storage, and full access to the Tactical Heatmap.

**On-Device RSA Verification:** StrikePoint mathematically verifies your App Store purchase locally via RSA-SHA1 signatures. This means you will never get locked out of your premium tools just because you lost cell service and the app couldn't contact a subscription server.

---

## 📞 Support
If you encounter a bug or need assistance:
**support@goodhopetech.com**
