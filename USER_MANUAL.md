# PianoToLife — User Manual

*Version 11.4.1 · [Version française](MANUEL.md) · Sampler mapping: [Sampler Manual](SAMPLER_MANUAL.md)*

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

1. Choose your piano plug-in in the **HOST** section (SCAN, the list, **Plug-ins...**) and open its window (**Show piano** / **Hide piano** once it is loaded, 10.7.1: the piano stays loaded).

   **Plug-ins...** (10.9.6, called Add VST3 before) manages the list of instruments, as a setting of your computer (not of
   a preset):
   - the VST3 found in the standard folders: pick one to add it without a full SCAN;
   - **Other location...**: a .vst3 or a whole folder anywhere — it is **remembered**, and SCAN looks there too;
   - **Locations scanned**: untick **Standard VST3 folders** to scan only your own locations; click one of your
     locations to forget it;
   - **Remove from the list**: an instrument you do not want (it stays out of the next scans too);
   - **FULL reset SCAN**: everything back to the start (standard folders, your locations forgotten, removed instruments
     back), then SCAN.
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
DAW it plays in real time). **Speed** (11.0.2, in the capture window): **Auto** (as fast as possible), **x4**,
**x2** (offline, slower) or **x1** (real time, safest). If a capture has to be redone or freezes with your hosted
piano, choose a slower speed: the piano has more time to read its samples from the disk. The choice is kept. In SAMPLER mode it is **read directly from the samples**, offline, at the centres of the
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

### NEED NEW SR? and Check by ear (11.1.1)

A small light at the end of the **Piano Model** line tells you whether the model still matches what you play:
**green** = up to date, **orange** = small changes (a new capture is optional), **red !** = capture again recommended,
**grey ?** = the model has no record to compare with (captured before 11.1.1). Hover over it for the details; click it
for the details and **Check by ear**. It costs no CPU (compared once a second, never in the audio).

- **SAMPLER**: the capture now remembers the settings it was rendered with — the set, the microphones' MIX (level, pan,
  width, delay), COLOR and, key by key, the level (BALANCE included) and the left / right balance — and compares them
  with yours. Red: another set, the MIX of a captured microphone or a COLOR changed, or many keys changed (more than 10,
  or one by more than 6 dB). The key tune, the A4 and the temperament are not judged: the resonance follows them.
- **HOST**: the hosted piano and its preset, as at the capture (older models too); for models captured with 11.1.1,
  also the piano's parameters (orange when they changed). Many pianos do not report their preset to the host: after
  changing it, use Check by ear.
- **Check by ear**: 9 keys (E1 to A6) are played silently, in a few seconds, exactly as the capture plays them, and
  compared with the Piano Model: the timbre of each key, the level between the keys and the left / right balance. The
  light then takes the result's colour, and a table of the differences is shown. SAMPLER: anywhere, also in a DAW;
  HOST: in the standalone (the hosted piano rendered offline, as for the capture). A capture cannot start meanwhile.
  Since 11.2.4 it follows SR A4 Tuning and Fine Pitch (a model checked far from its own pitch, at 350 Hz for instance),
  and each check is written key by key to **Stems/last-check-by-ear.txt**.

### Diapason and temperament (10.9.4)

**The resonance is always tuned like the piano you hear.** Each free string follows the tuning of its key, and the
strength with which a note excites another string is computed on the strings as they are tuned now: with a
temperament where a third is pure, its strings ring more, as on a real piano.

**HOST: the diapason of the hosted piano is detected.** The capture measures the A4 of the hosted piano (on its own
sound, to 0.1 Hz) and shows it in **SR A4 Tuning**: a piano tuned at 437 Hz reads 437.0 Hz after the capture. Since 11.1.5 the partials are looked for around the A4 set
before the capture (SR A4 Tuning, Transpose, Fine Pitch), refined on the piano itself: set SR A4 Tuning near the hosted
piano's diapason before capturing a piano tuned far from 440 Hz (e.g. 409 Hz). A
Piano Model is stored at A4 = 440 Hz, so it stays right when the diapason changes: change SR A4 Tuning with the
hosted piano's diapason (or link them with **ASSIGN to AU**: then the hosted piano gives the value and PianoToLife
never changes it). When a Piano Model is loaded, SR A4 Tuning goes back to the diapason it was captured at. **A preset or a session
wins** (11.0.2): its SR A4 Tuning (e.g. 432 Hz) is kept; the model's diapason is used only when it leaves 440 Hz.
Since 11.1.0 a preset or session saved with 11.1.0 or later keeps its SR A4 Tuning whatever it is, 440 Hz included
(without ASSIGN to AU). Since 11.1.6 the end of a capture says the A4 detected when it is not 440 Hz, and the
.srpiano file explains its reference in a "tuningNote" line (a SAMPLER capture keeps the samples' own tuning and
writes it as "referenceA4Hz").

**HOST: TEMPERAMENT** (11.0.2). The **TEMPERAMENT** button (on the SR A4 Tuning row) tells PianoToLife the
temperament set in your hosted piano, so the strings of the resonance follow it **without a new capture** (the hosted
piano itself is not changed):
- **Played in**: the temperament set in the hosted piano — **Original (as captured)** by default (no change: your
  piano and its Piano Model, as before), Equal, historical temperaments, or a **Scala file (.scl)** of 12 notes
  (**LOAD .scl...**), with its **tonic** (the key it is built on);
- **Model captured in**: the temperament the Piano Model was captured in (Equal for most pianos), with its tonic;
- a line shows the 12 offsets in cents applied to the strings. Kept in the preset and the session.

Pure intervals make the resonance stronger, as on a real piano: lower Resonance Level if needed. Most exact of all:
a Piano Model captured in the temperament played (**CAPTURE...**), then Played = Original. Name each model after its
temperament (e.g. *My Piano – Werckmeister III.srpiano*).

**HOST: the tuning of the hosted piano** (11.3.0). In HOST mode, TEMPERAMENT also shows the tuning of the hosted piano,
measured on its Piano Model: how many keys were measured, its A4, the temperament it is closest to, its stretch (C2,
C7) and the keys off its line. **Tune it to** a temperament (with its tonic), set the **Stretch** (100 % = the stretch
it is tuned with) and **FIX KEYS** (each key's own error taken out too), then **EXPORT .txt + .scl...** writes the table
of corrections: a `.txt` key by key, to enter in the hosted piano's own Tune of each key, and the same as Scala
`.scl` + `.kbm` for a piano that loads Scala files. **0.1 cent / 1 cent**: the rounding (some pianos accept only whole
cents). The line under it gives the largest correction. PianoToLife does not change the hosted piano itself.

**MIDI files** (11.3.0): pitch bend, tuning messages (RPN / NRPN, CC 6 / 38 / 96–101) and SysEx in MIDI files are
ignored by default: meant for a sound module, they detuned the piano or made its notes slide (old General MIDI files).
MIDI LOAD's menu: *Ignore pitch bend, tuning (RPN / NRPN) and SysEx in MIDI files*. The keyboard you play is never
filtered.

**MIDI files on one channel** (11.3.1): every event of a MIDI file is played on channel 1, as a DAW's MIDI track does.
Some files put the sustain pedal on another channel than the notes (e.g. the hands on channels 8 and 9, the pedal on 3):
by the MIDI rule that pedal holds no note, and the piano sounded dry while the resonance rang. MIDI LOAD's menu: *Play
every channel of MIDI files on one channel* (on by default). The keyboard you play is never changed.

**"PianoToLife cannot keep up"** (11.3.0): when sound is lost for several seconds (audio blocks not computed in time),
PianoToLife says so, apart from a real change of the sound card's rate, with what to do: a larger buffer (Options >
Audio), the power plan or the charger, other programs closed, the hosted piano's polyphony. *Don't show again* turns
it off.

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

**PANIC** (10.4.2, between Silent Key and DEFAULT; since 11.1.4 also in the compact bar): stops everything that sounds at once — stuck notes, the resonance,
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
writes a smooth curve; **COPY** / **PASTE** exchange it as text: `Velocity = [x0, x1, …; y0, y1, …]` (played → sent). Since 11.1.2 COPY copies the curve as it plays, **CURVE included** (set CURVE to 0 after pasting such a curve back). **CAL** calibrates the dynamics of your piano on a concert grand, a grand or an upright, from the layer
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
| **Recorded Room** (called Ambience before 10.9.3) | Right under SYMPATHETIC RESONANCE. **The room recorded in your samples**, detected by AUTO CAL and simulated for everything PianoToLife adds (resonance, release, noises), so that it blends with the piano — never around your piano's own sound, which already carries it. **It is not a reverb**: to put the whole instrument in a hall, use **REVERB** (ALGO or IR); a piano made dry (DRY) has no recorded room left (AUTO CAL switches Recorded Room off, 10.9.9). **Room**: Small, Medium, Default, Hall or **Auto** (10.8.0, see below). The slider goes from −6 to +6 dB around Default (10.8.0) |
| **Piano Comp**, **Reverb** | Placed after the resonance, so the whole instrument goes through them |
| **Reverb ALGO \| IR** (10.9.2) | Beside REVERB's DEFAULT. **ALGO**: PianoToLife's Piano Hall. **IR**: a convolution reverb with an **impulse response** of your choice (a real hall, a plate, a vintage reverb unit...). Click **IR**: choose an IR, **LOAD IR...** (a WAV, AIFF or FLAC you downloaded: it is copied into the `Impulse Responses` folder of your sample sets folder, and chosen), or **Open IR folder** (folders inside it, up to three levels, become sub-menus). Mono, stereo and **true stereo** IRs (4 channels, or a pair of files "... L" / "... R": choose either, both are taken) are read, at any sample rate, up to 10 s; B-format (ambisonic) files are not. The level is matched to the Piano Hall. Choosing an IR sets DECAY to the IR's own length and DAMP to 0 (the IR as recorded); then **DECAY** shortens its tail and **DAMP** makes its treble die sooner; MIX, PRE and LEVEL work as usual. No latency. A preset keeps the IR's name: if the file is missing, the Piano Hall plays and the button reads **IR ?**. DEFAULT = ALGO. Free IRs: [Voxengo](https://www.voxengo.com/impulses), [OpenAIR](https://www.openair.hosted.york.ac.uk/?page_id=2) (real halls, use the stereo files), [Airwindows](https://airwindows.com/airwindows-impulses); commercial libraries delivered in WAV work too |
| **EQ1 / EQ2** (10.4.2) | Click **EQ** under REVERB: the EQs take the place of COMP / REVERB (the same button brings them back). **EQ1 BEFORE FX** works before COMP and REVERB, to shape the tone of the piano; **EQ2 AFTER FX** works at the very end, before the Ceiling, to correct headphones. Each: **draw it on the curve** (double-click = a new point, drag = frequency and gain, mouse wheel on a point = its width Q, right-click = remove), PREAMP, RESET = flat, or **LOAD** a preset — a `ParametricEQ.txt` from AutoEq (oratory1990 measurements, Harman target) or an Equalizer APO file; load headphone presets in EQ2 (switch it off for a bounce or on loudspeakers). Up to 20 points each. Kept in the preset and the session. **EQ1 SHOW** (11.1.5, top right of the curve): each key held (keyboard or MIDI player) is a line at its fundamental's frequency, its 2nd and 3rd harmonics paler, with its name and Hz — at SR A4 Tuning and in the temperament. **EQ1 AUTO** (11.1.5): the Piano Model loaded compared with the default one (Steinway D274) over the 88 keys, by third octave; EQ1 gets one band per region that differs (a bell, or a shelf at an end), between 63 Hz and 6 kHz, -6 dB to +3 dB, with a negative preamp so it never clips. It replaces the EQ1 points; move them by hand afterwards. Nothing is changed in the Piano Model or in the keys' levels |
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
- **A very dry piano** (close or closed microphones): no room is found, and since 10.9.9 **Recorded Room is switched
  off** — there is no room to match (tick it again for a small room, Small, anyway). The same for a sampled piano whose
  room was taken out with **DRY / DENOISE** (SAMPLER): put the whole piano in a room with the **REVERB** (ALGO or IR) —
  see the [Sampler Manual](SAMPLER_MANUAL.md). When a room is found, Recorded Room is ticked again.
- ***The notes did not fully agree***: the measured notes differ (an old recording, tape hiss...): the result is
  usable, check it by ear.
- **After a Piano Model capture**, PianoToLife offers both AUTO CALs in a row: the resonance level, then the room.

---

## 12. Presets, MIDI player and views

- **Presets** keep every setting. In SAMPLER mode (10.6.0) the presets are the **instruments** (`.ptlset`, beside their
  samples `.wptl`, like Kontakt `.nki` / `.nkx`): see the Sampler Manual. Double-click a preset or an instrument
  (standalone) or drop it on the window.
  **Modified** (10.7.0): a **\*** when a setting differs from the preset loaded or saved — since 10.9.7 **before** the
  name, which turns to *italics* (never cut). Loading another preset, RELOAD, switching HOST / SAMPLER, dropping a
  preset or an instrument on the window, or choosing another version of the piano then asks first: lose the changes,
  **Save first** (saved in place, then it goes on), or Cancel. Each mode comes back with its own last preset /
  instrument.
  **What changed** (10.9.8): hover over the PRESET box while the **\*** is shown: a tooltip lists the **last
  modifications** ("Release Level: -2.0 dB → +1.5 dB"…, the 5 latest, then "+ N other changes"). **Right-click on the
  PRESET box**: **Undo all modifications** (RELOAD) or **Undo** the last one, named in the menu.
  **SAVE** (10.7.1) saves the current settings over the preset (instrument) shown, with no window; **SAVE AS** saves
  under a new name (SAVE opens it when there is no file yet, e.g. Last Session). **Right-click on the PRESET box**
  (10.7.1): **Rename** the preset shown, or **Move it to the Trash** (never deleted for good; for an instrument, only
  the `.ptlset` and, since 10.9.8, the settings of its versions ORIG. / DRY n - its samples `.wptl` stay; the box then
  shows **Not saved** while the piano still plays). **FOLDER** opens the Presets folder (HOST) or the current instrument's
  folder (SAMPLER).
- **MIDI player / recorder** (standalone): **LOAD MIDI**, **PLAY**, **REC**, **BOUNCE** (WAV, AIFF, FLAC or CAF) — to compare settings
  on exactly the same performance. After REC the take starts on your first note or pedal (pedals already down are
  kept); click REC again and the save window opens — save a **.mid**, or (11.0.2) a **.wav / .aiff / .flac** (the .mid is
saved beside it, then the BOUNCE options open); PLAY plays the take at once. LOAD MIDI and the save open the same
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
  **BOUNCE ALL** (11.0.2): with a playlist, **Pieces: All N pieces of the playlist** bounces every piece, one file each,
  in the folder chosen, named after the piece (never written over: *name (2).wav*). The MIDI line shows *Bounce all:
  i/N*; STOP stops the series. The media player's recording is never in a BOUNCE ALL. **Right-click on BOUNCE** (11.1.7):
  **Silence before the music**, none, 0.5 s or 1 s, written at the start of the file (for a piece that starts on its first
  note: some players cut the first milliseconds).
  **Sample rate in the standalone** (11.1.7): PianoToLife remembers the sample rate you choose in Options >
  Audio/MIDI Settings and sets the card back to it at start-up (it says so, or why it couldn't: another program holding
  the card). If another program or the card changes the rate while you play, PianoToLife follows and says so; if the
  system doesn't tell it, it measures the card's real rate and offers **RESTART AUDIO**. The VST3 and AU follow the DAW.
  You can also **drop MIDI files on the window** (10.6.2): one file, several (a playlist, in the order of their names)
  or an .m3u, as with LOAD MIDI. **II (PAUSE)** (10.6.2): the sound stops where it is and the place is kept; click
  again to go on from there (from a clean piano, with the pedals the file has at that point). PLAY starts from the
  beginning.
  **The MIDI player remembers** (11.1.1) its file or playlist and the piece it was at: they come back at the next start
  (ready, not playing; a take never saved is not kept).
  **11.4.1 — bars** in MAGIC VIEW (MIDI): a line and a number at each bar (the beats fainter), read from the file's tempo
  and time signature changes (4/4 and 120 BPM until it says otherwise; a take recorded in PianoToLife has none: "no bars").
  Its top: line 1 HANDS / VELOCITY / STAFF / ahead; line 2 **PLAY / PAUSE**, **STOP**, **BAR n : b**, the time signature
  and tempo there, **GO TO** (a bar number, Enter: it plays from the start of that bar, the notes released and the pedals
  set as the file has them there; the linked audio follows), then the time and the file's name. The main window shows
  BAR n : b on the MIDI player's line too. **BOUNCE with the media's audio** (11.4.1): **End** - at the MIDI's end (a
  take recorded: the moment of its STOP), the audio faded out over 3 s (default), or at the end of the audio file.
  **VIEW** (11.1.1, right of LOAD MIDI, also in the compact bar): **MAGIC VIEW (MIDI)** — the notes of the MIDI file
  playing, or of the take just recorded, falling onto a keyboard and lighting its keys when they sound, in their own
  window (resizable, its place remembered). **HANDS**: the left hand orange, the right hand blue (from the file's two
  main tracks or channels when it has them, otherwise guessed); or **VELOCITY**: the notes coloured by their velocity
  (green, yellow, orange, red). **ahead − / +**: how many seconds of notes you see coming. Under the keyboard the
  **three pedals** move with their depth (half pedal included); the keys you play light up in green.
  **MAGIC VIEW in 11.1.5: equal lanes** — each octave cut into 12 lanes of the same width, one per semitone: every
  falling note has the same width, a black key is its lane, and the fronts of C, D, E are about 5 % narrower than those
  of F, G, A, B; a thin dark line parts B | C and E | F.
  **MAGIC VIEW in 11.1.2**: a keyboard in a real keyboard's proportions (kept when the window is stretched), notes as
  wide as a black key, and **STAFF**: a grand staff above the falling notes — each note at its pitch on the treble or
  bass staff (by hand), its time across (a long note = a long line), scrolling past a red playhead, with the key
  signature (CHORDS' key; for a MIDI file alone, found from its notes) and the accidentals; bar lines from CHORDS in the
  Media view. It is not a rhythmic score: no note values are guessed, so it reads a free take as well.
  **MIDI controller** (11.1.2): right-click on **PLAY, REC, II, ◀ or ▶** → **LEARN**, then move a button, knob or pedal
  of your controller: that CC presses the button (a value of 64 or more) and is taken away from what is played. The
  pedals (CC 64 / 66 / 67) cannot be used. REC stopped from the controller saves the take at once as
  *P2L-date-time.mid* in the LOAD MIDI folder, with no window; since 11.1.6 the save window of a take proposes the same
  name. Right-click on REC (11.1.6) also switches **REC and PLAY with the audio of the MEDIA player (SYNC)**, the same
  setting as in the MEDIA window.
  **Recent** (11.1.2): LOAD MIDI and the media player's LOAD... list the 5 pieces played last.
  **METRO** (10.4.2): click = metronome on / off (the button shows the tempo); right-click = tempo (30–360 BPM, TAP),
  bar (none, 1/1, 2/2, 2/4, 3/4, 4/4, 5/4, 8/4, 3/8, 6/8, 7/8, 8/8, 9/8, 12/8 — first beat accented, the groups lighter), sound (wood or beep), volume and **count-in**. It is heard only — never in a
  bounce nor in the MIDI take. With the metronome on, REC starts on a bar (after one bar of count-in when ticked) and
  the tempo and time signature are written in the saved MIDI file, so the take sits on the grid of a DAW.
- **MEDIA player** (11.0.0, standalone): the **MEDIA** button, left of LOAD MIDI (also in the compact bar), opens a
  player in its own window, moved anywhere (MEDIA again closes it; the music goes on). It plays a recording or a video
  **along with you**: it is heard only and never goes through the piano's sound processing.
  - **LOAD...**: one or several files, a folder, or an **.m3u** playlist (and save the playlist). WAV, AIFF, FLAC, Ogg,
    MP3, M4A and **videos MP4, M4V, MOV** (also WMV and AVI on Windows; a video's sound is read once, then kept). A
    click on the name lists the pieces; **◀ PLAY STOP ▶ LOOP**, the position and VOL. The last playlist and piece come
    back at the next start (not playing).
  - **LEVEL**: every file played at the same loudness — **-14 / -16 LUFS** (streaming), **-23 LUFS** (broadcast) or Off
    (as recorded) — with one gain that never takes it over -1 dBTP. **CEIL.** (-1 / -2 / -3 dB): the media's own
    true-peak limiter, as the piano's Ceiling. While the media plays, piano and media together are kept under -0.3 dBFS.
  - **Play at A4 =** (432–448 Hz): the A4 of each file is measured (e.g. "Recorded at A4 = 438.6 Hz") and the file is
    played at the A4 you choose, so it is in tune with your piano. The tempo moves with it (20 cents = 1.2 %).
  - **REC and PLAY with the MIDI (and BOUNCE)** (♫ on the MIDI line): REC counts in (orange numbers, on a bar with
    METRO), then the MIDI take and the recording start together; the recording's name, place and tuning are written in
    the MIDI file. PLAY of such a take asks (11.1.1) **With the audio** (both in sync — PAUSE and STOP too, LOOP repeats both) or **MIDI only**; a MIDI file recorded without the audio never starts the media player. **BOUNCE** can put the recording
    in the audio file with your piano (option "Audio file: in the bounce").
  - **VIDEO** (SCREEN before 11.3.6): a window for a second screen, resizable, full screen with a double-click (its place and size are
    remembered). It shows the **video** in time with the player and the **lyrics** of a **.lrc** file of the same name
    beside the audio or video file (current line in bold, the next ones under it). Move the mouse: a bar for the
    lyrics' **colour**, **text** opacity, a see-through **band** behind them (over a video), **size** and full screen.
  - **CHORDS**: the chords of the piece playing, found by analysis (a few seconds, once per file): the chord playing in
    large letters, the **key** and the **tuning** of the recording, and the chords **scrolling** on the beats of the
    piece (bars marked), the playhead in white. **colour** and **zoom − / +**; the window is resizable.
    **AUTO | BEATS | FREE** (11.0.1): **BEATS** places the chords on the beats found from the attacks (stable);
    **FREE** follows the harmony alone, with no grid (free piano, rubato); **AUTO** keeps BEATS and adds the
    passing chords FREE hears between the beats. Each mode is analysed once, then you switch at once. **BEATS** is the
    default since 11.1.0 (the most stable); your choice is remembered.
  - **NO VOICE / NO PIANO / CLEAN** (11.1.0, in the CHORDS window): the **voice** and / or the **pianos** (acoustic
    and digital) taken out of the piece playing, to play or sing in their place; everything else stays the recording
    itself. The piece is **separated once**, in the background, before you play (a progress bar, **CANCEL**; about half
    the piece's length on a Mac with Apple Silicon), and kept in the **Stems** folder of your samples folder: the next
    time is instant. The buttons then switch at once while playing; the TUNING applies to them, and a BOUNCE with the
    media plays what you hear. **CLEAN** (with NO PIANO): where the piano plays almost alone (an intro), its last
    remains are taken out too. Nothing is exported. Since 11.2.4 each new piece (and each start) begins with NO VOICE
    and NO PIANO off: nothing is separated without a click (CLEAN keeps its choice). If a separation fails, what the engine said is in **Stems/last-separation-error.txt**. Works best on a Mac
    with Apple Silicon or a PC with an NVIDIA RTX card (Windows: the graphics card through Vulkan, otherwise the
    processor, much slower); on older computers it may be very slow and cannot be guaranteed. **CREDITS**: the model
    "MVSep Mega 53 Stems" by ZFTurbo and the engine BSRoformer.cpp (both MIT License); the licence texts are installed
    with PianoToLife.
  - **In the player too** (11.1.1): **NO VOICE / NO PIANO / CLEAN** under REC and PLAY, with the progress and
    **CANCEL** — the same switches as in CHORDS.
  - **FAST / QUALITY** (11.1.4, in the player and in CHORDS): **QUALITY** = the best separation (about half of the
    piece's length on a Mac M2 Pro, 2 to 2.5 times faster with a recent NVIDIA RTX), **FAST** = about twice as fast, a little less clean. Each is kept apart in the
    Stems folder; the better one already separated is played (FAST chosen and QUALITY there: QUALITY plays, nothing is
    separated again). QUALITY chosen with only FAST there: FAST plays while QUALITY is separated. Remembered.
  - **CLEAN PIANO** (11.1.4, formerly CLEAN) with its **strength slider** beside it: 0 % = no cleaning, 100 % = as
    separated, up to 200 % = deeper (the piano's remains taken out also where it dominates less; may thin out
    instruments playing the same notes). A new strength is computed once from the separated tracks (a few seconds;
    the state line says so). Double-click: 100 %.
  - **MAGIC VIEW** (11.1.1, in the player, once the piece is separated): the notes of its **PIANO**, its **VOICE** (one
    note at a time) or its **OTHER** instruments (the bass in orange), read on the separated tracks and falling onto a
    keyboard in time with the music (pauses, jumps, TUNING). It is a reading of the sound, not a transcription:
    **sens. − / +** shows more or fewer notes. **HANDS** (PIANO): the two hands guessed, left orange, right blue. The
    tuning of the recording is the one CHORDS measured (otherwise it is measured on the track). Its own window, which
    can be open beside MAGIC VIEW (MIDI). Since 11.1.2 it also works before the separation: **OTHER** then reads the
    whole recording (PIANO and VOICE need the separation); **sens.** is a slider; no pedals in this view.
  - **FOLDERS** (11.2.0, left of CHORDS): your folders of pieces as **playlists**, one click to switch (the one playing is
    ticked). A folder loaded with LOAD > folder is added by itself; **Add a folder...**, **Add this piece's folder**,
    **Remove**. **SEARCH** (11.2.0): a click on the piece's name opens the playlist with a search box — as you type,
    without case, accents or punctuation, every word in any order; Enter or a click plays it, up / down move.
  - **TRANSP.** (11.2.0, beside Play at A4): the piece played up to **6 semitones higher (+) or lower (−)**, its tempo kept
    (Signalsmith Stretch, MIT), live, after the A4 above. A MIDI take stays in time (its ~0.1 s of processing is made up);
    the stems, a BOUNCE with the media, CHORDS (the chords renamed as heard) and MAGIC VIEW follow. Remembered for each
    piece. Double-click: 0.
  - **LEVEL** also at **-20 / -21 / -22 LUFS** and **CEIL.** down to **-7 dB** (11.2.0); LEVEL's gain then stays under
    the CEIL. chosen. BOUNCE's **Normalise** has the same three levels, and its true-peak ceiling goes down to -7 dBTP.
  - **LYRICS** (11.2.0): PianoToLife listens to the **separated voice** of the piece (separated first if needed) and
    writes its lyrics in time — whisper.cpp with the Whisper *large-v3-turbo* model (MIT), on your computer. The model (1.6 GB) is
    downloaded once, the first time (a progress bar, CANCEL). **LANG**: AUTO or the language sung (helps short or
    unclear voices). The result is a standard **.lrc** file **beside the audio file**, same name (other programs read it
    too; asked before replacing one), also kept in the Stems folder. The **LYRICS** button lights up when the piece has
    its lyrics; a click then asks **FIND AGAIN / EDIT / CANCEL**. A .lrc of your own beside the audio always comes first.
  - **EDIT** (11.2.0): the corrector. **LRCLIB** (lrclib.net, a free lyrics database) is asked at once with the artist
    and the title (taken from "Artist - Title" in the file's name; change them and SEARCH) and the length: the best
    lyrics are proposed on the left, others in the menu (**SYNC**: with their own times). On the right, the same lyrics
    **aligned on the voice heard**, again at each change: green = the word was found in the voice, yellow / orange =
    placed between them, blue = LRCLIB's time only. **LRC SYNC** uses LRCLIB's times checked on the voice; **SMART**
    aligns a plain text (pasted or typed). Click a line on the right: play from it; **TAP** (key T): the selected line
    starts now; **OFFSET**: all the lines earlier / later; **SAVE**: the .lrc beside the audio, shown in SCREEN at once.
    The alignment engine is PianoToLife's own. The lyrics are for your personal use
    only: PianoToLife never distributes lyrics.
  - **SCREEN: LYRICS ON / OFF** (11.2.0) in its bar: the picture alone (a video that shows its own words).
  - **FFmpeg** (11.2.0, optional): when macOS or Windows cannot read a file (MKV, WebM, Opus, APE, WavPack, DSD, AC3,
    DTS, TS, VOB...), PianoToLife uses **the FFmpeg installed on your computer** (not given with PianoToLife: on a Mac
    "brew install ffmpeg", on Windows "winget install ffmpeg", or ffmpeg.org). It is found by itself, or chosen in
    **LOAD > FFmpeg...**. Its sound is read once into the cache. A file with **several audio tracks** (a film in several
    languages): the track is asked once, then a **right-click on the name** (or LOAD > Audio track) changes it, at the
    same place; each track has its own stems, lyrics (*name.t2.lrc*), chords and levels. The picture of an MKV / WebM is
    not shown yet.
  - **Video pictures** (11.2.2): when the system cannot decode a video's pictures (AV1 on a Mac M1 / M2, MKV, WebM,
    AVI...), SCREEN shows them through FFmpeg, decoded as it plays, nothing written on the disk; without FFmpeg it says
    so. **FULL SCREEN** (SCREEN, CHORDS, MAGIC VIEW) covers exactly the screen the window is on; the other screens stay
    as they are. Double-click the picture, or in SCREEN use the **FULL SCREEN** button (top right, in the bar shown when
    the mouse moves): on a Mac, the green button of the title bar is the macOS full screen, which can turn the other
    screens black.
  - **Virtual folders** (11.2.3, in FOLDERS): **PLAYED** — the 500 pieces played last, newest first, filled by itself
    (pieces can be removed from it) — and **your own lists**. *New, edit, fill the virtual folders...* opens a window: on
    the left a folder of FOLDERS (with a search), on the right a virtual folder — **ADD ▶** (or double-click), **FILES...**
    (from anywhere), **REMOVE**, **NEW...**, **RENAME...**, **DELETE**, **PLAY** (a double-click plays from that piece).
    Only links, nothing copied: each list is an `.m3u` in the folder *SympResHost Virtual folders*, beside the settings.
    A click on a list in FOLDERS plays it.
  - **VOL of the media** (11.2.3): **0 dB** at each start, so that you hear exactly the LUFS chosen in LEVEL; back to 0 dB
    when LEVEL or CEIL. changes; double-click: 0 dB. At the first opening LEVEL is at -20 LUFS and CEIL. at -7 dB.
  - **SCREEN karaoke and OFFSET** (11.2.4): the line sung fills from left to right as it is sung — on the words Whisper
    heard when the piece went through LYRICS, else evenly over the line — and the lines glide up smoothly. **OFFSET**
    (in the bar, -1000 to +1000 ms, double-click 0): the lyrics shown earlier (+, time to read them) or later (-), for
    every piece; the `.lrc` is not changed (EDIT's OFFSET corrects a piece's file).
  - **Virtual folder on the left** (11.2.4): in the virtual folders' window, the left list also offers the virtual
    folders (PLAYED too): select all (Cmd / Ctrl + A) and ADD to put a whole list into another one.
  - **PADS** (11.2.5, left of FOLDERS): 4 x 4 pads on 5 pages (◀ ▶, they slide). Drop audio or video files on the pads
    (several files fill the pads that follow), or click an empty pad; each pad shows the cover or a picture of the video
    (through FFmpeg) and its name. Click: play. Right-click: **MEDIA (A)** — in the media player, as a piece (stems,
    lyrics, SCREEN...) — or **PAD (B)** — over everything, the B pads add up, at **PAD VOL** and through the media's
    CEIL.; **TOGGLE** (a click plays, another one stops) or **HOLD** (plays while held); **MIDI LEARN** (then play a key, a
    pad or a CC of the device chosen at the top); forget its MIDI; empty the pad. Right-click on ◀ ▶: their MIDI LEARN.
    The MIDI of the pads works on every page and with the window closed. **STOP ALL** stops everything. 100 ms fades:
    no pop, no click. Kept in *SympResHost Pads.json*, beside the settings.
  - **STEMS READY** (11.2.5): a virtual folder made by PianoToLife — the pieces already separated (each separation writes
    *source.txt* in its Stems folder; older ones are found from FOLDERS and the virtual folders). In the lists (the
    playlist and its SEARCH, the virtual folders) and on the pads, a **green dot and a bold name** show them.
  - **11.2.6 — LYRICS on a piece not separated yet**: LYRICS asks **BEST** (the voice separated first, the most
    accurate) or **FASTER** (the whole piece heard at once, much quicker without a graphics card; correct with EDIT),
    with *Remember my choice*; the choice is changed in LANG's menu (*A piece not separated yet*). The lyrics found on
    the whole piece are kept when the piece is separated later.
  - **11.2.6 — the window buttons**: CHORDS, SCREEN, PADS, MAGIC VIEW (player) and VIEW (MAGIC VIEW MIDI) open their
    window, a second click closes it (its place and size are kept); the button is lit while its window is open.
    Right-click on a lit button: **Bring it to this screen**, and with several screens **Move it to screen N** (its size,
    the main one said; the one it is on ticked) — for a window left on a screen switched off or a projector.
  - **11.2.6 — RESET STEMS** (under FAST / QUALITY): after a confirmation, the separated tracks of the piece (FAST and
    QUALITY) are deleted from Samples/Stems; its lyrics are kept; the player goes back to the recording, NO VOICE / NO
    PIANO off (a click separates it again). **RESET LYRICS** (under it): the lyrics PianoToLife found for the piece are
    deleted (in Samples/Stems, and the `.lrc` beside the audio only when PianoToLife wrote it; a `.lrc` of your own is
    never deleted; the changes made with EDIT are lost too); LYRICS then finds them again.
  - **11.2.6 — measured speeds** (a piece of 3 min 25): Mac mini M2 Pro — FAST 48 s, QUALITY 99 s, LYRICS 8–9 s;
    Windows laptop with an NVIDIA GeForce RTX 5050 Laptop (8 GB) — FAST 22 s, QUALITY 39 s, LYRICS about 6 s. Without a
    graphics card, a separation can take 20 to 30 minutes. On Windows, LYRICS now uses a laptop's dedicated graphics
    card (before: its integrated one — about a minute). **Help complete these figures**: with a Mac with Apple
    Silicon or a PC with an NVIDIA RTX card only, send your computer, the length of the piece and the FAST / QUALITY
    times to pianotolife@outlook.com.
  - **11.3.0 — the stems folder**: right-click FAST / QUALITY: **Choose the stems folder...**, **Back to Samples/Stems
    (this computer)**, **Show it**. A folder shared on the network (a Mac's folder used by a PC, or the other way round)
    lets two computers use the same stems: the separation is done on the computer that asks for it, then only its
    result is copied to the shared folder. If the chosen folder cannot be reached, Samples/Stems is used meanwhile.
  - **11.3.0 — stems found by their content**: a piece's stems are found from what the file contains, not its path: a
    piece moved, renamed or played on another computer finds its stems and its lyrics again. Stems separated before
    11.3.0 are found too (by the piece's name and length) and renamed once.
  - **11.3.0 — played from memory**: the piece and its stems are read into memory, as DJ software does, so the disk is
    free while you play (a very long file, over 600 MB, is still read from the disk). On the network, the piece and its
    stems are prepared in the background (*Loading...*): the original plays first, then the stems. A folder or a
    virtual folder on the network is listed in the background too; a missing piece is skipped when its turn comes.
  - **11.3.0 — no click at PLAY / STOP**: the player starts from silence and STOP goes down to zero cleanly.
  - **11.3.1 — network folders really in the background**: on Windows, mapped network drives (M:, S:...) are recognised
    as network drives, so pieces, stems and lists on them are prepared in the background (the window never waits).
  - **11.3.1 — the next piece prepared**: a few seconds after a piece starts, the next one of the playlist is read into
    memory with its stems and lyrics; NEXT and the end of a piece install it at once.
  - **11.3.1 — PADS in memory**: the files of the page of pads shown are read into memory beforehand (at most 1.5 GB, the
    least recently used dropped); a pad starts at once.
  - **11.3.1 — folders**: a folder's list is kept while the folder does not change (one question to the disk instead of
    the whole list); FOLDERS ticks the folder or the virtual folder chosen; STEMS READY shows a piece just separated at
    once.
  - **11.3.3 — LIVE STEMS**: a click on **LIVE STEMS** separates the piece loaded slice by slice and plays it meanwhile.
    The button counts down to the first slice (*LIVE STEMS 12*, *11*...); at 0 the piece starts again from its beginning
    with its stems, and the next slices are separated while it plays (the part not separated yet plays as recorded,
    without a gap). Right-click: the first slice - **AUTO** (default: the shortest one with which the playing never
    catches up with the separation, from the speed of your computer, learnt at each separation, FAST and QUALITY apart)
    or 10 to 60 s - and **At 0, turn on**: NO VOICE, NO PIANO, both, or as chosen. LIVE STEMS is off at each start and
    each new piece. CLEAN PIANO cleans once the whole piece is separated; at the end the stems are kept as usual. Pieces
    up to 15 minutes (their tracks are held in memory); a computer too slow to keep up separates as usual.
  - **11.3.3 — separate on another computer**: the separation uses the processor of the computer that does it. To keep
    the one you play on free, let another computer (a PC or a Mac on the same network) separate for it: on **both**
    computers, right-click FAST / QUALITY > **Choose the stems folder...** and choose the **same** folder shared on the
    network, with the same quality (FAST or QUALITY). Separate the pieces on the other computer; they appear in **STEMS
    READY** on yours as soon as each is finished (a piece is written there only once complete), and are played from
    memory. Precautions: on the computer you play on, NO VOICE / NO PIANO / LIVE STEMS on a piece not separated yet
    separates it there; never separate the same piece on both computers at the same time.
  - **11.3.3 — PREVIOUS NOT FINISHED**: another piece shown while the previous one is still separated: said in red beside
    its percentage (LIVE STEMS is locked meanwhile; CANCEL stops it).
  - **11.3.3 — LYRICS EDIT**: SAVE shows *SAVED*; **SAVE AND CLOSE**; **CLOSE** closes without saving (the window's cross
    asks); **ANALYSE** does what LYRICS does (grey once the piece was heard). While an analysis runs, *ANALYSIS IN
    PROGRESS* and nothing can be changed (PLAY and CLOSE only); at its end the window opens again with the new lyrics. It
    follows the piece playing: another piece, it opens again for that one (lyrics are never saved into another piece's
    file). The LYRICS button shows **LYRICS C.** when PianoToLife's lyrics were corrected.
  - **11.3.4 — LOCAL / MASTER / FOLLOW**: with two computers on the same shared stems folder (see above), right-click
    FAST / QUALITY on each: **MASTER** on the one you play on, **FOLLOW** on the other (**LOCAL**, the default at each
    start: each computer works for itself). On the MASTER, NO VOICE / NO PIANO on a piece without stems, or LYRICS on a
    piece without lyrics, is asked to the FOLLOW computer: *Separating on <computer>...* or *LYRICS asked to
    <computer>...* is shown, and the piece keeps playing as recorded. The FOLLOW computer finds the same piece (same
    path, or the same file under one of its drives: same name, size and content), shows it stopped in its playlist,
    separates it at the quality asked (stems already there at any quality are enough), then makes its lyrics if asked
    and if it has none. The stems and lyrics appear on the MASTER as soon as they are ready, without reloading the
    piece. A new request goes first. If the FOLLOW computer cannot find the piece (its folder not shared, another
    drive), the MASTER says *<computer> cannot find this piece* and the next click works on the MASTER; if the FOLLOW
    computer stops answering for more than 2 minutes, the MASTER works for itself.
  - **11.3.4 — stems and lyrics made elsewhere, seen at once**: while the piece shown has no stems or no lyrics,
    PianoToLife checks every 5 s whether another computer has made them in the stems folder; they are used at once,
    without PREV / NEXT.
  - **11.3.4 — drag and drop**: drop audio or video files, a folder or an .m3u on the media player's window: as LOAD (the
    playlist is replaced; several files in the order of their names; a folder joins FOLDERS). Audio or video files or a
    folder dropped on the main window open the media player and load there (an .m3u dropped on the main window stays a
    MIDI playlist).
  - **11.3.5 — FOLDERS and the pieces beside the player**: at the player's left, the same height, a column with your
    folders and then the virtual folders (with their number of pieces; the one playing lit) - a click loads it as the
    FOLDERS menu does - and, at its left, the pieces of the playlist with their SEARCH (the piece playing lit, the green
    dot of the stems and a **blue dot** when the piece has its lyrics); a click plays it. The tab ◀ / ▶ folds or opens
    them (the window grows to the left, the player stays where it is); remembered.
  - **11.3.5 — AUTO** (beside LOOP, off by default): off, at the end of a piece it stays there, back at its start (LOOP:
    it again) - in live you choose the next piece yourself; on, the next one starts by itself (LOOP: the playlist again).
  - **11.3.5 — countdown**: a piece played from its beginning starts after a countdown (5 s by default; right-click on
    PLAY: off, 5, 10, 20 or 30 s), shown on PLAY and in big digits in SCREEN; PLAY again starts it at once; never for a
    pad.
  - **11.3.5 — SPEED** (beside the volume): the piece slower or faster, 50 to 150 %, its pitch kept (transparent from
    about 80 to 115 %); remembered for each piece; double-click 100 %. The lyrics, CHORDS and MAGIC VIEW follow.
  - **11.3.5 — TUNING and the tempo**: Play at A4 stays a varispeed by default - the cleanest, as an old recording's
    pitch comes from its tape's speed (20 cents = 1.2 % of tempo). Right-click on the A4: **Keep the original tempo**
    (the pitch alone corrected). With TRANSPOSE or SPEED at work, the tuning goes into the same process: the tempo is
    exact.
  - **11.3.5 — MEDIA pads**: a MEDIA pad starts at once and takes over; at its end, at STOP, at a 2nd click (TOGGLE) or
    when released (HOLD), the playlist's piece comes back, where it was. Right-click on a pad: **Start at...** (m:ss or
    seconds), *Start where the media player is now*, *Start at its beginning* (shown on the pad: ▶ 1:23.5); for MEDIA
    and PAD.
  - **11.3.5 — SCREEN**: **COVER** - the album's picture (inside the file, or cover.jpg / folder.jpg beside it) behind
    the lyrics of an audio piece; **SPLIT** - each long line in two halves, one under the other, so that Size (now up to
    300 %) can make them much bigger; **SCROLL** - STEP (line by line) or **CREDITS** ▲ / ▼: the lyrics roll on without
    stopping, like a film's credits, each line in the middle when it is sung.
  - **11.3.5 — LYRICS EDIT**: the artist, title and album are read from the file's tags (MP3, FLAC, M4A, MP4...); the
    file's name only without them. When LRCLIB has a version edited otherwise (an instrumental shorter or longer), its
    lines are followed to the end.
  - **11.3.6 — VIDEO** (SCREEN before): the same window, renamed. In the player, **KARAOKE** beside it shows or hides
    the lyrics in VIDEO (the same as LYRICS ON / OFF in VIDEO); turned on, it opens VIDEO. As a window, VIDEO keeps
    16:9. Its bar keeps LYRICS, FOR LIVE, **SETTINGS** and FULL SCREEN; SETTINGS opens a panel inside VIDEO (also on a
    second screen and in full screen) with COLOUR, COVER, SPLIT, FILL, STEP / CREDITS and the Text, Band, Size and
    Offset sliders; a click beside it closes it. Full screen on the Mac's own screen hides the menu bar and the Dock
    while it lasts.
  - **11.3.6 — the words are never cut**: a line too long for the window is drawn smaller (down to half its size), then
    on as many lines as it needs; the lines before and after it move to make room.
  - **11.3.6 — FOR LIVE** (VIDEO's bar; for a screen filmed with a phone): a thick black outline around the letters, the
    line sung in a frame, the next line in full colour - in every mode. **FILL** (SETTINGS): OFF, the whole line to sing
    is lit at once instead of filling as it is sung.
  - **11.3.6 — duets**: who sings a line, written at its start in the .lrc - **HE :**, **SHE :**, **1 :**, **2 :**,
    **BOTH :**, **CHOIR :** (also read: LUI, ELLE, ENSEMBLE, HIM, HER, CHOEUR...). In LYRICS EDIT, right-click a line:
    who sings it, *Rename all* (HE / SHE <-> 1 / 2, swap the two), or *Who sings each word...* - a brush per singer, a
    click or a drag over the words: those words are written "(SHE: words)" inside the line. In VIDEO the mark is shown
    when the singer changes, each singer in its colour. Check them, then SAVE.
  - **11.3.6 — LYRICS EDIT**: three columns - the lyrics proposed, **HEARD BY WHISPER** (its words with their times;
    the word heard now lit; click a word: play from it) and the lines aligned. **STOP** beside PLAY, **UNDO / REDO**
    (Cmd+Z / Cmd+Shift+Z) for what is typed and the marks put, **DELETE LYRICS** (what PianoToLife found for this piece;
    a .lrc of your own is kept), the **language** beside ANALYSE (the same as LANG in the player). ANALYSE listens to
    the separated voice when there is one, else to the whole piece. Lines added, pasted or moved keep LRCLIB's times
    even without words heard; lyrics saved here (or with duet marks) are kept when the window opens again.
  - **11.3.6 — LYRICS finds the words more often**: Whisper starts where the singing starts (a live recording with
    shouts or a long instrumental before the voice), its notes about the sound ("[Music]", "(applause)"...) are dropped,
    long silences are shortened, AUTO finds the language on the 30 s sung the most, and with almost nothing heard it
    listens again on the processor, then to the whole piece. When nothing is found, a folder "lyrics (failed)" in the
    piece's Stems folder keeps what Whisper was given and what it answered.
  - **11.3.6 — media player**: SEARCH finds the pieces by their tags too (artist, title, album; no case, no accents),
    shown in grey beside the name. Right-click a piece: **Tags...** - the tags edited and written into the file through
    FFmpeg (the sound copied as it is; the original to the Trash; its stems and lyrics follow it) - and **Show in Finder**
    (Mac) / **Show in Explorer** (Windows). A double-click on a piece plays it. The pieces column is wider or narrower
    with its left edge (double-click: back). **VOICE** and **PIANO**: that track alone (the stems row), CLEAN PIANO on
    its own line under them.
  - **11.3.6 — HOST tuning** (TEMPERAMENT, Piano Model): each key's pitch is its first partial when the capture measured
    it; the line of the partials (inharmonicity) is used only where it is missing - fewer false corrections in the
    treble with FIX KEYS.
  - **11.3.7 — singers' buttons** (under the stems, when the lyrics have duet marks): **LEAD** (the words without a
    mark, when some have one), **HE**, **SHE**, **1**, **2**, **3**, **4**, **BOTH**, **CHOIR** - only the ones the lyrics
    use. Lit: that singer is heard; several can be lit; none lit: the whole voice. The words of the singers not lit
    are taken out of the voice, without a break between them however long the silence, so that you sing their part.
    NO VOICE comes first (the whole voice out). Right-click NO VOICE: **CUT** (when the voice goes) and **BACK** (when
    it comes back), -1200 to +1200 ms, -300 by default; **FADE OUT** and **FADE IN** (0 to 500 ms, 100 by default).
    A mark at the start of a line (HE :) counts for the lines after it, up to the next one; "(SHE: words)" only for
    those words. Marks **3** and **4** for four singers.
  - **11.3.7 — VIDEO**: **BALL** (SETTINGS, instead of the pale fill): a ball jumps from word to word over the line
    sung, landing on each word as it starts. The lines never overlap; after a jump of the player VIDEO follows at once.
  - **11.3.7 — LYRICS EDIT**: a click on a line plays it at once; the columns stay where they are under the mouse.
    The line chosen on the right: **◀ 1 / ◀ .1 / .1 ▶ / 1 ▶** (or the arrow keys, Shift: 1 s) move it, Cmd+Z undoes the
    last move, SAVE keeps the times; its line is lit on the left. **TIMES** - **AUTO**: the lyrics' own times when they
    fit the voice, else **VOICE**: timed on the voice, the lines not heard stretched between the ones heard (a cover
    sung slower or faster); **LRC**: the lyrics' times as they are. With VOICE, lines this version does not sing are
    greyed and not saved (right-click: *Sung here*). The words are compared by their sound too (a word heard a little
    differently is found). The lyrics are saved by themselves before *Who sings each word...* and at its OK - the
    voice cut follows at once; the words of the line's singer are shown in its colour. The language menu has
    **MULTI** for a song in two languages (a pass in each). The LRCLIB results are ranked by what Whisper heard (the
    words outside brackets): **% heard** beside each one.
  - **11.3.7 — LYRICS**: the start of the singing is found back over up to 4 s of quiet.
  - **11.3.7 — BOUNCE ALL**: the pieces can be *From this piece to the end of the playlist*; each piece waits for the
    one before to be written (2 minutes at most), else it is skipped and listed at the end; the time left is shown.
    A fast bounce no longer starts again in real time for a long silence in the music (pauses between movements);
    when it does, the note says where the sound had a hole.
  - **11.3.7 — MASTER / FOLLOW**: CANCEL on the master stops a separation it sent; RESET STEMS / RESET LYRICS on the
    master is done on the follower too. Windows: the list of pieces no longer jumps back up while their tags are read.
  - **11.3.7 — ANALYSE DUO** is set aside in this version: put the marks by hand (right-click a line, *Who sings each
    word...*).
  - **11.3.8 — LYRICS with Whisper large-v3-turbo** (MIT): a larger speech model, downloaded once (1.6 GB) instead of
    small - far fewer wrong words, almost as fast with a graphics card (slower on the processor alone). The pieces
    already done keep their words: press ANALYSE (or RESET LYRICS) to hear them again with it. Whisper's loops (the
    same word written again and again, squeezed together) are dropped; two short words sung as one ("elle l'a") are
    found in time.
  - **11.3.8 — LYRICS EDIT**: **FIND / REPLACE** above the lyrics on the left - FIND (whole words, capitals or not; the
    number found shown; never a duet mark), REPLACE, **NEXT** (the next one replaced), **REPLACE ALL** (Enter),
    **CLEAR**; UNDO takes each change back. A line you add (with no time of its own) takes the time Whisper heard it
    at; two lines are never placed within half a second of each other.
  - **11.3.8 — VIDEO** takes at once a change of times saved in LYRICS EDIT (before, only a change of text was seen).
  - **11.3.8 — fast bounce**: a hole is counted only when the sound stops in the middle of a note (still loud just
    before); a silence in the music, however short, no longer makes the bounce start again in real time.
  - **11.4.1 — the list and the stems folder**: under the pieces, **BY TAGS** (Artist - Title, the file's name when it
    has no tags) or **BY FILES**, remembered. **DUPLICATES** (a virtual folder made by PianoToLife, as STEMS READY): the
    pieces of your FOLDERS and virtual folders that seem to be there twice, side by side - the same name or tags (what
    is between brackets is kept when it names a version: Club Mix, Edit, Live...; "Official Video", "Remastered" and
    track numbers left out) and the same length within 2 s, or the same file; an audio is never paired with a video.
    **FOLDERS > Clean stems...**: DELETE STEMS WITHOUT AUDIO (the piece deleted - only when its folder is there; its
    lyrics too), DELETE FAST IF QUALITY EXISTS, or the pieces chosen in a list (their tracks deleted, their lyrics kept);
    each asks first. **KEEP STEMS** (beside CLEAN PIANO, this computer, on by default): off, the separated tracks of a
    piece are deleted when you go on to another one (its lyrics kept) - LOCAL only, never in MASTER / FOLLOW.
    **STEMS READY and the dots** come from an index kept in the stems folder (*PianoToLife stems index.txt*), filled by
    every computer: the same list on each, whether the folder is on this computer, on the other one or on a shared disk;
    **FOLDERS > Reanalyse the stems index** reads every stems folder again. CANCEL sits beside PREPARE STEMS while it
    prepares; the line beside it only says what went wrong. MASTER / FOLLOW: PREPARING n % shows the follower's real
    progress; the follower takes the master's lyrics language (and keeps it); RESET LYRICS / RESET STEMS are done on both.
  - **11.4.0 — clearer buttons**: **FIND LYRICS (AI)** when the piece has no lyrics yet (then LYRICS, or LYRICS C. once
    corrected); **EDIT LYRICS** (was EDIT). The stems' state is a button at the start of its line: **PREPARE STEMS** (a
    click separates the piece once - kept, never done again), **PREPARING n %** (CANCEL beside it), **STEMS READY** (green:
    NO VOICE, NO PIANO, VOICE, PIANO and CLEAN PIANO play at once).
  - **Disk space** (11.2.1): a file the system cannot read directly — a video's sound, a format decoded by FFmpeg, or
    another audio track — is decoded once and **kept** in a cache (Mac: `~/Library/Application Support/PianoToLife/Video
    sound`; Windows: `%APPDATA%\PianoToLife\Video sound`), the 30 newest; a long film can take more than 1 GB. Delete
    that folder whenever you like: it is made again when needed. Ordinary files (MP3, FLAC, WAV, AIFF, M4A...) are read
    directly, never copied. The stems (150–200 MB per piece) and the Whisper model (1.6 GB) go to your samples folder.
  - **Internet** (11.2.0): PianoToLife goes on the Internet only when you ask — to download the Whisper model once, and
    when EDIT looks for lyrics on LRCLIB (only the artist, the title and the length are sent). Nothing else, nothing
    about you.
  - MEDIA is an **option (29 EUR or 29 USD minimum, one payment, no subscription)**: at the first click a window shows what it does and the PayPal
    link; write "Media" in the PayPal message and you receive the password by e-mail. Once entered, it is remembered on
    this computer. **TRY** (11.0.1): everything for **3 minutes of playing** each time you start PianoToLife (the time
    left shows in the player's title); a BOUNCE with the media needs the password.
  - **MIDI loop** (11.0.0): LOOP in the LOAD MIDI menu now also repeats a single MIDI file.
- **Compact view**: fold the interface into a small bar while you play (11.2.1: without tooltips). Since 10.4.2 it also has what serves while
  playing: the MIDI player and METRO (standalone), the chord you play, a lit and clickable keyboard, TRUE PEAK and LUFS,
  and since 10.6.2 the preset list (the instruments in SAMPLER mode). Since 10.6.3 the compact bar is always shown at
  100 %; the view size you choose (90 / 80 %; since 10.9.8 also 70 / 60 / 50 %) is for the full window. Since 10.7.0 it also has VOL, since 10.8.1 OUTPUT
  and the level meter, in its right column (see section 11). Since 10.9.6, **HOST | SAMPLER** sits where the pedal mode
  was, so you can switch mode and choose your presets in either from the compact bar (the pedal mode stays in the full
  window).
- **Damper mechanics view**: a live view of the dampers and strings (held keys in orange), at no CPU cost. Since
  10.4.0:
  - **an 88-key keyboard** under the strings lights up with them; its colour follows the velocity (pale = soft, full
    orange = loud), paler for notes kept by the pedal (much paler since 11.1.6 with the velocity colours); **right-click** (11.1.1): orange, **velocity colours** (green, yellow, orange, red) or orange to red — the compact keyboard too; since 11.1.2 both are drawn with relief, as in MAGIC VIEW. **Click it to play**: lower on the key = louder; drag across
    the keys for a glissando. These notes go through the same path as your keyboard (HOST and SAMPLER, MIDI Monitor,
    ENGINE MIDI REC);
  - **the chord you play**, in large letters left of BODY: the keys held and the notes the pedals keep ringing.
    Only chord names are shown (C, Am7, Cmaj7/E…; since 10.9.7 the 13th chords too: Cmaj13, C13, Cm13; since 10.9.9 Cmaj11 and Cm(maj11)). A chord held in the left hand stays shown while the right hand
    plays a melody over it, and is completed when the melody adds to it.
- **View size and small screens** (10.9.8): the menu left of the version offers **100 / 90 / 80 / 70 / 60 / 50 %**. At
  the start, if the window does not fit the screen, PianoToLife takes the largest size that fits (not remembered: on a
  bigger screen your size comes back) — e.g. a 1920 × 1080 laptop with Windows display scaling at 125 % (80 %) or
  175 % (50 %, about the size of 100 % on a normal screen). The standalone window always keeps its title bar on the
  screen, and after a change of size the whole window comes back into view.
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
| The window is larger than the screen, its title bar out of reach (Windows) | Choose a smaller view size (80 %, or 50 % with display scaling at 175 %); 10.9.8 does it at the start and keeps the title bar on the screen. Before 10.9.8: Alt + Space, Move, arrow keys |

A keyboard or a piano that behaves in its own way? Please contact me at
[pianotolife@outlook.com](mailto:pianotolife@outlook.com) with an explanation (a MIDI Monitor export is perfect).
