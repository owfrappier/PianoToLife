# PianoToLife — User Manual

*Version 10.3.2 · [Version française](MANUEL.md) · Sampler mapping: [Sampler Manual](SAMPLER_MANUAL.md)*

PianoToLife makes a virtual piano **behave like a real one**: the strings that ring in sympathy, the sustain pedal
and half pedal, the dampers, the release, the una corda, the noises of the mechanism. This manual explains how it
works, how to set it up, and what every section of the window does.

---

## Contents

1. [One modelling engine, two sources of sound](#1-one-modelling-engine-two-sources-of-sound)
2. [Why the sampler uses pedal-up samples only](#2-why-the-sampler-uses-pedal-up-samples-only)
3. [Installation and first start](#3-installation-and-first-start)
4. [HOST mode: setting up your piano](#4-host-mode-setting-up-your-piano)
5. [SAMPLER mode](#5-sampler-mode)
6. [Piano Models: calibrating the resonance](#6-piano-models-calibrating-the-resonance)
7. [Sympathetic resonance](#7-sympathetic-resonance)
8. [Pedals](#8-pedals)
9. [Release and dampers](#9-release-and-dampers)
10. [Keyboard, velocity and the MIDI Monitor](#10-keyboard-velocity-and-the-midi-monitor)
11. [Noises, body, room and output](#11-noises-body-room-and-output)
12. [Presets, MIDI player and views](#12-presets-midi-player-and-views)
13. [CPU and performance](#13-cpu-and-performance)
14. [Troubleshooting](#14-troubleshooting)

---

## 1. One modelling engine, two sources of sound

PianoToLife has two modes, chosen at the top of the window:

| Mode | Where the strike comes from | What PianoToLife adds |
|---|---|---|
| **HOST** | A piano plug-in you already own (AU or VST3), hosted inside PianoToLife | The whole modelling engine |
| **SAMPLER** | Your own piano samples, played by PianoToLife's built-in sampler | The same modelling engine |

In both modes, the **same engines** run on the sound:

- **Sympathetic resonance** of every free string, driven by the real audio of the notes you play;
- **Sustain pedal** and **half pedal**, pedal catch, sostenuto, re-pedalling;
- **Dampers and release**: the felt landing on a string that still vibrates, following your release speed;
- **Una corda** (soft pedal);
- **Key and pedal noises**, **Felt-Contact**, **BODY**, **Ambience**, **Piano Comp**, **Reverb** and the **Output
  Ceiling**.

On a real grand, sustain resonance and sympathetic resonance are **one single phenomenon**: the pedal only lifts
every damper at once.

| What you do | What happens inside the piano |
|---|---|
| One key held | One string is free to vibrate |
| A chord held | A few strings are free |
| Pedal down | Every string is free |
| Half pedal | Every string is free, but still lightly touched by the dampers |

PianoToLife models exactly that, with one engine, which is why transitions, half pedalling and chords caught in the
pedal sound natural.

---

## 2. Why the sampler uses pedal-up samples only

Because everything around the strike is **modelled**, the sampler only needs the **pedal-up notes** of a piano:

- **Pedal-down samples** contain the resonance of the whole instrument, *frozen at the moment of the recording*.
  PianoToLife builds that resonance live, from the strings that are really free at each instant. Playing both would
  put the resonance there twice, and the frozen one would not follow your pedalling.
- **Release samples** would duplicate PianoToLife's dampers, which follow your release speed and the pedal.
- **Pedal noises and resonance samples** are modelled too, following the pedal's travel and speed.

This is also why, in HOST mode, PianoToLife asks you to turn these options off in your piano (see
[section 4](#4-host-mode-setting-up-your-piano)). The result is a **hybrid**: the realism of real recordings for the
strike and its tone, and a live, physical behaviour for everything that happens around it, without hundreds of
extra samples. A 3- to 6-layer pedal-up library is enough.

To build a piano from samples (import, mapping, layers, microphones, streaming), see the
**[Sampler Manual](SAMPLER_MANUAL.md)**.

---

## 3. Installation and first start

| | macOS | Windows |
|---|---|---|
| System | macOS 14 or later, Apple Silicon | Windows 10 / 11, 64-bit |
| Formats | Audio Unit, VST3, Standalone | VST3, Standalone (ASIO) |
| Hosted piano | AU or VST3 built for Apple Silicon | x64 VST3 |

Install the package from the [Releases](../../releases/latest) page, then open PianoToLife in your DAW (as an
instrument) or as the standalone application. In the standalone, choose your audio device and MIDI keyboard in the
audio settings.

---

## 4. HOST mode: setting up your piano

1. Choose your piano plug-in in the **HOST** section (scan, list, Add VST3) and open its window.
2. **In the hosted piano**, turn off:
   - every *sympathetic*, *string*, *sustain* or *pedal resonance* option;
   - all **reverb, effects and compression** (rooms, ambience, EQ, limiters, wideners): PianoToLife listens to the
     **dry** sound to drive the strings;
   - what the **pedal mode** asks for (see below).
3. Set **Undamped Keys Above** to the last key with a damper on that piano (often G6 on a concert grand); with an
   extended-bass piano, drag the left handle of **Sustain Free To** down to C0.
4. Load or capture the **Piano Model** of that piano ([section 6](#6-piano-models-calibrating-the-resonance)).

Need a room or compression? Use PianoToLife's own **Piano Comp** and **Reverb**: they come after the resonance, so
the whole instrument goes through the same room.

### Pedal modes (HOST)

| Mode | The piano receives the pedal? | Use it for | Turn off in the piano |
|---|---|---|---|
| **Host Sustain** (default) | No: PianoToLife holds the notes | Most pianos, including those whose sustain samples cannot be turned off | Key / release noise, sympathetic resonance |
| **Host Sustain (stacked)** | No | Pianos that play a damper or release noise at each restrike | Same as Host Sustain |
| **Host Sustain (strict)** | No | Scripted libraries that ignore a softer restrike of a held note | Same as Host Sustain |
| **Pass-through** | Yes: the piano handles its dampers | Pianos whose own half pedal and re-pedalling you prefer | Sustain samples, sympathetic resonance (keep half pedal and re-pedalling) |

In Host Sustain, a note struck again under the pedal behaves like a hammer on a string that still vibrates: a softer
strike rings over the previous one, a strike at least as loud replaces it, and every strike gets its own Note Off.
Changing pedal mode lifts the pedals until you move the pedal again.

---

## 5. SAMPLER mode

Switch **HOST / SAMPLER** to SAMPLER: the hosted piano is set aside and PianoToLife's sampler plays your sample
sets. Choose a set in the list, adjust its microphones and streaming in **MIX**, and map new pianos in **EDIT**.

In SAMPLER mode, the pedal always works as **Host Sustain**, with a native **half pedal** on the voices themselves,
and the una corda is always **Simu**. Your HOST choices are kept for when you go back.

Everything about building a set is in the **[Sampler Manual](SAMPLER_MANUAL.md)**.

---

## 6. Piano Models: calibrating the resonance

The resonance follows the exact partials of each string, from a **Piano Model** (`.srpiano`) of the piano you play.
**Capture a model for each piano you use**: with another piano's model, many strings no longer match.

**Capture** plays the 88 notes pedal up, one by one, analyses their partials, tuning, inharmonicity and decay, and
records short strikes at up to 8 velocities placed in the middle of the piano's real layers (about 35 minutes, done
once). It works on a hosted piano and on a sample set.

Before capturing:

- set the piano **as loud as possible without clipping** (**LEVEL TEST** plays A0, C2, C4, C6, C8 at velocity 127
  and tells you);
- **no reverb, compression or effect**, nothing but the plain note (release samples, resonance, noises off);
- the piano's own **velocity curve linear**;
- preferably the **close microphones** (use PianoToLife's Ambience for the hall).

Every model is matched to the same resonance level when it is loaded; each keeps its own character. A model of a
concert grand is included.

**Layer detector**: plays a note at the 127 velocities and lists the piano's real velocity layers (export as text).

---

## 7. Sympathetic resonance

The main controls:

| Control | What it does |
|---|---|
| **SYMPATHETIC RESONANCE** on / off | The whole engine (resonance and PianoToLife's release) |
| **Resonance Level** | How much the free strings ring |
| **Harmonic Balance** | Colour of the resonance (low partials ↔ high partials) |
| **Fullness** / **Shimmer** | How much the free strings answer on their low / upper partials |
| **Undamped Keys Above** | Last key with a damper: the strings above ring freely, never damped |
| **Sustain Free From / To** | Range of strings freed by the pedal |
| **Inharmonicity** | Stretch of the partials, as measured on the piano |
| **Max Free Strings (CPU)** | How many strings may resonate at once |
| **Enable Multicore Processing** | Shares the resonance between CPU cores (same sound) |

The detailed settings fold away in a drawer; each reads **Default** at its default value, and **DEFAULT** resets
them all. **Full Piano / Piano Only / PianoToLife DSP Only** lets you hear the piano alone or only what PianoToLife
adds.

**Silent Key** (next to SYMPATHETIC RESONANCE): a silent key press lifts the damper without playing a note, so the
string is free to resonate. **≤ 1** (default), **≤ 2**, **≤ 3** = notes at that velocity or lower; **Disklavier /
N1** = polyphonic aftertouch 127 / 0; **Off** = none.

---

## 8. Pedals

- **Half pedal**: resonance and damping follow the pedal continuously. **Half Pedal Damping Start / Full** set where
  the dampers start and stop touching the strings.
- **Pedal Catch**: press the pedal just *after* the notes and the strings still sounding feed the freed strings, at a
  level that depends on how quickly you catch them. **Held**: the bloom of keys still held when the pedal goes down.
- **Pedal Release Time** (default 80 ms): the fastest a released pedal can come back up, so an on / off pedal never
  stops the sound abruptly.
- **Sustain: Progressive / Switch**: Switch for pedals that should act as on / off (64 and above = down).
- **Sostenuto** works in every mode.
- **Una corda**: **Simu** makes the soft pedal work with any piano (a softer, rounder note adapted to each piano, and
  the halo of the unstruck string); **BP** sends the pedal to the piano for its own una corda samples.

---

## 9. Release and dampers

When a key is released or the pedal comes up, the felt lands on a vibrating string and damps it progressively:
light contact silences the upper partials first, firm contact stops every partial together.

| Control | What it does |
|---|---|
| **Release Level** | PianoToLife's release (recommended: turn the release off in your piano and keep this on). Untick it to keep your piano's own release, or blend both |
| **Release Decay** | Length of the release tail (longer in the bass) |
| **Release Weights** | Colour of the release (100 % = partials as recorded) |
| **Ring** | Energy passing into the undamped treble strings and the duplex scale |
| **Damper Damping** / **Slope** | How fast the dampers stop the strings, longer in the bass, shorter in the treble |
| **Felt-Contact** | The felt touching a string that still vibrates, with its own volume and colour |

---

## 10. Keyboard, velocity and the MIDI Monitor

### Keyboard modes and release velocity

| Keyboard mode | For |
|---|---|
| **Standard** (default) | Every keyboard: each release is the calibrated normal release |
| **Release Velocity 1-127** | Keyboards that measure how fast you release the keys |
| **Kawai VPC1** | The VPC1, whose release velocity stops around 100 and easily drops to 1 |
| **N1X or others** | Yamaha hybrids that send the key position by aftertouch while the key comes back |
| **Yamaha P-525** | The P-525's release timing |

In every mode but Standard, the release goes through the **Keyboard Note-Off Floor** (1–16, default 16: the value
of your slowest release, never an endless one) and the **Keyboard Note-Off Curve**, on PianoToLife's internal 0–64
scale (64 = a normal release; from a 1-127 keyboard, 64 and above = normal). **Note-Off to Host** chooses what the
hosted piano gets: **Var** (the same value), **64** (always normal: no double treatment), **127**, or **Raw** (what
the keyboard sent). **Disable Aftertouch** / **Disable CC19** keep those messages away from the piano.

### Velocity

The **VELOCITY** curve is a line of points you can drag (double-click to add or remove one). **CURVE** quickly
writes a smooth curve; **COPY** / **PASTE** exchange it as text: `Velocity = [x0, x1, …; y0, y1, …]` (played →
sent). **CAL** calibrates the dynamics of your piano on a concert grand, a grand or an upright, from the layer
detector's result.

### MIDI Monitor

Three columns on the same line: what your **Keyboard** sends, the release velocity PianoToLife's **Engine** reads
(with the measured release time on an N1X or P-525), and what goes to the **Host**. Differences are highlighted;
**Export...** saves a text file — perfect to report a keyboard that behaves in its own way.

---

## 11. Noises, body, room and output

| Section | What it does |
|---|---|
| **Key Noise** (GRAND / UPRIGHT) | The wooden key action: hammer back on its rest, key landing, repetition |
| **Pedal Noise** | Wooden thumps, felts on the strings and freed bass strings, following the pedal's travel and speed |
| **BODY** | The perceived size of the piano (left of SOFT): each note's fundamental raised or lowered, in HOST and SAMPLER |
| **Ambience** | A hall around the resonance and release, when you play with close microphones |
| **Piano Comp**, **Reverb** | Placed after the resonance, so the whole instrument goes through them |
| **Output Ceiling** | Transparent true-peak safety limiter, with TRUE PEAK MAX, LUFS and the limiter's meter (LIM) |

---

## 12. Presets, MIDI player and views

- **Presets** keep every setting; SAMPLER presets are marked `[SAMP]` and carry the sample mapping and the resonance
  model. Double-click a preset (standalone) or drop it on the window.
- **MIDI player** (standalone): load, play, record and save MIDI, and bounce to WAV — to compare settings on exactly
  the same performance.
- **Compact view**: fold the interface into a small bar while you play.
- **Damper mechanics view**: a live view of the dampers and strings (held keys in orange), at no CPU cost.
- **Accessibility**: the interface works with screen readers (Narrator / NVDA, VoiceOver) and from the keyboard.

---

## 13. CPU and performance

The CPU load shown by your DAW **includes the hosted piano**. The heaviest case is a long glissando with the pedal
held (hundreds of partials ringing). What matters is **no crackles and no overload message**. If you hear crackles:
raise the buffer size, turn on **Enable Multicore Processing**, then lower **Max Free Strings (CPU)**. In SAMPLER
mode, see also the streaming settings in MIX ([Sampler Manual](SAMPLER_MANUAL.md#8-the-mix-window-microphones-and-streaming)).

---

## 14. Troubleshooting

| Problem | Solution |
|---|---|
| The resonance is weak or sounds wrong | Capture a Piano Model of *this* piano; check that the piano's own resonance and effects are off |
| The resonance sounds doubled or frozen | Turn off the piano's sustain / pedal-down samples and its own resonance (or use Host Sustain) |
| Release noises at the wrong moment | In Host Sustain, turn off the piano's key / release noise |
| Notes ring on after a slow key release | Keyboard Note-Off Floor (16 = safest); check the keyboard mode in the MIDI Monitor |
| A silent key plays | Silent Key list; check the velocities in the MIDI Monitor |
| Clipping | LEVEL TEST; Output Ceiling; lower the piano's volume |
| Crackles | See CPU and performance |

A keyboard or a piano that behaves in its own way? Please contact me at
[olivier.frappier@live.fr](mailto:olivier.frappier@live.fr) with an explanation (a MIDI Monitor export is perfect).
