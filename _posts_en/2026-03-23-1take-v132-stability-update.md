---
title: "1Take v1.3.2: Stability Improvements"
date: 2026-03-23
kind: release
tags: [1Take, release, v1.3.2, bugfix, stability]
summary: "v1.3.2 fixes crashes reported via Firebase Crashlytics, improving playback and recording stability."
---

## 1Take v1.3.2 Stability Update

**1Take v1.3.2** is now available on the App Store. This update addresses crashes reported by users through Crashlytics, improving overall app stability.

---

## What's Fixed

### Playback Crash Fix

Fixed a rare crash that could occur during audio playback.

- When an audio session interruption (incoming call, other app audio, etc.) occurred during playback, the play function could be called recursively, leading to a stack overflow crash
- The interruption handler now uses async dispatch with a re-entrant guard to prevent this entirely

### Recording Start Crash Fix

Fixed a rare crash when tapping the record button.

- If the audio hardware wasn't fully ready when the engine attempted to connect nodes, an invalid audio format (0 channels) would cause an unrecoverable crash
- The engine now validates the input format before connecting nodes and returns a proper error if hardware isn't ready

---

## How to Update

Update to the latest version from the App Store.

If you experience any issues or have feedback, please reach out through the settings screen in the app.

Thank you for using 1Take!
