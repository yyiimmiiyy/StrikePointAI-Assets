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
- **Per-Water-Body Species Engine:** The AI cross-references your exact water body using a 3-tier lookup: an organic cache (live GBIF data), a bundled offline core DB (USACE/USBR reservoirs, tournament lakes, state top-25 waters), and live GBIF fallback. This includes live monitoring of USACE pool elevations.
- **USGS NHD & NRCan NHN Hydrology Classifier:** The AI reads raw public-domain ArcGIS geometry from federal and provincial hydrography networks to classify your water type.
- **Hardware-Adaptive Inference:** StrikePoint dynamically tiers token budgets (2048 vs 3072) and utilizes a persistent session KV cache to prevent `liblitertlm_jni` crashes on older hardware. A "noun-drift" cache strictly prevents repetitive LLM speech patterns.

---

## ⚙️ Advanced AI Orchestration
StrikePoint is far more than a simple LLM wrapper; it utilizes a complex multi-agent orchestration layer to guarantee speed and accuracy.

- **Zero-Shot Semantic Intent Router & Hybrid Dispatchers:** Instead of feeding every query blindly to the LLM, the system uses Matryoshka embeddings to classify the query into 6 core intents. Geographic distance queries bypass the LLM entirely and use deterministic math via Hybrid Dispatchers.
- **Autonomous Tool Calling Engine:** The AI has the autonomy to execute 12 read-only JSON tool calls. Beyond the core 5 (`searchPublicHotspots`, `searchCatchHistory`, `searchTacticalIntel`, `getSpeciesIntel`, `refreshConditions`), it utilizes 7 on-demand telemetry tools (`getCurrentWeather`, `getRiverFlow`, `getTides`, `getMarineConditions`, `getWaterQuality`, `getAirQuality`, `getOptimalTackle`) to pull precisely the data it needs without prefilling the context window.
- **Pre-LLM Short-Circuit Registry:** The pipeline intercepts prompt injection attempts and trivial small-talk *before* they hit the heavy RAG pipeline, instantly returning lightweight responses to save battery.
- **8-Layer Guard Chain:** Absolute safety. A relentless chain of stream validators ensures the AI refuses to give illegal or unregulated creel limit advice.
- **State-Machine Insight Deduplication:** The UI filters actionable chips (like `📡 Offline Mode` or weather shifts) against the previous message state so you are never spammed with repetitive telemetry.
- **On-Device Evaluation Harness:** The app ships with a built-in debugging harness to run offline regression testing (measuring Time-To-First-Token, full inference ms, and RAG attribution) natively on the device hardware.

---

## 🧠 Tactical Vector Intelligence
StrikePoint utilizes a highly optimized offline SQLite vector database to store and retrieve expert knowledge without network access, using local Matryoshka embeddings.

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
2. Speak your query naturally. The AI uses **multimodal phonetic mapping** using custom fishing-domain IPA pronunciation (ensuring words like "bass" and "crappie" are processed correctly, not as audio or negative terms).
3. The system employs **silence-based auto-stop**—simply stop talking, and the native 16kHz WAV streaming will instantly package and route your audio.

---

## 🗺️ Offline Maps & Bathymetry
StrikePoint AI allows you to cache massive blocks of map data directly to your device so you can navigate and locate structure without cell service.

**How to download maps:**
1. Tap the **Download Icon** on the Map Screen.
2. The app will present a bounding box. Pan and zoom to select your expedition area.
3. If you have the **Bathymetry Layer** enabled (the topography icon), the app will *natively* download official NOAA (US) or CHS NONNA (Canada) WMS depth contour tiles alongside the standard map tiles—without relying on any restrictive 3rd-party tile APIs.
4. Tap **Download**.

---

## 📸 On-Device Vision (775-Class Fish ID)
Our custom Vision AI runs entirely on your phone's processor. Using a highly optimized **BEiTv2 TFLite** model, it can identify **775 unique species** of fish in milliseconds.

**How to log a catch:**
1. Tap the **Camera** button.
2. Take a photo of your catch. The AI analyzes the frame entirely offline.
3. If the AI is highly confident (≥ 60% cosine similarity), it automatically categorizes the species and opens the Catch Logger.

---

## 🎣 Digital Tackle Box & Matrix
The Tackle Box is not just a list of your gear—it is an active intelligence matrix.

When you ask the AI for advice, it analyzes live conditions and runs a **Cosine Similarity** search against your physical tackle inventory, telling you exactly which lure *that you own* is the mathematical best choice.

---

## 💾 Military-Grade Offline Portability (.spai Backups)
Your waypoints and catches are strictly yours. StrikePoint provides true offline data portability without forcing you onto a cloud provider.

**How to migrate devices off-grid:**
1. Go to Settings > **Backup & Export**.
2. Create a secure password.
3. The app packages your SQLCipher database and images into a `.spai` archive, protected by **AES-256-CBC, 100k PBKDF2 iterations, and an HMAC-SHA256 integrity tag**.
4. Transfer this single encrypted file via Bluetooth or USB and import it instantly.

---

## 💳 Pricing & Subscriptions
We hate subscriptions. You own your tools.

- **Free Tier:** Log unlimited catches, save unlimited waypoints, and use the offline map. You get 30 free AI queries during your first week, and 7 free queries every week after that.
- **Pro Unlock ($19.99):** A one-time purchase unlocks unlimited Gemma 4 AI interactions, unlimited tackle box storage, and full access to the Tactical Heatmap.

**On-Device RSA Verification:** StrikePoint mathematically verifies your App Store purchase locally via RSA-SHA1 signatures. You will never get locked out of your premium tools just because you lost cell service.

---

## 📞 Support
If you encounter a bug or need assistance:
**support@goodhopetech.com**
