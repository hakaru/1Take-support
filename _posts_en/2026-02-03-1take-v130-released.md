---
title: "1Take v1.3.0 Released: Recording Analysis, Auto-Calibration & Performance Boost"
date: 2026-02-03
kind: release
tags: [1Take, release, v1.3.0, recording, analysis]
summary: "1Take v1.3.0 brings automatic recording quality analysis, intelligent auto-record calibration, 5-band parametric EQ, and major stability improvements."
---

## 1Take v1.3.0 is Now Available!

We're excited to announce that **1Take v1.3.0** has passed App Store review and is now available for download. This release brings powerful new features for serious musicians and significant under-the-hood improvements.

---

## What's New in v1.3.0

### Recording Analysis System

Ever wondered if your recording was technically sound? Now 1Take automatically analyzes your recordings:

- **Peak & RMS levels** - See your actual recording levels
- **Crest Factor** - Understand your dynamic range at a glance
- **LUFS analysis** - Professional loudness measurement (ITU-R BS.1770-4)
- **THD+N** - Total Harmonic Distortion plus Noise evaluation
- **Background Noise** - Know exactly how clean your recording environment is

After each recording, you'll get a quality report with actionable recommendations.

### Auto-Record Intelligent Calibration

Setting the right threshold for auto-record just got smarter:

- **One-tap calibration** - Press the "Auto" button (formerly "Analyze")
- **Ambient noise measurement** - Automatically calculates optimal threshold based on your environment
- **Hysteresis control** - Prevents false triggers from transient sounds
- **Persistent settings** - Your calibrated threshold saves across app launches

No more guessing games. Let 1Take listen to your room and set the perfect trigger level.

### 5-Band Parametric EQ

Upgraded from 4-band to professional-grade 5-band parametric EQ:

- **Full control** - Frequency, Gain, and Q (bandwidth) per band
- **Visual feedback** - Draggable control points on the frequency response curve
- **Enhanced presets** - Studio and Live modes retuned for the new EQ

Shape your tone with precision before it hits the recorder.

### Sleep Prevention

Long recording session? Enable "Keep Screen On" in Recording Settings. Your iPhone won't sleep mid-take anymore.

---

## Under the Hood

### Critical Stability Fixes

- **Long recording sessions** - Fixed memory management issues causing crashes
- **Audio route changes** - Better recovery when plugging/unplugging mics
- **Thread safety** - Lock-free atomics for bulletproof audio processing

### Performance Optimizations

- **Zero Task creation** in audio callback (down from ~93/sec)
- **Swift Atomics** - Eliminated NSLock from real-time audio thread
- **VU ballistics** - Now computed in audio thread for zero-latency response

### Code Quality

- Major refactoring for maintainability
- 345 tests passing
- Mac Catalyst preparation

---

## Simplified Markers

Based on user feedback, we've streamlined the marker system:

- **Removed**: Manual Good/Bad/Memo markers
- **Kept**: Automatic CLIP and OVER markers

The auto-markers catch the moments that matter most—when your audio clips or exceeds safe levels. Less tapping, more playing.

---

## Download Now

Ready to experience the most stable and feature-rich 1Take yet?

- [Download on App Store](https://apps.apple.com/jp/app/1take/id6757945099)
- [Support Page](/)
- [Privacy Policy](/privacy)

Thank you for your continued support. Keep making great music!
