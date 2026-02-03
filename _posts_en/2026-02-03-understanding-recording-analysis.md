---
title: "Deep Dive: How 1Take's Recording Analysis System Works"
date: 2026-02-03
kind: technical
tags: [1Take, LUFS, audio analysis, recording, loudness]
summary: "A technical look at 1Take v1.3.0's Recording Analysis System - how it measures audio quality using broadcast-standard algorithms and what each metric means for your recordings."
---

## Introduction

With 1Take v1.3.0, we introduced a powerful Recording Analysis System that automatically evaluates your recordings using professional broadcast standards. But what do all these numbers mean? And how can you use them to improve your recordings?

In this article, we'll break down the technology behind the analysis and explain how to interpret each metric.

---

## The Science Behind Audio Analysis

### ITU-R BS.1770-4: The Broadcast Standard

1Take's analysis engine is built on **ITU-R BS.1770-4**, the international standard used by broadcast networks worldwide. This isn't just marketing speak—it's the same measurement algorithm used by:

- Netflix and streaming services for content delivery
- Radio and TV broadcasters for compliance
- Mastering engineers for loudness normalization
- Apple Music and Spotify for loudness matching

Why does this matter? Because your iPhone recordings are being measured against the same standards as professional productions.

---

## Understanding Each Metric

### 1. Peak Level (dBFS)

**What it is:** The absolute maximum sample value in your recording.

**How to read it:**
- **0 dBFS** = Digital maximum (clipping)
- **-1 to -3 dBFS** = Very hot, risk of clipping
- **-6 to -12 dBFS** = Ideal for most recordings
- **Below -20 dBFS** = Too quiet, noise may be an issue

**Pro tip:** 1Take's Clip Guard automatically marks moments that hit 0 dBFS. If you see CLIP markers, those sections may have digital distortion.

### 2. RMS Level (dBFS)

**What it is:** Root Mean Square—the "average" loudness over time. More representative of perceived volume than peak.

**How to read it:**
- **-10 to -14 dBFS RMS** = Loud, punchy (rock, EDM)
- **-14 to -18 dBFS RMS** = Balanced (most music)
- **-18 to -24 dBFS RMS** = Dynamic (classical, jazz)
- **Below -30 dBFS RMS** = Likely too quiet

### 3. Crest Factor (dB)

**What it is:** The difference between Peak and RMS. Measures how "dynamic" your audio is.

```
Crest Factor = Peak Level - RMS Level
```

**How to read it:**
- **3-6 dB** = Heavily compressed (broadcast, podcasts)
- **8-14 dB** = Moderate dynamics (pop, rock)
- **14-20 dB** = Very dynamic (classical, live jazz)
- **Above 20 dB** = Extreme dynamics or quiet passages

**Why it matters:** A very low crest factor might mean your recording sounds "squashed." A very high crest factor might mean inconsistent volume that's hard to listen to.

### 4. LUFS (Loudness Units Full Scale)

**What it is:** The modern standard for measuring perceived loudness. Unlike peak or RMS, LUFS accounts for how human ears actually perceive sound.

1Take measures three types:

#### Momentary LUFS (400ms window)
- Shows loudness right now
- Updates rapidly
- Useful for monitoring while recording

#### Short-term LUFS (3 second window)
- Smoothed loudness over recent seconds
- Good for identifying overall trends

#### Integrated LUFS (entire recording)
- The most important number
- Represents the perceived loudness of your entire recording
- Target values:
  - **-14 LUFS** = Spotify, YouTube, Apple Music target
  - **-16 LUFS** = European broadcast standard (EBU R128)
  - **-24 LUFS** = US broadcast standard (ATSC A/85)

### 5. True Peak (dBTP)

**What it is:** The actual peak level when audio is converted to analog. Digital samples can create inter-sample peaks that exceed 0 dBFS.

1Take uses **4x oversampling** (as specified by ITU-R BS.1770-4) to detect these hidden peaks.

**How to read it:**
- **Above 0 dBTP** = Will clip on playback (bad)
- **-1 dBTP** = Safe maximum for streaming
- **-2 to -3 dBTP** = Conservative, recommended

### 6. Loudness Range (LRA)

**What it is:** The statistical distribution of loudness over time, measured in LU (Loudness Units).

**How to read it:**
- **Below 5 LU** = Very consistent (podcasts, audiobooks)
- **5-10 LU** = Moderate variation (pop music)
- **10-15 LU** = Dynamic (rock, electronic)
- **Above 15 LU** = Very dynamic (classical, film scores)

---

## How the Analysis Works Internally

For the technically curious, here's what happens when 1Take analyzes your recording:

### K-Weighting Filter

Before any measurement, audio passes through a **K-weighting filter**—a two-stage process:

1. **Stage 1: Pre-filter (Shelf)**
   - Boosts high frequencies by ~4 dB
   - Models how we perceive highs as "louder"
   - Center frequency: 1681.97 Hz

2. **Stage 2: RLB High-pass**
   - Attenuates frequencies below 38 Hz
   - Removes inaudible rumble from measurements
   - Makes measurements match human perception

### Gated Measurement

For Integrated LUFS, 1Take uses a **gating algorithm**:

1. Audio is divided into 100ms blocks (with 75% overlap)
2. Blocks quieter than -70 LUFS are ignored (absolute gate)
3. The remaining blocks are averaged for the final measurement

This means silence between notes doesn't unfairly lower your loudness reading.

### True Peak Detection

The 4x oversampling for True Peak uses a **polyphase FIR filter**:

1. Input samples are upsampled 4x
2. A windowed sinc filter reconstructs inter-sample values
3. The maximum absolute value is tracked
4. All processing uses Apple's Accelerate framework (vDSP) for efficiency

---

## Using Analysis Results to Improve

### Recording Too Quiet?

**Symptoms:**
- Integrated LUFS below -24
- Peak level below -18 dBFS
- High background noise relative to signal

**Solutions:**
1. Increase Input Trim in 1Take settings
2. Move closer to the sound source
3. Use a higher-gain external microphone

### Recording Too Loud / Clipping?

**Symptoms:**
- CLIP markers in recording
- True Peak above -1 dBTP
- Peak at 0 dBFS

**Solutions:**
1. Reduce Input Trim
2. Move away from the sound source
3. Use Studio+ preset (has more aggressive limiting)
4. Enable the Maximizer for extra protection

### Dynamics Too Crushed?

**Symptoms:**
- Crest Factor below 6 dB
- LRA below 4 LU
- Recording sounds "flat" or fatiguing

**Solutions:**
1. Use Studio preset instead of Studio+ or Live
2. Reduce compressor ratio in preset settings
3. Raise compressor threshold

### Too Much Dynamic Variation?

**Symptoms:**
- Crest Factor above 18 dB
- LRA above 12 LU
- Recording volume feels inconsistent

**Solutions:**
1. Use Live preset for more compression
2. Lower compressor threshold
3. Practice more consistent mic technique

---

## Auto-Record Calibration

The v1.3.0 update also introduced intelligent calibration for auto-record:

1. **Press the Auto button** while in a quiet room
2. 1Take measures your ambient noise floor
3. The start threshold is set just above the noise
4. Hysteresis prevents false triggers

This means auto-record will start when you begin playing—not when the air conditioning kicks on.

---

## Conclusion

1Take's Recording Analysis System brings broadcast-quality measurement to your pocket. Whether you're recording podcast interviews, band rehearsals, or song ideas, you now have objective data to evaluate and improve your captures.

The best part? It all happens automatically. Just record, and 1Take tells you how it went.

---

- [Download 1Take on App Store](https://apps.apple.com/jp/app/1take/id6757945099)
- [Support Page](/)
- [Privacy Policy](/privacy)
