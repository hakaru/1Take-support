---
title: "1Take v1.3.2: Stability Improvements"
date: 2026-03-23
kind: release
tags: [1Take, release, v1.3.2, bugfix, stability]
summary: "v1.3.2 fixes crashes and makes deleted recordings recoverable from the Files app."
---

## 1Take v1.3.2 Stability Update

**1Take v1.3.2** is now available on the App Store. This update fixes crashes and improves recording deletion behavior.

---

## Improvements

### Deleted Recordings Are Now Recoverable

When you delete a recording, the audio file is now moved to **"Recently Deleted"** in the Files app instead of being permanently removed.

- Accidentally deleted recordings can be **recovered for up to 30 days**
- The delete confirmation dialog now informs you that recovery is possible

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
