---
layout: default
title: "1Take Changelog"
description: "Version history and release notes for 1Take"
---

# Changelog

All notable changes to 1Take will be documented here.

---

## [1.3.0] - 2026-02-03

Recording analysis, intelligent auto-calibration, 5-band EQ, and performance optimizations.

### Added
- **Recording Analysis System**
  - Automatic audio quality assessment after recording
  - Peak level, RMS level, Crest Factor, LUFS analysis
  - Dynamic Range evaluation
  - Recording quality report with recommendations

- **Auto-Record Intelligent Calibration**
  - Automatic threshold calculation based on ambient noise
  - Hysteresis control for stable triggering
  - One-tap setup via Auto button
  - Background noise measurement

- **5-Band Parametric EQ**
  - Professional-grade 5-band parametric equalizer
  - Frequency, Gain, Q (bandwidth) control per band
  - Visual frequency response curve with draggable control points

- **Sleep Prevention Setting**
  - Optional "Keep Screen On" setting in Recording Settings
  - Prevents device sleep during long recording sessions

- **Enhanced Microphone Recognition**
  - Better USB-C and Lightning audio interface detection
  - Improved external mic identification

### Changed
- Renamed "Analyze" button to "Auto" (Auto-Record calibration)
- Recording quality analysis now runs automatically after recording stops
- Marker system simplified: Removed manual Good/Bad/Memo markers (kept automatic CLIP/OVER markers)
- 4-Band EQ upgraded to 5-Band Parametric EQ

### Fixed
- Fixed long-duration recording crashes
- Improved audio engine error handling and recovery
- Better resource cleanup on audio route changes
- Thread-safe audio processing with lock-free atomics

### Performance
- Eliminated NSLock usage in real-time audio callback
- Introduced Swift Atomics for lock-free concurrency
- VU ballistics now computed in audio thread (zero latency)

---

## [1.2.0] - 2026-01-24

Professional LUFS metering, enhanced Pro features, and Firebase integration.

### Added
- **LUFS Metering (ITU-R BS.1770-4)**
  - Momentary (400ms), Short-term (3s), Integrated loudness
  - True Peak measurement with 4x oversampling
  - Tap meter to cycle: VU → GR → LUFS → VU

- **Pro Features (In-App Purchase)**
  - 24-bit WAV/BWF export for professional workflows
  - Custom audio presets with full parameter control
  - BWF (Broadcast Wave Format) with embedded metadata

- **BWF Format Support**
  - BEXT chunk with originator, description, time reference
  - Embedded cue markers for DAW compatibility

### Fixed
- Audio route change recovery with retry logic
- USB-C microphone disconnect handling improved
- LUFS analyzer thread safety

---

## [1.1.0] - 2026-01-22

Arm mode, Pre-roll, and Spectrum Analyzer.

### Added
- **Arm Mode** - ARM button to enter waiting state with circular buffer
- **Pre-roll Recording** - 5 seconds of audio captured before record button
- **Real-time Spectrum Analyzer** - FFT-based with 32-band logarithmic scale
- **GR (Gain Reduction) Meter** - Tap VU meter to switch
- **Input Source Badge** - Display current input source
- **In-App Help System** - 10+ help topics with English/Japanese localization

### Changed
- Spectrum tab removed from main navigation (now 2 tabs: Record, Recordings)
- Peak Reset changed to fixed 5-second interval

### Fixed
- Stereo recording now works correctly
- Route change during recording: safe stop + file close

---

## [1.0.0] - 2026-01-21

Initial release.

### Added
- High-quality audio recording (WAV 16-bit PCM, 48kHz)
- Stereo recording on supported devices
- Professional signal chain: Noise Gate → EQ → Compressor → Limiter
- Four presets: Flat, Studio, Studio+, Live
- VU meter with peak hold and clip detection
- Smart Context Markers (GOOD, BAD, MEMO, CLIP)
- Clip Guard with haptic feedback
- Recording management with Share Sheet export
- English and Japanese localization

---

[Back to Support Page](/)
