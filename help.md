---
layout: default
title: Help & Support
---

# StrikePoint AI User Guide

Welcome to StrikePoint AI. This is a tactical, offline-first fishing intelligence platform powered by an on-device Gemma 4 AI engine and a massive 28-source environmental data pipeline. 

This guide covers the core features, how to use them, and how they function when you leave cell service behind.

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

## 📸 On-Device Fish ID & Catch Logging

Our custom Vision AI runs entirely on your phone's processor. It can identify over 100+ species of fish in milliseconds.

**How to log a catch:**
1. Tap the **Camera** button in the main navigation.
2. Take a photo of your catch. The AI will immediately analyze the frame.
3. If the AI is highly confident (≥ 60% cosine similarity), it will automatically categorize the species and open the catch review sheet.
4. The Catch Logger instantly snapshots the current weather, barometric pressure, and solunar phase, saving the full environmental context to your local SQLCipher database.

---

## 🤖 The Tactical AI Engine (Gemma 4)

StrikePoint AI does not use the cloud to process your questions. We run Google's **Gemma 4 E2B** model directly on your device.

Before the AI answers you, our Data Engine pulls from 28 unique sources—including USGS river flows, NOAA tides, Open-Meteo marine conditions, and your own catch history. 

**Tips for the AI:**
- **Zero-Shot Routing:** The AI knows what you are asking. If you ask about Knot Tying, it will route your question to the Tactical knowledge base and ignore the local tide data.
- **Ask about your history:** Try asking, *"What lure was I using the last time I caught a Bass in these weather conditions?"* The AI will read your digital Tackle Box and Catch Log.
- **Tactical Heatmaps:** The AI powers the map Heatmap overlay. It calculates the dot-product similarity between the current live weather and the exact weather conditions of your past catches, literally making the map glow where you should cast.

---

## 🎣 Digital Tackle Box & Matrix

The Tackle Box is not just a list of your gear—it is an active intelligence matrix.

1. Add your lures, specifying their weight, color, and profile.
2. When you ask the AI for advice, it runs an **Optimal Tackle Matrix**.
3. It analyzes the live cloud cover (to suggest lure color theory), wind speed (to suggest lure profile), and water depth, and cross-references those physics against your actual inventory. 

---

## 💳 Pricing & Subscriptions

We hate subscriptions. You own your tools.

- **Free Tier:** Log unlimited catches, save unlimited waypoints, and use the offline map. You get 30 free AI queries during your first week, and 7 free queries every week after that.
- **Pro Unlock:** A one-time purchase of **$19.99** unlocks unlimited Gemma 4 AI interactions, unlimited tackle box storage, and full access to the Tactical Heatmap.

---

## 📞 Support

If you encounter a bug or need assistance:
**support@goodhopetech.com**
