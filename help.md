---
layout: default
title: Help & Support
---

# StrikePoint AI Technical User Guide

Welcome to StrikePoint AI. This is a tactical, offline-first fishing intelligence platform powered by an on-device Gemma 4 AI engine, a massive 28-source environmental data pipeline, and comprehensive local intelligence vectors.

This guide covers the advanced features, how to use them, and how they function when you leave cell service behind.

---

## 🤖 The Tactical AI Engine (Gemma 4)
StrikePoint AI does not use the cloud to process your questions. We run Google's **Gemma 4 E2B** model directly on your device via the `flutter_gemma` LiteRT engine.

Before the AI answers you, our Data Engine pulls from 28 unique environmental and tactical sources.

**Core AI Features:**
- **28-Source Context Aggregation Pipeline:** The engine aggregates data from USGS river flow rates, ECCC WaterOffice, EPA water quality, CHS/NOAA Tides, Open-Meteo Marine, and MODIS satellites. It employs dynamic heuristics like air-temperature regressions and 72-hour rain turbidity estimations when direct sensors are offline.
- **Per-Water-Body Species Engine:** The AI cross-references your exact water body using a 3-tier lookup: an organic cache of local species records, a bundled offline core database (major reservoirs, tournament lakes, state top-25 waters), and live regional fish occurrence data. This includes live monitoring of reservoir pool elevations.
- **USGS NHD & NRCan NHN Hydrology Classifier:** The AI reads raw public-domain ArcGIS geometry from federal and provincial hydrography networks to classify your water type.
- **Hardware-Adaptive Inference:** StrikePoint dynamically tiers token budgets (2048 vs 3072) and utilizes a persistent session KV cache to prevent `liblitertlm_jni` crashes on older hardware. A "noun-drift" cache strictly prevents repetitive LLM speech patterns.

---

## ⚙️ Advanced AI Orchestration
StrikePoint is far more than a simple LLM wrapper; it utilizes a complex multi-agent orchestration layer to guarantee speed and accuracy.

- **Smart Query Routing & Precision Math:** Instead of guessing, the system instantly categorizes your questions and uses precise math to calculate distances and solunar times, preventing mistakes.
- **Autonomous Agents:** The AI is equipped with 12 read-only tools. It can autonomously search the hotspot database, query your catch history, pull species biology, and fetch on-demand weather, tides, and river flows without asking for permission.
- **Efficient Processing:** Quickly handles simple greetings and irrelevant questions before they trigger the main data engine, preserving your device's battery life.
- **Absolute Safety:** A relentless chain of validators ensures the AI refuses to give illegal or unregulated creel limit advice.
- **Smart Notification Filtering:** The UI filters actionable alerts (like `📡 Offline Mode` or weather shifts) against previous messages so you are never spammed with repetitive information.
- **Built-in Diagnostics:** The app ships with a built-in debugging suite to ensure high-speed performance natively on your device.

---

## 🧠 Tactical Vector Intelligence
StrikePoint utilizes a highly optimized offline database to store and retrieve expert knowledge without network access, using advanced local pattern matching.

**What it powers:**
- **Structural Dictionary:** Detailed breakdown of drop-offs, points, and weedlines.
- **Knots & Rigs Mastery:** Step-by-step guidance for tying the right knot for the right presentation.
- **Match-the-Hatch Forage Diets:** Regional forage data to perfectly match local baitfish.
- **Seasonal Behavior Matrices:** Temperature and thermocline-driven fish behavior predictions.

---

## 🎙️ Global Hands-Free Voice Mode
StrikePoint AI features a fully native Voice-to-AI interaction loop, completely bypassing the keyboard.

**How to use:**
1. Tap the **Microphone** icon in the AI Chat.
2. Speak your query naturally. The system automatically detects when you stop speaking and is trained to understand fishing-specific terminology (ensuring words like "bass" and "crappie" are processed correctly).
3. The system employs **silence-based auto-stop**—simply stop talking, and the audio will be instantly processed.

---

## 🗺️ Offline Maps & Bathymetry
StrikePoint AI allows you to cache massive blocks of map data directly to your device so you can navigate and locate structure without cell service.

**How to download maps:**
1. Tap the **Download Icon** on the Map Screen.
2. The app will present a bounding box. Pan and zoom to select your expedition area.
3. If you have the **Bathymetry Layer** enabled (the topography icon), the app will natively download official NOAA (US) or CHS (Canada) depth contours alongside the standard map tiles—without relying on any restrictive 3rd-party mapping services.
4. Tap **Download**.

---

## 📸 On-Device Vision (100+ Class Fish ID)
Our custom Vision AI runs entirely on your phone's processor. Using a highly optimized local model, it can identify **100+ unique species** of fish in milliseconds.

**How to log a catch:**
1. Tap the **Camera** button.
2. Take a photo of your catch. The AI analyzes the frame entirely offline.
3. If the AI is highly confident, it automatically categorizes the species and opens the Catch Logger.

---

## 🎣 Digital Tackle Box & Matrix
The Tackle Box is not just a list of your gear—it is an active intelligence matrix.

When you ask the AI for advice, it analyzes live conditions and runs an advanced pattern match against your physical tackle inventory, telling you exactly which lure *that you own* is the mathematical best choice.

---

## 💾 Military-Grade Offline Portability (.spai Backups)
Your waypoints and catches are strictly yours. StrikePoint provides true offline data portability without forcing you onto a cloud provider.

**How to migrate devices off-grid:**
1. Go to Settings > **Backup & Export**.
2. Create a secure password.
3. The app packages your database and images into a `.spai` archive, protected by military-grade encryption.
4. Transfer this single encrypted file via Bluetooth or USB and import it instantly.

---

## 💳 Pricing & Subscriptions
We hate subscriptions. You own your tools.

- **Free Tier:** Log unlimited catches, save unlimited waypoints, use the offline map, and access the AI Tactical Heatmap. You get 30 free AI queries during your first week, and 7 free queries every week after that.
- **Pro Unlock ($19.99):** A one-time purchase unlocks unlimited Gemma 4 E2B AI interactions, unlimited tackle box storage, the 7-Day Strike Forecast, Deep Catch Analytics, and Advanced Log Filtering.

**Offline Purchase Verification:** StrikePoint securely verifies your App Store purchase directly on your device. You will never get locked out of your premium tools just because you lost cell service.

---

## 📞 Support
If you encounter a bug or need assistance:
**support@goodhopetech.com**
