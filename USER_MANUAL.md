# PianoToLife — User Manual

*Version 10.9.4 · [Version française](MANUEL.md) · Sampler mapping: [Sampler Manual](SAMPLER_MANUAL.md)*

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
- **Key and pedal noises**, **Felt-Contact**, **BODY**, **Recorded Room**, **Piano Comp**, **Reverb** and the **Output
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

1. Choose your piano plug-in in the **HOST** section (scan, list, Add VST3) and open its window (**Show piano** / **Hide piano** once it is loaded, 10.7.1: the piano stays loaded).
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
records short strikes at up to 8 velocities placed in the middle of the piano's real layers. It is done once. On a
hosted piano, in the standalone (10.7.0), it is **rendered offline**, as fast as your computer can: the hosted piano
is told it renders offline, as in a DAW's bounce, and if it cannot follow, the capture starts again in real time (in a
DAW it plays in real time). In SAMPLER mode it is **read directly from the samples**, offline, at the centres of the
set's own layers: a few minutes. The progress bar stays until the new model is loaded and AUTO CAL is offered.

Before capturing:

- set the piano **as loud as possible without clipping** (**LEVEL TEST** plays A0, C2, C4, C6, C8 at velocity 127
  and tells you);
- **no reverb, compression or effect**, nothing but the plain note (release samples, resonance, noises off);
- the piano's own **velocity curve linear**;
- preferably the **close microphones** (use PianoToLife's REVERB, ALGO or IR, for the hall).

Every model is matched to the same resonance level when it is loaded; each keeps its own character. A model of a
concert grand is included.

**Layer detector**: plays a note at the 127 velocities and lists the piano's real velocity layers (export as text).
HOST mode only (10.6.3): in SAMPLER mode the layers are known and already placed on the reference by AUTO DYN, so
ANALYSE and EXPORT are hidden.

### Diapason and temperament (10.9.4)

**The resonance is always tuned like the piano you hear.** Each free string follows the tuning of its key, and the
strength with which a note excites another string is computed on the strings as they are tuned now: with a
temperament where a third is pure, its strings ring more, as on a real piano.

**HOST: the diapason of the hosted piano is detected.** The capture measures the A4 of the hosted piano (on its own
sound, to 0.1 Hz) and shows it in **SR A4 Tuning**: a piano tuned at 437 Hz reads 437.0 Hz after the capture. A
Piano Model is stored at A4 = 440 Hz, so it stays right when the diapason changes: change SR A4 Tuning with the
hosted piano's diapason (or link them with **ASSIGN to AU**: then the hosted piano gives the value and PianoToLife
never changes it). When a Piano Model is loaded, SR A4 Tuning goes back to the diapason it was captured at.

**HOST: one Piano Model per temperament.** PianoToLife changes the temperament itself only in SAMPLER mode. If your
hosted piano offers temperaments, choose one there, then capture a Piano Model with it — the resonance then follows
that temperament exactly. Name each model after its temperament (e.g. *My Piano – Werckmeister III.srpiano*). The
**TEMPERAMENT** button (on the SR A4 Tuning row) explains this in HOST mode, with a CAPTURE button.

**SAMPLER: TEMPERAMENT.** The same button opens the temperament of your samples: measured, then changed key by key
without touching the files — see the [Sampler Manual](SAMPLER_MANUAL.md#temperament-and-diapason-1094). A SAMPLER
capture always measures the samples as recorded, whatever the Tune, temperament or diapason set.

**Your Piano Models are still good.** Those captured with the default settings play exactly as before (an older HOST
model is brought to 440 in memory and SR A4 Tuning shows its diapason; the file is not changed). Only capture again a
model made in SAMPLER with SR A4 Tuning, Transpose, Fine Pitch or the Tune of keys changed, or in HOST with SR A4
Tuning not at 440 Hz.

---

## 7. Sympathetic resonance

**The duplex scale and the body are already in the sound.** The duplex (aliquot) sections of a grand ring with every
note: they are part of each piano's recorded signature, in your pedal-up samples (SAMPLER) or in your hosted piano
(HOST). The sympathetic resonance is built from that same sound — the Piano Model capture measures it — so it carries
your own piano's duplex colour, not a generic one added on top. The release simulates it too: as the damper falls,
part of the energy passes into the undamped treble strings and the duplex scale, which keep shimmering briefly.
The **Ring** setting (section 9) brings that duplex shimmer of the undamped keys out more or less.

The main controls:

| Control | What it does |
|---|---|
| **SYMPATHETIC RESONANCE** on / off | The whole engine (resonance and PianoToLife's release) |
| **Resonance Level** | How much the free strings ring |
| **AUTO CAL** (10.5.0, next to Resonance Level) | Calibrates Resonance Level 0 dB on the piano and the resonance model loaded, in about 3 s (A3 held silently, A4 played once; don't play meanwhile). The resonance then keeps the same level compared with the piano's own sound, whatever the piano, its volume, the sample set level or the model. The button is lit while a calibration is in use and the Piano Model line shows it (e.g. AUTO CAL +4.8 dB); click it again any time to recalibrate; Resonance Level still turns it up or down around it. HOST and SAMPLER each keep their own calibration (the right one is used when you change mode). Kept in the preset / session; DEFAULT puts both back to 0. After a capture, PianoToLife offers to run it on the new model. Run it again after changing the piano, its volume or the model |
| **Harmonic Balance** | Colour of the resonance (low partials ↔ high partials) |
| **Fullness** / **Shimmer** | How much the free strings answer on their low / upper partials |
| **Undamped Keys Above** | Last key with a damper: the strings above ring freely, never damped. In SAMPLER, the keys above it on release Auto have no damper either; it is also in the EDIT key panel |
| **Sustain Free From / To** | Range of strings freed by the pedal |
| **Inharmonicity** | Stretch of the partials, as measured on the piano |
| **Max Free Strings (CPU)** | How many strings may resonate at once |
| **Enable Multicore Processing** | Shares the resonance between CPU cores (same sound). Since 10.9.1 it is a setting of your computer: **a preset never changes it**, and a new instance starts with your last choice (a DAW project keeps its own) |

The detailed settings fold away in a drawer; each reads **Default** at its default value, and **DEFAULT** resets
them all. **Full Piano = Piano Only + Half/rel/catch Pedal + Symp Res + Release + Noises + Room** (10.5.3; Room = the Recorded Room, called Ambience before 10.9.3; Half/rel/catch Pedal was called Pedal FX before 10.5.6): light one or more parts to hear
only them - they add up; none lit, or a click on **Full Piano**, = everything. **Half/rel/catch Pedal** = the strings PianoToLife plays
for the pedal (notes held by a half pedal, notes caught late, una corda); **Release** includes the Felt-Contact; **Noises** =
Key and Pedal Noise. The choice is kept in the preset and the session - e.g. one DAW track with Piano Only + Half/rel/catch Pedal (your
favourite microphones), a second one with the rest (from closer microphones). Comp, Reverb, EQ and Ceiling stay on.

**Silent Key** (next to SYMPATHETIC RESONANCE): a silent key press lifts the damper without playing a note, so the
string is free to resonate. **≤ 1** (default), **≤ 2**, **≤ 3** = notes at that velocity or lower; **Disklavier /
N1** = polyphonic aftertouch 127 / 0; **Off** = none.

**PANIC** (10.4.2, between Silent Key and DEFAULT): stops everything that sounds at once — stuck notes, the resonance,
the sampler's voices, the room, the caught strings (10.6.2) and the MIDI player — and sends All Notes Off, All Sound
Off and the pedals up to the hosted piano.

**A playback starts from a clean piano** (10.6.2): when your DAW starts playing or jumps to another place (cursor moved,
cycle), and at the standalone's PLAY / BOUNCE, PianoToLife stops what still sounds and puts the pedals up, then takes
the pedals the DAW sends: the same passage always sounds the same, wherever you start it. Live playing is unchanged.

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
- **Una corda LEVEL / TONE** (10.8.0): **click the SOFT pedal** in the damper mechanics view (it reads *settings*).
  **LEVEL** sets how much quieter the soft pedal makes the notes, **TONE** how much darker (SAMPLER only: in HOST the
  hosted piano's sound cannot be filtered note by note). 0 = as measured on a concert grand, −100 % = no change,
  +100 % = twice; LEVEL also sets the ring of the unstruck string. *settings* is written in bold when one of them is
  not at 0, and greyed with **BP**. Kept in the preset; the pedal **DEFAULT** puts them back to 0.

---

## 9. Release and dampers

When a key is released or the pedal comes up, the felt lands on a vibrating string and damps it progressively:
light contact silences the upper partials first, firm contact stops every partial together.

| Control | What it does |
|---|---|
| **Release Level** | PianoToLife's release (recommended: turn the release off in your piano and keep this on). Untick it to keep your piano's own release, or blend both. In HOST mode the pedal keeps its own strings even when this is off (10.5.3): the notes held by a half-lifted pedal die away naturally and a late pedal still catches the notes - only PianoToLife's release sound is gone (the CPU stays about the same) |
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
the keyboard sent). **Disable Aftertouch** / **Disable CC19** keep those messages away from the **hosted piano
only**: PianoToLife's engine (silent keys, N1X / P-525 release) and the MIDI recorder always see them.

### Velocity

The **VELOCITY** curve is a line of points you can drag (double-click to add or remove one). **CURVE** quickly
writes a smooth curve; **COPY** / **PASTE** exchange it as text: `Velocity = [x0, x1, …; y0, y1, …]` (played →
sent). **CAL** calibrates the dynamics of your piano on a concert grand, a grand or an upright, from the layer
detector's result. The strip on the left of the graph shows the piano's real layers (orange = never reached by this
curve). Since 10.7.0 a layer found within the Silent Key velocities (never sent) is shown in **grey**, is not counted
as "not reached", and CAL gives the keyboard to the real layers only.

**Large curve** (10.8.0): the small icon next to *sent* opens the same curve in a large, resizable window — easier for
fine adjustments. Both stay in step; the icon (or the window's close button) closes it.

**KEYBOARD range** (10.8.0), at the bottom of the large curve: many keyboards never send 127 (or never go very low), so
the top of a curve — the loudest layers of a calibrated CAL curve — is out of reach. Give PianoToLife the velocities
your keyboard really sends: type **min** / **max**, or click **LEARN**, play your softest and your loudest notes, then
**DONE**. They are stretched onto the whole curve, before CURVE and the points: every layer is reached again, and the
curve itself does not change. Live playing only (MIDI files, ANALYSE and AUTO CAL are not touched); the Silent Key
velocities are left alone. **FULL** = back to 1–127 (nothing changed), as do the velocity **DEFAULT** and ALL DEFAULT.
It belongs to your keyboard, not to the piano: it is kept for this computer, whatever the preset. When it is not
full, the small curve shows *keyboard min-max*.

### Real piano repetition (REP)

On a real piano, no two strikes sound exactly the same, even at the same velocity. A sampled piano replays the very
same recording at every strike — the "machine-gun" effect of fast repeated notes. The old cure of sample libraries
is **round robin**: several recordings of every note at every velocity, played in turn — heavy, and rarely complete.
**REP** (below CAL: **Off / Grand D / Grand B / Upright**) simulates the repetition of a real piano instead, with the
strike-to-strike differences measured on the chosen reference piano:

- **SAMPLER**: every strike gets its own small differences of level, brightness and decay, a slightly different
  attack in the bass and middle, a tiny detune in the bass; a key struck again while it still sounds (pedal down,
  fast repetitions) builds up as on the reference.
- **HOST**: the hosted piano makes the sound, so only the velocity varies (about 1, at most 3; never out of its
  velocity layer, never on a silent key).

Off by default; saved in presets and sessions (older ones open with REP Off); off while capturing or measuring.
Choose the reference closest to your piano. For a piano that already varies its strikes (a modelled piano, or a
library with round robins), leave REP Off.

### MIDI Monitor

Three columns on the same line: what your **Keyboard** sends, what PianoToLife's **Engine** reads — the release
velocity of each Note Off (with the measured release time on an N1X or P-525), the aftertouch and CC19 — and what
goes to the **Host**. Differences are highlighted;
**Export...** saves a text file — perfect to report a keyboard that behaves in its own way.

---

## 11. Noises, body, room and output

| Section | What it does |
|---|---|
| **Key Noise** (GRAND / UPRIGHT) | The wooden key action: hammer back on its rest, key landing, repetition |
| **Pedal Noise** | Wooden thumps, felts on the strings and freed bass strings, following the pedal's travel and speed |
| **BODY** | The perceived size of the piano (left of SOFT): each note's fundamental raised or lowered, in HOST and SAMPLER. Not an EQ: a small bell follows **each note that sounds**, on its own fundamental (keys and pedal followed). Why it helps: on a real piano the fundamental is radiated by the whole soundboard and builds up with distance; close microphones catch mostly the upper partials and the hammer, so a recorded piano often sounds bright but a little hollow. BODY gives back that presence, note by note; and in a mix the piano stands out without muddying the low end, since only the notes being played are raised (an EQ would raise everything in that band). In SAMPLER mode, **AUTO BODY** (10.9.3, EDIT > DRY / DENOISE / BODY) goes further: it makes the fundamentals of the samples coherent, layer by layer and key by key, written into the -dry ([Sampler Manual](SAMPLER_MANUAL.md)) |
| **Recorded Room** (called Ambience before 10.9.3) | Right under SYMPATHETIC RESONANCE. **The room recorded in your samples**, detected by AUTO CAL and simulated for everything PianoToLife adds (resonance, release, noises), so that it blends with the piano — never around your piano's own sound, which already carries it. **It is not a reverb**: to put the whole instrument in a hall, use **REVERB** (ALGO or IR); a piano made dry (DRY) has no recorded room left (Small). **Room**: Small, Medium, Default, Hall or **Auto** (10.8.0, see below). The slider goes from −6 to +6 dB around Default (10.8.0) |
| **Piano Comp**, **Reverb** | Placed after the resonance, so the whole instrument goes through them |
| **Reverb ALGO \| IR** (10.9.2) | Beside REVERB's DEFAULT. **ALGO**: PianoToLife's Piano Hall. **IR**: a convolution reverb with an **impulse response** of your choice (a real hall, a plate, a vintage reverb unit...). Click **IR**: choose an IR, **LOAD IR...** (a WAV, AIFF or FLAC you downloaded: it is copied into the `Impulse Responses` folder of your sample sets folder, and chosen), or **Open IR folder** (folders inside it, up to three levels, become sub-menus). Mono, stereo and **true stereo** IRs (4 channels, or a pair of files "... L" / "... R": choose either, both are taken) are read, at any sample rate, up to 10 s; B-format (ambisonic) files are not. The level is matched to the Piano Hall. Choosing an IR sets DECAY to the IR's own length and DAMP to 0 (the IR as recorded); then **DECAY** shortens its tail and **DAMP** makes its treble die sooner; MIX, PRE and LEVEL work as usual. No latency. A preset keeps the IR's name: if the file is missing, the Piano Hall plays and the button reads **IR ?**. DEFAULT = ALGO. Free IRs: [Voxengo](https://www.voxengo.com/impulses), [OpenAIR](https://www.openair.hosted.york.ac.uk/?page_id=2) (real halls, use the stereo files), [Airwindows](https://airwindows.com/airwindows-impulses); commercial libraries delivered in WAV work too |
| **EQ1 / EQ2** (10.4.2) | Click **EQ** under REVERB: the EQs take the place of COMP / REVERB (the same button brings them back). **EQ1 BEFORE FX** works before COMP and REVERB, to shape the tone of the piano; **EQ2 AFTER FX** works at the very end, before the Ceiling, to correct headphones. Each: **draw it on the curve** (double-click = a new point, drag = frequency and gain, mouse wheel on a point = its width Q, right-click = remove), PREAMP, RESET = flat, or **LOAD** a preset — a `ParametricEQ.txt` from AutoEq (oratory1990 measurements, Harman target) or an Equalizer APO file; load headphone presets in EQ2 (switch it off for a bounce or on loudspeakers). Up to 20 points each. Kept in the preset and the session |
| **Output Ceiling** | Transparent true-peak safety limiter, with TRUE PEAK MAX, LUFS and the limiter's meter (LIM). Since 10.8.1 **CEILING, OUTPUT, VOL and the level meter** sit together on the DAMPER MECHANICS title line, in the order of the sound. Since 10.9.1: **click once on CEILING to type a value**, double-click = default |
| **VOL** (10.7.0) | Listening volume, −40 to +12 dB, just before the Ceiling (which still protects). **Click once to type a value** (10.9.1), double-click = 0 dB. **Since 10.9.2 it is saved with the preset, the instrument and the session**, as the Ceiling (presets saved before open at 0 dB); ALL DEFAULT puts it back to 0 dB. Set the real level of each instrument where it belongs — the microphones and LEVEL in SAMPLER mode, the hosted piano's own volume in HOST mode — and keep VOL for the listening level |
| **OUTPUT** (10.8.1; SWAP L-R since 10.7.0) | **STEREO** as it is; **SWAP** left and right swapped (the audience's side instead of the pianist's); **MONO** left and right summed (for coincident or mono recordings); **MONO L** / **MONO R** one side only, on both outputs — with spaced microphones the sum sounds hollow (phase holes), one side does not: try both, keep the fuller one. For a single speaker, a stage monitor or a mono PA. It depends on your headphones / speakers, not on the piano: **loading a preset or an instrument never changes it**, it comes back at restart and with the session; ALL DEFAULT puts it back to STEREO |
| **Level meter** (10.8.1) | What really goes out, after VOL, OUTPUT and the Ceiling: L and R bars, body = RMS (what you hear), bright line = peak, small mark = the highest peak (1.5 s), red above −1 dBFS. Marks at −24, −12, −6 and 0 dBFS. Light on CPU |

### Recorded Room AUTO CAL: one room for the whole piano (10.8.0)

Your piano was recorded in a room, and that room is part of its sound. PianoToLife adds sounds the recording does not
contain: the sympathetic resonance, the release, the key and pedal noises. If they stay dry — or ring in another room
than the piano — the ear hears two spaces laid on top of each other: the sound is less natural, and the piano's own
room gets blurred.

**AUTO CAL** (next to Recorded Room, right under SYMPATHETIC RESONANCE) listens to your piano's room **in its own sound**:
PianoToLife plays a few high notes held and listens *between* their partials, where only the room rings. It finds how
long the room rings and how loud it is, and sets the **Room** to **Auto**. Everything PianoToLife adds then rings in
the same room as your piano, at the same level. Your piano's own sound is never touched. The result is often heard at
once: the piano's room comes out, instead of being masked.

- **Run it once per piano** (and again after changing its microphones or its own reverb). A few seconds offline in
  the standalone, about 25 s in a DAW; don't play meanwhile. The button stays lit once the piano was analysed.
- **The level found is shown in the Room** (e.g. *Auto +3 dB*). The Recorded Room slider still sets more or less around
  it: lower it a little if you find the room too present — often the case with very clean releases.
- **A very dry piano** (close or closed microphones): no room is found, the Room is set to **Small**. The same for a
  sampled piano whose room was taken out with **DRY / DENOISE** (SAMPLER, 10.9.0): choose the room you want — see the
  [Sampler Manual](SAMPLER_MANUAL.md).
- ***The notes did not fully agree***: the measured notes differ (an old recording, tape hiss...): the result is
  usable, check it by ear.
- **After a Piano Model capture**, PianoToLife offers both AUTO CALs in a row: the resonance level, then the room.

---

## 12. Presets, MIDI player and views

- **Presets** keep every setting. In SAMPLER mode (10.6.0) the presets are the **instruments** (`.ptlset`, beside their
  samples `.wptl`, like Kontakt `.nki` / `.nkx`): see the Sampler Manual. Double-click a preset or an instrument
  (standalone) or drop it on the window.
  **Modified** (10.7.0): a **\*** after the preset's name when a setting differs from the preset loaded or saved.
  Loading another preset, RELOAD, or switching HOST / SAMPLER then asks first: lose the changes, **Save first**, or
  Cancel. Each mode comes back with its own last preset / instrument.
  **SAVE** (10.7.1) saves the current settings over the preset (instrument) shown, with no window; **SAVE AS** saves
  under a new name (SAVE opens it when there is no file yet, e.g. Last Session). **Right-click on the PRESET box**
  (10.7.1): **Rename** the preset shown, or **Move it to the Trash** (never deleted for good; for an instrument, only
  the `.ptlset` - its samples `.wptl` stay). **FOLDER** opens the Presets folder (HOST) or the current instrument's
  folder (SAMPLER).
- **MIDI player / recorder** (standalone): **LOAD MIDI**, **PLAY**, **REC**, **BOUNCE** (WAV, AIFF, FLAC or CAF) — to compare settings
  on exactly the same performance. After REC the take starts on your first note or pedal (pedals already down are
  kept); click REC again and the save window opens; PLAY plays the take at once. LOAD MIDI and the save open the same
  folder. **ENGINE MIDI REC** (under Disable CC19, on by default): the take is written as the engine plays it — the
  converted release in every Note Off (64 = normal, lower = slower), the velocity curve applied, all the aftertouch
  kept (Disklavier / N1 compatible). Off: the raw keyboard input. In PianoToLife it replays in the N1X mode or in
  Release Velocity 1-127.
  **Playlists** (10.4.2): LOAD MIDI opens a menu — load several MIDI files at once, a folder, or an **.m3u** list;
  the pieces follow one another, **◀ / ▶** go to the previous / next one, and the menu can loop the playlist or save
  it as an .m3u. A missing file is skipped. Since 10.7.0 a click on the MIDI line (**2/5 ▾**) opens the list of the
  pieces: choose one. In the LOAD MIDI menu, **Ignore volume, pan, expression, effects and bank changes in MIDI files**
  (10.7.1, on by default): the player leaves out the files' CC7, CC10, CC11, CC91, CC93 and bank changes, so a file
  can no longer change your hosted piano's volume (Kontakt...); what you play on the keyboard is never filtered. BOUNCE records the piece loaded, until its sound has died away (10.5.4: notes still held at the end ring out).
  **BOUNCE options** (10.7.0): after the file, a window sets the **Format** (WAV, AIFF, FLAC — lossless, about half
  the size — or CAF), the **Resolution** (16 or 24 bits, 44.1 kHz) and the **Speed**: **Auto** renders offline, as
  fast as your computer can (SAMPLER: it waits for the disk before each block, exact at any speed; HOST: the hosted
  piano is told it renders offline — if it cannot follow, the bounce is redone in real time); **x4 / x2** hold that
  speed; **x1** is real time. The MIDI line shows the speed, then how it went. The metronome is never in the file.
  You can also **drop MIDI files on the window** (10.6.2): one file, several (a playlist, in the order of their names)
  or an .m3u, as with LOAD MIDI. **II (PAUSE)** (10.6.2): the sound stops where it is and the place is kept; click
  again to go on from there (from a clean piano, with the pedals the file has at that point). PLAY starts from the
  beginning.
  **METRO** (10.4.2): click = metronome on / off (the button shows the tempo); right-click = tempo (30–360 BPM, TAP),
  bar (none, 1/1, 2/2, 2/4, 3/4, 4/4, 5/4, 8/4, 3/8, 6/8, 7/8, 8/8, 9/8, 12/8 — first beat accented, the groups lighter), sound (wood or beep), volume and **count-in**. It is heard only — never in a
  bounce nor in the MIDI take. With the metronome on, REC starts on a bar (after one bar of count-in when ticked) and
  the tempo and time signature are written in the saved MIDI file, so the take sits on the grid of a DAW.
- **Compact view**: fold the interface into a small bar while you play. Since 10.4.2 it also has what serves while
  playing: the MIDI player and METRO (standalone), the chord you play, a lit and clickable keyboard, TRUE PEAK and LUFS,
  and since 10.6.2 the preset list (the instruments in SAMPLER mode). Since 10.6.3 the compact bar is always shown at
  100 %; the view size you choose (90 / 80 %) is for the full window. Since 10.7.0 it also has VOL, since 10.8.1 OUTPUT
  and the level meter, in its right column (see section 11).
- **Damper mechanics view**: a live view of the dampers and strings (held keys in orange), at no CPU cost. Since
  10.4.0:
  - **an 88-key keyboard** under the strings lights up with them; its colour follows the velocity (pale = soft, full
    orange = loud), paler for notes kept by the pedal. **Click it to play**: lower on the key = louder; drag across
    the keys for a glissando. These notes go through the same path as your keyboard (HOST and SAMPLER, MIDI Monitor,
    ENGINE MIDI REC);
  - **the chord you play**, in large letters left of BODY: the keys held and the notes the pedals keep ringing.
    Only chord names are shown (C, Am7, Cmaj7/E…). A chord held in the left hand stays shown while the right hand
    plays a melody over it, and is completed when the melody adds to it.
- **Accessibility**: the interface works with screen readers (Narrator / NVDA, VoiceOver) and from the keyboard.

---

## 13. CPU and performance

The CPU load shown by your DAW **includes the hosted piano**. The heaviest case is a long glissando with the pedal
held (hundreds of partials ringing). What matters is **no crackles and no overload message**. If you hear crackles:
raise the buffer size, turn on **Enable Multicore Processing**, then lower **Max Free Strings (CPU)**. If your DAW
freezes (Windows), untick **Enable Multicore Processing** and please tell me your DAW, its version and your CPU. In SAMPLER
mode, see also the streaming settings in MIX ([Sampler Manual](SAMPLER_MANUAL.md#8-the-mix-window-microphones-and-streaming)).
REP and SOFT / HARD TIMBRE add a few filters per voice in SAMPLER mode: a small cost (a few %).

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
