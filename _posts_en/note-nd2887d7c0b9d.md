---
title: "Light Memory and FET Violence on iPhone: The Madness of Dual-Stage Compression Beyond a Simple Recorder"
date: 2026-01-22
kind: tech
tags: [1Take, compression, LA-2A, 1176, audio]
summary: "The optical compression of LA-2A and the FET compression of 1176. How 1Take recreates the 'nonlinear aesthetics' of vintage gear."
canonical_url: "https://note.com/hakaru/n/nd2887d7c0b9d"
---

## Introduction

I'm the developer of 1Take. In my previous article, I covered the basics of compression, but this time I'm diving a bit deeper.

When designing 1Take, my benchmark wasn't the latest digital plugins. It was the physical behavior of the 1960s—when vacuum tubes and early transistors created "musical magic."

Why can't Voice Memos satisfy us? Because the "nonlinear aesthetics" that should be there is missing. Let me tell you about the "texture" that 1Take recreates on iPhone—something only gear nerds care about, but critically important for musicians.

---

## 1. The Nonlinear Breathing of the T4 Cell: Studio Mode Inheriting LA-2A

The model for the "Studio" preset is the undisputed king of optical compressors: **Teletronix LA-2A**.

### Deep Dive: The Romance of Bulb and Photocell

The heart of the LA-2A is the "T4 optical attenuator," combining a light bulb and photocell. When sound gets louder, the bulb inside glows, and the "photoconductor cell" detects that light to reduce volume. Magic happens in that moment when electricity converts to light.

### 1Take's Approach

I recreated the LA-2A's characteristic "dual-stage release" that slowly returns after being hit. After a big peak, it floats back over several seconds, while responding quickly to subtle sounds. This "breathing" is why vocals "float above" the mix.

**Check this**: Watch how the GR meter needle returns with a "sticky" feel, as if it has a mind of its own. Not sure what it's useful for, though.

---

## 2. FET's Electric Shock and Distortion Edge: Studio+ Mode's Destructive Power

"Studio+" models the 1967 monster: **UREI 1176**.

### Deep Dive: The "All Buttons In" Aesthetics of 0.00002 Seconds

The 1176's biggest feature is its insane attack speed from using FET (Field Effect Transistor) as the control element. At its fastest: 20 microseconds. It practically sculpts the "attack" of sound itself.

### 1Take's Approach

When you think 1176, you think "All Buttons In" mode—pressing all ratio buttons simultaneously. Studio+ also simulates that distinctive **"aggressive saturation."**

The default preset isn't that extreme, but the Pro version lets you go wild. Can't beat the real thing, though.

**Listen for this**: The "BANG!" explosion when hitting a snare. The sound doesn't get smaller—high-frequency harmonics rise, and the sound comes "forward." We extract that violently punchy FET character from iPhone's tiny microphone input.

---

## 3. Comp A→B Serial Patching: Recreating Classic Studio Technique

If you looked at 1Take's internal signal flow and thought "hmm?"—you're sharp. 1Take chains two compressors in series.

```
Input → [Comp A: Peak Tamer] → [Comp B: Body Builder] → Output
```

Apparently this is a proven patch passed down through legendary studios. There's also a parallel version called "New York something," but I don't really know the details.

- **Comp A (1176-style)**: Fast attack to "discipline" sudden peaks (wild drums, vocal accents) in milliseconds.
- **Comp B (LA-2A/VCA-style)**: Adds "density" to the signal Comp A has tamed, giving rich body with slow release.

People who know the real hardware probably think I'm talking nonsense, but it's a challenge to see how far we can go with limited features.

---

## 4. The GR Meter's "Min (Yellow Line)" Is the Engineer's Eye

Finally, let me talk about the UI detail I'm most proud of. 1Take's GR meter has a **"Min (yellow line)"** that holds the maximum compression over the last 5 seconds.

Gear nerds know how crucial that peak needle moment is.

> "That take—the 1176 (Studio+) was grabbing 12dB on the chorus high note. But since the LA-2A (Studio) release is smooth, it didn't fall apart musically."

I wanted to create that "dialogue with the gear" recording experience on iPhone.

Where that yellow line points—that's where the "heat" of your performance is recorded.

---

## Conclusion

The greatness of vintage gear isn't in spec sheet numbers—it's in that "clumsy yet musical behavior."

**1Take aims to trap analog "fluctuation" and "passion" inside the cold digital device that is iPhone.**

---

- [Download on App Store](https://apps.apple.com/jp/app/1take/id6757945099)
- [Support Page](/)
- [Privacy Policy](/privacy)

---

*Original article: [note.com](https://note.com/hakaru/n/nd2887d7c0b9d) (Japanese)*
