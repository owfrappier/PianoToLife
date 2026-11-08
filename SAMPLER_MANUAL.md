# PianoToLife Sampler — User Manual

*Version 10.9.9 · [Version française](MANUEL_SAMPLER.md) · General manual: [User Manual](USER_MANUAL.md)*

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
4. **Drop your samples** anywhere on the window: WAV, AIFF, FLAC or Kontakt `.ncw` files, a whole folder (its
   sub-folders too; releases, noises, pedal-down and una corda samples are left out by their names), an `.sfz` or a
   Decent Sampler `.dspreset`. PianoToLife listens to each sample, finds its key, and places the velocity layers. A
   progress bar shows the import; click the status line to stop it.
5. For other microphone positions, select **MIC 2**, **MIC 3**… and drop their samples the same way.
6. Click **AUTO DYN1** (a library recorded evenly key to key) or **AUTO DYN2** (an uneven one): PianoToLife listens
   to A4, places its layers on the loudness of a real grand, then maps every key (10.6.2).
7. Click **FIX STEPS**: the orange and red layer boundaries become green.
8. Click **ALIGN ATTACKS**: every strike starts at the same moment, whatever the layer and microphone.
9. Click **BALANCE ▸ Smooth**: the volume is even from one key to the next.
10. Click **SAVE SAMPLES...** (switch **FLAC** on first if you want a smaller file without any loss): the samples go
    into their `.wptl`. Then, in the main window, set its microphones in **MIX** and click **SAVE AS**: the instrument
    (`.ptlset`) is saved beside its samples with the mapping and every setting. Your piano is ready - two files, like a
    Kontakt `.nki` and its `.nkx` (10.6.0).

Every tool has **UNDO** (Cmd / Ctrl + Z) and **REDO** (Shift + Cmd / Ctrl + Z); since 10.6.2 the UNDO and REDO
buttons are in the right panel, just above the key's settings. Since 10.9.3 every step is named: the tooltip says what
UNDO / REDO will do (e.g. *UNDO: AUTO DYN2*), the status line what was undone, and a **right-click** on UNDO or REDO lists
the last steps (up to 30): choose one to go back to just before it, in one go.

---

## 3. Preparing your samples

**What to record or collect**

- **Pedal-up notes only**, one strike per file, long enough to hear the decay.
- Any number of velocity layers per key. More is better, but 3 layers already play well.
- Any number of keys: a library sampled every 2 or 3 notes is completed by **FILL GAPS**.
- Up to **5 microphone positions** (one per MIC).

**Formats**: WAV, AIFF, FLAC and Kontakt `.ncw` (10.3.5), mono or stereo, any bit depth. Samples above 48 kHz are
converted to 44.1 / 48 kHz when the set is saved (a piano has nothing useful above 20 kHz); `.ncw` samples are always
rewritten as WAV or FLAC in the set. Encrypted libraries are not read: use only libraries whose licence allows it
(since 10.9.2 a popup says so when encrypted `.ncw` files are dropped: they keep the extension but are not NCW).
Every analysis (key, level, brightness) is made **in stereo**, channel by channel: a key out of phase between two
spaced microphones is measured as you hear it.

**Naming your files** (optional but recommended). PianoToLife finds the key from the sound itself, but a clear name
makes everything safer:

| What | Write it as a separate word | Example |
|---|---|---|
| The key | note name or MIDI number (alone, or glued after letters) | `Piano_C4_mf.wav`, `Piano_F#7_p.wav`, `Piano_060_mf.wav`, `Piano-NP60-103.wav` |
| The layer: dynamics | `ppp pp p mp mf f ff fff` | `Steinway_C4_mp.wav` |
| The layer: velocity range | `1-12`, `033-064` | `Steinway_C4_033-064.wav` |
| The layer: velocity | `v64`, `vel64` | `Steinway_C4_v64.wav` |
| The layer: number | `layer3`, `L3`, `VL3`, `dyn3` | `Steinway_C4_L3.wav` |
| The layer: velocity right after the key (10.3.8) | a number after the note | `Piano-A2-40.wav`, `Piano-NP60-103.wav` |
| The layer: any number that follows the loudness (10.3.8) | found by comparing the numbers with the measured levels of the layers (a take or hammer-time number, in either direction) | `Piano_B3_M1_138_126.wav` |

Use **one style for the whole library**. A microphone (`mic2`) is never read as a layer. **Round robins** (`rr2`,
`seq2`, or a last number right after the key when the name has a layer: `Piano_Dyn1_21_02`) are left out after the
first: REP gives every strike its own variation. Note names in small letters work too (`f#7`, `c8`); a key written
`109` is read as C8. Names one or two octaves off for the whole library (A0 named `A-2` or `A-1`) are corrected on
import. With AUTO LAYERS off, velocities written in the names become the layers' ranges: from each number up to the
next one, or — when the numbers end at 127 and none is 1 — up to each number (the velocity the layer was recorded at).

**Imperfect libraries are fine.** PianoToLife handles libraries that are normalised (every layer raised to the same
peak), badly cut (strikes up to 1.5 s late, starts cut inside the sound), named one or two octaves off, or whose
microphones were cut separately. Very soft treble notes, where the hammer noise outlasts the string, are checked on
their first 150 ms (10.3.8).

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
| Show by playing | **SHOW BY MIDI** on (10.4.3): the key you play is shown in the side panel, with a red line in the zone that sounded at that velocity, and the velocity played next to the number of layers (10.4.6). The selection is not changed. |
| Listen to one sample | Right-click it in the side panel or in the grid (green ▶); right-click again = stop |

The **side panel** shows, in its title, the key, the microphone and the number of layers mapped on it (10.4.2), then the zones of the selected key: velocity range, gain, file, the key heard and its tuning in
cents, its brightness, the velocity whose timbre it has, the step to the layer below, and where its strike is.
An **orange** zone means the key heard differs from the file name: check it. In the side panel (10.3.8), a **click**
on a sample selects it (highlighted), the mouse **over** it shows its information (file, audio format, key, velocities,
gain, level, brightness, tuning, strike) and a **right-click** plays it alone. A long list scrolls with the mouse wheel
or the ▲ / ▼ lines, and follows the selection.

**What you hear in EDIT** (10.3.8): the microphone shown (MIC 1–5) alone and neutral — 0 dB, centred, full width, no
delay, no L↔R, BODY at 0 — whatever the MIX. Back to the main window, the MIX drives the microphones again.

### Options at the top

| Option | What it does | Default |
|---|---|---|
| **Reference** (Grand D / Grand B / Upright) | The piano whose loudness and brightness curves are used to place the layers and their gains | Grand B |
| **AUTO KEY** | Each sample goes to the key of its sound (checked against its file name). Off: key from the file name, else where you drop it | On |
| **AUTO LAYERS** | Velocity ranges and gains placed on the reference. Off: the layers of a key share the velocities equally (or take the ranges written in the names) | On |
| **Samples** (auto / Normalised / Not normalised, 10.3.8; next to AUTO LAYERS since 10.4.6) | How AUTO LAYERS and AUTO DYN order and place the layers of a key. **Not normalised** (the library keeps its dynamics): by their levels, on the reference's loudness curve. **Normalised** (every layer raised to the same level): by their brightness. **Auto**: by the levels when the layers of the key are more than 12 dB apart. AUTO DYN in auto also treats A4 as normalised when its layers peak at the same level. A change places every key again (keys set by hand kept). **Since 10.9.1, AUTO DYN tells you which one suits** (see AUTO DYN1 / AUTO DYN2) | Auto |
| **AUTO NAME** | The dynamics, velocities or layer numbers in the file names set the order of the layers (safer when two layers sound alike) | On |
| **SOFT TIMBRE** + COLOR | A note played below its layer's own velocity gets the darker timbre of a softer strike (the 2–4 kHz and 4–8 kHz colour of the reference piano, measured on every key and velocity), not only a lower level: pp under the softest layer and smooth boundaries. COLOR (−100 to +100 %) sets how much | On, 0 % |
| **HARD TIMBRE** + COLOR | A note played above its layer's velocity gets brighter, like a harder strike on the reference piano (measured on every key, up to +18 dB): with few layers, the velocities in between sound like real strikes. For a top layer that is not really fff, or a set with few layers | Off, 0 % |
| **MEDIUM TIMBRE** + COLOR (10.6.3) | The colour of the middle velocities (about v48–84, mp to mf), between SOFT and HARD, as the reference piano's voicing (measured). Higher = brighter, lower = darker; 0 % = as measured. The level does not change | On, 0 % |
| **HAMMER** (10.6.3) | The hardness of the hammers, for the whole piano and every velocity, as the reference piano's hammer hardness (measured). Lower: a piano you find too bright becomes softer, as if a technician had voiced (needled) its hammers — around −20 % a more romantic character, warmer forte; towards −100 % a very felted sound, close to an una corda. Higher: harder hammers, the soft notes get brighter. Timbre only, the level does not change. Set by hand (AUTO COLOR leaves it alone) | 0 % |
| **XCOLOR** (10.6.3) — Real layers transition enhancer | At each boundary between two layers, both play over this many velocities, the lower one fading out as the upper one fades in: you go from one real strike to the next gradually. Never more than two layers at once: the width is limited by the layers on each side, so a piano with many layers (50 or more) gets almost nothing of it, which is normal. Most useful up to about ten layers; it also softens a layer that sounds a little different from its neighbours (without replacing it). **16 is a good start**, then run **ALIGN ATTACKS**: with XCOLOR on it also puts each layer in phase with the one below, so they blend without a hollow, "comb" sound | Off |
| **FADE IN** | Every sample starts with a 1 ms fade: a start cut inside the sound never clicks | Off |
| **FLAC** | At the next SAVE SAMPLES, the samples are stored compressed without any loss (identical to the bit, often 3 to 6 times smaller). Off = WAV as they are | Off |

**SOFT TIMBRE / HARD TIMBRE and their COLOR**

| Setting | SOFT TIMBRE | HARD TIMBRE |
|---|---|---|
| Box unticked | No effect, whatever the COLOR | No effect, whatever the COLOR |
| COLOR **0 %** | **Active, as measured**: a note played below its layer's own velocity gets the darker timbre of a softer strike; at or above it, nothing changes | **Active, as measured**: above the layer's velocity, the brightening of the reference piano at that velocity (about twice as much in 4–8 kHz as in 2–4 kHz) |
| COLOR above 0 | More felted: every note sounds like a strike up to 24 velocities softer, even at its layer's own velocity | Brighter: starts up to 24 velocities lower |
| COLOR between 0 and −100 % | Less of the darkening | Less of the brightening |
| COLOR **−100 %** | **No effect** (same as unticked) | **No effect** (same as unticked) |

So 0 % does not mean "off": it means "as measured on the reference piano". To switch an effect off, untick its box
or set its COLOR to −100 %. With SOFT TIMBRE on, the steps between velocity layers can no longer be heard.
**MEDIUM TIMBRE** (10.6.3) works the same way for the middle velocities (about v48–84). Since 10.6.3 SOFT, MEDIUM and
HARD TIMBRE, HAMMER and XCOLOR have their own row in SAMPLER EDIT (the third one).

**LISTEN** (10.6.3, right panel, left of UNDO): plays the key shown from velocity 1 to 127, one velocity out of 1, 2,
4 or 8 (menu beside it), as you will hear it — its layers, their boundaries and the colours. Click again to stop.
Nothing is measured or changed. The ideal way to hear the transitions between layers after AUTO DYN, AUTO COLOR or
XCOLOR.

---

## 5. The mapping tools, in the recommended order

The tools are in the bottom bar, **in the order to use them**, with **>** between them (10.5.6):
**FILL GAPS > ALIGN ATTACKS > AUTO DYN1 or AUTO DYN2 > FIX STEPS > AUTO COLOR > BALANCE > AUTO RELEASE**. With
zones selected, most of them work on **their keys only**; with nothing selected, on **every key** of the displayed
microphone. AUTO DYN1 and AUTO DYN2 always work on every key. **SHOW BY MIDI** never selects anything: click an empty part of the grid to clear
a selection before working on every key.

1. **FILL GAPS** — every key without a sample is played by the nearest sampled key, transposed (half the gap each
   way). A key's own samples always win.
2. **ALIGN ATTACKS** — finds the strike in every sample and makes every layer and every microphone start 3 ms before
   it: no flam when the dynamics change, microphones in phase. The files are not changed. Before AUTO DYN, so that it
   listens to well-aligned strikes.
3. **AUTO DYN1 / AUTO DYN2** (10.6.2; one AUTO DYN before, called RECAL A4 before 10.4.2) — both listen to A4 at all
   127 velocities, place its layers where their loudness belongs on the reference curve and level them. They also
   measure A4's tuning (sent to SR A4 Tuning: that value plays the set as recorded; RESET in the TEMPERAMENT window
   goes back to it). Then:
   - **AUTO DYN1** (global, as before 10.5.6): every key with **as many layers as A4** gets A4's velocity ranges and is
     levelled; keys with another number of layers are left as they are (AUTO DYN2 places them). For a library
     recorded evenly key to key.
   - **AUTO DYN2** (per key, the AUTO DYN of 10.5.6): **every other key is listened to and placed on its own**, whatever
   its number of layers, on the same reference curve (the reference's level curve is the same on every key), then
   **smoothed with its neighbours** (2 keys each side) so that the boundaries do not jump from one key to the next, and
   levelled. Uneven libraries (a layer played louder on some keys, manual sampling, a layer missing in a register)
   become even along the keyboard. A4 stays the anchor; key gains (BALANCE) are kept. Works on normalised libraries
   (peak or loudness): A4 is then placed by the attack and brightness of its layers, and the other keys take A4's
   placement by rank. It follows the **Samples** setting (10.4.6). Since 10.5.1 it listens with SOFT / HARD COLOR as
   they are played, and when two or more soft layers would be piled under v16 (a pp recorded softer than the reference
   ever plays) they are spread evenly from v1 up to the first layer above, their gains set on the reference curve
   (Dynamics is not changed; a very soft layer's noise comes up with its gain).
   **RANGE** (10.9.0), in the AUTO DYN window once the analysis is done: the dynamic range of the whole keyboard,
   **−10 to +10 dB** — as between a finely regulated piano and a less even one (the regulation of the action and the
   voicing of the hammers change how soft and how loud a piano can play). **+** = wider (v1 up to 10 dB softer),
   **−** = narrower (the soft notes louder). v127 does not move and the layers played stay the same: only the levels
   change, along the reference curve; the green curve of the window follows. Nothing is listened to again; one UNDO;
   double-click = 0. **A new AUTO DYN puts RANGE back to 0**: set it after the analysis, then run AUTO COLOR again.
   **Which Samples setting suits your library** (10.9.1): before the AUTO DYN window, a message says what the raw
   samples show — whether the loudest layer peaks at the same level on nearly every key (a library normalised: a real
   recording varies from key to key), how far apart A4's layers are compared with a real piano — and whether the
   Samples setting used suits it. If it does not, **one click sets the advised one and runs the same AUTO DYN again**
   (or keep the result).
4. **FIX STEPS** — moves the orange / red boundaries to the velocity where the two timbres meet, smoothed over the
   neighbouring keys. Run it **after** AUTO DYN1 / DYN2 (they place the boundaries by loudness again).
5. **AUTO COLOR** (10.5.1) — sets SOFT, MEDIUM (10.6.3) and HARD COLOR so that the brightness of the layers follows
   the colour of the reference piano from soft to loud (measured on A2, A3, A4, A5 at 13 velocities, 2–4 and 4–8 kHz,
   as on the reference; only the shape counts, a piano may stay brighter or darker overall). Since 10.6.3 it first asks
   which zones to set: **SOFT, MEDIUM and HARD, all ticked by default** (they work best together); untick a zone to
   leave it as it is — it is then switched off, and its TIMBRE box in the row follows. HAMMER is never touched. Run it
   again after AUTO DYN. UNDO puts the sliders back. Since 10.9.0 it follows **RANGE**: a velocity made softer is aimed
   at a darker colour, a louder one at a brighter colour, as on a real piano.
6. **BALANCE** — evens out the volume from one key to the next, measured at velocity 127 (each key's layers follow).
   - **Smooth**: the set's own curve without the jumps (the register balance of the recording is kept).
   - **Grand D / Grand B / Upright**: the bass-to-treble balance of a reference piano, at your set's level.

   It sets the key gains (at most ±6 dB); velocity ranges, layer gains and dynamics are not touched.
7. **AUTO RELEASE** — each key's release time as measured on a concert grand (380–510 ms to −60 dB), Infinite above
   **Undamped Keys Above**. That setting is also in the key panel (**Undamped**, the same as the main window's);
   moved by hand, the keys that cross it get AUTO RELEASE again (10.3.8). Since 10.6.2, AUTO RELEASE first shows the
   last key with a damper and asks whether it really is your piano's last damped note; change it there if needed
   (the same setting everywhere), then AUTO RELEASE runs.
8. **LEVEL** and **AUTO** (left of the tools, by the level slider) — the level of the whole set; AUTO makes the loudest
   note at velocity 127 peak at −9 dBFS (room for chords, resonance and release). Best done at the end. This is the
   instrument's real level: VOL (by the Ceiling) is a listening volume (saved with the preset since 10.9.2), so set the
   level here and all your instruments stay coherent.

### Taking the room out of the samples: DRY / DENOISE (10.9.0)

Born from our research on modelling recordings of real pianos. A piano recorded in a room that rings too much — or that
does not suit your music — keeps that room in every sample. **DRY** takes it out, so that you can put the piano in the
room you choose with the **REVERB** (ALGO or IR, 10.9.2): one clean room for everything PianoToLife plays and adds.

**How it works.** For each sample, PianoToLife finds the partials of the note on the sample itself (in the bass from the
spacing of the strong partials, the fundamental of the lowest notes being very weak on every piano; in the treble
with a wider search, the tuning being stretched). It keeps the real content of each partial — the beating of the
unison strings included — and takes out what lies between them: the room, the hiss, part of the body. **The strike
stays the original**: DRY waits until the knock, the case and the neighbouring strings have faded to just above the
room (80 to 600 ms, measured on each sample), then comes in gradually. **100 % is safe**.

**DENOISE** is light and careful: the hiss is measured on each sample and lowered by 12 dB at most, smoothed in time so
that it never warbles.

**DRY / DENOISE / BODY is optional** (10.9.5): an extra processing of a set **already saved**. Finish your mapping and
**SAVE SAMPLES** first — MAKE works on the samples inside the set's .wptl (if they are not there yet, a message says so).
You can switch between the original and the processed samples at any time.

**Versions of the piano** (10.9.8): a piano has up to **four versions — ORIG., DRY 1, DRY 2, DRY 3**. A version is the
**whole piano** (every microphone), and **each version keeps its own settings**: mapping, EDIT options and every
setting of the main window — tune DRY 1 by ear (AUTO COLOR, BALANCE...) without touching ORIG.

**The DRY / DENOISE / BODY... button** (second row of EDIT, after FLAC) opens the panel; you listen to the **microphone
selected** at the top, and MAKE processes every microphone:

1. **Listen first.** Choose a **KEY** and a **VELOCITY**, then compare **> ORIGINAL** and **> PROCESSED** (the same
   button again stops). **A6** by default: **the room is easiest to hear in the treble**, where the partials are few
   and the notes short (with no release samples, the end of a treble note is mostly the room). With **SHOW BY MIDI**
   ticked, the key you play (and its velocity) is chosen. The sample is heard as it is, without the Recorded Room.
2. **MAKE** (10.9.8: **every microphone**, one after the other, each with its own AUTO BODY measure) processes every
   sample into a separate container beside the original one — `<name>-dry.wptl` for DRY 1, `-dry2`, `-dry3` (same
   encryption and password). In the background, with a progress bar, and **STOP** beside MAKE to cancel: nothing is
   written. **The original samples are never touched**, and MAKE always starts again from them (never dry on dry).
   The piano plays ORIG.: MAKE makes the first free version. The piano plays DRY n: MAKE asks whether to **replace**
   DRY n (its settings stay) or make a **new version** beside it, to compare processings. When it is done, the piano
   plays the version made: tune it by ear and **SAVE**.
3. **PIANO PLAYS: ORIG. | DRY 1 | DRY 2 | DRY 3** — the version the whole piano plays (also after the instrument's
   name, in the title of the main window: click it). Each one with its own settings: a version never saved starts
   from ORIG.'s. Changing version first offers to save the changes not saved. **Delete...** removes a version that is
   not playing (its samples and its settings; the originals and the other versions are untouched). Switching does
   not measure AUTO BODY again.
4. **Then make a new Piano Model capture (.srpiano), and run AUTO CAL of Resonance and of Recorded Room again**: they were
   measured on the sound with its room. The Recorded Room AUTO CAL then finds no room and switches **Recorded Room off**
   (10.9.9): put the piano in the room you want with the REVERB (ALGO or IR).

**Formats.** The original samples stay exactly as recorded. The -dry samples are always **24-bit FLAC** (lossless), at
the original's sample rate, even when the originals are 16-bit: once the room and the hiss are taken out, the tails of
the notes go below the 16-bit floor (−96 dB), and only 24 bits keep them clean. A -dry made from 16-bit samples is
therefore larger than the original container (about twice); MAKE's message shows both sizes.

**Safety.** If the -dry file is moved or deleted, or a sample is missing in it, the original is played (the panel says
so); the version chosen is kept and comes back with the file. A `<name>-dry.wptl` beside the `.wptl` is found on its
own. Instruments saved with 10.9.0 open in older versions with their original samples.

**Files of the versions** (10.9.8). SAVE writes the version playing in its own file — `Name.ptlset` for ORIG.,
`Name.dry.ptlset`, `Name.dry2.ptlset`, `Name.dry3.ptlset` for DRY 1–3 — beside the samples. You never deal with them:
the list shows **Name** once, and **Rename**, **Move to the Trash** and **SAVE AS** under a new name take the versions
along. Rename keeps the names of the samples (`.wptl`, `-dry.wptl`), which every version uses. An instrument saved
before 10.9.8 with some microphones on -DRY opens as it was saved; choose ORIG. to put them back on the originals.
**A protected library**: its instruments and their versions are never overwritten — SAVE AS under your own name
(the versions come along).

### Making the fundamentals coherent: AUTO BODY (10.9.3)

A real piano has a logical proportion between the **fundamental** of each note and its upper partials: very low in the
bass (on A0 the fundamental is 40 to 50 dB under the partials — normal on every piano), high in the treble, and falling
a little from pp to ff (a harder strike brings the upper partials up). That proportion, key by key, is part of what
makes one piano sound unlike another of the same model. Recordings break it: a layer recorded another day, close
microphones, a room mode. **AUTO BODY** measures it on every sample (the fundamental against partials 2 to 8, 100 ms to
0.6 s after the strike, 1.5 s in the bass) and moves each fundamental — its own band only — towards **the piano's own
coherent proportion**. No other piano is used as a reference: the piano is corrected from itself.

In the same panel (the button now reads **DRY / DENOISE / BODY...**):

- **BODY: OFF | LAYERS | LAYERS + KEYS.** **LAYERS** makes the layers of each key coherent with each other (a common
  progression from pp to ff, taken from the neighbouring keys); the level of each key — its character — is kept. It is
  the safe choice. **LAYERS + KEYS** also brings each key towards its neighbours: the piano becomes more even (it also
  corrects the microphones and the room), at the cost of some of its individual character — listen to the whole piano.
  At most ±6 dB.
  **Use LAYERS first** (10.9.5): a real piano is never even — some notes sing more, the registers and the change from
  wound to plain strings differ — and those small differences are a large part of its realism; LAYERS keeps them.
  Keep **LAYERS + KEYS** for a recording that is uneven from key to key because of the recording itself (a microphone
  that hollows out a register, a room mode that swells a few notes, keys recorded another day).
- **AMOUNT** (0–100 %): how much of the measured correction is applied (a bracket links AMOUNT and GLOBAL to BODY).
- **GLOBAL** (0 to +6 dB): added to every fundamental after AUTO BODY — the lack that close microphones share (the
  fundamental is radiated by the whole soundboard and builds up at a distance). All of it up to C5, fading to nothing
  at C7, as BODY on the main window. Works with BODY OFF too. A piano often needs less volume afterwards: part of the
  loudness we hear is the fundamental.

The line under the key shows the correction for the sample chosen (**BODY +2.8 dB** = its fundamental is raised,
**−3 dB** = lowered; the measure takes a few seconds the first time), and **> PROCESSED** plays it. **MAKE** writes it
into the -dry with DRY and DENOISE (or alone, with DRY and DENOISE at 0): nothing to compute when you play. The attack
stays the original: the change is faded in from the strike over 30 ms. When a raised fundamental could take a strike
above 0 dBFS, the whole -dry of the microphone is written lower by one value and given back when it is played: nothing
clips, the balance stays. A -dry made with 10.9.2 or before has no BODY: MAKE it again. Then run AUTO COLOR and BALANCE
again as usual.

### From a raw library to a finished piano (10.9.3)

Each step measures what the one before left, so the order matters (10.9.5: DRY is optional):

1. **Import** the samples; **FILL GAPS** if some keys have none, then **ALIGN ATTACKS**.
2. A **Piano Model capture** (.srpiano).
3. **AUTO DYN1** or **AUTO DYN2** (and the Samples setting it advises), **RANGE** if wanted, **FIX STEPS**.
4. **AUTO COLOR**, **BALANCE**, **AUTO RELEASE** (it asks for the last damped key), **LEVEL / AUTO**.
5. **SAVE SAMPLES**, then save the preset.
6. On the main window: **AUTO CAL** of Resonance and of Recorded Room, then the room — **ALGO** or an **IR** (REVERB);
   **TEMPERAMENT** if wanted.

**Optional, a dry version**: once the samples and the instrument are saved, **DRY / DENOISE / BODY** (BODY: **LAYERS**
first), **MAKE** (every microphone: the piano then plays DRY 1); then a new **Piano Model capture** and the **AUTO CAL**
again (they were measured on the sound with its room), and **SAVE**: DRY 1 keeps them, ORIG. keeps its own.

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
| **Release** | 0 = **Auto** (PianoToLife's damper model; no damper above Undamped Keys Above); a time in ms; all the way right = **Infinite** (no damper: undamped top keys) |
| **Tune** | Fine tune in cents. **ALL 0** (10.9.4, at the end of the row): every key's Tune back to 0, the pitch of the samples as recorded (one UNDO step) |
| **Pan** (10.9.9) | The key's place left / right, **L 100 %** to **R 100 %**: one side is lowered, nothing is mixed, so the stereo image of the note is kept. Click the value to type it ("L 12", "R 8", "C"). **ALL C**: every key back to the centre (one UNDO step). Saved with the instrument, each version its own. Not to be confused with **BALANCE** (the volume between the keys) |
| **Pan AUTO** (10.9.9, optional) | For recordings whose neighbouring keys do not sit at the same place (spaced microphones, few partials in the treble). It measures the left / right of every key and finds the piano's own line from the bass to the treble — **its slope and its ends are kept, no position of the microphones is guessed**. Only the keys clearly off that line get a Pan that brings them back onto it (at most 6 dB); the others go to the centre. The result window gives the line found and has an **AMOUNT** (70 % by default, heard at once while you play). **Not for every recording**: listen before and after, Cmd/Ctrl+Z if the places sounded more natural as recorded. Nothing changes when the piano shows no clear line |
| **LP** + cutoff + **LP Vel** | Optional low-pass per voice; LP Vel makes soft notes darker (up to 3 octaves lower at 100 %) |
| **Undamped** | Undamped Keys Above, for the whole piano (the main window's setting, in sync): the keys above it have no damper |

---

## 7. Saving and managing sets

| Button | What it does |
|---|---|
| **NEW** | An empty set (the set open now is not changed on disk) |
| **Name** (under the title) | Click to **RENAME** the set and its sample file (10.9.8: an instrument with DRY versions is renamed with its versions, and its samples keep their names) |
| **SAVE SAMPLES...** (10.6.0, was SAVE SET) | Makes the instrument: the samples go into an encrypted container (`.wptl`) in your library, rewritten only when samples change. The **mapping and all the settings are saved in the instrument** (`.ptlset`, **SAVE AS** in the main window) and in the session, as you hear them |
| Variants | A bright and a dark version of the same samples are simply **two instruments** (`.ptlset`) on the same `.wptl` - SAVE AS under another name (SAVE AS VARIANT is retired; old variants still open) |
| **PICTURE...** (10.6.0) | The picture of the sample bank (PNG / JPEG, like a Kontakt wallpaper), kept encrypted in its `.wptl` and shown in the main window in place of the strings photo, for every instrument of these samples. Remove it from the same menu |
| **PASSWORD...** | Protects EDIT with a password (playing the set never asks for it). Empty = no password |
| **CLEAR ALL** (10.4.3) | Empties the whole set (every key, every microphone), after a warning that gives the number of samples. UNDO brings it back; the files are not touched |
| **DELETE** | Removes the selected zones (see the table above) |
| **EXIT** (10.9.9, was BACK) | Returns to the main window. With changes not saved (**\*** in the preset box) it asks first: **Save and exit**, **Exit without saving** (nothing is lost: the settings stay until you load something else) or Cancel |

A set saved on Mac opens on Windows and back. Saving a preset in SAMPLER mode creates a **`[SAMP]` preset** that
carries the mapping and the resonance model; only the samples (`.wptl`) stay apart.

---

## 8. The MIX window: microphones and streaming

### Microphones

Each of the 5 microphones has its strip: **name** (double-click to rename), **ON** (an off microphone is not
loaded: no memory, no CPU), **solo**, **mute**, **L↔R** (mirrors the stereo image: the pianist's or the audience's view), **level**,
**Stereo** (10.8.1, see below), **WIDE**, **delay** (to line a distant
microphone up with the close ones, or keep its natural room delay) and a **TRUE PEAK** meter (red = it clipped;
click to reset). Ready-made mixes: **Close**, **Player**, **Hall** (moving a control makes it Custom).

**Stereo** (10.8.1, in place of Pan and Width): two points, **L** and **R**, show where the left and the right channel
of the microphone go. Drag a point; drag between them to move the whole image. Apart = as recorded; closer = a
narrower image you can place anywhere; crossed = mirrored (blue, L↔R lit — L↔R crosses them); together = one point
**M**, a mono microphone at that place (pull left or right to separate them). Double-click: as recorded. The text
under it gives the centre and the width. The image moves at constant power, without losing level (the old Pan was a
balance that lowered one side). **WIDE** (100–200 %) widens the image beyond the recording (click once to type a
value, double-click = 100 %). Older instruments are
converted (same place; a changed pan or width may sound slightly different).

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

**LIBRARY** chooses the folder of your sets (put it on your fastest disk). With the copy option, SAVE SAMPLES copies the
samples into a `Samples` folder beside the set.

---

## 9. Playing the sampler

In SAMPLER mode, PianoToLife's engines play on your samples:

- **Sympathetic resonance**, with the piano's own Piano Model (`.srpiano`) — capture one from your set
  (Capture), so the resonance has the colour of your piano. In SAMPLER mode the capture reads the samples directly,
  offline, at the centres of your layers: a few minutes instead of a real-time recording. Tick the microphones of the
  model in the capture window (MIC 1 by default) and prefer the **close microphones**: room microphones put the hall's
  reverberation into the decays of the strings (PianoToLife's Recorded Room gives that room back to what it adds, the REVERB puts the whole piano in a hall).
- **Sustain**: always Host Sustain in SAMPLER, with a native **half pedal** on the voices themselves (Progressive,
  or Switch for on / off pedals). Sostenuto works.
- **Una corda**: simulated on every voice (level and partials of a real una corda, plus the halo of the string not
  struck). Since 10.8.0, **click the SOFT pedal** (*settings*) to set its **LEVEL** (how much quieter) and **TONE**
  (how much darker) to your taste and your piano — 0 = as measured.
- **Recorded Room AUTO CAL** (10.8.0, called Ambience before 10.9.3): measures the room of your samples in their own sound and puts everything PianoToLife
  adds in the same room (Room **Auto**) — see the [User Manual](USER_MANUAL.md).
- **Release**: PianoToLife's dampers; with a keyboard that sends release velocity, a slow release lands the damper
  later (see Keyboard Note-Off Floor and Curve in the KEYBOARD section).
- **Repeated notes**: a new strike does not cut the previous one; it goes on, a little lower (Per key in MIX).
- **Real piano repetition (REP)**, below CAL: instead of the round robins of the old sample libraries (several
  recordings of each note, played in turn), every strike gets the small differences of a real piano — level,
  brightness, decay, attack, a tiny detune in the bass, and the build-up of a key struck again while it sounds — as
  measured on the chosen reference (Grand D / Grand B / Upright). Off by default; saved in presets
  ([User Manual](USER_MANUAL.md#real-piano-repetition-rep)).
- **Tuning**: SR Transpose, SR Fine Pitch and SR A4 Tuning play on the sampler; the temperament: **TEMPERAMENT**
  (below).
- **BODY**: the perceived size of the piano.

**Layer detector** (next to Capture): plays a note at the 127 velocities and lists the real layers of the piano, to
check a set.  **LEVEL TEST**: plays A0, C2, C4, C6, C8 at velocity 127 and tells you whether the piano clips.

### Temperament and diapason (10.9.4)

**TEMPERAMENT** (main window, on the SR A4 Tuning row — not in EDIT, so it works on a set protected by a password)
measures the temperament your samples were recorded in, from the pitch of every key, and lets you play the piano in
another one. **The samples are never changed**: each key gets an offset added to its Tune, and the sympathetic
resonance follows (each free string, and how strongly it answers).

- **Temperament**: *Original (as recorded)*, Equal, Pythagorean, Just intonation, Werckmeister III, Kirnberger III,
  Vallotti, Young, Meantone 1/4, 1/3, 1/5, 1/6 and 2/7 comma; at the bottom of the list, **Load a Scala file
  (.scl)...** (12 notes per octave, repeating at the octave) and **Export as a Scala file (.scl)...** (the temperament
  played; the stretch and the A4 are not in a Scala file).
- **Tonic**: the key the temperament is built on (its purest chords).
- **Stretch**: 100 % = the stretch this piano was tuned with (measured), 0 % = none (every octave exact), up to
  200 %.
- **Diapason A4**: the same setting as SR A4 Tuning; **RESET** puts back the A4 the piano was recorded at.
- **AS RECORDED**: back to the temperament, the stretch and the A4 of the recording.
- **The table**: for each of the 12 notes, in cents from equal temperament (A = 0), **Recorded** (measured on the
  samples, A2 to C6), **Played** and **Shift**. **Click a Shift value to type your own** (−60 to +60): the
  temperament becomes **Custom (edited)**, saved with the set. Under it: the stretch recorded (C2 to C7) and the
  temperament closest to the recording (e.g. *closest to Equal, 1.5 c rms*).

Each key keeps its own small differences (a real tuning is never perfect); only the temperament and the stretch
change. The temperament is saved in the set, the presets and the sessions; every change is a named UNDO step in EDIT.
Pitch bends and tuning messages of MIDI files are not used. The Piano Model capture always measures the samples as
recorded, so it never needs to be done again for a temperament.

---

## 10. Files and folders

| File | What it is |
|---|---|
| `.ptlset` | **The instrument** (like a Kontakt `.nki`): the mapping as you hear it (velocities, gains, key settings, AUTO DYN, BALANCE...), the resonance model and every PianoToLife setting. Always in the folder of its `.wptl`, which it names relatively |
| `.wptl` | **The samples** (like a Kontakt `.nkx`), in an encrypted container (password if set), with the bank's picture |
| `<name>-dry.wptl` | **The samples without their room** (10.9.0, made by DRY / DENOISE): same encryption, 24-bit FLAC, beside the `.wptl`. Optional: without it, the original samples play |

Since 10.6.0 a sampled piano is **two files: the `.ptlset` and the `.wptl`**, in the same folder of your library. In
SAMPLER mode the **PRESET list shows the instruments of your library** and the instrument's name is shown large above it;
**SAVE** (10.7.1) saves your changes over the instrument shown, **SAVE AS** saves the instrument beside its samples under
a new name, and saving over an instrument of **other samples** asks first (new name / replace / cancel). A
**right-click on the PRESET box** renames the instrument or moves it to the Trash (only the `.ptlset`: its samples
stay); **FOLDER** opens the instrument's folder. The library folder is asked the first time you use the SAMPLER (change it in MIX > LIBRARY).
An instrument elsewhere opens by **double-clicking it** (standalone) or **dropping it on the window**. **PASSWORD...**
(main window) locks / unlocks SAMPLER EDIT for a protected set. The `[SAMP]` presets of earlier versions are converted
into instruments the first time (the old files go to the Trash). Keep a piano's folder together: it can then be moved
or backed up as it is.

**Missing samples**: if a session or a preset points to a piano whose samples were deleted, moved or are on a disk
that is not connected, a window asks you to **LOCATE** them (PianoToLife remembers the new place) or to **FORGET**
that piano (it is then no longer asked about).

---

## 11. Troubleshooting

| Problem | Solution |
|---|---|
| A sample is on the wrong key or octave | Check the orange zones in the side panel; put the note in the file name (`C4`, `060`); AUTO KEY on |
| Two layers are in the wrong order | AUTO NAME with dynamics in the names; otherwise move them by hand |
| Steps when playing crescendo (orange / red boundaries) | AUTO DYN, then FIX STEPS; SOFT TIMBRE on; HARD TIMBRE for a dark top layer |
| Few layers: you still hear that it is another sample at a boundary | XCOLOR (16), then ALIGN ATTACKS; check with LISTEN (10.6.3) |
| The piano is too bright for you | HAMMER a little below 0 (−20 % is a good start) |
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
