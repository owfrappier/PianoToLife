# PianoToLife Sampler — User Manual

*Version 10.3.2 · [Version française](MANUEL_SAMPLER.md) · General manual: [User Manual](USER_MANUAL.md)*

PianoToLife's built-in sampler plays **your own piano samples** with all of PianoToLife's engines on top of
them. This manual explains how to turn a folder of samples into a playable piano, what every button does, and
how to get the best from it.

---

## Contents

1. [The idea: pedal-up samples, everything else modelled](#1-the-idea-pedal-up-samples-everything-else-modelled)
2. [Quick start: a piano in 10 steps](#2-quick-start-a-piano-in-10-steps)
3. [Preparing your samples](#3-preparing-your-samples)
4. [The EDIT window](#4-the-edit-window)
5. [The mapping tools, in the recommended order](#5-the-mapping-tools-in-the-recommended-order)
6. [Settings of each key](#6-settings-of-each-key)
7. [Saving and managing sets](#7-saving-and-managing-sets)
8. [The MIX window: microphones and streaming](#8-the-mix-window-microphones-and-streaming)
9. [Playing the sampler](#9-playing-the-sampler)
10. [Files and folders](#10-files-and-folders)
11. [Troubleshooting](#11-troubleshooting)
12. [Distributing sampled pianos](#12-distributing-sampled-pianos)

---

## 1. The idea: pedal-up samples, everything else modelled

A sampled piano usually needs thousands of files: pedal-down notes, release samples, resonance, pedal noises…
PianoToLife only needs **the pedal-up notes**. Everything that happens around the strike is **modelled live**:

- sympathetic resonance of the free strings;
- sustain pedal, half pedal and pedal noise;
- una corda (soft pedal);
- release, dampers and release velocity;
- repeated notes (a new strike does not cut the previous one).

A library of **3 to 6 velocity layers** is enough: PianoToLife smooths the steps between layers so that it plays
like a deeply sampled piano. Deep libraries (60 layers, several microphones, tens of gigabytes) are streamed from the
disk and play just as well.

---

## 2. Quick start: a piano in 10 steps

1. At the top of the main window, switch **HOST / SAMPLER** to **SAMPLER**, then open **EDIT**.
2. Click **NEW** for an empty set.
3. Choose the microphone (**MIC 1** for a single-microphone library).
4. **Drop your samples** anywhere on the window: WAV, AIFF or FLAC files, a whole folder, an `.sfz` or a Decent
   Sampler `.dspreset`. PianoToLife listens to each sample, finds its key, and places the velocity layers. A
   progress bar shows the import; click the status line to stop it.
5. For other microphone positions, select **MIC 2**, **MIC 3**… and drop their samples the same way.
6. Click **RECAL A4**: PianoToLife listens to A4, places its layers on the loudness of a real grand, then maps every
   key the same way.
7. Click **FIX STEPS**: the orange and red layer boundaries become green.
8. Click **ALIGN ATTACKS**: every strike starts at the same moment, whatever the layer and microphone.
9. Click **BALANCE ▸ Smooth**: the volume is even from one key to the next.
10. Click **SAVE SET...** (switch **FLAC** on first if you want a smaller file without any loss). Your piano is
    ready: choose it in the SAMPLER list of the main window, and set its microphones in **MIX**.

Every tool has **UNDO** (Cmd / Ctrl + Z) and **REDO** (Shift + Cmd / Ctrl + Z).

---

## 3. Preparing your samples

**What to record or collect**

- **Pedal-up notes only**, one strike per file, long enough to hear the decay.
- Any number of velocity layers per key. More is better, but 3 layers already play well.
- Any number of keys: a library sampled every 2 or 3 notes is completed by **FILL GAPS**.
- Up to **5 microphone positions** (one per MIC).

**Formats**: WAV, AIFF, FLAC, mono or stereo, any bit depth. Samples above 48 kHz are converted to 44.1 / 48 kHz when
the set is saved (a piano has nothing useful above 20 kHz).

**Naming your files** (optional but recommended). PianoToLife finds the key from the sound itself, but a clear name
makes everything safer:

| What | Write it as a separate word | Example |
|---|---|---|
| The key | note name or MIDI number | `Piano_C4_mf.wav`, `Piano_F#7_p.wav`, `Piano_060_mf.wav` |
| The layer: dynamics | `ppp pp p mp mf f ff fff` | `Steinway_C4_mp.wav` |
| The layer: velocity range | `1-12`, `033-064` | `Steinway_C4_033-064.wav` |
| The layer: velocity | `v64`, `vel64` | `Steinway_C4_v64.wav` |
| The layer: number | `layer3`, `L3`, `VL3`, `dyn3` | `Steinway_C4_L3.wav` |

Use **one style for the whole library**. A microphone (`mic2`) or a round robin (`rr2`) is never read as a layer.
Note names in small letters work too (`f#7`, `c8`).

**Imperfect libraries are fine.** PianoToLife handles libraries that are normalised (every layer raised to the same
peak), badly cut (strikes up to 1.5 s late, starts cut inside the sound), mapped one octave off, or whose
microphones were cut separately.

---

## 4. The EDIT window

### The map

The large grid shows the **88 keys** (horizontally) and the **velocities 1–127** (vertically). Each rectangle is a
**zone**: one sample, on one key, for a range of velocities. The grid shows the microphone selected with **MIC 1–5**.

The line between two layers of a key is coloured by the **timbre step** heard when you play across it:
**green** under 2 dB, **orange** under 5 dB, **red** above.

**Mouse and keyboard**

| Action | How |
|---|---|
| Select zones | Drag anywhere to draw a rectangle (like Kontakt); a click selects one zone; Shift adds or removes |
| Move zones | Drag a selected (white) zone |
| Change velocities | Drag the top or bottom edge of a selected zone; or Up / Down arrows (top edge), Alt / Option + arrows (bottom edge), Shift = 10 at a time |
| Stretch a sample over neighbour keys | Cmd / Ctrl + drag sideways (Cmd / Ctrl + click: no stretch) |
| Delete | Delete / Backspace: the selected zones; nothing selected: all the layers of the selected key (this MIC) |
| Select by playing | **SELECT BY MIDI** on: the key you play is selected, with the zone that sounded at that velocity (red velocity line) |

The **side panel** shows the zones of the selected key: velocity range, gain, file, the key heard and its tuning in
cents, its brightness, the velocity whose timbre it has, the step to the layer below, and where its strike is.
An **orange** zone means the key heard differs from the file name: check it.

### Options at the top

| Option | What it does | Default |
|---|---|---|
| **Reference** (Grand D / Grand B / Upright) | The piano whose loudness and brightness curves are used to place the layers and their gains | Grand B |
| **AUTO KEY** | Each sample goes to the key of its sound (checked against its file name). Off: key from the file name, else where you drop it | On |
| **AUTO LAYERS** | Velocity ranges and gains placed on the reference. Off: the layers of a key share the velocities equally (or take the ranges written in the names) | On |
| **AUTO NAME** | The dynamics or layer numbers in the file names set the order of the layers (safer when two layers sound alike) | On |
| **SOFT TIMBRE** + COLOR | A note played below its layer's own velocity gets the darker timbre of a softer strike, not only a lower level: pp under the softest layer and smooth boundaries. COLOR (−100 to +100 %) sets how much | On, 0 % |
| **HARD TIMBRE** + COLOR | A note played above its layer's velocity gets brighter, towards a harder strike (at most +6 dB, not in the deep bass). For a top layer that is not really fff | Off, 0 % |
| **FADE IN** | Every sample starts with a 1 ms fade: a start cut inside the sound never clicks | Off |
| **FLAC** | At the next SAVE SET, the samples are stored compressed without any loss (identical to the bit, often 3 to 6 times smaller). Off = WAV as they are | Off |

**SOFT TIMBRE / HARD TIMBRE and their COLOR**

| Setting | SOFT TIMBRE | HARD TIMBRE |
|---|---|---|
| Box unticked | No effect, whatever the COLOR | No effect, whatever the COLOR |
| COLOR **0 %** | **Active, as measured**: a note played below its layer's own velocity gets the darker timbre of a softer strike; at or above it, nothing changes | **Active, as measured**: above the layer's velocity, about +0.28 dB of brightness per velocity, at most +6 dB (nothing below C2) |
| COLOR above 0 | More felted: every note sounds like a strike up to 24 velocities softer, even at its layer's own velocity | Brighter: starts up to 24 velocities lower, up to +12 dB |
| COLOR between 0 and −100 % | Less of the darkening | Less of the brightening |
| COLOR **−100 %** | **No effect** (same as unticked) | **No effect** (same as unticked) |

So 0 % does not mean "off": it means "as measured on the reference piano". To switch an effect off, untick its box
or set its COLOR to −100 %. With SOFT TIMBRE on, the steps between velocity layers can no longer be heard.

---

## 5. The mapping tools, in the recommended order

The tools are in the bottom bar. With zones selected, most of them work on **their keys only**; with nothing
selected, on **every key** of the displayed microphone.

1. **RECAL A4** — listens to A4 at all 127 velocities, places its layers where their loudness belongs on the
   reference curve, levels them, then gives every key with the same number of layers A4's velocity ranges and
   listens to it the same way. It also measures A4's tuning (sent to SR A4 Tuning, so 440 Hz plays the set as
   recorded). Works on normalised libraries: it then reads the attack and brightness of each layer instead of its
   level.
2. **FIX STEPS** — moves the orange / red boundaries to the velocity where the two timbres meet, smoothed over the
   neighbouring keys. Run it **after** RECAL A4 (RECAL places the boundaries by loudness again).
3. **ALIGN ATTACKS** — finds the strike in every sample and makes every layer and every microphone start 3 ms before
   it: no flam when the dynamics change, microphones in phase. The files are not changed.
4. **FILL GAPS** — every key without a sample is played by the nearest sampled key, transposed (half the gap each
   way). A key's own samples always win.
5. **BALANCE** — evens out the volume from one key to the next, measured at velocity 127 (each key's layers follow).
   - **Smooth**: the set's own curve without the jumps (the register balance of the recording is kept).
   - **Grand D / Grand B / Upright**: the bass-to-treble balance of a reference piano, at your set's level.

   It sets the key gains (at most ±6 dB); velocity ranges, layer gains and dynamics are not touched.
6. **AUTO RELEASE** — each key's release time as measured on a concert grand (380–510 ms to −60 dB), Infinite above
   the last damped key.
7. **LEVEL** and **AUTO** — the level of the whole set; AUTO makes the loudest note at velocity 127 peak at −9 dBFS
   (room for chords, resonance and release).

---

## 6. Settings of each key

Select a key (or several zones) and use the knobs of the key panel. They apply to all the layers of the selected
keys.

| Knob | What it does |
|---|---|
| **Gain** | Level of the key, −24 to +12 dB (BALANCE writes it) |
| **Dynamics** | 100 % = the dynamic range of the reference piano. Less: smaller range (soft notes louder); more: wider |
| **Attack** | Fade-in time, 0 = the sample as recorded |
| **Decay** / **Sustain** | Time to reach the Sustain level; 0 = the natural decay of the sample |
| **Release** | 0 = **Auto** (PianoToLife's damper model); a time in ms; all the way right = **Infinite** (no damper: undamped top keys) |
| **Tune** | Fine tune in cents |
| **LP** + cutoff + **LP Vel** | Optional low-pass per voice; LP Vel makes soft notes darker (up to 3 octaves lower at 100 %) |

---

## 7. Saving and managing sets

| Button | What it does |
|---|---|
| **NEW** | An empty set (the set open now is not changed on disk) |
| **Name** (under the title) | Click to **RENAME** the set and its sample file |
| **SAVE SET...** | Saves the set in your library: the map (`.ptlset`) and its samples in an encrypted container (`.wptl`), rewritten only when samples change |
| **SAVE AS VARIANT** | Another set on the **same samples** (shares the `.wptl`, no copy) — e.g. a bright and a dark version |
| **PASSWORD...** | Protects EDIT with a password (playing the set never asks for it). Empty = no password |
| **DELETE** | Removes the selected zones (see the table above) |
| **BACK** | Returns to the main window |

A set saved on Mac opens on Windows and back. Saving a preset in SAMPLER mode creates a **`[SAMP]` preset** that
carries the mapping and the resonance model; only the samples (`.wptl`) stay apart.

---

## 8. The MIX window: microphones and streaming

### Microphones

Each of the 5 microphones has its strip: **name** (double-click to rename), **ON** (an off microphone is not
loaded: no memory, no CPU), **solo**, **mute**, **level**, **pan**, **width**, **delay** (to line a distant
microphone up with the close ones, or keep its natural room delay) and a **TRUE PEAK** meter (red = it clipped;
click to reset). Ready-made mixes: **Close**, **Player**, **Hall** (moving a control makes it Custom).

**ALL MICS TRUE PEAK** watches the 5 microphones together. **BODY** sets the perceived size of the piano (also on
the main window).

### Streaming

Large sets are played from the disk: only the beginning of each sample stays in memory.

| Setting | What it does | Default |
|---|---|---|
| **Disk** | Where your samples are: Auto (measured), SSD, HDD, Slow | Auto |
| **Preload** | Beginning of each sample kept in memory; Auto follows the disk (SSD 16 KB, HDD 64 KB, Slow 128 KB) | Auto |
| **Cache** | Memory shared by the playing voices for what comes from the disk; bigger = fewer dropouts with many voices | 128 MB |
| **Per key** | How many strikes of the same key may ring together (repeated notes under the pedal) | 4 |
| **Voices** | Polyphony, all microphones together (2 microphones = 2 voices per note). When reached, the quietest voice fades out in 8 ms | 256 (Max 512) |
| **Test again** | Measures the disk again (e.g. after moving the samples) | |

**LIBRARY** chooses the folder of your sets (put it on your fastest disk). With the copy option, SAVE SET copies the
samples into a `Samples` folder beside the set.

---

## 9. Playing the sampler

In SAMPLER mode, PianoToLife's engines play on your samples:

- **Sympathetic resonance**, with the piano's own Piano Model (`.srpiano`) — you can capture one from your set
  (Capture), so the resonance has the colour of your piano.
- **Sustain**: always Host Sustain in SAMPLER, with a native **half pedal** on the voices themselves (Progressive,
  or Switch for on / off pedals). Sostenuto works.
- **Una corda**: simulated on every voice (level and partials of a real una corda, plus the halo of the string not
  struck).
- **Release**: PianoToLife's dampers; with a keyboard that sends release velocity, a slow release lands the damper
  later (see Keyboard Note-Off Floor and Curve in the KEYBOARD section).
- **Repeated notes**: a new strike does not cut the previous one; it goes on, a little lower (Per key in MIX).
- **Tuning**: SR Transpose, SR Fine Pitch and SR A4 Tuning play on the sampler.
- **BODY**: the perceived size of the piano.

**Layer detector** (next to Capture): plays a note at the 127 velocities and lists the real layers of the piano, to
check a set.  **LEVEL TEST**: plays A0, C2, C4, C6, C8 at velocity 127 and tells you whether the piano clips.

---

## 10. Files and folders

| File | What it is |
|---|---|
| `.ptlset` | The set: the map, key settings and options (small) |
| `.wptl` | The samples, in an encrypted container (beside the set) |
| `[SAMP]` preset | A preset of the SAMPLER mode: mapping + resonance model; double-click it (standalone) or drop it on the window |

Keep a piano's folder together (preset, `.ptlset`, `.wptl`): it can then be moved or backed up as it is.

**Missing samples**: if a session or a preset points to a piano whose samples were deleted, moved or are on a disk
that is not connected, a window asks you to **LOCATE** them (PianoToLife remembers the new place) or to **FORGET**
that piano (it is then no longer asked about).

---

## 11. Troubleshooting

| Problem | Solution |
|---|---|
| A sample is on the wrong key or octave | Check the orange zones in the side panel; put the note in the file name (`C4`, `060`); AUTO KEY on |
| Two layers are in the wrong order | AUTO NAME with dynamics in the names; otherwise move them by hand |
| Steps when playing crescendo (orange / red boundaries) | RECAL A4, then FIX STEPS; SOFT TIMBRE on; HARD TIMBRE for a dark top layer |
| Some keys louder than their neighbours | BALANCE ▸ Smooth (or a reference piano) |
| A click at the start of some notes | ALIGN ATTACKS; FADE IN for starts cut inside the sound |
| Notes sound late or flam between layers | ALIGN ATTACKS |
| Dropouts or crackles with many notes | MIX: Test again, a bigger Cache, Preload one step up, fewer Voices, or the samples on an SSD |
| The piano clips | LEVEL ▸ AUTO; watch TRUE PEAK in MIX; LEVEL TEST |
| "Sample set not found" | LOCATE the folder, or FORGET the piano |

A keyboard or a library that behaves in its own way? Please contact me with an explanation (a MIDI Monitor export
is perfect).

---

## 12. Distributing sampled pianos

Making sample sets with PianoToLife and playing them for your own use is free. **Any public distribution of a
sampled piano made for PianoToLife's sampler** (sample sets, `.ptlset` / `.wptl` files, `[SAMP]` presets), **free or
paid, requires my prior authorization.** Please contact me at
[olivier.frappier@live.fr](mailto:olivier.frappier@live.fr) before publishing anything: together we will set up its
protection (encrypted container, password, licence in the buyer's name) and the way it is distributed.
